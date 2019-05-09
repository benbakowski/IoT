---

copyright:
  years: 2017, 2019
lastupdated: "2019-04-05"

keywords: device simulator, devices

subcollection: iot-platform

---

{:new_window: target="blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}
{:important: .important}


# 模擬裝置資料
{: #sim_device_data}

<p>此 {{site.data.keyword.cloud}} 文件集合與 {{site.data.keyword.iot_full}}「精簡」定價方案相關，包含了基本入門資訊、API 參考資料及一般疑難排解資訊。
如需完整的 {{site.data.keyword.iot_short_notm}} 特性文件，請參閱 IBM Knowledge Center 上的 [{{site.data.keyword.iot_short_notm}} 產品文件 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/overview/overview.html)。您可以在 [{{site.data.keyword.iot_short_notm}} 服務方案](/docs/services/IoT?topic=iot-platform-plans_overview#plans_overview)中找到各種方案的相關資訊。
</p>
{: important}

使用 {{site.data.keyword.iot_full}} 裝置模擬器，可為裝置設定模擬事件，以瞭解、測試及示範完整運作的 {{site.data.keyword.iot_short_notm}} 特性，而不必登錄及連接實際裝置。
{: shortdesc}

藉由使用裝置模擬器，您可以為現有裝置類型建立模擬裝置，或建立新的裝置類型及裝置。每一個模擬裝置都可以使用唯一的事件詳細資料，但您也可以建立一個套用至所有裝置的預設配置。

## 開始之前
{: #byb-simulation .sectiontitle}
為您的使用者 ID 啟用裝置模擬。
1. 登入 {{site.data.keyword.iot_short_notm}}。
2. 從主導覽窗格中，選取**設定**。
3. 在**資料和裝置**區段中，啟動裝置模擬器。

如果為您的使用者 ID 啟用了裝置模擬，則在您登入 {{site.data.keyword.iot_short_notm}} 儀表板時，所有啟用的模擬裝置都會自動啟動。

## 模擬裝置
{: #process-simulation .sectiontitle}
啟動時，可在所有儀表板頁面上使用裝置模擬器。畫面右下角的訊息指出執行中的模擬數目。

**重要事項：**您針對使用者 ID 定義的模擬裝置及裝置類型適用於 {{site.data.keyword.iot_short_notm}} 組織的其他使用者。不過，若要為您的裝置產生模擬資料，您必須在作用中的使用者階段作業中登入 {{site.data.keyword.iot_short_notm}} 儀表板。

若要模擬裝置資料，請執行下列動作：
1. 從 {{site.data.keyword.iot_short_notm}} 儀表板中，按一下「0 個模擬執行中」訊息。
3. 在開啟的**模擬**配置視窗中，按一下**建立模擬**。
4. 配置模擬詳細資料。  
按一下**匯入/匯出模擬**，以匯入[現有配置](#reuse)或手動配置詳細資料：
   1. 選取您要模擬其資料的現有裝置類型，或鍵入裝置類型名稱來建立新的裝置類型。
   2. 修改事件類型的預設名稱。
   3. 在**排程**下，設定事件的頻率。
   4. 編輯事件有效負載。  
   新增內容及其對應值來編輯範例 JSON 有效負載，或使用[函數](#functions)來新增動態產生的資料點。  
   您也可以上傳 [CSV 事件有效負載檔案](#csv)來設定有效負載。  
   {: tip}
5. 按一下**新建事件類型**，為裝置類型新增及配置其他事件類型。
5. 啟用**將事件儲存為歷程資料**，讓您的模擬裝置狀態資料可供稍後存取。  
啟用歷程資料時，即會建立 {{site.data.keyword.iot_short_notm}} [資料管理 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/platform/GA_information_management/ga_im_definitions.html){: new_window} 元件，而且可從相關聯的邏輯介面存取模擬裝置狀態。  
**重要事項：**在啟用裝置類型來儲存歷程資料之後，您無法新增或移除事件類型，也無法修改事件有效負載中呈現的欄位。
5. 按一下**儲存**來建立裝置類型。  
現在，您準備好可以建立一個以上的模擬裝置。
6. 按一下**建立模擬裝置**，來建立裝置並開始傳送資料。  
**提示：**若要建立多個裝置，請按一下 **1 x**，然後選取要建立的裝置數目。  
7. 如果要建立其他模擬，請按一下**新建模擬**，然後針對您要套用自訂設定的每一台裝置，重複這些配置步驟。   
畫面右下角的訊息顯示作用中模擬次數。
8. 在**裝置**頁面上，瀏覽至其中一個模擬裝置，然後選取**最近事件**標籤，以驗證模擬事件運作中。

您可以[匯出模擬事件配置](#reuse)，以供重複使用或共用。

## 事件類型函數
{: #functions .sectiontitle}

您可以使用一些特殊函數，為您的事件類型建立動態資料。

函數 | 用法 | 範例 
:--- | :---  | :--  
`random(lower, upper)`  | 在指定的範圍內產生亂數。| `{"random": random(0, 100)}`  
`$counter` | 顯示現行類型的模擬裝置數目。| `{"total": $counter}`  
`increment(start, increment)` | 指定起始值及其增量值。|`{"myNumber": increment(10, 1)}` </br> 在此範例中，`myNumber` 從 10 開始，而且每次傳送有效負載時加 1。


## CSV 事件有效負載檔案
{: #csv .sectiontitle}

如果想要針對特定情境建立受管制的事件資料，您可以在 CSV 輸入檔中設定資料流程。

### 需求
CSV 檔案必須符合下列需求：
- 每一個值都是有效的 [JSON 基本元素 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://json.org){: new_window}，但附註的除外：
  - 字串：   
  範例："Hello world"
  - 數字：  
  範例：0、0.1、-22、-2.43
  - 布林：  
  true 或 false
  - 空值：  
  空值
  - **不支援：**
    - 物件  
    範例：{}
    - 陣列  
    範例：[]
- 值必須以逗點區隔。
- 列必須使用換行字元 (`\n`) 來區隔。
- 標頭列必須僅由字串值組成。


### 範例 CSV 檔案
```
"temperature", "confidence","status"
1, 0.1, "normal"
2, 0.2, "normal"
3, 0.3, "error"
4, 0.4, "normal"
```

第一行或「標頭列」決定在所有產生的裝置 JSON 事件物件中併入裝置 JSON 的內容。
每一個後續行或「資料列」會在每一個產生的裝置 JSON 事件物件中設定那些內容的值。

**提示：**匯入 CSV 檔案時，您可以選取**為來自檔案的資料製作迴圈**，讓資料行依順序循環，以達成持續資料饋入。如果未設定此切換，則 CSV 中的每一個資料列都會依排程設定的頻率傳送一次。

範例 CSV 檔案會產生下列類型的事件有效負載：
```JSON
{
  "temperature": 1,
  "confidence": 0.1,
  "status": "normal"
}
```

## 共用及重複使用模擬
{: #reuse .sectiontitle}

您可以匯出模擬詳細資料，以供重複使用或共用：
1. 在**模擬**視窗中，按一下**匯入/匯出**。
2. 選取**匯出**標籤。
3. 將模擬詳細資料複製到剪貼簿，或以 JSON 檔案形式下載這些資訊。
