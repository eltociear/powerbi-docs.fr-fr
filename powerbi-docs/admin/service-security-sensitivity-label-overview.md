---
title: Étiquettes de sensibilité Microsoft Information Protection dans Power BI
description: Découvrez comment les étiquettes de sensibilité de Microsoft Information Protection fonctionnent dans Power BI
author: paulinbar
ms.author: painbar
manager: rkarlin
ms.service: powerbi
ms.subservice: powerbi-eim
ms.topic: how-to
ms.date: 08/16/2020
LocalizationGroup: Data from files
ms.openlocfilehash: 27d650fbe9415c2e771931801f5b573770eda5b2
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2020
ms.locfileid: "96412135"
---
# <a name="sensitivity-labels-in-power-bi"></a>Étiquettes de sensibilité dans Power BI

Cet article décrit les fonctionnalités des étiquettes de sensibilité de Microsoft Information Protection dans Power BI.

Pour plus d’informations sur l’activation des étiquettes de confidentialité sur un locataire, et notamment les conditions de licence et les prérequis, consultez [Activation des étiquettes de confidentialité des données dans Power BI](service-security-enable-data-sensitivity-labels.md).

Pour plus d’informations sur la façon d’appliquer des étiquettes de sensibilité à des rapports, des tableaux de bord, des jeux de données et des dataflows Power BI, consultez [Guide pratique pour appliquer des étiquettes de sensibilité dans Power BI](./service-security-apply-data-sensitivity-labels.md).

## <a name="introduction"></a>Introduction

Les étiquettes de sensibilité de Microsoft Information Protection offrent aux utilisateurs un moyen simple de classifier du contenu critique dans Power BI sans compromettre la productivité ni la possibilité de collaborer.

Les étiquettes de confidentialité peuvent être appliquées à des jeux de données, à des rapports, à des tableaux de bord et à des dataflows. Quand les données étiquetées quittent Power BI, que ce soit par exportation dans des fichiers Excel, PowerPoint ou PDF, ou suivant d’autres scénarios d’exportation pris en charge (par exemple, Analyser dans Excel ou tableaux croisés dynamiques de connexion active dans Excel), Power BI applique automatiquement l’étiquette au fichier exporté et le protège en fonction des paramètres de chiffrement de fichier de l’étiquette. Vos données sensibles restent ainsi protégées, quel que soit l’endroit où elles se trouvent.

Les étiquettes de confidentialité appliquées à des rapports, tableaux de bord, jeux de données et dataflows sont visibles à de nombreux endroits du service Power BI. Les étiquettes de sensibilité sur les rapports et les tableaux de bord sont également visibles dans les applications mobiles Power BI sur iOS et Android, et dans les visuels incorporés.

Un [rapport des métriques de protection](service-security-data-protection-metrics-report.md) disponible dans le portail d’administration Power BI donne aux administrateurs Power BI une visibilité complète sur les données sensibles du locataire Power BI. Par ailleurs, les journaux d’audit Power BI comportent des informations relatives aux étiquettes de confidentialité concernant diverses activités (par exemple, l’application, la suppression et la modification des étiquettes, ainsi que la visualisation des rapports, des tableaux de bord, etc.), ce qui donne aux administrateurs Power BI et aux administrateurs de la sécurité une visibilité sur la consommation des données sensibles à des fins de monitoring et d’examen des alertes de sécurité.

## <a name="important-considerations"></a>Considérations importantes

L’étiquetage de sensibilité **n’affecte pas** l’accès au contenu dans Power BI : l’accès au contenu dans Power BI est géré seulement par les autorisations de Power BI. Les étiquettes sont visibles, mais les paramètres de chiffrement associés (configurés dans le [Centre de sécurité Microsoft 365](https://security.microsoft.com/) ou dans le [Centre de conformité Microsoft 365](https://compliance.microsoft.com/)) ne sont pas appliqués. Ils ne s’appliquent qu’aux données qui quittent Power BI par exportation dans des fichiers Excel, PowerPoint ou PDF, ou suivant l’un des autres chemins d’exportation pris en charge.

Ni les étiquettes de confidentialité, ni le chiffrement de fichier **ne s’appliquent** dans les chemins d’exportation non pris en charge. L’administrateur Power BI peut bloquer l’exportation à partir de chemins d’exportation non pris en charge :

>[!NOTE]
> Les utilisateurs qui disposent d’une autorisation d’accès à un rapport sont autorisés à accéder à l’ensemble du jeu de données sous-jacent, sauf si la [sécurité au niveau des lignes (SNL)](./service-admin-rls.md) limite leur accès. Les auteurs de rapports peuvent classifier et étiqueter les rapports en utilisant des étiquettes de confidentialité. Si l’étiquette de sensibilité a des paramètres de protection, Power BI les applique quand les données des rapports sont exportées dans des fichiers Excel, PowerPoint ou PDF. Seuls les utilisateurs autorisés peuvent ouvrir des fichiers protégés.

## <a name="supported-export-paths"></a>Chemins d’exportation pris en charge
L’application des étiquettes de confidentialité et de la protection associée aux données qui quittent Power BI est actuellement prise en charge pour les chemins d’exportation suivants :
* Exportation dans des fichiers Excel, PowerPoint et PDF
* Analyser dans Excel à partir du service Power BI, qui déclenche le téléchargement d’un fichier Excel avec une connexion active à un jeu de données Power BI
* Tableau croisé dynamique dans Excel avec une connexion active à un jeu de données Power BI, pour les utilisateurs disposant de M365 E3 (ou version ultérieure) 



## <a name="how-sensitivity-labels-work-in-power-bi"></a>Fonctionnement des étiquettes de sensibilité dans Power BI

L’application d’une étiquette de sensibilité à un tableau de bord Power BI, un rapport, un jeu de données ou un dataflow est similaire à l’application d’une balise à cette ressource, ce qui offre les avantages suivants :
* **Personnalisable** : vous pouvez créer des catégories pour différents niveaux de contenu sensible dans votre organisation, comme Personnel, Public, Général, Confidentiel et Hautement confidentiel.
* **Texte en clair** : étant donné que l’étiquette est en texte clair, les utilisateurs peuvent facilement comprendre comment traiter le contenu en fonction des indications relatives à l’étiquette de sensibilité.
* **Persistante** : une fois qu’une étiquette de sensibilité a été appliquée au contenu, elle accompagne ce contenu quand il est exportée vers des fichiers Excel, PowerPoint et PDF, et devient la base pour l’application de stratégies.

Voici un exemple rapide de la façon dont fonctionnent les étiquettes de sensibilité dans Power BI. L’image ci-dessous montre comment une étiquette de sensibilité est appliquée à un rapport dans le service Power BI, puis comment les données du rapport sont exportées vers un fichier Excel, et enfin comment l’étiquette de sensibilité et ses protections persistent dans le fichier exporté.

![Image GIF animée montrant l’application et la persistance des étiquettes de sensibilité](media/service-security-sensitivity-label-overview/ApplyLabelandProtection.gif)

Les étiquettes de confidentialité appliquées au contenu sont conservées et suivent le contenu au fil de ses utilisations et partages dans Power BI. Vous pouvez utiliser l’étiquetage pour générer des rapports d’utilisation et voir les données d’activité de votre contenu sensible.

## <a name="sensitivity-label-inheritance-upon-creation-of-new-content"></a>Héritage des étiquettes de sensibilité lors de la création d’un nouveau contenu

Quand de nouveaux rapports et tableaux de bord sont créés dans le service Power BI, ils héritent automatiquement de l’étiquette de sensibilité précédemment appliquée sur le jeu de données ou le rapport parent. Par exemple, un nouveau rapport créé sur un jeu de données qui a une étiquette de sensibilité « Hautement confidentiel » reçoit automatiquement cette étiquette « Hautement confidentiel ».

L’illustration suivante montre comment l’étiquette de sensibilité d’un jeu de données est automatiquement appliquée à un rapport basé sur le jeu de données.

![Image GIF animée montrant l’héritage des étiquettes de sensibilité](media/service-security-sensitivity-label-overview/InheritanceUponCreation.gif)

>[!NOTE]
>Si pour une raison quelconque, l’étiquette de sensibilité ne peut pas être appliquée sur le nouveau rapport ou tableau de bord, Power BI ne bloque **pas** la création du nouvel élément.

## <a name="sensitivity-labels-and-protection-on-exported-data"></a>Étiquettes de sensibilité et protection sur les données exportées

Quand des données sont exportées depuis Power BI vers des fichiers Excel, PowerPoint ou PDF, Power BI applique automatiquement une étiquette de sensibilité sur le fichier exporté et le protège en fonction des paramètres de chiffrement de fichier de l’étiquette. De cette façon, vos données sensibles restent protégées, quel que soit l’endroit où elles se trouvent.

Un utilisateur qui exporte un fichier à partir de Power BI dispose d’autorisations pour accéder à ce fichier et le modifier en fonction des paramètres d’étiquette de sensibilité ; il ne reçoit pas les autorisations de propriétaire sur le fichier.

Les étiquettes de sensibilité et la protection ne sont pas appliquées quand les données sont exportées vers des fichiers .csv ou .pbix ou d’autres chemins d’accès d’exportation.

L’application d’une étiquette de sensibilité et d’une protection à un fichier exporté n’ajoute pas de marquage du contenu au fichier. Cependant, si l’étiquette est configurée pour appliquer des marquages de contenu, ceux-ci sont automatiquement appliqués par le client d’étiquetage unifié Azure Information Protection quand le fichier est ouvert dans des applications de poste de travail Office. Les marquages de contenu ne sont pas appliqués automatiquement quand vous utilisez l’étiquetage intégré pour les applications de bureau, mobiles ou web. Pour plus d’informations, consultez [Lorsque les applications Office appliquent le marquage de contenu et le chiffrement](/microsoft-365/compliance/sensitivity-labels-office-apps#when-office-apps-apply-content-marking-and-encryption).

L’exportation échoue si une étiquette ne peut pas être appliquée quand les données sont exportées vers un fichier. Pour vérifier si l’exportation a échoué parce que l’étiquette n’a pas pu être appliquée, cliquez sur le nom du rapport ou du tableau de bord au centre de la barre de titre et vérifiez si le message « Impossible de charger l’étiquette de confidentialité » apparaît dans la liste déroulante des informations qui s’ouvre. Ceci peut se produire à la suite d’un problème système temporaire, ou si l’étiquette appliquée a été supprimée ou si sa publication a été annulée par l’administrateur de la sécurité.

## <a name="sensitivity-label-inheritance-in-analyze-in-excel"></a>Héritage des étiquettes de sensibilité dans Analyser dans Excel

Lorsque vous créez un tableau croisé dynamique dans Excel avec une connexion active à un jeu de données Power BI (vous pouvez le faire à partir de Power BI à l’aide de [Analyser dans Excel](../collaborate-share/service-analyze-in-excel.md) ou de [Excel](https://support.microsoft.com/office/create-a-pivottable-from-power-bi-datasets-31444a04-9c38-4dd7-9a45-22848c666884?ui=en-US&rs=en-US&ad=US)), l’étiquette de sensibilité du jeu de données est héritée et appliquée à votre fichier Excel, ainsi que toute protection associée. Si, par la suite, l’étiquette du jeu de données devient plus restrictive, l’étiquette appliquée sur le fichier Excel lié est automatiquement mise à jour lors de l’actualisation des données.

![Capture d’écran d’Excel montrant l’étiquette de sensibilité héritée du jeu de données via la connexion active.](media/service-security-sensitivity-label-overview/live-connection-inheritance.png)
 
Les étiquettes de sensibilité dans Excel qui ont été définies manuellement ne sont pas automatiquement remplacées par l’étiquette de sensibilité du jeu de données. Au lieu de cela, une bannière vous avertit que le jeu de données a une étiquette de sensibilité et vous recommande de l’appliquer.

>[!NOTE]
>Si l’étiquette de sensibilité du jeu de données est moins restrictive que l’étiquette de sensibilité du fichier Excel, aucun héritage ou mise à jour d’étiquette n’a lieu. Un fichier Excel n’hérite jamais d’une étiquette de sensibilité moins restrictive.


## <a name="sensitivity-label-persistence-in-embedded-reports-and-dashboards"></a>Persistance des étiquettes de sensibilité dans les rapports et tableaux de bord incorporés

Vous pouvez incorporer des rapports, des tableaux de bord et des visuels Power BI dans des applications métier, comme Microsoft Teams et SharePoint, ou sur le site web d’une organisation. Quand vous incorporez un visuel, un rapport ou un tableau de bord auquel une étiquette de sensibilité est appliquée, l’étiquette de sensibilité est visible dans la vue incorporée et l’étiquette et sa protection persistent quand les données sont exportées vers Excel.

![Capture d’écran d’un rapport incorporé dans SharePoint Online](media/service-security-sensitivity-label-overview/embedded-report-sensitivity-label.png)

Les scénarios d’incorporation suivants sont pris en charge :
* [Incorporer pour votre organisation](../developer/embedded/embed-sample-for-your-organization.md)
* Applications Microsoft 365 (par exemple [Teams](../collaborate-share/service-embed-report-microsoft-teams.md) et [SharePoint](../collaborate-share/service-embed-report-spo.md))
* [Sécuriser l’incorporation d’URL](../collaborate-share/service-embed-secure.md) (incorporation à partir du service Power BI) 

## <a name="sensitivity-labels-in-the-power-bi-mobile-apps"></a>Étiquettes de sensibilité dans les applications mobiles Power BI

Les étiquettes de sensibilité peuvent être visualisées sur les rapports et les tableaux de bord dans les applications mobiles Power BI. Une icône près du nom du rapport ou du tableau de bord indique qu’il a une étiquette de sensibilité, et le type d’étiquette et sa description se trouvent dans la zone d’informations du rapport ou du tableau de bord.

![Capture d’écran d’une étiquette de sensibilité dans une application mobile](media/service-security-sensitivity-label-overview/mobile-app-sensitivity-label2.png)

## <a name="supported-clouds"></a>Clouds pris en charge
Les étiquettes de confidentialité sont prises en charge seulement pour les locataires dans des clouds (publics) mondiaux ; elles ne sont pas prises en charge dans des clouds comme les clouds nationaux.

## <a name="licensing-and-requirements"></a>Licences et configuration requise

Consultez [Licences et configuration requise](service-security-enable-data-sensitivity-labels.md#licensing-and-requirements).

## <a name="sensitivity-label-creation-and-management"></a>Création et gestion des étiquettes de sensibilité

Les étiquettes de sensibilité sont créées et gérées dans le [Centre de sécurité Microsoft 365](https://security.microsoft.com/) ou dans le [Centre de conformité Microsoft 365](https://compliance.microsoft.com/).

Pour accéder aux étiquettes de sensibilité dans un de ces centres, accédez à **Classification > Étiquettes de sensibilité**. Ces étiquettes de sensibilité peuvent être utilisées par plusieurs services Microsoft, comme Azure Information Protection, les applications Office et les services Office 365.

>[!Important]
> Si votre organisation utilise des étiquettes de sensibilité Azure Information Protection, vous devez [les migrer](/azure/information-protection/configure-policy-migrate-labels) vers un des services listés précédemment pour que les étiquettes soient utilisées dans Power BI.

## <a name="limitations"></a>Limites

La liste suivante présente certaines limitations des étiquettes de sensibilité dans Power BI :

* Les étiquettes de sensibilité peuvent être appliquées seulement sur des tableaux de bord, des rapports, des jeux de données et des dataflows. Les étiquettes de sensibilité ne sont pas disponibles pour les [rapports paginés](../paginated-reports/report-builder-power-bi.md) et les classeurs.
* Les étiquettes de sensibilité sur les ressources Power BI sont visibles dans les vues Liste d’espaces de travail, Traçabilité, Favoris et Applications ; elles ne sont actuellement pas visibles dans la vue Partagé avec moi. Notez, toutefois, qu’une étiquette appliquée à une ressource Power BI, même si elle n’est pas visible, est toujours conservée sur les données exportées vers des fichiers Excel, PowerPoint et PDF.
* Les étiquettes de sensibilité de données ne sont pas prises en charge pour les applications de modèle. Les étiquettes de sensibilité définies par le créateur de l’application de modèle sont supprimées lors de l’extraction et de l’installation de l’application, et les étiquettes de sensibilité ajoutées aux artefacts dans un modèle d’application installé par le consommateur de l’application sont perdues (réinitialisées sur Nothing (pas de sélection)) lorsque l’application est mise à jour.
* Power BI ne prend pas en charge les étiquettes de sensibilité des types de protection [Ne pas transférer](/microsoft-365/compliance/encryption-sensitivity-labels#let-users-assign-permissions), [Défini par l’utilisateur](/microsoft-365/compliance/encryption-sensitivity-labels#let-users-assign-permissions) et [HYOK](/azure/information-protection/configure-adrms-restrictions). Les types de protection Ne pas transférer et Défini par l’utilisateur font référence aux étiquettes définies dans le [Centre de sécurité Microsoft 365](https://security.microsoft.com/) ou dans le [Centre de conformité Microsoft 365](https://compliance.microsoft.com/).
* Il n’est pas recommandé d’autoriser les utilisateurs à appliquer des étiquettes parentes dans Power BI (une étiquette n’est considérée comme une étiquette parente que si elle comporte des sous-étiquettes). Si une étiquette parent est appliquée au contenu, l’exportation de données à partir de ce contenu vers un fichier (Excel, PowerPoint et PDF) échouera. Consultez [Sous-étiquettes (étiquettes de regroupement)](/microsoft-365/compliance/sensitivity-labels#sublabels-grouping-labels).

## <a name="next-steps"></a>Étapes suivantes

Cet article a fourni une vue d’ensemble de la protection des données dans Power BI. Les articles suivants fournissent plus de détails sur la protection des données dans Power BI. 

* [Activer les étiquettes de sensibilité dans Power BI](service-security-enable-data-sensitivity-labels.md)
* [Guide pratique pour appliquer des étiquettes de sensibilité dans Power BI](service-security-apply-data-sensitivity-labels.md)
* [Utilisation de contrôles Microsoft Cloud App Security dans Power BI](service-security-using-microsoft-cloud-app-security-controls.md)
* [Rapport des métriques de protection](service-security-data-protection-metrics-report.md)