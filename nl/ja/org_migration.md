---

copyright:
  years: 2016, 2019
lastupdated: "2019-02-13"

---

{:new_window: target="\_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}
{:important: .important}

# {{site.data.keyword.iot_short_notm}} ライトから {{site.data.keyword.iot_short_notm}} 非実稼働または実稼働へのマイグレーション
{: #org_migration}

<p>この {{site.data.keyword.Bluemix}} 資料コレクションは、{{site.data.keyword.iot_full}} ライトの料金プランが対象になっていて、基本的な入門情報や、API リファレンス、一般的なトラブルシューティング情報が含まれています。
すべての {{site.data.keyword.iot_short_notm}} 機能の資料については、{{site.data.keyword.IBM}} Knowledge Center 上の [{{site.data.keyword.iot_short_notm}} 製品資料 ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/overview/overview.html) を参照してください。 各種プランの詳細については、[{{site.data.keyword.iot_short_notm}} のサービス・プラン](/docs/IoT/plans_overview.html#plans_overview)を参照してください。 
</p>
{: important}

Watson IoT Platform ライトのチェックが済み、この製品が IoT 環境にどうフィットするかをしっかり把握できたら、[Watson IoT Platform 非実稼働プランかいずれかの実稼働プラン ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/overview/overview.html){: new_window} にアップグレードできます。
{:shortdesc}

**注:** この資料の対象読者はライト・インスタンスのユーザーに限られます。標準プランか拡張セキュリティー・プランのどちらかで IoT Platform のインスタンスを作成していた場合は、既存の {{site.data.keyword.iot_short_notm}} インスタンスを新しい非実稼働プランか実稼働プランにマイグレーションする作業を {{site.data.keyword.IBM}} がお客様と一緒に行います。

## マイグレーション・プロセスの概要
{: #org_migration_overview}

{{site.data.keyword.iot_short_notm}} にマイグレーションすると、ライト・プランの制限 (500 デバイスと月単位のデータ使用量) がなくなります。

{{site.data.keyword.iot_short_notm}} のプランには、エンドツーエンドの IoT アプリケーション・アーキテクチャーをサポートするための以下の追加のコンポーネントが含まれています。

- {{site.data.keyword.messagehub}} - アプリケーションで IoT データを受け取るために使用できる {{site.data.keyword.IBM_notm}} ホスト版の Kafka ストリーミング・プラットフォーム。
- 分析データ・ストレージ用の{{site.data.keyword.dashdbshort}}。
- 時系列データ用の {{site.data.keyword.cloudantfull}} DB。
- データの長期保存用の {{site.data.keyword.cos_full}}。

この資料では、既存のライト・インスタンスからフルバージョンにマイグレーションするとよいデータのタイプについて説明します。

**注:** 通常は、{{site.data.keyword.iot_short_notm}} の非実稼働環境や実稼働環境を初めからセットアップする方が簡単です。{{site.data.keyword.iot_short_notm}} ライト・サービスの範囲を超えたコンポーネントや機能が含まれているからです。また、ライト・バージョンでのテストのために作成したデバイスやユーザーを実稼働環境でもそのまま使用するわけではないかもしれません。

既存のライト設定の一部を転送する場合は、以下の各セクションでそのためのプロセスを確認してください。

[{{site.data.keyword.iot_short_notm}} API](/docs/IoT/reference/api.html#api_overview) の資料には、その API を呼び出す方法やフルセットのパラメーターの説明が記されています。


## 始めに
{: #org_migration_byb}

マイグレーション・プロセスを開始する前に、{{site.data.keyword.iot_short_notm}} (非実稼働か実稼働) を購入する必要があります。購入すると、{{site.data.keyword.IBM_notm}} のオペレーション・チームが新しい {{site.data.keyword.iot_short_notm}} インスタンスのプロビジョンを実施します。6 文字の英数字を使用した新しい組織 ID も提供されます。


## ユーザーのマイグレーション
{: #user_migration}

[ユーザー管理 API ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://docs.internetofthings.ibmcloud.com/apis/swagger/v0002/security.html#!/Authorization_-_User_Management){: new_window} には、{{site.data.keyword.iot_short_notm}} ユーザーのエクスポートとインポートを一括して実行するための機能が用意されています。その機能を使用して、新しい組織に保存するユーザーをエクスポートしてインポートできます。

1. ライトの組織からユーザーをエクスポートします。  
`GET /authorization/users` コマンドを使用して、ライト・アカウント組織からすべてのユーザーを JSON オブジェクトとしてエクスポートします。
2. ユーザー・リストをクリーンアップします。  
必要に応じてその JSON 構造を編集し、新しい組織にマイグレーションしなくてもよいユーザーを削除します。
3. 新しい組織にユーザーをインポートします。  
`POST /authorization/users/multiple` コマンドを使用して、編集済みの JSON ユーザー・リストを新しい組織にインポートします。

ユーザーが新しい組織にアクセスできるようになり、{{site.data.keyword.iot_short_notm}} ダッシュボードの組織セレクターに表示されます。

##  デバイスのマイグレーション  
{: #device_migration}

デバイスのマイグレーションは、3 つのステップで実行できます。  
1. 保存するデバイス・タイプを新しい組織にマイグレーションします。  
2. デバイス自体を新しい組織にマイグレーションします。  
3. デバイスから {{site.data.keyword.Bluemix_short}} に接続して新しい組織 ID での操作を開始するために使用するホスト名を更新します。
4. ライト・プラットフォームで作成したデータ管理情報をマイグレーションします。   
デバイスの物理/論理インターフェース、モノ、ルールなどの情報です。

<p>デバイス・タイプとデバイスは、以下の API によって一括してマイグレーションできます。
<table>
<tr>
<th> API 資料 </th>
<th> エクスポート API </th>
<th> インポート API </th>
</tr>
<tr>
<td> [デバイス・タイプ API ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://docs.internetofthings.ibmcloud.com/apis/swagger/v0002/org-admin.html) </td>
<td> `GET /device/types` </td>
<td> `POST /device/types` </td>
</tr>
<tr>
<td>  [デバイス API ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://docs.internetofthings.ibmcloud.com/apis/swagger/v0002/org-admin.html#!/Device_Bulk_Configuration) </td>
<td> `GET /bulk/devices` </td>
<td>  `POST /bulk/devices/add`</td>
</tr>
</table>
</p>
{: tip}


**重要:** {{site.data.keyword.iot_short_notm}} では、デバイスの認証トークンを保管しません。あるのは、ソルト付きのバージョンだけです。`GET /bulk/devices` を呼び出しても、保管してあるデバイスの認証トークンを返すことはできません。デバイスの認証トークンのレコードがあれば、一括ロードを実行する前に、そうした認証トークンを JSON オブジェクトに追加できます。そうでなければ、各デバイスの新しい認証トークンを生成してデバイスにコピーする必要があります。  

デバイスの認証のために認証トークンではなくデバイス側の証明書を使用するのであれば、その操作を実行する必要はありません。ただし、デバイス側の証明書を使用する場合は、新しい組織へのサインインに使用した証明書をアップロードすることが必要です。


## デバイスの更新
{: #update_devices}

デバイスを新しい組織に登録する時には、既存の各デバイスに存在する構成やコードを更新して、新しい組織のホスト名を使用するようにしなければなりません。

MQTT と HTTP のメッセージング・クライアントの場合は、以下のホスト名を使用します。  
`<orgId>.messaging.internetofthings.ibmcloud.com`

REST API クライアントの場合は、以下のホスト名をポイントします。  
`<orgId>.internetofthings.ibmcloud.com`

**重要:** デバイス用の新しい認証トークンを生成した場合は、その認証トークンを各デバイスにコピーする必要があります。


## デバイス管理のマイグレーション
{: #device_management}

The [データ管理 API ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://docs.internetofthings.ibmcloud.com/apis/swagger/v0002/state-mgmt.html){: new_window} には、デバイスの物理/論理インターフェース、モノの定義、ルールをエクスポートしてインポートするための API が含まれています。

**重要:** {{site.data.keyword.iot_short_notm}} は現在、データ取り込みのためのアセット・ツインのコンセプトをサポートしていません。

## ボードとカード
{: #boards_cards}

{{site.data.keyword.iot_short_notm}} には、ボードやカードの定義やカスタマイズをインポートしてエクスポートするための API が組み込まれていません。そうした定義やカスタマイズは、新しい組織で手動で再作成する必要があります。

## 必要な拡張機能の有効化
{: #extensions}

ライト・プラットフォームで有効にした拡張機能 ({{site.data.keyword.messagehub}}へのリンク、{{site.data.keyword.cloudant_short_notm}}、Jasper など) を新しい組織で再作成する必要があります。

## アプリケーションのマイグレーション
{: #application_migration}

データの送信/受信やサービスの管理などのために {{site.data.keyword.iot_short_notm}} ライト・サービスに用意されている API を呼び出すアプリケーションを開発していた場合は、そうしたアプリケーションを更新して、{{site.data.keyword.iot_short_notm}} の実稼働または非実稼働の新しいインスタンスを使用するようにしなければなりません。Node-RED フローを使用する場合は、そのフローについても同じようにする必要があります。
このマイグレーションには、以下の処理が含まれます。
- アプリケーションを更新して、新しい 6 文字の組織 ID を使用するようにします。
- アプリケーションを更新して、新しいサービス・インスタンスのために作成する API キーとトークンの資格情報を使用するようにします。

**重要:** Cloud Foundry バインディングを使用して組織 ID と資格情報をアプリケーションに渡していた場合は、別のメカニズムを使用しなければなりません。新しい {{site.data.keyword.iot_short_notm}} インスタンスは、Cloud Foundry スペースで稼働するようにプロビジョンされるわけではないからです。

### API 接続資格情報の生成

このマイグレーション・プロセスは、アプリケーションの性質によって異なります。通常はどのケースでも、最初のステップとして、アプリケーションで使用する API キーと認証トークンを取得します。

1. 新しい {{site.data.keyword.iot_short_notm}} サービスの最上位ダッシュボードにログインします。
2. **「使用法」**タブを選択します。
3. **「詳細を表示」**リンクをクリックして、{{site.data.keyword.iot_short_notm}} サービスの情報を表示します。  
以下の情報が表示されます。
   - 6 文字の orgID
   - API キーとトークン  
ここに表示される API キーを使用する代わりに、アプリケーションごとに新しい API キーを生成してください。そうすれば、アプリケーションごとに適切なアクセス権を設定できます。
   - ホスト URL
4. アプリケーションの API キーと認証トークンの組み合わせを作成します。  
組織に接続するための構成をアプリケーションで行う時に、その情報が必要になります。   
   1.  `「起動」`をクリックします。  
{{site.data.keyword.iot_short_notm}} ライト・サービスの管理に使用していた基本的なサービス・ダッシュボードが表示されます。
   2. **「アプリ」**を選択します。
   3. **「API キーの生成」**をクリックします。
   4. 表示される API キーと認証トークンの値をコピーします。
   5. アプリケーションに適した役割を選択します。   
   6. この API キーと認証トークンの組み合わせに関するわかりやすいコメントを追加します。
   7. **「生成」**をクリックします。
   8. **重要:** 認証トークンのローカル・コピーを作成してください。このウィンドウを閉じたら、再作成ができなくなります。


### Node-RED アプリケーションの更新
新しい {{site.data.keyword.iot_short_notm}} インスタンスに接続できるように Node-RED ノードを構成する必要があります。`ibmiot` ノードは、`BluemixService` の認証オプションを使用できなくなるので、代わりに`「API キー」`オプションを選択する必要があります。
1. 編集のために `ibmiot` ノードを開きます。
2. ノード・プロパティーの下で**「API キー」**を選択します。
3. 「API キー」フィールドで編集アイコンをクリックし、前のステップで保存した API キーと認証トークンを入力します。
4. 変更内容を保存して、Node-RED フローを再デプロイします。

### Cloud Foundry バインディングを使用しないアプリケーションの更新
アプリケーションで組織 ID と API キーと許可トークンを保管している場所を見つけ出し、前に保存した値にその情報を置き換えます。

アプリケーションでいずれかの {{site.data.keyword.iot_short_notm}} SDK を使用している場合は、おそらくプロパティー・ファイルにその値が保管されています。
{: tip}

### Cloud Foundry バインディングを使用するアプリケーションの更新

{{site.data.keyword.Bluemix_short}} には、Cloud Foundry アプリケーションを 1 つ以上の Cloud Foundry サービスにバインドするためのメカニズムが用意されています。バインディングを確立するには、{{site.data.keyword.Bluemix_short}} CLI を使用するか、{{site.data.keyword.Bluemix_short}} ダッシュボードでアプリケーションとサービスの間の`接続`を作成します。

アプリケーションをサービスにバインドすると、そのサービスの API キーと認証トークンの資格情報が、アプリケーションでその情報を取得できる場所から `VCAP_SERVICES` 環境変数にコピーされます。

**重要:** 新しい {{site.data.keyword.iot_short_notm}} サービスでは、このバインディング・メカニズムを使用できません。`VCAP_SERVICES` を読み取るコードをアプリケーション内で見つけて、API キーと許可トークンの保管場所からその値を読み取るコードに置き換える必要があります。更新を完了するには、アプリケーションの再ビルドと再デプロイが必要です。
