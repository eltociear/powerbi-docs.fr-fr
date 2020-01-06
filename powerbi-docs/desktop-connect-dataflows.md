---
title: Se connecter à des données créées par des dataflows Power BI dans Power BI Desktop (version bêta)
description: Se connecter et utiliser facilement des dataflows dans Power BI Desktop
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/08/2019
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: f1d782aa7409dce43d960956406e996cc7951a57
ms.sourcegitcommit: 6272c4a0f267708ca7d38a45774f3bedd680f2d6
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/06/2020
ms.locfileid: "73876472"
---
# <a name="connect-to-data-created-by-power-bi-dataflows-in-power-bi-desktop-beta"></a>Se connecter à des données créées par des dataflows Power BI dans Power BI Desktop (version bêta)
Dans **Power BI Desktop**, vous pouvez vous connecter à des données créées par des **dataflows Power BI** comme toute autre source de données dans Power BI Desktop.

![Se connecter à des dataflows](media/desktop-connect-dataflows/connect-dataflows_01.png)

Le connecteur **Dataflows Power BI (bêta)** vous permet d’établir des connexions à des entités créées par des dataflows dans le service Power BI. 

## <a name="considerations-and-limitations"></a>Considérations et limitations

Pour utiliser cette version bêta du **connecteur Dataflows Power BI**, vous devez exécuter la version la plus récente de **Power BI Desktop**. Vous pouvez toujours [télécharger Power BI Desktop](desktop-get-the-desktop.md) et l’installer sur votre ordinateur pour être certain d’avoir la version la plus récente.  

> [!NOTE]
> La version précédente du connecteur Dataflows Power BI vous obligeait à télécharger un fichier .MEZ et à la placer dans un dossier. Les versions actuelles de **Power BI Desktop** incluent le connecteur Dataflows Power BI, de sorte que le fichier n’est plus nécessaire et peut entrer en conflit avec la version du connecteur incluse. Si vous avez manuellement placé le fichier .MEZ dans le dossier, vous *devez* supprimer ce fichier .MEZ téléchargé de votre dossier **Documents > Power BI Desktop > Connecteurs personnalisés** pour éviter tout conflit. 

## <a name="desktop-performance"></a>Performances de Power BI Desktop
**Power BI Desktop** s’exécute localement sur l’ordinateur sur lequel il est installé. Les performances d’ingestion de flux de données sont déterminées par plusieurs facteurs. Ces facteurs incluent la taille des données, le processeur et la mémoire RAM de votre ordinateur, la bande passante réseau, la distance depuis le centre de données et d’autres facteurs.

Vous pouvez améliorer les performances d’ingestion des données des flux de données. Par exemple, si la taille des données ingérées est trop grande pour permettre à **Power BI Desktop** de les gérer sur votre ordinateur, vous pouvez utiliser des entités liées et calculées dans le flux de données pour agréger les données (au sein de flux de données) et recevoir uniquement les données agrégées et préalablement préparées. De cette manière, le traitement de données volumineuses est effectué en ligne dans le flux de données et non localement dans votre instance en cours d’exécution de **Power BI Desktop**. Cette approche permet à Power BI Desktop d’ingérer de petites quantités de données et maintient la réactivité et la rapidité des flux de données.

## <a name="considerations-and-limitations"></a>Considérations et limitations

La plupart des flux de données se trouvent dans le locataire du service Power BI. Toutefois, les utilisateurs de **Power BI Desktop** n’ont pas accès aux flux de données stockés dans un compte Azure Data Lake Storage Gen2, sauf s’ils sont propriétaires du flux de données ou explicitement autorisés à accéder au dossier CDM du flux de données. Prenons la situation suivante :

1.  Anna crée un espace de travail et le configure de façon à stocker les dataflows dans le lac de données de l’organisation.
2.  Ben, qui est également membre de l’espace de travail créé par Anna, veut utiliser Power BI Desktop et le connecteur de flux de données pour obtenir des données à partir du flux de données créé par Anna.
3.  Ben reçoit une erreur, car il n’a pas été autorisé à accéder au dossier CDM du dataflow dans le lac de données.

    ![Erreur en tentant d’utiliser le flux de données](media/service-dataflows-configure-workspace-storage-settings/dataflow-storage-settings_08.jpg)

Pour résoudre ce problème, Ben doit disposer d’autorisations de lecture sur le dossier CDM et ses fichiers. Pour savoir comment accorder l’accès au dossier CDM, voir [cet article](https://go.microsoft.com/fwlink/?linkid=2029121).




## <a name="next-steps"></a>Étapes suivantes
Les flux de données Power BI permettent d’effectuer toutes sortes de choses intéressantes. Pour plus d’informations, consultez les ressources suivantes :

* [Préparation des données en libre-service avec des flux de données](service-dataflows-overview.md)
* [Créer et utiliser des flux de données dans Power BI](service-dataflows-create-use.md)
* [Utilisation d’entités calculées sur Power BI Premium (préversion)](service-dataflows-computed-entities-premium.md)
* [Utilisation de flux de données avec des sources de données locales (préversion)](service-dataflows-on-premises-gateways.md)
* [Ressources du développeur pour les flux de données Power BI (préversion)](service-dataflows-developer-resources.md)

Pour plus d’informations sur l’intégration avec Azure Data Lake Storage Gen2, voir les articles suivants :

* [Flux de données et intégration à Azure Data Lake (préversion)](service-dataflows-azure-data-lake-integration.md)
* [Configurer les paramètres de flux de données d’espace de travail (préversion)](service-dataflows-configure-workspace-storage-settings.md)
* [Ajouter un dossier CDM à Power BI sous forme de flux de données (préversion)](service-dataflows-add-cdm-folder.md)
* [Connecter Azure Data Lake Storage Gen2 pour le stockage de flux de données (préversion)](service-dataflows-connect-azure-data-lake-storage-gen2.md)

Il existe également des articles sur **Power BI Desktop** qui peuvent vous être utiles :

* [Sources de données dans Power BI Desktop](desktop-data-sources.md)
* [Mettre en forme et combiner des données dans Power BI Desktop](desktop-shape-and-combine-data.md)
* [Entrer des données directement dans Power BI Desktop](desktop-enter-data-directly-into-desktop.md)   

