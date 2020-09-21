---
title: Paramètres d’URL dans les rapports paginés - Générateur de rapports Power BI
description: Cette rubrique décrit les utilisations courantes des paramètres des rapports Power BI Report Builder, les propriétés que l’on peut définir et plus encore.
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
author: maggiesMSFT
ms.author: maggies
ms.reviewer: cfinlan
ms.custom: ''
ms.date: 09/09/2020
ms.openlocfilehash: f81cf6625f02f71b1ccf8bcd2c442ded3329083d
ms.sourcegitcommit: 002c140d0eae3137a137e9a855486af6c55ad957
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/10/2020
ms.locfileid: "89642387"
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

## <a name="syntax-description"></a>Description de la syntaxe 

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

**Export format** : Spécifie le format de rendu et d’exportation d’un rapport.

Exemple : rdl:format = PDF

Les valeurs disponibles sont :
 
- PPTX (PowerPoint)
- MHTML 
- IMAGE 
- EXCELOPENXML (EXCEL) 
- WORDOPENXML (WORD) 
- CSV 
- PDF 
- ACCESSIBLEPDF (PDF)
- XML 

**Report View** Spécifie le type de vue à utiliser pour afficher le rapport.

-   rdl:reportView

    - « interactive » (par défaut) : permet de charger le rapport en mode Interactif.
    - « pageView » : permet de charger le rapport en mode Consultation de page.

**Parameter panel** Spécifie si le panneau des paramètres est fermé ou ouvert lors du chargement du rapport, ou s’il est entièrement masqué.

-   rdl:parameterPanel

    - 'collapsed' : charger le rapport avec le panneau de paramètres fermé. Le bouton de paramètre est activé pour que les utilisateurs puissent cliquer sur le bouton pour développer.
    - 'hidden' : charger le rapport avec le panneau de paramètres fermé et le bouton de paramètre désactivé.
    - 'expanded' (valeur par défaut) : charger le rapport avec le panneau de paramètres ouvert et le bouton de paramètre activé.

**Informations sur l’appareil** Vous pouvez spécifier des paramètres de sortie supplémentaires pour les formats d’exportation suivants. 

PDF/ACCESSIBLEPDF :

- rdl:AccessiblePDF=true/false
- rdl:Columns=integer
- rdl:ColumnSpacing=decimal(in)
- rdl:DpiX=integer
- rdl:DpiY=integer
- rdl:EndPage=integer
- rdl:HumanReadablePDF=true/false
- rdl:MarginBottom=decimal(in)
- rdl:MarginLeft=decimal(in)
- rdl:MarginRight=decimal(in)
- rdl:MarginTop=decimal(in)
- rdl:PageHeight=decimal(in)
- rdl:PageWidth=decimal(in)
    - rdl:StartPage=integer
    
CSV :

- rdl:Encoding=string
- rdl:ExcelMode=true/false
- rdl:FieldDelimiter=string
- rdl:NoHeader=true/false
- rdl:Qualifier=string
- rdl:RecordDelimiter=string
- rdl:SuppressLineBreaks=true/false
    - rdl:UseFormattedValues=true/false
    
WORDOPENXML (WORD) :

- rdl:AutoFit=string -> True/False/Never/Default
- rdl:ExpandToggles=true/false
- rdl:FixedPageWidth=true/false
- rdl:OmitHyperlinks=true/false
- rdl:OmitDrillthroughs=true/false

EXCELOPENXML (EXCEL) :

- rdl:OmitDocumentMap=true/false
- rdl:OmitFormulas=true/false
    - rdl:SimplePageHeaders=true/false
    
PPTX (PowerPoint) :
 
- rdl:Columns=integer
- rdl:ColumnSpacing=decimal(in)
- rdl:DpiX=integer
- rdl:DpiY=integer
- rdl:EndPage=integer
- rdl:MarginBottom=decimal(in)
- rdl:MarginLeft=decimal(in)
- rdl:MarginRight=decimal(in)
- rdl:MarginTop=decimal(in)
- rdl:PageHeight=decimal(in)
- rdl:PageWidth=decimal(in)
- rdl:StartPage=integer
    - rdl:UseReportPageSize=true/false

XML :

- rdl:XSLT=string
- rdl:MIMEType=string
- rdl:UseFormattedValues=true/false
- rdl:Indented=true/false
- rdl:OmitNamespace=true/false
- rdl:OmitSchema=true/false
- rdl:Encoding=string
- rdl:Schema=true/false

**Ouvrir le lien hypertexte dans la même fenêtre de navigateur** Vous pouvez ajouter 'rdl:targetSameWindow=true' à l’URL du lien hypertexte de votre rapport pour que Power BI ouvre ce lien hypertexte dans la même fenêtre de navigateur. Pour plus d’informations sur l’ajout de liens hypertexte à un rapport, consultez [Ajouter un lien hypertexte à une URL](https://docs.microsoft.com/sql/reporting-services/report-design/add-a-hyperlink-to-a-url-report-builder-and-ssrs) dans la documentation de SQL Server Reporting Services.

## <a name="next-steps"></a>Étapes suivantes

- [Passer un paramètre de rapport dans une URL pour un rapport paginé dans Power BI](report-builder-url-pass-parameters.md)
- [Présentation des rapports paginés dans Power BI Premium](paginated-reports-report-builder-power-bi.md)
