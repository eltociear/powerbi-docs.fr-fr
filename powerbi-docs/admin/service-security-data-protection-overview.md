---
title: Protection des données dans Power BI
description: Découvrir le fonctionnement de la protection des données dans Power BI
author: paulinbar
manager: rkarlin
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 05/21/2020
ms.author: painbar
LocalizationGroup: Data from files
ms.openlocfilehash: fa969f8f738cf09e9e01e284de8f60e2fd8ce9ab
ms.sourcegitcommit: cd64ddd3a6888253dca3b2e3fe24ed8bb9b66bc6
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/03/2020
ms.locfileid: "84315669"
---
# <a name="data-protection-in-power-bi"></a>Protection des données dans Power BI

Les entreprises modernes ont des réglementations et des exigences métier strictes pour gérer et protéger leurs données sensibles. Pour assurer le contrôle et la visibilité de ces données, Power BI est intégré à Microsoft Information Protection et Microsoft Cloud App Security. Vous pouvez ainsi effectuer les opérations suivantes :
* Utilisez les [étiquettes de sensibilité](https://docs.microsoft.com/microsoft-365/compliance/sensitivity-labels?view=o365-worldwide) de Microsoft Information Protection pour classifier et étiqueter du contenu (tableaux de bord, rapports, jeux de données et dataflows) dans le service Power BI, avec la même taxonomie que celle utilisée pour classifier et protéger les fichiers dans Office 365.
* Appliquez des étiquettes de sensibilité et la protection de Microsoft Information Protection aux données quand elles sont exportées vers des fichiers Excel, PowerPoint ou PDF.
* Utilisez Microsoft Cloud App Security pour superviser les activités dans Power BI, examiner les problèmes de sécurité et protéger le contenu dans Power BI avec le contrôle d’application par accès conditionnel de Microsoft Cloud App Security.

**Remarques importantes**
* L’étiquetage de sensibilité **n’affecte pas** l’accès au contenu dans Power BI : l’accès au contenu dans Power BI est géré seulement par les autorisations de Power BI. Les étiquettes sont visibles, mais les paramètres de chiffrement associés (configurés dans le [Centre de sécurité Microsoft 365](https://security.microsoft.com/) ou dans le [Centre de conformité Microsoft 365](https://compliance.microsoft.com/)) ne sont pas appliqués. Ils sont appliqués seulement aux données exportées vers des fichiers Excel, PowerPoint et PDF.
* Les étiquettes de sensibilité et le chiffrement de fichier **ne sont pas** appliqués aux chemins d’exportation autres que l’exportation vers Excel, PowerPoint et PDF. L’administrateur du locataire Power BI peut désactiver tout ou partie des chemins d’exportation qui ne prennent pas en charge l’application des étiquettes de sensibilité et les paramètres de chiffrement de fichier associés.

## <a name="sensitivity-labels-in-power-bi"></a>Étiquettes de sensibilité dans Power BI

Les étiquettes de sensibilité sont créées et gérées dans le [Centre de sécurité Microsoft 365](https://security.microsoft.com/) ou dans le [Centre de conformité Microsoft 365](https://compliance.microsoft.com/).

Pour accéder aux étiquettes de sensibilité dans un de ces centres, accédez à **Classification > Étiquettes de sensibilité**. Ces étiquettes de sensibilité peuvent être utilisées par plusieurs services Microsoft, comme Azure Information Protection, les applications Office et les services Office 365.

> [!Important]
> Si votre organisation utilise des étiquettes de sensibilité Azure Information Protection, vous devez [les migrer](https://docs.microsoft.com/azure/information-protection/configure-policy-migrate-labels) vers un des services listés précédemment pour que les étiquettes soient utilisées dans Power BI.

> [!NOTE]
> Les étiquettes de sensibilité sont prises en charge seulement pour les locataires dans les clouds publics. Elles ne sont pas prises en charge pour les locataires dans des clouds comme des clouds souverains.

## <a name="how-sensitivity-labels-work-in-power-bi"></a>Fonctionnement des étiquettes de sensibilité dans Power BI

L’application d’une étiquette de sensibilité à un tableau de bord Power BI, un rapport, un jeu de données ou un dataflow est similaire à l’application d’une étiquette à cette ressource, ce qui offre les avantages suivants :
* **Personnalisable** : vous pouvez créer des catégories pour différents niveaux de contenu sensible dans votre organisation, comme Personnel, Public, Général, Confidentiel et Hautement confidentiel.
* **Texte en clair** : étant donné que l’étiquette est en texte clair, les utilisateurs peuvent facilement comprendre comment traiter le contenu en fonction des indications relatives à l’étiquette de sensibilité.
* **Persistante** : une fois qu’une étiquette de sensibilité a été appliquée au contenu, elle accompagne ce contenu quand il est exportée vers des fichiers Excel, PowerPoint et PDF, et devient la base pour l’application de stratégies.

Cela signifie que l’étiquette de sensibilité suit le contenu quand il est exportée vers des fichiers Excel, PowerPoint et PDF, et qu’elle devient la base de l’application des stratégies.

Les administrateurs de locataires Power BI peuvent contrôler [l’exportation vers Excel](service-admin-portal.md#export-to-excel) et [l’exportation vers PowerPoint et PDF](service-admin-portal.md#export-reports-as-powerpoint-presentations-or-pdf-documents) dans le [portail d’administration Power BI](service-admin-portal.md).

## <a name="sensitivity-label-example"></a>Exemple d’étiquette de sensibilité

Voici un exemple rapide de la façon dont fonctionne une étiquette de sensibilité dans Power BI.
1. Dans le service Power BI, une étiquette de sensibilité **Hautement confidentiel** est appliquée à un rapport.

   ![Étiquettes de sensibilité en mode Liste](media/service-security-data-protection-overview/sensitivity-labels-overview-01.png)
   
1. Quand des données sont exportées vers un fichier Excel à partir de ce rapport, l’étiquette de sensibilité et la protection sont appliquées au fichier Excel exporté.

   ![L’étiquette de sensibilité suit le contenu](media/service-security-data-protection-overview/sensitivity-labels-overview-02.png)

Dans les applications Microsoft Office, une étiquette de sensibilité apparaît sous la forme d’une étiquette sur les e-mails ou les documents, comme dans l’image ci-dessus. Vous pouvez également affecter une classification au contenu (comme un autocollant) qui persiste et se déplace avec le contenu quand il est utilisé et partagé dans Power BI. Vous pouvez utiliser cette classification pour générer des rapports d’utilisation et voir les données d’activité de votre contenu sensible. En fonction de ces informations, vous pouvez toujours choisir ultérieurement d’appliquer des paramètres de protection.

## <a name="requirements-for-using-sensitivity-labels-in-power-bi"></a>Exigences pour l’utilisation d’étiquettes de sensibilité dans Power BI

Avant de pouvoir activer et utiliser vos étiquettes de sensibilité dans Power BI, vous devez d’abord respecter les prérequis suivants :
* Vérifiez que les étiquettes de sensibilité ont été définies dans le [Centre de sécurité Microsoft 365](https://security.microsoft.com/) ou dans le [Centre de conformité Microsoft 365](https://compliance.microsoft.com/).
* [Activez les étiquettes de sensibilité](service-security-enable-data-sensitivity-labels.md) dans Power BI.
* Vérifiez que les utilisateurs disposent des [licences appropriées](#licensing).
* Si vous utilisez Microsoft Cloud App Security avec Power BI, veillez à disposer des [licences appropriées](service-security-using-microsoft-cloud-app-security-controls.md#cloud-app-security-licensing).

## <a name="protect-content-using-microsoft-cloud-app-security"></a>Protéger du contenu avec Microsoft Cloud App Security

Vous pouvez protéger du contenu dans Power BI contre les fuites ou violations inattendues à l’aide de Microsoft Cloud App Security. Une fois Microsoft Cloud App Security défini et configuré, les administrateurs de la sécurité peuvent superviser l’accès et l’activité des utilisateurs, effectuer une analyse des risques en temps réel et définir des contrôles spécifiques aux étiquettes.

Par exemple, les organisations peuvent utiliser Microsoft Cloud App Security pour configurer une stratégie qui empêche les utilisateurs de télécharger des données sensibles de Power BI vers des appareils non gérés. Une telle configuration permet aux utilisateurs de rester productifs et de se connecter à Power BI depuis n’importe où, tout en utilisant Microsoft Cloud App Security pour empêcher de compromettre leurs actions, le tout en temps réel.

**Configuration requise**

Pour que vos étiquettes de sensibilité puissent utiliser Microsoft Cloud App Security, les prérequis suivants doivent être respectés :
* Cloud App Security et Azure Information Protection [doivent être activés pour votre locataire](https://docs.microsoft.com/cloud-app-security/azip-integration).
* L’application [ doit être connectée à Microsoft Cloud App Security](https://docs.microsoft.com/cloud-app-security/enable-instant-visibility-protection-and-governance-actions-for-your-apps).

## <a name="licensing"></a>Licences

* L’affichage et l’application d’étiquettes Microsoft Information Protection dans Power BI exigent que les utilisateurs disposent d’une licence Azure Information Protection Premium P1 ou Premium P2. Vous pouvez acheter Microsoft Azure Information Protection en autonome ou par le biais de l’une des suites de licences Microsoft. Pour plus d’informations, consultez les [tarifs Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection/).
* L’affichage et l’application d’étiquettes dans les applications Office sont soumis à des [conditions de licences](https://docs.microsoft.com/microsoft-365/compliance/get-started-with-sensitivity-labels#subscription-and-licensing-requirements-for-sensitivity-labels).
* Pour appliquer des étiquettes à du contenu Power BI, un utilisateur doit disposer d’une licence Power BI Pro en plus d’une des licences Azure Information Protection mentionnées ci-dessus.
* Vous devez disposer des [licences nécessaires pour Microsoft Cloud App Security](https://docs.microsoft.com/power-bi/admin/service-security-using-microsoft-cloud-app-security-controls#microsoft-cloud-app-security-licensing) si vous envisagez de l’utiliser pour protéger du contenu Power BI contre les fuites et les violations indésirables.

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

Cet article a fourni une vue d’ensemble de la protection des données dans Power BI. Les articles suivants fournissent plus de détails sur la protection des données dans Power BI. 

* [Activer les étiquettes de sensibilité des données dans Power BI](service-security-enable-data-sensitivity-labels.md)
* [Appliquer des étiquettes de sensibilité des données dans Power BI](../collaborate-share/service-security-apply-data-sensitivity-labels.md)
* [Utilisation de contrôles Microsoft Cloud App Security dans Power BI](service-security-using-microsoft-cloud-app-security-controls.md)
* [Rapport des métriques de protection des données](service-security-data-protection-metrics-report.md)