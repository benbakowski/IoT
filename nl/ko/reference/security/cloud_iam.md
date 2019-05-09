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


# {{site.data.keyword.iot_short_notm}}용 {{site.data.keyword.iamshort}} 인증 및 권한 부여(베타)
{: #cloud_iam}

<p>이 {{site.data.keyword.cloud}} 문서 콜렉션은 {{site.data.keyword.iot_full}} Lite 가격 플랜과 관계가 있으며 기본 시작하기 정보, API 참조 및 일반 문제점 해결 정보가 포함되어 있습니다.
전체 {{site.data.keyword.iot_short_notm}} 기능 문서는 {{site.data.keyword.IBM_notm}} Knowledge Center의 [{{site.data.keyword.iot_short_notm}} 제품 문서 ![외부 링크 아이콘](../../../../icons/launch-glyph.svg "외부 링크 아이콘")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/overview/overview.html)를 참조하십시오. 다양한 플랜에 대한 자세한 정보는 [{{site.data.keyword.iot_short_notm}} 서비스 플랜](/docs/services/IoT?topic=iot-platform-plans_overview#plans_overview)에서 찾을 수 있습니다.
</p>
{: important}

{{site.data.keyword.iot_full}} API는 IAM({{site.data.keyword.iamshort}})을 사용하여 사용자의 인증 및 권한 부여를 지원합니다.

{{site.data.keyword.iot_short_notm}}용 {{site.data.keyword.iamlong}} 인증 및 권한 부여는 제한된 베타 프로그램의 일부로만 사용 가능합니다. 향후 업데이트에는 이 기능의 현재 버전과 호환 가능한 변경사항이 포함될 수 있습니다. 시도해 보고 [의견을 보내주십시오. ![외부 링크 아이콘](../../../../icons/launch-glyph.svg)](https://developer.ibm.com/answers/smart-spaces/17/internet-of-things.html){: new_window}
{: important}

{{site.data.keyword.iamshort}}는 {{site.data.keyword.cloud_notm}}에 빌드되며 {{site.data.keyword.IBM_notm}} 서비스를 구성하고 관리해야 하는 관리자 및 개발자의 인증 및 권한 부여에 사용됩니다. {{site.data.keyword.iot_short_notm}} 대시보드에 액세스해야 하는 사용자는 {{site.data.keyword.iamshort}}를 사용하여 인증됩니다. {{site.data.keyword.iamshort}}에 대한 ID의 소스는 등록된 IBM ID 사용자이거나 SAML을 지원하는 고객의 디렉토리 서비스일 수 있습니다.  

{{site.data.keyword.iot_short_notm}}도 {{site.data.keyword.appid_short_notm}}를 통한 사용자 인증을 지원합니다. {{site.data.keyword.appid_short_notm}}는 {{site.data.keyword.cloud_notm}}에서 호스팅되는 애플리케이션에 액세스해야 하는 사용자를 인증하는 데 사용됩니다. {{site.data.keyword.appid_short_notm}} 사용자는 일반적으로 클라우드 서비스에서 관리 또는 개발 활동을 수행하지 않습니다. 자세한 정보는 [Watson IoT Platform용 {{site.data.keyword.appid_short_notm}} 인증 ![외부 링크 아이콘](../../../../icons/launch-glyph.svg "외부 링크 아이콘")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/platform/app_id.html#app_id){: new_window}을 참조하십시오.

IAM을 통해 사용자는 IAM OAuth 토큰을 가져올 수 있으며 이를 사용하여 API 호출을 인증할 수 있습니다. 예를 들어, {{site.data.keyword.containershort_notm}} CLI가 설치된 사용자는 다음 명령을 사용할 수 있습니다.

`bx iam oauth-tokens`

이 명령은 다음 형식으로 로그인한 사용자의 IAM 토큰을 리턴합니다.

`IAM Token: Bearer <some token>`

사용자는 다음 예제에 표시된 대로 IAM 토큰 엔드포인트를 사용하여 로그인하고 자체 IAM 토큰을 검색할 수도 있습니다.
`curl -s 'https://iam.cloud.ibm.com/identity/token?grant_type=urn:ibm:params:oauth:grant-type:apikey&response_type=cloud_iam&apikey=<apikey>' -H'Content-Type:x-www-form-urlencoded' -XPOST`

이 API 예제는 IAM API 키를 사용하여 IAM 토큰을 요청하고 `Bearer <token>`을 리턴합니다.

그런 다음 사용자가 {{site.data.keyword.iot_short_notm}} API를 호출하는 경우 권한 헤더 `Authorization: Bearer <token>`을 해당 API 호출에 제공할 수 있습니다.

## IAM 토큰 생성
{: #iam_generate}

{{site.data.keyword.cloud_notm}}를 인증하는 방법과 사용하는 {{site.data.keyword.cloud_notm}} ID 유형에 따라 IAM 토큰 작성을 자동화하는 방법을 선택할 수 있습니다.

비-연합 ID를 사용하는 경우에는 IAM 토큰 작성을 위한 다음 옵션 중 하나를 선택할 수 있습니다.
 - **{{site.data.keyword.cloud_notm}} 사용자 이름 및 비밀번호:** IAM 액세스 토큰의 작성을 완전히 자동화하기 위해 토큰을 작성할 수 있습니다.
 - **{{site.data.keyword.cloud_notm}} API 키 생성:** 생성되는 {{site.data.keyword.cloud_notm}} 계정에 의존하는 {{site.data.keyword.cloud_notm}} API 키를 사용합니다. {{site.data.keyword.cloud_notm}} API 키를 동일한 IAM 토큰의 다른 계정 ID와 결합할 수 없습니다. {{site.data.keyword.cloud_notm}} API 키가 기반인 계정 외에 다른 계정으로 작성된 클러스터에 액세스하려면, 계정에 로그인하여 새 API 키를 생성해야 합니다.

연합 ID를 사용하는 경우에는 IAM 토큰 작성을 위한 다음 옵션 중 하나를 선택할 수 있습니다.
 - **{{site.data.keyword.cloud_notm}} API 키 생성:** {{site.data.keyword.cloud_notm}} API 키는 생성되는 {{site.data.keyword.cloud_notm}} 계정에 의존합니다. {{site.data.keyword.cloud_notm}} API 키를 동일한 IAM 토큰의 다른 계정 ID와 결합할 수 없습니다. {{site.data.keyword.cloud_notm}} API 키가 기반인 계정 외에 다른 계정으로 작성된 클러스터에 액세스하려면, 계정에 로그인하여 새 API 키를 생성해야 합니다.
 - **일회성 패스코드 사용:** 일회성 패스코드를 검색하려면 웹 브라우저와 수동으로 상호작용해야 하므로, 일회성 패스코드를 사용하여 {{site.data.keyword.cloud_notm}}를 인증하는 경우에는 IAM 토큰 작성을 완전히 자동화할 수 없습니다. IAM 토큰 작성을 완전히 자동화하려면 {{site.data.keyword.cloud_notm}} API 키를 대신 작성해야 합니다.

액세스 토큰을 작성하는 경우 요청에 포함되는 본문 정보는 사용하는 {{site.data.keyword.cloud_notm}} 인증 방법에 따라 달라집니다. 다음 값을 대체하십시오.
- `<my_username>` = {{site.data.keyword.cloud_notm}} 사용자 이름.
- `<my_password>` = {{site.data.keyword.cloud_notm}} 비밀번호.
- `<my_api_key>` = {{site.data.keyword.cloud_notm}} API 키.
- `<my_passcode>` = {{site.data.keyword.cloud_notm}} 일회성 패스코드. `bx login --sso`를 실행하고 CLI 출력의 지시사항에 따라 웹 브라우저를 사용하여 일회성 패스코드를 검색하십시오.

예:
`POST https://iam.<region>.cloud.ibm.com/identity/token`

{{site.data.keyword.cloud_notm}} 지역을 지정하려면 API 엔드포인트에서 사용되는 지역 약어를 검토하십시오. 자세한 정보는 [{{site.data.keyword.cloud_notm}} 지역 API 엔드포인트 ![외부 링크 아이콘](../../../../icons/launch-glyph.svg)](https://cloud.ibm.com/docs/containers/cs_regions.html#bluemix_regions){: new_window}를 참조하십시오.

입력 매개변수	 |값
---------------- | -----------
헤더	| Content-Type:application/x-www-form-urlencoded<br>Authorization: Basic Xng7Png=<br>참고: 사용자 이름 bx 및 비밀번호 bx에 대한 URL 인코딩된 권한 `Xng7Png=`가 제공됩니다.
{{site.data.keyword.cloud_notm}} 사용자 이름 및 비밀번호의 본문	|	grant_type: password<br>response_type: cloud_iam, uaa<br>username: `<my_username>`<br>password: `<my_password>`<br>uaa_client_id: cf<br>uaa_client_secret:<br>참고: 값이 지정되지 않은 uaa_client_secret 키를 추가하십시오.
{{site.data.keyword.cloud_notm}} API 키의 본문	|	grant_type: urn:ibm:params:oauth:grant-type:apikey<br>response_type: cloud_iam<br>uaa<br>apikey: `<my_api_key>`<br>uaa_client_id: cf<br>uaa_client_secret:<br>참고: 값이 지정되지 않은 uaa_client_secret 키를 추가하십시오.
{{site.data.keyword.cloud_notm}} 일회성 패스코드의 본문	|	grant_type: urn:ibm:params:oauth:grant-type:passcode<br>response_type: cloud_iam, uaa<br>passcode: `<my_passcode>`<br>uaa_client_id: cf<br>uaa_client_secret:<br>참고: 값이 지정되지 않은 uaa_client_secret 키를 추가하십시오.

예제 API 출력:

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
API 출력의 **access_token** 필드에서 IAM 토큰을 찾을 수 있습니다.

다음 예제는 API 호출 중에 IAM 토큰을 사용하는 방법을 표시합니다.

```
GET https://org.domain/api/v0002/bulk/devices
```

입력 매개변수   |	값
----------------- | -----------
헤더	|	Content-Type: application/json<br>Authorization: bearer `<iam_token>`
