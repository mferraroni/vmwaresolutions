---

copyright:

  years:  2016, 2018

lastupdated: "2018-06-08"

---

# 扩展和收缩 Cloud Foundation 实例的容量

可以根据业务需求，通过添加或除去 ESXi 服务器，扩展或收缩 VMware Cloud Foundation 实例的容量。

一个 Cloud Foundation 实例最多可有 5 个集群，其中一个是缺省集群。每个初始集群最多可有 51 个 ESXi 服务器，其他集群最多可有 59 个 ESXi 服务器。

## 开始之前

* 不要通过 VMware vSphere Web Client 来添加或除去 ESXi 服务器。在 VMware vSphere Web Client 上所做的更改不会与 {{site.data.keyword.vmwaresolutions_short}} 控制台同步。
* 缺省情况下，订购的基本平台具有 4 个 ESXi 服务器。可以将该平台扩展到最多 32 个 ESXi 服务器。但是，一次可以添加的 {{site.data.keyword.baremetal_short}} 数量如下：
   * 对于**小型**和**大型**配置，一次可以添加 1 到 10 个 ESXi 服务器。
   * 对于**定制**配置，一次可以添加 1 到 20 个 ESXi 服务器。
* 可以除去已添加的 ESXi 服务器。但无法除去缺省 ESXi 服务器。
* 在除去安装有 F5 on {{site.data.keyword.cloud_notm}} 或 FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} 的 ESXi 服务器之前，必须将 F5 BIG-IP 和 FortiGate VM 迁移到与当前托管 VM 的 ESXi 服务器不同的 ESXi 服务器。
* 在除去安装了 IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} 服务的 ESXi 服务器之前，请确保没有任何活动（失败或正在进行）的备份或复原操作，因为这些活动的操作可能会阻止除去 ESXi 服务器。

## 过程

1. 在 {{site.data.keyword.vmwaresolutions_short}} 控制台中，单击左侧导航窗格上的**部署的实例**。
2. 在 **Cloud Foundation 实例**表中，单击要扩展或收缩其容量的实例。
3. 在左侧导航窗格上，单击**基础架构**。
4. 在**集群**表中，单击要在其中添加或除去 ESXi 服务器的集群。
5. 要添加 ESXi 服务器，请完成以下步骤：
   1. 在 **ESXi 服务器**部分中，单击**添加**。
   2. 在**添加服务器**窗口中，输入要添加的服务器数，复查估算成本，然后单击**添加**。
6. 要除去 ESXi 服务器，请在 **ESXi 服务器**部分中选择要除去的服务器，然后单击**除去**。

## 结果

启动添加或除去操作后，在实例状态从**可供使用**更改为**正在修改**时，可能会略有延迟。在对实例进行其他更改之前，请允许该操作完全完成。

添加或除去 ESXi 服务器后，系统会通过电子邮件通知您。除去服务器时，请注意，{{site.data.keyword.cloud_notm}} 基础架构将在 {{site.data.keyword.cloud_notm}} 计费周期（通常为 30 天）结束时才会完全回收 ESXi 服务器。

**注意**：在所除去 ESXi 服务器的 {{site.data.keyword.cloud_notm}} 计费周期结束之前，仍然会对您计费。

如果在集群中看不到添加到列表中的新 ESXi 服务器，请检查电子邮件或控制台通知以查找有关该故障的更多详细信息。

## 相关链接

* [Cloud Foundation 材料清单](sd_bom.html)
* [针对 Cloud Foundation 实例的需求和规划](sd_planning.html)
* [添加、查看和删除 Cloud Foundation 实例的集群](sd_addingviewingclusters.html)
* [将主机置于维护模式](http://pubs.vmware.com/vsphere-60/index.jsp?topic=%2Fcom.vmware.vsphere.resmgmt.doc%2FGUID-8F705E83-6788-42D4-93DF-63A2B892367F.html){:new_window}
* [Enhanced vMotion Compatibility (EVC) 处理器支持](https://kb.vmware.com/selfservice/microsites/search.do?language=en_US&cmd=displayKC&externalId=1003212){:new_window}
