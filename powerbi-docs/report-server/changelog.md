---
title: Journal des modifications pour Power BI Report Server
description: Ce journal des modifications a trait à Power BI Report Server. Il répertorie les éléments nouveaux et les corrections de bogues introduits dans chaque version officielle publiée.
author: jtarquino
manager: kfile
ms.reviewer: maggies
ms.service: powerbi
ms.component: powerbi-report-server
ms.topic: conceptual
ms.date: 03/31/2018
ms.author: jtarquino
ms.openlocfilehash: e0f90ccade44960cf24fd133b4caf46280b4a511
ms.sourcegitcommit: 80d6b45eb84243e801b60b9038b9bff77c30d5c8
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34482127"
---
# <a name="changelog-for-power-bi-report-server"></a>Journal des modifications pour Power BI Report Server

Ce journal des modifications a trait à Power BI Report Server. Il répertorie les éléments nouveaux et les corrections de bogues introduits dans chaque version officielle publiée.

Pour plus d’informations sur les nouvelles fonctionnalités, voir [Nouveautés dans Power BI Report Server](whats-new.md). 

## <a name="march-2018"></a>Mars 2018
- **Power BI Report Server**
    - *Version 1.2.6690.34729 (Build 15.0.2.402), publiée le 27 mars 2018*
        - Corrections de bogues
            - Activer la migration des catalogues SQL Server Reporting Services 2017
            - Pour les rapports Power BI (PBIX)
                - Les rapports peuvent être actualisés lorsqu’un serveur est configuré pour utiliser l’authentification personnalisée
                - La modification des propriétés d’un rapport ne réinitialise pas les informations d’identification de la source de données
            - Pour les rapports paginés (RDL)
                - L’utilisation de `Lookup()` ou de fonctions dérivées telles que `LookupSet()` et `MultiLookup()` dans RDL Expresssions ne génère plus de résultats dans `#Error`
                - Les rapports liés respectent le format de page du rapport cible lors de l’impression
                - Des abonnements peuvent être créés pour les rapports liés qui utilisent des paramètres en cascade
                - Les paramètres par défaut à valeurs multiples peuvent être modifiés lors de l’utilisation de IE11
                - Les options de remise d’abonnement piloté par les données sont modifiables
                - Les abonnements peuvent être affichés et modifiés pendant leur exécution
                - La définition des informations d’identification de la source de données ne supprime pas les chaînes de connexion basées sur une expression
            - Pour les indicateurs de performance clés
                - Les courbes de tendance sont actualisées lors de la mise à jour des données
            - Améliorations de la stabilité globale

    - *Version 1.2.6660.39920 (Build 15.0.2.389), publiée le 28 mars 2018*
        - Corrections de bogues
            - Pour les Rapports Power BI (PBIX), le correctif pour Exporter les données ne fonctionne pas à partir de Power BI Visuals
            - Pour les Rapports Power BI (PBIX), le correctif pour les filtres URL ne fonctionne pas
            - Pour les Rapports paginés (RDL), le correctif pour les images qui ne s’affichent pas correctement dans IE11 après la mise à niveau vers Power BI Report Server version publiée en mars

    - *Version 1.2.6648.38132 (Build 15.0.2.378), publiée le 19 mars 2018*
        - Mises à jour de sécurité
        - Améliorations de l’accessibilité
        - Corrections de bogues
            - Pour les rapports paginés (RDL), correctif pour la visibilité des paramètres dans un rapport lié qui est rétabli après la modification de ses propriétés
            - Correctif pour le portail web avec l’authentification de formulaires personnalisés qui ignore le cookie d’expiration décalée
            - Correctif pour l’exportation vers Word qui crée une hauteur de ligne inégale si le contenu de la ligne est vide
            - Pour les rapports paginés (RDL), correctif pour la chaîne de connexion basée sur une expression qui est supprimée quand vous changez les informations d’identification pour la source de données
            - Correctif pour la possibilité d’utiliser des indicateurs de performance clés avec des valeurs texte
            - Pour les rapports paginés (RDL), correctif pour pouvoir assigner un nouveau jeu de données à un rapport paginé (RDL) existant
            - Autres correctifs de stabilité et de facilité d’utilisation

- **Power BI Desktop optimisé pour Power BI Report Server**
    - Version : 2.56.5023.1043 (mars 2018), Date de publication : 19 mars 2018
        - Contient les modifications nécessaires pour la connexion à Power BI Report Server (mars 2018)

## <a name="october-2017"></a>Octobre 2017

- **Power BI Report Server**
    - *Version 1.1.6582.41691 (Build 14.0.600.442), publiée le 10 janvier 2018*
        - Mises à jour de sécurité
        - Résolutions de bogues
            - Correctif pour Model.GetParameters retournant 400
            - Correctif permettant d’affecter des rapports paginés (RDL) existants à un jeu de données partagé
            - Correctif pour ExecutionNotFoundException lors de l’exportation d’un rapport avec différentes valeurs de paramètre au format PDF

    - *Version 1.1.6551.5155 (Build 14.0.600.438), publiée le 11 décembre 2017*
        - Résolutions de bogues
            - Échec de l’enregistrement des données après actualisation pour certains rapports Power BI Desktop.

    - *Version 1.1.6530.30789 (Build 14.0.600.437), publiée le 17 novembre 2017*
        - Résolutions de bogues
            - Correctif pour les scénarios d’authentification de base 
            - Correctif servant à corriger le fait que les jours de la semaine n’étaient pas sélectionnables sur la page de planification pour Abonnements, Plans d’actualisation du cache et Captures instantanées d'historique sur le portail
            - Pour les rapports paginés (RDL), correctif corrigeant le problème suivant : quand des expressions de la zone de texte ont la propriété CanGrow définie sur false, aucune valeur ne s’affiche et les polices et couleurs sont erronées
            - Pour les rapports Power BI (PBIX), correctif corrigeant le problème suivant : l’ajout de légendes à un graphique en courbes restitue un visuel vide

    - *Version 1.1.6514.9163 (Build 14.0.600.434), publiée le 1e novembre 2017*
        - Résolutions de bogues
            - Correctif des problèmes de fiabilité de chargement pour les rapports PBIX de plus de 500 Mo
            - Résoudre le problème de chargement de données pour les rapports PBIX de plus de 1 Go

    - *Version 1.1.6513.3500 (Build 14.0.600.433), publiée le 31 octobre 2017*
        - Fonctionnalités
            - Prise en charge du modèle de données incorporée
            - Affichage de classeur Excel (avec l’intégration d’Office Online Server activée)
            - Actualisation des données planifiée (PBIX)
            - Prise en charge de requête directe
            - Prise en charge de fichiers volumineux (jusqu’à 2 Go)
            - API REST publique
            - Prise en charge du jeu de données partagé dans Power BI Desktop (via oData)
            - Prise en charge du paramètre d’URL pour les fichiers PBIX
            - Améliorations de l’accessibilité

- **Power BI Desktop optimisé pour Power BI Report Server**
    - *Version : 2.51.4885.3981 (octobre 2017), publiée le 10 avril 2018*
        - Mises à jour de sécurité

    - *Version : 2.51.4885.2501 (octobre 2017), publiée le 10 janvier 2018*
        - Mises à jour de sécurité

    - *Version : 2.51.4885.1423 (octobre 2017), publiée le 17 novembre 2017*
        - Résolutions de bogues
            - Correctif du problème suivant : la version 32 bits de Power BI Desktop ne parvient pas à s’exécuter sur les systèmes d’exploitation x86
            - Pour les rapports Power BI (PBIX), correctif de l’affichage du quadrillage de l’axe x
            - Autres correctifs mineurs de bogues

    - *Version : 2.51.4885.1041 (octobre 2017), publiée le 31 octobre 2017*
        - Fonctionnalités
            - Contient les modifications requises pour la connexion avec Power BI Report Server (octobre 2017)

## <a name="june-2017"></a>Juin 2017

- **Power BI Report Server**
    - *Version 14.0.600.309, publiée le 10 janvier 2018*
        - Mises à jour de sécurité

    - *Build 14.0.600.305, publiée le 19 septembre 2017*  
        - Résolutions de bogues
            - Mise à jour vers la dernière version [du contrôle web Bing Cartes](https://msdn.microsoft.com/library/mt712542.aspx)

    - *Build 14.0.600.301, publiée le 11 juillet 2017*
        - Résolutions de bogues
            - La balise `{{UserId}}` est remplacée par des informations d’identification stockées plutôt que par l’utilisateur qui exécute le rapport dans Rapports Power BI
            - Échec du rendu de certaines images dans des rapports de Power BI Report Server
            - Impossibilité de modifier le nom d’un rapport Power BI dans Power BI Report Server
            - Impossibilité de charger des éléments visuels personnalisés dans l’application Power BI Mobile (nécessite la réinstallation de l’application mobile pour effacer le cache local)

    - *Build 14.0.600.271, publiée le 12 juin 2017*
        - Publication initiale de Power BI Report Server

- **Power BI Desktop optimisé pour Power BI Report Server**
    - *Version : 2.47.4766.4901 (juin 2017), publiée le 10 janvier 2018*
        - Mises à jour de sécurité

## <a name="next-steps"></a>Étapes suivantes

[Présentation de Power BI Report Server](get-started.md)
[Vue d’ensemble de l’administrateur](admin-handbook-overview.md)  
[Installer Power BI Report Server](install-report-server.md)  
[Installer le Générateur de rapports](https://docs.microsoft.com/sql/reporting-services/install-windows/install-report-builder)  
[Télécharger SQL Server Data Tools (SSDT)](http://go.microsoft.com/fwlink/?LinkID=616714)

D’autres questions ? [Essayez d’interroger la communauté Power BI](https://community.powerbi.com/)
