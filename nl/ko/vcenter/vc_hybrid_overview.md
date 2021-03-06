---

copyright:

  years:  2016, 2018

lastupdated: "2018-06-07"

---

# vCenter Server with Hybridity Bundle 개요

vCenter Server with Hybridity Bundle은 V2.3 이상 릴리스에서 사용 가능한 인스턴스입니다.

VMware vCenter Server on {{site.data.keyword.cloud}} with Hybridity Bundle은 VMware vSphere 스택을 서비스로서 제공하는 호스팅된 프라이빗 클라우드입니다. VMware 환경은 네 개의 {{site.data.keyword.cloud_notm}} {{site.data.keyword.baremetal_short}} 위에 빌드되며, 전용 스토리지인 VMware vSAN을 포함하고, VMware NSX를 기반으로 하면서 관리하기 쉬운 논리 에지 방화벽의 자동 배치 및 구성을 제공하며, VMware HCX on {{site.data.keyword.cloud_notm}} 서비스를 포함합니다.

대부분의 경우 전체 환경은 하루 내에 프로비저닝할 수 있으며, 베어메탈 인프라는 필요에 따라 신속하고 탄력적으로 컴퓨팅 용량을 늘리거나 줄이도록 스케일링할 수 있습니다.

<!--Post-deployment, you can increase shared storage by ordering additional NFS (Network File System) file shares from the  {{site.data.keyword.slportal}} and manually attach them across all ESXi servers in a cluster. If you require dedicated storage, [NetApp ONTAP Select on IBM Cloud](../netapp/np_netappoverview.html) is offered in both high-performance (all SSD) and high-capacity (all SATA) configurations.-->

vSAN 클러스터의 vSAN 기반 스토리지 용량을 늘리기 위해 배치 후 더 많은 ESXi 서버를 추가할 수 있습니다.

사용자는 VMware NSX Advanced 에디션을 Enterprise 에디션으로 업그레이드할 수 있으며, VMware vRealize Operations와 같은 추가 VMware 컴포넌트를 구매할 수 있습니다.

가상화, 게스트 OS 또는 애플리케이션 계층의 일일 오퍼레이션 및 유지보수를 오프로드하려면 IBM Managed Services를 추가할 수 있습니다. 또한 IBM Cloud Professional Services 팀은 마이그레이션, 구현, 계획 및 온보딩 서비스를 통해 클라우드로 빨리 전환할 수 있도록 지원합니다.

## vCenter Server with Hybridity Bundle 아키텍처

다음 그림은 3-노드 vCenter Server with Hybridity Bundle 배치의 상위 레벨 아키텍처 및 컴포넌트를 나타냅니다.

그림 1. vCenter Server with Hybridity Bundle 상위 레벨 아키텍처

![vCenter Server with Hybridity Bundle 아키텍처](hybrid_architecture.svg "vCenter Server with Hybridity Bundle 상위 레벨 아키텍처")

### 실제 인프라

이 계층은 가상 인프라에서 사용할 실제 인프라(컴퓨팅, 스토리지 및 네트워크 리소스)를 제공합니다.

### 가상화 인프라(컴퓨팅, 스토리지 및 네트워크)

이 계층은 다른 VMware 제품을 통해 실제 인프라를 가상화합니다.
* VMware vSphere는 실제 컴퓨팅 리소스를 가상화합니다.
* vSAN(VMware Virtual SAN)은 실제 서버의 스토리지에 따라 소프트웨어 정의 공유 스토리지를 제공합니다.
* VMware NSX는 논리 네트워킹 컴포넌트 및 가상 네트워크를 제공하는 네트워크 가상화 플랫폼입니다.

### 가상화 관리

이 계층은 vCSA(vCenter Server Appliance), NSX Manager, 두 개의 NSX ESG, 세 개의 NSX Controller, PSC(Platform Services Controller) 가상 어플라이언스 및 IBM CloudDriver 가상 머신으로 구성됩니다.

기본 오퍼링은 최대 400개의 호스트와 최대 4000개의 VM이 포함된 환경을 지원하도록 크기가 조정된 vCenter Server 어플라이언스로 배치됩니다. 동일한 vSphere API 호환 도구 및 스크립트는 IBM 호스팅 VMware 환경을 관리하는 데 사용될 수 있습니다.

기본 오퍼링에는 가상화 관리 계층에 대해 예약된 총 38개의 vCPU와 67GB vRAM이 필요합니다. VM에 남아 있는 호스트 용량은 초과 구독 비율, VM 크기 조정 및 워크로드 성능 요구사항과 같은 여러 요인에 따라 달라집니다.

HCX on {{site.data.keyword.cloud_notm}} 서비스 배치 시의 추가 관리 리소스 요구사항은 [VMware HCX on {{site.data.keyword.cloud_notm}} 개요](../services/hcx_considerations.html)를 참조하십시오. 

### 인프라 하이브리드

이 계층은 사용자가 해당 IP 주소와 같은 VM 특성을 변경할 필요 없이 안전하고 쉽게 워크로드를 여기저기로 이동할 수 있도록 온프레미스 사이트와 {{site.data.keyword.cloud_notm}} 사이트 간 리소스의 추상화를 제공합니다.

VMware Hybrid Cloud Extension(HCX)에 따라 온프레미스와 IBM Cloud 사이트 간에 느슨하게 결합된 상호연결을 작성하여 작동 중단 없이 VM의 대량 마이그레이션 또는 VM의 실시간 vMotion을 사용할 수 있습니다.

## vCenter Server with Hybridity Bundle 기술 스펙

vCenter Server with Hybridity Bundle 인스턴스에는 다음 컴포넌트가 포함됩니다.

**참고:** 표준화된 하드웨어 구성의 가용성 및 가격 책정은 배치에 선택된 {{site.data.keyword.CloudDataCent}}에 따라 달라질 수 있습니다.

### Bare Metal Server

vCenter Server with Hybridity Bundle 인스턴스 주문에는 4개의 사용자 정의된 {{site.data.keyword.baremetal_short}}가 포함됩니다. 다음 CPU 모델이 사용 가능합니다.
  * 2CPU Intel Broadwell 세대(Intel Xeon E5-2600 v4 시리즈)
  * 2CPU Intel Skylake 세대(Intel Xeon 4100/5100/6100 시리즈)

<!--For NFS storage configuration, the recommended number of {{site.data.keyword.baremetal_short}} is set to the default of three.

**Note:** If you select vSAN storage, the configuration requires four {{site.data.keyword.baremetal_short}}.-->

### 네트워킹

다음 네트워킹 컴포넌트가 주문됩니다.
*  10Gbps 듀얼 공용 및 사설 네트워크 업링크
*  세 개의 VLAN(Virtual LANs): 한 개의 공인 VLAN 및 두 개의 사설 VLAN
*  계층 2(L2) 네트워크에 연결된 로컬 워크로드 간의 잠재적인 동쪽-서쪽 통신을 위해 DLR(Distributed Logical Router)이 포함된 하나의 VXLAN(Virtual eXtensible LAN). VXLAN은 VXLAN을 수정하거나 VXLAN에 빌드하거나 VXLAN을 제거할 수 있는 샘플 라우팅 토폴로지로 배치됩니다. 또한 추가 VXLAN을 연결하여 DLR의 새 논리 인터페이스에 보안 구역을 추가할 수 있습니다.
*  두 개의 VMware NSX Edge Services Gateway:
  * 관리 네트워킹 토폴로지의 일부로 IBM에서 배치되는 아웃바운드 HTTPS 관리 트래픽을 위한 보안 관리 서비스 VMware NSX Edge Services Gateway(ESG). 이 ESG는 자동화와 관련된 특정 외부 IBM 관리 컴포넌트와 통신하기 위해 IBM 관리 VM에서 사용됩니다. 자세한 정보는 [고객 관리 ESG를 사용하도록 네트워크 구성](../vcenter/vc_esg_config.html#configuring-your-network-to-use-the-customer-managed-nsx-esg-with-your-vms)을 참조하십시오.

    **중요**: 이 ESG에 액세스할 수 없고 ESG를 사용할 수 없습니다. 이를 수정하면 {{site.data.keyword.vmwaresolutions_short}} 콘솔에서 vCenter Server with Hybridity Bundle 인스턴스를 관리하지 못하게 될 수 있습니다. 또한 방화벽을 사용하거나 외부 IBM 관리 컴포넌트와의 ESG 통신을 사용 안함으로 설정하면 {{site.data.keyword.vmwaresolutions_short}}를 사용할 수 없게 됩니다.
  * VPN 액세스 또는 공용 액세스를 제공하도록 사용자가 수정할 수 있는 템플리트로 IBM에서 배치되는 아웃바운드 및 인바운드 HTTPS 워크로드 트래픽을 위한 보안 고객 관리 VMware NSX Edge Services Gateway. 자세한 정보는 [고객 관리 NSX Edge는 보안 위험을 발생시킵니까?](../vmonic/faq.html#does-the-customer-managed-nsx-edge-pose-a-security-risk-)를 참조하십시오.

HCX on {{site.data.keyword.cloud_notm}} 서비스를 배치할 때 주문된 네트워킹 컴포넌트에 대한 추가 정보는 [HCX on {{site.data.keyword.cloud_notm}} 개요](../services/hcx_considerations.html)를 참조하십시오.

### Virtual Server 인스턴스

다음 VSI(Virtual Server Instance)가 주문됩니다.
* 인스턴스 배치가 완료된 후 시스템이 종료되는 IBM CloudBuilder용 VSI
* 보안 및 강력한 추진력 향상을 위해 하나의 Microsoft Active Directory(AD)용 Microsoft Windows Server VSI 또는 관리 클러스터에 있는 두 개의 고가용성 Microsoft Windows VM을 배치하도록 선택할 수 있습니다. 또한 Veeam 서비스를 사용하여 VM을 백업하고 복원하는 옵션이 있습니다.

### 스토리지

vSAN 스토리지는 디스크 유형과 양에 대한 다양한 옵션을 포함하여 사용자 정의된 구성을 제공합니다.
* 디스크 양: 2, 4, 6 또는 8.
* 스토리지 디스크: 960GB SSD SED, 1.9TB SSD SED 또는 3.8TB SSD SED

  또한 호스트당 960GB의 두 가지 캐시 디스크도 주문됩니다.

### IBM 제공 라이센스 및 요금

vCenter Server with Hybridity Bundle 인스턴스 주문에는 다음 라이센스가 포함됩니다.

* VMware vSphere Enterprise Plus 6.5u1
* VMware vCenter Server 6.5
* VMware NSX Service Providers Edition(Advanced 또는 Enterprise) 6.3
* VMware vSAN(Advanced 또는 Enterprise) 6.6

추가 지원 및 서비스 요금이 적용될 수 있습니다.

## vCenter Server with Hybridity Bundle 확장 노드 컴포넌트

각 vCenter Server with Hybridity Bundle 확장 노드는 사용자의 {{site.data.keyword.cloud_notm}} 계정에 배치되며 다음 컴포넌트에 대한 비용을 발생시킵니다.

### 확장 노드를 위한 하드웨어

사용자 정의된 구성을 가진 하나의 Bare Metal Server.

### 확장 노드의 라이센스 및 요금

* 하나의 VMware vSphere Enterprise Plus 6.5u1
* 하나의 VMware NSX Service Providers Edition(Advanced 또는 Enterprise) 6.3
* 하나의 지원 및 서비스 요금
* VMware vSAN(Advanced 또는 Enterprise) 6.6

**중요**: {{site.data.keyword.slportal_full}} 또는 콘솔 외부의 다른 방법이 아닌 {{site.data.keyword.vmwaresolutions_short}} 콘솔의 {{site.data.keyword.cloud_notm}} 계정에서만 작성된 {{site.data.keyword.vmwaresolutions_short}} 컴포넌트를 관리해야 합니다. {{site.data.keyword.vmwaresolutions_short}} 콘솔 외부에서 컴포넌트를 변경하는 경우 변경사항은 콘솔과 동기화되지 않습니다.

**주의**: 인스턴스를 주문했을 때 {{site.data.keyword.cloud_notm}} 계정에 설치된 {{site.data.keyword.vmwaresolutions_short}} 컴포넌트를 {{site.data.keyword.vmwaresolutions_short}} 콘솔 외부에서 관리하면 환경이 불안정해질 수 있습니다. 이러한 관리 활동에는 다음이 포함됩니다.
*  컴포넌트 추가, 수정, 리턴 또는 제거
*  ESXi 서버 추가 또는 제거를 통한 인스턴스 용량의 확장 또는 축소
*  컴포넌트 전원 끄기
*  서비스 다시 시작

   이 활동에 대한 예외에는 {{site.data.keyword.slportal}}의 공유 스토리지 파일 공유 관리가 포함됩니다. 이러한 활동에는 공유 스토리지 파일 공유 주문, 삭제(마운트된 경우 데이터 저장소에 영향을 줄 수 있음), 권한 부여 및 마운트가 포함됩니다.

## 관련 링크

* [vCenter Server 소프트웨어 명세서](vc_bom.html)
* [vCenter Server with Hybridity Bundle 인스턴스에 대한 요구사항 및 계획](vc_hybrid_planning.html)
* [vCenter Server with Hybridity Bundle 인스턴스 주문](vc_hybrid_orderinginstance.html)
* [HCX on {{site.data.keyword.cloud_notm}} 개요](../services/hcx_considerations.html)
* [IBM 지원 센터에 문의](../vmonic/trbl_support.html)
