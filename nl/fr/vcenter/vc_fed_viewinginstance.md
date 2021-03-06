---

copyright:

  years:  2016, 2018

lastupdated: "2018-06-04"

---

# Affichage des instances VMware Federal

Cette procédure permet d'afficher les instances VMware Federal que vous avez commandées ainsi que des informations détaillées les concernant.

## Affichage du récapitulatif des instances VMware Federal

1. A partir de la console {{site.data.keyword.vmwaresolutions_short}}, cliquez sur **Instances déployées** dans le panneau de navigation de gauche.
2. Dans le tableau **Instances vCenter Server**, affichez la liste de vos instances.

Tableau 1. Eléments d'une instance VMware Federal

| Elément        | Description       |  
|:------------- |:------------- |
| Nom | Le nom de l'instance. |
| Version | La version d'édition dans laquelle l'instance a été déployée ou mise à niveau. |  
| Emplacement | {{site.data.keyword.CloudDataCent}} où l'instance est hébergée. |  
| Heure de création | La date et l'heure de création de l'instance. |  

L'instance peut prendre différents statuts.

Tableau 2. Description des statuts des instances d'un centre de données VMware Federal

| Statut        | Description       |
|:------------- |:------------- |
| Création en cours | L'instance est en cours de création. |
| Génération en cours | L'instance est en cours de configuration. |
| Prêt à l'emploi | L'instance est prête pour utilisation. |
| Modification en cours | L'instance est en cours de modification. |
| Sécurisé | L'instance déployée est déconnectée d'une connexion de gestion ouverte et d'une automatisation.
| Echec | Le processus de création, de configuration ou de modification a échoué. |
| Suppression en cours | L'instance est en cours de suppression. |
| Erreur de suppression | Une erreur s'est produite au cours du processus de suppression de l'instance. |
| Supprimé | L'instance a été supprimée. |

## Affichage des détails des propriétés d'une instance VMware Federal

Pour afficher les détails des propriétés d'une instance :

1. Dans le tableau **Instances vCenter Server**, cliquez sur le nom de l'instance.
2. Sous **Propriétés**, affichez les détails de l'instance.

Tableau 3. Propriétés d'instance VMware Federal

| Propriété        | Description       |
|:------------- |:------------- |
| Nom | Nom de l'instance. |
| ID | ID de l'instance. |
| Emplacement | {{site.data.keyword.CloudDataCent_notm}} où l'instance est hébergée. |
| Version en cours |  Version en cours d'{{site.data.keyword.vmwaresolutions_short}}. |
| Version de vCenter | Version de VMware vCenter Server.<br><br>**Remarque :** la version vCenter Server affichée sur la console {{site.data.keyword.vmwaresolutions_short}} et celle sur le client Web VMware vSphere sont légèrement différentes. Les deux sont correctes. |
| NSX for vSphere | Version du produit VMware NSX for vSphere. |
| Edition de licence NSX | Version et édition de la licence VMware NSX. |
| Domaine racine DNS | Le nom du domaine racine qui est le nom de domaine du serveur de noms de domaine (DNS, Domain Name System) et le nom de l’approbation de la racine Microsoft Active Directory (AD). |
| Domaine de connexion unique DNC | Il s'agit du domaine de connexion unique (Single Sign-On) vSphere. Le nom de domaine SSO est défini pour toutes les instances vCenter Server déployées avec la valeur <samp class="ph codeph">vsphere.local</samp>. |
| Sous-domaine DNS | Il s'agit du sous-domaine DNS du nom de domaine racine où résident les noms d'hôte des instances vCenter Server locales. Le nom de sous-domaine est au format <samp class="ph codeph"><var class="keyword varname">vcenter_server_instance_name</var>.<var class="keyword varname">root.domain_name</var></samp>. |
| Statut | Statut de l'instance. |

## Affichage des informations d'accès relatives aux instances VMware Federal

Sous **Informations d'accès**, affichez les informations d'accès relatives aux composants d'instance. Les mots de passe affichés sont les mots de passe initiaux générés par le système. Si vous les modifiez en dehors de la console {{site.data.keyword.vmwaresolutions_short}}, ils ne sont pas mis à jour sur la page récapitulative de l'instance.

Tableau 4. Informations d'accès relatives aux composants d'instance

| Composant        | Description       |
|:------------- |:------------- |
| AD/DNS IPs | Adresses IP des deux serveurs AD. |
| AD/DNS FQDNs | Les noms de domaine complets des serveurs AD/DNS.<br><br>**Remarque :** le même mot de passe administrateur peut être utilisé pour établir une connexion à tous les serveurs AD/DNS via une connexion bureau à distance. |
| AD/DNS ADMIN (Remote Desktop)  | Pour les instances principales, affiche le nom d'utilisateur et le mot de passe d'accès au serveur AD avec une connexion bureau à distance.
| NSX Manager IP  | L'adresse IP du gestionnaire NSX.  |
| NSX Manager FQDN  | Le nom de domaine complet du gestionnaire NSX.  |
| NSX Manager HTTP  | Le nom d'utilisateur et mot de passe utilisés pour accéder à la console Web du gestionnaire NSX. |
| PSC IP  | L'adresse IP du contrôleur PSC ( Platform Services Controller).  |
| PSC FQDN  | Le nom de domaine complet du PSC.  |    
| PSC ADMIN  | Le nom d'utilisateur et le mot de passe de connexion unique VMware vCenter que vous pouvez utiliser pour accéder à la console Web du PSC.  |
| PSC SSH  | Le nom d'utilisateur et le mot de passe que vous pouvez utiliser pour accéder à la machine virtuelle PSC via une connexion SSH.  |
| vCenter IP  | L'adresse IP du serveur vCenter Server.  |
| vCenter FQDN  | Le nom de domaine complet du serveur vCenter Server.  |
| vCenter ADMIN  | Le nom d'utilisateur et le mot de passe de connexion unique VMware vCenter que vous pouvez utiliser pour vous connecter au serveur vCenter Server à l'aide du client Web vSphere.  |
| vCenter SSH  | Le nom d'utilisateur et le mot de passe que vous pouvez utiliser pour accéder à la machine virtuelle vCenter Server via une connexion SSH.  |

## Affichage de l'historique de déploiement des instances VMware Federal

Sous **Historique de déploiement**, affichez l'historique de déploiement de l'instance.

Tableau 5. Historique de déploiement d'une instance VMware Federal

| Elément        | Description       |  
|:------------- |:------------- |
| Date | La date et l'heure de changement du statut de l'instance. |
| Récapitulatif | Les détails du changement. |

## Que faire en cas d'erreurs

Si des erreurs se produisent lors du déploiement ou de la suppression d'une instance, l'équipe de support {{site.data.keyword.cloud_notm}} est automatiquement prévenue. Pour connaître le statut de votre ticket, vous pouvez [contacter le support IBM](../vmonic/trbl_support.html).

## Etape suivante

Gérez vos instances depuis la console {{site.data.keyword.vmwaresolutions_short}} ou le client Web VMware vSphere.

**Important** : avant de cliquer sur **Console vCenter** sur la page récapitulative de l'instance pour accéder au client Web vSphere et commencer à gérer vos serveurs ESXi, vous devez vous connecter au portail VPN de l'{{site.data.keyword.CloudDataCent_notm}}. Survolez le bouton **Console vCenter** et suivez les instructions de manière à respecter toutes les exigences et à effectuer les étapes requises avant d'accéder au client Web vSphere.

Passez en revue les rubriques suivantes pour obtenir des informations qui vous aideront à exécuter les instructions de connexion :
*  Pour les exigences et procédures à effectuer avant d'accéder au client Web vSphere, voir [Dépassement du délai d'attente lors de la connexion au client Web vSphere](../vmonic/trbl_timeout_vc_console.html).
*  Pour la liste des points d'accès de connexion au réseau privé de l'infrastructure {{site.data.keyword.cloud_notm}} à l'aide du réseau privé virtuel (VPN), voir [Accès VPN](http://www.softlayer.com/vpn-access){:new_window}.
*  Si vous rencontrez des problèmes lors du déploiement d'un fichier OVF (Open Virtualization Format) à l'aide du client Web vSphere, voir [Déploiement d'un fichier OVF à l'aide du client Web vSphere](../vmonic/trbl_deploy_ovf.html).

## Liens connexes

* [Présentation de VMware Federal on IBM Cloud](vc_fed_overview.html)
* [Commande d'instances VMware Federal](vc_fed_orderinginstance.html)
* [Suppression d'instances VMware Federal](vc_fed_deletinginstance.html)
* [Contacter le support IBM](../vmonic/trbl_support.html)
