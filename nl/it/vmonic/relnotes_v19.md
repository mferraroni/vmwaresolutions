---

copyright:

  years:  2016, 2018

lastupdated: "2017-10-13"

---

# Note sulla release per la V1.9

Questa release include nuove funzioni, aggiornamenti dei componenti, miglioramenti dell'usabilità e correzioni di bug. Per un elenco di problemi risolti nelle diverse release, problemi noti con il prodotto e ulteriori suggerimenti per l'utilizzo di {{site.data.keyword.vmwaresolutions_full}}, vedi [{{site.data.keyword.vmwaresolutions_short}} dW Answers](https://developer.ibm.com/answers/topics/cloudvmw/){:new_window}.

## VMware vSphere on IBM Cloud

Questa release introduce l'offerta VMware vSphere on IBM Cloud, che ti consente di creare il tuo proprio ambiente virtuale VMware ospitato su IBM personalizzando e ordinando risorse di calcolo, archiviazione e rete compatibili con VMware in base ai componenti VMware selezionati. Anche se vSphere on IBM Cloud non automatizza l'istallazione, la configurazione e il richiamo dei componenti VMware facoltativi, hai la massima flessibilità per progettare e architettare un ambiente che risponda al meglio alle tue esigenze aziendali. Puoi iniziare creando un nuovo cluster vSphere di server ESXi o ridimensionando un cluster vSphere esistente in un data center IBM Cloud.

Per ulteriori informazioni, vedi:
* [Ordine di nuovi cluster vSphere](../vsphere/vs_orderinginstances.html)
* [Ridimensionamento di cluster vSphere esistenti](../vsphere/vs_scalingexistingclusters.html)

## NetApp ONTAP Select on IBM Cloud

Questa release introduce l'offerta NetApp ONTAP Select on IBM Cloud, un dispositivo virtuale per l'archiviazione definita dal software, che implementa NetApp ONTAP Select come servizio sui {{site.data.keyword.baremetal_short}} dedicati di IBM Cloud. NetApp ONTAP Select on IBM Cloud è offerto sia in configurazioni ad alte prestazioni (tutti gli SSD) che ad alta capacità (tutti i SATA).
Ospita l'archiviazione su un'infrastruttura dedicata e fornisce funzionalità NetApp, come la deduplicazione, la compressione e la crittografia dei dati inattivi. Con questa offerta, puoi fornire risorse di archiviazione con agilità e flessibilità e proteggere i dati utilizzando funzioni avanzate di gestione dei dati, come le copie NetApp Snapshot®, le copie FlexClone® e le repliche SnapMirror® veloci ed efficienti.

Per ulteriori informazioni, vedi:
* [Panoramica di NetApp ONTAP Select](../netapp/np_netappoverview.html)
* [Ordine di istanze NetApp ONTAP Select](../netapp/np_orderinginstances.html)

## Servizio F5 on IBM Cloud

Il servizio F5 BIG-IP Virtual Edition (VE) on IBM Cloud è ora disponibile sia per le istanze VMware Cloud Foundation che per le istanze VMware vCenter Server. Questo servizio fornisce servizi intelligenti di bilanciamento del carico L4-L7 e di gestione del traffico su scala locale e globale, una solida protezione firewall per reti e applicazioni web e accesso sicuro e federato alle applicazioni.
Puoi ordinare le istanze con il servizio F5 BIG-IP Virtual Edition (VE) on IBM Cloud incluso al momento dell'ordine della tua istanza o aggiungere questo servizio alle tue istanze esistenti in un secondo momento utilizzando la scheda **Servizi** nella pagina dei dettagli delle proprietà dell'istanza della console {{site.data.keyword.vmwaresolutions_short}}. A seconda dei tuoi requisiti, puoi selezionare una delle tre opzioni di licenza per BIG-IP VE.

Per ulteriori informazioni, vedi:
* [Considerazioni su F5 on IBM Cloud](../services/f5_considerations.html)
* [Gestione di F5 on IBM Cloud](../services/managing_f5.html)

## Servizi gestiti da IBM Integrated Managed Infrastructure

I servizi gestiti da IBM Integrated Managed Infrastructure (IMI) sono ora disponibili per le istanze VMware Cloud Foundation. IMI può semplificare la gestione dell'infrastruttura virtuale VMware con servizi modulari e può fungere da unico provider attendibile per ridurre la complessità del monitoraggio e della gestione delle infrastrutture IT virtuali. Scarica alcune operazioni quotidiane a IMI, come il monitoraggio, in modo che tu possa concentrarti su iniziative di valore più elevato.

Puoi richiedere una consulenza e un preventivo in qualsiasi momento dalla pagina **Introduzione**.
Per ulteriori informazioni, vedi [Richiesta di servizi gestiti da IMI](../services/managing_imi.html#requesting-managed-services-from-imi).

## Limitazioni sui nomi delle istanze vCenter Server e NetApp ONTAP Select

I nomi di istanza immessi in {{site.data.keyword.vmwaresolutions_short}} quando ordini le tue istanze non possono includere caratteri speciali (come il carattere trattino). Sono consentiti solo caratteri alfanumerici. Questa limitazione non si applica alle istanze Cloud Foundation.

Per ulteriori informazioni, vedi:
* [Ordine di istanze vCenter Server](../vcenter/vc_orderinginstance.html)
* [Ordine di istanze NetApp ONTAP Select](../netapp/np_orderinginstances.html)

## Aggiornamenti per le istanze VMware Cloud Foundation

### Personalizza la CPU e la memoria della tua istanza

Insieme alle opzioni Small e Standard precostruite e testate, è disponibile un'opzione di server personalizzabile dall'utente. Per abbinare al meglio il rapporto CPU-RAM dei carichi di lavoro con l'hardware compatibile con VMware, puoi ora selezionare in modo indipendente il numero totale di core su un server a doppia CPU e la quantità di RAM. L'archiviazione locale non è personalizzabile.

Per ulteriori informazioni, vedi [Ordine di istanze Cloud Foundation](../sddc/sd_orderinginstance.html).

## Aggiornamenti per le istanze VMware vCenter Server

### Supporto cluster in più data center

Per migliorare il ridimensionamento del tuo ambiente VMware ospitato, puoi ora creare un nuovo cluster in un pod dell'infrastruttura {{site.data.keyword.cloud_notm}} (SoftLayer) o in un data center IBM Cloud diverso rispetto al cluster iniziale distribuito nell'istanza.

Per ulteriori informazioni, vedi [Aggiunta e visualizzazione di cluster per le istanze vCenter Server](../vcenter/vc_addingviewingclusters.html).

### Modifica dei componenti

Questa release elimina l'impatto sulle operazioni all'interno della console {{site.data.keyword.vmwaresolutions_short}} quando l'amministratore del Single Sign-On modifica alcune risorse di vCenter Server da uno strumento VMware nativo. Ad esempio, puoi ora modificare il data center virtuale VMware, il cluster, gli switch, i gruppi di porte e i nomi di archivio dati dal client web VMware vSphere per personalizzare le distribuzioni in convenzioni di denominazione aziendale o personale e senza alcun impatto successivo sulle operazioni dall'interno della console {{site.data.keyword.vmwaresolutions_short}}.

Per ulteriori informazioni, vedi [Impatti della modifica di componenti per le istanze vCenter Server](../vcenter/vcenter_chg_impact.html).

### Ulteriori dimensioni della RAM

Quando ordini le istanze vCenter Server o aggiungi cluster per le istanze vCenter Server, puoi ora scegliere tra più dimensioni della RAM per abbinare meglio il rapporto CPU-RAM del carico di lavoro con l'hardware. Quando ordini un server dalla console {{site.data.keyword.vmwaresolutions_short}}, nell'opzione di configurazione **Personalizzato dall'utente**, sono disponibili le seguenti opzioni: 64 GB, 128 GB, 256 GB, 384 GB, 512 GB, 768 GB, 1,5 TB.

Per ulteriori informazioni, vedi [Ordine di istanze vCenter Server](../vcenter/vc_orderinginstance.html).

### Aggiornamento della versione NFS (Network File System)

La versione 4.1 di NFS (Network File System) non è più disponibile come impostazione di archiviazione dall'interfaccia utente. Tutte le istanze vCenter Server vengono distribuite con NFS V3. Sebbene NFS V3 sia una versione precedente del protocollo, abilita funzioni avanzate sugli ambienti VMware con supporto per VMware SDRS (Storage Distributed Resource Scheduler) e SIOC (Storage I/O Control).

Per ulteriori informazioni, vedi [Ordine di istanze vCenter Server](../vcenter/vc_orderinginstance.html).

### Nome del dominio Domain Name Server per un singolo sito

Durante un ordine, puoi ora fornire il nome del dominio DNS (Domain Name Server) per un'istanza vCenter Server. Viene distribuita una VSI (Virtual Server Instance) di Microsoft Windows Server consultabile, che funziona come DNS per l'istanza in cui sono registrati gli host e le macchine virtuali. Microsoft Active Directory (AD) è anche configurato sulla VSI di Microsoft Windows e il nome del dominio DNS è il nome root dell'insieme di strutture del dominio AD. Questa VSI di Microsoft Windows è disponibile solo nella V1.9 e successive.

Per ulteriori informazioni, vedi:
* [Panoramica di vCenter Server](../vcenter/vc_vcenterserveroverview.html)
* [Visualizzazione delle istanze vCenter Server](../vcenter/vc_viewinginstances.html)

## Requisiti per l'istallazione automatica degli aggiornamenti di Windows Server

Microsoft Active Directory (AD) / Domain Name Server (DNS) è configurato automaticamente solo per scaricare gli aggiornamenti. Non installa e riavvia automaticamente questi aggiornamenti. Devi installare gli aggiornamenti manualmente ed eseguire il riavvio in un momento pianificato che eviti interruzioni della configurazione del server Active Directory in corso e di altri lavori di backup. Per applicare gli aggiornamenti di Windows, installa gli aggiornamenti manualmente.

## Documentazione nuova e aggiornata

* Impara a salvaguardare le tue istanze VCF multisito private mentre estendi le tue applicazioni VMware per utilizzare i servizi IBM Cloud pubblici. Per ulteriori informazioni, vedi [Securely connect your private VMware workloads in the IBM Cloud](https://www.ibm.com/developerworks/library/se-securely-connect-private-vmware-workloads-ibm-cloud/index.html){:new_window}.
* Viene fornita ulteriore documentazione per la configurazione di firewall che consentono tutte le comunicazioni del protocollo dalle macchine virtuali IBM CloudDriver e SDDC Manager. Per ulteriori informazioni, vedi [Componenti e considerazioni per Fortinet on IBM Cloud](../services/fsa_considerations.html).
