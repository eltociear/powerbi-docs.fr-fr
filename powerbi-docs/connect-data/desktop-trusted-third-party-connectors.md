---
title: Connecteurs tiers approuvés dans Power BI
description: Comment approuver un connecteur tiers signé dans Power BI
author: cpopell
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 04/3/2019
ms.author: gepopell
LocalizationGroup: Connect to data
ms.openlocfilehash: 06b117a271671092a94aa8e7994269344b444178
ms.sourcegitcommit: 9350f994b7f18b0a52a2e9f8f8f8e472c342ea42
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90859609"
---
# <a name="trusted-third-party-connectors"></a>Connecteurs tiers de confiance

## <a name="why-do-you-need-trusted-third-party-connectors"></a>Pourquoi avez-vous besoin de connecteurs tiers approuvés ?

Dans Power BI, nous recommandons généralement de conserver le paramètre « Sécurité des extensions de données » au niveau le plus élevé, ce qui empêche le chargement de code non certifié par Microsoft. Toutefois, il peut y avoir de nombreux cas où vous souhaitez charger des connecteurs spécifiques, ceux que vous avez écrits ou ceux qui vous sont fournis par un consultant ou un fournisseur en dehors de la voie de certification Microsoft.

Le développeur d’un connecteur donné peut le signer à l’aide d’un certificat et vous fournir les informations dont vous avez besoin pour le charger de façon sécurisée sans alléger vos paramètres de sécurité.

Si vous souhaitez en savoir plus sur les paramètres de sécurité, cliquez [ici](./desktop-connector-extensibility.md).

## <a name="using-the-registry-to-trust-third-party-connectors"></a>Utilisation du Registre pour approuver des connecteurs tiers

L’approbation de connecteurs tiers dans Power BI s’effectue en listant l’empreinte numérique du certificat que vous souhaitez approuver dans une valeur de Registre spécifiée. Si cette empreinte numérique correspond à l’empreinte numérique du certificat sur le connecteur à charger, vous pourrez le charger dans le niveau de sécurité « recommandé » de Power BI. 

Le chemin du Registre est HKEY_LOCAL_MACHINE\Software\Policies\Microsoft\Power BI Desktop. Vérifiez que le chemin existe, ou créez-le. Nous avons choisi cet emplacement parce qu’il est principalement contrôlé par la stratégie informatique et nécessite un accès administrateur sur l’ordinateur local pour toute modification. 

![Registre Power BI Desktop sans clés tierces approuvées définies](media/desktop-trusted-third-party-connectors/desktoptrustedthird1.png)

Ajoutez une nouvelle valeur sous le chemin spécifié ci-dessus. Le type doit être « Valeur de chaînes multiples » (REG_MULTI_SZ) et le nom doit être « TrustedCertificateThumbprints ». 

![Registre Power BI Desktop avec une entrée pour les connecteurs tiers approuvés, mais sans clés](media/desktop-trusted-third-party-connectors/desktoptrustedthird2.png)

Ajoutez les empreintes numériques des certificats à approuver. Vous pouvez ajouter plusieurs certificats en utilisant « \0 » comme délimiteur, ou cliquer avec le bouton droit dans l’Éditeur du Registre sur > modifier et placer chaque empreinte numérique sur une nouvelle ligne. Un exemple d’empreinte numérique est extrait d’un certificat auto-signé. 

 ![Registre Power BI Desktop avec une clé tierce approuvée définie](media/desktop-trusted-third-party-connectors/desktoptrustedthird3.png)

Si vous avez correctement suivi les instructions et que le développeur vous a fourni l’empreinte numérique appropriée, vous devez maintenant pouvoir approuver sans problème les connecteurs signés avec le certificat associé.

## <a name="how-to-sign-connectors"></a>Comment signer des connecteurs

Si vous avez un connecteur que vous ou un développeur devez signer, vous pouvez consulter la documentation Power Query [ici](/power-query/handlingconnectorsigning).