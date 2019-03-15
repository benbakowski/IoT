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


# 模拟设备数据
{: #sim_device_data}

<p>该 {{site.data.keyword.Bluemix}} 文档集合与 {{site.data.keyword.iot_full}} 轻量价格套餐有关，并且包含基本入门信息、API 参考和一般故障诊断信息。
有关完整的 {{site.data.keyword.iot_short_notm}} 功能文档，请参阅 IBM Knowledge Center 上的 [{{site.data.keyword.iot_short_notm}} 产品文档 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/overview/overview.html)。可在 [{{site.data.keyword.iot_short_notm}} 服务套餐](/docs/IoT/plans_overview.html#plans_overview)中找到有关各种套餐的更多信息。
</p>
{: important}

通过使用 {{site.data.keyword.iot_full}} 设备模拟器，您可以设置设备的模拟事件。您可以使用模拟事件数据来了解、测试和演示功能全面的 {{site.data.keyword.iot_short_notm}} 功能。
{: shortdesc}

您可以使用现有设备类型和设备，并且模拟器使您能够为现有类型生成新设备。您可以配置每个设备的事件详细信息，或设置应用于所有设备的缺省配置。您可以导出模拟事件配置，以便可以对其复用或共享，从而设置其他模拟。

要模拟设备数据：

1. 登录到 {{site.data.keyword.iot_short_notm}}。
2. 从主导航窗格中，选择**设置**。
3. 在**数据和设备**部分中，激活设备模拟器。
4. 从主导航窗格中，选择**设备**。屏幕右下角的消息指示没有正在运行的模拟。
5. 单击“0 个模拟在运行”消息。
6. 在**模拟**弹出窗口中，单击**创建模拟**。
7. 选择想要为其模拟数据的现有设备类型，或者通过输入设备类型名称来创建新设备类型。
8. 单击**导入/导出模拟**以使用现有配置，或者手动配置设备类型的模拟详细信息：
   1. 单击 **+ 新建事件类型**以向设备类型添加事件类型。
   2. 输入事件类型的名称。
   3. 在**调度**下，设置事件的频率。
   3. 以 JSON 格式编辑事件类型详细信息并保存更新的事件类型。

   <p> 配置事件时，可以使用以下特殊变量：  
        - `range`：此变量将替换为两个提供的值之间的随机数，例如：`{"random": range(300, 100)}`  
        - `$counter`：此变量将替换为当前类型的模拟器中添加的设备数，例如：`{"total": $counter}`  
        - `increment`：此变量指示起始数量以及用于增加的增量，例如：`{"myNumber": increment(10, 1)}`。在此情况下，`myNumber` 从 10 开始，并且每次发送有效内容时增加 1（10、11、12，以此类推）。</p>
   {: tip}

9. 选择已注册的设备进行模拟，或者通过输入设备名称来创建新设备。
10. 要创建更多模拟，请单击**新建模拟**，并针对要应用定制设置的每个设备重复配置步骤。屏幕右下方的消息显示活动模拟的数量。
11. **可选：**为设备配置模拟后，请导出模拟详细信息，以便可以复用或共享这些模拟详细信息：
    1. 在**模拟**弹出窗口中，单击**导入/导出**。
    2. 选择**导出**选项卡。
    3. 将模拟详细信息复制到剪贴板或将其下载到 JSON 文件中。
12. 在**设备**页面上，浏览至其中一个模拟设备，然后选择**最近事件**选项卡，以验证模拟事件是否正在工作。
