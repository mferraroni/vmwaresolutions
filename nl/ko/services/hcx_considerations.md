---

copyright:

  years:  2016, 2018

lastupdated: "2018-06-14"

---

# VMware HCX on IBM Cloud 개요

HCX on {{site.data.keyword.cloud}} 서비스는 {{site.data.keyword.cloud_notm}}로 온프레미스 데이터 센터의 네트워크를 원활하게 확장할 수 있으며, 이를 통해 변환이나 변경 없이 {{site.data.keyword.cloud_notm}}에서 가상 머신(VM)을 마이그레이션할 수 있습니다.

**가용성**: 이 서비스는 V2.3 이상 릴리스에 배치된 VMware vCenter Server on IBM Cloud with Hybridity Bundle 인스턴스에서만 사용 가능합니다.

기존 vCenter Server 인스턴스를 vCenter Server with Hybridity Bundle 인스턴스로 업그레이드할 수 있습니다. 인스턴스 업그레이드 및 HCX on {{site.data.keyword.cloud_notm}} 서비스 배치에 대한 자세한 정보는 [vCenter Server with Hybridity Bundle 인스턴스로 업그레이드](../vcenter/vc_applyingupdates.html#applying-updates-to-vcenter-server-instances.html#upgrading-to-the-vcenter-server-with-hybridity-bundle-instance)를 참조하십시오.

**참고:** HCX on {{site.data.keyword.cloud_notm}}의 vCenter Server 인스턴스는 온프레미스 사이트의 세 개의 동시 연결로 제한됩니다.

## HCX on IBM Cloud 설치 시 고려사항

HCX on {{site.data.keyword.cloud_notm}}를 설치하기 전에 다음 고려사항을 검토하십시오.

### ESXi 서버의 수에 대한 요구사항

HCX on {{site.data.keyword.cloud_notm}} 서비스는 기본 클러스터에 52개 이상의 ESXi 서버가 있는 인스턴스에 설치될 수 없습니다. HCX on {{site.data.keyword.cloud_notm}}에서는 기본 클러스터의 vMotion 서브넷에 8개의 IP 주소가 필요하므로 ESXi 서버의 수가 51개를 초과하면 HCX on {{site.data.keyword.cloud_notm}}에 vMotion 서브넷의 IP 주소를 사용할 수 없습니다.

### 방화벽 규칙에 대한 요구사항

HCX on {{site.data.keyword.cloud_notm}} 서비스를 설치하기 전에 HCX Manager 가상 어플라이언스(HCX Manager)가 자체적으로 등록할 수 있도록 모든 아웃바운드 HTTPS 트래픽을 허용하려면 방화벽 규칙을 기존 방화벽에 추가해야 합니다. HCX Manager 설치가 완료되면 방화벽 규칙을 제거할 수 있습니다. 또한 HCX가 올바르게 작동하도록 방화벽 규칙을 구성해야 합니다. 자세한 정보는 [VMWare HCX on {{site.data.keyword.cloud_notm}} Solution Architecture](https://www.ibm.com/cloud/garage/files/HCX_Architecture_Design.pdf)의 *Appendix A - Port Access Requirements*를 참조하십시오.

## HCX on IBM Cloud 제거 시 고려사항

HCX on {{site.data.keyword.cloud_notm}} 서비스를 제거하기 전에 다음 고려사항을 검토하십시오.
* 온프레미스 소스 사이트와 {{site.data.keyword.cloud_notm}} 대상 사이트 간의 상호연결 및 확장된 네트워크가 제거되었는지 확인하십시오. 상호연결 및 확장된 네트워크를 제거하려면 온프레미스 VMware vSphere Web Client에서 HCX 사용자 인터페이스를 사용하십시오.
* 온프레미스 소스 사이트와 {{site.data.keyword.cloud_notm}} 대상 사이트 간의 사이트 페어링이 제거되었는지 확인하십시오. 사이트 페어링을 제거하려면 온프레미스 VMware vSphere Web Client에서 HCX 사용자 인터페이스를 사용하십시오.
* HCX on {{site.data.keyword.cloud_notm}}의 제거가 자동화됩니다. 이 서비스를 제거하려면 다음 프로시저를 완료하십시오.
   * 클라우드 측 HCX Manager에 대해 주문된 HCX 라이센스를 비활성화합니다. 
   * HCX Manager를 삭제합니다. 
   * HCX에 대해 예약된 vMotion IP 주소를 해제합니다. 
   * HCX 관련 리소스 풀이 비어 있는 경우 이를 제거합니다. 
   * HCX 관련 폴더가 비어 있는 경우 이를 제거합니다. 
   * HCX 관리 에지 어플라이언스를 삭제합니다. 

## 관련 링크

* [HCX on {{site.data.keyword.cloud_notm}} 주문](hcx_ordering.html)
* [HCX on {{site.data.keyword.cloud_notm}} 관리](managinghcx.html)
* [HCX 용어집](hcx_glossary.html)
* [IBM 지원 센터에 문의](../vmonic/trbl_support.html)
* [VMware Hybrid Cloud Extension 개요](https://cloud.vmware.com/vmware-hcx)
* [VMware Hybrid Cloud Extension 문서](https://hcx.vmware.com/#vm-documentation)
