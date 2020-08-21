---
title: Utiliser des clés gérées par le client dans Power BI
description: Découvrez comment utiliser des clés gérées par le client dans Power BI.
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: how-to
ms.date: 08/12/2020
LocalizationGroup: Premium
ms.openlocfilehash: 8d13cc7a24486fada7f8d428ba52abeaa49d2518
ms.sourcegitcommit: b60063c49ac39f8b28c448908ecbb44b54326335
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/12/2020
ms.locfileid: "88160929"
---
# <a name="use-customer-managed-keys-in-power-bi"></a>Utiliser des clés gérées par le client dans Power BI

Power BI chiffre les données au repos et in-process. Par défaut, Power BI utilise des clés managées par Microsoft pour chiffrer vos données. Les organisations peuvent choisir d’utiliser leurs propres clés pour le chiffrement du contenu utilisateur au repos sur Power BI, des images de rapport vers les jeux de données importés dans les capacités Premium. 

## <a name="why-use-customer-managed-keys"></a>Pourquoi utiliser des clés gérées par le client
Avec les clés gérées par le client (CMK) Power BI, les organisations peuvent répondre aux exigences de conformité pour le chiffrement des données au repos avec leur fournisseur de services cloud (dans ce cas, Microsoft). Les CMK permettent aux organisations de chiffrer leur contenu utilisateur Power BI avec une clé qu’ils fournissent et gèrent. La révocation d’une clé gérée par le client rend le contenu de l’utilisateur au sein de Power BI illisible pour tous les utilisateurs sous une heure, y compris pour Microsoft. Par rapport à l’offre BYOK, les CMK couvrent également le contenu utilisateur en dehors des capacités Power BI Premium ; elles appliquent des stratégies de mise en cache plus strictes et activent par défaut BYOK sur toutes les capacités. 
 
## <a name="how-to-use-customer-managed-keys"></a>Comment utiliser des clés gérées par le client
Pour activer les clés gérées par le client Power BI, votre organisation doit respecter les exigences de taille. L’administrateur général de votre organisation doit envoyer une demande de support à Microsoft, ou il peut contacter le responsable de compte Microsoft de votre organisation pour en savoir plus sur le processus.  


## <a name="next-steps"></a>Étapes suivantes

Les liens suivants fournissent des informations qui peuvent être utiles pour les clés gérées par le client :

* [Apporter vos propres clés de chiffrement pour Power BI](service-encryption-byok.md)
* [Configurer la prise en charge multigéographique pour Power BI Premium](service-admin-premium-multi-geo.md)
* [Fonctionnement des capacités](service-premium-what-is.md#how-capacities-function)
* [Actualisation incrémentielle](service-premium-incremental-refresh.md).
