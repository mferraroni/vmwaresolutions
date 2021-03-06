---

copyright:

  years:  2016, 2018

lastupdated: "2018-05-16"

---

# 刪除 NetApp ONTAP Select 實例

若要釋放您在 NetApp ONTAP Select 實例中訂購的元件，請刪除該實例。

刪除 NetApp ONTAP Select 實例時，會循序釋放下列元件：
1. 已部署的 NetApp ONTAP Select 叢集 VM（虛擬機器）及「NetApp ONTAP Select 部署 VM」
2. 支援與服務費用
3. VMware 產品授權
4. ESXi 伺服器
5. 子網路
6. VLAN

由於資源相依關係，當您刪除實例時，不會立即釋放實例中的元件。例如，在 {{site.data.keyword.cloud}} 基礎架構完整收回 ESXi 伺服器（發生於 {{site.data.keyword.cloud_notm}} 計費週期結束時）之前，無法刪除子網路及 VLAN。在計費週期（通常為 30 天）結束時，會收回子網路及 VLAN，並完成實例刪除。

**注意：**將向您收取已刪除的實例到計費週期結束為止的費用。

## 從已部署的實例頁面中刪除實例

1. 從 {{site.data.keyword.vmwaresolutions_short}} 主控台中，按一下左導覽窗格上的**已部署的實例**。
2. 在 **NetApp ONTAP Select 實例**表格中，尋找要刪除的實例。
3. 在**動作**直欄中，按一下「刪除」圖示。
   實例的狀態會變更為**正在刪除**。順利刪除實例且其狀態變更為**已刪除**時，請再按一下**動作**直欄中的刪除圖示。
4. 如果您要從 {{site.data.keyword.vmwaresolutions_short}} 主控台移除實例記錄，請完成下列步驟：
   1. 在**動作**直欄中，再按一次「刪除」圖示。
   2. 在**刪除實例**視窗中，按一下**確定**。

## 從實例詳細資料頁面中刪除實例

1. 從 {{site.data.keyword.vmwaresolutions_short}} 主控台中，按一下左導覽窗格上的**已部署的實例**。
2. 在 **NetApp ONTAP Select 實例**表格中，按一下要刪除的實例。
3. 按一下 **NetApp 主控台**右側的溢位功能表圖示，然後按一下**刪除實例**。
   實例的狀態會變更為**正在刪除**。順利刪除實例後，會釋出該實例的元件，且該實例的狀態會變更為**已刪除**。
4. 如果您要從 {{site.data.keyword.vmwaresolutions_short}} 主控台移除實例記錄，請完成下列步驟：
   1. 再按一次 **vCenter 主控台**右側的溢位功能表圖示，然後按一下**刪除實例**。
   2. 在**刪除實例**視窗中，按一下**確定**。

## 相關鏈結

* [訂購 NetApp ONTAP Select 實例](np_orderinginstances.html)
* [檢視 NetApp ONTAP Select 實例](np_viewinginstances.html)
* [與 IBM 支援中心聯絡](../vmonic/trbl_support.html)
