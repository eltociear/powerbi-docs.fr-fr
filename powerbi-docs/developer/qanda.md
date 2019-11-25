---
title: Questions et réponses dans Power BI Embedded
description: Power BI Embedded vous permet d’incorporer Questions et réponses dans une application et permet aux utilisateurs de poser des questions en utilisant un langage naturel.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 11/20/2017
ms.openlocfilehash: 5a3a7b91b0c97a75923876caff205ffb9abfce70
ms.sourcegitcommit: c395fe83d63641e0fbd7c98e51bbab224805bbcc
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74265181"
---
# <a name="qa-in-power-bi-embedded"></a>Questions et réponses dans Power BI Embedded

Power BI Embedded vous permet d’incorporer Questions et réponses dans une application et permet aux utilisateurs de poser des questions en utilisant un langage naturel, ainsi que de recevoir des réponses immédiates sous forme de visuels, par exemple des graphiques.

![Question Interactive Questions et réponses dans une image incorporée](media/qanda/embedded-qanda.gif)

Il existe deux modes pour l’incorporation de Questions et réponses au sein de votre application : **interactif** et **résultat uniquement**. Le mode **Interactif** vous permet de taper des questions et de les afficher dans le visuel. Si vous avez une question enregistrée, ou une question définie que vous souhaitez afficher, vous pouvez utiliser le mode **résultat uniquement** en remplissant la question dans la configuration de l’incorporation.

Voici à quoi ressemble le code JavaScript.

```javascript
// Embed configuration used to describe the what and how to embed.
// This object is used when calling powerbi.embed within the JavaScript API.
// You can find more information at https://github.com/Microsoft/PowerBI-JavaScript/wiki/Embed-Configuration-Details.
var config= {
    type: 'qna',
    tokenType:   models.TokenType.Embed | models.TokenType.Aad,
    accessToken: access token value,
    embedUrl:    https://app.powerbi.com/qnaEmbed (groupId to be appended as query parameter if required),
    datasetIds:  array of requested data set ids (at the moment we support only one dataset),
    viewMode:    models.QnaMode.Interactive | models.QnaMode.ResultOnly,
    question:    optional parameter for Explore mode (QnaMode.Interactive) and mandatory for Render Result mode (QnaMode.ResultOnly)
};

// Get a reference to the embedded QNA HTML element
var qnaContainer = $('#qnaContainer')[0];

// Embed the QNA and display it within the div container.
var qna = powerbi.embed(qnaContainer, config);
```

## <a name="set-question"></a>Question définie

Si vous avez utilisé le **mode résultat** avec une question définie, vous pouvez injecter des questions supplémentaires dans l’image et recevoir immédiatement une réponse qui remplace le résultat précédent. Un nouveau visuel correspondant à la nouvelle question est affiché.

Un exemple de cette utilisation est une liste de questions fréquentes. L’utilisateur peut parcourir les questions et obtenir des réponses au sein de la même partie incorporée.

**Extrait de code pour l’utilisation du SDK JS :**  

```javascript
// Get a reference to the embedded Q&A HTML element
var qnaContainer = $('#qnaContainer')[0];

// Get a reference to the embedded Q&A.
qna = powerbi.get(qnaContainer);

qna.setQuestion("This year sales")
    .then(function (result) {
        …….
    })
    .catch(function (errors) {
        …….
    });
```

## <a name="visual-rendered-event"></a>Événement rendu par un visuel

Pour le mode **interactif**, l’application peut être avertie par un événement de modification des données chaque fois que le visuel affiché change de façon à refléter la requête d’entrée tapée.

Écouter l’événement *visualRendered* vous permet d’enregistrer des questions pour une utilisation ultérieure. 

**Extrait de code pour l’utilisation du SDK JS :**  

```javascript
// Get a reference to the embedded Q&A HTML element
var qnaContainer = $('#qnaContainer')[0];

// Get a reference to the embedded Q&A.
qna = powerbi.get(qnaContainer);

// qna.off removes a given event listener if it exists.
qna.off("visualRendered");

// qna.on will add an event listener.
qna.on("visualRendered", function(event) {
     …….
});
```

## <a name="embed-token"></a>Jeton d’incorporation

Créez un jeton d’incorporation d’un jeu de données pour démarrer une partie Questions et réponses. Pour plus d’informations, consultez [Générer un jeton](https://docs.microsoft.com/rest/api/power-bi/embedtoken).

## <a name="next-steps"></a>Étapes suivantes

Pour essayer l’incorporation dans Questions et réponses, consultez l’[exemple d’incorporation JavaScript](https://microsoft.github.io/PowerBI-JavaScript/demo/).

D’autres questions ? [Essayez d’interroger la communauté Power BI](https://community.powerbi.com/)
