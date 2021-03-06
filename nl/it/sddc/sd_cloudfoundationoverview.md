---

copyright:

  years:  2016, 2018

lastupdated: "2018-06-22"

---

# Panoramica di Cloud Foundation

Quando ordini VMware Cloud Foundation on {{site.data.keyword.cloud}}, viene distribuito automaticamente un intero ambiente VMware. La distribuzione di base è composta da quattro {{site.data.keyword.baremetal_short}} {{site.data.keyword.cloud_notm}} con lo stack VMware Cloud Foundation preinstallato e configurato per fornire una piattaforma SDDC (Software-Defined Data Center) unificata. Cloud Foundation integra nativamente VMware vSphere, VMware NSX, VMware Virtual SAN e la sua architettura si basa su progetti convalidati da VMware.

## Architettura di Cloud Foundation

Il seguente grafico illustra l'architettura generale e i componenti della distribuzione di Cloud Foundation.

Figura 1. Architettura di Cloud Foundation

![Architettura di Cloud Foundation](sd_architecture.svg "Architettura di Cloud Foundation")

### Infrastruttura fisica

Questo livello fornisce l'infrastruttura fisica (risorse di calcolo, archiviazione e rete) che deve essere utilizzata dall'infrastruttura virtuale.

### Infrastruttura di virtualizzazione (calcolo, archiviazione e rete)

Questo livello virtualizza l'infrastruttura fisica attraverso diversi prodotti VMware:
* VMware vSphere virtualizza le risorse di calcolo fisiche.
* VMware Virtual SAN (vSAN) fornisce l'archiviazione condivisa definita dal software in base all'archiviazione nei server fisici.
* VMware NSX è la piattaforma di virtualizzazione di rete che fornisce componenti di rete logica e reti virtuali.

### Gestione della virtualizzazione

Questo livello è costituito da vCenter Server, che rappresenta il livello di gestione per l'ambiente virtualizzato. Gli stessi strumenti e script familiari compatibili con l'API vSphere possono essere utilizzati per gestire l'ambiente VMware ospitato da IBM.

Nella console {{site.data.keyword.vmwaresolutions_short}}, puoi espandere e contrarre la capacità delle tue istanze utilizzando la funzionalità di aggiunta e rimozione di server ESXi. Inoltre, sono disponibili anche funzioni di gestione del ciclo di vita come l'applicazione di aggiornamenti e l'aggiornamento dei componenti VMware nell'ambiente ospitato.

Per i dettagli sull'architettura, consulta [Panoramica della soluzione](../archiref/solution/solution_overview.html).

## Componenti dell'istanza Cloud Foundation

Nella tua istanza Cloud Foundation sono inclusi i seguenti componenti.

**Nota**: gli addebiti sostenuti per hardware, rete, macchine virtuali e archiviazione potrebbero variare in base al {{site.data.keyword.CloudDataCent_notm}} selezionato per la distribuzione.

### Bare Metal Server

Puoi ordinare {{site.data.keyword.baremetal_short}} {{site.data.keyword.cloud_notm}} con una delle seguenti configurazioni:
*  **Personalizzato**: {{site.data.keyword.baremetal_short}} con il modello CPU e la dimensione della RAM da te selezionati.   
   * 2-CPU Intel Broadwell (Intel Xeon E5-2600 v4 series)
   * 2-CPU Intel Skylake (Intel Xeon 4100/5100/6100 series)
**Nota:** se intendi utilizzare l'archiviazione vSAN, la configurazione richiede quattro {{site.data.keyword.baremetal_short}}.
* **Preconfigurato**: 2-CPU Intel Broadwell (Intel Xeon E5-2600 v4 series)
  * **Small** (Dual Intel Xeon E5-2650 v4 / 24 core totali, 2,2 GHz / 128 GB di RAM / 12 dischi)
  * **Large** (Dual Intel Xeon E5-2690 v4 / 28 core totali, 2,6 GHz / 512 GB di RAM / 12 dischi)

### Rete

Vengono ordinati i seguenti componenti di rete:
* Doppi uplink di rete privata e pubblica da 10 Gbps
* Tre VLAN (Virtual LAN): una VLAN pubblica e due VLAN private
* Gateway dei servizi edge (ESG) VMware NSX sicuro dei servizi di gestione per il traffico di gestione HTTPS in uscita, distribuito da IBM come parte della tipologia di rete di gestione. Questo ESG viene utilizzato dalle macchine virtuali di gestione IBM per comunicare con specifici componenti di gestione IBM esterni correlati all'automazione. Per ulteriori informazioni, vedi [L'edge NSX dei servizi di gestione rappresenta un rischio per la sicurezza?](../vmonic/faq.html#does-the-management-services-nsx-edge-pose-a-security-risk-)

  **Importante**: questo ESG non è accessibile a te e non puoi usarlo. Se lo modifichi, potresti non essere in grado di gestire l'istanza Cloud Foundation dalla console {{site.data.keyword.vmwaresolutions_short}}. Inoltre, tieni presente che l'utilizzo di un firewall o la disabilitazione delle comunicazioni ESG ai componenti di gestione IBM esterni causerà l'inutilizzabilità di {{site.data.keyword.vmwaresolutions_short}}.

* La funzione EVC (Enhanced vMotion Compatibility) viene abilitata automaticamente se disponi di un cluster esistente con i server ESXi supportati dalla versione corrente di VMware vSphere. EVC fornisce la compatibilità vMotion per tutti i server ESXi in un cluster garantendo che tutti i server ESXi del cluster espongano lo stesso insieme di funzioni CPU alle macchine virtuali. Utilizzando EVC, le macchine virtuali possono migrare tra qualsiasi server ESXi nel cluster, anche se le reali CPU sui server ESXi potrebbero essere diverse.

### VSI (Virtual Server Instance)

Vengono ordinate le seguenti VSI (Virtual Server Instance):
* Una VSI per i servizi Microsoft Active Directory (AD) e Domain Name System (DNS), richiesta per il supporto della configurazione multisito. La specifica di questa VSI è: Windows 2012 R2 (8 GB di RAM / 2 core CPU / disco da 100 GB / Doppi uplink privati da 1 Gbps).
* Una VSI per IBM CloudBuilder, che viene arrestata al termine della distribuzione dell'istanza.
* (Se viene ordinato Veeam on {{site.data.keyword.cloud_notm}}) Viene ordinata una VSI per il servizio di backup Veeam.

### Archiviazione

Viene ordinata la seguente archiviazione, a seconda della configurazione di {{site.data.keyword.baremetal_short}} che hai selezionato:
* Due dischi di avvio SATA da 1 TB
* Due dischi di cache SSD (Solid State Disk) da 960 GB
* Un controller disco RAID
* Solo per la configurazione **Personalizzato**, puoi impostare il numero di unità disco e il tipo e la capacità del disco in base ai tuoi requisiti.
* Solo per la configurazione **Preconfigurato**, **Small**: due dischi con capacità SSD da 1,9 TB
* Solo per la configurazione **Preconfigurato**, **Large**: quattro dischi con capacità SSD da 3,8 TB


### Archiviazione per i backup

Viene ordinata un'archiviazione a livello di file condivisa da 2 TB, che può essere ampliata fino a 12 TB.

**Nota**: l'archiviazione per i backup non è un componente standard per le istanze Cloud Foundation. Quando ordini un'istanza, puoi scegliere se desideri l'archiviazione per i backup selezionando o deselezionando un servizio di backup.

### Licenze (fornite da IBM o BYOL) e tariffe

* Quattro VMware vSphere Enterprise Plus 6.5u1
* Quattro VMware vCenter Server 6.5
* Quattro VMware NSX Enterprise 6.3
* Quattro VMware vSAN Advanced o Enterprise 6.6
* Quattro licenze SDDC Manager (solo fornite da IBM)
* Quattro tariffe per supporto e servizi

## Componenti del nodo di espansione Cloud Foundation

Ogni nodo di espansione Cloud Foundation verrà distribuito e addebitato per i seguenti componenti nel tuo account {{site.data.keyword.cloud_notm}}.

### Hardware per i nodi di espansione

Un Bare Metal Server {{site.data.keyword.cloud_notm}} con la configurazione presentata in [Componenti dell'istanza Cloud Foundation](../sddc/sd_cloudfoundationoverview.html#cloud-foundation-instance-components).

### Licenze e tariffe per i nodi di espansione

* Un VMware vSphere Enterprise Plus 6.5u1
* Un VMware vCenter Server 6.5
* Un VMware NSX Enterprise 6.3
* Un VMware vSAN Advanced o Enterprise 6.6
* Una licenza SDDC Manager
* Una tariffa per supporto e servizi

**Importante**: devi gestire i componenti {{site.data.keyword.vmwaresolutions_short}} creati nel tuo account {{site.data.keyword.cloud_notm}} solo attraverso la console {{site.data.keyword.vmwaresolutions_short}}, non il {{site.data.keyword.slportal}} o qualsiasi altro mezzo all'esterno della console. Se modifichi questi componenti al di fuori della console {{site.data.keyword.vmwaresolutions_short}}, le modifiche non saranno sincronizzate con la console.

**ATTENZIONE**: la gestione di un qualsiasi componente {{site.data.keyword.vmwaresolutions_short}}, installato nel tuo account {{site.data.keyword.cloud_notm}} nel momento in cui hai ordinato l'istanza, dall'esterno della console {{site.data.keyword.vmwaresolutions_short}} può rendere instabile il tuo ambiente. Queste attività di gestione includono:
*  Aggiunta, modifica, restituzione o rimozione dei componenti
*  Espansione o contrazione della capacità dell'istanza mediante l'aggiunta o la rimozione di server ESXi
*  Spegnimento dei componenti
*  Riavvio dei servizi

   Le eccezioni a queste attività includono la gestione delle condivisioni file di archiviazione condivisa dal {{site.data.keyword.slportal}}. Tali attività includono: l'ordine, l'eliminazione (che potrebbe influire sugli archivi di dati, se montati), l'autorizzazione e il montaggio di condivisioni file di archiviazione condivisa.

## Link correlati

* [Distinta base del software Cloud Foundation](sd_bom.html)
* [Pianificazione per le istanze Cloud Foundation](sd_planning.html)
* [Ordine di istanze Cloud Foundation](sd_orderinginstance.html)
* [Centro di documentazione di VMware vSphere](https://pubs.vmware.com/vsphere-60/index.jsp){:new_window}
* [Centro di documentazione di VMware NSX 6](https://pubs.vmware.com/NSX-6/index.jsp){:new_window}
* [EVC and CPU Compatibility FAQ](https://kb.vmware.com/s/article/1005764)
