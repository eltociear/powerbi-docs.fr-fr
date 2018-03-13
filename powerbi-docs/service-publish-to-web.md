---
title: "Publication sur le web à partir de Power BI"
description: "Avec la fonctionnalité Publier sur le web de Power BI, vous pouvez facilement incorporer des visualisations Power BI interactives en ligne, par exemple dans des billets de blog ou des sites web, par le biais d’e-mails ou de réseaux sociaux sur l’appareil de votre choix."
services: powerbi
documentationcenter: 
author: markingmyname
manager: kfile
backup: 
editor: 
tags: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 11/27/2017
ms.author: maghan
LocalizationGroup: Share your work
ms.openlocfilehash: ee1b403eaa8456266b452ff34814dc4f4059d9a6
ms.sourcegitcommit: 88c8ba8dee4384ea7bff5cedcad67fce784d92b0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/24/2018
---
# <a name="publish-to-web-from-power-bi"></a>Publication sur le web à partir de Power BI

Avec la fonctionnalité **Publier sur le web** de Power BI, vous pouvez facilement incorporer des visualisations Power BI interactives en ligne, par exemple dans des billets de blog ou des sites web, par le biais d’e-mails ou de réseaux sociaux sur l’appareil de votre choix.

Vous pouvez aussi facilement modifier, mettre à jour et actualiser vos éléments visuels publiés, ou encore en annuler le partage.

> [!WARNING]
> Quand vous utilisez la fonctionnalité **Publier sur le web**, le rapport ou visuel que vous publiez peut être consulté par tout le monde sur Internet. Aucune authentification n’est utilisée pour voir ces rapports. Utilisez uniquement la fonctionnalité Publier sur le web pour les rapports et données qui peuvent être vus par tout le monde sur Internet (membres non authentifiés du grand public). Cela inclut les données de niveau de détail qui sont agrégées dans vos rapports. Avant de publier ce rapport, vérifiez que vous avez le droit de partager les données et les visualisations publiquement. Ne publiez pas d’informations confidentielles ou propriétaires. En cas de doute, vérifiez les stratégies de votre organisation avant la publication.

## <a name="how-to-use-publish-to-web"></a>Comment utiliser Publier sur le web

La fonctionnalité **Publier sur le web** est disponible dans les rapports de vos espaces de travail personnel ou de groupe que vous pouvez modifier.  Vous ne pouvez pas l’utiliser avec les rapports qui ont été partagés avec vous ou ceux qui reposent sur la sécurité au niveau des lignes pour la sécurisation des données. Consultez la section **Limitations** ci-dessous pour obtenir la liste complète des situations où la publication sur le web n’est pas prise en charge. Reportez-vous à l’ **avertissement** plus haut dans cet article avant d’utiliser la fonctionnalité Publier sur le web.

Pour comprendre comment elle fonctionne, vous pouvez visionner la *petite vidéo*suivante. Ensuite, effectuez les étapes ci-dessous pour essayer vous-même cette fonctionnalité.

<iframe width="560" height="315" src="https://www.youtube.com/embed/UF9QtqE7s4Y" frameborder="0" allowfullscreen></iframe>


Les étapes suivantes décrivent comment utiliser **Publier sur le web**.

1. Dans un rapport sur votre espace de travail que vous pouvez modifier, sélectionnez **Fichier > Publier sur le web**
   
   ![](media/service-publish-to-web/publish_to_web1.png)

2. Lisez le contenu de la boîte de dialogue, puis sélectionnez **Créer un code incorporé** comme indiqué dans la boîte de dialogue suivante.
   
   ![](media/service-publish-to-web/publish_to_web2_ga.png)

3. Lisez l’avertissement, illustré dans la boîte de dialogue suivante, puis confirmez que les données peuvent être incorporées dans un site web public. Le cas échéant, sélectionnez **Publier**.
   
   ![](media/service-publish-to-web/publish_to_web3_ga.png)

4. Une boîte de dialogue s’affiche avec un lien que vous pouvez envoyer par e-mail, incorporer dans le code (comme un iFrame) ou coller directement dans votre page web ou votre blog.
   
   ![](media/service-publish-to-web/publish_to_web4.png)

5. Si vous avez déjà créé un code incorporé pour le rapport, celui-ci s’affiche rapidement. Vous pouvez créer un seul code incorporé pour chaque rapport.
   
   ![](media/service-publish-to-web/publish_to_web5.png)

## <a name="tips-and-tricks-for-view-modes"></a>Trucs et astuces pour les modes d’affichage

Quand vous incorporez du contenu dans un billet de blog, vous avez généralement besoin de l’ajuster à une taille d’écran spécifique.  Vous pouvez ajuster la hauteur et la largeur de la balise iFrame selon vos besoins, mais vous devez également vérifier que votre rapport tient dans la zone donnée de l’iFrame. C’est pourquoi vous devez également définir un mode d’affichage approprié quand vous modifiez le rapport.

Le tableau suivant fournit des instructions sur le mode d’affichage et les effets de son incorporation.

| Mode d’affichage | Son aspect quand il est incorporé |
| --- | --- |
| ![](media/service-publish-to-web/publish_to_web6b.png) |Le mode d’affichage **Ajuster à la page** respecte la hauteur et la largeur de page de votre rapport. Si vous définissez les proportions de votre page sur « Dynamique » (par exemple 16:9 ou 4:3), votre contenu est ajusté à l’iFrame que vous avez fourni. En cas d’incorporation dans un iFrame, l’utilisation de l’option **Ajuster à la page** risque de générer un **cadre**, où un fond gris est affiché dans des zones de l’iFrame après que le contenu a été mis à l’échelle de manière à s’ajuster à l’iFrame. Pour diminuer le cadre, définissez la hauteur et la largeur de votre iFrame de manière appropriée. |
| ![](media/service-publish-to-web/publish_to_web6d.png) |Avec le mode d’affichage **Taille réelle**, le rapport conserve sa taille telle qu’elle est définie dans la page de rapport. Du coup, des barres de défilement peuvent apparaître dans votre iFrame. Définissez-les afin d’éviter les barres de défilement. |
| ![](media/service-publish-to-web/publish_to_web6c.png) |Avec le mode d’affichage **Ajuster à la largeur**, le contenu tient dans la zone horizontale de votre iFrame. Une bordure apparaît quand même, mais le contenu est mis à l’échelle pour utiliser tout l’espace horizontal disponible. |

## <a name="tips-and-tricks-for-iframe-height-and-width"></a>Conseils et astuces pour la hauteur et la largeur de l’iFrame

Le code incorporé que vous recevez après une publication sur le web ressemble à ceci :

![](media/service-publish-to-web/publish_to_web7.png)

Vous pouvez modifier manuellement la largeur et la hauteur pour vous assurer que le code s’adapte exactement à la page dans laquelle vous l’incorporez.

Pour obtenir un ajustement idéal, vous pouvez essayer d’ajouter 56 pixels à la hauteur de l’iFrame. Cela correspond à la taille actuelle de la barre inférieure. Si la page de votre rapport utilise la taille dynamique, le tableau ci-dessous fournit des tailles que vous pouvez utiliser pour obtenir un ajustement sans cadre.

| Proportions | Taille | Dimensions (largeur x hauteur) |
| --- | --- | --- |
| 16:9 |Petite |640 x 416 px |
| 16:9 |Moyenne |800 x 506 px |
| 16:9 |Grande |960 x 596 px |
| 4:3 |Petite |640 x 536 px |
| 4:3 |Moyenne |800 x 656 px |
| 4:3 |Grande |960 x 776 px |

## <a name="managing-embed-codes"></a>Gestion des codes incorporés

Une fois que vous avez créé un code incorporé **Publier sur le web** , vous pouvez le gérer à partir du menu **Paramètres** du service Power BI. Si vous gérez des codes incorporés, vous pouvez supprimer l’élément visuel ou le rapport de destination d’un code (ce qui rend le code incorporé inutilisable) ou récupérer celui-ci.

1. Pour gérer vos codes incorporés **Publier sur le web** , ouvrez **Paramètres** et sélectionnez **Gérer des codes incorporés**.
   
   ![](media/service-publish-to-web/publish_to_web8.png)

2. La liste des codes incorporés que vous avez créés s’affiche, comme illustré dans l’image suivante.
   
   ![](media/service-publish-to-web/publish_to_web9.png)

3. Vous pouvez récupérer ou supprimer chaque code incorporé **Publier sur le web** figurant dans la liste. Une suppression rend inutilisable tous les liens vers le rapport ou l’élément visuel correspondant.
   
   ![](media/service-publish-to-web/publish_to_web10.png)

4. Si vous sélectionnez **Supprimer**, vous devez indiquer si vous êtes certain de vouloir supprimer le code incorporé.
   
   ![](media/service-publish-to-web/publish_to_web11.png)

## <a name="updates-to-reports-and-data-refresh"></a>Mises à jour des rapports et actualisation des données

Après avoir créé et partagé votre code incorporé **Publier sur le web** , le rapport est mis à jour avec les modifications que vous apportez. Toutefois, il est important de savoir que la mise à jour peut mettre du temps avant que vos utilisateurs puissent la voir. Les mises à jour apportées à un rapport ou élément visuel prennent environ une heure pour apparaître dans les codes incorporés Publier sur le web.

Au départ, quand vous utilisez la fonctionnalité **Publier sur le web** pour obtenir un code incorporé, le lien du code incorporé est immédiatement actif et visible par toute personne qui l’ouvre.  Après cette première action, il faudra environ une heure pour que les utilisateurs puissent voir les mises à jour de rapports ou d’éléments visuels vers lesquels pointe un lien Publier sur le web.

Pour en savoir plus, consultez la section **Fonctionnement** plus loin dans cet article. Si vous avez besoin que vos mises à jour soient disponibles immédiatement, vous pouvez supprimer le code incorporé et en créer un nouveau.

## <a name="data-refresh"></a>Actualisation des données

Les actualisations de données sont répercutées automatiquement dans votre rapport ou élément visuel incorporé. Un délai d’environ une heure peut être nécessaire pour que les données actualisées soient visibles à partir des codes incorporés. Vous pouvez désactiver l’actualisation automatique en sélectionnant **Ne pas actualiser** dans la planification du jeu de données utilisé par le rapport.  

## <a name="custom-visuals"></a>Éléments visuels personnalisés

Les éléments visuels personnalisés sont pris en charge par la fonctionnalité **Publier sur le web**. Quand vous utilisez la fonctionnalité Publier sur le web, les utilisateurs avec lesquels vous partagez votre élément visuel publié n’ont pas besoin d’activer les éléments visuels personnalisés pour afficher le rapport.

## <a name="limitations"></a>Limites

La fonctionnalité **Publier sur le web** est prise en charge pour la majeure partie des sources de données et rapports du service Power BI. Toutefois, les éléments suivants ne sont ni pris en charge ni disponibles avec la fonctionnalité Publier sur le web pour le moment :

1. Rapports qui utilisent la sécurité au niveau des lignes
2. Rapports qui utilisent une source de données de connexion active, notamment une source de données tabulaire Analysis Services hébergée localement, une source de données multidimensionnelle Analysis Services, Azure Analysis Services et le service Power BI.
3. Rapports partagés directement ou via un pack de contenu d’organisation
4. Rapports d’un groupe dans lequel vous n’êtes pas un membre doté d’autorisations de modification
5. Les éléments visuels R ne sont pas actuellement pris en charge dans les rapports Publier sur le web.

## <a name="tenant-setting"></a>Paramètres de locataire

Les administrateurs Power BI peuvent activer ou désactiver la fonctionnalité de publication sur le web. Ils peuvent également restreindre l’accès à des groupes spécifiques. Votre capacité à créer un code incorporé change en fonction de ce paramètre.

|Fonctionnalité |Activée pour toute l’organisation |Désactivée pour toute l’organisation |Groupes de sécurité spécifiques   |
|---------|---------|---------|---------|
|**Publier sur le web** sous le menu **Fichier** du rapport.|Activée pour tous|Non visible pour tous|Visible uniquement par les utilisateurs ou groupes autorisés.|
|**Gérer les codes d’incorporation** sous **Paramètres**|Activée pour tous|Activée pour tous|Activée pour tous<br><br>Option * **Supprimer** uniquement pour les utilisateurs ou groupes autorisés.<br>* **Obtenir les codes** activé pour tous.|
|**Codes d’incorporation** au sein du portail d’administration|L’état reflète une des options suivantes :<br>* Actif<br>* Non pris en charge<br>* Bloqué|L’état affiche **Désactivé**|L’état reflète une des options suivantes :<br>* Actif<br>* Non pris en charge<br>* Bloqué<br><br>Si un utilisateur n’est pas autorisé en fonction du paramètre de locataire, l’état affiche **violation**.|
|Rapports publiés existants|Tout activé|Tout désactivé|Les rapports continuent à être restitués pour tous.|

## <a name="understanding-the-embed-code-status-column"></a>Présentation de la colonne d’état du code incorporé

Quand vous affichez la page **Gérer des codes incorporés** de vos codes incorporés **Publier sur le web** , une colonne d’état est fournie. Les codes incorporés sont actifs par défaut, mais vous pouvez rencontrer un des états répertoriés ci-dessous.

| État | Description |
| --- | --- |
| **Actif** |Le rapport est à la disposition des utilisateurs Internet qui peuvent l’afficher et interagir avec. |
| **Bloqué** |Le contenu du rapport ne respecte pas les [conditions d’utilisation de Power BI](https://powerbi.microsoft.com/terms-of-service). Il a été bloqué par Microsoft. Si vous pensez que le contenu a été bloqué par erreur, contactez le support. |
| **Non pris en charge** |Le jeu de données du rapport utilise la sécurité au niveau des lignes ou une autre configuration non prise en charge. Pour obtenir la liste complète, consultez la section **Limitations**. |
| **Enfreint** |Le code incorporé est en dehors de la stratégie de locataire définie. Cela se produit généralement lorsqu’un code incorporé a été créé et que le paramètre de locataire pour la publication sur le web a été modifié de façon à exclure l’utilisateur qui possède le code incorporé. Si le paramètre de locataire est désactivé ou que l’utilisateur n’est plus autorisé à créer des codes incorporés, les codes incorporés existants affichent l’état **Enfreint**. |

## <a name="how-to-report-a-concern-with-publish-to-web-content"></a>Comment signaler un problème lié à du contenu Publier sur le web

Pour signaler un problème lié à du contenu **Publier sur le web** incorporé dans un site web ou un blog, utilisez l’icône représentant un **drapeau** située dans la barre inférieure, illustrée dans l’image suivante. Vous êtes invité à envoyer un e-mail à Microsoft pour expliquer le problème. Microsoft évalue le contenu au regard des conditions d’utilisation de Power BI et prend les mesures nécessaires.

Pour signaler un problème, sélectionnez l’icône représentant un **drapeau** dans la barre inférieure du rapport Publier sur le rapport que vous êtes en train de consulter.

![](media/service-publish-to-web/publish_to_web12_ga.png)

## <a name="licensing-and-pricing"></a>Gestion des licences et tarification

Vous devez être un utilisateur de Microsoft Power BI pour utiliser la fonctionnalité **Publier sur le web**. Les utilisateurs de votre rapport (lecteurs) n’ont pas besoin d’être des utilisateurs de Power BI.

## <a name="how-it-works-technical-details"></a>Fonctionnement (détails techniques)

Quand vous créez un code incorporé à l’aide de la fonctionnalité **Publier sur le web**, vous permettez aux utilisateurs Internet de voir le rapport. Comme votre rapport est disponible publiquement, vous pouvez vous attendre à ce que des lecteurs le partagent facilement au moyen des réseaux sociaux. Quand les utilisateurs consultent le rapport, soit en ouvrant l’URL publique directe, soit en le consultant incorporé dans une page web ou un blog, Power BI met en cache la définition du rapport et les résultats des requêtes requises pour l’afficher. Cette approche garantit que le rapport est consultable par des milliers d’utilisateurs simultanés sans aucun impact sur les performances.  

Le cache est un cache à long terme, donc si vous mettez à jour la définition du rapport (par exemple, si vous changez son mode d’affichage) ou actualisez les données du rapport, vous devez attendre environ une heure avant que les modifications ne soient répercutées dans la version du rapport consultée par vos utilisateurs. Il est donc recommandé d’anticiper votre travail et de créer le code incorporé **Publier sur le web** uniquement quand vous êtes satisfait des paramètres.

D’autres questions ? [Posez vos questions à la communauté Power BI](http://community.powerbi.com/)