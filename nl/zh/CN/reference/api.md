---

copyright:

years: 2017, 2019
lastupdated: "2019-02-13"

---

{:new_window: target="\_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:important: .important}


# API
{: #api_overview}

<p>该 {{site.data.keyword.Bluemix}} 文档集合与 {{site.data.keyword.iot_full}} 轻量价格套餐有关，并且包含基本入门信息、API 参考和一般故障诊断信息。
有关完整的 {{site.data.keyword.iot_short_notm}} 功能文档，请参阅 IBM Knowledge Center 上的 [{{site.data.keyword.iot_short_notm}} 产品文档 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/overview/overview.html)。可在 [{{site.data.keyword.iot_short_notm}} 服务套餐](/docs/IoT/plans_overview.html#plans_overview)中找到有关各种套餐的更多信息。
</p>
{: important}

有多个 API 可用于为连接到 {{site.data.keyword.iot_full}} 的设备、网关和应用程序开发代码。

HTTP API 以 HTTP 基本认证保护。当您使用仪表板生成 API 密钥时，系统即会向您呈现密钥和认证令牌。有关 API 密钥和令牌的更多信息，请参阅 [API 密钥连接 ![外部链接图标](../../../icons/launch-glyph.svg "外部链接图标")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/platform/platform_authorization.html#api-key)。


## 关于 HTTP API
{: #api_about}

注册自己的组织后，系统会向您提供 6 字符的组织标识，在任何 HTTP API 调用的主机名中都需要该标识。在以下地址中可访问组织的基本 URL：

https://<**orgId**>.internetofthings.ibmcloud.com/api/v0002

要认证应用程序 API 的请求，请将用户名设置为 API 密钥，将密码设置为认证令牌。

对于消息传递 API，请使用以下地址：

https://<**orgId**>.messaging.internetofthings.ibmcloud.com/api/v0002

## HTTP API
{: #api_http}

API|用于...
------------- | -------------
[组织管理 ![外部链接图标](../../../icons/launch-glyph.svg)](https://docs.internetofthings.ibmcloud.com/apis/swagger/v0002/orgAdmin.html){: new_window} |配置组织（包括创建和删除设备）、检查使用情况、查看服务状态和诊断设备连接问题。

[安全性 ![外部链接图标](../../../icons/launch-glyph.svg)](https://docs.internetofthings.ibmcloud.com/apis/swagger/v0002/security.html){: new_window} |管理用户、API 密钥和设备的认证和授权。
[信息管理 ![外部链接图标](../../../icons/launch-glyph.svg)](https://docs.internetofthings.ibmcloud.com/apis/swagger/v0002/info-mgmt.html){: new_window} |访问设备事件数据以及获取和更新设备位置并取得该位置的天气信息。
[数据管理 ![外部链接图标](../../../icons/launch-glyph.svg)](https://docs.internetofthings.ibmcloud.com/apis/swagger/v0002/state-mgmt.html){: new_window}   |组织和集成传入和传出 {{site.data.keyword.iot_short_notm}} 的数据。
[设备管理 ![外部链接图标](../../../icons/launch-glyph.svg)](https://docs.internetofthings.ibmcloud.com/apis/swagger/v0002/deviceMgmt.html){: new_window} |使用设备管理协议与受管设备进行交互。

[消息传递 ![外部链接图标](../../../icons/launch-glyph.svg)](https://docs.internetofthings.ibmcloud.com/apis/swagger/v0002/http-messaging.html){: new_window}   |使用 HTTP 发布事件并发送命令。
[风险管理 ![外部链接图标](../../../icons/launch-glyph.svg)](https://docs.internetofthings.ibmcloud.com/apis/swagger/v0002/riskmgmt.html){: new_window}   |管理风险管理策略和报告。

## 扩展 HTTP API
{: #api_extension}

API|用于...
------------- | -------------
[AT&T 扩展 ![外部链接图标](../../../icons/launch-glyph.svg)](https://docs.internetofthings.ibmcloud.com/apis/swagger/v0002/ext-atnt.html){: new_window} |管理 AT&T 设备。

[Jasper 扩展 ![外部链接图标](../../../icons/launch-glyph.svg)](https://docs.internetofthings.ibmcloud.com/apis/swagger/v0002/ext-jasper.html){: new_window} |管理 Jasper 设备。

[Orange 扩展 ![外部链接图标](../../../icons/launch-glyph.svg)](https://docs.internetofthings.ibmcloud.com/apis/swagger/v0002/ext-orange.html){: new_window} |查看与 {{site.data.keyword.iot_short_notm}} 组织连接且已安装 Orange SIM 卡的设备的 SIM 卡数据。


## Beta HTTP API
{: #api_beta}

API|用于...
------------- | -------------
[复原删除的设备 ![外部链接图标](../../../icons/launch-glyph.svg)](https://docs.internetofthings.ibmcloud.com/apis/swagger/v0002-beta/restore-device-beta.html){: new_window}   |如果误删除了设备，可以在 14 天内进行复原。
