---
title: Sortie Azure et Power BI
description: Comprendre les frais de sortie Azure et Power BI en fonction de l’emplacement du locataire et de Power BI Premium
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 05/08/2019
ms.author: davidi
LocalizationGroup: Data from databases
ms.openlocfilehash: 17175e1accb5013b960c5e1a71ae036b3dda72f3
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/05/2020
ms.locfileid: "73855563"
---
# <a name="power-bi-and-azure-egress"></a>Sortie Azure et Power BI

Quand vous utilisez Power BI avec des sources de données Azure, vous pouvez éviter des frais de sortie Azure en vous assurant que votre locataire Power BI se trouve dans la même région que vos sources de données Azure.

Quand votre locataire Power BI est déployé sur la même région Azure que celle sur laquelle vous déployez vos sources de données, vous n’encourez pas de frais de sortie pour l’actualisation planifiée et les interactions DirectQuery. 

## <a name="determining-where-your-power-bi-tenant-is-located"></a>Détermination de l’emplacement de votre locataire Power BI

Pour savoir où se trouve votre locataire Power BI, consultez l’article [Où est situé mon client Power BI ?](service-admin-where-is-my-tenant-located.md).

Pour les clients Multi-Géo Power BI Premium, si votre locataire Power BI ne se trouve pas à l’emplacement optimal pour certaines de vos sources de données basées sur Azure, vous pouvez déployer la fonctionnalité Multi-Géo Power BI Premium dans la région Azure souhaitée et réunir ainsi votre locataire Power BI et les sources de données Azure dans la même région Azure.

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations sur Power BI Premium ou la fonctionnalité Multi-Géo, consultez les ressources suivantes :

* [Qu’est-ce que Microsoft Power BI Premium ?](service-premium-what-is.md)
* [Acheter Power BI Premium](service-admin-premium-purchase.md)
* [Prise en charge de Multi-Géo dans Power BI Premium (préversion)](service-admin-premium-multi-geo.md)
* [Où est situé mon locataire Power BI ?](service-admin-where-is-my-tenant-located.md)
* [Questions fréquentes Power BI Premium](service-premium-faq.md)


