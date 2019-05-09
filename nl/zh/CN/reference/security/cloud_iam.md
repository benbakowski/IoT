---

copyright:
  years: 2018, 2019
lastupdated: "2019-04-22"

keywords: Cloud IAM Authentication, IAM OAuth token, IBM Watson

subcollection: iot-platform

---

{:new_window: target="\_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:important: .important}


# {{site.data.keyword.iot_short_notm}} 的 {{site.data.keyword.iamshort}} 认证和授权 (Beta)
{: #cloud_iam}

<p>该 {{site.data.keyword.cloud}} 文档集合与 {{site.data.keyword.iot_full}} 轻量价格套餐有关，并且包含基本入门信息、API 参考和一般故障诊断信息。
有关完整的 {{site.data.keyword.iot_short_notm}} 功能文档，请参阅 {{site.data.keyword.IBM_notm}} Knowledge Center 上的 [{{site.data.keyword.iot_short_notm}} 产品文档 ![外部链接图标](../../../../icons/launch-glyph.svg "外部链接图标")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/overview/overview.html)。可在 [{{site.data.keyword.iot_short_notm}} 服务套餐](/docs/services/IoT?topic=iot-platform-plans_overview#plans_overview)中找到有关各种套餐的更多信息。
</p>
{: important}

{{site.data.keyword.iot_full}} API 使用 {{site.data.keyword.iamshort}} (IAM) 来支持用户认证和授权。

{{site.data.keyword.iot_short_notm}} 的 {{site.data.keyword.iamlong}} 认证和授权只作为受限 Beta 程序的一部分提供。未来更新可能会包含与此功能当前版本不兼容的更改。请尝试此功能，[让我们了解您的想法 ![外部链接图标](../../../../icons/launch-glyph.svg)](https://developer.ibm.com/answers/smart-spaces/17/internet-of-things.html){: new_window}。
{: important}

{{site.data.keyword.iamshort}} 内置于 {{site.data.keyword.cloud_notm}} 中，用于对需要配置和管理其 {{site.data.keyword.IBM_notm}} 服务的管理用户和开发者用户进行认证和授权。需要访问 {{site.data.keyword.iot_short_notm}} 仪表板的用户使用 {{site.data.keyword.iamshort}} 进行认证。{{site.data.keyword.iamshort}} 的身份源可以是已注册的 IBM 标识用户，也可以是客户的支持 SAML 的目录服务。  

{{site.data.keyword.iot_short_notm}} 还支持通过 {{site.data.keyword.appid_short_notm}} 对用户进行认证。{{site.data.keyword.appid_short_notm}} 用于对需要访问在 {{site.data.keyword.cloud_notm}} 中托管的应用程序的用户进行认证。{{site.data.keyword.appid_short_notm}} 用户通常并不在云服务上执行管理或开发活动。有关更多信息，请参阅 [{{site.data.keyword.appid_short_notm}} Authentication for Watson IoT Platform ![外部链接图标](../../../../icons/launch-glyph.svg "外部链接图标")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/platform/app_id.html#app_id){: new_window}。

通过 IAM，用户能够获取 IAM OAuth 令牌并将其用于对 API 调用进行认证。例如，安装了 {{site.data.keyword.containershort_notm}} CLI 的用户可能会使用以下命令：

`bx iam oauth-tokens`

此命令会返回已登录用户的 IAM 令牌，格式如下：

`IAM Token: Bearer <some token>`

用户还可以使用 IAM 令牌端点来登录并检索其 IAM 令牌，如以下示例所示：`curl -s 'https://iam.cloud.ibm.com/identity/token?grant_type=urn:ibm:params:oauth:grant-type:apikey&response_type=cloud_iam&apikey=<apikey>' -H'Content-Type:x-www-form-urlencoded' -XPOST`

此 API 示例使用 IAM API 密钥来请求 IAM 令牌，并返回 `Bearer <token>`。

然后，用户调用 {{site.data.keyword.iot_short_notm}} API 时，可以在其 API 调用中提供授权头 `Authorization: Bearer<token>`。

## 生成 IAM 令牌
{: #iam_generate}

您可以选择如何自动创建 IAM 令牌，具体取决于您向 {{site.data.keyword.cloud_notm}} 认证的方式以及使用的 {{site.data.keyword.cloud_notm}} 标识的类型。

如果使用的是未联合标识，那么可以选择下列其中一个选项来创建 IAM 令牌：
 - **{{site.data.keyword.cloud_notm}} 用户名和密码：**您可以创建令牌以完全自动化 IAM 访问令牌的创建。
 - **生成 {{site.data.keyword.cloud_notm}} API 密钥：**使用 {{site.data.keyword.cloud_notm}} API 密钥，这些密钥依赖于为其生成这些密钥的 {{site.data.keyword.cloud_notm}} 帐户。您不能将 {{site.data.keyword.cloud_notm}} API 密钥与同一 IAM 令牌中的不同帐户标识组合使用。要访问使用非 {{site.data.keyword.cloud_notm}} API 密钥所基于的帐户创建的集群，必须登录该帐户以生成新的 API 密钥。

如果使用的是联合标识，那么可以选择下列其中一个选项来创建 IAM 令牌：
 - **生成 {{site.data.keyword.cloud_notm}} API 密钥：** {{site.data.keyword.cloud_notm}} API 密钥依赖于为其生成这些密钥的 {{site.data.keyword.cloud_notm}} 帐户。您不能将 {{site.data.keyword.cloud_notm}} API 密钥与同一 IAM 令牌中的不同帐户标识组合使用。要访问使用非 {{site.data.keyword.cloud_notm}} API 密钥所基于的帐户创建的集群，必须登录该帐户以生成新的 API 密钥。
 - **使用一次性通行码：**如果使用一次性通行码向 {{site.data.keyword.cloud_notm}} 进行认证，那么无法完全自动创建 IAM 令牌，因为检索一次性密码需要与 Web 浏览器进行手动交互。要完全自动化 IAM 令牌的创建，必须改为创建 {{site.data.keyword.cloud_notm}} API 密钥。

创建访问令牌时，请求中包含的主体信息会根据您使用的 {{site.data.keyword.cloud_notm}} 认证方法而变化。替换以下值：
- `<my_username>` = 您的 {{site.data.keyword.cloud_notm}} 用户名。
- `<my_password>` = 您的 {{site.data.keyword.cloud_notm}} 密码。
- `<my_api_key>` = 您的 {{site.data.keyword.cloud_notm}} API 密钥。
- `<my_passcode>` = 您的 {{site.data.keyword.cloud_notm}} 一次性通行码。运行 `bx login --sso`，并按照 CLI 输出中的指示信息，使用 Web 浏览器检索一次性密码。

示例：`POST https://iam.<region>.cloud.ibm.com/identity/token`

要指定 {{site.data.keyword.cloud_notm}} 区域，请查看 API 端点中使用的区域缩写。请参阅 [{{site.data.keyword.cloud_notm}} 区域 API 端点 ![外部链接图标](../../../../icons/launch-glyph.svg)](https://cloud.ibm.com/docs/containers/cs_regions.html#bluemix_regions){: new_window} 以获取更多信息。

输入参数|值
---------------- | -----------
头| Content-Type: application/x-www-form-urlencoded<br>Authorization: Basic Xng7Png=<br>注：为您提供了 `Xng7Png=`，这是对用户名 bx 和密码 bx 的 URL 编码的授权。
{{site.data.keyword.cloud_notm}} 用户名和密码的主体|	grant_type: password<br>response_type: cloud_iam, uaa<br>username: `<my_username>`<br>password: `<my_password>`<br>uaa_client_id: cf<br>uaa_client_secret:<br>注：添加不指定值的 uaa_client_secret 键。
{{site.data.keyword.cloud_notm}} API 密钥的主体|	grant_type: urn:ibm:params:oauth:grant-type:apikey<br>response_type: cloud_iam<br>uaa<br>apikey: `<my_api_key>`<br>uaa_client_id: cf<br>uaa_client_secret:<br>注：添加不指定值的 uaa_client_secret 键。
{{site.data.keyword.cloud_notm}} 一次性通行码的主体|	grant_type: urn:ibm:params:oauth:grant-type:passcode<br>response_type: cloud_iam, uaa<br>passcode: `<my_passcode>`<br>uaa_client_id: cf<br>uaa_client_secret:<br>注：添加不指定值的 uaa_client_secret 键。

示例 API 输出：

```
{
"access_token": "<iam_token>",
"refresh_token": "<iam_refresh_token>",
"uaa_token": "<uaa_token>",
"uaa_refresh_token": "<uaa_refresh_token>",
"token_type": "Bearer",
"expires_in": 3600,
"expiration": 1493747503
}
```
您可以在 API 输出的 **access_token** 字段中找到 IAM 令牌。

以下示例显示了如何在调用 API 时使用 IAM 令牌。

```
GET https://org.domain/api/v0002/bulk/devices
```

输入参数|	值
----------------- | -----------
头|	Content-Type: application/json<br>Authorization: bearer `<iam_token>`
