---
title: Utiliser des clés gérées par le client dans Power BI
description: Découvrez comment utiliser des clés gérées par le client dans Power BI.
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: how-to
ms.date: 10/21/2020
LocalizationGroup: Premium
ms.openlocfilehash: fc93ae0f54bfe4f72ec18687829e9eb78dfaedd7
ms.sourcegitcommit: 3ddfd9ffe2ba334a6f9d60f17ac7243059cf945b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2020
ms.locfileid: "92349365"
---
# <a name="use-customer-managed-keys-in-power-bi"></a>Utiliser des clés gérées par le client dans Power BI

Power BI chiffre les données au repos et in-process. Par défaut, Power BI utilise des clés managées par Microsoft pour chiffrer vos données. Les organisations peuvent choisir d’utiliser leurs propres clés pour le chiffrement du contenu utilisateur au repos sur Power BI, des images de rapport vers les jeux de données importés dans les capacités Premium. 

## <a name="why-use-customer-managed-keys"></a>Pourquoi utiliser des clés gérées par le client

Avec les clés gérées par le client (CMK) Power BI, les organisations peuvent répondre aux exigences de conformité pour le chiffrement des données au repos avec leur fournisseur de services cloud (dans ce cas, Microsoft). CMK est uniquement proposé aux nouveaux clients Power BI Premium et permet aux organisations de chiffrer leur contenu utilisateur Power BI à l’aide d’une clé qu’ils fournissent et gèrent. La révocation d’une clé gérée par le client rend le contenu de l’utilisateur au sein de Power BI illisible pour tous les utilisateurs sous une heure, y compris pour Microsoft. Par rapport à l’offre BYOK, CMK couvre également le contenu utilisateur généré par le service, en plus des données client importées dans les rapports et les jeux de données hébergés sur des capacités Premium. CMK applique des stratégies de mise en cache plus strictes et ne peut appliquer qu’une seule clé pour chiffrer toutes les données.


## <a name="how-to-use-customer-managed-keys"></a>Comment utiliser des clés gérées par le client
Pour choisir d’utiliser des clés gérées par le client Power BI, votre organisation doit contacter son responsable de compte Microsoft afin de vérifier qu’elle répond à certaines exigences de taille nécessaires à l’activation de CMK.  


## <a name="next-steps"></a>Étapes suivantes

Les liens suivants fournissent des informations qui peuvent être utiles pour les clés gérées par le client :

* [Apporter vos propres clés de chiffrement pour Power BI](service-encryption-byok.md)
* [Configurer la prise en charge multigéographique pour Power BI Premium](service-admin-premium-multi-geo.md)
* [Fonctionnement des capacités](service-premium-what-is.md#how-capacities-function)
* [Actualisation incrémentielle](service-premium-incremental-refresh.md).
