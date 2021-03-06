---

copyright:

  years:  2016, 2018

lastupdated: "2018-06-14"

---

# FortiGate Security Appliance on IBM Cloud 개요

FortiGate Security Appliance on {{site.data.keyword.cloud}} 서비스는 고가용성 모드에서 방화벽, 라우팅, NAT 및 VPN 서비스를 제공하도록 FSA(FortiGate Security Appliance) 300 시리즈 디바이스의 쌍을 배치하여 인스턴스의 공인 VLAN에서 모든 서버 및 가상 머신을 보호합니다.

SSH를 통해 FortiOS Web Client 또는 명령 인터페이스를 사용하여 이 서비스를 관리할 수 있습니다.

**가용성**: 이 서비스는 V1.8 이상 릴리스에 배치된 인스턴스에서만 사용 가능합니다.

## FortiGate Security Appliance on IBM Cloud의 컴포넌트

인스턴스에 대한 FortiGate Security Appliance on {{site.data.keyword.cloud_notm}} 서비스를 주문할 때 기존 인스턴스 또는 클러스터의 기본 공인 VLAN에 FortiGate Security Appliance 300 시리즈의 HA 쌍이 배치됩니다. 인스턴스의 공인 VLAN에 대한 모든 트래픽은 FortiGate Security Appliance를 통해 라우팅됩니다.

**참고:** 추가 클러스터를 주문하는 경우 새로 추가된 클러스터에 대한 공인 VLAN에는 Security Appliances의 HA 쌍이 없습니다.

## FortiGate Security Appliance on IBM Cloud 설치 시 고려사항

FortiGate Security Appliance on {{site.data.keyword.cloud_notm}} 서비스를 설치하기 전에 다음 고려사항을 검토하십시오.
* 사용 중인 {{site.data.keyword.cloud_notm}} 계정에 **Hardware Firewall** 권한이 있는지 확인하십시오. 이 권한은 인스턴스의 FortiGate Security Appliance on {{site.data.keyword.cloud_notm}} 서비스에 대한 방화벽 로그 및 설정을 편집하거나 보는 데 필요합니다.
* FortiGate Security Appliance on {{site.data.keyword.cloud_notm}} 서비스를 배치된 인스턴스에 추가하려면 아직 인스턴스의 공인 VLAN에 {{site.data.keyword.cloud_notm}} 인프라의 다른 방화벽이 없는지 확인하십시오.
* FortiGate Security Appliance on {{site.data.keyword.cloud_notm}} 서비스를 설치하면 새 공인 VALN이 추가됩니다.
* 서비스 배치 중에 일시적으로 인스턴스가 인터넷에 액세스할 수 없습니다.
* FortiGate Security Appliance on {{site.data.keyword.cloud_notm}} 서비스가 설치된 후 FortiGate 콘솔에서 FSA의 방화벽 규칙을 관리하고 구성할 수 있습니다. FSA 방화벽 규칙이 인터넷을 통해 {{site.data.keyword.cloud_notm}}의 외부 관리 데이터베이스와 통신하기 위해 관리 컴포넌트(예: IBM CloudDriver 가상 머신 또는 Zerto Virtual Manager)로 시작되는 아웃바운드 HTTPS(TCP 포트 443) 통신을 허용하도록 정의되어 있는지 확인해야 합니다. 아웃바운드 HTTPS(TCP 포트 443) 통신은 인스턴스에 있는 관리 서비스 VMware NSX Edge Services Gateway(ESG)의 공인 IP 주소에서 시작됩니다.
* 새 인스턴스의 일부로 FortiGate Security Appliance 디바이스의 쌍을 배치하는 경우 FortiGate Security Appliance 디바이스가 인스턴스와 공용 네트워크 간의 필수 아웃바운드 통신만 허용하고 기타 모든 통신을 거부하도록 구성됩니다.
* 기존 인스턴스의 일부로 FortiGate Security Appliance 디바이스의 쌍을 배치하는 경우 FortiGate Security Appliance 디바이스는 명시적인 규칙으로 인스턴스와 공용 네트워크 간의 모든 필수 아웃바운드 관리 통신을 허용하도록 구성됩니다. 또한 FortiGate Security Appliance 디바이스는 기존 애플리케이션 트래픽이 인터럽트되지 않기 위해 추가 규칙으로 기타 모든 통신을 허용하도록 구성됩니다. 필요한 통신만 허용하고 기타 모든 통신은 거부하도록 FortiGate Security Appliance 구성을 주의하여 관리해야 합니다.

## FortiGate Security Appliance on IBM Cloud 제거 시 고려사항

FortiGate Security Appliance on {{site.data.keyword.cloud_notm}} 서비스를 제거하기 전에 다음 고려사항을 검토하십시오.
* FortiGate Security Appliance on {{site.data.keyword.cloud_notm}} 서비스를 제거하면 추가된 공인 VALN이 제거됩니다.
* 서비스 제거 중에 일시적으로 인스턴스가 인터넷에 액세스할 수 없습니다.
* NAT 트래픽을 허용, 검사, 차단 및 라우트할 모든 FortiGate 규칙이 Fortinet 서비스와 함께 제거됩니다. NAT 규칙이 있는 경우 다시 구성해야 합니다.

## 관련 링크

* [FortiGate Security Appliance on {{site.data.keyword.cloud_notm}} 주문](fsa_ordering.html)
* [FortiGate Security Appliance on {{site.data.keyword.cloud_notm}} 관리](managingfsa.html)
* [IBM 지원 센터에 문의](../vmonic/trbl_support.html)
* [FAQ](../vmonic/faq.html)
* [Fortinet 웹 사이트](https://www.fortinet.com/){:new_window}
* [Fortinet Document Library](http://docs.fortinet.com/fortigate/admin-guides){:new_window}
