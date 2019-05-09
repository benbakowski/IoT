---

copyright:
  years: 2016, 2019
lastupdated: "2019-04-16"

keywords: IoT device, Watson IoT Platform, Watson IoT Platform service plans

subcollection: iot-platform

---

{:new_window: target="\_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}
{:important: .important}


# 入门教程
{: #getting-started}

<p>该 {{site.data.keyword.cloud}} 文档集合与 {{site.data.keyword.iot_full}} 轻量价格套餐有关，并且包含基本入门信息、API 参考和一般故障诊断信息。
有关完整的 {{site.data.keyword.iot_short_notm}} 功能文档，请参阅 IBM Knowledge Center 上的 [{{site.data.keyword.iot_short_notm}} 产品文档 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/overview/overview.html)。可在 [{{site.data.keyword.iot_short_notm}} 服务套餐](/docs/services/IoT?topic=iot-platform-plans_overview#plans_overview)中找到有关各种套餐的更多信息。
</p>
{: important}

在此 {{site.data.keyword.iot_short_notm}} 入门教程中，我们将 IoT 设备连接到 {{site.data.keyword.iot_short_notm}}。
{:shortdesc}

## 关于此任务
{: #about .sectiontitle}  

必须先将 IoT 设备连接到 {{site.data.keyword.iot_short_notm}}，然后才能开始从这些设备接收数据。将设备连接到 {{site.data.keyword.iot_short_notm}} 的过程包括向 {{site.data.keyword.iot_short_notm}} 注册该设备，然后使用注册信息来配置该设备以连接到 {{site.data.keyword.iot_short_notm}}。


## 开始之前
{: #byb .sectiontitle}  

要能够开始使用 {{site.data.keyword.iot_short_notm}}，必须先拥有以下项：  
* [{{site.data.keyword.cloud}} 帐户 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://cloud.ibm.com/registration/){: new_window}。
* {{site.data.keyword.iot_short_notm}} 实例。  
您可以直接从 [{{site.data.keyword.cloud_notm}} 服务目录中的 {{site.data.keyword.iot_short_notm}} 页面 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://{DomainName}/catalog/services/internet-of-things-platform/){:new_window} 创建 {{site.data.keyword.iot_short_notm}} 实例。  
* 满足以下需求的设备：  
  *	您的设备必须能够使用 HTTP 或 MQTT 协议进行通信。
  * 设备消息必须符合 {{site.data.keyword.iot_short_notm}} 消息有效内容需求。  
有关更多信息，请参阅 [在 {{site.data.keyword.iot_short_notm}} 上开发设备 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/platform/devices/device_dev_index.html){: new_window}。

根据具体情况研究以下选项：

 |  |已部署此服务|未部署此服务
 | -------------| ------------- | -------------
  |**我有要连接的设备**|请遵循本主题中概述的过程。|了解[使用 {{site.data.keyword.iot_short_notm}} ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](http://discover-iot.eu-gb.mybluemix.net/?cm_mc_uid=44491599487314618721024&cm_mc_sid_50200000=1462798151#/play){:new_window} 中的设备连接。
  |**我没有要连接的设备**| [模拟设备数据](/docs/services/IoT?topic=iot-platform-sim_device_data#sim_device_data)或者[连接智能手机 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](http://discover-iot.eu-gb.mybluemix.net/?cm_mc_uid=44491599487314618721024&cm_mc_sid_50200000=1462798151#/play/device/smartphone){:new_window}。|开始使用 [{{site.data.keyword.iot_short_notm}} 入门模板](https://cloud.ibm.com/docs/IoT-starter?topic=iot-starter-gettingstartedtemplate#gettingstartedtemplate){:new_window}。



## 步骤 1：注册设备
{: #step1 .sectiontitle}  
注册设备包括将设备归类为某种设备类型、为设备命名，以及提供设备信息。然后，提供连接令牌，或接受 {{site.data.keyword.iot_short_notm}} 生成的令牌。

**提示：**您可以从 [{{site.data.keyword.iot_short_notm}} 仪表板 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://internetofthings.ibmcloud.com){: new_window} 一次注册一个设备，也可使用 [{{site.data.keyword.iot_short_notm}} API ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://docs.internetofthings.ibmcloud.com/apis/swagger/v0002/org-admin.html#!/Device_Bulk_Configuration/post_bulk_devices_add){: new_window} 添加多个设备。

要从 {{site.data.keyword.iot_short_notm}} 仪表板添加设备，请执行以下操作：
1. 在 {{site.data.keyword.cloud_notm}} 控制台中，单击 {{site.data.keyword.iot_short_notm}} 服务详细信息页面上的**启动**。

    此时，{{site.data.keyword.iot_short_notm}} Web 控制台将在新浏览器选项卡中打开，URL 如下：

    ```
 https://org_id.internetofthings.ibmcloud.com/dashboard/#/overview
 ```

    其中，*org_id* 是 {{site.data.keyword.iot_short_notm}} 组织的标识。

2. 在“概述”仪表板中，从菜单窗格选择**设备**，然后单击**添加设备**。

3. 为要添加的设备创建设备类型。

    连接到 {{site.data.keyword.iot_short_notm}} 的每个设备都必须与一种设备类型相关联。设备类型是共享公共特征的设备组。

    1. 单击**创建设备类型**。
    2. 输入设备名称（如 `my_device_type`）以及设备类型描述。

        > **注：**设备类型名称不得超过 36 个字符，仅可包含字母数字字符（a-z、A-Z、0-9）和以下任何字符：`_`、`.` 和 `-`。

    3. 可选：输入设备类型属性和元数据。

        您可以稍后添加和编辑属性及元数据。
        {: tip}

4. 单击**下一步**以开始添加具有所选设备类型的设备的过程。

5. 输入设备标识，例如 `my_first_device`。

    设备标识用于在 {{site.data.keyword.iot_short_notm}} 仪表板中标识设备，也是将设备连接到 {{site.data.keyword.iot_short_notm}} 时必需的参数。

    > **注：**设备类型名称不得超过 36 个字符，仅可包含字母数字字符（a-z、A-Z、0-9）和以下任何字符：`_`、`.` 和 `-`。

    对于连接网络的设备，设备标识可以是不带任何分隔冒号的设备 MAC 地址。

5. 单击**下一步**以完成该过程。

6. 提供认证令牌或接受自动生成的令牌。如果选择创建您自己的令牌，请确保令牌的长度在 8 到 36 个字符之间，并且仅包含字母数字字符和以下字符：`_`、`.`、`!`、`&`、`@`、`?`、`\*`、`+`、`(`、`)` 和 `-`。

    此令牌不得包含重复的字符序列、字典单词、用户名或其他预定义序列。

7. 验证摘要信息是否正确，然后单击**添加**以添加连接。

8. 在设备信息页面中，复制并保存以下详细信息：

    * 组织标识
    * 设备类型
    * 设备标识
    * 认证方法
    * 认证令牌

    您将需要组织标识、设备类型、设备标识和认证令牌来配置设备以连接到 {{site.data.keyword.iot_short_notm}}。

## 步骤 2：将设备连接到 {{site.data.keyword.iot_short_notm}}
{: #step2 .sectiontitle}  

向 {{site.data.keyword.iot_short_notm}} 注册设备后，可使用注册信息来连接该设备并开始接收设备数据。

**提示：**{{site.data.keyword.IBM_notm}}.com 上的[设备连接诀窍 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://developer.ibm.com/recipes/tutorials/category/internet-of-things-iot/){: new_window} 中提供了针对一些常用设备的连接诀窍。

要将设备连接到 {{site.data.keyword.iot_short_notm}}：
1. 设置设备以实现 MQTT 消息传递，并使用组织标识、设备类型、设备标识和认证令牌进行认证。

2. 通过使用 MQTT 协议将设备消息发送到 {{site.data.keyword.iot_short_notm}} 组织。

    连接设备时需要以下信息：

    * URL：*org_id*.messaging.internetofthings.ibmcloud.com

      其中，*org_id* 是 {{site.data.keyword.iot_short_notm}} 组织的标识。

    * 端口：
      * 1883
      * 8883（已加密）
      * 443 (websocket)
    * 设备标识：d:_org_id:device_type:device_id_
    * 用户名：use-token-auth
    * 密码：_认证令牌_
    * 事件主题格式：iot-2/evt/_event_id/fmt/format_string_

      其中，_event_id_ 指定 {{site.data.keyword.iot_short_notm}} 中显示的事件名称，_format_string_ 是事件的格式（例如，JSON）。

    * 消息格式：JSON

  有关更多信息，请参阅[设备的 MQTT 连接 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/platform/devices/mqtt.html){:new_window}。


## 后续步骤  
{: #related .sectiontitle}

通过创建并连接您自己的应用程序以使用设备数据，从而扩展数据分析功能。
- 有关如何将特定设备类型连接到 {{site.data.keyword.iot_short_notm}} 的更多信息，请参阅 [developerWorks 诀窍 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://developer.ibm.com/recipes/tutorials/category/internet-of-things-iot/){:new_window}。
- 检查[客户机库 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/platform/iot_platform_client_lib.html){:new_window} 以获取工具来构建用于集成并连接设备和应用程序的代码。
- 探索 [{{site.data.keyword.iot_short_notm}} API 文档](/docs/services/IoT?topic=iot-platform-api_overview#api_overview)。
- [连接 {{site.data.keyword.cloudantfull}} 服务 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/platform/cloudant_connector.html){:new_window} 到 {{site.data.keyword.iot_short_notm}} 以存储历史设备数据。
- 要利用完整的 [{{site.data.keyword.iot_short_notm}} 功能集 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/overview/overview.html){:new_window}，您可以购买一个 Connection and Analytics Service 套餐，然后迁移现有环境。

要迁移套餐，请联系 {{site.data.keyword.IBM}} 代表或发出支持凭单。

{{site.data.keyword.IBM_notm}} Knowledge Center 上的 {{site.data.keyword.iot_short_notm}} 产品文档中还提供了一组更详细的入门指南和样本应用程序，用于逐步完成使用 {{site.data.keyword.iot_short_notm}} 开发生产就绪型端到端 IoT 原型系统的基本过程。如果您是使用 {{site.data.keyword.iot_short_notm}} 的新开发者，请使用[入门指南 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/platform/getting_started/getting-started-iot-overview.html#getting-started){:new_window} 部分中的逐步过程。
