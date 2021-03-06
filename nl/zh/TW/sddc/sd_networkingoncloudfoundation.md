---

copyright:

  years:  2016, 2018

lastupdated: "2018-06-04"

---

# Cloud Foundation 實例的網路考量

如需 Cloud Foundation 實例之網路考量及需求的詳細資料，請檢閱下列資訊。請確定您符合需求，讓實例能夠正常運作。

## Cloud Foundation 實例的網路元件

若要檢閱 Cloud Foundation 實例中所含的網路元件，請參閱 [Cloud Foundation 實例元件](sd_cloudfoundationoverview.html#cloud-foundation-instance-components)。

## 防火牆考量

如果您使用 NSX Distributed Firewall (DFW)，請檢閱下列需求：
* 您必須針對來自 {{site.data.keyword.IBM}} CloudDriver 及 SDDC Manager 虛擬機器 (VM) 的所有通訊配置規則，以容許所有通訊協定在 IP 位址 `10.0.0.0/8` 及 `161.26.0.0/16` 上進行通訊。
* 您必須建立 DFW 規則，以容許從 IBM CloudDriver VM 到任何目的地的 HTTPS 資料流量。
* DFW 規則必須優先於會封鎖進出這些 VM 的資料流量的任何其他規則。

## 搭配使用 VMware NSX 與 VM

在 Cloud Foundation 實例部署期間，會在實例中訂購、安裝、授權及配置 VMware NSX。同時，會設定 NSX Manager、NSX Controller 及「NSX 傳輸區域」，且每一部 ESXi 伺服器中都配置了 NSX 元件。

不過，如果您的工作負載 VM 需要彼此通訊，並存取網際網路，則您必須負責配置 NSX，以供 VM 使用。

如需如何設定 NSX 的相關資訊：
* 針對主要（單一）Cloud Foundation 實例，請參閱[在 VMware Cloud Foundation on IBM Cloud 上設定工作負載 VM 的 NSX](https://developer.ibm.com/recipes/tutorials/setting-up-nsx-for-workload-vms-on-vmware-cloud-foundation-on-ibm-cloud-vcf/)。
* 針對多站台 Cloud Foundation 實例，請參閱[在 IBM Cloud 中安全地連接專用 VMware 工作負載](https://www.ibm.com/developerworks/library/se-securely-connect-private-vmware-workloads-ibm-cloud/index.html)。

## 變更 NSX 元件密碼時的考量

請先檢閱下列考量，再變更 NSX Manager、NSX Controller 及 NSX Edge 的密碼：
* 不要變更 NSX Manager 密碼。您可以在 {{site.data.keyword.vmwaresolutions_short}} 主控台之實例的**摘要**頁面上找到此密碼。
* 您可以變更 NSX Controller 的密碼。如需如何變更 NSX Controller 密碼的指示，請參閱 [Change Controller Password](https://docs.vmware.com/en/VMware-NSX-for-vSphere/6.2/com.vmware.nsx.admin.doc/GUID-2667DD9E-E2F5-4403-BAC2-C7D1BBC23228.html)。
* 不要變更管理「VMware NSX Edge Services 閘道 (ESG)」的密碼。

## 相關鏈結

* [Overview of NSX](https://docs.vmware.com/en/VMware-NSX-for-vSphere/6.2/com.vmware.nsx-cross-vcenter-install.doc/GUID-10944155-28FF-46AA-AF56-7357E2F20AF4.html){:new_window}
* [NSX Edge Services Gateway]( https://www.ibm.com/cloud/garage/content/architecture/virtualizationArchitecture/nsx-esg){:new_window}
* [Managing NAT Rules](https://docs.vmware.com/en/VMware-NSX-for-vSphere/6.2/com.vmware.nsx.admin.doc/GUID-5896D8CF-20E0-4691-A9EB-83AFD9D36AFD.html){:new_window}
