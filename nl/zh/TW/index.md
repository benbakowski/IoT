---

copyright:
  years: 2016, 2019
lastupdated: "2019-04-05"

keywords: Watson IoT Platform, gateway devices, Watson IoT Platform service plans

subcollection: iot-platform

---

{:new_window: target="\_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}
{:important: .important}


# 入門指導教學
{: #getting-started-with-iotp .task}

<p>此 {{site.data.keyword.cloud}} 文件集合與 {{site.data.keyword.iot_full}}「精簡」定價方案相關，包含了基本入門資訊、API 參考資料及一般疑難排解資訊。
如需完整的 {{site.data.keyword.iot_short_notm}} 特性文件，請參閱 IBM Knowledge Center 上的 [{{site.data.keyword.iot_short_notm}} 產品文件 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/overview/overview.html)。您可以在 [{{site.data.keyword.iot_short_notm}} 服務方案](/docs/services/IoT?topic=iot-platform-plans_overview#plans_overview)中找到各種方案的相關資訊。
</p>
{: important}

在此 {{site.data.keyword.iot_full}} 入門指導教學中，我們將 IoT 裝置連接至 {{site.data.keyword.iot_short_notm}}。
{:shortdesc}

## 關於此作業
{: #index-about .sectiontitle}  

您必須先將 IoT 裝置連接至 {{site.data.keyword.iot_full}}，才能開始接收來自 IoT 裝置的資料。若要將裝置連接至 {{site.data.keyword.iot_short_notm}}，需要向 {{site.data.keyword.iot_short_notm}} 登錄裝置，然後使用登錄資訊配置裝置，以便連接至 {{site.data.keyword.iot_short_notm}}。


## 開始之前
{: #index-byb .sectiontitle}  

開始使用 {{site.data.keyword.iot_short_notm}} 之前，需要下列項目：  
* [IBM Cloud 帳戶 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://cloud.ibm.com/registration/){: new_window}。
* {{site.data.keyword.iot_short_notm}} 實例。  
您可以直接從 [IBM Cloud Services 型錄的 {{site.data.keyword.iot_short_notm}} 頁面 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://{DomainName}/catalog/services/internet-of-things-platform/){:new_window} 建立 {{site.data.keyword.iot_short_notm}} 實例。  
* 符合下列需求的裝置：  
  *	您的裝置必須能夠使用 HTTP 或 MQTT 通訊協定進行通訊。
  * 裝置訊息必須符合 {{site.data.keyword.iot_short_notm}} 訊息有效負載需求。  
如需相關資訊，請參閱[在 Watson IoT Platform 上開發裝置 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/platform/devices/device_dev_index.html){: new_window}。

根據您的狀況來探索下列選項：

 |  |已部署的服務|未部署的服務
 | -------------| ------------- | -------------
  |**我有要連接的裝置**|請遵循本主題中概述的程序。|在 [Play with {{site.data.keyword.iot_short_notm}} ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](http://discover-iot.eu-gb.mybluemix.net/?cm_mc_uid=44491599487314618721024&cm_mc_sid_50200000=1462798151#/play){:new_window} 中探索裝置連線。
  |**我沒有裝置可連接**|[模擬裝置資料](/docs/services/IoT?topic=iot-platform-sim_device_data#sim_device_data)或 [Connect your Smartphone ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](http://discover-iot.eu-gb.mybluemix.net/?cm_mc_uid=44491599487314618721024&cm_mc_sid_50200000=1462798151#/play/device/smartphone){:new_window}。|開始使用 [Watson IoT Platform 入門範本](https://cloud.ibm.com/docs/IoT-starter?topic=iot-starter-gettingstartedtemplate#gettingstartedtemplate){:new_window}。




## 步驟 1：登錄裝置
{: #index-step1 .sectiontitle}  
若要登錄裝置，需要將裝置分類成裝置類型、為裝置命名，並提供裝置資訊。然後，您可以提供連線記號，或是接受 {{site.data.keyword.iot_short_notm}} 產生的記號。

**提示：**您可以從 [{{site.data.keyword.iot_short_notm}} 儀表板 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://internetofthings.ibmcloud.com){: new_window} 一次登錄一台裝置，或是使用 [ Watson IoT Platform API ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://docs.internetofthings.ibmcloud.com/apis/swagger/v0002/org-admin.html#!/Device_Bulk_Configuration/post_bulk_devices_add){: new_window}，以新增多台裝置。

若要從 {{site.data.keyword.iot_short_notm}} 儀表板新增裝置，請執行下列動作：
1. 在 {{site.data.keyword.cloud_notm}} 主控台中，按一下 {{site.data.keyword.iot_short_notm}} 服務詳細資料頁面上的**啟動**。

    {{site.data.keyword.iot_short_notm}} Web 主控台會在新瀏覽器分頁中開啟，其 URL 為：

    ```
 https://org_id.internetofthings.ibmcloud.com/dashboard/#/overview
 ```

    其中 *org_id* 是 {{site.data.keyword.iot_short_notm}} 組織的 ID。

2. 在「概觀」儀表板中，從功能表窗格中選取**裝置**，然後按一下**新增裝置**。

3. 建立您要新增之裝置的裝置類型。

    連接至 {{site.data.keyword.iot_short_notm}} 的每一個裝置都必須與裝置類型相關聯。裝置類型是一群共用相同性質的裝置。

    1. 按一下**建立裝置類型**。
    2. 輸入裝置名稱（例如 `my_device_type`）及裝置類型的說明。

        > **附註：**裝置類型名稱不得超過 36 個字元，且只能包含英數字元（a-z、A-Z、0-9）及下列任何字元：`_`、`.` 和 `-`。



    3. 選用項目：輸入裝置類型屬性和 meta 資料。  
 

        您可以稍後再新增及編輯屬性和 meta 資料。
        {: tip}

4. 按**下一步**，開始新增所選取裝置類型的裝置。

5. 輸入裝置 ID（例如 `my_first_device`）。

    裝置 ID 可用來識別 {{site.data.keyword.iot_short_notm}} 儀表板中的裝置，它也是將裝置連接至 {{site.data.keyword.iot_short_notm}} 的必要參數。

    > **附註：**裝置類型名稱不得超過 36 個字元，且只能包含英數字元（a-z、A-Z、0-9）及下列任何字元：`_`、`.` 和 `-`。



    若為連接網路的裝置，裝置 ID 可以是不含任何分隔冒號的裝置 MAC 位址。

5. 按**下一步**，以完成處理程序。

6. 提供鑑別記號，或接受自動產生的記號。如果您選擇建立自己的記號，請確定其長度為 8 到 36 個字元，並且只包含英數字元及下列字元：`_`、`.`、`!`、`&`、`@`、`?`、`\*`、`+`、`(`、`)` 及 `-`。

    記號不得包含重複的字元順序、字典單字、使用者名稱或其他預先定義的順序。

7. 驗證摘要資訊正確無誤，然後按一下**新增**，以新增連線。

8. 在裝置資訊頁面中，複製並儲存下列詳細資料：

    * 組織 ID
  
    * 裝置類型
    * 裝置 ID
    * 鑑別方法
  
    * 鑑別記號
  

    您需要有「組織 ID」、「裝置類型」、「裝置 ID」及「鑑別記號」，才能配置您的裝置來連接至 {{site.data.keyword.iot_short_notm}}。

## 步驟 2：將您的裝置連接至 {{site.data.keyword.iot_short_notm}}
{: #index-step2 .sectiontitle}  

向 {{site.data.keyword.iot_short_notm}} 登錄裝置之後，您可以使用登錄資訊來連接裝置，並開始接收裝置資料。

**提示：**在 IBM.com 中的 [裝置連線秘訣 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://developer.ibm.com/recipes/tutorials/category/internet-of-things-iot/){: new_window} 提供某些常用裝置的連線秘訣。

若要將裝置連接至 {{site.data.keyword.iot_short_notm}}，請執行下列動作：
1. 設定裝置來進行 MQTT 傳訊，並使用「組織 ID」、「裝置類型」、「裝置 ID」及「鑑別記號」進行鑑別。

2. 使用 MQTT 通訊協定將裝置訊息傳送至 {{site.data.keyword.iot_short_notm}} 組織。

    連接裝置時，需要下列資訊：

    * URL：*org_id*.messaging.internetofthings.ibmcloud.com

      其中 *org_id* 是 {{site.data.keyword.iot_short_notm}} 組織的 ID。

    * 埠：
      * 1883
      * 8883（已加密）
      * 443 (websockets)
    * 裝置 ID：d:_org_id:device_type:device_id_
    * 使用者名稱：use-token-auth
    * 密碼：_鑑別記號_
    * 事件主題格式：iot-2/evt/_event_id/fmt/format_string_

      其中 _event_id_ 指定顯示在 {{site.data.keyword.iot_short_notm}} 中的事件名稱，而 _format_string_ 是事件的格式，例如 JSON。

    * 訊息格式：JSON

  如需相關資訊，請參閱 [MQTT connectivity for devices ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/platform/devices/mqtt.html){:new_window}。


## 下一步為何？  
{: #index-related .sectiontitle}

建立並連接您自己的應用程式來使用裝置資料，以延伸資料分析特性。
- 如需如何將特定裝置類型連接至 {{site.data.keyword.iot_short_notm}} 的相關資訊，請參閱 [developerWorks 秘訣 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://developer.ibm.com/recipes/tutorials/category/internet-of-things-iot/){:new_window}。
- 參閱工具的[用戶端程式庫 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/platform/iot_platform_client_lib.html){:new_window} 來建置程式碼，以便整合及連接您的裝置和應用程式。
- 探索 [{{site.data.keyword.iot_short_notm}} API 文件](/docs/services/IoT?topic=iot-platform-api_overview#api_overview)。
- [將 {{site.data.keyword.cloudantfull}} 服務連接 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/platform/cloudant_connector.html){:new_window} 至您的 {{site.data.keyword.iot_short_notm}}，以儲存歷程裝置資料。
- 如果要利用完整的 [{{site.data.keyword.iot_short_notm}} 特性集 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/overview/overview.html){:new_window}，您可以購買其中一個連線及分析服務方案，然後移轉現有的環境。

如果要移轉方案，請與您的 {{site.data.keyword.IBM}} 代表聯絡，或提出支援問題單。

在 IBM Knowledge Center 的 {{site.data.keyword.iot_short_notm}} 產品說明文件中，也提供了一組更詳細的「入門手冊」和範例應用程式，介紹使用 {{site.data.keyword.iot_short_notm}} 逐步開發現成可用的端對端 IoT 原型系統的基本觀念。如果您是使用 {{site.data.keyword.iot_short_notm}} 的新手開發人員，請使用[入門手冊 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/platform/getting_started/getting-started-iot-overview.html#getting-started){:new_window} 小節中的逐步程序。
