---
title: Activer ou désactiver l’inscription et l’achat en libre-service
description: Consignes destinées aux administrateurs afin de désactiver la possibilité pour les utilisateurs de s’inscrire à Power BI et d’acheter une licence.
author: kfollis
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 04/08/2020
ms.author: kfollis
LocalizationGroup: Administration
ms.openlocfilehash: 561d8b6cd0e17e885ced984315a04376400a2a58
ms.sourcegitcommit: b2cb0b02bdc451bf11a92a68f2c4d560a811f563
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81447507"
---
# <a name="enable-or-disable-self-service-sign-up-and-purchasing"></a>Activer ou désactiver l’inscription et l’achat en libre-service

Dans la plupart des organisations, l’inscription en libre-service est activée par défaut. Les utilisateurs individuels de votre organisation peuvent s’inscrire à Power BI à l’aide de leur compte professionnel ou scolaire. Ils peuvent également acheter directement une licence Power BI Pro s’ils essaient d’utiliser une fonctionnalité nécessitant une licence Pro. En tant qu’administrateur, vous déterminez s’il faut activer ou désactiver l’inscription libre-service. Vous pouvez également contrôler si les utilisateurs de votre organisation peuvent effectuer des achats en libre-service afin d’obtenir de leur propre licence.

> [!NOTE]
>Si vous avez acquis Power BI par le biais d’un fournisseur de solutions Microsoft cloud (CSP), le paramètre peut être désactivé pour empêcher les utilisateurs de s’inscrire individuellement. Votre fournisseur de services cloud peut également jouer le rôle d’administrateur général pour votre organisation, ce qui vous oblige à le contacter pour vous aider à modifier ce paramètre.
>
>

Vous utilisez les commandes PowerShell pour modifier les paramètres qui contrôlent l’inscription et l’achat en libre-service. Il existe deux paramètres qui contrôlent si les utilisateurs de votre organisation peuvent s’inscrire ou effectuer des achats en libre-service.

- Si vous souhaitez désactiver toutes les inscriptions en libre-service, modifiez un paramètre dans Azure Active Directory nommé **AllowAdHocSubscriptions** à l’aide de commandes PowerShell Azure AD. Suivez les étapes de cet article pour [activer ou désactiver l’inscription en libre-service](#enable-or-disable-self-service-signup). Cette option désactive l’inscription en libre-service pour *tous* les services et applications cloud Microsoft.

- Si vous souhaitez empêcher les utilisateurs d’acheter leur propre licence Pro, modifiez le paramètre **AllowSelfServicePurchase** à l’aide de commandes PowerShell MSCommerce. Ce paramètre vous permet de désactiver l’achat en libre-service de produits spécifiques. Suivez les étapes décrites dans cet article pour [activer ou désactiver l’achat en libre-service de licences Power BI Pro](#enable-or-disable-self-service-purchase).

## <a name="enable-or-disable-self-service-signup"></a>Activer ou désactiver l’inscription en libre-service

Si l’inscription en libre-service est activée, la valeur de **AllowAdHocSubscriptions** est *true*. Examinons ce qu’il se passe lorsque vous définissez ce paramètre sur *false* :

- Si vous changez le paramètre de true en false, l’inscription individuelle de nouveaux utilisateurs de votre organisation est bloquée. Tous les utilisateurs inscrits à Power BI avant la modification du paramètre conservent leurs licences.

- Si vous définissez le paramètre sur false, les utilisateurs disposant d’une licence Power BI (gratuite) peuvent toujours s’inscrire pour obtenir une version d’évaluation gratuite individuelle de Power BI Pro.

- Un administrateur doit attribuer toutes les licences Power BI aux nouveaux utilisateurs qui en ont besoin.

### <a name="before-you-begin"></a>Avant de commencer

Ces étapes utilisent des commandes PowerShell Azure Active Directory pour modifier la valeur du paramètre **AllowAdHocSubscriptions**. Le module PowerShell Azure AD doit être installé pour que ces commandes soient disponibles. Pour plus d'informations sur l’utilisation de PowerShell, consultez la page [Prise en main de Windows PowerShell](https://docs.microsoft.com/powershell/scripting/getting-started/getting-started-with-windows-powershell?view=powershell-7).

Pour installer le module Azure AD, démarrez Windows PowerShell en tant qu’administrateur. Assurez-vous que votre stratégie d’exécution locale vous permet d’exécuter des scripts. Si vous rencontrez des problèmes, consultez [Stratégies d’exécution PowerShell](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_execution_policies?view=powershell-7#powershell-execution-policies) pour savoir comment modifier votre stratégie locale.

Exécutez la commande suivante pour installer le module Azure AD :

```powershell
Install-Module MSOnline
```

### <a name="change-the-self-service-signup-policy"></a>Modifier la stratégie d’inscription en libre-service

Dans PowerShell, exécutez la commande suivante pour vous connecter à Azure AD :

```powershell
Connect-MsolService
```

Entrez vos informations d’identification d’administrateur dans la boîte de dialogue de connexion, en effectuant toutes les authentifications à deux facteurs requises. Après la vérification, vous êtes redirigé vers la fenêtre PowerShell.

Pour afficher le paramètre actuel, exécutez la commande suivante. La sortie est dirigée vers une liste mise en forme à l’aide du commutateur « fl ».

```powershell
Get-MsolCompanyInformation | fl AllowAdHocSubscriptions
```

Pour modifier le paramètre actuel, exécutez cette commande :

```powershell
Set-MsolCompanySettings -AllowAdHocSubscriptions $false
```

Après l’exécution de cette commande, l’inscription en libre-service est désactivée pour tous les utilisateurs. Pour la réactiver, réexécutez cette commande et définissez la valeur sur $true.

## <a name="enable-or-disable-self-service-purchase"></a>Activer ou désactiver l’achat en libre-service

Si l’achat en libre-service est activé, la valeur de **AllowSelfServicePurchase** est *true*. Examinons ce qu’il se passe lorsque vous définissez ce paramètre sur *false* :

- Si vous changez le paramètre de true en false, les utilisateurs de votre organisation ne peuvent pas acheter leur propre licence Power BI Pro. Tous les utilisateurs qui ont acheté une licence avant la modification du paramètre conservent leurs licences.

- Si vous définissez le paramètre sur false, les utilisateurs disposant d’une licence Power BI (gratuite) ne peuvent pas obtenir de licence Power BI Pro individuelle. 

- Un administrateur doit attribuer une licence Pro à tous les utilisateurs qui en ont besoin.

### <a name="before-you-begin"></a>Avant de commencer

Ces étapes utilisent des commandes PowerShell MSCommerce pour modifier la valeur du paramètre **AllowSelfServicePurchase**. Le module PowerShell MSCommerce doit être installé pour que ces commandes soient disponibles. Pour plus d'informations sur l’utilisation de PowerShell, consultez la page [Prise en main de Windows PowerShell](https://docs.microsoft.com/powershell/scripting/getting-started/getting-started-with-windows-powershell?view=powershell-7).

Pour installer le module MSCommerce, démarrez Windows PowerShell en tant qu’administrateur. Assurez-vous que votre stratégie d’exécution locale vous permet d’exécuter des scripts. Si vous rencontrez des problèmes, consultez [Stratégies d’exécution PowerShell](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_execution_policies?view=powershell-7#powershell-execution-policies) pour savoir comment modifier votre stratégie locale.

Entrez la commande suivante pour installer le module MSCommerce :

```powershell
Install-Module -name MSCommerce
```

### <a name="change-the-self-service-signup-policy"></a>Modifier la stratégie d’inscription en libre-service

Dans PowerShell, exécutez la commande suivante pour vous connecter :

```powershell
Connect-MSCommerce
```

Entrez vos informations d’identification d’administrateur dans la boîte de dialogue de connexion, en effectuant toutes les authentifications à deux facteurs requises. Après la vérification, la fenêtre PowerShell affiche une connexion réussie.

Pour afficher le paramètre actuel, exécutez la commande suivante. Pour empêcher la troncation du texte, la sortie est dirigée vers une liste mise en forme à l’aide du commutateur « fl ».

```powershell
Get-MSCommercePolicy -PolicyId AllowSelfServicePurchase | fl
```

Vous pouvez désactiver le paramètre qui autorise l’achat en libre-service d’un produit individuel en fournissant son **ProductId**. Pour modifier le paramètre actuel du service Power BI, exécutez la commande suivante :

```powershell
Update-MSCommerceProductPolicy -PolicyId AllowSelfServicePurchase -ProductId CFQ7TTC0L3PB -Enabled $False
```

Après l’exécution de cette commande, l’achat en libre-service pour Power BI est désactivé pour tous les utilisateurs. Pour le réactiver, réexécutez cette commande et définissez la valeur sur $true.

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations sur l’achat en libre-service dans Power BI et le reste de la plateforme Power, consultez les articles suivants :

- [FAQ sur l’achat en libre-service](https://docs.microsoft.com/microsoft-365/commerce/subscriptions/self-service-purchase-faq?view=o365-worldwide#admin-capabilities)
- [Utiliser AllowSelfServicePurchase pour le module MSCommerce PowerShell](https://docs.microsoft.com/microsoft-365/commerce/subscriptions/allowselfservicepurchase-powershell?view=o365-worldwide)
