---
title: Capturer les informations de diagnostic supplémentaires
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
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "65100211"
---
# <a name="capture-additional-diagnostic-information-for-power-bi"></a>Capturer les informations de diagnostic supplémentaires pour Power BI

Cet article fournit des instructions pour collecter manuellement les informations de diagnostic supplémentaires à partir du client web de Power BI.

1. Accédez à [Power BI](https://app.powerbi.com) avec Microsoft Edge ou Internet Explorer.

1. Appuyez sur **F12** pour ouvrir les outils de développement Microsoft Edge.

   ![Onglet éléments des outils de capture d’écran de Microsoft Edge pour les développeurs.](media/service-admin-capturing-additional-diagnostic-information-for-power-bi/edge-developer-tools.png)

1. Sélectionnez l’onglet **Réseau**. Il répertorie le trafic capturé.

   ![Onglet réseau capture d’écran de Microsoft Edge pour les développeurs d’outils.](media/service-admin-capturing-additional-diagnostic-information-for-power-bi/edge-network-tab.png)

    Vous pouvez soit :

    * Rechercher dans la fenêtre et reproduire les problèmes que vous êtes susceptible de rencontrer.

    * Masquer et afficher les fenêtre Outils de développeur à tout moment pendant la session en appuyant sur F12.

1. Pour arrêter la session de profilage, vous pouvez sélectionner le carré rouge sur le **réseau** onglet du développeur des outils de zone.

   ![Onglet réseau d’outils de capture d’écran de Microsoft Edge pour les développeurs avec un appel hors du bouton d’arrêt.](media/service-admin-capturing-additional-diagnostic-information-for-power-bi/edge-network-tab-stop.png)

1. Sélectionnez l’icône de disquette pour exporter les données dans un fichier d’Archive HTTP (HAR).

   ![Onglet réseau d’outils de capture d’écran de Microsoft Edge pour les développeurs avec une légende de l’icône de disquette.](media/service-admin-capturing-additional-diagnostic-information-for-power-bi/edge-network-tab-save.png)

1. Entrez un nom de fichier, puis enregistrez le fichier HAR.

    Le fichier HAR contiendra toutes les informations sur les demandes réseau entre la fenêtre de navigateur et Power BI, notamment :

    * L’ID d’activité pour chaque demande.

    * L’horodatage précis de chaque demande.

    * Aucune information d’erreur retourné au client.

    Ce suivi contient également les données utilisées pour renseigner les éléments visuels affichés à l’écran.

1. Vous pouvez fournir le fichier HAR à prendre en charge pour la révision.

D’autres questions ? [Essayez d’interroger la communauté Power BI](http://community.powerbi.com/)
