---

copyright:

  years:  2016, 2018

lastupdated: "2018-06-11"

---

# VMware Federal on IBM Cloud 개요

VMware Federal on {{site.data.keyword.cloud}}는 미국 연방 정부 기관에 배치된 vCenter Server 인스턴스를 보안하는 옵션을 제공하고 기본 vCenter Server 인스턴스를 주문하기 위한 지원을 제공합니다. 배치된 인스턴스를 보호하는 옵션을 선택하면 인스턴스에 대해 저장된 중요 정보가 제거되고 관리 기능(예: 호스트와 클라이언트 추가 및 제거)의 인스턴스에 지속적으로 액세스하기 위해 열린 관리 연결이 제거됩니다. 보안 옵션을 선택한 후 전체 인스턴스 삭제를 제외한 모든 관리 기능이 사용 안함으로 설정됩니다.

vCenter Server on {{site.data.keyword.cloud_notm}} 및 vCenter Server 아키텍처에 대한 자세한 정보는 [vCenter Server 개요](vc_vcenterserveroverview.html)를 참조하십시오.

**주의:** VMware Federal on {{site.data.keyword.cloud_notm}}는 vCenter Server 오퍼링의 서브세트만 제공합니다. 다중 사이트 구성, 사전 구성된 {{site.data.keyword.cloud_notm}} Bare Metal Server, BYOL(Bring Your Own License) 및 추가 서비스 주문 옵션은 지원되지 않습니다.

## VMware Federal on IBM Cloud의 vCenter Server 인스턴스 컴포넌트

다음 컴포넌트가 포함됩니다.

### Bare Metal Server

다음 구성 중 하나로 둘 이상의 사용자 정의된 {{site.data.keyword.baremetal_short}}를 주문할 수 있습니다.

* 2CPU Intel Broadwell 세대(Intel Xeon E5-2600 v4 시리즈)
* 2CPU Intel Skylake 세대(Intel Xeon 4100/5100/6100 시리즈)

NFS 스토리지 구성의 경우 {{site.data.keyword.baremetal_short}}의 권장 수는 기본값인 3으로 설정됩니다.

**참고:** vSAN 스토리지를 선택하는 경우 구성에는 네 개의 {{site.data.keyword.baremetal_short}}가 필요합니다.

### 네트워킹

다음 네트워킹 컴포넌트가 주문됩니다.
*  세 개의 VLAN(Virtual LANs): 한 개의 공인 VLAN 및 두 개의 사설 VLAN
*  계층 2(L2) 네트워크에 연결된 로컬 워크로드 간의 잠재적인 동쪽-서쪽 통신을 위해 DLR(Distributed Logical Router)이 포함된 하나의 VXLAN(Virtual eXtensible LAN). VXLAN은 VXLAN을 수정하거나 VXLAN에 빌드하거나 VXLAN을 제거할 수 있는 샘플 라우팅 토폴로지로 배치됩니다. 또한 추가 VXLAN을 연결하여 DLR의 새 논리 인터페이스에 보안 구역을 추가할 수 있습니다.
*  두 개의 VMware NSX Edge Services Gateway:
  * 관리 네트워킹 토폴로지의 일부로 IBM에서 배치되는 아웃바운드 HTTPS 관리 트래픽을 위한 보안 관리 서비스 VMware NSX Edge Services Gateway(ESG). 이 ESG는 자동화와 관련된 특정 외부 IBM 관리 컴포넌트와 통신하기 위해 IBM 관리 가상 머신에서 사용됩니다. 자세한 정보는 [고객 관리 ESG를 사용하도록 네트워크 구성](../vcenter/vc_esg_config.html#configuring-your-network-to-use-the-customer-managed-nsx-esg-with-your-vms)을 참조하십시오.

    **중요**: 이 ESG에 액세스할 수 없고 ESG를 사용할 수 없습니다. 수정하는 경우 {{site.data.keyword.vmwaresolutions_short}} 콘솔에서 vCenter Server 인스턴스를 관리하지 못할 수 있습니다. 또한 방화벽을 사용하거나 외부 IBM 관리 컴포넌트와의 ESG 통신을 사용 안함으로 설정하면 {{site.data.keyword.vmwaresolutions_short}}를 사용할 수 없게 됩니다.
  * VPN 액세스 또는 공용 액세스를 제공하도록 사용자가 수정할 수 있는 템플리트로 IBM에서 배치되는 아웃바운드 및 인바운드 HTTPS 워크로드 트래픽을 위한 보안 고객 관리 VMware NSX Edge Services Gateway. 자세한 정보는 [고객 관리 NSX Edge는 보안 문제점을 발생시킵니까?](../vmonic/faq.html#does-the-customer-managed-nsx-edge-pose-a-security-risk-)를 참조하십시오.

  **참고:** 아웃바운드 HTTPS 관리 트래픽을 위한 VMware NSX Edge Services(ESG)가 배치된 VMware Federal 인스턴스를 보안하는 조치의 일부로 제거됩니다. 자세한 정보는 [VMware Federal 인스턴스 보호](vc_fed_securinginstance.html)를 참조하십시오.

### Virtual Server 인스턴스

다음 VSI(Virtual Server Instances)가 주문됩니다.
* 인스턴스 배치가 완료된 후 시스템이 종료되는 IBM CloudBuilder용 VSI
* (인스턴스 V2.3 이상의 경우) 보안 및 강력한 추진력 향상을 위해 하나의 Microsoft Active Directory(AD)용 Microsoft Windows Server VSI 또는 관리 클러스터에 있는 두 개의 고가용성 Microsoft Windows VM을 배치하도록 선택할 수 있습니다.
* (인스턴스 V2.2의 경우) 호스트 및 가상 머신이 등록된 인스턴스를 위한 DNS로 작동하는 Microsoft Active Directory(AD)용 Microsoft Windows Server VSI가 배치되고 검색될 수 있습니다.

### 스토리지

초기 배치 중에 vSAN과 NFS 스토리지 옵션 중에서 선택할 수 있습니다.

vSAN 옵션은 디스크 유형과 양에 대한 다양한 옵션을 포함하여 사용자 정의된 구성을 제공합니다.
* 디스크 양: 2, 4, 6 또는 8.
* 스토리지 디스크: 960GB SSD SED, 1.9TB SSD SED 또는 3.8TB SSD SED

  또한 호스트당 960GB의 두 가지 캐시 디스크도 주문됩니다.

NFS 옵션은 크기 및 성능에 대한 다양한 옵션을 포함하여 워크로드의 사용자 정의된 공유 파일 레벨 스토리지를 제공합니다.
* 크기: 1, 2, 4, 8 또는 12TB.
* 성능: 2, 4 또는 10IOPS/GB.
* 개별적으로 파일 공유 구성

NFS 옵션을 선택한 경우 관리 컴포넌트용 하나의 2TB, 4IOPS/GB 파일 공유가 주문됩니다.

### IBM 제공 라이센스 및 요금

* VMware vSphere Enterprise Plus 6.5u1
* VMware vCenter Server 6.5
* VMware NSX Service Providers Edition(Base, Advanced 또는 Enterprise) 6.3
* (vSAN 클러스터의 경우) VMware vSAN Advanced 또는 Enterprise 6.6

## vCenter Server 확장 노드 컴포넌트

각 vCenter Server 확장 노드가 배치되고 {{site.data.keyword.cloud_notm}} 계정에서 다음 컴포넌트에 대한 비용이 발생합니다.

### 확장 노드를 위한 하드웨어

[VMware Federal on IBM Cloud의 vCenter Server 인스턴스 컴포넌트](../vcenter/vc_fed_overview.html#vcenter-server-instance-components-for-vmware-federal-on-ibm-cloud)에 제시된 구성을 포함하는 하나의 Bare Metal Server.

### 확장 노드의 라이센스 및 요금

* 하나의 VMware vSphere Enterprise Plus 6.5u1
* 하나의 VMware NSX Service Providers Edition(Base, Advanced 또는 Enterprise) 6.3
* (vSAN 클러스터의 경우) VMware vSAN Advanced 또는 Enterprise 6.6

**중요**: {{site.data.keyword.slportal_full}} 또는 콘솔 외부의 다른 방법이 아닌 {{site.data.keyword.vmwaresolutions_short}} 콘솔의 {{site.data.keyword.cloud_notm}} 계정에서만 작성된 {{site.data.keyword.vmwaresolutions_short}} 컴포넌트를 관리해야 합니다. {{site.data.keyword.vmwaresolutions_short}} 콘솔 외부에서 컴포넌트를 변경하는 경우 변경사항은 콘솔과 동기화되지 않습니다.

**주의**: 인스턴스를 주문했을 때 {{site.data.keyword.cloud_notm}} 계정에 설치된 {{site.data.keyword.vmwaresolutions_short}} 컴포넌트를 {{site.data.keyword.vmwaresolutions_short}} 콘솔 외부에서 관리하면 환경이 불안정해질 수 있습니다. 이러한 관리 활동에는 다음이 포함됩니다.
*  컴포넌트 추가, 수정, 리턴 또는 제거
*  ESXi 서버 추가 또는 제거를 통한 인스턴스 용량의 확장 또는 축소
*  컴포넌트 전원 끄기
<!--*  Restarting services-->

   이 활동에 대한 예외에는 {{site.data.keyword.slportal}}의 공유 스토리지 파일 공유 관리가 포함됩니다. 이러한 활동에는 공유 스토리지 파일 공유 주문, 삭제(마운트된 경우 데이터 저장소에 영향을 줄 수 있음), 권한 부여 및 마운트가 포함됩니다.

## 관련 링크

* [vCenter Server 소프트웨어 명세서](vc_bom.html)
* [VMware Federal 인스턴스에 대한 요구사항 및 계획](vc_fed_planning.html)
* [VMware Federal 인스턴스 주문](vc_fed_orderinginstance.html)
* [VMware Federal 인스턴스 보호](vc_fed_securinginstance.html)
* [IBM 지원 센터에 문의](../vmonic/trbl_support.html)
* [{{site.data.keyword.cloud_notm}} file and block storage](https://www.ibm.com/cloud/garage/content/architecture/virtualizationArchitecture/shared-storage){:new_window}
