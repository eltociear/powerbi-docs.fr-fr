---
title: Utiliser SAP HANA dans Power BI Desktop
description: Utiliser SAP HANA dans Power BI Desktop
author: davidiseminger
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 01/15/2020
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 9b205a0ae9b58acf054a9afe43196e77ee404c84
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83289117"
---
# <a name="connect-to-sap-hana-databases-in-power-bi-desktop"></a>Découvrez comment vous connecter à des bases de données SAP HANA dans Power BI Desktop

Avec Power BI Desktop, vous pouvez désormais accéder aux bases de données *SAP HANA* . Pour utiliser SAP HANA, le pilote ODBC HANA SAP doit être installé sur l’ordinateur client local pour que la connexion de données SAP HANA de Power BI Desktop fonctionne correctement. Vous pouvez télécharger les outils clients SAP HANA depuis [Outils de développement SAP](https://tools.hana.ondemand.com/#hanatools), qui contient le pilote ODBC nécessaire. Vous pouvez aussi l’obtenir auprès du [Centre de téléchargement de logiciels SAP](https://support.sap.com/en/my-support/software-downloads.html). Dans le portail des logiciels, recherchez *SAP HANA CLIENT* pour les ordinateurs Windows. Étant donné que le Centre de téléchargement de logiciels SAP modifie sa structure fréquemment, des informations plus spécifiques sur la navigation dans ce site ne sont pas disponibles.

Pour vous connecter à une base de données SAP HANA, sélectionnez **Obtenir des données**, choisissez **Base de données** > **Base de données SAP HANA**, puis sélectionnez **Se connecter** :

![Base de données SAP HANA, boîte de dialogue Obtenir des données, Power BI Desktop](media/desktop-sap-hana/sap-hana-1.png)

Quand vous vous connectez à une base de données SAP HANA, spécifiez le nom du serveur. Ensuite, dans la zone de liste déroulante et d’entrée, spécifiez le port.

Dans cette version, SAP HANA en mode [DirectQuery](desktop-directquery-sap-hana.md) est pris en charge dans Power BI Desktop et le service Power BI. Vous pouvez publier et charger des rapports qui utilisent SAP HANA en mode DirectQuery dans le service Power BI. Vous pouvez aussi publier et charger des rapports dans le service Power BI quand vous n’utilisez pas SAP HANA en mode DirectQuery.

## <a name="supported-features-for-sap-hana"></a>Fonctionnalités prises en charge pour SAP HANA

Cette version présente de nombreuses fonctionnalités pour SAP HANA, comme indiqué dans la liste suivante :

* Le connecteur Power BI pour SAP HANA utilise le pilote ODBC SAP pour offrir la meilleure expérience utilisateur.

* SAP HANA prend en charge les options DirectQuery et Importer.

* Power BI prend en charge les modèles d’informations HANA, comme les vues d’analytique et de calcul, et bénéficie d’un mode de navigation optimisé.

* Avec SAP HANA, vous pouvez également utiliser la fonctionnalité SQL direct pour la connexion aux tables de lignes et de colonnes.

* Power BI comprend la navigation optimisée pour les modèles HANA.

* Power BI prend en charge les variables et paramètres d’entrée SAP HANA.

* Power BI prend en charge les vues de calcul basées sur un conteneur HDI.

  * La prise en charge des vues de calcul basées sur un conteneur HDI est en préversion publique dans la version d’août 2019 de Power BI Desktop. Pour accéder à vos vues de calcul basées sur un conteneur HDI dans Power BI, assurez-vous que les utilisateurs de base de données HANA que vous utilisez avec Power BI ont l’autorisation d’accéder au conteneur d’exécution HDI qui stocke les vues auxquelles vous souhaitez accéder. Pour accorder cet accès, créez un rôle qui autorise l’accès à votre conteneur HDI. Ensuite, attribuez le rôle à l’utilisateur de base de données HANA que vous utiliserez avec Power BI. (Cet utilisateur doit également avoir l’autorisation de lire les tables système dans le schéma \_SYS\_BI, comme d’habitude.) Pour obtenir des instructions détaillées sur la création et l’affectation des rôles de base de données, consultez la documentation SAP officielle. [Ce billet de blog SAP](https://blogs.sap.com/2018/01/24/the-easy-way-to-make-your-hdi-container-accessible-to-a-classic-database-user/) peut être un bon point de départ.

  * Il existe actuellement des limitations pour les variables HANA associées à des vues de calcul basées sur HDI. Ces limitations sont dues à des erreurs côté HANA.
  
    Premièrement, il n’est pas possible d’appliquer une variable HANA à une colonne partagée d’une vue de calcul basée sur un conteneur HDI. Pour supprimer cette limitation, effectuez une mise à niveau vers HANA 2 version 37.02 et ultérieure ou HANA 2 version 42 et ultérieure. Deuxièmement, les valeurs par défaut multi-entrées pour les variables et les paramètres ne sont pas affichées dans l’interface utilisateur Power BI. C’est une erreur dans SAP HANA qui entraîne cette limitation, mais SAP n’a pas encore annoncé de correctif.

## <a name="limitations-of-sap-hana"></a>Limitations de SAP HANA

Il existe également quelques limitations à l’utilisation de SAP HANA, indiquées ci-dessous :

* Les chaînes NVARCHAR sont tronquées à 4 000 caractères Unicode.
* SMALLDECIMAL n’est pas pris en charge.
* VARBINARY n’est pas pris en charge.
* Les dates valides sont comprises entre le 30/12/1899 et le 31/12/9999.

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations sur DirectQuery et SAP HANA, consultez les ressources suivantes :

* [DirectQuery et SAP HANA](desktop-directquery-sap-hana.md)
* [Utiliser DirectQuery dans Power BI](desktop-directquery-about.md)
* [Sources de données Power BI](power-bi-data-sources.md)
* [Activer le chiffrement pour SAP HANA](desktop-sap-hana-encryption.md)
