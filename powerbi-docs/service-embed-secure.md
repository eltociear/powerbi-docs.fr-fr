---
title: Incorporer un rapport dans un site web ou portail sécurisé
description: Power BI incorpore fonctionnalité permet aux utilisateurs de facilement et en toute sécurité incorporer des rapports dans les portails web interne.
author: rkarlin
ms.author: rkarlin
manager: kfile
ms.reviewer: lukaszp
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 05/20/2019
LocalizationGroup: Share your work
ms.openlocfilehash: bf9d7bcdf6ddaf7d0063843a5314233989b2dadd
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66222236"
---
# <a name="embed-a-report-in-a-secure-portal-or-website"></a>Incorporer un rapport dans un site web ou portail sécurisé

Avec la nouvelle **Embed** option pour Power BI les rapports, vous pouvez facilement et en toute sécurité incorporer des rapports dans les portails web interne. Ces portails peuvent être **nuage** ou **hébergées en local**, telles que SharePoint 2019. Rapports incorporés respectent toutes les autorisations et les données de sécurité des éléments de via [au niveau des lignes (RLS) de sécurité](service-admin-rls.md). Ils fournissent sans code incorporation dans n’importe quel portail qui accepte une URL ou un iFrame. 

Le **Embed** option prend en charge [filtres URL](service-url-filters.md) et paramètres d’URL. Il vous permet d’intégrer les portails à l’aide d’une approche peu de code nécessitant uniquement HTML et JavaScript une connaissance élémentaire.

## <a name="how-to-embed-power-bi-reports-into-portals"></a>Comment **incorporer** des rapports Power BI dans des portails

1. La nouvelle option **Incorporer** est disponible dans le menu **Fichier** pour les rapports dans le service Power BI.

    ![Option déroulante Incorporer sécurisée](media/service-embed-secure/secure-embed-drop-down-menu.png)

2. Sélectionnez le **Embed** option pour ouvrir une boîte de dialogue qui fournit un lien et un iFrame, vous pouvez utiliser pour incorporer le rapport en toute sécurité.

    ![Boîte de dialogue de l’option Incorporer](media/service-embed-secure/secure-embed-code-dialog.png)

3. Si un utilisateur ouvre une URL de rapport directement, ou un incorporé dans un portail web, accès aux rapports requiert l’authentification. L’écran suivant s’affiche si un utilisateur a non signé dans Power BI dans sa session de navigateur. Lorsqu’ils sélectionnent **connexion**, une nouvelle fenêtre de navigateur ou un onglet peut ouvrir. Demandez-lui de vérifier bloqueurs de fenêtres publicitaires si elles n’invités à vous connecter.

    ![Connectez-vous pour voir ce rapport](media/service-embed-secure/secure-embed-sign-in.png)

4. Une fois que l’utilisateur connecté, le rapport s’ouvre, affichant les données et ce qui permet la navigation entre les pages et le paramètre de filtre. Seuls les utilisateurs qui ont l’autorisation view peuvent afficher le rapport sur Power BI. Tous les [au niveau des lignes (RLS) de sécurité](service-admin-rls.md) règles sont également appliquées. Enfin, l’utilisateur doit disposer d’une licence correcte. Il doit avoir une licence Power BI Pro, ou le rapport doit être dans un espace de travail qui se trouve dans une capacité Power BI Premium. L’utilisateur doit se connecter chaque fois qu’ils ouvrent une nouvelle fenêtre de navigateur. Toutefois, une fois connecté, autres rapports chargent automatiquement.

    ![Incorporer un rapport](media/service-embed-secure/secure-embed-report.png)

5. Lorsque vous utilisez un iFrame, vous devrez peut-être modifier le **hauteur** et **largeur** pour qu’il tient dans votre page de portail web.

    ![Définir la hauteur et la largeur](media/service-embed-secure/secure-embed-size.png)

## <a name="granting-report-access"></a>Octroi d’accès aux rapports

Le **Embed** option automatiquement ne permet pas aux utilisateurs d’afficher le rapport. Afficher les autorisations sont définies dans le service Power BI.

Dans le service Power BI, vous pouvez partager des rapports incorporés avec les utilisateurs qui requièrent un accès. Si vous utilisez un groupe Office 365, vous pouvez répertorier l’utilisateur comme membre d’un espace de travail d’application. Pour plus d’informations, consultez Comment [gérer votre espace de travail d’application dans Power BI et Office 365](service-manage-app-workspace-in-power-bi-and-office-365.md).

## <a name="licensing"></a>Licensing

Pour afficher le rapport incorporé, les utilisateurs doivent soit une licence Power BI Pro ou le contenu doit se trouver dans un espace de travail qui se trouve dans un [capacité Power BI Premium (EM ou référence (SKU) P)](service-admin-premium-purchase.md).

## <a name="customize-your-embed-experience-using-url-settings"></a>Personnaliser votre expérience d’incorporation à l’aide des paramètres d’URL

Vous pouvez personnaliser l’expérience utilisateur à l’aide des paramètres d’entrée de l’URL d’incorporation. Dans l’iFrame fourni, vous pouvez mettre à jour l’URL **src** paramètres.

| Propriété  | Description  |  |  |  |
|--------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---|---|---|
| pageName  | Vous pouvez utiliser la **pageName** paramètre de chaîne pour définir quelle page de rapport pour ouvrir de requête. Vous pouvez trouver cette valeur à la fin de l’URL rapport lorsque vous affichez un rapport dans le service Power BI, comme indiqué ci-dessous. |  |  |  |
| Filtres d’URL  | Vous pouvez utiliser [filtres URL](service-url-filters.md) dans l’URL d’incorporation que vous avez reçu à partir de l’interface utilisateur de Power BI pour filtrer le contenu incorporé. Ainsi, vous pouvez créer des intégrations avec peu de code et des connaissances de base de HTML et de JavaScript.  |  |  |  |

## <a name="set-which-page-opens-for-an-embedded-report"></a>Jeu de page qui s’ouvre pour un rapport incorporé 

Vous pouvez trouver la **pageName** valeur à la fin de l’URL rapport lorsque vous affichez un rapport dans le service Power BI.

1. Ouvrir le rapport à partir du service Power BI dans votre navigateur web et copiez l’URL de barre d’adresse.

    ![Section du rapport](media/service-embed-secure/secure-embed-report-section.png)

2. Ajoutez le paramètre **pageName** à l’URL.

    ![Ajouter pageName](media/service-embed-secure/secure-embed-append-page-name.png)

## <a name="filter-report-content-using-url-filters"></a>Filtrer le contenu du rapport à l’aide de filtres d’URL 

Vous pouvez utiliser [filtres URL](service-url-filters.md) pour proposer des vues différentes de rapport. Par exemple, l’URL ci-dessous filtre le rapport pour afficher les données pour le secteur de l’énergie.

L’utilisation de la combinaison de **pageName** et de [filtres d’URL](service-url-filters.md) peut être très puissante. Vous pouvez créer des expériences à l’aide de code HTML et JavaScript de base.

Par exemple, Voici un bouton que vous pouvez ajouter à une page HTML :

```html
<button class="textLarge" onclick='show("ReportSection", "Energy");' style="display: inline-block;">Show Energy</button>
```

Lorsque sélectionné, le bouton appelle une fonction pour mettre à jour de l’iFrame avec une URL de mise à jour, ce qui inclut le filtre du secteur de l’énergie.

```javascript
function show(pageName, filterValue)

{

var newUrl = baseUrl + "&pageName=" + pageName;

if(null != filterValue && "" != filterValue)

{

newUrl += "&$filter=Industries/Industry eq '" + filterValue + "'";

}

//Assumes there’s an iFrame on the page with id=”iFrame”

var report = document.getElementById("iFrame")

report.src = newUrl;

}
```

![Filtrer](media/service-embed-secure/secure-embed-filter.png)

Vous pouvez ajouter autant de boutons que vous le souhaitez pour créer une expérience personnalisée avec peu de code. 

## <a name="considerations-and-limitations"></a>Considérations et limitations

* Ne prend pas en charge les utilisateurs invités externes avec Azure B2B.

* L’incorporation sécurisée fonctionne pour les rapports publiés sur le service Power BI.

* L’utilisateur doit se connecter pour afficher le rapport chaque fois qu’ils ouvrent une nouvelle fenêtre de navigateur.

* Certains navigateurs vous obligent à actualiser la page après la connexion, en particulier lorsque vous utilisez des modes InPrivate ou Incognito.

* Pour obtenir une expérience d’authentification unique, utilisez l’objet incorporé dans l’option SharePoint Online ou générer une intégration personnalisée à l’aide de la [utilisateur possède les données](developer/embed-sample-for-your-organization.md) l’incorporation de méthode. 

* La fonctionnalité d’authentification automatique fournie avec l’option **Incorporer** ne fonctionne pas avec l’API JavaScript Power BI. Pour l’API JavaScript de Power BI, utilisez le [utilisateur possède les données](developer/embed-sample-for-your-organization.md) l’incorporation de méthode. 

## <a name="next-steps"></a>Étapes suivantes

* [Moyens de partager votre travail dans Power BI](service-how-to-collaborate-distribute-dashboards-reports.md)

* [Filtrer un rapport à l’aide des paramètres de chaîne de requête dans l’URL](service-url-filters.md)

* [Incorporer avec le composant WebPart rapport dans SharePoint Online](service-embed-report-spo.md)

* [Publier sur le Web à partir de Power BI](service-publish-to-web.md)