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

## 8. 補足：iFlowの接続先と認証情報を管理する方法

### 8-1. 今回説明した接続方法の前提

Salesforceから受注データを取得し、変換してS/4HANAへ登録依頼する連携を想定しています。以下は、標準のHTTP・ODataアダプターなどで、接続先URLと認証情報の参照名を設定する場合の基本的な整理です。

実際のAPI、アダプター、認証方式はまだ未決定です。必要な設定項目は、それらによって変わります。

### 8-2. 設定する場所は三つに分ける

| 順番 | 場所 | 管理する内容 |
|---|---|---|
| 一つ目 | iFlow | データを取得・変換・送信する処理の流れ |
| 二つ目 | iFlowのアダプター | 接続先URL、認証方式、使用する認証情報の登録名など |
| 三つ目 | Integration SuiteのSecurity Material | ユーザー名・パスワードやOAuth用の認証情報などを、種類に応じて登録 |

**URLはアダプター、認証情報はSecurity Material、アダプターから登録名で参照する**、という関係です。

ユーザー名やパスワードを、iFlowごとに直接書き込むという意味ではありません。登録済みの認証情報を複数のiFlowから参照することもできます。

### 8-3. S/4HANAへの接続をどこで定義するか

一つ目：iFlowの送り先として、S/4HANAを表すReceiverを配置します。

二つ目：送信処理（例えばRequest Reply）からReceiverへ線をつなぎ、利用するAPIに合わせた受信アダプターを選びます。

三つ目：その接続線のアダプターを選択し、Connectionなどの設定欄で接続先や認証を設定します。登録操作や送信方法などは、アダプターに応じてProcessingなどで設定します。

ここで「Receiver」は、データを受け取る相手であるS/4HANAを指します。「受信アダプター」という名称でも、iFlowから相手へ送るための接続設定です。

Receiverの箱は送り先を表し、接続線のアダプターが実際の接続方法を定義します。

### 8-4. Security Materialの場所と操作例

画面の場所：

**Integration Suite → Monitor → Integrations and APIs → Manage Security → Security Material**

ここには、名前を付けて登録した認証情報が一覧で表示されます。BTPコックピットのDestinationsとは別の画面です。

ユーザー名とパスワードで認証する場合の例：

1. Security Materialで **Create → User Credentials** を選びます。
2. 名前と、接続先で認証に使用するユーザー名・パスワードを登録し、利用可能な状態にします。
3. iFlowのアダプターで、接続先URLと対応する認証方式を設定します。
4. **Credential Name** に、Security Materialで登録した名前を指定します。
5. iFlowを反映してテストし、接続結果と送り先での処理結果を確認します。

実行時は、指定した登録名に対応する認証情報を使って接続します。OAuthの場合は、認証方式に応じた種類の認証情報を登録します。アクセストークンを常に手作業で入力する、という意味ではありません。

### 8-5. BTP Destinationsとの違い

| 比較 | BTP Destinations | Cloud IntegrationのSecurity Material |
|---|---|---|
| 場所 | BTPコックピットのConnectivity → Destinations | Integration SuiteのMonitor内 |
| 役割 | URLや認証方式などをまとめた接続設定を、名前付きで管理する | Cloud Integrationで利用する認証情報を管理する |
| 名前が指すもの | 接続設定の名前 | 認証情報の名前 |
| 今回説明したHTTP・OData接続での扱い | 登録しただけでは、その名前から接続設定が自動的に引き継がれるわけではない | アダプターのCredential Nameなどから参照する |

**今回説明した方式では、BTP Destinationsへの登録を前提にせず、iFlowのアダプター設定とSecurity Materialを組み合わせて接続します。**

ただし、DestinationがiFlowで一切使えない、という意味ではありません。例えばRFC受信アダプターには、BTPに定義したRFC Destinationの名前を指定する設定があります。HTTP用とRFC用のDestinationは区別します。

### 8-6. Integration Suiteの内側と外側で準備すること

Integration Suite側で管理するもの：

1. iFlowの処理手順。
2. アダプターの接続先URL・認証方式など。
3. Security Materialなどに登録する認証情報。

相手のシステム側で準備するもの：

1. SalesforceやS/4HANAの利用対象API。
2. APIを呼び出せるユーザーやアプリの権限、認証設定。
3. 必要なネットワーク接続。社内ネットワークへの接続では、構成に応じてCloud Connectorなども準備する。

したがって、「連携設定はIntegration Suite側でまとめて管理する」という理解はできますが、相手側のAPIや権限の準備も必要です。

## 参考：公式資料

- [SAP Integration Suiteの概要](https://learning.sap.com/courses/exploring-sap-platform-capabilities/illustrating-the-sap-integration-suite_b1c98a93-d3ca-4121-88ef-36bd397fae52)
- [パッケージとiFlowの作成・デプロイ](https://developers.sap.com/tutorials/cp-starter-integration-cpi-design-iflow)
- [Cloud Integrationの処理機能](https://help.sap.com/docs/cloud-integration/sap-cloud-integration/integration-capabilities?locale=en)
- [外部APIを呼び出すRequest Reply](https://help.sap.com/docs/integration-suite/sap-integration-suite/define-request-reply)
- [CAP Javaのサービス公開](https://cap.cloud.sap/docs/java/cqn-services/application-services)
- [Apache Groovy](https://groovy-lang.org/)
- [認証情報（User Credentials）の登録](https://help.sap.com/docs/integration-suite/isuite-integrations-and-apis/deploying-user-credentials-artifact)
- [HTTP受信アダプター](https://help.sap.com/docs/integration-suite/sap-integration-suite/http-receiver-adapter)
- [OData V4受信アダプター](https://help.sap.com/docs/cloud-integration/sap-cloud-integration/configure-odata-v4-receiver-adapter)
- [RFC受信アダプターとRFC Destination](https://help.sap.com/docs/integration-suite/sap-integration-suite/rfc-receiver-adapter)
- [BTP Destinationの作成](https://developers.sap.com/tutorials/cp-cf-create-destination)
