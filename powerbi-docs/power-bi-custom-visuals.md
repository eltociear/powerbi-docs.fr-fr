---
title: Éléments visuels personnalisés dans Power BI
description: Visualisations personnalisées dans Power BI
author: sranins
ms.author: rasala
manager: kfile
ms.reviewer: maghan
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/15/2019
LocalizationGroup: Visualizations
ms.openlocfilehash: 3fd2f3e47c9b6dd2144ed5a66d45e65a00c5b92e
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66051255"
---
# <a name="custom-visuals-in-power-bi"></a>Éléments visuels personnalisés dans Power BI

Lorsque vous créez ou modifiez un rapport Power BI, vous pouvez utiliser de nombreux types différents d’éléments visuels. Les icônes pour ces visuels apparaissent dans le **visualisations** volet. Ces éléments visuels livrée préalable lorsque vous téléchargez [Power BI Desktop](https://powerbi.microsoft.com/desktop/) ou ouvrez le [service Power BI](https://app.powerbi.com).

![visualisations](media/power-bi-custom-visuals/power-bi-visualizations.png)

Toutefois, vous n’êtes pas limité à ce jeu d’éléments visuels. Si vous sélectionnez les points de suspension (...) en bas, une autre source de visuels de rapport devient disponible -*visuels personnalisés*.

Les développeurs de créent des visuels personnalisés à l’aide du Kit de développement de visuels personnalisés. Ces éléments visuels permettent aux utilisateurs d’afficher leurs données d’une manière qui convient à leur activité. Les auteurs de rapports peuvent ensuite importer les fichiers de visuels personnalisés dans leurs rapports et les utiliser comme ils le feraient tous les autres visuels de Power BI. Les visuels personnalisés sont des citoyens de première classes dans Power BI et peuvent être filtrés, mis en surbrillance, modifiés, partagés et ainsi de suite.

Visuels personnalisés sont déployés de trois façons :

* Fichiers de visuels personnalisés
* Visuels organisationnels
* Visuels de la Place de marché

## <a name="custom-visual-files"></a>Fichiers de visuels personnalisés

Visuels personnalisés sont des packages qui incluent du code pour rendre les données, ils reçoivent. Toute personne peut créer un visuel personnalisé et l’empaqueter en tant qu’un seul `.pbiviz` fichier, qui peut ensuite être importé dans un rapport Power BI.

> [!WARNING]
> Un élément visuel personnalisé peut contenir du code présentant des risques la sécurité et confidentialité. Assurez-vous que vous faites confiance à l’auteur et le code source visual personnalisé avant l’importation à votre rapport.

## <a name="organizational-visuals"></a>Visuels organisationnels

Les administrateurs Power BI approuver et déploiement des éléments visuels personnalisés dans leur organisation, ce qui les auteurs de rapports puissent facilement détecter, mettre à jour et utiliser. Les administrateurs peuvent facilement gérer (par exemple, mettre à jour de version, désactiver/activer) ces visuels.

 [En savoir plus sur les éléments visuels d’organisation](power-bi-custom-visuals-organization.md).

## <a name="marketplace-visuals"></a>Visuels de la Place de marché

Membres de la Communauté et Microsoft ont contribué leurs visuels personnalisés pour avantage publique et les a publiés à le [AppSource](https://appsource.microsoft.com/marketplace/apps?product=power-bi-visuals) place de marché. Vous pouvez télécharger ces éléments visuels les ajouter à vos rapports Power BI. Microsoft a testé et approuvé ces visuels personnalisés pour la fonctionnalité et de qualité.

Qu’est-ce qu’[AppSource](developer/office-store.md) ? C’est l’endroit que vous pouvez trouver des applications, des compléments et extensions pour vos logiciels Microsoft. [AppSource](https://appsource.microsoft.com/) connecte des millions d’utilisateurs de produits à l’instar de Office 365, Azure, Dynamics 365, Cortana et Power BI, pour les solutions qui les aident à travailler plus efficacement, leur et parfaitement qu’auparavant.

### <a name="certified-visuals"></a>Visuels certifiés

Power BI certifiés visuels sont des éléments visuels de la place de marché qui ont passé des tests supplémentaire qualité rigoureuse et pris en charge dans d’autres scénarios, tels que [abonnements par e-mail](https://docs.microsoft.com/power-bi/service-report-subscribe), et [exporter vers PowerPoint](https://docs.microsoft.com/power-bi/service-publish-to-powerpoint).
Pour afficher la liste des visuels personnalisés certifiés ou pour soumettre les vôtres, voir [Visuels personnalisés certifiés](https://docs.microsoft.com/power-bi/power-bi-custom-visuals-certified).

Vous êtes un développeur web et souhaitez créer vos propres visualisations et les ajouter à AppSource ? Consultez [développer un visuel personnalisé Power BI](developer/custom-visual-develop-tutorial.md) et découvrez comment [publier des visuels personnalisés dans AppSource](https://docs.microsoft.com/power-bi/developer/office-store).

### <a name="import-a-custom-visual-from-a-file"></a>Importer un visuel personnalisé à partir d’un fichier

1. Sélectionnez les points de suspension à partir du bas de la **visualisations** volet.

    ![visualisations2](media/power-bi-custom-visuals/power-bi-visualizations2.png)

2. Dans la liste déroulante, sélectionnez **Importer à partir d'un fichier**.

    ![importer à partir du fichier](media/power-bi-custom-visuals/power-bi-custom-visual-import-from-file.png)

3. Dans le menu Ouvrir un fichier, sélectionnez le `.pbiviz` fichier que vous souhaitez importer, puis choisissez **Open**. Icône de l’élément du visuel personnalisé est ajouté au bas de votre **visualisations** volet et est désormais disponible pour une utilisation dans votre rapport.

    ![visuel personnalisé importé](media/power-bi-custom-visuals/power-bi-custom-visual-imported.png)

### <a name="import-organizational-visuals"></a>Importer des visuels organisationnels

1. Sélectionnez les points de suspension à partir du bas de la **visualisations** volet.

    ![visuel org 1](media/power-bi-custom-visuals/power-bi-visual-org-01.png)

2. Dans la liste déroulante, sélectionnez **Importer à partir de la Place de marché**.

    ![visuel org 2](media/power-bi-custom-visuals/power-bi-visual-org-02.png)

3. Sélectionnez **MON ORGANISATION** dans le menu de l’onglet supérieur.

    ![visuel org 3](media/power-bi-custom-visuals/power-bi-visual-org-03.png)

4. Faites défiler la liste pour rechercher le visuel à importer.

    ![visuel org 4](media/power-bi-custom-visuals/power-bi-visual-org-04.png)

5. Sélectionnez **ajouter** pour importer le visuel personnalisé. Son icône est ajouté au bas de votre **visualisations** volet et est désormais disponible pour une utilisation dans votre rapport.

    ![visuel org 5](media/power-bi-custom-visuals/power-bi-visual-org-05.png)

## <a name="download-or-import-custom-visuals-from-microsoft-appsource"></a>Télécharger ou importer des visuels personnalisés à partir de Microsoft AppSource

Vous avez deux options de téléchargement et importation de visuels personnalisés : à partir de Power BI et à partir de la [site Web AppSource](https://appsource.microsoft.com/).

### <a name="import-custom-visuals-from-within-power-bi"></a>Importer des visuels personnalisés à partir de Power BI

1. Sélectionnez les points de suspension à partir du bas de la **visualisations** volet.

    ![visualisations 2](media/power-bi-custom-visuals/power-bi-visualizations2.png)

2. Dans la liste déroulante, sélectionnez **Importer à partir de la Place de marché**.

    ![visuel org 2](media/power-bi-custom-visuals/power-bi-visual-org-02.png)

3. Faites défiler la liste pour rechercher le visuel à importer.

    ![importer un visuel](media/power-bi-custom-visuals/power-bi-import-visual.png)

4. Pour en savoir plus sur un des visuels, mettez-le en surbrillance et sélectionnez-le.

    ![Sélectionner](media/power-bi-custom-visuals/power-bi-select.png)

5. Sur la page de détails, vous pouvez voir des captures d’écran, des vidéos, une description détaillée et bien plus encore.

    ![Synoptique](media/power-bi-custom-visuals/power-bi-synoptic.png)

6. Faites défiler vers le bas pour voir les avis.

    ![Revues](media/power-bi-custom-visuals/power-bi-reviews.png)

7. Sélectionnez **ajouter** pour importer le visuel personnalisé. Son icône est ajouté au bas de votre **visualisations** volet et est désormais disponible pour une utilisation dans votre rapport.

    ![visuel importé](media/power-bi-custom-visuals/power-bi-custom-visual-imported.png)

### <a name="download-and-import-custom-visuals-from-microsoft-appsource"></a>Télécharger et importer des visuels personnalisés à partir de Microsoft AppSource

1. Ouvrez [Microsoft AppSource](https://appsource.microsoft.com) et sélectionnez l’onglet **Applications**.

    ![AppSource](media/power-bi-custom-visuals/power-bi-appsource-apps.png)

2. Accédez alors à la [page de résultats d’applications](https://appsource.microsoft.com/marketplace/apps) dans laquelle vous pouvez afficher les principales applications dans chaque catégorie, notamment les *applications Power BI*. Nous recherchons des visuels personnalisés, nous allons donc sélectionnez **visuels Power BI** dans la liste de navigation de gauche pour limiter les résultats.

    ![Visuels AppSource](media/power-bi-custom-visuals/power-bi-appsource-visuals.png)

3. AppSource affiche une vignette pour chaque visuel personnalisé.  Chaque vignette a un instantané visuel personnalisé avec une brève description et un lien de téléchargement. Pour afficher plus de détails, sélectionnez la vignette.

    ![Sélection du visuel personnalisé](media/power-bi-custom-visuals/powerbi-custom-select-visual.png)

4. Sur la page de détails, vous pouvez voir des captures d’écran, des vidéos, une description détaillée et bien plus encore. Sélectionnez **obtenez-le maintenant** pour télécharger le visuel personnalisé et acceptez les conditions d’utilisation.

    ![Obtenir dans AppSource](media/power-bi-custom-visuals/power-bi-appsource-get.png)

5. Sélectionnez le lien pour télécharger le visuel personnalisé.

    ![Télécharger](media/power-bi-custom-visuals/powerbi-custom-download.png)

    La page de téléchargement contient également des instructions sur l’importation de l’élément visuel personnalisé dans Power BI Desktop et le service Power BI.

    Vous pouvez également télécharger un exemple de rapport incluant le visuel personnalisé et présentant ses fonctionnalités.

    ![Essayer un exemple](media/power-bi-custom-visuals/powerbi-custom-try-sample.png)

6. Enregistrer le `.pbiviz` de fichier, puis ouvrez Power BI.

7. Importer le `.pbiviz` fichier dans votre rapport. (Consultez la section [Importer un visuel personnalisé à partir d’un fichier](#import-a-custom-visual-from-a-file) ci-dessus.)

## <a name="considerations-and-limitations"></a>Considérations et limitations

* Un élément visuel personnalisé est ajouté à un rapport spécifique lors son importation. Si vous souhaitez utiliser l’élément visuel dans un autre rapport, vous devez l’y importer. Quand un rapport comportant un élément visuel personnalisé est enregistré à l’aide de l’option **Enregistrer sous** , une copie de l’élément visuel personnalisé est enregistrée avec le nouveau rapport.

* Si vous ne voyez pas un **visualisations** volet, ce qui signifie que vous n’avez pas de modifier les autorisations de rapport.  Vous pouvez uniquement ajouter des visuels personnalisés aux rapports que vous pouvez modifier, et non à ceux qui ont été partagés avec vous.

## <a name="troubleshoot"></a>Résoudre des problèmes

Pour résoudre les problèmes, consultez [résolution des problèmes de vos visuels personnalisés Power BI](power-bi-custom-visuals-troubleshoot.md).

## <a name="faq"></a>FORUM AUX QUESTIONS

Pour plus d’informations et des réponses à vos questions, visitez [Questions fréquentes sur les visuels personnalisés Power BI](power-bi-custom-visuals-faq.md#organizational-custom-visuals).

## <a name="next-steps"></a>Étapes suivantes

* [Visualisations dans les rapports Power BI](visuals/power-bi-report-visualizations.md)

D’autres questions ? [Posez vos questions à la Communauté Power BI](http://community.powerbi.com/).
