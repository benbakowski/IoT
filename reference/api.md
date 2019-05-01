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


# APIs
{: #api_overview}

<p>This {{site.data.keyword.cloud}} documentation collection pertains to the {{site.data.keyword.iot_full}} Lite pricing plan and includes basic getting started information, API references, and general troubleshooting information. 
For the full {{site.data.keyword.iot_short_notm}} feature documentation, see the [{{site.data.keyword.iot_short_notm}} product documentation ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/overview/overview.html) on IBM Knowledge Center. More information about the various plans can be found in [{{site.data.keyword.iot_short_notm}} service plans](/docs/services/IoT?topic=iot-platform-plans_overview#plans_overview). 
</p>
{: important}

Several APIs are available for developing code for devices, gateways, and applications that connect to {{site.data.keyword.iot_full}}.

The HTTP APIs are protected by HTTP basic authentication. When you generate an API key by using the dashboard, you are presented with a key and an authentication token. For more information about API keys and tokens, see [API key connection ![External link icon](../../../icons/launch-glyph.svg)](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/platform/platform_authorization.html#api-key){: new_window}.


## About HTTP APIs
{: #api_about}

Each {{site.data.keyword.iot_short_notm}} organization is identified by a 6-character organization ID which is required in the host name for any HTTP API call.   

### API docs
{: #api_docs}

To view the API docs, go to the [IBM Watson IoT Platform REST APIs ![External link icon](../../../icons/launch-glyph.svg)](https://docs.internetofthings.ibmcloud.com/apis/swagger/index.html){: new_window} page. From this landing page, you can access the documentation for the available {{site.data.keyword.iot_short_notm}} APIs.

### Interactive API docs

To view and use the interactive API docs, the base URL for your organization can be accessed at the following address:

`https://<orgId>.internetofthings.ibmcloud.com/docs/index.html`

From this landing page, you can access the documentation for the available {{site.data.keyword.iot_short_notm}} APIs. To have access to run the API calls directly from the documentation, you must be authorized.

To automatically be authorized, complete the following steps:

1. Log in to the {{site.data.keyword.iot_short_notm}} dashboard.
2. In the same browser, open a new tab and go to the interactive API docs landing page.

If you are not logged in to the {{site.data.keyword.iot_short_notm}} dashboard, complete the following steps:

1. Go to the interactive API docs landing page.
2. Select `Authorize`.
3. In the `Available authorizations` box, set the username to the API key and the password to the authentication token. Select `Authorize`.
4. Close the `Available authorizations` box. **Important:** Do not select `Logout`.

After you are authorized, go to specific API calls and use the `Try it out` button to run the API calls directly from the documentation.

<!-- To authenticate requests to the application API, set the username to the API key and the password to the authentication token. -->
