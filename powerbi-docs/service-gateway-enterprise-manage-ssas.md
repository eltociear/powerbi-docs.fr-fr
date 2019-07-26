---
title: Gérer votre source de données - Analysis Services
description: Gestion de la passerelle de données locale et des sources de données associées. Cela s’applique à Analysis Services en mode multidimensionnel et en mode tabulaire.
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: conceptual
ms.date: 07/15/2019
ms.author: mblythe
LocalizationGroup: Gateways
ms.openlocfilehash: 93475f6476f8baad73229473bd3ce60db68a320b
ms.sourcegitcommit: 277fadf523e2555004f074ec36054bbddec407f8
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/16/2019
ms.locfileid: "68271646"
---
# <a name="manage-your-data-source---analysis-services"></a>Gérer votre source de données - Analysis Services

[!INCLUDE [gateway-rewrite](includes/gateway-rewrite.md)]

Une fois que vous avez [installé la passerelle de données locale](/data-integration/gateway/service-gateway-install), vous devez [ajouter des sources de données](service-gateway-data-sources.md#add-a-data-source) qui peuvent être utilisées avec la passerelle. Cet article examine comment travailler avec des passerelles et des sources de données Analysis Services utilisées pour l’actualisation planifiée ou pour des connexions actives.

Pour plus d’informations sur la configuration d’une connexion active à Analysis Services, [regardez cette vidéo](https://www.youtube.com/watch?v=GPf0YS-Xbyo&feature=youtu.be).

> [!NOTE]
> Si vous avez une source de données Analysis Services, vous devez installer la passerelle sur un ordinateur associé à la même forêt ou au même domaine que votre serveur Analysis Services.

## <a name="add-a-data-source"></a>Ajouter une source de données

Pour plus d’informations sur l’ajout d’une source de données, consultez [Ajouter une source de données](service-gateway-data-sources.md#add-a-data-source). Sélectionnez Analysis Services comme **Type de source de données** si vous vous connectez à un serveur multidimensionnel ou tabulaire.

![Ajouter la source de données Analysis Services](media/service-gateway-enterprise-manage-ssas/datasourcesettings2-ssas.png)

Vous devez ensuite renseigner les informations relatives à la source de données, notamment le **Serveur** et la **Base de données**. La passerelle utilise le **nom d’utilisateur** et le **mot de passe** que vous entrez pour se connecter à l’instance Analysis Services.

> [!NOTE]
> Le compte Windows que vous utilisez doit disposer des autorisations d’administrateur de serveur pour l’instance à laquelle vous vous connectez. Si le mot de passe de ce compte s’accompagne d’une date d’expiration, une erreur de connexion peut survenir si le mot de passe n’a pas été mis à jour pour la source des données. Pour plus d’informations sur la façon dont les informations d’identification sont stockées, consultez [Stockage d’informations d’identification chiffrées dans le cloud](service-gateway-data-sources.md#storing-encrypted-credentials-in-the-cloud).

![Spécification des paramètres de la source de données](media/service-gateway-enterprise-manage-ssas/datasourcesettings3-ssas.png)

Sélectionnez **Ajouter** après avoir renseigné toutes les informations. Vous pouvez à présent utiliser cette source de données pour l’actualisation planifiée ou des connexions actives sur une instance Analysis Services locale. L’indication *Connexion réussie* apparaît une fois la connexion établie.

![Affichage de l’état de la connexion](media/service-gateway-enterprise-manage-ssas/datasourcesettings4.png)

### <a name="advanced-settings"></a>Paramètres avancés

Vous pouvez aussi configurer le niveau de confidentialité de votre source de données. Ceci contrôle la façon dont les données peuvent être combinées. Cette option concerne uniquement l’actualisation planifiée ; elle ne s’applique pas aux connexions actives. Pour plus d’informations sur les niveaux de confidentialité de votre source de données, consultez [Niveaux de confidentialité (Power Query)](https://support.office.com/article/Privacy-levels-Power-Query-CC3EDE4D-359E-4B28-BC72-9BEE7900B540).

![Définition du niveau de confidentialité](media/service-gateway-enterprise-manage-ssas/datasourcesettings9.png)

## <a name="usernames-with-analysis-services"></a>Noms d’utilisateur avec Analysis Services

<iframe width="560" height="315" src="https://www.youtube.com/embed/Qb5EEjkHoLg" frameborder="0" allowfullscreen></iframe>

Chaque fois qu’un utilisateur interagit avec un rapport connecté à Analysis Services, le nom de l’utilisateur effectif est transmis à la passerelle, puis à votre serveur Analysis Services local. L’adresse e-mail utilisée pour vous connecter à Power BI est ce que nous passons à Analysis Services comme utilisateur effectif. Ces informations sont passées dans la propriété de connexion [EffectiveUserName](https://msdn.microsoft.com/library/dn140245.aspx#bkmk_auth). Cette adresse e-mail doit correspondre à un nom d’utilisateur principal défini dans le domaine Active Directory local. L’UPN est une propriété de compte Active Directory. Ce compte Windows doit ensuite se trouver dans un rôle d’Analysis Services. S’il n’existe pas correspondance dans Active Directory, la connexion échoue. Pour plus d’informations Active Directory et le nommage des utilisateurs, consultez [Attributs du nommage des utilisateurs](https://msdn.microsoft.com/library/ms677605.aspx).

Vous pouvez aussi [mapper votre nom de connexion Power BI à un UPN d’un annuaire local](service-gateway-enterprise-manage-ssas.md#mapping-usernames-for-analysis-services-data-sources).

## <a name="mapping-usernames-for-analysis-services-data-sources"></a>Mappage des noms d’utilisateurs pour les sources de données Analysis Services

<iframe width="560" height="315" src="https://www.youtube.com/embed/eATPS-c7YRU" frameborder="0" allowfullscreen></iframe>

Power BI autorise le mappage des noms d’utilisateurs pour les sources de données Analysis Services. Vous pouvez configurer des règles pour mapper un nom d’utilisateur connecté avec Power BI au nom qui a été transmis comme nom d’utilisateur en vigueur sur la connexion Analysis Services. La fonctionnalité de mappage des noms d’utilisateurs est un excellent moyen de contournement quand votre nom d’utilisateur AAD ne correspond pas à un nom d’utilisateur principal (UPN) de votre annuaire Active Directory local. Par exemple, si votre adresse e-mail est nancy@contoso.onmicrsoft.com, vous pouvez la mapper à nancy@contoso.com. Cette valeur est ensuite transmise à la passerelle.

Vous pouvez mapper les noms d’utilisateur Analysis Services de deux manières :

* Remappage manuel des utilisateurs
* Recherche de propriétés Active Directory locale pour remapper les UPN (nom d’utilisateur principal) AAD avec les utilisateurs Active Directory (mappage de recherche AD)

Même s’il est possible d’effectuer un mappage manuel avec la deuxième approche, cette opération serait fastidieuse et difficile à gérer. Elle est particulièrement difficile quand la mise en correspondance du modèle ne suffit pas, par exemple quand les noms de domaine sont différents entre AAD et AD local, ou quand les noms de compte d’utilisateur sont différents entre AAD et AD. Par conséquent, le mappage manuel avec la deuxième approche n’est pas recommandé.

Nous décrivons ces deux approches dans l’ordre, dans les deux sections suivantes.

### <a name="manual-user-name-re-mapping"></a>Remappage manuel des noms d’utilisateur

Pour les sources de données Analysis Services, vous pouvez configurer des règles UPN (nom d’utilisateur principal) personnalisées. Cela vous aidera si vos noms de connexion au service Power BI ne correspondent pas à votre UPN de répertoire local. Par exemple, si vous vous connectez à Power BI avec john@contoso.com, mais que votre UPN de répertoire local est john@contoso.local, vous pouvez configurer une règle de mappage pour que john@contoso.local soit transmis à Analysis Services.

Pour accéder à l’écran de mappage de nom UPN, procédez comme suit.

1. Accédez à l’**icône Engrenage**, puis sélectionnez **Gérer les passerelles**.
2. Développez la passerelle qui contient la source de données Analysis Services. Ou, si vous n’avez pas créé la source de données Analysis Services, vous pouvez aussi le faire à ce stade.
3. Sélectionnez la source de données, puis sélectionnez l’onglet **Utilisateurs**.
4. Sélectionnez **Mapper les noms d’utilisateur**.

    ![Écran de mappage des UPN](media/service-gateway-enterprise-manage-ssas/gateway-enterprise-map-user-names_02.png)

Vous verrez alors des options permettant d’ajouter des règles ainsi que d’effectuer un test pour un utilisateur donné.

> [!NOTE]
> Vous pouvez modifier par inadvertance un utilisateur alors que vous ne le vouliez pas. Par exemple, si votre valeur **Remplacer (Nom d’origine)** est <em>@contoso.com</em> et que votre valeur **Avec (Nouveau nom)** est <em>@contoso.local</em>, tous les utilisateurs disposant d’une connexion qui contient <em>@contoso.com</em> sont alors remplacés par <em>@contoso.local</em>. De plus, si votre valeur **Remplacer (Nom d’origine)** est <em>dave@contoso.com</em> et que votre valeur **Avec (Nouveau nom)** est <em>dave@contoso.local</em>, un utilisateur disposant d’une connexion v-dave@contoso.com serait envoyé en tant que v-dave<em>@contoso.local</em>.

### <a name="ad-lookup-mapping"></a>Mappage de recherche AD

Pour effectuer la recherche de propriétés Active Directory en local afin de remapper les UPN AAD avec les utilisateurs Active Directory, suivez les étapes de cette section. Pour commencer, voyons comment cela fonctionne.

Dans le **service Power BI**, voici ce qui se passe :

* Pour chaque requête effectuée par un utilisateur AAD Power BI à un serveur SSAS local, une chaîne d’UPN est transmise au format suivant :      firstName.lastName@contoso.com

> [!NOTE]
> Les mappages manuels d’utilisateurs UPN définis dans la configuration de la source de données Power BI sont toujours appliqués *avant* l’envoi de la chaîne de nom d’utilisateur à la passerelle de données locale.

Sur la passerelle de données locale avec le mappage d’utilisateur personnalisé configurable défini, procédez comme suit :

1. Identifiez l’annuaire Active Directory où effectuer la recherche (automatique ou configurable).
2. Recherchez l’attribut de la personne AD (tel que le *courrier électronique*) en fonction d’une chaîne UPN entrante (« firstName.lastName@contoso.com ») à partir du **service Power BI**.
3. Si la recherche AD échoue, elle tente d’utiliser l’UPN transmis en tant qu’utilisateur effectif à SSAS.
4. Si la recherche AD réussit, elle récupère le nom d’utilisateur principal (*UserPrincipalName*) de cette personne AD.
5. Elle passe l’e-mail de *UserPrincipalName* en tant que *EffectiveUser* à SSAS sous la forme <em>Alias@corp.on-prem.contoso</em>.

Pour configurer votre passerelle pour qu’elle effectue la recherche AD :

1. [Téléchargez et installez la passerelle la plus récente](/data-integration/gateway/service-gateway-install).

2. Dans la passerelle, vous devez modifier le **service de passerelle de données locale** pour qu’il s’exécute avec un compte de domaine (au lieu d’un compte de service local, sinon la recherche AD ne fonctionne pas correctement lors de l’exécution). Accédez à l’[application de passerelle de données locale](/data-integration/gateway/service-gateway-app) sur votre machine, puis accédez à **Paramètres du service > Modifier le compte de service**. Vérifiez que vous disposez de la clé de récupération pour cette passerelle, car vous devrez la restaurer sur le même ordinateur, sauf si vous souhaitez créer une passerelle à la place. Vous devez redémarrer le service de passerelle pour que les modifications entrent en vigueur.

3. Accédez au dossier d’installation de la passerelle *C:\Program Files\On-premises data gateway* en tant qu’administrateur pour vérifier que vous disposez des autorisations d’écriture, puis ouvrez le fichier *Microsoft.PowerBI.DataMovement.Pipeline.GatewayCore.dll.config*.

4. Modifiez les deux valeurs de configuration suivantes en fonction de *vos* configurations d’attributs Active Directory de vos utilisateurs AD. Les valeurs de configuration illustrées ci-dessous sont des exemples uniquement : vous devez les spécifier en fonction de votre configuration Active Directory. Ces configurations sont sensibles à la casse : veillez donc à ce qu’elles correspondent aux valeurs spécifiées dans Active Directory.

    ![Paramètres Azure Active Directory](media/service-gateway-enterprise-manage-ssas/gateway-enterprise-map-user-names_03.png)

    Si aucune valeur n’est fournie pour la configuration ADServerPath, la passerelle utilise le catalogue global par défaut. Vous pouvez également spécifier plusieurs valeurs pour ADServerPath. Chaque valeur doit être séparée par un point-virgule, comme dans l’exemple suivant.

    ```xml
    <setting name="ADServerPath" serializeAs="String">
        <value> >GC://serverpath1; GC://serverpath2;GC://serverpath3</value>
    </setting>
    ```

    La passerelle analyse les valeurs spécifiées pour ADServerPath de gauche à droite jusqu'à ce qu’elle trouve une correspondance. Si aucune correspondance n’est trouvée, l’UPN d’origine est utilisé. Assurez-vous que le compte exécutant le service de passerelle (PBIEgwService) dispose des autorisations de requête pour tous les serveurs Active Directory que vous spécifiez dans ADServerPath.

    La passerelle prend en charge deux types de chemin ADServerPath, comme dans les exemples suivants.

    **WinNT**

    ```xml
    <value="WinNT://usa.domain.corp.contoso.com,computer"/>
    ```

    **GC**

    ```xml
    <value> GC://USA.domain.com </value>
    ```

5. Redémarrez le service **Passerelle de données locale** pour que les modifications de configuration entrent en vigueur.

### <a name="working-with-mapping-rules"></a>Utilisation des règles de mappage

Pour créer une règle de mappage, entrez une valeur pour **Nom d’origine** et pour **Nouveau nom**, puis sélectionnez **Ajouter**.

| Champ | Description |
| --- | --- |
| Remplacer (nom d’origine) |Adresse e-mail avec laquelle que vous vous êtes connecté à Power BI. |
| Par (nouveau nom) |Valeur par laquelle vous voulez la remplacer. Le résultat du remplacement est ce qui sera passé à la propriété *EffectiveUserName* pour la connexion Analysis Services. |

![Création d’une règle de mappage](media/service-gateway-enterprise-manage-ssas/gateway-enterprise-map-user-names-effective-user-names.png)

Quand vous sélectionnez un élément dans la liste, vous pouvez choisir de modifier son ordre à l’aide des **icônes représentant des chevrons**, ou de **Supprimer** l’entrée.

![Réorganisation d’un élément dans la liste](media/service-gateway-enterprise-manage-ssas/gateway-enterprise-map-user-names-entry-selected.png)

### <a name="using-wildcard-"></a>Utilisation de caractères génériques (\*)

Vous pouvez utiliser un caractère générique pour votre chaîne **Remplacer (nom d’origine)** . Il peut être utilisé seul uniquement, et non avec une autre partie de la chaîne. Cela vous permet de prendre tous les utilisateurs et de transmettre une valeur unique à la source de données. Cela est utile lorsque vous souhaitez que tous les utilisateurs de votre organisation utilisent le même utilisateur dans votre environnement local.

### <a name="test-a-mapping-rule"></a>Tester une règle de mappage

Vous pouvez valider ce par quoi un nom d’origine sera remplacé en entrant une valeur pour **Nom d’origine**, puis en sélectionnant **Tester la règle**.

![Test d’une règle de mappage](media/service-gateway-enterprise-manage-ssas/gateway-enterprise-test-mapping-rule.png)

> [!NOTE]
> Quelques minutes sont nécessaires avant que les règles enregistrées commencent à être utilisées par le service. Dans le navigateur, la règle fonctionne immédiatement.

### <a name="limitations-for-mapping-rules"></a>Limitations relatives aux règles de mappage

Le mappage s’applique à la source de données spécifique en cours de configuration. Il ne s’agit pas de paramètres globaux. Si vous avez plusieurs sources de données Analysis Services, vous devez mapper les utilisateurs pour chaque source de données.

## <a name="authentication-to-a-live-analysis-services-data-source"></a>Authentification auprès d’une source de données Analysis Services active

Chaque fois qu’un utilisateur interagit avec Analysis Services, le nom de l’utilisateur en vigueur est transmis à la passerelle, puis à votre serveur Analysis Services local. Le nom d’utilisateur principal (UPN), qui est généralement l’adresse e-mail utilisée pour la connexion au cloud, est celui que nous passons à Analysis Services en tant qu’utilisateur effectif. Le nom d’utilisateur principal est transmis dans la propriété de connexion EffectiveUserName. Cette adresse de messagerie doit correspondre à un nom d’utilisateur principal défini dans le domaine Active Directory local. L’UPN est une propriété de compte Active Directory. Pour avoir accès au serveur, ce compte Windows doit se trouver dans un rôle Analysis Services. La connexion échoue s’il n’existe aucune correspondance dans Active Directory.

Analysis Services peut également fournir un filtrage basé sur ce compte. Le filtrage peut se produire avec la sécurité basée sur les rôles ou au niveau des lignes.

## <a name="role-based-security"></a>Sécurité basée sur les rôles

Les modèles fournissent une solution de sécurité basée sur les rôles d’utilisateur. Les rôles sont définis pour un projet de modèle spécifique pendant la procédure de création dans SQL Server Data Tools - Business Intelligence (SSDT-BI) ou après le déploiement d’un modèle, à l’aide de SQL Server Management Studio (SSMS). Les rôles contiennent des membres définis par leurs noms d’utilisateur Windows ou par leur groupe Windows. Les rôles définissent les autorisations dont dispose un utilisateur pour interroger le modèle ou effectuer des actions sur ce dernier. La plupart des utilisateurs appartiennent à un rôle doté d’autorisations de lecture. Les autres rôles sont destinés aux administrateurs qui possèdent des autorisations pour traiter les éléments, gérer les fonctions de base de données et gérer les autres rôles.

## <a name="row-level-security"></a>Sécurité au niveau des lignes

La sécurité au niveau des lignes est propre à Analysis Services. Les modèles peuvent proposer une solution de sécurité dynamique au niveau des lignes. Contrairement au cas où les utilisateurs appartiennent à au moins un rôle, la sécurité dynamique est inutile pour tout modèle tabulaire. À un haut niveau, la sécurité dynamique définit l’accès en lecture d’un utilisateur à des données directement au niveau d’une ligne particulière dans une table donnée. Similaire aux rôles, la sécurité dynamique au niveau des lignes s’appuie sur le nom d’utilisateur Windows d’un utilisateur.

L’aptitude d’un utilisateur à interroger et à afficher les données de modèle est déterminée en premier lieu par les rôles dont son compte utilisateur Windows est membre et en second lieu par la sécurité dynamique au niveau des lignes, si elle est configurée.

La mise en œuvre d’une sécurité basée sur les rôles et dynamique au niveau des lignes dans les modèles dépasse le cadre de cet article. Pour en savoir plus, consultez les rubriques [Rôles (SSAS Tabulaire)](https://msdn.microsoft.com/library/hh213165.aspx) et [Rôles de sécurité (Analysis Services - Données multidimensionnelles)](https://msdn.microsoft.com/library/ms174840.aspx) sur MSDN. De plus, pour approfondir au maximum votre compréhension de la sécurité des modèles tabulaires, téléchargez et lisez le livre blanc [Securing the Tabular BI Semantic Model](https://msdn.microsoft.com/library/jj127437.aspx).

## <a name="what-about-azure-active-directory"></a>Qu’en est-il d’Azure Active Directory ?

Les services cloud Microsoft utilisent [Azure Active Directory](/azure/active-directory/fundamentals/active-directory-whatis) pour prendre en charge l’authentification des utilisateurs. Azure Active Directory est le locataire qui contient les groupes de sécurité et les noms d’utilisateur. En règle générale, un utilisateur se connecte avec l’adresse de messagerie qui correspond au nom d’utilisateur principal du compte.

Qu’est-ce qu’un rôle Active Directory local ?

Pour qu’Analysis Services puisse déterminer si un utilisateur se connectant à ce dernier appartient à un rôle doté d’autorisations de lecture des données, le serveur doit convertir le nom d’utilisateur en vigueur transmis depuis AAD à la passerelle, puis au serveur Analysis Services. Le serveur Analysis Services passe le nom d’utilisateur en vigueur à un contrôleur de domaine Active Directory. Ensuite, le contrôleur de domaine Active Directory confirme que le nom d’utilisateur en vigueur correspond à un UPN valide sur un compte local et renvoie le nom d’utilisateur Windows de cet utilisateur au serveur Analysis Services.

Le nom d’utilisateur en vigueur ne peut pas être utilisé sur un serveur Analysis Services non joint au domaine. Le serveur Analysis Services doit être joint à un domaine pour éviter les erreurs de connexion.

### <a name="how-do-i-tell-what-my-upn-is"></a>Comment savoir quel est mon UPN ?

Vous ne savez pas peut-être pas quel est votre UPN, et vous n’êtes peut-être pas un administrateur de domaine. Vous pouvez utiliser la commande suivante à partir de votre station de travail pour connaître l’UPN de votre compte.

    whoami /upn

Le résultat est similaire à une adresse e-mail, mais il s’agit en fait de l’UPN qui se trouve sur votre compte de domaine. Si vous utilisez une source de données Analysis Services pour des connexions actives, et si cela ne correspond pas à l’adresse e-mail avec laquelle vous vous connectez à Power BI, il peut être utile de regarder comment [mapper des noms d’utilisateur](#mapping-usernames-for-analysis-services-data-sources).

## <a name="synchronize-an-on-premises-active-directory-with-azure-active-directory"></a>Synchroniser un service Active Directory local avec Azure Active Directory

Si vous souhaitez utiliser des connexions actives Analysis Services, vous voulez que vos comptes Active Directory locaux correspondent à Azure Active Directory. De même, l’UPN doit être identique pour tous les comptes.

Les services cloud reconnaissent uniquement les comptes dans Azure Active Directory. Même si vous avez ajouté un compte dans votre annuaire Active Directory local, s’il n’existe pas dans AAD, il ne peut pas être utilisé. Il existe différentes méthodes pour faire correspondre vos comptes Active Directory locaux avec Azure Active Directory.

1. Vous pouvez ajouter manuellement des comptes à Azure Active Directory.

   Vous pouvez créer un compte sur le portail Azure ou dans le centre d’administration Microsoft 365. Le nom du compte correspond alors au nom d’utilisateur principal du compte Active Directory local.

2. Vous pouvez utiliser l’outil [Azure AD Connect](/azure/active-directory/hybrid/how-to-connect-sync-whatis) pour synchroniser les comptes locaux avec votre locataire Azure Active Directory.

   L’outil Azure AD Connect offre des options de synchronisation des répertoires et de configuration de l’authentification, y compris la synchronisation du hachage de mot de passe, l’authentification directe et la fédération. Si vous n’êtes pas administrateur de locataire ou administrateur de domaine local, vous devez contacter votre administrateur informatique pour qu’il se charge de la configuration.

L’utilisation d’Azure AD Connect permet de vérifier que les UPN d’AAD et de votre annuaire Active Directory local correspondent.

> [!NOTE]
> La synchronisation des comptes avec l’outil Azure AD Connect crée des comptes au sein de votre client AAD.

## <a name="using-the-data-source"></a>Utilisation de la source de données

Une fois la source de données créée, elle peut être utilisée avec des connexions actives ou via une actualisation planifiée.

> [!NOTE]
> Le nom du serveur et celui de la base de données doivent correspondre entre Power BI Desktop et la source de données dans la passerelle de données locale.

Le lien entre votre jeu de données et la source de données dans la passerelle est basé sur le nom de votre serveur et sur le nom de votre base de données. Ils doivent correspondre. Par exemple, si vous fournissez une adresse IP pour le nom du serveur, dans Power BI Desktop, vous devez utiliser l’adresse IP de la source de données dans la configuration de la passerelle. Si vous utilisez *SERVEUR\INSTANCE*, dans Power BI Desktop, vous devez utiliser la même valeur dans la source de données configurée pour la passerelle.

C’est le cas pour les connexions actives et pour l’actualisation planifiée.

### <a name="using-the-data-source-with-live-connections"></a>Utilisation de la source de données avec des connexions actives

Vous devez vérifier que le nom du serveur et celui de la base de données correspondent entre Power BI Desktop et la source de données configurée pour la passerelle. Vous devez également vérifier que votre utilisateur est listé sous l’onglet **Utilisateurs** de la source de données pour pouvoir publier des jeux de données de connexion active. Pour les connexions actives, la sélection se produit dans Power BI Desktop la première fois que vous importez des données.

Une fois la publication effectuée, que ce soit à partir de Power BI Desktop ou de l’option **Obtenir les données**, vos rapports doivent commencer à fonctionner. Après la création de la source de données dans la passerelle, plusieurs minutes peuvent être nécessaires pour que la connexion puisse être utilisée.

### <a name="using-the-data-source-with-scheduled-refresh"></a>Utilisation de la source de données avec une actualisation planifiée

Si vous êtes listé sous l’onglet **Utilisateurs** de la source de données configurée dans la passerelle, et que le nom du serveur et celui de la base de données correspondent, la passerelle s’affiche comme option à utiliser avec l’actualisation planifiée.

![Affichage des utilisateurs](media/service-gateway-enterprise-manage-ssas/powerbi-gateway-enterprise-schedule-refresh.png)

### <a name="limitations-of-analysis-services-live-connections"></a>Limitations des connexions actives Analysis Services

Vous pouvez utiliser une connexion active à des instances tabulaires ou multidimensionnelles.

| **Version du serveur** | **Référence (SKU) requise** |
| --- | --- |
| 2012 SP1 CU4 ou version ultérieure |Business Intelligence et Enterprise |
| 2014 |Business Intelligence et Enterprise |
| 2016 |Référence (SKU) standard ou version ultérieure |

* Les fonctionnalités de mise en forme au niveau de la cellule et les fonctions de traduction ne sont pas prises en charge.
* Actions et jeux nommés ne sont pas exposés à Power BI, mais vous pouvez toujours vous connecter à des cubes multidimensionnels qui contiennent également les propriétés Actions ou Jeux nommés et créer des rapports et des éléments visuels.

## <a name="next-steps"></a>Étapes suivantes

* [Résolution des problèmes de passerelle de données locale](/data-integration/gateway/service-gateway-tshoot)
* [Résoudre les problèmes liés aux passerelles - Power BI](service-gateway-onprem-tshoot.md)

D’autres questions ? [Posez vos questions à la communauté Power BI](http://community.powerbi.com/)

