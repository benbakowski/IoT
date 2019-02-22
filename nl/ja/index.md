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


# 概説のチュートリアル
{: #getting-started-with-iotp .task}

<p>この {{site.data.keyword.Bluemix}} 資料コレクションは、{{site.data.keyword.iot_full}} ライトの料金プランが対象になっていて、基本的な入門情報や、API リファレンス、一般的なトラブルシューティング情報が含まれています。
全ての {{site.data.keyword.iot_short_notm}} 機能の資料については、IBM Knowledge Center 上の [{{site.data.keyword.iot_short_notm}} 製品資料 ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/overview/overview.html) を参照してください。 各種プランの詳細については、[{{site.data.keyword.iot_short_notm}} のサービス・プラン](/docs/IoT/plans_overview.html#plans_overview)を参照してください。 
</p>
{: important}

この {{site.data.keyword.iot_full}} の概説のチュートリアルでは、IoT デバイスを {{site.data.keyword.iot_short_notm}} に接続します。
{:shortdesc}

## このタスクについて
{: #index-about .sectiontitle}  

IoT デバイスからデータを受信する操作を開始するには、その前にデバイスを {{site.data.keyword.iot_full}} に接続する必要があります。 デバイスを {{site.data.keyword.iot_short_notm}} に接続するには、まずデバイスを {{site.data.keyword.iot_short_notm}} に登録してから、登録情報を使用してデバイスを {{site.data.keyword.iot_short_notm}} に接続するための構成を行います。

## 始めに
{: #index-byb .sectiontitle}  

{{site.data.keyword.iot_short_notm}} の使用を開始する前に、以下のものを揃えておいてください。  
* [IBM Cloud アカウント ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://console.bluemix.net/registration/){: new_window}。
* {{site.data.keyword.iot_short_notm}} インスタンス。  
{{site.data.keyword.iot_short_notm}} インスタンスは、[IBM Cloud サービス・カタログの {{site.data.keyword.iot_short_notm}} ページ ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://{DomainName}/catalog/services/internet-of-things-platform/){:new_window} から直接作成できます。  
* 以下の要件を満たしたデバイス。  
  *	デバイスは、HTTP プロトコルまたは MQTT プロトコルを使用して通信できるようでなければなりません。
  * デバイス・メッセージは、{{site.data.keyword.iot_short_notm}} のメッセージ・ペイロードの要件に準拠していなければなりません。  
詳しくは、[Watson IoT Platform でのデバイスの開発 ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/platform/devices/device_dev_index.html){: new_window} を参照してください。

状況に応じて、以下のオプションを検討します。

 |  |   サービスがデプロイされている | サービスがデプロイされていない
 | -------------| ------------- | -------------
  |**接続するデバイスがある** | このトピックで説明されているプロセスを実行します。| [Play with {{site.data.keyword.iot_short_notm}} ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](http://discover-iot.eu-gb.mybluemix.net/?cm_mc_uid=44491599487314618721024&cm_mc_sid_50200000=1462798151#/play){:new_window} で、デバイスの接続を試すことができます。
  |**接続するデバイスがない** | [デバイス・データをシミュレートする](/docs/IoT/devices/device_sim.html)か、[スマートフォンを接続します ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](http://discover-iot.eu-gb.mybluemix.net/?cm_mc_uid=44491599487314618721024&cm_mc_sid_50200000=1462798151#/play/device/smartphone){:new_window}。| [Watson IoT Platform の概説](https://console.bluemix.net/docs/IoT-starter/iot500.html#gettingstartedtemplate){:new_window}から始めます。



## 手順 1: デバイスの登録
{: #index-step1 .sectiontitle}  
デバイスを登録するには、デバイスをデバイス・タイプごとに分類し、デバイスに名前を付けて、デバイス情報を指定します。 その後、接続トークンを指定するか、{{site.data.keyword.iot_short_notm}} によって生成されるトークンを受け入れます。

**ヒント:** [{{site.data.keyword.iot_short_notm}} ダッシュボード ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://internetofthings.ibmcloud.com){: new_window} から 1 つずつデバイスを登録することも、[Watson IoT Platform API ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://docs.internetofthings.ibmcloud.com/apis/swagger/v0002/org-admin.html#!/Device_Bulk_Configuration/post_bulk_devices_add){: new_window} を使用して複数のデバイスを追加することも可能です。

{{site.data.keyword.iot_short_notm}} ダッシュボードからデバイスを追加するには、以下のようにします。
1. {{site.data.keyword.Bluemix_notm}} コンソールで、{{site.data.keyword.iot_short_notm}} サービスの詳細ページの**「起動」**をクリックします。

    新しいブラウザー・タブで以下の URL の {{site.data.keyword.iot_short_notm}} Web コンソールが開きます。

    ```
    https://org_id.internetofthings.ibmcloud.com/dashboard/#/overview
    ```

    *org_id* は、{{site.data.keyword.iot_short_notm}} 組織の ID です。

2. 「概要」ダッシュボードのメニュー・ペインから**「デバイス」**を選択し、**「デバイスの追加」**をクリックします。

3. 追加するデバイスのデバイス・タイプを作成します。

    {{site.data.keyword.iot_short_notm}} に接続する各デバイスには、デバイス・タイプを関連付ける必要があります。 デバイス・タイプとは、共通の特性を共有するデバイス・グループのことです。

    1. **「デバイス・タイプの作成」**をクリックします。
    2. `my_device_type` などのデバイス名と、デバイス・タイプの説明を入力します。

        > **注意:** デバイス・タイプ名は 36 文字以内にする必要があり、英数字の文字 (a-z, A-Z, 0-9) と、`_`、`.`、および `-`のいずれかのみを含めることができます。

    3. オプション: デバイス・タイプの属性やメタデータを入力します。

        属性とメタデータは、後で追加および編集できます。
        {: tip}

4. **「次へ」**をクリックして、選択したデバイス・タイプのデバイスを追加するプロセスを開始します。

5. `my_first_device` などのデバイス ID を入力します。

    デバイス ID は、{{site.data.keyword.iot_short_notm}} ダッシュボードでデバイスを識別するために使用され、デバイスを {{site.data.keyword.iot_short_notm}} に接続するための必須パラメーターでもあります。

    > **注意:** デバイス・タイプ名は 36 文字以内にする必要があり、英数字の文字 (a-z, A-Z, 0-9) と、`_`、`.`、および `-`のいずれかのみを含めることができます。

    ネットワークに接続されたデバイスの場合は、デバイス MAC アドレス (区切り文字のコロンは付けない) をデバイス ID として入力できます。

5. **「次へ」**をクリックすると、プロセスが完了します。

6. 認証トークンを指定するか、自動生成されたトークンを受け入れます。 自分でトークンを作成する場合は、長さを 8 文字から 36 文字の間にして、英数字と、`_`、`.`、`!`、`&`、`@`、`?`、`\*`、`+`、`(`、`)`、`-` だけを使用してください。

    反復した文字シーケンスや、辞書に出てくる単語やユーザー名などの事前定義シーケンスをトークンに含めないでください。

7. 要約情報が正しいことを確認してから、**「追加」**をクリックして接続を追加します。

8. デバイス情報のページで、以下の詳細をコピーして保存します。

    * 組織 ID
    * デバイス・タイプ
    * デバイス ID
    * 認証方式
    * 認証トークン

    {{site.data.keyword.iot_short_notm}} へのデバイスの接続を構成するときに、組織 ID、デバイス・タイプ、デバイス ID、および認証トークンが必要になります。

## 手順 2: {{site.data.keyword.iot_short_notm}} とデバイスの接続
{: #index-step2 .sectiontitle}  

デバイスを {{site.data.keyword.iot_short_notm}} に登録したら、登録情報を使用してデバイスを接続し、デバイス・データの受信を開始できます。

**ヒント:** 一般的なデバイスに対応した接続レシピが IBM.com の [デバイス接続のレシピ ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://developer.ibm.com/recipes/tutorials/category/internet-of-things-iot/){: new_window} に用意されています。

デバイスを {{site.data.keyword.iot_short_notm}} に接続するには、以下のようにします。
1. MQTT メッセージングを使用するようにデバイスをセットアップし、組織 ID、デバイス・タイプ、デバイス ID、および認証トークンを使用して認証します。

2. MQTT プロトコルを使用して、デバイス・メッセージを {{site.data.keyword.iot_short_notm}} 組織に送信します。

    デバイスを接続するときには、以下の情報が必要になります。

    * URL: *org_id*.messaging.internetofthings.ibmcloud.com

      *org_id* は、{{site.data.keyword.iot_short_notm}} 組織の ID です。

    * ポート:
      * 1883
      * 8883 (暗号化)
      * 443 (Web ソケット)
    * デバイス ID: d:_org_id:device_type:device_id_
    * ユーザー名: use-token-auth
    * パスワード: _Authentication token_
    * イベント・トピック形式: iot-2/evt/_event_id/fmt/format_string_

      _event_id_ では、{{site.data.keyword.iot_short_notm}} に表示されるイベント名を指定します。_format_string_ は、イベントの形式 (JSON など) です。

    * メッセージ形式: JSON

  詳しくは、[デバイスの MQTT 接続 ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/platform/devices/mqtt.html){:new_window} を参照してください。


## 次の作業  
{: #index-related .sectiontitle}

デバイス・データをコンシュームする独自のアプリを作成して接続することで、データ分析機能を拡張します。
- 特定のデバイス・タイプを {{site.data.keyword.iot_short_notm}} に接続する方法について詳しくは、[developerWorks recipes ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://developer.ibm.com/recipes/tutorials/category/internet-of-things-iot/){:new_window} を参照してください。
- デバイスとアプリを統合し、接続するためのコードをビルドする場合は、ツールの[クライアント・ライブラリー ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/platform/iot_platform_client_lib.html){:new_window} を参照してください。
- [{{site.data.keyword.iot_short_notm}} API 資料](/docs/IoT/reference/api.html)を調べてください。
- {{site.data.keyword.iot_short_notm}} に [{{site.data.keyword.cloudantfull}} サービスを接続して ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/platform/cloudant_connector.html){:new_window}、デバイスの履歴データを格納してください。
- 接続/分析のいずれかのサービス・プランを購入して既存の環境をマイグレーションすれば、[{{site.data.keyword.iot_short_notm}}のフルセットの機能 ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/overview/overview.html){:new_window} を利用できます。

プランをマイグレーションする場合は、{{site.data.keyword.IBM}} 担当者に連絡するか、サポート・チケットを開いてください。

さらに詳しい一連の概説ガイドとサンプル・アプリケーションもあります。{{site.data.keyword.iot_short_notm}} を使用して、実稼働環境ですぐに利用できるエンドツーエンド IoT プロトタイプ・システムを開発する基本的な手順を段階的に取り上げた資料です。IBM Knowledge Center にある {{site.data.keyword.iot_short_notm}} 製品資料を参照してください。{{site.data.keyword.iot_short_notm}} の操作を始めたばかりの開発者であれば、[概説ガイド ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/platform/getting_started/getting-started-iot-overview.html#getting-started){:new_window} のセクションにあるステップバイステップ・プロセスを使用してください。
