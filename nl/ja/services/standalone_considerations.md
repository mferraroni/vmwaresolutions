---

copyright:

  years:  2016, 2018

lastupdated: "2018-06-14"

---

# オンプレミスの VMware HCX on IBM Cloud インスタンスに関する考慮事項

オンプレミスで使用するために注文した HCX on {{site.data.keyword.cloud}} インスタンスをインストールまたは削除する前に、以下の考慮事項を検討してください。

**注:** vCenter Server with HCX on {{site.data.keyword.cloud_notm}} インスタンスでは、オンプレミス・サイトからの同時接続が 3 つまでに制限されています。

## オンプレミス HCX on IBM Cloud インスタンスをインストールする際の考慮事項

HCX on {{site.data.keyword.cloud_notm}} コンポーネントを {{site.data.keyword.cloud_notm}} とオンプレミス vSphere 環境の両方にインストールする必要があります。 HCX on {{site.data.keyword.cloud_notm}} サービスを {{site.data.keyword.cloud_notm}} 上の vCenter Server with Hybridity Bundle インスタンスにインストールしてから、オンプレミス HCX on {{site.data.keyword.cloud_notm}} インスタンスをインストールすることをお勧めします。 詳しくは、[HCX on {{site.data.keyword.cloud_notm}} に関する考慮事項](../services/hcx_considerations.html)を参照してください。

### IP アドレスに関する要件

HCX の全機能を利用するには、少なくとも 5 つのプライベート IP アドレスが必要で、それらにインターネットへのアクセスを許可する必要があります。

### オンプレミス HCX on IBM Cloud インスタンスのデプロイメント・プロセス

オンプレミス HCX on {{site.data.keyword.cloud_notm}} インスタンスを正常にインストールするには、以下のタスクを実行する必要があります。
1. {{site.data.keyword.vmwaresolutions_short}} コンソールで、以下のステップを実行します。
    1. 左側のナビゲーション・ペインから**「デプロイ済みインスタンス」**をクリックします。
    2. HCX on {{site.data.keyword.cloud_notm}} サービスがインストールされている vCenter Server with Hybridity Bundle インスタンスをクリックします。 これは、オンプレミス vSphere 環境からの接続先となるクラウド側に相当します。
    3. **「サービス」**タブで、**「インストール済みサービス」**をクリックします。
    4. **「HCX on {{site.data.keyword.cloud_notm}}」**カードをクリックします。
    5. **「HCX クラウド・コンソールの表示」**をクリックし、vCenter Server 資格情報を使用してコンソールにログインして、クラウド側の HCX on {{site.data.keyword.cloud_notm}} サービスの詳細を表示します。
2. **「HCX クラウド・コンソール」**で、以下のステップを実行します。
    1. **「管理」**タブをクリックします。
    2. **「システム更新」**タブで、**「ダウンロード・リンクの要求」**をクリックします。
    3. **「リンクのコピー」**をクリックし、このリンクを使用して、オンプレミス vSphere 環境へのアクセス権限によって HCX Enterprise Client をオンプレミス環境にダウンロードします。
3. VMware vSphere Web Client で、HCX Enterprise Client を HCX Manager 仮想アプライアンス (HCX Manager) としてオンプレミス環境にデプロイします。

   **注**: オンプレミス HCX Manager をプライベート・ネットワークにデプロイし、パブリック・ネットワークへのアクセスを許可する必要があります。 NSX Edge、Vyatta、または類似のゲートウェイを使用して、オンプレミス HCX Manager へのインターネット・アクセスを許可することができます。 使用するゲートウェイがプライベート・ネットワーク・アクセスとパブリック・ネットワーク・アクセスとで異なる場合は、デフォルト・ゲートウェイを使用してパブリック・ネットワーク・アクセスを許可し、オンプレミスの**「HCX Manager 管理コンソール」**を使用して、プライベート・ネットワーク・アクセス用の静的ルートを作成することをお勧めします。
4. HCX Manager のデプロイメントが完了したら、**「HCX Manager 管理コンソール」**を使用して、オンプレミス HCX Manager をアクティブ化します。 オンプレミス HCX Manager のアクティベーション・キーを入手するには、{{site.data.keyword.vmwaresolutions_short}} コンソールでオンプレミス HCX on {{site.data.keyword.cloud_notm}} インスタンスを注文します。 詳しくは、[オンプレミス HCX インスタンスの注文](../services/standalone_orderingserviceinstances.html)を参照してください。
5. HCX on {{site.data.keyword.cloud_notm}} サービスの注文時に自己署名 SSL 証明書を使用した場合は、以下のステップを実行して、その証明書をオンプレミス HCX Manager にインポートする必要があります。
    1. オンプレミスの**「HCX Manager 管理コンソール」**で、**「管理」**タブをクリックします。
    2. 左側のナビゲーション・ペインで、**「トラステッド CA 証明書」**をクリックし、右側の**「インポート」**をクリックします。
    3. **「URL」**をクリックし、適用する証明書の URL、つまり **HCX クラウド IP** (``https://<cloud-side public IP>``) を入力します。これは、{{site.data.keyword.vmwaresolutions_short}} コンソールの HCX on {{site.data.keyword.cloud_notm}} サービス詳細ページで確認できます。
    4. **「適用」**をクリックします。

オンプレミス HCX Manager の基本的なセットアップがこれで完了しました。 続いて、オンプレミス HCX on {{site.data.keyword.cloud_notm}} サイトをクラウド側 HCX サイトとペアにします。

詳しくは、[VMware Hybrid Cloud Extension](https://cloud.vmware.com/vmware-hcx) を参照してください。

## オンプレミス HCX on IBM Cloud インスタンスを削除する際の考慮事項

オンプレミスで使用するために注文した HCX on {{site.data.keyword.cloud_notm}} インスタンスを削除する前に、以下の考慮事項を検討してください。
1. VMware vSphere Web Client で、HCX ユーザー・インターフェースに移動し、以下の項目を確認します。
    1. HCX マイグレーションまたは災害復旧操作が実行中でないことを確認します。
    2. すべての拡張ネットワークが削除されていることを確認します。
    3. ペアのクラウド・サイトとの相互接続コンポーネントがすべて削除されていることを確認します。

   **重要**: 次のステップに進む前に、考慮事項をすべて完了している必要があります。 そうしないと、オンプレミス HCX on {{site.data.keyword.cloud_notm}} インスタンスのライセンスがキャンセルされ、マイグレーションを実行できなくなります。そして、エラーが HCX コンポーネントに発生する可能性があります。  
2. {{site.data.keyword.vmwaresolutions_short}} コンソールで、オンプレミス HCX Manager のアクティベーション・キーを入手するために注文した、オンプレミス HCX on {{site.data.keyword.cloud_notm}} インスタンスを削除します。 コンソールで、削除したインスタンスが使用不可になったことを確認してから、次のステップに進んでください。

   詳しくは、[オンプレミス HCX on {{site.data.keyword.cloud_notm}} インスタンスの削除](../services/standalone_deletingserviceinstances.html)を参照してください。
3. VMware vSphere Web Client で、オンプレミス HCX Manager を削除します。

## 関連リンク

* [オンプレミス HCX on {{site.data.keyword.cloud_notm}} インスタンスの参照](../services/standalone_viewingserviceinstances.html)
* [HCX の用語集](hcx_glossary.html)
* [VMware Hybrid Cloud Extension の資料](https://hcx.vmware.com/#vm-documentation)
* [VMware HCX Enterprise installation and user guide](https://hcx.vmware.com/content/docs/vmware-hcx-enterprise-install-guide.pdf){:new_window}
* [IBM サポートへのお問い合わせ](../vmonic/trbl_support.html)
