---

copyright:
  years: 2016, 2019
lastupdated: "2019-04-05"

keywords: Lite plan, migrate, Watson IoT Platform

subcollection: iot-platform

---

{:new_window: target="\_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}
{:important: .important}

# 将 {{site.data.keyword.iot_short_notm}} 轻量套餐迁移至 {{site.data.keyword.iot_short_notm}} 非生产或生产套餐
{: #org_migration}

<p>该 {{site.data.keyword.cloud}} 文档集合与 {{site.data.keyword.iot_full}} 轻量价格套餐有关，并且包含基本入门信息、API 参考和一般故障诊断信息。
有关完整的 {{site.data.keyword.iot_short_notm}} 功能文档，请参阅 {{site.data.keyword.IBM}} Knowledge Center 上的 [{{site.data.keyword.iot_short_notm}} 产品文档 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/overview/overview.html)。可在 [{{site.data.keyword.iot_short_notm}} 服务套餐](/docs/services/IoT?topic=iot-platform-plans_overview#plans_overview)中找到有关各种套餐的更多信息。
</p>
{: important}

在“试用”Watson IoT Platform 轻量套餐并清楚了解它适合您的 IoT 环境的程度之后，您可以升级至 [Watson IoT Platform 非生产套餐或一个生产套餐 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/overview/overview.html){: new_window}。
{:shortdesc}

**注：**本文档仅适用于拥有轻量实例的用户。如果先前使用标准或高级安全套餐创建了 IoT Platform 实例，{{site.data.keyword.IBM}} 将与您一起将现有 {{site.data.keyword.iot_short_notm}} 实例迁移到新的非生产或生产套餐。

## 迁移过程概述
{: #org_migration_overview}

通过迁移至 {{site.data.keyword.iot_short_notm}}，即可除去轻量套餐中 500 个设备和每月数据消耗量的限制。

{{site.data.keyword.iot_short_notm}} 套餐包含以下附加组件以支持端到端 IoT 应用程序体系结构：

- {{site.data.keyword.messagehub}} - Kafka 流式平台的 {{site.data.keyword.IBM_notm}} 托管版本，可由应用程序用于接收 IoT 数据。
- {{site.data.keyword.dashdbshort}}，用于分析数据存储。
- {{site.data.keyword.cloudantfull}} 数据库，用于时间序列数据。
- {{site.data.keyword.cos_full}}，用于长期数据保留。

本文档描述您可能想要从现有轻量实例迁移至完整版本的数据的类型。

**注：**通常，最简单的方法是从头开始设置 {{site.data.keyword.iot_short_notm}} 非生产或生产环境，因为其中包含除 {{site.data.keyword.iot_short_notm}} 轻量服务之外的组件和功能部件。另外，在轻量版本中创建用于测试的设备和用户很可能与用于生产的不同。

但是，如果想要传输某些现有轻量设置，以下部分指导您完成此过程。

有关 [{{site.data.keyword.iot_short_notm}} APIs]/docs/services/IoT?topic=iot-platform-api_overview#api_overview) 的文档提供有关如何调用 API 及其完整参数集的指示信息。


## 开始之前
{: #org_migration_byb}

要能够启动迁移过程，必须先购买 {{site.data.keyword.iot_short_notm}}（生产或非生产）。购买后，{{site.data.keyword.IBM_notm}} 运营团队将为您供应新的 {{site.data.keyword.iot_short_notm}} 实例。这将包括新的六字符字母数字组织标识。


## 迁移用户
{: #user_migration}

[用户管理 API![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://docs.internetofthings.ibmcloud.com/apis/swagger/v0002/security.html#!/Authorization_-_User_Management){: new_window} 提供 {{site.data.keyword.iot_short_notm}} 用户的批量导出和导入，并且可用于导出和导入想要在新组织中保留的用户。

1. 从轻量组织导出用户。  
使用 `GET /authorization/users` 命令以将轻量帐户组织中的所有用户导出为 JSON 对象。
2. 清除用户列表。  
如果需要，请编辑 JSON 结构以除去不想迁移到新组织的任何用户。
3. 将这些用户导入到新组织。  
使用 `POST /authorization/users/multiple` 命令以将编辑的用户 JSON 列表导入到新组织。

现在，这些用户有权访问新组织，该组织将在 {{site.data.keyword.iot_short_notm}} 仪表板上的组织选择器中显示。

##  迁移设备  
{: #device_migration}

可通过以下步骤完成设备迁移：  
1. 将想要保留的设备类型迁移到新组织。  
2. 将设备自身迁移到新组织。  
3. 将设备用于连接到 {{site.data.keyword.cloud_notm}} 的主机名更新为以新的组织标识开头。
4. 迁移在轻量平台中创建的任何数据管理信息。   
这可能包括设备物理和逻辑接口、事物和规则。

<p>可使用以下 API 批量迁移设备类型和设备：
<table>
<tr>
<th> API 文档</th>
<th> 导出 API</th>
<th> 导入 API</th>
</tr>
<tr>
<td> [设备类型 API ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://docs.internetofthings.ibmcloud.com/apis/swagger/v0002/org-admin.html) </td>
<td> `GET /device/types` </td>
<td> `POST /device/types` </td>
</tr>
<tr>
<td>  [设备 API ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://docs.internetofthings.ibmcloud.com/apis/swagger/v0002/org-admin.html#!/Device_Bulk_Configuration) </td>
<td> `GET /bulk/devices` </td>
<td>  `POST /bulk/devices/add`</td>
</tr>
</table>
</p>
{: tip}


**重要信息：**{{site.data.keyword.iot_short_notm}} 不存储设备认证令牌，而只存储这些令牌的加密盐版本。因此，`GET /bulk/devices` 调用无法返回存储的设备的认证令牌。如果您有设备认证令牌的记录，那么可先将这些令牌添加到 JSON 对象，然后再执行批量装入。否则，必须针对每个设备生成新的设备认证令牌，并将它们复制到设备。  

如果是使用设备端证书来认证设备，而不是使用认证令牌，那么无需执行此操作。但是，如果是使用设备端证书，那么必须将用于对其签名的证书上传到新组织。


## 更新设备
{: #update_devices}

在新组织中注册设备时，必须更新每个现有设备上存在的配置或代码以使用新组织的主机名。

对于 MQTT 和 HTTP 消息传递客户机，请使用以下主机名：  
`<orgId>.messaging.internetofthings.ibmcloud.com`

将 REST API 客户机指向以下主机名：  
`<orgId>.internetofthings.ibmcloud.com`

**重要信息：**如果针对设备生成了新的认证令牌，那么必须将这些令牌复制到每个设备。


## 设备管理迁移
{: #device_management}

[数据管理 API ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://docs.internetofthings.ibmcloud.com/apis/swagger/v0002/state-mgmt.html){: new_window} 包含用于导出和导入设备物理和逻辑接口、事物定义和规则的 API。

**重要信息：**{{site.data.keyword.iot_short_notm}} 当前不支持用于数据并入的资产双联概念。

## 板和卡
{: #boards_cards}

{{site.data.keyword.iot_short_notm}} 不包含用于导入和导出板和卡的定义和定制内容的 API。您必须在新组织中手动重新创建这些 API。

## 启用任何必需的扩展
{: #extensions}

您必须在新组织中重新创建在轻量平台中启用的任何扩展，例如，指向 {{site.data.keyword.messagehub}}、{{site.data.keyword.cloudant_short_notm}} 和 Jasper 的链接。

## 迁移应用程序
{: #application_migration}

如果您开发的应用程序调用通过 {{site.data.keyword.iot_short_notm}} 轻量服务提供的 API 来发送或接收数据或者管理服务等，那么您必须更新这些 API 以使用新的 {{site.data.keyword.iot_short_notm}} 生产或非生产实例。这也适用于您可能在使用的任何 Node-RED 流程。
迁移涉及：
- 更新应用程序以使用新的六字符组织标识。
- 更新应用程序以使用您为新服务实例创建的 API 密钥和令牌凭证。

**重要信息：**如果已在使用 Cloud Foundry 绑定来将组织标识和凭证传递到应用程序，那么必须使用不同的机制，因为未供应新的 {{site.data.keyword.iot_short_notm}} 实例以在 Cloud Foundry 空间中运行。

### 生成 API 连接凭证

要遵循的迁移过程依赖于应用程序的性质。通常，对于所有情况，第一步是获取 API 密钥和认证令牌以供应用程序使用。

1. 登录到新的 {{site.data.keyword.iot_short_notm}} 服务的顶级仪表板。
2. 选择**使用情况**选项卡。
3. 单击**查看详细信息**链接以显示 {{site.data.keyword.iot_short_notm}} 服务信息。  
将显示以下信息：
   - 六字符组织标识
   - API 密钥和令牌。  
您应该为每个应用程序生成新的 API 密钥，而不是使用此处显示的 API 密钥。这将允许您为每个应用程序设置相应的许可权。
   - 主机 URL。
4. 为应用程序创建 API 密钥和认证令牌组合。  
配置应用程序以连接到组织时，您将需要这些信息。   
   1.  单击`启动`。  
这将带您进入底层服务仪表板，您已使用该仪表板来管理 {{site.data.keyword.iot_short_notm}} 轻量服务。
   2. 选择**应用程序**。
   3. 单击**生成 API 密钥**
   4. 复制列出的 API 密钥和认证令牌值。
   5. 选择适合您的应用程序的角色。   
   6. 添加注释，以便您可以轻松识别此 API 密钥和认证令牌组合。
   7. 单击**生成**。
   8. **重要信息：**生成认证令牌的本地副本。关闭窗口后无法重新创建令牌。


### 更新 Node-RED 应用程序
您将需要配置 Node-RED 节点以连接到新的 {{site.data.keyword.iot_short_notm}} 实例。您的 `ibmiot` 节点将不再能够使用 `BluemixService` 认证选项，因此需要改为选择 `API 密钥`选项。
1. 打开 `ibmiot` 节点以进行编辑。
2. 在节点属性下，选择 **API 密钥**。
3. 对于“API 密钥”字段，单击编辑图标，然后输入在先前步骤中保存的“API 密钥”和“认证令牌”。
4. 保存更改并重新部署 Node-RED 流程。

### 更新不使用 Cloud Foundry 绑定的应用程序
确定应用程序存储组织标识、API 密钥和认证令牌的位置，并将它们替换为先前保存的值。

如果应用程序使用其中一个 {{site.data.keyword.iot_short_notm}} SDK，那么这些值可能保存在“属性”文件中。
{: tip}

### 更新使用 Cloud Foundry 绑定的应用程序

{{site.data.keyword.cloud_notm}} 提供一个机制以将 Cloud Foundry 应用程序绑定到一个或多个 Cloud Foundry 服务。可以使用 {{site.data.keyword.cloud_notm}} CLI 建立绑定，也可以通过在 {{site.data.keyword.cloud_notm}} 仪表板中的应用程序和服务之间创建`连接`来建立绑定。

在将应用程序绑定到服务时，会将服务“API 密钥”和“认证令牌”凭证复制到 `VCAP_SERVICES` 环境变量，应用程序可从中检索这些凭证。

**重要信息：**此绑定机制无法用于新的 {{site.data.keyword.iot_short_notm}} 服务。您必须在应用程序中找到从 `VCAP_SERVICES` 进行读取的代码，并将其替换为从现在用于存储 API 密钥和认证令牌的位置读取值的代码。要完成更新，必须重新构建并重新部署应用程序。
