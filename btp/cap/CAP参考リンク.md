# CAP 参考リンク

CAP（Node.js / JavaScript）を学ぶために参照できる、公開 GitHub サンプルと公式ドキュメントの一覧です。

## 学習する順番

1. まず CAP Node.js の JavaScript 基礎を確認する
2. 次に、CAP と Fiori elements を組み合わせた構成を確認する
3. 画面 annotation、Draft、Action、初期ソートなどを確認する
4. 公式ドキュメントでイベントハンドラと OData の標準機能を確認する

## 公開サンプル

| 用途 | リポジトリ | 主に確認する内容 |
| --- | --- | --- |
| CAP Node.js / JavaScript の基本 | [cloud-cap-with-javascript-basics](https://github.com/SAP-samples/cloud-cap-with-javascript-basics) | `db`、`srv`、`app` の基本構成、JavaScript、`before` / `on` / `after` |
| CAP + HANA + Fiori の実践構成 | [cloud-cap-hana-swapi](https://github.com/SAP-samples/cloud-cap-hana-swapi) | データモデル、サービス CDS、Fiori annotation、Node.js ハンドラ、テスト |
| Fiori elements の画面設定 | [fiori-elements-feature-showcase](https://github.com/SAP-samples/fiori-elements-feature-showcase) | List Report、Object Page、Draft、Action、初期ソート・フィルター |
| CAP CDS の学習 | [cap-cds-hands-on](https://github.com/SAP-samples/cap-cds-hands-on) | CDS のデータモデル、関連、サービス定義 |
| CAP Java の基本・実践 | [cloud-cap-samples-java](https://github.com/SAP-samples/cloud-cap-samples-java) | CDS、OData V4、Fiori、Spring Boot、Java の Event Handler |


## CAP Java の例

- [cloud-cap-samples-java](https://github.com/SAP-samples/cloud-cap-samples-java) は、SAP が公開している CAP Java SDK の公式サンプルです。
- 本の管理・注文処理を題材に、CDS のデータモデル、OData V4、Fiori、H2 / SAP HANA、Java の Custom Event Handler を確認できます。
- Java で実装する業務処理は主に `srv/src/main/java` 配下に置かれます。CAP Node.js の `srv/*.js` に相当する役割です。
- `db/*.cds` や `srv/*.cds` などの CDS は、CAP Node.js / JavaScript / TypeScript と同じ書き方で共通して使えます。
- ローカル起動には Java 21 と Maven が必要です。詳細はリポジトリの README を確認してください。

## 今回の資料との対応

| 確認したい内容 | このリポジトリ内の資料 | 公開サンプルでの確認先 |
| --- | --- | --- |
| CAP の全体構成 | [CAP構成.md](./CAP構成.md) | `db`、`srv`、`app` の各フォルダ |
| サービス CDS | [CAP構成.md](./CAP構成.md) の「サービス定義」 | `srv/*-service.cds` |
| UI CDS と Fiori annotation | [CAP構成.md](./CAP構成.md) の「画面定義」 | `srv/*-ui.cds`、Fiori annotation |
| Validation / Determination 相当 | [capとrapの比較.md](./capとrapの比較.md) | `srv/*.js` の `before` ハンドラ |
| Action | [capとrapの比較.md](./capとrapの比較.md) | サービス CDS の Action と `srv/*.js` の `on` ハンドラ |
| 検索・ソート・ページング | [CAP構成.md](./CAP構成.md) の「検索、ソート、ページング」 | OData の `$filter`、`$orderby`、`$top`、`$skip` |

## 公式ドキュメント

- [CAPire: Node.js Core Services](https://cap.cloud.sap/docs/node.js/core-services)
  - `before`、`on`、`after` のイベントハンドラ
  - Validation、Action、トランザクション

- [CAPire: OData API](https://cap.cloud.sap/docs/guides/protocols/odata)
  - `$filter`、`$orderby`、`$top`、`$skip`、`$search`
  - CRUD、ETag、Draft などの OData 機能

- [CAPire: Generic Service Providers](https://cap.cloud.sap/docs/guides/services/served-ootb)
  - 標準 CRUD、入力検証、ページング、Fiori 対応の標準機能

## 確認のポイント

- 最初は `srv` の CDS と JavaScript を分けて確認する
- UI annotation は `*-ui.cds` または `*-annotations.cds` を探す
- 入力チェックや金額計算は `before CREATE` / `before UPDATE` を探す
- 承認・取消などは CDS の Action と JavaScript の `on` を対応させて確認する
- ソート・ページングは、まず OData の標準機能を使う。全件を JavaScript で取得して処理しない
