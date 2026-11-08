# SAP RAP 学習用 Markdown 構成ガイド

このディレクトリでは、SAP RAP（RESTful Application Programming Model）の開発を、基礎からFiori Elements連携、運用時のトラブル対応まで段階的に学べるように整理します。

## 学習の進め方

1. `README.md` で全体像と前提知識を確認します。
2. `01_RAPアーキテクチャ.md` と `02_CDS_View.md` でデータモデルとRAPの構造を理解します。
3. `03_Behavior_Definition.md` から `06_Draft.md` で業務ロジックと編集処理を学びます。
4. `07_Fiori_Elements.md` でUI公開までを確認します。
5. 問題が発生した場合は `08_トラブルシューティング.md` を参照します。

## ファイル構成

| ファイル | 目的 | 想定記載内容 |
| --- | --- | --- |
| [README.md](./README.md) | 学習ガイドの入口 | RAPの概要、対象読者、必要な開発環境（ADT／ABAP環境）、学習順序、サンプルの実行方法、関連資料へのリンク |
| [01_RAPアーキテクチャ.md](./01_RAPアーキテクチャ.md) | RAPの全体構造を理解する | レイヤー構成（CDSデータモデル、Behavior、Service Definition／Binding、Fiori Elements）、Managed／Unmanaged RAPの違い、処理フロー、主な開発オブジェクト |
| [02_CDS_View.md](./02_CDS_View.md) | データモデルを定義する | Interface ViewとProjection Viewの役割、エンティティ・関連・コンポジション、キー設計、アノテーション、RAPで使用するCDS Viewの実装例 |
| [03_Behavior_Definition.md](./03_Behavior_Definition.md) | CRUDと業務操作を定義する | Behavior Definition（BDEF）の構文、Managed／Unmanagedの選択、create／update／delete、Action、Feature Control、Authorization、Behavior Implementationとの関係 |
| [04_Determination.md](./04_Determination.md) | 自動補完・派生値計算を実装する | Determinationの実行タイミング、`on modify`／`on save`、デフォルト値、項目連動、再入防止、実装パターンとテスト観点 |
| [05_Validation.md](./05_Validation.md) | 入力値・業務ルールを検証する | Validationの実行タイミング、メッセージと`reported`／`failed`、単項目・複数項目・関連エンティティの検証、エラー表示とテスト例 |
| [06_Draft.md](./06_Draft.md) | 下書き編集を扱う | Draft有効化の目的、Active／Draftデータ、Root／Child構成、Edit／Activate／Discardの流れ、ロック、ドラフト利用時の注意点 |
| [07_Fiori_Elements.md](./07_Fiori_Elements.md) | RAPサービスを標準UIへ公開する | Service Definition／Service Binding、OData V4、UIアノテーション、List Report／Object Page、Facet・LineItem・SelectionField、プレビューと公開手順 |
| [08_トラブルシューティング.md](./08_トラブルシューティング.md) | よくある問題を調査・解決する | Activationエラー、Behavior定義と実装の不整合、OData公開エラー、Draft・Lockの問題、Fiori表示不備、ログ確認、切り分け手順 |

## 推奨ディレクトリ構成

```text
btp/rap/
├── 構成md.md
├── README.md
├── 01_RAPアーキテクチャ.md
├── 02_CDS_View.md
├── 03_Behavior_Definition.md
├── 04_Determination.md
├── 05_Validation.md
├── 06_Draft.md
├── 07_Fiori_Elements.md
└── 08_トラブルシューティング.md
```

## 記載方針

各学習ファイルでは、次の順序を基本とします。

- **目的**：何を理解・実装するのか
- **前提条件**：必要なCDS、Behavior、権限、開発環境
- **実装手順**：ADTでの作成・設定・有効化の流れ
- **コード例**：ABAP CDS／BDEF／Behavior Implementation／アノテーション
- **確認方法**：サービスプレビュー、Fiori Elements、テストケース
- **注意点**：設計判断、制約、よくある失敗

> ファイル名の先頭番号は学習推奨順です。実際の開発では、CDS・Behavior・サービス定義・UIアノテーションを往復しながら実装します。
