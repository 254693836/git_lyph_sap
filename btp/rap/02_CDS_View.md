# CDS View

## 役割

RAPではCDS View Entityを使い、データ構造、関連、意味情報を定義します。通常は内部利用のInterface Viewと、サービス公開用のProjection Viewを分けます。

## Interface Viewの例

```abap
@AccessControl.authorizationCheck: #NOT_REQUIRED
@EndUserText.label: 'Travel'
define root view entity ZI_TRAVEL
  as select from ztravel as Travel
  composition [0..*] of ZI_BOOKING as _Booking
{
  key Travel.travel_id as TravelId,
      Travel.agency_id as AgencyId,
      Travel.customer_id as CustomerId,
      Travel.begin_date as BeginDate,
      Travel.end_date as EndDate,
      Travel.status as OverallStatus,
      _Booking
}
```

## Projection Viewの例

```abap
@EndUserText.label: 'Travel Projection'
@Metadata.allowExtensions: true
define root view entity ZC_TRAVEL
  provider contract transactional_query
  as projection on ZI_TRAVEL
{
  key TravelId,
      AgencyId,
      CustomerId,
      BeginDate,
      EndDate,
      OverallStatus,
      _Booking : redirected to composition child ZC_BOOKING
}
```

## 重要な設計要素

| 要素 | 用途 | 注意点 |
| --- | --- | --- |
| `key` | レコードの一意性を定義 | 更新可能なエンティティでは安定したキーを使用 |
| Association | エンティティ間の参照 | 親子関係でなければAssociationを使用 |
| Composition | ルートと子のライフサイクルを共有 | 子はルート経由で操作する設計が基本 |
| Annotation | UI・検索・意味情報を付与 | UI用はProjection層に置くことを基本とする |

## よく使うUIアノテーション

```abap
@UI.lineItem: [{ position: 10 }]
@UI.selectionField: [{ position: 10 }]
@EndUserText.label: '顧客'
CustomerId,
```

## 確認観点

- ルートと子の関連が正しく定義されているか。
- キー項目がProjectionにも公開されているか。
- 画面専用のアノテーションが内部モデルへ過度に混在していないか。
- CDSを有効化した後、参照先も有効になっているか。
