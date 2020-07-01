---
title: Créer des paramètres de rapports paginés dans le service Power BI
description: Dans cet article, vous allez apprendre créer des paramètres de rapports paginés dans le service Power BI.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: report-builder
ms.topic: how-to
ms.date: 12/03/2019
ms.openlocfilehash: ab2d0a0678fb5ff251e65d42784f02c1fb8c0cea
ms.sourcegitcommit: eef4eee24695570ae3186b4d8d99660df16bf54c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85219602"
---
# <a name="create-parameters-for-paginated-reports-in-the-power-bi-service"></a>Créer des paramètres de rapports paginés dans le service Power BI

Dans cet article, vous allez apprendre créer des paramètres de rapports paginés dans le service Power BI.  Un paramètre de rapport permet de choisir des données de rapport et de varier la présentation du rapport. Vous pouvez fournir une valeur par défaut et une liste de valeurs disponibles, et les lecteurs de votre rapport peuvent modifier la sélection.  

L’illustration suivante montre le mode Design dans le Générateur de rapports Power BI pour un rapport avec les paramètres @BuyingGroup, @Customer, @FromDate et @ToDate. 
  
![Paramètres dans le Générateur de rapports](media/paginated-reports-parameters/power-bi-paginated-parameters-report-builder.png)
  
1.  Les paramètres du rapport dans le volet Données de rapport.  
  
2.  La table avec l’un des paramètres du jeu de données.  
  
3.  Le volet Paramètres. Vous pouvez personnaliser la disposition des paramètres dans le volet des paramètres. 
  
4.  Les paramètres @FromDate et @ToDate ont le type de données **DateTime**. Lorsque vous affichez le rapport, vous pouvez taper une date dans la zone de texte ou choisir une date dans le contrôle calendrier. 

5.  L’un des paramètres dans la boîte de dialogue **Propriétés du jeu de données**.  

  
## <a name="create-or-edit-a-report-parameter"></a>Créer ou modifier un paramètre de rapport  
  
1.  Ouvrez votre rapport paginé dans le Générateur de rapports Power BI.

1. Dans le volet **Données de rapport**, cliquez avec le bouton droit le **Paramètres** nœud > **Ajouter un paramètre**. La boîte de dialogue **Propriétés des paramètres du rapport** s’ouvre.  
  
2.  Dans **Nom**, tapez un nom pour le paramètre ou acceptez le nom par défaut.  
  
3.  Dans **Invite**, tapez le texte devant apparaître en regard de la zone de texte du paramètre lorsque l’utilisateur exécute le rapport.  
  
4.  Dans **Type de données**, sélectionnez le type de données pour la valeur du paramètre.  
  
5.  Si le paramètre peut contenir une valeur vide, sélectionnez **Autoriser une valeur vide**.  
  
6.  Si le paramètre peut contenir une valeur Null, sélectionnez **Autoriser une valeur Null**.  
  
7.  Pour autoriser un utilisateur à sélectionner plusieurs valeurs pour le paramètre, sélectionnez **Autoriser plusieurs valeurs**.  
  
8.  Définissez l’option de visibilité.  
  
    -   Pour afficher le paramètre dans la barre d’outils en haut du rapport, sélectionnez **Visible**.  
  
    -   Pour masquer le paramètre afin qu’il ne s’affiche pas dans la barre d’outils, sélectionnez **Masqué**.  
  
    -   Pour masquer le paramètre et empêcher sa modification sur le serveur de rapports une fois le rapport publié, sélectionnez **Interne**. Le paramètre du rapport ne peut alors s’afficher que dans la définition de rapport. Pour cette option, vous devez définir une valeur par défaut ou autoriser le paramètre à accepter une valeur Null.  
  
9. Sélectionnez **OK**. 

## <a name="considerations-and-troubleshooting"></a>Considérations et résolution des problèmes

- Si vous utilisez un jeu de données Power BI ou un modèle Analysis Services comme source de données, vous ne pouvez pas passer plus de 1 000 valeurs de paramètre dans une seule requête en raison de limitations propres à DAX. 

 
## <a name="next-steps"></a>Étapes suivantes

Consultez [Afficher les paramètres des rapports paginés](../consumer/paginated-reports-view-parameters.md) pour voir à quoi ressemblent les paramètres dans le service Power BI.

Pour obtenir des informations détaillées sur les paramètres dans les rapports paginés, consultez [Paramètres de rapport dans le Générateur de rapports Power BI](report-builder-parameters.md).
