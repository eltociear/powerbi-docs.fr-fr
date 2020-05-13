---
title: Questions fréquentes sur les visuels Power BI
description: Parcourir une liste de questions fréquentes et de réponses sur les visuels Power BI
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.topic: conceptual
ms.subservice: powerbi-custom-visuals
ms.custom: ''
ms.date: 12/17/2018
ms.openlocfilehash: 0a66b0fc1a984e0905fba209ca59afb3a02696b2
ms.sourcegitcommit: bfc2baf862aade6873501566f13c744efdd146f3
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83131306"
---
# <a name="power-bi-visuals-faq"></a>Questions fréquentes (FAQ) sur les visuels Power BI

## <a name="organizational-power-bi-visuals"></a>Visuels Power BI d’organisation

Le portail d’administration vous permet de gérer des visuels Power BI pour votre organisation.

### <a name="how-can-the-admin-manage-organizational-power-bi-visuals"></a>Comment l’administrateur peut-il gérer les visuels Power BI d’organisation ?

Dans le portail d’administration, sous l’onglet *Visuels d’organisation*, l’administrateur peut voir et [gérer tous les visuels Power BI d’organisation dans l’entreprise](../../admin/service-admin-portal.md#organizational-visuals). Cela inclut l'ajout, la désactivation, l'activation et la suppression de visuels Power BI.

Les utilisateurs dans l’organisation peuvent facilement trouver des visuels Power BI et les importer dans leurs rapports directement depuis Power BI Desktop ou Service.

Une fois que l’administrateur charge une nouvelle version d’un visuel Power BI de l’organisation, tous les membres de l’organisation obtiennent la même version mise à jour. Tous les rapports utilisant des visuels Power BI mis à jour sont automatiquement mis à jour.

Les utilisateurs trouveront les visuels Power BI de l’organisation dans le magasin Power BI Desktop et Power BI Service intégré, sous l'onglet *MON ORGANISATION*. 

### <a name="if-an-admin-uploads-a-power-bi-visual-from-the-public-marketplace-to-the-organization-store-is-it-automatically-updated-once-a-vendor-updates-the-visual-in-the-public-marketplace"></a>Si un administrateur charge un visuel Power BI à partir de la Place de marché publique dans le magasin de l’organisation, est-il automatiquement mis à jour une fois qu’un fournisseur met à jour le visuel dans la Place de marché publique ?

Non, il n’y a pas de mise à jour automatique à partir de la Place de marché publique. L’administrateur a la responsabilité de la mise à jour de la version des visuels Power BI de l’organisation.

### <a name="is-there-a-way-to-disable-the-organization-store"></a>Est-il possible de désactiver le magasin de l’organisation ?

Non, les utilisateurs voient toujours l’onglet *MON ORGANISATION* dans Power BI Desktop et Power BI Service. Si un administrateur désactive ou supprime tous les visuels Power BI de l’organisation du portail d’administration, le magasin de l’organisation sera vide.
  
### <a name="if-the-admin-disables-power-bi-visuals-from-the-admin-portal-tenant-settings-do-users-still-have-access-to-the-organizational-power-bi-visuals"></a>Si l’administrateur désactive les visuels Power BI à partir du portail d’administration (paramètres du client), les utilisateurs ont-ils toujours accès aux visuels Power BI de l’organisation ?

Oui, si l’administrateur désactive les visuels Power BI à partir du portail d’administration, cela n’affecte pas le magasin d’organisation.

Certaines organisations désactivent les visuels Power BI et activent seulement des visuels sélectionnés manuellement qui ont été importés et chargés par l’administrateur Power BI dans le magasin d’organisation.

La désactivation des visuels Power BI à partir du portail d’administration n’est pas appliquée dans Power BI Desktop. Les utilisateurs de Power BI Desktop peuvent toujours ajouter et utiliser des visuels Power BI à partir de la Place de marché publique dans leurs rapports. Cependant, ces visuels Power BI publics cessent d’être affichés une fois qu’ils sont publiés sur le service Power BI et ils émettent une erreur appropriée. 

Lorsque le paramètre des visuels Power BI dans le portail d’administration est appliqué, les utilisateurs du service Power BI ne peuvent pas importer des visuels Power BI à partir de la Place de marché publique. Seuls les visuels du magasin de l’organisation peuvent être importés.

### <a name="what-are-the-advantages-of-power-bi-visuals-in-the-organizational-store"></a>Quels sont les avantages des visuels Power BI dans le magasin de l’organisation ?

* Tout le monde reçoit la même version du visuel, qui est contrôlée par l’administrateur Power BI. Une fois que l’administrateur met à jour la version du visuel dans le portail d’administration, tous les utilisateurs dans l’organisation obtiennent automatiquement la version mise à jour.

* Pas besoin de partager des fichiers de visuels par e-mail ou par le biais de dossiers partagés. Les offres du magasin de l’organisation sont visibles pour tous les membres connectés.

* En termes de sécurité et de prise en charge, les nouvelles versions des visuels Power BI d’organisation sont automatiquement mises à jour dans tous les rapports.

* Les administrateurs peuvent contrôler quels visuels Power BI sont disponibles dans l’organisation.

* Les administrateurs peuvent activer/désactiver les visuels à des fins de test à partir du portail d’administration.

## <a name="certified-power-bi-visuals"></a>Visuels Power BI certifiés

### <a name="what-are-certified-power-bi-visuals"></a>Qu’est-ce que les visuels Power BI certifiés ?

Les visuels Power BI certifiés sont des visuels Power BI qui répondent à certaines [exigences](power-bi-custom-visuals-certified.md) et sont certifiés par Microsoft.

Sur la [Place de marché](https://appsource.microsoft.com/marketplace/apps?page=1&product=power-bi-visuals), les visuels Power BI certifiés affichent un badge jaune indiquant qu'ils sont certifiés.

Microsoft n’est pas l’auteur des visuels Power BI de tiers. Nous conseillons aux utilisateurs de contacter directement leur auteur pour vérifier de fonctionnement des visuels tiers.

### <a name="what-tests-are-done-during-the-certification-process"></a>Quels sont les tests effectués durant le processus de certification ?

Le processus de certification comprend, entre autres, les tests suivants : 
* Examens du code
* Analyse statique du code
* Fuite de données
* Test à données aléatoires (fuzzing)
* Test de pénétration
* Test d’accès XSS
* Injection de données malveillantes
* Validation d’entrée
* Test fonctionnel
 
### <a name="are-certified-power-bi-visual-checked-again-with-every-new-submission-upgrade"></a>Un visuel Power BI certifié fait-il l’objet d’une nouvelle vérification à chaque nouvelle soumission (mise à niveau) ?

Oui. Chaque fois qu’une nouvelle version d’un visuel certifié est soumise à la Place de marché, la mise à jour de la version du visuel fait l’objet des mêmes vérifications de certification.

La certification d’une mise à jour de la version est automatique. Si une violation entraîne le rejet de la mise à jour, un e-mail est envoyé au développeur pour lui expliquer ce qui doit être corrigé.

### <a name="can-a-certified-power-bi-visual-stop-lose-its-certification-after-a-new-update"></a>Un visuel Power BI certifié peut-il perdre sa certification après une nouvelle mise à jour ?

Non, cela n’est pas possible. Un visuel certifié ne peut pas perdre sa certification après une mise à jour. La mise à jour est rejetée.
 
### <a name="do-i-need-to-share-my-code-in-a-public-repository-if-im-certifying-my-power-bi-visual"></a>Dois-je partager mon code dans un référentiel public si je certifie mon visuel Power BI ?

Non, vous n’avez pas besoin de partager votre code publiquement.

Fournissez les autorisations de lecture pour vérifier le code du visuel Power BI. Par exemple, en utilisant un référentiel privé dans GitHub.
 
### <a name="does-a-certified-power-bi-visual-have-to-be-in-the-marketplace"></a>Un visuel Power BI certifié doit-il être mis sur la Place de marché ?

Oui. Les visuels privés ne sont pas certifiés.
 
### <a name="how-long-does-it-take-to-certify-my-visual"></a>Combien de temps faut-il pour certifier un visuel ?

La certification d'un nouveau visuel Power BI (première certification) peut prendre jusqu'à quatre semaines. 

La certification d'une version mise à jour d'un visuel Power BI peut prendre jusqu'à trois semaines. 

### <a name="does-the-certification-process-ensure-that-there-is-no-data-leakage"></a>Le processus de certification garantit-il l’absence de fuites de données ?

Les tests effectués sont conçus pour vérifier que le visuel n’a pas accès à des services ni à des ressources externes. 

Microsoft n’est pas l’auteur des visuels Power BI de tiers. Nous conseillons aux utilisateurs de contacter directement leur auteur pour vérifier de fonctionnement des visuels Power BI tiers.
 
### <a name="are-uncertified-power-bi-visuals-safe-to-use"></a>Les visuels Power BI non certifiés présentent-ils des risques ?

Un visuel Power BI non certifié ne présente pas nécessairement des risques pour la sécurité.

Certains visuels ne sont pas certifiés car ils ne remplissent pas une ou plusieurs [conditions de certification](power-bi-custom-visuals-certified.md#certification-requirements). Citons par exemple les visuels de carte qui se connectent à un service externe ou ceux qui utilisent des bibliothèques commerciales.
 
## <a name="visuals-with-additional-purchases"></a>Visuels avec achats supplémentaires

### <a name="what-is-a-visual-with-additional-purchases"></a>Qu’est-ce qu’un visuel avec achats supplémentaires ?

Un visuel avec des achats supplémentaires est similaire à un achat dans l'application (IAP). Ces compléments incluent une étiquette de prix **Un autre achat peut être requis**.

Les visuels Power BI IAP sont des visuels Power BI gratuits et téléchargeables. Les utilisateurs n’ont rien à payer pour télécharger ces visuels Power BI à partir de la Place de marché.

Les visuels IAP proposent des achats facultatifs dans l’application pour les fonctionnalités avancées.  

### <a name="what-is-changing-in-the-submission-process"></a>Qu’est-ce qui change dans le processus de soumission ?

Le processus de soumission des visuels Power BI IAP à la Place de marché est identique à celui des visuels Power BI gratuits. Vous pouvez soumettre un visuel Power BI afin qu’il soit certifié en utilisant l’[Espace partenaires](https://docs.microsoft.com/partner-center/).


Lors de l'inscription de votre visuel Power BI, accédez à l'onglet *Programme d’installation du produit*, puis cochez la case *Mon produit nécessite l'achat d'un service*.

### <a name="what-should-i-do-beforesubmittingmy-iap-power-bi-visual"></a>Que dois-je faire avant de soumettre mon visuel Power BI IAP ?

Si vous travaillez sur un visuel Power BI IAP, assurez-vous qu’il soit conforme aux [instructions](guidelines-powerbi-visuals.md).  

> [!NOTE]
> Les visuels Power BI gratuits avec une fonction IAP supplémentaire doivent conserver les mêmes fonctionnalités gratuites que celles offertes précédemment. Vous pouvez compléter les fonctionnalités gratuites existantes par des fonctionnalités avancées payantes facultatives. Nous vous recommandons de soumettre le visuel Power BI IAP avec les fonctionnalités avancées en tant que nouveau visuel Power BI, et de ne pas mettre à jour l'ancien visuel gratuit.

### <a name="do-iap-power-bi-visuals-need-to-be-certified"></a>Les visuels Power BI IAP doivent-ils être certifiés ?

Le processus de [certification](power-bi-custom-visuals-certified.md) est facultatif. Il incombe au développeur de décider de certifier ou non ses visuels Power BI IAP.

### <a name="can-i-get-my-iap-power-bi-visual-certified"></a>Puis-je certifier mes visuels Power BI IAP ?

Oui, une fois votre visuel Power BI IAP approuvé par l’équipe AppSource, vous pouvez soumettre votre visuel Power BI afin qu’il soit [certifié](power-bi-custom-visuals-certified.md).

La certification est un processus facultatif. C’est à vous de décider si vous souhaitez que votre visuel IAP soit certifié.

## <a name="additional-questions"></a>Questions supplémentaires

### <a name="how-to-get-support"></a>Comment obtenir de l’aide ?

N’hésitez pas à contacter le support technique des visuels Power BI à l’adresse pbicvsupport@microsoft.com si vous avez des questions, des commentaires ou des problèmes.  

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations, consultez [Résolution des problèmes de vos visuels Power BI](power-bi-custom-visuals-troubleshoot.md).
