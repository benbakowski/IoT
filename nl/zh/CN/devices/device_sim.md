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


# 模拟设备数据
{: #sim_device_data}

<p>该 {{site.data.keyword.cloud}} 文档集合与 {{site.data.keyword.iot_full}} 轻量价格套餐有关，并且包含基本入门信息、API 参考和一般故障诊断信息。
有关完整的 {{site.data.keyword.iot_short_notm}} 功能文档，请参阅 IBM Knowledge Center 上的 [{{site.data.keyword.iot_short_notm}} 产品文档 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/overview/overview.html)。可在 [{{site.data.keyword.iot_short_notm}} 服务套餐](/docs/services/IoT?topic=iot-platform-plans_overview#plans_overview)中找到有关各种套餐的更多信息。
</p>
{: important}

使用 {{site.data.keyword.iot_full}} 设备模拟器，设置模拟事件以便设备了解、测试和演示完全运行的 {{site.data.keyword.iot_short_notm}} 功能，而无需注册和连接实际设备。
{: shortdesc}

通过使用设备模拟器，可为现有设备类型创建模拟设备，或者创建新设备类型和设备。每个模拟设备都可以使用唯一的事件详细信息，但您也可以创建应用于所有设备的缺省配置。

## 开始之前
{: #byb-simulation .sectiontitle}
为您的用户标识启用设备模拟。
1. 登录到 {{site.data.keyword.iot_short_notm}}。
2. 从主导航窗格中，选择**设置**。
3. 在**数据和设备**部分中，激活设备模拟器。

如果为您的用户标识启用了设备模拟，那么登录 {{site.data.keyword.iot_short_notm}} 仪表板时，将自动启动所有已启用的模拟设备。

## 模拟设备
{: #process-simulation .sectiontitle}
激活后，设备模拟器在所有仪表板页面上都可用。屏幕右下角的消息指示正在运行的模拟次数。

**重要：**您为用户标识定义的模拟设备和设备类型可供 {{site.data.keyword.iot_short_notm}} 组织的其他用户使用。但是，要为设备生成模拟数据，必须在活动用户会话中登录到 {{site.data.keyword.iot_short_notm}} 仪表板。

要模拟设备数据：
1. 从 {{site.data.keyword.iot_short_notm}} 仪表板，单击“0 个模拟在运行”消息。
3. 在打开的**模拟**配置窗口中，单击**创建模拟**。
4. 配置模拟详细信息。  
单击**导入/导出模拟**以导入[现有配置](#reuse)，或者手动配置详细信息：
   1. 选择想要为其模拟数据的现有设备类型，或者通过输入设备类型名称来创建新设备类型。
   2. 修改事件类型的缺省名称。
   3. 在**调度**下，设置事件的频率。
   4. 编辑事件有效内容。  
   通过添加属性及其对应值来编辑样本 JSON 有效内容，或使用[函数](#functions)添加动态生成的数据点。  
  您还可以上传 [CSV 事件有效内容文件](#csv)以设置有效内容。  
   {: tip}
5. 单击**新建事件类型**，为设备类型添加和配置更多事件类型。
5. 启用**将事件保存为历史数据**，以使您的模拟设备状态数据可供以后访问。  
启用历史数据后，会创建 {{site.data.keyword.iot_short_notm}} [数据管理 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/platform/GA_information_management/ga_im_definitions.html){: new_window} 组件，可从关联逻辑界面访问模拟设备状态。  
**重要：**启用设备类型以保存历史数据后，无法添加或除去事件类型，也无法修改事件有效内容中存在的字段。
5. 单击**保存**以创建设备类型。  
现在，您已准备好创建一个或多个模拟设备。
6. 单击**创建模拟设备**以创建设备并开始发送数据。  
**提示：**要创建多个设备，请单击 **1 x** 并选择要创建的设备数。  
7. 要创建更多模拟，请单击**新建模拟**，并针对要应用定制设置的每个设备重复配置步骤。   
屏幕右下角的消息显示活动模拟的数量。
8. 在**设备**页面上，浏览至其中一个模拟设备，然后选择**最近事件**选项卡，以验证模拟事件是否正在工作。

您可以[导出模拟的事件配置](#reuse)以进行复用或共享。

## 事件类型函数
{: #functions .sectiontitle}

您可以使用多个特殊函数，为事件类型创建动态数据。

函数 | 用法 | 示例  
:--- | :---  | :--  
`random(lower, upper)`  | 生成指定范围内的随机数。 | `{"random": random(0, 100)}`  
`$counter` | 显示当前类型的模拟设备数。 | `{"total": $counter}`  
`increment(start, increment)` | 指定开始值及其增量值。 |`{"myNumber": increment(10, 1)}` </br> 在此示例中，`myNumber` 从 10 开始，每次发送有效内容时增加 1。


## CSV 事件有效内容文件
{: #csv .sectiontitle}

如果要为特定场景创建受控事件数据，那么可在 CSV 输入文件中设置数据流。

### 要求
CSV 文件必须满足以下要求：
- 每个值为有效的 [JSON 原语 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://json.org){: new_window}，除非另有说明：
  - 字符串：   
  示例：“Hello world”
  - 数字：  
  示例：0、0.1、-22、-2.43
  - 布尔值：  
  true 或 false
  - null：  
  null
  - **不支持：**
    - 对象  
    示例：{}
    - 数组  
    示例：[]
- 值必须用逗号分隔。
- 必须使用换行符 (`\n`) 来分隔行。
- 标题行只能包含字符串值。


### 样本 CSV 文件
```
"temperature", "confidence","status"
1, 0.1, "normal"
2, 0.2, "normal"
3, 0.3, "error"
4, 0.4, "normal"
```

第一行或“标题行”确定所有生成的设备 JSON 事件对象中设备 JSON 中包含的属性。
后续每行或“数据行”在每个生成的设备 JSON 事件对象中设置这些属性的值。

**提示：**导入 CSV 文件时，可选择**从文件循环模拟数据**，以按顺序循环数据行，从而实现连续数据馈送。如果未设置此切换，那么 CSV 中的每个数据行将按计划设置的频率发送一次。

样本 CSV 文件会生成以下类型的事件有效内容：
```JSON
{
  "temperature": 1,
  "confidence": 0.1,
  "status": "normal"
}
```

## 共享和复用模拟
{: #reuse .sectiontitle}

您可以导出模拟详细信息以进行复用或共享：
1. 在**模拟**窗口中，单击**导入/导出**。
2. 选择**导出**选项卡。
3. 将模拟详细信息复制到剪贴板或将其下载到 JSON 文件中。
