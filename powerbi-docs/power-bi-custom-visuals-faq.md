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
ms.openlocfilehash: ff20ece0b96c5037e0ca98be953d77b921e37585
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2019
ms.locfileid: "73874547"
---
# <a name="frequently-asked-questions-about-power-bi-visuals"></a>Questions fréquentes sur les visuels Power BI

## <a name="organizational-visuals"></a>Visuels organisationnels

Le portail d’administration vous permet de gérer un visuel Power BI pour votre organisation.

### <a name="how-can-the-admin-manage-the-organizational-power-bi-visuals"></a>Comment l’administrateur peut-il gérer les visuels Power BI d’organisation ?

Dans le portail d’administration, sous l’onglet « Visuels d’organisation », l’administrateur peut voir et [gérer tous les visuels Power BI d’organisation dans l’entreprise](service-admin-portal.md#organizational-visuals) : ajouter, désactiver, activer et supprimer.
Il n’est plus nécessaire de partager ces visuels par e-mails ou par le biais d’un dossier partagé ! Une fois ces visuels déployés dans le référentiel de l’organisation, les utilisateurs peuvent facilement les trouver et les importer dans leurs rapports, directement depuis Power BI Desktop ou depuis le service Power BI. Les visuels d’organisation sont accessibles à partir du magasin intégré (dans Power BI Desktop et le service Power BI) sous l’onglet *MON ORGANISATION*. Une fois que l’administrateur charge la version d’un nouveau visuel personnalisé de l’organisation, tous les membres de l’organisation obtiennent la même version mise à jour. Les créateurs de rapports n’ont pas besoin de supprimer le visuel dans leurs rapports pour obtenir la nouvelle version de ces visuels, car tous les rapports utilisant ces visuels sont automatiquement actualisés ! Le mécanisme de mise à jour est similaire pour les visuels de la Place de marché.

### <a name="if-an-admin-uploads-a-custom-visual-from-the-public-marketplace-to-the-organization-store-is-it-automatically-updated-once-a-vendor-updates-the-visual-in-the-public-marketplace"></a>Si un administrateur charge un visuel personnalisé à partir de la Place de marché publique dans le magasin de l’organisation, est-il automatiquement mis à jour une fois qu’un fournisseur met à jour le visuel dans la Place de marché publique ?

Non, il n’y a pas de mise à jour automatique à partir de la Place de marché publique.
L’administrateur a la responsabilité de la mise à jour de la version des visuels d’organisation.

### <a name="is-there-a-way-to-disable-the-organizational-store"></a>Est-il possible de désactiver le magasin de l’organisation ?

Non, les utilisateurs voient toujours l’onglet « MON ORGANISATION » à partir de Power BI Desktop et Service. L’administrateur peut désactiver ou supprimer tous les visuels d’organisation dans le portail d’administration. Le magasin d’organisation est alors vide.
  
### <a name="if-the-administrator-disables-power-bi-visuals-from-the-admin-portal-tenant-settings-do-users-still-have-access-to-the-organizational-visuals"></a>Si l’administrateur désactive les visuels Power BI à partir du portail d’administration (Paramètres du client), les utilisateurs ont-ils toujours accès aux visuels d’organisation ?

Oui, si l’administrateur désactive les visuels Power BI à partir du portail d’administration, cela n’affecte pas le magasin d’organisation. Certaines organisations désactivent les visuels Power BI et activent seulement des visuels sélectionnés manuellement qui ont été importés et chargés par l’administrateur Power BI dans le magasin d’organisation. La désactivation des visuels Power BI à partir du portail d’administration n’est pas appliquée dans Power BI Desktop. Les utilisateurs de Power BI Desktop peuvent toujours ajouter et utiliser des visuels Power BI à partir de la Place de marché publique dans leurs rapports. Cependant, ces visuels Power BI publics cessent d’être affichés une fois qu’ils sont publiés sur le service Power BI et ils émettent une erreur appropriée. Quand vous utilisez le service Power BI, vous ne pouvez pas importer des visuels Power BI à partir de la Place de marché publique. Seuls les visuels provenant du magasin d’organisation peuvent être importés, car le paramètre des visuels Power BI dans le portail d’administration est appliqué dans le service Power BI.

### <a name="why-does-the-organizational-store-and-organizational-visuals-make-a-great-enterprise-solution"></a>En quoi le magasin d’organisation et les visuels d’organisation constituent-ils une excellente solution pour l’entreprise ?

* Tout le monde reçoit la même version du visuel, qui est contrôlée par l’administrateur Power BI. Une fois que l’administrateur met à jour la version du visuel dans le portail d’administration, tous les utilisateurs dans l’organisation obtiennent automatiquement la version mise à jour.

* Il n’est plus nécessaire de partager des fichiers de visuels par e-mail ou par le biais de dossiers partagés ! Un seul endroit, visible par tous les membres qui sont connectés.

* En termes de sécurité et de prise en charge, les nouvelles versions des visuels d’organisation sont automatiquement mises à jour dans tous les rapports, comme les visuels de la Place de marché.

* Les utilisateurs de l’organisation utilisant les visuels d’organisation doivent être connectés pour voir et utiliser les visuels d’organisation, qui constituent un élément de sécurité pour l’organisation.

* Les administrateurs peuvent contrôler quels visuels Power BI sont disponibles dans l’organisation.

* Les administrateurs peuvent activer/désactiver les visuels à des fins de test à partir du portail d’administration. Meilleure mise en œuvre de la sécurité : ces visuels seront autorisés aux seuls membres de l’organisation.

## <a name="certified-power-bi-visuals"></a>Visuels Power BI certifiés

### <a name="what-are-certified-power-bi-visuals"></a>Qu’est-ce que les visuels Power BI certifiés ?

Les visuels Power BI certifiés sont des visuels de la [Place de marché](https://appsource.microsoft.com/marketplace/apps?page=1&product=power-bi-visuals) répondant à certaines exigences de code [spécifiées](power-bi-custom-visuals-certified.md) et aux tests de l’équipe Power BI.  Les tests effectués sont conçus pour vérifier que le visuel n’a pas accès à des services ni à des ressources externes. Cependant, Microsoft n’étant pas l’auteur des visuels Power BI de tiers, nous conseillons aux clients de contacter directement leur auteur pour vérifier leur fonctionnement.

### <a name="what-tests-are-done-during-the-certification-process"></a>Quels sont les tests effectués durant le processus de certification ?

Le processus de certification comprend, entre autres, les tests suivants : révisions de code, analyse du code statique, fuite de données, test à données aléatoires (fuzzing), test de pénétration, test d’accès au moyen de scripts de site à site (XSS), injection de données malveillantes, validation de l’entrée et test fonctionnel.
 
### <a name="do-you-certify-visuals-every-submission"></a>Certifiez-vous les visuels à chaque soumission ?

Oui. Chaque fois qu’une nouvelle version d’un visuel certifié est soumise à la Place de marché, la mise à jour de la version du visuel fait l’objet des mêmes vérifications de certification.

Remarque à l’attention des développeurs : Si vous soumettez une mise à jour de la version d’un visuel certifié, il est inutile d’envoyer un e-mail distinct de [demande de certification initiale](https://docs.microsoft.com/power-bi/power-bi-custom-visuals-certified#process-for-submitting-a-custom-visual-for-certification). La certification d’une mise à jour de version se produit automatiquement, et toute violation provoquant un rejet génère l’envoi d’un e-mail qui explique ce qui doit être corrigé. 

### <a name="is-it-possible-that-a-certified-visual-stops-being-certified-with-a-new-update"></a>Est-il possible qu’un visuel certifié ne soit plus certifié après une mise à jour ?

Non, cela n’est pas possible. Un visuel certifié ne peut pas perdre sa certification après une mise à jour. La mise à jour est rejetée.
 
### <a name="do-i-need-to-share-my-code-in-public-repository-if-i-am-submitting-to-the-certification-process"></a>Dois-je partager mon code dans un dépôt public si je le soumets au processus de certification ?

Non, vous n’avez pas besoin de partager votre code publiquement. Toutefois, vous devez nous accorder des autorisations en lecture afin que nous puissions vérifier le code du visuel. par exemple dépôt privé dans GitHub.
 
### <a name="do-we-have-to-publishhttpsdocsmicrosoftcompower-bideveloperoffice-store-the-visual-in-the-marketplacehttpsappsourcemicrosoftcommarketplaceappspage1productpower-bi-visuals-to-certify-it"></a>Est-il nécessaire de [publier](https://docs.microsoft.com/power-bi/developer/office-store) le visuel dans la [Place de marché](https://appsource.microsoft.com/marketplace/apps?page=1&product=power-bi-visuals) pour le certifier ?

Oui. La publication du visuel dans la Place de marché est une condition obligatoire pour la certification.
Pour certifier un visuel personnalisé, il doit être sur nos serveurs. Nous ne pouvons pas certifier les visuels privés.
 
### <a name="how-long-does-it-take-to-certify-my-visual"></a>Combien de temps faut-il pour certifier un visuel ?

Une version mise à jour peut prendre jusqu’à 3 semaines. Une nouvelle soumission (première certification) peut nécessiter jusqu’à 4 semaines. 

### <a name="does-the-certification-process-ensure-that-no-data-leakage-occurs"></a>Le processus de certification garantit-il l’absence de fuites de données ?

Les tests effectués sont conçus pour vérifier que le visuel n’a pas accès à des services ni à des ressources externes. Cependant, Microsoft n’étant pas l’auteur des visuels Power BI de tiers, nous conseillons aux clients de contacter directement leur auteur pour vérifier leur fonctionnement.
 
### <a name="are-uncertified-power-bi-visuals-safe-to-use"></a>Les visuels Power BI non certifiés présentent-ils des risques ?

Un visuel Power BI non certifié ne présente pas nécessairement des risques pour la sécurité.
Certains visuels ne sont pas certifiés car ils ne sont pas conformes à un ou plusieurs [critères de certification](https://docs.microsoft.com/power-bi/power-bi-custom-visuals-certified?#certification-requirements). Citons par exemple les visuels de carte qui se connectent à un service externe ou ceux qui utilisent des bibliothèques commerciales.
 
## <a name="visuals-with-additional-purchases"></a>Visuels avec achats supplémentaires

### <a name="what-is-a-visual-with-additional-purchases"></a>Qu’est-ce qu’un visuel avec achats supplémentaires ?

Un visuel avec achats supplémentaires est similaire aux compléments d’achat dans l’application (IAP) sur la Place de marché. Ces compléments ont une étiquette de prix indiquant **Un autre achat peut être requis**.

Les visuels Power BI IAP sont gratuits et téléchargeables : les utilisateurs n’ont rien à payer pour télécharger ces visuels Power BI à partir de la Place de marché. Les visuels IAP proposent des achats facultatifs dans l’application pour les fonctionnalités avancées.  

### <a name="whats-the-benefit-to-developers"></a>Quel en est l’avantage pour les développeurs ?

Les visuels Power BI IAP dans AppSource sont découvrables par les nombreux visiteurs quotidiens, entraînant un trafic important et une sensibilisation accrue pour vos visuels Power BI IAP et pour vous-même en tant que développeur.

Si jusqu’à récemment vous gériez ces visuels depuis votre site Web, vous pouvez désormais les soumettre à AppSource. Cela permet d’augmenter le niveau de découverte et de visibilité des visuels IAP au sein de la Communauté Power BI.

Les visuels dans AppSource profitent d’un canal de retour direct de vos clients qui utilisent le visuel IAP personnalisé, grâce aux avis et au système d’évaluation dans le magasin.  

Une fois le visuel IAP approuvé par l’équipe de validation AppSource, vous pouvez également soumettre ces visuels pour certification. Il s’agit d’un processus facultatif.  

Une fois le visuel certifié, les visuels Power BI IAP peuvent être exportés vers PowerPoint et affichés dans les e-mails reçus quand un utilisateur s’abonne à des pages de rapport. Ainsi, les visuels Power BI IAP peuvent également être certifiés et prendre en charge un jeu de fonctionnalités supplémentaires quand vous les soumettez à la Place de marché.  

### <a name="do-iap-visuals-need-to-be-certified"></a>Les visuels IAP doivent-ils être certifiés ?

Le processus de certification est facultatif. Il incombe au développeur de décider de certifier ou non ses visuels Power BI IAP , comme pour les visuels gratuits.

### <a name="what-is-changing-in-the-submission-process"></a>Qu’est-ce qui change dans le processus de soumission ?

Le processus de soumission des visuels Power BI IAP à la Place de marché est identique à celui des visuels gratuits. Il s’effectue par le biais du tableau de bord vendeur.  La seule différence dans le processus de soumission est que les développeurs devront indiquer, dans les notes de développeur du tableau de bord vendeur : « Visuels avec achat dans l’application ». Vous devrez également fournir une clé/un jeton de licence, si nécessaire, pour valider les fonctionnalités payantes/avancées.  

Il n’y aura aucune option *Gratuit avec achat dans l’application* dans le tableau de bord vendeur. Vous devez soumettre vos visuels IAP comme étant *gratuits*.

En outre, faites savoir à vos utilisateurs à quoi s’attendre, en fournissant, dans votre magasin, une longue description pour expliquer quelles fonctionnalités sont gratuites et quelles fonctionnalités nécessitent des achats supplémentaires pour fonctionner.  

### <a name="what-should-i-do-beforesubmittingmy-iap-custom-visual"></a>Que dois-je faire avant de soumettre mon visuel IAP personnalisé ?

Si vous travaillez sur un visuel IAP personnalisé ou que vous avez déjà un, assurez-vous qu’il soit conforme aux instructions.  

Si vous avez un logo dans le visuel personnalisé, assurez-vous qu’il soit conforme aux instructions relatives aux logos (couleur, emplacement, taille et déclenchement d’action).

Vous trouverez également des notes de bonnes pratiques dans les instructions.  
> [!Note]
> Tous les visuels gratuits doivent conserver les mêmes fonctionnalités gratuites que celles proposées précédemment. Vous pouvez compléter les fonctionnalités gratuites existantes par des fonctionnalités avancées payantes facultatives. Nous vous recommandons de soumettre les visuels IAP avec les fonctionnalités avancées en tant que nouveaux visuels au lieu de mettre à jour les fonctionnalités gratuites existantes.

### <a name="can-i-get-my-iap-custom-visual-certified"></a>Puis-je certifier mes visuels IAP personnalisés ?

Oui, comme pour les visuels gratuits.  Une fois votre visuel IAP personnalisé approuvé par l’équipe AppSource, vous pouvez soumettre votre visuel au processus de certification.

Pour certifier votre visuel, il faut que ce dernier respecte les exigences de certification. Par exemple, le visuel ne peut pas accéder à des services externes pour la validation de licences.

Souvenez-vous que la certification est un processus facultatif. C’est à vous de décider si vous souhaitez que votre visuel IAP soit certifié.

## <a name="additional-questions"></a>Questions supplémentaires

### <a name="how-to-get-support"></a>Comment obtenir de l’aide ?

N’hésitez pas à contacter le support technique des visuels Power BI : *pbicvsupport@microsoft.com*   si vous avez des questions, des commentaires ou des problèmes.  

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations, consultez [Résolution des problèmes de vos visuels Power BI de Power BI](power-bi-custom-visuals-troubleshoot.md).
