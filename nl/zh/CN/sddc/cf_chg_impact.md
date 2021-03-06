---

copyright:

  years:  2016, 2018

lastupdated: "2018-06-08"

---

# 关于更改 Cloud Foundation 工件的注意事项

更改保留用于 {{site.data.keyword.vmwaresolutions_full}} 的用户、资源或子网可能会影响 VMware Cloud Foundation 实例的管理操作。

## 特定于服务的用户帐户

每个服务在 vCenter Server 中都会创建一个内部用户帐户。此帐户是必需的，有了此帐户，与服务关联的管理操作才能连接到 vCenter Server 以对该服务执行操作。

**重要信息**：为了防止发生中断和连接问题，如果更改此用户帐户的用户标识、密码或密码到期时间设置，请确保同时更新关联服务中的相应信息。

此帐户的用户标识的格式为 `<service_name>-<service_uuid>@VSPHERE.LOCAL`。例如，Veeam on {{site.data.keyword.cloud_notm}} 服务用于连接到 vCenter Server 以执行安排的备份的用户标识为 `Veeam-<Veeam_uuid>@VSPHERE.LOCAL`。

## Cloud Foundation 实例的 VMware 资源

下表列出了在 {{site.data.keyword.vmwaresolutions_short}} 控制台外部更改 VMware 资源时，可能会影响到的操作。如果用于恢复的解决方案可用，那么还会提供该解决方案。

表 1. 对于 SSO 管理员（客户）影响到的操作

|尝试的更改|影响的操作|严重性|恢复方法|
|:------------- |:------------- |:--------------|:--------------|
|更改 VMware 虚拟数据中心名称。|添加 VMware 数据中心可能会失败，因为新 ESXi 服务器无法连接更改后的数据中心。|重要|将 VMware 虚拟数据中心名称更改回原始名称。|
|更改任何端口组名称。|添加 ESXi 服务器可能会失败。|重要|将端口组名称更改回原始名称。|
|更改集群名称。|添加 ESXi 服务器可能会失败。|重要|将集群名称更改回原始名称。
|更改公共或专用分布式虚拟交换机 (DVS) 名称。|添加 ESXi 服务器可能会失败。|重要|将 DVS 名称更改回原始名称。
|更改 VSAN 数据存储名称。|添加 ESXi 服务器可能会失败。<br><br>升级实例可能会失败。|重要|将 VSAN 数据存储名称更改回原始名称 **vsanDatastore**。
|更改实例名称或域名。|实例不可用。|严重|不适用

## Cloud Foundation 实例的管理子网

以下信息讨论了 {{site.data.keyword.vmwaresolutions_short}} 订购的子网，并提供了一些选项，供您订购额外子网以供自己使用。

**注意**：不要将这些组件用于其他用途，否则环境的稳定性将受到严重影响。

每次订购 {{site.data.keyword.cloud_notm}} 裸机服务器时，缺省情况下都会订购以下 IP 地址范围：

*  32 个 IP 地址的主公共范围
*  64 个 IP 地址的主专用范围

此外，还会为 {{site.data.keyword.vmwaresolutions_short}} 保留以下管理子网：

*  第一个 VLAN 上包含 64 个 IP 地址的两个可移植专用子网：一个用于管理，另一个用于 VTEPS。
*  第二个 VLAN 上包含 64 个 IP 地址的两个可移植专用子网：一个用于 vMotion，另一个用于 vSAN。
*  公用 VLAN 上包含 16 个 IP 地址的公用可移植子网。

如果需要使用更多子网，可以通过下列其中一种方式来获取要使用的 IP 地址：

* **选项 1（建议）**：使用 VMware NSX 虚拟网络覆盖。订购时提供了样本 VXLAN 模板。此 VXLAN 模板可用作构建 SDN 的起点。
* **选项 2**：订购您自己的可移植公用子网或专用子网以获取 IP 地址。要使订购的子网区别于管理子网，可以向订购的所有子网添加注释。
