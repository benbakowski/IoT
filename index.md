---

copyright:
  years: 2016, 2018
lastupdated: "2018-05-08"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Getting started with {{site.data.keyword.iot_short_notm}}
{: #gettingstartedtemplate}

{{site.data.keyword.iot_full}} for {{site.data.keyword.Bluemix_notm}} gives you a versatile toolkit that includes gateway devices, device management, and powerful application access. By using {{site.data.keyword.iot_short_notm}}, you can collect connected device data and perform analytics on real-time data from your organization.
{:shortdesc}

## Before you begin
{: #byb}

Before connecting devices and utilizing data, register for an {{site.data.keyword.Bluemix_notm}} account and create an instance of the {{site.data.keyword.iot_short_notm}} service in your {{site.data.keyword.Bluemix_notm}} organization. You can create an {{site.data.keyword.iot_short_notm}} instance directly from the [{{site.data.keyword.iot_short_notm}} page in the IBM Cloud Services Catalog ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://console.{DomainName}/catalog/services/internet-of-things-platform/){:new_window}.  

For detailed information about how to sign up for an account on {{site.data.keyword.Bluemix_notm}}, configure regions, and other account management settings, see [Managing your IBM Cloud account](https://console.ng.bluemix.net/docs/admin/account.html#signup).

You can set up and configure your {{site.data.keyword.iot_short_notm}} instance from the dashboard. To open the dashboard, go to your {{site.data.keyword.iot_short_notm}} service instance in  {{site.data.keyword.Bluemix_notm}}, and then click **Launch**.

## About this task

The following steps describe how you can quickly get started with your {{site.data.keyword.iot_short_notm}} service.

A more detailed set of getting started guides and sample applications that step through the basics of developing a ready-for-production, end-to-end IoT prototype system with {{site.data.keyword.iot_short_notm}} are also available. If you are a developer who is new to working with {{site.data.keyword.iot_short_notm}}, use the step-by-step processes in the [Getting started guides](https://console.bluemix.net/docs/services/IoT/getting_started/getting-started-iot-overview.html#getting-started) section.

## Step 1: Connect your devices
{: #up_and_running}

To get up and running with the service, explore the following options depending on your situation:

|  |   The service is deployed | The service is not deployed
 | -------------| ------------- | -------------
  |**I have a device to connect** | [Connect your device to {{site.data.keyword.iot_short_notm}}](iotplatform_task.html#iotplatform_task).| Explore device connection in the [Play with {{site.data.keyword.iot_short_notm}} ![External link icon](../../icons/launch-glyph.svg "External link icon")](http://discover-iot.eu-gb.mybluemix.net/?cm_mc_uid=44491599487314618721024&cm_mc_sid_50200000=1462798151#/play){:new_window}.
  |**I do not have a device to connect** | [Create and connect a Node-RED device simulator](nodereddevice_sample.html){:new_window}. Or [Connect your Smartphone ![External link icon](../../icons/launch-glyph.svg "External link icon")](http://discover-iot.eu-gb.mybluemix.net/?cm_mc_uid=44491599487314618721024&cm_mc_sid_50200000=1462798151#/play/device/smartphone){:new_window}. | Get started with [Watson IoT Platform Starter](https://console.bluemix.net/docs/starters/IoT-starter/iot500.html).
  
For more information on how to connect specific device types to {{site.data.keyword.iot_short_notm}}, see [developerWorks recipes ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://developer.ibm.com/recipes/tutorials/category/internet-of-things-iot/){:new_window}.  

For device connection developer documentation, see:
- [MQTT connectivity for devices](devices/mqtt.html).
- [MQTT connectivity for gateways](gateways/mqtt.html).

<!--
## Step 2: Analyze your device data
{: #analyzing_data}
Start exploring the real-time data that the devices are sending to {{site.data.keyword.iot_short_notm}}.
{{site.data.keyword.iot_short_notm}} includes the following analytics tools:  
- [Boards and cards](data_visualization.html) to visualize your real-time device data.
- [Rules and actions](analytics.html) that are triggered by real-time device data.
For a quick getting started example, see the [Using Rules and Actions with IBM Watson IoT Platform Cloud Analytics ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://developer.ibm.com/recipes/tutorials/using-rules-and-actions-with-ibm-watson-iot-platform-cloud-analytics/){:new_window} developerWorks recipe.
-->

## Step 2: Create applications to consume your device data
{: #develop_applications}

Create and connect your own applications to consume device data.

For more information, see the following topics:   
- Explore the [application developer documentation](applications/api.html) and the [{{site.data.keyword.iot_short_notm}} API Documentation](reference/api.html).
- Explore the [{{site.data.keyword.iot_short_notm}} client libraries](iot_platform_client_lib.html) that provide tools and files to build and develop code for integrating and connecting your devices and applications.
- [Connect a {{site.data.keyword.cloudantfull}} service](cloudant_connector.html) to your {{site.data.keyword.iot_short_notm}} to store historical device data.
- Create your own rules by using the new [embedded rules (Beta)](information_management/im_rules.html) feature.
