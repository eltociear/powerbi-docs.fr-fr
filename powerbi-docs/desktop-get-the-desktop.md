---
title: Obtenir Power BI Desktop
description: Télécharger et installer Power BI Desktop
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 05/02/2018
ms.author: davidi
LocalizationGroup: Get started
ms.openlocfilehash: eee341314b309eda119dd282eafd18188f8fdfd0
ms.sourcegitcommit: 638de55f996d177063561b36d95c8c71ea7af3ed
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/17/2018
ms.locfileid: "34286632"
---
# <a name="get-power-bi-desktop"></a>Obtenir Power BI Desktop
**Power BI Desktop** vous permet de créer des requêtes, des modèles et des rapports avancés qui visualisent des données. Avec **Power BI Desktop**, vous pouvez créer des modèles de données et des rapports et partager votre travail en le publiant sur le service Power BI.  Le téléchargement de **Power BI Desktop** est gratuit.

Vous pouvez obtenir **Power BI Desktop** de deux façons. Celles-ci sont décrites dans les sections suivantes :

* **Télécharger** directement (package MSI téléchargé et installé sur votre ordinateur)
* Installer en tant qu’application sur le **Microsoft Store**

Quelle que soit l’option choisie, vous obtenez la dernière version de **Power BI Desktop** sur votre ordinateur. Il existe toutefois quelques différences qui sont décrites dans les sections suivantes.

## <a name="download-power-bi-desktop"></a>Télécharger Power BI Desktop
Pour télécharger la version la plus récente de **Power BI Desktop**, cliquez sur l’icône de téléchargement en haut à droite du service Power BI et sélectionnez **Power BI Desktop**.

![](media/desktop-get-the-desktop/getpbid_downloads.png)

Vous pouvez également télécharger la dernière version de Power BI Desktop en cliquant sur la page de téléchargement suivante :

* [**Téléchargement de Power BI Desktop** (versions 32 et 64 bits)](https://powerbi.microsoft.com/desktop).
  
  [![](media/service-admin-power-bi-security/PBI_Security_01.png)](https://powerbi.microsoft.com/desktop)

Quel que soit le type de téléchargement, une fois que vous avez téléchargé **Power BI Desktop**, vous êtes invité à exécuter le fichier d’installation :

![](media/desktop-get-the-desktop/getpbid_3.png)

**Power BI Desktop** est installé en tant qu’application et s’exécute sur votre bureau.

![](media/desktop-get-the-desktop/designer_gsg_install.png)

> [!NOTE]
> L’installation de la version téléchargée (MSI) et de la version du **Microsoft Store** de **Power BI Desktop** sur le même ordinateur (parfois appelée installation *côte à côte*) n’est pas prise en charge.
> 
> 

## <a name="install-as-an-app-from-the-microsoft-store"></a>Installer en tant qu’application sur le Microsoft Store
Vous pouvez également récupérer **Power BI Desktop** sur le Microsoft Store en cliquant sur le lien suivant :

* [Installer **Power BI Desktop** sur le **Microsoft Store**](http://aka.ms/pbidesktopstore)

![](media/desktop-get-the-desktop/getpbid_04.png)

Il peut être intéressant de récupérer **Power BI Desktop** sur le Microsoft Store pour plusieurs raisons :

* **Mises à jour automatiques** : Windows télécharge automatiquement la dernière version en arrière-plan dès qu’elle est disponible. Votre version est donc toujours à jour.
* **Téléchargements plus petits** : le **Microsoft Store** s’assure que seuls les composants qui ont été modifiés lors de la mise à jour sont téléchargés sur votre ordinateur. Le téléchargement de chaque mise à jour s’en trouve donc réduit.
* **Le privilège d’administration n’est pas obligatoire** : quand vous téléchargez le fichier MSI directement et que vous l’installez, vous devez être administrateur pour que l’installation s’effectue correctement. Si vous vous procurez **Power BI Desktop** sur le Microsoft Store, le privilège Administrateur n’est *pas* requis.
* **Déploiement activé** : la version du **Microsoft Store** est plus facile à *déployer* auprès des utilisateurs de l’organisation. Elle peut mettre à disposition **Power BI Desktop** par le biais du **Microsoft Store pour Entreprises**.
* **Détection de la langue** : la version du **Microsoft Store** comprend toutes les langues prises en charge et vérifie les langues utilisées sur l’ordinateur à chaque démarrage. Cela affecte également la localisation des modèles créés dans **Power BI Desktop**, par exemple les hiérarchies de dates intégrées correspondent à la langue que **Power BI Desktop** utilisait lorsque le fichier .pbix a été créé.

L’installation de **Power BI Desktop** sur le Microsoft Store fait l’objet de quelques limitations et mises en garde :

* Si vous utilisez le connecteur SAP, vous devrez peut-être déplacer vos fichiers de pilote SAP vers le dossier *Windows\System32*.
* L’installation de **Power BI Desktop** sur le Microsoft Store ne copie pas les paramètres utilisateur de la version MSI. Vous devrez peut-être vous reconnecter à vos dernières sources de données et entrer à nouveau vos identifiants de source de données. 

> [!NOTE]
> L’installation de la version téléchargée (MSI) et de la version du **Microsoft Store** de **Power BI Desktop** sur le même ordinateur (parfois appelée installation *côte à côte*) n’est pas prise en charge. Il est recommandé de désinstaller manuellement **Power BI Desktop** avant de le télécharger sur le **Microsoft Store**.
> 
> [!NOTE]
> La version Power BI Report Server de **Power BI Desktop** est une installation distincte et différente des versions présentées dans cet article. Pour plus d’informations sur la version Report Server de **Power BI Desktop**, voir [Créer un rapport Power BI pour Power BI Report Server](report-server/quickstart-create-powerbi-report.md).
> 
> 

## <a name="using-power-bi-desktop"></a>Utilisation de Power BI Desktop
Quand vous lancez **Power BI Desktop**, un écran de *Bienvenue* s’affiche.

![](media/desktop-get-the-desktop/getpbid_05.png)

Si vous utilisez **Power BI Desktop** pour la première fois (si l’installation n’est pas une mise à niveau), vous êtes invité à remplir un formulaire et à répondre à quelques questions ou à vous connecter au **service Power BI** avant de continuer.

Dès lors, vous pouvez commencer à créer des modèles de données ou des rapports, puis les partager avec d’autres utilisateurs sur le service Power BI. Consultez les liens **plus d’informations** référencés à la fin de cet article pour être redirigé vers des guides qui peuvent vous aider à maîtriser **Power BI Desktop**.

## <a name="minimum-requirements"></a>Configuration minimale requise
La liste suivante présente la configuration minimale requise pour exécuter **Power BI Desktop** :

* Windows 7/ Windows Server 2008 R2 ou version ultérieure
* .NET 4.5
* Internet Explorer 9 ou version ultérieure
* **Mémoire (RAM) :** au moins 1 Go de disponible (1,5 Go ou plus recommandés).
* **Affichage :** résolution minimale de 1440 x 900 (1600 x 900 ou 16:9 recommandée). Les résolutions inférieures telles que 1024 x 768 ou 1280 x 800 ne sont pas recommandées, car certains contrôles comme la fermeture de l’écran de démarrage apparaissent au-delà de ces résolutions.
* **Paramètres d’affichage de Windows :** si vos paramètres d’affichage sont définis pour modifier la taille du texte, les applications et les autres éléments de plus de 100 %, il est possible que vous ne puissiez pas afficher certaines boîtes de dialogue qui doivent être fermées ou auxquelles vous devez répondre pour pouvoir continuer en utilisant **Power BI Desktop**. Si vous rencontrez ce problème, vérifiez vos **Paramètres d’affichage** en accédant à **Paramètres > Système > Affichage** dans Windows, puis utilisez le curseur pour rétablir les paramètres d’affichage sur 100 %.
* **Processeur :** 1 gigahertz (GHz) ou plus rapide (processeur x86 ou x64 bits recommandé).

## <a name="next-steps"></a>Étapes suivantes
Après avoir installé **Power BI Desktop**, consultez le contenu suivant pour apprendre à maîtriser l’application :

* [Prise en main de Power BI Desktop](desktop-getting-started.md)
* [Présentation des requêtes dans Power BI Desktop](desktop-query-overview.md)
* [Sources de données dans Power BI Desktop](desktop-data-sources.md)
* [Se connecter aux données dans Power BI Desktop](desktop-connect-to-data.md)
* [Mettre en forme et combiner des données dans Power BI Desktop](desktop-shape-and-combine-data.md)
* [Tâches courantes relatives aux requêtes dans Power BI Desktop](desktop-common-query-tasks.md)   

