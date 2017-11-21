---
title: Journal des modifications pour Power BI Report Server
description: "Ce journal des modifications a trait à Power BI Report Server. Il répertorie les éléments nouveaux et les corrections de bogues introduits dans chaque version officielle publiée."
services: powerbi
documentationcenter: 
author: jtarquino
manager: jonhp
backup: asaxton
editor: 
tags: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 09/19/2017
ms.author: jaimeta
ms.openlocfilehash: 9fdc757fca252c5c35d308dcd0b326098683b159
ms.sourcegitcommit: 99cc3b9cb615c2957dde6ca908a51238f129cebb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/13/2017
---
# <a name="changelog-for-power-bi-report-server"></a>Journal des modifications pour Power BI Report Server
Ce journal des modifications a trait à Power BI Report Server. Il répertorie les éléments nouveaux et les corrections de bogues introduits dans chaque version officielle publiée.

Pour plus d’informations sur les nouvelles fonctionnalités, voir [Nouveautés dans Power BI Report Server](whats-new.md).

## <a name="october-2017"></a>Octobre 2017
* **Power BI Report Server**
  * *Version 1.1.6514.9163 (Build 14.0.600.434), publiée le 1e novembre 2017*
    * Corrections de bogues
      * Résoudre des problèmes de fiabilité de chargement pour les rapports PBIX de plus de 500 Mo
      * Résoudre le problème de chargement de données pour les rapports PBIX de plus de 1 Go
  * *Version 1.1.6513.3500 (Build 14.0.600.433), publiée le 31 octobre 2017*
    * Fonctionnalités
      * Prise en charge du modèle de données incorporée
      * Affichage de classeur Excel (avec l’intégration d’Office Online Server activée)
      * Actualisation des données planifiée (PBIX)
      * Prise en charge de requête directe
      * Prise en charge de fichiers volumineux (jusqu’à 2 Go)
      * API REST publique
        * Prise en charge du jeu de données partagé dans Power BI Desktop (via oData)
      * Prise en charge du paramètre d’URL pour les fichiers PBIX
      * Améliorations de l’accessibilité
* **Power BI Desktop optimisé pour Power BI Report Server**
  * *Version : 2.51.4885.1041 (octobre 2017), publiée le 31 octobre 2017*
    * Contient les modifications requises pour la connexion avec Power BI Report Server (octobre 2017)

## <a name="june-2017"></a>Juin 2017
* **Power BI Report Server**
  
  * *Build 14.0.600.305, publiée le 19 septembre 2017*  
    
    * Corrections de bogues
      * Mise à jour vers la dernière version [du contrôle web Bing Cartes](https://msdn.microsoft.com/library/mt712542.aspx)
  * *Build 14.0.600.301, publiée le 11 juillet 2017*
    
    * Corrections de bogues
      * La balise {{UserId}} est remplacée par des informations d’identification stockées plutôt que par l’utilisateur qui exécute le rapport dans Rapports Power BI
      * Échec d’affichage de certaines images dans les rapports de Power BI Report Server
      * Impossibilité de modifier le nom d’un rapport Power BI dans Power BI Report Server
      * Impossibilité de charger des éléments visuels personnalisés dans l’application Power BI Mobile (nécessite la réinstallation de l’application mobile pour effacer le cache local)
  * *Build 14.0.600.271, publiée le 12 juin 2017*
    
    * Publication initiale de Power BI Report Server

## <a name="next-steps"></a>Étapes suivantes
[Manuel de l’utilisateur](user-handbook-overview.md)  
[Manuel de l’administrateur](admin-handbook-overview.md)  
[Démarrage rapide : installer Power BI Report Server](quickstart-install-report-server.md)  
[Installer le Générateur de rapports](https://docs.microsoft.com/sql/reporting-services/install-windows/install-report-builder)  
[Télécharger SQL Server Data Tools (SSDT)](http://go.microsoft.com/fwlink/?LinkID=616714)

D’autres questions ? [Essayez d’interroger la communauté Power BI](https://community.powerbi.com/)

