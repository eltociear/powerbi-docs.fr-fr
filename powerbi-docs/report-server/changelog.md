---
title: Journal des modifications pour Power BI Report Server
description: Ce journal des modifications a trait à Power BI Report Server. Il répertorie les éléments nouveaux et les corrections de bogues introduits dans chaque version officielle publiée.
ms.author: jaimeta
author: jtarquino
ms.reviewer: maggies
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.topic: conceptual
ms.date: 10/29/2020
ms.openlocfilehash: 3173108abe6082c199cbf6ff1229ca57fde31064
ms.sourcegitcommit: a5fa368abad54feb44a267fe26c383a731c7ec0d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93044779"
---
# <a name="change-log-for-power-bi-report-server"></a>Journal des modifications pour Power BI Report Server

Ce journal des modifications a trait à Power BI Report Server. Il répertorie les éléments nouveaux et les corrections de bogues introduits dans chaque version officielle publiée.

Pour plus d’informations sur les nouvelles fonctionnalités, consultez [Nouveautés dans Power BI Report Server](whats-new.md). 

## <a name="october-2020"></a>Octobre 2020
- **Power BI Report Server**
    - *Version : 1.9.7604.41261 (build 15.0.1104.239), Date de publication : 27 octobre 2020*
         - Fonctionnalités
            - Ajout de la prise en charge des métadonnées de jeu de données avancées dans Power BI Report Server.
            - Ajout de la possibilité de mettre à jour des connexions de rapports Power BI pour DirectQuery et de les actualiser (pour plus d’informations, consultez [Chaînes de connexion de source de données](./connect-data-source-apis.md)).
        - Mises à jour de sécurité
        - Corrections de bogues
            - Résolution du problème qui empêchait les utilisateurs de modifier les planifications d’actualisation des rapports Power BI.
            - Correction du message d’erreur équivoque qui s’affichait lorsque les utilisateurs géraient les rapports alors que les informations d’identification avaient expiré.
            - Correction du problème lié à l’exportation des rapports dont le nom comporte des points.
            - Résolution des problèmes de lecteur d’écran dans un tableau matriciel.
            - Correction du problème lors duquel les fichiers journaux étaient vides dans certains cas.
            - Correction du problème lié à la boîte de dialogue « Se connecter à Power BI »
            - Mise à jour du convertisseur MHTML pour utiliser un DOCTYPE HTML plus récent

- **Power BI Desktop optimisé pour Power BI Report Server**
   - *Version : 2.86.961.0 (octobre 2020), Date de publication : 27 octobre 2020* (nouvelle build et nouvelle version)
        - Contient les changements nécessaires pour la connexion à Power BI Report Server (octobre 2020)        
   
## <a name="may-2020"></a>Mai 2020
- **Power BI Report Server**
    - *Version : 1.8.7485.35104 (Build 15.0.1103.234), Date de publication : 30 juin 2020*
        - Corrections de bogues
            - Correction d’un problème dans les scénarios de scale-out où les rapports ne reflétaient pas immédiatement les modifications sur le serveur après le chargement.
    - *Version : 1.8.7468.41510 (Build 15.0.1103.232), Date de publication : 15 juin 2020*
        - Corrections de bogues
            - Correction d’un problème où les rapports ne reflétaient pas immédiatement les modifications sur le serveur après le chargement.
            - Correction d’un problème où l’actualisation échouait lorsque la correspondance approximative était utilisée pour fusionner les requêtes.
    - *Version : 1.8.7450.37410 (Build 15.0.1103.227), Date de publication : 27 mai 2020*
         - Fonctionnalités
            -  Ajout de la prise en charge de la personnalisation de la taille du pool de connexions du catalogue (pour plus d’informations, consultez [paramètre MaxCatalogConnectionPoolSizePerProcess](/sql/reporting-services/report-server/rsreportserver-config-configuration-file#bkmk_service)).
            -  Comportement amélioré lors de l’affichage d’un rapport pendant une opération d’actualisation.
        - Mises à jour de sécurité
        - Corrections de bogues
            - Correction de deux problèmes liés aux guillemets simples dans les noms des dossiers et des rapports.
            - Correction d’un problème lié au défilement horizontal avec certains navigateurs et la fonctionnalité Afficher les enregistrements.
            - Correction d’un problème où l’actualisation planifiée alors que le rapport est ouvert peut parfois entraîner des erreurs de schéma dans le modèle sous-jacent.
            - Correction d’un problème où le texte de remplacement pour l’exportation PDF n’était pas correctement encodé pour les caractères multioctets.
            - Correction d’un problème où les applications personnalisées exécutant LoadReport ne recevaient pas correctement une erreur TrustedHeader.
            - Correction d’un problème où une charge importante de l’actualisation planifiée pouvait entraîner l’échec des actualisations.
            - Correction d’un problème où les rapports étaient enregistrés à un emplacement incorrect si le nom du rapport correspondait au nom du dossier.
            - Correction de problèmes de tabulation dans l’Explorateur de documents.
            - Correction d’un problème lié à l’échec des abonnements pilotés par les données lors de l’utilisation de requêtes DAX.
            - Correction d’un problème dans l’accès aux URL provoquant la non-localisation des correspondances par FindString.
            - Correction d’un problème qui endommageait les sources de données incorporées quand des rapports étaient déplacés.
            - Correction d’un problème provoquant l’échec de l’actualisation planifiée pour certaines sources de données.
            - Ajout d’une vérification à la planification des rapports pour réduire les risques de demandes non valides.


- **Power BI Desktop optimisé pour Power BI Report Server**
   - *Version : 2.81.5831.1181 (mai 2020). Date de publication : 9 juin 2020*
        - Correctif de bogue
           -  Correctif pour les visuels de la Place de marché
   - *Version : 2.81.5831.941 (mai 2020). Date de publication : 27 mai 2020* (nouvelle build et nouvelle version)
        - Contient les modifications nécessaires pour la connexion à Power BI Report Server (mai 2020)        
   
## <a name="january-2020"></a>Janvier 2020
- **Power BI Report Server**
    - *Version : 1.6.7364.4075 (build 15.0.1102.777), date de publication : 2 mars 2020*
         - Résolutions de bogues
           -  Correctif pour les rapports de Power BI qui ne sont pas téléchargés pour certaines sources de données
           -  Correctif pour l’emplacement de téléchargement du lien de Power BI Report Server à partir du portail
           -  Correctif pour le rendu Excel de DynamicImageDPI
           -  Correctif des connexions Oracle utilisant une culture de thread incorrecte dans certains scénarios multiutilisateurs (pour plus d’informations, consultez [Documentation de UseInstalledUICulture](./connect-data-sources.md))
           -  Correctif pour la valeur par défaut CustomHeaders provoquant des échecs d’incorporation de rapports
           -  Correctif pour les noms de paramètres SQL générés de manière incorrecte dans certains cas
    - *Version : 1.6.7327.3007 (build 15.0.1102.759), date de publication : 23 janvier 2020*
         - Fonctionnalités
            -  Exportation vers Excel à partir de rapports Power BI.
           -  Prise en charge des jeux de données Power BI Premium pour les rapports paginés.
           -  Prise en charge d’AltText (texte de remplacement) pour les éléments de rapports paginés.
           -  Prise en charge des en-têtes personnalisés.
           -  Prise en charge d’Azure SQL Managed Instance comme catalogue.
           -  Chiffrement transparent de base de données pour le catalogue.
        - Mises à jour de sécurité
        - Corrections de bogues
            - Correction de l’accessibilité des lecteurs d’écran, de la génération de rapports et de la navigation au clavier.
            - Correction de l’enregistrement des titres de rapports sur plusieurs octets.
            - Correction de la journalisation détaillée qui affecte la fiabilité du serveur de rapports.
          - Correction permettant d’obtenir des données en direct dans les rapports Power BI sur mobile.
          - Correction de l’application de la mise en surbrillance sur plusieurs visuels dans l’exportation filtrée de rapports Power BI.
          - Correction de l’écriture des pieds de page lors de l’exportation vers Word avec expression de la visibilité des rapports paginés. 
     
- **Power BI Desktop optimisé pour Power BI Report Server**
    - *Version : 2.76.5678.1521 (janvier 2020), date de publication : 23 janvier 2020* (nouvelle build et nouvelle version)
        - Contient les changements nécessaires pour la connexion à Power BI Report Server (janvier 2020)        


## <a name="september-2019"></a>Septembre 2019
- **Power BI Report Server**
    - *Version : 1.6.7236.4246 (Build 15.0.1102.646), date de publication : 25 octobre 2019*
        - Mises à jour de sécurité
        - Corrections de bogues
            - Correctif pour .NET Framework 4.7 non installé.
            - Correctif pour les rapports paginés pour Teradata avec des paramètres à valeurs multiples avec l’erreur 110083.
            - Le correctif pour la valeur URLRoot ne fonctionne pas s’il existe plusieurs liaisons d’URL de service web et que l’une d’elles est https://+80/reportserver.
          - Correctif pour les valeurs de paramètre à valeurs multiples des rapports paginés apparaissant hors de la zone de rapport.
          
    - *Version : 1.6.7221.30698 (Build 15.0.1102.620), date de publication : 9 octobre 2019*
        - Corrections de bogues
            - Correction pour le visuel personnalisé de filtre de texte.
            - Correction des problèmes de performances des segments de liste déroulante.
            - Correction de suppression des informations d’identification personnelle de la télémétrie.
          - Correction pour que les URL ne respectent pas la casse.
          
    - *Version 1.6.7206.38019 (Build 15.0.1102.597), Publication : 26 septembre 2019*
        - Mises à jour de sécurité
        - Corrections de bogues
           - Rapports paginés
             - Correction des problèmes d’accessibilité rencontrés lors de l’utilisation d’Internet Explorer et de Microsoft Edge.
             - Correctif pour les problèmes de SAP HANA lors du test de la connexion.
             - Correctif pour les problèmes rencontrés lors de la spécification d’une liste d’adresses e-mail.
             - Correctif pour les rapports Power BI qui utilisent une source de données DirectQuery et l’authentification intégrée.
             - Correctif pour les rapports paginés à afficher avec des paramètres de filtre quand l’instantané est activé.
             - Correctif pour l’exécution en double des procédures stockées pendant l’exécution des rapports.
             - Correctif pour le compte de service par défaut auquel des autorisations de connexion à SQL Server sont accordées, quand le compte de service personnalisé est configuré pour exécuter Power BI Report Server.
             - Correctif pour l’accès aux modèles pendant l’actualisation dans le fuseau horaire japonais.
             - Correctif pour les modèles obsolètes quand une nouvelle version du rapport est chargée lors de l’actualisation.
             - Correctif pour les valeurs de paramètre qui contiennent le caractère « & ».
         - Programmabilité
             - API web mise à jour : /PowerBIReports({Id})/DataSources (PATCH) pour autoriser les mises à jour de la chaîne de connexion.
         
- **Power BI Desktop optimisé pour Power BI Report Server**
    - *Version : 2.73.5586.1501 (septembre 2019), date de publication : 25 octobre 2019*
        - Corrections de bogues
            - Correctif pour les données de télémétrie.
            
    - *Version : 2.73.5586.1241 (Septembre 2019), date de publication : 9 octobre 2019*
        - Corrections de bogues
            - Correction pour le visuel personnalisé de filtre de texte.
            - Correction des performances des segments de liste déroulante.
            - Correction de suppression des informations d’identification personnelle de la télémétrie.
            
    - *Version : 2.73.5586.821 (Septembre 2019), Publication : 26 septembre 2019* (nouvelle build et nouvelle version)
        - Contient les changements nécessaires pour la connexion à Power BI Report Server (septembre 2019)

    
## <a name="may-2019"></a>Mai 2019

- **Power BI Report Server**          
    - *Version 1.5.7074.36177 (Build 15.0.1102.371), date de publication : 21 mai 2019*
        - Résolutions de bogues
            - Rapports paginés
                - Correctif pour toujours activer l’incorporation des polices dans les PDF.
                - Correctif pour définir les cookies envoyés via le protocole HTTPS comme étant sécurisés
                - Correctif pour l’affichage de messages liés à des erreurs de script
                - Correction des problèmes d’affichage avec l’application Mobile sur les téléphones Android
                - Correctif pour le navigateur de temps de rapport mobile, afin d’afficher les bons numéros de semaine, quel que soit le début de l’année fiscale
                - Ajout de la propriété configurable 'RestrictedResourceMimeTypeForUpload' pour permettre aux administrateurs de spécifier les types mime interdits
         - Fonctionnalités
            - Ajout de la prise en charge des visuels approuvés dans PBIRS

- **Power BI Desktop optimisé pour Power BI Report Server**
    - *Version : 2.69.5467.1801 (mai 2019). Publication : 21 mai 2019*
        - Corrections de bogues
            - Correctif pour éviter d’entrer une nouvelle fois les informations d’identification lors du chargement de PBIX dans PBIRS
            - Correctifs pour l’ouverture des documents dont le nom comprend le caractère #
            - Ajout d’un lien de navigation arrière dans la fenêtre de sélection PBIRS
            - Correctif pour le mode Contraste élevé dans PBIRS pour l’affichage du bouton Précédent et des messages d’avertissement visuels.
            - Correctifs de l’interface utilisateur du volet Sélection et de la mise à l’échelle des canevas.

    - *Version : 2.69.5467.5201 (mai 2019). Publication : 30 juillet 2019*
        - Corrections de bogues
            - Correction de journalisation de télémétrie incorrecte

## <a name="january-2019"></a>Janvier 2019

- **Power BI Report Server**          
    - *Version 1.4.7024.16477 (Build 15.0.1102.299), Publication : 28 mars 2019*
        - Résolutions de bogues
            - Rapports Power BI
                - Résolution du problème des informations d’identification de base lors de l’utilisation d’une requête directe pour SAP Hana et SAP BW
                - Correction du problème aboutissant à l’échec d’actualisation des données de flux OData avec le message « Impossible de charger le fichier ou l’assembly 'Microsoft.OData.Core.NetFX35.V7 »

- **Power BI Report Server**            
    - *Version 1.4.6969.7395 (Build 15.0.1102.235), date de publication : 30 janvier 2019*
        - Résolutions de bogues
            - Rapports Power BI
                - Résolution du problème des informations d’identification de base lors de l’utilisation d’une requête directe
                - Correction des relations bidirectionnelles avec les filtres de sécurité de niveau ligne appliqués
                - Correction des données périmées après une actualisation de modèle dans un environnement de scale-out
                - Correction de la double barre de défilement pour la table/matrice sur Firefox 63+
                - Correction de la taille d’icône +/- dans Internet Explorer
            - Rapports paginés
                - Résolution du problème de mise à jour de l’utilisation d’une source de données partagée pour un rapport

    - *Version 1.4.6960.38798 (Build 15.0.1102.222), date de publication : 22 janvier 2019*
        - Fonctionnalités
            - Rapports Power BI 
                - Prise en charge de la sécurité au niveau des lignes
                - Développer et réduire les en-têtes de lignes d’une matrice
                - Faire des copier-coller d’un fichier .pbix à un autre
                - Guides d’alignement intelligents
                - Prise en charge du connecteur SAP BW 2.0
            - Administrateurs
                - Possibilité de limiter les extensions des ressources pouvant être chargées sur le serveur de rapports
                - Possibilité de limiter les schémas de lien hypertexte pris en charge
            - Programmabilité
                - Nouvelle API web : /PowerBIReports({Id})/DataModelRoles (GET)
                - Nouvelle API web : /PowerBIReports({Id})/DataModelRoleAssignments (GET & PUT)
                - Consulter [API REST Power BI Report Server](https://app.swaggerhub.com/apis/microsoft-rs/PBIRS/2.0) pour plus de détails
        - Résolutions de bogues
            - Vulnérabilité de l’injection de code HTML
            - Exporter au format PDF n’affiche pas le symbole Euro
            - L’enregistrement d’un mot de passe avec plusieurs sources de données dans les rapports Power BI invalide les mots de passe inchangés
            - Problèmes d’affichage des visuels dans l’application Power BI Mobile après une période d’inactivité

- **Power BI Desktop optimisé pour Power BI Report Server**
    - *Version : 2.65.5313.1562 (janvier 2019), date de publication : 30 janvier 2019*
        - Les icônes de raccourci et épinglées restent après la désinstallation de Power BI Report Server
        - Correction de l’épinglage de Power BI Report Server dans le menu Démarrer qui donnait du texte noir sur une icône noire

    - *Version : 2.65.5313.1421 (janvier 2019), date de publication : 22 janvier 2019* (nouvelle build et nouvelle version)
        - Contient les changements nécessaires pour la connexion à Power BI Report Server (janvier 2019) 
    - *Version : 2.65.5313.5141 (janvier 2019), date de publication : 31 juillet 2019* (nouvelle build et nouvelle version)
        - Corrections de bogues
            - Correction de journalisation de télémétrie incorrecte

## <a name="august-2018"></a>Août 2018

- **Power BI Report Server**
    - *Version 1.3.6816.37243 (Build 15.0.2.557), publiée : 30 août 2018*
        - Corrections de bogues
            - Correction d’un problème qui survenait lorsque le serveur était mis à niveau à partir des versions antérieures de PBI Report Server et qu’une redirection de liaison n’était pas mise à jour. Les clients voyaient ce message :      
            *`
            Failed to load expression host assembly. Details: Could not load file or assembly 'Microsoft.ReportingServices.ProcessingObjectModel, Version=2018.7.0.0, Culture=neutral, PublicKeyToken=89845dcd8080cc91' or one of its dependencies. The located assembly's manifest definition does not match the assembly reference. (Exception from HRESULT: 0x80131040) (rsErrorLoadingExprHostAssembly)
             `*
             
            - Le bogue de transparence de l’étiquette de données a été corrigé.
            
    - *Version 1.3.6801.38816 (Build 15.0.2.540), publiée : 15 août 2018*
        - Fonctionnalités
            - La prise en charge de DirectQuery avec authentification unique SAP HANA avec Kerberos est désormais disponible pour les rapports Power BI
            - API des visuels personnalisés livrée avec la version - version 1.13.0
            - Les visuels Power BI utiliseront comme solution de repli une version antérieure compatible avec la version actuelle de l’API du serveur (si elle est disponible)

- **Power BI Desktop optimisé pour Power BI Report Server**
    - *Version : 2.61.5192.641 (August 2018), publiée : 15 août 2018*
        - Contient les modifications nécessaires pour la connexion à Power BI Report Server (août 2018)         
    - *Version : 2.61.5192.7701 (août 2018), publiée : 8 août 2019* (nouvelle build et nouvelle version)
        - Corrections de bogues
            - Correction de journalisation de télémétrie incorrecte
            
## <a name="march-2018"></a>Mars 2018

- **Power BI Report Server**
    - *Version 1.2.6690.34729 (Build 15.0.2.402), publiée : 27 avril 2018*
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

    - *Version 1.2.6660.39920 (Build 15.0.2.389), publiée : 28 mars 2018*
        - Corrections de bogues
            - Pour les Rapports Power BI (PBIX), le correctif pour Exporter les données ne fonctionne pas à partir de Power BI Visuals
            - Pour les Rapports Power BI (PBIX), le correctif pour les filtres URL ne fonctionne pas
            - Pour les Rapports paginés (RDL), le correctif pour les images qui ne s’affichent pas correctement dans IE11 après la mise à niveau vers Power BI Report Server version publiée en mars

    - *Version 1.2.6648.38132 (Build 15.0.2.378), publiée : 19 mars 2018*
        - Mises à jour de sécurité
        - Améliorations de l’accessibilité
        - Corrections de bogues
            - Pour les rapports paginés (RDL), correctif pour la visibilité des paramètres dans un rapport lié qui est rétabli après la modification de ses propriétés
            - Correctif pour le portail web avec l’authentification de formulaires personnalisés qui ignore le cookie d’expiration décalée
            - Correctif pour l’exportation vers Word qui crée une hauteur de ligne inégale si le contenu de la ligne est vide
            - Pour les rapports paginés (RDL), correctif pour la chaîne de connexion basée sur une expression qui était supprimée quand vous changiez les informations d’identification pour la source de données
            - Correctif pour la possibilité d’utiliser des indicateurs de performance clés avec des valeurs texte
            - Pour les rapports paginés (RDL), correctif pour pouvoir assigner un nouveau jeu de données à un rapport paginé (RDL) existant
            - Autres correctifs de stabilité et de facilité d’utilisation

- **Power BI Desktop optimisé pour Power BI Report Server**
    - Version : 2.56.5023.1043 (Mars 2018), publiée : 19 mars 2018
        - Contient les modifications nécessaires pour la connexion à Power BI Report Server (mars 2018)

## <a name="october-2017"></a>Octobre 2017

- **Power BI Report Server**
    - *Version 1.1.6582.41691 (Build 14.0.600.442), publiée : 10 janvier 2018*
        - Mises à jour de sécurité
        - Résolutions de bogues
            - Correctif pour Model.GetParameters retournant 400
            - Correctif permettant d’affecter des rapports paginés (RDL) existants à un jeu de données partagé
            - Correctif pour ExecutionNotFoundException lors de l’exportation d’un rapport avec différentes valeurs de paramètre au format PDF

    - *Version 1.1.6551.5155 (Build 14.0.600.438), publiée : 11 décembre 2017*
        - Résolutions de bogues
            - Échec de l’enregistrement des données après actualisation pour certains rapports Power BI Desktop.

    - *Version 1.1.6530.30789 (Build 14.0.600.437), publiée : 17 novembre 2017*
        - Résolutions de bogues
            - Correctif pour les scénarios d’authentification de base 
            - Correctif servant à corriger le fait que les jours de la semaine n’étaient pas sélectionnables sur la page de planification pour Abonnements, Plans d’actualisation du cache et Captures instantanées d'historique sur le portail
            - Pour les rapports paginés (RDL), correctif corrigeant le problème suivant : quand des expressions de la zone de texte ont la propriété CanGrow définie sur false, aucune valeur ne s’affiche et les polices et couleurs sont erronées
            - Pour les rapports Power BI (PBIX), correctif corrigeant le problème suivant : l’ajout de légendes à un graphique en courbes restitue un visuel vide

    - *Version 1.1.6514.9163 (Build 14.0.600.434), publiée : 1er novembre 2017*
        - Résolutions de bogues
            - Correction des problèmes de fiabilité de chargement pour les rapports PBIX de plus de 500 Mo
            - Correction du problème de chargement de données pour les rapports PBIX de plus de 1 Go

    - *Version 1.1.6513.3500 (Build 14.0.600.433), publiée : 31 octobre 2017*
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
    - *Version : 2.51.4885.3981 (Octobre 2017), publiée : 10 avril 2018*
        - Mises à jour de sécurité

    - *Version : 2.51.4885.2501 (Octobre 2017), publiée : 10 janvier 2018*
        - Mises à jour de sécurité

    - *Version : 2.51.4885.1423 (Octobre 2017), publiée : 17 novembre 2017*
        - Résolutions de bogues
            - Correctif du problème suivant : la version 32 bits de Power BI Desktop ne parvient pas à s’exécuter sur les systèmes d’exploitation x86
            - Pour les rapports Power BI (PBIX), correctif de l’affichage du quadrillage de l’axe x
            - Autres correctifs mineurs de bogues

    - *Version : 2.51.4885.1041 (Octobre 2017), publiée : 31 octobre 2017*
        - Fonctionnalités
            - Contient les modifications requises pour la connexion avec Power BI Report Server (octobre 2017)

## <a name="june-2017"></a>Juin 2017

- **Power BI Report Server**
    - *Build 14.0.600.309, publiée : 10 janvier 2018*
        - Mises à jour de sécurité

    - *Build 14.0.600.305, publiée : 19 septembre 2017*  
        - Résolutions de bogues
            - Mise à jour vers la dernière version [du contrôle web Bing Cartes](/bingmaps/v8-web-control/)

    - *Build 14.0.600.301, publiée : 11 juillet 2017*
        - Résolutions de bogues
            - La balise `{{UserId}}` est remplacée par des informations d’identification stockées plutôt que par l’utilisateur qui exécute le rapport dans Rapports Power BI
            - Échec du rendu de certaines images dans des rapports de Power BI Report Server
            - Impossibilité de modifier le nom d’un rapport Power BI dans Power BI Report Server
            - Impossibilité de charger des visuels Power BI dans l’application Power BI Mobile (nécessite la réinstallation de l’application mobile pour effacer le cache local)

    - *Build 14.0.600.271, Date de publication : 12 juin 2017*
        - Publication initiale de Power BI Report Server

- **Power BI Desktop optimisé pour Power BI Report Server**
    - *Version : 2.47.4766.4901 (Juin 2017), publiée : 10 janvier 2018*
        - Mises à jour de sécurité

## <a name="next-steps"></a>Étapes suivantes

[Présentation de Power BI Report Server](get-started.md)
[Vue d’ensemble de l’administrateur](admin-handbook-overview.md)  
[Installer Power BI Report Server](install-report-server.md)  
[Télécharger le Générateur de rapports](https://www.microsoft.com/download/details.aspx?id=53613)  
[Télécharger SQL Server Data Tools (SSDT)](/sql/ssdt/download-sql-server-data-tools-ssdt)

D’autres questions ? [Essayez d’interroger la communauté Power BI](https://community.powerbi.com/)
