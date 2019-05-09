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

<p>此 {{site.data.keyword.cloud}} 文件集合與 {{site.data.keyword.iot_full}}「精簡」定價方案相關，包含了基本入門資訊、API 參考資料及一般疑難排解資訊。
如需完整的 {{site.data.keyword.iot_short_notm}} 特性文件，請參閱 IBM Knowledge Center 上的 [{{site.data.keyword.iot_short_notm}} 產品文件 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/overview/overview.html)。您可以在 [{{site.data.keyword.iot_short_notm}} 服務方案](/docs/services/IoT?topic=iot-platform-plans_overview#plans_overview)中找到各種方案的相關資訊。
</p>
{: important}

數個 API 適用於開發連接至 {{site.data.keyword.iot_full}} 的裝置、閘道及應用程式的程式碼。

HTTP API 是藉由 HTTP 基本鑑別來保護。當您使用儀表板來產生 API 金鑰時，會出現金鑰及鑑別記號。如需 API 金鑰及記號的相關資訊，請參閱 [API 金鑰連線 ![外部鏈結圖示](../../../icons/launch-glyph.svg)](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/platform/platform_authorization.html#api-key){: new_window}。


## 關於 HTTP API
{: #api_about}

每一個 {{site.data.keyword.iot_short_notm}} 組織都是藉由 6 字元組織 ID 加以識別，主機名稱中需有此 ID，才能進行任何 HTTP API 呼叫。   

### API 文件
{: #api_docs}

若要檢視 API 文件，請移至 [IBM Watson IoT Platform REST APIs ![外部鏈結圖示](../../../icons/launch-glyph.svg)](https://docs.internetofthings.ibmcloud.com/apis/swagger/index.html){: new_window} 頁面。從這個登陸頁面中，您可以存取可用 {{site.data.keyword.iot_short_notm}} API 的文件。

### 互動式 API 文件

若要檢視及使用互動式 API 文件，可在下列位址存取您組織的基本 URL：

`https://<orgId>.internetofthings.ibmcloud.com/docs/index.html`

從這個登陸頁面中，您可以存取可用 {{site.data.keyword.iot_short_notm}} API 的文件。若要具有存取權，直接從文件執行 API 呼叫，您必須獲得授權。

若要自動獲得授權，請完成下列步驟：

1. 登入 {{site.data.keyword.iot_short_notm}} 儀表板。
2. 在同一個瀏覽器中，開啟新標籤並移至互動式 API 文件登陸頁面。

如果您未登入 {{site.data.keyword.iot_short_notm}} 儀表板，請完成下列步驟：

1. 移至互動式 API 文件登陸頁面。
2. 選取`授權`。
3. 在`可用授權`方框中，將使用者名稱設為 API 金鑰，並將密碼設為鑑別記號。選取`授權`。
4. 關閉`可用授權`方框。**重要事項：**請不要選取`登出`。

在獲得授權之後，請移至特定的 API 呼叫，並使用`試用`按鈕，直接從文件執行 API 呼叫。

<!-- To authenticate requests to the application API, set the username to the API key and the password to the authentication token. -->
