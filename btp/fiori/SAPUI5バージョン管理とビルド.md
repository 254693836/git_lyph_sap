# SAPUI5 / Fiori バージョン管理と開発・ビルドの整理

> SAP Fiori / Fiori Elements 開発についての会話を整理した学習メモ。バージョン番号は会話中の例であり、各環境の実測値を保証するものではありません。

## 1. 最重要：バージョンは一種類ではない

| 対象 | 設定・確認場所 | 意味・注意点 |
|---|---|---|
| 実際のSAPUI5ランタイム | ブラウザF12 Consoleで `sap.ui.version` | 現在の画面でロードされたSAPUI5のバージョン |
| S/4HANA / ABAPサーバー | Fiori Launchpadでの実測、Basisへの確認 | 本番側が提供するUI5ランタイム。配信元や構成を確認する |
| `manifest.json` | `sap.ui5.dependencies.minUI5Version` | アプリが要求する最低UI5バージョンの宣言。実行時のバージョンを固定する設定ではない |
| `ui5.yaml` | `framework.version` | UI5 Toolingで使うフレームワークライブラリのバージョン。ローカルserveやbuildに関係する |
| `package.json` | `@ui5/cli` 等のdependencies / devDependencies | 開発ツールのバージョン。SAPUI5ランタイムのバージョンとは別 |
| `webapp/index.html` 等 | `sap-ui-core.js` のbootstrap `src` | どこからUI5をロードするか。CDN、ローカル、サーバー等によりランタイムが変わる |
| 型定義・IDE補完 | npmパッケージ、拡張機能 | VS Codeでの補完や型チェックの基準。本番環境に自動連動するとは限らない |

**例**：ローカル画面で `sap.ui.version` が `1.141`、本番のUI5が `1.136` の場合、ローカルで動く新しいAPIが本番では利用できない可能性がある。

## 2. ローカルの実際のバージョンを確認する

1. VS Codeでプロジェクトを開き、必要に応じて `npm install`。
2. `npx ui5 serve` などで起動する（プロジェクトに応じて `npm run start` も利用）。
3. ブラウザでF12 → Console → `sap.ui.version` を実行。
4. F12 → Networkで `sap-ui-core.js` の読み込み元URLを確認。
5. `ui5.yaml` の `framework.version`、`index.html` のbootstrap設定、`manifest.json` の `minUI5Version` を照合。

**注意**：`sap.ui.version` はUI5 CLIのバージョンではなく、ブラウザで実行中のSAPUI5ランタイムのバージョン。

## 3. npm / UI5 Tooling のコマンド

| コマンド | 意味 |
|---|---|
| `npm install` | `package.json` / lockfileに基づき依存パッケージをインストール |
| `npm install --global @ui5/cli` | UI5 CLIをグローバルインストール（UI5ランタイムそのものではない） |
| `npx ui5 serve` | UI5 Toolingでローカル開発サーバーを起動。通常、ローカルCLIがあればそれを使用 |
| `npm run start` | `package.json` の `scripts.start` を実行。実際の処理はプロジェクトごとに異なる |
| `npx ui5 build` | UI5 Toolingでビルド。設定や引数に応じて出力内容が変わる |
| `npm run build` | `package.json` の `scripts.build` を実行。例：`ui5 build --all` |

`npm run start` と `npx ui5 serve` は常に同じとは限らない。まず `package.json` のscriptsを確認する。

## 4. buildで確認できること・できないこと

ビルドはアプリのリソース処理・最適化・圧縮・プリロード生成などを行い、通常は `dist/` に成果物を出力する。例：`Component-preload.js`。通常、SAPUI5フレームワーク全体をアプリ内に同梱するわけではない。

- 検出できる可能性：一部の設定不備、処理対象リソースの問題、ビルド時に検出される構文・変換エラーなど。
- **保証できないこと**：メソッドが本番UI5バージョンに存在するか、引数が正しいか、実行時にnull参照が起きないか、業務ロジックが正しいか。
- JavaScriptの例：`const obj = null; obj.getName();` は構文自体は成立するが、実行時にエラーになる。
- `npm run start` がソースをserveする設定なら、`npm run build` の後でも必ずしも `dist/` を表示しているわけではない。

**結論：ビルド成功 ≠ 本番での正常動作保証。** 実行テスト、対応API確認、必要に応じてLint・型チェック・自動テストを併用する。

## 5. 実際のプロジェクトでのバージョン方針

一般的な進め方：

1. **本番環境を確認**：S/4HANA / Launchpadで実際に読み込むSAPUI5のバージョン・配信元を確認。
2. **開発基準を決定**：本番で利用可能なAPIと互換性のあるバージョンをチーム標準とする。
3. **設定を整合**：`ui5.yaml`、`manifest.json`、型定義などの役割を踏まえて調整。すべてに同じ数字を機械的に記載するわけではない。
4. **ツールを別管理**：Node.js、UI5 CLI、npmなどは互換性を考慮して別途バージョンを決める。
5. **実環境で検証**：ローカルだけでなく、実際のデプロイ先やそれに近い環境で動作確認。

例：本番SAPUI5が `1.136` の場合、チームでそのバージョンを互換性の基準として合意し、`1.136` に存在しないAPIに依存しないようにする。開発ツールのバージョンまで `1.136` に揃える意味ではない。

## 6. トラブルシューティングのチェックリスト

- [ ] F12 Consoleの `sap.ui.version` を記録したか
- [ ] Networkで `sap-ui-core.js` の配信元を確認したか
- [ ] `ui5.yaml` の `framework.version` を確認したか
- [ ] `manifest.json` の `minUI5Version` を確認したか
- [ ] `index.html` やLaunchpadのbootstrapを確認したか
- [ ] `package.json` のscriptsとUI5 CLI依存を確認したか
- [ ] ビルドだけでなく実行時のConsoleエラーを確認したか
- [ ] 本番バージョンで利用可能なAPIか確認したか
- [ ] デプロイ先で動作検証したか

## 7. 会議での30秒説明例

「結論から申し上げると、ビルドが成功しても、本番環境で正常に動くとは限りません。原因として考えられるのは、ローカル環境と本番環境のSAPUI5バージョンの違いです。そのため、まず実際に読み込まれているUI5のバージョンと配信元を確認し、APIの互換性を検証する必要があります。」

---
作成日：2026-11-13
