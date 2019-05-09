---

copyright:

years: 2017, 2019
lastupdated: "2019-04-05"

keywords: Data backup Use, data backup strategy, records of device management requests

subcollection: iot-platform

---

{:new_window: target="\_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:important: .important}



# データ・バックアップ
{: #back_up}

<p>この {{site.data.keyword.cloud}} 資料コレクションは、{{site.data.keyword.iot_full}} ライトの料金プランが対象になっていて、基本的な入門情報や、API リファレンス、一般的なトラブルシューティング情報が含まれています。
全ての {{site.data.keyword.iot_short_notm}} 機能の資料については、IBM Knowledge Center 上の [{{site.data.keyword.iot_short_notm}} 製品資料 ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/overview/overview.html) を参照してください。 各種プランの詳細については、[{{site.data.keyword.iot_short_notm}} のサービス・プラン](/docs/services/IoT?topic=iot-platform-plans_overview#plans_overview)を参照してください。 
</p>
{: important}

以下の情報を読んで、{{site.data.keyword.iot_full}} のデータ・バックアップ・ストラテジーを確認してください。

## バックアップされるのはどのようなタイプのデータですか?

{{site.data.keyword.iot_short_notm}} の現在のストラテジーでは、以下のタイプのクライアント・データがバックアップされます。

- 組織情報
- デバイス情報
- API キーとトークン
- ユーザー情報
- デバイス管理要求のすべてのレコード (開始された要求の履歴や要求の現在の状態など)
- カスタム・デバイス管理要求バンドルの定義

**注:** 組織のすべてのデータは、サービスをプロビジョン解除した後 14 日間保存されます。 組織をリストアするには、14 日以内にサポートに連絡してください。

## バックアップされないのはどのようなタイプのデータですか?

{{site.data.keyword.iot_short_notm}} では、以下のタイプのデータはバックアップされません。

- デバイス・イベント
- メッセージの一時的な状態 (伝送途中のデータなど)
- デバイス管理要求で送受信された MQTT メッセージ
<!-- - Analytics rules and alert configuration -->

## データ・バックアップの頻度と保管場所は?

データ・バックアップの頻度は 24 時間ごとです。

メインの {{site.data.keyword.iot_short_notm}} サービスのデータがオフサイトで保管されています。予備のデータを保管することによって、重大インシデントの発生時にサービスのリストアが可能になります。 データのリストアが必要になった場合は、クライアントに連絡が入ります。 全データが暗号化されており、該当する国や地域のデータ保護要件に準拠しています。

データ・バックアップのために現在使用されているオフサイト・ロケーションは以下のとおりです。

ロケーション                   | バックアップ・ロケーション                      
------------- | -------------
IBM Cloud 米国南部 (ダラス)| ワシントン
IBM Cloud 英国 (ロンドン) | フランクフルト
IBM Cloud ドイツ (フランクフルト) | ロンドン
IBM Cloud Dedicated | {{site.data.keyword.iot_short_notm}} Dedicated 注文時のお客様の要請による

**注:** 今後、データ・プライバシーに関する法律に合わせてロケーションが変更されることもあります。例えば、EU から英国が離脱した場合にデータ主権のルールがどんな影響を受けるか、といったこともからんでくるかもしれません。
