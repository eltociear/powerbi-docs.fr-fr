---
title: Exporter des rapports au format PDF
description: Découvrez comment exporter un rapport Power BI au format PDF.
author: mihart
manager: kvivek
ms.custom: ''
ms.reviewer: cmfinlan
ms.service: powerbi
ms.subservice: powerbi-consumer
ms.topic: conceptual
ms.date: 02/14/2019
ms.author: mihart
LocalizationGroup: Share your work
ms.openlocfilehash: 35efd62e6f00edd9ce6b58774dd73925a721dec5
ms.sourcegitcommit: a054782370dec56d49bb205ee10b7e2018f22693
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56661925"
---
# <a name="export-reports-from-power-bi-to-pdf"></a>Exporter des rapports Power BI au format PDF
Power BI vous permet de publier votre rapport au format PDF et de créer facilement un document basé sur votre rapport. Quand vous **exportez au format PDF**, chaque page du rapport Power BI devient une page individuelle du document PDF.

## <a name="how-to-export-your-power-bi-report-to-pdf"></a>Comment exporter votre rapport Power BI au format PDF
Dans le service Power BI, sélectionnez un rapport pour l’afficher dans le canevas. Vous pouvez également sélectionner un rapport dans votre page d’accueil, vos applications ou toute autre section du volet de navigation de gauche.

1. Sélectionnez **Fichier** > **Exporter au format PDF** dans la barre de menus.

    ![Sélection de Fichier dans la barre de menus, flèche pointant vers Exporter au format PDF](media/end-user-pdf/power-bi-export-pdf.png)

    Une fenêtre contextuelle s’affiche, dans laquelle vous pouvez sélectionner l’option **Vue actuelle** ou **Vue par défaut**.  L’option **Vue actuelle** exporte le rapport dans l’état actuel, qui inclut les modifications actives apportées aux valeurs de segment et de filtre.  La plupart des utilisateurs choisissent cette option.  Vous pouvez aussi sélectionner l’option **Vue par défaut**, qui exporte le rapport dans son état initial (l’état au moment du partage par l’auteur), sans refléter les modifications que vous avez apportées à cet état initial.
    
    En outre, la fenêtre contient une case à cocher qui vous permet de spécifier si les onglets masqués d’un rapport doivent ou non être exportés.  Cochez cette case si vous souhaitez exporter uniquement les onglets du rapport qui sont visibles dans votre navigateur.  Laissez-la décochée si vous préférez inclure tous les onglets masqués dans l’exportation.  Si la case à cocher est grisée, cela indique que le rapport ne contient pas d’onglets masqués.  Une fois que vous avez effectué vos sélections, cliquez sur le bouton Exporter pour continuer.
    
    Une barre de progression s’affiche en haut à droite. L’exportation peut prendre quelques minutes. Pendant ce temps, vous pouvez continuer à travailler dans Power BI.

    ![Messages de progression de l’exportation](media/end-user-pdf/power-bi-export-message.png)

    Une fois que vous avez terminé, la bannière de notification change pour vous informer que le service Power BI a terminé le processus d’exportation.

2. Votre fichier est ensuite disponible à l’endroit où votre navigateur affiche les fichiers téléchargés. Dans l’image suivante, il est affiché sous forme de bannière de téléchargement au bas de la fenêtre du navigateur.

    ![Emplacement du fichier téléchargé](media/end-user-pdf/power-bi-save-file.png)

C’est tout. Vous pouvez télécharger le fichier et l’ouvrir avec n’importe quelle visionneuse PDF, comme celle disponible dans Microsoft Edge.


## <a name="limitations-and-considerations"></a>Considérations et limitations
Voici quelques considérations et limitations à prendre en compte quand vous utilisez la fonctionnalité **Exporter au format PDF**.

* Les **éléments visuels R** ne sont actuellement pas pris en charge. Dans le fichier PDF, ces visuels sont vides et affichent un message d’erreur.  

* Les **éléments visuels personnalisés** qui ont été **certifiés** sont pris en charge. Pour plus d’informations sur les éléments visuels personnalisés certifiés, notamment concernant la manière de certifier un élément visuel personnalisé, voir [Obtention d’un visuel personnalisé certifié](../power-bi-custom-visuals-certified.md). Les visuels personnalisés non certifiés ne sont pas pris en charge. Dans le fichier PDF, ils s’affichent avec un message d’erreur.   

* Les rapports contenant plus de 30 pages ne peuvent pas être exportés actuellement.

* Le processus d’exportation du rapport au format PDF peut prendre quelques minutes. Soyez patient. Les facteurs qui peuvent avoir un impact sur la durée d’exportation sont la structure du rapport et la charge actuelle sur le service Power BI.

* Si l’option de menu **Exporter au format PDF** n’est pas disponible dans le service Power BI, il est probable que votre administrateur ait désactivé la fonctionnalité. Pour plus d’informations, contactez l’administrateur du locataire.

* Les images en arrière-plan sont rognées en fonction du cadre englobant du graphique. Il est fortement recommandé de supprimer les images en arrière-plan avant d’exporter au format PDF.

* Vous ne pouvez pas publier au format PDF un rapport qui appartient à un utilisateur externe à votre domaine de locataire Power BI (par exemple, un rapport appartenant à une personne extérieure à votre organisation et partagé avec vous).

* Si vous partagez un tableau de bord avec une personne externe à votre organisation (et donc un utilisateur qui n’est pas dans votre locataire Power BI), cet utilisateur ne peut pas exporter es rapports associés du tableau de bord partagé au format PDF. Par exemple, si vous êtes aaron@contoso.com, vous pouvez partager avec cassie@cohowinery.com. Mais cassie@cohowinery.com ne peut pas exporter les rapports associés au format PDF.

* Lorsque vous exportez au format PDF avec des rapports qui contiennent une image d’arrière-plan, vous pouvez voir une image déformée dans l’exportation si vous utilisez l’option « Ajustement » pour l’arrière-plan de la page.  Pour de meilleurs résultats, il est recommandé d’utiliser les options « Normal » ou « Remplissage » afin d’éviter des problèmes avec votre document exporté.

* Le service Power BI utilise votre paramètre de langue Power BI pour l’exportation au format PDF. Pour afficher ou définir vos préférences de langue, sélectionnez l’icône représentant une roue dentée > **Paramètres** >  **Général** > **Langue**.

## <a name="next-steps"></a>Étapes suivantes
[Imprimer un rapport](end-user-print.md)
