---
title: FAQ Passerelle de données locale
description: Voici les questions fréquemment posées au sujet de la passerelle de données locale. Ce Forum Aux Questions collecte les questions fréquemment posées dans un emplacement spécifique pour la passerelle.
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-gateways
ms.topic: conceptual
ms.date: 01/24/2018
ms.author: mblythe
LocalizationGroup: Gateways
ms.openlocfilehash: b4ecec3b2e53c2fea0fcbb7d78d1114da1a105ed
ms.sourcegitcommit: 2a7bbb1fa24a49d2278a90cb0c4be543d7267bda
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/26/2018
ms.locfileid: "34299628"
---
# <a name="on-premises-data-gateway-faq"></a>FAQ Passerelle de données locale
<!-- Shared FAQ shared Include -->
[!INCLUDE [gateway-onprem-faq-shared-include](./includes/gateway-onprem-faq-shared-include.md)]

## <a name="analysis-services"></a>Analysis Services
**Question :** puis-je utiliser msdmpump.dll pour créer des mappages de noms d’utilisateur effectifs personnalisés pour Analysis Services ?  
**Réponse :** Non. Cette opération n’est pas prise en charge à ce stade.

**Question :** puis-je utiliser la passerelle pour me connecter à une instance multidimensionnelle (OLAP) ?  
**Réponse :** oui. La passerelle de données locale prend en charge les connexions actives aux modèles multidimensionnels et tabulaires Analysis Services.

**Question :** que se passe-t-il si j’installe la passerelle sur un ordinateur appartenant à un domaine différent de mon serveur local et utilisant l’authentification Windows ?  
**Réponse :** Aucune garantie n’est donnée ici. Tout dépend de la relation d’approbation existant entre les deux domaines. Si les deux domaines figurent dans un modèle de domaines approuvés, la passerelle peut être en mesure de se connecter au serveur Analysis Services et le nom d’utilisateur en vigueur peut être résolu. Si ce n’est pas le cas, la connexion peut échouer.

**Question :** Comment puis-je savoir quel nom d’utilisateur effectif est passé à mon serveur Analysis Services local ?  
**Réponse :** Nous répondons à cette question dans l’[article sur la résolution des problèmes](service-gateway-onprem-tshoot.md).

**Question :** Je possède 25 bases de données dans Analysis Services. Existe-t-il un moyen de les activer en une seule fois pour la passerelle ?  
**Réponse :** non. Cela est prévu, mais aucune date de sortie n’est définie pour le moment.

## <a name="administration"></a>Administration
**Question :** Puis-je avoir plusieurs administrateurs pour une passerelle ?  
**Réponse :** oui. Lorsque vous gérez une passerelle, vous pouvez accéder à l’onglet de l’administrateur pour ajouter des administrateurs.

**Question :** L’administrateur de la passerelle doit-il être un administrateur sur l’ordinateur où est installée la passerelle ?  
**Réponse :** non. L’administrateur de la passerelle permet de gérer la passerelle à partir du service.

**Question :** Puis-je empêcher les utilisateurs de mon organisation de créer une passerelle ?  
**Réponse :** non. Cela est prévu, mais aucune date de sortie n’est définie pour le moment.

**Question :** Puis-je obtenir des informations statistiques et sur l’utilisation des passerelles de mon organisation ?  
**Réponse :** non. Cela est prévu, mais aucune date de sortie n’est définie pour le moment.

## <a name="power-bi"></a>Power BI
**Question :** Ai-je besoin de mettre à niveau la passerelle personnelle ?
**Réponse :** Non. Vous pouvez continuer à utiliser la passerelle personnelle Power BI.

**Question :** à quelle fréquence les vignettes du tableau de bord sont-elles actualisées dans Power BI lorsque l’utilisateur est connecté via la passerelle de données locale ?  
**Réponse :** Environ toutes les dix minutes. Les connexions DirectQuery ne font rien de plus. Cela ne signifie pas qu’une vignette envoie une requête à votre serveur local ou envoie de nouvelles données toutes les dix minutes.

**Question :** puis-je charger des classeurs Excel avec des modèles de données Power Pivot qui se connectent à des sources de données locales ? L’utilisation d’une passerelle est-elle requise pour ce scénario ?  
**Réponse :** Oui, vous pouvez télécharger le classeur. Et non, vous n’avez pas besoin d’une passerelle. Cependant, étant donné que les données résident dans le modèle de données Excel, les rapports dans Power BI et basés sur le classeur Excel ne seront pas actifs. Pour actualiser les rapports dans Power BI, vous devez chaque fois télécharger de nouveau un classeur mis à jour. Vous pouvez également utiliser la passerelle avec une actualisation planifiée.

**Question :** Si des utilisateurs partagent des tableaux de bord dotés d’une connexion DirectQuery, les autres utilisateurs peuvent-ils voir les données même s’ils ne disposent pas des mêmes autorisations ?  
**Réponse :** pour un tableau de bord connecté à Analysis Services, les utilisateurs voient seulement les données auxquelles ils ont accès. Si les utilisateurs n’ont pas les mêmes autorisations, ils ne pourront voir aucune donnée. Pour les autres sources de données, tous les utilisateurs partagent les informations d’identification entrées par l’administrateur pour cette source de données.

**Question :** Pourquoi ne puis-je pas me connecter à mon serveur Oracle ?  
**Réponse :** Vous devez peut-être installer le client Oracle et configurer le fichier tnsnames.ora avec les informations appropriées pour vous connecter à votre serveur Oracle. Il s’agit d’une installation distincte en dehors de la passerelle. Pour plus d’informations, consultez [Installation du client Oracle](service-gateway-onprem-manage-oracle.md#installing-the-oracle-client).

**Question :** La passerelle fonctionne-t-elle avec ExpressRoute ?  
**Réponse :** Oui. Pour plus d’informations sur ExpressRoute et Power BI, consultez [Power BI et ExpressRoute](service-admin-power-bi-expressroute.md).

## <a name="next-steps"></a>Étapes suivantes
[Passerelle de données locale](service-gateway-onprem.md)  
[Informations approfondies sur la passerelle de données locale](service-gateway-onprem-indepth.md)  
[Résolution des problèmes de passerelle de données locale](service-gateway-onprem-tshoot.md)  
D’autres questions ? [Posez vos questions à la communauté Power BI](http://community.powerbi.com/)

