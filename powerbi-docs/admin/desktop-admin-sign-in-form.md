---
title: Gestion du formulaire de connexion Power BI Desktop par les administrateurs
description: Découvrez comment vous pouvez gérer le formulaire de connexion initial lors de l’ouverture de Power BI Desktop.
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: how-to
ms.date: 04/15/2019
ms.openlocfilehash: 633d71326009881b22b7b7d235316b4ebe5c132f
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2020
ms.locfileid: "96386878"
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

