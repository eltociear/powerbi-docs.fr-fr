---
title: Forum aux questions sur la passerelle de données locale - Power BI
description: Cet article contient des questions fréquemment posées au sujet de la passerelle de données locale pour Power BI. Il rassemble les questions fréquemment posées pour la passerelle utilisée dans Power BI.
author: mgblythe
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: conceptual
ms.date: 07/15/2019
ms.author: mblythe
LocalizationGroup: Gateways
ms.openlocfilehash: 4aa3d46741044498846865278db51859980a19b9
ms.sourcegitcommit: 0d7ad791a2d2bef45d5d60e38e0af4c9fc22187b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/13/2019
ms.locfileid: "74010838"
---
# <a name="on-premises-data-gateway-faq---power-bi"></a>Forum aux questions sur la passerelle de données locale - Power BI

[!INCLUDE [gateway-rewrite](includes/gateway-rewrite.md)]

## <a name="power-bi"></a>Power BI

**Question :** Ai-je besoin de mettre à niveau la passerelle de données locale (mode personnel) ?

**Réponse :** Non. Vous pouvez continuer à utiliser la passerelle (mode personnel) Power BI.

**Question :** Des autorisations spéciales sont-elles nécessaires pour installer la passerelle et pour la gérer dans le service Power BI ?

**Réponse :** Aucune autorisation spéciale n’est nécessaire.

**Question :** Puis-je charger des classeurs Excel avec des modèles de données Power Pivot qui se connectent à des sources de données locales ? L’utilisation d’une passerelle est-elle requise pour ce scénario ? 

**Réponse :** Oui, vous pouvez charger le classeur. Et non, vous n’avez pas besoin d’une passerelle. Cependant, étant donné que les données résident dans le modèle de données Excel, les rapports dans Power BI et basés sur le classeur Excel ne sont pas actifs. Pour actualiser les rapports dans Power BI, vous devez chaque fois télécharger de nouveau un classeur mis à jour. Vous pouvez également utiliser la passerelle avec une actualisation planifiée.

**Question :** Si des utilisateurs partagent des tableaux de bord dotés d’une connexion DirectQuery, les autres utilisateurs peuvent-ils voir les données même s’ils ne disposent pas des mêmes autorisations ? 

**Réponse :** Pour un tableau de bord connecté à Azure Analysis Services, les utilisateurs voient seulement les données auxquelles ils ont accès. Si les utilisateurs n’ont pas les mêmes autorisations, ils ne peuvent voir aucune donnée. Pour les autres sources de données, tous les utilisateurs partagent les informations d’identification entrées par l’administrateur pour cette source de données.

**Question :** Pourquoi ne puis-je pas me connecter à mon serveur Oracle ? 

**Réponse :** Vous devez peut-être installer le client Oracle et configurer le fichier tnsnames.ora avec les informations appropriées pour vous connecter à votre serveur Oracle. Il s’agit d’une installation distincte en dehors de la passerelle. Pour plus d’informations, consultez [Installer le client Oracle](service-gateway-onprem-manage-oracle.md#install-the-oracle-client).

**Question :** J’utilise des scripts R. Est-ce qu’ils sont pris en charge ?

**Réponse** : Les scripts R sont pris en charge uniquement pour le mode personnel.

## <a name="analysis-services-in-power-bi"></a>Analysis Services dans Power BI

**Question :** Puis-je utiliser msdmpump.dll pour créer des mappages de noms d’utilisateur effectifs personnalisés pour Analysis Services ? 

**Réponse :** Non. Cette utilisation n’est pas prise en charge à ce stade.

**Question :** Puis-je utiliser la passerelle pour me connecter à une instance multidimensionnelle (OLAP) ? 

**Réponse :** Oui. La passerelle de données locale prend en charge les connexions actives aux modèles multidimensionnels et tabulaires Analysis Services.

**Question :** Que se passe-t-il si j’installe la passerelle sur un ordinateur appartenant à un domaine différent de mon serveur local et utilisant l’authentification Windows ? 

**Réponse :** Aucune garantie n’est donnée ici. Tout dépend de la relation d’approbation existant entre les deux domaines. Si les deux domaines figurent dans un modèle de domaines approuvés, la passerelle peut être en mesure de se connecter au serveur Analysis Services et le nom d’utilisateur effectif peut être résolu. Si ce n’est pas le cas, la connexion peut échouer.

**Question :** Comment puis-je savoir quel nom d’utilisateur effectif est passé à mon serveur Analysis Services local ? 

**Réponse :** Nous répondons à cette question dans [l’article sur la résolution des problèmes](service-gateway-onprem-tshoot.md).

## <a name="next-steps"></a>Étapes suivantes

* [Résolution des problèmes de passerelle de données locale](/data-integration/gateway/service-gateway-tshoot)

D’autres questions ? Essayez la [communauté Power BI](https://community.powerbi.com/).

