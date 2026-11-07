# RAP と CAP（Node.js）の比較

> 対象は ABAP Cloud の RAP と SAP CAP Node.js（JavaScript、OData V4）です。両者は Fiori elements と CDS を活用できる一方、実装単位と実行基盤は異なります。ここでの「対応」は設計上の対応関係であり、構文をそのまま置換できることを意味しません。

## 1. 役割と全体像

| 観点 | RAP（ABAP RESTful Application Programming Model） | CAP Node.js |
| --- | --- | --- |
| 主な実行基盤 | ABAP Cloud / ABAP Platform | SAP BTP（Node.js） |
| データモデル | ABAP CDS View Entity | CAP CDS（`.cds`） |
| 業務動作 | Behavior Definition（BDEF）と Behavior Implementation（ABAP） | CDS サービスとイベントハンドラ（JavaScript） |
| 公開 API | Service Definition / Service Binding | `service.cds` と `cds.service.impl` |
| UI | Fiori elements（CDS annotation） | Fiori elements（CDS annotation） |
| トランザクション | RAP の LUW・EML | `cds.tx(req)` を使う CAP トランザクション |

RAP は BDEF で CRUD、Action、Draft、ロックなどの**振る舞いを宣言**し、ABAP 実装で未管理の部分や独自ロジックを補います。CAP は CDS でモデルとサービスを宣言し、標準 CRUD はフレームワークに任せ、必要な箇所だけ JavaScript の `before` / `on` / `after` ハンドラで拡張します。

## 2. 代表的なファイル構成

| 目的 | RAP の例 | CAP Node.js の例 |
| --- | --- | --- |
| 永続モデル | `ZI_ORDER`（CDS view entity） | `db/schema.cds` |
| 公開用投影 | `ZC_ORDER`（projection view） | `srv/catalog-service.cds` の projection |
| 振る舞い定義 | `ZI_ORDER` の BDEF | CDS の entity / action 定義 |
| 振る舞い実装 | Behavior Pool（ABAP class） | `srv/catalog-service.js` |
| サービス公開 | Service Definition / Binding | CDS service（OData V4 を提供） |
| UI 定義 | Metadata Extension / CDS annotation | `app/.../annotations.cds` またはサービス CDS |
| DB 変更 | ABAP Dictionary / CDS テーブル定義 | `db/*.cds`、デプロイメント設定 |

CAP では概ね `db` にドメインモデル、`srv` に API と業務ロジック、`app` に Fiori UI を置きます。RAP では Interface View（`ZI_*`）を業務モデル、Projection View（`ZC_*`）を公開モデルとして分ける構成が一般的です。

## 3. CDS と BDEF の対応

### RAP：CDS + BDEF

RAP の CDS はデータモデル／投影を表現し、BDEF が変更可能性や業務操作を表現します。Managed RAP では `create`、`update`、`delete`、`association`、`action`、`determination`、`validation`、`lock master`、`etag master` などを BDEF に宣言します。Unmanaged RAP は永続化や保存を ABAP 実装で制御します。

```abap
managed implementation in class zbp_i_order unique;
strict ( 2 );
define behavior for ZI_Order alias Order
persistent table zorder
lock master
etag master ChangedAt
{
  create;
  update;
  delete;
  association _Items { create; }
  action approve result [1] $self;
  determination setInitialStatus on modify { create; }
  validation validateHeader on save { create; update; }
}
```

### CAP：CDS + イベントハンドラ

CAP の CDS は永続エンティティ、サービスへの公開、association/composition、action/function、annotation を表現します。振る舞いのタイミングや実装は JavaScript ハンドラで登録します。単純な CRUD は実装不要です。

```cds
// db/schema.cds
namespace my.bookshop;
using { cuid, managed } from '@sap/cds/common';

entity Orders : cuid, managed {
  status : String(20) default 'NEW';
  amount : Decimal(15,2);
  items  : Composition of many OrderItems on items.parent = $self;
}
entity OrderItems : cuid {
  parent   : Association to Orders not null;
  product  : String(80) not null;
  quantity : Integer not null;
}
```

```cds
// srv/catalog-service.cds
using { my.bookshop as db } from '../db/schema';
service CatalogService {
  @odata.draft.enabled
  entity Orders as projection on db.Orders actions {
    action approve() returns Orders;
  };
  entity OrderItems as projection on db.OrderItems;
}
```

## 4. CRUD の考え方

| 処理 | RAP | CAP Node.js |
| --- | --- | --- |
| 標準 CRUD | BDEF に `create; update; delete;` を宣言（Managed RAP は標準永続化） | サービスに entity を公開すれば標準 OData CRUD を提供 |
| 独自 CRUD | Unmanaged RAP または ABAP 実装で保存ロジックを記述 | `this.on('CREATE' / 'UPDATE' / 'DELETE', ...)` は標準処理の置換が必要なときだけ使用 |
| 検証 | Validation を BDEF に宣言し、ABAP 実装 | `before` ハンドラで `req.error` / `req.reject` |
| 表示用補正 | Determination / 取得ロジック／仮想要素 | `after('READ', ...)`。大量件数の全件加工は避ける |

CAP では標準 CRUD を不要に `on('READ')` で置換しないことが重要です。標準の `$filter`、`$select`、ページング、認可を保ちやすくなります。

## 5. Determination と Validation

### RAP

- **Determination**: 作成・更新・アクションなどの契機に派生値や状態を設定します。`on modify` / `on save` を目的に応じて使い分けます。
- **Validation**: 保存時に業務ルールを検証し、`reported` / `failed` でメッセージと失敗キーを返します。
- 同じトランザクション内で複数エンティティを扱う場合は、実行順序・副作用（side effects）も設計します。

### CAP Node.js

- **Determination 相当**: `before('CREATE'/'UPDATE')` で初期値・正規化を設定し、必要に応じて `after` で応答用の値を補います。
- **Validation 相当**: `before` で入力値、状態遷移、親子関係、認可を検証します。UI の必須表示だけには依存しません。
- 親子の合計や状態を更新する場合は、子の変更と親の再計算を同じ `cds.tx(req)` で実行します。

```js
// srv/catalog-service.js
const cds = require('@sap/cds')
const { SELECT, UPDATE } = cds.ql

module.exports = cds.service.impl(function () {
  const { Orders } = this.entities

  this.before(['CREATE', 'UPDATE'], Orders, req => {
    if (req.data.amount != null && req.data.amount < 0) {
      req.error(400, '金額は 0 以上を入力してください', 'amount')
    }
    if (req.event === 'CREATE' && !req.data.status) req.data.status = 'NEW'
  })

  this.on('approve', Orders, async req => {
    const tx = cds.tx(req)
    const order = await tx.run(SELECT.one.from(Orders).where({ ID: req.params[0].ID }))
    if (!order) return req.reject(404, '対象データがありません')
    if (order.status !== 'SUBMITTED') return req.reject(400, '申請済みだけ承認できます')

    await tx.run(UPDATE(Orders).set({ status: 'APPROVED' }).where({ ID: order.ID }))
    return tx.run(SELECT.one.from(Orders).where({ ID: order.ID }))
  })
})
```

## 6. Action

RAP の Action は BDEF に定義し、Behavior Pool のメソッドで実装します。CAP の Action はサービス CDS に定義し、`this.on()` に処理を書きます。どちらも承認・取消・再計算のように、単純 CRUD では表せない意図ある業務操作に適しています。

| 設計ポイント | RAP | CAP Node.js |
| --- | --- | --- |
| 定義場所 | BDEF | service CDS |
| 実装場所 | Behavior Pool | `srv/*.js` の `this.on()` |
| 対象 | instance / static action | bound / unbound action |
| 実行前確認 | 状態、権限、対象行 | 状態、権限、対象行 |
| 更新単位 | RAP LUW | `cds.tx(req)` |

Action の実装では、対象の存在確認、状態遷移可能性、利用者権限、更新件数を確認し、失敗を利用者が理解できるメッセージに変換します。外部連携を伴う長時間処理は同期 Action に閉じ込めず、メッセージングやジョブへの委譲を検討します。

## 7. Draft と Lock

| 機能 | RAP | CAP Node.js |
| --- | --- | --- |
| Draft | BDEF の `with draft` と Draft Table／Draft Action | entity に `@odata.draft.enabled`。CAP が draft 管理を提供 |
| 編集競合 | `lock master` / `lock dependent`、ETag | 楽観ロックは `@odata.etag` でバージョン用項目を指定。必要時は DB のロック戦略も設計 |
| 同時更新対策 | Lock と ETag の役割を分けて設計 | ETag、トランザクション、更新条件で競合を扱う |

Draft は「保存前の編集中データ」を扱うための機能であり、単なる同時更新防止とは別です。RAP では Draft 対応の BDEF、CAP では `@odata.draft.enabled` を起点にし、Fiori elements の編集フローと整合させます。運用要件（編集の引継ぎ、放棄、期限切れ）も確認します。

## 8. UI Annotations

両方とも CDS annotation で Fiori elements の List Report / Object Page を大きく構成できます。表示列、検索、Value Help、フィールドグループ、編集可否、Action の表示をまず annotation で定義し、UI5 extension は標準機能で足りない場合に限定します。

```cds
annotate CatalogService.Orders with @(
  UI.HeaderInfo : {
    TypeName       : '受注',
    TypeNamePlural : '受注一覧',
    Title          : { Value: ID },
    Description    : { Value: status }
  },
  UI.LineItem : [
    { Value: ID,     Label: 'ID' },
    { Value: status, Label: '状態' },
    { Value: amount, Label: '金額' },
    { $Type: 'UI.DataFieldForAction', Action: 'CatalogService.approve', Label: '承認' }
  ],
  UI.SelectionFields : [ status ],
  UI.FieldGroup #General : { Data: [
    { Value: status }, { Value: amount }
  ] }
);
```

RAP では Metadata Extension に分離することが多く、CAP では CDS の annotation ファイルに分離できます。いずれも UI annotation は画面上の利便性を与えるものであり、認可や業務検証の代替にはなりません。

## 9. Header / Child（親子）検証

親子は、RAP では composition と BDEF の association／lock／authorization を組み合わせ、CAP では `Composition of many` とサービス投影を用いて扱います。重要なのは API や画面を経由しない更新でも整合性を守ることです。

| チェック対象 | 実装方針 |
| --- | --- |
| 子の親 ID | 子を作成・変更する際、親が存在し、利用者がその親を操作できることを確認 |
| 子の項目 | 数量が正、品目が有効、単位・通貨が親と矛盾しないことを確認 |
| 親の状態 | 親が確定・取消済みなら、子の追加・変更・削除を拒否 |
| 合計値 | 子の確定後に DB 集計で親の合計を再計算。クライアント値を信用しない |
| 保存順序 | 親子の更新を同一トランザクションで処理。失敗時は全体をロールバック |

CAP の例では、子の処理後に親を再計算する場合、対象の親を特定し、`cds.tx(req)` 内で集計・更新します。複数子行を一度に変更するケース、削除時、Draft 有効時もテスト対象に含めます。

```js
// 例: 子の入力検証（実際の entity 名・親子更新方針に合わせて調整）
this.before(['CREATE', 'UPDATE'], this.entities.OrderItems, async req => {
  if (req.data.quantity != null && req.data.quantity <= 0) {
    req.error(400, '数量は 1 以上を入力してください', 'quantity')
  }
  const parentId = req.data.parent_ID
  if (parentId) {
    const parent = await cds.tx(req).run(
      SELECT.one.from(this.entities.Orders).where({ ID: parentId })
    )
    if (!parent) req.error(400, '親データが存在しません', 'parent_ID')
    else if (['APPROVED', 'CANCELLED'].includes(parent.status)) {
      req.error(400, '確定または取消済みの受注は明細を変更できません')
    }
  }
})
```

## 10. 実装時の判断基準

1. **標準 CRUD を優先する**: RAP は Managed RAP、CAP は自動公開 CRUD をまず使います。
2. **業務操作は Action にする**: 承認、取消、再計算、一括更新は明示的な Action にします。
3. **検証はバックエンドで保証する**: UI annotation やクライアントチェックだけで済ませません。
4. **認可は宣言的設定を主軸にする**: RAP の access control／authorization、CAP の `@requires` / `@restrict` を使い、必要な行レベル判定を実装で補います。
5. **整合性は一つのトランザクションで守る**: 親子更新、合計、状態更新を分断しません。
6. **外部連携は安全に分離する**: 接続先・秘密情報をコードに埋め込まず、Destination／サービスバインディングを使い、再送・冪等性・失敗時の扱いを設計します。

## 11. レビュー用チェックリスト

- [ ] CDS のモデル、公開 API、UI annotation の責務が分かれている
- [ ] RAP の BDEF または CAP のイベントハンドラに、必要な業務ルールがある
- [ ] 標準 CRUD を不要に独自実装していない
- [ ] Action は状態・認可・対象存在を確認してから更新する
- [ ] Draft とロック／ETag の目的を混同していない
- [ ] Header / Child の存在、状態、合計、保存単位をバックエンドで検証している
- [ ] 失敗時のメッセージが利用者に理解でき、技術情報や秘密情報を含まない
- [ ] 正常系、入力エラー、認可エラー、競合、Action、親子更新をテストしている
