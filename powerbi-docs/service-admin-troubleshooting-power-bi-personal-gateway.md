---
title: Résolution des problèmes de Power BI Gateway - Personal
description: Résolution des problèmes de Power BI Gateway - Personal
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 12/06/2017
ms.author: mblythe
LocalizationGroup: Troubleshooting
ms.openlocfilehash: 58e6dc99198eb4f031dd28b5c80cc8babb03dbfb
ms.sourcegitcommit: 998b79c0dd46d0e5439888b83999945ed1809c94
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/17/2018
---
# <a name="troubleshooting-power-bi-gateway---personal"></a>Résolution des problèmes de Power BI Gateway - Personal
Cet article décrit certains problèmes courants que vous pouvez rencontrer lors de l’utilisation de Power BI Gateway - Personal.

> [!NOTE]
> La version actuelle de la passerelle utilisée à des fins personnelles est la suivante : **Passerelle de données locale (mode personnel)**. Mettez à jour votre installation pour utiliser cette version.
> 
> 

## <a name="update-to-the-latest-version"></a>Procéder à une mise à jour vers la dernière version
De nombreux problèmes peuvent faire surface quand la version de la passerelle est obsolète.  Nous vous recommandons de vérifier que vous possédez bien la dernière version.  Si vous n’avez pas mis à jour la passerelle depuis un mois ou plus, vous pouvez envisager d’installer la dernière version de la passerelle pour voir si vous pouvez reproduire le problème.

## <a name="installation"></a>Installation
**La passerelle personnelle est de 64 bits** - Si vous avez un ordinateur 32 bits, vous ne pouvez pas installer la passerelle personnelle. Vous devez utiliser un système d’exploitation 64 bits. Vous devez installer une version 64 bits de Windows ou installer la passerelle personnelle sur un ordinateur 64 bits.

**Échec de l’installation de Personal Gateway comme service même si vous êtes un administrateur local de l’ordinateur** : l’installation peut échouer si l’utilisateur fait partie du groupe Administrateur local de l’ordinateur, mais que la stratégie de groupe n’autorise pas ce nom d’utilisateur à ouvrir une session en tant que service.  À ce stade, vérifiez que la stratégie de groupe permet à un utilisateur d’ouvrir une session en tant que service. Nous travaillons sur la résolution de ce problème. [En savoir plus](https://technet.microsoft.com/library/cc739424.aspx)

**Délai dépassé pour l’opération** : ce problème est courant si l’ordinateur (machine physique ou virtuelle) sur lequel vous installez Personal Gateway dispose d’un processeur à cœur unique. Fermez toutes les applications et désactivez tous les processus non essentiels, puis retentez l’installation.

**La passerelle de gestion des données ou Analysis Services Connector ne peut pas être installé sur le même ordinateur que Personal Gateway** : si vous disposez déjà de Analysis Services Connector ou d’une passerelle de gestion des données, vous devez d’abord désinstaller le connecteur ou la passerelle, puis essayer d’installer Personal Gateway.

> [!NOTE]
> Si vous rencontrez un problème lors de l’installation, les journaux d’installation peuvent vous fournir des informations utiles à sa résolution. Consultez [Journaux d’installation](#SetupLogs) pour en savoir plus.
> 
> 

 **Configuration du proxy** Vous risquez de rencontrer des problèmes avec la configuration de la passerelle personnelle si votre environnement nécessite l’utilisation d’un proxy. Pour en savoir plus sur la configuration des informations du proxy, consultez [Configuration des paramètres de proxy pour les passerelles Power BI](service-gateway-proxy.md)

## <a name="schedule-refresh"></a>Planifier l’actualisation
**Erreur : les informations d’identification stockées dans le cloud sont manquantes.**

Vous pouvez obtenir cette erreur dans les paramètres pour \<jeu de données\> si vous avez planifié une actualisation, puis désinstallé et réinstallé Personal Gateway. Quand vous désinstallez Personal Gateway, les informations d’identification de la source de données pour un jeu de données qui a été configuré pour l’actualisation sont supprimées du service Power BI.

**Solution :** dans Power BI, accédez aux paramètres d’actualisation pour un jeu de données. Dans Gérer les sources de données, pour toute source de données avec une erreur, cliquez sur Modifier les informations d’identification et connectez-vous à nouveau à la source de données.

**Erreur : les informations d’identification fournies pour le jeu de données ne sont pas valides. Mettez à jour les informations d’identification via une actualisation ou dans la boîte de dialogue Paramètres de la source de données pour continuer.**

**Solution :** si vous obtenez un message relatif aux informations d’identification, cela peut signifier ce qui suit :

* Vérifiez que les noms d’utilisateur et mots de passe utilisés pour se connecter aux sources de données sont à jour. Dans Power BI, accédez aux paramètres d’actualisation pour le jeu de données. Dans Gérer les sources de données, cliquez sur Modifier les informations d’identification pour mettre à jour ces informations pour la source de données.
* Dans une même requête, les applications web hybrides entre une source cloud et une source locale ne parviennent pas à s’actualiser dans la passerelle personnelle si l’une des sources utilise OAuth pour l’authentification. C’est le cas, par exemple, d’une application web hybride entre CRM Online et un serveur SQL Server local. Cette opération échoue, car CRM Online requiert OAuth.
  
  Il s’agit d’un problème connu qui est actuellement traité. Pour contourner le problème, utilisez une requête distincte pour la source cloud et la source locale et optez pour une requête de fusion ou d’adjonction pour combiner ces deux sources.

**Erreur : source de données non prise en charge.**

**Solution :** si vous obtenez un message indiquant une source de données non prise en charge dans les paramètres de planification de l’actualisation, cela peut signifier ce qui suit : 

* La source de données n’est actuellement pas prise en charge pour l’actualisation dans Power BI. 
* Le classeur Excel ne contient pas un modèle de données, seulement des données de feuille de calcul. Power BI ne prend actuellement en charge l’actualisation que si le classeur Excel téléchargé contient un modèle de données. Quand vous importez des données à l’aide de Power Query dans Excel, veillez à choisir l’option pour charger des données dans un modèle de données. Ainsi, les données sont importées dans un modèle de données. 

**Erreur : [Impossible de combiner des données] &lt;partie de requête&gt;/&lt;…&gt;/&lt;…&gt; accède à des sources de données dont les niveaux de confidentialité ne peuvent pas être utilisés ensemble. Reconstruisez cette combinaison de données.**

**Solution**: cette erreur est due à des restrictions du niveau de confidentialité et aux types de sources de données que vous utilisez.

**Erreur : Erreur de source de données : Désolé... Nous n'avons pas pu convertir la valeur « \[Table\] » en type Table.**

**Solution**: cette erreur est due à des restrictions du niveau de confidentialité et aux types de sources de données que vous utilisez.

**Erreur : espace insuffisant pour cette ligne.**

Cela se produit si la taille d’une seule ligne est supérieure à 4 Mo. Vous devez identifier la ligne dans votre source de données et essayer de l’éliminer ou d’en réduire la taille.

## <a name="data-sources"></a>Sources de données
**Fournisseur de données manquant** : Personal Gateway est une version 64 bits uniquement. Il requiert une version 64 bits des fournisseurs de données à installer sur le même ordinateur où Personal Gateway est installé. Par exemple, si la source de données dans le jeu de données est Microsoft Access, vous devez installer le fournisseur ACE 64 bits sur le même ordinateur où Personal Gateway est installé.  

>[!NOTE]
>Si vous disposez de la version 32 bits d’Excel, vous ne pouvez pas installer un fournisseur ACE 64 bits sur le même ordinateur.

**L’authentification Windows n’est pas prise en charge pour la base de données Access** : Power BI ne prend actuellement en charge que l’authentification anonyme pour la base de données Access. Nous travaillons sur l’activation de l’authentification Windows pour la base de données Access.

**Erreur de connexion lors de la saisie des informations d’identification pour une source de données** : si vous obtenez une erreur similaire à celle-ci quand vous entrez des informations d’identification Windows pour une source de données, vous utilisez peut-être toujours une ancienne version de Personal Gateway. [Installez la dernière version de Power BI Gateway - Personal](https://powerbi.microsoft.com/gateway/).

  ![](media/service-admin-troubleshooting-power-bi-personal-gateway/pbi_pg_credentialserror.jpg.png)

**Erreur : Erreur de connexion lors de la sélection de l’authentification Windows pour une source de données avec ACE OLEDB**. Si vous obtenez l’erreur suivante lors de la saisie des informations d’identification de la source de données pour une source de données avec le fournisseur ACE OLEDB :

![](media/service-admin-troubleshooting-power-bi-personal-gateway/aceoledberror.png)

Power BI ne prend actuellement pas en charge l’authentification Windows pour une source de données avec le fournisseur ACE OLEDB.

**Solution :** pour contourner cette erreur, vous pouvez sélectionner l’authentification anonyme. Pour le fournisseur ACE OLEDB hérité, les informations d’identification anonymes sont équivalentes aux informations d’identification Windows.

## <a name="tile-refresh"></a>Actualisation des vignettes
Si vous recevez une erreur relative à l’actualisation des vignettes de tableau de bord, reportez-vous à l’article suivant.

[Résolution des erreurs de vignette](refresh-troubleshooting-tile-errors.md)

## <a name="tools-for-troubleshooting"></a>Outils de résolution des problèmes
### <a name="refresh-history"></a>Historique des actualisations
L’**historique des actualisations** peut vous aider à déterminer les erreurs qui se sont produites. Vous pouvez aussi y trouver des données utiles au cas où vous auriez besoin de créer une demande de support. Vous pouvez visualiser à la fois les actualisations planifiées et les actualisations à la demande. Voici comment accéder à l’**historique des actualisations**.

1. Dans le volet de navigation Power BI, dans **Jeux de données**, sélectionnez un jeu de données &gt; Menu Ouvrir &gt; **Planifier l’actualisation**
   ![](media/service-admin-troubleshooting-power-bi-personal-gateway/scheduled-refresh.png)
2. Dans **Paramètres pour...** &gt;**Planifier l’actualisation**, sélectionnez **Historique des actualisations**.  
   ![](media/service-admin-troubleshooting-power-bi-personal-gateway/scheduled-refresh-2.png)
   
   ![](media/service-admin-troubleshooting-power-bi-personal-gateway/refresh-history.png)

### <a name="event-logs"></a>Journaux d’événements
Plusieurs journaux d’événements peuvent fournir des informations. Les deux premiers, **Passerelle de gestion des données** et **PowerBIGateway**, sont disponibles si vous êtes administrateur de l’ordinateur.  Si vous n’êtes pas administrateur et que vous utilisez Personal Gateway, vous trouverez les entrées de journal dans le journal **Application** .

Les journaux **Passerelle de gestion des données** et **PowerBIGateway** se situent sous **Journaux des applications et des services**.

![](media/service-admin-troubleshooting-power-bi-personal-gateway/event-logs.png)

### <a name="fiddler-trace"></a>Trace Fiddler
[Fiddler](http://www.telerik.com/fiddler) est un outil gratuit de Telerik qui surveille le trafic HTTP.  Vous pouvez voir les allers et retours au niveau du service Power BI à partir de l’ordinateur client. Vous pouvez ainsi repérer les erreurs et d’autres informations connexes.

![](media/service-admin-troubleshooting-power-bi-personal-gateway/fiddler.png)

<a name="SetupLogs"></a>

### <a name="setup-logs"></a>Journaux d’installation
Si **Personal Gateway** ou le connecteur Analysis Services ne s’installe pas, vous trouverez un lien pour consulter le journal d’installation. Vous y trouverez peut-être les détails de l’échec. Il s’agit de journaux Windows Install, aussi appelés journaux MSI. Ils peuvent être assez complexes et difficiles à lire. En général, l’erreur rencontrée apparaît en bas, mais il n’est pas simple d’en déterminer la cause. Elle peut être due à des erreurs dans un autre journal ou à une erreur apparue plus haut dans le journal.

![](media/service-admin-troubleshooting-power-bi-personal-gateway/setup-log.png)

Vous pouvez aussi accéder à votre **dossier temporaire** (%temp%) et y rechercher des fichiers qui commencent par **Power\_BI\_**.

> [!NOTE]
> En accédant à %temp%, vous risquez de vous retrouver dans un sous-dossier de temp.  Les fichiers **Power\_BI\_** se trouvent à la racine du répertoire temp.  Vous serez peut-être amené à monter d’un ou deux niveaux.
> 
> 

![](media/service-admin-troubleshooting-power-bi-personal-gateway/setup-logs2.png)

## <a name="next-steps"></a>Étapes suivantes
[Configuration des paramètres de proxy pour les passerelles Power BI](service-gateway-proxy.md)  
[Actualisation des données](refresh-data.md)  
[Power BI Gateway - Personal](personal-gateway.md)  
[Résolution des erreurs de vignette](refresh-troubleshooting-tile-errors.md)  
[Résolution des problèmes de passerelle de données locale](service-gateway-onprem-tshoot.md)  
D’autres questions ? [Posez vos questions à la communauté Power BI](http://community.powerbi.com/)

