---
title: Sous-rapports dans les rapports paginés Power BI
description: Dans cet article, vous allez découvrir les sources de données prises en charge pour les rapports paginés dans le service Power BI, et comment vous connecter à des sources de données Azure SQL Database.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.date: 04/29/2020
ms.openlocfilehash: 784e3fd3883adb9fc5b773cc730b992135d7ef8b
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83272807"
---
# <a name="subreports-in-power-bi-paginated-reports"></a>Sous-rapports dans les rapports paginés Power BI

Un *sous-rapport* est un élément de rapport paginé qui affiche un autre rapport paginé à l'intérieur du corps d'un rapport paginé principal. D'un point de vue conceptuel, un sous-rapport d'un rapport ressemble à un cadre d'une page Web. Vous pouvez l’utiliser pour incorporer un rapport dans un autre. Vous pouvez utiliser n’importe quel rapport en tant que sous-rapport. Vous stockez le rapport qui s’affiche en tant que sous-rapport dans le même espace de travail Premium que le rapport parent. Vous pouvez concevoir le rapport parent de sorte qu'il passe des paramètres au sous-rapport. Un sous-rapport peut être répété au sein de régions de données, en utilisant un paramètre pour filtrer les données de chaque instance du sous-rapport.  
  
 ![Sous-rapport dans un rapport paginé](media/subreports/paginated-report-subreport.png "Sous-rapport de rapport paginé")  
  
 Dans cette illustration, les informations de contact affichées dans le rapport Sales Order principal proviennent en fait d'un sous-rapport Contacts.  
  
Vous créez et modifiez des fichiers de définition de rapport (.rdl) paginé dans Power BI Report Builder. Vous pouvez télécharger des sous-rapports stockés dans SQL Server Reporting Services vers un espace de travail Premium du service Power BI. Les rapports principaux et les sous-rapports doivent être publiés dans le même espace de travail. Installez [Power BI Report Builder](https://go.microsoft.com/fwlink/?linkid=2086513).
  
## <a name="work-with-report-builder-and-the-power-bi-service"></a>Utiliser Report Builder et le service Power BI

Power BI Report Builder peut utiliser les rapports paginés présents sur votre ordinateur (appelés rapports locaux) ou les rapports disponibles dans le service Power BI.  Lorsque vous ouvrez Report Builder pour la première fois, vous êtes invité à vous connecter à votre compte Power BI. Si ce n’est pas le cas, sélectionnez **Se connecter** dans le coin supérieur droit.

:::image type="content" source="media/subreports/report-builder-sign-in.png" alt-text="Se connecter à Power BI":::

Une fois connecté, vous voyez s’afficher une option **Service Power BI** dans Power BI Report Builder pour les options **Ouvrir** et **Enregistrer sous** dans le menu **Fichier**. Lorsque vous sélectionnez l’option **Power BI service** pour enregistrer un rapport, vous créez une connexion active entre Power BI Report Builder et le service Power BI. 

:::image type="content" source="media/subreports/report-builder-subreport-open-service.png" alt-text="Ouvrir à partir du service Power BI":::

## <a name="save-a-local-report-to-the-power-bi-service"></a>Enregistrer un rapport local dans le service Power BI

Avant de pouvoir ajouter un sous-rapport à un rapport principal, créez d’abord les deux rapports, puis enregistrez-les dans le même espace de travail Power BI Premium. 

1. Pour ouvrir un rapport local existant, dans le menu **Fichier**, sélectionnez **Ouvrir** > **Ce PC**, puis choisissez un fichier .rdl.  

2. Dans le menu **Fichier**, sélectionnez **Enregistrer sous** > **Service Power BI**.  Voir [Publier un rapport paginé dans le service Power BI](paginated-reports-save-to-power-bi-service.md) pour plus de détails.

    > [!NOTE]
    > Vous pouvez également télécharger un rapport en commençant dans le service Power BI. Vous trouverez plus de détails dans ce même article [Publier un rapport paginé dans le service Power BI](paginated-reports-save-to-power-bi-service.md).

3. Dans la boîte de dialogue **Enregistrer sous**, sélectionnez un espace de travail Power BI Premium dans lequel vous pouvez stocker vos rapports paginés.  Les espaces de travail affichent une icône en forme de losange ![icône losange Premium](media/subreports/report-builder-premium-diamond.png) en regard de leur nom.

    :::image type="content" source="media/subreports/report-builder-subreport-save-as-service.png" alt-text="Enregistrer sous le service Power BI":::

4. Sélectionnez **Enregistrer**.

## <a name="add-a-subreport-to-a-report"></a>Ajouter un sous-rapport à un rapport

Maintenant que vous avez enregistré les deux rapports dans le même espace de travail Premium, vous pouvez en ajouter un à l’autre en tant que sous-rapport. Il existe deux façons d’ajouter un sous-rapport. 

1. Dans le ruban **Insérer**, sélectionnez le bouton **Sous-rapport**, ou cliquez avec le bouton droit sur le canevas du rapport, puis sélectionnez **Insérer** > **Sous-rapport**.

    :::image type="content" source="media/subreports/report-builder-insert-subreport.png" alt-text="Insérer un sous-rapport dans un rapport":::

    La boîte de dialogue **Propriétés du sous-rapport** s’affiche.  

2. Sélectionnez le bouton **Parcourir** > accédez au rapport que vous souhaitez utiliser comme sous-rapport > spécifiez le nom du sous-rapport dans la zone de texte **Nom**.

3. Configurez d’autres propriétés si nécessaire, notamment les [paramètres](#use-parameters-in-subreports).

## <a name="use-parameters-in-subreports"></a>Utiliser des paramètres dans des sous-rapports  
 Pour passer les paramètres du rapport parent au sous-rapport, définissez un paramètre dans le rapport que vous souhaitez utiliser à titre de sous-rapport. Lorsque vous placez le sous-rapport dans le rapport parent, vous pouvez sélectionner le paramètre de rapport et une valeur à passer du rapport parent au paramètre de rapport dans le sous-rapport.  
  
> [!NOTE]  
> Le paramètre que vous sélectionnez à partir du sous-rapport est un paramètre de *rapport*, et non un paramètre de *requête*.  
  
 Vous pouvez placer un sous-rapport dans le corps principal du rapport ou dans une région de données. Si vous le placez dans une région de données, il se répète avec chaque instance du groupe ou chaque ligne de la région de données. Vous pouvez passer une valeur du groupe ou de la ligne au sous-rapport. Dans la propriété de la valeur du sous-rapport, utilisez une expression de champ pour le champ qui contient la valeur à passer au paramètre du sous-rapport.  
  
 Pour plus d’informations sur l’utilisation des paramètres et des sous-rapports, consultez [Ajouter un sous-rapport et des paramètres](https://docs.microsoft.com/sql/reporting-services/report-design/add-a-subreport-and-parameters-report-builder-and-ssrs) dans la documentation de SQL Server Reporting Services.  

## <a name="preview-paginated-reports-in-report-builder"></a>Aperçu de rapports paginés dans Report Builder

Vous pouvez obtenir un aperçu de vos rapports dans Report Builder.

- Dans le ruban **Accueil**, sélectionnez **Exécuter**. 

Report Builder étant un outil de conception, l’aperçu du rapport peut paraître différent du rendu du rapport dans le service Power BI.

### <a name="notes-about-previewing"></a>Remarques sur l’aperçu

- Report Builder ne stocke pas les informations d’identification des sources de données utilisées dans les rapports.  Report Builder vous demande de saisir chacune des informations d’identification lors de l’aperçu.  
- Si les sources de données du rapport sont locales, vous devez configurer une passerelle après avoir enregistré le rapport dans l’espace de travail Power BI.
- Si Report Builder rencontre une erreur lors de l’aperçu, il renvoie un message générique.  Si l’erreur est difficile à déboguer, essayez d’afficher le rapport dans le service Power BI.  

## <a name="considerations"></a>Considérations

### <a name="maintaining-the-connection"></a>Gestion de la connexion

Report Builder ne conserve pas la connexion à Power BI lorsque vous fermez le fichier.  Vous pouvez utiliser un rapport principal local avec des sous-rapports stockés dans l’espace de travail Power BI. Veillez à enregistrer le rapport principal dans l’espace de travail Power BI avant de fermer le rapport.  Sinon, vous risquez d’obtenir un message « introuvable » lors de l’aperçu, car il n’existe aucune connexion active au service Power BI.  Dans ce cas, accédez à un sous-rapport et sélectionnez ses propriétés.  Ouvrez à nouveau le sous-rapport à partir du service Power BI.  Cette opération rétablit la connexion, et tous les autres sous-rapports devraient s’afficher correctement.

### <a name="renaming-a-subreport"></a>Attribution d’un nouveau nom à un sous-rapport

Si vous renommez un sous-rapport dans l’espace de travail, vous devez corriger la référence de nom dans le rapport principal. Sinon, le sous-rapport ne s’affichera pas. Le rapport principal affiche toujours un message d’erreur dans l’élément de sous-rapport.

## <a name="migrate-large-reports"></a>Migrer des rapports volumineux

Si vous migrez des rapports volumineux vers Power BI, vous pouvez utiliser l’[outil RdlMigration](../guidance/migrate-ssrs-reports-to-power-bi.md).  L’outil RdlMigration a été mis à jour pour gérer les noms de sous-rapports en double.  Des noms de sous-rapports en double peuvent se produire lorsque plusieurs rapports partagent le même nom mais résident dans des sous-répertoires différents.  Si les noms ne sont pas résolus de manière unique, seul le premier sous-rapport est reconnu.

Si vous souhaitez utiliser Report Builder pour migrer des rapports volumineux, nous vous recommandons d’utiliser d’abord les sous-rapports. Enregistrez chaque rapport dans l’espace de travail Power BI pour empêcher les noms de rapport en double.

## <a name="share-reports-with-subreports"></a>Partage de rapports avec des sous-rapports

Comme nous l’avons indiqué, le rapport principal et les sous-rapports doivent se trouver dans le même espace de travail. Sinon, le sous-rapport ne s’affiche pas. Lors du partage du rapport principal, vous devez également partager les sous-rapports. Si vous partagez le rapport principal dans une application, veillez à inclure également les sous-rapports dans cette application. Si vous partagez directement le rapport principal avec des utilisateurs ou des groupes d’utilisateurs, veillez à partager également chaque sous-rapport avec le même ensemble d’utilisateurs ou groupes d’utilisateurs.
  
## <a name="next-steps"></a>Étapes suivantes

[Résoudre les problèmes de sous-rapports dans les rapports paginés Power BI](subreports-troubleshoot.md)

[Afficher un rapport paginé dans le service Power BI](../consumer/paginated-reports-view-power-bi-service.md)

D’autres questions ? [Essayez la communauté Power BI](https://community.powerbi.com/)
