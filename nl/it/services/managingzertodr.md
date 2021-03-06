---

copyright:

  years:  2016, 2018

lastupdated: "2018-06-07"

---

# Gestione di Zerto on IBM Cloud

Dopo aver distribuito il servizio Zerto on {{site.data.keyword.cloud}} nella tua istanza, puoi configurare o aggiornare Zerto Virtual Replication e distribuire più dispositivi Virtual Replication Appliance ai server ESXi appena aggiunti.

## Utilizzo del tuo certificato per Zerto

Come procedura consigliata, dovresti utilizzare il tuo certificato SSL per Zerto Virtual Manager (ZVM). Dopo aver distribuito Zerto on {{site.data.keyword.cloud_notm}}, sostituisci il certificato SSL per ZVM con il tuo certificato seguendo le istruzioni indicate in [How to use a CER SSL Certificate to Replace the Self-Signed Certificate for the ZVM, ZSSP, or ZCM](https://www.zerto.com/myzerto/knowledge-base/how-to-use-a-cer-ssl-certificate-to-replace-the-self-signed-certificate-for-the-zvm-zssp-or-zcm/){:new_window}.

## Gestione della configurazione delle repliche Zerto

Per gestire la configurazione delle repliche Zerto (come ad esempio ripetere l'associazione delle istanze Zerto o configurare i gruppi di protezione virtuali per replicare le macchine virtuali), accedi alla console Zerto Virtual Replication utilizzando le credenziali di vCenter con autorizzazioni di amministratore.

Se stai eseguendo la replica tra diverse istanze di {{site.data.keyword.cloud_notm}} Zerto, puoi configurare la replica direttamente tra le istanze Zerto. Se stai eseguendo la replica tra l'istanza {{site.data.keyword.cloud_notm}} Zerto e il tuo proprio data center, devi installare tu stesso Zerto nel tuo data center. Questa istanza di Zerto che installi nel tuo data center può autorizzarsi automaticamente quando la abbini all'istanza {{site.data.keyword.cloud_notm}} Zerto.

Poiché la replica di Zerto non supporta l'attraversamento NAT (Network Address Translation), stabilire la connettività tra l'istanza di {{site.data.keyword.cloud_notm}} Zerto e il tuo data center potrebbe richiedere la personalizzazione di rotte sui dispositivi Zerto Virtual Manager (ZVM) o Zerto Virtual Replication Appliance (VRA) su entrambi i lati e potrebbe richiedere anche un tunneling sicuro tra i siti. Quando configuri o riconfiguri le rotte sui dispositivi ZVM, devi assicurarti che tutti questi dispositivi possano connettersi correttamente a `zerto.com` per la segnalazione di utilizzo. Puoi verificare questa connessione aprendo una sessione del browser in `https://www.zerto.com` dal dispositivo ZVM.

**Nota**: il gateway dei servizi edge (ESG) VMware NSX di gestione delle istanze Cloud Foundation e vCenter Server su {{site.data.keyword.cloud_notm}} è preconfigurato per consentire le comunicazioni HTTPS in uscita (porta TCP 443) originate da ZVM.

## Aggiornamento di Zerto Virtual Replication

Per aggiornare Zerto Virtual Replication, accedi alla console di Zerto Virtual Replication.

## Distribuzione di VRA ai server ESXi appena aggiunti

Quando aggiungi o rimuovi i server ESXi per il cluster primario della tua istanza, i VRA vengono distribuiti o rimossi automaticamente. I VRA non vengono distribuiti automaticamente ai server ESXi nei cluster secondari della tua istanza, ma puoi distribuirli autonomamente dalla console di Zerto Virtual Replication.

## Link correlati

* [Panoramica di Zerto on IBM Cloud](addingzertodr.html)
* [Richiesta di servizi gestiti per Zerto on {{site.data.keyword.cloud_notm}}](managing_zerto_services.html)
* [Sito web zerto.com](https://www.zerto.com){:new_window}
* [Documentazione tecnica di Zerto](https://www.zerto.com/myzerto/technical-documentation/){:new_window}
* [Ripristino di emergenza Zerto](https://www.ibm.com/devops/method/content/architecture/virtCloudFoundationPlatform/zerto){:new_window}
* [Spiegazione degli avvisi di Zerto Virtual Replication](https://www.zerto.com/myzerto/knowledge-base/explanation-of-zvr-alerts/)
