---

copyright:

  years:  2016, 2018

lastupdated: "2018-06-08"

---

# Kapazität für vCenter Server-Instanzen erweitern und verringern

Sie können die Kapazität Ihrer VMware vCenter Server-Instanz entsprechend Ihren Geschäftsanforderungen erweitern oder verringern, indem Sie ESXi-Server hinzufügen oder entfernen.

Wenn Ihr erster Cluster vSAN als Speicher verwendet, kann das Hinzufügen von einem oder mehreren ESXi-Servern nach der Bereitstellung die Speicherkapazität des Clusters erhöhen.

## Vorbereitende Schritte

* Verwenden Sie nicht VMware vSphere Web Client, um ESXi-Server hinzuzufügen oder zu entfernen. Die Änderungen, die Sie in vSphere Web Client vornehmen, werden nicht mit der {{site.data.keyword.vmwaresolutions_short}}-Konsole synchronisiert.
* Eine vCenter Server-Instanz mit NFS-Speicher benötigt mindestens 2 ESXi-Server. Bei in V2.1 oder höheren Versionen bereitgestellten Instanzen können Sie den Standardcluster auf bis zu 51 ESXi-Server erweitern. Jeder Cluster, bei dem es sich nicht um den Standardcluster handelt, kann auf bis zu 59 ESXi-Server erweitert werden.
* Eine vCenter Server-Instanz mit vSAN-Speicher benötigt mindestens 4 ESXi-Server.
* Bevor Sie ESXi-Server mit installiertem Service "F5 on {{site.data.keyword.cloud_notm}}" oder "FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}}" entfernen, müssen Sie die VMs für F5 BIG-IP und FortiGate auf einen ESXi-Server verlagern, auf dem die VMs nicht aktuell gehostet werden.
* Stellen Sie vor dem Entfernen von ESXi-Servern mit installiertem Service "IBM Spectrum Protect&trade; Plus on {{site.data.keyword.cloud_notm}}" sicher, dass keine (fehlgeschlagenen oder laufenden) Sicherungs- oder Wiederherstellungsoperationen aktiv sind, da diese aktiven Operationen das Entfernen der ESXi-Server verhindern könnten.
* Wenn Sie ESXi-Server entfernen, werden die Server in den Wartungsmodus versetzt. Anschließend werden alle virtuellen Maschinen (VMs), die auf den Servern ausgeführt werden, migriert, bevor sie aus vCenter Server entfernt werden. Damit die Verlagerung von VMs maximal gesteuert werden kann, empfiehlt es sich, die zu entfernenden ESXi-Server in den Wartungsmodus zu versetzen und die auf ihnen ausgeführten VMs manuell mithilfe von VMware vSphere Web Client zu migrieren. Anschließend entfernen Sie die ESXi-Server in der {{site.data.keyword.vmwaresolutions_full}}-Konsole.
* Bei vCenter Server-Instanzen, die in V2.0 oder einer früheren Version bereitgestellt wurden, können Sie jeden Cluster auf bis zu 32 ESXi-Server erweitern. Für die Anzahl der {{site.data.keyword.baremetal_short}}-Instanzen, die Sie jeweils hinzufügen können, gilt Folgendes:
   * Bei Konfigurationen des Typs **S (Klein)**, **M (Mittel)** und **L (Groß)** können Sie gleichzeitig 1 bis 10 ESXi-Server hinzufügen.
   * Bei Konfigurationen des Typs **Angepasst** können Sie gleichzeitig 1 bis 20 ESXi-Server hinzufügen. Weitere Informationen zum Minimum von ESXi-Servern finden Sie im Abschnitt [Ist eine Serverinstanz mit zwei Knoten hoch verfügbar?](../vmonic/faq.html#is-a-two-node-vcenter-server-instance-highly-available-)

## Vorgehensweise

1. Klicken Sie in der {{site.data.keyword.vmwaresolutions_short}}-Konsole im linken Navigationsfenster auf **Bereitgestellte Instanzen**.
2. Klicken Sie in der Tabelle **vCenter Server-Instanzen** auf die Instanz, für die Sie die Kapazität erweitern oder verringern wollen.
3. Klicken Sie im linken Navigationsfenster auf **Infrastruktur**.
4. Klicken Sie in der Tabelle **CLUSTER** auf den Cluster, zu dem ESXi-Server hinzugefügt oder aus dem ESXi-Server entfernt werden sollen.
5. Gehen Sie zum Hinzufügen von ESXi-Servern folgendermaßen vor:
   1. Klicken Sie im Abschnitt **ESXi-Server** auf **Hinzufügen**.
   2. Geben Sie im Fenster **Server hinzufügen** die Anzahl der Server ein, die Sie hinzufügen wollen. Prüfen Sie geschätzten Kosten und klicken Sie dann auf **Hinzufügen**.
6. Um ESXi-Server zu entfernen, wählen Sie die entsprechenden Server im Abschnitt **ESXi-Server** aus und klicken Sie dann auf **Entfernen**.

## Ergebnisse

Nachdem Sie die Operation zum Hinzufügen oder Entfernen gestartet haben, stellen Sie möglicherweise eine leichte Verzögerung fest, während sich der Instanzstatus von **Bereit** in **Wird geändert** ändert. Warten Sie, bis die Operation vollständig abgeschlossen ist, bevor Sie weitere Änderungen an der Instanz vornehmen.

Sie werden per E-Mail benachrichtigt, dass Ihre Anforderung zum Hinzufügen oder Entfernen von ESXi-Servern verarbeitet wird. Der Status des Clusters, der den ESXi-Servern zugeordnet ist, ändert sich in **Wird geändert**. Beim Entfernen von Servern ist zu beachten, dass die ESXi-Server am Ende des Abrechnungszyklus für die {{site.data.keyword.cloud_notm}}-Infrastruktur (der in der Regel 30 Tage umfasst) vollständig von der {{site.data.keyword.cloud_notm}}-Infrastruktur zurückgefordert werden.

**Achtung** Die entfernten ESXi-Server werden Ihnen bis zum Ende des Abrechnungszyklus für die {{site.data.keyword.cloud_notm}}-Infrastruktur berechnet.

Wenn die neuen ESXi-Server nicht zur Liste im Cluster hinzugefügt werden, überprüfen Sie die E-Mail- oder Konsolenbenachrichtigungen, um weitere Details über den Fehler zu ermitteln.

## Zugehörige Links

* [vCenter Server-Teileliste](vc_bom.html)
* [Voraussetzungen und Planung für vCenter Server-Instanzen](vc_planning.html)
* [Cluster für vCenter Server-Instanzen hinzufügen, anzeigen und löschen](vc_addingviewingclusters.html)
* [Place a host in maintenance mode](http://pubs.vmware.com/vsphere-60/index.jsp?topic=%2Fcom.vmware.vsphere.resmgmt.doc%2FGUID-8F705E83-6788-42D4-93DF-63A2B892367F.html){:new_window}
* [Enhanced vMotion Compatibility (EVC) processor support](https://kb.vmware.com/selfservice/microsites/search.do?language=en_US&cmd=displayKC&externalId=1003212){:new_window}
