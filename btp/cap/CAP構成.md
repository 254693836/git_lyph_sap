# CAP（Node.js）構成

この資料は、SAP Cloud Application Programming Model（CAP）を Node.js と Fiori elements で実装する際の標準的な構成を、受注ヘッダー／明細アプリを例に整理したものです。

## 1. 全体構成

```text
sales-cap/
├─ db/
│  ├─ schema.cds                 # 永続データモデル、親子関係
│  └─ data/                      # 開発用の初期データ（必要な場合）
├─ srv/
│  ├─ sales-service.cds          # 公開する OData サービスと Action
│  ├─ sales-service.js           # 業務ロジック、検証、計算
│  └─ sales-ui.cds               # Fiori elements 用の UI annotation
├─ app/
│  └─ sales/
│     └─ webapp/manifest.json    # Fiori アプリと OData サービスの接続設定
├─ test/                         # 自動テスト
└─ package.json                  # 依存関係、CAP の実行設定
```

| レイヤー | 主な責務 | 主なファイル |
| --- | --- | --- |
| `db` | データモデル、テーブル、関連、初期データ | `schema.cds` |
| `srv` の CDS | OData API、公開範囲、Action、画面 metadata | `*-service.cds`、`*-ui.cds` |
| `srv` の JavaScript | 入力チェック、状態遷移、計算、外部連携 | `*-service.js` |
| `app` | Fiori elements の画面、ルーティング、UI5 拡張 | `webapp/manifest.json` |
| `test` | API・業務ルール・認可の自動テスト | `*.test.js` |

## 2. データモデル：`db/schema.cds`

データの項目、主キー、親子関係を定義します。受注ヘッダーと明細は `Composition` で表すと、親を中心とした深い登録・更新に適しています。

```cds
namespace sales;
using { cuid, managed } from '@sap/cds/common';

entity Orders : cuid, managed {
  orderNo     : String(20) not null;
  status      : String(20) default 'NEW';
  customer    : String(100) not null;
  totalAmount : Decimal(15,2) default 0;
  items       : Composition of many OrderItems on items.parent = $self;
}

entity OrderItems : cuid {
  parent    : Association to Orders not null;
  product   : String(100) not null;
  quantity  : Integer not null;
  unitPrice : Decimal(15,2) not null;
  amount    : Decimal(15,2);
}
```

- `cuid` は UUID の主キーを、`managed` は作成者・作成日時・更新者・更新日時を提供します。
- クライアントが送った合計値を信用せず、明細からサーバー側で再計算します。

## 3. サービス定義：`srv/sales-service.cds`

サービスで公開するエンティティを projection として定義します。単純な CRUD は CAP の標準機能が処理するため、個別実装は不要です。

```cds
using { sales as db } from '../db/schema';

service SalesService {
  @odata.draft.enabled
  entity Orders as projection on db.Orders actions {
    action approve() returns Orders;
  };

  entity OrderItems as projection on db.OrderItems;
}
```

| 要素 | 意味 |
| --- | --- |
| `projection` | DB モデルのうち、サービスとして公開する形を定義する |
| 標準 CRUD | `POST`、`PATCH`、`DELETE`、`GET` を CAP が提供する |
| `action approve()` | 承認のように、CRUD だけでは表せない業務操作を表す |
| `@odata.draft.enabled` | Fiori elements の編集途中データを扱う Draft を有効化する |

## 4. 業務処理：`srv/sales-service.js`

CAP では RAP の Determination / Validation のような専用キーワードではなく、イベントハンドラで実装します。

| 処理 | 主なイベント | 例 |
| --- | --- | --- |
| Validation | `before CREATE` / `before UPDATE` | 数量が 1 以上、単価が 0 以上か確認 |
| Determination 相当 | `before CREATE` / `before UPDATE` | 初期ステータス、明細金額を設定 |
| Action | `on('approve')` | 承認可能な状態か確認して状態を更新 |
| 表示専用の補正 | `after READ` | DB に保存しない表示値を追加 |

```js
const cds = require('@sap/cds')
const { SELECT, UPDATE } = cds.ql

module.exports = cds.service.impl(function () {
  const { Orders, OrderItems } = this.entities

  this.before(['CREATE', 'UPDATE'], OrderItems, req => {
    const { quantity, unitPrice } = req.data

    if (quantity != null && quantity <= 0) {
      req.error(400, '数量は 1 以上を入力してください', 'quantity')
    }
    if (unitPrice != null && unitPrice < 0) {
      req.error(400, '単価は 0 以上を入力してください', 'unitPrice')
    }
    if (quantity != null && unitPrice != null) {
      req.data.amount = quantity * unitPrice
    }
  })

  this.on('approve', Orders, async req => {
    const tx = cds.tx(req)
    const order = await tx.run(SELECT.one.from(Orders).where({ ID: req.params[0].ID }))

    if (!order) return req.reject(404, '対象の受注がありません')
    if (order.status !== 'SUBMITTED') {
      return req.reject(400, '申請済みの受注だけ承認できます')
    }

    await tx.run(UPDATE(Orders).set({ status: 'APPROVED' }).where({ ID: order.ID }))
    return tx.run(SELECT.one.from(Orders).where({ ID: order.ID }))
  })
})
```

親子を更新する場合、子の金額と親の合計を同じ `cds.tx(req)` の中で扱います。失敗時に一部だけが保存されないようにするためです。

## 5. 画面定義：`srv/sales-ui.cds`

ファイル名は自由です。`srv` 配下の CDS として読み込まれ、`using` と `annotate` で対象サービス・エンティティを指定します。

```cds
using { SalesService } from './sales-service';

annotate SalesService.Orders with @(
  UI.LineItem : [
    { Value: orderNo,     Label: '受注番号' },
    { Value: customer,    Label: '顧客' },
    { Value: status,      Label: 'ステータス' },
    { Value: totalAmount, Label: '合計金額' },
    { $Type: 'UI.DataFieldForAction',
      Action: 'SalesService.approve', Label: '承認' }
  ],
  UI.SelectionFields : [ orderNo, customer, status ],
  UI.PresentationVariant #Default : {
    SortOrder : [ { Property: createdAt, Descending: true } ]
  }
);
```

| UI 要件 | 主な annotation | 実装場所 |
| --- | --- | --- |
| 一覧に出す列 | `UI.LineItem` | `srv/*-ui.cds` |
| 検索・フィルター項目 | `UI.SelectionFields` | `srv/*-ui.cds` |
| 初期ソート | `UI.PresentationVariant` | `srv/*-ui.cds` |
| 業務ボタン | `UI.DataFieldForAction` | `srv/*-ui.cds` |
| Value Help、表示・編集可否 | CDS annotation | `srv/*-ui.cds` を基本とする |

標準 annotation で表現できない特殊なレイアウト、複雑な画面操作、独自ダイアログは、Fiori / UI5 extension 側で実装します。

## 6. 検索、ソート、ページング

CAP の OData サービスは、標準的な検索・ソート・ページングを提供します。Node.js で全件を取得してから JavaScript で並べ替える実装は、通常は避けます。

| 機能 | 主な担当 | 例 |
| --- | --- | --- |
| フィルター | OData / Fiori elements | `$filter=status eq 'NEW'` |
| ソート | OData / Fiori elements | `$orderby=createdAt desc` |
| ページング | OData / CAP | `$top=20&$skip=0` |
| 全文検索 | OData / CAP | `$search=顧客名` |
| 初期表示の順序 | UI annotation | `PresentationVariant` の `SortOrder` |

ページングの既定件数や上限は、要件と性能に応じて CAP の query limit 設定を設計します。大量データに対する全件読込や、JavaScript 上での絞り込みは避けます。

## 7. Fiori アプリとの関係

Fiori elements は `manifest.json` で OData サービスを参照し、サービスの metadata に含まれる UI annotation を読み取って画面を生成します。

```text
Fiori elements
    ↓ OData metadata を取得
SalesService
    ├─ sales-service.cds  （公開 API と Action）
    ├─ sales-ui.cds       （一覧、検索、初期ソート、ボタン）
    └─ sales-service.js   （チェック、計算、状態遷移）
    ↓
db/schema.cds             （データモデル）
```

## 8. 実装・レビュー時の確認事項

- [ ] データ項目と親子関係は `db` に定義されている
- [ ] 公開するエンティティだけを `srv` の projection に出している
- [ ] 入力チェックと業務ルールは UI だけでなく `before` でも検証している
- [ ] 合計・状態更新は同一トランザクションで行っている
- [ ] 承認・取消などは Action として明示している
- [ ] 一覧列・検索・初期ソートは UI annotation を優先している
- [ ] ソート・ページングを独自の全件 JavaScript 処理で実装していない
- [ ] UI だけでは表現できない場合に限って UI5 extension を使っている
