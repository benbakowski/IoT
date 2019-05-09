---

copyright:
  years: 2016, 2019
lastupdated: "2019-04-05"

keywords: Lite plan, migrate, Watson IoT Platform

subcollection: iot-platform

---

{:new_window: target="\_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}
{:important: .important}

# 將 {{site.data.keyword.iot_short_notm}} Lite 移轉至 {{site.data.keyword.iot_short_notm}} 非正式作業或正式作業
{: #org_migration}

<p>此 {{site.data.keyword.cloud}} 文件集合與 {{site.data.keyword.iot_full}}「精簡」定價方案相關，包含了基本入門資訊、API 參考資料及一般疑難排解資訊。
如需完整的 {{site.data.keyword.iot_short_notm}} 特性文件，請參閱 {{site.data.keyword.IBM}} Knowledge Center 上的 [{{site.data.keyword.iot_short_notm}} 產品文件 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/overview/overview.html)。您可以在 [{{site.data.keyword.iot_short_notm}} 服務方案](/docs/services/IoT?topic=iot-platform-plans_overview#plans_overview)中找到各種方案的相關資訊。
</p>
{: important}

在您嘗試使用 Watson IoT Platform Lite 之後，了解此產品如何在您的 IoT 環境中運作，您可以升級至 [Watson IoT Platform 非正式作業或至其中一個正式作業方案 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/overview/overview.html){: new_window}。
{:shortdesc}

**附註：**本文件僅適用於具有「精簡」實例的使用者。如果您先前已使用「標準」或「進階」安全方案建立 IoT Platform 的實例，則 {{site.data.keyword.IBM}} 會與您一同將現有的 {{site.data.keyword.iot_short_notm}} 實例移轉至新的非正式作業或正式作業方案。

## 移轉處理程序概觀
{: #org_migration_overview}

透過移轉至 {{site.data.keyword.iot_short_notm}}，您可以移除 500 台裝置和每月資料耗用的「精簡」方案限制。

{{site.data.keyword.iot_short_notm}} 方案包括下列其他元件，以支援端對端 IoT 應用程式架構：

- Kafka 串流平台的 {{site.data.keyword.messagehub}} - {{site.data.keyword.IBM_notm}} 管理版本，您的應用程式可使用它來接收 IoT 資料。
- {{site.data.keyword.dashdbshort}}，用於分析資料儲存。
- {{site.data.keyword.cloudantfull}} DB，用於時間序列資料。
- {{site.data.keyword.cos_full}}，用於長期資料保留。

本文件說明您可能想要從現有「精簡」實例移轉至完整版本的資料類型。

**附註：**通常最容易的是從頭開始設定 {{site.data.keyword.iot_short_notm}} 非正式作業或正式作業環境，因為它包括 {{site.data.keyword.iot_short_notm}}「精簡」服務以外的元件及特性。此外，在「精簡」版本中建立來進行測試的裝置及使用者，可能不是您要用於正式作業的相同裝置及使用者。

不過，如果您想要轉移部分現有的「精簡」設定，下列各節將指導您完成整個程序。

關於 [{{site.data.keyword.iot_short_notm}} API](/docs/services/IoT?topic=iot-platform-api_overview#api_overview) 的文件，提供了如何呼叫 API 及其完整參數集的指示。


## 開始之前
{: #org_migration_byb}

您必須先購買{{site.data.keyword.iot_short_notm}}（正式作業或非正式作業環境），才能開始進行移轉處理程序。購買時，{{site.data.keyword.IBM_notm}} 作業團隊將為您佈建新的 {{site.data.keyword.iot_short_notm}} 實例。這會包括一個新的六個英數字元的組織 ID。


## 移轉使用者
{: #user_migration}

[使用者管理 API ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://docs.internetofthings.ibmcloud.com/apis/swagger/v0002/security.html#!/Authorization_-_User_Management){: new_window} 提供大量匯出及匯入 {{site.data.keyword.iot_short_notm}} 使用者，可用來匯出及匯入您想要保存在新組織中的使用者。

1. 從「精簡」組織匯出使用者。  
使用 `GET /authorization/users` 指令，將您的「精簡」帳戶組織中的所有使用者匯出為 JSON 物件。
2. 清除使用者清單。  
必要的話，編輯 JSON 結構以移除您不想移轉至新組織的任何使用者。
3. 將使用者匯入到新組織。  
使用 `POST /authorization/users/multiple` 指令，可將已編輯的 JSON 使用者清單匯入到新組織。

使用者現在可以存取新組織，該組織將顯示在 {{site.data.keyword.iot_short_notm}} 儀表板上的組織選取器中。

##  移轉裝置  
{: #device_migration}

您可以在下列步驟中完成移轉裝置：  
1. 將您想要保留的「裝置類型」移轉至新組織。  
2. 將裝置本身移轉至新組織。  
3. 更新裝置用來連接至 {{site.data.keyword.cloud_notm}} 的主機名稱，以開始使用您的新組織 ID。
4. 移轉您在 Lite 平台中所建立的任何「資料管理」資訊。   
這可能包括「裝置實體」及「邏輯介面」、「物品」及「規則」。

<p>可以使用下列 API 來大量移轉「裝置類型」及「裝置」：
<table>
<tr>
<th> API 文件</th>
<th> 匯出 API</th>
<th> 匯入 API</th>
</tr>
<tr>
<td> [裝置類型 API ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://docs.internetofthings.ibmcloud.com/apis/swagger/v0002/org-admin.html) </td>
<td> `GET /device/types` </td>
<td> `POST /device/types` </td>
</tr>
<tr>
<td>  [裝置 API ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://docs.internetofthings.ibmcloud.com/apis/swagger/v0002/org-admin.html#!/Device_Bulk_Configuration) </td>
<td> `GET /bulk/devices` </td>
<td>  `POST /bulk/devices/add`</td>
</tr>
</table>
</p>
{: tip}


**重要事項：**{{site.data.keyword.iot_short_notm}} 不會儲存裝置鑑別記號（只會儲存其隨機版本）。`GET /bulk/devices` 呼叫因此無法傳回已儲存裝置的鑑別記號。如果有裝置鑑別記號的記錄，您可以在執行大量載入之前，將這些記號新增至 JSON 物件。否則，您必須為每一個裝置產生新的裝置鑑別記號，並將它們複製到裝置。  

如果您使用裝置端憑證來鑑別裝置（而非使用鑑別記號），則不需要執行此動作。不過，如果您是使用裝置端憑證，則必須上傳用來將它們簽署至新組織的憑證。


## 更新裝置
{: #update_devices}

在新組織中登錄裝置時，您必須更新每一個現有裝置上呈現的配置或程式碼，以使用新組織的主機名稱。

若為 MQTT 及 HTTP 傳訊用戶端，請使用下列主機名稱：  
`<orgId>.messaging.internetofthings.ibmcloud.com`

在下列主機名稱處指出 REST API 用戶端：  
`<orgId>.internetofthings.ibmcloud.com`

**重要事項：**如果您為裝置產生新的鑑別記號，則必須將這些記號複製到每一個裝置。


## 裝置管理移轉
{: #device_management}

[資料管理 API![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://docs.internetofthings.ibmcloud.com/apis/swagger/v0002/state-mgmt.html){: new_window} 包括用於匯出及匯入裝置實體及邏輯介面、物品定義及規則的 API。

**重要事項：**{{site.data.keyword.iot_short_notm}} 目前不支援資料吸收的資產成對概念。

## 板及卡片
{: #boards_cards}

{{site.data.keyword.iot_short_notm}} 不包括用於匯入與匯出板及卡片定義與自訂作業的 API。您必須在新組織中手動重建這些項目。

## 啟用任何必要的延伸規格
{: #extensions}

您必須重建在 Lite 平台中已啟用的任何延伸規格，例如：在新組織中 {{site.data.keyword.messagehub}}、{{site.data.keyword.cloudant_short_notm}} 及 Jasper 的鏈結。

## 移轉應用程式
{: #application_migration}

如果您已開發應用程式來呼叫 {{site.data.keyword.iot_short_notm}}「精簡」服務（例如：傳送、接收資料，或管理服務）提供的 API，則必須更新這些應用程式，以使用新的 {{site.data.keyword.iot_short_notm}} 正式作業或非正式作業實例。這也適用於您可能使用的任何 Node-RED 流程。
移轉涉及：
- 更新應用程式，以使用新的六個字元組織 ID。
- 更新應用程式，以使用您為新服務實例建立的 API 金鑰及記號認證。

**重要事項：**如果您已使用 Cloud Foundry 連結以將組織 ID 及認證傳遞給應用程式，則必須使用其他機制，因為新的 {{site.data.keyword.iot_short_notm}} 實例未佈建為在您的 Cloud Foundry 空間中執行。

### 產生 API 連線認證

要遵循的移轉處理程序取決於您的應用程式性質。通常，對於所有情況，第一步是獲取應用程式要使用的 API 金鑰及身分鑑別記號。

1. 登入新的 {{site.data.keyword.iot_short_notm}} 服務的最上層儀表板。
2. 選取**用法**標籤。
3. 按一下**檢視詳細資料**鏈結，以啟動 {{site.data.keyword.iot_short_notm}} 服務資訊。  
會顯示下列資訊：
   - 六個字元的 orgID
   - API 金鑰和記號。  
   您應該為每一個應用程式產生新的 API 金鑰，而不是使用此處顯示的 API 金鑰。這可讓您設定每一個應用程式的適當許可權。
   - 主機 URL。
4. 建立應用程式的 API 金鑰及鑑別記號組合。  
配置應用程式以連接至組織時，您需要這些項目。   
   1.  按一下`啟動`。  
這會引導您前往用來管理 {{site.data.keyword.iot_short_notm}}「精簡」服務的基礎服務儀表板。
   2. 選取**應用程式**。
   3. 按一下**產生 API 金鑰**
   4. 複製列出的 API 金鑰及鑑別記號值。
   5. 請選取適合您應用程式的角色。   
   6. 新增註解，以輕鬆識別此 API 金鑰及鑑別記號組合。
   7. 按一下**產生**。
   8. **重要事項：**建立鑑別記號的本端副本。在您關閉視窗之後，無法重新建立它。


### 更新 Node-RED 應用程式
您需要配置 Node-RED 節點來連接新的 {{site.data.keyword.iot_short_notm}} 實例。您的 `ibmipot` 節點將無法再使用 `BluemixService` 鑑別選項，因此您需要改為選取 `API 金鑰`選項。
1. 開啟 `ibmiot` 節點來進行編輯。
2. 在節點內容之下，選取 **API 金鑰**。
3. 針對 API 金鑰欄位，按一下編輯圖示，然後輸入您從前一個步驟儲存的 API 金鑰和鑑別記號。
4. 儲存變更並重新部署 Node-RED 流程。

### 更新不使用 Cloud Foundry 連結的應用程式
識別應用程式儲存組織 ID、「API 金鑰」及「授權記號」的位置，並將它們取代為先前儲存的值。

如果您的應用程式使用其中一個 {{site.data.keyword.iot_short_notm}} SDK，這些值可能會保留在一個 properties 檔中。
{: tip}

### 更新使用 Cloud Foundry 連結的應用程式

{{site.data.keyword.cloud_notm}} 提供一種將 Cloud Foundry 應用程式連結至一個以上 Cloud Foundry 服務的機制。可以使用 {{site.data.keyword.cloud_notm}} CLI 建立連結，或者透過在 {{site.data.keyword.cloud_notm}} 儀表板的「應用程式」及「服務」之間建立`連線`來建立連結。

當應用程式連結至服務時，會將服務 API 金鑰及鑑別記號認證複製到 `VCAP_SERVICES` 環境變數，應用程式可從中擷取它們。

**重要事項：**此連結機制不能與新的 {{site.data.keyword.iot_short_notm}} 服務一起使用。您必須在應用程式中尋找讀取 `VCAP_SERVICES` 的程式碼，並將它取代為從現在儲存「API 金鑰」和「授權」記號的位置讀取值的程式碼。若要完成更新，您必須重建及重新部署應用程式。
