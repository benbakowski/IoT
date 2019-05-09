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

# 外部服務整合
{: #ref-index}

<p>此 {{site.data.keyword.cloud}} 文件集合與 {{site.data.keyword.iot_full}}「精簡」定價方案相關，包含了基本入門資訊、API 參考資料及一般疑難排解資訊。
如需完整的 {{site.data.keyword.iot_short_notm}} 特性文件，請參閱 IBM Knowledge Center 上的 [{{site.data.keyword.iot_short_notm}} 產品文件 ![外部鏈結圖示](../../../../icons/launch-glyph.svg "外部鏈結圖示")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/overview/overview.html)。您可以在 [{{site.data.keyword.iot_short_notm}} 服務方案](/docs/services/IoT?topic=iot-platform-plans_overview#plans_overview)中找到各種方案的相關資訊。
</p>
{: important}

外部服務整合可讓您從協力廠商或 {{site.data.keyword.iot_full}} 組織中的外部服務存取資料與作業。

## Jasper
{: #jasper}

Jasper 是 SIM 裝置的系統管理和管理平台。Jasper 整合在 {{site.data.keyword.iot_short_notm}} 儀表板中，讓您能夠透過 {{site.data.keyword.iot_short_notm}} 組織儀表板來管理 Jasper 裝置。

### 支援的 Jasper 作業

我們平台所提供的內建 Jasper 整合為下列 Jasper 作業提供支援：

- 檢視整體 Jasper 資料
  - 顯示狀態、費率方案、月初至今的資料使用情形、月初至今的 SMS 使用情形、月初至今的語音使用情形、超額限制、新增日期和修改日期。
- 變更 SIM 啟動狀態
  - 從下列項目中選取：庫存、啟動就緒、已啟動、已關閉、已淘汰。
- 檢視 SIM 使用情形
  - 顯示週期開始日期、可計費資料和資料總計、可計費 SMS 和 SMS 總計、可計費語音和語音總計。
  - 週期開始日期可使用 YYYY-MM-DD 資料格式來設定。
- 傳送 SMS 至 SIM
- 變更費率方案

完成下列配置步驟之後，您可以在 Jasper 連接裝置的裝置往下探查中，存取支援的作業：

### Jasper 的 REST API
若要存取 Jasper 的 REST API，請參閱 [{{site.data.keyword.iot_short_notm}} HTTP REST API ![外部鏈結圖示](../../../../icons/launch-glyph.svg "外部鏈結圖示")](https://docs.internetofthings.ibmcloud.com/apis/swagger/v0002/ext-jasper.html){: new_window} 文件中的「Jasper 延伸規格」小節。

### Jasper 的配置

若要將 Jasper 服務連接至 {{site.data.keyword.iot_short_notm}} 組織，您必須完成兩個配置階段。首先，{{site.data.keyword.iot_short_notm}} 必須連接至 Jasper 裝置，然後必須配置 {{site.data.keyword.iot_short_notm}} 裝置。


1. 啟用 Jasper 延伸規格。若要讓 Jasper 與 {{site.data.keyword.iot_short_notm}} 組織整合，請完成下列步驟：
  1. 從 {{site.data.keyword.iot_short_notm}} 儀表板選取**延伸規格**。
  2. 在**延伸規格**頁面上，按一下**新增延伸規格**。
  3. 按一下 Jasper 旁的**新增**。
  4. 輸入您的 Jasper 使用者名稱、密碼、存取金鑰及網域 ID。
  5. 按一下**完成**。

2. 配置裝置。您可以配置同時連接 {{site.data.keyword.iot_short_notm}} 組織和 Jasper 帳戶的裝置，以在 {{site.data.keyword.iot_short_notm}} 儀表板中顯示 Jasper 的資料。  
**重要事項：**在「新增裝置」程序中無法套用 Jasper 配置。只有先前已連接的裝置可以用 Jasper 來配置。  
若要配置 Jasper 連接的裝置，請完成下列步驟：
 1. 在 {{site.data.keyword.iot_short_notm}} 儀表板的「裝置」頁面中，尋找要配置的 Jasper 連接裝置。
 2. 選取裝置，以開啟「裝置往下探查」視圖。
 3. 向下捲動至延伸配置。
 4. 使用下列 JSON 格式來輸入延伸配置，然後按一下**確認變更**以儲存配置。  

```json  
    {
        "jasper": {
            "iccid": "string"
        }
    }

```

順利配置組織之後，「延伸規格」區段會顯示在「裝置往下探查」視圖的「延伸規格配置」區段下。

## AT&T
{: #att}

### 支援的 AT&T 作業

AT&T 延伸規格可讓您執行下列 AT&T 作業：

- 檢視整體 AT&T 資料
  - 顯示狀態、費率方案、月初至今的資料使用情形、月初至今的 SMS 使用情形、月初至今的語音使用情形、超額限制、新增日期和修改日期。
- 變更 SIM 啟動狀態
  - 從下列項目中選取：庫存、啟動就緒、已啟動、已關閉、已淘汰。
- 檢視 SIM 使用情形
  - 顯示：週期開始日期、可計費資料和資料總計、可計費 SMS 和 SMS 總計、可計費語音和語音總計。
  - 週期開始日期可使用 YYYY-MM-DD 資料格式來設定。
- 傳送 SMS 至 SIM
- 變更費率方案

### AT&T 的 REST API
若要存取 AT&T 的 REST API，請參閱 [{{site.data.keyword.iot_short_notm}} HTTP REST API ![外部鏈結圖示](../../../../icons/launch-glyph.svg "外部鏈結圖示")](https://docs.internetofthings.ibmcloud.com/apis/swagger/v0002/ext-atnt.html){: new_window} 文件中的「AT&T 延伸規格」小節。

### AT&T 的配置

若要將 {{site.data.keyword.iot_short_notm}} 組織連接至 AT&T，您必須完成組織配置及裝置配置。

若要配置 {{site.data.keyword.iot_short_notm}} 平台，請完成下列步驟：

1. 啟用 AT&T 延伸規格。若要讓 AT&T 與 {{site.data.keyword.iot_short_notm}} 組織整合，請完成下列步驟：
  1. 從 {{site.data.keyword.iot_short_notm}} 儀表板選取**延伸規格**。
  2. 在**延伸規格**頁面上，按一下**新增延伸規格**。
  3. 按一下 AT&T 旁的**新增**。
  4. 輸入 AT&T 使用者名稱、密碼、存取金鑰及網域 ID。
  5. 按一下**完成**。

若要將您的 {{site.data.keyword.iot_short_notm}} 組織與 AT&T 帳戶連接，您必須完成兩個配置階段。先完成組織配置，然後再配置您的裝置。


2. 配置您的裝置
您可以配置同時連接 {{site.data.keyword.iot_short_notm}} 組織和 AT&T 帳戶的裝置，以在 {{site.data.keyword.iot_short_notm}} 儀表板中顯示 AT&T 的資料。  
**重要事項：在「新增裝置」程序中無法套用 **AT&T 配置。只有先前已連接的裝置可以用 AT&T 來配置。  
若要配置 AT&T 連接的裝置，請完成下列步驟：
 1. 在 {{site.data.keyword.iot_short_notm}} 儀表板的「裝置」頁面中，尋找要配置的 AT&T 連接裝置。
 2. 選取裝置，以開啟「裝置往下探查」視圖。
 3. 向下捲動至延伸配置。
 4. 使用下列 JSON 格式來輸入延伸配置，然後按一下**確認變更**以儲存配置。  

```json  
    {
        "atnt": {
            "iccid": "string"
        }
    }

```

順利配置組織之後，「延伸規格」區段會顯示在「裝置往下探查」視圖的「延伸規格配置」區段下。

## Arm Mbed 橋接器
{: #arm}

橋接器可讓 Arm Mbed 裝置與 {{site.data.keyword.iot_short_notm}} 整合，並雙向交換訊息。若要啟用此整合，您首先需要註冊 Arm Mbed Cloud 帳戶，然後為 {{site.data.keyword.iot_short_notm}} 配置提供所要求的連線資訊。

### 設定配置


1. 啟用 Arm Mbed 橋接器延伸規格。若要啟用此延伸規格，請完成下列步驟：
  1. 從 {{site.data.keyword.iot_short_notm}} 儀表板選取**延伸規格**。
  2. 在「延伸規格」頁面上，按一下**新增延伸規格**。
  3. 按一下 Arm Mbed 橋接器延伸規格旁的**新增**。
  4. 輸入 Arm Mbed 存取金鑰。您可以使用 Arm Mbed 入口網站（網址為 [https://portal.mbedcloud.com![外部鏈結圖示](../../../../icons/launch-glyph.svg "外部鏈結圖示")](https://portal.mbedcloud.com){: new_window}）來建立它。
  5. 按一下**檢查連線**按鈕，以檢查認證正確無誤。
  6. 按一下**完成**。

### 有效負載格式

Arm Mbed 平台使用兩種類型的送入訊息：通知及非同步回應。{{site.data.keyword.iot_short_notm}} 可以將指令傳送給連接至 Arm Mbed 平台的裝置。

#### 通知

裝置或感應器資料中的變更會產生通知。{{site.data.keyword.iot_short_notm}} 處理訊息之後，訊息會傳送至裝置事件主題，而且方法與將裝置直接連接至 {{site.data.keyword.iot_short_notm}} 一樣。源自連接至 Arm Mbed 平台之裝置的通知所使用的事件類型是 `notify`。

下列程式碼範例顯示 Arm Mbed 平台 API 所傳送通知的有效負載格式：

```
{
  "ep":<endpoint/deviceID>,
  "path":<resource path>,
  "ct":<content type>,
  "payload":<Base64 encoded payload>,
  "max-age":<how long the payload is valid, in seconds>
}
```

#### 非同步回應

{{site.data.keyword.iot_short_notm}} 將指令傳送給連接至 Arm Mbed 平台的裝置時，裝置會將確認訊息傳送回 {{site.data.keyword.iot_short_notm}}。此確認訊息稱為_非同步回應_，使用事件類型 `asyncResponse`。

下列程式碼範例顯示 Arm Mbed Cloud 服務所傳送非同步回應的有效負載格式：

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

#### 將指令傳送至 Arm Mbed 平台

{{site.data.keyword.iot_short_notm}} 可以將指令傳送給連接至 Arm Mbed 平台的裝置。傳送至 Arm Mbed 平台的指令必須使用下列 JSON 格式：

```
{
  "method":<PUT or POST>,
  "deviceId":<endpoint/deviceId>,
  "resourceId":<resource path>,
  "payload": <Base64 encoded payload>
}
```
選擇的方法區分大小寫。必須跳過資源路徑的起始 `/`。


有效負載必須發佈於下列主題：

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

## 歷程資料儲存
{: #historical_data}

歷程資料儲存延伸規格可讓您尋找及配置 IoT 資料的相容訊息儲存服務（例如 [{{site.data.keyword.cloudantfull}} ![外部鏈結圖示](../../../../icons/launch-glyph.svg "外部鏈結圖示")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/platform/cloudant_connector.html){: new_window} 或 [{{site.data.keyword.messagehub_full}} ![外部鏈結圖示](../../../../icons/launch-glyph.svg "外部鏈結圖示")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/platform/message_hub.html){: new_window}。

## 自訂裝置管理套件
{: #device_mgmt}

裝置管理是 {{site.data.keyword.iot_short_notm}} 的核心特性，不過，可以加以延伸，以開發其他功能。自訂裝置管理套件必須包含有效的 JSON，並定義至少一個自訂裝置管理動作。

如需自訂裝置管理功能（包括所需 JSON 格式的範例）的相關資訊，請參閱[裝置管理自訂延伸規格 ![外部鏈結圖示](../../../../icons/launch-glyph.svg "外部鏈結圖示")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/platform/devices/device_mgmt/custom_actions.html){: new_window}。

### 新增自訂裝置管理套件

使用 {{site.data.keyword.iot_short_notm}} 儀表板或 API，即可新增自訂裝置管理套件。

若要使用 {{site.data.keyword.iot_short_notm}} 儀表板新增自訂裝置管理套件，請執行下列動作：

1. 從 {{site.data.keyword.iot_short_notm}} 儀表板中，按一下導覽列中的**設定**。
2. 按一下**自訂裝置管理套件**。
3. 按一下**新增套件**按鈕。
4. 選取套件檔，然後按一下**開啟**。

若要使用 API 新增自訂裝置管理套件，請參閱 [{{site.data.keyword.iot_short_notm}} API 文件 ![外部鏈結圖示](../../../../icons/launch-glyph.svg "外部鏈結圖示")](https://docs.internetofthings.ibmcloud.com/apis/swagger/v0002/orgAdmin.html){: new_window}。

## 電子郵件
{: #email}

使用電子郵件邀請，即可將使用者新增至 {{site.data.keyword.iot_short_notm}}。如需相關資訊，請參閱[管理使用者存取權](/docs/services/IoT?topic=iot-platform-managing-user-access#managing-user-access)。

若要使用電子郵件邀請功能，必須將電子郵件延伸規格配置為使用 SendGrid 線上服務或「簡易郵件傳送通訊協定 (SMTP)」服務。延伸規格也可以使用 SendGrid {{site.data.keyword.cloud_notm}} 應用程式。

### SendGrid 線上服務

若要配置電子郵件延伸規格來與 SendGrid 線上服務搭配使用，請遵循下列步驟：

1. 從 SendGrid 線上帳戶中擷取經授權的 API 金鑰。
2. 在 {{site.data.keyword.iot_short_notm}} 儀表板中，按一下導覽列中的**延伸規格**。
3. 在**電子郵件**區段中，按一下**設定**。
4. 選取**具有 API 金鑰的 SendGrid**。
5. 輸入網站管理者的姓名及電子郵件位址，以及經授權的 API 金鑰。

### SMTP 服務

若要配置電子郵件延伸規格來與 SMTP 服務搭配使用，請遵循下列步驟：

1. 在 {{site.data.keyword.iot_short_notm}} 儀表板中，按一下導覽列中的**延伸規格**。
2. 在**電子郵件**區段中，按一下**設定**。
3. 選取 **SMTP**。
4. 輸入 SMTP 服務的配置詳細資料。

### SendGrid {{site.data.keyword.cloud_notm}} 應用程式

若要配置電子郵件延伸規格來與 SendGrid {{site.data.keyword.cloud_notm}} 應用程式搭配使用，請遵循下列步驟：

1. 建立虛擬的應用程式，並連結 SendGrid 服務。  
為了擷取配置認證，請將 SendGrid 服務新增並連結至虛擬的應用程式。

 1. 從 {{site.data.keyword.cloud_notm}} 儀表板中，按一下**建立服務**。
 2. 從型錄中選取 SendGrid 服務，然後按一下**建立**。
 3. 從 {{site.data.keyword.cloud_notm}} 儀表板中，新增 {{site.data.keyword.runtime_nodejs_full}} 應用程式。
 4. 從 {{site.data.keyword.cloud_notm}} 儀表板中，按一下 {{site.data.keyword.runtime_nodejs_notm}} 應用程式，然後按一下**連結服務或 API**。
 5. 選取 SendGrid 服務，然後按一下**新增**。
 6. 重新編譯打包 {{site.data.keyword.runtime_nodejs_notm}} 應用程式。
2. 準備配置 {{site.data.keyword.iot_short_notm}} 服務。  
使用 {{site.data.keyword.iot_short_notm}} 儀表板或使用 {{site.data.keyword.iot_short_notm}} API，即可配置 {{site.data.keyword.iot_short_notm}}。  
 1. 從 {{site.data.keyword.cloud_notm}} 儀表板中，按一下 {{site.data.keyword.runtime_nodejs_notm}} 應用程式。
 2. 從導覽列中，按一下**環境變數**。
 3. 將顯示的 JSON 複製到暫存文字檔。  
JSON 的格式應該如下：
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
3. 將配置資料新增至 {{site.data.keyword.iot_short_notm}} 組織。
 1. 開啟 {{site.data.keyword.iot_short_notm}} 儀表板。
 2. 從導覽列中，按一下**延伸規格**。
 3. 按一下**電子郵件**圖示下的**設定**。
 4. 選取**具有使用者名稱的 SendGrid**。
 5. 輸入暫存文字檔中的配置資料。
 6. 按一下**完成**。
