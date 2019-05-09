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

<p>该 {{site.data.keyword.cloud}} 文档集合与 {{site.data.keyword.iot_full}} 轻量价格套餐有关，并且包含基本入门信息、API 参考和一般故障诊断信息。
有关完整的 {{site.data.keyword.iot_short_notm}} 功能文档，请参阅 IBM Knowledge Center 上的 [{{site.data.keyword.iot_short_notm}} 产品文档 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/overview/overview.html)。可在 [{{site.data.keyword.iot_short_notm}} 服务套餐](/docs/services/IoT?topic=iot-platform-plans_overview#plans_overview)中找到有关各种套餐的更多信息。
</p>
{: important}

有多个 API 可用于为连接到 {{site.data.keyword.iot_full}} 的设备、网关和应用程序开发代码。

HTTP API 使用 HTTP 基本认证进行保护。当您使用仪表板生成 API 密钥时，系统即会向您呈现密钥和认证令牌。有关 API 密钥和令牌的更多信息，请参阅 [API 密钥连接 ![外部链接图标](../../../icons/launch-glyph.svg)](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/platform/platform_authorization.html#api-key){: new_window}。


## 关于 HTTP API
{: #api_about}

每个 {{site.data.keyword.iot_short_notm}} 组织由 6 个字符的组织标识进行标识，该标识在任何 HTTP API 调用的主机名中都是必需的。   

### API 文档
{: #api_docs}

要查看 API 文档，请转至 [IBM Watson IoT Platform REST APIs ![外部链接图标](../../../icons/launch-glyph.svg)](https://docs.internetofthings.ibmcloud.com/apis/swagger/index.html){: new_window} 页面。从此登录页面，可访问可用 {{site.data.keyword.iot_short_notm}} API 的文档。

### 交互 API 文档

要查看和使用交互 API 文档，可在以下地址中访问组织的基本 URL：

`https://<orgId>.internetofthings.ibmcloud.com/docs/index.html`

从此登录页面，可访问可用 {{site.data.keyword.iot_short_notm}} API 的文档。您必须获得授权，才有权直接从文档运行 API 调用。

要自动获得授权，请完成以下步骤：

1. 登录到 {{site.data.keyword.iot_short_notm}} 仪表板。
2. 在相同浏览器中，打开新选项卡并转至交互 API 文档登录页面。

如果您未登录到 {{site.data.keyword.iot_short_notm}} 仪表板，请完成以下步骤：

1. 转至交互 API 文档登录页面。
2. 选择 `Authorize`。
3. 在 `Available authorizations` 框中，将用户名设置为认证令牌的 API 密钥和密码。选择 `Authorize`。
4. 关闭 `Available authorizations` 框。**重要信息：**请勿选择 `Logout`。

获得授权后，转至特定 API 调用，使用 `Try it out` 按钮以直接从文档运行 API 调用。

<!-- To authenticate requests to the application API, set the username to the API key and the password to the authentication token. -->
