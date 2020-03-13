---
title: Configurer les paramètres d’interaction de rapport
description: Découvrez comment remplacer les paramètres d’interaction par défaut des rapports.
author: paulinbar
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-mobile
ms.topic: conceptual
ms.date: 03/08/2020
ms.author: painbar
ms.openlocfilehash: c7280b2b6bb34b070e7ced3785959d61c74cd165
ms.sourcegitcommit: 87b7cb4a2e626711b98387edaa5ff72dc26262bb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/10/2020
ms.locfileid: "79041252"
---
# <a name="configure-report-interaction-settings"></a>Configurer les paramètres d’interaction de rapport

## <a name="overview"></a>Vue d’ensemble

L’application mobile Power BI a un certain nombre de paramètres « d’interaction » configurables qui vous permettent de contrôler la façon dont vous interagissez avec vos données et de définir la façon dont certains éléments de l’application mobile Power BI se comportent. Le tableau ci-dessous répertorie les paramètres d’interaction actuellement disponibles et les appareils qui en disposent.

|| Téléphone Android | iPhone | Tablette Android  | iPad |
|-|:-:|:-:|:-:|:-:|
| [Interaction de type appui simple ou double sur les visuels de rapport](#single-tap) |✔|✔|||
| [Sélection multiple ou sélection unique de points de données sur les visuels de rapport](#multi-select) |✔|✔|✔|✔|
| [Pied de page de rapport ancré ou dynamique](#docked-report-footer) |✔|✔|||
| [Actualisation de rapport lancée via un bouton ou via Balayer pour actualiser](#report-refresh) |✔||||
|

Pour accéder aux paramètres d’interaction, appuyez sur l’image de votre profil pour ouvrir le [panneau latéral](./mobile-apps-home-page.md#header), choisissez **Paramètres** et recherchez la section **Interaction**.

![Paramètres d’interaction](./media/mobile-app-interaction-settings/powerbi-mobile-app-interactions-section.png)

Les paramètres d’interaction sont décrits dans les sections ci-dessous.

## <a name="interaction-settings"></a>Paramètres d’interaction

### <a name="single-tap"></a>Appui simple
Quand vous téléchargez l’application mobile Power BI, elle est définie pour une interaction avec appui simple. Cela signifie que quand vous appuyez dans un visuel pour effectuer une action, par exemple la sélection d’un élément d’un sélecteur, la sélection croisée, un clic sur un lien ou un bouton, etc., l’appui sélectionne le visuel et effectue aussi l’action souhaitée.

Si vous préférez, vous pouvez désactiver l’interaction avec appui simple. L’interaction se fait alors via un appui double. Avec l’interaction d’appui double, vous appuyez d’abord sur un visuel pour le sélectionner, puis vous rappuyez dans le visuel pour effectuer l’action souhaitée.

### <a name="multi-select"></a>Sélection multiple

L’option de sélection multiple permet de sélectionner plusieurs points de données sur une page de rapport. Lorsque la sélection multiple est activée, chaque point de données sur lequel vous appuyez est ajouté aux autres points de données sélectionnés, et les résultats combinés sont automatiquement mis en surbrillance dans tous les visuels de la page. Lorsque la sélection multiple est désactivée, lorsque vous appuyez pour sélectionner un point de données, la nouvelle sélection remplace la sélection actuelle.

Pour désélectionner un point de données, appuyez à nouveau dessus.

>[!NOTE]
>La sélection multiple n’est pas prise en charge dans les visuels personnalisés.
>
>Le mode de sélection multiple sera pris en charge sur Power BI Report Server dans la prochaine version du serveur de rapports.

### <a name="docked-report-footer"></a>Pied de page de rapport ancré

Le paramètre de pied de page de rapport ancré détermine si le pied de page du rapport reste ancré (c’est-à-dire fixe et toujours visible) au bas du rapport, ou s’il est masqué et réapparaît en fonction de vos actions dans le rapport, comme le défilement.

Sur les téléphones Android, le paramètre de pied de page de rapport ancré est **activé** par défaut, ce qui signifie que le pied de page du rapport est ancré et toujours visible au bas du rapport. Passez le paramètre sur **Désactivé** si vous préférez un pied de page de rapport dynamique qui apparaît et disparaît, en fonction de vos actions sur le rapport.

### <a name="report-refresh"></a>Actualisation de rapport

Le paramètre d’actualisation des rapports définit la façon dont vous lancez les actualisations des rapports. Vous pouvez choisir d’avoir un bouton d’actualisation sur les en-têtes de tous les rapports ou bien d’utiliser l’action Balayer pour actualiser (en effectuant un léger balayage de haut en bas) sur la page du rapport pour l’actualiser. La figure ci-dessous illustre les deux alternatives. 

![Bouton d’actualisation et Balayer pour actualiser](./media/mobile-app-interaction-settings/powerbi-mobile-app-interactions-refresh-button-versus-pull.png)

Sur les téléphones Android, un bouton d’actualisation est ajouté par défaut.

Pour changer le paramètre d’actualisation des rapports, accédez à l’élément d’actualisation des rapports dans les paramètres d’interaction. La valeur actuelle du paramètre est affichée. Appuyez sur la valeur pour ouvrir une fenêtre contextuelle où vous pouvez choisir une nouvelle valeur.

![Définir l’actualisation](./media/mobile-app-interaction-settings/powerbi-mobile-app-interactions-set-refresh.png)

## <a name="remote-configuration"></a>Configuration distante

Les interactions peuvent également être configurées à distance par un administrateur via un outil MDM avec un fichier de configuration d’application. De cette façon, il est possible de standardiser l’expérience d’interaction des rapports au sein de l’organisation ou pour des groupes spécifiques d’utilisateurs de l’organisation. Pour plus d’informations, consultez [Configurer l’interaction avec la gestion des appareils mobiles](./mobile-app-configuration.md).


## <a name="next-steps"></a>Étapes suivantes
* [Interaction avec les rapports](./mobile-reports-in-the-mobile-apps.md#interact-with-reports)
* [Configurer l’interaction avec la gestion des appareils mobiles](./mobile-app-configuration.md)
