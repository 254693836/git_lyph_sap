# Behavior Definition

## 役割

Behavior Definition（BDEF）は、エンティティに対して許可する更新操作、Action、Validation、Determination、Draftなどを宣言します。Managed RAPでは標準CRUDの保存処理をフレームワークに委ねられます。

## Managed Behaviorの例

```abap
managed implementation in class zbp_i_travel unique;
strict ( 2 );

define behavior for ZI_TRAVEL alias Travel
persistent table ztravel
lock master
authorization master ( instance )
{
  create;
  update;
  delete;

  association _Booking { create; }

  action ( features : instance ) accept result [1] $self;
  determination setInitialStatus on modify { create; }
  validation validateDates on save { create; update; field BeginDate, EndDate; }

  mapping for ztravel
  {
    TravelId      = travel_id;
    AgencyId      = agency_id;
    CustomerId    = customer_id;
    BeginDate     = begin_date;
    EndDate       = end_date;
    OverallStatus = status;
  }
}
```

## Projection Behavior

公開層では、Interface Behaviorで定義した操作のうち、外部へ公開するものだけを `use` で指定します。

```abap
projection;
strict ( 2 );

define behavior for ZC_TRAVEL alias Travel
{
  use create;
  use update;
  use delete;
  use action accept;
}
```

## 代表的な宣言

| 宣言 | 用途 |
| --- | --- |
| `create; update; delete;` | 標準CRUDの許可 |
| `action` | 業務固有の操作 |
| `determination` | 項目の自動補完・派生値計算 |
| `validation` | 保存前の業務ルール検証 |
| `lock master` | ルートエンティティのロック管理 |
| `authorization master` | インスタンス単位の権限制御 |

## 設計上の注意

- UIから不要な操作を公開しないため、Projection Behaviorで公開範囲を明示します。
- Actionは更新・確定・取消など、CRUDでは表しにくい業務操作に使います。
- 標準CRUDの範囲で実現できる処理を、不要にUnmanaged化しないようにします。
