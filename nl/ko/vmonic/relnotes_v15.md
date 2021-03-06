---

copyright:

  years:  2016, 2018

lastupdated: "2017-03-30"

---

# V1.5 릴리스 정보

이 릴리스에는 새 기능, 사용성 개선사항 및 버그 수정이 포함됩니다. 다른 릴리스에서 수정된 문제, 제품에 대해 알려진 문제 및 {{site.data.keyword.vmwaresolutions_full}}에 사용할 추가 팁의 목록은 [{{site.data.keyword.vmwaresolutions_short}} dW Answers](https://developer.ibm.com/answers/topics/cloudvmw/){:new_window}를 참조하십시오.

## VRF 대 클래식 SoftLayer 계정 요구사항

클래식 SoftLayer® 계정의 경우, VLAN Spanning은 계정 레벨에서 사용으로 설정될 수 있는 설정입니다. {{site.data.keyword.vmwaresolutions_short}}에서는 VLAN Spanning이 사용으로 설정되어야 합니다.

VRF(Virtual Routing and Forwarding) SoftLayer 계정의 경우, VLAN Spanning은 변경할 수 없는 영구적인 설정과 상응합니다. VRF 계정에 사용자 구성이 필요하지 않습니다.

주문하기 전에 VLAN Spanning이 사용으로 설정된 상태에서 SoftLayer 계정이 VRF 계정인지 또는 클래식(VRF 아님) 계정인지 확인해야 합니다. 그렇지 않으면 주문이 실패할 수 있습니다.

SoftLayer 계정이 VRF 계정인지 확인하려면 IBM Bluemix 지원 센터에 확인하십시오. 클래식 계정의 경우, [LAN Spanning 사용 또는 사용 안함](../../../infrastructure/vlans/vlan-spanning.html){:new_window}의 지시사항에 따라 VLAN Spanning을 사용으로 설정해야 합니다.

## 서비스 비용 모델 업데이트

Cloud Foundation 인스턴스의 경우, 각 노드에 적용되는 월별 요금인 새 _SDDC Manager_ 라이센스가 도입되었습니다. 자세한 정보는 [Cloud Foundation 인스턴스 컴포넌트](../sddc/sd_cloudfoundationoverview.html#cloud-foundation-instance-components)를 참조하십시오.

## 사용성 개선사항

개선사항은 사용자 인터페이스를 통해 수행됩니다.

* 여러 데이터 센터의 사용성 및 데이터 센터에 주문을 수행할 수 있는 충분한 자원 명세가 있는지 여부는 인스턴스 주문 중에 데이터 센터 선택에 대한 올바른 결정을 할 수 있도록 사용자 인터페이스에 명확하게 표시됩니다. 자세한 정보는 [Cloud Foundation 인스턴스에 대한 요구사항 및 계획](../sddc/sd_planning.html) 및 [vCenter Server 인스턴스에 대한 요구사항 및 계획](../vcenter/vc_planning.html)을 참조하십시오.
* Cloud Foundation 인스턴스의 경우, 입력 필드에 필수 정보를 입력하는 동안 인스턴스 이름, 도메인 및 하위 도메인 이름, 데이터 센터 위치와 같은 정보가 그래프 형식으로 자동 표시됩니다. 자세한 정보는 [Cloud Foundation 인스턴스 주문](../sddc/sd_orderinginstance.html)을 참조하십시오.
