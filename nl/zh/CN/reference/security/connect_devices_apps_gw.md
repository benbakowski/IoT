---

copyright:
  years: 2015, 2019
lastupdated: "2019-04-05"

keywords: Client connection URLs, MQTT protocol, device authentication tokens

subcollection: iot-platform

---

{:new_window: target="\_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}
{:pre: .pre}
{:important: .important}

# 应用程序、设备和网关的连接信息
{: #connect_devices_apps_gw}

<p>该 {{site.data.keyword.cloud}} 文档集合与 {{site.data.keyword.iot_full}} 轻量价格套餐有关，并且包含基本入门信息、API 参考和一般故障诊断信息。
有关完整的 {{site.data.keyword.iot_short_notm}} 功能文档，请参阅 IBM Knowledge Center 上的 [{{site.data.keyword.iot_short_notm}} 产品文档 ![外部链接图标](../../../../icons/launch-glyph.svg "外部链接图标")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/overview/overview.html)。可在 [{{site.data.keyword.iot_short_notm}} 服务套餐](/docs/services/IoT?topic=iot-platform-plans_overview#plans_overview)中找到有关各种套餐的更多信息。
</p>
{: important}

您可以使用 MQTT 协议将应用程序、设备和网关连接到 {{site.data.keyword.iot_full}}。还可以使用 HTTP REST API 将设备连接到 {{site.data.keyword.iot_short_notm}}。
{: shortdesc}


## 客户机连接 URL
{: #client_connect_url}

要将设备、应用程序和网关客户机连接到 {{site.data.keyword.iot_short_notm}} 实例，请使用以下连接 URL：

### 消息传递地址

<pre class="pre"><var class="keyword varname">orgId</var>.messaging.internetofthings.ibmcloud.com</pre>
{: codeblock}

### HTTP REST API 连接 URL

<pre class="pre"><code class="hljs">https://<var class="keyword varname">orgId</var>.internetofthings.ibmcloud.com/api/v0002/device/types/<var class="keyword varname">typeId</var>/devices/<var class="keyword varname">deviceId</var>/events/<var class="keyword varname">eventId</var></code></pre>
{: codeblock}

**注释**
- 其中，*orgId* 是注册服务实例时生成的唯一组织标识。
- 如果要将设备或应用程序连接到 Quickstart 服务，请将“quickstart”指定为 *orgId* 值。

### 端口安全性
{: #client_port_security}

设备、网关和应用程序使用 MQTT 或 HTTP 协议连接到 {{site.data.keyword.iot_short_notm}}。连接可以是非安全或安全的。

|连接类型|协议|端口号|
|:---|:---|:---|
|非安全*|MQTT 和 HTTP|1883 或 80|
|安全 (TLS)|MQTT 和 HTTPS|8883 或 443|

&ast; 缺省情况下，针对消息传递禁用了端口 1883 和 80。有关更改缺省设置的信息，请参阅[配置安全策略 ![外部链接图标](../../../../icons/launch-glyph.svg "外部链接图标")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/platform/reference/security/set_up_policies.html#set_up_policies.html){: new_window}。

MQTT 通过 TCP 和 WebSocket 进行支持。MQTT 客户机通过使用相应凭证（例如，针对设备的设备认证令牌，以及针对应用程序的 API 密钥和令牌）进行连接。由于通过非安全端口 1883 的 MQTT 消息传递会以明文发送这些凭证，请改为始终使用安全备用端口 8883 或 443。TLS 凭证在通过安全端口发送时始终会加密。请注意，必须在应用程序中启用 TLS（例如，使用 Python MQTT 库中的 `tls_set()` 方法）。否则，数据的发送可能会不安全。

在端口 8883 或 443 上使用安全 MQTT 消息传递时，较新的客户机库会自动信任 {{site.data.keyword.iot_short_notm}} 所提供的缺省证书。如果这不适用于您的客户机环境，那么可从 [messaging.pem ![外部链接图标](../../../../icons/launch-glyph.svg "外部链接图标")](https://github.com/ibm-watson-iot/iot-python/blob/master/src/wiotp/sdk/messaging.pem){: new_window} 下载和使用完整证书链。如果已上传定制证书，可能需要确保将相应的信任链添加到客户机环境。

## 防火墙配置
{: #firewall_configuration .sectiontitle}

要将设备和应用程序连接到 {{site.data.keyword.iot_short_notm}}，必须确保任何防火墙都已配置为允许特定端口上的流量。防火墙可能位于本地计算机上、路由器上，或者作为公司网络的一部分。

确保所需 IP 地址已打开并启用以进行通信。

|区域|IP 地址|消息传递端口</br>（不安全）|消息传递端口（安全）|
|:---|:---|:---| :---|
|us-south|169.45.2.16/28* </br>169.46.7.56/29</br>169.48.234.208/29</br>169.62.202.128/29|1883,80 | 8883,443|
|eu-gb|159.8.169.208/28* </br>158.175.111.152/29</br>158.176.104.24/29</br>141.125.70.152/29|1883,80 | 8883,443|
|eu-de|159.122.121.80/28* </br>149.81.125.176/29</br>158.177.82.208/29</br>161.156.96.80/29|1883,80 | 8883,443|
|Quickstart|169.45.2.16/28* </br>169.46.7.56/29</br>169.48.234.208/29</br>169.62.202.128/29|1883,80 |不可用|
|Dedicated {{site.data.keyword.iot_short_notm}}|请与 {{site.data.keyword.IBM}} 代表联系。|-| - |
&ast; 在 2019 年第一季度之后不再使用。

## TLS 需求
{: #tls_requirements}

一些传输层安全性 (TLS) 客户机库不支持包含通配符的域。如果无法成功更改库，请禁用证书检查。

TLS 需求取决于是要使用 MQTT 还是 HTTP 协议连接到 {{site.data.keyword.iot_short_notm}}。以下部分显示了使用缺省服务器证书时支持的密码套件。如果要使用您自己的客户机证书，那么支持的密码套件取决于所使用的证书。

### 针对 MQTT 连接的 TLS 需求

{{site.data.keyword.iot_short_notm}} 需要 TLS V1.2。请确保至少允许下列其中一个密码套件：

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

### 针对 HTTP 连接的 TLS 需求

如果要使用缺省服务器证书，那么 {{site.data.keyword.iot_short_notm}} 需要 TLS V1.2。请确保至少允许下列其中一个密码套件：


- TLS_ECDHE_RSA_WITH_AES_128_CBC_SHA
- TLS_DHE_RSA_WITH_AES_128_CBC_SHA
- TLS_ECDHE_RSA_WITH_AES_256_CBC_SHA
- TLS_DHE_RSA_WITH_AES_256_CBC_SHA
- TLS_RSA_WITH_AES_256_CBC_SHA
- TLS_RSA_WITH_AES_128_CBC_SHA

使用密码列表中的转发保密密码 ECDHE 或 DHE 来增加加密强度。

## MQTT 客户机认证
{: #mqtt_authentication}

**重要信息：**每个 MQTT 客户机都需要唯一的客户机标识。如果尝试通过使用已连接的客户机标识来连接您组织中的客户机，那么第一个连接会断开。

直接连接到 {{site.data.keyword.iot_short_notm}} 的设备和网关会在仪表板上显示一个状态图标，指示其已连接。通过网关间接连接的设备会显示为断开连接，因为仪表板识别不到通过网关连接的设备。

### MQTT 客户机标识

要使设备、应用程序和网关可成功认证，请通过使用以下客户机标识和格式定义每个 MQTT 客户机：

|客户机类型|标识|MQTT 标识格式|
|:---|:---|:---|
|应用程序|a|<pre class="pre">a:<var class="keyword varname">orgId</var>:<var class="keyword varname">appId</var></pre>
|可扩展应用程序|A|<pre class="pre">A:<var class="keyword varname">orgId</var>:<var class="keyword varname">appId</var></pre>
|设备|d|<pre class="pre">d:<var class="keyword varname">orgId</var>:<var class="keyword varname">deviceType</var>:<var class="keyword varname">deviceId</var></pre>|
|网关|g|<pre class="pre">g:<var class="keyword varname">orgId</var>:<var class="keyword varname">typeId</var>:<var class="keyword varname">deviceId</var></pre>|

其中：
- *orgId* 是注册服务时生成的 6 字符唯一组织标识。
- *appId* 是客户机的用户定义唯一字符串标识。
- *deviceId* 在所有类型中唯一标识某个设备或网关，与序列号相似。
- *device_type* 是要连接的设备类型的标识，与型号相似。
- *typeId* 是要连接的网关类型的标识，与型号相似。

*appId*、*type_id*、*device_type* 和 *device_id* 值不得超过 36 个字符，而且只能包含以下字符：
- 字母数字字符（a-z、A-Z 和 0-9）
- 连字符 (-)
- 下划线 (_)
- 点 ( . )

**注：**
- 连接到 Quickstart 服务时，不需要进行认证。
- 连接之前，不需要注册应用程序。

有关共享预订格式的信息，请参阅[应用程序的 MQTT 连接 ![外部链接图标](../../../../icons/launch-glyph.svg "外部链接图标")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/platform/applications/mqtt.html){: new_window}。


### 使用 MQTT 连接应用程序

{{site.data.keyword.iot_short_notm}} 应用程序需要 API 密钥以连接到组织。注册 API 密钥时，会生成令牌，此令牌必须与该 API 密钥配合使用。

以下代码提供 API 密钥示例：

<pre class="pre">a-<var class="keyword varname">orgId</var>-a84ps90Ajs</pre>
{: codeblock}

以下示例显示了典型的认证令牌：

```
 MP$08VKz!8rXwnR-Q*
```

通过使用 API 密钥建立 MQTT 连接时，确保满足以下需求：

- MQTT 客户机标识采用以下格式：a:*orgId*:*appId*
- MQTT 用户名是 API 密钥，例如，a-*orgId*-a84ps90Ajs
- MQTT 密码是认证令牌，例如，*MP$08VKz!8rXwnR-Q**

有关更多信息，请参阅[应用程序的 MQTT 连接 ![外部链接图标](../../../../icons/launch-glyph.svg "外部链接图标")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/platform/applications/mqtt.html){: new_window}。

### 设备认证

#### 用户名
{{site.data.keyword.iot_short_notm}} 服务仅支持对设备进行基于令牌的认证；因此，每个设备仅具有一个有效用户名。
`use-token-auth` 值向服务指示：网关或设备的认证令牌用作 MQTT 连接的密码。

有关更多信息，请参阅[设备的 MQTT 连接![外部链接图标](../../../../icons/launch-glyph.svg "外部链接图标")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/platform/devices/mqtt.html){: new_window}。

#### 密码
如果客户机使用的是基于令牌的认证，请提交设备认证令牌作为所有 MQTT 连接的密码。
