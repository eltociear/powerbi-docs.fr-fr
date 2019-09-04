---
title: Utiliser SAP HANA dans Power BI Desktop
description: Utiliser SAP HANA dans Power BI Desktop
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 08/21/2019
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 1932848cb2f8ad7d75e841870265cc22308467c2
ms.sourcegitcommit: a00fe5fb545c3df13b7cd13a701fd6a2b2521a17
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/31/2019
ms.locfileid: "70200868"
---
# <a name="use-sap-hana-in-power-bi-desktop"></a>Utiliser SAP HANA dans Power BI Desktop
Avec Power BI Desktop, vous pouvez désormais accéder aux bases de données **SAP HANA** . Pour utiliser **SAP HANA**, le pilote ODBC de HANA SAP doit être installé sur l’ordinateur client local pour que la connexion de données **SAP HANA** de Power BI Desktop fonctionne correctement. Vous pouvez télécharger le pilote ODBC de SAP HANA à partir du [centre de téléchargement des logiciels SAP](https://support.sap.com/swdc). À partir de là, recherchez SAP HANA CLIENT pour les ordinateurs Windows. Étant donné que le **Centre de téléchargement de logiciels SAP** modifie sa structure fréquemment, des informations plus spécifiques sur la navigation dans ce site ne sont pas disponibles.

Pour vous connecter à une base de données **SAP HANA**, sélectionnez **Obtenir des données > Base de données > Base de données SAP HANA**, comme indiqué dans l’image suivante :

![](media/desktop-sap-hana/sap-hana-1.png)

Quand vous vous connectez à une base de données SAP HANA, spécifiez le nom du serveur. Ensuite, dans la zone de liste déroulante et d’entrée, spécifiez le port.

Dans cette version, **SAP HANA** en mode [DirectQuery](desktop-directquery-sap-hana.md) est pris en charge dans Power BI Desktop et le service Power BI, et vous pouvez publier ou charger des rapports qui utilisent **SAP HANA** en mode DirectQuery pour le service Power BI. Vous pouvez également publier et charger des rapports dans le service Power BI quand vous n’utilisez pas **SAP HANA** en mode DirectQuery.

## <a name="supported-features-for-sap-hana"></a>Fonctionnalités prises en charge pour SAP HANA
Cette version comporte de nombreuses fonctionnalités pour **SAP HANA**, comme indiqué dans la liste suivante :

* Le connecteur Power BI pour **SAP HANA** utilise le pilote ODBC de SAP pour offrir la meilleure expérience utilisateur.
* **SAP HANA** prend en charge les options DirectQuery et Importer.
* Power BI prend en charge les modèles d’informations HANA (comme les vues analytiques et de calcul) et il a un mode de navigation optimisé
* Avec **SAP HANA**, vous pouvez également utiliser la fonctionnalité SQL direct pour la connexion aux tables Row et Column.
* Comprend la navigation améliorée pour les modèles HANA
* Power BI prend en charge les variables et paramètres d’entrée **SAP HANA** .
* Vues de calcul basées sur un conteneur HDI
  * La prise en charge des vues de calcul basées sur un conteneur HDI est en préversion publique dans la version d’août 2019 de Power BI Desktop. Pour accéder à vos vues de calcul basées sur un conteneur HDI dans Power BI, assurez-vous que le ou les utilisateurs de base de données HANA que vous utilisez avec Power BI ont l’autorisation d’accéder au conteneur d’exécution HDI qui stocke les vues auxquelles vous souhaitez accéder. Pour accorder cet accès, vous devez créer un rôle qui autorise l’accès à votre conteneur HDI et attribuer le rôle à l’utilisateur de base de données HANA que vous allez utiliser avec Power BI (cet utilisateur doit également avoir l’autorisation de lire les tables système dans le schéma \_SYS\_BI, comme d’habitude). Pour obtenir des instructions détaillées sur la création et l’affectation des rôles de base de données, consultez la documentation SAP officielle. [Ce billet de blog SAP](https://nam06.safelinks.protection.outlook.com/?url=https%3A%2F%2Fblogs.sap.com%2F2018%2F01%2F24%2Fthe-easy-way-to-make-your-hdi-container-accessible-to-a-classic-database-user%2F&data=02%7C01%7Cv-adbold%40microsoft.com%7Cf7e0a405fe334598ba0608d7096ef5b4%7C72f988bf86f141af91ab2d7cd011db47%7C1%7C0%7C636988244476739316&sdata=PuRu61GPRYp34mLuGbQk6gdbRikdgbxfqo8q1RBQtm0%3D&reserved=0) peut être un bon point de départ.
  * Notez qu’il existe actuellement des limitations pour les variables HANA associées à des vues de calcul basées sur HDI. Ces limitations sont dues à des erreurs du côté HANA et seront traitées dans les futures versions de SAP HANA. Premièrement, il n’est pas possible d’appliquer une variable HANA à une colonne partagée d’une vue de calcul basée sur un conteneur HDI. Cette limitation peut être corrigée en effectuant une mise à niveau vers HANA 2 versions 37.02 et ultérieures ou HANA 2 versions 42 et ultérieures. Deuxièmement, les valeurs par défaut à plusieurs entrées pour les variables et les paramètres ne sont pas affichées dans l’interface utilisateur Power BI. Cela est également dû à une erreur dans SAP HANA, mais SAP n’a pas encore annoncé de correctif.

## <a name="limitations-of-sap-hana"></a>Limitations de SAP HANA
Il existe également quelques limitations à l’utilisation de **SAP HANA**, indiquées ci-dessous :

* Les chaînes NVARCHAR sont tronquées à 4 000 caractères Unicode.
* SMALLDECIMAL n’est pas pris en charge.
* VARBINARY n’est pas pris en charge.
* Les dates valides sont comprises entre le 30/12/1899 et le 31/12/9999.


## <a name="next-steps"></a>Étapes suivantes
Pour plus d’informations sur DirectQuery et SAP HANA, consultez les ressources suivantes :

* [DirectQuery et SAP HANA](desktop-directquery-sap-hana.md)
* [DirectQuery dans Power BI](desktop-directquery-about.md)
* [Sources de données prises en charge par DirectQuery](desktop-directquery-data-sources.md)
* [Activer le chiffrement pour SAP HANA](desktop-sap-hana-encryption.md)


