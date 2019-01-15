---
title: Questions fréquentes sur les visuels personnalisés Power BI
description: Parcourir une liste de questions fréquentes et de réponses sur les visuels personnalisés Power BI
author: markingmyname
ms.author: maghan
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.custom: ''
ms.date: 12/17/2018
ms.openlocfilehash: 0418016fd7a194ff2e37e979219b97e94520f9ae
ms.sourcegitcommit: c8c126c1b2ab4527a16a4fb8f5208e0f7fa5ff5a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/15/2019
ms.locfileid: "54282100"
---
# <a name="frequently-asked-questions-about-power-bi-custom-visuals"></a>Questions fréquentes sur les visuels personnalisés Power BI

## <a name="organizational-custom-visuals"></a>Visuels personnalisés d’une organisation

### <a name="how-can-the-admin-manage-the-organizational-custom-visuals"></a>Comment l’administrateur peut-il gérer les visuels personnalisés d’une organisation ?

Dans le portail d’administration, sous l’onglet « Visuels personnalisés de l’organisation » l’administrateur peut voir et [gérer tous les visuels personnalisés de l’organisation dans l’entreprise](https://docs.microsoft.com/power-bi/service-admin-portal#organization-visuals) : ajouter, désactiver, activer et supprimer.
Il n’est plus nécessaire de partager ces visuels par e-mails ou par le biais d’un dossier partagé ! Une fois ces visuels déployés dans le référentiel de l’organisation, les utilisateurs peuvent facilement les trouver et les importer dans leurs rapports, directement depuis Power BI Desktop ou Service. Les visuels personnalisés d’une organisation sont accessibles à partir du magasin intégré (dans Desktop et Service) sous l’onglet *MON ORGANISATION*. Une fois que l’administrateur charge la version d’un nouveau visuel personnalisé de l’organisation, tous les membres de l’organisation obtiennent la même version mise à jour. Les créateurs de rapports n’ont pas besoin de supprimer le visuel dans leurs rapports pour obtenir la nouvelle version de ces visuels, car tous les rapports utilisant ces visuels sont automatiquement actualisés ! Le mécanisme de mise à jour est similaire pour les visuels de la Place de marché.

### <a name="if-an-admin-uploads-a-custom-visual-from-the-public-marketplace-to-the-organization-store-is-it-automatically-updated-once-a-vendor-updates-the-visual-in-the-public-marketplace"></a>Si un administrateur charge un visuel personnalisé à partir de la Place de marché publique dans le magasin de l’organisation, est-il automatiquement mis à jour une fois qu’un fournisseur met à jour le visuel dans la Place de marché publique ?

Non, il n’y a pas de mise à jour automatique à partir de la Place de marché publique.
L’administrateur doit mettre à jour la version des visuels personnalisés de l’organisation.

### <a name="is-there-a-way-to-disable-the-organizational-store"></a>Est-il possible de désactiver le magasin de l’organisation ?

Non, les utilisateurs voient toujours l’onglet « MON ORGANISATION » à partir de Power BI Desktop et Service. L’administrateur peut désactiver ou supprimer tous les visuels personnalisés de l’organisation dans le portail d’administration. Le magasin de l’organisation est alors vide.
  
### <a name="if-the-administrator-disables-custom-visuals-from-the-admin-portal-tenant-settings-do-users-still-have-access-to-the-organizational-custom-visuals"></a>Si l’administrateur désactive les visuels personnalisés à partir du portail d’administration (paramètres du locataire), les utilisateurs ont-ils toujours accès aux visuels personnalisés de l’organisation ?

Oui, si l’administrateur désactive les visuels personnalisés à partir du portail d’administration, cela n’affecte pas le magasin de l’organisation. Certaines organisations désactivent les visuels personnalisés et activent uniquement des visuels sélectionnés manuellement qui ont été importés et chargés par l’administrateur Power BI dans le magasin de l’organisation. La désactivation des visuels personnalisés à partir du portail d’administration n’est pas appliquée dans Power BI Desktop. Les utilisateurs de Desktop peuvent toujours ajouter et utiliser des visuels personnalisés à partir de la Place de marché publique dans leurs rapports. Toutefois, le rendu de ces visuels personnalisés publiques ne s’exécute plus une fois qu’ils sont publiés sur le service Power BI et ils émettent une erreur appropriée. Lorsque vous utilisez le service Power BI, vous ne pouvez pas importer des visuels personnalisés à partir de la Place de marché publique. Seuls les visuels à partir du magasin de l’organisation peuvent être importés, car le paramètre des visuels personnalisés dans le portail d’administration est appliqué dans le service Power BI.

### <a name="why-does-the-organizational-store-and-organizational-custom-visuals-make-a-great-enterprise-solution"></a>En quoi le magasin d’organisation et les visuels personnalisés d’organisation constituent-ils une excellente solution pour l’entreprise ?

* Tout le monde reçoit la même version du visuel, qui est contrôlée par l’administrateur Power BI. Une fois que l’administrateur met à jour la version du visuel dans le portail d’administration, tous les utilisateurs dans l’organisation obtiennent automatiquement la version mise à jour.

* Il n’est plus nécessaire de partager des fichiers de visuels par e-mail ou par le biais de dossiers partagés ! Un seul endroit, visible par tous les membres qui sont connectés.

* En termes de sécurité et de prise en charge, les nouvelles versions des visuels personnalisés d’organisation sont automatiquement mis à jour dans tous les rapports, comme les visuels de la Place de marché.

* Les utilisateurs de l’organisation utilisant les visuels personnalisés d’organisation doivent être connectés pour voir et utiliser les visuels personnalisés d’organisation, qui constituent un élément de sécurité pour l’organisation.

* Les administrateurs peuvent contrôler les visuels personnalisés disponibles dans l’organisation.

* Les administrateurs peuvent activer/désactiver les visuels à des fins de test à partir du portail d’administration. Meilleure mise en œuvre de la sécurité : ces visuels seront autorisés aux seuls membres de l’organisation.

## <a name="certified-custom-visuals"></a>Visuels personnalisés certifiés

### <a name="what-are-certified-custom-visuals"></a>En quoi consistent les visuels personnalisés certifiés ?

Les visuels personnalisés certifiés sont des visuels dans la [Place de marché](https://appsource.microsoft.com/marketplace/apps?page=1&product=power-bi-visuals) répondant à certaines exigences de code [spécifiées](power-bi-custom-visuals-certified.md) et aux tests de l’équipe Power BI.  Les tests effectués sont conçus pour vérifier que le visuel n’a pas accès à des services ni à des ressources externes. Cependant, Microsoft n’est pas l’auteur des visuels personnalisés tiers. Nous conseillons aux utilisateurs de contacter directement leur auteur pour vérifier leur fonctionnement.

## <a name="visuals-with-additional-purchases"></a>Visuels avec achats supplémentaires

### <a name="what-is-a-visual-with-additional-purchases"></a>Qu’est-ce qu’un visuel avec achats supplémentaires ?

Un visuel avec achats supplémentaires est similaire aux compléments d’achat dans l’application (IAP) sur la Place de marché. Ces compléments ont une étiquette de prix indiquant  **Un autre achat peut être requis**.

Les visuels IAP personnalisés sont gratuits et téléchargeables : les utilisateurs n’ont rien à payer pour télécharger ces visuels personnalisés à partir de la Place de marché. Les visuels IAP proposent des achats facultatifs dans l’application pour les fonctionnalités avancées.  

### <a name="whats-the-benefit-to-developers"></a>Quel en est l’avantage pour les développeurs ?

Les visuels IAP personnalisés dans AppSource seront découvrables par les nombreux visiteurs quotidiens, entraînant un trafic important et une sensibilisation accrue pour vos visuels IAP personnalisés et vous en tant que développeur.

Si jusqu’à récemment vous gériez ces visuels depuis votre site Web, vous pouvez désormais les soumettre à AppSource. Cela permet d’augmenter le niveau de découverte et de visibilité des visuels IAP au sein de la Communauté Power BI.

Les visuels dans AppSource profitent d’un canal de retour direct de vos clients qui utilisent le visuel IAP personnalisé, grâce aux avis et au système d’évaluation dans le magasin.  

Une fois le visuel IAP approuvé par l’équipe de validation AppSource, vous pouvez également soumettre ces visuels pour certification. Il s’agit d’un processus facultatif.  

Une fois le visuel certifié, les visuels IAP personnalisés peuvent être exportés vers PowerPoint et apparaissent dans les e-mails reçus lorsqu’un utilisateur s’inscrit aux pages du rapport. Ainsi, les visuels IAP personnalisés peuvent également être certifiés et prendre en charge un jeu de fonctionnalités supplémentaires en les soumettant à la Place de marché.  

### <a name="do-iap-visuals-need-to-be-certified"></a>Les visuels IAP doivent-ils être certifiés ?

Le processus de certification est facultatif. Il incombe au développeur de décider de certifier ses visuels IAP personnalisés ou non, ainsi que ses visuels gratuits.

### <a name="what-is-changing-in-the-submission-process"></a>Qu’est-ce qui change dans le processus de soumission ?

Le processus de soumission des visuels IAP personnalisés à la Place de marché est identique à celui des visuels gratuits. Il s’effectue par le biais du tableau de bord vendeur.  La seule différence dans le processus de soumission est que les développeurs devront indiquer, dans les notes de développeur du tableau de bord vendeur : « Visuels avec achat dans l’application ». Vous devrez également fournir une clé/un jeton de licence, si nécessaire, pour valider les fonctionnalités payantes/avancées.  

Il n’y aura aucune option *Gratuit avec achat dans l’application* dans le tableau de bord vendeur. Vous devez soumettre vos visuels IAP comme étant *gratuits*.

En outre, faites savoir à vos utilisateurs à quoi s’attendre, en fournissant, dans votre magasin, une longue description pour expliquer quelles fonctionnalités sont gratuites et quelles fonctionnalités nécessitent des achats supplémentaires pour fonctionner.  

### <a name="what-should-i-do-beforesubmittingmy-iap-custom-visual"></a>Que dois-je faire avant de soumettre mon visuel IAP personnalisé ?

Si vous travaillez sur un visuel IAP personnalisé ou que vous avez déjà un, assurez-vous qu’il soit conforme aux instructions.  

Si vous avez un logo dans le visuel personnalisé, assurez-vous qu’il soit conforme aux instructions relatives aux logos (couleur, emplacement, taille et déclenchement d’action).

Vous trouverez également des notes de bonnes pratiques dans les instructions.  

### <a name="can-i-get-my-iap-custom-visual-certified"></a>Puis-je certifier mes visuels IAP personnalisés ?

Oui, comme pour les visuels gratuits.  Une fois votre visuel IAP personnalisé approuvé par l’équipe AppSource, vous pouvez soumettre votre visuel au processus de certification.

Pour certifier votre visuel, il faut que ce dernier respecte les exigences de certification. Par exemple, le visuel ne peut pas accéder à des services externes pour la validation de licences.

Souvenez-vous que la certification est un processus facultatif. C’est à vous de décider si vous souhaitez que votre visuel IAP soit certifié.

## <a name="additional-questions"></a>Questions supplémentaires

### <a name="how-to-get-support"></a>Comment obtenir de l’aide ?

N’hésitez pas à contacter le support technique des visuels personnalisés : *pbicvsupport@microsoft.com* si vous avez des questions, des commentaires ou des problèmes.  

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations, consultez [Résolution des problèmes de vos visuels personnalisés Power BI](power-bi-custom-visuals-troubleshoot.md).
