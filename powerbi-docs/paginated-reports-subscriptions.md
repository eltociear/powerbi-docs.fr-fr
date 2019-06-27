---
title: S’abonner à des rapports paginés dans le service Power BI
description: Dans cet article, vous allez découvrir certains points à prendre en compte concernant l’abonnement aux rapports paginés dans le service Power BI.
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.date: 05/24/2019
ms.openlocfilehash: 472606fcb3b823cdcb722c9d8d6421d0ec652d24
ms.sourcegitcommit: 797bb40f691384cb1b23dd08c1634f672b4a82bb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/12/2019
ms.locfileid: "66839549"
---
# <a name="subscribe-yourself-and-others-to-paginated-reports-in-the-power-bi-service"></a>Vous abonner vous et d’autres utilisateurs à des rapports paginés dans le service Power BI 

Vous pouvez maintenant configurer des abonnements par e-mail pour vous-même et d’autres personnes à des rapports paginés dans le service Power BI. En règle générale, le processus est le même que pour les [abonnements aux rapports et tableaux de bord dans le service Power BI](service-report-subscribe.md). Cet article énumère les différences et considérations. 

Lors de la configuration des abonnements, vous choisissez la fréquence à laquelle vous souhaitez recevoir des e-mails : quotidienne, hebdomadaire ou toutes les heures. Si vous choisissez une fréquence quotidienne ou hebdomadaire, vous pouvez choisir l’heure d’exécution de l’abonnement. Vous pouvez définir jusqu’à 24 abonnements différents par jour pour chaque rapport. 

## <a name="considerations-for-paginated-report-subscriptions"></a>Considérations sur les abonnements aux rapports paginés 

- Contrairement aux abonnements pour les tableaux de bord ou les rapports Power BI, votre abonnement contient une pièce jointe de l’intégralité de la sortie du rapport.  Les types de pièce jointe suivants sont pris en charge : PDF, présentation PowerPoint (PPTX), classeur Excel (XLSX), document Word (DOCX), fichier CSV et XML.

- Il n’existe aucune image d’aperçu du rapport dans le corps du message.  Nous prévoyons de proposer l’image de la première page du rapport comme élément facultatif. 

- La taille maximale d’une pièce jointe de rapport est de 25 Mo. 

- Vous pouvez abonner d’autres utilisateurs à des rapports paginés qui se connectent à n’importe quelle source de données actuellement prise en charge, notamment les jeux de données Power BI ou Azure Analysis Services. N’oubliez pas que la pièce jointe du rapport reflète les données conformément à vos autorisations, comme c’est le cas aujourd’hui avec SQL Server Reporting Services. 

- Les abonnements aux pages de rapports sont liés au nom du rapport.  

- Les abonnements aux e-mails sont envoyés avec les valeurs de paramètres par défaut du rapport. 

- Il n’y a aucune option **Après l’actualisation des données** pour la fréquence avec les rapports paginés. Vous obtenez toujours les valeurs les plus récentes à partir de la source de données sous-jacente. 

## <a name="next-steps"></a>Étapes suivantes

[Vous abonner vous et d’autres utilisateurs à des rapports et tableaux de bord dans le service Power BI](service-report-subscribe.md)

[Présentation des rapports paginés dans Power BI Premium](paginated-reports-report-builder-power-bi.md)
