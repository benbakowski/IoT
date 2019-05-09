---

copyright:

years: 2017, 2019
lastupdated: "2019-04-16"

keywords: own organization, Extension HTTP APIs, API Use, AT&T Extension, Administer AT&T

subcollection: iot-platform

---

{:new_window: target="\_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:tip: .tip}
{:pre: .pre}
{:important: .important}


# API
{: #api_overview}

<p>この {{site.data.keyword.cloud}} 資料コレクションは、{{site.data.keyword.iot_full}} ライトの料金プランが対象になっていて、基本的な入門情報や、API リファレンス、一般的なトラブルシューティング情報が含まれています。
全ての {{site.data.keyword.iot_short_notm}} 機能の資料については、IBM Knowledge Center 上の [{{site.data.keyword.iot_short_notm}} 製品資料 ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/overview/overview.html) を参照してください。 各種プランの詳細については、[{{site.data.keyword.iot_short_notm}} のサービス・プラン](/docs/services/IoT?topic=iot-platform-plans_overview#plans_overview)を参照してください。 
</p>
{: important}

{{site.data.keyword.iot_full}} に接続するデバイス、ゲートウェイ、アプリケーション向けのコードの開発用に、いくつかの API を使用できます。

HTTP API は、HTTP 基本認証で保護されています。ダッシュボードを使用して API キーを生成すると、キーと認証トークンが提示されます。 API キーとトークンについて詳しくは、[API キー接続 ![外部リンク・アイコン](../../../icons/launch-glyph.svg)](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/platform/platform_authorization.html#api-key){: new_window} を参照してください。


## HTTP API について
{: #api_about}

それぞれの {{site.data.keyword.iot_short_notm}} 組織は、あらゆる HTTP API 呼び出しのためにホスト名に必要な 6 文字の組織 ID で識別されます。   

### API 資料
{: #api_docs}

API 資料を見るには、[IBM Watson IoT Platform REST APIs ![外部リンク・アイコン](../../../icons/launch-glyph.svg)](https://docs.internetofthings.ibmcloud.com/apis/swagger/index.html){: new_window} ページを参照してください。このランディング・ページから、使用可能な {{site.data.keyword.iot_short_notm}} API の資料にアクセスできます。

### 対話式の API 資料

対話式の API 資料を表示および使用する場合、組織のベース URL には、以下のアドレスでアクセスできます。

`https://<orgId>.internetofthings.ibmcloud.com/docs/index.html`

このランディング・ページから、使用可能な {{site.data.keyword.iot_short_notm}} API の資料にアクセスできます。API 呼び出しを資料から直接実行するためのアクセス権限を得るには、許可を受ける必要があります。

自動的に許可されるようにするには、以下のステップを実行します。

1. {{site.data.keyword.iot_short_notm}} ダッシュボードにログインします。
2. 同じブラウザーで、新しいタブを開き、対話式の API 資料のランディング・ページに移動します。

{{site.data.keyword.iot_short_notm}} ダッシュボードにログインしていない場合は、以下のステップを実行します。

1. 対話式の API 資料のランディング・ページに移動します。
2. `「許可」`を選択します。
3. `「使用可能な許可 (Available authorizations)」`ボックスで、ユーザー名を API キーに設定し、パスワードを認証トークンに設定します。`「許可」`を選択します。
4. `「使用可能な許可 (Available authorizations)」`ボックスを閉じます。**重要:** `「ログアウト」`を選択しないでください。

許可されたら、特定の API 呼び出しに移動し、`「試してみる (Try it out)」`ボタンを使用して、API 呼び出しを資料から直接実行します。

<!-- To authenticate requests to the application API, set the username to the API key and the password to the authentication token. -->
