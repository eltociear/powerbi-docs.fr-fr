---
title: Sécurité dynamique au niveau des lignes avec le modèle tabulaire Analysis Services
description: Sécurité dynamique au niveau des lignes avec le modèle tabulaire Analysis Services
author: davidiseminger
ms.reviewer: davidi
editor: davidi
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: tutorial
ms.date: 01/17/2020
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 1b90357aa6d8f66612857e8247a8b48dc2c2c369
ms.sourcegitcommit: 02342150eeab52b13a37b7725900eaf84de912bc
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2020
ms.locfileid: "76539591"
---
# <a name="implement-row-level-security-in-an-analysis-services-tabular-model"></a>Implémenter la sécurité au niveau des lignes avec un modèle tabulaire Analysis Services

Les étapes de ce tutoriel montrent, avec un exemple de jeu de données, comment implémenter la [**sécurité au niveau des lignes**](service-admin-rls.md) dans un *modèle tabulaire Analysis Services* et comment l’utiliser dans un rapport Power BI.

* Créer une table de sécurité dans la [base de données AdventureworksDW2012](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks)
* Générer le modèle tabulaire avec les tables de faits et de dimension nécessaires
* Définir des autorisations et rôles d’utilisateur
* Déployer le modèle dans une instance du *modèle tabulaire Analysis Services*
* Générer un rapport Power BI Desktop qui affiche des données adaptées à l’utilisateur accédant au rapport
* Déployer le rapport dans le *service Power BI*
* Créer un tableau de bord basé sur le rapport
* Partager le tableau de bord avec vos collègues

Ce tutoriel utilise la [base de données AdventureworksDW2012](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks).

## <a name="task-1-create-the-user-security-table-and-define-data-relationship"></a>Tâche 1 : Créer la table de sécurité utilisateur et définir la relation de données

Il existe de nombreux articles expliquant comment définir la sécurité dynamique au niveau des lignes avec le modèle *tabulaire SQL Server Analysis Services (SSAS)*. Pour notre exemple, nous utilisons l’article [Implémenter la sécurité dynamique à l’aide des filtres de lignes](/analysis-services/tutorial-tabular-1200/supplemental-lesson-implement-dynamic-security-by-using-row-filters).

Les étapes décrites ici nécessitent l’utilisation de la base de données relationnelle AdventureworksDW2012.

1. Dans AdventureworksDW2012, créez la table `DimUserSecurity` comme indiqué ci-dessous. Vous pouvez utiliser [SQL Server Management Studio (SSMS)](/sql/ssms/download-sql-server-management-studio-ssms) pour créer la table.

   ![Créer la table DimUserSecurity](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/createusersecuritytable.png)

1. Après avoir créé et enregistré la table, vous devez établir la relation entre la colonne `SalesTerritoryID` de la table `DimUserSecurity` et la colonne `SalesTerritoryKey` de la table `DimSalesTerritory`, comme indiqué ci-dessous.

   Dans SSMS, cliquez avec le bouton droit sur **DimUserSecurity**, puis sélectionnez **Conception**. Sélectionnez ensuite **Concepteur de tables** > **Relations...**. Une fois terminé, enregistrez la table.

   ![Relations de clé étrangère](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/createusersecuritytable_keys.png)

1. Ajoutez des utilisateurs à la table. Cliquez avec le bouton droit sur **DimUserSecurity**, puis sélectionnez **Modifier les 200 lignes du haut**. Une fois que vous avez ajouté des utilisateurs, la table `DimUserSecurity` doit ressembler à l’exemple suivant :

   ![Table DimUserSecurity contenant des exemples d’utilisateurs](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/createusersecuritytable_users.png)

   Vous verrez ces utilisateurs lors des prochaines tâches.

1. Ensuite, établissez une *jointure interne* avec la table `DimSalesTerritory`, qui affiche les détails de région associés à l’utilisateur. Le code SQL présenté ici établit la jointure interne, et l’image montre à quoi ressemble ensuite la table.

    ```sql
    select b.SalesTerritoryCountry, b.SalesTerritoryRegion, a.EmployeeID, a.FirstName, a.LastName, a.UserName from [dbo].[DimUserSecurity] as a join [dbo].[DimSalesTerritory] as b on a.[SalesTerritoryID] = b.[SalesTerritoryKey]
    ```

   La table jointe montre qui est responsable de chaque région de vente, grâce à la relation créée à l’étape 2. Par exemple, vous voyez que *Rita Santos* est responsable de l’*Australie*.

## <a name="task-2-create-the-tabular-model-with-facts-and-dimension-tables"></a>Tâche 2 : Créer le modèle tabulaire avec les tables de faits et de dimension

Une fois que votre entrepôt de données relationnelles est en place, vous devez définir votre modèle tabulaire. Vous pouvez créer le modèle à l’aide de [SQL Server Data Tools (SSDT)](/sql/ssdt/sql-server-data-tools). Pour plus d’informations, consultez [Créer un projet de modèle tabulaire](/sql/analysis-services/lesson-1-create-a-new-tabular-model-project).

1. Importez toutes les tables nécessaires dans le modèle, comme indiqué ci-dessous.

    ![Tables importées avec SQL Server Data Tools](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/ssdt_model.png)

1. Définissez ensuite un rôle appelé *SalesTerritoryUsers* avec l’autorisation Lecture. Sélectionnez le menu **Modèle** dans SQL Server Data Tools, puis sélectionnez **Rôles**. Dans le **Gestionnaire de rôles**, sélectionnez **Nouveau**.

1. Sous **Membres** dans le **Gestionnaire de rôles**, ajoutez les utilisateurs que vous avez définis dans la table `DimUserSecurity` lors de la [tâche 1](#task-1-create-the-user-security-table-and-define-data-relationship).

    ![Ajouter des utilisateurs dans le Gestionnaire de rôles](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/rolemanager.png)

1. Maintenant, ajoutez les fonctions appropriées pour les tables `DimSalesTerritory` et `DimUserSecurity`, comme indiqué ci-dessous sous l’onglet **Filtres de lignes**.

    ![Ajouter des fonctions aux filtres de lignes](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/rolemanager_complete.png)

1. La fonction `LOOKUPVALUE` retourne les valeurs d’une colonne où le nom d’utilisateur Windows correspond à celui retourné par la fonction `USERNAME`. Vous pouvez ensuite limiter les requêtes aux emplacements où les valeurs retournées par `LOOKUPVALUE` correspondent à celles de la même table ou d’une table associée. Dans la colonne **Filtre DAX**, tapez la formule suivante :

    ```sql
        =DimSalesTerritory[SalesTerritoryKey]=LOOKUPVALUE(DimUserSecurity[SalesTerritoryID], DimUserSecurity[UserName], USERNAME(), DimUserSecurity[SalesTerritoryID], DimSalesTerritory[SalesTerritoryKey])
    ```

    Dans cette formule, la fonction `LOOKUPVALUE` retourne toutes les valeurs de la colonne `DimUserSecurity[SalesTerritoryID]`, où `DimUserSecurity[UserName]` est le même que le nom d’utilisateur Windows actuellement connecté et où `DimUserSecurity[SalesTerritoryID]` est identique à `DimSalesTerritory[SalesTerritoryKey]`.

    > [!IMPORTANT]
    > Lors de l’utilisation de la sécurité au niveau des lignes, la fonction DAX [USERELATIONSHIP](/dax/userelationship-function-dax) n’est pas prise en charge.

   L’ensemble des valeurs `SalesTerritoryKey` retournées par `LOOKUPVALUE` est ensuite utilisé pour limiter les lignes affichées dans `DimSalesTerritory`. Seules les lignes où la valeur `SalesTerritoryKey` figure dans les ID retournés par la fonction `LOOKUPVALUE` sont affichées.

1. Pour la table `DimUserSecurity`, dans la colonne **Filtre DAX**, ajoutez la formule suivante :

    ```sql
        =FALSE()
    ```

    Cette formule spécifie que toutes les colonnes sont résolues à la valeur `false`, ce qui signifie que les colonnes de la table `DimUserSecurity` ne peuvent pas être interrogées.

Vous devez à présent traiter et déployer le modèle. Pour plus d’informations, consultez [Déployer](/sql/analysis-services/lesson-13-deploy).

## <a name="task-3-add-data-sources-within-your-on-premises-data-gateway"></a>Tâche 3 : Ajouter des sources de données dans la passerelle de données locale

Une fois que votre modèle tabulaire est déployé et prêt à être utilisé, vous devez ajouter une connexion de source de données à votre serveur tabulaire Analysis Services local.

1. Pour permettre au service Power BI d’accéder à votre service d’analyse local, une [passerelle de données locale](service-gateway-onprem.md) doit être installée et configurée dans votre environnement.

1. Une fois que la passerelle de données locale est correctement configurée, vous devez créer une connexion à la source de données pour votre instance tabulaire *Analysis Services*. Pour plus d’informations, consultez [Gérer votre source de données - Analysis Services](service-gateway-enterprise-manage-ssas.md).

   ![Créer une connexion à la source de données](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/pbi_gateway.png)

Au terme de cette procédure, la passerelle est configurée et prête à interagir avec votre source de données Analysis Services locale.

## <a name="task-4-create-report-based-on-analysis-services-tabular-model-using-power-bi-desktop"></a>Tâche 4 : Créer un rapport basé sur le modèle tabulaire Analysis Services à l’aide de Power BI Desktop

1. Démarrez Power BI Desktop et sélectionnez **Obtenir les données** > **Base de données**.

1. Dans la liste des sources de données, sélectionnez **Base de données SQL Server Analysis Services**, puis **Connexion**.

   ![Se connecter à la base de données SQL Server Analysis Services](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/getdata.png)

1. Renseignez les détails de l’instance tabulaire Analysis Services et sélectionnez **Connexion directe**. Sélectionnez ensuite **OK**.
  
   ![Détails de l’instance Analysis Services](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/getdata_connectlive.png)

   Dans Power BI, la sécurité dynamique fonctionne uniquement avec une connexion directe.

1. Vous pouvez constater que le modèle déployé est dans l’instance Analysis Services. Sélectionnez le modèle en question, puis **OK**.

   Power BI Desktop affiche maintenant tous les champs disponibles, à droite du canevas dans le volet **Champs**.

1. Dans le volet **Champs**, sélectionnez la mesure **SalesAmount** dans la table **FactInternetSales** et la dimension **SalesTerritoryRegion** dans la table **SalesTerritory**.

1. Pour que ce rapport reste simple, nous n’ajouterons pas de colonnes pour le moment. Pour avoir une représentation plus significative des données, définissez la visualisation sur **Graphique en anneau**.

   ![Visualisation sous forme de graphique en anneau](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/donut_chart.png)

1. Une fois que le rapport est prêt, vous pouvez le publier directement sur le portail Power BI. Dans le ruban **Accueil** de Power BI Desktop, sélectionnez **Publier**.

## <a name="task-5-create-and-share-a-dashboard"></a>Tâche 5 : Créer et partager un tableau de bord

Vous avez créé le rapport et vous l’avez publié sur le service **Power BI**. Maintenant, vous pouvez utiliser l’exemple créé lors des étapes précédentes pour illustrer le scénario de sécurité du modèle.

Avec son rôle de *Responsable des ventes*, l’utilisatrice Grace peut voir les données de toutes les différentes régions de vente. Grace crée ce rapport et le publie sur le service Power BI. Ce rapport a été créé lors des tâches précédentes.

Grace crée ensuite un tableau de bord basé sur ce rapport dans le service Power BI, qu’elle nomme *TabularDynamicSec*. Comme le montre l’image suivante, Grace peut voir les données relatives à toutes les régions de vente.

   ![Tableau de bord du service Power BI](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/donut_chart_1.png)

Grace partage maintenant le tableau de bord avec sa collègue Rita, qui est responsable des ventes dans la région Australie.

   ![Partager un tableau de bord Power BI](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/pbi_dashboard.png)

Quand Rita se connecte au service Power BI et affiche le tableau de bord partagé créé par Grace, elle voit uniquement les ventes de la région Australie.

Félicitations ! Le service Power BI montre la sécurité dynamique au niveau des lignes définie dans le modèle tabulaire Analysis Services local. Power BI utilise la propriété `EffectiveUserName` pour envoyer les informations d’identification de l’utilisateur Power BI actuel à la source de données locale en vue d’exécuter les requêtes.

## <a name="task-6-understand-what-happens-behind-the-scenes"></a>Tâche 6 : Comprendre ce qui se passe en arrière-plan

Cette tâche suppose que vous êtes familiarisé avec [SQL Server Profiler](/sql/tools/sql-server-profiler/sql-server-profiler), car vous devez capturer une trace SQL Server Profiler sur votre instance tabulaire SSAS locale.

La session est initialisée dès que l’utilisatrice Rita accède au tableau de bord dans le service Power BI. Vous pouvez voir que le rôle **salesterritoryusers** prend effet immédiatement avec le nom d’utilisateur en vigueur **<EffectiveUserName>rita@contoso.com</EffectiveUserName>**

       <PropertyList><Catalog>DefinedSalesTabular</Catalog><Timeout>600</Timeout><Content>SchemaData</Content><Format>Tabular</Format><AxisFormat>TupleFormat</AxisFormat><BeginRange>-1</BeginRange><EndRange>-1</EndRange><ShowHiddenCubes>false</ShowHiddenCubes><VisualMode>0</VisualMode><DbpropMsmdFlattened2>true</DbpropMsmdFlattened2><SspropInitAppName>PowerBI</SspropInitAppName><SecuredCellValue>0</SecuredCellValue><ImpactAnalysis>false</ImpactAnalysis><SQLQueryMode>Calculated</SQLQueryMode><ClientProcessID>6408</ClientProcessID><Cube>Model</Cube><ReturnCellProperties>true</ReturnCellProperties><CommitTimeout>0</CommitTimeout><ForceCommitTimeout>0</ForceCommitTimeout><ExecutionMode>Execute</ExecutionMode><RealTimeOlap>false</RealTimeOlap><MdxMissingMemberMode>Default</MdxMissingMemberMode><DisablePrefetchFacts>false</DisablePrefetchFacts><UpdateIsolationLevel>2</UpdateIsolationLevel><DbpropMsmdOptimizeResponse>0</DbpropMsmdOptimizeResponse><ResponseEncoding>Default</ResponseEncoding><DirectQueryMode>Default</DirectQueryMode><DbpropMsmdActivityID>4ea2a372-dd2f-4edd-a8ca-1b909b4165b5</DbpropMsmdActivityID><DbpropMsmdRequestID>2313cf77-b881-015d-e6da-eda9846d42db</DbpropMsmdRequestID><LocaleIdentifier>1033</LocaleIdentifier><EffectiveUserName>rita@contoso.com</EffectiveUserName></PropertyList>

Sur la base de la requête du nom d’utilisateur en vigueur, Analysis Services convertit la requête en informations d’identification `contoso\rita` après interrogation de l’annuaire Active Directory local. Après avoir obtenu les informations d’identification, Analysis Services retourne les données que l’utilisateur est autorisé à voir et auxquelles il est autorisé à accéder.

Si d’autres activités ont lieu dans le tableau de bord, avec SQL Server Profiler, une requête spécifique est renvoyée vers le modèle tabulaire Analysis Services en tant que requête DAX. Par exemple, si Rita accède au rapport sous-jacent à partir du tableau de bord, la requête suivante est exécutée.

   ![Requête DAX renvoyée au modèle Analysis Services](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/profiler1.png)

Vous pouvez également voir ci-dessous la requête DAX exécutée pour remplir les données du rapport.
   
   ```sql
   EVALUATE
     ROW(
       "SumEmployeeKey", CALCULATE(SUM(Employee[EmployeeKey]))
     )
   
   <PropertyList xmlns="urn:schemas-microsoft-com:xml-analysis">``
             <Catalog>DefinedSalesTabular</Catalog>
             <Cube>Model</Cube>
             <SspropInitAppName>PowerBI</SspropInitAppName>
             <EffectiveUserName>rita@contoso.com</EffectiveUserName>
             <LocaleIdentifier>1033</LocaleIdentifier>
             <ClientProcessID>6408</ClientProcessID>
             <Format>Tabular</Format>
             <Content>SchemaData</Content>
             <Timeout>600</Timeout>
             <DbpropMsmdRequestID>8510d758-f07b-a025-8fb3-a0540189ff79</DbpropMsmdRequestID>
             <DbPropMsmdActivityID>f2dbe8a3-ef51-4d70-a879-5f02a502b2c3</DbPropMsmdActivityID>
             <ReturnCellProperties>true</ReturnCellProperties>
             <DbpropMsmdFlattened2>true</DbpropMsmdFlattened2>
             <DbpropMsmdActivityID>f2dbe8a3-ef51-4d70-a879-5f02a502b2c3</DbpropMsmdActivityID>
           </PropertyList>
   ```

## <a name="considerations"></a>Considérations

* La sécurité locale au niveau des lignes dans Power BI est disponible uniquement avec une connexion directe.

* Une fois le modèle traité, les modifications apportées aux données sont immédiatement affichées pour les utilisateurs qui accèdent au rapport avec une connexion active à partir du service Power BI.

