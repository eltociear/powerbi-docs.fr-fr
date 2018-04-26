---
title: Gestion du formulaire de connexion Power BI Desktop par les administrateurs
description: Découvrez comment vous pouvez gérer le formulaire de connexion initial lors de l’ouverture de Power BI Desktop.
services: powerbi
documentationcenter: ''
author: davidiseminger
manager: kfile
backup: ''
editor: ''
tags: ''
qualityfocus: no
qualitydate: ''
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 04/24/2018
ms.author: davidi
ms.openlocfilehash: 65bf0a39351b394232211af50692072f7cec7e89
ms.sourcegitcommit: 3f2f254f6e8d18137bae879ddea0784e56b66895
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
---
# <a name="how-administrators-can-manage-the-power-bi-desktop-sign-in-form"></a>Gestion du formulaire de connexion Power BI Desktop par les administrateurs
La première fois que Power BI Desktop est lancé, un formulaire de connexion s’affiche. Vous pouvez remplir les informations demandées ou vous connecter à Power BI pour continuer. Les administrateurs peuvent gérer ce formulaire à l’aide d’une clé de Registre. 

![Formulaire de connexion initial pour Power BI Desktop](media/desktop-admin-sign-in-form/sign-in-form.png)

Les administrateurs peuvent utiliser la clé de Registre suivante pour désactiver le formulaire de connexion. Cela peut également être effectué en utilisant des stratégies globales dans toute l’organisation.

```
Key: HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Power BI Desktop
valueName: ShowLeadGenDialog
```

La valeur 0 désactive la boîte de dialogue.

D’autres questions ? [Essayez d’interroger la communauté Power BI](http://community.powerbi.com/)

