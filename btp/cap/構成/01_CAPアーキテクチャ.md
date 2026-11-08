# CAPアーキテクチャ

## CAPとは

SAP CAPは、CDSでデータモデルとサービス契約を定義し、Node.jsまたはJavaで業務ロジックを実装するクラウドアプリケーション開発モデルです。標準CRUD、OData公開、認証連携、Fiori Elementsとの接続をフレームワークが支援します。

## レイヤー構成

| レイヤー | フォルダ | 主な責務 |
| --- | --- | --- |
| データ | `db/` | CDSエンティティ、関連、初期データ、DB設定 |
| サービス | `srv/` | OData公開、Action、イベントハンドラ、業務ルール |
| UI | `app/` | Fioriアプリ、UI5設定、画面固有の資産 |
| テスト | `test/` | API・業務ロジックの自動テスト |

## リクエストの流れ

```text
Fiori / 外部クライアント
  ↓ HTTP / OData
CAP Service（srv/*.cds）
  ↓ before / on / after handler
CDS Model（db/schema.cds）
  ↓
SQLite（ローカル） / SAP HANA Cloud（本番）
```

## 標準CRUDと独自ロジック

- Entityをサービスで公開すると、CAPは通常のCRUD OData APIを提供します。
- 入力補正や検証は `before` ハンドラで実装します。
- 標準CRUDを置き換える必要がある場合だけ `on` ハンドラを使います。
- 応答データの補完には `after` ハンドラを使います。
- 業務固有の確定・取消などはCDS Actionとして定義します。

## 推奨する開発順序

1. `db/schema.cds` でモデルを作成する。
2. `srv/*-service.cds` で公開対象を定義する。
3. `cds watch` でメタデータとCRUDを確認する。
4. `srv/*-service.js` で検証・Actionを実装する。
5. UIアノテーションとFiori Elementsを追加する。
6. テスト、認可、HANA／BTP向け設定を整備する。
