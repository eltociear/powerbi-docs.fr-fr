---
title: Se connecter aux données d’Azure Consumption Insights dans Power BI Desktop (bêta)
description: Se connecter aisément à Azure pour obtenir des informations sur la consommation et l’utilisation à l’aide de Power BI Desktop
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 04/24/2018
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 59723d4c8e241781b7f29773ea182cd5b075e0c2
ms.sourcegitcommit: 80d6b45eb84243e801b60b9038b9bff77c30d5c8
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34288196"
---
# <a name="connect-to-azure-consumption-insights-in-power-bi-desktop-beta"></a>Se connecter à Azure Consumption Insights dans Power BI Desktop (bêta)
Le connecteur **Azure Consumption Insights** vous permet d’utiliser **Power BI Desktop** pour vous connecter à Azure afin d’obtenir des données et informations détaillées sur l’utilisation des services Azure par votre organisation. Vous pouvez également créer des mesures, des colonnes personnalisées et des visuels afin de rapporter et partager l’utilisation d’Azure par votre organisation. Le connecteur **Azure Consumption Insights** étant publié en version bêta, il est susceptible de changer.

![](media/desktop-connect-azure-consumption-insights/azure-consumption-insights_01.png)

Cet article explique comment se connecter avec le connecteur **Azure Consumption Insights** pour obtenir des données et comment migrer depuis le connecteur Azure Enterprise. Il présente également un mappage des *colonnes de détails d’utilisation* disponibles dans l’API **ACI** (Azure Consumption Insights).

## <a name="connect-to-azure-consumption-insights"></a>Se connecter à Azure Consumption Insights
Pour pouvoir vous connecter à l’aide du connecteur **Azure Consumption Insights**, vous devez avoir accès aux fonctionnalités d’entreprise au sein du portail Azure.

Pour vous connecter avec le connecteur **Azure Consumption Insights**, dans le ruban **Accueil** de **Power BI Desktop**, sélectionnez **Obtenir des données**. Sélectionnez **Services en ligne** dans les catégories à gauche pour afficher **Microsoft Azure Consumption Insights (bêta)**. Sélectionnez **Se connecter**.

![](media/desktop-connect-azure-consumption-insights/azure-consumption-insights_01b.png)

Dans la boîte de dialogue qui s’affiche, entrez votre *Numéro d’inscription*.

![](media/desktop-connect-azure-consumption-insights/azure-consumption-insights_02.png)

* Vous pouvez trouver celui-ci sur le portail [Azure Enterprise Portal](https://ea.azure.com), à l’emplacement montré dans l’image suivante :
  
  ![](media/desktop-connect-azure-consumption-insights/azure-consumption-insights_08.png)
  
  Cette version du connecteur prend en charge seulement les inscriptions d’entreprise depuis https://ea.azure.com. Les inscriptions en Chine ne sont pas prises en charge actuellement.

Ensuite, entrez votre *Clé d’accès* pour établir la connexion.

![](media/desktop-connect-azure-consumption-insights/azure-consumption-insights_03.png)

* Votre clé d’accès pour l’inscription est disponible sur le portail [Microsoft Azure Enterprise Portal](https://ea.azure.com).
  
  ![](media/desktop-connect-azure-consumption-insights/azure-consumption-insights_09.png)

Après que avez entré votre *Clé d’accès* et sélectionné **Se connecter**, une fenêtre du **Navigateur** affiche les quatre tables à votre disposition : *Résumé*, *Utilisation*, *Grille tarifaire* et *Place de marché*. Vous pouvez activer une case à cocher en regard d’une table pour afficher un aperçu. Vous pouvez sélectionner une ou plusieurs tables en cochant la case en regard de leur nom, puis sélectionner **Charger**.

![](media/desktop-connect-azure-consumption-insights/azure-consumption-insights_04.png)

> [!NOTE]
> Les tableaux *Résumé* et *Grille tarifaire* sont disponibles seulement pour la clé d’API au niveau inscription. De plus, les données de ces tables sont, par défaut, celles du mois en cours pour l’*Utilisation* et la *Grille tarifaire*. Les tables *Résumé* et *Place de marché* ne sont pas limitées au mois en cours.
> 
> 

Lorsque vous sélectionnez **Charger**, les données sont chargées dans **Power BI Desktop**.

![](media/desktop-connect-azure-consumption-insights/azure-consumption-insights_05.png)

Une fois les données sélectionnées chargées, les tables et les champs que vous avez sélectionnés sont visibles dans le volet **Champs**.

![](media/desktop-connect-azure-consumption-insights/azure-consumption-insights_06.png)

## <a name="using-azure-consumption-insights"></a>Utilisation d’Azure Consumption Insights
Pour pouvoir utiliser le connecteur **Azure Consumption Insights**, vous devez avoir accès aux fonctionnalités d’entreprise au sein du portail Azure.

Une fois les données chargées à l’aide du connecteur **Azure Consumption Insights**, vous pouvez créer vos propres mesures et colonnes personnalisées à l’aide de l’**Éditeur de requête**, ainsi que générer des visuels, rapports et tableaux de bord à partager dans le **service Power BI**.

Azure comprend également une collection d’exemples de requêtes personnalisées que vous pouvez récupérer à l’aide d’une requête vide. Pour cela, dans le ruban **Accueil** de **Power BI Desktop**, sélectionnez la flèche déroulante **Obtenir des données**, puis choisissez **Requête vide**. Vous pouvez également faire cela dans l’**Éditeur de requête** en cliquant avec le bouton droit sur le volet**Requêtes** à gauche, puis en sélectionnant **Nouvelle requête > Requête vide** dans le menu qui s’affiche.

Dans la **Barre de formule**, tapez ce qui suit :

    = MicrosoftAzureConsumptionInsights.Contents

Une collection d’exemples s’affiche, comme illustré dans l’image suivante :

![](media/desktop-connect-azure-consumption-insights/azure-consumption-insights_07.png)

Lors de la manipulation de rapports et de la création de requêtes, utilisez ce qui suit :

* Pour définir le nombre de mois à partir de la date actuelle, utilisez *numberOfMonth*.
  * Utilisez une valeur comprise entre 1 et 36 pour représenter le nombre de mois que vous voulez importer à partir de la date actuelle. Nous vous recommandons de ne pas récupérer plus de 12 mois de données afin d’éviter les seuils en lien avec les contraintes d’importation et le volume autorisé de données pour les requêtes dans Power BI.
* Pour définir une période de mois dans une fenêtre de temps historique, utilisez *startBillingDataWindow* et *endBillingDataWindow*.
* N’utilisez *pas* *numberOfMonth* avec *startBillingDataWindow* ou *endBillingDataWindow*.

## <a name="migrating-from-the-azure-enterprise-connector"></a>Migration à partir du connecteur Azure Enterprise
Certains clients ont créé des visuels l’aide du *connecteur Azure Enterprise (bêta)*, qui sera finalement supprimé et remplacé par le connecteur **Azure Consumption Insights**. Le connecteur **Azure Consumption Insights** intègre les fonctionnalités et améliorations suivantes :

* Sources de données supplémentaires disponibles pour la *Synthèse de solde* et les *Achats sur la Place de marché*.
* Paramètres nouveaux et avancés, tels que *startBillingDataWindow* et *endBillingDataWindow*.
* Performances et réactivité améliorées.

Pour aider les clients à opérer la transition vers le nouveau connecteur **Azure Consumption Insights**, ainsi qu’à préserver leur travail de création de tableaux de bord ou de rapports personnalisés, les étapes suivantes montrent comment migrer vers le nouveau connecteur.

### <a name="step-1-connect-to-azure-using-the-new-connector"></a>Étape 1 : se connecter à Azure à l’aide du nouveau connecteur
La première étape consiste à se connecter à l’aide du connecteur **Azure Consumption Insights** décrit en détail précédemment dans cet article. Dans le cadre de cette étape, dans le ruban **Accueil** de **Power BI Desktop**, sélectionnez **Obtenir des données > Requête vide**.

### <a name="step-2-use-the-advanced-editor-to-create-a-query"></a>Étape 2 : utiliser l’Éditeur avancé pour créer une requête
Dans l’**Éditeur de requête**, dans la section **Requête** du ruban **Accueil**, sélectionnez **Éditeur avancé**. Dans la fenêtre **Éditeur avancé** qui apparaît, entrez la requête suivante :

    let    
        enrollmentNumber = "100",
        optionalParameters = [ numberOfMonth = 6, dataType="DetailCharges" ],
        data = MicrosoftAzureConsumptionInsights.Contents(enrollmentNumber, optionalParameters)   
    in     
        data

![](media/desktop-connect-azure-consumption-insights/azure-consumption-insights_10.png)

Bien entendu, vous devez remplacer la valeur *enrollmentNumber* par votre propre numéro d’inscription, que vous pouvez obtenir sur le portail [Azure Enterprise Portal](https://ea.azure.com). Le paramètre *numberOfMonth* spécifie le nombre de mois de données sur lesquels vous voulez revenir à partir de la date en cours. Utilisez zéro (0) pour le mois en cours.

Quand vous sélectionnez **Terminé** dans la fenêtre **Éditeur avancé**, l’aperçu est actualisé pour afficher les données de la plage de mois spécifiée dans la table. Sélectionnez **Fermer & appliquer**, puis appuyez sur Entrée.

### <a name="step-3-move-measures-and-custom-columns-to-the-new-report"></a>Étape 3 : déplacer les mesures et les colonnes personnalisées vers le nouveau rapport
Vous devez à présent déplacer les colonnes personnalisées ou les mesures que vous avez créées vers la nouvelle table des détails. Voici comment procéder.

1. Ouvrez l’application Bloc-notes (ou un autre éditeur de texte).
2. Sélectionnez la mesure à déplacer, puis copiez le texte du champ *Formule* et collez-le dans l’application Bloc-notes.
   
   ![](media/desktop-connect-azure-consumption-insights/azure-consumption-insights_11.png)
3. Remplacez *Query1* par le nom de la table des détails d’origine.
4. Créez de nouvelles mesures et des colonnes personnalisées dans votre table en cliquant avec le bouton droit sur la table et en choisissant **Nouvelle mesure**, puis coupez et collez toutes les mesures et colonnes de votre magasin.

### <a name="step-4-re-link-tables-that-had-relationships"></a>Étape 4 : lier de nouveau les tables qui avaient des relations
De nombreux tableaux de bord comportent des tables supplémentaires qui sont utilisées pour la recherche ou le filtrage, telles que des tables de dates ou des tables destinées à des projets personnalisés. Le rétablissement de ces relations résout la plupart des problèmes restants. Voici comment procéder.

- Sous l’onglet **Modélisation** de **Power BI Desktop**, sélectionnez **Gérer les relations** pour afficher une fenêtre permettant de gérer les relations au sein du modèle. Liez de nouveau vos tables, en fonction des besoins.
   
    ![](media/desktop-connect-azure-consumption-insights/azure-consumption-insights_12.png)

### <a name="step-5-verify-your-visuals-and-adjust-field-formatting-as-needed"></a>Étape 5 : vérifier vos visuels et ajuster la mise en forme des champs au besoin
À ce stade, la plupart de vos visuels, tables et vues détaillées d’origine devraient fonctionner comme prévu. Toutefois, quelques ajustements mineurs de la mise en forme peuvent être nécessaires pour obtenir l’aspect souhaité. Prendre un peu de temps pour jeter un coup d’œil à chacun de vos tableaux de bord et visuels afin de vous assurer qu’ils s’affichent comme vous le souhaitez.

## <a name="using-the-azure-consumption-and-insights-aci-api-to-get-consumption-data"></a>Utilisation de l’API ACI (Azure Consumption Insights) pour obtenir des données de consommation
Azure fournit également l’[ **API ACI (Azure Consumption Insights)**](https://azure.microsoft.com/blog/announcing-general-availability-of-consumption-and-charge-apis-for-enterprise-azure-customers/). L’API ACI vous permet de créer vos propres solutions personnalisées pour la collecte et la visualisation d’informations, ainsi que la création de rapports.

### <a name="mapping-names-and-usage-details-between-the-portal-the-connector-and-the-api"></a>Mappage des noms et des détails d’utilisation entre le portail, le connecteur et l’API
Les colonnes et les noms des détails sur le portail Azure sont similaires dans l’API et le connecteur, mais pas toujours rigoureusement identiques. Par souci de clarté, le tableau ci-dessous fournit un mappage entre l’API, le connecteur et les colonnes que vous voyez sur le portail Azure. Il spécifie également si des colonnes sont obsolètes. Pour plus d’informations et des définitions de ces termes, consultez le [dictionnaire des données de facturation d’Azure](https://docs.microsoft.com/azure/billing/billing-enterprise-api-usage-detail).

| Connecteur ACI / ContentPack ColumnName | Nom de colonne dans l’API ACI | Nom de colonne dans EA | Obsolète / présent pour la compatibilité descendante |
| --- | --- | --- | --- |
| AccountName |accountName |Account Name |Non |
| AccountId |accountId | |Oui |
| AcccountOwnerId |accountOwnerEmail |AccountOwnerId |Non |
| AdditionalInfo |additionalInfo |AdditionalInfo |Non |
| AdditionalInfold | | |Oui |
| Consumed Quantity |consumedQuantity |Consumed Quantity |Non |
| Consumed Service |consumedService |Consumed Service |Non |
| ConsumedServiceId |consumedServiceId | |Oui |
| Cost |cost |ExtendedCost |Non |
| Cost Center |costCenter |Cost Center |Non |
| Date |date |Date |Non |
| Jour | |Jour |Non |
| DepartmentName |departmentName |Department Name |Non |
| DepartmentID |departmentId | |Oui |
| Instance ID | | |Oui |
| InstanceId |instanceId |Instance ID |Non |
| Emplacement | | |Oui |
| Meter Category |meterCategory |Meter Category |Non |
| Meter ID | | |Oui |
| Meter Name |meterName |Meter Name |Non |
| Meter Region |meterRegion |Meter Region |Non |
| Meter Sub-Category |meterSubCategory |Meter Sub-Category |Non |
| MeterId |meterId |Meter ID |Non |
| Month | |Month |Non |
| Product |product |Product |Non |
| ProductId |productId | |Oui |
| Groupe de ressources |resourceGroup |Groupe de ressources |Non |
| Resource Location |resourceLocation |Resource Location |Non |
| ResourceGroupId | | |Oui |
| ResourceLocationId |resourceLocationId | |Oui |
| ResourceRate |resourceRate |ResourceRate |Non |
| ServiceAdministratorId |serviceAdministratorId |ServiceAdministratorId |Non |
| ServiceInfo1 |serviceInfo1 |ServiceInfo1 |Non |
| ServiceInfo1Id | | |Oui |
| ServiceInfo2 |serviceInfo2 |ServiceInfo2 |Non |
| ServiceInfo2Id | | |Oui |
| Store Service Identifier |storeServiceIdentifier |Store Service Identifier |Non |
| StoreServiceIdentifierId | | |Oui |
| Nom de l’abonnement |subscriptionName |Nom de l’abonnement |Non |
| Balises |tags |Balises |Non |
| TagsId | | |Oui |
| Unit Of Measure |unitOfMeasure |Unit Of Measure |Non |
| Year | |Year |Non |
| SubscriptionId |subscriptionId |SubscriptionId |Oui |
| SubscriptionGuid |subscriptionGuid |SubscriptionGuid |Non |

## <a name="next-steps"></a>Étapes suivantes
Vous pouvez connecter toutes sortes de données à l’aide de Power BI Desktop. Pour plus d’informations sur les sources de données, consultez les ressources suivantes :

* [Prise en main de Power BI Desktop](desktop-getting-started.md)
* [Sources de données dans Power BI Desktop](desktop-data-sources.md)
* [Mettre en forme et combiner des données dans Power BI Desktop](desktop-shape-and-combine-data.md)
* [Se connecter à des classeurs Excel dans Power BI Desktop](desktop-connect-excel.md)   
* [Entrer des données directement dans Power BI Desktop](desktop-enter-data-directly-into-desktop.md)   

