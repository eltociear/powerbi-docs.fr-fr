---
title: Créer un lien vers un emplacement spécifique dans les applications mobiles Power BI
description: Apprenez à créer un lien ciblé qui pointe vers un rapport, une vignette ou un tableau de bord spécifique dans l’application mobile Power BI à l’aide d’un URI (Uniform Resource Identifier).
author: paulinbar
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-mobile
ms.topic: how-to
ms.date: 11/16/2020
ms.author: painbar
ms.openlocfilehash: 08ddac0cf407444b4a4c135494c5951bab515cdd
ms.sourcegitcommit: bd133cb1fcbf4f6f89066165ce065b8df2b47664
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "94669060"
---
# <a name="create-a-link-to-a-specific-location-in-the-power-bi-mobile-apps"></a>Créer un lien vers un emplacement spécifique dans les applications mobiles Power BI
Vous pouvez utiliser des liens pour accéder directement à du contenu Power BI spécifique, comme un rapport spécifique, une page de rapport, un tableau de bord, une vignette, etc.

Il existe deux principaux scénarios pour utiliser des liens afin d’accéder à du contenu dans les applications mobiles Power BI : 

* Ouvrir Power BI **en dehors de l’application mobile** pour accéder à du contenu spécifique. Il s’agit généralement d’un scénario d’intégration dans lequel vous ouvrez l’application mobile Power BI à partir d’une autre application. 
* Pour **naviguer** dans Power BI. C’est généralement ce que vous faites pour créer une navigation personnalisée dans Power BI.

Cet article aborde les cas suivants :
* Utilisation de liens pour ouvrir du contenu Power BI spécifique en dehors de l’application mobile. Deux formats de lien sont décrits. L’un utilise une méthode de redirection que vous pouvez utiliser quel que soit l’endroit où Power BI s’ouvre. L’autre s’ouvre directement dans l’appareil mobile Power BI et fonctionne uniquement sur des appareils mobiles sur lesquels l’application mobile est installée.
* Utilisation de liens à l’intérieur de Power BI pour accéder à du contenu Power BI spécifique.

## <a name="use-links-from-outside-the-mobile-app"></a>Utiliser des liens en dehors de l’application mobile
Quand vous voulez créer un lien vers un élément spécifique dans Power BI en dehors de l’application mobile, vous avez deux possibilités, selon l’endroit où le lien va être ouvert :

* Si vous voulez que le lien s’ouvre correctement quel que soit l’endroit où l’utilisateur clique dessus, dans le navigateur de son ordinateur ou sur un appareil mobile, vous pouvez créer un tel lien. Ce comportement intelligent du lien est possible grâce à une syntaxe de redirection spéciale.

* Si vous savez que le lien va uniquement être ouvert sur un appareil mobile sur lequel l’application mobile Power BI est installée, vous pouvez éviter la surcharge liée à la redirection dans la méthode ci-dessus et utiliser une autre syntaxe de lien qui ouvre le lien directement dans l’application mobile Power BI sur l’appareil mobile. Toutefois, il est important de noter que, si ce lien évite la surcharge liée à la redirection dans la première méthode, il ne fonctionnera pas s’il est ouvert ailleurs que sur un appareil mobile sur lequel l’application Power BI mobile est installée.

### <a name="create-a-link-that-works-anywhere"></a>Créer un lien qui fonctionne partout
Le format de lien décrit dans cette section utilise une redirection pour garantir le bon fonctionnement du lien, quel que soit l’endroit où l’utilisateur clique dessus.
* Si l’utilisateur clique sur le lien sur un appareil mobile, ce dernier utilise forcément l’application mobile Power BI pour ouvrir le lien. Si l’application mobile n’est pas installée sur l’appareil, l’utilisateur est invité à accéder au Store pour l’obtenir.
* Si l’utilisateur clique sur le lien sur un ordinateur, l’élément correspondant s’ouvre dans le portail web de Power BI.

Le lien doit commencer par un préfixe spécial, suivi de paramètres de requête :

https<nolink>://app.powerbi.com/Redirect? **[QUERYPARAMETERS]** </code>

> [!IMPORTANT]
> Si votre contenu est hébergé dans un centre de données spécial, comme celui du gouvernement des États-Unis, de la Chine, etc., le lien doit commencer par l’adresse de Power BI appropriée, par exemple **app.powerbigov.us** ou **app.powerbi.cn**.

Les paramètres de requête sont :

|Paramètre  | Valeur  | Description |
|---------|---------|---------|
|**action** (obligatoire)    | OpenApp<br>OpenReport<br>OpenDashboard<br>OpenTile | |
|**appId**| GUID de 36 caractères | Doit être spécifié si vous voulez ouvrir un rapport ou un tableau de bord faisant partie d’une application.<br>Exemple : **appId = baf4b16d-b5bd-4360-8a3a-51d11242c09b** |
|**groupObjectId**| GUID de 36 caractères | Spécifie l’espace de travail quand vous voulez ouvrir un rapport ou un tableau de bord qui ne fait pas partie de Mon espace de travail.<br>Exemple : **groupObjectId=9a3841c6-74b3-46f1-85fd-bdd78f27b30e** |
| **dashboardObjectId** | GUID de 36 caractères | ID d’objet du tableau de bord (si l’action est OpenDashboard ou OpenTile)<br>Exemple : **dashboardObjectId=033bb049-5b68-4392-b3ef-ae9a43738a4a** |
| **reportObjectId** | GUID de 36 caractères | ID d’objet du rapport (si l’action est OpenReport)<br>Exemple : **reportObjectId=6114cec7-78e1-4926-88ff-0bc5338452cf** |
| **tileObjectId** | GUID de 36 caractères | ID d’objet de la vignette (si l’action est OpenTile)<br>Exemple : **tileObjectId=a845dcb8-a289-43a8-94ea-67a8c0a068f9** |
| **reportPage** | ReportSection&lt;num&gt; | Nom de la page si vous voulez ouvrir une page de rapport spécifique (si l’action est OpenReport).<br>Exemple : **reportPage=ReportSection6**  |
| **bookmarkGuid** | GUID de 36 caractères | ID de signet, si vous voulez ouvrir une vue spécifique marquée d’un signet (si l’action est OpenReport).<br>Exemple : **bookmarkGuid=18e8872f-6db8-4cf8-8298-3b2ab254cc7f** |
| **ctid** | GUID de 36 caractères | ID d’organisation de l’élément (valable pour les scénarios B2B, peut être omis si l’élément appartient à l’organisation de l’utilisateur).<br>Exemple : **ctid=5367c770-09d0-4110-bf6a-d760cb5ef681**. |
||||

**Exemples :**

Dans les exemples suivants, les espaces réservés aux valeurs des paramètres sont mis en gras. Pour obtenir les valeurs réelles, accédez au service Power BI, ouvrez l’élément vers lequel vous voulez créer un lien et extrayez les valeurs dont vous avez besoin de l’URL de l’élément.

* **Ouvrir une application**

    https<nolink>://app.powerbi.com/Redirect?action=OpenApp&appId= **&lt;appid-guid&gt;** &ctid= **&lt;ctid-guid&gt;**
   
* **Ouvrir un tableau de bord faisant partie d’une application**

    https<nolink>://app.powerbi.com/Redirect?action=OpenDashboard&appId= **&lt;appid-guid&gt;** &dashboardObjectId= **&lt;dashboardid-guid&gt;** &ctid= **&lt;ctid-guid&gt;**

* **Ouvrir un rapport qui fait partie d’un espace de travail autre que Mon espace de travail**

    https<nolink>://app.powerbi.com/Redirect?Action=OpenReport&reportObjectId= **&lt;reportid-guid&gt;** &groupObjectId= **&lt;groupobjectid-guid&gt;** &reportPage=**ReportSection&lt;num&gt;**

### <a name="how-to-get-the-correct-link-format"></a>Comment obtenir le format de lien correct

#### <a name="links-to-apps-and-items-in-apps"></a>Liens vers des applications et éléments dans des applications

Pour les **applications et pour les rapports et tableaux de bord faisant partie d’une application**, le moyen le plus simple d’obtenir le lien consiste à accéder à l’espace de travail de l’application et à choisir **Mettre à jour l’application**. L’expérience de « publication de l’application » s’ouvre alors. Ouvrez l’onglet des autorisations et développez la section des liens pour voir les liens vers l’application et tout son contenu. Vous pouvez utiliser ces liens en dehors de Power BI pour accéder directement à l’application et à son contenu.

![Liens de publication des applications Power BI ](./media/mobile-apps-links/mobile-link-copy-app-links.png)

#### <a name="links-to-items-that-are-not-in-an-app"></a>Liens vers des éléments qui ne font pas partie d’une application 

Pour les rapports et les tableaux de bord qui ne font pas partie d’une application, vous devez extraire les ID d’objet dont vous avez besoin de l’URL de l’élément. Pour cela, accédez au service Power BI, puis à l’élément vers lequel vous voulez créer un lien et recherchez les valeurs dont vous avez besoin dans l’URL que vous voyez dans la barre d’adresse du navigateur.

Les exemples ci-dessous montrent où vous pouvez trouver les ID dont vous avez besoin dans les URL des éléments vers lesquels vous voulez créer un lien.

* Pour trouver un ID d’objet de tableau de bord de 36 caractères, accédez au tableau de bord spécifique vers lequel vous voulez créer un lien dans le service Power BI et recherchez l’ID d’objet du tableau de bord et tous les autres ID nécessaires aux emplacements indiqués ci-dessous :

    https<nolink>://app.powerbi.com/groups/me/dashboards/ **&lt;dashboard-object-id&gt;** ?ctid= **&lt;org-object-id&gt;**

* Pour trouver un ID d’objet de rapport de 36 caractères, accédez au rapport spécifique vers lequel vous voulez créer un lien dans le service Power BI et recherchez les ID nécessaires, comme illustré ci-dessous. Notez que cet exemple contient une référence à une page de rapport spécifique et un signet spécifique.

    https<nolink>://app.powerbi.com/groups/me/reports/ **&lt;report-object-id&gt;** /**ReportSection&lt;num&gt;** ?bookmarkGuid= **&lt;bookmark-id&gt;**

* Pour créer un lien vers un élément dans un espace de travail autre que Mon espace de travail, vous devez extraire l’ID d’objet de groupe. Cet exemple montre un rapport provenant d’un espace de travail autre que Mon espace de travail.

    https<nolink>://app.powerbi.com/groups/ **&lt;group-object-id&gt;** /reports/ **&lt;report-object-id&gt;** /**ReportSection&lt;report-section-num&gt;** ?ctid= **&lt;org-object-id&gt;**

### <a name="create-a-link-that-opens-only-on-a-device-that-has-the-power-bi-mobile-app-installed"></a>Créer un lien qui s’ouvre uniquement sur un appareil sur lequel l’application mobile Power BI est installée

Le format de lien décrit dans cette section permet de créer un lien vers un emplacement spécifique situé au sein des applications mobiles Power BI sur toutes les plateformes mobiles : appareils iOS, Android et Windows 10. Ce format de lien ouvre l’emplacement directement, sans impliquer aucune redirection dans la méthode décrite dans la section précédente. **Ce format ne peut être ouvert que sur des appareils mobiles sur lesquels l’application mobile Power BI est installée**.

Les liens dans ce format peuvent pointer directement vers des tableaux de bord, des vignettes et des rapports. La destination du lien ciblé détermine son format. Pour créer des liens ciblés vers différents emplacements, suivez les étapes ci-après. 

* **Ouvrir l’application mobile Power BI**

    Pour ouvrir l’application mobile Power BI sur un appareil, utilisez ce lien :

    mspbi://app/

* **Ouvrir un tableau de bord spécifique**

    Ce lien ouvre l’application mobile Power BI sur un tableau de bord spécifique :

    mspbi://app/OpenDashboard?DashboardObjectId= **<36-character-dashboard-id>**

    Pour obtenir l’ID d’objet de tableau de bord contenant 36 caractères, accédez au tableau de bord spécifique dans le service Power BI et extrayez-le de l’URL. Par exemple, l’ID d’objet de tableau de bord est mis en surbrillance dans l’URL suivante du service Power BI :

    https<nolink>://app.powerbi.com/groups/me/dashboards/ **&lt;61b7e871-cb98-48ed-bddc-6572c921e270&gt;**

    Si le tableau de bord n’est pas dans Mon espace de travail, vous avez besoin d’ajouter également l’ID d’objet de groupe, avant ou après l’ID de tableau de bord. Le lien ciblé indiqué ci-dessous a le paramètre ID d’objet de groupe ajouté après l’ID d’objet de tableau de bord :

    mspbi://app/OpenDashboard?DashboardObjectId=**e684af3a-9e7f-44ee-b679-b9a1c59b5d60**&GroupObjectId=**8cc900cc-7339-467f-8900-fec82d748248**</code>

    Remarquez l’esperluette (&) entre les deux paramètres.

* **Ouvrir une vignette spécifique en mode focus**

    Ce lien ouvre une vignette spécifique en mode focus dans l’application mobile Power BI :

    mspbi://app/OpenTile?DashboardObjectId= **<36-character-dashboard-id>** &TileObjectId= **<36-character-tile-id>**

    Pour rechercher les ID d’objet de vignette et de tableau de bord contenant 36 caractères, accédez au tableau de bord spécifique dans le service Power BI et ouvrez la vignette en mode focus. Dans l’exemple ci-dessous, les ID de tableau de bord et de vignette sont mis en surbrillance.

    https<nolink>://app.powerbi.com/groups/me/dashboards/**3784f99f-b460-4d5e-b86c-b6d8f7ec54b7**/tiles/**565f9740-5131-4648-87f2-f79c4cf9c5f5**/infocus

    Pour ouvrir cette vignette directement, le lien est le suivant :

    mspbi://app/OpenTile?DashboardObjectId=3784f99f-b460-4d5e-b86c-b6d8f7ec54b7&TileObjectId=565f9740-5131-4648-87f2-f79c4cf9c5f5

    Remarquez l’esperluette (&) entre les deux paramètres.

    Si le tableau de bord n’est pas dans Mon espace de travail, ajoutez le paramètre GroupObjectId, par exemple &GroupObjectId=<36-character-group-id>

* **Ouvrir un rapport spécifique**

    Ce lien ouvre un rapport spécifique dans l’application mobile Power BI :

    mspbi://app/OpenReport?ReportObjectId= **<36-character-report-id>**

    Pour rechercher l’ID d’objet de rapport contenant 36 caractères, accédez au rapport correspondant dans le service Power BI. L’URL suivante du service Power BI illustre l’ID de rapport que vous avez besoin d’extraire.

    https<nolink>://app.powerbi.com/groups/me/reports/**df9f0e94-31df-450b-b97f-4461a7e4d300**

    Si le rapport ne se trouve pas dans Mon espace de travail, vous devez également ajouter **&GroupObjectId=<36-character-group-id>** , avant ou après l’ID de rapport. Par exemple, dans cet exemple, le lien ciblé est :

    mspbi://app/OpenReport?ReportObjectId=**e684af3a-9e7f-44ee-b679-b9a1c59b5d60**&GroupObjectId=**8cc900cc-7339-467f-8900-fec82d748248**

    Remarquez l’esperluette (&) entre les deux paramètres.

* **Ouvrir une page de rapport spécifique**

    Ce lien ouvre une page de rapport spécifique dans l’application mobile Power BI :

    mspbi://app/OpenReport?ReportObjectId= **<36-character-report-id>** &reportPage=**ReportSection&lt;number&gt;**

    La page de rapport porte le nom **ReportSection** suivi d’un nombre. Là encore, pour trouver les valeurs dont vous avez besoin, ouvrez le rapport dans le service Power BI, accédez à la page de rapport spécifique, puis extrayez les valeurs dont vous avez besoin de l’URL. Par exemple, les sections mises en surbrillance de cette URL représentent les valeurs dont vous avez besoin pour ouvrir une page de rapport spécifique :

    https<nolink>://app.powerbi.com/groups/me/reports/**df9f0e94-31df-450b-b97f-4461a7e4d300**/**ReportSection11**</code>

* **Ouvrir en mode plein écran (pour les appareils Windows uniquement)**

    Pour les appareils Windows, vous pouvez aussi ajouter le paramètre **openFullScreen** pour ouvrir un rapport spécifique en mode plein écran. L’exemple suivant ouvre une page de rapport en mode plein écran :

    mspbi://app/OpenReport?ReportObjectId=500217de-50f0-4af1-b345-b81027224033&**openFullScreen=true**

* **Ajouter un contexte** (facultatif)

    Vous pouvez également ajouter un contexte à la chaîne. Par la suite, si vous avez besoin de nous contacter, nous pouvons utiliser ce contexte pour filtrer nos données afin de retrouver ce qui concerne votre application. Pour ajouter un contexte, ajoutez le paramètre **context=&lt;nom_application&gt;** au lien :

    Par exemple, l’exemple suivant montre un lien qui comprend un paramètre de contexte : 

    mspbi://app/OpenReport?ReportObjectId=**e684af3a-9e7f-44ee-b679-b9a1c59b5d60**&GroupObjectId=**8cc900cc-7339-467f-8900-fec82d748248**&**context=SlackDeepLink**

## <a name="use-links-inside-power-bi"></a>Utiliser des liens à l’intérieur de Power BI

Dans les applications mobiles Power BI, les liens à l’intérieur de Power BI fonctionnent exactement comme ils le font dans le service Power BI.

Si vous voulez ajouter à votre rapport un lien qui pointe vers un autre élément Power BI, vous pouvez copier l’URL de cet élément à partir de la barre d’adresse du navigateur. Découvrez comment [ajouter un lien hypertexte à une zone de texte](https://docs.microsoft.com/power-bi/service-add-hyperlink-to-text-box).

## <a name="next-steps"></a>Étapes suivantes
Vos commentaires nous aident à développer les futurs processus d’implémentation. N’oubliez pas de voter pour les fonctionnalités que vous aimeriez voir dans les applications mobiles Power BI. 

* [Applications Power BI pour appareils mobiles](mobile-apps-for-mobile-devices.md)
* Suivez @MSPowerBI sur Twitter
* Rejoindre la conversation de la [Communauté Power BI](http://community.powerbi.com/)
* [Qu’est-ce que Power BI ?](../../power-bi-overview.md)
