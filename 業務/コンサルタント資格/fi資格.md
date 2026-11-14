# SAP FI コンサルタント認定資格ガイド

> 最終確認日：2026-11-14（SAP公式公開情報を基準）
>
> **注意**：認定試験の形式・受験条件・価格は変更されます。申込前に必ず[公式認定資格ページ](https://learning.sap.com/certifications)と購入画面で再確認してください。

## 1. FI資格の種類と比較

SAP FI（Financial Accounting：財務会計）関連の代表的な認定資格は、次の2つです。

| 項目 | C_TS4FI | C_S4CFI |
|---|---|---|
| 公式資格名 | SAP Certified – SAP S/4HANA Cloud Private Edition, Financial Accounting | SAP Certified – Implementation Consultant – SAP S/4HANA Cloud Public Edition, Financial Accounting |
| 主な対象 | S/4HANA Cloud Private Editionの財務会計設定・運用 | S/4HANA Cloud Public EditionのFI導入・設定 |
| 試験時間 | **180分（3時間）** | **180分（3時間）** |
| 試験言語 | **英語** | **英語** |
| 現行試験形式 | **System Based Assessment（SAPシステムを用いた実技評価）** | **System Based Assessment（SAPシステムを用いた実技評価）** |
| 公式の試験構成 | **1 Activity** | **1 Activity** |
| 合格基準 | **60%** | **61%** |
| 公式URL | [C_TS4FI](https://learning.sap.com/certifications/sap-certified-associate-sap-s-4hana-for-financial-accounting) | [C_S4CFI](https://learning.sap.com/certifications/sap-certified-associate-implementation-consultant-sap-s-4hana-cloud-public-edition-financial-accounting-1) |

**「1 Activity」＝「問題が1問だけ」という意味ではありません。** 1つの実技評価の中に複数の操作タスクが含まれる可能性がありますが、公式ページでは個別タスク数は公表されていません。

### 過去の試験形式との違い

- 旧バージョン（例：`C_TS4FI_2023`）では選択式・複数選択式の知識問題が中心でした。
- 上記の**現行C_TS4FI / C_S4CFIは実技形式**です。旧試験向けの「80問」などの情報を現行試験にそのまま当てはめないでください。
- このフォルダの[fi練習問題50問.md](./fi練習問題50問.md)は**知識定着用のオリジナル選択式問題**で、SAP公式の過去問・現行実技試験の再現問題ではありません。

## 2. 現行試験の形式・受験方法

1. **System Based Assessment**：用意されたSAPシステム上で設定・業務操作などのタスクを実行し、システムの結果に基づいて評価されます。
2. **オープンブック**：SAP Help Portal、SAP Learning、SAP Communityなどの公開資料を参照できます。AIツールの利用条件はSAP公式の最新ルールを確認してください。
3. **ライブ試験監督なし（Unproctored）**：従来のWebカメラ監督型と異なる形式です。SAP Universal ID等で本人・受験権限を管理します。
4. **受験前の準備**：SAP Universal ID（異なるドメインのメールアドレスを2つ紐づける案内あり）、有効な受験回数、技術的な接続・PC環境を確認します。
5. **受験開始**：対象資格の公式ページまたはLearning Journeyの試験画面から開始します。残り受験回数と制限時間を確認してください。
6. **合格後**：デジタルバッジを取得します。認定は原則12か月有効で、更新（Stay Certified）に関する条件があります。

参照：[SAP実技試験FAQ](https://learning.sap.com/helpcenter/certification-support/certification-practical-exam)／[実技試験の準備FAQ](https://learning.sap.com/helpcenter/certification-support/practical-exam-preparation)／[受験手順](https://learning.sap.com/helpcenter/certification-support/step-by-step-guide-practical-exams)。

## 3. C_TS4FI の主な試験範囲（SAP公式の表示）

| 出題領域（公式英語表記） | 公式の比率 |
|---|---|
| Accounts Payable | **21–30%** |
| Create a new Document Type | **11–20%** |
| Perform Value Adjustments for Overdue Receivables | **10%以下** |
| Accounts Receivable | **10%以下** |
| Create a House Bank, Configure and Execute the Payment Run | **10%以下** |
| Perform Customizing, Acquisition, and Depreciation Postings | **10%以下** |
| Asset Accounting | **10%以下** |
| Establish a new Company Code | **10%以下** |
| General Ledger | **10%以下** |

※上記は2026-11-14に公式ページで確認した分類です。各比率は単純に合計して100%にするための数値ではなく、SAPが公開する範囲表示をそのまま記載しています。

### C_S4CFI の主な試験範囲（SAP公式の表示）

- General Ledger – Closing：**11–20%**
- Accounts Receivable：**11–20%**
- Segment Reporting、Deferral Postings、G/L Tolerances and Automatic Clearing、General Ledger、Dunning Process for a Delayed Payer、Create Fixed Asset in a new Asset Class、Asset Accounting、Down Payment Processing via Automatic Payment、Accounts Payable、Business Partner and Payment Terms：**それぞれ10%以下**

## 4. 受験料・購入プラン

**2026-11-14時点、SAP日本公式の認定試験販売ページでは「Price upon request（価格は問い合わせ）」と表示されており、日本円の確定価格は公開ページから確認できませんでした。** 金額を固定値として扱わず、SAP Store／SAP Trainingの購入画面で国・税区分・購入条件を指定して確認してください。

| 選択肢 | 公式に確認できた内容 | 料金 |
|---|---|---|
| SAP Certification exam, **two attempts** | **受験2回分**。同一資格の再受験または異なる2分野への受験に使用可能。対象の実機練習環境**10時間**が含まれる | **要見積・購入画面で確認** |
| **SAP Learning Hub** | 年間**4回分の認定試験**、学習コンテンツ、実習環境、Stay Certifiedの更新評価など | **要見積・購入画面で確認** |
| 1回・6回などの旧／別販売プラン | SAPサイトに案内が残る場合があります。提供状況・価格は地域・時期で異なります。例：旧CER001は公式商品ページで**2026-09-30販売終了予定**と案内 | **購入可能かを要確認** |

- 受験権と認定維持は別の問題です。**2回受験チケットにStay Certified更新評価は含まれない**ため、認定維持にはLearning Hub等の最新条件を確認してください。
- 古いブログやPDFに掲載された数万円の価格は、**2026年11月の確定価格ではありません**。
- 公式価格・購入窓口：[SAP Certification 日本サイト](https://www.sap.com/japan/training-certification/sap-certification.html)、[SAP Learning Hub 日本サイト](https://www.sap.com/japan/training-certification/learning-hub.html)。

## 5. 有効期限・更新

- 認定資格のデジタルバッジは原則**12か月有効**。
- 更新対象の場合、満了前の**90日間の更新期間**にStay Certifiedの評価を受ける案内があります。
- Learning Hubの契約有無などにより更新方法が変わるため、更新直前に公式情報を確認してください。
- 参考：[SAP認定プログラムFAQ](https://learning.sap.com/helpcenter/certification-support/certification-program)、[SAP実技試験受験手順](https://learning.sap.com/helpcenter/certification-support/step-by-step-guide-practical-exams)。

## 6. 学習すべきFIの基本知識

| 分野 | 重要事項・設定例 | 関連T-code（主にSAP GUIの代表例） |
|---|---|---|
| 組織構造 | 会社コード、勘定コード表、会計年度バリアント | OX02、OB29 |
| G/L | 勘定マスタ、伝票タイプ、転記キー、転記期間、統制勘定 | FS00、OBA7、OB41、OB52、FB50 |
| AP | 仕入先BP、請求書、支払条件、支払、消込 | BP、FB60、F-53、F-44、F110 |
| AR | 得意先BP、請求書、入金、消込、督促 | BP、FB70、F-28、F-32、F150 |
| 銀行 | House Bank、銀行勘定、自動支払、銀行明細 | FI12（環境によりFiori等）、FBZP、F110 |
| 固定資産 | 資産クラス、減価償却領域、取得・除却、償却 | AS01、AFAB |
| 決算 | 外貨評価、残高繰越、財務諸表バージョン、元帳 | 環境・リリースにより異なる |
| S/4HANA固有 | Universal Journal、ACDOCA、Business Partner、Ledger | BP、SE16H等 |

**注意**：T-codeはSAP GUIを用いるPrivate Edition / On-Premiseでの学習例です。Public EditionではFioriアプリや設定手順が異なる場合があります。

## 7. 推奨学習方法

1. **知識の確認**：まず[FI練習問題50問](./fi練習問題50問.md)を解く（学習目標：正答率80%以上）。
2. **SAP操作の練習**：会社コード、伝票タイプ、G/L、仕入先・得意先、支払、固定資産を実機で設定・操作する。
3. **エラーへの対応**：転記期間未開放、勘定設定不備、権限不足、消込不一致などを再現して原因を説明する。
4. **英語での練習**：公式試験は英語のため、FI用語・操作指示を英語でも理解する。
5. **公式Learning Journeyで仕上げる**：実技課題・Practice System・技術要件を確認する。

## 8. 公式参照URL一覧

1. [SAP認定資格一覧](https://learning.sap.com/certifications)
2. [C_TS4FI（Private Edition FI）](https://learning.sap.com/certifications/sap-certified-associate-sap-s-4hana-for-financial-accounting)
3. [C_S4CFI（Public Edition FI）](https://learning.sap.com/certifications/sap-certified-associate-implementation-consultant-sap-s-4hana-cloud-public-edition-financial-accounting-1)
4. [実技試験FAQ（形式・言語・参照資料）](https://learning.sap.com/helpcenter/certification-support/certification-practical-exam)
5. [実技試験の準備FAQ](https://learning.sap.com/helpcenter/certification-support/practical-exam-preparation)
6. [実技試験の受験手順・受験回数・更新](https://learning.sap.com/helpcenter/certification-support/step-by-step-guide-practical-exams)
7. [SAP認定プログラムFAQ（料金・受験方式）](https://learning.sap.com/helpcenter/certification-support/certification-program)
8. [SAP Certification 日本サイト（購入・価格確認）](https://www.sap.com/japan/training-certification/sap-certification.html)
9. [SAP Learning Hub 日本サイト](https://www.sap.com/japan/training-certification/learning-hub.html)

---
**免責**：この資料は自主学習用に作成した非公式まとめです。SAPの認定・価格・試験規約はSAP公式の最新表示を優先してください。
