---
title: S’abonner à des rapports paginés dans le service Power BI
description: Dans cet article, vous allez découvrir des points à prendre en compte concernant l’abonnement à des rapports paginés dans le service Power BI.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.date: 12/03/2019
ms.openlocfilehash: c7f377c1295d4cd8f0d226331fcb6db697786e5a
ms.sourcegitcommit: bfc2baf862aade6873501566f13c744efdd146f3
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83141267"
---
# <a name="subscribe-yourself-and-others-to-paginated-reports-in-the-power-bi-service"></a>Vous abonner vous et d’autres utilisateurs à des rapports paginés dans le service Power BI 

Vous pouvez maintenant configurer des abonnements par e-mail pour vous-même et d’autres personnes à des rapports paginés dans le service Power BI. En général, le processus est le même que pour un [abonnement aux rapports et tableaux de bord du service Power BI](end-user-subscribe.md). Cet article énumère les différences et considérations. 

Lors de la configuration des abonnements, vous choisissez la fréquence à laquelle vous voulez recevoir des e-mails : quotidienne, hebdomadaire, mensuelle ou toutes les heures. Vous pouvez également choisir la ou les heures auxquelles l’abonnement doit être exécuté. Vous pouvez définir en tout jusqu’à 24 abonnements différents pour chaque rapport. 

## <a name="considerations-for-paginated-report-subscriptions"></a>Considérations sur les abonnements aux rapports paginés 

- Contrairement aux abonnements pour les tableaux de bord ou les rapports Power BI, votre abonnement contient une pièce jointe de l’intégralité de la sortie du rapport.  Les types de pièce jointe suivants sont pris en charge : PDF, présentation PowerPoint (PPTX), classeur Excel (XLSX), document Word (DOCX), fichier CSV et XML.

- Vous pouvez inclure une image d’aperçu du rapport dans le corps de l’e-mail.  Ceci est facultatif et l’image peut différer légèrement de la première page de votre document de rapport attaché, selon le format sélectionné pour la pièce jointe. 

- La taille maximale d’une pièce jointe de rapport est de 25 Mo. 

- Vous pouvez abonner d’autres utilisateurs à des rapports paginés qui se connectent à n’importe quelle source de données actuellement prise en charge, notamment les jeux de données Power BI ou Azure Analysis Services. N’oubliez pas que la pièce jointe du rapport reflète les données conformément à vos autorisations, comme c’est le cas aujourd’hui avec SQL Server Reporting Services. 

- Les abonnements par e-mail peuvent être envoyés avec les paramètres actuellement sélectionnés ou avec les paramètres par défaut de votre rapport.  Vous pouvez définir des valeurs de paramètre différentes pour chaque abonnement que vous créez pour votre rapport. 

- Si le créateur de votre rapport a défini des paramètres basés sur une expression (par exemple, la valeur par défaut est toujours la date du jour), l’abonnement l’utilise comme valeur par défaut. Vous pouvez modifier d’autres valeurs de paramètre et choisir d’utiliser les valeurs actuelles ; cependant, sauf si vous changez explicitement cette valeur, l’abonnement utilise le paramètre basé sur une expression.

- Il n’y a aucune option **Après l’actualisation des données** pour la fréquence avec les rapports paginés. Vous obtenez toujours les valeurs les plus récentes à partir de la source de données sous-jacente. 

## <a name="next-steps"></a>Étapes suivantes

[Vous abonner vous et d’autres utilisateurs à des rapports et tableaux de bord dans le service Power BI](../collaborate-share/service-report-subscribe.md)

[Rapports paginés dans le service Power BI](end-user-paginated-report.md)
