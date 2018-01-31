---
title: Administration de Power BI dans votre organisation
description: Administration de Power BI dans votre organisation
services: powerbi
documentationcenter: 
author: markingmyname
manager: kfile
backup: 
editor: 
tags: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 11/28/2017
ms.author: maghan
ms.openlocfilehash: 0fd6226ca14a4b48c94e13eaae8b085381a5f9a6
ms.sourcegitcommit: 6e693f9caf98385a2c45890cd0fbf2403f0dbb8a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/30/2018
---
# <a name="administering-power-bi-in-your-organization"></a>Administration de Power BI dans votre organisation
Microsoft Power BI permet aux utilisateurs de visualiser des données, de partager des découvertes et de collaborer de façon intuitive. Pour en savoir plus, consultez [Prise en main de Power BI](service-get-started.md).

L’administration de Power BI peut s’effectuer dans plusieurs emplacements. Voici deux emplacements courants.

> [!NOTE]
> Pour obtenir l’accès au portail d’administration Power BI, votre compte doit être un compte d’**Administrateur global** dans Office 365 ou Azure Active Directory, ou doit avoir été assigné au rôle d’Administrateur de Service Power BI. Pour plus d’informations sur le rôle d’administrateur de Service Power BI, voir [Présentation du rôle d’administrateur Power BI](service-admin-role.md).
> 
> 

* [Portail d’administration Power BI](https://app.powerbi.com/admin-portal)
* [Centre d’administration Office 365](https://portal.office.com/adminportal/home)

Pour plus d’informations sur le rôle d’administrateur de Service Power BI, consultez [Présentation du rôle d’administrateur Power BI](service-admin-role.md).

## <a name="whats-in-this-article"></a>Que contient cet article ?
**S’inscrire à Power BI**

* [Comment les utilisateurs peuvent-ils s’inscrire à Power BI ?](#how-do-users-sign-up-for-power-bi)
* [Comment les utilisateurs individuels de mon organisation peuvent-ils s’inscrire ?](#how-do-individual-users-in-my-organization-sign-up)
* [Comment empêcher les utilisateurs de rejoindre mon locataire Office 365 existant ?](#how-can-i-prevent-users-from-joining-my-existing-office-365-tenant)
* [Comment puis-je permettre aux utilisateurs de s’associer à mon locataire Office 365 existant ?](#how-can-i-allow-users-to-join-my-existing-office-365-tenant)
* [Comment vérifier que le blocage est activé dans le locataire ?](#how-do-i-verify-if-i-have-the-block-on-in-the-tenant)
* [Comment empêcher les utilisateurs existants d’utiliser Power BI ?](#how-can-i-prevent-my-existing-users-from-starting-to-use-power-bi)
* [Comment puis-je autoriser mes utilisateurs existants à s’inscrire à Power BI ?](#how-can-i-allow-my-existing-users-to-sign-up-for-power-bi)

**Administration de Power BI**

* [Quelles seront les conséquences sur ma méthode actuelle de gestion des identités pour les utilisateurs de mon organisation ?](#how-will-this-change-the-way-i-manage-identities-for-users-in-my-organization-today)
* [Comment faire pour gérer Power BI ?](#how-do-we-manage-power-bi)
* [Quelle est la procédure à suivre pour gérer un locataire créé par Microsoft pour mes utilisateurs ?](#what-is-the-process-to-manage-a-tenant-created-by-Microsoft-for-my-users)
* [Si j’utilise plusieurs domaines, puis-je contrôler le locataire Office 365 auquel sont ajoutés les utilisateurs ?](#if-i-have-multiple-domains-can-i-control-the-office-365-tenant-that-users-are-added-to)
* [Comment supprimer Power BI pour les utilisateurs déjà inscrits ?](#how-do-i-remove-power-bi-for-users-that-already-signed-up)
* [Comment connaître la date à laquelle les nouveaux utilisateurs ont rejoint mon locataire ?](#how-do-i-know-when-new-users-have-joined-my-tenant)
* [Quels sont les éventuels autres aspects auxquels je dois être préparé ?](#are-there-any-additional-things-i-should-be-prepared-for)
* [Est-ce gratuit ? Ces licences me seront-elles facturées ?](#is-this-free-will-i-be-charged-for-these-licenses)
* [Où est situé mon locataire Power BI ?](#where-is-my-power-bi-tenant-located)
* [Présentation du contrat SAL Power BI](#what-is-the-power-bi-sla)

**Sécurité dans Power BI**

* [Power BI répond-il aux exigences de conformité nationales, régionales et sectorielles ?](#does-power-bi-meet-national-regional-and-industry-specific-compliance-requirements)
* [Comment fonctionne la sécurité dans Power BI ?](#how-does-security-work-in-power-bi?)

## <a name="sign-up-for-power-bi"></a>S’inscrire à Power BI
### <a name="how-do-users-sign-up-for-power-bi"></a>Comment les utilisateurs peuvent-ils s’inscrire à Power BI ?
Vous pouvez vous inscrire à Power BI sur le [site web de Power BI](https://powerbi.microsoft.com). Vous pouvez également vous abonner depuis la page Services d’achat du Centre d’administration Office 365. Quand un administrateur s’inscrit à Power BI, il peut attribuer des licences aux utilisateurs autorisés.

En outre, les utilisateurs de votre organisation peuvent s’inscrire à Power BI sur le [site web de Power BI](https://powerbi.microsoft.com). Quand un utilisateur de votre organisation s’inscrit à Power BI, il reçoit automatiquement une licence Power BI. [En savoir plus](service-self-service-signup-for-power-bi.md)

### <a name="how-do-individual-users-in-my-organization-sign-up"></a>Comment les utilisateurs individuels de mon organisation peuvent-ils s’inscrire ?
Trois scénarios peuvent s’appliquer aux utilisateurs de votre organisation :

Scénario 1 : votre organisation possède déjà un environnement Office 365 et l’utilisateur qui s’inscrit à Power BI a déjà un compte Office 365.
Dans ce scénario, si un utilisateur possède déjà un compte professionnel ou scolaire dans le client (par exemple, contoso.com) mais n’a pas encore Power BI, Microsoft activera simplement l’offre pour ce compte et l’utilisateur sera automatiquement informé en relation avec l’utilisation du service Power BI.

Scénario 2 : votre organisation possède un environnement Office 365 et l’utilisateur qui s’inscrit à Power BI n’a pas de compte Office 365.
Dans ce scénario, l’utilisateur possède une adresse de messagerie appartenant au domaine de votre organisation (par exemple, contoso.com), mais il ne possède pas encore de compte Office 365. Dans ce cas, l’utilisateur peut s’inscrire à Power BI et recevoir automatiquement un compte. Il peut ainsi accéder au service Power BI. Par exemple, si une employée nommée Nancy utilise son adresse de messagerie professionnelle (par exemple, Nancy@contoso.com) pour s’inscrire, Microsoft ajoute automatiquement Nancy en tant qu’utilisateur dans l’environnement Office 365 de Contoso et active Power BI pour son compte.

Scénario 3 : votre organisation n’a pas d’environnement Office 365 connecté à votre domaine de messagerie.
Il n’est pas nécessaire que votre organisation prenne une action administrative pour utiliser Power BI. Les utilisateurs seront ajoutés à un nouveau répertoire utilisateur situé dans le cloud et vous aurez la possibilité de devenir l’administrateur client et de gérer les utilisateurs.

> [!IMPORTANT]
> Si votre organisation possède plusieurs domaines de messagerie et si vous préférez que toutes les extensions d’adresse de messagerie appartiennent au même client, ajoutez tous les domaines d’adresse de messagerie à un client Azure Active Directory avant que des utilisateurs ne s’inscrivent. Il n’existe aucun mécanisme automatique permettant de déplacer des utilisateurs d’un client à l’autre une fois ceux-ci créés. Pour plus d’informations sur ce processus, consultez [Si j’utilise plusieurs domaines, puis-je contrôler le client Office 365 auquel sont ajoutés les utilisateurs ?](#if-i-have-multiple-domains-can-i-control-the-office-365-tenant-that-users-are-added-to) plus loin dans cet article, ainsi que l’article en ligne [Add your domain to Office 365](https://support.office.com/article/Add-your-users-and-domain-to-Office-365-6383f56d-3d09-4dcb-9b41-b5f5a5efd611) (Ajouter votre domaine à Office 365).
> 
> 

### <a name="how-can-i-prevent-users-from-joining-my-existing-office-365-tenant"></a>Comment empêcher les utilisateurs de rejoindre mon client Office 365 existant ?
En tant qu’administrateur, vous disposez de plusieurs moyens pour empêcher les utilisateurs de s’associer à votre client Office 365 existant. Dans ce cas, quand les utilisateurs tenteront de s’inscrire, ils recevront un message d’erreur leur indiquant de contacter l’administrateur de leur entreprise. Il est inutile de répéter ce processus si vous avez déjà désactivé la distribution automatique des licences (par exemple, Office 365 pour l’éducation, pour les étudiants, les enseignants et le personnel).

Ces étapes nécessitent l’utilisation de Windows PowerShell. Pour commencer à utiliser Windows PowerShell, consultez le [guide de prise en main de PowerShell](http://go.microsoft.com/fwlink/p/?LinkID=286814).

Pour effectuer les étapes suivantes, vous devez installer la dernière version 64 bits du [module Azure Active Directory pour Windows PowerShell](http://go.microsoft.com/fwlink/p/?LinkID=236297).

Après avoir cliqué sur le lien, sélectionnez **Exécuter** pour exécuter le package d’installation.

**Disable automatic tenant join** (Désactiver l’association automatique au client) : utilisez cette commande Windows PowerShell pour empêcher les nouveaux utilisateurs de s’associer à un client géré :

* Pour désactiver l’association automatique des nouveaux utilisateurs au client :
  
    $msolcred = get-credential   connect-msolservice -credential $msolcred
  
    Set-MsolCompanySettings -AllowEmailVerifiedUsers $false
* Pour activer l’association automatique des nouveaux utilisateurs au client :
  
    $msolcred = get-credential   connect-msolservice -credential $msolcred
  
    Set-MsolCompanySettings -AllowEmailVerifiedUsers $true

> [!NOTE]
> Ce blocage empêche les nouveaux utilisateurs de votre organisation de s’inscrire à Power BI. Les utilisateurs qui se sont inscrits à Power BI avant que vous ne désactiviez les nouvelles inscriptions conserveront leurs licences. Consultez la section « Comment supprimer Power BI pour les utilisateurs déjà inscrits ? » pour obtenir des instructions sur la façon de supprimer l’accès à Power BI pour les utilisateurs déjà inscrits au service.
> 
> 

### <a name="how-can-i-allow-users-to-join-my-existing-office-365-tenant"></a>Comment puis-je permettre aux utilisateurs de s’associer à mon client Office 365 existant ?
Pour autoriser les utilisateurs à s’associer à votre locataire, exécutez la commande inverse, comme décrit dans la section ci-dessus.

Pour effectuer les étapes suivantes, vous devez installer la dernière version 64 bits du [module Azure Active Directory pour Windows PowerShell](http://go.microsoft.com/fwlink/p/?LinkID=236297).

    $msolcred = get-credential
    connect-msolservice -credential $msolcred

    Set-MsolCompanySettings -AllowEmailVerifiedUsers $true

### <a name="how-do-i-verify-if-i-have-the-block-on-in-the-tenant"></a>Comment vérifier que le blocage est activé dans le client ?
Utilisez le script PowerShell suivant.

Pour effectuer les étapes suivantes, vous devez installer la dernière version 64 bits du [module Azure Active Directory pour Windows PowerShell](http://go.microsoft.com/fwlink/p/?LinkID=236297).

    $msolcred = get-credential
    connect-msolservice -credential $msolcred

    Get-MsolCompanyInformation | fl allow*

### <a name="how-can-i-prevent-my-existing-users-from-starting-to-use-power-bi"></a>Comment empêcher les utilisateurs existants d’utiliser Power BI ?
En tant qu’administrateur, vous disposez de plusieurs moyens pour empêcher les utilisateurs de s’inscrire à Power BI. Dans ce cas, quand les utilisateurs tenteront de s’inscrire, ils recevront un message d’erreur leur indiquant de contacter l’administrateur de leur entreprise. Il est inutile de répéter ce processus si vous avez déjà désactivé la distribution automatique des licences (par exemple, Office 365 pour l’éducation, pour les étudiants, les enseignants et le personnel). [En savoir plus](service-admin-service-free-in-your-organization.md#enable-or-disable-individual-user-sign-up-in-azure-active-directory)

Le paramètre AAD qui contrôle cette option est **AllowAdHocSubscriptions**. Chez la plupart des clients, ce paramètre est configuré sur True. Cela signifie qu’il est activé. Si vous avez acquis Power BI via un partenaire, ce paramètre peut être configuré sur False par défaut. Cela signifie qu’il est désactivé.

Pour effectuer les étapes suivantes, vous devez installer la dernière version 64 bits du [module Azure Active Directory pour Windows PowerShell](http://go.microsoft.com/fwlink/p/?LinkID=236297).

1. Vous devez tout d’abord vous connecter à Azure Active Directory à l’aide de vos informations d’identification Office 365. La première ligne vous invite à indiquer vos informations d’identification. La deuxième ligne établit la connexion à Azure Active Directory.
   
     $msolcred = get-credential   connect-msolservice -credential $msolcred
2. Une fois connecté, vous pouvez émettre la commande suivante pour voir la configuration actuelle de votre client.
   
     Get-MsolCompanyInformation | fl AllowAdHocSubscriptions
3. Vous pouvez utiliser cette commande pour activer ($true) ou désactiver ($false) AllowAdHocSubscriptions.
   
     Set-MsolCompanySettings -AllowAdHocSubscriptions $true

> [!NOTE]
> L’indicateur AllowAdHocSubscriptions permet de contrôler plusieurs fonctionnalités d’utilisateur dans votre organisation, notamment la possibilité pour les utilisateurs de s’inscrire au service Azure Rights Management. La modification de cet indicateur affecte toutes ces fonctionnalités.
> 
> 

### <a name="how-can-i-allow-my-existing-users-to-sign-up-for-power-bi"></a>Comment puis-je autoriser mes utilisateurs existants à s’inscrire à Power BI ?
Pour permettre aux utilisateurs existants de s’inscrire à Power BI, exécutez la commande indiquée dans la section précédente, mais passez la valeur true au lieu de la valeur false.

Pour effectuer les étapes suivantes, vous devez installer la dernière version 64 bits du [module Azure Active Directory pour Windows PowerShell](http://go.microsoft.com/fwlink/p/?LinkID=236297).

1. Vous devez tout d’abord vous connecter à Azure Active Directory à l’aide de vos informations d’identification Office 365. La première ligne vous invite à indiquer vos informations d’identification. La deuxième ligne établit la connexion à Azure Active Directory.
   
     $msolcred = get-credential   connect-msolservice -credential $msolcred
2. Une fois connecté, vous pouvez émettre la commande suivante pour voir la configuration actuelle de votre client.
   
     Get-MsolCompanyInformation | fl AllowAdHocSubscriptions
3. Vous pouvez utiliser cette commande pour activer ($true) ou désactiver ($false) AllowAdHocSubscriptions.
   
     Set-MsolCompanySettings -AllowAdHocSubscriptions $true

> [!NOTE]
> L’indicateur AllowAdHocSubscriptions permet de contrôler plusieurs fonctionnalités d’utilisateur dans votre organisation, notamment la possibilité pour les utilisateurs de s’inscrire au service Azure Rights Management. La modification de cet indicateur affecte toutes ces fonctionnalités.
> 
> 

## <a name="administration-of-power-bi"></a>Administration de Power BI
### <a name="how-will-this-change-the-way-i-manage-identities-for-users-in-my-organization-today"></a>Quelles seront les conséquences sur ma méthode actuelle de gestion des identités pour les utilisateurs de mon organisation ?
Si votre organisation possède déjà un environnement Office 365 et que tous les utilisateurs de votre organisation ont des comptes Office 365, la gestion des identités ne change pas.

Si votre organisation possède déjà un environnement Office 365, mais que tous les utilisateurs n’ont pas de compte Office 365, Microsoft crée un utilisateur dans le client et attribue des licences en fonction de l’adresse de messagerie professionnelle ou académique de l’utilisateur. Cela signifie que le nombre d’utilisateurs que vous gérez à un moment donné augmente à mesure que les utilisateurs de votre entreprise s’inscrivent au service.

Si vous gérez votre répertoire localement et utilisez Active Directory Federation Services (AD FS), Microsoft n’ajoute pas les utilisateurs à votre client. Les utilisateurs qui tentent de rejoindre votre client reçoivent un message leur indiquant de contacter l’administrateur de l’organisation.

Si votre organisation ne possède pas d’environnement Office 365 connecté à votre domaine de messagerie, la gestion des identités ne sera pas modifiée. Les utilisateurs seront ajoutés à un nouveau répertoire utilisateur situé dans le cloud et vous aurez la possibilité de devenir l’administrateur client et de gérer les utilisateurs.

### <a name="how-do-we-manage-power-bi"></a>Comment faire pour gérer Power BI ?
Power BI fournit un portail d’administration qui permet d’afficher les statistiques d’utilisation. Il fournit également un lien vers le Centre d’administration Office 365 qui permet de gérer les utilisateurs et les groupes, ainsi que de contrôler les paramètres au niveau du client. 

> [!NOTE]
> Pour obtenir l’accès au portail d’administration Power BI, votre compte doit être un compte **Administrateur global** dans Office 365 ou Azure Active Directory.
> 
> 

Pour plus d’informations, consultez [Portail d’administration Power BI](service-admin-portal.md).

### <a name="what-is-the-process-to-manage-a-tenant-created-by-microsoft-for-my-users"></a>Quel est la procédure à suivre pour gérer un client créé par Microsoft pour mes utilisateurs ?
Si un client a été créé par Microsoft, vous pouvez le revendiquer et le gérer en procédant comme suit :

1. Associez-vous au client en vous inscrivant à Power BI et en utilisant un domaine d’adresse de messagerie correspondant au domaine de client que vous voulez gérer. Par exemple, si Microsoft a créé le client contoso.com, vous devez vous associer au client dont l’adresse de messagerie se termine par @contoso.com.
2. Revendiquez le contrôle d’administrateur en vérifiant que vous êtes propriétaire du domaine. Une fois dans le client, vous pouvez vous attribuer vous-même le rôle *d’administrateur global* en vérifiant la propriété du domaine. Pour ce faire, procédez comme suit :
   
   1. Accédez à [https://portal.office.com](https://portal.office.com).
   2. Sélectionnez l’icône du lanceur d’applications en haut à gauche, puis choisissez **Administrateur**.
   3. Lisez les instructions de la page **Become the admin** (Devenir administrateur), puis choisissez **Yes, I want to be the admin** (Oui, je souhaite devenir administrateur).
      
      > [!NOTE]
      > Si cette option n’apparaît pas, cela signifie qu’un administrateur Office 365 a déjà été désigné.
      > 
      > 

### <a name="if-i-have-multiple-domains-can-i-control-the-office-365-tenant-that-users-are-added-to"></a>Si j’utilise plusieurs domaines, puis-je contrôler le client Office 365 auquel sont ajoutés les utilisateurs ?
Si vous ne faites rien, un client est créé pour chaque domaine et sous-domaine de messagerie d’utilisateur.

Si vous voulez regrouper tous les utilisateurs dans un seul client quelle que soit leur extension d’adresse de messagerie :

* Créez un client cible au préalable, ou utilisez un client existant, puis ajoutez tous les domaines et sous-domaines existants que vous voulez consolider au sein de ce client. Tous les utilisateurs dont l’adresse de messagerie se termine par ces domaines et sous-domaines seront alors automatiquement associés au client cible lors de leur inscription.

> [!IMPORTANT]
> Il n’existe aucun mécanisme automatique permettant de déplacer des utilisateurs d’un client à l’autre une fois ceux-ci créés. Pour en savoir plus sur l’ajout de domaines à un seul client Office 365, consultez [Vérifier votre domaine dans Office 365, configurer des domaines](https://support.office.com/article/Add-your-users-and-domain-to-Office-365-6383f56d-3d09-4dcb-9b41-b5f5a5efd611).
> 
> 

### <a name="how-do-i-remove-power-bi-for-users-that-already-signed-up"></a>Comment supprimer Power BI pour les utilisateurs déjà inscrits ?
Si vous ne voulez pas qu’un utilisateur déjà inscrit à Power BI puisse accéder à ce service, vous pouvez supprimer la licence Power BI de cet utilisateur.

1. Accédez au Centre d’administration Office 365.
2. Dans la barre de navigation de gauche, sélectionnez **Utilisateurs** > **Utilisateurs actifs**.
3. Recherchez l’utilisateur dont vous voulez supprimer la licence, sélectionnez son nom, puis cliquez sur **Modifier**.
4. Sur la page concernant les détails sur l’utilisateur, cliquez sur **Licences** dans la barre de navigation gauche.
5. Décochez la case **Power BI (gratuit)** ou **Power BI Pro**, selon la licence appliquée à son compte.
6. Sélectionnez **Enregistrer**.

> [!NOTE]
> Vous pouvez également effectuer une gestion en bloc des licences utilisateurs. Pour ce faire, sélectionnez plusieurs utilisateurs, puis sélectionnez **Modifier**.
> 
> 

### <a name="how-do-i-know-when-new-users-have-joined-my-tenant"></a>Comment connaître la date à laquelle les nouveaux utilisateurs ont rejoint mon client ?
Les utilisateurs qui ont rejoint votre client dans le cadre de ce programme se voient attribuer une licence unique, que vous pouvez filtrer dans votre volet d’utilisateur actif dans le tableau de bord d’administration.

Pour créer cette nouvelle vue, dans le Centre d’administration Office 365, accédez à **Utilisateurs** > **Utilisateurs actifs**. Ensuite, dans le menu **Select a View** (Sélectionner une vue), sélectionnez **New View** (Nouvelle vue). Nommez votre nouvelle vue, puis, sous **Licence attribuée**, sélectionnez **Power BI (gratuit)** ou **Power BI Pro**. Vous ne pouvez sélectionner qu’une seule licence par vue. Si votre organisation a à la fois des licences **Power BI (gratuit)** et des licences **Power BI Pro**, vous devrez créer deux vues. Une fois la nouvelle vue créée, vous pourrez voir tous les utilisateurs de votre client qui se sont inscrits au programme.

### <a name="are-there-any-additional-things-i-should-be-prepared-for"></a>Quels sont les éventuels autres aspects auxquels je dois être préparé ?
Vous pouvez avoir à gérer une augmentation des demandes de réinitialisation de mot de passe. Pour plus d’informations sur ce processus, consultez [Réinitialiser le mot de passe d’un utilisateur dans Office 365](https://support.office.com/article/Reset-a-users-password-7a5d073b-7fae-4aa5-8f96-9ecd041aba9c).

Vous pouvez supprimer un utilisateur de votre client en suivant le processus standard dans le Centre d’administration Office 365. Cependant, si l’utilisateur a toujours une adresse de messagerie active au sein de votre organisation, il pourra s’associer au client, sauf si vous empêchez tous les utilisateurs de le faire.

### <a name="is-this-free-will-i-be-charged-for-these-licenses"></a>Est-ce gratuit ? Ces licences me seront-elles facturées ?
Les licences **Power BI (gratuit)** correspondent à la version gratuite de Power BI. Si vous êtes intéressé par des fonctionnalités supplémentaires, consultez [Contenu Power BI Pro - De quoi s’agit-il ?](service-premium.md).

### <a name="where-is-my-power-bi-tenant-located"></a>Où est situé mon client Power BI ?
Pour savoir comment trouver l’emplacement de votre client Power BI, également appelé région de données, consultez [Où est situé mon client Power BI ?](service-admin-where-is-my-tenant-located.md)

### <a name="what-is-the-power-bi-sla"></a>Présentation du contrat SLA Power BI
Pour plus d’informations sur le contrat SLA Power BI, consultez les [termes du contrat de licence et la documentation](http://www.microsoftvolumelicensing.com/DocumentSearch.aspx?Mode=3&DocumentTypeId=37) dans la section **Licences** du site web Microsoft Licensing.

## <a name="security-in-power-bi"></a>Sécurité dans Power BI
### <a name="does-power-bi-meet-national-regional-and-industry-specific-compliance-requirements"></a>Power BI répond-il aux exigences de conformité nationales, régionales et sectorielles ?
Pour plus d’informations sur la conformité Power BI, consultez le [Centre de gestion de la confidentialité Microsoft](http://go.microsoft.com/fwlink/?LinkId=785324).

### <a name="how-does-security-work-in-power-bi"></a>Comment fonctionne la sécurité dans Power BI ?
Power BI repose sur les bases d’Office 365, qui lui-même repose sur des services Azure comme Azure Active Directory. Pour obtenir une vue d’ensemble de l’architecture de Power BI, consultez [Sécurité de Power BI](service-admin-power-bi-security.md). 

## <a name="next-steps"></a>Étapes suivantes
[Portail d’administration Power BI](service-admin-portal.md)  
[Présentation du rôle d’administrateur Power BI](service-admin-role.md)  
[Inscription en libre-service à Power BI](service-self-service-signup-for-power-bi.md)  
[Power BI (gratuit) dans votre organisation](service-admin-service-free-in-your-organization.md)  
[Achat de Power BI Pro](service-admin-purchasing-power-bi-pro.md)  
[Qu’est-ce que Power BI Premium ?](service-premium.md)  
[Acheter Power BI Premium](service-admin-premium-purchase.md)  
[Gestion des comptes utilisateur (Office 365)](https://technet.microsoft.com/library/office-365-user-account-management.aspx)  
[Gestion des groupes Office 365](https://support.office.com/Article/Find-help-about-Groups-in-Office-365-7a9b321f-b76a-4d53-b98b-a2b0b7946de1)  
[Gérer votre groupe dans Power BI et Office 365](service-manage-app-workspace-in-power-bi-and-office-365.md)  
[Livre blanc sur Power BI Premium](https://aka.ms/pbipremiumwhitepaper)  

D’autres questions ? [Essayez d’interroger la communauté Power BI](http://community.powerbi.com/)

