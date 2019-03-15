---

copyright:
  years: 2017, 2019
lastupdated: "2019-02-13"
---

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

<p>此 {{site.data.keyword.Bluemix}} 文件集合與 {{site.data.keyword.iot_full}}「精簡」定價方案相關，包括基本入門資訊、API 參考資料及一般疑難排解資訊。
如需完整的 {{site.data.keyword.iot_short_notm}} 特性文件，請參閱 IBM Knowledge Center 上的 [{{site.data.keyword.iot_short_notm}} 產品文件 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/overview/overview.html)。您可以在 [{{site.data.keyword.iot_short_notm}} 服務方案](/docs/IoT/plans_overview.html#plans_overview)中找到各種方案的相關資訊。
</p>
{: important}

使用 {{site.data.keyword.iot_full}} 裝置模擬器，即可設定裝置的模擬事件。您可以使用模擬事件資料來瞭解、測試及示範完整運作的 {{site.data.keyword.iot_short_notm}} 特性。
{: shortdesc}

您可以使用現有裝置類型及裝置，而且模擬器可讓您產生現有類型的新裝置。您可以配置每一個裝置的事件詳細資料，或設定用於套用至所有裝置的預設配置。您可以匯出模擬事件配置，以重複使用或共用該配置來設定其他模擬。

若要模擬裝置資料，請執行下列動作：

1. 登入 {{site.data.keyword.iot_short_notm}}。
2. 從主導覽窗格中，選取**設定**。
3. 在**資料和裝置**區段中，啟動裝置模擬器。
4. 從主導覽窗格中，選取**裝置**。畫面右下角的訊息指出未執行任何模擬。
5. 按一下「0 個模擬執行中」訊息。
6. 在**模擬**蹦現視窗中，按一下**建立模擬**。
7. 選取您要模擬其資料的現有裝置類型，或鍵入裝置類型名稱來建立新的裝置類型。
8. 按一下**匯入/匯出模擬**，以使用現有的配置，或手動配置裝置類型的模擬詳細資料：
   1. 按一下**+ 新建事件類型**，將事件類型新增至裝置類型。
   2. 輸入事件類型的名稱。
   3. 在**排程**下，設定事件的頻率。
   3. 以 JSON 格式編輯事件類型詳細資料，並且儲存已更新的事件類型。

   <p> 配置事件時，您可以使用下列特殊變數：  
        - `range`：此變數會取代為介於兩個所提供值之間的亂數，例如：`{"random": range(300, 100)}`  
        - `$counter`：此變數會取代為模擬器中針對現行類型所新增的裝置數目，例如：`{"total": $counter}`  
        - `increment`：此變數指出起始數目和它增加的增量，例如，`{"myNumber": increment(10, 1)}`。在此情況下，`myNumber` 會從 10 開始，並且在每次傳送有效負載時加 1（10、11、12 依此類推）。</p>
   {: tip}

9. 選取模擬的已登錄裝置，或鍵入裝置名稱來建立新的裝置。
10. 如果要建立其他模擬，請按一下**新建模擬**，然後針對您要套用自訂設定的每一台裝置，重複這些配置步驟。畫面右下方的訊息顯示作用中模擬次數。
11. **選用項目：**在您配置裝置的模擬之後，請匯出模擬詳細資料，以重複使用或共用這些資訊：
    1. 在**模擬**蹦現視窗中，按一下**匯入/匯出**。
    2. 選取**匯出**標籤。
    3. 將模擬詳細資料複製到剪貼簿，或以 JSON 檔案形式下載這些資訊。
12. 在**裝置**頁面上，瀏覽至其中一個模擬裝置，然後選取**最近事件**標籤，以驗證模擬事件運作中。
