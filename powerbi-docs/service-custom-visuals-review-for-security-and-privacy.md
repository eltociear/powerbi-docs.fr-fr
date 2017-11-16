---
title: "Examen des éléments visuels personnalisés pour la sécurité et la confidentialité"
description: "Avant d’activer un visuel personnalisé, vous devez l’examiner afin de déterminer s’il présente un risque en matière de sécurité et de confidentialité et s’il répond aux standards de votre organisation."
services: powerbi
documentationcenter: 
author: guyinacube
manager: kfile
backup: 
editor: 
tags: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 09/05/2017
ms.author: asaxton
ms.openlocfilehash: 40c2c713615f6e9e5378d36b6b228dc864bcb57c
ms.sourcegitcommit: 284b09d579d601e754a05fba2a4025723724f8eb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/15/2017
---
# <a name="review-custom-visuals-for-security-and-privacy"></a>Examen des éléments visuels personnalisés pour la sécurité et la confidentialité
Avant d’activer un visuel personnalisé, vous devez l’examiner afin de déterminer s’il présente un risque en matière de sécurité et de confidentialité et s’il répond aux standards de votre organisation.

## <a name="enable-a-custom-visual"></a>Activation d’un élément visuel personnalisé
<a name="enable"></a>Un élément visuel personnalisé dans le rapport est désactivé jusqu’à ce que vous activiez l’option **Activer les visuels personnalisés**, comme illustré ci-dessous.  

![](media/service-custom-visuals-review-for-security-and-privacy/emptyvisual.png)

## <a name="considerations-before-you-enable-a-custom-visual"></a>Considérations préalables à l’activation d’un élément visuel personnalisé
<a name="considerations"></a>

> [!WARNING]
> Un élément visuel personnalisé peut contenir du code présentant des risques en matière de sécurité ou de confidentialité. Par conséquent, tout élément visuel personnalisé dans le rapport est désactivé jusqu’à ce que vous choisissiez d’activer les éléments visuels personnalisés. Voici quelques aspects à prendre en considération pour décider de l’opportunité d’activer un élément visuel personnalisé :
> 
> 

1. Assurez-vous que vous pouvez avoir confiance dans l’auteur et dans la source des éléments visuels personnalisés utilisés dans le rapport.
2. Si vous ne savez que faire, nous vous conseillons de contacter votre équipe informatique afin de déterminer si vous devez activer les éléments visuels personnalisés pour les rapports que vous consultez.
3. Si quelqu’un partage avec vous un rapport contenant un élément visuel personnalisé, même s’il s’agit d’un étroit collaborateur, ne vous sentez pas obligé d’activer l’élément visuel personnalisé. Vous pouvez prendre du recul et évaluer si cet élément est indispensable pour la tâche en cours. Si l’élément visuel personnalisé ne vous inspire pas confiance, vous pouvez toujours demander à recevoir un rapport exempt de cet élément.

## <a name="security-best-practices-for-it-professionals-to-enable-a-custom-visual"></a>Meilleures pratiques de sécurité en relation avec l’activation d’un élément visuel personnalisé pour les professionnels de l’informatique
<a name="security"></a>

> [!WARNING]
> Un élément visuel personnalisé peut contenir du code présentant des risques en matière de sécurité ou de confidentialité. Par conséquent, tout élément visuel personnalisé dans le rapport est désactivé jusqu’à ce que vous choisissiez d’activer les éléments visuels personnalisés. Il existe plusieurs pratiques recommandées que vous pouvez suivre pour évaluer un élément visuel personnalisé en relation avec la sécurité et la confidentialité.
> 
> 

1. Mettez en place un processus d’analyse des éléments visuels personnalisés au sein de votre organisation. Après analyse, les éléments visuels personnalisés seraient partagés avec les utilisateurs internes via un site web interne, par exemple, une bibliothèque de documents SharePoint ou un document OneNote.
2. Fournissez aux utilisateurs professionnels des instructions sur l’utilisation appropriée des éléments visuels personnalisés, et une messagerie de groupe à laquelle ils puissent adresser des questions relatives à la sécurité et à la confidentialité.
3. Évaluez le code JavaScript dans le fichier pbiviz de l’élément visuel personnalisé.

**Pour évaluer le code JavaScript dans un élément visuel personnalisé**

Un élément visuel personnalisé utilise du code JavaScript et peut donc présenter des risques en matière de sécurité ou de confidentialité. Si vous recevez un élément visuel personnalisé ou un fichier pbix contenant un élément visuel personnalisé de source inconnue, vous souhaiterez probablement examiner le code JavaScript pour voir s’il est sûr.

Pour évaluer le code JavaScript d’un élément visuel personnalisé, extrayez ce code. Voici comment extraire le code :  

1. Enregistrez le fichier .pbiviz dans un dossier.
2. Renommez le fichier au format .zip.
3. Extrayez le fichier .zip dans un dossier local.

## <a name="custom-visual-file-contents"></a>Contenu du fichier d’élément visuel personnalisé
Voici le contenu d’un fichier pbiviz :

| **Fichier** | **Description** |
|:--- |:--- |
| ./package.json |Fichier manifeste indiquant les fichiers à charger pour l’élément visuel personnalisé. |
| ./resources |Contient la feuille de style CSS, le code TypeScript et le code JavaScript utilisés par l’élément visuel personnalisé. |
| ./resources/&lt;nom&gt; |&lt;nom&gt; est le nom de l’élément visuel personnalisé. |
| ./resources/&lt;nom&gt;.css |Fichier de ressources css pour l’élément visuel personnalisé. |
| ./resources/&lt;nom&gt;.js |Code exécuté quand un utilisateur clique sur Activer les visuels personnalisés ou après qu’il a importé un élément visuel personnalisé. Avertissement : un code JavaScript peut présenter des risques en matière de sécurité ou de confidentialité. |
| ./resources/&lt;nom&gt;.ts |Code source JavaScript de l’élément visuel au format TypeScript. Avertissement : un code JavaScript ou TypeScript peut présenter des risques en matière de sécurité ou de confidentialité. |
| ./resources/&lt;nom&gt;.png |Icône affichée à l’utilisateur pour l’élément visuel. |

Après avoir extrait le fichier pbiviz, vous pouvez évaluer le code. Voici quelques meilleures pratiques et menaces à rechercher.

## <a name="best-practices-to-evaluate-the-javascript-or-typescript-code"></a>Meilleures pratiques pour évaluer du code JavaScript ou TypeScript
Un code **JavaScript** ou **TypeScript** peut présenter des risques en matière de sécurité ou de confidentialité. Voici quelques meilleures pratiques et menaces à rechercher.

### <a name="best-practices-to-evaluate-javascript-code"></a>Meilleures pratiques pour évaluer du code JavaScript
* Évaluez toujours le contenu du fichier .js. Il s’agit du code qui s’exécute. Il se peut que le contenu du fichier .ts ne se compile pas en fichier .js inclus dans l’élément visuel personnalisé.
* Évaluez toujours le contenu du fichier .ts. Vous pouvez charger le fichier .ts dans les **outils de développement**, exporter l’élément visuel et comparer le fichier .js qui en résulte dans le fichier .pbiviz nouvellement créé au fichier .js d’origine contenu dans l’élément visuel
* Vérifiez que l’icône de l’élément visuel personnalisé ne ressemble pas trop à d’autres éléments visuels avec lesquels l’utilisateur est familiarisé.
* Évaluez toujours l’élément visuel dans un compte test disposant de privilèges minimaux et n’ayant pas accès à des données sensibles. Dans l’idéal, le compte test doit être un compte local dépourvu d’informations de connexion à des services autres que Power BI.

### <a name="threats-to-look-for-in-javascript-code"></a>Menaces à rechercher dans le code JavaScript
* Vérifiez l’activité réseau lorsque l’élément visuel est utilisé tant en mode édition qu’en mode affichage. Assurez-vous que les demandes effectuées sont acceptables. Vous ne devriez pas observer de demandes adressées à des ressources extérieures au domaine Power BI, sauf si l’auteur de l’élément visuel vous a informé de cela par avance.
* Toutes les données qui sortent du domaine Power BI doivent correspondre à vos attentes en relation avec une utilisation « normale ». Par exemple, si l’élément visuel implémente un lecteur vidéo qui utilise un iFrame pour afficher une vidéo provenant d’un autre site, certaines informations doivent figurer dans les demandes IFrame pour produire un rendu correct de l’image vidéo. En revanche, si vous constatez que le jeu de données entier est envoyé via le câble, il peut être utile d’examiner si cela est indispensable et souhaitable.
* Vérifiez si des informations d’identification personnelle sont envoyées ou stockées par l’élément visuel personnalisé.
* Vérifiez si l’élément visuel personnalisé essaie d’accéder à des ressources de l’ordinateur local, par exemple, pour écrire des fichiers sur le disque ou accéder aux cookies.
* Vérifiez si l’élément visuel personnalisé contient du code obscur ou sans un objectif clair.
* Enregistrez une copie de chaque élément visuel examiné par le passé.
* Si vous examinez une mise à jour d’un élément visuel examiné précédemment, veillez à vérifier les modifications. Examinez toujours les mises à jour avec la même rigueur que lors de la première analyse de l’élément visuel
* Si vous détectez un élément suspect ou peu clair, veuillez nous contacter. Nous sommes là pour vous aider.

## <a name="next-steps"></a>Étapes suivantes
[Visualisations dans Power BI](power-bi-report-visualizations.md)  
[Visualisations personnalisées dans Power BI](power-bi-custom-visuals.md)  
[Télécharger et utiliser les visuels personnalisés de l’Office Store](service-custom-visuals-office-store.md)  
[Ajout de visualisations personnalisées à un rapport (Power BI Desktop)](power-bi-custom-visuals-use.md)  
[Ajout d’une visualisation personnalisée à un rapport (service Power BI)](power-bi-report-add-custom-visual.md)  
[Publier des visuels personnalisés dans l’Office Store](developer/office-store.md)  
[Bien démarrer avec les outils de développement de visuels personnalisés](service-custom-visuals-getting-started-with-developer-tools.md)  
[Comment certifier un visuel personnalisé](power-bi-custom-visuals-certified.md)    
[Vidéo : Création de visualisations personnalisées pour Power BI avec Sachin Patney et Nico Cristache](https://www.youtube.com/watch?v=kULc2VbwjCc)  

D’autres questions ? [Essayez d’interroger la communauté Power BI](http://community.powerbi.com/)

