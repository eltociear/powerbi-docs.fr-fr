---
title: Utiliser une adresse de messagerie de secours
description: Utiliser une adresse de messagerie de secours
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 04/23/2019
ms.author: mblythe
LocalizationGroup: Troubleshooting
ms.openlocfilehash: 88432f55fc8cfeefa07b66ea68437bbb23f12531
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "64906652"
---
# <a name="use-an-alternate-email-address"></a>Utiliser une adresse de messagerie de secours

Lorsque vous vous inscrivez à Power BI, vous fournissez une adresse e-mail. Par défaut, Power BI utilise cette adresse pour vous envoyer des mises à jour sur l’activité dans le service. Par exemple, quand quelqu’un vous envoie une invitation de partage, elle est expédiée à cette adresse.

Dans certains cas, vous souhaiterez peut-être que ces e-mails soient envoyés à une autre adresse e-mail que celle utilisée pour vous inscrire. Cet article explique comment spécifier une autre adresse dans Office 365 et dans PowerShell. Cet article explique comment Azure Active Directory (Azure AD) résout une adresse de messagerie.

> [!NOTE]
> La spécification d’une autre adresse n’affecte pas l’adresse e-mail utilisée par Power BI pour les mises à jour du service, les lettres d’information et les autres communications publicitaires. Ces communications sont toujours envoyées à l’adresse de messagerie que vous avez utilisé lorsque vous êtes inscrit à Power BI.

## <a name="use-office-365"></a>Utiliser Office 365

Pour spécifier une autre adresse dans Office 365, procédez comme suit.

1. Ouvrez la [page d’informations personnelles Office 365](https://portal.office.com/account/#personalinfo). Si l’application vous y invite, connectez-vous à l’adresse e-mail et le mot de passe utilisé pour Power BI.

1. Dans le menu de gauche, sélectionnez **informations personnelles**.

1. Dans la section **Détails du contact**, sélectionnez **Modifier**.

    Si vous ne pouvez pas modifier les détails de votre, cela signifie que votre administrateur Office 365 gère votre adresse de messagerie. Contactez votre administrateur pour mettre à jour votre adresse de messagerie.

    ![Détails du contact](media/service-admin-alternate-email-address-for-power-bi/contact-details.png)

1. Dans le **autre adresse de messagerie** , entrez l’adresse de messagerie que vous souhaitez que Office 365 pour les mises à jour de Power BI.

## <a name="use-powershell"></a>Utiliser PowerShell

Pour spécifier une autre adresse dans PowerShell, utilisez la commande [Set-AzureADUser](/powershell/module/azuread/set-azureaduser/).

```powershell
Set-AzureADUser -ObjectId john@contoso.com -OtherMails "otheremail@somedomain.com"
```

## <a name="email-address-resolution-in-azure-ad"></a>Résolution d’adresse e-mail ans Azure AD

Pour capturer un Azure AD le jeton incorporé pour Power BI, vous pouvez utiliser une des trois différents types d’adresses de messagerie :

* L’adresse de messagerie principale associée à un compte d’utilisateur Azure AD

* L’adresse e-mail UPN (UserPrincipalName)

* L’attribut de tableau *autre adresse e-mail*

Power BI sélectionne l’e-mail à utiliser en fonction de la séquence suivante :

1. Si l’attribut de messagerie est défini dans l’objet utilisateur Azure AD, Power BI l’utilise pour l’adresse e-mail.

1. Si l’adresse e-mail UPN n’est *pas* une adresse e-mail du domaine **\*.onmicrosoft.com** (informations après le symbole « \@ »), Power BI utilise cet attribut de messagerie pour l’adresse e-mail.

1. Si le *autre adresse de messagerie* attribut de tableau dans l’objet utilisateur Azure AD n’est présent, alors que Power BI utilise la première adresse e-mail dans cette liste (dans la mesure où il peut y avoir une liste d’e-mails dans cet attribut).

1. Si aucune des conditions ci-dessus sont présentes, Power BI utilise l’adresse UPN.

D’autres questions ? [Posez vos questions à la communauté Power BI](http://community.powerbi.com/)