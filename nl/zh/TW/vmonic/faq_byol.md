---

copyright:

  years:  2016, 2018

lastupdated: "2018-05-25"

---

# 授權及 BYOL 的常見問題

尋找授權相關常見問題的回答，其中包括 {{site.data.keyword.vmwaresolutions_full}} 的自帶授權 (BYOL) 特性。

## 何謂 BYOL？

「自帶授權」或 BYOL 是 1.8 版及更新版本中的 VMware Cloud Foundation 實例以及 2.0 版及更新版本中的 vCenter Server 及 vSphere 叢集可用的特性。在訂購實例時，BYOL 可讓您對下列一個以上的 VMware 軟體元件使用您自己的 VMware 授權：
* VMware vCenter Server
* VMware vSphere
* VMware NSX
* VMware vSAN

如果您選擇要對 VMware 元件使用您自己的授權，並為它提供有效的授權碼，則不會向 IBM 訂購此元件的授權，且不會在您的 {{site.data.keyword.cloud}} 基礎架構帳戶中收取此元件的每月授權費用。

**附註：**BYOL 特性不適用於「事業夥伴」使用者。

## 哪裡可以管理透過 VMware vSphere on IBM Cloud 訂購的授權和元件？

在送出為 VMware vSphere on {{site.data.keyword.cloud_notm}} 建立新叢集的訂單之後，會遞送 VMware 授權、ESXi 伺服器及其他網路元件，並可從 {{site.data.keyword.slportal}} 進行管理。

部署之後，請移至 {{site.data.keyword.vmwaresolutions_short}} 主控台，利用已儲存的配置來擴充新叢集。如需擴充大小的相關資訊，請參閱[擴充現有的 vSphere 叢集大小](../vsphere/vs_scalingexistingclusters.html)。

## BYOL 需要哪些授權版本及 CPU 數量？

下列需求適用於 BYOL 的授權版本。

### vCenter Server 實例的 BYOL 需求

表 1. vCenter Server 實例的授權版本及 CPU 最低需求

  |VMware 元件|需要的授權版本|需要的最低 CPU
  |:-------------  |:-------------  |:-------|
  |vCenter Server |Standard                |N/A |
  |vSphere        |Enterprise Plus |8 CPU |
  |vSAN           |Advanced 或 Enterprise |8 CPU |
  |NSX            |Standard、Advanced 或 Enterprise |8 CPU |

### Cloud Foundation 實例的 BYOL 需求

表 2. Cloud Foundation 實例的授權版本及 CPU 最低需求

  |VMware 元件|需要的授權版本|需要的最低 CPU
  |:-------------  |:-------------  |:-------|
  |vCenter Server |Standard |N/A |
  |vSphere        |Enterprise Plus |8 CPU |
  |vSAN           |Advanced 或 Enterprise |8 CPU |
  |NSX            |Enterprise |8 CPU |

## 如果我提供的授權碼不正確會發生生什麼情況？

您提供的所有授權碼都會經過驗證，以確保它們對於對應的 VMware 元件是正確的，而且符合 VMware 元件的最低版本和 CPU 需求。如果任何授權碼驗證失敗，您會得到通知，且無法繼續進行實例訂購。

## 我可以提供超過 8 個 CPU 的授權碼嗎？

是的。對於每一個 VMware 元件，需要每個 CPU 一個授權。目前，所有 vCenter Server 和 Cloud Foundation 伺服器都有兩個 CPU，因此每部伺服器需要兩個授權。建議您提供的授權碼能支援基本實例，以及您未來要新增至該實例的任何擴充節點。

## 使用 BYOL 特性時，是否可以提供 SDDC Manager 授權？

不。我們與 VMware 的合約規定我們必須接受客戶的實際授權碼。雖然 Cloud Foundation 部署包含 SDDC Manager 授權，但我們無法接受任何 SDDC Manager 授權碼檔案並用來驗證 BYOL。因此，IBM 會針對所有實例的 SDDC Manager 授權收費。SDDC Manager 授權代表 Cloud Foundation 實例整體授權費用中很小的一部分。

## 我可以對某些 VMware 元件使用 BYOL 特性，並對某些元件購買每月授權嗎？

是的。您可以針對四個 VMware 元件的任何組合使用 BYOL 特性或購買授權。當您訂購 vCenter Server 或 Cloud Foundation 實例時，{{site.data.keyword.vmwaresolutions_short}} 主控台會直接讓您選取授權選項。您在初次訂購實例時的授權選項，在該實例的生命期限內皆適用。

## 針對特定 VMware 元件，我可以對部分授權使用 BYOL，並向 IBM 購買其餘授權嗎？

是的。如果您為特定 VMware 元件選取 BYOL，您可以選擇在建立新叢集時輸入新的 BYOL 金鑰、繼續使用現有的 BYOL 金鑰，或為該叢集購買 IBM 提供的授權。目前，只有 VMware vSphere Enterprise 和 VMware vSAN 可以使用每個叢集的授權。

## 建立新叢集時，我可以使用 BYOL 嗎？

是的。您可以從現有的 BYOL 授權使用 BYOL，或在建立新叢集時輸入新的 BYOL。您還可以在建立新叢集時選擇購買 IBM 提供的訂閱授權。目前，只有 VMware vSphere Enterprise 和 VMware vSAN 可以使用每個叢集的授權。

## 如何管理 BYOL 授權？

您可以在完成實例部署之後使用 VMware vSphere Web Client 來管理 BYOL 授權。

## 當我稍後新增其他 ESXi 伺服器到我的實例時，該實例會驗證我的 BYOL 授權容量是否足夠嗎？

是的。當您新增其他 ESXi 伺服器到已部署的實例時，會針對指定的 ESCi 伺服器數量自動檢查您的 BYOL 授權容量。如果容量不足，則不會新增 ESXi 伺服器，且您會收到主控台通知。

## 我如何得知具有 BYOL 的叢集上有多少可用的授權容量？

您可以移至**已部署的實例**頁面、尋找並按一下實例，然後在**基礎架構**標籤上按一下要檢查授權容量的叢集，來尋找授權碼中可用的 CPU 數目。可用的 CPU 數目會列在**使用者提供的授權**表格中。

## 如果我選取 BYOL 授權選項，IBM 是否提供支援？

「IBM 支援中心」會繼續作為您任何實例配置問題的聯絡窗口。不過，如果所報告的問題被判定是關於 BYOL VMware 元件，則會引導您到「VMware 支援中心」。

## 如果我使用 BYOL，為何價格預估清單上會顯示 vSphere 授權費用？有向我收取此費用嗎？

{{site.data.keyword.baremetal_short}} 佈建時已安裝 VMware vSphere，並已包括 vSphere 授權。如果您為 vSphere 選取 BYOL，則在實例部署時會自動起始程序來移除已包括的 vSphere 授權。然後，授權費用將在您的 {{site.data.keyword.cloud_notm}} 帳戶記入貸方。您不需要在此程序中執行任何動作。

## 我是否仍然可以對 BYOL 使用現有的手動程序？

在引進 BYOL 特性時，不建議繼續使用手動程序。如果您要使用 BYOL，請在訂購實例時提供您自己的授權。

## 有針對其他 VMware 產品支援 BYOL 嗎？例如，VMware vRealize Automation、VMware vRealize Operations 或 VMware vRealize Log Insight？

不，因為這些 VMware 產品不是實例部署的一部分。這些 VMware 產品可能安裝在起始部署之上，這需要客戶或其代理人執行安裝和授權。

## 我可以訂購 vCenter Server with Hybridity Bundle 的 NFS 儲存空間嗎？

對於新部署的實例，僅支援 vSAN 全快閃記憶體儲存空間。vCenter Server with Hybridity Bundle 供應項目包括 vSAN Advanced 或 Enterprise 授權。

如果您的 vCenter Server 實例具有 NFS 儲存空間，則可以將現有實例升級至 vCenter Server with Hybridity Bundle。在升級期間訂購 vSAN Advanced 授權時，您不需要佈建全快閃記憶體 vSAN 叢集。

## 我可以使用 BYOL 與 vCenter Server with Hybridity Bundle 搭配嗎？

您無法將自己的 VMware 授權 (BYOL) 帶到 {{site.data.keyword.cloud_notm}}。vCenter Server with Hybridity Bundle 需要 IBM 提供所有 VMware 授權。

## vCenter Server with Hybridity Bundle 授權與 vCenter Server 授權之間的差異為何？

vCenter Server 中可用的個別 VMware 授權是根據 CPU 計價。與 IBM 所提供的所有個別 CPU VMware 授權相同，個別 CPU 有 16 個以上核心的所有伺服器在價格方面會有 1.3x 的額外費用（例如，針對「雙重 Intel Xeon Gold 6140」）。

vCenter Server with Hybridity Bundle 是根據核心授權的一組預定 VMware 授權及版本，而不是根據 CPU。因此，這些實例的授權價格不會變更。

## 哪些 IBM 提供的 VMware 授權元件及版本適用於 vCenter Server with Hybridity Bundle？

新的 vCenter Server with Hybridity Bundle 實例，包括 VMware vSphere Enterprise Plus、VMware vCenter Standard、VMware NSX Advanced 或 Enterprise、VMware vSAN Advanced 或 Enterprise，以及 VMware Hybrid Cloud Extension (HCX)。

如果您的 vCenter Server 實例具有 NSX Base 版本，則會在您訂購 vCenter Server with Hybridity Bundle 時自動將您升級至 NSX Advanced。

## 我可以將 vCenter Server with Hybridity Bundle 所含的 NSX Advanced 版本升級至 NSX Enterprise 版本嗎？

vCenter Server with Hybridity Bundle 包括 NSX Advanced 時，您可以在訂購 vCenter Server with Hybridity Bundle 之後升級至 NSX Enterprise 版本。若要這樣做，請使用 {{site.data.keyword.vmwaresolutions_short}} 主控台之實例詳細資料頁面上的**更新及修補程式**標籤。

### 相關鏈結

* [訂購 Cloud Foundation 實例](../sddc/sd_orderinginstance.html)
* [Cloud Foundation 實例](../sddc/sd_cloudfoundationoverview.html)
* [存取主控台](loginmethod.html)
* [與 IBM 支援中心聯絡](trbl_support.html)
* [vRealize Automation](https://www.ibm.com/devops/method/content/architecture/virtCloudFoundationPlatform/vRealizeAutomation){:new_window}
