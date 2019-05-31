---
title: Espace de travail archivé Power BI
description: Espace de travail archivé Power BI après la gestion de votre client Office 365
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 11/02/2018
ms.author: mblythe
LocalizationGroup: Administration
ms.openlocfilehash: d2eeab8241de06f9a4d0e654696173d076e01ad2
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "61187051"
---
# <a name="power-bi-archived-workspace"></a>Espace de travail archivé Power BI

Avec Power BI, tout le monde peut s’inscrire et commencer à utiliser le service en quelques minutes.  Par la suite, le service informatique de votre organisation peut choisir d’assurer la gestion de Power BI pour les utilisateurs de votre organisation.  Dans ce cas, vous bénéficiez de la gestion centralisée des utilisateurs et des autorisations dans votre organisation. Vous pouvez également profiter d’une connexion rationalisée avec les mêmes nom d’utilisateur et mot de passe utilisés pour d’autres services dans votre organisation.

Tout contenu que vous avez créé avant que le service informatique n’assume la gestion de Power BI est placé dans un espace de travail archivé Power BI, accessible à partir de la navigation de gauche dans [Power BI](https://app.powerbi.com). Vous devez commencer à créer du contenu Power BI dans Mon espace de travail, qui est un emplacement sécurisé et géré par le service informatique de votre organisation.  Votre espace de travail archivé continue à exister, mais il existe des restrictions quant aux actions que vous pouvez effectuer sur le contenu dans cet espace de travail.  Pour supprimer ces restrictions, vous devez migrer le contenu de votre espace de travail archivé vers Mon espace de travail, qui est géré par votre service informatique.

## <a name="restrictions-in-your-archived-workspace"></a>Restrictions applicables à votre espace de travail archivé

Power BI ne supprimera pas de contenu de votre espace de travail archivé. Vous pouvez continuer à obtenir des données, créer des rapports et des tableaux de bord, et actualiser des jeux de données. Les utilisateurs existants avec lesquels vous avez partagé du contenu peuvent également toujours afficher le contenu dans leur espace de travail archivé. Toutefois, certaines restrictions s’appliquent au contenu de votre espace de travail archivé :

* **OneDrive Entreprise** : Pour les jeux de données dans votre espace de travail archivé, vous ne pouvez plus obtenir de données ni les actualiser à partir de OneDrive Entreprise.  Si vous essayez de vous connecter à cette source, un avertissement s’affiche.

* **Partage de tableaux de bord** : Vous ne pouvez pas partager des tableaux de bord avec d’autres utilisateurs à partir de votre espace de travail archivé.  Tous les utilisateurs qui y ont déjà accès continuent à pouvoir afficher les tableaux de bord partagés en accédant à leur espace de travail archivé.

* **Création de groupes** : Impossible de créer des groupes dans votre espace de travail archivé.

* **Accès dans les applications mobiles Power BI** : Même si vous pouvez toujours afficher du contenu web dans votre espace de travail archivé, ce contenu n’apparaît plus dans les applications mobiles Power BI.

## <a name="migrating-content-in-your-archived-workspace"></a>Migration de contenu dans votre espace de travail archivé

Pour continuer à utiliser Power BI, vous devez créer du contenu dans Mon espace de travail. Vous devez également planifier la migration du contenu de votre espace de travail archivé vers Mon espace de travail.  La façon dont vous migrez le contenu varie selon le type de contenu :

* **Jeux de données Excel ou Power BI Desktop** : Migrez ces jeux de données en basculant de votre espace de travail archivé vers Mon espace de travail, puis en rechargeant le fichier Excel ou Power BI Desktop en cliquant sur le bouton **Mes données**.  Si vous avez configuré l’actualisation planifiée, vous devez reconfigurer ces paramètres pour le nouveau jeu de données dans Mon espace de travail.

* **Autres jeux de données** : Basculez vers Mon espace de travail, puis cliquez sur le bouton **Obtenir des données** pour vous reconnecter à d’autres jeux de données que vous avez créés dans votre espace de travail archivé.  Vous devrez peut-être réentrer les informations de connexion ou de sécurité.

* **Rapports** : Les rapports contenus dans des fichiers Excel ou Power BI Desktop sont recréés automatiquement une fois que vous rechargez le fichier Excel ou Power BI Desktop correspondant. Les rapports installés comme partie d’un pack de contenu sont également recréés lorsque vous vous reconnectez au pack de contenu. Si vous avez créé vos propres rapports par l’intermédiaire du service Power BI, recréez-les dans Mon espace de travail.

* **Tableaux de bord** : Les tableaux de bord installés dans le cadre de packs de contenu sont recréés automatiquement lorsque vous vous reconnectez au pack de contenu dans Mon espace de travail. Si vous avez créé vos propres tableaux de bord par l’intermédiaire du service Power BI, recréez-les dans Mon espace de travail.

D’autres questions ? [Essayez d’interroger la communauté Power BI](http://community.powerbi.com/)

