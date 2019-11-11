---
title: Résolution des problèmes liés aux valeurs imbriquées retournées sous forme de texte dans le service Power BI
description: Découvrir comment corriger des valeurs imbriquées converties en chaîne quand des paramètres de confidentialité de source de données incorrects sont utilisés
author: cpopell
ms.reviewer: ''
ms.custom: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: troubleshooting
ms.date: 6/4/2019
ms.author: gepopell
LocalizationGroup: Reports
ms.openlocfilehash: ab40ca9c415dacf52f4d82eb2c157d57aef92f93
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2019
ms.locfileid: "73871282"
---
# <a name="troubleshooting-nested-values-returned-as-text-in-power-bi-service"></a>Résolution des problèmes liés aux valeurs imbriquées retournées sous forme de texte dans le service Power BI

## <a name="cause"></a>Cause

Avant, il pouvait arriver qu’un rapport Power BI s’actualise correctement dans Desktop, mais échoue dans le service Power BI avec une erreur telle que « Nous ne pouvons pas convertir la valeur « [Tableau] » en type Tableau ». Une des causes de cette erreur : quand le pare-feu de confidentialité des données met en mémoire tampon une source de données, des valeurs non scalaires imbriquées (comme des tableaux, des enregistrements, des listes et des fonctions) sont automatiquement converties en valeurs texte (comme « [Tableau] » ou « [Enregistrement] »).

Maintenant que le service Power BI prend en charge la définition des niveaux de confidentialité (ou la désactivation totale du pare-feu), ces erreurs peuvent être évitées en [configurant les paramètres de confidentialité de la source de données](https://powerbi.microsoft.com/blog/privacy-levels-for-cloud-data-sources/) dans le service Power BI pour qu’ils soient non privés.

À partir de juin, quand le pare-feu met en mémoire tampon un tableau/un enregistrement/une liste/etc. imbriqué(e), au lieu de convertir automatiquement ces valeurs en texte, Power BI génère l’erreur suivante : 

`We cannot return a value of type Table in this context`

## <a name="effect-on-loadrefresh"></a>Effet sur le chargement/l’actualisation

Alors que ce changement est motivé par la mise en mémoire tampon du pare-feu, son impact s’étend également au chargement/à l’actualisation. Pour corriger le comportement de mise en mémoire tampon du pare-feu, nous avons dû également changer le comportement de chargement des tableaux/enregistrements/etc. imbriqués pour le modèle Power BI et le modèle de données Excel dans Power Query pour Excel. Avant, les tableaux/enregistrements/etc. imbriqués étaient chargés en tant que valeurs texte (comme « [Tableau] » ou « [Enregistrement] »). À présent, ils seront traités comme des erreurs, ce qui aboutira à une valeur nulle dans le tableau chargé et une augmentation du nombre d’erreurs dans les résultats de chargement.

Étant donné que ces erreurs se produisent uniquement pendant le chargement/l’actualisation, elles n’apparaîtront pas dans l’éditeur Power Query.

### <a name="before"></a>Avant

- Chargement/actualisation sans erreur
- Le tableau chargé contient « [Tableau] », « [Enregistrement] », etc.
 

### <a name="after"></a>Après

- Chargement/actualisation avec erreurs
- Le tableau chargé contient des valeurs NULL (au lieu de « [Tableau] », « [Enregistrement] », etc.)
 

## <a name="resolution"></a>Résolution

Vous chargez une colonne qui contient des valeurs non scalaires (par exemple tableaux, listes, enregistrements, etc.) ?
Si oui, vous devriez pouvoir éliminer les erreurs en supprimant la colonne.
Si vous ne pouvez pas supprimer la colonne, vous devriez pouvoir répliquer l’ancien comportement en ajoutant une colonne personnalisée et en utilisant une logique comme l’exemple suivant :

`if [MyColumn] is table then "[Table]" else if [MyColumn] is record then "[Record]" else if [MyColumn] is list then "[List]" else if [MyColumn] is function then "[Function]" else [MyColumn]`

Le problème se reproduit-il dans Power BI Desktop si vous définissez tous vos paramètres de confidentialité de source de données sur Privé ?
Si oui, vous devriez pouvoir résoudre l’erreur en [configurant vos paramètres de confidentialité de source de données](https://powerbi.microsoft.com/blog/privacy-levels-for-cloud-data-sources/) dans le service Power BI pour qu’ils soient Non privés.
