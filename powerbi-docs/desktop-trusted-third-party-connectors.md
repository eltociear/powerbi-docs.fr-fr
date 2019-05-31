---
title: Approuvé par des tiers des connecteurs dans Power BI
description: Comment approuver un connecteur tiers signé dans Power BI
author: cpopell
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 04/3/2019
ms.author: gepopell
LocalizationGroup: Connect to data
ms.openlocfilehash: 30b7457c6149320c43f24b967a842382821b01b1
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "65607776"
---
# <a name="trusting-third-party-connectors"></a>Connecteurs de tiers autorisé à approuver

## <a name="why-do-you-need-trusted-third-party-connectors"></a>Pourquoi devez-vous confiance les connecteurs tiers ?

Dans Power BI, nous vous recommandons généralement de conservation « extension sécurité de vos données » au niveau au niveau supérieur, ce qui empêche le chargement de code non certifié par Microsoft. Toutefois, il peut arriver nombreuses dans lequel vous souhaitez charger des connecteurs spécifiques--ceux que vous avez écrit, ou celles qui sont fournies pour vous par un consultant ou un fournisseur en dehors du chemin d’accès de certification Microsoft.

Le développeur d’un connecteur donné peut se connecter avec un certificat et vous fournir les informations nécessaires pour la charger en toute sécurité sans en réduisant vos paramètres de sécurité.

Si vous souhaitez en savoir plus sur les paramètres de sécurité, vous pouvez découvrir les [ici](https://docs.microsoft.com/power-bi/desktop-connector-extensibility).

## <a name="using-the-registry-to-trust-third-party-connectors"></a>À l’aide du Registre pour les connecteurs de tiers de confiance

Approbation de connecteurs de tiers dans Power BI est effectuée en répertoriant l’empreinte numérique du certificat que vous souhaitez approuver dans une valeur de Registre spécifiée. Si cette empreinte numérique correspond à l’empreinte numérique du certificat sur le connecteur que vous souhaitez charger, vous serez en mesure de le charger dans le niveau de sécurité « Recommandées » de Power BI. 

Le chemin d’accès du Registre est HKEY_LOCAL_MACHINE\Software\Policies\Microsoft\Power BI Desktop. Assurez-vous que le chemin d’accès existe ou créez-le. Nous avons choisi de cet emplacement en raison de sa principalement contrôlé par la stratégie informatique, mais aussi nécessitant un accès administration ordinateur local à modifier. 

![Définir de Power BI Desktop Registre sans clés tiers approuvé](media/desktop-trusted-third-party-connectors/desktoptrustedthird1.png)

Ajouter une nouvelle valeur sous le chemin d’accès spécifié ci-dessus. Le type doit être « Valeur de chaînes multiples » (REG_MULTI_SZ), et elle doit être appelée « TrustedCertificateThumbprints » 

![Power BI Desktop Registre avec une entrée pour les connecteurs de tiers approuvés, mais aucune clé](media/desktop-trusted-third-party-connectors/desktoptrustedthird2.png)

Ajoutez les empreintes numériques des certificats que vous souhaitez approuver. Vous pouvez ajouter plusieurs certificats à l’aide de « \0 » comme un délimiteur, ou dans l’Éditeur du Registre, droit, cliquez sur -> modifient et placer chaque empreinte sur une nouvelle ligne. Exemple d’empreinte provient d’un certificat auto-signé. 

 ![Power BI Desktop Registre avec un jeu de clés approuvé par des tiers](media/desktop-trusted-third-party-connectors/desktoptrustedthird3.png)

Si vous avez suivi les instructions correctement et disposent de l’empreinte numérique approprié par votre développeur, vous devez maintenant pouvoir en toute sécurité les connecteurs de confiance signés avec le certificat associé.

## <a name="how-to-sign-connectors"></a>Comment signer des connecteurs

Si vous avez un connecteur vous ou un développeur obligé de vous connecter, vous trouverez plus d’informations dans la documentation de Power Query [ici](https://docs.microsoft.com/power-query/handlingconnectorsigning).
