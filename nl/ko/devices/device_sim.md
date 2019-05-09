---

copyright:
  years: 2017, 2019
lastupdated: "2019-04-05"

keywords: device simulator, devices

subcollection: iot-platform

---

{:new_window: target="blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}
{:important: .important}


# 디바이스 데이터 시뮬레이션
{: #sim_device_data}

<p>이 {{site.data.keyword.cloud}} 문서 콜렉션은 {{site.data.keyword.iot_full}} Lite 가격 플랜과 관계가 있으며 기본 시작하기 정보, API 참조 및 일반 문제점 해결 정보가 포함되어 있습니다.
전체 {{site.data.keyword.iot_short_notm}} 기능 문서는 IBM Knowledge Center의 [{{site.data.keyword.iot_short_notm}} 제품 문서 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/overview/overview.html)를 참조하십시오. 다양한 플랜에 대한 자세한 정보는 [{{site.data.keyword.iot_short_notm}} 서비스 플랜](/docs/services/IoT?topic=iot-platform-plans_overview#plans_overview)에서 찾을 수 있습니다.
</p>
{: important}

{{site.data.keyword.iot_full}} 디바이스 시뮬레이터를 사용하여 디바이스에 시뮬레이션된 이벤트를 설정하여 실제 디바이스를 등록하고 연결하지 않고 완전히 작동하는 {{site.data.keyword.iot_short_notm}} 기능을 알아보고 테스트하고 보여줄 수 있습니다.
{: shortdesc}

디바이스 시뮬레이터를 사용하여 기존 디바이스 유형에 해당하는 시뮬레이션된 디바이스를 작성하거나 새 디바이스 유형과 디바이스를 작성할 수 있습니다. 각 시뮬레이션된 디바이스는 고유한 이벤트 세부사항을 사용할 수 있지만 모든 디바이스에 적용되는 기본 구성을 작성할 수도 있습니다.

## 시작하기 전에
{: #byb-simulation .sectiontitle}
사용자 ID에 대한 디바이스 시뮬레이션을 사용으로 설정하십시오. 
1. {{site.data.keyword.iot_short_notm}}에 로그인하십시오.
2. 기본 탐색 분할창에서 **설정**을 선택하십시오.
3. **데이터 및 디바이스** 섹션에서 디바이스 시뮬레이터를 활성화하십시오.

사용자 ID에 디바이스 시뮬레이션이 사용으로 설정된 경우 {{site.data.keyword.iot_short_notm}} 대시보드에 로그인하면 사용으로 설정된 모든 시뮬레이션된 디바이스가 자동으로 시작됩니다.

## 디바이스 시뮬레이션
{: #process-simulation .sectiontitle}
활성화되면 모든 대시보드 페이지에서 디바이스 시뮬레이터를 사용할 수 있습니다. 화면의 오른쪽 하단 구석에 있는 메시지에 실행되고 있는 시뮬레이션의 수가 표시됩니다.

**중요:** 사용자 ID에 대해 정의한 시뮬레이션된 디바이스 및 디바이스 유형은 {{site.data.keyword.iot_short_notm}} 조직의 다른 사용자가 사용할 수 있습니다. 그러나 디바이스의 시뮬레이션된 데이터를 생성하려면 활성 사용자 세션의 {{site.data.keyword.iot_short_notm}} 대시보드에 로그인해야 합니다.

디바이스 데이터를 시뮬레이션하려면 다음을 수행하십시오.
1. {{site.data.keyword.iot_short_notm}} 대시보드에서 "0개의 시뮬레이션 실행 중" 메시지를 클릭하십시오.
3. 열린 **시뮬레이션** 구성 창에서 **시뮬레이션 작성**을 클릭하십시오.
4. 시뮬레이션 세부사항을 구성하십시오.  
**시뮬레이션 가져오기/내보내기**를 클릭하여 [기존 구성](#reuse)을 가져오거나 세부사항을 수동으로 구성하십시오.
   1. 데이터를 시뮬레이션할 기존의 디바이스 유형을 선택하거나 디바이스 유형 이름을 입력하여 새 디바이스를 작성하십시오.
   2. 이벤트 유형의 기본 이름을 수정하십시오.
   3. **스케줄** 아래에서 이벤트 빈도를 설정하십시오.
   4. 이벤트 페이로드를 편집하십시오.  
   특성 및 해당 값을 추가하여 샘플 JSON 페이로드를 편집하거나 [함수](#functions)를 사용하여 동적으로 생성된 데이터 포인트를 추가하십시오.  
   [CSV 이벤트 페이로드 파일](#csv)을 업로드하여 페이로드를 설정할 수도 있습니다.  
   {: tip}
5. 디바이스 유형에 추가 이벤트 유형을 추가하고 구성하려면 **새 이벤트 유형**을 클릭하십시오.
5. **이벤트를 히스토리 데이터로 저장**을 사용으로 설정하여 시뮬레이션된 디바이스 상태 데이터를 나중에 액세스할 수 있도록 하십시오.  
히스토리 데이터가 사용으로 설정되면 {{site.data.keyword.iot_short_notm}} [데이터 관리 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/platform/GA_information_management/ga_im_definitions.html){: new_window} 컴포넌트가 작성되며 시뮬레이션된 디바이스 상태를 연관된 논리 인터페이스에서 액세스할 수 있습니다.  
**중요:** 디바이스 유형을 사용으로 설정하여 히스토리 데이터를 저장한 후에는 이벤트 유형을 추가 또는 삭제할 수 없으며 이벤트 페이로드에 있는 필드를 수정할 수 없습니다.
5. **저장**을 클릭하여 디바이스 유형을 작성하십시오.  
이제 하나 이상의 시뮬레이션된 디바이스를 작성할 준비가 되었습니다.
6. **시뮬레이션된 디바이스 작성**을 클릭하여 디바이스를 작성하고 데이터 전송을 시작하십시오.  
**팁:** 두 개 이상의 디바이스를 작성하려면 **1 x**를 클릭하고 작성할 디바이스의 수를 선택하십시오.  
7. 더 많은 시뮬레이션을 작성하려면, **새 시뮬레이션**을 클릭하고 사용자 정의 설정을 적용할 각 디바이스에 대해 구성 단계를 반복하십시오.   
화면의 오른쪽 하단에 있는 메시지는 활성 시뮬레이션의 수를 표시합니다.
8. **디바이스** 페이지에서 시뮬레이션된 디바이스 중 하나로 이동하고 **최근 이벤트** 탭을 선택하여 시뮬레이션된 이벤트가 작동 중인지 확인하십시오.

재사용 또는 공유를 위해 [시뮬레이션된 이벤트 구성을 내보내기](#reuse)할 수 있습니다.

## 이벤트 유형 함수
{: #functions .sectiontitle}

많은 특수 함수를 사용하여 이벤트 유형에 대한 동적 데이터를 작성할 수 있습니다.

함수 | 사용법 |예제  
:--- | :---  | :--  
`random(lower, upper)`  | 지정된 범위에서 난수를 생성합니다.  | `{"random": random(0, 100)}`  
`$counter` | 현재 유형의 시뮬레이션된 디바이스 수를 표시합니다. | `{"total": $counter}`  
`increment(start, increment)` | 시작 값과 증가되는 증분 값을 지정합니다. |`{"myNumber": increment(10, 1)}` </br> 이 예제에서 `myNumber`는 10에서 시작하여 페이로드가 전송될 때마다 1씩 증가합니다.


## CSV 이벤트 페이로드 파일
{: #csv .sectiontitle}

특정 시나리오에 대해 제어된 이벤트 데이터를 작성하려는 경우 CSV 입력 파일에 데이터 플로우를 설정할 수 있습니다.

### 요구사항
CSV 파일은 다음 요구사항을 충족해야 합니다.
- 각 값은 다음 사항을 제외하고 유효한 [JSON 기본요소 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://json.org){: new_window}입니다.
  - 문자열:   
  예: "Hello world"
  - 숫자:  
  예: 0, 0.1, -22, -2.43
  - 부울:  
  true 또는 false
  - 널:  
  널
  - **지원되지 않음:**
    - 오브젝트  
    예: {}
    - 배열  
    예: []
- 값은 쉼표로 구분해야 합니다.
- 행은 줄 바꾸기 문자(`\n`)로 구분해야 합니다.
- 헤더 행은 문자열 값으로만 구성되어야 합니다.


### 샘플 CSV 파일
```
"temperature", "confidence","status"
1, 0.1, "normal"
2, 0.2, "normal"
3, 0.3, "error"
4, 0.4, "normal"
```

첫 번째 행 또는 "헤더 행"은 생성된 모든 디바이스 JSON 이벤트 오브젝트의 디바이스 JSON에 포함된 특성을 판별합니다.
각 후속 행 또는 "데이터 행"은 각 생성된 디바이스 JSON 이벤트 오브젝트의 해당 특성 값을 설정합니다.

**팁:** CSV 파일을 가져올 때 **파일에서 시뮬레이션된 데이터 루프**를 선택하여 데이터 행을 순차적으로 순환시켜 연속적인 데이터 피드를 달성할 수 있습니다. 이 토글이 설정되지 않은 경우 CSV의 각 데이터 행은 스케줄에 의해 설정된 빈도로 한 번 전송됩니다.

샘플 CSV 파일은 다음 유형의 이벤트 페이로드를 생성합니다.
```JSON
{
  "temperature": 1,
  "confidence": 0.1,
  "status": "normal"
}
```

## 시뮬레이션 공유 및 재사용
{: #reuse .sectiontitle}

재사용 또는 공유를 위해 다음과 같이 시뮬레이션 세부사항을 내보낼 수 있습니다.
1. **시뮬레이션** 창에서 **가져오기/내보내기**를 클릭하십시오.
2. **내보내기** 탭을 선택하십시오.
3. 시뮬레이션 세부사항을 클립보드에 복사하거나 JSON 파일에 다운로드하십시오.
