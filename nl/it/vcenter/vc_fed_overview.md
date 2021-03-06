---

copyright:

  years:  2016, 2018

lastupdated: "2018-06-11"

---

# Panoramica di VMware Federal on IBM Cloud

VMware Federal on {{site.data.keyword.cloud}} fornisce supporto per ordinare un'istanza vCenter Server di base oltre a fornire alle agenzie del Governo federale degli Stati Uniti l'opzione per proteggere le istanze vCenter Server distribuite. La selezione dell'opzione per proteggere le istanze distribuite rimuove le informazioni sensibili memorizzate sull'istanza e rimuove la connessione di gestione aperta per l'accesso in corso all'istanza per le funzioni di gestione, come l'aggiunta e la rimozione di host e cluster. Dopo aver selezionato l'opzione di protezione, vengono disabilitate tutte le funzioni di gestione ad eccezione dell'eliminazione completa dell'istanza.

Per ulteriori informazioni su vCenter Server on {{site.data.keyword.cloud_notm}} e sull'architettura di vCenter Server, vedi [Panoramica di vCenter Server](vc_vcenterserveroverview.html).

**Attenzione:** VMware Federal on {{site.data.keyword.cloud_notm}} offre solo un sottoinsieme delle offerte di vCenter Server. La configurazione multisito, i server bare metal {{site.data.keyword.cloud_notm}} preconfigurati, BYOL (Bring Your Own License) e l'opzione per ordinare servizi aggiuntivi non sono supportati.

## Componenti dell'istanza vCenter Server per VMware Federal on IBM Cloud

Sono inclusi i seguenti componenti:

### Bare Metal Server

Puoi ordinare due o più {{site.data.keyword.baremetal_short}} personalizzati con una delle seguenti configurazioni:

* 2-CPU Intel Broadwell (Intel Xeon E5-2600 v4 series)
* 2-CPU Intel Skylake (Intel Xeon 4100/5100/6100 series)

Per la configurazione dell'archiviazione NFS, il numero consigliato di {{site.data.keyword.baremetal_short}} è impostato sul valore predefinito di tre.

**Nota:** se selezioni l'archiviazione vSAN, la configurazione richiede quattro {{site.data.keyword.baremetal_short}}.

### Rete

Vengono ordinati i seguenti componenti di rete:
*  Tre VLAN (Virtual LAN): una VLAN pubblica e due VLAN private
*  Una VXLAN (Virtual eXtensible LAN) con DLR (Distributed Logical Router) per la potenziale comunicazione est-ovest tra carichi di lavoro locali connessi alle reti di livello 2 (L2). La VXLAN viene distribuita come topologia di instradamento di esempio, che puoi modificare, compilare o rimuovere. Puoi anche aggiungere zone di sicurezza collegando ulteriori VXLAN a nuove interfacce logiche sul DLR.
*  Due gateway dei servizi edge VMware NSX:
  * Un gateway dei servizi edge (ESG) VMware NSX sicuro dei servizi di gestione per il traffico di gestione HTTPS in uscita, distribuito da IBM come parte della tipologia di rete di gestione. Questo ESG viene utilizzato dalle macchine virtuali di gestione IBM per comunicare con specifici componenti di gestione IBM esterni correlati all'automazione. Per ulteriori informazioni, vedi [Configurazione della rete per utilizzare l'ESG gestito dal cliente](../vcenter/vc_esg_config.html#configuring-your-network-to-use-the-customer-managed-nsx-esg-with-your-vms).

    **Importante**: questo ESG non è accessibile a te e non puoi usarlo. Se lo modifichi, potresti non essere in grado di gestire l'istanza vCenter Server dalla console {{site.data.keyword.vmwaresolutions_short}}. Inoltre, tieni presente che l'utilizzo di un firewall o la disabilitazione delle comunicazioni ESG ai componenti di gestione IBM esterni causerà l'inutilizzabilità di {{site.data.keyword.vmwaresolutions_short}}.
  * Un gateway dei servizi edge VMware NSX sicuro gestito dal cliente per il traffico del carico di lavoro HTTPS in uscita e in entrata, distribuito da IBM come template che puoi modificare per fornire l'accesso VPN o l'accesso pubblico. Per ulteriori informazioni, vedi [L'edge NSX gestito dal cliente rappresenta un rischio per la sicurezza?](../vmonic/faq.html#does-the-customer-managed-nsx-edge-pose-a-security-risk-).

  **Nota**: il gateway dei servizi edge (ESG) VMware NSX per il traffico di gestione HTTPS in uscita viene rimosso come parte dell'azione per proteggere la tua istanza VMware Federal distribuita. Per ulteriori informazioni, vedi [Protezione di istanze VMware Federal](vc_fed_securinginstance.html).

### VSI (Virtual Server Instance)

Vengono ordinate le seguenti VSI (Virtual Server Instance):
* Una VSI per IBM CloudBuilder, che viene arrestata al termine della distribuzione dell'istanza.
* (Per le istanze della V2.3 e successive) Puoi scegliere di distribuire una singola VSI di Microsoft Windows Server per Microsoft Active Directory (AD) o due VM Microsoft Windows ad alta disponibilità nel cluster di gestione per migliorare la sicurezza e la solidità.
* (Per le istanze della V2.2) Viene distribuita una VSI di Microsoft Windows Server per Microsoft Active Directory (AD) consultabile, che funziona come DNS per l'istanza in cui sono registrati gli host e le macchine virtuali.

### Archiviazione

Durante la distribuzione iniziale, puoi scegliere tra le opzioni di archiviazione vSAN e NFS.

L'opzione vSAN offre configurazioni personalizzate, con varie opzioni per tipo e quantità di dischi:
* Quantità dischi: 2, 4, 6 o 8.
* Disco di archiviazione: SED SSD da 960 GB, SED SSD da 1,9 TB o SED SSD da 3,8 TB.

  Inoltre, vengono ordinati 2 dischi di cache da 960 GB per ciascun host.

L'opzione NFS offre l'archiviazione a livello di file condivisa personalizzata per carichi di lavoro con varie opzioni per dimensioni e prestazioni:
* Dimensioni: 1, 2, 4, 8 o 12 TB.
* Prestazioni: 2, 4 o 10 IOPS/GB.
* Configurazione individuale per le condivisioni file.

Se scegli l'opzione NFS, viene ordinata una condivisione file da 2 TB con 4 IOPS/GB per i componenti di gestione.

### Licenze fornite da IBM e tariffe

* VMware vSphere Enterprise Plus 6.5u1
* VMware vCenter Server 6.5
* VMware NSX Service Providers Edition (Base, Advanced o Enterprise) 6.3
* (Per i cluster vSAN) VMware vSAN Advanced o Enterprise 6.6

## Componenti del nodo di espansione vCenter Server

Ogni nodo di espansione vCenter Server verrà distribuito e addebitato per i seguenti componenti nel tuo account {{site.data.keyword.cloud_notm}}.

### Hardware per i nodi di espansione

Un Bare Metal Server con la configurazione presentata in [Componenti dell'istanza vCenter Server per VMware Federal on IBM Cloud](../vcenter/vc_fed_overview.html#vcenter-server-instance-components-for-vmware-federal-on-ibm-cloud).

### Licenze e tariffe per i nodi di espansione

* Un VMware vSphere Enterprise Plus 6.5u1
* Un VMware NSX Service Providers Edition (Base, Advanced o Enterprise) 6.3
* (Per i cluster vSAN) VMware vSAN Advanced o Enterprise 6.6

**Importante**: devi gestire i componenti {{site.data.keyword.vmwaresolutions_short}} creati nel tuo account {{site.data.keyword.cloud_notm}} solo attraverso la console {{site.data.keyword.vmwaresolutions_short}}, non il {{site.data.keyword.slportal_full}} o qualsiasi altro mezzo all'esterno della console. Se modifichi questi componenti al di fuori della console {{site.data.keyword.vmwaresolutions_short}}, le modifiche non saranno sincronizzate con la console.

**ATTENZIONE**: la gestione di un qualsiasi componente {{site.data.keyword.vmwaresolutions_short}}, installato nel tuo account {{site.data.keyword.cloud_notm}} nel momento in cui hai ordinato l'istanza, dall'esterno della console {{site.data.keyword.vmwaresolutions_short}} può rendere instabile il tuo ambiente. Queste attività di gestione includono:
*  Aggiunta, modifica, restituzione o rimozione dei componenti
*  Espansione o contrazione della capacità dell'istanza mediante l'aggiunta o la rimozione di server ESXi
*  Spegnimento dei componenti
<!--*  Restarting services-->

   Le eccezioni a queste attività includono la gestione delle condivisioni file di archiviazione condivisa dal {{site.data.keyword.slportal}}. Tali attività includono: l'ordine, l'eliminazione (che potrebbe influire sugli archivi di dati, se montati), l'autorizzazione e il montaggio di condivisioni file di archiviazione condivisa.

## Link correlati

* [Distinta base del software vCenter Server](vc_bom.html)
* [Requisiti e pianificazione per le istanze VMware Federal](vc_fed_planning.html)
* [Ordine di istanze VMware Federal](vc_fed_orderinginstance.html)
* [Protezione di istanze VMware Federal](vc_fed_securinginstance.html)
* [Come contattare il supporto IBM](../vmonic/trbl_support.html)
* [Archiviazione file e blocchi di {{site.data.keyword.cloud_notm}}](https://www.ibm.com/cloud/garage/content/architecture/virtualizationArchitecture/shared-storage){:new_window}
