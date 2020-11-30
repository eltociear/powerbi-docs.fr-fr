---
title: Points à prendre en considération pour générer un jeton d’incorporation
description: En savoir plus sur les considérations, les limitations et les autorisations requises pour la génération d’un jeton incorporé
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.custom: ''
ms.date: 10/15/2020
ms.openlocfilehash: cea97f16cf06e80b7b16ef7740fcf3103b2f1eb4
ms.sourcegitcommit: 9d033abd9c01a01bba132972497dda428d7d5c12
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95513777"
---
# <a name="considerations-when-generating-an-embed-token"></a>Considérations relatives à la génération d’un jeton incorporé

[Générer un jeton](/rest/api/power-bi/embedtoken) est une API REST qui vous permet de générer un jeton pour incorporer un élément Power BI dans une application web ou un portail. Le jeton est utilisé pour autoriser votre demande sur le service Power BI.

L’API Générer un jeton utilise une identité unique (un utilisateur maître ou un principal du service) pour générer un jeton pour un utilisateur individuel, en fonction des informations d’identification de cet utilisateur dans l’application (identité effective).

Une fois l’authentification réussie, l’accès aux données pertinentes est accordé.

>[!NOTE]
>Générer un jeton s’applique uniquement lorsque vous [*incorporez pour vos clients*](embed-sample-for-customers.md) (scénario aussi appelé *L’application possède les données*).

Vous pouvez utiliser les API suivantes pour générer un jeton :

* [Tableaux de bord](/rest/api/power-bi/embedtoken/dashboards_generatetokeningroup)

* [Groupes de données](/rest/api/power-bi/embedtoken/datasets_generatetokeningroup)

* [Générer un jeton pour plusieurs rapports](/rest/api/power-bi/embedtoken/generatetoken)


* [Création de rapports](/rest/api/power-bi/embedtoken/reports_generatetokenforcreateingroup)

* [Rapports](/rest/api/power-bi/embedtoken/reports_generatetokeningroup)

* [Vignettes](/rest/api/power-bi/embedtoken/tiles_generatetokeningroup)

## <a name="workspace-versions"></a>Versions de l’espace de travail

Power BI propose deux versions de l’espace de travail : un espace de travail *classique* et un *nouvel* espace de travail. Vous pouvez en apprendre davantage sur les différences entre ces espaces de travail dans [Différences entre les espaces de travail nouveaux et classiques](../../collaborate-share/service-new-workspaces.md#new-and-classic-workspace-differences).

Lors de la création d’un jeton incorporé, les différents espaces de travail ont des points différents à prendre en compte et nécessitent des autorisations différentes.

|                  |Espace de travail *classique* |*Nouvel* espace de travail|
|------------------|---------|--------|
|**Considérations**|<li>Le jeu de données et l’élément doivent se trouver dans le même espace de travail</li><li>Le principal du service ne peut pas être utilisé</li>  |Le jeu de données et l’élément peuvent se trouver dans deux *nouveaux* espaces de travail différents |
|**Autorisations d’espace de travail**|L’utilisateur maître doit être un administrateur de l’espace de travail  |Le principal du service ou l’utilisateur maître doit être au moins un membre des deux espaces de travail |

>[!NOTE]
>* Vous ne pouvez pas créer de jeton incorporé pour [Mon espace de travail](../../consumer/end-user-workspaces.md#types-of-workspaces).
>* Le mot *élément* fait référence à un élément de Power BI, comme un tableau de bord, une vignette, Q&A ou un rapport.

## <a name="securing-your-data"></a>Sécurisation de vos données

Lorsque vous créez votre solution, envisagez les deux approches suivantes pour la sécurisation de vos données :

* [Isolation basée sur l’espace de travail](embed-multi-tenancy.md#power-bi-workspace-based-isolation)

* [Isolation basée sur la sécurité au niveau des lignes](embed-multi-tenancy.md#row-level-security-based-isolation)

Si vous envisagez d’utiliser l’approche RLS, passez en revue les [considérations et limitations de RLS](generate-embed-token.md#row-level-security) à la fin de cet article.

## <a name="token-permissions"></a>Autorisations du jeton

Dans les API Générer un jeton, la section *GenerateTokenRequest* décrit les autorisations de jeton.

>[!NOTE]
>Les autorisations de jeton répertoriées dans cette section ne s’appliquent pas à l’API [Générer un jeton pour plusieurs rapports](/rest/api/power-bi/embedtoken/generatetoken).

### <a name="access-level"></a>Niveau d’accès

Utilisez le paramètre *accessLevel* pour déterminer le niveau d’accès de l’utilisateur.

* **Affichage** : accordez à l’utilisateur les autorisations d’affichage.

* **Modification** : accordez à l’utilisateur les autorisations d’affichage et de modification (s’applique uniquement lors de la génération d’un jeton incorporé pour un rapport).

    Si vous utilisez l’API [Générer un jeton pour plusieurs rapports](/rest/api/power-bi/embedtoken/generatetoken), utilisez le paramètre *allowEdit* pour accorder à l’utilisateur l’autorisation d’afficher et de modifier les autorisations.

* **Création** : accordez aux utilisateurs les autorisations nécessaires pour créer un rapport (s’applique uniquement lors de la génération d’un jeton incorporé pour la création d’un rapport).

    Pour la création de rapports, vous devez également fournir le paramètre *datasetId*.

### <a name="saving-a-copy-of-the-report"></a>Enregistrer une copie du rapport

Utilisez le booléen *allowSaveAs* pour permettre aux utilisateurs d’enregistrer le rapport en tant que nouveau rapport. Ce paramètre a la valeur *false* par défaut.

Ce paramètre s’applique uniquement lors de la génération d’un jeton incorporé pour un rapport.

### <a name="row-level-security"></a>Sécurité au niveau des lignes

Avec la [Sécurité au niveau des lignes (RLS)](embedded-row-level-security.md), vous pouvez choisir d’utiliser une identité différente de l’identité du principal du service ou de l’utilisateur maître avec lequel vous générez le jeton. Avec cette option, vous pouvez afficher des informations incorporées en fonction de l’utilisateur que vous ciblez. Par exemple, dans votre application, vous pouvez demander aux utilisateurs de se connecter, puis afficher un rapport contenant uniquement des informations sur les ventes si l’utilisateur connecté est un employé du service commercial.

Si vous utilisez la sécurité au niveau des lignes, vous pouvez, dans certains cas, ignorer l’identité de l’utilisateur (le paramètre *EffectiveIdentity*). Cela permet au jeton d’avoir accès à la totalité de la base de données. Cette méthode peut être utilisée pour accorder l’accès aux utilisateurs, comme les administrateurs et les responsables, qui disposent des autorisations nécessaires pour afficher l’ensemble du jeu de données. Toutefois, vous ne pouvez pas utiliser cette méthode dans tous les scénarios. Le tableau ci-dessous répertorie les différents types de RLS et indique la méthode d’authentification qui peut être utilisée sans spécifier l’identité d’un utilisateur.

Le tableau indique également les considérations et limitations applicables à chaque type de RLS.

|Type de RLS  |Puis-je générer un jeton d’incorporation sans spécifier d’ID d’utilisateur effectif ?  |Observations et limitations  |
|---------|---------|---------|
|Sécurité au niveau des lignes cloud (RLS cloud)      |✔ Utilisateur maître<br/>✖ Principal de service          |         |
|RDL (rapports paginés)     |✖ Utilisateur maître<br/>✔ Principal de service        |Vous ne pouvez pas utiliser un utilisateur maître pour générer un jeton d’incorporation pour RDL.         |
|Analysis Services (AS) sur une connexion active locale    |✔ Utilisateur maître<br/>✖ Principal de service         |L’utilisateur qui génère le jeton incorporé a également besoin de l’une des autorisations suivantes :<li>Autorisations d’administrateur de passerelle</li><li>Autorisation d’emprunt d’identité de source de données (*ReadOverrideEffectiveIdentity*)</li>         |
|Connexion active Azure Analysis Services (AS)    |✔ Utilisateur maître<br/>✖ Principal de service         |L’identité de l’utilisateur qui génère le jeton incorporé ne peut pas être substituée. Les données personnalisées peuvent être utilisées pour implémenter une sécurité RLS dynamique ou un filtrage sécurisé.<br/><br/>**Remarque :** Le principal du service doit fournir son ID d’objet en tant qu’identité effective (nom d'utilisateur RLS).         |
|Authentification unique     |✔ Utilisateur maître<br/>✖ Principal de service         |Une identité explicite (SSO) peut être fournie à l’aide de la propriété d’objet Blob d’identité dans un objet d’identité effective         |
|Authentification unique et RLS cloud     |✔ Utilisateur maître<br/>✖ Principal de service         |Vous devez fournir les éléments suivants :<li>Identité explicite (SSO) dans la propriété d’objet Blob d’identité dans un objet d’identité effective</li><li>Identité effective (RLS) (nom d’utilisateur)</li>         |

>[!NOTE]
>Le principal du service doit toujours fournir les éléments suivants :
>* Identité pour tout élément avec un jeu de données RLS.
>* Pour un jeu de données avec authentification unique, une identité RLS effective avec la propriété UserName définie.

## <a name="next-steps"></a>Étapes suivantes

>[!div class="nextstepaction"]
>[Inscrire une application](register-app.md)

> [!div class="nextstepaction"]
>[Power BI Embedded pour vos clients](embed-sample-for-customers.md)

>[!div class="nextstepaction"]
>[Objets d’application et de principal de service dans Azure Active Directory](/azure/active-directory/develop/app-objects-and-service-principals)

>[!div class="nextstepaction"]
>[Sécurité au niveau des lignes à l’aide d’une passerelle de données locale avec principal de service](embedded-row-level-security.md#on-premises-data-gateway-with-service-principal)

>[!div class="nextstepaction"]
>[Incorporer du contenu Power BI dans un principal de service](embed-service-principal.md)