---

copyright:

  years:  2016, 2018

lastupdated: "2018-05-07"

---

# NetApp ONTAP Select インスタンスの注文

ソフトウェアで定義できる可用性の高い専用ストレージ・アプライアンスを備えた VMware 仮想化プラットフォームをデプロイするには、NetApp ONTAP Select インスタンスを注文してください。

## 要件

以下の作業を完了していることを確認してください。
*  **「設定」**ページで {{site.data.keyword.cloud}} インフラストラクチャーの資格情報を構成する。 詳しくは、[ユーザー・アカウントと設定の管理](../vmonic/useraccount.html)を参照してください。
*  [NetApp ONTAP Select インスタンスの要件と計画](np_planning.html)に記載されている要件と考慮事項を確認した。

**重要: 注文時およびインスタンスのデプロイ時に設定した値は変更しないでください。 変更すると、インスタンスが使用できなくなる可能性があります。**

## システム設定

NetApp ONTAP Select インスタンスを注文する際には、次の基本設定を指定する必要があります。

### Instance name

インスタンス名は、次の要件を満たす必要があります。
* 英数字とダッシュ (-) の文字だけを使用できます。
* インスタンス名の先頭と末尾は英数字である必要があります。
* インスタンス名の最大の長さは 10 文字です。
* インスタンス名はアカウント内で固有である必要があります。

## ネットワーク・インターフェースの設定

NetApp ONTAP Select インスタンスを注文する際には、以下のネットワーク・インターフェース設定を指定する必要があります。

### Host name prefix

ホスト名接頭部は、次の要件を満たす必要があります。
*  英数字とダッシュ (-) の文字だけを使用できます。
*  ホスト名接頭部の先頭と末尾は英数字である必要があります。
*  ホスト名接頭部の最大長は 10 文字です。

### Subdomain label

サブドメイン・ラベルは、次の要件を満たす必要があります。
*  英数字とダッシュ (-) の文字だけを使用できます。
*  サブドメイン・ラベルの先頭と末尾は英数字である必要があります。
*  サブドメイン・ラベルの最大長は 10 文字です。
*  サブドメイン・ラベルは、アカウント内で固有でなければなりません。

### Domain name

ルート・ドメイン・ネームは、次の要件を満たす必要があります。
* ドメイン・ネームは、ピリオド (.) で区切られた 2 つ以上のストリングで構成されていなければなりません。
* 最初の文字列は、英字で始まり英数字で終わらなければなりません。
* 最後の文字列を除き、文字列で使用できるのは、英数字とダッシュ (-) だけです。
* 最後の文字列には、英字しか使用できません。
* 最後の文字列の長さは、2 文字から 24 文字までの範囲でなければなりません。

**注:** ホストと VM (仮想マシン) の FQDN (完全修飾ドメイン・ネーム) の最大長は 50 文字です。 この最大長に対応するドメイン・ネームにする必要があります。

## ライセンス交付の設定

4 つの{{site.data.keyword.baremetal_short}}にそれぞれ 1 つのライセンスが必要なので、4 つの NetApp ライセンス交付ファイルをアップロードする必要があります。 高性能または大容量のデプロイメントの場合は、NetApp 営業チームに問い合わせて、該当するライセンス交付を取得してください。

## ベア・メタル・サーバーの設定

### データ・センターの場所

インスタンスがホストされる {{site.data.keyword.CloudDataCent_notm}}を選択する必要があります。<!-- Only the {{site.data.keyword.CloudDataCents_notm}} that meet the Bare Metal Server specification you selected previously are displayed.-->

### Bare Metal Server configuration

要件に応じてベア・メタル・サーバー構成を選択できます。
* **ハイパフォーマンス (ミディアム)** –プレミアム・ライセンス / Dual Intel Xeon E5-2650 v4 (合計 24 コア、2.2 GHz) / 128 GB RAM / ノードあたり 22 個の 1.9 TB SSD ドライブ容量 / 4 ノード・クラスターの実効容量– 59 TB
* **ハイパフォーマンス (ラージ)** –プレミアム・ライセンス / Dual Intel Xeon E5-2650 v4 (合計 24 コア、2.2 GHz) / 128 GB RAM / ノードあたり 22 個の 3.8 TB SSD ドライブ容量 / 4 ノード・クラスターの実効容量– 118 TB
* **大容量** – 標準ライセンス / Dual Intel Xeon E5-2650 v4 (合計 24 コア、2.2 GHz) / 64 GB RAM / ノード当たり 34 個の 4 TB SATA ドライブ容量 / 4 ノード・クラスターの有効容量 – 190 TB

**注:** 3.8 TB SSD (ソリッド・ステート・ディスク) ドライブは、{{site.data.keyword.CloudDataCent_notm}}内で一般出荷可能になったときにサポートされます。

<!--For guidance on what bare metal server configuration to choose, see the _Bill of Materials_ document on the [Reference Architecture](https://www.ibm.com/cloud/garage/content/architecture/virtualizationArchitecture/reference-architecture) page.-->

### ベア・メタル・サーバーの数

NetApp ONTAP Select インスタンスの ESXi サーバーの数は、デフォルトで 4 台です。 これは変更できません。 すべての ESXi サーバーが同じ構成を共有します。

## 手順

1. {{site.data.keyword.cloud_notm}} のカタログで、左側のナビゲーション・ペインの**「VMware」**をクリックしてから、**「Virtual Data Centers」**セクションの**「NetApp ONTAP Select」**をクリックします。
2. **「NetApp ONTAP Select」**ページで、**「作成」**をクリックします。
3. **「NetApp ONTAP」**ページで、インスタンス名を入力します。
4. **「ホスト名接頭部」**、**「サブドメイン・ラベル」**、および**「ドメイン・ネーム」**を入力して、ネットワーク・インターフェースの設定を完了します。
5. **「ライセンス・ファイルの追加」**をクリックし、4 台の{{site.data.keyword.baremetal_short}}に必要な 4 つの NetApp ライセンス・ファイルをアップロードして、ライセンス設定を実行します。
6. ベア・メタル・サーバーの設定を次の手順で実行します。
   1. インスタンスをホストする {{site.data.keyword.CloudDataCent_notm}}を選択します。
   2. ベア・メタル・サーバー構成を選択します。
7. **「発注要約」**ペインで、インスタンス構成を確認してから注文を実行します。
    1. インスタンスの設定を確認します。
    2. インスタンスの見積もりコストを確認します。 PDF のサマリーを生成するには、**「料金詳細」**をクリックします。 注文のサマリーを保存または印刷するには、PDF ウィンドウの右上にある**「印刷」**アイコンまたは **「ダウンロード」**アイコンをクリックします。
    3. 課金されるアカウントが正しいことを確認した後、**「下にリストされているアカウントが課金されることを確認しました」**チェック・ボックスを選択します。
    4. 注文に適用される使用条件のリンクをクリックします。 それらの使用条件に同意してから、**「以下に表示されるサード・パーティー・サービス契約を読み、同意します」**チェック・ボックスを選択します。
    5. **「プロビジョン」**をクリックします。

## 結果

インスタンスのデプロイメントが自動的に開始されます。 注文が処理されていることを示す確認メッセージが表示されます。インスタンスの詳細を表示してデプロイメントの状況を確認できます。

インスタンスが正常にデプロイされると、[NetApp ONTAP Select インスタンスのコンポーネント](../netapp/np_netappoverview.html#netapp-ontap-select-instance-components)に記述されているコンポーネントが VMware 仮想プラットフォームにインストールされます。

インスタンスが使用可能になると、インスタンスの状況が**「使用可能」**に変わり、E メールで通知されます。

## 次に行うこと

注文した NetApp ONTAP Select インスタンスを表示して管理します。

**重要**: {{site.data.keyword.cloud_notm}} アカウントで作成した {{site.data.keyword.vmwaresolutions_short}} コンポーネントは、{{site.data.keyword.vmwaresolutions_short}} コンソールから管理する必要があります。{{site.data.keyword.slportal}}やその他の手段でコンソール以外から管理することはできません。 {{site.data.keyword.vmwaresolutions_short}} コンソール以外で変更した場合、変更がコンソールと同期されません。

**注意**: インスタンスを注文したときに {{site.data.keyword.cloud_notm}} アカウントにインストールされた {{site.data.keyword.vmwaresolutions_short}} コンポーネントを、{{site.data.keyword.vmwaresolutions_short}} コンソール以外で管理すると、環境が不安定になる可能性があります。 これには以下の管理アクティビティーが該当します。
*  コンポーネントの追加、変更、返却、または削除
*  コンポーネントのパワーオフ

   {{site.data.keyword.slportal}}での共有ストレージのファイル共有の管理は、上記アクティビティーに該当しません。 これには、共有ストレージのファイル共有の注文、削除 (マウントされている場合はデータ・ストアに影響する可能性があります)、承認、マウントなどのアクティビティーが含まれます。

## 関連リンク

* [NetApp ONTAP Select インスタンスの表示](np_viewinginstances.html)
* [NetApp ONTAP Select インスタンスの削除](np_deletinginstance.html)
* [　 NetApp ONTAP 9 ドキュメント・センター](http://docs.netapp.com/ontap-9/index.jsp?topic=%2Fcom.netapp.doc.exp-clus-peer%2Fhome.html)
* [Attach dedicated storage to NetApp ONTAP Select deployments](https://developer.ibm.com/recipes/tutorials/steps-to-attach-dedicated-storage-to-existing-ic4v-deployments-on-ibm-cloud/)
