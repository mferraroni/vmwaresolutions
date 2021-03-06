---

copyright:

  years:  2016, 2018

lastupdated: "2018-06-04"

---

# vCenter Server 实例的联网注意事项

请查看以下信息，以获取有关 vCenter Server 实例的联网注意事项和需求的详细信息。确保满足这些需求，以便实例能正常运行。

## vCenter Server 实例的联网组件

要查看 vCenter Server 实例中包含的联网组件，请参阅 [vCenter Server 概述](vc_vcenterserveroverview.html)中的 _vCenter Server 技术规范_部分。

## NSX 防火墙注意事项

如果使用的是 NSX 分布式防火墙 (DFW)，请查看以下需求：
* 必须针对来自 {{site.data.keyword.IBM}} CloudDriver 虚拟机 (VM) 的所有通信配置规则，以允许所有协议在 IP 地址 `10.0.0.0/8` 和 `161.26.0.0/16` 上进行通信。
* 必须创建允许将 HTTPS 流量从 IBM CloudDriver VM 传递到任何目标的 DFW 规则。
* 该 DFW 规则必须位于会阻止流量进出这些 VM 的其他任何规则之前。

## 将 NSX 与虚拟机配合使用

在 vCenter Server 实例部署期间，将在该实例中订购、安装、许可和配置 VMware NSX。此外，还会设置 NSX Manager、NSX Controller 和 NSX 传输区域，并且每个 ESXi 服务器都会配置有 NSX 组件。

此外，还部署了 NSX Edge 服务网关，以供工作负载 VM 使用。有关更多信息，请参阅[配置网络以将客户管理的 NSX ESG 用于 VM](vc_esg_config.html#configuring-your-network-to-use-the-customer-managed-nsx-esg-with-your-vms)。

## 更改 NSX 组件密码时的注意事项

在更改 NSX Manager、NSX Controller 和 NSX Edge 的密码之前，请查看以下注意事项：
* 不要更改 NSX Manager 的密码，此密码可以在 {{site.data.keyword.vmwaresolutions_short}} 控制台中实例的**摘要**页面上找到。
* 可以更改 NSX Controller 的密码。有关如何更改 NSX Controller 密码的指示信息，请参阅[更改控制器密码](https://docs.vmware.com/en/VMware-NSX-for-vSphere/6.2/com.vmware.nsx.admin.doc/GUID-2667DD9E-E2F5-4403-BAC2-C7D1BBC23228.html)。
* 可以更改客户管理的 VMware NSX Edge 服务网关 (ESG) 的密码和 SSH 设置。不要更改“管理 VMware NSX Edge 服务网关 (ESG)”及相关分布式逻辑路由器的密码。

## 相关链接

* [NSX 概述](https://docs.vmware.com/en/VMware-NSX-for-vSphere/6.2/com.vmware.nsx-cross-vcenter-install.doc/GUID-10944155-28FF-46AA-AF56-7357E2F20AF4.html){:new_window}
* [NSX Edge 服务网关](https://www.ibm.com/cloud/garage/content/architecture/virtualizationArchitecture/nsx-esg){:new_window}
* [管理 NAT 规则](https://docs.vmware.com/en/VMware-NSX-for-vSphere/6.2/com.vmware.nsx.admin.doc/GUID-5896D8CF-20E0-4691-A9EB-83AFD9D36AFD.html){:new_window}
