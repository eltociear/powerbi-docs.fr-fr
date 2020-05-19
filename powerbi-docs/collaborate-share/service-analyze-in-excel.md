---
title: Analyser dans Excel pour Power BI
description: Découvrez comment analyser des jeux de données Power BI dans Excel
author: davidiseminger
ms.reviewer: ''
ms.custom: contperfq4
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 05/06/2020
ms.author: davidi
LocalizationGroup: Reports
ms.openlocfilehash: 48e1df6f8d47b996145d8734f89b2e15d17abf9c
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83275061"
---
# <a name="analyze-in-excel"></a>Analyser dans Excel
Vous pouvez utiliser Excel pour afficher un jeu de données Power BI et interagir avec celui-ci. L’option qui permet cela se nomme **Analyser dans Excel**. Cette option permet également d’accéder aux fonctionnalités de segments, de graphiques et de tableaux croisés dynamiques d’Excel, selon le jeu de données qui se trouve dans Power BI.

## <a name="two-ways-to-get-started"></a>Deux méthodes pour commencer
Il existe deux façons différentes d’explorer des jeux de données Power BI dans Excel : si vous partez de Power BI, vous suivrez la procédure décrite dans ce document.  Les utilisateurs disposant de certaines références SKU Office ont maintenant la possibilité d’accéder à leurs jeux de données en partant directement de l’expérience Obtenir des données dans un classeur Excel.  Ils peuvent parcourir les jeux de données auxquels ils ont accès pour voir s’ils sont certifiés ou promus et si des étiquettes de protection des données ont été appliquées.  Pour plus d’informations sur cette expérience, consultez [Création d’un tableau croisé dynamique à partir de jeux de données Power BI](https://support.office.com/article/31444a04-9c38-4dd7-9a45-22848c666884) dans la documentation Excel.

## <a name="requirements"></a>Configuration requise
Il existe certaines conditions à l’utilisation de l’option **Analyser dans Excel** :

* **Analyser dans Excel** est compatible avec Microsoft Excel 2010 SP1 et versions ultérieures.

* Les tableaux croisés dynamiques d’Excel ne prennent pas en charge l’agrégation des champs numériques en mode glisser-déposer. Des *mesures doivent être prédéfinies* pour votre jeu de données dans Power BI. Apprenez-en plus sur la [création de mesures](../transform-model/desktop-measures.md).
* Certaines organisations appliquent des règles de stratégie de groupe qui empêchent l’installation des mises à jour requises relatives à l’option **Analyser dans Excel**. Si vous ne parvenez pas à installer les mises à jour, contactez votre administrateur.
* **Analyser dans Excel** nécessite que le jeu de données soit dans Power BI Premium ou que l’utilisateur dispose d’une licence Power BI Pro. Pour plus d’informations sur les différences de fonctionnalités entre les différents types de licences, consultez la section _Comparaison des fonctionnalités de Power BI_ de la rubrique [Prix de Power BI](https://powerbi.microsoft.com/pricing/).
* Les utilisateurs peuvent se connecter aux jeux de données par le biais de la fonctionnalité Analyser dans Excel s’ils disposent d’une autorisation d’accès au jeu de données sous-jacent.  Un utilisateur peut obtenir cette autorisation de plusieurs façons, par exemple en ayant le rôle de membre de l’espace de travail contenant le jeu de données, en bénéficiant du partage d’un rapport ou tableau de bord qui utilise le jeu de données ou en ayant l’autorisation de génération pour le jeu de données dans un espace de travail ou une application qui contient le jeu de données. Découvrez plus en détail l’[autorisation de génération](../connect-data/service-datasets-build-permissions.md) pour les jeux de données.
* Les utilisateurs invités ne peuvent pas utiliser **Analyser dans Excel** pour les jeux de données envoyés à partir d’un autre locataire. 
* La fonctionnalité **Analyser dans Excel** est une fonctionnalité du service Power BI et n’est pas disponible dans Power BI Report Server et Power BI Embedded. 
* **Analyser dans Excel** est pris en charge uniquement sur les ordinateurs exécutant Microsoft Windows.

## <a name="how-does-it-work"></a>Comment ça marche ?
Quand vous sélectionnez **Analyser dans Excel** à partir du menu **Autres options** (...) associé à un jeu de données ou à un rapport dans **Power BI**, Power BI crée un fichier .ODC et le télécharge sur votre ordinateur à partir du navigateur.

![Analyser dans Excel](media/service-analyze-in-excel/power-bi-analyze-in-excel.png)

Quand vous ouvrez le fichier dans Excel, une liste de **champs** et de **tableaux croisés dynamiques** vides s’affiche avec tous les tableaux, les champs et les mesures de votre jeu de données Power BI. Vous pouvez créer des tableaux croisés dynamiques et des graphiques, et analyser le jeu de données comme vous le feriez pour un jeu de données local dans Excel.

Le fichier .ODC comporte une chaîne de connexion MSOLAP, connectée à votre jeu de données dans Power BI. Quand vous analysez ou manipulez les données, Excel interroge le jeu de données de Power BI et renvoie les résultats à Excel. Si le jeu de données est connecté à une source de données active via DirectQuery, Power BI interroge la source de données et renvoie les résultats vers Excel.

L’option **Analyser dans Excel** est très utile pour les jeux de données et les rapports qui se connectent aux bases de données *multidimensionnelles* ou *tabulaires Analysis Services* ou à partir de fichiers Power BI Desktop ou de classeurs Excel avec des modèles de données qui possèdent des mesures modèles créés à l’aide de Data Analysis Expressions (DAX).

## <a name="get-started-with-analyze-in-excel-in-power-bi"></a>Prise en main de la fonctionnalité Analyser dans Excel dans Power BI
Dans Power BI, sélectionnez le menu **Autres options** (...) en regard du nom d’un rapport ou d’un jeu de données, puis, dans le menu qui s’affiche, sélectionnez **Analyser dans Excel**.

![Analyser dans Excel](media/service-analyze-in-excel/power-bi-analyze-menu.png)

### <a name="install-excel-updates"></a>Installer les mises à jour d’Excel
Quand vous utilisez **Analyser dans Excel**, vous devez installer les mises à jour des bibliothèques Excel. Vous serez invité à télécharger et à exécuter les mises à jour Excel. Cela démarrera l’installation du package Windows Installer *SQL_AS_OLEDDB.msi*. Ce package installe **Microsoft AS OLE DB Provider pour SQL Server 2016 RC0 (version préliminaire)** .

> [!NOTE]
> Veillez à activer l’option **Ne plus afficher ce message** dans la boîte de dialogue **Installer les mises à jour Excel**. La mise à jour ne doit être installée qu’une seule fois.
> 
> 

![Case à cocher Ne plus afficher](media/service-analyze-in-excel/pbi_anlz_excel_dontshow.png)

Si vous avez besoin d’installer de nouveau les mises à jour Excel pour l’option **Analyser dans Excel**, vous pouvez les télécharger à partir de l’icône de **téléchargement** de Power BI, comme illustré dans l’image suivante.

![Installer les mises à jour](media/service-analyze-in-excel/pbi_anlz_excel_download_again.png)

### <a name="sign-in-to-power-bi"></a>Connectez-vous à Power BI
Même si vous êtes déjà connecté à Power BI dans votre navigateur, vous êtes invité à vous connecter à Power BI avec votre compte Power BI la première fois que vous ouvrez un nouveau fichier .ODC dans Excel. Cela permet d’authentifier la connexion entre Excel et Power BI.

### <a name="users-with-multiple-power-bi-accounts"></a>Utilisateurs disposant de plusieurs comptes Power BI
Certains utilisateurs possèdent plusieurs comptes Power BI. Il peut arriver qu’ils soient connectés dans Power BI avec un compte, alors que le compte utilisé par l’option Analyser dans Excel pour accéder au jeu de données est un compte différent. Dans ce cas, vous risquez d’obtenir une erreur **Interdit** ou un message d’échec de connexion si vous tentez d’accéder à un jeu de données qui est utilisé par l’option Analyser dans Excel.

Vous aurez l’occasion de vous connecter à nouveau. Vous pourrez alors vous connecter à l’aide du compte Power BI qui a accès au jeu de données utilisé par l’option Analyser dans Excel. Vous pouvez également sélectionner votre nom dans le ruban supérieur d’Excel, ce qui permet d’identifier le compte avec lequel vous êtes actuellement connecté. Se déconnecter et se connecter avec un autre compte.

### <a name="enable-data-connections"></a>Activez les connexions de données
Afin d’analyser vos données Power BI dans Excel, vous êtes invité à vérifier le nom et le chemin du fichier .odc, puis à sélectionner **Activer**.

![Activez les connexions de données](media/service-analyze-in-excel/pbi_anlz_excel_enable.png)

> [!NOTE]
> Les administrateurs de locataires Power BI peuvent utiliser le *portail d’administration Power BI* pour désactiver l’utilisation de la fonction **Analyser dans Excel** avec les jeux de données locaux hébergés dans des bases de données Analysis Services (AS). Lorsque cette option est désactivée, la fonction **Analyser dans Excel** est désactivée pour les bases de données, mais reste disponible pour une utilisation avec d’autres jeux de données.
> 
> 

## <a name="analyze-away"></a>Analyser
Maintenant qu’Excel est ouvert et que vous disposez d’un tableau croisé dynamique vide, vous êtes prêt à effectuer toutes sortes d’analyses avec votre jeu de données Power BI. Comme avec les autres classeurs locaux, la fonctionnalité Analyser dans Excel vous permet de créer des tableaux croisés dynamiques et des graphiques, d’ajouter des données à partir d’autres sources, etc. Bien sûr, vous pouvez également créer des feuilles de calcul variées avec différents types d’affichages de données.

![Tableaux et graphiques croisés dynamiques dans Excel](media/service-analyze-in-excel/pbi_anlz_excel_chart.png)

> [!NOTE]
> L’utilisation de l’**analyse dans Excel** expose toutes les données de niveau de détail à tous les utilisateurs autorisés à accéder au jeu de données.
> 
> 

## <a name="save"></a>Enregistrer
Vous pouvez enregistrer ce classeur connecté au jeu de données Power BI comme n’importe quel autre classeur. Toutefois, vous ne pouvez pas publier ni importer le classeur dans Power BI, car vous pouvez uniquement publier ou importer dans Power BI les classeurs qui comprennent des tables de données ou des modèles de données. Étant donné que le nouveau classeur est connecté au jeu de données dans Power BI, la publication ou l’importation dans Power BI seraient redondantes.

## <a name="share"></a>Partager
Une fois que le classeur est enregistré, vous pouvez le partager avec d’autres utilisateurs Power BI dans votre organisation.

Quand un utilisateur avec lequel vous avez partagé votre classeur ouvre celui-ci pour la première fois, vos tableaux croisés dynamiques et vos données s’affichent tels qu’ils étaient quand vous avez enregistré le classeur pour la dernière fois. Il peut donc ne pas s’agir de la dernière version de vos données. Pour obtenir la dernière version des données, l’utilisateur doit cliquer sur le bouton **Actualiser** du ruban **Données**. Étant donné que le classeur se connecte à un jeu de données dans Power BI, les utilisateurs qui tentent d’actualiser le classeur doivent se connecter à Power BI et installer les mises à jour Excel la première fois qu’ils tentent une mise à jour à l’aide de cette méthode.

Étant donné que les utilisateurs doivent actualiser le jeu de donnée et que l’actualisation n’est pas prise en charge dans Excel Online pour les connexions externes, il est recommandé d’ouvrir le classeur dans une version de bureau d’Excel.

## <a name="troubleshooting"></a>Résolution des problèmes
Il peut arriver que vous obteniez un résultat inattendu lors de l’utilisation de la fonctionnalité Analyser dans Excel, ou que la fonctionnalité ne fonctionne pas comme prévu. [Cette page offre des résolutions communes des problèmes associés à l’utilisation de Analyser dans Excel](desktop-troubleshooting-analyze-in-excel.md)

## <a name="next-steps"></a>Étapes suivantes

Les articles suivants pourraient également vous intéresser :

* [Use cross-report drillthrough in Power BI Desktop](../create-reports/desktop-cross-report-drill-through.md) (Utiliser une extraction interrapport dans Power BI Desktop)
* [Utilisation de segments Power BI Desktop](../visuals/power-bi-visualization-slicers.md)



