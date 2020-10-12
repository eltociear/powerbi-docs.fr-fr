---
title: Résoudre les problèmes de sous-rapports dans les rapports paginés Power BI
description: Découvrez les solutions aux problèmes courants liés à l’utilisation de sous-rapports, qui sont des éléments de rapport à l’intérieur d’un rapport paginé.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: report-builder
ms.topic: troubleshooting
ms.date: 04/29/2020
ms.openlocfilehash: 6a0e90036b759c409a9f5b3e994571c2a0eb510c
ms.sourcegitcommit: 6bc66f9c0fac132e004d096cfdcc191a04549683
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/06/2020
ms.locfileid: "91747502"
---
# <a name="troubleshoot-subreports-in-power-bi-paginated-reports"></a>Résoudre les problèmes de sous-rapports dans les rapports paginés Power BI

Vous pouvez parfois obtenir un résultat inattendu lors de l’utilisation de rapports paginés, ou la fonctionnalité ne fonctionne pas comme prévu. Cet article fournit des solutions pour les problèmes courants lors de l’utilisation de sous-rapports. Un *sous-rapport* est un élément de rapport qui affiche un autre rapport à l'intérieur du corps d'un rapport paginé principal. Voir [Sous-rapports dans les rapports paginés Power BI](subreports.md) pour plus d’informations.

## <a name="subreport-couldnt-be-found"></a>Le sous-rapport est introuvable

**Description :** Le sous-rapport ne s’affiche pas. Au lieu de cela, un message d’erreur s’affiche.

### <a name="message"></a>Message

« Le sous-rapport 'Subreport1' est introuvable à l’emplacement spécifié 'CustomerDetails'. Vérifiez qu’il a été publié et que le nom est correct. »

### <a name="possible-reasons"></a>Causes possibles

- Un sous-rapport portant le nom spécifié n’existe pas dans le même espace de travail ou dans la même application que le rapport principal.
- L’utilisateur n’a pas accès au sous-rapport.
- Le nombre de sous-rapports dans le rapport principal a atteint la limite des sous-rapports (50 sous-rapports).

### <a name="troubleshooting-steps"></a>Étapes de dépannage

**Dans un espace de travail**

- Vérifiez que le rapport portant le nom figurant dans le message d’erreur existe. Le nom ne respecte pas la casse.

**Dans une application**

- Vérifiez que le rapport portant le nom figurant dans le message d’erreur existe dans l’application. Contactez l’auteur de l’application pour obtenir de l’aide.

**Si le rapport est partagé**

1. Vérifiez que le rapport portant le nom figurant dans le message d’erreur est partagé avec vous.
2. Si le rapport existe, vérifiez que le nom du propriétaire est identique pour le rapport principal et le sous-rapport. Puis contactez le propriétaire du rapport principal afin de lui communiquer ces informations.

## <a name="subreport-renders-with-unexpected-content"></a>Le sous-rapport affiche un contenu inattendu

### <a name="possible-reason"></a>Raison possible

Power BI permet aux utilisateurs d’avoir plusieurs rapports portant le même nom dans le même espace de travail

### <a name="troubleshooting-steps-for-report-authors"></a>Étapes de dépannage (pour les auteurs de rapport)

1. Ouvrez le rapport principal dans Power BI Report Builder et déterminez le nom du sous-rapport.
2. Recherchez les rapports portant le même nom dans l’espace de travail.
3. Recherchez le rapport attendu et renommez les autres rapports.

**Pour les non-auteurs :** Contactez l’auteur.

## <a name="data-retrieval-fails"></a>La récupération des données échoue

**Description :** La récupération des données échoue lors de l’affichage du sous-rapport. Le sous-rapport ne s’affiche pas. Au lieu de cela, un message d’erreur s’affiche.

### <a name="message"></a>Message

« Échec de la récupération des données pour le sous-rapport, 'Subreport1', situé à l’emplacement suivant : 'InvoiceDetails'. Pour plus d'informations, consultez les fichiers journaux. »

### <a name="troubleshooting-steps"></a>Étapes de dépannage

Identiques aux étapes de dépannage générales pour les rapports avec des problèmes d’accès aux données.

## <a name="rendering-fails-unspecified-parameters"></a>L’affichage échoue : Paramètres non spécifiés

**Description :** L’affichage du sous-rapport échoue en raison de paramètres non spécifiés. Le sous-rapport comporte des paramètres obligatoires, mais le rapport principal ne les définit pas tous.

### <a name="message"></a>Message 
« Un ou plusieurs paramètres n'ont pas été spécifiés pour le sous-rapport, 'Subreport1', situé à l'emplacement suivant : 'SubreportAWithDS'."

### <a name="troubleshooting-steps-for-the-report-author"></a>Étapes de dépannage (pour l’auteur du rapport)

1. Ouvrez le rapport principal dans Power BI Report Builder.
2. Ouvrez le sous-rapport dans Power BI Report Builder.
3. Vérifiez que l’ensemble de paramètres passés dans l’élément du sous-rapport dans le rapport principal correspond à l’ensemble de paramètres du sous-rapport.

**Pour les non-auteurs :** Contactez l’auteur.

## <a name="rendering-fails-recursion-limit"></a>L’affichage échoue : Limite de récursivité

**Description :** L’affichage du sous-rapport échoue en raison de la limite de récursivité. Les sous-rapports ne peuvent pas être imbriqués au-delà de 20 niveaux.

### <a name="message"></a>Message

« Le rapport ou sous-rapport a un sous-rapport récursif, 'Subreport1', qui a dépassé la limite de récursivité maximale autorisée. »

### <a name="troubleshooting-steps-for-report-authors"></a>Étapes de dépannage (pour les auteurs de rapport)

- Réduisez l’imbrication.
- Modifiez la structure du rapport.

## <a name="other-errors"></a>Autres erreurs

**Description :** Erreurs qui ne figurent dans aucune des catégories précédentes.

### <a name="message"></a>Message

« Erreur : Impossible d'afficher le sous-rapport. »

### <a name="possible-reasons"></a>Causes possibles

- Plusieurs erreurs lors de l’affichage du sous-rapport, par exemple, incompatibilité des paramètres avec problèmes de récupération des données.
- Erreurs inattendues.

### <a name="troubleshooting-steps-for-report-authors"></a>Étapes de dépannage (pour les auteurs de rapport)

1. Vérifiez que le sous-rapport peut s’afficher directement.
2. Si le sous-rapport peut être affiché, vérifiez les paramètres du sous-rapport et du rapport principal.
3. Assurez-vous que le rapport principal ne comporte pas plus de 50 sous-rapports uniques et que le sous-rapport n’est pas imbriqué au-delà de 20 niveaux.
4. Si vous ne parvenez pas à résoudre le problème, contactez le support technique Power BI.

**Pour les non-auteurs :** Contactez l’auteur.

## <a name="next-steps"></a>Étapes suivantes

[Sous-rapports dans les rapports paginés Power BI](subreports.md)

[Afficher un rapport paginé dans le service Power BI](../consumer/paginated-reports-view-power-bi-service.md)

D’autres questions ? [Posez vos questions à la communauté Power BI](https://community.powerbi.com/)
