---
title: Limitations de Questions et réponses dans Power BI
description: Limitations actuelles de Questions et réponses dans Power BI
author: maggiesMSFT
ms.author: maggies
ms.service: powerbi
ms.subservice: pbi-reports-dashboards
ms.topic: conceptual
ms.date: 09/09/2020
ms.openlocfilehash: 6ad81bc88ee559fa08400b5ed8a74dd1a9b6051f
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2020
ms.locfileid: "96410019"
---
# <a name="limitations-of-power-bi-qa"></a>Limitations de Questions et réponses dans Power BI

La fonctionnalité Questions et réponses de Power BI présente actuellement certaines limitations.

## <a name="data-sources"></a>Sources de données

### <a name="supported-data-sources"></a>Sources de données prises en charge

Questions et réponses prend en charge les configurations suivantes de sources de données dans le service Power BI :

- Mode Importation
- Connexion directe à Azure Analysis Services
- Connexion directe à SQL Server Analysis Services (avec une passerelle)
- Jeux de données Power BI.

Dans chacune de ces configurations, la sécurité au niveau des lignes est également prise en charge.

**Prise en charge de DirectQuery dans Questions et réponses** (préversion)

Questions et réponses prend désormais en charge les sources DirectQuery SQL, notamment SQL Server 2019, Azure SQL Database et Azure Synapse Analytics. Vous pouvez utiliser Questions et réponses pour poser des questions en langage naturel sur ces sources de données. Il y a un léger changement de comportement de Questions et réponses en mode DirectQuery : Une fois que vous avez tapé votre question, vous devez sélectionner le bouton **Envoyer**. Ce changement empêche la surcharge de la source DirectQuery avec des requêtes inutiles au fur et à mesure de votre saisie.

Les autres sources DirectQuery ne sont pas prises en charge dans Questions et réponses. Nous ne bloquons pas Questions et réponses si vous avez d’autres sources DirectQuery dans votre jeu de données, mais il se peut que certaines questions ne soient pas correctement traitées ou qu’elles retournent des erreurs.

### <a name="data-sources-not-supported"></a>Sources de données non prises en charge

Questions et réponses dans Power BI ne prend actuellement pas en charge les configurations suivantes :

- Sécurité au niveau objet avec n’importe quel type de source de données
- Modèles composites
- Reporting Services 

## <a name="tooling-limitations"></a>Limitations des outils

La nouvelle boîte de dialogue d’outils permet aux utilisateurs de personnaliser et d’améliorer le langage naturel dans Questions et réponses. Pour en savoir plus sur les outils, lisez [Présentation des outils Questions et réponses](q-and-a-tooling-intro.md).

## <a name="review-question-limitations"></a>Limitations de la fonctionnalité Passer en revue les questions

La fonctionnalité Passer en revue les questions stocke seulement 28 jours les questions posées par rapport à votre modèle de données. Lorsque vous utilisez la nouvelle fonctionnalité Passer en revue les questions, vous pouvez remarquer que certaines questions ne sont pas enregistrées. Le fait qu’elles ne soient pas enregistrées est défini par conception, du fait que le moteur de langage naturel effectue une série d’étapes de nettoyage des données pour garantir que chaque séquence de touches d’un utilisateur n’est pas enregistrée ou affichée.

Les administrateurs Power BI peuvent utiliser les paramètres du locataire pour gérer la capacité à stocker les questions. Ces autorisations sont basées sur les groupes de sécurité. 

Les utilisateurs peuvent également empêcher l’enregistrement de leurs questions en sélectionnant **Paramètres** > **Général** et en désélectionnant **Autoriser Questions et réponses à enregistrer mon énoncé**. 

## <a name="teach-qa-limitations"></a>Limitations de la fonctionnalité Enseigner à Questions et réponses

La fonctionnalité Enseigner à Questions et réponses vous permet de corriger deux types d’erreurs :

- Affectation d’un mot à un champ
- Affectation d’un mot à une condition de filtre

Actuellement, nous ne prenons pas en charge la redéfinition d’un terme reconnu ou la définition d’autres types de conditions ou d’expressions. De plus, lorsque vous définissez des conditions de filtrage, vous ne pouvez utiliser qu’un sous-ensemble limité de la langue, notamment :

- Pays égal à EUA
- Pays différent de EUA
- Produits > 100
- Produits supérieur à 100
- Produits = 100
- Produits égal à 100
- Produits < 100
- Produits inférieur à 100

> [!NOTE]
> Les outils Questions et réponses prennent en charge uniquement le mode Importation. Ils ne prennent pas encore en charge la connexion à une source de données locale ou Azure Analysis Services. Cette limitation actuelle sera supprimée dans les versions ultérieures de Power BI.

### <a name="statements-not-supported"></a>Instructions non prises en charge

- Les conditions multiples ne sont pas prises en charge. Pour contourner ce problème, créez une colonne calculée DAX qui équivaut au booléen d’une instruction multicondition et utilisez ce champ à la place.
- Si vous ne spécifiez pas de condition de filtre quand Questions et réponses vous invite à fournir un sous-ensemble de données, vous ne pouvez pas enregistrer la définition, même si la totalité de l’instruction n’a aucun trait de soulignement rouge.

## <a name="next-steps"></a>Étapes suivantes

Il existe diverses bonnes pratiques permettant d’améliorer le moteur de langage naturel. Pour plus d’informations, consultez [Meilleures pratiques de Questions et réponses](q-and-a-best-practices.md).
