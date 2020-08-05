---
title: Copier-coller d’une visualisation dans le service Power BI
description: Copiez et collez une visualisation dans le service Power BI.
author: mihart
ms.reviewer: maggie.tsang
ms.service: powerbi
ms.subservice: powerbi-consumer
ms.topic: how-to
ms.date: 06/25/2020
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: dc5cba8953a527e87768815759a14dd8f2cf7ee1
ms.sourcegitcommit: 2131f7b075390c12659c76df94a8108226db084c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/03/2020
ms.locfileid: "87537846"
---
# <a name="copy-a-visual-as-an-image-to-your-clipboard"></a>Copier un visuel en tant qu’image dans le Presse-papiers

[!INCLUDE[consumer-appliesto-yyyn](../includes/consumer-appliesto-yyyn.md)]

Avez-vous déjà voulu partager une image d’un rapport ou d’un tableau de bord Power BI ? Vous pouvez maintenant copier le visuel et le coller dans toute autre application qui prend en charge le collage. 

Lorsque vous copiez une image statique d’un visuel, vous obtenez une copie du visuel avec les métadonnées. Cela comprend :
* un lien pour retourner au rapport Power BI ou au tableau de bord
* le titre du rapport ou du tableau de bord
* un message précisant que l’image contient des informations confidentielles
* l’horodatage de la dernière mise à jour
* les filtres appliqués au visuel

### <a name="copy-from-a-dashboard-tile"></a>Copie à partir d’une vignette de tableau de bord

1. Accédez au tableau de bord à partir duquel vous souhaitez effectuer la copie.

2. En haut à droite du visuel, sélectionnez **Plus d’actions (…)** , puis choisissez **Copier le visuel comme une image**. 

    ![Icône de copie d’un visuel sous forme d’image affichée](media/end-user-copy-paste/power-bi-copy-dashboard.png)

3. Quand la boîte de dialogue **Votre visuel est prêt à être copié** s’affiche, sélectionnez **Copier dans le Presse-papiers**.

    ![boîte de dialogue avec l’option Copier dans le Presse-papiers](media//end-user-copy-paste/power-bi-copied.png)

4. Une fois le visuel copié, collez-le dans une autre application en appuyant sur **Ctrl+V** ou en cliquant avec le bouton droit > Coller. Dans la capture d’écran ci-dessous, nous avons collé le visuel dans Microsoft Word. 

    ![visuel collé dans Outlook](media//end-user-copy-paste/power-bi-paste-word.png)

### <a name="copy-from-a-report-visual"></a>Copie à partir d’un visuel de rapport 

1. Accédez au rapport à partir duquel vous voulez effectuer la copie.

2. Dans l’angle supérieur droit du visuel, sélectionnez l’icône **Copier le visuel comme une image**. 

    ![Icône de copie d’un visuel sous forme d’image affichée](media/end-user-copy-paste/power-bi-copy-icon.png)

3. Quand la boîte de dialogue **Votre visuel est prêt à être copié** s’affiche, sélectionnez **Copier dans le Presse-papiers**.

    ![boîte de dialogue avec l’option Copier dans le Presse-papiers](media//end-user-copy-paste/power-bi-copied.png)


4. Une fois le visuel copié, collez-le dans une autre application en appuyant sur **Ctrl+V** ou en cliquant avec le bouton droit > Coller. Dans la capture d’écran ci-dessous, nous avons collé le visuel dans un message électronique.

    ![visuel collé dans Outlook](media//end-user-copy-paste/power-bi-copy-email.png)

5. Si le rapport comporte une étiquette de sensibilité des données, un avertissement s’affiche lorsque vous sélectionnez l’icône de copie.  

    ![avertissement de données sensibles](media//end-user-copy-paste/power-bi-sensitive.png)

    Une étiquette de sensibilité sera ajoutée aux métadonnées sous le visuel collé. 

    ![visuel avec étiquette d’informations confidentielles](media//end-user-copy-paste/power-bi-confidential.png)



## <a name="considerations-and-troubleshooting"></a>Considérations et résolution des problèmes

   ![copie non disponible](media//end-user-copy-paste/power-bi-copy-grey.png)


Q : Pourquoi l’icône de copie est-elle désactivée sur un visuel ?    
R : Nous prenons actuellement en charge les visuels Power BI natifs et les visuels personnalisés certifiés. Certains visuels sont pris en charge de façon limitée, notamment : 
- ESRI et autres visuels de carte 
- Visuels Python 
- Visuels R 
- PowerApps    

R : La possibilité de copier un visuel peut être désactivée par votre service informatique ou par votre administrateur Power BI.


Q : Pourquoi mon visuel n’est-il pas correctement collé ?    
R : Il existe des limitations pour les visuels personnalisés et les visuels animés. 



## <a name="next-steps"></a>Étapes suivantes
En savoir plus sur les [visualisations dans les rapports Power BI](end-user-visual-type.md)

D’autres questions ? [Posez vos questions à la communauté Power BI](https://community.powerbi.com/)

