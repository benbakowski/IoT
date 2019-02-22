---

copyright:
  years: 2016, 2019
lastupdated: "2019-02-13"

---

{:new_window: target="blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:important: .important}

# 사용자 액세스 관리
{: #managing-user-access}

<p>이 {{site.data.keyword.Bluemix}} 문서 콜렉션은 {{site.data.keyword.iot_full}} Lite 가격 플랜과 관계가 있으며 기본 시작하기 정보, API 참조 및 일반 문제점 해결 정보가 포함되어 있습니다.
전체 {{site.data.keyword.iot_short_notm}} 기능 문서는 IBM Knowledge Center의 [{{site.data.keyword.iot_short_notm}} 제품 문서 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/overview/overview.html)를 참조하십시오. 다양한 플랜에 대한 자세한 정보는 [{{site.data.keyword.iot_short_notm}} 서비스 플랜](/docs/IoT/plans_overview.html#plans_overview)에서 찾을 수 있습니다.
</p>
{: important}

대시보드의 구성원 페이지에서 {{site.data.keyword.iot_full}} 조직에 대한 액세스를 제어 및 관리할 수 있습니다. 사용자 추가, 초대 또는 가져오기로 사용자를 추가할 수 있습니다. 또한 역할을 지정하여 사용자에 대해 다양한 액세스 레벨을 부여할 수도 있습니다.
{:shortdesc}

## 사용자 추가
{: #adding-new-users}

대시보드의 **구성원** 페이지에서 추가 기능을 사용하여 개별 구성원을 추가할 수 있습니다. 또한 가져오기 기능을 사용하여 여러 구성원을 동시에 추가할 수 있습니다.

기본적으로, 구성원 계정은 만료되지 않습니다. 사용자를 {{site.data.keyword.iot_short_notm}} 조직에 추가할 때 선택적으로 해당 계정에 대한 만료 날짜를 설정할 수 있습니다.

### {{site.data.keyword.iot_short_notm}} 조직에 구성원 추가

조직에 구성원을 추가하려면 구성원의 IBM ID가 필요합니다. 구성원 추가를 위해 구성원의 확인을 받을 필요는 없습니다.

{{site.data.keyword.iot_short_notm}} 조직에 단일 구성원을 추가하려면 다음을 수행하십시오.
1. {{site.data.keyword.iot_short_notm}} 대시보드의 탐색줄에서 **구성원**을 클릭하십시오.
2. **구성원 추가**를 클릭하고 **추가** 탭을 선택하십시오.
3. 구성원의 IBM ID를 입력하십시오.
4. 구성원의 역할을 선택하십시오.
5. 선택사항: 만료 날짜를 설정하십시오.
6. **추가**를 클릭하십시오.

여러 구성원을 동시에 추가하려면 IBM ID, 역할 및 각 구성원에 대한 만료 날짜가 포함된 `.csv` 파일을 업로드해야 합니다. 관련 정보는 [CSV 파일 생성](#constructing-your-csv)을 참조하십시오.
1. {{site.data.keyword.iot_short_notm}} 대시보드의 탐색줄에서 **구성원**을 클릭하십시오.
2. **구성원 추가**를 클릭하고 **가져오기** 탭을 선택하십시오.
3. 파일을 찾아보거나 `.csv` 파일을 **CSV 업로드** 창으로 끌어오십시오.
4. CSV 파일에 지정된 역할이 인식되지 않는 경우 사용할 기본 역할을 선택하십시오.
5. CSV 파일의 열 번호를 해당하는 IBM ID, 역할 및 선택적 만료 날짜 항목에 맵핑하십시오.
6. `.csv` 파일에 사용된 구분 기호와 일치하도록 적절한 쉼표 또는 세미콜론 열 구분 기호를 선택하십시오.
7. IBM ID를 가져오고 구성원을 작성하려면 **가져오기**를 클릭하십시오.


### CSV 파일 생성
{: #constructing-your-csv}

조직에 구성원을 가져오기 위해 CSV 파일을 생성할 때는 사용 중인 메소드에 대한 필수 정보를 반드시 포함해야 합니다. 쉼표 또는 세미콜론을 사용하여 열을 구분하십시오.  
**중요:** CSV 파일을 업로드하는 경우 **CSV 설정** 아래에서 올바른 열 구분 기호를 선택했는지 확인하십시오.

샘플 CSV 파일(쉼표 구분 기호 사용):  
```
user1@sample.com,PD_DEVELOPER_USER,2018-03-13
user2@sample.com,PD_OPERATOR_USER,2018-03-13
user3@sample.com,PD_ADMIN_USER,2018-03-13
```
다음 열 항목이 사용되는 위치:  
- 1열: 사용자의 이메일 주소.  
구성원을 추가하는 경우 올바른 IBM ID에 해당하는 이메일 주소를 사용해야 합니다. 구성원을 초대하는 경우에는 모든 올바른 이메일 주소를 사용할 수 있습니다.
- 2열: 사용자에게 지정될 역할.  
다음 역할 중 하나를 입력하십시오.
 - PD_ADMIN_USER
 - PD_OPERATOR_USER
 - PD_DEVELOPER_USER
 - PD_ANALYST_USER
 - PD_READER_USER  
사용자 역할에 대한 자세한 정보는 [사용자, 애플리케이션, 게이트웨이 역할 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/platform/roles_index.html#user_roles){: new_window}을 참조하십시오.
- 3열: 사용자 만료 날짜에 해당하는 ISO 6801 날짜(예: `2018-03-13`).

## 사용자 편집
{: #editing-users}

사용자를 편집하여 해당 역할을 변경하고 액세스 만기 날짜를 추가, 제거 또는 변경하거나 조직에 대한 액세스 권한을 추가 또는 제거할 수 있습니다.

1. {{site.data.keyword.iot_short_notm}} 대시보드의 탐색줄에서 **구성원**을 클릭하십시오.
2. 편집하려는 사용자 옆의 **편집** 아이콘을 클릭하십시오.
3. 원하는 대로 사용자를 변경하십시오.
4. **저장**을 클릭하십시오.

## 사용자 액세스 차단
{: #blocking-users}

조직 멤버십은 그대로 유지하면서 {{site.data.keyword.iot_short_notm}} 조직에 액세스하지 못하도록 사용자를 차단할 수 있습니다.

1. {{site.data.keyword.iot_short_notm}} 대시보드의 탐색줄에서 **구성원**을 클릭하십시오.
2. {{site.data.keyword.iot_short_notm}} 조직에 액세스하지 못하도록 차단할 사용자 옆의 토글 단추를 클릭하십시오.

## 사용자 액세스 제한
{: #limiting-users}

리소스 레벨 액세스 제어를 통해 조직의 디바이스에 대한 액세스를 제한할 수 있습니다. 리소스 그룹을 사용하여 각 사용자 또는 API 키가 관리할 수 있는 디바이스를 지정할 수 있습니다. 리소스 레벨 액세스 제어를 구성하는 방법에 대한 정보는 [ 리소스 레벨 액세스 제어 구성 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/platform/reference/rlac.html#configure_RLAC){: new_window}을 참조하십시오.

## 사용자 제거
{: #removing-users}

사용자를 {{site.data.keyword.iot_short_notm}} 조직에서 완전히 제거할 수 있습니다. 사용자 제거는 취소될 수 없으며, 액세스 권한을 복원하려면 사용자를 [플랫폼에 추가](#adding-new-users)해야 합니다.

1. {{site.data.keyword.iot_short_notm}} 대시보드의 탐색줄에서 **구성원**을 클릭하십시오.
2. 제거할 사용자 옆의 **삭제** 아이콘을 클릭하십시오.
3. 확인 대화 상자에서 **삭제**를 클릭하십시오.
