---

copyright:

  years:  2016, 2018

lastupdated: "2018-06-04"

---

# vCenter Server 實例的網路考量

如需關於 vCenter Server 實例的網路考量及需求的詳細資料，請檢閱下列資訊。請確定您符合需求，讓實例能夠正常運作。

## vCenter Server 實例的網路元件

若要檢閱 vCenter Server 實例所包含的網路元件，請參閱 [vCenter Server 概觀](vc_vcenterserveroverview.html)中的 _vCenter Server 技術規格_ 小節。

## NSX 防火牆考量

如果您使用 NSX Distributed Firewall (DFW)，請檢閱下列需求：
* 您必須針對來自 {{site.data.keyword.IBM}} CloudDriver 虛擬機器 (VM) 的所有通訊配置規則，以容許所有通訊協定在 IP 位址 `10.0.0.0/8` 和 `161.26.0.0/16` 上進行通訊。
* 您必須建立 DFW 規則，以容許從 IBM CloudDriver VM 到任何目的地的 HTTPS 資料流量。
* DFW 規則必須優先於會封鎖進出這些 VM 的資料流量的任何其他規則。

## 使用 NSX 與虛擬機器搭配

在 vCenter Server 實例部署期間，會在實例中訂購、安裝、授權及配置 VMware NSX。同時，會設定 NSX Manager、NSX Controller 及「NSX 傳輸區域」，且每一部 ESXi 伺服器中都配置了 NSX 元件。

也會部署 NSX Edge Services Gateway，供您的工作負載 VM 使用。如需相關資訊，請參閱[配置網路以使用客戶管理的 NSX ESG 來搭配您的 VM](vc_esg_config.html#configuring-your-network-to-use-the-customer-managed-nsx-esg-with-your-vms)。

## 變更 NSX 元件密碼時的考量

在變更 NSX Manager、NSX Controller 及 NSX Edge 的密碼之前，請檢閱下列考量：
* 不要變更 NSX Manager 密碼，您可以在 {{site.data.keyword.vmwaresolutions_short}} 主控台之實例的**摘要**頁面上找到此密碼。
* 您可以變更 NSX Controller 的密碼。如需如何變更 NSX Controller 密碼的指示，請參閱 [Change Controller Password](https://docs.vmware.com/en/VMware-NSX-for-vSphere/6.2/com.vmware.nsx.admin.doc/GUID-2667DD9E-E2F5-4403-BAC2-C7D1BBC23228.html)。
* 您可以變更客戶管理的 VMware NSX Edge Services Gateway (ESG) 的密碼和 SSH 設定。請勿變更 Management VMware NSX Edge Services Gateway (ESG) 及相關「分散式邏輯路由器」的密碼。

## 相關鏈結

* [Overview of NSX](https://docs.vmware.com/en/VMware-NSX-for-vSphere/6.2/com.vmware.nsx-cross-vcenter-install.doc/GUID-10944155-28FF-46AA-AF56-7357E2F20AF4.html){:new_window}
* [NSX Edge Services Gateway](https://www.ibm.com/cloud/garage/content/architecture/virtualizationArchitecture/nsx-esg){:new_window}
* [Managing NAT Rules](https://docs.vmware.com/en/VMware-NSX-for-vSphere/6.2/com.vmware.nsx.admin.doc/GUID-5896D8CF-20E0-4691-A9EB-83AFD9D36AFD.html){:new_window}
