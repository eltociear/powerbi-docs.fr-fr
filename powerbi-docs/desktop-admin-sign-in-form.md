---
title: Gestion du formulaire de connexion Power BI Desktop par les administrateurs
description: Découvrez comment vous pouvez gérer le formulaire de connexion initial lors de l’ouverture de Power BI Desktop.
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 11/28/2018
ms.author: davidi
ms.openlocfilehash: a61075993afaa75aea420f55babc773dec075f73
ms.sourcegitcommit: c8c126c1b2ab4527a16a4fb8f5208e0f7fa5ff5a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/15/2019
ms.locfileid: "54280886"
---
# <a name="how-administrators-can-manage-the-power-bi-desktop-sign-in-form"></a>Gestion du formulaire de connexion Power BI Desktop par les administrateurs
La première fois que Power BI Desktop est lancé, un formulaire de connexion s’affiche. Vous pouvez renseigner les informations demandées ou vous connecter à Power BI pour continuer. Les administrateurs gèrent ce formulaire avec une clé de Registre. 

![Formulaire de connexion initial pour Power BI Desktop](media/desktop-admin-sign-in-form/sign-in-form.png)

Les administrateurs utilisent la clé de Registre suivante pour désactiver le formulaire de connexion. Ceci peut également être envoyé (push) à toute une organisation avec des stratégies globales.

```
Key: HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Power BI Desktop
valueName: ShowLeadGenDialog
```

La valeur 0 désactive la boîte de dialogue.

D’autres questions ? [Essayez d’interroger la communauté Power BI](http://community.powerbi.com/)

