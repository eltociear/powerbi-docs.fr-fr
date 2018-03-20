---
title: "Créer des packs de contenu de modèle dans Power BI"
description: "Création d’un pack de contenu de modèle"
services: powerbi
documentationcenter: 
author: markingmyname
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
ms.date: 10/09/2017
ms.author: maghan
ms.openlocfilehash: bfed948be385439d33b335b08da68b103cd7c1b8
ms.sourcegitcommit: ee5d044db99e253c27816e0ea6bdeb9e39a2cf41
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/08/2018
---
# <a name="author-template-content-packs-in-power-bi"></a>Créer des packs de contenu de modèle dans Power BI
La création d’un pack de contenu de modèle implique l’utilisation de Power BI Desktop et PowerBI.com. Il existe quatre composants pour votre pack de contenu :

* Les requêtes vous permettent de [connecter](../desktop-connect-to-data.md) et [transformer](../desktop-query-overview.md) les données, ainsi que de définir les [paramètres](https://powerbi.microsoft.com/blog/deep-dive-into-query-parameters-and-power-bi-templates/)  
* Le modèle de données vous permet de créer les [relations](../desktop-create-and-manage-relationships.md), [mesures](../desktop-measures.md) et améliorations Q&R  
* Les [pages](../desktop-report-view.md) de rapport comprennent des éléments visuels et des filtres pour vous fournir des analyses sur vos données  
* Le [tableau de bord](../service-dashboards.md) et les [vignettes](../service-dashboard-create.md) vous offrent une vue d’ensemble des analyses incluses  

Vous connaissez peut-être chacun de ces éléments en tant que fonctionnalités Power BI existantes. Lors de la création d’un pack de contenu, d’autres points sont à prendre en compte pour chaque aspect. Consultez la section suivante pour plus de détails.

<a name="queries"></a>

## <a name="queries"></a>Requêtes
Pour les packs de contenu de modèle, les requêtes développées dans Power BI Desktop sont utilisées pour vous connecter à votre source de données et importer des données. Ces requêtes sont nécessaires pour renvoyer un schéma cohérent, et elles sont prises en charge pour l’actualisation des données planifiée (les requêtes directes ne sont pas prises en charge).

Les packs de contenu de modèle prennent en charge une seule source de données, aussi définissez vos requêtes avec soin. Une source de données est définie en tant que source qui requiert la même authentification. Vous pouvez effectuer plusieurs appels d’API dans différentes requêtes si tous les appels ont lieu vers le même point de terminaison d’API et utilisent la même authentification. Les packs de contenu Power BI ne prennent pas en charge plusieurs sources qui exigent différentes authentifications.

### <a name="connect-to-your-api"></a>Vous connecter à votre API
Pour commencer, vous devez vous connecter à votre API à partir de Power BI Desktop pour commencer à créer vos requêtes.

Vous pouvez utiliser les connecteurs de données prêts à l’emploi disponibles dans Power BI Desktop pour vous connecter à votre API. Vous pouvez utiliser le connecteur de données web (Obtenir des données -> Web) pour vous connecter à votre API REST ou le connecteur OData (Obtenir des données -> Flux OData) pour vous connecter à votre flux OData. Notez que ces connecteurs fonctionnent seulement si votre API prend en charge l’authentification de base.

> [!NOTE]
> Si votre API utilise d’autres types d’authentification, tels que OAuth 2.0 ou Clé d’API web, vous devez développer votre propre connecteur de données pour que Power BI Desktop se connecte et s’authentifie correctement auprès de votre API. Pour plus d’informations sur la façon de développer votre propre connecteur de données pour votre pack de contenu, consultez la documentation sur les connecteurs de données disponible [ici](https://aka.ms/DataConnectors). 
> 
> 

### <a name="consider-the-source"></a>Considérer la source
Les requêtes définissent les données comprises dans le modèle de données. Selon la taille de votre système, ces requêtes doivent également inclure des filtres pour garantir que vos clients manipulent des données de taille gérable pour votre scénario d’application professionnelle.

Les packs de contenu Power BI peuvent exécuter plusieurs requêtes en parallèle, et pour plusieurs utilisateurs simultanément.  Planifiez votre stratégie de limitation et de simultanéité, et demandez-nous comment rendre votre pack de contenu résistant aux pannes.

### <a name="schema-enforcement"></a>Application du schéma
Assurez-vous que vos requêtes résistent aux modifications dans votre système, car les modifications de schéma lors de l’actualisation peuvent nuire au modèle. Si la source peut renvoyer un résultat de schéma de valeur null/vide pour certaines requêtes, considérez le renvoi d’une table vide ou de messages d’erreur personnalisés, qui seront compréhensibles pour les utilisateurs.

### <a name="parameters"></a>Paramètres
Les [paramètres](https://powerbi.microsoft.com/blog/deep-dive-into-query-parameters-and-power-bi-templates/) dans Power BI Desktop permettent aux utilisateurs de fournir des valeurs d’entrée qui personnalisent les données récupérées par l’utilisateur. Considérez les paramètres à l’avance pour éviter d’avoir à retravailler après avoir consacré du temps à la création de requêtes ou rapports détaillés.

> [!NOTE]
> Les packs de contenu de modèle prennent uniquement en charge les paramètres texte pour le moment. Les autres types de paramètres peuvent être utilisés lors du développement, mais lors de la partie de [test](template-content-pack-testing.md#templates), toutes les valeurs fournies par les utilisateurs seront littérales.
> 
> 

### <a name="additional-query-tips"></a>Conseils supplémentaires pour les requêtes
* Veillez à bien saisir tous les noms de colonnes  
* Les colonnes doivent avoir des noms informatifs (voir Q&R)  
* Pour la logique partagée, considérez l’utilisation de fonctions ou de requêtes  
* Les niveaux de confidentialité ne sont pas actuellement pris en charge dans le service : si vous recevez une invite de commande concernant les niveaux de confidentialité, vous pourriez avoir à réécrire la requête pour utiliser des chemins d’accès relatifs  

## <a name="data-model"></a>Modèle de données
Un modèle de données bien défini garantit que vos clients peuvent facilement et intuitivement interagir avec le pack de contenu. Créez le modèle de données dans Power BI Desktop.

> [!NOTE]
> Une grande partie de la modélisation de base (saisie, noms de colonnes) doit être effectuée avec des [requêtes](#queries).
> 
> 

### <a name="qa"></a>Questions/Réponses (Q&R)
La modélisation affecte également la façon dont les Q&R peuvent fournir des résultats pour vos clients. Veillez à ajouter des synonymes pour les colonnes fréquemment utilisées et à nommer les colonnes correctement dans les [requêtes](#queries).

### <a name="additional-data-model-tips"></a>Conseils supplémentaires pour les modèles de données
* La mise en forme est appliquée à toutes les colonnes de valeur
    >[!NOTE]
    >Les types doivent être appliqués dans la requête.  
* Toutes les mesures doivent avoir une mise en forme appliquée  
* Le résumé par défaut doit être défini. En particulier « Ne pas résumer », le cas échéant (pour les valeurs uniques, par exemple)  
* La catégorie de données a été définie, le cas échéant  
* Les relations sont définies comme nécessaire  

## <a name="reports"></a>Rapports
Les pages du rapport offrent des informations supplémentaires sur les données incluses dans votre pack de contenu. Utilisez les pages des rapports pour répondre aux questions professionnelles essentielles auxquelles votre pack de contenu essaye de répondre. Créez le rapport à l’aide de Power BI Desktop.

> [!NOTE]
> Un seul rapport peut être inclus dans un pack de contenu, exploitez les différentes pages pour appeler des sections particulières de votre scénario.
> 
> 

### <a name="additional-report-tips"></a>Conseils supplémentaires pour les rapports
* Utilisez plusieurs éléments visuels par page pour le filtrage croisé  
* Alignez les éléments visuels soigneusement (sans chevauchement)  
* Définissez la disposition sur 4:3 ou 16:9  
* Toutes les agrégations présentées sont cohérentes numériquement (moyennes, valeurs uniques)  
* Le découpage produit des résultats rationnels  
* Le logo est présent au moins sur le premier rapport  
* Les éléments sont autant que possible dans le schéma de couleurs du client  

<a name="dashboard"></a>

## <a name="dashboard"></a>tableau de bord
Le tableau de bord est le principal point d’interaction avec votre pack de contenu pour vos clients. Il doit inclure une vue d’ensemble du contenu inclus, en particulier les mesures les plus importantes de votre scénario d’application professionnelle.

Pour créer un tableau de bord pour votre pack de contenu de modèle, téléchargez simplement votre PBIX via Obtenir des données > Fichiers, ou publiez directement à partir de Power BI Desktop.

> [!NOTE]
> Les packs de contenu de modèle nécessitent actuellement un rapport unique et un jeu de données par pack de contenu. N’épinglez pas le contenu de plusieurs rapports/jeux de données sur le tableau de bord utilisé dans le pack de contenu.
> 
> 

### <a name="additional-dashboard-tips"></a>Conseils supplémentaires pour le tableau de bord
* Conservez le même thème lors de l’épinglage de sorte que les vignettes sur votre tableau de bord soient cohérentes  
* Épinglez un logo au thème afin que les consommateurs sachent d’où provient le pack  
* La disposition suggérée pour travailler avec la plupart des résolutions d’écran est 5-6 petites vignettes de large  
* Toutes les vignettes d’un tableau de bord doivent avoir des titres/sous-titres appropriés  
* Considérez les regroupements dans le tableau de bord pour différents scénarios, verticalement ou horizontalement  

<a name="restrictions"></a>

## <a name="summary-of-restrictions"></a>Résumé des restrictions
Comme indiqué dans les sections ci-dessus, seuls les packs de contenu de modèle disposent d’un ensemble de restrictions :  

| Pris en charge | *Non pris en charge* |
| --- | --- |
| Jeux de données intégrés à PBI Desktop |*Jeux de données d’autres packs de contenu ou entrées comme les fichiers Excel* |
| Source de données prise en charge pour l’actualisation planifiée des données sur cloud |*Requêtes directes et connectivité locale non prises en charge* |
| Requêtes renvoyant un schéma cohérent ou des erreurs, le cas échéant |*Schémas dynamiques ou personnalisés* |
| Une source de données par jeu de données |*Sources de données multiples, dont les mashup et URL détectées comme sources de données multiples* |
| Paramètres de type texte |*Autres types de paramètres (dont la date) ou « liste de valeurs autorisées »* |
| Un tableau de bord, rapport ou jeu de données |*Plusieurs tableaux de bord, rapports ou jeux de données* |

## <a name="next-step"></a>Étape suivante
[Test et envoi du pack de contenu](template-content-pack-testing.md)

