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
{:important: .important}

# {{site.data.keyword.iot_short_notm}} のトラブルシューティング
{: #ts}

<p>この {{site.data.keyword.Bluemix}} 資料コレクションは、{{site.data.keyword.iot_full}} ライトの料金プランが対象になっていて、基本的な入門情報や、API リファレンス、一般的なトラブルシューティング情報が含まれています。
全ての {{site.data.keyword.iot_short_notm}} 機能の資料については、IBM Knowledge Center 上の [{{site.data.keyword.iot_short_notm}} 製品資料 ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/overview/overview.html) を参照してください。 各種プランの詳細については、[{{site.data.keyword.iot_short_notm}} のサービス・プラン](/docs/IoT/plans_overview.html#plans_overview)を参照してください。 
</p>
{: important}

{{site.data.keyword.Bluemix_notm}} 上での {{site.data.keyword.iot_full}} の使用についての一般的なトラブルシューティングの質問に対する答えを提供します。
{:shortdesc}

## {{site.data.keyword.iot_short_notm}} 組織へのアクセスの問題
{: #access-expiry-problem}

自分の {{site.data.keyword.iot_short_notm}} 組織にログインできません。
{:shortdesc}

組織の URL または `https://internetofthings.ibmcloud.com` を使用して自分の {{site.data.keyword.iot_short_notm}} 組織に直接アクセスできません。
{: tsSymptoms}

自分の {{site.data.keyword.iot_short_notm}} 組織へのアクセスが期限切れになっている可能性があります。 {{site.data.keyword.Bluemix}} を使用して作成された {{site.data.keyword.iot_short_notm}} 組織では、デフォルトで一時ユーザー・プロファイルが使用されます。
{: tsCauses}

この問題は、{{site.data.keyword.iot_short_notm}} 組織にアクセスするか、{{site.data.keyword.Bluemix_notm}} を使用して、ユーザー・プロファイルの有効期限の設定を変更することで解決できます。 ユーザーの有効期限の設定を変更するには、以下のようにします。

1. {{site.data.keyword.Bluemix_notm}} ダッシュボードで、{{site.data.keyword.iot_short_notm}} サービスを開きます。
2. ナビゲーション・バーから**「メンバー」**をクリックします。
3. **「編集」**アイコンをクリックします。
4. **「アクセスの有効期限が切れました」**のチェック・ボックスをクリアして、**「保存」**をクリックします。
{: tsResolve}

## {{site.data.keyword.iot_short_notm}} への接続の問題
{: #connection_problem}

{{site.data.keyword.iot_short_notm}} への接続が予期せずドロップまたは切断されます。
{:shortdesc}

{{site.data.keyword.iot_short_notm}} に接続しようとすると、デバイスまたはアプリケーションがエラーを受け取ります。
{: tsSymptoms}

同じクライアント ID と資格情報を使って複数のデバイスが接続を試行している可能性があります。 clientID ごとに 1 つの固有の接続のみが許可されています。 同じ ID による複数の同時接続はできません。アプリケーションは同じ API キーを共有できますが、MQTT ではクライアント ID が常に固有であることが必要です。
{: tsCauses}

複数のデバイスが同じ資格情報で接続を試みてはいないことを確認すれば、この理由を排除できます。
{: tsResolve}

## デバイスが {{site.data.keyword.iot_short_notm}} から断続的に切断されます。
{: #disconnection_problem}

{{site.data.keyword.iot_short_notm}} へのデバイスの接続が予期せず断続的にドロップします。
{:shortdesc}

{{site.data.keyword.iot_short_notm}} サービスに接続しているデバイスが断続的に切断されます。 デバイスは再接続しますが、しばらくすると再び予期せずに切断されます。
{: tsSymptoms}

接続時に使用する MQTT の ping オプションの値が小さすぎるため、接続タイムアウトになったと認識されている可能性があります。 例えば、クライアント MQTT が正しく設定されていない場合、ping はタイミング良く受信されず、接続が閉じてしまいます。
{: tsCauses}

この問題は、接続の ping パラメーターと KeepAlive パラメーターを正しく設定することで修正できます。   
{: tsResolve}
