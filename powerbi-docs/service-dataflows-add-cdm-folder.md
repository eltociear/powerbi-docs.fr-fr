---
title: Ajouter un dossier CDM comme flux de données à Power BI
description: Configurer un espace de travail pour stocker ses fichiers de données et de définition de dataflow dans Azure Data Lake Storage Gen2
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 04/02/2019
ms.author: davidi
LocalizationGroup: Data from files
ms.openlocfilehash: cc47820e5903426d4f3635c78e0dc108049f897e
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/05/2020
ms.locfileid: "81439339"
---
# <a name="add-a-cdm-folder-to-power-bi-as-a-dataflow-preview"></a>Ajouter un dossier CDM à Power BI sous forme de flux de données (préversion)

Dans Power BI, vous pouvez ajouter sous forme de flux de données des dossiers CDM (Common Data Model) stockés dans le compte Azure Data Lake Storage Gen2 de votre organisation. Une fois que vous avez créé un flux de données à partir d’un dossier CDM, vous pouvez utiliser **Power BI Desktop** et le **service Power BI** pour créer des jeux de données, des rapports, des tableaux de bord et des applications basés sur les données des dossiers CDM.

![Dataflow issu d’un dossier CDM](media/service-dataflows-add-cdm-folder/dataflow-from-cdm-folder_01.jpg)

La création de flux de données à partir de dossiers CDM est soumise aux conditions suivantes :

* Un administrateur doit lier le compte de stockage ADLS Gen2 dans Power BI avant de pouvoir être utilisé. Consultez [Se connecter à Azure Data Lake Storage Gen2 pour le stockage de dataflow](service-dataflows-connect-azure-data-lake-storage-gen2.md) pour découvrir comment lier un compte ADLS Gen2 à Power BI.
* La création de flux de données à partir de dossiers CDM est *uniquement* disponible dans la [nouvelle expérience d’espace de travail](service-create-the-new-workspaces.md). 
* Pour pouvoir ajouter un dossier CDM à Power BI, l’utilisateur doit avoir [l’autorisation d’accès au dossier CDM et à ses fichiers](https://go.microsoft.com/fwlink/?linkid=2029121).
* Vous devez recevoir des autorisations de lecture et d’exécution sur tous les fichiers et dossiers dans le dossier CDM pour les ajouter à Power BI.

Les sections suivantes expliquent comment créer un flux de données à partir d’un dossier CDM.

## <a name="authorizing-users-for-cdm-folders-to-create-a-dataflow"></a>Autorisation de créer un flux de données à partir de dossiers CDM pour les utilisateurs

Pour créer un flux de données à partir d’un dossier CDM, vous devez ajouter les autorisations suivantes :
* L’utilisateur qui accèdera au dossier CDM par le biais de Power BI doit disposer du rôle **Propriétaire des données Storage Blob** du compte de stockage.
* L’utilisateur qui accèdera au dossier CDM par le biais de Power BI doit disposer des listes ACL **Accès en lecture** et **Accès en exécution** sur le dossier CDM lui-même et sur tous les fichiers et dossiers qu’il contient. 

## <a name="create-a-dataflow-from-a-cdm-folder"></a>Créer un flux de données à partir d’un dossier CDM

Pour commencer la création d’un dataflow à partir d’un dossier CDM, lancez le **service Power BI** et sélectionnez un **espace de travail** dans le volet de navigation. Vous pouvez également créer un espace de travail dans lequel vous génèrerez votre flux de données.

![Créer un flux de données dans le service Power BI](media/service-dataflows-add-cdm-folder/dataflow-from-cdm-folder_02.jpg)

Sur l’écran qui s’affiche, sélectionnez **Créer et attacher**, comme l’illustre l’image suivante.

![Créer et attacher un nouveau flux de données](media/service-dataflows-add-cdm-folder/dataflow-from-cdm-folder_03.jpg)

L’écran qui s’affiche ensuite permet de donner un nom et une description au flux de données et d’indiquer le chemin d’accès au dossier CDM dans le compte Azure Data Lake Storage Gen2 de l’organisation. Lisez la section de l’article qui explique [comment obtenir le chemin d’accès au dossier CDM](service-dataflows-configure-workspace-storage-settings.md#get-the-uri-of-stored-dataflow-files). 

![Flux de données issu d’un dossier CDM](media/service-dataflows-add-cdm-folder/dataflow-from-cdm-folder_01.jpg)

Après avoir entré les informations demandées, sélectionnez **Créer et attacher** pour créer le flux de données.

Les flux de données issus de dossiers CDM sont marqués de l’icône *externe* dans Power BI. Dans la section suivante, nous décrirons les différences entre les flux de données standard et les flux de données créés à partir de dossiers CDM.

Une fois les autorisations correctement définies (cf. plus haut dans cet article), vous pouvez vous connecter à votre flux de données dans **Power BI Desktop**.


## <a name="considerations-and-limitations"></a>Considérations et limitations

Si vous travaillez avec des autorisations sur un flux de données créé à partir d’un dossier CDM, le processus est similaire aux sources de données externes dans Power BI. Les autorisations sont gérées au niveau de la source de données et non dans Power BI. Les autorisations doivent être correctement définies sur la source de données proprement dite (par exemple, un flux de données créé à partir d’un dossier CDM) pour fonctionner correctement avec Power BI.

Les listes suivantes visent à clarifier le fonctionnement des flux de données issus de dossiers CDM avec Power BI.

Espaces de travail Power BI Pro, Premium et Embedded :
* Les dataflows issus de dossiers CDM ne sont pas modifiables
* Les autorisations nécessaires pour lire un flux de données créé à partir d’un dossier CDM sont gérées par le propriétaire du dossier CDM et non par Power BI.

Power BI Desktop :
* Seuls les utilisateurs autorisés à accéder à l’espace de travail dans lequel le dataflow a été créé et le dossier CDM peuvent accéder à ses données à partir du connecteur Power BI Dataflows


Autres considérations à prendre en compte :

* La création de flux de données à partir de dossiers CDM est *uniquement* disponible dans la [nouvelle expérience d’espace de travail](service-create-the-new-workspaces.md).
* Les entités liées ne sont pas disponibles pour les flux de données créés à partir de dossiers CDM.


Les clients **Power BI Desktop** peuvent accéder aux dataflows stockés dans le compte Azure Data Lake Storage Gen2, sauf s’ils sont propriétaires du dataflow ou s’ils ont été explicitement autorisé à accéder au dossier CDM du dataflow. Prenons la situation suivante :

1.    Anna crée un espace de travail et le configure de façon à stocker les dataflows issus d’un dossier CDM.
2.    Ben, qui est également membre de l’espace de travail créé par Anna, veut utiliser Power BI Desktop et le connecteur de flux de données pour obtenir des données à partir du flux de données créé par Anna.
3.    Ben a reçu une erreur car Ben n’était pas ajouté comme utilisateur autorisé à accéder au dossier CDM du dataflow dans le lac de données.

  ![Erreur en tentant d’utiliser le flux de données](media/service-dataflows-configure-workspace-storage-settings/dataflow-storage-settings_08.jpg)

Pour résoudre ce problème, Ben doit disposer d’autorisations de lecture sur le dossier CDM et ses fichiers. Pour savoir comment accorder l’accès au dossier CDM, voir [cet article](https://go.microsoft.com/fwlink/?linkid=2029121).


## <a name="next-steps"></a>Étapes suivantes

Cet article aide à configurer le stockage d’espace de travail pour les flux de données. Pour plus d’informations, voir les articles suivants :

Pour plus d’informations sur les flux de données, le format CDM et Azure Data Lake Storage Gen2, voir les articles suivants :

* [Flux de données et intégration à Azure Data Lake (préversion)](service-dataflows-azure-data-lake-integration.md)
* [Configurer les paramètres de flux de données d’un espace de travail (préversion)](service-dataflows-configure-workspace-storage-settings.md)
* [Connecter Azure Data Lake Storage Gen2 pour le stockage de flux de données (préversion)](service-dataflows-connect-azure-data-lake-storage-gen2.md)

Pour plus d’informations sur les flux de données en général, voir les articles suivants :

* [Créer et utiliser des flux de données dans Power BI](service-dataflows-create-use.md)
* [Utilisation d’entités calculées sur Power BI Premium](service-dataflows-computed-entities-premium.md)
* [Utilisation de flux de données avec des sources de données locales](service-dataflows-on-premises-gateways.md)
* [Ressources du développeur pour les flux de données Power BI](service-dataflows-developer-resources.md)

Pour plus d’informations sur le stockage Azure, voir les articles suivants :
* [Guide de sécurité sur le Stockage Azure](https://docs.microsoft.com/azure/storage/common/storage-security-guide)
* [Configuration d’une actualisation planifiée](refresh-scheduled-refresh.md)
* [Bien démarrer avec les exemples GitHub d’Azure Data Services](https://aka.ms/cdmadstutorial)

Pour plus d’informations sur le modèle Common Data Model, vous pouvez lire son article de présentation :
* [Vue d’ensemble du modèle CMD (Common Data Model) ](https://docs.microsoft.com/powerapps/common-data-model/overview)
* [Dossiers CDM](https://go.microsoft.com/fwlink/?linkid=2045304)
* [Définition du fichier model CDM](https://go.microsoft.com/fwlink/?linkid=2045521)

Vous pouvez aussi [poser des questions à la Communauté Power BI](https://community.powerbi.com/).

