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

# 管理用户访问权
{: #managing-user-access}

<p>该 {{site.data.keyword.Bluemix}} 文档集合与 {{site.data.keyword.iot_full}} 轻量价格套餐有关，并且包含基本入门信息、API 参考和一般故障诊断信息。
有关完整的 {{site.data.keyword.iot_short_notm}} 功能文档，请参阅 IBM Knowledge Center 上的 [{{site.data.keyword.iot_short_notm}} 产品文档 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/overview/overview.html)。可在 [{{site.data.keyword.iot_short_notm}} 服务套餐](/docs/IoT/plans_overview.html#plans_overview)中找到有关各种套餐的更多信息。
</p>
{: important}

在仪表板的“成员”页面中，可以控制和管理对 {{site.data.keyword.iot_full}} 组织的访问权。添加用户的方式包括添加、邀请或导入用户。还可以通过分配角色来向用户授予不同的访问级别。
{:shortdesc}

## 添加用户
{: #adding-new-users}

在仪表板的**成员**页面中，可以使用“添加”功能来添加单个成员。还可以使用“导入”功能来同时添加多个成员。

缺省情况下，成员帐户不会到期。向 {{site.data.keyword.iot_short_notm}} 组织添加用户时，可以选择为其帐户设置到期日期。

### 向 {{site.data.keyword.iot_short_notm}} 组织添加成员

要向组织添加成员，您将需要该成员的 IBM 标识。添加成员时，无需得到该成员的确认。

要向 {{site.data.keyword.iot_short_notm}} 组织添加单个成员，请执行以下操作：
1. 在 {{site.data.keyword.iot_short_notm}} 仪表板的导航栏中，单击**成员**。
2. 单击**添加成员**，然后选择**添加**选项卡。
3. 输入成员的 IBM 标识。
4. 为成员选择角色。
5. 可选：设置到期日期。
6. 单击**添加**。

要同时添加多个成员，必须上传 `.csv` 文件，此文件包含每个成员的 IBM 标识、角色和可选的到期日期。有关信息，请参阅[构造 CSV 文件](#constructing-your-csv)。
1. 在 {{site.data.keyword.iot_short_notm}} 仪表板的导航栏中，单击**成员**。
2. 单击**添加成员**，然后选择**导入**选项卡。
3. 浏览文件或将 `.csv` 文件拖入**上传 CSV** 窗口中。
4. 如果无法识别 CSV 文件中指定的角色，请选择要使用的缺省角色。
5. 将 CSV 文件中的列编号映射到相应的 IBM 标识、角色和可选的到期日期条目。
6. 选择相应的逗号或分号列分隔符，以匹配 `.csv` 文件中使用的分隔符。
7. 单击**导入**以导入 IBM 标识并创建成员。


### 构造 CSV 文件
{: #constructing-your-csv}

构造用于将成员导入组织中的 CSV 文件时，确保包含所用方法的必需信息。请使用逗号或分号来分隔列。  
**重要信息：**上传 CSV 文件时，确保在 **CSV 设置**下选择正确的列分隔符。

以逗号分隔的样本 CSV 文件：  
```
user1@sample.com,PD_DEVELOPER_USER,2018-03-13
user2@sample.com,PD_OPERATOR_USER,2018-03-13
user3@sample.com,PD_ADMIN_USER,2018-03-13
```
在使用以下列条目的位置：  
- 列 1：用户的电子邮件地址。  
如果您要添加成员，请确保使用对应于有效 IBM 标识的电子邮件地址。如果您要邀请成员，那么您可以使用任何有效电子邮件地址。
- 列 2：要分配给用户的角色。  
输入以下其中一个角色：
 - PD_ADMIN_USER
 - PD_OPERATOR_USER
 - PD_DEVELOPER_USER
 - PD_ANALYST_USER
 - PD_READER_USER  
有关用户角色的更多信息，请参阅[用户、应用程序和网关角色 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/platform/roles_index.html#user_roles){: new_window}。
- 列 3：对应于用户到期日期的 ISO 6801 日期（例如，`2018-03-13`）。

## 编辑用户
{: #editing-users}

可以对用户进行编辑，以更改其角色，添加、除去或更改访问权到期日期，或者添加或除去对组织的访问权。

1. 在 {{site.data.keyword.iot_short_notm}} 仪表板的导航栏中，单击**成员**。
2. 单击要编辑的用户旁的**编辑**图标。
3. 对用户进行所需的更改。
4. 单击**保存**。

## 阻止用户访问
{: #blocking-users}

可以阻止用户访问 {{site.data.keyword.iot_short_notm}} 组织，同时仍保留其组织成员资格。

1. 在 {{site.data.keyword.iot_short_notm}} 仪表板的导航栏中，单击**成员**。
2. 单击要阻止其访问 {{site.data.keyword.iot_short_notm}} 组织的用户旁的切换开关。

## 限制用户访问权
{: #limiting-users}

资源级别的访问控制使您能够限制对组织内设备的访问权。您可以使用资源组来指定每个用户或 API 密钥可管理的设备。有关如何配置资源级别访问控制的信息，请参阅[配置资源级别访问控制 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/platform/reference/rlac.html#configure_RLAC){: new_window}。

## 除去用户
{: #removing-users}

可以从 {{site.data.keyword.iot_short_notm}} 组织中完全除去用户。除去用户的操作不可撤销，要恢复已除去用户的访问权，必须将相应用户[添加到平台](#adding-new-users)。

1. 在 {{site.data.keyword.iot_short_notm}} 仪表板的导航栏中，单击**成员**。
2. 单击要除去的用户旁的**删除**图标。
3. 单击确认对话框中的**删除**。
