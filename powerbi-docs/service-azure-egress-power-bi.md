---
title: Sortie Azure et Power BI
description: Comprendre les frais de sortie Azure et Power BI en fonction de l’emplacement du locataire et de Power BI Premium
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 10/18/2018
ms.author: davidi
LocalizationGroup: Data from databases
ms.openlocfilehash: 528d31a72d2c78b0a00f853d2df82f3a4eb04eae
ms.sourcegitcommit: c8c126c1b2ab4527a16a4fb8f5208e0f7fa5ff5a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/15/2019
ms.locfileid: "54295330"
---
# <a name="power-bi-and-azure-egress"></a>Sortie Azure et Power BI

Quand vous utilisez Power BI avec des sources de données Azure, vous pouvez éviter des frais de sortie Azure en vous assurant que votre locataire Power BI se trouve dans la même région que vos sources de données Azure.

Quand votre locataire Power BI est déployé sur la même région Azure que celle sur laquelle vous déployez vos sources de données, vous n’encourez pas de frais de sortie pour l’actualisation planifiée et les interactions DirectQuery. 

## <a name="determining-where-your-power-bi-tenant-is-located"></a>Détermination de l’emplacement de votre locataire Power BI

Pour savoir où se trouve votre locataire Power BI, consultez l’article [Où est situé mon client Power BI ?](service-admin-where-is-my-tenant-located.md).

Pour les clients Multi-Géo Power BI Premium, si votre locataire Power BI ne se trouve pas à l’emplacement optimal pour certaines de vos sources de données basées sur Azure, vous pouvez déployer la fonctionnalité Multi-Géo Power BI Premium dans la région Azure souhaitée et réunir ainsi votre locataire Power BI et les sources de données Azure dans la même région Azure.

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations sur Power BI Premium ou la fonctionnalité Multi-Géo, consultez les ressources suivantes :

* [Qu’est-ce que Microsoft Power BI Premium ?](service-premium.md)
* [Acheter Power BI Premium](service-admin-premium-purchase.md)
* [Prise en charge de Multi-Géo dans Power BI Premium (préversion)](service-admin-premium-multi-geo.md)
* [Où est situé mon locataire Power BI ?](service-admin-where-is-my-tenant-located.md)
* [Questions fréquentes Power BI Premium](service-premium-faq.md)


