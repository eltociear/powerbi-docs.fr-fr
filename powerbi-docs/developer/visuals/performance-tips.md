---
title: Conseils relatifs aux performances
description: Guide pratique pour créer un visuel Power BI hautes performances
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: how-to
ms.date: 04/20/2020
ms.openlocfilehash: c22c634ef59a1aae2994dcacaae62dc8ebed7474
ms.sourcegitcommit: 6bc66f9c0fac132e004d096cfdcc191a04549683
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/06/2020
ms.locfileid: "91746073"
---
# <a name="how-to-build-a-high-performance-power-bi-visual"></a>Guide pratique pour créer un visuel Power BI hautes performances
Cet article aborde les techniques permettant à un développeur d’obtenir des performances élevées lors du rendu des visuels. 

Personne ne veut d’un visuel qui est lent à s’afficher : limiter au maximum dans le code chaque diminution des performances devient critique lors du rendu. 

> [!NOTE]
> Comme nous continuons à améliorer la plateforme, de nouvelles versions de l’API sont publiées en continu. Pour tirer le meilleur parti de la plateforme et des fonctionnalités des visuels Power BI, il est recommandé de toujours utiliser la version la plus récente.
>
> Depuis la **version 2.1**, les temps de chargement des visuels Power BI se sont améliorés de 20 % en moyenne.

## <a name="power-bi-visual-performance-tips"></a>Conseils sur les performances des visuels Power BI
Voici quelques recommandations sur la façon d’obtenir des performances visuelles optimales. 

### <a name="use-user-timing-api"></a>Utiliser l’API User Timing
L’utilisation de l’**API User Timing** pour mesurer les performances JavaScript de votre application peut vous aider à déterminer quelles parties du script nécessitent une optimisation.

Pour plus d’informations, consultez [API User Timing](https://msdn.microsoft.com/library/hh772738(v=vs.85).aspx).

### <a name="review-animation-loops"></a>Examiner les boucles d’animation
La boucle d’animation redessine-t-elle les éléments inchangés ? 

 - Problème : Redessiner les éléments qui ne changent pas d’une image à l’autre est une perte de temps.

 - Solution : Mettre à jour les images de façon sélective. 
 
Quand il s’agit d’animer des visualisations statiques, il est tentant de regrouper le code qui réalise le dessin en une seule fonction de mise à jour et de l’appeler de façon répétée avec de nouvelles données pour chaque itération de la boucle d’animation.

Au lieu de cela, examinez le modèle de mise à jour suivant : vous utilisez une méthode de constructeur de visuel pour dessiner tout ce qui est statique, puis vous utilisez une fonction de mise à jour qui doit dessiner seulement les éléments qui changent dans le visuel. 

   > [!TIP]
   > Les boucles d’animation inefficaces se trouvent généralement dans les axes et légendes.

### <a name="cache-dom-nodes"></a>Mettre en cache les nœuds du modèle DOM 
Quand un nœud ou une liste de nœuds est récupérée auprès du modèle DOM, vous devez réfléchir à la possibilité de les réutiliser dans des calculs ultérieurs (parfois même dans l’itération suivante de la boucle). Tant que vous n’avez pas besoin d’ajouter ou de supprimer des nœuds supplémentaires dans la zone appropriée, leur mise en cache peut améliorer l’efficacité globale de votre application.

Pour être sûr que votre code est rapide et ne ralentit pas le navigateur, accédez le moins possible au modèle DOM. 

- Avant : 

   ```javascript
   public update(options: VisualUpdateOptions) { 
       let axis = $(".axis"); 
   }
   ```

- Après : 

   ```javascript
   public constructor(options: VisualConstructorOptions) { 
       this.$root = $(options.element); 
       this.xAxis = this.$root.find(".xAxis"); 
   } 
 
   public update(options: VisualUpdateOptions) { 
       let axis = this.axis; 
   }
   ```

### <a name="avoid-dom-manipulation"></a>Éviter la manipulation du modèle DOM 
Limitez autant que possible la manipulation du modèle DOM.  Les opérations d’insertion comme `prepend()`, `append()` et `after()` prennent du temps et ne doivent pas être utilisées sauf si elles sont vraiment nécessaires.

Exemple :

  ```javascript
  for (let i=0; i<1000; i++) { 
      $('#list').append('<li>'+i+'</li>');
  }
  ```

L’exemple ci-dessus peut être rendu plus rapide en utilisant `html()` et en créant la liste au préalable : 

  ```javascript
  let list = ''; 
  for (let i=0; i<1000; i++) { 
      list += '<li>'+i+'</li>'; 
  } 

  $('#list').html(list); 
  ```

### <a name="reconsider-jquery"></a>Reconsidérer JQuery

La limitation de vos frameworks JS et l’utilisation de JS en mode natif dans la mesure du possible peuvent augmenter la bande passante disponible et réduire la charge de votre traitement. Cela peut également limiter les problèmes de compatibilité avec des navigateurs plus anciens. 

Pour plus d’informations, consultez [youmightnotneedjquery.com](http://youmightnotneedjquery.com/) pour obtenir d’autres exemples de fonctions JQuery, comme `show`, `hide`, `addClass`, etc.  

### <a name="use-canvas-or-webgl"></a>Utiliser Canvas ou WebGL 
Pour une utilisation répétée d’animations, envisagez d’utiliser **Canvas** ou **WebGL** au lieu de SVG. Contrairement à SVG, avec ces options, les performances sont déterminées par la taille plutôt que par le contenu. 

Pour plus d’informations sur les différences, consultez [SVG vs Canvas: How to Choose](/previous-versions/windows/internet-explorer/ie-developer/samples/gg193983(v=vs.85)). 

### <a name="use-requestanimationframe-instead-of-settimeout"></a>Utiliser requestAnimationFrame au lieu de setTimeout 
Si vous utilisez [requestAnimationFrame](https://www.w3.org/TR/animation-timing/) pour mettre à jour vos animations à l’écran, vos fonctions d’animation sont appelées **avant** que le navigateur appelle une autre fonction pour actualiser le dessin.

Pour plus d’informations, consultez cet [exemple](https://testdrive-archive.azurewebsites.net/Graphics/RequestAnimationFrame/Default.html) d’animation fluide avec `requestAnimationFrame`.

## <a name="next-steps"></a>Étapes suivantes

Découvrez plus d’informations sur les techniques d’optimisation dans le [Guide d’optimisation pour Power BI](../../guidance/power-bi-optimization.md).