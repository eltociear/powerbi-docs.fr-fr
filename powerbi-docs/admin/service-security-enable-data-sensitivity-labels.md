---
title: Activer les étiquettes de sensibilité des données dans Power BI
description: Découvrir comment activer les étiquettes de sensibilité des données dans Power BI
author: paulinbar
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 05/23/2020
ms.author: painbar
LocalizationGroup: Data from files
ms.openlocfilehash: ba1cacfa930bcc0ed51234dea13639420ac8fab7
ms.sourcegitcommit: cd64ddd3a6888253dca3b2e3fe24ed8bb9b66bc6
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/03/2020
ms.locfileid: "84315646"
---
# <a name="enable-data-sensitivity-labels-in-power-bi"></a>Activer les étiquettes de sensibilité des données dans Power BI

Pour que [les étiquettes de sensibilité des données de Microsoft Information Protection](https://docs.microsoft.com/microsoft-365/compliance/sensitivity-labels) puissent être utilisées dans Power BI, elles doivent être activées sur le locataire. Cet article explique comment les administrateurs de locataire Power BI procèdent pour cela. Pour une vue d’ensemble des étiquettes de sensibilité des données dans Power BI, consultez [Protection des données dans Power BI](service-security-data-protection-overview.md). Pour plus d’informations sur l’application des étiquettes de sensibilité dans Power BI, consultez [Application d’étiquettes de sensibilité](../collaborate-share/service-security-apply-data-sensitivity-labels.md) 

Quand les étiquettes de sensibilité sont activées :

* Des utilisateurs et des groupes de sécurité spécifiés d’une organisation peuvent classifier et [appliquer des étiquettes de sensibilité](../collaborate-share/service-security-apply-data-sensitivity-labels.md) à leurs tableaux de bord, rapports, jeux de données et dataflows Power BI.
* Tous les membres de l’organisation peuvent voir ces étiquettes.

L’activation des étiquettes de sensibilité des données nécessite une licence Azure Information Protection. Pour plus d’informations, consultez [Gestion des licences](service-security-data-protection-overview.md#licensing).

## <a name="enable-data-sensitivity-labels"></a>Activer les étiquettes de sensibilité des données

Accédez au **Portail d’administration** de Power BI, ouvrez le volet **Paramètres du client** et recherchez la section **Information Protection**.

![Rechercher la section Information Protection](media/service-security-enable-data-sensitivity-labels/enable-data-sensitivity-labels-01.png)

Dans la section **Information Protection**, effectuez les étapes suivantes :
1. Ouvrez **Autoriser les utilisateurs à appliquer des étiquettes de confidentialité pour le contenu Power BI**.
1. Activez le bouton bascule.
1. Définissez qui peut appliquer et changer les étiquettes de sensibilité dans les ressources Power BI. Par défaut, toutes les personnes de votre organisation peuvent appliquer des étiquettes de sensibilité. Toutefois, vous pouvez choisir d’activer le paramétrage des étiquettes de sensibilité uniquement pour des utilisateurs ou des groupes de sécurité spécifiques. Si vous avez sélectionné l’ensemble de l’organisation ou des groupes de sécurité particuliers, vous pouvez exclure des sous-ensembles spécifiques d’utilisateurs ou de groupes de sécurité.
   
   * Quand les étiquettes de sensibilité sont activées pour l’ensemble de l’organisation, les exceptions sont généralement des groupes de sécurité.
   * Quand les étiquettes de sensibilité sont activées uniquement pour des utilisateurs ou des groupes de sécurité spécifiques, les exceptions sont généralement des utilisateurs spécifiques.  
    Cette approche permet d’empêcher certains utilisateurs d’appliquer des étiquettes de sensibilité dans Power BI, même s’ils appartiennent à un groupe disposant des autorisations nécessaires.

1. Appuyez sur **Appliquer**.

![Activer les étiquettes de sensibilité](media/service-security-enable-data-sensitivity-labels/enable-data-sensitivity-labels-02.png)

> [!IMPORTANT]
> Seuls les utilisateurs Power BI Pro qui disposent d’autorisations *créer* et *modifier* sur la ressource et qui font partie du groupe de sécurité approprié défini dans cette section peuvent définir et modifier les étiquettes de sensibilité. Les utilisateurs qui ne font pas partie de ce groupe ne peuvent pas définir ou modifier l’étiquette.  

## <a name="troubleshooting"></a>Résolution des problèmes

Power BI utilise les étiquettes de sensibilité Microsoft Information Protection. Par conséquent, si un message d’erreur s’affiche lors d’une tentative d’activation des étiquettes de sensibilité, cela peut être dû à l’une des raisons suivantes :

* Vous ne disposez pas de [licence](service-security-data-protection-overview.md#licensing) Azure Information Protection.
* Les étiquettes de sensibilité n’ont pas été migrées vers la version de Microsoft Information Protection prise en charge par Power BI. Découvrez des informations supplémentaires sur la [migration des étiquettes de sensibilité](https://docs.microsoft.com/azure/information-protection/configure-policy-migrate-labels).
* Aucune étiquette de sensibilité Microsoft Information Protection n’a été définie dans l’organisation. Notez que pour être utilisable, une étiquette doit faire partie d’une stratégie publiée. [Apprenez-en davantage sur les étiquettes de sensibilité](https://docs.microsoft.com/Office365/SecurityCompliance/sensitivity-labels). Vous pouvez également visiter le [Centre de sécurité et de conformité Microsoft](https://sip.protection.office.com/sensitivity?flight=EnableMIPLabels) pour savoir comment définir des étiquettes et publier des stratégies pour votre organisation.

## <a name="considerations-and-limitations"></a>Considérations et limitations

La liste suivante présente certaines limitations des étiquettes de sensibilité dans Power BI :

**Général**
* Les étiquettes de sensibilité ne peuvent être appliquées que sur les tableaux de bord, les rapports, les jeux de données et les dataflows. Les étiquettes de sensibilité ne sont pas disponibles pour les [rapports paginés](../paginated-reports/report-builder-power-bi.md) et les classeurs.
* Les étiquettes de sensibilité sur les ressources Power BI sont visibles dans les vues Liste d’espaces de travail, Traçabilité, Favoris et Applications ; elles ne sont actuellement pas visibles dans la vue Partagé avec moi. Notez, toutefois, qu’une étiquette appliquée à une ressource Power BI, même si elle n’est pas visible, est toujours conservée sur les données exportées vers des fichiers Excel, PowerPoint et PDF.
* Les étiquettes de sensibilité sont uniquement prises en charge pour les locataires dans le cloud global (public). Les étiquettes de sensibilité ne sont pas prises en charge pour les locataires dans les autres clouds.
* Les étiquettes de sensibilité de données ne sont pas prises en charge pour les applications de modèle. Les étiquettes de sensibilité définies par le créateur de l’application de modèle sont supprimées lors de l’extraction et de l’installation de l’application, et les étiquettes de sensibilité ajoutées aux artefacts dans un modèle d’application installé par le consommateur de l’application sont perdues (réinitialisées sur Nothing (pas de sélection)) lorsque l’application est mise à jour.
* Power BI ne prend pas en charge les étiquettes de sensibilité des types de protection [Ne pas transférer](https://docs.microsoft.com/microsoft-365/compliance/encryption-sensitivity-labels?view=o365-worldwide#let-users-assign-permissions), [Défini par l’utilisateur](https://docs.microsoft.com/microsoft-365/compliance/encryption-sensitivity-labels?view=o365-worldwide#let-users-assign-permissions) et [HYOK](https://docs.microsoft.com/azure/information-protection/configure-adrms-restrictions). Les types de protection Ne pas transférer et Défini par l’utilisateur font référence aux étiquettes définies dans le [Centre de sécurité Microsoft 365](https://security.microsoft.com/) ou dans le [Centre de conformité Microsoft 365](https://compliance.microsoft.com/).
* Il n’est pas recommandé d’autoriser les utilisateurs à appliquer des étiquettes parentes dans Power BI. Si une étiquette parente est appliquée au contenu, l’exportation de données à partir de ce contenu vers un fichier (Excel, PowerPoint et PDF) échouera. Consultez [Sous-étiquettes (étiquettes de regroupement)](https://docs.microsoft.com/microsoft-365/compliance/sensitivity-labels?view=o365-worldwide#sublabels-grouping-labels).

**Export**
* Les contrôles d’étiquette et de protection sont appliqués seulement quand les données sont exportées vers des fichiers Excel, PowerPoint et PDF. L’étiquette et la protection ne sont pas appliquées quand les données sont exportées vers des fichiers .csv ou .pbix, Analyser dans Excel ou tout autre chemin d’exportation.
* L’application d’une étiquette de sensibilité et d’une protection à un fichier exporté n’ajoute de marquage de contenu au fichier. Cependant, si l’étiquette est configurée pour appliquer des marquages de contenu, ceux-ci sont automatiquement appliqués par le client d’étiquetage unifié Azure Information Protection quand le fichier est ouvert dans des applications de poste de travail Office. Les marquages de contenu ne sont pas appliqués automatiquement quand vous utilisez l’étiquetage intégré pour les applications de bureau, mobiles ou web. Pour plus d’informations, consultez [Lorsque les applications Office appliquent le marquage de contenu et le chiffrement](https://docs.microsoft.com/microsoft-365/compliance/sensitivity-labels-office-apps?view=o365-worldwide#when-office-apps-apply-content-marking-and-encryption).
* Un utilisateur qui exporte un fichier à partir de Power BI dispose d’autorisations pour accéder à ce fichier et le modifier en fonction des paramètres d’étiquette de sensibilité. L’utilisateur qui exporte les données n’obtient pas d’autorisations de propriétaire sur le fichier.
* L’exportation échoue si une étiquette ne peut pas être appliquée quand les données sont exportées vers un fichier. Pour vérifier si l’exportation a échoué parce que l’étiquette n’a pas pu être appliquée, cliquez sur le nom du rapport ou du tableau de bord au centre de la barre de titre et vérifiez si le message « Impossible de charger l’étiquette de confidentialité » apparaît dans la liste déroulante des informations qui s’ouvre. Ceci peut se produire si l’étiquette appliquée a été supprimée ou si sa publication a été annulée par l’administrateur de la sécurité, ou à la suite d’un problème système temporaire.

## <a name="next-steps"></a>Étapes suivantes

L’objectif de cet article était d’expliquer comment activer les étiquettes de sensibilité des données dans Power BI. Les articles suivants fournissent plus de détails sur la protection des données dans Power BI. 

* [Vue d’ensemble de la protection des données dans Power BI](service-security-data-protection-overview.md)
* [Appliquer des étiquettes de sensibilité des données dans Power BI](../collaborate-share/service-security-apply-data-sensitivity-labels.md)
* [Utilisation de contrôles Microsoft Cloud App Security dans Power BI](service-security-using-microsoft-cloud-app-security-controls.md)
* [Rapport des métriques de protection des données](service-security-data-protection-metrics-report.md)