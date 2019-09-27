---
title: Capturer des informations de diagnostic supplémentaires
description: Ces instructions décrivent deux options qui permettent de collecter manuellement des informations de diagnostic supplémentaires à partir du client web Power BI.
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 04/25/2019
ms.author: mblythe
ms.custom: seodec18
LocalizationGroup: Troubleshooting
ms.openlocfilehash: 710fb4cdcf9efb051434966d47c2eaced17ac9ba
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "65100211"
---
# <a name="capture-additional-diagnostic-information-for-power-bi"></a>Capturer des informations de diagnostic supplémentaires pour Power BI

Cet article donne les instructions pour collecter manuellement des informations de diagnostic supplémentaires à partir du client web Power BI.

1. Accédez à [Power BI](https://app.powerbi.com) avec Microsoft Edge ou Internet Explorer.

1. Appuyez sur **F12** pour ouvrir les outils de développement Microsoft Edge.

   ![Capture d’écran de l’onglet Éléments des outils de développement Microsoft Edge.](media/service-admin-capturing-additional-diagnostic-information-for-power-bi/edge-developer-tools.png)

1. Sélectionnez l’onglet **Réseau**. Il répertorie le trafic capturé.

   ![Capture d’écran de l’onglet Réseau des outils de développement Microsoft Edge.](media/service-admin-capturing-additional-diagnostic-information-for-power-bi/edge-network-tab.png)

    Vous pouvez soit :

    * Parcourez la fenêtre et reproduisez les problèmes que vous pouvez rencontrer.

    * Masquez ou affichez la fenêtre Outils de développement à tout moment pendant la session en appuyant sur F12.

1. Pour arrêter le profilage de la session, il vous suffit de sélectionner le carré rouge sous l’onglet **Réseau** de la zone d’outils de développement.

   ![Capture d’écran de l’onglet Réseau des outils de développement Microsoft Edge avec le bouton Arrêter mis en évidence.](media/service-admin-capturing-additional-diagnostic-information-for-power-bi/edge-network-tab-stop.png)

1. Sélectionnez l’icône représentant une disquette pour exporter les données sous la forme de fichier d’archive HTTP (HAR).

   ![Capture d’écran de l’onglet Réseau des outils de développement Microsoft Edge avec l’icône de disquette mise en évidence.](media/service-admin-capturing-additional-diagnostic-information-for-power-bi/edge-network-tab-save.png)

1. Entrez un nom de fichier, puis enregistrez le fichier HAR.

    Ce dernier contient toutes les informations sur les demandes réseau entre la fenêtre du navigateur et Power BI, dont :

    * Les ID d’activité pour chaque demande.

    * L’horodatage précis pour chaque requête.

    * Toutes les informations d’erreur retournées au client.

    Ce suivi contient également les données utilisées pour renseigner les éléments visuels affichés à l’écran.

1. Vous pouvez fournir le fichier HAR à prendre en charge pour la révision.

D’autres questions ? [Essayez d’interroger la communauté Power BI](http://community.powerbi.com/)
