---

copyright:
  years: 2015, 2019
lastupdated: "2019-04-10"

keywords: IoT Platform organization, SIM devices, IBM Watson

subcollection: iot-platform

---

{:new_window: target="\_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:important: .important}

# 외부 서비스 통합
{: #ref-index}

<p>이 {{site.data.keyword.cloud}} 문서 콜렉션은 {{site.data.keyword.iot_full}} Lite 가격 플랜과 관계가 있으며 기본 시작하기 정보, API 참조 및 일반 문제점 해결 정보가 포함되어 있습니다.
전체 {{site.data.keyword.iot_short_notm}} 기능 문서는 IBM Knowledge Center의 [{{site.data.keyword.iot_short_notm}} 제품 문서 ![외부 링크 아이콘](../../../../icons/launch-glyph.svg "외부 링크 아이콘")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/overview/overview.html)를 참조하십시오. 다양한 플랜에 대한 자세한 정보는 [{{site.data.keyword.iot_short_notm}} 서비스 플랜](/docs/services/IoT?topic=iot-platform-plans_overview#plans_overview)에서 찾을 수 있습니다.
</p>
{: important}

외부 서비스 통합을 사용하면 {{site.data.keyword.iot_full}} 조직에 있는 서드파티 또는 외부 서비스의 오퍼레이션과 데이터에 액세스할 수 있습니다.

## Jasper
{: #jasper}

Jasper는 SIM 디바이스의 관리 플랫폼입니다. Jasper는 {{site.data.keyword.iot_short_notm}} 대시보드에 통합되므로 {{site.data.keyword.iot_short_notm}} 조직 대시보드를 통해 Jasper 디바이스를 관리할 수 있습니다.

### Jasper에 지원되는 오퍼레이션

IBM 플랫폼을 통해 제공되는 기본 제공 Jasper 통합에서는 다음과 같은 Jasper 오퍼레이션을 지원합니다.

- 전체 Jasper 데이터 보기
  - 상태, 요금제, 월별 데이터 사용, 월별 SMS 사용, 월별 음성 사용, 초과 한도, 추가된 날짜 및 수정된 날짜를 표시합니다.
- SIM 활성화 상태 변경
  - 인벤토리, 활성화 준비, 활성화됨, 비활성화됨 및 폐기됨 중에 선택하십시오.
- SIM 사용 보기
  - 주기 시작 날짜, 청구 가능 및 총 데이터, 청구 가능 및 총 SMS, 청구 가능 및 총 음성을 표시합니다.
  - 주기 시작 날짜는 YYYY-MM-DD 날짜 형식을 사용하여 설정할 수 있습니다.
- SIM에 SMS 전송
- 요금제 변경

다음 구성 단계가 완료되고 나면 Jasper에 연결된 디바이스의 디바이스 드릴 다운에서 지원되는 오퍼레이션에 액세스할 수 있습니다.

### Jasper용 REST API
Jasper용 REST API에 액세스하려면 [{{site.data.keyword.iot_short_notm}} HTTP REST API ![외부 링크 아이콘](../../../../icons/launch-glyph.svg "외부 링크 아이콘")](https://docs.internetofthings.ibmcloud.com/apis/swagger/v0002/ext-jasper.html){: new_window} 문서에서 Jasper 확장기능 섹션을 참조하십시오.

### Jasper 구성

{{site.data.keyword.iot_short_notm}} 조직에 Jasper 서비스를 연결하려면 두 단계의 구성을 완료해야 합니다. 먼저 {{site.data.keyword.iot_short_notm}}을 Jasper 서비스에 연결한 다음 {{site.data.keyword.iot_short_notm}} 디바이스를 구성해야 합니다.


1. Jasper 확장기능을 사용하십시오. {{site.data.keyword.iot_short_notm}} 조직과 Jasper를 통합할 수 있으려면 다음 단계를 완료하십시오.
  1. {{site.data.keyword.iot_short_notm}} 대시보드에서 **확장기능**을 선택하십시오.
  2. **확장기능** 페이지에서 **확장기능 추가**를 클릭하십시오.
  3. Jasper 옆의 **추가**를 클릭하십시오.
  4. Jasper 사용자 이름, 비밀번호, 액세스 키 및 도메인 ID를 입력하십시오.
  5. **완료**를 클릭하십시오.

2. 디바이스를 구성합니다.
{{site.data.keyword.iot_short_notm}} 대시보드에서 Jasper의 데이터를 표시하도록 {{site.data.keyword.iot_short_notm}} 조직 및 Jasper 계정에 모두 연결되어 있는 디바이스를 구성할 수 있습니다.  
**중요:** Jasper 구성은 디바이스 추가 프로세스의 일부로 적용할 수 없습니다. 이전에 연결된 디바이스만 Jasper로 구성할 수 있습니다.  
Jasper 연결 디바이스를 구성하려면 다음 단계를 완료하십시오.
 1. {{site.data.keyword.iot_short_notm}} 대시보드의 디바이스 페이지에서, 구성할 Jasper 연결 디바이스를 찾으십시오.
 2. 디바이스 드릴다운 보기를 열 디바이스를 선택하십시오.
 3. 확장기능 구성까지 화면을 아래로 이동하십시오.
 4. 다음 JSON 형식을 사용하여 확장기능 구성을 입력한 다음 **변경 확인**을 클릭하여 구성을 저장하십시오.  

```json  
    {
        "jasper": {
            "iccid": "string"
        }
    }

```

조직이 정상적으로 구성되면 확장기능 섹션이 디바이스 드릴 다운 보기의 확장기능 구성 섹션에 표시됩니다.

## AT&T
{: #att}

### AT&T에 지원되는 오퍼레이션

AT&T 확장기능을 사용하면 다음 AT&T 오퍼레이션을 수행할 수 있습니다.

- 전체 AT&T 데이터 보기
  - 상태, 요금제, 월별 데이터 사용, 월별 SMS 사용, 월별 음성 사용, 초과 한도, 추가된 날짜 및 수정된 날짜를 표시합니다.
- SIM 활성화 상태 변경
  - 인벤토리, 활성화 준비, 활성화됨, 비활성화됨 및 폐기됨 중에 선택하십시오.
- SIM 사용 보기
  - 주기 시작 날짜, 청구 가능 및 총 데이터, 청구 가능 및 총 SMS, 청구 가능 및 총 음성을 표시합니다.
  - 주기 시작 날짜는 YYYY-MM-DD 날짜 형식을 사용하여 설정할 수 있습니다.
- SIM에 SMS 전송
- 요금제 변경

### AT&T용 REST API
AT&T용 REST API에 액세스하려면 [{{site.data.keyword.iot_short_notm}} HTTP REST API ![외부 링크 아이콘](../../../../icons/launch-glyph.svg "외부 링크 아이콘")](https://docs.internetofthings.ibmcloud.com/apis/swagger/v0002/ext-atnt.html){: new_window} 문서에서 AT&T 확장 섹션을 참조하십시오.

### AT&T의 구성

{{site.data.keyword.iot_short_notm}} 조직을 AT&T에 연결하려면 조직 구성 및 디바이스 구성을 완료해야 합니다.

{{site.data.keyword.iot_short_notm}} 플랫폼을 구성하려면 다음 단계를 완료하십시오.

1. AT&T 확장 기능을 사용하십시오. AT&T와 {{site.data.keyword.iot_short_notm}} 조직을 통합할 수 있으려면 다음 단계를 완료하십시오.
  1. {{site.data.keyword.iot_short_notm}} 대시보드에서 **확장기능**을 선택하십시오.
  2. **확장기능** 페이지에서 **확장기능 추가**를 클릭하십시오.
  3. AT&T 옆의 **추가**를 클릭하십시오.
  4. AT&T 사용자 이름, 비밀번호, 액세스 키 및 도메인 ID를 입력하십시오.
  5. **완료**를 클릭하십시오.

{{site.data.keyword.iot_short_notm}} 조직을 AT&T 계정과 연결하려면 두 단계의 구성을 완료해야 합니다. 조직 구성을 완료한 다음 디바이스를 구성하십시오.


2. 디바이스를 구성하십시오.
{{site.data.keyword.iot_short_notm}} 대시보드에서 AT&T의 데이터를 표시하도록 {{site.data.keyword.iot_short_notm}} 조직과 AT&T 계정에 모두 연결된 디바이스를 구성할 수 있습니다.  
**중요:** AT&T 구성은 디바이스 추가 프로세스의 일부로 적용할 수 없습니다. 이전에 연결된 디바이스만 AT&T로 구성할 수 있습니다.  
AT&T 연결 디바이스를 구성하려면 다음 단계를 완료하십시오.
 1. {{site.data.keyword.iot_short_notm}} 대시보드의 디바이스 페이지에서 구성할 AT&T 연결 디바이스를 찾으십시오.
 2. 디바이스 드릴다운 보기를 열 디바이스를 선택하십시오.
 3. 확장기능 구성까지 화면을 아래로 이동하십시오.
 4. 다음 JSON 형식을 사용하여 확장기능 구성을 입력한 다음 **변경 확인**을 클릭하여 구성을 저장하십시오.  

```json  
    {
        "atnt": {
            "iccid": "string"
        }
    }

```

조직이 정상적으로 구성되면 확장기능 섹션이 디바이스 드릴 다운 보기의 확장기능 구성 섹션에 표시됩니다.

## Arm Mbed 브릿지
{: #arm}

브릿지를 사용하여 Arm Mbed 디바이스는 {{site.data.keyword.iot_short_notm}}과 통합하고 메시지를 양방향으로 교환할 수 있습니다. 이 통합을 사용하려면 우선 Arm Mbed Cloud 계정에 등록한 후에 {{site.data.keyword.iot_short_notm}} 구성에 대해 요청된 연결 정보를 제공해야 합니다.

### 구성 설정


1. Arm Mbed 브릿지 확장기능 사용을 설정하십시오. 확장기능을 사용하려면 다음 단계를 완료하십시오.
  1. {{site.data.keyword.iot_short_notm}} 대시보드에서 **확장기능**을 선택하십시오.
  2. 확장기능 페이지에서 **확장기능 추가**를 클릭하십시오.
  3. Arm Mbed 브릿지 확장기능 옆의 **추가**를 클릭하십시오.
  4. Arm Mbed 액세스 키를 입력하십시오. Arm Mbed 포털([https://portal.mbedcloud.com ![외부 링크 아이콘](../../../../icons/launch-glyph.svg "외부 링크 아이콘")](https://portal.mbedcloud.com){: new_window})을 사용하여 작성할 수 있습니다.
  5. **연결 확인** 단추를 클릭하여 인증 정보가 올바른지 확인하십시오.
  6. **완료**를 클릭하십시오.

### 페이로드 형식

Arm Mbed 플랫폼은 두 가지 유형의 수신 메시지(알림 및 비동기 응답)를 사용합니다. {{site.data.keyword.iot_short_notm}}은 Arm Mbed 플랫폼에 연결된 디바이스로 명령을 보낼 수 있습니다.

#### 알림

디바이스 또는 센서 데이터의 변경사항에 의해 알림이 생성됩니다. {{site.data.keyword.iot_short_notm}}에서 메시지를 처리하고 나면 {{site.data.keyword.iot_short_notm}}에 직접 연결된 디바이스와 동일한 방식으로 디바이스 이벤트 주제에 전송됩니다. Arm Mbed 플랫폼에 연결된 디바이스에서 시작되는 알림에 사용되는 이벤트 유형은 `notify`입니다.

다음 코드 샘플은 Arm Mbed 플랫폼 API에서 전송한 알림에 대한 페이로드 형식을 표시합니다.

```
{
  "ep":<endpoint/deviceID>,
  "path":<resource path>,
  "ct":<content type>,
  "payload":<Base64 encoded payload>,
  "max-age":<how long the payload is valid, in seconds>
}
```

#### 비동기 응답

{{site.data.keyword.iot_short_notm}}이 Arm Mbed 플랫폼에 연결된 디바이스로 명령을 보내면, 디바이스는 확인 메시지를 다시 {{site.data.keyword.iot_short_notm}}에 보냅니다. 이 확인 메시지는 _비동기 응답_이라고 하며 이벤트 유형 `asyncResponse`를 사용합니다.

다음 코드 샘플은 Arm Mbed 클라우드 서비스에서 보낸 비동기 응답의 페이로드 형식을 표시합니다.

```
{
  "id":<transaction id>,
  "status":<200 is command was sucessfully executed. Check other HTTP response codes>,
  "ct":<content type>,
  "max-age":<how long the payload is valid, in seconds>,
  "payload":<base64 encoded payload>,
  "ep":<endpoint/deviceID affected by the command>,
  "path":<resource path affected by the command>
}
```

#### Arm Mbed 플랫폼에 명령 전송

{{site.data.keyword.iot_short_notm}}은 Arm Mbed 플랫폼에 연결된 디바이스로 명령을 보낼 수 있습니다. Arm Mbed 플랫폼으로 전송되는 명령은 다음 JSON 형식을 사용해야 합니다.

```
{
  "method":<PUT or POST>,
  "deviceId":<endpoint/deviceId>,
  "resourceId":<resource path>,
  "payload": <Base64 encoded payload>
}
```
선택한 메소드는 대소문자를 구분합니다. 리소스 경로의 처음 `/`는 건너뛰어야 합니다.


페이로드는 다음 주제에서 공개되어야 합니다.

```
iot-2/type/<device_type>/id/<deviceId>/cmd/<command_type>/fmt/<command_format>
```

<!--
## Orange
{: #orange}

The Orange extension allows you to view SIM card data from devices that are connected to your {{site.data.keyword.iot_short_notm}} and have an Orange SIM card installed.

### Supported operations for Orange

If you have a device that is connected to your {{site.data.keyword.iot_short_notm}} service and has an Orange SIM card, you can use the Orange extension to view the following SIM card data:

- SIM serial number
- Activation status
- Last status change
- Last status refresh
- Location status

### REST APIs for Orange
To access the REST API for Orange, see the Orange Extension section in the [{{site.data.keyword.iot_short_notm}} HTTP REST API ![External link icon](../../../../icons/launch-glyph.svg "External link icon")](https://docs.internetofthings.ibmcloud.com/apis/swagger/v0002/ext-orange.html){: new_window} documentation.

### Configuration for Orange

To enable the Orange extension:

1. From the {{site.data.keyword.iot_short_notm}} dashboard, select **Extensions**.
2. On the **Extensions** page, click **Add Extension**.
3. Click **Add** next to the Orange extension.
4. Enter your Orange user name and password.
6. Click **Done**.

After the Orange extension has been enabled, each device that has an Orange SIM card must be configured to display Orange SIM data.

1. In the devices tab of your {{site.data.keyword.iot_short_notm}} dashboard, find the Orange SIM device to configure.
2. Select the device and scroll down to **Extension Configuration**.
3. Enter the extension configuration by using the following JSON format and then click **Confirm changes** to save your configuration.

```json
    {
        "orange": {
            "serialnumber": "<serial number of Orange SIM>"
        }
    }

```
When the organization is successfully configured, the Extensions section is displayed under the Extensions Configuration section in the Device Drilldown view.
-->

## 히스토리 데이터 스토리지
{: #historical_data}

히스토리 데이터 스토리지 확장 기능을 사용하면 IoT 데이터에 대해 호환 가능한 메시지 스토리지 서비스(예: [{{site.data.keyword.cloudantfull}} ![외부 링크 아이콘](../../../../icons/launch-glyph.svg "외부 링크 아이콘")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/platform/cloudant_connector.html){: new_window} 또는 [{{site.data.keyword.messagehub_full}} ![외부 링크 아이콘](../../../../icons/launch-glyph.svg "외부 링크 아이콘")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/platform/message_hub.html){: new_window})를 찾아 구성할 수 있습니다.

## 사용자 정의 디바이스 관리 패키지
{: #device_mgmt}

디바이스 관리는 {{site.data.keyword.iot_short_notm}}의 코어 기능이지만 이를 확장하여 추가 기능을 개발할 수 있습니다.  사용자 정의 디바이스 관리 패키지는 올바른 JSON으로 구성되어야 하며 최소한 하나의 사용자 정의 디바이스 관리 조치를 정의해야 합니다.

필수 JSON 형식의 예제를 포함하여 사용자 정의 디바이스 관리 기능에 대한 자세한 정보는 [디바이스 관리 사용자 정의 확장기능 ![외부 링크 아이콘](../../../../icons/launch-glyph.svg "외부 링크 아이콘")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/platform/devices/device_mgmt/custom_actions.html){: new_window}을 참조하십시오.

### 사용자 정의 디바이스 관리 패키지 추가

{{site.data.keyword.iot_short_notm}} 대시보드를 사용하거나 API를 사용하여 사용자 정의 디바이스 관리 패키지를 추가할 수 있습니다.

{{site.data.keyword.iot_short_notm}} 대시보드를 사용하여 사용자 정의 디바이스 관리 패키지를 추가하려면 다음을 수행하십시오.

1. {{site.data.keyword.iot_short_notm}} 대시보드의 탐색줄에서 **설정**을 클릭하십시오.
2. **사용자 정의 디바이스 관리 패키지**를 클릭하십시오.
3. **패키지 추가** 단추를 클릭하십시오.
4. 패키지 파일을 선택하고 **열기**를 클릭하십시오.

API를 사용하여 사용자 정의 디바이스 관리 패키지를 추가하려면 [{{site.data.keyword.iot_short_notm}} API 문서 ![외부 링크 아이콘](../../../../icons/launch-glyph.svg "외부 링크 아이콘")](https://docs.internetofthings.ibmcloud.com/apis/swagger/v0002/orgAdmin.html){: new_window}를 참조하십시오.

## 이메일
{: #email}

사용자는 이메일 초대를 사용하여 {{site.data.keyword.iot_short_notm}}에 추가될 수 있습니다. 자세한 정보는 [사용자 액세스 관리](/docs/services/IoT?topic=iot-platform-managing-user-access#managing-user-access)를 참조하십시오.

이메일 초대 기능을 사용하려면, 이메일 확장기능이 SendGrid 온라인 서비스 또는 SMTP(Simple Mail Transfer Protocol) 서비스를 사용하도록 구성되어 있어야 합니다. 이메일 확장기능은 SendGrid {{site.data.keyword.cloud_notm}} 애플리케이션을 사용할 수도 있습니다.

### SendGrid 온라인 서비스

SendGrid 온라인 서비스와 함께 사용하도록 이메일 확장기능을 구성하려면 다음 단계를 따르십시오.

1. SendGrid 온라인 계정에서 인증 API 키를 검색하십시오.
2. {{site.data.keyword.iot_short_notm}} 대시보드의 탐색줄에서 **확장기능**을 클릭하십시오.
3. **이메일** 섹션에서 **설정**을 클릭하십시오.
4. **API 키가 있는 SendGrid**를 선택하십시오.
5. 사이트 관리자의 이름과 이메일 주소 및 권한이 부여된 API 키를 입력하십시오.

### SMTP 서비스

SMTP 서비스와 함께 사용하도록 이메일 확장기능을 구성하려면 다음 단계를 따르십시오.

1. {{site.data.keyword.iot_short_notm}} 대시보드의 탐색줄에서 **확장기능**을 클릭하십시오.
2. **이메일** 섹션에서 **설정**을 클릭하십시오.
3. **SMTP**를 선택하십시오.
4. SMTP 서비스의 구성 세부사항을 입력하십시오.

### SendGrid {{site.data.keyword.cloud_notm}} 애플리케이션

SendGrid {{site.data.keyword.cloud_notm}} 애플리케이션과 함께 사용하도록 이메일 확장기능을 구성하려면 다음 단계를 따르십시오.

1. 더미 애플리케이션을 작성하고 SendGrid 서비스를 바인드하십시오.  
구성 인증 정보를 검색하려면 더미 애플리케이션에 SendGrid 서비스를 추가하고 바인드하십시오.

 1. {{site.data.keyword.cloud_notm}} 대시보드에서 **서비스 작성**을 클릭하십시오.
 2. 카탈로그에서 SendGrid 서비스를 선택하고 **작성**을 클릭하십시오.
 3. {{site.data.keyword.cloud_notm}} 대시보드에서 {{site.data.keyword.runtime_nodejs_full}} 애플리케이션을 추가하십시오.
 4. {{site.data.keyword.cloud_notm}} 대시보드에서 {{site.data.keyword.runtime_nodejs_notm}} 애플리케이션을 클릭하고 **서비스 또는 API 바인드**를 클릭하십시오.
 5. SendGrid 서비스를 선택하고 **추가**를 클릭하십시오.
 6. {{site.data.keyword.runtime_nodejs_notm}} 애플리케이션을 다시 스테이징하십시오.
2. {{site.data.keyword.iot_short_notm}} 서비스 구성을 준비하십시오.  
{{site.data.keyword.iot_short_notm}}은 {{site.data.keyword.iot_short_notm}} 대시보드를 사용하거나 {{site.data.keyword.iot_short_notm}} API를 사용하여 구성될 수 있습니다.  
 1. {{site.data.keyword.cloud_notm}} 대시보드에서 {{site.data.keyword.runtime_nodejs_notm}} 애플리케이션을 클릭하십시오.
 2. 탐색줄에서 **환경 변수**를 클릭하십시오.
 3. 임시 텍스트 파일에 표시된 JSON을 복사하십시오.  
 JSON은 다음 형식이어야 합니다.
```
{
  "name": "SendGridServiceName",
  "label": "user-provided",
  "credentials": {
    "password": "xxx",
    "hostname": "smtp.sendgrid.net",
    "username": "username"
  }
}
```
3. 구성 데이터를 {{site.data.keyword.iot_short_notm}} 조직에 추가하십시오.
 1. {{site.data.keyword.iot_short_notm}} 대시보드를 여십시오.
 2. 탐색줄에서 **확장기능**을 클릭하십시오.
 3. **이메일** 아이콘 아래의 **설정**을 클릭하십시오.
 4. **사용자 이름이 있는 SendGrid**를 선택하십시오.
 5. 임시 텍스트 파일의 구성 데이터를 입력하십시오.
 6. **완료**를 클릭하십시오.
