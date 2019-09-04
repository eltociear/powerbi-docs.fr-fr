---
title: Paramètres d’URL dans les rapports paginés - Générateur de rapports Power BI
description: Cette rubrique décrit les utilisations courantes des paramètres de rapport du Générateur de rapports paginés Power BI, les propriétés que vous pouvez définir et plus encore.
ms.service: powerbi
ms.subservice: report-builder
ms.custom: ''
ms.topic: conceptual
author: maggiesMSFT
ms.author: maggies
ms.reviewer: cfinlan
ms.date: 08/29/2019
ms.openlocfilehash: 4dae849a18bbfc6e85eedc7ae9e338ad205cb436
ms.sourcegitcommit: b53a6f5575f5f8bc443ecdca9c72525ce123518f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/30/2019
ms.locfileid: "70189343"
---
# <a name="url-parameters-in-paginated-reports-in-power-bi"></a>Paramètres d’URL dans les rapports paginés de Power BI

Vous pouvez envoyer des commandes à des rapports paginés dans Power BI en ajoutant un paramètre à une URL. Par exemple, vous pouvez avoir affiché le rapport en utilisant un ensemble spécifique de valeurs de paramètre de rapport. Vous encapsulez ces informations dans l’URL avec des paramètres d’accès par URL prédéfinis. Vous pouvez personnaliser davantage la façon dont Power BI traite le rapport en incorporant des paramètres pour les formats de rendu ou pour l’apparence de la barre d’outils du rapport. Vous collez ensuite cette URL directement dans un e-mail ou une page web pour que d’autres utilisateurs voient votre rapport de la même manière dans le navigateur. 

Voici les actions que vous pouvez effectuer via des paramètres d’accès par URL : 

- Envoyer des paramètres de rapport à un rapport. 
- Lancer l’exportation du contenu du rapport dans un format de fichier pris en charge. 
- Masquer ou afficher le volet des paramètres. 
- Spécifier le paramètre DeviceInfo. 

Pour obtenir la liste complète des commandes et paramètres disponibles via l’accès par URL, consultez  [Informations de référence sur les paramètres d’accès par URL](#url-access-parameter-reference) plus loin dans cet article. 

## <a name="url-access-concepts"></a>Concepts de l’accès par URL 

Les demandes URL envoyées à Power BI contiennent des paramètres qui sont traités par le service. La façon dont le service gère les demandes URL dépend des paramètres, des préfixes de paramètre et des types d’éléments inclus dans l’URL. La fonctionnalité URL des rapports paginés est compatible avec la plupart des navigateurs et applications qui prennent en charge l’adressage URL standard. 

## <a name="url-access-syntax"></a>Syntaxe de l’accès par URL 

Les demandes URL peuvent contenir plusieurs paramètres, listés dans n’importe quel ordre. Les paramètres sont séparés par une esperluette (&). Les paires nom/valeur sont séparées par un signe égal (=). Par exemple :

```
powerbiserviceurl?rp:parametervalueh&rdl:parameter=value  
```

## <a name="syntax-description"></a>description de la syntaxe 

### <a name="powerbiserviceurl"></a>powerbiserviceurl 

URL du service web de votre locataire Power BI. Par exemple : 

**&**  : Utilisé pour séparer les paires nom/valeur des paramètres d’accès par URL.

**préfixe** : Préfixe pour le paramètre d’URL (par exemple rp: ou rdl:) qui spécifie une action dans le service Power BI. 

> [!NOTE]
> Les paramètres de rapport nécessitent un préfixe de paramètre et respectent la casse. 

**paramètre** : Nom du paramètre. 

### <a name="value"></a>valeur 

Texte de l’URL correspondant à la valeur du paramètre utilisé. 

Pour obtenir des exemples de passage de paramètres de rapport sur l’URL, consultez  [Passer un paramètre de rapport dans une URL](report-builder-url-pass-parameters.md).

## <a name="url-access-parameter-reference"></a>Informations de référence sur les paramètres d’accès par URL

Vous pouvez utiliser les paramètres suivants dans une URL pour configurer l’apparence de vos rapports paginés dans Power BI. Les paramètres les plus courants sont listés dans cette section. Les paramètres ne respectent pas la casse et commencent par le préfixe de paramètre  `rdl:`  s’ils concernent le format de sortie.  

### <a name="report-commands-rdl"></a>Commandes de rapport (`rdl:`) 

**Export format** : Spécifie le format de rendu et d’exportation d’un rapport. Les valeurs incluent : 
- PPTX 
- MHTML 
- IMAGE 
- EXCEL 
- WORD 
- CSV 
- PDF 
- XML 

## <a name="next-steps"></a>Étapes suivantes

- [Passer un paramètre de rapport dans une URL pour un rapport paginé dans Power BI](report-builder-url-pass-parameters.md)
- [Présentation des rapports paginés dans Power BI Premium](paginated-reports-report-builder-power-bi.md)