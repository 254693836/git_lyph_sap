# SAP Integration Suite 学習メモ

今回の相談内容を、初めて使う方向けに整理したメモです。

## 1. BTPとIntegration Suiteの関係

- **SAP BTP**：アプリ開発やデータ活用、システム連携などを支えるプラットフォーム。
- **SAP Integration Suite**：SAPや社内外のシステムを連携するためのサービス群。
- **Cloud Integration**：Integration Suiteの機能の一つ。データを受け取り、加工して、送り先へ届ける。
- **iFlow（アイフロー）**：Cloud Integrationで作成・実行する、具体的なデータ連携の処理手順。

## 2. 主な役割を四つに分けて理解する

これは学習のための整理です。公式に機能が四つだけと決まっているわけではなく、役割が重なる場合もあります。

| 順番 | 役割 | 何をするか | 例 |
|---|---|---|---|
| 一つ目 | Cloud Integration | データを受け取り、変換して、送る | Salesforceの受注データをSAP向けの形式に変えて送る |
| 二つ目 | API Management | APIの利用者、アクセス回数、利用状況などを管理する | 在庫照会APIを利用できる人や呼び出し回数を制御する |
| 三つ目 | イベント連携 | 出来事を通知し、受信したシステムが処理を開始する | 注文確定を倉庫システムに知らせる |
| 四つ目 | B2B・EDI連携 | 取引先と、合意した形式で業務データを交換する | 発注書や請求書を会社間で交換する |

APIは、他のシステムの機能を呼び出すための窓口です。イベントは「注文が入った」などの出来事、B2Bは会社同士の取引、EDIは決められた形式の電子データ交換を指します。

## 3. 今回想定している案件

**Salesforce（SFDC）から受注データを取得 → マッピング → SAP S/4HANAへ受注の新規登録を依頼する。**

一つ目：Salesforceから必要な受注データを取得する。

二つ目：送り先のAPIが受け取れる項目・形式に変換する。これがマッピング。

三つ目：変換したデータをS/4HANAへ送り、登録結果を確認する。

この目的なら、Cloud IntegrationとiFlowの設計・開発が中心になります。実際の作業には、接続・認証の設定、エラー対応、テストも含まれます。

※Salesforce側の取得対象、取得方法、S/4HANA側の登録APIは、この相談ではまだ決めていません。

## 4. iFlowの中でデータを変換する方法

代表的な方法を三つ挙げます。必要に応じて組み合わせます。

### 一つ目：Message Mapping

画面で、送り元と送り先の項目を対応させます。標準関数を使った加工もできます。

例：送り元の商品コードを、送り先の品目番号に対応する項目へ設定する。コードの値そのものが異なる場合は、対応表などを使った変換も必要です。

### 二つ目：Content Modifier

固定値や、処理の途中で使う値、メッセージの内容などを設定します。

例：接続先への送信に必要な値を設定する。

### 三つ目：Groovy Script

画面の標準設定だけでは表しにくい処理を、Groovyで記述します。

例：独自の条件による値の変換、データの整形、複数項目を使った計算。

**まず標準機能を使い、足りない部分をスクリプトで補う**と考えると整理しやすくなります。単純な文字列加工や日付変換は、標準機能でもできる場合があります。

## 5. GroovyとCAPの違い

| 項目 | GroovyをiFlow内で使う方法 | CAPで別のサービスを作る方法 |
|---|---|---|
| 作るもの | iFlow内の加工処理 | 独立した業務アプリやAPI |
| 開発方法 | iFlowにスクリプトのステップを追加する | JavaやNode.jsなどでCAPアプリを開発する |
| 実行場所 | Cloud Integration | アプリを配置した実行環境 |
| iFlowとの関係 | 処理の一部として実行する | 公開したAPIをiFlowから呼び出す |

GroovyはJavaに近いプログラミング言語です。短いスクリプトとして書けて、Javaのクラスやライブラリも利用できます。

今回の案では、まずiFlow内の標準機能とGroovyで実現できるか考えます。複雑だから必ずCAPが必要、というわけではありません。

別のサービスを使う場合の例：

**受注取得 → CAPアプリのAPIを呼ぶ → 独自チェックの結果を受け取る → マッピング → S/4HANAへ登録依頼**

外部APIの呼び出しには、例えばRequest Replyのステップを使います。

## 6. 画面操作の大筋

Integration Suiteの利用環境と必要な権限が準備されている前提です。画面の表記は環境により異なる場合があります。

### 一つ目：連携パッケージを作る

**Design → Integrations and APIs → Create**

関連するiFlowなどをまとめる入れ物を作ります。既存のパッケージを使う場合は、それを開きます。

### 二つ目：パッケージの中にiFlowを追加する

**Artifacts → Add → Integration Flow**

名前を付けて作成し、編集画面を開きます。

### 三つ目：処理の流れを編集する

**Edit**を選び、開始・終了の間に必要な処理を組み立てます。開始方法は、定期的にデータを取得するか、外部から受信するかなどによって変わります。

### 四つ目：接続を設定する

Salesforceからのデータ取得とS/4HANAへの送信に必要な接続方法、接続先、認証情報などを設定します。

### 五つ目：変換処理を設定する

Message Mappingで項目を対応させ、必要な場合にContent ModifierやGroovy Scriptを追加します。

処理の例：

**開始 → 受注取得 → 必要な前処理 → マッピング → S/4HANAへの登録依頼 → 結果の処理 → 終了**

これは処理順序を示す概念図です。実際のステップ構成は、開始方法や使用するAPIに合わせて決めます。

Groovyはマッピングの前後など、必要な位置に置けます。iFlow全体をGroovyで書く必要はありません。

### 六つ目：保存・反映・テストをする

**Save → Deploy**で実行環境に反映します。テストデータを流し、監視画面と送り先で、処理結果やエラー、受注の登録結果を確認します。

## 7. 今回の要点

1. 今回の案件は、SalesforceからS/4HANAへの受注データ連携。
2. 中心になるのは、Cloud IntegrationでiFlowを作る作業。
3. 変換は標準のマッピング機能を基本にし、必要な処理をGroovyで補う。
4. 必要なら、CAPなどで開発した外部APIを途中から呼ぶこともできる。
5. 最初にパッケージを作り、その中にiFlowを作成する。

## 参考：公式資料

- [SAP Integration Suiteの概要](https://learning.sap.com/courses/exploring-sap-platform-capabilities/illustrating-the-sap-integration-suite_b1c98a93-d3ca-4121-88ef-36bd397fae52)
- [パッケージとiFlowの作成・デプロイ](https://developers.sap.com/tutorials/cp-starter-integration-cpi-design-iflow)
- [Cloud Integrationの処理機能](https://help.sap.com/docs/cloud-integration/sap-cloud-integration/integration-capabilities?locale=en)
- [外部APIを呼び出すRequest Reply](https://help.sap.com/docs/integration-suite/sap-integration-suite/define-request-reply)
- [CAP Javaのサービス公開](https://cap.cloud.sap/docs/java/cqn-services/application-services)
- [Apache Groovy](https://groovy-lang.org/)

