---

copyright:

  years:  2016, 2018

lastupdated: "2018-05-25"

---

# 供應項目比較圖表

檢閱下列圖表以瞭解 VMware Cloud Foundation 實例、VMware vCenter Server 實例、VMware vCenter Server with Hybridity Bundle 實例及 VMware vSphere 叢集之功能支援的差異。

表 1. Cloud Foundation、vCenter Server、vCenter Server with Hybridity Bundle 及 vSphere 叢集的支援功能

|功能                          |Cloud Foundation    |vCenter Server | vCenter Server with Hybridity |VMware vSphere |
|:----------------------------------|:--------------------|:---------------|:-------------------------|:-------------- |
|採用 {{site.data.keyword.IBM}} 進階自動化技術 <sup>1</sup> |是|是|是|否。自行建置及配置|
|儲存空間選項|vSAN                |vSAN 或共用檔案層次儲存空間 (NFS)|vSAN                |vSAN 或共用檔案層次儲存空間 (NFS)|
|起始叢集中的 ESXi 伺服器數目|4 |4 部用於 vSAN，且至少 2 部（強烈建議 3 部）用於 NFS|4 |1 部以便擴充現有叢集，4 部用於新的 vSAN 叢集，且至少 3 部用於具有 NFS 的新叢集|
|ESXi 伺服器數目上限 <sup>2</sup> |每個叢集 32 部|每個叢集 59 部|每個叢集 59 部|每個叢集 60 部|
|雲端自動化多站台部署|在 2.0 版或更新版本中部署的新實例受到支援|在 2.0 版或更新版本中部署的新實例受到支援|支援           |支援。未包括自動化配置|
|新增 ESXi 伺服器              |支援           |支援           |支援           |支援。未包括自動化配置|
|移除 ESXi 伺服器           |支援           |支援           |支援           |支援。未包括自動化配置|
|多叢集支援         |5 個叢集|10 個叢集|10 個叢集|支援。未包括自動化配置|
|用戶端管理 VMware 堆疊的更新及修補 |IBM CloudDriver 及 VMware 更新|IBM CloudDriver |IBM CloudDriver |未包括自動化修補|
|備份及還原            |支援           |支援           |支援           |未包括自動化備份解決方案配置|
|軟體定義網路   |NSX Enterprise   |NSX Base、Advanced 或 Enterprise |NSX Advanced 或 Enterprise |NSX Standard、Base 或 Enterprise。未包括自動化配置|
|對於 vSphere 及 vSAN 的 BYOL |對每個叢集充分支援   |對每個叢集充分支援   |不支援|支援           |
|對於 vCenter 及 NSX 的 BYOL |對每個實例充分支援|對每個實例充分支援|不支援|支援           |
|NSX 授權升級選項           |無   |可從 NSX Base 升級至 Advanced 或 Enterprise，以及從 NSX Advanced 升級至 Enterprise。可以升級至 vCenter Server with Hybridity Bundle。|可從 NSX Advanced 升級至 Enterprise  |無   |
|vSAN 授權版本         |vSAN Advanced 或 Enterprise  |vSAN Advanced 或 Enterprise  |vSAN Advanced 或 Enterprise  |vSAN Advanced 或 Enterprise  |
|附加服務               |支援，不包括 HCX on {{site.data.keyword.cloud_notm}}。|支援，不包括 HCX on {{site.data.keyword.cloud_notm}}。可以升級至 vCenter Server with Hybridity Bundle。|支援，包括 HCX on {{site.data.keyword.cloud_notm}}。|支援。未包括自動化配置|

**附註**：

<sup>1</sup> 根據已驗證的設計並在部署期間驗證。

<sup>2</sup> 您可以將 vSAN 叢集中的 ESXi 伺服器數目增加到最多 64 個。如需相關資訊，請參閱[關於 ESXi 伺服器的常見問題](faq_esxi.html)中的_我可以新增多少部 ESXi 伺服器至叢集？_。

### 相關鏈結

* [常見問題](faq.html)
* [Cloud Foundation 概觀](../sddc/sd_cloudfoundationoverview.html)
* [vCenter Server 概觀](../vcenter/vc_vcenterserveroverview.html)
* [vCenter Server Hybridity 概觀](../vcenter/vc_hybrid_overview.html)
* [Vmware vSphere 概觀](../vsphere/vs_vsphereclusteroverview.html)
* [Cloud Foundation BOM](../sddc/sd_bom.html)
* [vCenter Server BOM](../vcenter/vc_bom.html)
* [Vmware vSphere BOM](../vsphere/vs_bom.html)
