---
title: Exporter des rapports de Power BI vers PowerPoint (version préliminaire)
description: Découvrez comment exporter un rapport Power BI vers PowerPoint.
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 07/27/2018
ms.author: davidi
LocalizationGroup: Share your work
ms.openlocfilehash: 954264018babcf8a2a95ec5686ac7688cd52fe24
ms.sourcegitcommit: f01a88e583889bd77b712f11da4a379c88a22b76
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2018
ms.locfileid: "39328416"
---
# <a name="export-reports-from-power-bi-to-powerpoint-preview"></a>Exporter des rapports de Power BI vers PowerPoint (version préliminaire)
Avec Power BI, vous pouvez à présent publier votre rapport dans **Microsoft PowerPoint** et créer facilement un ensemble de diapositives en fonction de votre rapport Power BI. Lorsque vous **exportez vers PowerPoint**, les éléments suivants se produisent :

* Chaque page du rapport Power BI devient une diapositive dans PowerPoint.
* Chaque page du rapport Power BI est exportée en tant qu’image haute résolution dans PowerPoint
* Les zones de texte du rapport Power BI deviennent modifiables dans PowerPoint.
* Dans PowerPoint, un lien est créé. Il renvoie vers le rapport Power BI.

Il est facile d’exporter un **rapport Power BI** dans **PowerPoint**. Suivez les étapes décrites dans la section suivante.

## <a name="how-to-export-your-power-bi-report-to-powerpoint"></a>Exporter un rapport Power BI vers PowerPoint
Dans le service Power BI, sélectionnez la section **Rapports** dans le volet de navigation gauche pour la développer, puis sélectionnez votre rapport pour l’afficher sur le canevas. Vous pouvez également sélectionner un rapport dans la section **Mon espace de travail** ou vos **Favoris** si le rapport se trouve dans un de ces emplacements.

![](media/service-publish-to-powerpoint/powerbi_to_powerpoint_0.png)

Lorsque le rapport que vous souhaitez exporter vers PowerPoint est affiché sur le canevas, sélectionnez **Fichier > Exporter vers PowerPoint (version préliminaire)** à partir de la barre de menus dans le service Power BI, comme illustré dans l’image suivante.

![](media/service-publish-to-powerpoint/powerbi_to_powerpoint_1.png)

Dans l’angle supérieur droit de la fenêtre du navigateur du service Power BI, une bannière de notification indique que le rapport est en cours d’exportation vers PowerPoint. Cette opération peut prendre quelques minutes. Pendant ce temps, vous pouvez continuer à travailler dans Power BI.

![](media/service-publish-to-powerpoint/powerbi_to_powerpoint_2.png)

Une fois que vous avez terminé, la bannière de notification change pour vous informer que le service Power BI a terminé le processus d’exportation.

![](media/service-publish-to-powerpoint/powerbi_to_powerpoint_3.png)

Votre fichier est ensuite disponible à l’endroit où votre navigateur affiche les fichiers téléchargés. Dans l’image suivante, il est affiché sous forme de bannière de téléchargement au bas de la fenêtre du navigateur.

![](media/service-publish-to-powerpoint/powerbi_to_powerpoint_4.png)

C’est tout. Vous pouvez télécharger le fichier, l’ouvrir dans PowerPoint, puis le modifier ou l’améliorer tout comme vous le feriez pour n’importe quel autre diaporama PowerPoint.

## <a name="checking-out-your-exported-powerpoint-file"></a>Extraction du fichier PowerPoint exporté
Lorsque vous ouvrez le fichier PowerPoint que Power BI a exporté, quelques éléments intéressants et utiles s’affichent. Examinez l’image suivante, puis vérifiez les éléments numérotés ci-dessous qui décrivent certaines de ces fonctionnalités intéressantes.

![](media/service-publish-to-powerpoint/powerbi_to_powerpoint_5.png)

1. La première page de l’ensemble de diapositives inclut le nom de votre rapport et un lien qui vous permet d’**afficher dans Power BI** le rapport sur lequel repose l’ensemble de diapositives.
2. Vous obtenez également des informations utiles sur le rapport, y compris la *dernière actualisation des données* sur laquelle est basé le rapport exporté et l’heure et la date de *téléchargement*, qui correspondent à l’heure et à la date auxquelles le rapport Power BI a été exporté dans un fichier PowerPoint.
3. Chaque page du rapport est une diapositive distincte, comme indiqué dans le volet de navigation gauche.
4. Votre rapport publié s’affiche dans la langue définie dans vos paramètres Power BI, ou selon les paramètres régionaux de votre navigateur. Pour afficher ou définir vos préférences de langue, sélectionnez l’icône représentant une roue dentée ![](media/service-report-subscribe/power-bi-settings-icon.png) **> Paramètres > Général > Langue**. Pour obtenir des informations locales, consultez [Langues et pays/régions pris en charge pour Power BI](supported-languages-countries-regions.md).
5. La présentation PowerPoint inclut une diapositive de couverture indiquant l’heure d’exportation dans le fuseau horaire correct.

Lorsque vous accédez à une diapositive, vous remarquez que chaque page de rapport est une image indépendante.

>[!NOTE]
> Avoir un seul visuel pour chaque page du rapport est un nouveau comportement. Le comportement précédent, qui fournissait une image indépendante pour chaque visuel, n’est plus implémenté. 
 

![](media/service-publish-to-powerpoint/powerbi_to_powerpoint_6.png)

À partir de là, vous pouvez faire ce que vous voulez avec votre présentation PowerPoint ou les images haute résolution.

## <a name="limitations"></a>Limites
Voici quelques considérations et limitations à prendre en compte lorsque vous utilisez la fonctionnalité **Exporter vers PowerPoint**.

* Les **éléments visuels R** ne sont actuellement pas pris en charge. Tout élément visuel de ce type est exporté en tant qu’image vide dans PowerPoint, avec un message d’erreur indiquant que l’élément visuel n’est pas pris en charge.
* Les **éléments visuels personnalisés** qui ont été **certifiés** sont pris en charge. Pour plus d’informations sur les éléments visuels personnalisés certifiés, notamment concernant la manière de certifier un élément visuel personnalisé, voir [Obtention d’un visuel personnalisé certifié](power-bi-custom-visuals-certified.md). Les éléments visuel personnalisés non certifiés ne sont pas pris en charge. Tout élément visuel de ce type est exporté en tant qu’image vide dans PowerPoint, avec un message d’erreur indiquant que l’élément visuel n’est pas pris en charge.
* Les **visuels personnalisés certifiés** sont pris en charge. Un visuel personnalisé certifié a été approuvé pour une utilisation avec Power BI, répond à certaines exigences de code et a réussi des tests de sécurité stricts. Vous pouvez [en savoir plus **sur les visuels personnalisés certifiés**](power-bi-custom-visuals-certified.md).
* Les rapports contenant plus de 15 pages ne peuvent pas être exportés actuellement.
* Le processus d’exportation du rapport vers PowerPoint peut prendre quelques minutes. Soyez patient. Les facteurs qui peuvent avoir un impact sur la durée d’exportation sont la structure du rapport et la charge actuelle sur le service Power BI.
* Si l’option de menu **Exporter vers PowerPoint (version préliminaire)** n’est pas disponible dans le service Power BI, il est probable que votre administrateur ait désactivé la fonctionnalité. Pour plus d’informations, contactez l’administrateur du locataire.
* Les images en arrière-plan sont rognées en fonction du cadre englobant du graphique. Il est fortement recommandé de supprimer les images en arrière-plan avant d’exporter vers PowerPoint.
* L’**interactivité dans la session**, comme la mise en évidence et le filtrage, l’exploration, etc. n’est pas encore pris en charge lors de l’exportation vers PowerPoint. Le PowerPoint exporté montre les visuels d’origine tels qu’ils ont été enregistrés dans le rapport.
* Les pages dans PowerPoint sont toujours créées dans la taille standard 9:16, quelles que soient les tailles de page ou dimensions d’origine dans le rapport Power BI.
* Vous ne pouvez pas publier vers PowerPoint les rapports possédés par un utilisateur extérieur de votre domaine de locataire Power BI (par exemple, un rapport appartenant à une personne extérieure à votre organisation et partagé avec vous).
* Si vous partagez un tableau de bord avec une personne externe à votre organisation (et par conséquent, un utilisateur qui n’est pas dans votre locataire Power BI), cet utilisateur ne peut pas exporter vers PowerPoint les rapports associés du tableau de bord partagé. Par exemple, si vous êtes aaron@contoso.com, vous pouvez partager avec david@cohowinery.com. Mais david@cohowinery.com ne peut pas exporter les rapports associés vers PowerPoint.
* Comme mentionné précédemment, chaque page du rapport est exportée en tant qu’image unique dans le fichier PowerPoint.
* Le service Power BI utilise votre paramètre de langue Power BI pour l’exportation PowerPoint. Pour afficher ou définir vos préférences de langue, sélectionnez l’icône représentant une roue dentée ![](media/service-report-subscribe/power-bi-settings-icon.png) **> Paramètres > Général > Langue**.
* **L’heure de téléchargement** qui apparaît sur la diapositive de couverture du fichier PowerPoint exporté est définie en fonction du fuseau horaire de l’ordinateur au moment de l’exportation.

## <a name="next-steps"></a>Étapes suivantes
[Analyser dans Excel](service-analyze-in-excel.md)

[Données Excel dans Power BI](service-excel-workbook-files.md)

[Obtention d’un visuel personnalisé certifié](power-bi-custom-visuals-certified.md)

