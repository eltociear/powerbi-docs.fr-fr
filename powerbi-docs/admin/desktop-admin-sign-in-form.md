---
title: Gestion du formulaire de connexion Power BI Desktop par les administrateurs
description: Découvrez comment vous pouvez gérer le formulaire de connexion initial lors de l’ouverture de Power BI Desktop.
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: how-to
ms.date: 04/15/2019
ms.author: davidi
ms.openlocfilehash: 44add6bf76e5bc4445df08a76859e05c8fa1638d
ms.sourcegitcommit: c18130ea61e67ba111be870ddb971c6413a4b632
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/09/2020
ms.locfileid: "86160867"
---
# <a name="administrators-manage-the-power-bi-desktop-sign-in-form"></a>Administrateurs : Gérer le formulaire de connexion Power BI Desktop
La première fois que Power BI Desktop est lancé, un formulaire de connexion s’affiche. Vous pouvez renseigner les informations demandées ou vous connecter à Power BI pour continuer. Les administrateurs gèrent ce formulaire avec une clé de Registre. 

![Capture d’écran d’un formulaire de connexion initiale pour Power BI Desktop.](media/desktop-admin-sign-in-form/sign-in-form.png)

Les administrateurs utilisent la clé de Registre suivante pour désactiver le formulaire de connexion. Ceci peut également être envoyé (push) à toute une organisation avec des stratégies globales.

```
Key: HKEY_CURRENT_USER\SOFTWARE\Policies\Microsoft\Microsoft Power BI Desktop
valueName: ShowLeadGenDialog
```
Vous pouvez également essayer la clé suivante, qui a réussi pour certains clients en fonction de leurs configurations :

```
Key: HKEY_CURRENT_USER\SOFTWARE\Microsoft\Microsoft Power BI Desktop
valueName: ShowLeadGenDialog
```

La valeur 0 désactive la boîte de dialogue.




D’autres questions ? [Essayez d’interroger la communauté Power BI](https://community.powerbi.com/)

