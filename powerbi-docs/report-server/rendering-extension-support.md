---
title: Conformité de l’extension de rendu PDF à la norme ISO 14289-1 - Power BI Report Server
description: Ce document décrit la conformité de l’extension de rendu PDF de Power BI Report Server et SQL Reporting Services aux spécifications ISO 14289-1 (PDF/UA).
author: maggiesMSFT
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.topic: conceptual
ms.date: 11/04/2019
ms.author: maggies
ms.openlocfilehash: c800ee995bc3c03b3cbcda91503e6dea9495f6b5
ms.sourcegitcommit: 721cf375627b010e8ad12c4c668295f38d450a17
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/06/2019
ms.locfileid: "73638077"
---
# <a name="pdf-rendering-extension-conformance-to-iso-14289-1---power-bi-report-server"></a>Conformité de l’extension de rendu PDF à la norme ISO 14289-1 - Power BI Report Server 

S’applique à : Power BI Report Server et SQL Reporting Services

Ce document décrit la conformité de l’extension de rendu PDF de Power BI Report Server et SQL Reporting Services aux spécifications [ISO 14289-1 (PDF/UA)](https://www.pdfa.org/publication/pdfua-in-a-nutshell/).

> [!NOTE]
> Vous pouvez enregistrer ou imprimer ce livre blanc en sélectionnant **Imprimer** dans votre navigateur, puis **Enregistrer au format PDF**.

## <a name="1--scope"></a>1.  Étendue

Non applicable

## <a name="2--normative-references"></a>2.  Références normatives

Non applicable

## <a name="3--terms-and-definitions"></a>3.  Termes et définitions

Non applicable

## <a name="4--notation"></a>4.  Notation

Non applicable

## <a name="5-version-identification"></a>5. Identification de la version

L’extension de rendu PDF assure la prise en charge de PDF/UA telle qu’elle est décrite dans ce document. Dans certains cas, indiqués ci-dessous, il incombe à l’utilisateur de prendre des mesures pour s’assurer qu’un PDF est pleinement compatible avec PDF/UA.  Nous attendons de l’utilisateur qu’il ajoute la version PDF/UA appropriée et les identificateurs de conformité dans la dernière étape de ce processus, indiquant que le travail nécessaire a été effectué pour rendre le fichier PDF pleinement conforme à la norme PDF/UA.

Tout ce qui est mentionné dans ce document est basé sur le rendu d’un document PDF avec le paramètre d’informations de périphérique AccessiblePdf défini sur `true`. Dans certains cas, les limitations de conformité sont dues à des limitations dans le langage RDL (Report Definition Language).

## <a name="6--conformance-requirements"></a>6.  Exigences en matière de conformité

|     Critères     |     Fonctionnalité de prise en charge     |     Remarques      |
|----|--------|--------|
|    6.1 Général    |                 Pris en charge    |    L’extension de rendu PDF crée des PDF version 1.7.    |
|    6.2 Conformité des fichiers    |                 Pris en charge avec des exceptions    |    Consultez les remarques dans la section 7 – Exigences relatives au format de fichier.    |
|    6.3 Conformité du lecteur    |     Non applicable     |         |
|    6.4 Conformité de la technologie d’assistance    |     Non applicable     |         |

## <a name="7--file-format-requirements"></a>7.  Exigences relatives au format de fichier

|     Critères     |     Fonctionnalité de prise en charge     |     Remarques      |
|-----|-------|------------------------|
|    7.1 Général    |                 Pris en charge avec des exceptions    |    Tout le contenu réel sera balisé comme défini dans ISO 32000-1:2008, 14.8. Les artefacts (ISO 32000-1:2008, 14.8.2.2.2) ne seront pas balisés dans l’arborescence de la structure. <li> L’extension de rendu PDF n’offre pas la possibilité de marquer explicitement les éléments individuels en tant qu’artefacts. Par conséquent, elle marque comme artefact tout ce qui correspond aux critères figurant dans ISO 32000-1:2008, 14.8.2.2.2.<br>Le contenu sera marqué dans l’arborescence de structure avec des étiquettes appropriées au niveau sémantique dans un ordre de lecture logique. <br> **Note** 4  La règle 1.4 des WCAG 2.0 explique les problèmes relatifs au contraste, à la couleur et à d’autres aspects de la mise en forme pour l’accessibilité. <br><li> L’utilisateur doit s’assurer que son document n’est pas concerné par ces problèmes. <br>Les balises standard définies dans ISO 32000-1:2008, 14.8.4, ne seront pas remappées. <li> L’extension de rendu PDF n’effectue pas le remappage des balises standard. Tout document commence par l’élément racine du document. <br>Tout fichier censé être conforme à cette norme internationale aura une valeur Suspects égale à false (ISO 32000-1:2008, table 321). <li> L’extension de rendu PDF n’a pas l’entrée Suspects. Cette propriété est facultative.    |
|    7.2 Texte    |                 Pris en charge avec des exceptions    |    Le contenu sera étiqueté dans l’ordre de lecture logique. La balise la plus appropriée au niveau sémantique sera utilisée pour chaque élément logique dans le contenu du document. <br><li> L’extension de rendu PDF étiquette le contenu dans l’ordre de lecture logique dans la mesure du possible.<br>Les codes de caractères seront mappés au format Unicode, comme décrit dans ISO 32000-1:2008, 14.8.2.4.2. Les caractères non inclus dans la spécification Unicode peuvent utiliser la zone à usage privé Unicode ou déclarer un autre encodage de caractères. <br>Le langage naturel sera déclaré comme indiqué dans ISO 32000-1:2008, 14.9.2 et/ou comme décrit dans ISO 32000-1:2008, 7.9.2. Les modifications en langage naturel seront déclarées. Les modifications en langage naturel dans les chaînes de texte (par exemple, dans des descriptions alternatives) seront déclarées à l’aide d’un identificateur de langue, comme décrit dans ISO 32000-1:2008, 14.9.2.2. <br><li> L’extension de rendu PDF déclare uniquement le langage naturel au niveau du document    |
|    7.3 Graphiques    |                 Pris en charge avec des exceptions    |    Les objets graphiques, autres que les objets texte, seront étiquetés avec une balise de figure, comme décrit dans ISO 32000-1:2008, 14.8.4.5, table 340. Si l’une quelconque des exceptions suivantes est vraie, le graphique sera marqué en tant qu’artefact : <br><li> le graphique ne représente pas un contenu explicite ou <li>  le graphique apparaît en tant qu’arrière-plan d’une annotation de lien, auquel cas le texte alternatif du lien décrira à la fois le graphique et le lien. <li> L’extension de rendu PDF étiquette les objets graphiques avec la balise de figure. <br>Une légende qui accompagne une figure sera étiquetée avec une balise de légende. <li> L’extension de rendu PDF n’étiquette pas actuellement les légendes des figures avec une balise de légende. <br>Les balises de figure incluront une représentation alternative ou un texte de remplacement représentant le contenu marqué avec la balise de figure, comme indiqué dans ISO 32000-1:2008, 14.7.2, table 323. <br>**Note** 1 Voir aussi la règle 1.1 des WCAG 2.0. <br>Si le texte représenté dans un graphique n’est pas du texte en langage naturel destiné à être lu par un lecteur humain, un texte alternatif décrivant la nature ou l’objectif du graphique sera fourni. <br>**Note** 2 Un texte représentant un exemple de type ou un exemple du système d’écriture utilisé par un langage est un exemple de texte qui n’est pas en langage naturel.   L’extension de rendu PDF prend en charge le texte de légende des figures, bien qu’il incombe à l’utilisateur d’ajouter le texte de légende. <br>Note supplémentaire concernant l’attribut BBox : <br><li> L’extension de rendu PDF n’écrit pas actuellement l’attribut BBox. <li> Une solution de contournement consiste à réétiqueter manuellement les illustrations en tant que nouvelles figures ou en tant qu’artefacts.    |
|    7.4 Titres    |                 Non applicable    |    Le langage RDL ne prend pas en charge le marquage des titres de quelque manière que ce soit. Il incombe à l’utilisateur de les étiqueter comme il convient.    |
|    7.5 Tables    |                 Pris en charge avec des exceptions    |    Les tables doivent inclure des en-têtes. Les en-têtes de table seront étiquetées conformément à ISO 32000-1:2008, table 337 et table 349. <br>**Note** 1 Les tables peuvent contenir des en-têtes de colonnes, des en-têtes de lignes ou les deux. <br>**Note** 2 Le plus d’informations possible sur la structure des tables doivent être disponibles lorsque l’on s’appuie sur la technologie d’assistance. Les en-têtes jouent un rôle clé dans la fourniture d’informations structurelles. <br><li> Il incombe à l’utilisateur d’inclure ou non des en-têtes dans les tables. Le langage RDL et l’extension de rendu PDF prennent en charge les en-têtes de lignes. <br>  Les éléments de structure de type TH auront un attribut d’étendue (Scope).   <li> L’extension de rendu PDF inclut un attribut d’étendue (Scope) sur les éléments TH pour les membres de colonne et de ligne, mais pas pour les cellules d’angle.<br>Les structures d’étiquetage de table seront utilisées uniquement pour étiqueter le contenu présenté dans des relations logiques de lignes ou de colonnes.   <li> Cela dépend de la façon dont l’utilisateur a choisi d’utiliser les tables dans le langage RDL.    |
|    7.6 Listes    |                 Non applicable    |    Le langage RDL ne prend pas en charge le marquage des listes. Dans le langage RDL, elles correspondent structurellement à une table à une seule cellule. <br>Il incombe à l’utilisateur de les réétiqueter comme il convient.    |
|    7.7 Expressions mathématiques    |                 Pris en charge avec des exceptions    |    Toutes les expressions mathématiques seront placées dans une étiquette de formule, comme indiqué dans la norme ISO 32000-1:2008, 14.8.4.5, et auront un attribut Alt. <br><li> L’extension de rendu PDF ne place pas actuellement les expressions mathématiques dans une balise de formule. <br>Les exigences relatives au mappage de caractères dans Unicode s’appliqueront aux expressions mathématiques, telles qu’énoncées dans ISO 32000-1:2008, 9.10.2 et 14.8.2.4. <br><li> Cela est pris en charge par l’extension de rendu PDF.    |
|    7.8 En-têtes et pieds de page    |                 Pris en charge    |    Les en-têtes et pieds de page en cours d’exécution seront identifiés comme artefacts de pagination et seront classés comme sous-types d’en-tête ou de pied de page conformément à ISO 32000-1:2008, 14.8.2.2.2, table 330. <br><li> Les en-têtes et les pieds de page sont traités et étiquetés en tant qu’artefacts.    |
|    7.9 Notes et références    |                 Non applicable    |    L’extension de rendu PDF ne prend pas en charge le marquage des notes et des références. <br>Il incombe à l’utilisateur de les étiqueter comme il convient.    |
|    7.10 Contenu facultatif    |                 Non applicable    |         |
|    7.11 Fichiers incorporés    |                 Non applicable    |         |
|    7.12 Threads d’article    |                 Non applicable    |         |
|    7.13 Signatures numériques    |                 Non applicable    |         |
|    7.14 Formulaires non interactifs    |                 Non applicable    |         |
|    7.15 XFA    |                 Non applicable    |         |
|    7.16 Sécurité    |                 Non applicable    |         |
|    7.17 Navigation    |                 Pris en charge    |    Un document doit inclure une structure de document correspondant à l’ordre de lecture et au niveau des cibles de navigation (ISO 32000-1:2008, 12.3.3). <br><li> Le langage RDL prend en charge les signets pour un élément de rapport, mais l’utilisateur doit sélectionner cette option. Ces signets sont ensuite affichés en tant que structure du document par l’extension de rendu PDF. <br>Si elles sont présentes, les entrées de l’arborescence numérique PageLabels (ISO 32000-1:2008, 7.7.2, table 28) doivent être appropriées au niveau sémantique. <br><li> L’extension de rendu PDF n’inclut pas d’arborescence numérique PageLabels.    |
|    7.18 Annotations    |                 Non applicable    |    Le langage RDL ne prend pas en charge les annotations    |
|    7.21 Polices    |                 Pris en charge    |         |
|    7.21.1 Général    |                 Pris en charge    |         |
|    7.21.2 Types de polices    |                 Pris en charge    |         |
|    7.21.3 Polices composites    |                 Pris en charge    |         |
|    7.21.3.1 Général    |                 Pris en charge    |         |
|    7.21.3.2 CIDFonts    |                 Pris en charge    |         |
|    7.21.3.3 CMaps    |                 Pris en charge    |         |
|    7.21.4 Incorporation    |                 Pris en charge    |         |
|    7.21.4.1 Général    |                 Pris en charge    |         |
|    7.21.4.2 Incorporation de sous-ensemble    |                 Pris en charge    |         |
|    7.21.5 Métriques de polices    |                 Pris en charge    |         |
|    7.21.6 Codages de caractères    |                 Pris en charge    |         |
|    7.21.7 Mappages des caractères Unicode    |                 Pris en charge    |         |
|    7.21.8 Utilisation du glyphe .notdef    |                 Pris en charge    |         |

## <a name="8--conforming-reader-requirements"></a>8.  Exigences de conformité du lecteur

Non applicable

## <a name="9--at-requirements"></a>9.  Configuration requise AT

Non applicable

## <a name="disclaimer"></a>Disclaimer

© 2017 Microsoft Corporation. All rights reserved. The names of actual companies and products mentioned herein may be the trademarks of their respective owners. The information contained in this document represents the current view of Microsoft Corporation on the issues discussed as of the date of publication. Microsoft cannot guarantee the accuracy of any information presented after the date of publication. Microsoft regularly updates its websites with new information about the accessibility of products as that information becomes available.

Customization of the product voids this conformance statement from Microsoft. Please consult with Assistive Technology (AT) vendors for compatibility specifications of specific AT products.

This document is for informational purposes only. MICROSOFT MAKES NO WARRANTIES, EXPRESS OR IMPLIED, IN THIS DOCUMENT.


## <a name="next-steps"></a>Étapes suivantes
[Vue d’ensemble de l’administrateur](admin-handbook-overview.md)  

D’autres questions ? [Essayez d’interroger la communauté Power BI](https://community.powerbi.com/)

