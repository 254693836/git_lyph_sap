# Fiori Elements

## 役割

Fiori Elementsは、CAPサービスのODataメタデータとUIアノテーションを利用して、List ReportやObject Pageを生成します。標準的な業務UIを少ないUI5コードで実装できます。

## UIアノテーション例

```cds
using CatalogService from './catalog-service';

annotate CatalogService.Orders with @(
  UI: {
    HeaderInfo: {
      TypeName: '注文',
      TypeNamePlural: '注文一覧',
      Title: { Value: customer }
    },
    LineItem: [
      { Value: ID,        Label: '注文ID' },
      { Value: customer,  Label: '顧客' },
      { Value: status,    Label: 'ステータス' },
      { Value: totalAmount, Label: '合計金額' }
    ],
    SelectionFields: [ status, orderDate ],
    Facets: [
      { $Type: 'UI.ReferenceFacet', Label: '基本情報',
        Target: '@UI.FieldGroup#General' }
    ],
    FieldGroup #General: {
      Data: [
        { Value: customer },
        { Value: orderDate },
        { Value: status }
      ]
    }
  }
);
```

## 画面追加の流れ

1. `cds add fiori` またはFiori toolsでアプリを作成します。
2. サービスURLとMain Entityを指定します。
3. UIアノテーションを追加します。
4. `cds watch` でローカルプレビューします。
5. 一覧、詳細、作成、更新、検索、エラー表示を確認します。

## 確認ポイント

- ODataメタデータにEntityとActionが含まれていること。
- LineItem、SelectionFields、HeaderInfoが意図した位置に表示されること。
- 権限によって不要な編集操作が実行できないこと。
- スマートフォンを含む各画面幅で表示が破綻しないこと。
