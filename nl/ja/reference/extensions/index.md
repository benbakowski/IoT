---

copyright:
  years: 2015, 2019
lastupdated: "2019-04-10"

keywords: IoT Platform organization, SIM devices, IBM Watson

subcollection: iot-platform

---

{:new_window: target="\_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:important: .important}

# 外部サービスの統合
{: #ref-index}

<p>この {{site.data.keyword.cloud}} 資料コレクションは、{{site.data.keyword.iot_full}} ライトの料金プランが対象になっていて、基本的な入門情報や、API リファレンス、一般的なトラブルシューティング情報が含まれています。
全ての {{site.data.keyword.iot_short_notm}} 機能の資料については、IBM Knowledge Center 上の [{{site.data.keyword.iot_short_notm}} 製品資料 ![外部リンク・アイコン](../../../../icons/launch-glyph.svg "外部リンク・アイコン")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/overview/overview.html) を参照してください。 各種プランの詳細については、[{{site.data.keyword.iot_short_notm}} のサービス・プラン](/docs/services/IoT?topic=iot-platform-plans_overview#plans_overview)を参照してください。 
</p>
{: important}

外部サービスの統合は、{{site.data.keyword.iot_full}} 組織内で、サード・パーティーまたは外部サービスからデータや操作にアクセスするためのものです。

## Jasper
{: #jasper}

Jasper は SIM デバイスの管理プラットフォームです。 Jasper は {{site.data.keyword.iot_short_notm}} ダッシュボードに統合されているため、{{site.data.keyword.iot_short_notm}} 組織のダッシュボードにより Jasper デバイスを管理することが可能です。

### Jasper でサポートされる操作

当社のプラットフォームで提供されている組み込み Jasper 統合では、以下の Jasper 操作がサポートされます。

- 全体的な Jasper データの表示
  - 表示されるのは、状況、料金プラン、過去 1 カ月間のデータ使用状況、過去 1 カ月間の SMS 使用状況、過去 1 カ月間のボイス使用状況、超過限度、追加日付、そして変更日付です。
- SIM アクティベーション状態の変更
  - インベントリー、アクティベーション準備完了、アクティブ、非アクティブ、廃止から選択します。
- SIM 使用状況の表示
  - 表示されるのは、サイクル開始日、請求対象と合計データ、請求対象と合計 SMS、請求対象と合計ボイスです。
  - サイクル開始日は YYYY-MM-DD の日付形式を使用して設定できます。
- SMS から SIM への送信
- 料金プランの変更

以下に示す構成手順を実行すると、それ以降、Jasper 接続デバイスのデバイス・ドリルダウンの中で、サポートされている操作にアクセスできるようになります。

### Jasper 用の REST API
Jasper 用の REST API にアクセスする場合は、[{{site.data.keyword.iot_short_notm}} HTTP REST API ![外部リンク・アイコン](../../../../icons/launch-glyph.svg "外部リンク・アイコン")](https://docs.internetofthings.ibmcloud.com/apis/swagger/v0002/ext-jasper.html){: new_window} の資料にある Jasper 拡張のセクションを参照してください。

### Jasper 用の構成

Jasper サービスを {{site.data.keyword.iot_short_notm}} 組織に接続するには、2 段階の構成を完了する必要があります。 まず、{{site.data.keyword.iot_short_notm}} が Jasper サービスに接続されていなければならず、次に {{site.data.keyword.iot_short_notm}} デバイスが構成されていなければなりません。


1. Jasper 拡張を有効にします。 Jasper と {{site.data.keyword.iot_short_notm}} 組織の統合を有効にするには、以下の手順を実行します。
  1. {{site.data.keyword.iot_short_notm}} ダッシュボードから、**「拡張」**を選択します。
  2. **「拡張」**ページで、**「拡張の追加 (Add Extension)」**をクリックします。
  3. Jasper の横にある**「追加」**をクリックします。
  4. Jasper ユーザー名、パスワード、アクセス・キー、ドメイン ID を入力します。
  5. **「完了」**をクリックします。

2. デバイスを構成します。
{{site.data.keyword.iot_short_notm}} 組織と Jasper アカウントの両方に接続されているデバイスを構成することにより、Jasper からのデータを {{site.data.keyword.iot_short_notm}} ダッシュボードに表示することができます。  
**重要:** Jasper 構成を「デバイスの追加」プロセスの一部として適用することはできません。 Jasper で構成できるのは、それ以前に接続されているデバイスだけです。  
Jasper 接続済みデバイスを構成するには、以下の手順を実行します。
 1. {{site.data.keyword.iot_short_notm}} ダッシュボードの「デバイス」ページで、構成する Jasper 接続デバイスを見つけます。
 2. デバイスを選択して、「デバイス・ドリルダウン (Device Drilldown)」ビューを開きます。
 3. 「拡張構成」までスクロールダウンします。
 4. 以下の JSON 形式を使用して拡張の構成を入力した後、**「変更の確認」**をクリックして構成を保存します。  

```json  
    {
        "jasper": {
            "iccid": "string"
        }
    }

```

組織が正常に構成されると、「デバイス・ドリルダウン (Device Drilldown)」ビューの「拡張構成」セクションに「拡張」セクションが表示されます。

## AT&T
{: #att}

### AT&T でサポートされる操作

AT&T 拡張により、以下の AT&T 操作が有効になります。

- 全体的な AT&T データの表示
  - 表示されるのは、状況、料金プラン、過去 1 カ月間のデータ使用状況、過去 1 カ月間の SMS 使用状況、過去 1 カ月間のボイス使用状況、超過限度、追加日付、そして変更日付です。
- SIM アクティベーション状態の変更
  - インベントリー、アクティベーション準備完了、アクティブ、非アクティブ、廃止から選択します。
- SIM 使用状況の表示
  - 表示されるのは、サイクル開始日、請求対象と合計データ、請求対象と合計 SMS、請求対象と合計ボイスです。
  - サイクル開始日は YYYY-MM-DD の日付形式を使用して設定できます。
- SMS から SIM への送信
- 料金プランの変更

### AT&T 用の REST API
AT&T 用の REST API にアクセスする場合は、[{{site.data.keyword.iot_short_notm}} HTTP REST API![外部リンク・アイコン](../../../../icons/launch-glyph.svg "外部リンク・アイコン")](https://docs.internetofthings.ibmcloud.com/apis/swagger/v0002/ext-atnt.html){: new_window} の資料にある AT&T 拡張のセクションを参照してください。

### AT&T 用の構成

{{site.data.keyword.iot_short_notm}} 組織を AT&T に接続するには、組織の構成とデバイスの構成を完了する必要があります。

{{site.data.keyword.iot_short_notm}} プラットフォームを構成するには、以下の手順を実行します。

1. AT&T 拡張を有効にします。 AT&T と {{site.data.keyword.iot_short_notm}} 組織の統合を有効にするには、以下の手順を実行します。
  1. {{site.data.keyword.iot_short_notm}} ダッシュボードから、**「拡張」**を選択します。
  2. **「拡張」**ページで、**「拡張の追加 (Add Extension)」**をクリックします。
  3. AT&T の横にある**「追加」**をクリックします。
  4. AT&T ユーザー名、パスワード、アクセス・キー、ドメイン ID を入力します。
  5. **「完了」**をクリックします。

{{site.data.keyword.iot_short_notm}} 組織と AT&T アカウントを接続するには、2 段階の構成を完了する必要があります。 組織の構成を実行した後、デバイスの構成を実行します。


2. デバイスを構成します
{{site.data.keyword.iot_short_notm}} 組織と AT&T アカウントの両方に接続されているデバイスを構成することにより、AT&T からのデータを {{site.data.keyword.iot_short_notm}} ダッシュボードに表示することができます。  
**重要:** AT&T 構成を「デバイスの追加」プロセスの一部として適用することはできません。 AT&T で構成できるのは、それ以前に接続されているデバイスだけです。  
AT&T 接続済みデバイスを構成するには、以下の手順を実行します。
 1. {{site.data.keyword.iot_short_notm}} ダッシュボードの「デバイス」ページで、構成する AT&T 接続デバイスを見つけます。
 2. デバイスを選択して、「デバイス・ドリルダウン (Device Drilldown)」ビューを開きます。
 3. 「拡張構成」までスクロールダウンします。
 4. 以下の JSON 形式を使用して拡張の構成を入力した後、**「変更の確認」**をクリックして構成を保存します。  

```json  
    {
        "atnt": {
            "iccid": "string"
        }
    }

```

組織が正常に構成されると、「デバイス・ドリルダウン (Device Drilldown)」ビューの「拡張構成」セクションに「拡張」セクションが表示されます。

## Arm Mbed ブリッジ
{: #arm}

ブリッジにより、Arm Mbed デバイスは {{site.data.keyword.iot_short_notm}} と統合し、メッセージを双方向で交換することができます。 この統合を有効にするには、まず Arm Mbed Cloud アカウントに登録してから、{{site.data.keyword.iot_short_notm}} 構成に必要な接続情報を提供する必要があります。

### 構成のセットアップ


1. Arm Mbed ブリッジ拡張を有効にします。 拡張を有効にするには、以下のステップを実行します。
  1. {{site.data.keyword.iot_short_notm}} ダッシュボードから、**「拡張」**を選択します。
  2. 「拡張」ページで、**「拡張の追加 (Add Extension)」**をクリックします。
  3. Arm Mbed ブリッジ拡張の横にある**「追加 (Add)」**をクリックします。
  4. Arm Mbed アクセス・キーを入力します。 これは Arm Mbed ポータル ([https://portal.mbedcloud.com ![外部リンク・アイコン](../../../../icons/launch-glyph.svg "外部リンク・アイコン")](https://portal.mbedcloud.com){: new_window}) を使用することで作成できます。
  5. **「接続の確認 (Check Connection)」**ボタンをクリックして、資格情報が正しいことを確認します。
  6. **「完了」**をクリックします。

### ペイロード・フォーマット

Arm Mbed プラットフォームでは、通知と非同期応答という 2 種類の着信メッセージを使用します。 {{site.data.keyword.iot_short_notm}} は、Arm Mbed プラットフォームに接続されているデバイスにコマンドを送信することができます。

#### 通知

通知は、デバイスまたはセンサー・データでの変更によって生成されます。 {{site.data.keyword.iot_short_notm}} がメッセージを処理した後、そのメッセージは {{site.data.keyword.iot_short_notm}} に直接接続されているデバイスと同じ方法でデバイス・イベント・トピックに送信されます。 Arm Mbed プラットフォームに接続されているデバイスで発生する通知で使用されるイベント・タイプは、`notify` です。

以下のコード・サンプルは、Arm Mbed プラットフォーム API によって送信される通知のペイロード形式を示しています。

```
{
  "ep":<endpoint/deviceID>,
  "path":<resource path>,
  "ct":<content type>,
  "payload":<Base64 encoded payload>,
  "max-age":<how long the payload is valid, in seconds>
}
```

#### 非同期応答

Arm Mbed プラットフォームに接続されているデバイスに {{site.data.keyword.iot_short_notm}} がコマンドを送信すると、デバイスは {{site.data.keyword.iot_short_notm}} に確認メッセージを送り戻します。 この確認メッセージは_非同期応答_と呼ばれ、イベント・タイプ `asyncResponse` を使用します。

以下のコード・サンプルは、Arm Mbed Cloud サービスによって送信される非同期応答のペイロード形式を示しています。

```
{
  "id":<transaction id>,
  "status":<200 is command was sucessfully executed. Check other HTTP response codes>,
  "ct":<content type>,
  "max-age":<how long the payload is valid, in seconds>,
  "payload":<base64 encoded payload>,
  "ep":<endpoint/deviceID affected by the command>,
  "path":<resource path affected by the command>
}
```

#### Arm Mbed プラットフォームへのコマンドの送信

{{site.data.keyword.iot_short_notm}} は、Arm Mbed プラットフォームに接続されているデバイスにコマンドを送信することができます。 Arm Mbed プラットフォームに送信されるコマンドは、以下の JSON 形式を使用する必要があります。

```
{
  "method":<PUT or POST>,
  "deviceId":<endpoint/deviceId>,
  "resourceId":<resource path>,
  "payload": <Base64 encoded payload>
}
```
選択する方式には大/小文字の区別があります。 リソース・パスの最初の `/` はスキップする必要があります。


ペイロードは、以下のトピックでパブリッシュする必要があります。

```
iot-2/type/<device_type>/id/<deviceId>/cmd/<command_type>/fmt/<command_format>
```

<!--
## Orange
{: #orange}

The Orange extension allows you to view SIM card data from devices that are connected to your {{site.data.keyword.iot_short_notm}} and have an Orange SIM card installed.

### Supported operations for Orange

If you have a device that is connected to your {{site.data.keyword.iot_short_notm}} service and has an Orange SIM card, you can use the Orange extension to view the following SIM card data:

- SIM serial number
- Activation status
- Last status change
- Last status refresh
- Location status

### REST APIs for Orange
To access the REST API for Orange, see the Orange Extension section in the [{{site.data.keyword.iot_short_notm}} HTTP REST API ![External link icon](../../../../icons/launch-glyph.svg "External link icon")](https://docs.internetofthings.ibmcloud.com/apis/swagger/v0002/ext-orange.html){: new_window} documentation.

### Configuration for Orange

To enable the Orange extension:

1. From the {{site.data.keyword.iot_short_notm}} dashboard, select **Extensions**.
2. On the **Extensions** page, click **Add Extension**.
3. Click **Add** next to the Orange extension.
4. Enter your Orange user name and password.
6. Click **Done**.

After the Orange extension has been enabled, each device that has an Orange SIM card must be configured to display Orange SIM data.

1. In the devices tab of your {{site.data.keyword.iot_short_notm}} dashboard, find the Orange SIM device to configure.
2. Select the device and scroll down to **Extension Configuration**.
3. Enter the extension configuration by using the following JSON format and then click **Confirm changes** to save your configuration.

```json
    {
        "orange": {
            "serialnumber": "<serial number of Orange SIM>"
        }
    }

```
When the organization is successfully configured, the Extensions section is displayed under the Extensions Configuration section in the Device Drilldown view.
-->

## 履歴データ・ストレージ
{: #historical_data}

履歴データ・ストレージ拡張を使用すれば、IoT データ用の互換メッセージ・ストレージ・サービス ([{{site.data.keyword.cloudantfull}} ![外部リンク・アイコン](../../../../icons/launch-glyph.svg "外部リンク・アイコン")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/platform/cloudant_connector.html){: new_window} や [{{site.data.keyword.messagehub_full}} ![外部リンク・アイコン](../../../../icons/launch-glyph.svg "外部リンク・アイコン")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/platform/message_hub.html){: new_window} など) を見つけて構成できます。

## カスタム・デバイス管理パッケージ
{: #device_mgmt}

デバイス管理は {{site.data.keyword.iot_short_notm}} の中核となるフィーチャーですが、追加機能開発のため、拡張することができます。 カスタム・デバイス管理パッケージには、有効な JSON が含まれている必要があり、少なくとも 1 つのカスタム・デバイス・アクションが定義されていなければなりません。

カスタム・デバイス管理機能について詳しくは、必要な JSON フォーマットの例を含め、[デバイス管理のカスタム拡張 ![外部リンク・アイコン](../../../../icons/launch-glyph.svg "外部リンク・アイコン")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/platform/devices/device_mgmt/custom_actions.html){: new_window} を参照してください。

### カスタム・デバイス管理パッケージの追加

カスタム・デバイス管理パッケージは、{{site.data.keyword.iot_short_notm}} ダッシュボードまたは API のいずれかを使用して追加できます。

{{site.data.keyword.iot_short_notm}} ダッシュボードを使用してカスタム・デバイス管理パッケージを追加するには、次のようにします。

1. {{site.data.keyword.iot_short_notm}} ダッシュボードで、ナビゲーション・バーから**「設定」**をクリックします。
2. **「カスタム・デバイス管理パッケージ」**をクリックします。
3. **「パッケージの追加」**ボタンをクリックします。
4. パッケージ・ファイルを選択し、**「開く」**をクリックします。

API を使用してカスタム・デバイス管理パッケージを追加する場合は、[{{site.data.keyword.iot_short_notm}} API 資料 ![外部リンク・アイコン](../../../../icons/launch-glyph.svg "外部リンク・アイコン")](https://docs.internetofthings.ibmcloud.com/apis/swagger/v0002/orgAdmin.html){: new_window} を参照してください。

## E メール
{: #email}

招待メールを使用して、ユーザーを {{site.data.keyword.iot_short_notm}} に追加することができます。 詳しくは、[ユーザーのアクセス権限の管理](/docs/services/IoT?topic=iot-platform-managing-user-access#managing-user-access)を参照してください。

招待メール機能を使用するには、SendGrid オンライン・サービスまたは Simple Mail Transfer Protocol (SMTP) サービスを使用するように E メール拡張機能を構成する必要があります。 この拡張機能では、SendGrid {{site.data.keyword.cloud_notm}} アプリケーションを使用することもできます。

### SendGrid オンライン・サービス

SendGrid オンライン・サービスを使用するように E メール拡張機能を構成するには、以下の手順に従います。

1. SendGrid オンライン・アカウントから、許可済み API キーを取得します。
2. {{site.data.keyword.iot_short_notm}} ダッシュボードのナビゲーション・バーから**「拡張」**をクリックします。
3. **「E メール」**セクションで、**「セットアップ」**をクリックします。
4. **「SendGrid で API キーを使用」**を選択します。
5. サイト管理者の名前および E メール・アドレスと、許可済み API キーを入力します。

### SMTP サービス

SMTP サービスを使用するように E メール拡張機能を構成するには、以下の手順に従います。

1. {{site.data.keyword.iot_short_notm}} ダッシュボードのナビゲーション・バーから**「拡張」**をクリックします。
2. **「E メール」**セクションで、**「セットアップ」**をクリックします。
3. **「SMTP」**を選択します。
4. SMTP サービスの構成の詳細を入力します。

### SendGrid {{site.data.keyword.cloud_notm}} アプリケーション

SendGrid {{site.data.keyword.cloud_notm}} アプリケーションを使用するように E メール拡張機能を構成するには、以下の手順に従います。

1. ダミー・アプリケーションを作成し、SendGrid サービスをバインドします。  
構成資格情報を取得するには、SendGrid サービスをダミー・アプリケーションに追加してバインドします。

 1. {{site.data.keyword.cloud_notm}} ダッシュボードから、**「サービスの作成」**をクリックします。
 2. カタログから SendGrid サービスを選択し、**「作成」**をクリックします。
 3. {{site.data.keyword.cloud_notm}} ダッシュボードから、{{site.data.keyword.runtime_nodejs_full}} アプリケーションを追加します。
 4. {{site.data.keyword.cloud_notm}} ダッシュボードから {{site.data.keyword.runtime_nodejs_notm}} アプリケーションをクリックし、**「サービスまたは API のバインド」**をクリックします。
 5. SendGrid サービスを選択し、**「追加」**をクリックします。
 6. {{site.data.keyword.runtime_nodejs_notm}} アプリケーションを再ステージングします。
2. {{site.data.keyword.iot_short_notm}} サービスを構成する準備をします。  
{{site.data.keyword.iot_short_notm}} は、{{site.data.keyword.iot_short_notm}} ダッシュボードまたは {{site.data.keyword.iot_short_notm}} API を使用して構成することができます。  
 1. {{site.data.keyword.cloud_notm}} ダッシュボードから、{{site.data.keyword.runtime_nodejs_notm}} アプリケーションをクリックします。
 2. ナビゲーション・バーから**「環境変数」**をクリックします。
 3. 表示された JSON を一時テキスト・ファイルにコピーします。  
 JSON は次の形式になるはずです。
```
{
  "name": "SendGridServiceName",
  "label": "user-provided",
  "credentials": {
    "password": "xxx",
    "hostname": "smtp.sendgrid.net",
    "username": "username"
  }
}
```
3. 構成データを {{site.data.keyword.iot_short_notm}} 組織に追加します。
 1. {{site.data.keyword.iot_short_notm}} ダッシュボードを開きます。
 2. ナビゲーション・バーから**「拡張」**をクリックします。
 3. **「E メール」**アイコンの下にある**「セットアップ」**をクリックします。
 4. **「SendGrid でユーザー名を使用」**を選択します。
 5. 一時テキスト・ファイル内の構成データを入力します。
 6. **「完了」**をクリックします。
