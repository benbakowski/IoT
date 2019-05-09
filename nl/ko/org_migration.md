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

# {{site.data.keyword.iot_short_notm}} Non-production 또는 Production으로 {{site.data.keyword.iot_short_notm}} Lite 마이그레이션
{: #org_migration}

<p>이 {{site.data.keyword.cloud}} 문서 콜렉션은 {{site.data.keyword.iot_full}} Lite 가격 플랜과 관계가 있으며 기본 시작하기 정보, API 참조 및 일반 문제점 해결 정보가 포함되어 있습니다.
전체 {{site.data.keyword.iot_short_notm}} 기능 문서는 {{site.data.keyword.IBM}} Knowledge Center의 [{{site.data.keyword.iot_short_notm}} 제품 문서 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/overview/overview.html)를 참조하십시오. 다양한 플랜에 대한 자세한 정보는 [{{site.data.keyword.iot_short_notm}} 서비스 플랜](/docs/services/IoT?topic=iot-platform-plans_overview#plans_overview)에서 찾을 수 있습니다.
</p>
{: important}

Watson IoT Platform Lite의 품질과 성능에 대한 사전 점검을 완료하고 귀사의 IoT 환경에 얼마나 적합한지 이해했다면 [Watson IoT Platform Non-production 또는 Production 플랜 중 하나 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/overview/overview.html){: new_window}로 업그레이드할 수 있습니다.
{:shortdesc}

**참고:** 이 문서는 Lite 인스턴스가 있는 사용자 전용입니다. 이전에 Standard 또는 Advanced Security 플랜을 사용하여 IoT Platform의 인스턴스를 작성한 경우 {{site.data.keyword.IBM}}에서는 기존의 {{site.data.keyword.iot_short_notm}} 인스턴스를 새로운 Non-production 또는 Production 플랜으로 마이그레이션하도록 지원합니다.

## 마이그레이션 프로세스 개요
{: #org_migration_overview}

{{site.data.keyword.iot_short_notm}}으로 마이그레이션하면 500개 디바이스 및 월별 데이터 사용에 대한 Lite 플랜 한계가 제거됩니다.

{{site.data.keyword.iot_short_notm}} 플랜에는 엔드-투-엔드 애플리케이션 아키텍처를 지원하기 위해 다음과 같은 추가 컴포넌트가 포함되어 있습니다.

- {{site.data.keyword.messagehub}} - 애플리케이션이 IoT 데이터를 검색하는 데 사용할 수 있는 Kafka 스트리밍 플랫폼의 {{site.data.keyword.IBM_notm}} 호스팅 버전.
- {{site.data.keyword.dashdbshort}} - 분석 데이터 스토리지용.
- {{site.data.keyword.cloudantfull}} DB - 시계열 데이터용.
- {{site.data.keyword.cos_full}} - 장기 데이터 보관용.

이 문서에서는 기존의 Lite 인스턴스에서 전체 버전으로 마이그레이션하려는 데이터 유형에 대해 설명합니다.

**참고:** {{site.data.keyword.iot_short_notm}} Lite 서비스 이상의 컴포넌트 및 기능을 포함하므로 처음부터 {{site.data.keyword.iot_short_notm}} 비프로덕션 또는 프로덕션 환경을 설정하는 것이 일반적으로 가장 쉽습니다. 또한 Lite 버전에서 테스트를 위해 작성한 디바이스 및 사용자는 프로덕션에 사용할 디바이스와 동일하지 않을 수 있습니다.

그러나 기존의 Lite 설정 중 일부를 이전하려는 경우에는 다음 절에서 안내하는 프로세스를 참조하십시오.

[{{site.data.keyword.iot_short_notm}} API](/docs/services/IoT?topic=iot-platform-api_overview#api_overview)의 문서에서는 API 및 전체 매개변수 세트를 호출하는 방법에 대한 지시사항을 제공합니다.


## 시작하기 전에
{: #org_migration_byb}

마이그레이션 프로세스를 시작하려면 {{site.data.keyword.iot_short_notm}}(프로덕션 또는 비프로덕션)을 구매해야 합니다. 구매할 때 {{site.data.keyword.IBM_notm}} 운영 팀에서 귀하를 위해 새 {{site.data.keyword.iot_short_notm}} 인스턴스를 프로비저닝합니다. 여기에는 6자의 신규 영숫자 조직 ID가 포함됩니다.


## 사용자 마이그레이션
{: #user_migration}

[사용자 관리 API ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://docs.internetofthings.ibmcloud.com/apis/swagger/v0002/security.html#!/Authorization_-_User_Management){: new_window}는 {{site.data.keyword.iot_short_notm}} 사용자의 대량 내보내기 및 가져오기 기능을 제공하며 새 조직에서 유지하려는 사용자를 내보내고 가져오는 데 사용할 수 있습니다.

1. Lite 조직의 사용자를 내보내십시오.  
`GET /authorization/users` 명령을 사용하여 Lite 계정 조직의 모든 사용자를 JSON 오브젝트로 내보냅니다.
2. 사용자 목록을 정리하십시오.  
필요한 경우 JSON 구조를 편집하여 새 조직으로 마이그레이션하지 않으려는 사용자를 제거합니다.
3. 사용자를 새 조직으로 가져오십시오.  
`POST /authorization/users/multiple` 명령을 사용하여 편집한 JSON 사용자 목록을 새 조직으로 가져옵니다.

이제 사용자는 새 조직에 대한 액세스 권한을 갖게 되고 {{site.data.keyword.iot_short_notm}} 대시보드의 조직 선택기에 표시됩니다.

##  디바이스 마이그레이션  
{: #device_migration}

디바이스 마이그레이션은 다음 단계를 통해 완료할 수 있습니다.  
1. 새 조직에 유지하려는 디바이스 유형을 마이그레이션하십시오.  
2. 새 조직에 디바이스 자체를 마이그레이션하십시오.  
3. 디바이스가 {{site.data.keyword.cloud_notm}}에 연결하는 데 사용하는 호스트 이름을 업데이트하여 새 조직 ID로 시작하십시오.
4. Lite 플랫폼에서 작성한 데이터 관리 정보를 마이그레이션하십시오.   
여기에는 디바이스 실제 및 논리 인터페이스, 항목 및 규칙이 포함될 수 있습니다.

<p>디바이스 유형 및 디바이스는 다음 API를 사용하여 대량으로 마이그레이션할 수 있습니다.
<table>
<tr>
<th> API 문서 </th>
<th> 내보내기 API </th>
<th> 가져오기 API </th>
</tr>
<tr>
<td> [디바이스 유형 API ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://docs.internetofthings.ibmcloud.com/apis/swagger/v0002/org-admin.html) </td>
<td> `GET /device/types` </td>
<td> `POST /device/types` </td>
</tr>
<tr>
<td>  [디바이스 API ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://docs.internetofthings.ibmcloud.com/apis/swagger/v0002/org-admin.html#!/Device_Bulk_Configuration) </td>
<td> `GET /bulk/devices` </td>
<td>  `POST /bulk/devices/add`</td>
</tr>
</table>
</p>
{: tip}


**중요:** {{site.data.keyword.iot_short_notm}}은 디바이스 인증 토큰을 저장하지 않으며 솔트 처리된 버전만 저장합니다. 따라서 `GET /bulk/devices` 호출은 저장된 디바이스에 대한 인증 토큰을 리턴할 수 없습니다. 디바이스 인증 토큰 레코드가 있다면 벌크 로드를 수행하기 전에 JSON 오브젝트에 레코드를 추가할 수 있습니다. 그렇지 않으면 각 디바이스에 대한 새 디바이스 인증 토큰을 생성하고 디바이스에 복사해야 합니다.  

디바이스를 인증하는 데 인증 토큰이 아닌 디바이스측 인증서를 사용하는 경우에는 이를 수행할 필요가 없습니다. 그러나 디바이스측 인증서를 사용하면 새 조직에 서명하는 데 사용된 인증서를 업로드해야 합니다.


## 디바이스 업데이트
{: #update_devices}

디바이스가 새 조직에 등록된 경우 기존 디바이스 각각에 존재하는 구성 또는 코드를 업데이트하여 새 조직의 호스트 이름을 사용해야 합니다.

MQTT 및 HTTP 메시징 클라이언트의 경우 다음 호스트 이름을 사용하십시오.  
`<orgId>.messaging.internetofthings.ibmcloud.com`

다음 호스트 이름의 REST API 클라이언트를 가리키십시오.  
`<orgId>.internetofthings.ibmcloud.com`

**중요:** 디바이스에 대한 새 인증 토큰을 생성한 경우 해당 토큰을 각 디바이스에 복사해야 합니다.


## 디바이스 관리 마이그레이션
{: #device_management}

[데이터 관리 API ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://docs.internetofthings.ibmcloud.com/apis/swagger/v0002/state-mgmt.html){: new_window}에는 디바이스 실제 인터페이스 및 논리 인터페이스, 항목 정의 및 규칙을 내보내고 가져오기 위한 API가 포함되어 있습니다.

**중요:** {{site.data.keyword.iot_short_notm}}은 현재 데이터 수집에 대한 자산 트윈스 개념을 지원하지 않습니다.

## 보드 및 카드
{: #boards_cards}

{{site.data.keyword.iot_short_notm}}에는 보드 및 카드에 대한 정의와 사용자 정의를 가져오고 내보내기 위한 API가 포함되어 있지 않습니다. 새 조직에서 수동으로 다시 작성해야 합니다.

## 필수 확장기능 사용
{: #extensions}

Lite 플랫폼에서 사용하도록 설정한 확장기능은 새 조직에서 다시 작성해야 합니다(예: {{site.data.keyword.messagehub}}, {{site.data.keyword.cloudant_short_notm}} 및 Jasper에 대한 링크).

## 애플리케이션 마이그레이션
{: #application_migration}

예를 들어, 데이터를 보내고 받거나 서비스를 관리하기 위해 {{site.data.keyword.iot_short_notm}} Lite 서비스와 함께 제공된 API를 호출하는 애플리케이션을 개발한 경우 새 {{site.data.keyword.iot_short_notm}} Production 또는 Non-production 인스턴스를 사용하도록 애플리케이션을 업데이트해야 합니다. 이는 사용할 수 있는 Node-RED 플로우에도 적용됩니다.
마이그레이션 과정은 다음과 같습니다.
- 6자의 새 조직 ID를 사용하도록 애플리케이션을 업데이트합니다.
- 새 서비스 인스턴스를 위해 작성하는 토큰 인증 정보 및 API키를 사용하도록 애플리케이션을 업데이트합니다.

**중요:** 조직 ID 및 인증 정보를 애플리케이션에 전달하는 데 Cloud Foundry 바인딩을 사용하는 경우 Cloud Foundry 공간에서 실행되도록 새 {{site.data.keyword.iot_short_notm}} 인스턴스가 프로비저닝되지 않으므로 다른 메커니즘을 사용해야 합니다.

### API 연결 인증 정보 생성

수행할 마이그레이션 프로세스는 애플리케이션의 특성에 따라 다릅니다. 일반적으로 모든 경우의 첫 번째 단계는 사용할 애플리케이션에 대한 API키 및 인증 토큰을 획득하는 것입니다.

1. 새 {{site.data.keyword.iot_short_notm}} 서비스의 최상위 레벨 대시보드에 로그인하십시오.
2. **사용량** 탭을 선택하십시오.
3. {{site.data.keyword.iot_short_notm}} 서비스 정보를 표시하려면 **보기 세부사항** 링크를 클릭하십시오.  
다음 정보가 표시됩니다.
   - 6자의 orgID
   - API 키 및 토큰  
   여기에 표시된 API 키를 사용하는 대신 각 애플리케이션에 대한 새 API 키를 생성해야 합니다. 그러면 각 애플리케이션에 대한 적절한 권한을 설정할 수 있습니다.
   - 호스트 URL
4. 애플리케이션에 대한 API 키 및 인증 토큰 조합을 작성하십시오.  
조직에 연결하기 위해 애플리케이션을 구성할 때 이러한 사항이 필요합니다.   
   1.  `실행`을 클릭하십시오.  
   {{site.data.keyword.iot_short_notm}} Lite 서비스를 관리하는 데 사용한 기본 서비스 대시보드로 이동하게 됩니다.
   2. **앱**을 연결하십시오.
   3. **API 키 생성**을 클릭하십시오.
   4. 나열된 API 키 및 인증 토큰 값을 복사하십시오.
   5. 애플리케이션에 적합한 역할을 선택하십시오.   
   6. 이 API 키 및 인증 토큰 조합을 쉽게 식별할 수 있도록 주석을 추가하십시오.
   7. **생성**을 클릭하십시오.
   8. **중요:** 인증 토큰의 로컬 사본을 작성하십시오. 창을 닫은 후에는 다시 작성할 수 없습니다.


### Node-RED 애플리케이션 업데이트
새 {{site.data.keyword.iot_short_notm}} 인스턴스에 연결하도록 Node-RED 노드를 구성해야 합니다. `ibmiot` 노드를 더 이상 `BluemixService` 인증 옵션에 사용할 수 없으므로 대신 `API Key` 옵션을 선택해야 합니다.
1. 편집을 위해 `ibmiot` 노드를 여십시오.
2. 노드 특성 아래에서 **API 키**를 선택하십시오.
3. API 키 필드의 경우 편집 아이콘을 클릭한 후 이전 단계에서 저장한 API 키 및 인증 토큰을 입력하십시오.
4. 변경사항을 저장하고 Node-RED 플로우를 다시 배치하십시오.

### Cloud Foundry 바인딩을 사용하지 않는 애플리케이션 업데이트
애플리케이션에서 조직 ID, API 키 및 인증 토큰을 저장하는 위치를 식별하고 이전에 사용자가 저장한 값으로 이를 대체하십시오.

애플리케이션에서 {{site.data.keyword.iot_short_notm}} SDK 중 하나를 사용하는 경우 이러한 값은 특성 파일에 있을 수 있습니다.
{: tip}

### Cloud Foundry 바인딩을 사용하는 애플리케이션 업데이트

{{site.data.keyword.cloud_notm}}에서는 Cloud Foundry 애플리케이션을 하나 이상의 Cloud Foundry 서비스에 바인딩하는 메커니즘을 제공합니다. {{site.data.keyword.cloud_notm}} CLI를 사용하거나 {{site.data.keyword.cloud_notm}} 대시보드에서 애플리케이션과 서비스 간에 `Connection`을 작성하여 바인딩을 설정할 수 있습니다.

애플리케이션이 서비스에 바인드되면 서비스 API키 및 인증 토큰 인증 정보가 애플리케이션에서 검색할 수 있는 위치의 `VCAP_SERVICES` 환경 변수에 복사됩니다.

**중요:** 이 바인딩 메커니즘은 새 {{site.data.keyword.iot_short_notm}} 서비스와 함께 사용할 수 없습니다. `VCAP_SERVICES`로부터 읽는 애플리케이션의 코드를 찾아 지금 API 키와 인증 토큰을 저장하는 위치로부터 값을 읽는 코드로 대체해야 합니다. 업데이트를 완료하려면 애플리케이션을 다시 빌드하고 다시 배치해야 합니다.
