# SAP Fiori Launchpad 設定と SAP BTP 比較

更新日: 2026-11-13。主対象: SAP S/4HANA オンプレミスの Fiori Launchpad（FLP）。BTP側は主に SAP Build Work Zone, standard edition を想定。リリース・サービスのエディションによって画面名や機能が異なる。

## 1. 基本構成

- **Business Catalog**: アプリの起動コンテンツを管理。アプリランチャー（タイル）やターゲットマッピングを含む。
- **Semantic Object + Action**: 例 `#SalesOrder-display`。Intent-Based Navigation に使う識別子で、ターゲットマッピングが起動先アプリへ解決する。
- **Space → Page → Section → タイル**: Launchpad上のナビゲーション・表示レイアウト。
- **PFCG Role**: Business Catalog、Space、バックエンド権限などをユーザーへ付与。異なるロール経由で付与することも可能。
- **業務権限**: タイル表示・アプリ起動とは別。会社コード、利益センタ、活動などの権限オブジェクトやCDSアクセス制御がデータの可視性・更新可否を決める。

```text
ユーザー
  └─ PFCGロール
      ├─ Business Catalog ── タイル/Target Mapping ── アプリ起動
      ├─ Space ── Page ── Section ── タイル配置
      └─ 業務・サービス権限 ── OData/ABAP/CDS ── データ参照・更新
```

**ポイント**: カタログへの登録はアプリの起動資格に関係し、ページへの配置は表示場所に関係する。カタログにあるアプリをページへ置かなくても、検索から起動できる場合があるが、検索機能や権限設定に依存する。

## 2. S/4HANA オンプレミスの設定手順

1. アプリの種類、SAPUI5 component、サービス（OData等）、必要なICFサービス、システムエイリアスを確認する。
2. Launchpad Content Manager（環境例: `/UI2/FLPCM_CUST`）などで Business Catalog、アプリランチャー、Target Mapping を整備する。
3. Target Mapping で Semantic Object、Action、アプリ種別、起動先の識別子/パス等を正しく設定する。
4. Space と Page を作り、Page 内の Section にアプリを配置し、Space に Page を関連付ける。
5. PFCGロールへカタログとSpaceを割り当て、必要なサービス権限・業務権限も設定する。権限プロファイル生成とユーザー割当を確認する。
6. 対象ユーザーで「タイル表示 → 起動 → データ参照/更新」を別々にテストする。

管理トランザクション、Space/Page編集方法、メニュー名はS/4HANAのリリースで異なる。

## 3. 検索名と表示名：今回の実機検証

今回の操作では、カタログ内のアプリ設定に表示名と検索名があり、異なる値を入力した結果、**検索名では見つかるが表示名では見つからない**ことを確認した。また、カタログから検索したアプリをホーム画面へ追加できた。

これは**今回のシステム・検索画面での観察**であり、全FLPに共通する仕様とは断定しない。検索対象フィールド、複数キーワード入力可否、区切り文字、ホーム画面への追加可否はリリース・検索モード・パーソナライズ設定に依存する。

運用時は、ユーザーが実際に入力する業務用語で検索できるかをテストする。表示名と検索名を同じにすることが必須とは限らない。

## 4. 従来のGroups方式とSpaces & Pages

| 項目 | Groups方式 | Spaces & Pages方式 |
|---|---|---|
| 表示構造 | Groupにタイルを配置 | Space → Page → Sectionにタイルを配置 |
| 特徴 | 従来型のホーム画面 | ナビゲーションを階層化 |
| アプリ起動 | CatalogとTarget Mapping等 | CatalogとTarget Mapping等 |
| 権限 | PFCG等 | PFCG等 |
| 利用可否 | リリース/設定次第 | リリース/設定次第 |

## 5. S/4HANA FLP と BTP Launchpad の比較

「BTP Launchpad」は文脈によって旧Launchpad serviceやSAP Build Work Zoneを指す。以下は **SAP Build Work Zone, standard edition** を中心とした概念比較で、設定項目が完全に1対1で対応するわけではない。

| 観点 | S/4HANAオンプレミス FLP | BTP / SAP Build Work Zone, standard edition |
|---|---|---|
| 主な基盤 | S/4HANA ABAP環境 | SAP BTPサブアカウント |
| 主な管理 | FLP Content Manager、Space/Page管理、PFCG | Site/Content管理、BTP cockpit等 |
| コンテンツ | Business Catalog、Target Mapping、Space/Page | Content Provider、Catalog、Role、Siteなど |
| ロール | ABAP PFCG | BTP Role Collection、サービス側Roleなど |
| 表示レイアウト | Space → Page → Section | Site内のページ/ナビゲーション（エディション依存） |
| アプリ配置 | S/4標準Fiori、独自SAPUI5など | BTPアプリ、連携したS/4コンテンツなど |
| 接続 | ABAP/Gateway/ICF/ODataなど | Destination、必要に応じCloud Connector |
| 業務データ権限 | S/4の業務権限が必要 | BTP側権限に加え、接続先S/4側の権限も必要 |
| 注意点 | クライアント、サービス有効化、PFCG | 認証、サブアカウント、Destination、コンテンツ公開 |

## 6. トラブルシューティング

| 症状 | 主な確認事項 |
|---|---|
| タイルが表示されない | ユーザーへのSpace割当、Page/Section配置、Catalog割当、パーソナライズ |
| 検索でアプリが見つからない | 検索画面の種類、検索名/キーワード、Catalog権限、検索設定 |
| タイルはあるが起動できない | Semantic Object/Action、Target Mapping、アプリID/パス、ICF/OData |
| アプリ起動後に権限エラー | PFCG、サービス権限、`SU53`、`STAUTHTRACE` |
| 特定データだけ参照できない | 会社コード等の業務権限、CDS DCL、検索条件 |
| ODataエラー | ブラウザNetwork、`/IWFND/ERROR_LOG`、バックエンドログ |

## 7. 学習時の確認ポイント

- 「画面に表示される」「検索で見つかる」「アプリが起動する」「業務データを操作できる」は別の条件。
- Target Mapping の Semantic Object/Action は主に起動先解決に使い、検索用語そのものとは区別する。
- BTP側は **どの製品/エディションか** を先に特定してから設定を比較する。
- 変更後は管理者画面だけでなく、実ユーザーの権限で動作確認する。
