---

copyright:

  years:  2016, 2018

lastupdated: "2018-06-14"

---

# FortiGate Virtual Appliance on IBM Cloud overview

The FortiGate Virtual Appliance on {{site.data.keyword.cloud}} service deploys a pair of FortiGate Virtual Appliances to your environment, which can help you reduce risk by implementing critical security controls within your virtual infrastructure.

You can install multiple instances of this service as needed. You can manage this service by using the FortiOS Web Client or the command line interface via SSH.

**Availability**: This service is available only to instances that are deployed in V2.0 or later releases.

## Components of FortiGate Virtual Appliance on IBM Cloud

When you order the FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} service, a pair of FortiGate Virtual Appliances is deployed with:
* A network interface configured for the management network.
* Nine additional network interfaces that you can configure to protect data traffic, as needed.

The FortiGate Virtual Appliances are not preconfigured as highly available (HA) pair. After deployment, you can configure HA settings, which includes Virtual Router Redundancy Protocol (VRRP) and FortiGate Cluster Protocol (FGCP), according to your needs.

## Considerations when installing FortiGate Virtual Appliance on IBM Cloud

Review the following considerations before you install the FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} service:
* The FortiGate virtual machines (VMs) will be deployed only into the default cluster.
* Based on the deployment size and license model that you select, the two FortiGate VMs are deployed with one of the following configurations:
    * Small (2 vCPUs / 4 GB RAM)
    * Medium (4 vCPUs / 6 GB RAM)
    * Large (8 vCPUs / 12 GB RAM)

  In addition, 100% of CPU and RAM for the two FortiGate VMs are also reserved because these VMs are in the data plane of the network
  communications and it is critical that resources are still available for them.

  To calculate the CPU and RAM reservation for a single FortiGate VM, use the following formula:
   * `CPU reservation = CPU speed of ESXi server * number of vCPUs`
   * `RAM reservation = RAM size`
* When you deploy an HA-pair of FortiGate Virtual Appliances to you instance, SNAT and firewall rules are defined on the Management NSX Edge Services Gateway (ESG) along with static routes on the FortiGate Virtual Appliances to allow outbound HTTPS communications from your instance to the public network for license activation and for acquiring latest security policies and content.
* You cannot change the license level after service installation. To change the license level, you must remove the existing service and then reinstall the service by selecting a different license option.
* You must meet the following requirements to avoid failures with FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}}:
   * At least two active ESXi servers are available for the two FortiGate VMs to be deployed with the anti-affinity rule of keeping the VMs on separate servers.
   * The two active ESXi servers have enough resources available so that one FortiGate VM can be hosted on each ESXi server with 100% CPU and RAM reservation.
   * VMware vSphere HA has enough resources to host two FortiGate VMs with 100% CPU and RAM.

  Due to these requirements, you must plan for the space needed for FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} carefully. If needed, before ordering FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}}, add 1 - 2 ESXi servers to your instance, or reduce the vSphere HA CPU reservation for failover, or both.

## FortiGate Virtual Appliance on IBM Cloud order example

You order a VMware vCenter Server **Small** instance with 2 ESXi servers with the following configuration: 16 cores at 2.10 GHz each with 128 GB RAM. For FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}}, you select the **Large** (8 vCPUs / 12 GB RAM) for deployment size and any subscription license model.

In this case, a single FortiGate VM requires, on each server:
* 2.1 GHz * 8 vCPU = 16.8 GHz of CPU, and
* 12 GB RAM

In total, that is 33.6 GHz CPU and 24 GB RAM for two FortiGate VMs.

Each ESXi server has a capacity of 16 cores * 2.1 GHz = 33.6 GHz, so we meet the first two requirements if both servers are active and there is at least 16.8 GHz of CPU and 12 GB RAM available on each server.

By default however, vSphere HA reserves 50% of CPU and RAM for failover on vCenter Server instances that were initially deployed with 2 ESXi servers, so we only have:

`50% of 2 * 16 cores * 2.1 GHz = 33.6 GHz available`

Since other workloads will exist on the ESXi servers, for example, IBM CloudDriver, VMware NSX Controller, or VMware NSX Edge, by using these resources, the third requirement is not met. This is because we need 33.6 GHz of CPU and 24 GB RAM for the two FortiGate VMs.

In this case, the FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} installation might fail, unless at least one ESXi server is added to the environment and vShpere HA failover reservations are updated appropriately to ensure that there are enough resources for two FortiGate VMs.

If additional resources are needed to run the FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} service, you can add more ESXi servers before installing the service.

## Considerations when removing FortiGate Virtual Appliance on IBM Cloud

Before you remove the FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} service, ensure that the configuration of the existing FortiGate Virtual Appliances is removed correctly. Specifically, network traffic must be routed around FortiGate Virtual Appliances instead of through FortiGate Virtual Appliances. Otherwise, the existing data traffic within your environment might be impacted.

## Related links

* [Ordering FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}}](fortinetvm_ordering.html)
* [Managing FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}}](managingfortinetvm.html)
* [Contacting IBM Support](../vmonic/trbl_support.html)
* [FAQ](../vmonic/faq.html)
* [Fortinet website](https://www.fortinet.com/){:new_window}
* [Fortinet Document Library](http://docs.fortinet.com/fortigate/admin-guides){:new_window}
