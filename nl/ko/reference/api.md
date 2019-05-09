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


# API
{: #api_overview}

<p>이 {{site.data.keyword.cloud}} 문서 콜렉션은 {{site.data.keyword.iot_full}} Lite 가격 플랜과 관계가 있으며 기본 시작하기 정보, API 참조 및 일반 문제점 해결 정보가 포함되어 있습니다.
전체 {{site.data.keyword.iot_short_notm}} 기능 문서는 IBM Knowledge Center의 [{{site.data.keyword.iot_short_notm}} 제품 문서 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/overview/overview.html)를 참조하십시오. 다양한 플랜에 대한 자세한 정보는 [{{site.data.keyword.iot_short_notm}} 서비스 플랜](/docs/services/IoT?topic=iot-platform-plans_overview#plans_overview)에서 찾을 수 있습니다.
</p>
{: important}

다양한 API를 {{site.data.keyword.iot_full}}에 연결된 디바이스, 게이트웨이 및 애플리케이션의 코드를 개발하는 데 사용할 수 있습니다.

HTTP API는 HTTP 기본 인증으로 보호됩니다. 대시보드를 사용하여 API 키를 생성하는 경우 키와 인증 토큰이 제공됩니다. API 키 및 토큰에 대한 자세한 정보는 [API 키 연결 ![외부 링크 아이콘](../../../icons/launch-glyph.svg)](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/platform/platform_authorization.html#api-key){: new_window}을 참조하십시오.


## HTTP API 정보
{: #api_about}

각 {{site.data.keyword.iot_short_notm}} 조직은 HTTP API 호출의 호스트 이름에 필요한 6자의 조직 ID로 식별됩니다.   

### API 문서
{: #api_docs}

API 문서를 보려면 [IBM Watson IoT Platform REST API ![외부 링크 아이콘](../../../icons/launch-glyph.svg)](https://docs.internetofthings.ibmcloud.com/apis/swagger/index.html){: new_window} 페이지로 이동하십시오. 이 랜딩 페이지에서 사용 가능한 {{site.data.keyword.iot_short_notm}} API에 대한 문서에 액세스할 수 있습니다. 

### 대화식 API 문서

대화식 API 문서를 보고 사용하기 위해 다음 주소에서 조직의 기본 URL에 액세스할 수 있습니다. 

`https://<orgId>.internetofthings.ibmcloud.com/docs/index.html`

이 랜딩 페이지에서 사용 가능한 {{site.data.keyword.iot_short_notm}} API에 대한 문서에 액세스할 수 있습니다. 액세스하여 문서에서 API 호출을 문서에서 직접 실행하려면 권한을 부여 받아야 합니다.

자동으로 권한을 부여 받으려면 다음 단계를 완료하십시오.

1. {{site.data.keyword.iot_short_notm}} 대시보드에 로그인하십시오. 
2. 동일한 브라우저에서 새 탭을 열고 대화식 API 문서 랜딩 페이지로 이동하십시오.

{{site.data.keyword.iot_short_notm}} 대시보드에 로그인하지 않은 경우 다음 단계를 완료하십시오.

1. 대화식 API 문서 랜딩 페이지로 이동하십시오.
2. `Authorize`를 선택하십시오.
3. `Available authorizations` 상자에서 사용자 이름을 API 키로 설정하고 비밀번호를 인증 토큰으로 설정하십시오. `Authorize`를 선택하십시오.
4. `Available authorizations` 상자를 닫으십시오. **중요:** `Logout`을 선택하지 마십시오.

권한이 부여되면 특정 API 호출로 이동하고 `Try it out` 단추를 사용하여 문서에서 API 호출을 직접 실행하십시오.

<!-- To authenticate requests to the application API, set the username to the API key and the password to the authentication token. -->
