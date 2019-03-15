---

copyright:
  years: 2018, 2019
lastupdated: "2019-02-13"

---

{:new_window: target="\_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:important: .important}


# {{site.data.keyword.iamshort}} 鑑別及 {{site.data.keyword.iot_short_notm}} 的授權（測試版）
{: #cloud_iam}

<p>此 {{site.data.keyword.Bluemix}} 文件集合與 {{site.data.keyword.iot_full}}「精簡」定價方案相關，包括基本入門資訊、API 參考資料及一般疑難排解資訊。
如需完整的 {{site.data.keyword.iot_short_notm}} 特性文件，請參閱 {{site.data.keyword.IBM_notm}} Knowledge Center 上的 [{{site.data.keyword.iot_short_notm}} 產品文件 ![外部鏈結圖示](../../../../icons/launch-glyph.svg "外部鏈結圖示")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/overview/overview.html)。您可以在 [{{site.data.keyword.iot_short_notm}} 服務方案](/docs/IoT/plans_overview.html#plans_overview)中找到各種方案的相關資訊。
</p>
{: important}

{{site.data.keyword.iot_full}} API 支援使用 {{site.data.keyword.iamshort}} (IAM) 來鑑別及授權使用者。

{{site.data.keyword.iamlong}} 鑑別及 {{site.data.keyword.iot_short_notm}} 的授權僅提供為有限測試版程式的一部分。未來更新可能包含與此特性的目前版本不相容的變更。請試用，並且[讓我們知道您的想法 ![外部鏈結圖示](../../../../icons/launch-glyph.svg)](https://developer.ibm.com/answers/smart-spaces/17/internet-of-things.html){: new_window}。
{: important}

{{site.data.keyword.iamshort}} 內建於 {{site.data.keyword.Bluemix_notm}}，並用於鑑別及授權需要配置與管理其 {{site.data.keyword.IBM_notm}} 服務的管理和開發人員使用者。需要存取 {{site.data.keyword.iot_short_notm}} 儀表板的使用者使用 {{site.data.keyword.iamshort}} 進行鑑別。{{site.data.keyword.iamshort}} 的身分來源可以是登錄的 IBM ID 使用者，也可以是支援 SAML 的客戶目錄服務。  

{{site.data.keyword.iot_short_notm}} 也支援透過 {{site.data.keyword.appid_short_notm}} 來鑑別使用者。{{site.data.keyword.appid_short_notm}} 用於鑑別需要存取 {{site.data.keyword.Bluemix_notm}} 中所管理應用程式的使用者。{{site.data.keyword.appid_short_notm}} 使用者一般不會對雲端服務執行管理或開發活動。如需相關資訊，請參閱
[Watson IoT Platform 的 {{site.data.keyword.appid_short_notm}} 鑑別 ![外部鏈結圖示](../../../../icons/launch-glyph.svg "外部鏈結圖示")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/platform/app_id.html#app_id){: new_window}。

IAM 可讓使用者取得 IAM OAuth 記號，並使用它來鑑別 API 呼叫。例如，已安裝 {{site.data.keyword.containershort_notm}} CLI 的使用者可能會使用下列指令：

`bx iam oauth-tokens`

這個指令會以下列格式傳回已登入之使用者的 IAM 記號：

`IAM Token: Bearer <some token>`

使用者也可以使用 IAM 記號端點來登入並擷取其 IAM 記號，如下列範例所示：`curl -s 'https://iam.bluemix.net/oidc/token?grant_type=urn:ibm:params:oauth:grant-type:apikey&response_type=cloud_iam&apikey=<apikey>' -H'Content-Type:x-www-form-urlencoded' -XPOST`

此 API 範例使用 IAM API 金鑰來要求 IAM 記號，並傳回 `Bearer<token>`。

然後，當使用者呼叫 {{site.data.keyword.iot_short_notm}} API 時，可以在其 API 呼叫上提供授權標頭 `Authorization: Bearer<token>`。

## 產生 IAM 記號
{: #iam_generate}

您可以選擇如何自動建立 IAM 記號，視您如何向 {{site.data.keyword.Bluemix_notm}} 進行鑑別以及您使用的 {{site.data.keyword.Bluemix_notm}} ID 類型而定。

如果您使用未聯合 ID，則可以選擇下列其中一個選項來建立 IAM 記號：
 - **{{site.data.keyword.Bluemix_notm}} 使用者名稱和密碼：**您可以建立記號，以完全自動建立 IAM 存取記號。
 - **產生 {{site.data.keyword.Bluemix_notm}} API 金鑰：**使用 {{site.data.keyword.Bluemix_notm}} API 金鑰，API 金鑰會與產生它們時所針對的 {{site.data.keyword.Bluemix_notm}} 帳戶相依。您無法將 {{site.data.keyword.Bluemix_notm}} API 金鑰與不同帳戶 ID 結合在相同的 IAM 記號中。如果要存取的叢集是以不同於 {{site.data.keyword.Bluemix_notm}} API 金鑰所根據帳戶的帳戶建立，您必須登入此帳戶才能產生新的 API 金鑰。

如果您使用聯合 ID，則可以選擇下列其中一個選項來建立 IAM 記號：
 - **產生 {{site.data.keyword.Bluemix_notm}} API 金鑰：** {{site.data.keyword.Bluemix_notm}} API 金鑰與產生它們時的 {{site.data.keyword.Bluemix_notm}} 帳戶相依。您無法將 {{site.data.keyword.Bluemix_notm}} API 金鑰與不同帳戶 ID 結合在相同的 IAM 記號中。如果要存取的叢集是以不同於 {{site.data.keyword.Bluemix_notm}} API 金鑰所根據帳戶的帳戶建立，您必須登入此帳戶才能產生新的 API 金鑰。
 - **使用一次性密碼：**如果您使用一次性密碼來向 {{site.data.keyword.Bluemix_notm}} 進行鑑別，則無法完全自動建立您的 IAM 記號，因為擷取一次性密碼需要與 Web 瀏覽器進行手動互動。若要完全自動建立 IAM 記號，您必須改為建立一個 {{site.data.keyword.Bluemix_notm}} API 金鑰。

當您建立存取記號時，根據使用的 {{site.data.keyword.Bluemix_notm}} 鑑別方法，要求中所包括的內文資訊會不同。請取代下列值：
- `<my_username>` = 您的 {{site.data.keyword.Bluemix_notm}} 使用者名稱。
- `<my_password>` = 您的 {{site.data.keyword.Bluemix_notm}} 密碼。
- `<my_api_key>` = 您的 {{site.data.keyword.Bluemix_notm}} API 金鑰。
- `<my_passcode>` = 您的 {{site.data.keyword.Bluemix_notm}} 一次性密碼。執行 `bx login --sso`，並遵循 CLI 輸出中的指示，利用 Web 瀏覽器來擷取一次性密碼。

範例：`POST https://iam.<region>.bluemix.net/oidc/token`

若要指定 {{site.data.keyword.Bluemix_notm}} 地區，請檢閱在 API 端點中使用地區時的地區縮寫。如需相關資訊，請參閱 [{{site.data.keyword.Bluemix_notm}} 地區 API 端點 ![外部鏈結圖示](../../../../icons/launch-glyph.svg)](https://console.bluemix.net/docs/containers/cs_regions.html#bluemix_regions){: new_window}。

輸入參數	 | 值
---------------- | -----------
標頭	| Content-Type:application/x-www-form-urlencoded<br>授權：基本 Xng7Png=<br>附註：系統會提供您 `Xng7Png=`，也就是使用者名稱 bx 及密碼 bx 的 URL 編碼授權。
{{site.data.keyword.Bluemix_notm}} 使用者名稱及密碼的內文 |	grant_type: password<br>response_type: cloud_iam, uaa<br>username: `<my_username>`<br>password: `<my_password>`<br>uaa_client_id: cf<br>uaa_client_secret:<br>附註：請新增uaa_client_secret 金鑰且不指定任何值。
{{site.data.keyword.Bluemix_notm}} API 金鑰的內文 |	grant_type: urn:ibm:params:oauth:grant-type:apikey<br>response_type: cloud_iam<br>uaa<br>apikey: `<my_api_key>`<br>uaa_client_id: cf<br>uaa_client_secret:<br>附註：請新增uaa_client_secret 金鑰且不指定任何值。
{{site.data.keyword.Bluemix_notm}} 一次性密碼的內文	|	grant_type: urn:ibm:params:oauth:grant-type:passcode<br>response_type: cloud_iam, uaa<br>passcode: `<my_passcode>`<br>uaa_client_id: cf<br>uaa_client_secret:<br>附註：請新增uaa_client_secret 金鑰且不指定任何值。

API 輸出範例：

```
{
"access_token": "<iam_token>",
"refresh_token": "<iam_refresh_token>",
"uaa_token": "<uaa_token>",
"uaa_refresh_token": "<uaa_refresh_token>",
"token_type": "Bearer",
"expires_in": 3600,
"expiration": 1493747503
}
```
您可以在 API 輸出的 **access_token** 欄位中找到 IAM 記號。

下列範例顯示如何在呼叫 API 時使用 IAM 記號。

```
GET https://org.domain/api/v0002/bulk/devices
```

輸入參數	 |	值
----------------- | -----------
標頭	|	Content-Type: application/json<br>Authorization: bearer `<iam_token>`
