---
title: Administration de Power BI - Forum Aux Questions (FAQ)
description: Découvrez les réponses aux questions fréquemment posées sur l’inscription à Power BI, gestion de client et d’autres tâches d’administration.
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 11/16/2018
ms.author: mblythe
LocalizationGroup: Administration
ms.openlocfilehash: 2e51017333a940bd9d7838e6a903c1a66ce2e342
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "65100786"
---
# <a name="administering-power-bi---frequently-asked-questions-faq"></a>Administration de Power BI - Forum Aux Questions (FAQ)

Cet article répond aux questions fréquemment posées concernant l’administration de Power BI. Pour une vue d’ensemble de l’administration de Power BI, consultez [Présentation de l’administration de Power BI](service-admin-administering-power-bi-in-your-organization.md).

## <a name="whats-in-this-article"></a>Que contient cet article ?

### <a name="sign-up-for-power-bi-section"></a>S’inscrire à la section Power BI

* [Avec PowerShell](#using-powershell)
* [Comment les utilisateurs peuvent-ils s’inscrire à Power BI ?](#how-do-users-sign-up-for-power-bi)
* [Comment les utilisateurs individuels de mon organisation peuvent-ils s’inscrire ?](#how-do-individual-users-in-my-organization-sign-up)
* [Comment empêcher les utilisateurs de rejoindre mon locataire Office 365 existant ?](#how-can-i-prevent-users-from-joining-my-existing-office-365-tenant)
* [Comment puis-je permettre aux utilisateurs de s’associer à mon locataire Office 365 existant ?](#how-can-i-allow-users-to-join-my-existing-office-365-tenant)
* [Comment vérifier que le bloc activé dans le client ?](#how-do-i-check-if-i-have-the-block-on-in-the-tenant)
* [Comment empêcher les utilisateurs existants d’utiliser Power BI ?](#how-can-i-prevent-my-existing-users-from-starting-to-use-power-bi)
* [Comment puis-je autoriser mes utilisateurs existants à s’inscrire à Power BI ?](#how-can-i-allow-my-existing-users-to-sign-up-for-power-bi)

### <a name="administration-of-power-bi-section"></a>Administration de la section Power BI

* [Quelles seront les conséquences sur ma méthode actuelle de gestion des identités pour les utilisateurs de mon organisation ?](#how-will-this-change-the-way-i-manage-identities-for-users-in-my-organization-today)
* [Comment faire pour gérer Power BI ?](#how-do-we-manage-power-bi)
* [Quelle est la procédure à suivre pour gérer un locataire créé par Microsoft pour mes utilisateurs ?](#what-is-the-process-to-manage-a-tenant-created-by-microsoft-for-my-users)
* [Si j’utilise plusieurs domaines, puis-je contrôler le client Office 365 auquel les utilisateurs sont ajoutés à ?](#if-i-have-multiple-domains-can-i-control-the-office-365-tenant-that-users-get-added-to)
* [Comment supprimer Power BI pour les utilisateurs déjà inscrits ?](#how-do-i-remove-power-bi-for-users-that-already-signed-up)
* [Comment connaître la date à laquelle les nouveaux utilisateurs ont rejoint mon locataire ?](#how-do-i-know-when-new-users-have-joined-my-tenant)
* [Existe-t-il des éventuels autres aspects que je dois préparer ?](#are-there-any-additional-things-i-should-prepare-for)
* [Où est situé mon locataire Power BI ?](#where-is-my-power-bi-tenant-located)
* [Présentation du contrat SAL Power BI](#what-is-the-power-bi-sla)
* [Comment Power BI gère la haute disponibilité et le basculement ?](#how-does-power-bi-handle-high-availability-and-failover)

### <a name="security-in-power-bi-section"></a>Sécurité dans la section Power BI

* [Power BI répond-il aux exigences de conformité nationales, régionales et sectorielles ?](#does-power-bi-meet-national-regional-and-industry-specific-compliance-requirements)
* [Comment fonctionne la sécurité dans Power BI ?](#how-does-security-work-in-power-bi)

## <a name="sign-up-for-power-bi"></a>S’inscrire à Power BI

### <a name="using-powershell"></a>Avec PowerShell

Certaines procédures de cette section nécessitent des scripts Windows PowerShell. Si vous n’êtes pas familiarisé avec PowerShell, nous vous recommandons le [guide de prise en main de PowerShell](http://go.microsoft.com/fwlink/p/?LinkID=286814). Pour exécuter les scripts, commencez par installer la dernière version 64 bits d’[Azure Active Directory PowerShell for Graph](/powershell/azure/active-directory/).

### <a name="how-do-users-sign-up-for-power-bi"></a>Comment les utilisateurs peuvent-ils s’inscrire à Power BI ?

En tant qu’administrateur, vous pouvez vous inscrire à Power BI sur le [site web de Power BI](https://powerbi.microsoft.com) ou [acheter des services](https://admin.microsoft.com/AdminPortal/Home#/catalog) page sur le centre d’administration Microsoft 365. Lorsqu’un administrateur s’inscrit à Power BI, ils peuvent affecter les licences utilisateur pour les utilisateurs qui doivent avoir accès.

En outre, les utilisateurs de votre organisation peuvent s’inscrire à Power BI sur le [site web de Power BI](https://powerbi.microsoft.com). Lorsqu’un utilisateur de votre organisation s’inscrit à Power BI, le service affecte automatiquement une licence Power BI à l’utilisateur. Pour plus d’informations, consultez [inscrivant à Power BI en tant qu’individu](service-self-service-signup-for-power-bi.md) et [gestion des licences Power BI dans votre organisation](service-admin-licensing-organization.md).

### <a name="how-do-individual-users-in-my-organization-sign-up"></a>Comment les utilisateurs individuels de mon organisation peuvent-ils s’inscrire ?

Trois scénarios peuvent s’appliquer aux utilisateurs de votre organisation :

* **Scénario 1** : votre organisation possède déjà un environnement Office 365, et l’utilisateur qui s’inscrit à Power BI a déjà un compte Office 365.
    Dans ce scénario, si un utilisateur possède déjà un travail ou scolaire dans le locataire (par exemple, contoso.com), mais ne dispose pas encore Power BI, Microsoft Active simplement le plan pour ce compte. L’utilisateur est automatiquement averti avec les informations sur la façon d’utiliser le service Power BI.

* **Scénario 2** : votre organisation possède déjà un environnement Office 365, mais l’utilisateur qui s’inscrit à Power BI n’a pas de compte Office 365.
    Dans ce scénario, l’utilisateur dispose d’une adresse de messagerie dans le domaine de votre organisation (par exemple, contoso.com) mais ne dispose pas encore un compte Office 365. Dans ce cas, l’utilisateur peut s’inscrire à Power BI et reçoit automatiquement un compte. Cette action permet l’accès utilisateur au service Power BI. Par exemple, si une employée nommée Nancy utilise son adresse de messagerie professionnelle (comme nancy@contoso.com) pour vous inscrire, Microsoft ajoute automatiquement Nancy en tant qu’utilisateur dans l’environnement Office 365 de Contoso et Active Power BI pour ce compte.

* **Scénario 3** : Votre organisation n’a pas d’environnement Office 365 connecté à votre domaine de messagerie.
    Il n’existe aucune action d’administration est nécessaire pour votre organisation afin de tirer parti de Power BI. Le service ajoute des utilisateurs à un annuaire d’utilisateurs de nouveau, uniquement dans le cloud. Vous pouvez également reprendre tant qu’administrateur du locataire et les gérer.

> [!IMPORTANT]
> Si votre organisation possède plusieurs domaines de messagerie et si vous préférez que toutes les extensions d’adresse de messagerie appartiennent au même client, ajoutez tous les domaines d’adresse de messagerie à un client Azure Active Directory avant que des utilisateurs ne s’inscrivent. Une fois que vous avez créé des utilisateurs, il n’existe aucun mécanisme automatique pour déplacer les utilisateurs. Pour plus d’informations sur ce processus, consultez [si je possède plusieurs domaines, puis-je contrôler le client Office 365 auquel les utilisateurs sont ajoutés à ?](#if-i-have-multiple-domains-can-i-control-the-office-365-tenant-that-users-get-added-to) plus loin dans cet article et [ajouter un domaine à Office 365](/office365/admin/setup/add-domain/).

### <a name="how-can-i-prevent-users-from-joining-my-existing-office-365-tenant"></a>Comment empêcher les utilisateurs de rejoindre mon client Office 365 existant ?

En tant qu’administrateur, vous disposez de plusieurs moyens pour empêcher les utilisateurs de s’associer à votre client Office 365 existant. Si vous bloquez l’accès, les tentatives d’utilisateurs pour vous inscrire en panne, et un message leur demandant de contacter l’administrateur de. leur organisation Vous n’avez pas besoin de répéter ce processus si vous avez déjà désactivé la distribution automatique de licences (par exemple, via Office 365 Éducation pour les étudiants, enseignants et le personnel).

Utilisez le script PowerShell suivant pour empêcher les nouveaux utilisateurs de s’associer à un client géré. ([En savoir plus sur PowerShell][1].)

```powershell
$msolcred = get-credential
connect-msolservice -credential $msolcred

Set-MsolCompanySettings -AllowEmailVerifiedUsers $false
```

> [!NOTE]
> Le blocage de l’accès empêche les nouveaux utilisateurs de votre organisation de s’inscrire à Power BI. Les utilisateurs qui s’inscrivent à Power BI avant la désactivation des nouvelles inscriptions conservent leurs licences. Pour supprimer un utilisateur, consultez [Comment supprimer Power BI pour les utilisateurs déjà inscrits ?](#how-do-i-remove-power-bi-for-users-that-already-signed-up) plus loin dans cet article.

### <a name="how-can-i-allow-users-to-join-my-existing-office-365-tenant"></a>Comment puis-je permettre aux utilisateurs de s’associer à mon client Office 365 existant ?

Utilisez le script PowerShell suivant pour vous permettre de nouveaux utilisateurs joindre un client géré. ([En savoir plus sur PowerShell][1].)

```powershell
$msolcred = get-credential
connect-msolservice -credential $msolcred

Set-MsolCompanySettings -AllowEmailVerifiedUsers $true
```

### <a name="how-do-i-check-if-i-have-the-block-on-in-the-tenant"></a>Comment vérifier que le bloc activé dans le client ?

Utilisez le script PowerShell suivant pour vérifier les paramètres. *AllowEmailVerifiedUsers* doit avoir la valeur False. ([En savoir plus sur PowerShell][1].)

```powershell
$msolcred = get-credential
connect-msolservice -credential $msolcred

Get-MsolCompanyInformation | fl allow*
```

### <a name="how-can-i-prevent-my-existing-users-from-starting-to-use-power-bi"></a>Comment empêcher les utilisateurs existants d’utiliser Power BI ?

Le paramètre Azure AD qui contrôle cette option est **AllowAdHocSubscriptions**. La plupart des clients sont défini sur true, ce qui signifie qu’il est activé. Si vous avez acquis Power BI auprès d’un partenaire, il peut être défini sur false, ce qui signifie qu’elle est désactivée.

Utilisez le script PowerShell suivant pour désactiver les abonnements ad hoc. ([En savoir plus sur PowerShell][1].)

1. Connectez-vous à Azure Active Directory avec vos informations d’identification Office 365. La première ligne du script PowerShell suivant vous invite à entrer vos informations d’identification. La deuxième ligne établit la connexion à Azure Active Directory.

    ```powershell
     $msolcred = get-credential
     connect-msolservice -credential $msolcred
    ```

   ![Capture d’écran d’Azure Active Directory connectez-vous via PowerShell](media/service-admin-licensing-organization/azure-ad-sign-in.png)

1. Une fois que vous vous connecterez, exécutez la commande suivante pour voir comment votre client est actuellement configuré.

    ```powershell
     Get-MsolCompanyInformation | fl AllowAdHocSubscriptions
    ```

1. Exécutez la commande suivante pour activer (`$true`) ou désactiver (`$false`) **AllowAdHocSubscriptions**.

    ```powershell
     Set-MsolCompanySettings -AllowAdHocSubscriptions $false
    ```

> [!NOTE]
> Utilisez le **AllowAdHocSubscriptions** indicateur pour contrôler plusieurs fonctionnalités d’utilisateur dans votre organisation, notamment la possibilité pour les utilisateurs à s’inscrire pour le Service Azure Rights Management. La modification de cet indicateur affecte toutes ces fonctionnalités.

### <a name="how-can-i-allow-my-existing-users-to-sign-up-for-power-bi"></a>Comment puis-je autoriser mes utilisateurs existants à s’inscrire à Power BI ?

Pour autoriser vos utilisateurs existants à s’inscrire à Power BI, exécutez la commande indiquée pour la question précédente, mais passer `$true` au lieu de `$false` à l’étape précédente.

## <a name="administration-of-power-bi"></a>Administration de Power BI

### <a name="how-will-this-change-the-way-i-manage-identities-for-users-in-my-organization-today"></a>Quelles seront les conséquences sur ma méthode actuelle de gestion des identités pour les utilisateurs de mon organisation ?

Trois scénarios peuvent s’appliquer aux utilisateurs de votre organisation :

* **Scénario 1** : Si votre organisation possède déjà un environnement Office 365 et que tous les utilisateurs de votre organisation ont des comptes Office 365, il n’existe aucune modification dans la gestion des identités.

* **Scénario 2** : Si votre organisation possède déjà un environnement Office 365, mais pas tous les utilisateurs de votre organisation ont des comptes Office 365, nous créer un utilisateur dans le locataire et attribuer des licences en fonction de travail de l’utilisateur ou adresse e-mail scolaire.

    Par conséquent, le nombre d’utilisateurs que vous gérez à un moment donné augmente mesure que les utilisateurs de votre organisation s’inscrivent pour le service.

* **Scénario 3** : Si votre organisation n’a pas d’environnement Office 365 connecté à votre domaine de messagerie, il n’existe aucune modification dans la gestion des identités.

    Le service ajoute des utilisateurs à un annuaire d’utilisateurs de nouveau, uniquement dans le cloud. En outre, vous pouvez choisir reprendre tant qu’administrateur du locataire et les gérer.

### <a name="how-do-we-manage-power-bi"></a>Comment faire pour gérer Power BI ?

Power BI fournit un portail d’administration qui vous permet d’afficher les statistiques d’utilisation, fournit un lien vers le centre d’administration Microsoft 365 pour gérer les utilisateurs et groupes et offre la possibilité de contrôler les paramètres de l’échelle du client.

Pour utiliser le portail d’administration Power BI, vous devez marquer votre compte comme un **administrateur général** dans Office 365 ou Azure Active Directory, ou une personne doit affecter le rôle d’administrateur de service Power BI à votre compte d’utilisateur. Pour plus d’informations, consultez [présentation du rôle d’administrateur Power BI](service-admin-role.md) et [portail d’administration Power BI](service-admin-portal.md).

### <a name="what-is-the-process-to-manage-a-tenant-created-by-microsoft-for-my-users"></a>Quel est la procédure à suivre pour gérer un client créé par Microsoft pour mes utilisateurs ?

Lorsqu’un utilisateur libre-service s’inscrit pour un service cloud qui utilise Azure AD, le service les ajoute à un Azure non géré annuaire AD en fonction de son domaine de messagerie. Vous pouvez revendiquer et gérer le client que quelqu'un créé à l’aide d’un processus appelé un *prise en charge administrateur*. Le type de prise en charge de procéder varie selon s’il existe un existant de client associé à votre domaine géré :

* Utilisez une *prise de contrôle interne* afin de créer un nouveau client managé pour le domaine.

* Utilisez une *prise de contrôle externe* pour déplacer le domaine vers un locataire managé existant.

Pour plus d’informations, consultez [reprendre un répertoire non géré en tant qu’administrateur dans Azure Active Directory](/azure/active-directory/users-groups-roles/domains-admin-takeover).

Lorsque vous effectuez une prise en charge externe, le service place Power BI contenu qui a été créé avant la prise en charge dans un [espace de travail Power BI archivé](service-admin-power-bi-archived-workspace.md). Vous devez migrer manuellement le contenu que vous souhaitez utiliser dans le nouveau locataire.

### <a name="if-i-have-multiple-domains-can-i-control-the-office-365-tenant-that-users-get-added-to"></a>Si j’utilise plusieurs domaines, puis-je contrôler le client Office 365 auquel les utilisateurs sont ajoutés à ?

Si vous ne faites rien, le service crée un client pour chaque domaine de messagerie d’utilisateur et un sous-domaine. Si vous voulez regrouper tous les utilisateurs dans un seul client quelle que soit leur extension d’adresse de messagerie : Créer un client cible au préalable, ou utilisez un client existant. Puis ajoutez tous les domaines et sous-domaines existants que vous voulez consolider au sein de ce client. Chaque utilisateur avec les adresses de messagerie se terminant par ces domaines et sous-domaines automatiquement joindre le client cible lors de leur inscription.

> [!IMPORTANT]
> Une fois que vous avez créé des utilisateurs, il n’existe aucun mécanisme automatisé pris en charge pour déplacer les utilisateurs. Pour en savoir plus sur l’ajout de domaines à un seul client Office 365, consultez [Vérifier votre domaine dans Office 365, configurer des domaines](/office365/admin/setup/add-domain/).

### <a name="how-do-i-remove-power-bi-for-users-that-already-signed-up"></a>Comment supprimer Power BI pour les utilisateurs déjà inscrits ?

Si vous ne voulez pas qu’un utilisateur déjà inscrit à Power BI puisse accéder à ce service, vous pouvez supprimer sa licence Power BI.

1. Accédez au [Centre d’administration Microsoft 365](https://admin.microsoft.com/AdminPortal/Home#/homepage).

1. Dans la barre de navigation de gauche, sélectionnez **Utilisateurs** > **Utilisateurs actifs**.

1. Recherchez l’utilisateur dont vous voulez supprimer la licence, puis sélectionnez son nom.

    Vous pouvez également effectuer une gestion en bloc des licences utilisateurs. Pour ce faire, sélectionnez plusieurs utilisateurs, puis sélectionnez **Modifier les licences de produits**.

1. À la page de détails de l’utilisateur, à côté de **Licences de produits** et sélectionnez **Modifier**.

1. Selon ce que vous la licence appliquée à leur compte, définissez **Power BI (gratuit)** ou **Power BI Pro** à **hors**.

1. Sélectionnez **Enregistrer**.

### <a name="how-do-i-know-when-new-users-have-joined-my-tenant"></a>Comment connaître la date à laquelle les nouveaux utilisateurs ont rejoint mon client ?

Les utilisateurs qui ont rejoint votre client dans le cadre de ce programme sont affectés une licence unique que vous pouvez filtrer dans votre volet de l’utilisateur actif dans le tableau de bord d’administration. Pour créer cette nouvelle vue, procédez comme suit.

1. Accédez au [Centre d’administration Microsoft 365](https://admin.microsoft.com/AdminPortal/Home#/homepage).

1. Dans la barre de navigation de gauche, sélectionnez **Utilisateurs** > **Utilisateurs actifs**.

1. Dans le menu **Vues**, sélectionnez **Ajouter un affichage personnalisé**.

1. Nommez votre nouvelle vue, puis, sous **Licence produit attribuée**, sélectionnez **Power BI (gratuit)** ou **Power BI Pro**.

    Vous ne pouvez sélectionner qu’une seule licence par vue. Si votre organisation a à la fois des licences **Power BI (gratuit)** et des licences **Power BI Pro**, vous devrez créer deux vues.

1. Entrez d’autres conditions de votre choix, puis sélectionnez **Ajouter**.

1. Après avoir créé la nouvelle vue, il est disponible à partir de la **vues** menu.

### <a name="are-there-any-additional-things-i-should-prepare-for"></a>Existe-t-il des éventuels autres aspects que je dois préparer ?

Vous pouvez avoir à gérer une augmentation des demandes de réinitialisation de mot de passe. Pour plus d’informations sur ce processus, consultez [réinitialiser un mot de passe utilisateur](/office365/admin/add-users/reset-passwords).

Vous pouvez supprimer un utilisateur de votre locataire en suivant le processus standard dans le Centre d’administration Microsoft 365. Cependant, si l’utilisateur a toujours une adresse e-mail active au sein de votre organisation, il peut s’associer au client, sauf si vous empêchez tous les utilisateurs de le faire.

### <a name="where-is-my-power-bi-tenant-located"></a>Où est situé mon client Power BI ?

Pour plus d’informations sur la région de données trouve votre client Power BI, consultez [où est situé mon client Power BI ?](service-admin-where-is-my-tenant-located.md).

### <a name="what-is-the-power-bi-sla"></a>Présentation du contrat SLA Power BI

Pour plus d’informations sur le contrat SLA (Service Level Agreement) de Power BI, consultez le [termes du contrat de licence et Documentation](http://www.microsoftvolumelicensing.com/DocumentSearch.aspx?Mode=3&DocumentTypeId=37) article dans le **Licensing** section du site Web Microsoft Licensing.

### <a name="how-does-power-bi-handle-high-availability-and-failover"></a>Comment Power BI gère la haute disponibilité et le basculement ?

Pour plus d’informations sur la haute disponibilité et de basculement, consultez [Power BI haute disponibilité, basculement et récupération d’urgence FAQ](service-admin-failover.md).

## <a name="security-in-power-bi"></a>Sécurité dans Power BI

### <a name="does-power-bi-meet-national-regional-and-industry-specific-compliance-requirements"></a>Power BI répond-il aux exigences de conformité nationales, régionales et sectorielles ?

Pour plus d’informations sur la conformité Power BI, consultez le [Centre de gestion de la confidentialité Microsoft](https://www.microsoft.com/TrustCenter/CloudServices/business-application-platform/default.aspx).

### <a name="how-does-security-work-in-power-bi"></a>Comment fonctionne la sécurité dans Power BI ?

Microsoft a créé Power BI sur les fondations d’Office 365, qui à son tour s’appuie sur les services Azure comme Azure Active Directory. Pour obtenir une vue d’ensemble de l’architecture de Power BI, consultez [Sécurité de Power BI](service-admin-power-bi-security.md).

## <a name="next-steps"></a>Étapes suivantes

[Portail d’administration Power BI](service-admin-portal.md)  
[Présentation du rôle d’administrateur Power BI](service-admin-role.md)  
[Inscription en libre-service à Power BI](service-self-service-signup-for-power-bi.md)  
[Achat de Power BI Pro](service-admin-purchasing-power-bi-pro.md)  
[Qu’est-ce que Power BI Premium ?](service-premium-what-is.md)  
[Comment acheter Power BI Premium](service-admin-premium-purchase.md)  
[Livre blanc sur Power BI Premium](https://aka.ms/pbipremiumwhitepaper)  
[Gérer votre groupe dans Power BI et Office 365](service-manage-app-workspace-in-power-bi-and-office-365.md)  
[Gestion des comptes utilisateur (Office 365)](/office365/servicedescriptions/office-365-platform-service-description/user-account-management/)  
[Gestion des groupes Office 365](/office365/admin/email/create-edit-or-delete-a-security-group/)  

D’autres questions ? [Essayez d’interroger la communauté Power BI](http://community.powerbi.com/)

[1]: https://docs.microsoft.com/powershell/scripting/overview