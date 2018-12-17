---
title: Exporter des rapports de Power BI vers PowerPoint
description: Découvrez comment exporter un rapport Power BI vers PowerPoint.
author: mihart
manager: kvivek
ms.custom: seodec18
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 12/06/2018
ms.author: mihart
LocalizationGroup: Share your work
ms.openlocfilehash: 9f17cd76a733dff22ebf0b54eabc3d9b6c8f6839
ms.sourcegitcommit: cd85d88fba0d9cc3c7a4dc03d2f35d2bd096759b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/12/2018
ms.locfileid: "53281066"
---
# <a name="export-reports-from-power-bi-to-powerpoint"></a>Exporter des rapports de Power BI vers PowerPoint
Avec Power BI, vous pouvez publier votre rapport dans **Microsoft PowerPoint** et créer facilement un ensemble de diapositives en fonction de votre rapport Power BI. Lorsque vous **exportez vers PowerPoint**, les éléments suivants se produisent :

* Chaque page du rapport Power BI devient une diapositive dans PowerPoint.
* Chaque page du rapport Power BI est exportée en tant qu’image haute résolution dans PowerPoint <!-- * The filters and slicers settings that you added to the report are preserved. -->
* Dans PowerPoint, un lien est créé. Il renvoie vers le rapport Power BI. 

L’exportation d’un **rapport Power BI** dans **PowerPoint** est rapide. Suivez les étapes décrites dans la section suivante.

## <a name="how-to-export-your-power-bi-report-to-powerpoint"></a>Exporter un rapport Power BI vers PowerPoint
Dans le service Power BI, sélectionnez un rapport pour l’afficher dans le canevas. Vous pouvez également sélectionner un rapport dans votre page **Accueil**, vos **applications** ou toute autre section dans votre volet de navigation de gauche.

![Sélection du fichier dans la barre de menus, flèche pointant vers Exporter vers PowerPoint](media/end-user-powerpoint/power-bi-publish.png)

Lorsque le rapport que vous souhaitez exporter vers PowerPoint est affiché sur le canevas, sélectionnez **Fichier > Exporter vers PowerPoint** à partir de la barre de menus dans le service Power BI.

![Gros plan sur la barre de navigation de gauche avec Mon espace de travail sélectionné, Liste déroulante Fichier sélectionnée](media/end-user-powerpoint/powerbi_to_powerpoint_1.png)

Dans l’angle supérieur droit de la fenêtre du navigateur du service Power BI, une bannière de notification indique que le rapport est en cours d’exportation vers PowerPoint. Cette opération peut prendre quelques minutes. Pendant ce temps, vous pouvez continuer à travailler dans Power BI.

![notification d’exportation vers PowerPoint en cours](media/end-user-powerpoint/powerbi_to_powerpoint_2.png)

Une fois que vous avez terminé, la bannière de notification change pour vous informer que le service Power BI a terminé le processus d’exportation.

![Affichage du message de réussite](media/end-user-powerpoint/powerbi_to_powerpoint_3.png)

Votre fichier est ensuite disponible à l’endroit où votre navigateur affiche les fichiers téléchargés. Dans l’image suivante, il est affiché sous forme de bannière de téléchargement au bas de la fenêtre du navigateur.

![flèche pointant vers la notification du navigateur en bas de l’écran](media/end-user-powerpoint/powerbi_to_powerpoint_4.png)

C’est tout. Vous pouvez télécharger le fichier, l’ouvrir dans PowerPoint, puis le modifier ou l’améliorer tout comme vous le feriez pour n’importe quel autre diaporama PowerPoint.

## <a name="checking-out-your-exported-powerpoint-file"></a>Extraction du fichier PowerPoint exporté
Lorsque vous ouvrez le fichier PowerPoint que Power BI a exporté, quelques éléments intéressants et utiles s’affichent. Examinez l’image suivante, puis vérifiez les éléments numérotés ci-dessous qui décrivent certaines de ces fonctionnalités intéressantes.

![PowerPoint s’ouvre](media/end-user-powerpoint/powerbi_to_powerpoint_5.png)

1. La première page de l’ensemble de diapositives inclut le nom de votre rapport et un lien qui vous permet d’**afficher dans Power BI** le rapport sur lequel repose l’ensemble de diapositives.
2. Vous obtenez également des informations utiles sur le rapport, y compris la *dernière actualisation des données* sur laquelle est basé le rapport exporté et l’heure et la date de *téléchargement*, qui correspondent à l’heure et à la date auxquelles le rapport Power BI a été exporté dans un fichier PowerPoint.
3. Chaque page du rapport est une diapositive distincte, comme indiqué dans le volet de navigation gauche. 
4. Votre rapport publié s’affiche dans la langue définie dans vos paramètres Power BI, ou selon les paramètres régionaux de votre navigateur. Pour voir ou définir vos préférences de langue, sélectionnez l’icône représentant une roue dentée ![icône de roue dentée](media/end-user-powerpoint/power-bi-settings-icon.png) **> Paramètres > Général > Langue**. Pour obtenir des informations locales, consultez [Langues et pays/régions pris en charge pour Power BI](../supported-languages-countries-regions.md).
5. La présentation PowerPoint inclut une diapositive de couverture indiquant l’heure d’exportation dans le fuseau horaire correct.

Lorsque vous accédez à une diapositive, vous remarquez que chaque page de rapport est une image indépendante.

>[!NOTE]
> Avoir un seul visuel pour chaque page du rapport est un nouveau comportement. Le comportement précédent, qui fournissait une image indépendante pour chaque visuel, n’est plus implémenté. 
 

![Image montrant que chaque visuel est une image distincte](media/end-user-powerpoint/powerbi_to_powerpoint_6.png)

À partir de là, vous pouvez faire ce que vous voulez avec votre présentation PowerPoint ou les images haute résolution.

## <a name="limitations"></a>Limites
Voici quelques considérations et limitations à prendre en compte lorsque vous utilisez la fonctionnalité **Exporter vers PowerPoint**.

* L’interactivité dans la session, comme la mise en évidence et le filtrage, l’exploration, etc. n’est pas encore pris en charge lors de l’exportation vers PowerPoint. Le PowerPoint exporté montre les visuels d’origine tels qu’ils ont été enregistrés dans le rapport. Si vous avez appliqué des filtres et des segments, et si vous souhaitez les conserver dans l’exportation, enregistrez le rapport et procédez à l’exportation.
* Les **éléments visuels R** ne sont actuellement pas pris en charge. Tout élément visuel de ce type est exporté en tant qu’image vide dans PowerPoint, avec un message d’erreur indiquant que l’élément visuel n’est pas pris en charge.
* Les **éléments visuels personnalisés** qui ont été **certifiés** sont pris en charge. Pour plus d’informations sur les éléments visuels personnalisés certifiés, notamment concernant la manière de certifier un élément visuel personnalisé, voir [Obtention d’un visuel personnalisé certifié](../power-bi-custom-visuals-certified.md). Les éléments visuel personnalisés non certifiés ne sont pas pris en charge. Tout élément visuel de ce type est exporté en tant qu’image vide dans PowerPoint, avec un message d’erreur indiquant que l’élément visuel n’est pas pris en charge.
* Les rapports contenant plus de 30 pages ne peuvent pas être exportés actuellement.
* Le processus d’exportation du rapport vers PowerPoint peut prendre quelques minutes. Soyez patient. Les facteurs qui peuvent avoir un impact sur la durée d’exportation sont la structure du rapport et la charge actuelle sur le service Power BI.
* Si l’option de menu **Exporter vers PowerPoint** n’est pas disponible dans le service Power BI, il est probable que votre administrateur ait désactivé la fonctionnalité. Pour plus d’informations, contactez l’administrateur du locataire.
* Les images en arrière-plan sont rognées en fonction du cadre englobant du graphique. Il est fortement recommandé de supprimer les images en arrière-plan avant d’exporter vers PowerPoint.
* Les pages dans PowerPoint sont toujours créées dans la taille standard 9:16, quelles que soient les tailles de page ou dimensions d’origine dans le rapport Power BI.
* Vous ne pouvez pas publier vers PowerPoint les rapports possédés par un utilisateur extérieur de votre domaine de locataire Power BI (par exemple, un rapport appartenant à une personne extérieure à votre organisation et partagé avec vous).
* Si vous partagez un tableau de bord avec une personne externe à votre organisation (et par conséquent, un utilisateur qui n’est pas dans votre locataire Power BI), cet utilisateur ne peut pas exporter vers PowerPoint les rapports associés du tableau de bord partagé. Par exemple, si vous êtes aaron@contoso.com, vous pouvez partager avec david@cohowinery.com. Mais david@cohowinery.com ne peut pas exporter les rapports associés vers PowerPoint.
* Comme mentionné précédemment, chaque page du rapport est exportée en tant qu’image unique dans le fichier PowerPoint.
* Le service Power BI utilise votre paramètre de langue Power BI pour l’exportation PowerPoint. Pour voir ou définir vos préférences de langue, sélectionnez l’icône représentant une roue dentée ![icône de roue dentée](media/end-user-powerpoint/power-bi-settings-icon.png) **> Paramètres > Général > Langue**.
* **L’heure de téléchargement** qui apparaît sur la diapositive de couverture du fichier PowerPoint exporté est définie en fonction du fuseau horaire de l’ordinateur au moment de l’exportation.

## <a name="next-steps"></a>Étapes suivantes
[Imprimer un rapport](end-user-print.md)