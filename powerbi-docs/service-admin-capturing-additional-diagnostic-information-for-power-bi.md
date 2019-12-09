---
title: Capturer des informations de diagnostic supplémentaires
description: Ces instructions décrivent deux options qui permettent de collecter manuellement des informations de diagnostic supplémentaires à partir du client web Power BI.
author: kfollis
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 09/17/2019
ms.author: kfollis
ms.custom: seodec18
LocalizationGroup: Troubleshooting
ms.openlocfilehash: 670373afb5cb890c87a24a129cd43fde7bd5d892
ms.sourcegitcommit: f77b24a8a588605f005c9bb1fdad864955885718
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2019
ms.locfileid: "74698897"
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

D’autres questions ? [Essayez d’interroger la communauté Power BI](https://community.powerbi.com/)
