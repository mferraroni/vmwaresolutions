---

copyright:

  years:  2016, 2018

lastupdated: "2018-06-08"

---

# F5 on IBM Cloud の注文

F5 on {{site.data.keyword.cloud_notm}} サービスを注文するには、BIG-IP Virtual Edition (VE) を組み込む形で新しいインスタンスを注文するか、BIG-IP VE を既存のインスタンスに追加します。

## 新しいインスタンスでの F5 on IBM Cloud の注文

以下のいずれかの方法を使用して、新しいインスタンスで F5 on {{site.data.keyword.cloud_notm}} を注文できます。
* {{site.data.keyword.vmwaresolutions_full}} コンソールから新しいインスタンスを注文する時に、**「サービス」**セクションで**「F5 on IBM Cloud」**を選択します。
* {{site.data.keyword.cloud_notm}} カタログから**「F5 on {{site.data.keyword.cloud_notm}} service」**を選択し、サービス設定を指定し、**「Add to New Instance」**を選択します。

## 既存のインスタンスでの F5 on IBM Cloud の注文

以下のいずれかの方法を使用して、既存のインスタンスに F5 on {{site.data.keyword.cloud_notm}} サービスを追加できます。
* {{site.data.keyword.vmwaresolutions_short}} コンソールから、サービスを追加する対象のインスタンスを表示し、左側のナビゲーション・ペインにある**「サービス」**をクリックし、**「サービスの追加」**をクリックします。
* {{site.data.keyword.cloud_notm}} カタログから**「F5 on IBM Cloud service」**を選択し、サービス設定を指定し、**「Add to Existing Instance」**を選択します。

## F5 on IBM Cloud サービスの構成

このサービスを注文する際には、以下の設定を行います。

### 名前

サービス名を入力します。

### ライセンス・モデル

F5 on {{site.data.keyword.cloud_notm}} サービスのライセンス・モデルには、以下のオプションがあります。
<dl class="dl">
        <dt class="dt dlterm">Good</dt>
        <dd class="dd">このオファーでは、フルプロキシー・アーキテクチャーとして機能する BIG-IP Local Traffic Manager™ (LTM) VE を利用して、ローカル・トラフィックをインテリジェントに管理し、SSL トラフィックを完全に可視化し、分析とヘルス・モニタリングを行うことによって、ユーザーが常にアプリケーション・サーバーを使用できるようにします。</dd>
        <dt class="dt dlterm">Better</dt>
        <dd class="dd">このオファーは**「Good」**オプションの利点をベースに構築されており、BIG-IP DNS™、BIG-IP Advanced Firewall Manager™ (AFM)、BIG-IP Application Acceleration Manager™ (AAM) の各モジュールが追加されています。 グローバル・トラフィック管理サービス、アプリケーション・パフォーマンス最適化機能、高機能ネットワーク・ファイアウォール機能、分散型サービス妨害 (Distributed Denial of Service: DDoS) 緩和機能を備えています。</dd>
        <dt class="dt dlterm">Best</dt>
        <dd class="dd">**「Good」**と**「Better」**のオファーに加えて、BIG-IP Application Security Manager™ (ASM) が L7 DDoS、Open Web Application Security Project (OWASP) の上位 10 の脅威、一般的なアプリケーション脆弱性に対して、総合的にアプリケーションを保護します。 SSO (シングル・サインオン) や MFA (多要素認証) などのフィーチャーが取り込まれた BIG-IP Access Policy Manager™ (APM) を使用することにより、ユーザーは、マルチクラウド環境内に置かれたアプリケーションに安全かつ簡単にアクセスできます。</dd>
</dl>

**重要**: サービスのインストール後にライセンス・モデルを変更することはできません。 ライセンス・モデルを変更するには、既存のサービスを削除し、別のライセンス・モデルを使用してサービスを再インストールする必要があります。

### 最大帯域幅

F5 BIG–IP アプライアンスの最大スループットを指定します。

## 関連リンク

* [F5 on {{site.data.keyword.cloud_notm}} の概要](f5_considerations.html)
* [F5 on {{site.data.keyword.cloud_notm}} の管理](managing_f5.html)
* [Cloud Foundation インスタンス用サービスの注文、表示、削除](../sddc/sd_addingremovingservices.html)
* [vCenter Server インスタンスのサービスの注文、表示、削除](../vcenter/vc_addingremovingservices.html)
* [vCenter Server with Hybridity Bundle インスタンスのサービスの注文、表示、削除](../vcenter/vc_hybrid_addingremovingservices.html)
* [IBM サポートへのお問い合わせ](../vmonic/trbl_support.html)
* [FAQ](../vmonic/faq.html)
* [F5 Deployment Guides](https://f5.com/solutions/deployment-guides){:new_window}
