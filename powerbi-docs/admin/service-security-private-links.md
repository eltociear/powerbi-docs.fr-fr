---
title: Liaisons privées pour accéder à Power BI
description: Comment configurer une liaison privée pour utiliser Power BI
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-security
ms.topic: how-to
ms.date: 11/12/2020
ms.custom: ''
LocalizationGroup: Administration
ms.openlocfilehash: 446c3620cf3b2a7435897108cfcd9c8972ad8bb4
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2020
ms.locfileid: "96412158"
---
# <a name="private-links-for-accessing-power-bi"></a>Liaisons privées pour accéder à Power BI

La mise en réseau Azure offre la fonctionnalité de liaisons privées Azure qui permet à Power BI de garantir un accès sécurisé par le biais de points de terminaison privés Azure Networking. Avec les liaisons privées Azure et les points de terminaison privés, le trafic de données est envoyé en privé à l’aide de l’infrastructure réseau principale de Microsoft, ce qui signifie que les données ne transitent pas par Internet. 

Les liaisons privées garantissent que les utilisateurs Power BI utilisent le segment principal du réseau privé Microsoft pour accéder aux ressources du service Power BI.

Découvrez-en plus sur les [liaisons privées Azure](https://azure.microsoft.com/services/private-link/).

## <a name="understanding-private-links"></a>Compréhension des liaisons privées

Les liaisons privées garantissent que le trafic qui passe *dans* les artefacts Power BI de votre organisation (comme des rapports ou des espaces de travail) suit toujours le chemin réseau de la liaison privée configurée de votre organisation. Le trafic utilisateur vers vos artefacts Power BI doit provenir de la liaison privée établie et vous pouvez configurer Power BI pour refuser toutes les demandes qui ne proviennent pas du chemin réseau configuré. 

Les liaisons privées ne garantissent *pas* que le trafic depuis Power BI vers vos sources de données externes, dans le cloud ou localement, est sécurisé. Vous devez alors configurer des règles de pare-feu et des réseaux virtuels pour sécuriser davantage vos sources de données. 

### <a name="power-bi-and-private-links-integration"></a>Intégration de Power BI et des liaisons privées

Le point de terminaison privé Azure pour Power BI est une interface réseau qui vous connecte en privé et de manière sécurisée au service Power BI, avec Azure Private Link.   

L’intégration des points de terminaison privés permet de déployer les services PaaS (platform as a service) et d’y accéder en privé à partir des réseaux locaux et virtuels du client, alors que le service est toujours en cours d’exécution en dehors du réseau du client. Les points de terminaison privés sont une technologie unique et directionnelle qui permet aux clients d’établir des connexions à un service donné, mais qui ne permet pas au service d’établir une connexion au réseau des clients. Ce modèle d’intégration de point de terminaison privé assure l’isolement de la gestion, puisque le service peut fonctionner indépendamment de la configuration de la stratégie réseau du client. Pour les services multi-locataires, ce modèle de point de terminaison privé fournit des identificateurs de liaison pour empêcher l’accès aux autres ressources des clients hébergées au sein du même service. Quand vous utilisez des points de terminaison privés, seul un ensemble limité des autres ressources de service PaaS est accessible à partir des services par le biais de l’intégration.  

Le service Power BI implémente des points de terminaison privés, et non des points de terminaison de service.  

L’utilisation de liaisons privées avec Power BI offre les avantages suivants :

1. Les liaisons privées garantissent que le trafic transite par le segment principal Azure vers un point de terminaison privé pour les ressources cloud Azure. 

2. L’isolement du trafic réseau par rapport à une infrastructure non-Azure, comme un accès local, exigerait que les clients disposent d’ExpressRoute ou d’un réseau privé virtuel (VPN) configuré.  

## <a name="using-secure-private-links-to-access-power-bi"></a>Utilisation de liaisons privées sécurisées pour accéder à Power BI

Dans Power BI, vous pouvez configurer et utiliser un point de terminaison par lequel votre organisation pourra accéder à Power BI en mode privé. Pour configurer des liaisons privées, vous devez être administrateur Power BI et avoir les autorisations dans Azure qui vous permettent de créer et configurer des ressources telles que des machines virtuelles et des réseaux virtuels. 

Voici les étapes nécessaires pour accéder de façon sécurisée à Power BI par le biais de liaisons privées :

1. [Activer des liaisons privées pour Power BI](#enable-private-links-for-power-bi)
2. [Créer une ressource Power BI dans le portail Azure](#create-a-power-bi-resource-in-the-azure-portal)
3. [Création d'un réseau virtuel](#create-a-virtual-network)
4. [Créer une machine virtuelle](#create-a-virtual-machine-vm)
5. [Créer un point de terminaison privé](#create-a-private-endpoint)
6. [Se connecter à une machine virtuelle à l’aide du Bureau à distance (RDP)](#connect-to-a-vm-using-remote-desktop-rdp)
7. [Accéder à Power BI en mode privé à partir de la machine virtuelle](#access-power-bi-privately-from-the-vm)
8. [Désactiver l’accès public pour Power BI](#disable-public-access-for-power-bi)

Les sections suivantes fournissent des informations supplémentaires pour chaque étape.

## <a name="enable-private-links-for-power-bi"></a>Activer des liaisons privées pour Power BI

Pour commencer, connectez-vous à Power BI sur app.powerbi.com en tant qu’administrateur, puis accédez au portail d’administration. Sélectionnez **Paramètres du locataire** et faites défiler le contenu jusqu’à **Mise en réseau avancée**, puis activez la case d’option pour activer **Azure Private Link**, comme illustré dans l’image suivante. 

La configuration d’une liaison privée pour un locataire prend environ 15 minutes, ce qui comprend la configuration d’un nom de domaine complet distinct pour le locataire qui permet la communication en mode privé avec les services Power BI.

![Activer Azure Private Link](media/service-security-private-links/service-private-links-01.png)

Une fois l’opération terminée, vous pouvez passer à l’étape suivante.

## <a name="create-a-power-bi-resource-in-the-azure-portal"></a>Créer une ressource Power BI dans le portail Azure

Connectez-vous ensuite au [portail Azure](https://portal.azure.com) et créez une ressource Power BI en utilisant un **modèle Azure**. Remplacez les paramètres de l’exemple de modèle ARM, indiqués dans le tableau suivant, pour créer une ressource Power BI.


|**Paramètre**  |**Valeur**  |
|---------|---------|
|```<resource-name>```    | myPowerBIResource         |
|```<tenant-object-id>```     | 52d40f65-ad6d-48c3-906f-1ccf598612d4         |

Créer le modèle ARM 

```
{
  "$schema": "http://schema.management.azure.com/schemas/2015-01-01/deploymentTemplate.json#",
  "contentVersion": "1.0.0.0",
  "parameters": {},
  "resources": [
      {
          "type":"Microsoft.PowerBI/privateLinkServicesForPowerBI",
          "apiVersion": "2020-06-01",
          "name" : "<resource-name>",
          "location": "global",
          "properties" : 
          {
               "tenantId": "<tenant-object-id>"
          }
      }
  ]
}
```

Dans la boîte de dialogue qui s’affiche, cochez la case pour accepter les conditions générales, puis sélectionnez **Acheter**.

![Accepter les conditions générales, puis acheter le modèle](media/service-security-private-links/service-private-links-02.png)


## <a name="create-a-virtual-network"></a>Créez un réseau virtuel

L’étape suivante consiste à créer un réseau virtuel et un sous-réseau. Remplacez les paramètres en exemple dans le tableau ci-dessous par les vôtres pour créer un réseau virtuel et un sous-réseau.

| Paramètre |   Valeur| 
|---------|---------|
| ```<resource-group-name>```   | myResourceGroup |
| ```<virtual-network-name>```  | myVirtualNetwork |
| ```<region-name>```   | USA Centre  |
| ```<IPv4-address-space>```    | 10.1.0.0/16 |
| ```<subnet-name>```   | mySubnet |
| ```<subnet-address-range>```  | 10.1.0.0/24 |

1. En haut à gauche de l’écran, sélectionnez **Créer une ressource > Réseau > Réseau virtuel**, ou recherchez **Réseau virtuel** à partir de la zone de recherche.
2. Dans **Créer un réseau virtuel**, entrez ou sélectionnez les informations suivantes sous l’onglet **Général** :

    |Paramètres | Valeur |
    |-------------------|---------|
    |**Détails du projet**|
    |Abonnement | Sélectionner votre abonnement Azure |
    |Groupe de ressources |   Sélectionnez **Créer**, entrez ```<resource-group-name>```, puis sélectionnez **OK**, ou sélectionnez un ```<resource-group-name>``` existant en fonction des paramètres. |
    |**Détails de l’instance** |
    | Nom  | Entrez ```<virtual-network-name>``` |
    |Region | Sélectionnez ```<region-name>``` |
    
    L’image suivante montre l’onglet **Général**.
    
    ![Créer un réseau virtuel, onglet Général](media/service-security-private-links/service-private-links-03.png)


3. Maintenant, sélectionnez l’onglet **Adresses IP**, ou sélectionnez le **bouton Suivant : Adresses IP** au bas du formulaire. Sous l’onglet Adresses IP, entrez les informations suivantes :

    |Paramètres | Valeur |
    |-------------------|---------|
    |Espace d’adressage IPv4 |Entrez ```<IPv4-address-space>``` |
    
    ![Créer un réseau virtuel, onglet Adresses IP](media/service-security-private-links/service-private-links-04.png)
    

4. Dans **Nom du sous-réseau**, sélectionnez le mot *par défaut*, puis dans **Modifier le sous-réseau**, entrez les informations suivantes :

    |Paramètres | Valeur |
    |-------------------|---------|
    | Nom du sous-réseau |Entrez ```<subnet-name>``` |
    | Plage d’adresses de sous-réseau | Entrez ```<subnet-address-range>``` |
    
    
    ![Créer un réseau virtuel, onglet Modifier le sous-réseau](media/service-security-private-links/service-private-links-05.png)

5. Sélectionnez **Enregistrer**, puis sélectionnez l’onglet **Vérifier + créer**, ou sélectionnez le bouton **Vérifier + créer**. 

6. Sélectionnez ensuite **Create** (Créer).

Après avoir terminé ces étapes, vous pouvez créer une machine virtuelle comme cela est décrit dans la section suivante.

## <a name="create-a-virtual-machine-vm"></a>Créer une machine virtuelle


L’étape suivante consiste à créer un réseau virtuel et le sous-réseau où sera hébergée la machine virtuelle.

1. En haut à gauche de l’écran dans le portail Azure, sélectionnez **Créer une ressource > Calcul > Machine virtuelle**.

2. Dans **Créer une machine virtuelle - Général**, entrez ou sélectionnez les informations suivantes :

    |Paramètres | Valeur |
    |-------------------|---------|
    |**Détails du projet**||
    |Abonnement | Sélectionner votre abonnement Azure |
    |Groupe de ressources |   Sélectionnez le groupe **myResourceGroup** que vous avez créé dans la section précédente. |
    |**Détails de l’instance** ||
    |Nom | Entrez **myVm** |
    |Region | Sélectionnez **USA Centre** |
    |Options de disponibilité| Conservez la valeur par défaut **Aucune redondance d’infrastructure nécessaire** |
    |Image | Sélectionnez **Windows 10 Professionnel** |
    |Taille | Conservez la valeur par défaut **Standard DS1 v2** |
    |COMPTE ADMINISTRATEUR ||
    |Nom d’utilisateur |Entrez un nom d’utilisateur de votre choix |
    |Mot de passe | Entrez un mot de passe de votre choix. Le mot de passe doit contenir au moins 12 caractères et satisfaire aux [exigences de complexité définies](/azure/virtual-machines/windows/faq#what-are-the-password-requirements-when-creating-a-vm) |
    |Confirmer le mot de passe | Entrez à nouveau le mot de passe |
    |RÈGLES DES PORTS D’ENTRÉE ||
    |Aucun port d’entrée public | Conservez la valeur par défaut **Aucun** |
    |ÉCONOMISEZ DE L’ARGENT ||
    |Vous disposez déjà d’une licence Windows ? |  Conservez la valeur par défaut **Non** |

3. Ensuite, sélectionnez **Next: Disques**
4. Dans **Créer une machine virtuelle - Disks**, conservez les valeurs par défaut et sélectionnez **Suivant : Mise en réseau**.
5. Dans **Créer une machine virtuelle - Mise en réseau**, sélectionnez les informations suivantes :

    |Paramètres | Valeur |
    |-------------------|---------|
    |Réseau virtuel|   Conservez la valeur par défaut **MyVirtualNetwork**|
    |Espace d’adressage| Conservez la valeur par défaut **10.1.0.0/24**|
    |Subnet |Conservez la valeur par défaut **mySubnet (10.1.0.0/24)**|
    |Adresse IP publique| Conservez la valeur par défaut **(new) myVm-ip**|
    |Aucun port d’entrée public|  Sélectionnez **Autoriser les ports sélectionnés**|
    |Sélectionner des ports d’entrée|  Sélectionnez **RDP**|

6. Sélectionnez **Revoir + créer**. Vous êtes redirigé vers la page **Vérifier + créer** où Azure valide votre configuration.
7. Lorsque le message **Validation passed** (Validation réussie) apparaît, sélectionnez **Créer**.


## <a name="create-a-private-endpoint"></a>Créer un Private Endpoint

L’étape suivante, qui est décrite dans cette section, consiste à créer un point de terminaison privé pour Power BI.

1. En haut à gauche de l’écran dans le portail Azure, sélectionnez **Créer une ressource > Mise en réseau > Centre de liaisons privées (préversion)** .
2. Dans **Centre de liaisons privées - Vue d’ensemble**, dans l’option pour **Générer une connexion privée à un service**, sélectionnez **Créer un point de terminaison privé**.
3. Dans **Créer un point de terminaison privé (préversion) - Général**, entrez ou sélectionnez les informations suivantes :

    |Paramètres | Valeur |
    |-------------------|---------|
    |**Détails du projet** ||
    |Abonnement|  Sélectionner votre abonnement Azure|
    |Groupe de ressources|    Sélectionnez **myResourceGroup**. Vous avez créé ce groupe dans la section précédente|
    |**Détails de l’instance** ||
    |Nom|  Entrez *myPrivateEndpoint*. Si ce nom est utilisé, créez un nom unique|
    |Region|    Sélectionnez **USA Centre**|
    
    L’image suivante montre la fenêtre **Créer un point de terminaison privé - Général**.
    
    ![Créer un point de terminaison privé, général](media/service-security-private-links/service-private-links-06.png)

4. Une fois ces informations renseignées, sélectionnez **Suivant : Ressource** et, dans la page **Créer un point de terminaison privé - Ressource**, entrez ou sélectionnez les informations suivantes :

    |Paramètres | Valeur |
    |-------------------|---------|
    |Méthode de connexion| Sélectionner Se connecter à une ressource Azure dans mon répertoire|
    |Abonnement|  Sélectionnez votre abonnement|
    |Type de ressource| Sélectionnez **Microsoft.PowerBI/privateLinkServicesForPowerBI** |
    |Ressource|  myPowerBIResource|
    |Sous-ressource cible|   Locataire|
    
    L’image suivante montre la fenêtre **Créer un point de terminaison privé - Ressource**.
    
    ![Créer un point de terminaison privé, ressource](media/service-security-private-links/service-private-links-07.png)

5. Après avoir entré ces informations correctement, sélectionnez **Suivant : Configuration** et, dans **Créer un point de terminaison privé (préversion) - Configuration**, entrez ou sélectionnez les informations suivantes :

    |Paramètres | Valeur |
    |-------------------|---------|
    |**MISE EN RÉSEAU** ||
    |Réseau virtuel|   Sélectionner *myVirtualNetwork* |
    |Subnet |Sélectionnez *mySubnet* |
    |**INTÉGRATION À DNS PRIVÉ** ||
    |Intégrer à une zone DNS privée|   Sélectionnez **Oui** |
    |Zone DNS privée   |Sélectionnez <br> *(New)privatelink.analysis.windows.net* <br> *(New)privatelink.pbidedicated.windows.net* <br> *(New)privatelink.tip1.powerquery.microsoft.com* |
    
    L’image suivante montre la fenêtre **Créer un point de terminaison privé - Configuration**.
    
    ![Créer un point de terminaison privé, configuration](media/service-security-private-links/service-private-links-08.png)
    
    Sélectionnez ensuite **Vérifier + créer**, qui affiche la page **Vérifier + créer** dans laquelle Azure valide votre configuration. Lorsque le message **Validation passed** (Validation réussie) apparaît, sélectionnez **Créer**.

## <a name="connect-to-a-vm-using-remote-desktop-rdp"></a>Se connecter à une machine virtuelle à l’aide du Bureau à distance (RDP)

Une fois que vous avez créé votre machine virtuelle, appelée **myVm**, connectez-la à partir d’Internet en effectuant les étapes ci-dessous :

1. Dans la barre de recherche du portail, entrez *myVm*.
2. Sélectionnez le bouton **Connexion**. La sélection du bouton **Connexion** entraîne l’ouverture de la page **Se connecter à la machine virtuelle**.
3. Sélectionnez **Télécharger le fichier RDP**. Azure crée un fichier de protocole RDP (Remote Desktop Protocol) ( .rdp) et le télécharge sur votre ordinateur.
4. Ouvrez le fichier .rdp téléchargé.
5. Si vous y êtes invité, sélectionnez **Connexion**.
6. Entrez le nom d’utilisateur et le mot de passe spécifiés quand vous avez créé la machine virtuelle à l’étape précédente.
7. Sélectionnez **OK**.
8. Un avertissement de certificat peut s’afficher pendant le processus de connexion. Si vous recevez un avertissement de certificat, sélectionnez **Oui** ou **Continuer**.

## <a name="access-power-bi-privately-from-the-vm"></a>Accéder à Power BI en mode privé à partir de la machine virtuelle

L’étape suivante consiste à accéder à Power BI en mode privé, à partir de la machine virtuelle que vous avez créée à l’étape précédente, en procédant comme suit : 

1. Dans le Bureau à distance de myVM, ouvrez PowerShell.
2. Entrez nslookup 52d40f65ad6d48c3906f1ccf598612d4-api.privatelink.analysis.windows.net.
3. Vous recevez un message similaire à celui ci :

    ```
    Server:  UnKnown
    Address:  168.63.129.16
    
    Non-authoritative answer:
    Name:    52d40f65ad6d48c3906f1ccf598612d4-api.privatelink.analysis.windows.net
    Address:  10.1.0.4
    ```

4. Ouvrez le navigateur et connectez-vous à app.powerbi.com pour accéder à Power BI en mode privé.

## <a name="disable-public-access-for-power-bi"></a>Désactiver l’accès public pour Power BI

Enfin, vous devez désactiver l’accès public pour Power BI. 

Connectez-vous à app.powerbi.com en tant qu’administrateur, puis accédez au **portail d’administration**. Sélectionnez **Paramètres du locataire** et faites défiler le contenu jusqu’à la section **Mise en réseau avancée**. Activez le bouton bascule dans la section **Bloquer l’accès Internet public**, comme indiqué dans l’image suivante. Il faut environ 15 minutes au système pour désactiver l’accès de votre organisation à Power BI à partir de l’Internet public.

Vous avez terminé ces étapes. Votre organisation a maintenant accès à Power BI uniquement à partir de liaisons privées et plus à partir de l’Internet public. 

## <a name="considerations-and-limitations"></a>Considérations et limitations

Il y a plusieurs points à prendre en compte si vous utilisez des liaisons privées dans Power BI :

* Il n’est pas possible d’utiliser des images ou thèmes externes dans un environnement de liaison privée, et cela peut impacter les visuels personnalisés
* Les services d’exportation, comme Exporter en PDF, l’exportation vers Excel à partir d’un rapport et d’autres services d’exportation ne fonctionnent pas dans un environnement de liaison privée
* Les rapports SQL Server Reporting Services, communément appelés fichiers RDL (fichiers au format *.rdl), ne peuvent pas être visualisés dans les environnements de liaison privée
* Si l’accès à Internet est désactivé et que le jeu de données ou le flux de données se connecte à un jeu de données ou à un flux de données Power BI comme source de données, la connexion échoue.
* Les métriques d’utilisation *ne fonctionnent pas* quand des liaisons privées sont activées
* La publication sur le web est grisée (ce qui signifie qu’elle n’est pas prise en charge) quand vous activez **Bloquer l’accès Internet public** dans Power BI


## <a name="next-steps"></a>Étapes suivantes

- [Administration de Power BI dans votre organisation](service-admin-administering-power-bi-in-your-organization.md)  
- [Présentation du rôle d’administrateur Power BI](service-admin-role.md)  
- [Audit de Power BI dans votre organisation](service-admin-auditing.md)  

D’autres questions ? [Essayez d’interroger la communauté Power BI](https://community.powerbi.com/)
