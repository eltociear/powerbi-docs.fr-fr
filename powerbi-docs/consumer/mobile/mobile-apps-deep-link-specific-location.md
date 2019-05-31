---
title: Créer un lien vers un emplacement spécifique dans les applications mobiles Power BI
description: Apprenez à créer un lien ciblé qui pointe vers un rapport, une vignette ou un tableau de bord spécifique dans l’application mobile Power BI à l’aide d’un URI (Uniform Resource Identifier).
author: mshenhav
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-mobile
ms.topic: conceptual
ms.date: 04/24/2019
ms.author: mshenhav
ms.openlocfilehash: 4e09b10e38b018f8e5572343b343a243ace3bf81
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "64906527"
---
# <a name="create-a-link-to-a-specific-location-in-the-power-bi-mobile-apps"></a>Créer un lien vers un emplacement spécifique dans les applications mobiles Power BI
Vous pouvez utiliser des liens pour accéder directement à des éléments spécifiques dans Power BI : Rapport, tableau de bord et vignette.

Il existe principalement deux scénarios d’utilisation des liens dans Power BI Mobile : 

* Pour ouvrir Power BI à partir de **en dehors de l’application**et se retrouver sur un contenu spécifique (tableau de bord/rapports/application). Il s’agit généralement un scénario d’intégration, lorsque vous souhaitez ouvrir Power BI Mobile à partir de l’autre application. 
* Pour **accédez** à l’intérieur de Power BI. Il s’agit généralement lorsque vous souhaitez créer une navigation personnalisée dans Power BI.


## <a name="use-links-from-outside-of-power-bi"></a>Utiliser des liens à partir en dehors de Power BI
Lorsque vous utilisez un lien à partir en dehors de l’application Power BI, vous souhaitez vous assurer qu’il sera ouvert par l’application, et si l’application n’est pas installée sur l’appareil, puis propose à l’utilisateur pour l’installer. Nous avons créé un format de lien spécial pour prendre en charge exactement qui. Ce format de lien, permet de garantir que l’appareil est à l’aide de l’application pour ouvrir le lien, et si l’application n’est pas installée sur l’appareil, il propose de l’utilisateur pour accéder à la banque pour l’obtenir.

Le lien doit commencer par les éléments suivants  
```html
https://app.powerbi.com/Redirect?[**QUERYPARAMS**]
```

> [!IMPORTANT]
> Si votre contenu est hébergé dans le centre de données spéciaux tels que le gouvernement, Chine, etc. Le lien doit commencer par l’adresse appropriée de Power BI, comme `app.powerbigov.us` ou `app.powerbi.cn`.   
>


Le **requête PARAMS** sont :
* **action** (obligatoire) = OpenApp / OpenDashboard / OpenTile / OpenReport
* **appId** = si vous souhaitez ouvrir un rapport ou un tableau de bord qui font partie d’une application 
* **groupObjectId** = si vous souhaitez ouvrir un rapport ou un tableau de bord qui font partie de l’espace de travail (mais pas mon espace de travail)
* **dashboardObjectId** = ID d’objet de tableau de bord (si l’action est OpenDashboard ou OpenTile)
* **reportObjectId** = ID d’objet de rapport (si l’action est OpenReport)
* **tileObjectId** = ID d’objet de vignette (si l’action est OpenTile)
* **reportPage** = si vous souhaitez ouvrir la section de rapport spécifique (si l’action est OpenReport)
* **ctId** = élément ID d’organisation (pertinente pour le scénario de B2B. Cela peut être omis si l’élément appartient à l’organisation de l’utilisateur).

**Exemples :**

* Lien d’ouvrir l’application 
  ```html
  https://app.powerbi.com/Redirect?action=OpenApp&appId=appidguid&ctid=organizationid
  ```

* Tableau de bord ouvert qui fait partie d’une application 
  ```html
  https://app.powerbi.com/Redirect?action=OpenDashboard&appId=**appidguid**&dashboardObjectId=**dashboardidguid**&ctid=**organizationid**
  ```

* Ouvrir le rapport qui fait partie d’un espace de travail
  ```html
  https://app.powerbi.com/Redirect?Action=OpenReport&reportObjectId=**reportidguid**&groupObjectId=**groupidguid**&reportPage=**ReportSectionName**
  ```

### <a name="how-to-get-the-right-link-format"></a>Comment obtenir le format de lien de droite

#### <a name="links-of-apps-and-items-in-app"></a>Liens des applications et des éléments dans l’application

Pour **applications, rapports et tableau de bord qui font partie d’une application**, pour obtenir le lien le plus simple consiste à accéder à l’espace de travail d’application et choisissez « Application de la mise à jour ». Cette opération ouvre l’expérience « Publier l’application », et dans l’onglet accès, vous trouverez un **liens** section. Développant que section et vous verrez la liste de l’application et les liens de tout son contenu peut être utilisé pour y accéder directement.

![Liens de l’application de publication de Power BI ](./media/mobile-apps-links/mobile-link-copy-app-links.png)

#### <a name="links-of-items-not-in-app"></a>Liens d’éléments pas dans l’application 

Pour les rapports et tableaux de bord qui ne font pas partie d’une application, vous devez extraire l’ID de l’URL de l’élément.

Par exemple, pour rechercher le caractère de 36 **tableau de bord** ID d’objet, accédez au tableau de bord spécifique dans le service Power BI 

```html
https://app.powerbi.com/groups/me/dashboards/**dashboard guid comes here**?ctid=**organization id comes here**`
```

Pour rechercher le caractère de 36 **rapport** ID d’objet, accédez au rapport spécifique dans le service Power BI.
Il s’agit d’un exemple de rapport à partir de « Mon espace de travail »

```html
https://app.powerbi.com/groups/me/reports/**report guid comes here**/ReportSection3?ctid=**organization id comes here**`
```
L’URL ci-dessus contient également de page de rapport spécifique **« ReportSection3 »** .

Il s’agit d’un exemple d’un rapport à partir d’un espace de travail (pas mon espace de travail)

```html
https://app.powerbi.com/groups/**groupid comes here**/reports/**reportid comes here**/ReportSection1?ctid=**organizationid comes here**
```

## <a name="use-links-inside-power-bi"></a>Utilisez les liens à l’intérieur de Power BI

Liens à l’intérieur de Power BI fonctionnent dans les applications mobiles exactement comme dans le Service Power BI.

Si vous souhaitez ajouter un lien à votre rapport qui pointe vers un autre élément de Power BI, vous pouvez simplement copier cette URL de l’élément à partir de la barre d’adresses du navigateur. En savoir plus sur [comment ajouter un lien hypertexte à une zone de texte dans un rapport](https://docs.microsoft.com/power-bi/service-add-hyperlink-to-text-box).

## <a name="use-report-url-with-filter"></a>Utilisez l’URL de rapport avec filtre
Même en tant que service Power BI, applications mobiles Power BI prennent également en charge les URL de rapport qui contient un paramètre de requête de filtre. Vous pouvez ouvrir un rapport dans application Power BI Mobile et filtrer en état spécifique. Par exemple, cette URL ouvre le rapport de ventes et la filtrer par secteur

```html
https://app.powerbi.com/groups/me/reports/**report guid comes here**/ReportSection3?ctid=**organization id comes here**&filter=Store/Territory eq 'NC'
```

En savoir plus sur [comment générer param de requête pour filtrer des rapports](https://docs.microsoft.com/power-bi/service-url-filters).

## <a name="next-steps"></a>Étapes suivantes
Vos commentaires nous aident à développer les futurs processus d’implémentation. N’oubliez pas de voter pour les fonctionnalités que vous aimeriez voir dans les applications mobiles Power BI. 

* [Applications Power BI pour appareils mobiles](mobile-apps-for-mobile-devices.md)
* Suivez @MSPowerBI sur Twitter
* Rejoindre la conversation de la [Communauté Power BI](http://community.powerbi.com/)
* [Qu’est-ce que Power BI ?](../../power-bi-overview.md)

