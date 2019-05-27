---
title: Distribuer le contenu Power BI à des utilisateurs invités externes à l’aide d’Azure Active Directory B2B
description: Livre blanc qui explique comment utiliser Azure Active Directory B2B à distribuer Power BI aux utilisateurs invités externes
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 03/07/2019
ms.author: davidi
LocalizationGroup: Conceptual
ms.openlocfilehash: 79b8ae80413cc54b065d12bf36ccb1651a670812
ms.sourcegitcommit: ec5b6a9f87bc098a85c0f4607ca7f6e2287df1f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/23/2019
ms.locfileid: "66051597"
---
# <a name="distribute-power-bi-content-to-external-guest-users-using-azure-active-directory-b2b"></a>Distribuer le contenu Power BI à des utilisateurs invités externes à l’aide d’Azure Active Directory B2B

**Résumé :** Il s’agit d’un livre blanc technique, le mode plan de la distribution de contenu aux utilisateurs en dehors de l’organisation à l’aide de l’intégration d’Azure Active Directory Business-to-business (Azure AD B2B).

**Auteurs :** Lukasz Pawlowski, Kasper de Jonge

**Réviseurs techniques :** ADAM Wilson, Sheng Liu, Qian Liang, Sergei Gundorov, Jacob Grimm, Adam Saxton, Shenhav Maya, Nimrod Shalit, Elisabeth Olson

> [!NOTE]
> Vous pouvez enregistrer ou imprimer ce livre blanc en sélectionnant **Imprimer** dans votre navigateur, puis **Enregistrer au format PDF**.

## <a name="introduction"></a>Introduction

Power BI offre aux organisations une vue à 360 degrés de leur entreprise et met à votre disposition tous les membres de ces organisations à prendre des décisions intelligentes à l’aide de données. La plupart de ces organisations ont fortes et approuvées les relations avec des partenaires externes, les clients et les sous-traitants. Ces organisations doivent fournir un accès sécurisé aux tableaux de bord Power BI et des rapports pour les utilisateurs de ces partenaires externes.

Power BI s’intègre à [Azure Active Directory Business-to-business (Azure AD B2B)](https://docs.microsoft.com/azure/active-directory/b2b/what-is-b2b) pour permettre une distribution sécurisée de Power BI contenu aux utilisateurs invités extérieurs à l’organisation, bien que toujours conserver le contrôle et qui régissent l’accès aux données internes.

Ce livre blanc couvre les toutes les informations que nécessaires pour comprendre l’intégration de Power BI avec Azure Active Directory B2B. Nous abordons ses cas d’usage plus courant, le programme d’installation, Gestionnaire de licences et la sécurité au niveau ligne.

> [!NOTE]
> Dans ce livre blanc, nous faisons référence à Azure Active Directory en tant qu’Azure AD et Azure Active Directory B2b en tant qu’Azure AD B2B.

## <a name="scenarios"></a>Scénarios

Contoso est un fabricant automobile et fonctionne avec de nombreux fournisseurs différents qui lui fournit tous les composants, les supports et les services nécessaires pour exécuter ses opérations de fabrication. Contoso souhaite simplifier sa chaîne logistique et les plans pour utiliser Power BI pour surveiller les mesures de performances clés de sa chaîne logistique. Contoso souhaite partager avec analytique de partenaires de chaîne logistique externes de manière sécurisée et facile à gérer.

Contoso peut activer les expériences suivantes pour les utilisateurs externes à l’aide de Power BI et Azure AD B2B.

### <a name="ad-hoc-per-item-sharing"></a>Ponctuel par le partage d’éléments

Contoso fonctionne avec un fournisseur qui s’appuie radiateurs pour les voitures de Contoso. Souvent, ils doivent optimiser la fiabilité des radiateurs à l’aide de données à partir de toutes les voitures de Contoso. Un analyste chez Contoso utilise Power BI pour partager un rapport de fiabilité radiateur avec un ingénieur principal chez le fournisseur. L’ingénieur reçoit un e-mail contenant un lien pour afficher le rapport.

Comme décrit ci-dessus, ce partage ad hoc est effectué par les utilisateurs en fonction des besoins métier. Le lien envoyé par Power BI à l’utilisateur externe est un lien d’invitation Azure AD B2B. Lorsque l’utilisateur externe s’ouvre le lien, ils sont invités à rejoindre l’organisation d’Azure AD de Contoso en tant qu’un utilisateur invité. Une fois l’invitation acceptée, le lien ouvre le rapport spécifique ou un tableau de bord. L’administrateur Azure Active Directory délègue autorisé à inviter des utilisateurs externes à l’organisation et choisit ce que ces utilisateurs peuvent faire une fois qu’ils acceptent l’invitation, comme décrit dans la section de gouvernance de ce document. L’analyste de Contoso peut inviter l’utilisateur invité uniquement parce que l’administrateur Azure AD autorisé cette action et Power BI administrateur les utilisateurs autorisé à inviter des invités pour afficher le contenu dans les paramètres du client de Power BI.

![Inviter des invités à Power BI à l’aide d’AAD](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_01.png)

1. Le processus commence par un utilisateur interne Contoso partager un tableau de bord ou un rapport avec un utilisateur externe. Si l’utilisateur externe n’est pas déjà un invité dans Azure de Contoso AD, ils sont invités. Un e-mail est envoyé à une adresse e-mail qui inclut une invitation à Azure de Contoso AD
2. Le destinataire accepte l’invitation à Contoso d’Azure AD et est ajoutée en tant qu’un utilisateur invité dans Azure de Contoso AD.
3. Le destinataire est ensuite redirigé vers l’application, qui sont en lecture seule pour l’utilisateur, rapport ou tableau de bord Power BI.

Le processus est considéré comme ad hoc dans la mesure où les utilisateurs professionnels dans Contoso effectuer l’action de l’invitation en fonction des besoins pour leurs besoins professionnels. Chaque élément partagé est un lien unique, l’utilisateur externe peut accéder pour afficher le contenu.

Une fois que l’utilisateur externe a été invité à accéder aux ressources de Contoso, un compte de clichés instantanés peut-être être créé pour eux dans Azure AD de Contoso, et ils n’êtes pas obligé d’être invité à nouveau.  La première fois qu’ils tentent d’accéder à une ressource de Contoso comme un tableau de bord Power BI, elles passent par un processus de consentement, ce qui a utilisé l’invitation.  Si elles ne s’achèvent pas le consentement, ils ne peut pas accéder à n’importe quel contenu de Contoso.  S’ils ont des difficultés à utiliser leur invitation via le lien d’origine fourni, un administrateur Azure AD peut renvoyer un lien d’invitation spécifique pour qu’ils puissent échanger.

### <a name="planned-per-item-sharing"></a>Planifié par le partage d’éléments

Contoso fonctionne avec un sous-traitant pour effectuer une analyse de fiabilité de radiateurs. Le sous-traitant dispose d’une équipe de 10 personnes qui ont besoin d’accéder aux données dans l’environnement de Contoso Power BI. L’administrateur de Contoso Azure AD est impliqué pour inviter tous les utilisateurs et pour gérer les ajouts/modifications comme personnel lors de la modification de sous-traitants. L’administrateur Azure AD crée un groupe de sécurité pour tous les employés à la sous-traitance. À l’aide du groupe de sécurité, les employés de Contoso peuvent facilement gérer l’accès aux rapports et vérifiez tout le personnel sous-traitant requis ont accès à tous les rapports demandés, les tableaux de bord et les applications Power BI. L’administrateur Azure AD peut également éviter d’être impliqué dans le processus d’invitation complètement en choisissant de déléguer des droits d’invitation à un employé de confiance chez Contoso, ou à un sous-traitant pour vous assurer du personnel en temps voulu gestion.

Certaines organisations nécessitent davantage de contrôle sur quand les utilisateurs externes sont ajoutés, invitez nombre d’utilisateurs dans une organisation externe ou de nombreuses organisations externes. Dans ce cas, partage planifié peut servir à gérer la mise à l’échelle de partage, d’appliquer des stratégies d’organisation et même de déléguer des droits aux personnes de confiance d’inviter et gérer des utilisateurs externes. Azure AD B2B prend en charge les invitations planifiées pour être envoyés directement [à partir du portail Azure par un administrateur informatique](https://docs.microsoft.com/azure/active-directory/b2b/add-users-administrator), ou via [PowerShell à l’aide de l’API du Gestionnaire d’invitation](https://docs.microsoft.com/azure/active-directory/b2b/customize-invitation-api) où un ensemble d’utilisateurs peut être invité dans un action. À l’aide de la planifié invite approche, l’organisation peut contrôler qui peut inviter des utilisateurs et implémenter des processus d’approbation. Azure AD de capacités avancées comme des groupes dynamiques peuvent rendre facile à gérer l’appartenance au groupe de sécurité automatiquement.


![Contrôle quels invités peuvent consulter le contenu](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_02.png)



1. Les étoiles de processus avec un administrateur informatique peut inviter l’utilisateur invité manuellement ou via l’API fournie par Azure Active Directory
2. L’utilisateur accepte l’invitation à l’organisation.
3. Une fois que l’utilisateur a accepté l’invitation, un utilisateur dans Power BI peut partager un rapport ou un tableau de bord avec l’utilisateur externe, ou ils se trouvent dans un groupe de sécurité. Comme avec le partage régulière dans Power BI, l’utilisateur externe reçoit un e-mail contenant le lien vers l’élément.
4. Lorsque les accès utilisateur externe le lien, leur authentification dans leur annuaire est passé à Contoso d’Azure AD et utilisé pour accéder au contenu Power BI.

### <a name="ad-hoc-or-planned-sharing-of-power-bi-apps"></a>Ad hoc ou planifiée partage des applications Power BI

Contoso possède un ensemble de rapports et tableaux de bord que dont ils ont besoin de partager avec un ou plusieurs fournisseurs. Pour garantir que tous les utilisateurs externes requis ont accès à ce contenu, il est fourni comme une application Power BI. Les utilisateurs externes sont ajoutés soit directement à la liste d’accès aux applications ou par le biais des groupes de sécurité. Quelqu'un chez Contoso envoie ensuite l’URL de l’application à tous les utilisateurs externes, par exemple dans un message électronique. Quand les utilisateurs externes d’ouvrir le lien, ils voient tout le contenu dans un seul facile à parcourir l’expérience.

À l’aide d’une application Power BI rend plus facile pour que Contoso puisse créer un portail BI pour ses fournisseurs. Une liste d’accès unique contrôle l’accès à tout le contenu requis en réduisant le temps perdu la vérification et définition des autorisations au niveau élément. Azure AD B2B gère la sécurité d’accès à l’aide d’identité native du fournisseur pour les utilisateurs n’aient des informations d’identification de connexion supplémentaires. Si à l’aide de planifié invite avec des groupes de sécurité, gestion de l’accès à l’application lorsque le personnel tournez vers ou à partir du projet est simplifiée. L’appartenance à la sécurité des groupes manuellement ou à l’aide de [groupes dynamiques](https://docs.microsoft.com/azure/active-directory/b2b/use-dynamic-groups), de sorte que tous les utilisateurs externes à partir d’un fournisseur sont automatiquement ajoutés au groupe de sécurité approprié.


![Contrôle de contenu avec AAD](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_03.png)

1. Le processus commence par l’utilisateur invité à l’organisation d’Azure AD de Contoso par le biais du portail Azure ou de PowerShell
2. L’utilisateur peut être ajouté à un groupe d’utilisateurs dans Azure AD. Un groupe d’utilisateurs statique ou dynamique peut être utilisé, mais des groupes dynamiques vous aider à réduire le travail manuel.
3. Les utilisateurs externes obtiennent un accès à l’application Power BI via le groupe d’utilisateurs. L’application URL doit être envoyée directement à l’utilisateur externe ou placée sur un site, ils ont accès. Power BI vous permet de mieux pour envoyer un e-mail avec le lien de l’application aux utilisateurs externes, mais lorsque vous utilisez des groupes d’utilisateurs dont les membres peuvent changer, Power BI n’est pas en mesure d’envoyer à tous les utilisateurs externes gérées via des groupes d’utilisateurs.
4. Lorsque l’utilisateur externe accède à l’URL de l’application Power BI, ils sont authentifiés par Contoso Azure AD, l’application est installée pour l’utilisateur, et l’utilisateur peut voir tous les rapports de relation contenant-contenus et des tableaux de bord au sein de l’application.

Les applications ont également une fonctionnalité unique qui permet aux auteurs d’application installer l’application automatiquement pour l’utilisateur, elle est disponible lorsque l’utilisateur se connecte. Cette fonctionnalité installe uniquement automatiquement pour les utilisateurs externes qui font déjà partie d’une organisation de Contoso au moment de l’application est publiée ou mis à jour. Par conséquent, il est préférable d’utiliser l’approche de l’invitation planifiée et dépend de l’application en cours publiés ou mis à jour une fois que les utilisateurs sont ajoutés à Azure de Contoso AD. Les utilisateurs externes peuvent toujours installer l’application en utilisant le lien de l’application.

### <a name="commenting-and-subscribing-to-content-across-organizations"></a>Ajout de commentaires et d’abonnement au contenu entre plusieurs organisations

Comme Contoso continue de fonctionner avec ses sous-traitants ou les fournisseurs, les ingénieurs externes doivent travailler en étroite collaboration avec les analystes de Contoso. Power BI fournit plusieurs fonctionnalités de collaboration qui permettent aux utilisateurs de communiquer sur le contenu, qu'ils peuvent consommer. Commentaire du tableau de bord (et bientôt créer des rapports de commentaires) permet aux utilisateurs de discuter des points de données, ils voient et communiquent avec les auteurs de rapports pour poser des questions.

Actuellement, les utilisateurs invités externes peuvent participer de commentaires en laisser des commentaires et en lisant les réponses. Toutefois, contrairement aux utilisateurs internes, les utilisateurs invités ne peut pas être @mentioned et ne reçoivent pas de notifications qu’ils ont reçu un commentaire. Les utilisateurs invités ne pouvez pas utiliser la fonctionnalité d’abonnements au sein de Power BI au moment de l’écriture. Dans une prochaine version, ces restrictions seront levées et l’utilisateur invité reçoit un e-mail quand un commentaire @mentions , ou quand un abonnement est remis à sa messagerie qui contient un lien vers le contenu dans Power BI.

### <a name="access-content-in-the-power-bi-mobile-apps"></a>Accéder au contenu dans les applications mobiles Power BI

Dans une prochaine version, lorsque les utilisateurs de Contoso partagent des rapports ou tableaux de bord avec leurs homologues invité externes, Power BI envoie un e-mail de notification de l’invité. Lorsque l’utilisateur invité s’ouvre le lien vers le rapport ou le tableau de bord sur leur appareil mobile, le contenu s’ouvre dans les applications mobiles Power BI natives sur leur appareil, s’ils sont installés. L’utilisateur invité sera ensuite en mesure de naviguer entre le contenu partagé avec eux dans le locataire externe et à leur propre contenu à partir de leur client de base.

> [!NOTE]
> L’utilisateur invité ne peut pas ouvrir l’application mobile Power BI et accédez immédiatement au client externe, ils doivent commencer par un lien vers un élément dans le client externe. Solutions de contournement courants sont décrits dans le [distribution liens vers du contenu dans Power BI l’organisation parente](#distributing-links-to-content-in-the-parent-organizations-power-bi) section plus loin dans ce document.

### <a name="cross-organization-editing-and-management-of-power-bi-content"></a>Modification entre les organisations et la gestion de contenu Power BI

Contoso et ses fournisseurs et les sous-traitants de travaillent plus en plus étroitement ensemble. Un analyste sous-traitant doit souvent des visualisations de mesures ou des données supplémentaires à ajouter à un rapport, que Contoso a partagé avec eux. Les données doivent résider dans le locataire de Power BI de Contoso, mais les utilisateurs externes doivent être en mesure de le modifier, créer du contenu et même les distribuer aux personnes appropriées.

Power BI fournit une option qui permet de **des utilisateurs invités externes peuvent modifier et gérer le contenu** dans l’organisation. Par défaut, les utilisateurs externes ont une expérience orientée sur la consommation en lecture seule. Toutefois, ce nouveau paramètre permet à l’administrateur de Power BI choisir les utilisateurs externes peuvent modifier et gérer les contenus dans leur propre organisation. Une fois autorisés, l’utilisateur externe peut modifier des rapports, des tableaux de bord, publier ou mettre à jour les applications fonctionnent dans les espaces de travail et se connecter aux données qu’ils sont autorisés à utiliser.

Ce scénario est décrit en détail dans les section Activation externe d’utilisateurs pour modifier et gérer le contenu au sein de Power BI plus loin dans ce document.

## <a name="organizational-relationships-using-power-bi-and-azure-ad-b2b"></a>Relations organisationnelles à l’aide de Power BI et Azure AD B2B

Lorsque tous les utilisateurs de Power BI sont internes à l’organisation, il est inutile d’utiliser Azure AD B2B. Toutefois, une fois que deux ou plusieurs organisations veulent collaborer sur les données et insights, prise en charge de Power BI pour Azure AD B2B rend facile et rentable à le faire.

Voici les structures organisationnelles généralement rencontrés qui sont bien adaptés pour Azure AD B2B une collaboration inter-organisations style dans Power BI. Azure AD B2B fonctionne bien dans la plupart des cas, mais dans certaines situations courantes des approches alternatives traitées à la fin de ce document méritent.

### <a name="case-1-direct-collaboration-between-organizations"></a>Cas 1 : Collaboration directe entre les organisations

Relation de Contoso avec son fournisseur radiateur est un exemple de collaboration directe entre les organisations. Dans la mesure où il existe relativement peu d’utilisateurs chez Contoso et son fournisseur ont besoin d’accéder aux informations du fiabilité radiateur, à l’aide d’Azure AD B2B en fonction de partage externe sont idéal. Il est facile à utiliser et facile à gérer. Il s’agit également un modèle courant dans les services de conseil où un consultant peut-être générer le contenu d’une organisation.

![Partager entre les organisations](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_04.png)


En règle générale, ce partage se produit initialement à l’aide d’Ad hoc par le partage d’éléments. Toutefois, la croissance des équipes ou approfondir les relations, la planifié par le partage d’éléments approche devient la méthode recommandée pour réduire les frais de gestion. En outre, l’Ad hoc ou planifiée de partage des applications Power BI, commentaires et l’abonnement au contenu entre plusieurs organisations, accès au contenu dans les applications mobiles peuvent provenir dans play ainsi, la modification entre les organisations et la gestion de contenu Power BI. Plus important encore, si les utilisateurs de deux entreprises disposent de licences Power BI Pro dans leurs départements respectifs, ils peuvent utiliser ces licences Pro dans les environnements de Power BI à l’autre. Ainsi, les licences avantageux dans la mesure où l’organisation invitante n’ayez pas à payer pour une licence Power BI Pro pour les utilisateurs externes. Ce sujet est abordé plus en détail dans la section Gestion des licences plus loin dans ce document.

### <a name="case-2-parent-and-its-subsidiaries-or-affiliates"></a>Cas 2 : Parent et de ses filiales ou affiliés

Certaines structures d’organisation sont plus complexes, y compris les filiales partiellement ou totalement détenus, ses sociétés affiliées ou des relations de fournisseur de service géré. Ces organisations disposent d’une organisation de parent par exemple, une société de portefeuille, mais les organisations sous-jacent obéissent point-virgule autonome, parfois des exigences différentes régionales. Cela conduit à chaque organisation ayant son propre environnement Azure AD et les locataires Power BI distincts.

![Utilisation de filiales](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_05.png)


Dans cette structure, l’organisation parente doit en général distribuer insights standardisés à ses filiales. En règle générale, ce partage se produit à l’aide du partage Ad hoc ou planifiée de l’approche d’applications Power BI comme illustré dans l’image suivante, car elle permet la distribution de contenu de référence standardisée à un large public. Dans la pratique, une combinaison de tous les scénarios mentionnés plus haut dans ce document est utilisée.

![Combinaison de scénarios](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_06.png)


Cela suit le processus suivant :

1. Les utilisateurs à partir de chaque filiale sont invités à Azure de Contoso AD
2. Puis l’application Power BI est publiée pour leur accorder l’accès aux données requises
3. Enfin, l’utilisateur ouvre l’application via un lien que leur a été accordé pour afficher les rapports

Plusieurs problèmes importants sont rencontrés par les organisations dans cette structure :

- Comment distribuer des liens vers du contenu dans Power BI l’organisation parente
- Comment autoriser des utilisateurs à accéder à la source de données hébergée par l’organisation parente de filiale

#### <a name="distributing-links-to-content-in-the-parent-organizations-power-bi"></a>Distribution des liens vers du contenu dans Power BI l’organisation parente

Trois approches sont couramment utilisés pour distribuer des liens vers du contenu. La première et la plupart des basic est pour envoyer le lien à l’application pour les utilisateurs requis ou de le placer dans un site SharePoint Online à partir duquel il peut être ouvert. Les utilisateurs peuvent signet puis le lien dans un navigateur pour un accès plus rapide aux données que dont ils ont besoin.

La deuxième approche s’appuie sur la modification entre les organisations et la gestion de la fonctionnalité de contenu Power BI. L’organisation parente permet aux utilisateurs des filiales d’accéder à son Power BI et contrôle qu’ils peuvent accéder via l’autorisation. Cela donne accès à Power BI page d’accueil où l’utilisateur à partir de la filiale voit une liste complète des contenus partagés avec eux dans le client de l’organisation parente. Puis l’URL à l’environnement de Power BI de l’organisation parente est donnée aux utilisateurs dans les filiales.

La dernière approche utilise une application de Power BI créée au sein du locataire Power BI pour chaque filiale. L’application Power BI inclut un tableau de bord avec [vignettes configurés avec l’option de lien externe](https://docs.microsoft.com/power-bi/service-dashboard-edit-tile#hyperlink). Lorsque l’utilisateur appuie sur la vignette, ils sont dirigés vers le rapport approprié, un tableau de bord ou une application dans Power BI l’organisation parente. Cette approche présente l’avantage que l’application peut être installée automatiquement pour tous les utilisateurs dans la filiale et s’il est disponible pour les chaque fois qu’ils se connectent à leur propre environnement Power BI. Un autre avantage de cette approche est qu’elle fonctionne bien avec les applications mobiles Power BI capable d’ouvrir le lien en mode natif. Vous pouvez également combiner ceci avec la deuxième approche pour activer la plus facile de basculer entre les environnements de Power BI.

#### <a name="allowing-subsidiary-users-to-access-data-sources-hosted-by-the-parent-organization"></a>Permettre aux utilisateurs de filiale accéder aux sources de données hébergés par l’organisation parente

Souvent les analystes à une filiale ont besoin créer leurs propres analytique à l’aide des données fournies par l’organisation parente. Dans ce cas, les sources de données de cloud sont couramment pour relever le défi.

Tire parti de la première approche [Azure Analysis Services](https://docs.microsoft.com/azure/analysis-services/analysis-services-overview) pour créer un entrepôt de données de niveau entreprise qui répond aux besoins d’analystes entre le parent et ses filiales, comme le montre l’image suivante. Contoso peut héberger les données et utiliser des fonctionnalités telles que la sécurité au niveau des lignes permettant aux utilisateurs dans chaque filiale peut accéder uniquement à leurs données. Analystes à chaque organisation peuvent accéder à l’entrepôt de données via Power BI Desktop et publier analytique qui en résulte à leurs clients respectifs de Power BI.

![Comment le partage s’effectue avec les locataires Power BI](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_07.png)


La deuxième approche s’appuie sur [base de données SQL Azure](https://azure.microsoft.com/services/sql-database/) pour générer un data warehouse relationnel pour fournir l’accès aux données. Cela fonctionne comme l’approche Azure Analysis Services, bien que certaines fonctionnalités telles que la sécurité au niveau des lignes peut être plus difficile à déployer et maintenir entre les filiales.

Approches plus sophistiquées sont également possibles, mais la méthode ci-dessus sont de loin le plus courante.

### <a name="case-3-shared-environment-across-partners"></a>Cas 3 : Environnement partagé entre les partenaires

Contoso peut établir un partenariat avec un concurrent pour conjointement générer une voiture sur une ligne d’assembly partagée, mais pour distribuer le véhicule sous différentes marques ou dans différentes régions. Cela nécessite une collaboration extensible et copropriété de données, l’intelligence et analytique entre plusieurs organisations. Cette structure est également courante dans le secteur des services Conseil où une équipe de consultants peut-être faire analytique basée sur le projet pour un client.

![Environnement partagé entre les partenaires](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_08.png)



Dans la pratique, ces structures sont complexes, comme illustré dans l’image suivante et imposer que le personnel à gérer. Pour être efficace cette structure s’appuie sur la modification entre les organisations et la gestion de la fonctionnalité de contenu Power BI, car elle permet aux organisations de réutiliser des licences Power BI Pro achetées pour leurs clients respectifs de Power BI.

![Licences et le contenu d’organisation partagé](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_09.png)



Pour établir un locataire Power BI partagé, Azure Active Directory doit être créé et au moins un compte d’utilisateur Power BI Pro doit être acheté pour un utilisateur dans active directory. Cet utilisateur invite les utilisateurs requis pour l’organisation partagée. Plus important encore, dans ce scénario, les utilisateurs de Contoso sont traités en tant qu’utilisateurs externes qui fonctionnent au sein Power BI de l’entreprise partagés.

Le processus est comme suit :

1. L’organisation partagé est établie en tant qu’un nouveau Azure Active Directory et au moins un compte d’utilisateur est créé dans la nouvelle organisation. Cet utilisateur doit avoir une licence de Power BI Pro.
2. Ensuite, cet utilisateur établit un locataire Power BI et invite les utilisateurs requis à partir de Contoso et l’organisation partenaire. L’utilisateur établit également les ressources de données partagé comme Azure Analysis Services. Contoso et les utilisateurs du partenaire peuvent accéder à Power BI l’organisation partagée en tant qu’utilisateurs invités. Si autorisé à modifier et gérer le contenu dans Power BI les utilisateurs externes peuvent utiliser Power BI domestique, utilisez des espaces de travail, téléchargement ou modifiez contenu et partager des rapports. En règle générale, toutes les ressources partagées sont stockées et accessibles à partir de l’organisation partagée.
3. Selon la façon dont les parties conviennent de collaborer, il est possible pour chaque organisation développer leurs propres données propriétaires et l’analytique à l’aide des ressources de l’entrepôt de données partagée. Ils peuvent leur distribution à leurs utilisateurs respectifs d’internes à l’aide de leurs clients de Power BI internes.

### <a name="case-4-distribution-to-hundreds-or-thousands-of-external-partners"></a>Cas 4 : Distribution à des centaines voire des milliers de partenaires externes

Bien que Contoso a créé un rapport de fiabilité radiateur pour un seul fournisseur, Contoso souhaite maintenant créer un ensemble de rapports standardisés pour des centaines de fournisseurs. Cela permet à Contoso d’assurer tous les fournisseurs l’analytique dont ils ont besoin pour apporter des améliorations ou corriger les défauts de fabrication.

![Distribution à de nombreux partenaires](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_10.png)


Lorsqu’une organisation doit distribuer les données standardisées et informations pour les nombreux utilisateurs/organisations externes, ils peuvent utiliser le partage Ad hoc ou planifiée du scénario d’applications Power BI pour créer un portail BI rapidement et sans les coûts de développement complète. Le processus pour générer cet un portail à l’aide d’une application Power BI est traité dans l’étude de cas : Création d’un portail de BI à l’aide de Power BI + l’Azure AD B2B – étape par étape des instructions plus loin dans ce document.

Une variante courante de ce cas est lorsqu’une organisation tente de partager des informations aux consommateurs, en particulier lors de la recherche pour utiliser Azure B2C avec Power BI. Power BI ne prend pas en charge Azure B2C. Si vous évaluez les options pour ce cas, envisagez d’utiliser autre Option 2 dans les approches alternatives courantes à la section plus loin dans ce document.

## <a name="case-study-building-a-bi-portal-using-power-bi--azure-ad-b2b--step-by-step-instructions"></a>Étude de cas : Création d’un portail de BI à l’aide de Power BI + l’Azure AD B2B – obtenir des instructions pas à pas

Intégration de Power BI avec Azure AD B2B permet de Contoso fluide et de simplicité pour fournir aux utilisateurs invités un accès sécurisé à son portail BI. Contoso peut configurer ceci avec trois étapes :

![Création d’un portail](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_11.png)


1. Créer un portail BI dans Power BI

    La première tâche pour Contoso consiste à créer leur portail BI dans Power BI. Portail de BI de Contoso se compose d’une collection des tableaux de bord et rapports qui vont être apportées à de nombreux utilisateurs internes et invités. La méthode recommandée pour effectuer cette opération dans Power BI consiste à créer une application Power BI. En savoir plus sur [applications dans Power BI](https://powerbi.microsoft.com/blog/distribute-to-large-audiences-with-power-bi-apps/).

- L’équipe de Contoso BI crée un espace de travail d’application dans Power BI

    ![Espace de travail d’application](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_12.png)
    

- D’autres auteurs sont ajoutés à l’espace de travail

    ![Ajouter des auteurs](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_13.png)


- Le contenu est créé à l’intérieur de l’espace de travail

    ![Créer du contenu à l’intérieur de l’espace de travail](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_14.png)


    Maintenant que le contenu est créé dans un espace de travail d’application, Contoso est prêt à inviter des utilisateurs dans des organisations partenaires à consommer ce contenu.

2. Convier des utilisateurs invités

    Il existe deux façons pour Contoso inviter des utilisateurs à son portail BI dans Power BI :

    * Invitations planifiées
    * Invitations ad hoc

    **Invitations planifiées**

    Dans cette approche, Contoso invite les utilisateurs invités à son Azure AD avance et puis distribue le contenu Power BI. Contoso peut inviter des utilisateurs à partir du portail Azure ou à l’aide de PowerShell. Voici les étapes pour inviter des utilisateurs à partir du portail Azure :

    - L’administrateur Azure AD de Contoso accède à **portail Azure > Azure Active Directory > utilisateurs et groupes > tous les utilisateurs > nouvel utilisateur invité**

    ![Utilisateur invité](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_15.png)


    - Ajouter un message d’invitation pour les utilisateurs invités et cliquez sur invitation

    ![Ajouter l’invitation](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_16.png)


    > [!NOTE]
    > Pour inviter des utilisateurs à partir du portail Azure, vous avez besoin à un administrateur pour Azure Active Directory de votre client.

    Si Contoso souhaite inviter de nombreux utilisateurs invités, ils peuvent utiliser PowerShell. L’administrateur de Contoso Azure AD stocke les adresses de messagerie de tous les utilisateurs invités dans un fichier CSV. Voici [Azure Active Directory B2B collaboration code et exemples PowerShell](https://docs.microsoft.com/azure/active-directory/b2b/code-samples) et obtenir des instructions.

    Une fois l’invitation, les utilisateurs invités reçoivent un e-mail avec le lien d’invitation.

    ![Lien d’invitation](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_17.png)


    Une fois que les utilisateurs invités sur le lien, ils peuvent accéder au contenu dans le locataire Contoso Azure AD.

    > [!NOTE]
    > Il est possible de modifier la disposition de l’e-mail d’invitation à l’aide de la fonctionnalité de personnalisation d’Azure AD comme décrit [ici](https://docs.microsoft.com/azure/active-directory/active-directory-b2b-invitation-email).


    **Invitations ad hoc**

    Que se passe-t-il si Contoso ne sait pas tous les utilisateurs invités qu'il souhaite inviter avance ? Ou bien, que se passe-t-il si l’analyste de Contoso qui a créé le portail BI souhaite distribuer du contenu à des utilisateurs invités lui-même ? Nous avons également en charge ce scénario dans Power BI avec les invitations ad-hoc.

    L’analyste peut suffit d’ajouter les utilisateurs externes à la liste d’accès de l’application quand ils sont la publication. Les utilisateurs invités Obtient une invitation et une fois qu’ils l’acceptez pas, ils sont automatiquement redirigés vers le contenu Power BI.

    ![Ajouter un utilisateur externe](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_18.png)


    > [!NOTE]
    > Invitations sont nécessaires uniquement la première fois qu'un utilisateur externe est invité à votre organisation.


3. Distribuer du contenu

    Maintenant que l’équipe de Contoso BI a créé le portail de BI et invité des utilisateurs invités, ils peuvent distribuer leur portail à leurs utilisateurs finaux en donnant des accès utilisateurs invités à l’application et en la publiant. Power BI complète automatiquement les noms des utilisateurs invités qui ont été précédemment ajoutés au locataire Contoso. Invitations ad hoc à d’autres utilisateurs invités peuvent également être ajoutées à ce stade.

    > [!NOTE]
    > Si vous utilisez des groupes de sécurité pour gérer l’accès à l’application pour les utilisateurs externes, utilisez l’approche planifié invite et partager le lien de l’application directement avec chaque utilisateur externe qui doive y accéder. Sinon, l’utilisateur externe ne peut pas être en mesure d’installer ou d’afficher le contenu à partir de l’application. _

    Les utilisateurs invités reçoivent un e-mail contenant un lien vers l’application.

    ![Lien d’invitation par courrier électronique](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_19.png)


    Lorsque vous cliquez sur ce lien, les utilisateurs invités sont invités à vous authentifier avec l’identité de leur propre organisation.

    ![Page de connexion](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_20.png)


    Une fois qu’ils sont authentifiés avec succès, ils sont redirigés vers l’application de BI de Contoso.

    ![Consultez le contenu partagé](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_21.png)

    Les utilisateurs invités peuvent obtenir par la suite à l’application de Contoso en cliquant sur le lien dans l’e-mail ou le lien de création de signets. Contoso peut également faciliter pour les utilisateurs invités en ajoutant ce lien à n’importe quel portail extranet existant qui utilisent déjà des utilisateurs invités.

4. Étapes suivantes

    À l’aide d’une application Power BI et Azure AD B2B, Contoso a pu rapidement créer un portail BI pour ses fournisseurs de manière sans code. Cela est considérablement simplifiée d’analytique standardisé pour tous les fournisseurs qui en avait besoin de distribution.

    Tandis que l’exemple a montré comment un rapport commun unique peut être réparti entre les fournisseurs, Power BI peut aller plus loin. Pour garantir que chaque partenaire voit uniquement les données pertinentes pour eux-mêmes, sécurité au niveau des lignes peuvent être ajoutée facilement pour le modèle de rapport et des données. La sécurité des données de la section des partenaires externes plus loin dans ce document décrit ce processus dans les détails.

    Tableaux de bord et rapports souvent individuels doivent être incorporé à un portail existant. Cela peut également être accompli réutiliser la plupart des techniques présentées dans l’exemple. Toutefois, dans ces situations, il peut être plus facile incorporer des rapports ou tableaux de bord directement à partir d’un espace de travail. Le processus de l’invitation et affectez une autorisation de sécurité pour les utilisateurs doit rester le même.

## <a name="under-the-hood-how-is-lucy-from-supplier1-able-to-access-power-bi-content-from-contosos-tenant"></a>Sous le capot : Comment est Lucy à partir de Supplier1 en mesure d’accéder au contenu de Power BI de locataire de Contoso ?

Maintenant que nous avons vu comment Contoso est en mesure de distribuer en toute transparence le contenu de Power BI à des utilisateurs invités dans des organisations partenaires, nous allons voir comment cela fonctionne sous le capot.

Lorsque Contoso invité [ lucy@supplier1.com ](mailto:lucy@supplier1.com) à son répertoire, Azure AD crée un lien entre [ Lucy@supplier1.com ](mailto:Lucy@supplier1.com) et le locataire Contoso Azure AD. Ce lien permet de savoir que Azure AD Lucy@supplier1.com peuvent accéder au contenu dans le locataire Contoso.

Lorsque Lucy tente d’accéder à application de Power BI de Contoso, Azure AD vérifie que Lucy accessible le locataire Contoso et Power BI fournit un jeton qui indique que Lucy est authentifiée à l’accès de contenu dans le locataire Contoso. Power BI utilise ce jeton pour autoriser et assurez-vous que Lucy a accès à l’application de Power BI de Contoso.

![Vérification et autorisation](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_22.png)

L’intégration de Power BI avec Azure AD B2B fonctionne avec toutes les adresses de messagerie d’entreprise. Si l’utilisateur ne dispose pas d’une identité Azure AD, ils peuvent être vous y êtes invités à en créer un. L’illustration suivante montre le flux détaillé :

![Diagramme de flux d’intégration](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_23.png)


Il est important de reconnaître que le compte Azure AD sera utilisé ou créé dans la partie externe d’Azure AD, ce qui permettra marque, il est possible que Lucy peut utiliser son propre nom d’utilisateur et le mot de passe et que ses informations d’identification seront automatiquement cessera de fonctionner dans d’autres clients chaque fois qu’elle quitte l’entreprise lors de son organisation utilise également Azure AD.

## <a name="licensing"></a>Licensing

Contoso peut choisir une des trois approches pour les utilisateurs invités de licence à partir de ses fournisseurs et les organisations partenaires à accéder au contenu de Power BI.

> [!NOTE]
> _Niveau gratuit de B2B de AD Azure est suffisant pour utiliser Power BI avec Azure AD B2B. Certaines fonctionnalités Azure AD B2B avancées telles que les groupes dynamiques nécessitent des licences supplémentaires. Reportez-vous à la documentation d’Azure AD B2B pour plus d’informations :_ [_https://docs.microsoft.com/azure/active-directory/b2b/licensing-guidance_](https://docs.microsoft.com/azure/active-directory/b2b/licensing-guidance)

### <a name="approach-1-contoso-uses-power-bi-premium"></a>Approche 1 : Contoso utilise Power BI Premium

Avec cette approche, Contoso achète de capacité Power BI Premium et assigne son contenu portail BI à cette capacité. Ainsi, les utilisateurs d’organisations partenaires à accéder à application de Power BI de Contoso sans licence Power BI.

Les utilisateurs externes sont également soumis à la consommation des expériences uniquement proposés aux utilisateurs « Gratuits » dans Power BI lors de la consommation de contenu au sein de Power BI Premium.

Contoso peut également tirer parti des autres fonctionnalités premium de Power BI pour ses applications comme les fréquences de rafraîchissement accrues, une capacité dédiée et tailles de modèle de grande taille.

![Fonctionnalités supplémentaires](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_24.png)


### <a name="approach-2-contoso-assigns-power-bi-pro-licenses-to-guest-users"></a>Approche 2 : Contoso affecte des licences Power BI Pro aux utilisateurs invités

Avec cette approche, Contoso attribue des licences pro à des utilisateurs invités de partenaire organisations : cela est possible à partir du centre d’administration Microsoft 365 de Contoso. Ainsi, les utilisateurs d’organisations partenaires à accéder l’application de Power BI de Contoso sans acheter une licence eux-mêmes. Cela peut être appropriée pour le partage avec des utilisateurs externes dont l’organisation n’a pas arrêté encore Power BI.

> [!NOTE]
> _Licence pro de Contoso s’applique aux utilisateurs invités uniquement lorsqu’ils y accéder dans le locataire Contoso. Licences Pro activer l’accès au contenu qui n’est pas une capacité Power BI Premium. Toutefois, les utilisateurs externes avec une licence Pro sont restreintes par défaut pour une expérience de consommation uniquement. Cela peut être modifié à l’aide de l’approche décrite dans la_ _permettre aux utilisateurs externes à modifier et gérer le contenu au sein de Power BI_ _section plus loin dans ce document._

![Informations de licence](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_25.png)


### <a name="approach-3-guest-users-bring-their-own-power-bi-pro-license"></a>Approche 3 : Les utilisateurs invités porter leur propre licence Power BI Pro

Avec cette approche, fournisseur 1 attribue une licence Power BI Pro à Lucy. Elle peut ensuite accéder à application de Power BI de Contoso avec cette licence. Étant donné que Lucy peut utiliser sa licence Pro à partir de sa propre organisation lors de l’accès à un environnement de Power BI externe, cette approche est parfois appelée _apportez votre propre licence_ (BYOL). Si les deux organisations sont à l’aide de Power BI, cela offre la gestion des licences avantageuse pour la solution d’analytique globale et minimise la surcharge de l’attribution de licences aux utilisateurs externes.

> [!NOTE]
> _La licence pro accordée Lucy par fournisseur 1 s’applique à n’importe quel client Power BI où Lucy est un utilisateur invité. Licences Pro activer l’accès au contenu qui n’est pas une capacité Power BI Premium. Toutefois, les utilisateurs externes avec une licence Pro sont restreintes par défaut pour une expérience de consommation uniquement. Cela peut être modifié à l’aide de l’approche décrite dans la_ _permettre aux utilisateurs externes à modifier et gérer le contenu au sein de Power BI_ _section plus loin dans ce document._

![Conditions de licence Pro](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_26.png)

## <a name="data-security-for-external-partners"></a>Sécurité des données pour les partenaires externes

Couramment lorsque vous travaillez avec plusieurs fournisseurs externes, Contoso doit s’assurer que chaque fournisseur voit les données uniquement sur ses propres produits. Sécurité basée sur l’utilisateur et la sécurité au niveau ligne dynamique facilitent la tâche à accomplir avec Power BI.

### <a name="user-based-security"></a>Sécurité basée sur l’utilisateur

Une des fonctionnalités plus puissantes de Power BI est Row Level Security. Cette fonctionnalité permet à Contoso créer un rapport unique et un jeu de données, mais toujours appliquer les règles de sécurité différentes pour chaque utilisateur. Pour obtenir une explication détaillée, consultez [sécurité au niveau des lignes (RLS)](https://powerbi.microsoft.com/documentation/powerbi-admin-rls/).

Intégration de Power BI avec Azure AD B2B permet à Contoso d’attribuer des règles de sécurité de niveau ligne pour les utilisateurs invités dès qu’ils sont invités au locataire Contoso. Comme nous l’avons vu précédemment, Contoso peut ajouter des utilisateurs invités à l’aide invitations ad hoc ou planifié. Si Contoso souhaite appliquer une sécurité au niveau ligne, il est fortement recommandé d’utiliser des invitations planifiées pour ajouter les utilisateurs invités avant l’heure et de les assigner aux rôles de sécurité avant de partager le contenu. Si Contoso utilise à la place les invitations ad hoc, il peut y avoir une courte période de temps où les utilisateurs invités ne seront pas en mesure d’accéder aux données.

> [!NOTE]
> Ce délai dans l’accès aux données protégées par RLS lorsqu’à l’aide d’ad-hoc invite peut conduire à prendre en charge des demandes à votre équipe informatique, car les utilisateurs verront vide ou rompu recherche rapports/tableaux de bord lors de l’ouverture d’un partage de lien dans l’e-mail qu’ils reçoivent. Par conséquent, il est fortement recommandé d’utiliser invitations planifiées dans scenario.* *

Nous allons étudier cela avec un exemple.

Comme mentionné précédemment, Contoso dispose de fournisseurs dans le monde, et ils veulent s’assurer que les utilisateurs de leurs organisations fournisseur obtiennent des informations à partir des données à partir de simplement son territoire.  Mais les utilisateurs de Contoso peuvent accéder à toutes les données. Au lieu de créer plusieurs rapports différents, Contoso crée un rapport unique et filtre les données en fonction de l’utilisateur à afficher.

![Contenu partagé](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_27.png)

Pour vous assurer de que Contoso peut filtrer les données en fonction de qui se connecte, deux rôles sont créés dans Power BI desktop. Une pour filtrer toutes les données à partir de la SalesTerritory « Europe » et l’autre pour « North America ».

![La gestion des rôles](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_28.png)

Chaque fois que les rôles sont définis dans le rapport, un utilisateur doit être affecté à un rôle spécifique pour qu’ils puissent accéder à toutes les données. L’attribution de rôles se produit dans le service Power BI ( **jeux de données > sécurité** )

![Définition de la sécurité](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_29.png)

Cette opération ouvre une page où l’équipe de Contoso BI permettre voir les deux rôles, ils ont créés.  L’équipe de Contoso BI permettre désormais affecter des utilisateurs aux rôles.

![Sécurité au niveau des lignes](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_30.png)

Dans l’exemple Contoso est Ajout d’un utilisateur dans une organisation partenaire avec l’adresse de messagerie «[adam@themeasuredproduct.com](mailto:adam@themeasuredproduct.com)» pour le rôle de l’Europe :

![Paramètres de sécurité de niveau ligne](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_31.png)

Cela est résolu par Azure AD, Contoso peut voir le nom apparaît dans la fenêtre prêt à ajouter :

![Afficher les rôles](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_32.png)

Maintenant lorsque cet utilisateur ouvre l’application qui a été partagée avec lui, il voit uniquement un rapport avec les données d’Europe :

![Afficher le contenu](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_33.png)

### <a name="dynamic-row-level-security"></a>Sécurité au niveau ligne dynamique

Un autre sujet intéressant est de voir le travail de sécurité au niveau (RLS) avec Azure AD B2B de ligne dynamique.

En bref, la sécurité au niveau ligne dynamique fonctionne en filtrant les données dans le modèle basé sur le nom d’utilisateur de la personne qui se connecte à Power BI. Au lieu d’ajouter plusieurs rôles pour les groupes d’utilisateurs, vous définissez les utilisateurs dans le modèle. Nous ne décrirons pas le modèle en détail ici. Kasper de Jong offre une écriture détaillée jusqu'à sur toutes les versions de la sécurité de niveau ligne dans [Power BI Desktop dynamique aide-mémoire sécurité](https://www.kasperonbi.com/power-bi-desktop-dynamic-security-cheat-sheet/)et dans [ce livre blanc](https://msdn.microsoft.com/library/jj127437.aspx) .

Examinons un exemple de petit - Contoso dispose d’un rapport simple sur les ventes par groupes :

![Exemple de contenu](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_34.png)

À présent ce rapport doit être partagé avec les deux utilisateurs invités et d’un utilisateur interne : l’utilisateur interne peut voir tous les éléments, mais les utilisateurs invités peuvent voir uniquement les groupes, ils ont accès. Cela signifie que nous devons filtrer les données uniquement pour les utilisateurs invités. Pour filtrer les données de manière appropriée, Contoso utilise le modèle de lignes dynamiques comme décrit dans le billet de blog et le livre blanc. Cela signifie, Contoso ajoute les noms d’utilisateur aux données elles-mêmes :

![Afficher les utilisateurs de lignes pour les données proprement dites](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_35.png)

Ensuite, Contoso crée le modèle de données de droite qui filtre les données correctement avec les relations de droite :

![Les données appropriées s’affichent](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_36.png)

Pour filtrer les données automatiquement en fonction des personnes connectées, Contoso a besoin créer un rôle qui passe de l’utilisateur qui se connecte. Dans ce cas, Contoso crée deux rôles : le premier est le « securityrole » qui filtre le tableau des utilisateurs avec le nom d’utilisateur actuel de l’utilisateur connecté à Power BI (cela fonctionne même pour les utilisateurs invités Azure AD B2B).

![Gérer les rôles](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_37.png)

Contoso crée également un autre « AllRole » pour ses utilisateurs internes qui peuvent voir tout : ce rôle n’a pas de n’importe quel prédicat de sécurité.

Après avoir téléchargé le fichier Power BI desktop dans le service, Contoso peut affecter les utilisateurs invités aux utilisateurs internes à la « AllRole » et « SecurityRole »

Désormais, lorsque les utilisateurs invités ouvrent le rapport, ils ne voit que ventes de groupe a :

![Uniquement à partir de groupe A](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_38.png)

Dans la matrice à droite, vous pouvez voir le résultat de la fonction USERNAME() et USERPRINCIPALNAME() que toutes deux retournent le qu'adresse de messagerie des utilisateurs invités.

L’utilisateur interne obtienne désormais voir toutes les données :

![Toutes les données affichées](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_39.png)

Comme vous pouvez le voir, RLS dynamique fonctionne avec les utilisateurs internes ou invités.

> [!NOTE]
> Ce scénario fonctionne également lorsque vous utilisez un modèle dans Azure Analysis Services. Généralement, votre Service d’analyse Azure est connecté à la même instance Azure AD en tant que votre Power BI : dans ce cas, Azure Analysis Services sait également que les utilisateurs invités via Azure AD B2B.

## <a name="connecting-to-on-premises-data-sources"></a>Connexion aux sources de données locales

Power BI offre la possibilité pour que Contoso puisse tirer parti de sources de données de site comme [SQL Server Analysis Services](https://powerbi.microsoft.com/documentation/powerbi-gateway-enterprise-manage-ssas/) ou [SQL Server](https://powerbi.microsoft.com/documentation/powerbi-gateway-kerberos-for-sso-pbi-to-on-premises-data/) directement grâce à la [passerelle de données locale](https://powerbi.microsoft.com/documentation/powerbi-gateway-onprem/). Il est même possible de se connecter à ces sources de données avec les mêmes informations d’identification que celles utilisées avec Power BI.

> [!NOTE]
> Lorsque vous installez une passerelle pour se connecter à votre client Power BI, vous devez utiliser un utilisateur créé au sein de votre client. Les utilisateurs externes ne peuvent pas installer une passerelle et le connecter à votre client. _

Pour les utilisateurs externes, cela peut être plus compliqué car les utilisateurs externes ne sont généralement pas connues à sur site AD. Power BI offre une solution de contournement pour ce en permettant aux administrateurs de Contoso mapper les noms d’utilisateurs externes à des noms d’utilisateur interne comme décrit dans [gérer votre source de données - Analysis Services](https://powerbi.microsoft.com/documentation/powerbi-gateway-enterprise-manage-ssas/). Par exemple, [ lucy@supplier1.com ](mailto:lucy@supplier1.com) peut être mappé à [lucy\_supplier1\_com #EXT@contoso.com](mailto:lucy_supplier1_com).

![Mappage de noms d’utilisateur](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_40.png)

Cette méthode consiste si Contoso dispose uniquement d’une poignée d’utilisateurs ou si Contoso peut mapper tous les utilisateurs externes à un seul compte interne. Pour des scénarios plus complexes où chaque utilisateur a besoin de leurs propres informations d’identification, il existe une approche plus avancée qui utilise [attributs AD personnalisés](https://technet.microsoft.com/library/cc961737.aspx) pour effectuer le mappage, comme décrit dans [gérer votre source de données - Analysis Services](https://powerbi.microsoft.com/documentation/powerbi-gateway-enterprise-manage-ssas/). Cela permet à l’administrateur de Contoso définir un mappage pour chaque utilisateur dans Azure AD (également des utilisateurs B2B externes).  Ces attributs peuvent être définis via le modèle d’objet AD à l’aide de scripts ou du code afin de Contoso peut automatiser entièrement le mappage sur invitation ou sur une cadence planifiée.

## <a name="enabling-external-users-to-edit-and-manage-content-within-power-bi"></a>Permettre aux utilisateurs externes à modifier et gérer le contenu au sein de Power BI

Contoso peut autoriser des utilisateurs externes à contribuer au contenu au sein de l’organisation, comme décrit précédemment dans l’inter-organisations modification et la gestion de la section de contenu Power BI.

> [!NOTE]
> Pour modifier et gérer le contenu au sein Power BI de votre organisation, l’utilisateur doit avoir une licence Power BI Pro dans un espace de travail autre que mon espace de travail. Les utilisateurs peuvent obtenir des licences Pro tel qu’indiqué dans l’option _Licensing__section de ce document._

Le portail d’administration Power BI fournit le **autoriser à modifier et gérer des utilisateurs invités externes contenu dans l’organisation** définissant dans Paramètres du locataire. Par défaut, le paramètre est défini sur désactivé, ce qui signifie que les utilisateurs externes Obtient une expérience en lecture seule contrainte par défaut. Le paramètre s’applique aux utilisateurs avec UserType défini sur invité dans Azure AD. Le tableau ci-dessous décrit les comportements à rencontrent des utilisateurs en fonction de leur UserType et la façon dont les paramètres sont configurés.

| **Type d’utilisateur dans Azure AD** | **Autoriser les utilisateurs invités externes à modifier et gérer les paramètres de contenu** | **Behavior** |
| --- | --- | --- |
| Invité | Désactivé pour l’utilisateur (par défaut) | Par la consommation affichage des éléments uniquement. Autorise l’accès en lecture seule aux rapports, des tableaux de bord et des applications lorsqu’ils sont affichés via une URL envoyée à l’utilisateur invité. Applications mobiles Power BI fournissent une vue en lecture seule à l’utilisateur invité. |
| Invité | Activé pour l’utilisateur | L’utilisateur externe accède à l’expérience complète de Power BI, même si certaines fonctionnalités ne sont pas disponibles pour eux. L’utilisateur externe devez vous connecter à Power BI à l’aide de l’URL du Service Power BI avec les informations de locataire incluses. L’Obtient de l’utilisateur basé sur les autorisations, l’expérience d’accueil et un mon espace de travail permettre Parcourir, afficher et créer du contenu. </br></br> Applications mobiles Power BI fournissent une vue en lecture seule à l’utilisateur invité. |

> [!NOTE]
> Les utilisateurs externes dans Azure AD peuvent également être définis à UserType membre. Cela n'est pas actuellement pris en charge dans Power BI.

Dans le portail d’administration Power BI, le paramètre est indiqué dans l’image suivante.

![Paramètres administrateur](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_41.png)

Les utilisateurs invités obtiennent l’expérience par défaut en lecture seule et qui peut modifier et gérer le contenu. La valeur par défaut est désactivé, ce qui signifie que tous les utilisateurs invités ont l’expérience en lecture seule. L’administration de Power BI peuvent activer le paramètre pour tous les utilisateurs invités dans l’organisation ou des groupes de sécurité spécifiques définis dans Azure AD. Dans l’image suivante, l’administrateur de Contoso Power BI créé un groupe de sécurité dans Azure AD pour gérer les utilisateurs externes peuvent modifier et gérer du contenu dans le locataire Contoso.

Pour aider ces utilisateurs à se connecter à Power BI, fournissez-lui l’URL de locataire. Pour trouver l’URL de locataire, effectuez les étapes suivantes.

1. Dans le service Power BI, dans le menu supérieur, sélectionnez l’aide ( **?** ) puis **sur Power BI**.
2. Recherchez la valeur regard **URL de locataire**. Il s’agit de l’URL de locataire que vous pouvez partager avec vos utilisateurs invités.

    ![URL de locataire](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_42.png)

Lorsque vous utilisez l’autoriser les utilisateurs invités externes pour modifier et gérer le contenu de l’organisation, les utilisateurs invités spécifié accéder à Power BI votre organisation et consultez n’importe quel contenu auquel ils ont l’autorisation. Ils peuvent accéder accueil, parcourir et contribuer au contenu aux espaces de travail, installer des applications où ils figurent dans la liste d’accès et ont un mon espace de travail. Ils peuvent créer ou être des administrateurs d’espaces de travail qui utilisent la nouvelle expérience d’espace de travail.

> [!NOTE]
> Lorsque cette option veillez à consulter la section de gouvernance de ce document, car les paramètres Azure AD par défaut empêchent les utilisateurs invités pour utiliser certaines fonctionnalités telles que les sélecteurs de personnes, ce qui peuvent entraîner une réduction experience.* *

Pour les utilisateurs invités activées via l’autoriser les utilisateurs invités externes à modifier et gérer le contenu dans le paramètre du client de l’organisation, certaines expériences ne sont pas à leur disposition. Pour mettre à jour ou publier des rapports, les utilisateurs invités doivent utiliser l’interface utilisateur, y compris obtenir des données pour charger des fichiers Power BI Desktop du web de service de Power BI. Les expériences suivantes ne sont pas prises en charge :

- Diriger la publication de Power BI Desktop vers le service Power BI
- Les utilisateurs invités ne peuvent pas utiliser Power BI Desktop pour se connecter à des jeux de données du service dans le service Power BI
- Espaces de travail classiques liés à des groupes Office 365 : Un utilisateur invité ne peut pas créer ou être un administrateur de ces espaces de travail. Ils peuvent être membres.
- L’envoi d’invitations ad hoc n’est pas pris en charge pour les listes d’accès aux espaces de travail
- Power BI Publisher pour Excel n’est pas pris en charge pour les utilisateurs invités
- Les utilisateurs invités ne peuvent pas installer une passerelle Power BI Gateway et la connecter à votre organisation
- Les utilisateurs invités ne peuvent pas installer d’applications à publier dans toute l’organisation
- Les utilisateurs invités ne peuvent pas utiliser, créer, mettre à jour ou installer des packs de contenu d’organisation
- Les utilisateurs invités ne peuvent pas utiliser la fonctionnalité Analyser dans Excel
- Les utilisateurs invités ne peuvent pas être @mentioned en commentant (cette fonctionnalité sera ajoutée dans une prochaine version)
- Les utilisateurs invités ne peuvent pas utiliser des abonnements (cette fonctionnalité sera ajoutée dans une prochaine version)
- Les utilisateurs invités qui utilisent cette fonctionnalité doivent disposer d’un compte professionnel ou scolaire. Les utilisateurs invités à l’aide de comptes personnels rencontrent des limitations plus en raison de restrictions de connexion.



## <a name="governance"></a>Governance

### <a name="additional-azure-ad-settings-that-affect-experiences-in-power-bi-related-to-azure-ad-b2b"></a>Autres paramètres Azure AD qui affectent des expériences dans Power BI liés à Azure AD B2B

Quand vous utilisez Azure AD B2B de partage, l’administrateur Azure Active Directory détermine les aspects de l’expérience de l’utilisateur externe. Ceux-ci sont contrôlées sur la page de paramètres de collaboration externe dans les paramètres Azure Active Directory pour votre client.

Plus d’informations sur les paramètres sont disponibles ici :

[https://docs.microsoft.com/azure/active-directory/b2b/delegate-invitations](https://docs.microsoft.com/azure/active-directory/b2b/delegate-invitations)

> [!NOTE]
> Par défaut, les autorisations d’utilisateurs invités sont limitées option est définie sur Oui, pour les utilisateurs invités au sein de Power BI ont limité des expériences en particulier entourer de partage où le sélecteur de personnes des interfaces utilisateur ne fonctionnent pas pour ces utilisateurs. Il est important de travailler avec votre administrateur Azure AD pour le définir sur non, comme indiqué ci-dessous pour garantir une bonne experience.* *

![Paramètres de collaboration externes](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_43.png)


### <a name="control-guest-invites"></a>Invitations d’invités de contrôle

Les administrateurs Power BI peuvent contrôler le partage externe uniquement pour Power BI en visitant le portail d’administration Power BI. Mais les administrateurs clients peuvent également contrôler le partage externe avec différentes stratégies d’Azure AD.  Ces stratégies permettent aux administrateurs de locataire

- Désactiver les invitations par les utilisateurs finaux
- Seuls les administrateurs et les utilisateurs du rôle Inviteur d’invités peuvent inviter
- Administrateurs, le rôle Inviteur d’invités et les membres peuvent inviter
- Tous les utilisateurs, y compris les invités, peuvent inviter

Vous trouverez plus d’informations sur ces stratégies dans [déléguer des invitations pour Azure Active Directory B2B collaboration](https://docs.microsoft.com/azure/active-directory/active-directory-b2b-delegate-invitations).

Toutes les actions de Power BI par des utilisateurs externes sont également [auditée dans notre portail audit](https://powerbi.microsoft.com/documentation/powerbi-admin-auditing/).

### <a name="conditional-access-policies-for-guest-users"></a>Stratégies d’accès conditionnel pour les utilisateurs invités

Contoso peut appliquer des stratégies d’accès conditionnel pour les utilisateurs invités qui accèdent au contenu à partir du locataire Contoso. Vous trouverez des instructions détaillées dans [l’accès conditionnel pour les utilisateurs de collaboration B2B](https://docs.microsoft.com/azure/active-directory/active-directory-b2b-mfa-instructions).

## <a name="common-alternative-approaches"></a>Autres approches courantes

Bien que Azure AD B2B facilite le partage des données et les rapports entre plusieurs organisations, il existe plusieurs autres approches qui sont couramment utilisés et peuvent être supérieures dans certains cas.

### <a name="alternative-option-1-create-duplicate-identities-for-partner-users"></a>Autre Option 1 : Créer des utilisateurs des identités en double pour le partenaire

Avec cette option, Contoso devait créer manuellement des identités en double pour chaque utilisateur partenaire dans le locataire Contoso, comme illustré dans l’image suivante. Ensuite dans Power BI, Contoso peut partager aux identités affectées les rapports appropriés, les tableaux de bord ou les applications.

![Définition des noms et les mappages appropriés](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_44.png)

Raisons de choisir cette solution :

- Étant donné que l’identité de l’utilisateur est contrôlée par votre organisation, les consignées service comme l’e-mail, SharePoint, etc. sont également dans le contrôle de votre organisation. Vos administrateurs informatiques peuvent réinitialiser les mots de passe, désactiver l’accès aux comptes ou auditer les activités dans ces services.
- Les utilisateurs qui utilisent des comptes personnels pour leur activité sont souvent limités d’accéder à certains services peuvent donc besoin d’un compte d’organisation.
- Certains services fonctionnent uniquement sur les utilisateurs de votre organisation. Par exemple, à l’aide d’Intune pour gérer le contenu sur les appareils personnels/mobiles des utilisateurs externes à l’aide d’Azure B2B peut-être pas possible.

Raisons de ne pas choisir cette solution :

- Les utilisateurs d’organisations partenaires doivent n’oubliez pas les deux ensembles d’informations d’identification : un pour accéder au contenu de leur propre organisation et l’autre pour accéder au contenu à partir de Contoso. Cette opération est laborieuse pour ces utilisateurs invités et de nombreux utilisateurs invités sont perturbés par cette expérience.
- Contoso doit acheter et attribuer des licences par utilisateur à ces utilisateurs. Si un utilisateur doit recevoir des messages électroniques ou utiliser les applications office, dont ils ont besoin les licences appropriées, notamment Power BI Pro pour modifier et partager du contenu dans Power BI.
- Contoso souhaiterez appliquer d’autorisation plus stricte et des stratégies de gouvernance pour les utilisateurs externes par rapport aux utilisateurs internes. Pour ce faire, Contoso doit créer une nomenclature en interne pour les utilisateurs externes et tous les utilisateurs de Contoso doivent être informés de cette nomenclature.
- Lorsque l’utilisateur quitte l’organisation, ils continuent à avoir accès à des ressources de Contoso jusqu'à ce que l’administrateur de Contoso supprime manuellement leur compte
- Les administrateurs de Contoso ont gérer l’identité de l’invité, notamment la création, de réinitialisations de mot de passe, etc.

### <a name="alternative-option-2-create-a-custom-power-bi-embedded-application-using-custom-authentication"></a>Autre Option 2 : Créer une application Power BI Embedded personnalisée à l’aide de l’authentification personnalisée

Une autre option pour Contoso doit créer sa propre application personnalisée, Power BI embedded avec l’authentification personnalisée ([« Application possède les données »](https://docs.microsoft.com/power-bi/developer/embed-sample-for-customers)). Bien que de nombreuses organisations n’ont pas de temps ou ressources pour créer une application personnalisée pour Power BI de distribuer du contenu à leurs partenaires externes, pour certaines organisations est la meilleure approche et mérite une réflexion approfondie.

Souvent, les organisations ont des portails de partenaire existant qui centralisent accès à toutes les ressources de l’organisation pour les partenaires, assurent l’isolement des ressources internes de l’organisation et fournissent une expérience simplifiée pour les partenaires prendre en charge de nombreux partenaires et les utilisateurs individuels.

![Plusieurs portails des partenaires](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_45.png)

Dans l’exemple ci-dessus, les utilisateurs à partir de chaque connexion fournisseur au portail des partenaires de Contoso qui utilise AAD comme fournisseur d’identité. Il peut utiliser AAD B2B, B2C d’Azure, les identités natives ou fédérer avec un nombre quelconque d’autres fournisseurs d’identité. L’utilisateur serait se connecter et accéder à une build de portail du partenaire à l’aide de l’application Web Azure ou une infrastructure similaire.

Dans l’application web, les rapports Power BI sont incorporés à partir d’un déploiement de Power BI Embedded. L’application web serait rationaliser l’accès pour les rapports et tous les services associés dans une expérience cohérente visant à faciliter pour les fournisseurs d’interagir avec Contoso. Cet environnement portail serait isolé à partir d’AAD interne Contoso et l’environnement de Contoso interne Power BI pour vous assurer de fournisseurs n’a pas pu accéder à ces ressources. En règle générale, les données seraient être stockées dans un entrepôt de données partenaire distinct pour garantir l’isolation des données. Cette isolation présente des avantages, car elle limite le nombre d’utilisateurs externes d’accéder directement aux données de votre organisation, limiter les données peut potentiellement être disponibles pour l’utilisateur externe et en limitant le partage accidentel avec des utilisateurs externes.

À l’aide de Power BI Embedded, le portail peut tirer parti de la gestion des licences avantageux, à l’aide du jeton d’application ou utilisateur principal plus de capacité premium achetés dans un modèle Azure, ce qui simplifie les problèmes sur l’attribution des licences aux utilisateurs finaux et pouvez monter/descendre en fonction on attendu utilisation. Le portail peut offrir une globale de haute qualité et une expérience cohérente dans la mesure où les partenaires accéder à un portail unique conçu avec tous les besoins d’un partenaire à l’esprit. Enfin, étant donné que Power BI Embedded en solutions sont généralement conçues pour être architecture mutualisée, elle facilite garantir l’isolation entre organisations partenaires.

Raisons de choisir cette solution :

- Augmente plus facile à gérer en tant que le nombre d’organisations partenaires. Étant donné que les partenaires sont ajoutés à un répertoire séparé isolé à partir de l’annuaire de Contoso interne AAD, il simplifie ses droits de gouvernance et permet d’empêcher le partage accidentel de données internes pour les utilisateurs externes.
- Typique portails des partenaires sont hautement marque les expériences avec une expérience cohérente entre les partenaires et simplifiés pour répondre aux besoins des partenaires classiques. Contoso peut par conséquent offrir une meilleure expérience globale aux partenaires en intégrant tous les services requis dans un portail unique.
- Les coûts pour les scénarios avancés tels que le contenu d’édition dans le Power BI Embedded est couvert par Azure des licences acheté Power BI Premium et ne nécessitent pas d’attribution de licences Power BI Pro aux utilisateurs.
- Fournit une meilleure isolation entre les partenaires si conçus sous forme d’une solution mutualisée.
- Le portail partenaire inclut souvent d’autres outils pour le partenaire au-delà des rapports Power BI, les tableaux de bord et les applications.

Raisons de ne pas choisir cette solution :

- Des efforts considérables sont nécessaire pour créer, exploiter et maintenir cet un portail rend un investissement significatif dans le temps et de ressources.
- Temps de la solution est beaucoup plus longue que l’utilisation du partage B2B depuis une planification soignée et l’exécution sur plusieurs flux de travail est nécessaire.
- Lorsqu’il existe un plus petit nombre de partenaires de l’effort requis pour cette solution est probablement trop élevé pour justifier.
- La collaboration avec le partage ad hoc est le scénario principal rencontré par votre organisation.
- Les rapports et les tableaux de bord est différents pour chaque partenaire. Cette alternative présente la gestion au-delà de surcharge simplement partagent directement avec des partenaires.



## <a name="faq"></a>FORUM AUX QUESTIONS

**Contoso peut envoyer une invitation est remboursée automatiquement, afin que l’utilisateur est simplement « prêt » ? Ou l’utilisateur dispose toujours cliquer sur l’URL d’échange ?**

L’utilisateur final doit toujours cliquer sur l’expérience du consentement avant qu’ils peuvent accéder au contenu.

Si vous invitez serez des nombreux utilisateurs invités, nous vous recommandons de déléguer cela à partir de vos administrateurs core Azure AD par [Ajout d’un utilisateur au rôle inviteur d’invités dans l’organisation de ressource](https://docs.microsoft.com/azure/active-directory/active-directory-b2b-add-guest-to-role). Cet utilisateur peut inviter d’autres utilisateurs dans l’organisation partenaire à l’aide de l’interface utilisateur de connexion, les scripts PowerShell, ou des API. Cela réduit la charge administrative sur vos administrateurs Azure AD pour inviter ou renvoyer des invitations aux utilisateurs de l’organisation partenaire.

**Contoso peut forcer l’authentification multifacteur pour les utilisateurs invités si ses partenaires n’ont pas l’authentification multifacteur ?**

Oui. Pour plus d’informations, consultez [l’accès conditionnel pour les utilisateurs de collaboration B2B](https://docs.microsoft.com/azure/active-directory/active-directory-b2b-mfa-instructions).

**Comment B2B collaboration fonctionne lorsque le partenaire invité est en utilisant la fédération pour ajouter leur propre authentification locale ?**

Si le partenaire a un locataire Azure AD qui est fédéré à l’infrastructure d’authentification en local, sur site-session unique (SSO) s’effectue automatiquement. Si le partenaire n’a pas un locataire Azure AD, un compte Azure AD peut être créé pour les nouveaux utilisateurs.

**Puis-je inviter des utilisateurs avec des comptes de messagerie consommateur ?**

Inviter des utilisateurs avec les comptes de messagerie de consommateur est pris en charge dans Power BI. Cela inclut des domaines tels que hotmail.com, outlook.com et gmail.com. Toutefois, ces utilisateurs peuvent rencontrer des limitations au-delà de ce que les utilisateurs avec des ou comptes scolaires rencontrent.
