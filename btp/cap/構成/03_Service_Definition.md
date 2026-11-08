# Service Definition

## 役割

サービス定義は、データモデルのうち外部へ公開するEntity、投影、Actionを定義します。内部のDBモデルをそのまま公開せず、サービスごとに必要な形へProjectionするのが基本です。

## サービス例

```cds
using { my.sales as db } from '../db/schema';

@path: '/catalog'
service CatalogService {
  entity Orders as projection on db.Orders {
    *,
    items
  };
  entity OrderItems as projection on db.OrderItems;

  action submitOrder(orderID : UUID) returns Orders;
}
```

## ODataでの確認

```bash
cds watch
```

起動後に次を確認します。

- `/odata/v4/catalog/$metadata` が表示できる
- `/odata/v4/catalog/Orders` でEntity Setを取得できる
- `POST`、`PATCH`、`DELETE` が想定どおり動く
- Actionがメタデータに公開されている

## 設計上の注意

| 観点 | 指針 |
| --- | --- |
| 公開範囲 | Entity・項目とも必要最小限にする |
| サービス名 | 業務領域を表す安定した名前にする |
| Projection | API契約をDB構造から分離する |
| バージョン | 破壊的変更時は利用者への影響を確認する |
| Path | 外部公開URLとして分かりやすく固定する |

サービスを追加したら、必ずメタデータと実際の応答を確認してからUIや外部連携を進めます。
