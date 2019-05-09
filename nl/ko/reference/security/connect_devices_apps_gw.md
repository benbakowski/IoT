---

copyright:
  years: 2015, 2019
lastupdated: "2019-04-05"

keywords: Client connection URLs, MQTT protocol, device authentication tokens

subcollection: iot-platform

---

{:new_window: target="\_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}
{:pre: .pre}
{:important: .important}

# 애플리케이션, 디바이스 및 게이트웨이에 대한 연결 정보
{: #connect_devices_apps_gw}

<p>이 {{site.data.keyword.cloud}} 문서 콜렉션은 {{site.data.keyword.iot_full}} Lite 가격 플랜과 관계가 있으며 기본 시작하기 정보, API 참조 및 일반 문제점 해결 정보가 포함되어 있습니다.
전체 {{site.data.keyword.iot_short_notm}} 기능 문서는 IBM Knowledge Center의 [{{site.data.keyword.iot_short_notm}} 제품 문서 ![외부 링크 아이콘](../../../../icons/launch-glyph.svg "외부 링크 아이콘")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/overview/overview.html)를 참조하십시오. 다양한 플랜에 대한 자세한 정보는 [{{site.data.keyword.iot_short_notm}} 서비스 플랜](/docs/services/IoT?topic=iot-platform-plans_overview#plans_overview)에서 찾을 수 있습니다.
</p>
{: important}

MQTT 프로토콜을 사용하여 {{site.data.keyword.iot_full}}에 애플리케이션, 디바이스 및 게이트웨이를 연결할 수 있습니다. 또한 HTTP REST API를 사용하여 {{site.data.keyword.iot_short_notm}}에 디바이스를 연결할 수도 있습니다.
{: shortdesc}


## 클라이언트 연결 URL
{: #client_connect_url}

디바이스, 애플리케이션 및 게이트웨이 클라이언트를 {{site.data.keyword.iot_short_notm}} 인스턴스에 연결하려면 다음 연결 URL을 사용하십시오.

### 메시징 주소

<pre class="pre"><var class="keyword varname">orgId</var>.messaging.internetofthings.ibmcloud.com</pre>
{: codeblock}

### HTTP REST API 연결 URL

<pre class="pre"><code class="hljs">https://<var class="keyword varname">orgId</var>.internetofthings.ibmcloud.com/api/v0002/device/types/<var class="keyword varname">typeId</var>/devices/<var class="keyword varname">deviceId</var>/events/<var class="keyword varname">eventId</var></code></pre>
{: codeblock}

**참고**
- 여기서 *orgId*는 서비스 인스턴스를 등록할 때 생성된 고유 조직 ID입니다.
- Quickstart 서비스에 디바이스 또는 애플리케이션을 연결하는 경우 *orgId* 값으로 'quickstart'를 지정하십시오.

### 포트 보안
{: #client_port_security}

디바이스, 게이트웨이 및 애플리케이션은 MQTT 또는 HTTP 프로토콜을 사용하여 {{site.data.keyword.iot_short_notm}}에 연결됩니다. 연결은 비보안(보안이 설정되지 않음) 또는 보안(보안이 설정됨)일 수 있습니다.

|연결 유형 |프로토콜|포트 번호|
|:---|:---|:---|
|비보안*|MQTT 및 HTTP|1883 또는 80|
|보안(TLS)|MQTT 및 HTTPS|8883 또는 443|

&ast; 포트 1883 및 80은 기본적으로 메시징에 사용 안함으로 설정되어 있습니다. 기본 설정 변경에 대한 정보는 [보안 정책 구성 ![외부 링크 아이콘](../../../../icons/launch-glyph.svg "외부 링크 아이콘")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/platform/reference/security/set_up_policies.html#set_up_policies.html){: new_window}을 참조하십시오.

MQTT는 TCP 및 WebSocket에서 지원됩니다. MQTT 클라이언트에서는 디바이스 인증 토큰(디바이스의 경우) 및 API 키와 토큰(애플리케이션의 경우)과 같은 적절한 인증 정보를 사용하여 연결합니다. 비보안 포트 1883에 보내는 MQTT 메시징에서는 일반 텍스트로 인증 정보를 보내므로 항상 보안 대체 포트인 8883 또는 443을 대신 사용하십시오. TLS 인증 정보는 보안 포트에서 전송될 때 항상 암호화됩니다. (예를 들어, Python MQTT 라이브러리에서 `tls_set()` 메소드를 사용하여) 애플리케이션에서 TLS를 사용으로 설정해야 합니다. 그렇지 않으면 데이터가 보안되지 않은 상태로 전송될 수 있습니다.

8883 또는 443 포트에서 보안 MQTT 메시징을 사용하는 경우 새 클라이언트 라이브러리는 {{site.data.keyword.iot_short_notm}}에서 제공하는 기본 인증서를 자동으로 신뢰합니다. 사용자 클라이언트 환경에서 이에 해당되지 않는 경우에는 [messaging.pem ![외부 링크 아이콘](../../../../icons/launch-glyph.svg "외부 링크 아이콘")](https://github.com/ibm-watson-iot/iot-python/blob/master/src/wiotp/sdk/messaging.pem){: new_window}에서 전체 인증서 체인을 다운로드하여 사용할 수 있습니다. 사용자 정의 인증서를 업로드한 경우에는 적절한 신뢰 체인이 클라이언트 환경에 추가되었는지 확인해야 할 수 있습니다.

## 방화벽 구성
{: #firewall_configuration .sectiontitle}

디바이스 및 애플리케이션을 {{site.data.keyword.iot_short_notm}}에 연결하려면 특정 포트의 트래픽을 허용하도록 방화벽이 구성되어 있어야 합니다. 방화벽은 로컬 시스템, 사용자 라우터에 있거나 회사 네트워크 일부로 있을 수 있습니다.

필수 IP 주소가 열려 있고 통신에 사용할 수 있는지 확인하십시오.

|지역 | IP 주소|메시징 포트</br>(비보안) | 메시징 포트(보안)|
|:---|:---|:---| :---|
|us-south|169.45.2.16/28* </br>169.46.7.56/29</br>169.48.234.208/29</br>169.62.202.128/29|1883,80 | 8883,443|
|eu-gb|159.8.169.208/28* </br>158.175.111.152/29</br>158.176.104.24/29</br>141.125.70.152/29|1883,80 | 8883,443|
|eu-de|159.122.121.80/28* </br>149.81.125.176/29</br>158.177.82.208/29</br>161.156.96.80/29|1883,80 | 8883,443|
|Quickstart|169.45.2.16/28* </br>169.46.7.56/29</br>169.48.234.208/29</br>169.62.202.128/29|1883,80 | unavailable|
|데디케이티드 {{site.data.keyword.iot_short_notm}}|{{site.data.keyword.IBM}} 담당자에게 문의하십시오.|-| - |
&ast;2019년 1분기 이후에는 더 이상 사용되지 않습니다.

## TLS 요구사항
{: #tls_requirements}

일부 TLS(Transport Layer Security) 클라이언트 라이브러리에서는 와일드 카드를 포함하는 도메인을 지원하지 않습니다. 라이브러리를 변경할 수 없으면 인증 검사를 사용 안함으로 설정하십시오.

TLS 요구사항은 MQTT 또는 HTTP 프로토콜을 사용하여 {{site.data.keyword.iot_short_notm}}에 연결 중인지 여부에 따라 달라집니다. 다음 절에서는 기본 서버 인증서가 사용되는 경우에 지원되는 암호 스위트를 표시합니다. 자체 클라이언트 인증서를 사용 중인 경우,
지원되는 암호 스위트는 사용되는 인증서에 따라 다릅니다.

### MQTT 연결을 위한 TLS 요구사항

{{site.data.keyword.iot_short_notm}}에서는 TLS v1.2가 필요합니다. 다음 암호 스위트 중 최소한 하나가 허용되는지 확인하십시오.

- TLS_ECDHE_RSA_WITH_AES_128_GCM_SHA256
- TLS_DHE_RSA_WITH_AES_128_GCM_SHA256
- TLS_ECDHE_RSA_WITH_AES_128_CBC_SHA
- TLS_DHE_RSA_WITH_AES_128_CBC_SHA
- TLS_ECDHE_RSA_WITH_AES_256_GCM_SHA384
- TLS_DHE_RSA_WITH_AES_256_GCM_SHA384
- TLS_ECDHE_RSA_WITH_AES_256_CBC_SHA
- TLS_DHE_RSA_WITH_AES_256_CBC_SHA
- TLS_RSA_WITH_AES_128_GCM_SHA256
- TLS_RSA_WITH_AES_256_GCM_SHA384

### HTTP 연결을 위한 TLS 요구사항

기본 서버 인증서를 사용하는 경우에는 {{site.data.keyword.iot_short_notm}}에서 TLS v1.2가 필요합니다. 다음 암호 스위트 중 최소한 하나가 허용되는지 확인하십시오.


- TLS_ECDHE_RSA_WITH_AES_128_CBC_SHA
- TLS_DHE_RSA_WITH_AES_128_CBC_SHA
- TLS_ECDHE_RSA_WITH_AES_256_CBC_SHA
- TLS_DHE_RSA_WITH_AES_256_CBC_SHA
- TLS_RSA_WITH_AES_256_CBC_SHA
- TLS_RSA_WITH_AES_128_CBC_SHA

암호 목록에서 전방향 보안성(forward secrecy) 암호 ECDHE 또는 DHE를 사용하여 암호화의 강도를 높이십시오.

## MQTT 클라이언트 인증
{: #mqtt_authentication}

**중요:** 각 MQTT 클라이언트에는 고유 클라이언트 ID가 필요합니다. 이미 연결된 클라이언트 ID를 사용하여 조직의 클라이언트에 연결하면 첫 번째 연결이 끊깁니다.

{{site.data.keyword.iot_short_notm}}에 직접 연결된 디바이스와 게이트웨이는 현재 연결되어 있음을 표시하기 위해 대시보드에 상태 아이콘이 표시됩니다. 대시보드에서는 게이트웨이를 통해 연결된 디바이스를 인식하지 못하므로 게이트웨이를 통해 간접적으로 연결된 디바이스는 연결이 끊김으로 표시됩니다.

### MQTT 클라이언트 ID

디바이스, 애플리케이션 및 게이트웨이가 성공적으로 인증되도록 다음 클라이언트 ID와 형식을 사용하여 각 MQTT 클라이언트를 정의하십시오.

|클라이언트 유형 |ID|MQTT ID 형식|
|:---|:---|:---|
|애플리케이션|a|<pre class="pre">a:<var class="keyword varname">orgId</var>:<var class="keyword varname">appId</var></pre>
|확장 가능 애플리케이션|A|<pre class="pre">A:<var class="keyword varname">orgId</var>:<var class="keyword varname">appId</var></pre>
|디바이스|d|<pre class="pre">d:<var class="keyword varname">orgId</var>:<var class="keyword varname">deviceType</var>:<var class="keyword varname">deviceId</var></pre>|
|게이트웨이|g|<pre class="pre">g:<var class="keyword varname">orgId</var>:<var class="keyword varname">typeId</var>:<var class="keyword varname">deviceId</var></pre>|

여기서
- *orgId*는 서비스 인스턴스를 등록할 때 생성된 6자의 고유 구성 ID입니다.
- *appId*는 클라이언트의 사용자 정의 고유 문자열 ID입니다.
- *deviceId*는 모든 유형에서 디바이스나 게이트웨이를 고유하게 식별하며 일련 번호와 비슷합니다.
- *device_type*은 연결 중인 디바이스 유형의 ID이며 모델 번호와 비슷합니다.
- *typeId*는 연결 중인 게이트웨이 유형의 ID이며 모델 번호와 비슷합니다.

*appId*, *type_id*, *device_type* 및 *device_id* 값은 36자 이하여야 하며 다음만 포함할 수 있습니다.
- 영숫자 문자(a-z, A-Z, 0-9)
- 대시(-)
- 밑줄(_)
- 점( . )

**참고:**
- Quickstart 서비스에 연결할 때는 인증이 필요하지 않습니다.
- 연결하기 전에 애플리케이션을 등록하지 않아도 됩니다.

공유 구독의 형식에 대한 정보는 [애플리케이션용 MQTT 연결 ![외부 링크 아이콘](../../../../icons/launch-glyph.svg "외부 링크 아이콘")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/platform/applications/mqtt.html){: new_window}을 참조하십시오.


### MQTT을 사용하여 애플리케이션 연결

{{site.data.keyword.iot_short_notm}} 애플리케이션을 조직에 연결하려면 API 키가 필요합니다. API 키를 등록할 때 토큰이 생성되므로 해당 API 키와 사용해야 합니다.

다음 코드에서는 API 키의 예를 제공합니다.

<pre class="pre">a-<var class="keyword varname">orgId</var>-a84ps90Ajs</pre>
{: codeblock}

다음 예제는 일반적인 인증 토큰을 보여줍니다.

```
 MP$08VKz!8rXwnR-Q*
```

API 키를 사용하여 MQTT 연결 시, 다음 요구사항이 충족되는지 확인하십시오.

- MQTT 클라이언트 ID의 형식이 다음과 같습니다. a:*orgId*:*appId*
- MQTT 사용자 이름은 API 키입니다(예: a-*orgId*-a84ps90Ajs).
- MQTT 비밀번호는 인증 토큰입니다(예: *MP$08VKz!8rXwnR-Q**).

자세한 정보는 [애플리케이션용 MQTT 연결 ![외부 링크 아이콘](../../../../icons/launch-glyph.svg "외부 링크 아이콘")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/platform/applications/mqtt.html){: new_window}을 참조하십시오.

### 디바이스 인증

#### 사용자 이름
{{site.data.keyword.iot_short_notm}} 서비스에서는 디바이스의 토큰 기반 인증만 지원하므로 각 디바이스에는 올바른 사용자 이름이 하나뿐입니다.
`use-token-auth`의 값을 사용하여 게이트웨이 또는 디바이스의 인증 토큰을 MQTT 연결의 비밀번호로 사용함을 서비스에 표시합니다.

자세한 정보는 [디바이스용 MQTT 연결 ![외부 링크 아이콘](../../../../icons/launch-glyph.svg "외부 링크 아이콘")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/platform/devices/mqtt.html){: new_window}을 참조하십시오.

#### 비밀번호
클라이언트가 토큰 기반 인증을 사용 중인 경우 모든 MQTT 연결에 대한 비밀번호로 디바이스 인증 토큰을 제출하십시오.
