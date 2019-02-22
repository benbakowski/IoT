---

copyright:
  years: 2016, 2019
lastupdated: "2019-02-13"

---

{:new_window: target="\_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}
{:important: .important}


# 시작하기 튜토리얼
{: #gettingstartedtemplate .task}

<p>이 {{site.data.keyword.Bluemix}} 문서 콜렉션은 {{site.data.keyword.iot_full}} Lite 가격 플랜과 관계가 있으며 기본 시작하기 정보, API 참조 및 일반 문제점 해결 정보가 포함되어 있습니다.
전체 {{site.data.keyword.iot_short_notm}} 기능 문서는 IBM Knowledge Center의 [{{site.data.keyword.iot_short_notm}} 제품 문서 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/overview/overview.html)를 참조하십시오. 다양한 플랜에 대한 자세한 정보는 [{{site.data.keyword.iot_short_notm}} 서비스 플랜](/docs/IoT/plans_overview.html#plans_overview)에서 찾을 수 있습니다.
</p>
{: important}

이 {{site.data.keyword.iot_short_notm}} 시작하기 튜토리얼에서 IoT 디바이스를 {{site.data.keyword.iot_short_notm}}에 연결합니다.
{:shortdesc}

## 이 태스크에 관한 정보
{: #about .sectiontitle}  

IoT 디바이스에서 데이터 수신을 시작하려면 {{site.data.keyword.iot_short_notm}}에 연결해야 합니다. 디바이스를 {{site.data.keyword.iot_short_notm}}에 연결하려면 디바이스를 {{site.data.keyword.iot_short_notm}}에 등록한 다음 {{site.data.keyword.iot_short_notm}}에 연결하도록 등록 정보를 사용하여 디바이스를 구성해야 합니다.

## 시작하기 전에
{: #byb .sectiontitle}  

{{site.data.keyword.iot_short_notm}}을 사용하려면 다음 항목이 있어야 합니다.  
* [{{site.data.keyword.Bluemix}} 계정 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://console.bluemix.net/registration/){: new_window}.
* {{site.data.keyword.iot_short_notm}} 인스턴스.  
[{{site.data.keyword.Bluemix_short}} 서비스 카탈로그의 {{site.data.keyword.iot_short_notm}} 페이지 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://{DomainName}/catalog/services/internet-of-things-platform/){:new_window}에서 {{site.data.keyword.iot_short_notm}} 인스턴스를 직접 작성할 수 있습니다.   
* 다음 요구사항을 충족하는 디바이스:  
  *	디바이스가 HTTP 또는 MQTT 프로토콜을 사용하여 통신할 수 있어야 합니다.
  * 디바이스 메시지가 {{site.data.keyword.iot_short_notm}} 메시지 페이로드 요구사항을 준수해야 합니다.  
자세한 정보는 [{{site.data.keyword.iot_short_notm}}에서 디바이스 개발 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/platform/devices/device_dev_index.html){: new_window}을 참조하십시오.

상황에 따라 다음 옵션을 탐색하십시오.

 |  |서비스가 배치됨 |서비스가 배치되지 않음
 | -------------| ------------- | -------------
  |**연결할 디바이스가 있음** | 이 주제에서 간략히 설명된 프로세스를 따르십시오. |[{{site.data.keyword.iot_short_notm}}으로 재생 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](http://discover-iot.eu-gb.mybluemix.net/?cm_mc_uid=44491599487314618721024&cm_mc_sid_50200000=1462798151#/play){:new_window}에서 디바이스 연결을 탐색합니다.
  |**연결할 디바이스가 없음** | [디바이스 데이터 시뮬레이션](/docs/IoT/devices/device_sim.html) 또는 [스마트폰 연결 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](http://discover-iot.eu-gb.mybluemix.net/?cm_mc_uid=44491599487314618721024&cm_mc_sid_50200000=1462798151#/play/device/smartphone){:new_window}. | [{{site.data.keyword.iot_short_notm}} 스타터](https://console.bluemix.net/docs/IoT-starter/iot500.html#gettingstartedtemplate){:new_window}를 시작합니다.



## 1단계: 디바이스 등록
{: #step1 .sectiontitle}  
디바이스를 등록하려면 디바이스 유형으로 디바이스를 분류하고 디바이스에 이름을 제공하며 디바이스 정보를 제공해야 합니다. 그런 다음 연결 토큰을 제공하거나 {{site.data.keyword.iot_short_notm}}에서 생성된 토큰을 승인합니다.

**팁:** [{{site.data.keyword.iot_short_notm}} 대시보드 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://internetofthings.ibmcloud.com){: new_window}에서 디바이스를 하나씩 등록하거나 [{{site.data.keyword.iot_short_notm}} API ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://docs.internetofthings.ibmcloud.com/apis/swagger/v0002/org-admin.html#!/Device_Bulk_Configuration/post_bulk_devices_add){: new_window}를 사용하여 여러 디바이스를 추가할 수 있습니다.

{{site.data.keyword.iot_short_notm}} 대시보드에서 디바이스를 추가하려면 다음을 수행하십시오.
1. {{site.data.keyword.Bluemix_notm}} 콘솔의 {{site.data.keyword.iot_short_notm}} 서비스 세부사항 페이지에서 **실행**을 클릭하십시오.

    {{site.data.keyword.iot_short_notm}} 웹 콘솔은 새 브라우저 탭에서 다음 URL을 엽니다.

    ```
 https://org_id.internetofthings.ibmcloud.com/dashboard/#/overview
    ```

    여기서 *org_id*는 {{site.data.keyword.iot_short_notm}} 조직의 ID입니다.

2. 개요 대시보드의 메뉴 분할창에서 **디바이스**를 선택한 다음 **디바이스 추가**를 클릭하십시오.

3. 추가하는 디바이스의 디바이스 유형을 작성하십시오.

    {{site.data.keyword.iot_short_notm}}에 연결된 각 디바이스는 디바이스 유형과 연관되어야 합니다. 디바이스 유형은 공통 특성을 공유하는 디바이스 그룹입니다.

    1. **디바이스 유형 작성**을 클릭합니다.
    2. 디바이스 이름(예: `my_device_type`) 및 디바이스 유형에 대한 설명을 입력합니다.

        > **참고:** 디바이스 유형 이름은 36자를 넘지 않아야 하며 영숫자 문자(a-z, A-Z, 0-9) 및 특수 문자 `_`, `.` 및 `-`만 포함할 수 있습니다.

    3. 선택사항: 디바이스 유형 속성 및 메타데이터를 입력합니다.

        속성과 메타데이터는 나중에 추가하고 편집할 수 있습니다.
        {: tip}

4. **다음**을 클릭하여 선택한 디바이스 유형의 디바이스를 추가하는 프로세스를 시작하십시오.

5. 디바이스 ID(예: `my_first_device`)를 입력하십시오.

    디바이스 ID는 {{site.data.keyword.iot_short_notm}} 대시보드에서 디바이스를 식별하는 데 사용하고 디바이스를 {{site.data.keyword.iot_short_notm}}에 연결하는 데도 필요한 매개변수입니다.

    > **참고:** 디바이스 유형 이름은 36자를 넘지 않아야 하며 영숫자 문자(a-z, A-Z, 0-9) 및 특수 문자 `_`, `.` 및 `-`만 포함할 수 있습니다.

    네트워크 연결 디바이스의 경우, 구분하는 콜론이 없는 디바이스 MAC 주소가 디바이스 ID가 될 수 있습니다.

5. **다음**을 클릭하여 프로세스를 완료하십시오.

6. 인증 토큰을 제공하거나 자동으로 생성된 토큰을 허용하십시오. 고유 토큰을 작성하도록 선택하는 경우, 길이는 8 - 36자이고 영숫자 문자와 특수 문자(`_`, `.`, `!`, `&`, `@`, `?`, `\*`, `+`, `(`, `)` 및 `-`로만 구성되어야 합니다.

    토큰에는 반복된 문자 시퀀스, 사전 단어, 사용자 이름 또는 기타 사전 정의된 시퀀스가 포함되지 않아야 합니다.

7. 요약 정보가 올바른지 확인한 후에 **추가**를 클릭하여 연결을 추가하십시오.

8. 디바이스 정보 페이지에서 다음 세부사항을 복사하고 저장하십시오.

    * 조직 ID
    * 디바이스 유형
    * 디바이스 ID
    * 인증 방법
    * 인증 토큰

    디바이스를 {{site.data.keyword.iot_short_notm}}에 연결하도록 구성하려면 조직 ID, 디바이스 유형, 디바이스 ID 및 인증 토큰이 필요합니다.

## 2단계: {{site.data.keyword.iot_short_notm}}에 디바이스 연결
{: #step2 .sectiontitle}  

{{site.data.keyword.iot_short_notm}}에 디바이스를 등록하고 나면 등록 정보를 사용하여 디바이스를 연결하고 디바이스 데이터 수신을 시작할 수 있습니다.

**팁:** 일반적으로 사용되는 일부 디바이스에 대해 {{site.data.keyword.IBM_notm}}.com의 [디바이스 연결 레시피 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://developer.ibm.com/recipes/tutorials/category/internet-of-things-iot/){: new_window}에서 연결 레시피를 사용할 수 있습니다.

디바이스를 {{site.data.keyword.iot_short_notm}}에 연결하려면 다음을 수행하십시오.
1. MQTT 메시징에 대해 디바이스를 설정하고 조직 ID, 디바이스 유형, 디바이스 ID 및 인증 토큰을 사용하여 인증하십시오.

2. MQTT 프로토콜을 사용하여 {{site.data.keyword.iot_short_notm}} 조직에 디바이스 메시지를 보냅니다.

    디바이스에 연결할 때 다음 정보가 필요합니다.

    * URL: *org_id*.messaging.internetofthings.ibmcloud.com

      여기서 *org_id*는 {{site.data.keyword.iot_short_notm}} 조직의 ID입니다.

    * 포트:
      * 1883
      * 8883(암호화됨)
      * 443(websockets)
    * 디바이스 ID: d:_org_id:device_type:device_id_
    * 사용자 이름: use-token-auth
    * 비밀번호: _인증 토큰_
    * 이벤트 주제 형식: iot-2/evt/_event_id/fmt/format_string_

      여기서 _event_id_는 {{site.data.keyword.iot_short_notm}}에 표시된 이벤트 이름을 지정하며, _format_string_은 이벤트의 형식(예: JSON)입니다.

    * 메시지 형식: JSON

  자세한 정보는 [디바이스용 MQTT 연결 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/platform/devices/mqtt.html){:new_window}을 참조하십시오.


## 다음에 수행할 작업  
{: #related .sectiontitle}

디바이스 데이터를 이용하기 위해 고유 앱을 작성 및 연결하여 데이터 분석 기능을 확장합니다.
- 특정 디바이스 유형을 {{site.data.keyword.iot_short_notm}}에 연결하는 방법에 대한 자세한 정보는 [developerWorks 레시피 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://developer.ibm.com/recipes/tutorials/category/internet-of-things-iot/){:new_window}를 참조하십시오.
- 디바이스와 앱을 통합한 후 연결하기 위해 코드를 빌드하도록 도구에 대한 [클라이언트 라이브러리 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/platform/iot_platform_client_lib.html){:new_window}를 체크아웃하십시오.
- [{{site.data.keyword.iot_short_notm}} API 문서](/docs/IoT/reference/api.html)를 탐색하십시오.
- [{{site.data.keyword.cloudantfull}} 서비스 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/platform/cloudant_connector.html){:new_window}를 {{site.data.keyword.iot_short_notm}}에 연결하여 히스토리 디바이스 데이터를 저장하십시오.
- 전체 [{{site.data.keyword.iot_short_notm}} 기능 세트 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/overview/overview.html){:new_window}를 활용하기 위해, 연결 및 분석 서비스 플랜 중 하나를 구매한 후 기존 환경을 마이그레이션할 수 있습니다.

플랜을 마이그레이션하려면 {{site.data.keyword.IBM}} 담당자에게 문의하거나 지원 티켓을 여십시오.

{{site.data.keyword.iot_short_notm}}에서 프로덕션을 위해 준비된 엔드-투-엔드 IoT 프로토타입 시스템을 개발하기 위한 기본사항을 안내하는 시작하기 안내서 및 샘플 애플리케이션 세부사항도 {{site.data.keyword.IBM_notm}} Knowledge Center의 {{site.data.keyword.iot_short_notm}} 제품 문서에서 사용 가능합니다. {{site.data.keyword.iot_short_notm}}에 대한 작업을 처음 수행하는 개발자인 경우 [시작하기 안내서 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/platform/getting_started/getting-started-iot-overview.html#getting-started){:new_window} 섹션의 단계별 프로세스를 사용하십시오.
