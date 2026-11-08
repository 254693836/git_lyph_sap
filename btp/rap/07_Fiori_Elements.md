# Fiori Elements

## 役割

Fiori Elementsは、RAPが公開するODataサービスとCDS UIアノテーションから標準的なSAP Fiori画面を生成するフレームワークです。代表的なテンプレートはList ReportとObject Pageです。

## 公開までの流れ

1. Projection Viewを作成する。
2. Projection Behaviorで公開操作を定義する。
3. Service Definitionにエンティティを公開する。
4. OData V4のService Bindingを作成し、Publishする。
5. UIアノテーションを追加し、Fiori Elements Previewで確認する。

## Service Definitionの例

```abap
@EndUserText.label: 'Travel Service'
define service ZUI_TRAVEL {
  expose ZC_TRAVEL as Travel;
  expose ZC_BOOKING as Booking;
}
```

## 代表的なUIアノテーション

```abap
@UI.headerInfo: {
  typeName: 'Travel',
  typeNamePlural: 'Travels',
  title: { value: 'TravelId' }
}
annotate entity ZC_TRAVEL with
{
  @UI.lineItem: [{ position: 10 }]
  @UI.selectionField: [{ position: 10 }]
  TravelId;

  @UI.lineItem: [{ position: 20 }]
  CustomerId;

  @UI.facet: [{ id: 'General', type: #IDENTIFICATION_REFERENCE,
                label: '基本情報', position: 10 }]
  @UI.identification: [{ position: 10 }]
  BeginDate;
}
```

## 主なアノテーション

| アノテーション | 表示場所 |
| --- | --- |
| `@UI.lineItem` | List Reportの一覧列 |
| `@UI.selectionField` | 検索・絞り込み条件 |
| `@UI.identification` | Object Pageの項目 |
| `@UI.facet` | Object Pageのセクション |
| `@UI.headerInfo` | Object Pageのヘッダー |
| `@UI.fieldGroup` | 関連項目のグループ |

## 確認ポイント

- Service Bindingが有効化・Publish済みであること。
- UIアノテーションがProjection ViewまたはMetadata Extensionに定義されていること。
- Projection Behaviorで必要なCRUD／Actionを公開していること。
- ブラウザのメタデータキャッシュを考慮して、変更後に再読込すること。
