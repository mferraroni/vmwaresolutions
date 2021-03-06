---

copyright:

  years:  2016, 2018

lastupdated: "2018-05-30"

---

# 管理系統通知

您可以檢查通知，以瞭解系統或使用者作業的狀態。您也可以利用該資訊來診斷可能發生的問題並進行疑難排解。

## 檢視通知

1. 從 {{site.data.keyword.vmwaresolutions_short}} 主控台中，按一下左導覽窗格中的**通知**。
2. 在**通知歷程**表格中，檢視關於所有通知的摘要。

   表 1. 通知歷程

    <table>
      <tr>
        <th>直欄</th>
        <th>說明       </th>
      </tr>
      <tr>
        <td>嚴重性</td>
        <td>通知所報告事件的嚴重性。<dl class="dl">
          <dt class="dt dlterm">嚴重 </dt>
          <dd class="dd">嚴重事件可能會影響整個系統或服務。</dd>
          <dt class="dt dlterm">錯誤</dt>
          <dd class="dd">在可能需要管理者或一般使用者人為介入的作業期間，發生錯誤事件。</dd>
          <dt class="dt dlterm">警告</dt>
          <dd class="dd">元件失敗或未正常運作。不過，失敗不會干擾元件的進行中程序。</dd>
            <dt class="dt dlterm">參考資訊</dt>
            <dd class="dd">已完成系統作業或使用者作業。通常，下列事件會報告參考資訊通知：<ul class="ul">
                <li class="li">已安裝服務。</li>
                <li class="li">已升級服務。</li>
                <li class="li">已移除服務。</li>
                <li class="li">會針對已新增的 ESXi 伺服器重新配置所有服務。</li>
                <li class="li">會針對已移除的 ESXi 伺服器重新配置所有服務。</li>
              </ul>
            </dd>
          </dl>
        </td>
       </tr>
       <tr>
         <td>類型      </td>
         <td>所報告事件相關的元件類型：<ul><li>vCenter Server 實例</li><li>Cloud Foundation 實例</li><li>服務</li><li>系統</li></ul></td>
       </tr>
       <tr>
         <td>資源</td>
         <td>傳送通知的實例或服務名稱。</td>
       </tr>
       <tr>
         <td>說明       </td>
         <td>通知的簡要說明。</td>
       </tr>
       <tr>
         <td>日期 </td>
         <td>傳送通知的日期和時間。</td>
       </tr>
    </table>                                       

3. 按一下通知列，以檢視通知的詳細資料。

## 過濾通知

依預設，會顯示所有未讀取通知。您可以依狀態、嚴重性和類型來過濾通知。若要過濾通知，請僅針對要在**狀態**、**嚴重性**或**類型**下拉清單中顯示的項目來選取勾選框。

## 相關鏈結

* [常見問題](faq.html)
* [使用者帳戶及設定](useraccount.html)
