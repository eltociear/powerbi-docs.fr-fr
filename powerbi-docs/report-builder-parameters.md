---
title: Paramètres de rapport dans le Générateur de rapports Power BI
description: Cette rubrique décrit les utilisations courantes des paramètres de rapport du Générateur de rapports paginés Power BI, les propriétés que vous pouvez définir et plus encore.
ms.service: powerbi
ms.subservice: report-builder
ms.custom: ''
ms.topic: conceptual
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.date: 06/06/2019
ms.openlocfilehash: 21fe08c2cba004a6aff77eae12303d0181ab56ec
ms.sourcegitcommit: 797bb40f691384cb1b23dd08c1634f672b4a82bb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/12/2019
ms.locfileid: "66840530"
---
# <a name="report-parameters-in-power-bi-report-builder"></a>Paramètres de rapport dans le Générateur de rapports Power BI

Cette rubrique décrit les utilisations courantes des paramètres de rapport du Générateur de rapports paginés Power BI, les propriétés que vous pouvez définir et plus encore. Les paramètres de rapport vous permettent de contrôler les données du rapport, de relier des rapports connexes et de modifier la présentation du rapport. Vous pouvez utiliser des paramètres de rapport dans les rapports paginés que vous créez dans le Générateur de rapports.

## <a name="bkmk_Common_Uses_for_Parameters"></a> Utilisations courantes des paramètres

 Voici quelques-unes des méthodes les plus courantes pour utiliser les paramètres.  
  
**Contrôler les données des rapports paginés**
  
- Filtrez les données de rapport paginé au niveau de la source de données en écrivant des requêtes de jeu de données qui contiennent des variables.  
  
- Autorisez les utilisateurs à spécifier des valeurs pour personnaliser les données dans un rapport paginé. Par exemple, fournissez deux paramètres pour la date de début et la date de fin des données de ventes.  
  
**Modifier la présentation du rapport**
  
- Autorisez les utilisateurs à spécifier des valeurs pour personnaliser l’apparence d’un rapport. Par exemple, fournissez un paramètre Boolean pour indiquer s’il faut développer ou réduire tous les groupes de lignes imbriqués dans un tableau.  
  
- Autorisez les utilisateurs à personnaliser l’apparence et les données d’un rapport en incluant des paramètres dans une expression.  
  
## <a name="UserInterface"></a> Affichage d’un rapport avec des paramètres

Lorsque vous affichez un rapport avec des paramètres, la barre d’outils de la visionneuse de rapports présente chaque paramètre pour vous permettre de spécifier de manière interactive les valeurs. L’illustration suivante montre la zone des paramètres d’un rapport avec les paramètres @ReportMonth, @ReportYear, @EmployeeID, @ShowAll, @ExpandTableRows, @CategoryQuota et @SalesDate.  

![Afficher un rapport avec des paramètres](media/report-builder-parameters/report-builder-parameters-power-bi-service.png "Afficher un rapport avec des paramètres")
  
1. **Volet des paramètres** La barre d’outils de la visionneuse de rapports affiche une invite et une valeur par défaut pour chaque paramètre. Vous pouvez personnaliser la disposition des paramètres dans le volet des paramètres.  
  
2. Paramètre **@SalesDate**  Le paramètre @SalesDate est le type de données **DateTime**. L’invite Sélectionner la date apparaît à côté de la zone de texte. Pour modifier la date, tapez une nouvelle date dans la zone de texte ou utilisez le calendrier.  
  
3. Paramètre **@ShowAll**  Le paramètre @ShowAll est le type de données **Boolean**. Utilisez les cases d’option pour spécifier **True** ou **False**.  
  
4. **Poignée Afficher ou masquer la zone de paramètres** Dans la barre d’outils de la visionneuse de rapports, cliquez sur cette flèche pour afficher ou masquer le volet des paramètres.  
  
5. Paramètre **@CategoryQuota**  Le paramètre @CategoryQuota est le type de données **Float**, donc il prend une valeur numérique.  @CategoryQuota est défini pour autoriser plusieurs valeurs.  
  
6. **Afficher le rapport** Après avoir entré des valeurs de paramètre, cliquez sur **Afficher le rapport** pour exécuter le rapport. Si tous les paramètres ont des valeurs par défaut, le rapport s’exécute automatiquement au premier affichage.  
  
## <a name="bkmk_Create_Parameters"></a> Création de paramètres

Vous pouvez créer des paramètres de rapport de différentes manières.
  
> [!NOTE]
>  Les sources de données ne prennent pas toutes en charge les paramètres.
  
**Requête de jeu de données ou procédure stockée avec des paramètres**
  
 Ajoutez une requête de jeu de données qui contient des variables, ou une procédure stockée de jeu de données qui contient des paramètres d’entrée. Un paramètre de jeu de données est créé pour chaque variable ou paramètre d’entrée, tandis qu’un paramètre de rapport est créé pour chaque paramètre de jeu de données.  
  
![Propriétés du jeu de données dans les paramètres du Générateur de rapports](media/report-builder-parameters/report-builder-parameter-dataset.png "Propriétés du jeu de données dans les paramètres du Générateur de rapports")

  
 Cette image du Générateur de rapports montre :  
  
1.  Les paramètres du rapport dans le volet Données de rapport.  
  
2.  Le jeu de données avec les paramètres.  
  
3.  Le volet Paramètres.  
  
4.  Les paramètres listés dans la boîte de dialogue Propriétés du jeu de données.  
  
**Créer un paramètre manuellement**
  
Créez un paramètre manuellement à partir du volet Données de rapport. Vous pouvez configurer les paramètres de rapport pour permettre à l’utilisateur d’entrer de manière interactive des valeurs en vue de personnaliser le contenu ou l’apparence d’un rapport. Vous pouvez également configurer les paramètres de rapport pour que l’utilisateur ne puisse pas changer les valeurs préconfigurées.  
  
> [!NOTE]  
>  Étant donné que les paramètres sont gérés indépendamment sur le serveur, si vous republiez un rapport principal avec de nouveaux paramètres, vous ne remplacez pas les paramètres existants sur le rapport.  

### <a name="parameter-values"></a>Valeurs de paramètre

 Voici une liste d’options servant à sélectionner des valeurs de paramètre dans le rapport.  
  
- Sélectionner une valeur de paramètre dans une liste déroulante.  
  
- Sélectionner plusieurs valeurs de paramètre dans une liste déroulante.  
  
- Sélectionner une valeur dans une liste déroulante pour un paramètre, qui détermine les valeurs qui sont disponibles dans la liste déroulante pour un autre paramètre. Il s’agit de paramètres en cascade. Les paramètres en cascade vous permettent de filtrer successivement des valeurs de paramètre sur des milliers de valeurs pour arriver à un nombre plus gérable.  
  
- Exécuter le rapport sans devoir d’abord sélectionner une valeur de paramètre, car une valeur par défaut a été créée pour le paramètre.  
  
## <a name="bkmk_Report_Parameters"></a> Propriétés des paramètres de rapport

 Vous pouvez changer les propriétés des paramètres de rapport à l’aide de la boîte de dialogue Propriétés du rapport. Le tableau suivant récapitule les propriétés que vous pouvez définir pour chaque paramètre :  
  
|Propriété|Description|  
|--------------|-----------------|  
|Nom|Tapez un nom sensible à la casse pour le paramètre. Le nom doit commencer par une lettre et peut contenir des lettres, des chiffres et un trait de soulignement (_). Le nom ne peut pas contenir d’espace. Pour les paramètres générés automatiquement, le nom correspond au paramètre dans la requête de jeu de données. Par défaut, les paramètres créés manuellement sont similaires à ReportParameter1.|  
|Invite|Texte qui apparaît à côté du paramètre dans la barre d’outils de la visionneuse de rapports.|  
|Type de données|Un paramètre de rapport doit être l’un des types de données suivants :<br /><br /> **Boolean**. L’utilisateur sélectionne True ou False via une case d’option.<br /><br /> **DateTime**. L’utilisateur sélectionne une date dans un calendrier.<br /><br /> **Integer**. L’utilisateur tape des valeurs dans une zone de texte.<br /><br /> **Float**. L’utilisateur tape des valeurs dans une zone de texte.<br /><br /> **Text**. L’utilisateur tape des valeurs dans une zone de texte.<br /><br /> Lorsque des valeurs disponibles sont définies pour un paramètre, l’utilisateur choisit des valeurs dans une liste déroulante, même si le type de données est **DateTime**.|  
|Autoriser une valeur vide|Sélectionnez cette option si la valeur du paramètre peut être une chaîne vide ou une valeur vide.<br /><br /> Si vous spécifiez des valeurs valides pour un paramètre et que vous voulez qu’une valeur vide soit l’une des valeurs valides, vous devez l’inclure en tant qu’une des valeurs que vous spécifiez. La sélection de cette option n’inclut pas automatiquement une valeur vide pour les valeurs disponibles.|  
|Autoriser une valeur null|Sélectionnez cette option si la valeur du paramètre peut être une valeur null.<br /><br /> Si vous spécifiez des valeurs valides pour un paramètre et que vous voulez qu’une valeur null soit l’une des valeurs valides, vous devez inclure null en tant qu’une des valeurs que vous spécifiez. La sélection de cette option n’inclut pas automatiquement une valeur null pour les valeurs disponibles.|  
|Autoriser plusieurs valeurs|Fournissez les valeurs disponibles pour créer une liste déroulante dans laquelle vos utilisateurs peuvent choisir. C’est un bon moyen de vous assurer que seules les valeurs valides sont soumises dans la requête de jeu de données.<br /><br /> Sélectionnez cette option si la valeur du paramètre peut être plusieurs valeurs affichées dans une liste déroulante. Les valeurs null ne sont pas autorisées. Lorsque cette option est sélectionnée, les cases à cocher sont ajoutées à la liste des valeurs disponibles dans une liste déroulante de paramètres. En haut de la liste se trouve une case à cocher pour **Tout sélectionner**. Les utilisateurs peuvent cocher les valeurs qu’ils souhaitent.<br /><br /> Si les données qui fournissent les valeurs changent rapidement, la liste que voit l’utilisateur risque de ne pas être la plus récente.|  
|Visible|Sélectionnez cette option pour afficher le paramètre de rapport en haut du rapport quand celui-ci est exécuté. Cette option permet aux utilisateurs de sélectionner des valeurs de paramètre lors de l’exécution.|  
|Masqué|Sélectionnez cette option pour masquer le paramètre de rapport dans le rapport publié. Les valeurs de paramètre de rapport peuvent quand même être définies sur une URL de rapport, dans une définition d’abonnement ou sur le serveur de rapports.|  
|Interne|Sélectionnez cette option pour masquer le paramètre de rapport. Dans le rapport publié, le paramètre de rapport peut uniquement s’afficher dans la définition de rapport.|  
|Valeurs disponibles|Si vous avez spécifié des valeurs disponibles pour un paramètre, les valeurs valides apparaissent toujours sous forme de liste déroulante. Par exemple, si vous fournissez les valeurs disponibles pour un paramètre **DateTime**, une liste déroulante de dates s’affiche dans le volet de paramètres au lieu d’un calendrier.<br /><br /> Pour vous assurer qu’une liste de valeurs est cohérente dans un rapport et ses sous-rapports, vous pouvez définir une option dans la source de données afin d’utiliser une seule transaction pour toutes les requêtes des jeux de données qui sont associés à une source de données.<br /><br /> **Note de sécurité** Dans un rapport qui contient un paramètre de type de données **Text**, veillez à utiliser une liste de valeurs disponibles (également appelée liste de valeurs valides) et vérifiez que l’utilisateur qui exécute le rapport dispose uniquement des autorisations nécessaires pour voir les données dans le rapport.|  
|Valeurs par défaut|Définissez les valeurs par défaut à partir d’une requête ou d’une liste statique.<br /><br /> Quand chaque paramètre a une valeur par défaut, le rapport s’exécute automatiquement au premier affichage.|  
|Avancé|Définissez l’attribut de définition de rapport **UsedInQuery**, valeur qui indique si ce paramètre affecte directement ou indirectement les données d’un rapport.<br /><br /> **Déterminer automatiquement le moment de l’actualisation**<br /> Choisissez cette option lorsque vous souhaitez que le processeur de rapports détermine un paramètre pour cette valeur. La valeur est **True** si le processeur de rapports détecte une requête de jeu de données avec une référence directe ou indirecte à ce paramètre, ou si le rapport présente des sous-rapports.<br /><br /> **Toujours actualiser**<br /> Choisissez cette option quand le paramètre de rapport est utilisé directement ou indirectement dans une requête de jeu de données ou une expression de paramètre. Cette option définit **UsedInQuery** sur True.<br /><br /> **Ne jamais actualiser**<br /> Choisissez cette option quand le paramètre de rapport n’est pas utilisé directement ou indirectement dans une requête de jeu de données ou une expression de paramètre. Cette option définit **UsedInQuery** sur False.<br /><br /> **Attention** Utilisez **Ne jamais actualiser** avec précaution. Sur le serveur de rapports, **UsedInQuery** est utilisé pour permettre de contrôler les options de cache pour les données de rapport et les rapports rendus, ainsi que les options de paramètre pour les rapports d’instantané. Si vous ne définissez pas **Ne jamais actualiser** correctement, vous pouvez entraîner la mise en cache de rapports ou de données de rapport incorrects, ou la présence de données incohérentes dans les rapports d’instantané. |  
  
##  <a name="bkmk_Dataset_Parameters"></a> Requête de jeu de données  
 Pour filtrer les données dans la requête de jeu de données, vous pouvez inclure une clause de restriction qui limite les données récupérées en spécifiant des valeurs à inclure ou exclure du jeu de résultats.  
  
 Utilisez le Concepteur de requêtes pour la source de données pour vous aider à créer une requête paramétrable.  
  
-   Pour les requêtes Transact-SQL, les différentes sources de données prennent en charge une syntaxe différente pour les paramètres. La prise en charge englobe les paramètres qui sont identifiés dans la requête par position ou par nom. Dans le Concepteur de requêtes relationnelles, vous devez sélectionner l’option de paramètre pour un filtre afin de créer une requête paramétrable.   
  
-   Pour les requêtes qui sont basées sur une source de données multidimensionnelle telle que Microsoft SQL Server Analysis Services, vous pouvez spécifier s’il faut créer un paramètre basé sur un filtre que vous indiquez dans le Concepteur de requêtes. 
  
##  <a name="bkmk_Manage_Parameters"></a> Gestion des paramètres pour un rapport publié  
 Lorsque vous concevez un rapport, les paramètres de rapport sont enregistrés dans la définition de rapport. Lorsque vous publiez un rapport, les paramètres de rapport sont enregistrés et gérés à part de la définition de rapport.  
  
 Pour un rapport publié, vous pouvez utiliser les éléments suivants :  
  
-   **Propriétés des paramètres de rapport.** Changez les valeurs de paramètre de rapport directement sur le serveur de rapports, indépendamment de la définition de rapport.  
  
-   **Abonnements aux rapports.** Vous pouvez spécifier des valeurs de paramètre pour filtrer les données et remettre les rapports via des abonnements. 
  
 Les propriétés de paramètre pour un rapport publié sont conservées si vous republiez la définition de rapport. Si la définition de rapport est republiée comme même rapport et que les types de données et les noms de paramètre restent les mêmes, vos paramètres de propriété sont conservés. Si vous ajoutez ou supprimez des paramètres dans la définition de rapport ou que vous changez le nom d’un paramètre existant ou le type de données, vous devrez peut-être changer les propriétés de paramètre dans le rapport publié.  
  
 Les paramètres ne peuvent pas tous être modifiés dans tous les cas. Si un paramètre de rapport obtient une valeur par défaut à partir d’une requête de jeu de données, cette valeur ne peut pas être modifiée pour un rapport publié et ne peut pas être modifiée sur le serveur de rapports. La valeur utilisée au moment de l’exécution est déterminée quand la requête s’exécute, ou dans le cas de paramètres basés sur des expressions, quand l’expression est évaluée.  
  
 Les options d’exécution de rapport peuvent affecter la façon dont les paramètres sont traités. Un rapport qui s’exécute en tant qu’instantané ne peut pas utiliser les paramètres qui sont dérivés d’une requête, sauf si la requête inclut des valeurs par défaut pour les paramètres.  
  
##  <a name="bkmk_Parameters_Subscription"></a> Paramètres d’un abonnement  
 Vous pouvez définir un abonnement sur demande ou pour un instantané et spécifier des valeurs de paramètre à utiliser lors du traitement de l’abonnement.  
  
-   **Rapport à la demande.**  Pour un rapport à la demande, vous pouvez spécifier une valeur de paramètre différente de la valeur publiée pour chaque paramètre listé pour le rapport. Par exemple, supposons que vous avez un rapport Service d’appel qui utilise un paramètre *Période de temps* pour répondre aux demandes du service clientèle le même jour, la même semaine ou le même mois. Si la valeur du paramètre par défaut pour le rapport est définie sur **aujourd’hui**, votre abonnement peut utiliser une valeur de paramètre différente (comme **semaine** ou **mois**) pour produire un rapport qui contient des chiffres hebdomadaires ou mensuels.  
  
## <a name="next-steps"></a>Étapes suivantes

- [Présentation des rapports paginés dans Power BI Premium](paginated-reports-report-builder-power-bi.md)  
 
 
