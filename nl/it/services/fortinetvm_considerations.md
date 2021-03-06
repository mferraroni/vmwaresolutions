---

copyright:

  years:  2016, 2018

lastupdated: "2018-06-14"

---

# Panoramica di FortiGate Virtual Appliance on IBM Cloud

Il servizio FortiGate Virtual Appliance on {{site.data.keyword.cloud}} distribuisce una coppia di dispositivi FortiGate Virtual Appliance al tuo ambiente, che può aiutarti a ridurre i rischi implementando controlli di sicurezza critici all'interno della tua infrastruttura virtuale.

Puoi installare più istanze di questo servizio a seconda delle necessità. Puoi gestire questo servizio utilizzando il client web FortiOS o l'interfaccia della riga di comando tramite SSH.

**Disponibilità**: questo servizio è disponibile solo per le istanze distribuite nelle release della V2.0 o successive.

## Componenti di FortiGate Virtual Appliance on IBM Cloud

Quando ordini il servizio FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}}, viene distribuita una coppia di FortiGate Virtual Appliance con:
* Un'interfaccia di rete configurata per la rete di gestione.
* Nove ulteriori interfacce di rete che puoi configurare per proteggere il traffico dati, se necessario.

I dispositivi FortiGate Virtual Appliance non sono preconfigurati come coppia altamente disponibile (HA). Dopo la distribuzione, puoi configurare le impostazioni HA, che includono Virtual Router Redundancy Protocol (VRRP) e FortiGate Cluster Protocol (FGCP), in base alle tue esigenze.

## Considerazioni sull'istallazione di FortiGate Virtual Appliance on IBM Cloud

Esamina le seguenti considerazioni prima di installare il servizio FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}}:
* Le macchine virtuali (VM) FortiGate verranno distribuite solo nel cluster predefinito.
* In base alle dimensioni di distribuzione e al modello di licenza selezionati, le due VM FortiGate vengono distribuite con una delle seguenti configurazioni:
    * Small (2 vCPU / 4 GB di RAM)
    * Medium (4 vCPU / 6 GB di RAM)
    * Large (8 vCPU / 12 GB di RAM)

  Inoltre, viene prenotato anche il 100% di CPU e RAM per le due VM FortiGate perché queste VM si trovano nel piano dati delle comunicazioni di rete
  ed è fondamentale che per loro siano ancora disponibili risorse. 

  Per calcolare la prenotazione di CPU e RAM per una singola VM FortiGate, utilizza la seguente formula:
   * `Prenotazione CPU = velocità CPU del server ESXi * numero di vCPU`
   * `Prenotazione RAM = dimensione RAM`
* Quando distribuisci una coppia HA di dispositivi FortiGate Virtual Appliance nella tua istanza, vengono definite regole SNAT e firewall sul gateway dei servizi edge (ESG) NSX di gestione insieme a rotte statiche sui dispositivi FortiGate Virtual Appliance per consentire comunicazioni HTTPS in uscita dalla tua istanza alla rete pubblica per l'attivazione della licenza e per l'acquisizione di contenuti e politiche di sicurezza più recenti.
* Non puoi modificare il livello di licenza dopo l'installazione del servizio. Per modificare il livello di licenza, devi rimuovere il servizio esistente e quindi reinstallare il servizio selezionando un'opzione di licenza diversa.
* Per evitare errori con FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}}, devi soddisfare i seguenti requisiti:
   * Sono disponibili almeno due server ESXi attivi per le due VM FortiGate da distribuire con la regola di anti-affinità di mantenere le VM su server separati.
   * I due server ESXi attivi hanno sufficienti risorse disponibili in modo che una VM FortiGate possa essere ospitata su ciascun server ESXi con prenotazione del 100% di CPU e RAM.
   * VMware vSphere HA dispone di risorse sufficienti per ospitare due VM FortiGate con il 100% di CPU e RAM.

  A causa di questi requisiti, devi pianificare attentamente lo spazio necessario per FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}}. Se necessario, prima di ordinare FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}}, aggiungi 1-2 server ESXi alla tua istanza e/o riduci la prenotazione di CPU di vSphere HA per il failover. 

## Esempio di ordine di FortiGate Virtual Appliance on IBM Cloud

Ordini un'istanza **Small** di VMware vCenter Server con 2 server ESXi con la seguente configurazione: 16 core a 2,10 GHz ciascuno con 128 GB di RAM. Per FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}}, selezioni l'opzione **Large** (8 vCPU / 12 GB di RAM) per la dimensione di distribuzione e qualsiasi modello di licenza di sottoscrizione.

In questo caso, una singola VM FortiGate richiede, su ciascun server:
* 2,1 GHz * 8 vCPU = 16,8 GHz di CPU e
* 12 GB di RAM

In totale, si tratta di 33,6 GHz di CPU e 24 GB di RAM per due VM FortiGate.

Ogni server ESXi ha una capacità di 16 core * 2,1 GHz = 33,6 GHz, quindi soddisfiamo i primi due requisiti se entrambi i server sono attivi e ci sono almeno 16,8 GHz di CPU e 12 GB di RAM disponibili su ciascun server.

Tuttavia, per impostazione predefinita, vSphere HA riserva il 50% di CPU e RAM per il failover sulle istanze vCenter Server che sono state inizialmente distribuite con 2 server ESXi, quindi abbiamo solo:

`50% di 2 * 16 core * 2,1 GHz = 33,6 GHz disponibili`

Poiché saranno presenti altri carichi di lavoro sui server ESXi, ad esempio, IBM CloudDriver, VMware NSX Controller o VMware NSX Edge, utilizzando queste risorse, il terzo requisito non viene soddisfatto. Questo perché abbiamo bisogno di 33.6 GHz di CPU e 24 GB di RAM per due VM FortiGate.

In questo caso, l'installazione di FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} potrebbe non riuscire, a meno che almeno un server ESXi venga aggiunto all'ambiente e le prenotazioni di failover di vSphere HA vengano aggiornate in modo appropriato per garantire che ci siano risorse sufficienti per due VM FortiGate. 

Se sono necessarie risorse aggiuntive per eseguire il servizio FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}}, puoi aggiungere altri server ESXi prima di installare il servizio.

## Considerazioni sulla rimozione di FortiGate Virtual Appliance on IBM Cloud

Prima di rimuovere il servizio FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}}, assicurati che la configurazione dei dispositivi FortiGate Virtual Appliance esistenti sia stata rimossa correttamente. In particolare, il traffico di rete deve essere instradato attorno ai FortiGate Virtual Appliance anziché tramite i FortiGate Virtual Appliance. In caso contrario, il traffico di dati esistente all'interno del tuo ambiente potrebbe essere influenzato.

## Link correlati

* [Ordine di FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}}](fortinetvm_ordering.html)
* [Gestione di FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}}](managingfortinetvm.html)
* [Come contattare il supporto IBM](../vmonic/trbl_support.html)
* [Domande frequenti](../vmonic/faq.html)
* [Sito web Fortinet](https://www.fortinet.com/){:new_window}
* [Libreria di documenti Fortinet](http://docs.fortinet.com/fortigate/admin-guides){:new_window}
