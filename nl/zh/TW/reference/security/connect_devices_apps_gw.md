---

copyright:
  years: 2015, 2019
lastupdated: "2019-02-13"

---

{:new_window: target="\_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}
{:pre: .pre}
{:important: .important}

# 應用程式、裝置及閘道的連接資訊
{: #connect_devices_apps_gw}

<p>此 {{site.data.keyword.Bluemix}} 文件集合與 {{site.data.keyword.iot_full}}「精簡」定價方案相關，包括基本入門資訊、API 參考資料及一般疑難排解資訊。
如需完整的 {{site.data.keyword.iot_short_notm}} 特性文件，請參閱 IBM Knowledge Center 上的 [{{site.data.keyword.iot_short_notm}} 產品文件 ![外部鏈結圖示](../../../../icons/launch-glyph.svg "外部鏈結圖示")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/overview/overview.html)。您可以在 [{{site.data.keyword.iot_short_notm}} 服務方案](/docs/IoT/plans_overview.html#plans_overview)中找到各種方案的相關資訊。
</p>
{: important}

您可以使用 MQTT 通訊協定將應用程式、裝置及閘道連接至 {{site.data.keyword.iot_full}}。您也可以使用 HTTP REST API 將裝置連接至 {{site.data.keyword.iot_short_notm}}。
{: shortdesc}


## 用戶端連線 URL
{: #client_connect_url}

若要將裝置、應用程式和閘道用戶端連接至 {{site.data.keyword.iot_short_notm}} 實例，請使用下列連線 URL：

### 傳訊位址

<pre class="pre"><var class="keyword varname">orgId</var>.messaging.internetofthings.ibmcloud.com</pre>
{: codeblock}

### HTTP REST API 連線 URL

<pre class="pre"><code class="hljs">https://<var class="keyword varname">orgId</var>.internetofthings.ibmcloud.com/api/v0002/device/types/<var class="keyword varname">typeId</var>/devices/<var class="keyword varname">deviceId</var>/events/<var class="keyword varname">eventId</var></code></pre>
{: codeblock}

**附註**
- 其中 *orgId* 是在登錄服務實例時所產生的唯一組織 ID。
- 如果您要將裝置或應用程式連接至 Quickstart 服務，請指定 'quickstart' 作為 *orgId* 值。

## 防火牆配置
{: #firewall_configuration}

若要將裝置及應用程式連接至 {{site.data.keyword.iot_short_notm}}，您必須確保將任何防火牆配置為容許在特定埠上進行資料傳輸。防火牆可能位於您的本端機器、您的路由器上或作為公司網路的一部分。

### 埠安全
{: #client_port_security}

使用 MQTT 或 HTTP 通訊協定將裝置、閘道及應用程式連接至 {{site.data.keyword.iot_short_notm}}。連線不一定安全。

|連線類型|通訊協定|埠號|
|:---|:---|:---|
|非安全*|MQTT 及 HTTP|1883 或 80|
|安全 (TLS)|MQTT 及 HTTPS|8883 或 443|

&ast; 依預設，會停用埠 1883 和 80，以進行傳訊。如需變更預設設定的相關資訊，請參閱[配置安全原則 ![外部鏈結圖示](../../../../icons/launch-glyph.svg "外部鏈結圖示")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/platform/reference/security/set_up_policies.html#set_up_policies.html){: new_window}。

MQTT 是透過 TCP 及 WebSockets 所支援。MQTT 用戶端會使用適當的認證來連接，例如適用於裝置的裝置鑑別記號，以及適用於應用程式的 API 金鑰和記號。因為傳訊至非安全埠 1883 的 MQTT 會以純文字格式來傳送這些認證，所以請務必改用安全的替代埠 8883 或 443。透過安全埠傳送時，一律會加密 TLS 認證。請注意，您必須在應用程式中啟用 TLS（例如：使用 Python MQTT 程式庫中的 `tls_set()` 方法）。否則，可能會以不安全的方式傳送資料。

當您在埠 8883 或 443 上使用安全的 MQTT 傳訊時，較新的用戶端程式庫會自動信任 {{site.data.keyword.iot_short_notm}} 所呈現的預設憑證。如果您的用戶端環境不是這種情形，您可以從 [messaging.pem ![外部鏈結圖示](../../../../icons/launch-glyph.svg "外部鏈結圖示")](https://github.com/ibm-watson-iot/iot-python/blob/master/src/wiotp/sdk/messaging.pem){: new_window} 下載並使用完整的憑證鏈。如果您已上傳自訂憑證，則可能需要確保將適當的信任鏈新增至用戶端環境。

## 防火牆配置
{: #firewall_configuration .sectiontitle}

若要將裝置及應用程式連接至 {{site.data.keyword.iot_short_notm}}，您必須確保將任何防火牆配置為容許在特定埠上進行資料傳輸。防火牆可能位於您的本端機器、您的路由器上或作為公司網路的一部分。

請確保所需的 IP 位址已開啟並已啟用，可進行通訊。

|地區|IP 位址|傳訊埠</br> （非安全）| 傳訊埠（安全）|
|:---|:---|:---| :---|
|美國南部|169.45.2.16/28* </br>169.46.7.56/29</br>169.48.234.208/29</br>169.62.202.128/29|1883,80 | 8883,443|
|英國|159.8.169.208/28* </br>158.175.111.152/29</br>158.176.104.24/29</br>141.125.70.152/29|1883,80 | 8883,443|
|德國|159.122.121.80/28* </br>149.81.125.176/29</br>158.177.82.208/29</br>161.156.96.80/29|1883,80 | 8883,443|
|快速入門|169.45.2.16/28* </br>169.46.7.56/29</br>169.48.234.208/29</br>169.62.202.128/29|1883,80 |不可用|
|專用 {{site.data.keyword.iot_short_notm}}|請聯絡您的 {{site.data.keyword.IBM}} 代表。|-| - |
&ast; 2019 年第一季之後不再使用。

## TLS 需求
{: #tls_requirements}

部分「傳輸層安全 (TLS)」用戶端程式庫不支援包含萬用字元的網域。如果您無法順利變更程式庫，請停用憑證檢查。

您的 TLS 需求會根據您使用 MQTT 還是 HTTP 通訊協定連接至 {{site.data.keyword.iot_short_notm}} 而定。下列各節顯示使用預設伺服器憑證時所支援的密碼組合。如果您使用自己的用戶端憑證，則支援的密碼組合取決於所使用的憑證。

### MQTT 連線的 TLS 需求

{{site.data.keyword.iot_short_notm}} 需要 TLS 1.2 版。請確定至少容許下列其中一個密碼組合：

- TLS_ECDHE_RSA_WITH_AES_128_GCM_SHA256
- TLS_DHE_RSA_WITH_AES_128_GCM_SHA256
- TLS_ECDHE_RSA_WITH_AES_128_CBC_SHA
- TLS_DHE_RSA_WITH_AES_128_CBC_SHA
- TLS_ECDHE_RSA_WITH_AES_256_GCM_SHA384
- TLS_DHE_RSA_WITH_AES_256_GCM_SHA384
- TLS_ECDHE_RSA_WITH_AES_256_CBC_SHA
- TLS_DHE_RSA_WITH_AES_256_CBC_SHA
- TLS_RSA_WITH_AES_128_GCM_SHA256
- TLS_RSA_WITH_AES_256_GCM_SHA384

### HTTP 連線的 TLS 需求

如果您使用預設伺服器憑證，則 {{site.data.keyword.iot_short_notm}} 需要 TLS 1.2 版。請確定至少容許下列其中一個密碼組合：


- TLS_ECDHE_RSA_WITH_AES_128_CBC_SHA
- TLS_DHE_RSA_WITH_AES_128_CBC_SHA
- TLS_ECDHE_RSA_WITH_AES_256_CBC_SHA
- TLS_DHE_RSA_WITH_AES_256_CBC_SHA
- TLS_RSA_WITH_AES_256_CBC_SHA
- TLS_RSA_WITH_AES_128_CBC_SHA

在密碼清單中使用轉遞秘密密碼 ECDHE 或 DHE，以增加加密強度。

## MQTT 用戶端鑑別
{: #mqtt_authentication}

**重要事項：**每一個 MQTT 用戶端都需要唯一的用戶端 ID。如果您嘗試使用已連接的用戶端 ID 來連接組織中的用戶端，則第一個連線會中斷。

直接連接到 {{site.data.keyword.iot_short_notm}} 的裝置和閘道會在儀表板上顯示狀態圖示，指出其已連接。透過閘道間接連接的裝置會顯示為已斷線，因為儀表板無法感知透過閘道連接的裝置。

### MQTT 用戶端 ID

為了讓裝置、應用程式和閘道順利鑑別，請使用下列用戶端 ID 和格式來定義每一個 MQTT 用戶端：

|用戶端類型|ID|MQTT ID 格式|
|:---|:---|:---|
|應用程式|a|<pre class="pre">a:<var class="keyword varname">orgId</var>:<var class="keyword varname">appId</var></pre>
|可擴充應用程式|A|<pre class="pre">A:<var class="keyword varname">orgId</var>:<var class="keyword varname">appId</var></pre>
|裝置|d|<pre class="pre">d:<var class="keyword varname">orgId</var>:<var class="keyword varname">deviceType</var>:<var class="keyword varname">deviceId</var></pre>|
|閘道|g|<pre class="pre">g:<var class="keyword varname">orgId</var>:<var class="keyword varname">typeId</var>:<var class="keyword varname">deviceId</var></pre>|

其中
- *orgId* 是在登錄服務時所產生、6 個字元的唯一組織 ID。
- *appId* 是用戶端的使用者定義唯一字串 ID。
- *deviceId* 能在所有類型中唯一地識別裝置或閘道，且類似於序號。
- *device_type* 是正在連接之裝置的類型 ID，且類似於型號。
- *typeId* 是正在連接之閘道的類型 ID，且類似於型號。

*appId*、*type_id*、*device_type* 和 *device_id* 值不得超過 36 個字元，而且只能包含：
- 英數字元（a-z、A-Z、0-9）
- 橫線 ( - )
- 底線 ( _ )
- 句點 ( . )

**附註：**
- 當您連接至 Quickstart 服務時，不需要鑑別。
- 在連接之前，您不需要登錄應用程式。

如需共用訂閱格式的相關資訊，請參閱[應用程式的 MQTT 連線功能 ![外部鏈結圖示](../../../../icons/launch-glyph.svg "外部鏈結圖示")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/platform/applications/mqtt.html){: new_window}。


### 使用 MQTT 來連接應用程式

{{site.data.keyword.iot_short_notm}} 應用程式需要有 API 金鑰才能連接至組織。登錄 API 金鑰時，會產生必須與該 API 金鑰搭配使用的記號。

下列程式碼提供 API 金鑰的範例：

<pre class="pre">a-<var class="keyword varname">orgId</var>-a84ps90Ajs</pre>
{: codeblock}

下列範例顯示一般鑑別記號：

```
 MP$08VKz!8rXwnR-Q*
```

當您使用 API 金鑰建立 MQTT 連線時，請確定符合下列需求：

- MQTT 用戶端 ID 的格式為：a:*orgId*:*appId*
- MQTT 使用者名稱是 API 金鑰，例如 a-*orgId*-a84ps90Ajs
- MQTT 密碼是鑑別記號，例如 *MP$08VKz!8rXwnR-Q**

如需相關資訊，請參閱 [應用程式的 MQTT 連線功能 ![外部鏈結圖示](../../../../icons/launch-glyph.svg "外部鏈結圖示")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/platform/applications/mqtt.html){: new_window}。

### 裝置鑑別

#### 使用者名稱
{{site.data.keyword.iot_short_notm}} 服務僅支援裝置的記號型鑑別；因此每一個裝置都只有一個有效使用者名稱。
`use-token-auth` 的值向服務指出，閘道或裝置的鑑別記號會用來作為 MQTT 連線的密碼。

如需相關資訊，請參閱 [裝置的 MQTT 連線功能 ![外部鏈結圖示](../../../../icons/launch-glyph.svg "外部鏈結圖示")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/platform/devices/mqtt.html){: new_window}。

#### 密碼
如果用戶端是使用記號型鑑別，請提交裝置鑑別記號作為所有 MQTT 連線的密碼。
