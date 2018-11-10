---
title: Questions fréquentes sur les visuels personnalisés Power BI
description: Parcourir une liste de questions fréquentes et de réponses sur les visuels personnalisés Power BI
author: markingmyname
ms.author: maghan
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 10/29/2018
LocalizationGroup: Visualizations
ms.openlocfilehash: 064d32944f52f6e391d4a7ec4df41ecbf09b7e3f
ms.sourcegitcommit: 02f918a4f27625b6f4e47473193ebc8219db40e2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2018
ms.locfileid: "51223073"
---
# <a name="frequently-asked-questions-about-power-bi-custom-visuals"></a>Questions fréquentes sur les visuels personnalisés Power BI

## <a name="organizational-custom-visuals"></a>Visuels personnalisés d’une organisation

**Comment l’administrateur peut-il gérer les visuels personnalisés d’une organisation ?**

Dans le portail d’administration, sous l’onglet « Visuels personnalisés de l’organisation » l’administrateur peut voir et [gérer tous les visuels personnalisés de l’organisation dans l’entreprise](https://docs.microsoft.com/power-bi/service-admin-portal#organization-visuals) : ajouter, désactiver, activer et supprimer.
Il n’est plus nécessaire de partager ces visuels par e-mails ou par le biais d’un dossier partagé ! Une fois ces visuels déployés dans le référentiel de l’organisation, les utilisateurs peuvent facilement les découvrir et les importer dans leurs rapports, directement depuis Power BI Desktop ou Service. Les visuels personnalisés d’une organisation sont accessibles à partir du magasin intégré (dans Desktop et Service) sous l’onglet « MON ORGANISATION ». Une fois que l’administrateur charge la version d’un nouveau visuel personnalisé de l’organisation, tous les membres de l’organisation obtiennent la même version mise à jour. Les créateurs de rapports n’ont pas besoin de supprimer le visuel dans leurs rapports pour obtenir la nouvelle version de ces visuels, car tous les rapports utilisant ces visuels sont automatiquement actualisés ! Le mécanisme de mise à jour est similaire pour les visuels de la Place de marché.

**Si un administrateur charge un visuel personnalisé à partir de la Place de marché publique dans le magasin de l’organisation, est-il automatiquement mis à jour une fois qu’un fournisseur met à jour le visuel dans la Place de marché publique ?**

Non, il n’y a pas de mise à jour automatique à partir de la Place de marché publique.
L’administrateur doit mettre à jour la version des visuels personnalisés de l’organisation si nécessaire.

**Est-il possible de désactiver le magasin de l’organisation ?**

Non, les utilisateurs voient toujours l’onglet « MON ORGANISATION » à partir de Power BI Desktop et Service. L’administrateur peut désactiver ou supprimer tous les visuels personnalisés de l’organisation dans le portail d’administration. Le magasin de l’organisation est alors vide.
  
**Si l’administrateur désactive les visuels personnalisés à partir du portail d’administration (paramètres du locataire), les utilisateurs ont-ils toujours accès aux visuels personnalisés de l’organisation ?**

Oui, si l’administrateur désactive les visuels personnalisés à partir du portail d’administration, cela n’affecte pas le magasin de l’organisation. Certaines organisations désactivent les visuels personnalisés et activent uniquement des visuels sélectionnés manuellement qui ont été importés et chargés par l’administrateur Power BI dans le magasin de l’organisation. La désactivation des visuels personnalisés à partir du portail d’administration n’est pas appliquée dans Power BI Desktop. Les utilisateurs de Desktop peuvent toujours ajouter et utiliser des visuels personnalisés à partir de la Place de marché publique dans leurs rapports. Toutefois, le rendu de ces visuels personnalisés publiques ne s’exécute plus une fois qu’ils sont publiés sur le service Power BI et ils émettent une erreur appropriée. Lorsque vous utilisez le service Power BI, vous ne pouvez pas importer des visuels personnalisés à partir de la Place de marché publique. Seuls les visuels à partir du magasin de l’organisation peuvent être importés, car le paramètre des visuels personnalisés dans le portail d’administration est appliqué dans le service Power BI.

**En quoi le magasin d’organisation et les visuels personnalisés d’organisation constituent-ils une excellente solution pour l’entreprise ?**

* Tout le monde reçoit la même version du visuel, qui est contrôlée par l’administrateur Power BI. Une fois que l’administrateur met à jour la version du visuel dans le portail d’administration, tous les utilisateurs dans l’organisation obtiennent automatiquement la version mise à jour.

* Il n’est plus nécessaire de partager des fichiers de visuels par e-mail ou par le biais de dossiers partagés ! Un seul endroit, visible par tous les membres qui sont connectés.

* En termes de sécurité et de prise en charge, les nouvelles versions des visuels personnalisés d’organisation sont automatiquement mis à jour dans tous les rapports, comme les visuels de la Place de marché.

* Les utilisateurs de l’organisation utilisant les visuels personnalisés d’organisation doivent être connectés pour voir et utiliser les visuels personnalisés d’organisation, qui constituent un élément de sécurité pour l’organisation.

* Les administrateurs peuvent contrôler les visuels personnalisés disponibles dans l’organisation.

* Les administrateurs peuvent activer/désactiver les visuels à des fins de test à partir du portail d’administration. Meilleure mise en œuvre de la sécurité : ces visuels seront autorisés aux seuls membres de l’organisation.

## <a name="certified-custom-visuals"></a>Visuels personnalisés certifiés

**Que sont les visuels personnalisés certifiés ?**

Les visuels personnalisés certifiés sont des visuels dans la [Place de marché](https://appsource.microsoft.com/marketplace/apps?page=1&product=power-bi-visuals) répondant à certaines exigences de code [spécifiées](power-bi-custom-visuals-certified.md) et aux tests de l’équipe Power BI.  Les tests effectués sont conçus pour vérifier que le visuel n’accède pas à des services ou ressources externes. Toutefois, Microsoft n’est pas l’auteur de visuels personnalisés tiers, et nous conseillons aux utilisateurs de contacter l’auteur directement pour vérifier la fonctionnalité d’un visuel.

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations, visitez [Résolution des problèmes de vos visuels personnalisés Power BI](power-bi-custom-visuals-troubleshoot.md).
