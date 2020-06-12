---
title: Principal de service - Créer une application
description: Principal de service - Créer une application
services: powerbi
author: KesemSharabi
ms.author: kesharab
ms.topic: include
ms.date: 05/20/2020
ms.custom: include file
ms.openlocfilehash: 0fe3e1743cb8853d6626b59b748d70bfcc292dbd
ms.sourcegitcommit: cd64ddd3a6888253dca3b2e3fe24ed8bb9b66bc6
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/03/2020
ms.locfileid: "84315781"
---
1. Connectez-vous à [Microsoft Azure](https://ms.portal.azure.com/#allservices).

2. Recherchez les **inscriptions d’applications**, puis cliquez sur le lien **Inscriptions d’applications**.

    ![inscription d’application azure](media/embedded-service-principal/azure-app-registration.png)

3. Cliquez sur **Nouvelle inscription**.

    ![nouvelle inscription](media/embedded-service-principal/new-registration.png)

4. Entrez les informations obligatoires :
    * **Nom** : entrer un nom pour votre application
    * **Types de comptes pris en charge** : sélectionner les types de comptes pris en charge
    * (facultatif) **Rédiriger l’URI** : entrer un URI si nécessaire

5. Cliquez sur **S'inscrire**.

6. Une fois l’inscription terminée, l’*ID d’application* est disponible dans l’onglet **Vue d’ensemble**. Copiez et enregistrez l’*ID de l’application* pour une future utilisation.

    ![ID d’application](media/embedded-service-principal/application-id.png)