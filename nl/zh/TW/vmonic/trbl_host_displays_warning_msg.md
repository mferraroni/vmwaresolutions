---

copyright:

  years:  2016, 2018

lastupdated: "2017-06-29"

---

# ESXi 伺服器顯示配置問題

## 問題
配置問題會顯示在 vSphere 用戶端的 VMware ESXi 伺服器**監視器**標籤的**問題**標籤中。

在 ESXi 伺服器的**問題**標籤中，會顯示下列訊息：

`This host currently has no management network redundancy`

即使提供備援的專用分散式交換器有兩個可用的上行鏈路，也會顯示此訊息。

## 解決方法
這是 VMware 已知問題。如果要解決這個問題，請遵循[當測試條件為 false 時 ESX/ESXi 主機顯示警告訊息 (2008602)](https://kb.vmware.com/selfservice/search.do?cmd=displayKC&docType=kc&docTypeID=DT_KB_1_1&externalId=2008602){:new_window} 中的指示。
