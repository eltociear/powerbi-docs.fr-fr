---
title: Définir les informations de contact pour les rapports et les tableaux de bord
description: Découvrez comment définir les informations de contact pour les rapports et les tableaux de bord.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-reports-dashboards
ms.topic: how-to
ms.date: 10/08/2019
LocalizationGroup: Common tasks
ms.openlocfilehash: 4518ac8eff4b4f52ab2eeb715c0c460bb478678f
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2020
ms.locfileid: "96388330"
---
# <a name="set-contact-information-for-reports-and-dashboards-in-the-power-bi-service"></a>Définir les informations de contact pour les rapports et les tableaux de bord dans le service Power BI
Cet article vous explique comment définir les informations de contact d'un tableau de bord ou d'un rapport dans le service Power BI.

> [!NOTE]
> Les informations de contact peuvent être définies pour les éléments d'un espace de travail classique ou nouveau. Vous ne pouvez pas définir les informations de contact pour les éléments de votre espace Mon espace de travail. La carte d'information s'affiche lorsque vous ouvrez un rapport ou un tableau de bord dans la [nouvelle apparence](../consumer/service-new-look.md).

Vous pouvez ajouter plusieurs utilisateurs ou groupes au contact d'un élément. Ce peut être :
* Une personne
* Un groupe Microsoft 365
* Un groupe de sécurité à extension messagerie
* Une liste de distribution

Par défaut, la personne qui crée un rapport ou tableau de bord est la personne à contacter. Si vous définissez une valeur, elle remplace la valeur par défaut. Vous pouvez bien sûr supprimer toutes les personnes ou tous les groupes de la liste de contacts. Dans ce cas, pour les espaces de travail classiques, le groupe Microsoft 365 pour l’espace de travail apparaît. Pour les espaces de travail de la nouvelle apparence, la liste de [contacts de l'espace de travail](../collaborate-share/service-create-the-new-workspaces.md#create-a-contact-list) sera utilisée. Si la liste des contacts de l'espace de travail n'est pas définie, les administrateurs de l'espace de travail sont affichés.

Les informations de contact sont affichées aux personnes qui consultent l'élément. 

 ![contact du rapport de service](media/service-item-contact/service-report-contact.png)

Lorsque vous cliquez sur la liste de contacts, un e-mail est créé et vous permet de poser des questions ou d’obtenir de l'aide. 

 ![e-mail du contact de service](media/service-item-contact/service-contact-email.png)
 
Les informations de la liste de contacts sont également utilisées à d'autres endroits. Par exemple, il s’affiche dans certains scénarios d'erreur dans la boîte de dialogue de l’erreur. Les e-mails automatisés liés à l'élément, notamment les demandes d'accès, sont envoyés à la liste de contacts. 

> [!NOTE]
> Lors de la publication d'une application, les informations de contact sur les éléments individuels sont définies sur la personne qui a publié ou mis à jour l'application. Vous pouvez définir l'URL de support de l'application pour permettre aux utilisateurs de l'application d’obtenir l'aide dont ils ont besoin.

## <a name="set-contact-information-for-a-report"></a>Définir les informations de contact pour un rapport
1. Dans votre espace de travail, sélectionnez l’onglet **Rapports**.
2. Localisez le rapport souhaité, puis sélectionnez l'icône **Paramètres**.
3. Localisez le champ d’entrée **Contact**, puis définissez une valeur.

     ![paramètre du contact du rapport de service](media/service-item-contact/service-report-contact-setting.png)

## <a name="set-contact-information-for-a-dashboard"></a>Définir les informations de contact pour un tableau de bord
1. Dans votre espace de travail, sélectionnez l’onglet **Tableaux de bord**.
2. Localisez le tableau de bord souhaité, puis sélectionnez l'icône **Paramètres**
3. Localisez le champ d’entrée **Contact**, puis définissez une valeur.

     ![paramètre de contact du tableau de bord du service](media/service-item-contact/service-dashboard-contact-setting.png)

## <a name="limitations-and-considerations"></a>Considérations et limitations
* Le contact est automatiquement défini pour les nouveaux éléments créés dans le service Power BI. Les éléments existants afficheront l'espace de travail par défaut.
* Vous pouvez définir n'importe quel utilisateur ou groupe dans la liste de contacts, mais ils n'auront pas automatiquement l'autorisation d'accéder à l'élément. Utilisez le partage ou donnez à l'utilisateur qui en a besoin l'accès à l'espace de travail en lui attribuant un rôle. 
* La liste de contacts au niveau élément ne fait pas l’objet d’une transmission de type push dans les applications lors de leur publication. La nouvelle expérience de navigation dans les applications comporte une URL de support configurable de façon à mieux gérer les commentaires d’un grand nombre d’utilisateurs.


## <a name="next-steps"></a>Étapes suivantes

D’autres questions ? [Posez vos questions à la communauté Power BI](https://community.powerbi.com/)
