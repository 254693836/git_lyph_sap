# CDSデータモデル

## 基本方針

CAPのデータモデルは `db/schema.cds` に定義します。業務上のまとまりをEntityとして表し、親子関係はComposition、参照関係はAssociationで表現します。

## モデル例

```cds
namespace my.sales;

using { cuid, managed } from '@sap/cds/common';

entity Orders : cuid, managed {
  customer     : String(100) not null;
  orderDate    : Date;
  status       : String(20) default 'OPEN';
  totalAmount  : Decimal(15,2);
  items        : Composition of many OrderItems
                   on items.parent = $self;
}

entity OrderItems : cuid {
  parent       : Association to Orders not null;
  product      : String(100) not null;
  quantity     : Integer not null;
  unitPrice    : Decimal(15,2) not null;
}
```

## よく使う共通要素

| 要素 | 用途 |
| --- | --- |
| `cuid` | UUIDの主キー `ID` を自動で持つ |
| `managed` | 作成者・作成日時・更新者・更新日時を持つ |
| `Association to` | 他Entityへの参照 |
| `Composition of many` | 親と同じライフサイクルの明細 |
| `not null` | 必須項目の宣言 |
| `default` | 初期値の宣言 |

## AssociationとCompositionの選び方

- 注文と明細のように、親の削除時に子も削除される関係にはCompositionを使います。
- 顧客、商品マスタのように独立して存在する参照先にはAssociationを使います。
- Compositionの子は、通常は親経由で作成・更新します。

## 開発確認

```bash
cds compile db/schema.cds
cds watch
```

起動後、`/odata/v4/` のサービス一覧を確認します。モデル変更後は、キー、必須項目、関連の名前と多重度をレビューします。
