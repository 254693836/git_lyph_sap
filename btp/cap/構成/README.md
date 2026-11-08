# SAP CAP 学習・実装ガイド

このフォルダは、SAP Cloud Application Programming Model（CAP）をNode.jsで開発するための実践ガイドです。データモデルからODataサービス、業務ロジック、Fiori Elements、運用上の確認までを順に学べます。

## 対象環境

- Node.js LTS
- SAP CDS Development Kit（`@sap/cds-dk`）
- Visual Studio Code と CDS Language Support
- SAP BTP（Cloud Foundry）および、必要に応じてSAP HANA Cloud

## 学習順序

1. [01_CAPアーキテクチャ.md](./01_CAPアーキテクチャ.md) — プロジェクト構造と処理の流れ
2. [02_CDS_Model.md](./02_CDS_Model.md) — データモデルと関連
3. [03_Service_Definition.md](./03_Service_Definition.md) — ODataサービス公開
4. [04_Event_Handlers.md](./04_Event_Handlers.md) — 業務ロジックとAction
5. [05_Validation.md](./05_Validation.md) — 入力検証とエラー応答
6. [06_Authentication_Authorization.md](./06_Authentication_Authorization.md) — 認証・認可
7. [07_Fiori_Elements.md](./07_Fiori_Elements.md) — Fiori Elements UI
8. [08_トラブルシューティング.md](./08_トラブルシューティング.md) — 調査と解決

## 最小プロジェクト構成

```text
my-cap-app/
├── db/
│   ├── schema.cds
│   └── data/
├── srv/
│   ├── catalog-service.cds
│   ├── catalog-service.js
│   └── catalog-ui.cds
├── app/
│   └── catalog/
├── test/
├── package.json
└── mta.yaml                # BTPへMTAデプロイする場合
```

## 最初の実行

```bash
npm install
cds watch
```

起動後、ターミナルに表示されるURLを開き、サービスエンドポイントとFioriプレビューを確認します。最初はSQLiteでローカル実行し、アプリケーションの完成後にHANA CloudとBTP向け設定を追加する進め方が安全です。

> 既存の [CAP構成.md](../CAP構成.md) は、受注アプリを例にした全体構成資料です。本フォルダはそれを補う、実装順の学習資料です。
