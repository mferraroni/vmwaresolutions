---

copyright:

  years:  2016, 2018

lastupdated: "2018-04-16"

---

# Notes sur l'édition pour la version 2.1

Cette édition inclut de nouvelles fonctionnalités, des mises à jour de composant, des améliorations d'utilisation et des corrections d'erreur. Pour la liste des erreurs rectifiées dans les différentes éditions, les problèmes connus concernant le produit et des conseils supplémentaires pour l'utilisation d'{{site.data.keyword.vmwaresolutions_full}}, voir [{{site.data.keyword.vmwaresolutions_short}} dW Answers](https://developer.ibm.com/answers/topics/cloudvmw/){:new_window}.

## Résolution de Spectre et Meltdown

{{site.data.keyword.vmwaresolutions_short}} a publié des correctifs depuis VMware afin de remédier à des vulnérabilités identifiées sous l'appellation Spectre et Meltdown (CVE-2017-5753, CVE-2017-5715 et CVE-2017-5754).

* CVEID : [CVE-2017-5753](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5753)
* CVEID : [CVE-2017-5715](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5715)
* CVEID : [CVE-2017-5754](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5754)

Pour plus d'informations, voir [Résolution des vulnérabilités Spectre et Meltdown](../vmonic/trbl_fix_spectre.html).

## VMware HCX on IBM Cloud

Le service HCX on {{site.data.keyword.cloud_notm}} est désormais disponible pour les instances VMware Cloud Foundation et VMware vCenter Server qui exécutent vSphere 6.5 et qui sont déployées dans ou mises à niveau vers la version 2.1 ou des éditions ultérieures. Ce service peut en toute transparence étendre les réseaux de vos centres de données locaux dans {{site.data.keyword.cloud_notm}}, ce qui permet la migration bidirectionnelle des machines virtuelles entre vos centres de données locaux et {{site.data.keyword.cloud_notm}} sans aucune modification. En établissant un pont à 2 couches, HCX tire profit de l'optimisation, de la déduplication, de la compression et du chiffrement de WAN pour migrer les données plus rapidement et en toute sécurité via un tunnel VPN ou de lien direct. La migration en vrac des machines virtuelles est compatible en amont avec VMware vSphere version 5.1 ou ultérieure. Si vous utilisez une version 6.0 ou ultérieure de vSphere en local, vous pouvez activer des machines virtuelles via vMotion depuis des sites sur un centre de données IBM Cloud. Il n'est pas nécessaire d'installer VMware NSX dans votre centre de données lorsque vous utilisez HCX.

Vous pouvez commander des instances Cloud Foundation ou vCenter Server avec le service HCX on {{site.data.keyword.cloud_notm}} déjà inclus ou vous pouvez ajouter ultérieurement ce service à vos instances existantes à partir de l'onglet **Services** de la page des détails d'instance.

Vous pouvez également commander une instance HCX locale pour l'octroi de licence et l'activation de votre installation HCX locale.

Pour plus d'informations, voir :
* [Remarques relatives au service HCX on IBM Cloud](../services/hcx_considerations.html)
* [Gestion de HCX on IBM Cloud](../services/managinghcx.html)
* [Remarques relatives aux instances HCX locales](../services/standalone_considerations.html)
* [Commande d'instances HCX locales](../services/standalone_orderingserviceinstances.html)

## Modèle BYOL (Bring Your Own License) plus souple pour VMware Cloud Foundation et vCenter Server

L'utilisation de votre propre licence (BYOL) ou l'achat d'une licence d'abonnement fournie par IBM lors de la création d'un nouveau cluster sont désormais possibles pour les versions 2.1 et ultérieures des instances VMware Cloud Foundation et VMware vCenter Server ce qui vous permet de tirer parti de votre clé de composant existante ou de louer la licence auprès d'IBM. Avant la version 2.1, vous ne pouviez pas acheter de licence fournie par IBM pour un composant VMware spécifique si vous utilisiez BYOL. Actuellement, seuls VMware vSphere et VMware vSAN sont disponibles pour l'octroi de licence par cluster.

De plus, lors de l'ajout de noeuds à un cluster sous licence avec votre clé, la console vous invite à fournir une nouvelle clé de licence si le nombre de noeuds dépasse la capacité de la clé.

Pour plus d'informations, voir :

* [Ajout et affichage des clusters des instances Cloud Foundation](../sddc/sd_addingviewingclusters.html)
* [Ajout et affichage des clusters des instances vCenter Server](../vcenter/vc_addingviewingclusters.html)
* [Foire aux questions sur le mode BYOL](../vmonic/faq_byol.html)

## Mises à jour du composants de service Zerto on IBM Cloud

Zerto Virtual Replication 5.5u2 est mis à disposition pour le service Zerto on {{site.data.keyword.cloud_notm}} déployé dans des instances Cloud Foundation et vCenter Server version 2.1 et ultérieures. Des dispositifs de réplication virtuels Zerto (VRA, Virtual Replication Appliance) sont désormais déployés dans le magasin de données de gestion (vSAN ou Endurance) au lieu du magasin de données local pour de meilleures performances. Si vous disposez de dispositifs VRA existants, vous devez envisager de migrer leur stockage vers le magasin de données de gestion pour améliorer les performances.

Pour plus d'informations, voir [Présentation de Zerto on IBM Cloud](../services/addingzertodr.html).

## Mises à jour des instances VMware vCenter Server

### Paramètres de configuration de MTU réseau

A partir de l'édition V2.1, de nouvelles instances vCenter Server sont commandées avec la valeur MTU 1500 définie par défaut pour le paramètre Distributed Virtual Switch (DVS) public. Pour plus d'informations, voir la section _Paramètres de configuration de MTU réseau_ dans la rubrique [Nomenclature vCenter Server](../vcenter/vc_bom.html).

### Réplication automatique des mises à jour et correctifs VMware ESXi sur les hôtes

Sur les instances VMware vCenter Server version 2.0 et antérieures, les correctifs n'étaient pas automatiquement appliqués aux hôtes ESXi ajoutés à un cluster.

Sur les instances version 2.1 et ultérieures, l'automatisation applique des correctifs aux nouveaux hôtes ESXi de manière à faire correspondre le niveau de correctif à celui en vigueur lors de la mise à disposition de l'instance initiale. C'est à vous d''appliquer manuellement tous les correctifs et mises à jour ultérieurs.
Lorsque des correctifs et des mises à jour VMware sont disponibles dans des éditions ultérieures, l'automatisation analyse les hôtes ESXi de vos instances existantes et vous envoie un courrier électronique pour vous rappeler d'appliquer manuellement les derniers correctifs et mises à jour.

Pour plus d'informations, voir [Application de mises à jour à des instances vCenter Server](../vcenter/vc_applyingupdates.html).

### Mises à jour des estimations de prix des licences VMware NSX

Vous pouvez désormais afficher une estimation de prix avant de soumettre une commande de mise à niveau vers l'édition VMware NSX Advanced ou Enterprise. La tarification est basée sur le nombre d'hôtes ESXi de l'instance vCenter Server. Cet achat modifie uniquement la clé de licence NSX et effectue une mise à niveau de votre édition VMware NSX Base vers l'édition Advanced ou Enterprise. L'achat n'effectue pas de mise à niveau de la version du logiciel NSX.

Pour plus d'informations, voir [Présentation de vCenter Server](../vcenter/vc_vcenterserveroverview.html).

### Augmentation du nombre maximum de 32 serveurs par cluster

Vous pouvez déployer ou augmenter le nombre de serveurs du cluster par défaut d'une instance jusqu'à 51 serveurs. Pour tous les clusters suivants d'une instance, vous pouvez déployer ou augmenter jusqu'à 59 serveurs. Pour plus d'informations, voir [Ajout et affichage des clusters des instances vCenter Server](../vcenter/vc_addingviewingclusters.html).

**Remarque :** cette possibilité n'est offerte qu'aux instances déployées en version 2.1 et ultérieures. Les instances mises à niveau vers la version 2.1 depuis des éditions antérieures ne disposent pas de cette possibilité.

### Options de configuration des serveurs bare metal IBM Cloud Server personnalisée par l'utilisateur

La configuration des serveurs bare metal personnalisée par l'utilisateur offre désormais une configuration Dual Intel Xeon Gold 6140 de 36 coeurs au total, à 2,3 GHz.

Pour plus d'informations, voir :
* [Présentation de vCenter Server](../vcenter/vc_vcenterserveroverview.html)
* [Commande d'instances vCenter Server](../vcenter/vc_orderinginstance.html)

### Configurations de partage de fichiers NFS individuel

Vous avez désormais la possibilité de configurer des partages de fichiers NFS individuellement. Sélectionnez une taille de fichier et un niveau de performance pour chaque partage de fichiers individuel ou sélectionnez les mêmes taille de fichier et niveau de performance pour tous les partages de fichiers que vous commandez.

Pour plus d'informations, voir :
* [Présentation de vCenter Server](../vcenter/vc_vcenterserveroverview.html)
* [Commande d'instances vCenter Server](../vcenter/vc_orderinginstance.html)
* [Ajout et affichage des clusters des instances vCenter Server](../vcenter/vc_addingviewingclusters.html)

## Améliorations et mises à jour apportées à l'interface utilisateur

Des améliorations ont été apportées à l'interface utilisateur, à savoir :

* L'option **Commander une instance** a été supprimée du panneau de navigation de gauche. Cliquez sur **Initiation** pour finaliser la procédure de commande d'une instance.
* La zone **Préfixe de sous-domaine** sur la page **De base** lors de la procédure de commande d'une instance a été renommée **Libellé de sous-domaine**.
* En plus de pouvoir afficher le coût estimé sur la page **Récapitulatif** lors de la commande d'une instance vCenter Server ou Cloud Foundation principale ou secondaire, vous pouvez désormais calculer le coût estimé sur chaque panneau à mesure que vous fournissez les détails de votre commande d'instance.
* Le trajet de navigation a été ajouté à la page **Instances déployées** comme méthode de navigation alternative, ce qui réduit le nombre d'étapes nécessaires pour accéder aux pages parent de ces pages.
* Diverses améliorations ont été apportées au niveau des messages d'erreur et des infobulles pour vous aider à sélectionner le paramétrage approprié sur l'interface utilisateur.

## Documentation nouvelle et mise à jour

Une nouvelle fiche de recette developerWorks est disponible avec des instructions détaillées sur la manière de lier un stockage dédié à des déploiements {{site.data.keyword.vmwaresolutions_full}} existants à l'aide de NetApp ONTAP Select on IBM Cloud. Pour plus d'informations, voir [Procédure de liaison d'un stockage dédié à VMware Solutions on IBM Cloud](https://developer.ibm.com/recipes/tutorials/steps-to-attach-dedicated-storage-to-existing-ic4v-deployments-on-ibm-cloud/).
