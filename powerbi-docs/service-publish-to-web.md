---
title: Publication sur le web à partir de Power BI
description: Avec la fonctionnalité Publier sur le web de Power BI, vous pouvez facilement incorporer des visualisations Power BI interactives en ligne, par exemple dans des billets de blog ou des sites web, par le biais d’e-mails ou de réseaux sociaux sur l’appareil de votre choix.
author: rkarlin
ms.author: rkarlin
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 05/16/2019
LocalizationGroup: Share your work
ms.openlocfilehash: 1b5dfc0b05595e96c9a297a5be3700e71cdbe229
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66051581"
---
# <a name="publish-to-web-from-power-bi"></a>Publication sur le web à partir de Power BI

Avec Power BI **publier sur le web** option, vous pouvez facilement incorporer des visualisations Power BI interactives en ligne, comme dans billets de blog, sites Web, par le biais des e-mails ou des médias sociaux, à partir de n’importe quel appareil. Vous pouvez également modifier, mettre à jour ou actualiser vos éléments visuels publiés, ou bien annuler leur partage.

> [!WARNING]
> Lorsque vous utilisez **publier sur le web**, toute personne sur Internet permettre afficher votre rapport publié ou un visuel. Cela ne requiert aucune authentification et notamment l’affichage des données de détail vos rapports agrégation. Avant de publier un rapport, assurez-vous qu’il est OK, vous pouvez partager les données et les visualisations publiquement. Ne publiez pas d’informations confidentielles ou propriétaires. En cas de doute, vérifiez les stratégies de votre organisation avant la publication.

>[!Note]
>Pour incorporer votre contenu en toute sécurité dans un portail interne ou site web, utilisez les options [Incorporer](service-embed-secure.md) ou [Incorporer dans SharePoint Online](service-embed-report-spo.md). Cela garantit que toutes les autorisations et la sécurité des données sont appliquées lorsque vos utilisateurs affichent vos données internes.

## <a name="how-to-use-publish-to-web"></a>Comment utiliser Publier sur le web

**Publier sur le web** est disponible pour les rapports dans vos espaces de travail personnels ou de groupes que vous pouvez modifier.  Il n’est pas disponible pour les rapports partagés avec vous ou ceux s’appuyer sur la sécurité au niveau des lignes pour sécuriser les données. Consultez le [ **Limitations** ](#limitations) section ci-dessous pour obtenir la liste complète des cas où **publier sur le web** n’est pas pris en charge. Examinez le **avertissement** plus haut dans cet article avant d’utiliser **publier sur le web**.

Ce qui suit *courte vidéo* illustre le fonctionnement de cette fonctionnalité. Ensuite, essayez par vous-même dans les étapes ci-dessous.

<iframe width="560" height="315" src="https://www.youtube.com/embed/UF9QtqE7s4Y" frameborder="0" allowfullscreen></iframe>

Les étapes suivantes décrivent comment utiliser **Publier sur le web**.

1. Ouvrir un rapport dans votre espace de travail que vous pouvez modifier et sélectionnez **fichier > publier sur le web**.

   ![PtW1](media/service-publish-to-web/publish_to_web1.png)

2. Passez en revue la boîte de dialogue contenu et sélectionnez **créer un code incorporé**.

   ![PtW2](media/service-publish-to-web/publish_to_web2_ga.png)

3. Lisez l’avertissement, comme illustré ici et vérifiez que les données sont OK à incorporer dans un site Web public. Dans le cas, sélectionnez **publier**.

   ![PtW3](media/service-publish-to-web/publish_to_web3_ga.png)

4. Une boîte de dialogue s’affiche avec un lien. Vous pouvez envoyer ce lien dans un message électronique, l’incorporer dans le code comme un iFrame ou coller directement dans une page web ou votre blog.

   ![PtW4](media/service-publish-to-web/publish_to_web4.png)

5. Si vous avez créé précédemment un code incorporé pour un rapport et que vous sélectionnez **publier sur le web**, vous ne verrez pas les boîtes de dialogue dans les étapes 2 à 4. Au lieu de cela, le **code incorporé** boîte de dialogue s’affiche :

   ![PtW5](media/service-publish-to-web/publish_to_web5.png)

   Vous pouvez créer un seul code incorporé pour chaque rapport.


## <a name="tips-and-tricks-for-view-modes"></a>Trucs et astuces pour les modes d’affichage

Lorsque vous incorporez du contenu au sein d’un billet de blog, vous devez généralement ajuster à une taille d’écran spécifique.  Vous pouvez ajuster la hauteur et la largeur de la balise iFrame selon vos besoins. Toutefois, vous devez vous assurer de que votre rapport tient dans la zone de l’iFrame donné, vous devez également définir un Mode d’affichage approprié lors de la modification du rapport.

Le tableau suivant fournit des instructions sur le mode d’affichage et les effets de son incorporation.

| Mode d’affichage | Son aspect quand il est incorporé |
| --- | --- |
| ![PtW6b](media/service-publish-to-web/publish_to_web6b.png) |**Ajuster à la page** respecte la hauteur de page et la largeur de votre rapport. Si vous définissez votre page de rapports « Dynamique » comme 16:9 ou 4:3 votre contenu sera ajusté l’iFrame. Lorsqu’il est incorporé dans un iFrame, à l’aide **ajuster à la page** peut entraîner **cadre**, où un fond gris est affiché dans les zones de l’iFrame après le contenu comme mise à l’échelle pour s’ajuster au iFrame. Pour diminuer le cadre, définissez votre d’iFrame hauteur et largeur en conséquence. |
| ![PtW6d](media/service-publish-to-web/publish_to_web6d.png) |**Taille réelle** garantit le rapport conserve sa taille telle que définie sur la page de rapport. Cela peut entraîner les barres de défilement qui apparaissent dans votre iFrame. Définir la hauteur de l’iFrame et la largeur pour éviter les barres de défilement. |
| ![PtW6c](media/service-publish-to-web/publish_to_web6c.png) |**Ajuster à la largeur** le contenu tient dans la zone horizontale de l’iFrame. Une bordure est toujours affichée, mais le contenu s’adapte pour utiliser tout l’espace horizontal disponible. |

## <a name="tips-and-tricks-for-iframe-height-and-width"></a>Conseils et astuces pour la hauteur et la largeur de l’iFrame

Un **publier sur le web** incorporer le code ressemble à ce qui suit :

![PtW7](media/service-publish-to-web/publish_to_web7.png)
 
Vous pouvez modifier la largeur et la hauteur manuellement afin de garantir que précisément comment vous le souhaitez pour tenir dans la page où vous l’incorporez.

Pour obtenir un ajustement idéal, vous pouvez essayer d’ajouter 56 pixels à hauteur de l’iFrame pour prendre en compte la taille actuelle de la barre inférieure. Si la page de votre rapport utilise la taille dynamique, le tableau ci-dessous fournit des tailles que vous pouvez utiliser pour obtenir un ajustement sans cadre.

| Proportions | Taille | Dimensions (largeur x hauteur) |
| --- | --- | --- |
| 16:9 |Petite |640 x 416 px |
| 16:9 |Moyenne |800 x 506 px |
| 16:9 |Grande |960 x 596 px |
| 4:3 |Petite |640 x 536 px |
| 4:3 |Moyenne |800 x 656 px |
| 4:3 |Grande |960 x 776 px |

## <a name="manage-embed-codes"></a>Gérer des codes incorporés

Une fois que vous créez un **publier sur le web** incorporer du code, vous pouvez gérer vos codes de la **paramètres** menu dans Power BI. Gestion des codes incorporés inclut la possibilité de supprimer la destination visual ou un rapport pour un code (ce qui rend le code incorporé inutilisable), ou bien le code incorporé.

1. Pour gérer vos codes incorporés **Publier sur le web** , ouvrez **Paramètres** et sélectionnez **Gérer des codes incorporés**.

   ![PtW8](media/service-publish-to-web/publish_to_web8.png)

2. Vos codes incorporés s’affichent.

   ![PtW9](media/service-publish-to-web/publish_to_web9.png)

3. Vous pouvez récupérer ou supprimer un code incorporé. Sa suppression désactive tous les liens vers ce rapport ou élément visuel.

   ![PtW10](media/service-publish-to-web/publish_to_web10.png)

4. Si vous sélectionnez **supprimer**, vous êtes invité à confirmer.

   ![PtW11](media/service-publish-to-web/publish_to_web11.png)

## <a name="updates-to-reports-and-data-refresh"></a>Mises à jour des rapports et actualisation des données

Après avoir créé votre **publier sur le web** code incorporé et partage, le rapport est à jour avec toutes les modifications que vous apportez et le lien du code incorporé est immédiatement actif et toute personne qui ouvre le lien peut les afficher. Toutefois, après l’action initiale, mises à jour des rapports ou d’éléments visuels peuvent prendre environ une heure avant de devenir visible par vos utilisateurs. Si vous avez besoin que vos mises à jour soient disponibles immédiatement, vous pouvez supprimer le code incorporé et en créer un nouveau. Pour plus d’informations, consultez le [ **son fonctionnement** ](#howitworks) section plus loin dans cet article. 

## <a name="data-refresh"></a>Actualisation des données

Les actualisations de données sont répercutées automatiquement dans votre rapport ou élément visuel incorporé. Un délai d’environ une heure peut être nécessaire pour que les données actualisées soient visibles à partir des codes incorporés. Pour désactiver l’actualisation automatique, vous pouvez sélectionner **ne s’actualisent pas** sur la planification pour le jeu de données que le rapport utilise.  

## <a name="custom-visuals"></a>Visuels personnalisés

Les éléments visuels personnalisés sont pris en charge par la fonctionnalité **Publier sur le web**. Lorsque vous utilisez **publier sur le web**, les utilisateurs avec lesquels vous partagez votre élément visuel publié n’êtes pas obligé d’activer les visuels personnalisés afficher le rapport.

## <a name="limitations"></a>Limites

**Publier sur le web** est pris en charge pour la grande majorité des données sources et des rapports dans le service Power BI, toutefois, les éléments suivants sont **pas actuellement pris en charge ou disponible** avec **publier sur le web** :

- Rapports qui utilisent la sécurité au niveau des lignes
- Rapports qui utilisent une source de données de connexion active, notamment une source de données tabulaire Analysis Services hébergée localement, une source de données multidimensionnelle Analysis Services et Azure Analysis Services.
- Rapports partagés directement ou via un pack de contenu d’organisation
- Rapports d’un groupe dans lequel vous n’êtes pas un membre doté d’autorisations de modification
- « R » visuels ne sont pas actuellement pris en charge dans **publier sur le web** rapports.
- Exportation de données à partir de visuels dans un rapport, ce qui a été publié sur le web.
- ArcGIS Maps for Power BI les éléments visuels.
- Rapports contenant des mesures DAX au niveau du rapport.
- Modèles de requête de données de l’authentification unique.
- [Sécuriser les informations confidentielles ou propriétaires](#publish-to-web-from-power-bi).
- La fonctionnalité d’authentification automatique fournie avec l’option **Incorporer** ne fonctionne pas avec l’API JavaScript Power BI. Pour l’API JavaScript Power BI, utilisez l’approche [les données appartiennent à l’utilisateur](developer/embed-sample-for-your-organization.md) pour l’incorporation. En savoir plus sur [les données appartiennent à l’utilisateur](developer/embed-sample-for-your-organization.md).

## <a name="tenant-setting"></a>Paramètres de locataire

Les administrateurs Power BI peuvent activer ou désactiver la **publier sur le web** fonctionnalité. Ils peuvent également restreindre l’accès à des groupes spécifiques, ce qui peuvent avoir un impact sur votre capacité à créer un code incorporé.

|Caractéristique |Activée pour toute l’organisation |Désactivée pour toute l’organisation |Groupes de sécurité spécifiques   |
|---------|---------|---------|---------|
|**Publier sur le web** sous du rapport **fichier** menu|Activée pour tous|Non visible pour tous|Visible uniquement par les utilisateurs ou groupes autorisés.|
|**Gérer les codes d’incorporation** sous **Paramètres**|Activée pour tous|Activée pour tous|Activé pour tous.<br><br>Option * **Supprimer** uniquement pour les utilisateurs ou groupes autorisés.<br>* **Obtenir les codes** activé pour tous.|
|**Codes d’incorporation** au sein du portail d’administration|L’état reflète une des options suivantes :<br>* Actif<br>* Non pris en charge<br>* Bloqué|L’état affiche **Désactivé**|L’état reflète une des options suivantes :<br>* Actif<br>* Non pris en charge<br>* Bloqué<br><br>Si un utilisateur n’est pas autorisé en fonction du paramètre de locataire, l’état affiche **violation**.|
|Rapports publiés existants|Tout activé|Tout désactivé|Les rapports continuent à être restitués pour tous.|

## <a name="understanding-the-embed-code-status-column"></a>Présentation de la colonne d’état du code incorporé

Le **gérer des codes incorporés** page comprend une colonne d’état. Par défaut, les codes incorporés sont **Active**, mais peut également être un des états répertoriés ci-dessous.

| État | Description |
| --- | --- |
| **Actif** |Le rapport est à la disposition des utilisateurs Internet qui peuvent l’afficher et interagir avec. |
| **Bloqué** |Le contenu du rapport ne respecte pas la [conditions d’utilisation de Power BI](https://powerbi.microsoft.com/terms-of-service). Microsoft l’a bloqué. Si vous pensez que le contenu a été bloqué par erreur, contactez le support. |
| **Non pris en charge** |Le jeu de données du rapport utilise la sécurité au niveau des lignes ou une autre configuration non prise en charge. Consultez le [ **Limitations** ](#limitations) section pour obtenir la liste complète. |
| **Enfreint** |Le code incorporé est en dehors de la stratégie de locataire définie. Cela se produit généralement quand un code incorporé a été créé, puis le **publier sur le web** paramètre du client a été modifié pour exclure l’utilisateur qui possède le code incorporé. Si le paramètre du client est désactivé, ou l’utilisateur n’est plus autorisée à créer des codes incorporés, afficher des codes d’incorporés existants une **enfreint** état. |

## <a name="how-to-report-a-concern-with-publish-to-web-content"></a>Comment signaler un problème lié à du contenu Publier sur le web

À signaler un problème lié à **publier sur le web** contenu incorporé dans un site Web ou un blog, utilisez le **indicateur** icône dans la barre inférieure, comme illustré dans l’image suivante. Vous devez envoyer un e-mail à Microsoft expliquant votre préoccupation. Microsoft évalue le contenu selon les termes du contrat de Service Power BI et agir en conséquence.

Pour signaler un problème, sélectionnez le **indicateur** icône dans la barre en bas de la **publier sur le web** vous voyez de rapports.

![PtW12](media/service-publish-to-web/publish_to_web12_ga.png)

## <a name="licensing-and-pricing"></a>Gestion des licences et tarification

Vous devez être un utilisateur de Microsoft Power BI pour utiliser la fonctionnalité **Publier sur le web**. Les visionneuses de votre rapport est inutile pour les utilisateurs de Power BI.

<a name="howitworks"></a>
## <a name="how-it-works-technical-details"></a>Fonctionnement (détails techniques)

Lorsque vous créez un code incorporé à l’aide **publier sur le web**, le rapport est rendu visible aux utilisateurs d’Internet. Il est disponible publiquement, donc vous pouvez vous attendre visionneuses facilement partager le rapport via des médias sociaux à l’avenir. Quand les utilisateurs consultent le rapport, soit en ouvrant l’URL publique directe, soit en le consultant incorporé dans une page web ou un blog, Power BI met en cache la définition du rapport et les résultats des requêtes requises pour l’afficher. Cela garantit que des milliers d’utilisateurs simultanés peuvent afficher le rapport sans affecter les performances.

Le cache est à long terme, donc si vous mettez à jour la définition de rapport (par exemple, si vous changez son mode d’affichage) ou actualisez les données de rapport, il peut prendre environ une heure avant que les modifications sont répercutées dans la version du rapport que permet d’afficher vos utilisateurs. Il est donc recommandé d’anticiper votre travail et de créer le code incorporé **Publier sur le web** uniquement quand vous êtes satisfait des paramètres.

## <a name="next-steps"></a>Étapes suivantes

- [Composant web du rapport SharePoint Online](service-embed-report-spo.md) 

- [Incorporer un rapport dans un site web ou portail sécurisé](service-embed-secure.md)

D’autres questions ? [Posez vos questions à la communauté Power BI](http://community.powerbi.com/)
