---

copyright:

  years:  2016, 2018

lastupdated: "2018-05-07"

---

# 訂購 NetApp ONTAP Select 實例

若要使用專用且高可用的軟體定義儲存空間應用裝置來部署 VMware 虛擬化平台，請訂購 NetApp ONTAP Select 實例。

## 需求

請確定您已完成下列作業：
*  您已在**設定**頁面上配置 {{site.data.keyword.cloud}} 基礎架構認證。如需相關資訊，請參閱[管理使用者帳戶及設定](../vmonic/useraccount.html)。
*  您已檢閱 [NetApp ONTAP Select 實例的需求及規劃](np_planning.html)中的需求及考量。

**重要事項：請不要修改在訂購及實例部署期間設定的任何值。這樣做會導致您的實例變成無法使用。**

## 系統設定

當您訂購 NetApp ONTAP Select 實例時，必須指定下列基本設定。

### 實例名稱

實例名稱必須符合下列需求：
* 只容許英數及橫線 (-) 字元。
* 實例名稱的開頭及結尾必須是英數字元。
* 實例名稱的長度上限為 10 個字元。
* 實例名稱在您的帳戶中必須是唯一的。

## 網路介面設定

訂購 NetApp ONTAP Select 實例時，您必須指定下列網路介面設定。

### 主機名稱字首

主機名稱字首必須符合下列需求：
*  只容許英數及橫線 (-) 字元。
*  主機名稱字首的開頭及結尾必須是英數字元。
*  主機名稱字首的長度上限為 10 個字元。

### 子網域標籤

子網域標籤必須符合下列需求：
*  只容許英數及橫線 (-) 字元。
*  子網域標籤的開頭及結尾必須是英數字元。
*  子網域標籤的長度上限為 10 個字元。
*  子網域標籤在您的帳戶內必須是唯一的。

### 網域名稱

根網域名稱必須符合下列需求：
* 網域名稱必須包含兩個以上以句點 (.) 區隔的字串
* 第一個字串的開頭必須是英文字母，而且結尾必須是英數字元。
* 除了最後一個字串以外，所有字串都只能包含英數字元和橫線 (-) 字元。
* 最後一個字串只能包含英文字母。
* 最後一個字串的長度範圍必須在 2 到 24 個字元之間。

**附註：**主機和 VM（虛擬機器）的 FQDN（完整網域名稱）長度上限為 50 個字元。網域名稱必須在這個長度上限以內。

## 授權設定

您必須上傳四個 NetApp 授權檔，因為這四個 {{site.data.keyword.baremetal_short}} 都需要一個授權。請聯絡您的 NetApp 銷售團隊，以針對高效能或高容量部署採購適當的授權。

## Bare Metal Server 設定

### 資料中心位置

您必須選取要管理實例的 {{site.data.keyword.CloudDataCent_notm}}。<!-- Only the {{site.data.keyword.CloudDataCents_notm}} that meet the Bare Metal Server specification you selected previously are displayed.-->

### Bare Metal Server 配置

您可以根據需求來選取 Bare Metal Server 配置：
* **高效能（中型）**- 超值授權/雙重 Intel Xeon E5-2650 v4（總計 24 核心，2.2 GHz）/128 GB RAM/每個節點有 22 個 1.9 TB SSD 磁碟機容量/4 節點叢集的有效容量 - 59 TB
* **高效能（大型）**- 超值授權/雙重 Intel Xeon E5-2650 v4（總計 24 核心，2.2 GHz）/128 GB RAM/每個節點有 22 個 3.8 TB SSD 磁碟機容量/4 節點叢集的有效容量 - 118 TB
* **高容量** - 標準授權/雙重 Intel Xeon E5-2650 v4（總計 24 核心，2.2 GHz）/64 GB RAM/每個節點有 34 個 4 TB SATA 磁碟機容量/4 節點叢集的有效容量 - 190 TB

**附註：**3.8 TB SSD（固態磁碟）磁碟機在正式發行至 {{site.data.keyword.CloudDataCent_notm}} 時就會予以支援。

<!--For guidance on what bare metal server configuration to choose, see the _Bill of Materials_ document on the [Reference Architecture](https://www.ibm.com/cloud/garage/content/architecture/virtualizationArchitecture/reference-architecture) page.-->

### Bare Metal Server 數目

依預設，NetApp ONTAP Select 實例的 ESXi 伺服器數目為 4。您無法變更它。所有 ESXi 伺服器都會共用相同的配置。

## 程序

1. 在「{{site.data.keyword.cloud_notm}} 型錄」中，按一下左導覽窗格上的 **VMware**，然後按一下**虛擬資料中心**區段中的 **NetApp ONTAP Select**。
2. 在 **NetApp ONTAP Select** 頁面上，按一下**建立**。
3. 在 **NetApp ONTAP** 頁面上，輸入實例名稱。
4. 輸入**主機名稱字首**、**子區域標籤**及**網域名稱**，來完成網路介面設定。
5. 按一下**新增授權檔**以上傳四部 {{site.data.keyword.baremetal_short}} 所需的四個 NetApp 授權檔，來完成授權設定。
6. 完成 Bare Metal Server 設定：
   1. 選取 {{site.data.keyword.CloudDataCent_notm}} 來管理實例。
   2. 選取 Bare Metal Server 配置。
7. 在**訂單摘要**窗格上，先驗證實例配置，再下訂單。
    1. 檢閱實例的設定。
    2. 檢閱預估實例成本。按一下**定價詳細資料**以產生 PDF 摘要。若要儲存或列印訂單摘要，請按一下 PDF 視窗右上方的**列印**或**下載**圖示。
    3. 確定要收費的帳戶正確，然後選取**我瞭解將會向下面列出的帳戶收費**勾選框。
    4. 按一下適用於您訂單的條款鏈結。確定您同意這些條款，然後選取**我已閱讀並同意下面列出的協力廠商服務合約**勾選框。
    5. 按一下**佈建**。

## 結果

實例的部署會自動啟動。您將會收到正在處理訂單的確認，您可以檢視實例詳細資料來檢查部署的狀態。

順利部署實例時，會在 VMware 虛擬平台上安裝 [NetApp ONTAP Select 實例元件](../netapp/np_netappoverview.html#netapp-ontap-select-instance-components)中所述的元件。

實例已備妥可供使用時，實例的狀態會變更為**備妥使用**，而且您會透過電子郵件收到通知。

## 下一步

檢視及管理您訂購的 NetApp ONTAP Select 實例。

**重要事項**：您必須從 {{site.data.keyword.vmwaresolutions_short}} 主控台管理 {{site.data.keyword.cloud_notm}} 帳戶中所建立的 {{site.data.keyword.vmwaresolutions_short}} 元件，而不是在主控台以外的 {{site.data.keyword.slportal}} 或透過任何其他方法進行管理。如果您在 {{site.data.keyword.vmwaresolutions_short}} 主控台以外變更這些元件，則變更不會與主控台同步。

**警告**：從 {{site.data.keyword.vmwaresolutions_short}} 主控台以外管理任何 {{site.data.keyword.vmwaresolutions_short}} 元件（元件已在訂購實例時安裝至 {{site.data.keyword.cloud_notm}} 帳戶）可能會讓您的環境不穩定。這些管理活動包括：
*  新增、修改、退回或移除元件
*  關閉元件電源

   這些活動的例外包括從 {{site.data.keyword.slportal}} 管理共用儲存空間檔案共用。這類活動包括：訂購、刪除（這可能會影響已裝載的資料儲存庫）、授權及裝載共用儲存空間檔案共用。

## 相關鏈結

* [檢視 NetApp ONTAP Select 實例](np_viewinginstances.html)
* [刪除 NetApp ONTAP Select 實例](np_deletinginstance.html)
* [NetApp ONTAP 文件中心](http://docs.netapp.com/ontap-9/index.jsp?topic=%2Fcom.netapp.doc.exp-clus-peer%2Fhome.html)
* [Attach dedicated storage to NetApp ONTAP Select deployments](https://developer.ibm.com/recipes/tutorials/steps-to-attach-dedicated-storage-to-existing-ic4v-deployments-on-ibm-cloud/)
