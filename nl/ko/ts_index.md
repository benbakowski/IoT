---

copyright:
  years: 2016, 2019
lastupdated: "2019-04-05"

keywords: Watson IoT Platform, Watson IoT Platform organization, IoT Platform, troubleshooting

subcollection: iot-platform

---

{:new_window: target="\_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:important: .important}

# {{site.data.keyword.iot_short_notm}} 문제점 해결
{: #ts}

<p>이 {{site.data.keyword.cloud}} 문서 콜렉션은 {{site.data.keyword.iot_full}} Lite 가격 플랜과 관계가 있으며 기본 시작하기 정보, API 참조 및 일반 문제점 해결 정보가 포함되어 있습니다.
전체 {{site.data.keyword.iot_short_notm}} 기능 문서는 IBM Knowledge Center의 [{{site.data.keyword.iot_short_notm}} 제품 문서 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/overview/overview.html)를 참조하십시오. 다양한 플랜에 대한 자세한 정보는 [{{site.data.keyword.iot_short_notm}} 서비스 플랜](/docs/services/IoT?topic=iot-platform-plans_overview#plans_overview)에서 찾을 수 있습니다.
</p>
{: important}

여기에는 {{site.data.keyword.cloud_notm}}에서 {{site.data.keyword.iot_full}} 사용에 대한 일반 문제점 해결 질문에 대한 답변이 있습니다.
{:shortdesc}

## {{site.data.keyword.iot_short_notm}} 조직에 액세스하는 문제점
{: #access-expiry-problem}

소유한 {{site.data.keyword.iot_short_notm}} 조직에 로그인할 수 없습니다.
{:shortdesc}

`https://internetofthings.ibmcloud.com`을 사용하거나 조직 URL을 사용하여 직접 {{site.data.keyword.iot_short_notm}} 조직에 로그인할 수 없습니다.
{: tsSymptoms}

{{site.data.keyword.iot_short_notm}} 조직에 대한 액세스 권한이 만료되었을 수 있습니다. {{site.data.keyword.cloud}}를 사용하여 작성된 {{site.data.keyword.iot_short_notm}} 조직은 기본적으로 임시 사용자 프로파일을 사용합니다.
{: tsCauses}

{{site.data.keyword.cloud_notm}}를 사용하여 {{site.data.keyword.iot_short_notm}} 조직에 액세스하고 사용자 프로파일의 만기 설정을 변경하여 이 문제점을 해결할 수 있습니다. 사용자 만기 설정을 변경하려면 다음을 수행하십시오.

1. {{site.data.keyword.cloud_notm}} 대시보드에서 {{site.data.keyword.iot_short_notm}} 서비스를 여십시오.
2. 탐색줄에서 **구성원**을 클릭하십시오.
3. **편집** 아이콘을 클릭하십시오.
4. **액세스 만료** 선택란의 선택을 취소하고 **저장**을 클릭하십시오.
{: tsResolve}

## {{site.data.keyword.iot_short_notm}} 연결 문제
{: #connection_problem}

{{site.data.keyword.iot_short_notm}}에 대한 연결이 예상치 못하게 삭제되거나 연결이 끊깁니다.
{:shortdesc}

{{site.data.keyword.iot_short_notm}}에 연결하려고 하면 디바이스나 애플리케이션에서 오류가 발생합니다.
{: tsSymptoms}

동일한 클라이언트 ID 및 인증 정보로 연결을 시도하는 둘 이상의 디바이스가 있을 수 있습니다. clientID당 하나의 고유 연결만 허용됩니다. 동일한 ID를 사용하여 여러 개를 동시에 연결할 수 없습니다. 애플리케이션에서는 동일한 API 키를 공유할 수 있지만 MQTT에서는 클라이언트 ID가 항상 고유해야 합니다.
{: tsCauses}

여러 개의 디바이스가 동일한 인증 정보를 사용하여 연결을 시도하지 않음을 확인하면 이 원인을 제외할 수 있습니다.
{: tsResolve}

## {{site.data.keyword.iot_short_notm}}에서 간헐적으로 디바이스 연결이 끊김
{: #disconnection_problem}

{{site.data.keyword.iot_short_notm}}에 대한 디바이스 연결이 간헐적으로 예상치 못하게 삭제됩니다.
{:shortdesc}

{{site.data.keyword.iot_short_notm}} 서비스에 연결된 디바이스가 간헐적으로 연결이 끊깁니다. 디바이스가 다시 연결되지만 잠시 후에 예상치 못하게 다시 연결이 끊깁니다.
{: tsSymptoms}

연결할 때 너무 낮은 MQTT ping 옵션 값을 사용하여 연결 제한시간이 초과된 것처럼 보이기 때문일 수 있습니다. 예를 들어 클라이언트 MQTT가 잘못 설정되면 ping이 제때에 수신되지 않으므로 연결이 닫힙니다.
{: tsCauses}

연결의 ping 및 KeepAlive 매개변수를 제대로 설정했는지 확인하여 이 문제점을 수정할 수 있습니다.   
{: tsResolve}
