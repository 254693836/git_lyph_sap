# CAP JavaScript（Node.js）と CAP Java の比較

SAP Cloud Application Programming Model（CAP）は、Node.js / JavaScript と Java のどちらでも開発できます。両者は CDS、OData、Fiori elements を共通して利用しますが、業務処理の実装言語と開発環境が異なります。

## 1. 結論

- データモデル、サービス定義、UI annotation は CDS で記述し、JavaScript と Java でほぼ共通です。
- 入力チェック、金額計算、承認処理などの業務ロジックは、JavaScript では Node.js のイベントハンドラ、Java では Java の Event Handler で実装します。
- Fiori elements、OData、標準 CRUD、Action、Draft の考え方は共通です。
- JavaScript は手軽に始めやすく、Java は Spring Boot・静的型付け・既存 Java 資産との統合に向いています。

## 2. 全体比較

| 観点 | CAP JavaScript（Node.js） | CAP Java |
| --- | --- | --- |
| 主な言語 | JavaScript（必要に応じて TypeScript） | Java |
| 実行基盤 | Node.js | Java VM、一般に Spring Boot |
| パッケージ・ビルド | npm | Maven または Gradle |
| CDS | 共通 | 共通 |
| OData / Fiori elements | 共通 | 共通 |
| 標準 CRUD | CAP の generic handler | CAP Java の generic handler |
| 業務ロジック | `srv/*.js` のイベントハンドラ | `srv/src/main/java` の Event Handler |
| 型 | JavaScript は動的型。TypeScript を追加可能 | 静的型 |
| 主な起動方法 | `cds watch` / `npm start` | `mvn spring-boot:run` |
| 向いている場面 | Node.js・JavaScript の経験、迅速な開発、BTP サービス連携 | Java・Spring の経験、既存 Java 資産との統合、型安全性重視 |

## 3. ファイル構成の比較

### CAP JavaScript

```text
project/
├─ db/
│  └─ schema.cds
├─ srv/
│  ├─ sales-service.cds
│  ├─ sales-service.js
│  └─ sales-ui.cds
├─ app/
│  └─ sales/
└─ package.json
```

### CAP Java

```text
project/
├─ db/
│  └─ schema.cds
├─ srv/
│  ├─ sales-service.cds
│  ├─ sales-ui.cds
│  └─ src/main/java/
│     └─ .../SalesServiceHandler.java
├─ app/
│  └─ sales/
└─ pom.xml
```

| 役割 | JavaScript | Java |
| --- | --- | --- |
| データモデル | `db/schema.cds` | `db/schema.cds` |
| OData 公開・Action 定義 | `srv/sales-service.cds` | `srv/sales-service.cds` |
| Fiori UI annotation | `srv/sales-ui.cds` | `srv/sales-ui.cds` |
| 業務ロジック | `srv/sales-service.js` | `srv/src/main/java/...Handler.java` |
| 依存関係・ビルド | `package.json` | `pom.xml` |

## 4. CDS は共通

CDS は、JavaScript を選んでも Java を選んでも基本的に同じ書き方です。

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

サービス公開、Action、Fiori elements 用の UI annotation も CDS で定義します。したがって、JavaScript と Java のどちらを選んでも、CDS の知識は再利用できます。

## 5. サービス CDS と UI CDS は共通

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

```cds
using { SalesService } from './sales-service';

annotate SalesService.Orders with @(
  UI.LineItem : [
    { Value: orderNo, Label: '受注番号' },
    { Value: customer, Label: '顧客' },
    { Value: status, Label: 'ステータス' },
    { Value: totalAmount, Label: '合計金額' }
  ],
  UI.SelectionFields : [ orderNo, customer, status ]
);
```

- `sales-service.cds` は、どのデータと Action を OData API として公開するかを定義します。
- `sales-ui.cds` は、一覧列、検索条件、初期ソート、Action ボタンなどの Fiori 画面設定を定義します。
- この二つの CDS の役割は JavaScript と Java で変わりません。

## 6. 業務ロジックの比較

### JavaScript：イベントハンドラ

```js
module.exports = cds.service.impl(function () {
  const { OrderItems } = this.entities

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
})
```

### Java：Event Handler

```java
@Component
@ServiceName(SalesService_.CDS_NAME)
public class SalesServiceHandler implements EventHandler {

  @Before(event = { CqnService.EVENT_CREATE, CqnService.EVENT_UPDATE },
          entity = OrderItems_.CDS_NAME)
  public void validateAndCalculate(CdsWriteEventContext context) {
    // 数量・単価を検証し、明細金額を設定する
    // 実際の実装では context のデータを取得して検証・設定する
  }
}
```

| CAP の目的 | JavaScript | Java |
| --- | --- | --- |
| Validation | `before('CREATE' / 'UPDATE')` | `@Before` |
| Determination 相当 | `before` で初期値・計算値を設定 | `@Before` で初期値・計算値を設定 |
| Action 実装 | `on('approve', ...)` | `@On(event = 'approve')` |
| 応答値の追加 | `after('READ', ...)` | `@After` |
| トランザクション | `cds.tx(req)` | CAP Java のトランザクション管理を利用 |

## 7. 検索・ソート・ページング

両方とも、OData の標準機能を利用します。

| 機能 | JavaScript | Java |
| --- | --- | --- |
| フィルター | 共通：`$filter` | 共通：`$filter` |
| ソート | 共通：`$orderby` | 共通：`$orderby` |
| ページング | 共通：`$top` / `$skip` | 共通：`$top` / `$skip` |
| 全文検索 | 共通：`$search` | 共通：`$search` |
| 一覧の初期ソート | 共通：UI annotation | 共通：UI annotation |

これらは CAP / OData の標準機能なので、全件を取得して JavaScript や Java で独自にソート・ページングする必要は通常ありません。

## 8. 選択の目安

### JavaScript（Node.js）を選ぶ場合

- JavaScript / Node.js の経験がある
- CAP を早く学習・試作したい
- Node.js の BTP サービスや npm パッケージを活用したい
- 小規模から中規模のサービスを素早く作りたい

### Java を選ぶ場合

- Java / Spring Boot の経験や既存資産がある
- 厳密な型チェックを重視したい
- Java のライブラリや社内標準を使いたい
- 大規模な Java チームの開発プロセスに合わせたい

## 9. 参考リンク

- [CAP JavaScript 基礎サンプル](https://github.com/SAP-samples/cloud-cap-with-javascript-basics)
- [CAP Java 公式サンプル](https://github.com/SAP-samples/cloud-cap-samples-java)
- [CAPire: Node.js Core Services](https://cap.cloud.sap/docs/node.js/core-services)
- [CAPire: Java](https://cap.cloud.sap/docs/java/)
- [CAP参考リンク.md](./CAP参考リンク.md)
