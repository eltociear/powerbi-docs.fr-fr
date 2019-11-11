---
title: Intégrer un rapport Power BI Report Server à l’aide d’un iFrame dans SharePoint Server
description: Cet article montre comment incorporer un rapport Power BI Report Server dans un iFrame sur SharePoint Server.
author: maggiesMSFT
ms.author: maggies
ms.date: 08/12/2019
ms.topic: conceptual
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.custom: mvc
ms.openlocfilehash: 195be0766e135dcccc2124a998fb5a32e8703d5b
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2019
ms.locfileid: "73875015"
---
# <a name="embed-a-power-bi-report-server-report-using-an-iframe-in-sharepoint-server"></a>Intégrer un rapport Power BI Report Server à l’aide d’un iFrame dans SharePoint Server

Dans cet article, vous allez apprendre à incorporer un rapport Power BI Report Server à l’aide d’un iFrame dans une page SharePoint. Si vous utilisez SharePoint Online, Power BI Report Server doit être accessible publiquement. Dans SharePoint Online, le composant Power BI WebPart qui fonctionne avec le service Power BI ne fonctionnera pas avec Power BI Report Server.  

![Exemple iFrame](media/quickstart-embed/quickstart_embed_01.png)

## <a name="prerequisites"></a>Conditions préalables
* [Power BI Report Server](https://powerbi.microsoft.com/report-server/) installé et configuré
* [Power BI Desktop optimisé pour Power BI Report Server](install-powerbi-desktop.md) installé
* Un environnement [SharePoint](https://docs.microsoft.com/sharepoint/install/install) installé et configuré

## <a name="create-the-power-bi-report-url"></a>Créer l’URL d’un rapport Power BI

1. Téléchargez l’exemple à partir de GitHub : [Blog Demo](https://github.com/Microsoft/powerbi-desktop-samples). Sélectionnez **Clone or download** (Cloner ou télécharger), puis sélectionnez **Download ZIP** (Télécharger le zip).

    ![Télécharger l’exemple de fichier PBIX](media/quickstart-embed/quickstart_embed_14.png)

2. Décompressez le fichier .zip, puis ouvrez l’exemple de fichier .pbix dans Power BI Desktop optimisé pour Power BI Report Server.

    ![Outil PBI RS Desktop](media/quickstart-embed/quickstart_embed_02.png)

3. Enregistrez le rapport dans **Power BI Report Server**. 

    ![Enregistrement PBI RS](media/quickstart-embed/quickstart_embed_03.png)

4. Affichez le rapport dans le portail web Power BI Report Server.

    ![Portail web](media/quickstart-embed/quickstart_embed_04.png)

### <a name="capture-the-url-parameter"></a>Capturer le paramètre d’URL

Une fois que vous avez votre URL, vous pouvez créer un iFrame dans une page SharePoint pour y héberger le rapport. Pour les URL de rapport Power BI Report Server, vous devez ajouter le paramètre de chaîne de requête suivant afin d’incorporer votre rapport dans un iFrame SharePoint : `?rs:embed=true`.

   Par exemple :
    ``` 
    https://myserver/reports/powerbi/Sales?rs:embed=true
    ```
## <a name="embed-the-report-in-a-sharepoint-iframe"></a>Incorporer le rapport dans un iFrame SharePoint

1. Accédez à une page **Contenu du site** SharePoint.

    ![Page Contenu du site](media/quickstart-embed/quickstart_embed_05.png)

2. Sélectionnez la page où vous souhaitez ajouter votre rapport.

    ![Application page Contenu du site](media/quickstart-embed/quickstart_embed_06.png)

3. Sélectionnez l’icône en forme de roue dentée située en haut à droite, puis sélectionnez **Modifier la page**.

    ![Option Modifier la page](media/quickstart-embed/quickstart_embed_07.png)

4. Sélectionnez **Ajouter un composant WebPart**.

5. Sous **Catégories**, sélectionnez **Média et contenu**. Sous **Composants WebPart**, sélectionnez **Éditeur de contenu**, puis sélectionnez **Ajouter**.

    ![Sélectionner un composant WebPart dans l’éditeur de contenu](media/quickstart-embed/quickstart_embed_09.png)

6. Sélectionnez **Cliquez ici pour ajouter un nouveau contenu**.

7. Dans le menu supérieur, sélectionnez **Mettre le texte en forme**, puis sélectionnez **Modifier la source**.

     ![Modifier la source](media/quickstart-embed/quickstart_embed_11.png)

8. Dans la fenêtre **Modifier la source**, collez votre code iFrame dans **Source HTML**, puis sélectionnez **OK**.

    ![Code iFrame](media/quickstart-embed/quickstart_embed_12.png)

     Par exemple :
     ```html
     <iframe width="800" height="600" src="https://myserver/reports/powerbi/Sales?rs:embed=true" frameborder="0" allowFullScreen="true"></iframe>
     ```

9. Dans le menu supérieur, sélectionnez **Page**, puis sélectionnez **Arrêter la modification**.

    ![Arrêter la modification](media/quickstart-embed/quickstart_embed_13.png)

    Le rapport s’affiche dans la page.

    ![Exemple iFrame](media/quickstart-embed/quickstart_embed_01.png)

## <a name="next-steps"></a>Étapes suivantes

- [Créer un rapport Power BI pour Power BI Report Server](quickstart-create-powerbi-report.md)  
- [Créer un rapport paginé pour Power BI Report Server](quickstart-create-paginated-report.md)  

D’autres questions ? [Posez vos questions à la Communauté Power BI](https://community.powerbi.com/). 