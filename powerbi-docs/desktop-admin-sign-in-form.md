---
title: Gestion du formulaire de connexion Power BI Desktop par les administrateurs
description: Découvrez comment vous pouvez gérer le formulaire de connexion initial lors de l’ouverture de Power BI Desktop.
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 04/15/2019
ms.author: davidi
ms.openlocfilehash: 5c31277b640b16882bef5c5f2cd9c56b441ede82
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "61329873"
---
# <a name="how-administrators-can-manage-the-power-bi-desktop-sign-in-form"></a>Gestion du formulaire de connexion Power BI Desktop par les administrateurs
La première fois que Power BI Desktop est lancé, un formulaire de connexion s’affiche. Vous pouvez renseigner les informations demandées ou vous connecter à Power BI pour continuer. Les administrateurs gèrent ce formulaire avec une clé de Registre. 

![Formulaire de connexion initial pour Power BI Desktop](media/desktop-admin-sign-in-form/sign-in-form.png)

Les administrateurs utilisent la clé de Registre suivante pour désactiver le formulaire de connexion. Ceci peut également être envoyé (push) à toute une organisation avec des stratégies globales.

```
Key: HKEY_CURRENT_USER\SOFTWARE\Policies\Microsoft\Microsoft Power BI Desktop
valueName: ShowLeadGenDialog
```
Vous pouvez également essayer la clé suivante, qui s’est déroulée correctement pour certains clients selon leurs configurations :

```
Key: HKEY_CURRENT_USER\SOFTWARE\Microsoft\Microsoft Power BI Desktop
valueName: ShowLeadGenDialog
```

La valeur 0 désactive la boîte de dialogue.




D’autres questions ? [Essayez d’interroger la communauté Power BI](http://community.powerbi.com/)

