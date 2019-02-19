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


# Simulating device data
{: #sim_device_data}

<p>This {{site.data.keyword.Bluemix}} documentation collection pertains to the {{site.data.keyword.iot_full}} Lite pricing plan and includes basic getting started information, API references, and general troubleshooting information. 
For the full {{site.data.keyword.iot_short_notm}} feature documentation, see the [{{site.data.keyword.iot_short_notm}} product documentation ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/overview/overview.html) on IBM Knowledge Center. More information about the various plans can be found in [{{site.data.keyword.iot_short_notm}} service plans](/docs/IoT/plans_overview.html#plans_overview). 
</p>
{: important}

By using the {{site.data.keyword.iot_full}} device simulator, you can set up simulated events for devices. You can use the simulated event data to learn about, test, and demonstrate fully functioning {{site.data.keyword.iot_short_notm}} features.
{: shortdesc}

You can use existing device types and devices, and the simulator enables you to generate new devices for existing types. You can configure the event details for each device or set a default configuration that is applied to all devices. You can export a simulated event configuration so that it can be reused or shared to set up other simulations.

To simulate device data:

1. Log in to {{site.data.keyword.iot_short_notm}}.
2. From the main navigation pane, select **Settings**.
3. In the **Data and Devices** section, activate the device simulator.
4. From the main navigation pane, select **Devices**. A message in the lower right corner of the screen indicates that no simulations are running.
5. Click on the "0 Simulations running" message.
6. In the **Simulations** pop-up window, click **Create Simulation**.
7. Select an existing device type that you want to simulate data for or create a new device type by typing the device type name.
8. Click **Import/Export Simulation** to use an existing configuration or manually configure the simulation details for the device type:
   1. Click **+ New Event Type** to add an event type to the device type.
   2. Enter a name for the event type.
   3. Under **Schedule**, set the frequency of the event.
   3. Edit the event type details in JSON format and save the updated event type.

   <p> You can use the following special variables when configuring events:  
        - `range`:  This variable is replaced with a random number that is between the two provided values, for example: `{"random": range(300, 100)}`  
        - `$counter`: This variable is replaced with the number of devices that are added in the simulator for the current type, for example: `{"total": $counter}`  
        - `increment`: This variable indicates the starting number and the increment by which it increases, for example, `{"myNumber": increment(10, 1)}`. In this case, `myNumber` starts at 10 and increases by 1 each time a payload is sent (10, 11, 12, and so on).</p>
   {: tip}

9. Select a registered device for the simulation or create a new device by typing the device name.
10. To create more simulations, click **New Simulation** and repeat the configuration steps for each device that you want to apply custom settings to. The message in the lower right of the screen shows the number of active simulations.
11. **Optional:** After you configure simulations for devices, export the simulation details so that they can be reused or shared:
    1. In the **Simulations** pop-up window, click **Import/Export**.
    2. Select the **Export** tab.
    3. Copy the simulation details to the clipboard or download them in a JSON file.
12. On the **Devices** page, browse to one of the simulated devices and select the **Recent Events** tab to verify that the simulated events are working.
