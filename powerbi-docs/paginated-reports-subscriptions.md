---
title: S’abonner à des rapports paginés dans le service Power BI
description: Dans cet article, vous découvrez les choses à prendre en compte sur l’abonnement aux rapports paginés dans le service Power BI.
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.date: 05/24/2019
ms.openlocfilehash: ccec6658808d94728f2a4f14de67c36da0f51def
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66222195"
---
# <a name="subscribe-yourself-and-others-to-paginated-reports-in-the-power-bi-service"></a>S’abonner vous-même et autres rapports paginés dans le service Power BI 

Vous pouvez maintenant configurer les abonnements par courrier électronique pour vous-même et d’autres pour les rapports paginés dans le service Power BI. En règle générale, le processus est identique à [abonnement aux rapports et tableaux de bord dans le service Power BI](service-report-subscribe.md). Cet article énonce les différences et considérations. 

Dans la configuration d’abonnements, vous choisissez la fréquence à laquelle vous souhaitez recevoir des e-mails : quotidienne, hebdomadaire ou toutes les heures. Si vous choisissez quotidienne ou hebdomadaire, vous pouvez choisir le moment vous souhaitez que l’exécution de l’abonnement. En tout, vous pouvez définir jusqu'à 24 différents abonnements par jour pour chaque rapport. 

## <a name="considerations-for-paginated-report-subscriptions"></a>Considérations pour les abonnements de rapport paginé 

- Contrairement aux abonnements pour les tableaux de bord ou rapports Power BI, votre abonnement contient une pièce jointe de la sortie de l’intégralité du rapport.  Les types suivants de la pièce jointe sont prises en charge : PDF, présentation PowerPoint (PPTX), classeur Excel (XLSX), Document Word (DOCX), un fichier CSV et XML.

- Il n’existe aucune image d’aperçu du rapport dans le corps du message.  Nous avons l’intention de l’image de la première page du rapport comme un élément facultatif. 

- La taille de pièce jointe maximale de rapport est de 25 Mo. 

- Vous pouvez vous abonner d’autres utilisateurs pour les rapports paginés qui se connectent à toutes les sources de données actuellement pris en charge, y compris les jeux de données Azure Analysis Services ou Power BI. N’oubliez pas que la pièce jointe de rapport reflète les données selon vos autorisations, comme SQL Server Reporting Services dès aujourd'hui. 

- Les abonnements aux pages de rapport sont liés au nom du rapport.  

- Abonnements par courrier électronique sont envoyées avec les valeurs de paramètre par défaut du rapport. 

- Il existe aucune **après l’actualisation des données** option pour la fréquence des rapports paginés. Vous obtenez toujours les valeurs les plus récentes de la source de données sous-jacente. 

## <a name="next-steps"></a>Étapes suivantes

[S’abonner vous-même et autres rapports et tableaux de bord dans le service Power BI](service-report-subscribe.md)

[Présentation des rapports paginés dans Power BI Premium (préversion)](paginated-reports-report-builder-power-bi.md)
