---

copyright:
  years: 2016, 2019
lastupdated: "2019-02-13"

---

{:new_window: target="blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:important: .important}

# 管理使用者存取權
{: #managing-user-access}

<p>此 {{site.data.keyword.Bluemix}} 文件集合與 {{site.data.keyword.iot_full}}「精簡」定價方案相關，包含了基本入門資訊、API 參考資料及一般疑難排解資訊。
如需完整的 {{site.data.keyword.iot_short_notm}} 特性文件，請參閱 IBM Knowledge Center 上的 [{{site.data.keyword.iot_short_notm}} 產品文件 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/overview/overview.html)。您可以在 [{{site.data.keyword.iot_short_notm}} 服務方案](/docs/IoT/plans_overview.html#plans_overview)中找到各種方案的相關資訊。
</p>
{: important}

從儀表板的「成員」頁面中，您可以控制及管理對 {{site.data.keyword.iot_full}} 組織的存取權。您可以透過新增、邀請或匯入的方式來新增使用者。您也可以透過指派角色，授與使用者不同的存取權層次。
{:shortdesc}

## 新增使用者
{: #adding-new-users}

從儀表板的**成員**頁面，您可以使用「新增」功能來新增個別成員。您也可以使用「匯入」功能，同時新增多位成員。

依預設，成員帳戶不會到期。將使用者新增至 {{site.data.keyword.iot_short_notm}} 組織時，您可以選擇是否設定其帳戶的到期日。

### 將成員新增至您的 {{site.data.keyword.iot_short_notm}} 組織

若要將成員新增至組織，您將需要成員的 IBM ID。新增成員時，您不需要成員的確認。

若要將單一成員新增至您的 {{site.data.keyword.iot_short_notm}} 組織，請執行下列動作：
1. 在 {{site.data.keyword.iot_short_notm}} 儀表板中，按一下導覽列中的**成員**。
2. 按一下**新增成員**，然後選取**新增**標籤。
3. 輸入成員的 IBM ID。
4. 選取成員的角色。
5. 選用項目：設定到期日。
6. 按一下**新增**。

若要同時新增多位成員，您必須上傳 `.csv` 檔案，其中包含每一位成員的 IBM ID、角色及選用性的到期日。如需相關資訊，請參閱[建構 CSV 檔案](#constructing-your-csv)。
1. 在 {{site.data.keyword.iot_short_notm}} 儀表板中，按一下導覽列中的**成員**。
2. 按一下**新增成員**，然後選取**匯入**標籤。
3. 瀏覽您的檔案，或將 `.csv` 檔案拖曳至**上傳 CSV** 視窗。
4. 選取在無法辨識 CSV 檔案中指定的角色時，所要使用的預設角色。
5. 將 CSV 檔案中的直欄號碼對映至相對應的 IBM ID、角色和選用性的到期日項目。
6. 配合 `.csv` 檔案中使用的分隔字元，選取適當的逗點或分號直欄分隔字元。
7. 按一下**匯入**，以匯入 IBM ID 並建立成員。


### 建構 CSV 檔案
{: #constructing-your-csv}

建構 CSV 檔案以將成員匯入至您的組織時，請確保您在所使用的方法中包含必要資訊。請使用逗點或分號來區隔直欄。  
**重要事項：**上傳 CSV 檔案時，請在 **CSV 設定**下，確定您選取正確的直欄分隔字元。

以逗點定界的 CSV 檔案範例：  
```
user1@sample.com,PD_DEVELOPER_USER,2018-03-13
user2@sample.com,PD_OPERATOR_USER,2018-03-13
user3@sample.com,PD_ADMIN_USER,2018-03-13
```
使用下列直欄項目的位置：  
- 直欄 1：使用者的電子郵件位址。  
如果您要新增成員，請確定您使用的電子郵件位址對應於有效的 IBM ID。如果您要邀請成員，可以使用任何有效的電子郵件位址。
- 直欄 2：要指派給使用者的角色。  
請輸入下列其中一個角色：
 - PD_ADMIN_USER
 - PD_OPERATOR_USER
 - PD_DEVELOPER_USER
 - PD_ANALYST_USER
 - PD_READER_USER  
如需使用者角色的相關資訊，請參閱[使用者、應用程式及閘道角色：![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/platform/roles_index.html#user_roles){: new_window}。
- 直欄 3：對應於使用者到期日的 ISO 6801 日期（例如 `2018-03-13`）。

## 編輯使用者
{: #editing-users}

您可以編輯使用者以變更其角色；新增、移除或變更存取到期日，或是新增或移除組織的存取權。

1. 在 {{site.data.keyword.iot_short_notm}} 儀表板中，按一下導覽列中的**成員**。
2. 按一下您想要編輯之使用者旁的**編輯**圖示。
3. 對使用者進行想要的變更。
4. 按一下**儲存**。

## 封鎖使用者存取權
{: #blocking-users}

您可以封鎖使用者存取 {{site.data.keyword.iot_short_notm}} 組織，同時仍然維護組織成員資格。

1. 在 {{site.data.keyword.iot_short_notm}} 儀表板中，按一下導覽列中的**成員**。
2. 按一下您想要封鎖存取 {{site.data.keyword.iot_short_notm}} 組織之使用者旁的切換按鈕。

## 限制使用者存取權
{: #limiting-users}

資源層次存取控制可讓您限制組織中的裝置存取權。您可以使用資源群組來指定每位使用者或每個 API 金鑰可管理的裝置。如需如何配置資源層次存取控制的相關資訊，請參閱[配置資源層次存取控制 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/platform/reference/rlac.html#configure_RLAC){: new_window}。

## 移除使用者
{: #removing-users}

您可以從 {{site.data.keyword.iot_short_notm}} 組織中完全移除使用者。移除使用者是無法復原的作業，而且必須將使用者[新增至平台](#adding-new-users)才能還原存取權。

1. 在 {{site.data.keyword.iot_short_notm}} 儀表板中，按一下導覽列中的**成員**。
2. 按一下要移除的使用者旁邊的**刪除**圖示。
3. 按一下確認對話框中的**刪除**。
