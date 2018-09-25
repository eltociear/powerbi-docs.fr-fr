---
title: Ajouter un image, du texte, une vidéo, des données de streaming à votre tableau de bord
description: Documentation sur la façon d’utiliser le widget Ajouter une vignette pour ajouter une vignette d’image, de vidéo, de zone de texte, de code web de données de streaming à un tableau de bord.
author: mihart
manager: kfile
ms.reviewer: ''
featuredvideoid: e2PD8m1Q0vU
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 03/02/2018
ms.author: mihart
LocalizationGroup: Dashboards
ms.openlocfilehash: 68195883f2aad0f3131ec14c508334ac41cd918b
ms.sourcegitcommit: 0ff358f1ff87e88daf837443ecd1398ca949d2b6
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/21/2018
ms.locfileid: "46545863"
---
# <a name="add-image-text-video-and-more-to-your-dashboard"></a>Ajouter des images, du texte, de la vidéo, etc. à votre tableau de bord
<iframe width="560" height="315" src="https://www.youtube.com/embed/e2PD8m1Q0vU" frameborder="0" allowfullscreen></iframe>


## <a name="add-tile"></a>Ajouter une vignette
Le contrôle **Ajouter une vignette** vous permet d’ajouter directement une image, une zone de texte, une vidéo, des données de streaming ou du code web à votre tableau de bord.

1. Sélectionnez **Ajouter une vignette** dans la barre de menus supérieure. Selon les limitations d’espace, vous pouvez voir uniquement le signe plus ![signe plus](media/service-dashboard-add-widget/power-bi-add-tile-icon-small.png).
   
    ![icône Ajouter une vignette](media/service-dashboard-add-widget/power-bi-add-tile-icon.png)
2. Sélectionnez le type de vignette à ajouter : **Image**, **Zone de texte**, **Vidéo**, **Contenu web** ou **Données de streaming personnalisées**.
   
    ![fenêtre Ajouter une vignette](media/service-dashboard-add-widget/power-bi-add-tile.png)

## <a name="add-an-image"></a>Ajouter une image
Supposons que vous voulez faire figurer le logo de votre entreprise ou toute autre image sur le tableau de bord. Vous devez enregistrer le fichier image en ligne et lui associer un lien. Vérifiez que des informations d’identification spéciales ne sont pas nécessaires pour accéder au fichier image. Par exemple, OneDrive et SharePoint requièrent l’authentification et les images qui y sont stockées ne peuvent pas être ajoutées à un tableau de bord de cette façon.  

1. Sélectionnez **Image** > **Suivant**.
2. Ajoutez des informations sur l’image dans la fenêtre **Ajouter une vignette d’image**.
   
    ![fenêtre Ajouter une vignette d’image](media/service-dashboard-add-widget/pbi-widget-add-image-new.png)
   
   * Pour afficher un titre au-dessus de l’image, sélectionnez *Afficher le titre et le sous-titre* et tapez un titre et/ou un sous-titre.
   * Entrez l’URL de l’image.
   * Pour transformer la vignette en lien hypertexte, sélectionnez **Définir un lien personnalisé** et entrez l’URL.  Quand vos collègues cliquent sur cette image ou sur un titre, ils sont dirigés vers cette URL.
   * Sélectionnez **Appliquer**.  Dans le tableau de bord, redimensionnez et déplacez l’image selon vos besoins.
     
     ![image sur le tableau de bord](media/service-dashboard-add-widget/power-bi-add-image-dash.png)

## <a name="add-a-text-box-or-dashboard-heading"></a>Ajouter une zone de texte ou un en-tête de tableau de bord
1. Sélectionnez **Zone de texte > Suivant**.
   
   > **Remarque** : Pour ajouter un en-tête de tableau de bord, tapez l’en-tête dans la zone de texte et augmentez la taille de la police.
   > 
2. Mettez en forme la zone de texte :
   
   * Pour afficher un titre au-dessus de la zone de texte, sélectionnez **Afficher le titre et le sous-titre** et tapez un titre et/ou un sous-titre.
   * Entrez et mettez en forme le contenu de la zone de texte.  
   * Définissez éventuellement un lien personnalisé pour le titre. Un lien personnalisé peut être un site externe ou un tableau de bord ou rapport dans votre espace de travail. En revanche, dans cet exemple, nous avons ajouté des liens hypertexte dans la zone de texte elle-même, alors laissez la case **Définir un lien personnalisé** décochée.

     ![fenêtre Ajouter une vignette de zone de texte](media/service-dashboard-add-widget/power-bi-add-textbox.png)
   
3. Sélectionnez **Appliquer**.  Dans le tableau de bord, redimensionnez et déplacez la zone de texte selon vos besoins.
   
   ![tableau de bord avec une image et une zone de texte](media/service-dashboard-add-widget/pbi-widget-text-added-new.png)

## <a name="add-a-video"></a>Ajouter une vidéo
Quand vous ajoutez une vignette de vidéo YouTube ou Vimeo à votre tableau de bord, la vidéo est lue directement dans votre tableau de bord.

1. Sélectionnez **Vidéo > Suivant**.
2. Ajoutez des informations sur la vidéo dans la fenêtre **Ajouter une vignette de vidéo**.
   
    ![fenêtre Ajouter une vignette de vidéo](media/service-dashboard-add-widget/power-bi-add-video-new.png)
   
   * Pour afficher un titre et un sous-titre en haut de la vignette vidéo, sélectionnez *Afficher le titre et le sous-titre* et tapez un titre et/ou un sous-titre. Dans cet exemple, nous ajoutons un sous-titre, puis nous le transformons en lien hypertexte dans la playlist sur YouTube.
   * Entrez l’URL de la vidéo.
   * Ajoutez un lien hypertexte pour le titre et le sous-titre.  Vous voulez peut-être que vos collègues, après avoir visionné la vidéo incorporée, puissent accéder à toute la playlist sur YouTube : ajoutez un lien vers votre playlist ici.
   * Sélectionnez **Appliquer**.  Dans le tableau de bord, redimensionnez et déplacez la vidéo selon vos besoins.
     
      ![tableau de bord avec la vignette de vidéo ajoutée](media/service-dashboard-add-widget/pbi-widget-video-added-new.png)
3. Sélectionnez la vignette de la vidéo pour lire la vidéo.
4. Sélectionnez le sous-titre pour accéder à la playlist sur YouTube.

## <a name="add-streaming-data"></a>Ajouter des données de streaming
<iframe width="560" height="315" src="https://www.youtube.com/embed/kOuINwgkEkQ" frameborder="0" allowfullscreen></iframe>

## <a name="add-web-content"></a>Ajouter du contenu web
Collez ou saisissez n’importe quel contenu HTML.  Power BI l’ajoute à votre tableau de bord sous forme de vignette. Entrez le code intégré manuellement ou copiez et collez-le à partir de sites tels que Twitter, YouTube, embed.ly et bien plus encore.

1. Sélectionnez **Contenu web > Suivant**.
2. Ajoutez des informations dans le volet **Ajouter une vignette de contenu web**.
   
    ![fenêtre Ajouter une vignette de contenu web](media/service-dashboard-add-widget/power-bi-add-web-content.png)
   
   * Pour afficher un titre au-dessus de la vignette, sélectionnez *Afficher le titre et le sous-titre* et tapez un titre et/ou un sous-titre.
   * Entrez le code incorporé. Dans cet exemple, nous allons copier et coller un flux Twitter.
3. Sélectionnez **Appliquer**.  Dans le tableau de bord, redimensionnez et déplacez le contenu web selon vos besoins.
     
      ![tableau de bord avec 4 vignettes](media/service-dashboard-add-widget/pbi-widget-code-added-new.png)

## <a name="tips-for-embedding-web-content"></a>Conseils pour l'incorporation de contenu web
* Pour des IFrames, utilisez une source sécurisée. Si vous entrez votre code intégré d’IFrame et obtenez une vignette vide, vérifiez si le protocole **http** est utilisé pour la source IFrame.  Dans ce cas, remplacez-le par **https**.
  
  ```
  <iframe src="https://xyz.com">
  ```
* Modifiez les informations de largeur et de hauteur. Ce code intégré incorpore une vidéo et définit le lecteur vidéo à 560 x 315 pixels.  Cette taille ne change pas lors du redimensionnement de la vignette.
  
  ```
  <iframe width="560" height="315"
  src="https://www.youtube.com/embed/Cle_rKBpZ28" frameborder="0"
   allowfullscreen></iframe>
  ```
  
  Si vous souhaitez que le lecteur doit être redimensionné pour s'ajuster à la taille de la vignette, définissez sa largeur et sa hauteur à 100 %.
  
  ```
  <iframe width="100%" height="100%"
  src="https://www.youtube.com/embed/Cle_rKBpZ28" frameborder="0"
   allowfullscreen></iframe>
  ```
* Ce code incorpore un tweet et conserve, sous forme de liens séparés dans le tableau de bord, des liens pour les éléments suivants : podcast **AFK** , **page Twitter de @GuyInACube**, **Suivre**, **#analytics**, **répondre**, **retweeter** et **j’aime**.  Sélectionner la vignette elle-même ouvre le podcast sur Twitter.
  
  ```
  <blockquote class="twitter-tweet" data-partner="tweetdeck">
  <p lang="en" dir="ltr">Listen to
  <a href="https://twitter.com/GuyInACube">@GuyInACube</a> talk to
  us about making videos about Microsoft Business Intelligence
  platform
  <a href="https://t.co/TmRgalz7tv">https://t.co/TmRgalz7tv </a>
  <a href="https://twitter.com/hashtag/analytics?src=hash">
  #analytics</a></p>&mdash; AFTK Podcast (@aftkpodcast) <a
  href="https://twitter.com/aftkpodcast/status/693465456531771392">
  January 30, 2016</a></blockquote> <script async src="//platform.twitter.com/widgets.js" charset="utf-8"></script>
  ```

## <a name="edit-a-tile"></a>Modifier une vignette
Pour apporter des modifications à une vignette...

1. Placez le curseur en haut à droite de la vignette et sélectionnez les points de suspension.
   
    ![sélectionner les points de suspension de la vignette](media/service-dashboard-add-widget/pbi_ellipses.png)
2. Sélectionnez l’icône de modification pour rouvrir le volet **Détails de la vignette** et apporter des modifications.
   
    ![icône d’édition en forme de crayon](media/service-dashboard-add-widget/pbi-edit.png)

## <a name="considerations-and-troubleshooting"></a>Considérations et résolution des problèmes
* Pour faciliter le déplacement de la vignette sur votre tableau de bord, ajoutez un titre et/ou un sous-titre.
* Si vous souhaitez incorporer du contenu à partir d'un site web, mais que celui-ci ne dispose pas de code intégré à copier et coller, consultez embed.ly pour découvrir comment générer ce code intégré.

## <a name="next-steps"></a>Étapes suivantes
[Vignettes du tableau de bord](consumer/end-user-tiles.md)

D’autres questions ? [Posez vos questions à la Communauté Power BI](http://community.powerbi.com/).

