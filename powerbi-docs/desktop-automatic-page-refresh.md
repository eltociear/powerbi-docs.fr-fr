---
title: Actualisation automatique des pages dans Power BI Desktop (préversion)
description: Découvrez comment actualiser automatiquement des pages pour les sources DirectQuery dans Power BI Desktop
author: davidiseminger
ms.reviewer: ''
ms.custom: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 11/26/2019
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 50daa90f937a9d1c7081d9b22e3c743da950945c
ms.sourcegitcommit: fe9253a6021b9e198afa28aa9c670c3bacf59674
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2019
ms.locfileid: "74548561"
---
# <a name="automatic-page-refresh-in-power-bi-desktop-preview"></a>Actualisation automatique des pages dans Power BI Desktop (préversion)

Lors de la surveillance des événements critiques, il est important que les données soient actualisées dès que les données source sont mises à jour. Par exemple, dans le secteur de la fabrication, il est essentiel de savoir quand un ordinateur ne fonctionne pas correctement ou est sur le point de connaître une défaillance.

La fonctionnalité d’actualisation automatique de la page de Power BI permet à votre page de rapport active de rechercher de nouvelles données, à une cadence prédéfinie, pour les sources [DirectQuery](https://docs.microsoft.com/power-bi/desktop-directquery-about).

## <a name="using-automatic-page-refresh"></a>Utilisation de l’actualisation automatique de la page

Pour cette version préliminaire, vous devez activer la fonctionnalité d’actualisation automatique de la page dans Power BI Desktop. Accédez à **Fichier > Options et paramètres**, puis sélectionnez **Options** et sélectionnez **Fonctionnalités en version préliminaire** dans le volet de gauche. Activez la fonctionnalité en cochant la case à côté de *Actualisation automatique de la page*. L’actualisation automatique de la page est disponible uniquement pour les sources de données DirectQuery.

Pour utiliser l’actualisation automatique de la page, sélectionnez la page de rapport pour laquelle vous souhaitez activer l’actualisation. Dans le volet **Visualisations**, sélectionnez l’icône de **Mise en forme** (un rouleau de peinture) et recherchez **Actualisation de la page** en bas du volet. 

![Emplacement d’Actualisation de la page](media/desktop-automatic-page-refresh/automatic-page-refresh-01.png)

L’image suivante montre la carte **Actualisation de la page**. Les explications pour les éléments numérotés sont décrites dans les paragraphes suivants :

![Carte Actualisation de page](media/desktop-automatic-page-refresh/automatic-page-refresh-02.png)

1.  Curseur d’actualisation automatique de la page : active ou désactive l’actualisation de la page
2.  Valeur de l’intervalle d’actualisation de la page : valeur numérique de l’intervalle d’actualisation
3.  Unité d’intervalle d’actualisation de la page : l’unité de l’intervalle d’actualisation de la page

Ici, vous pouvez activer l’actualisation de la page et sélectionner la durée d’actualisation. La valeur par défaut est de 30 minutes, et l’intervalle d’actualisation minimal est d’une seconde). Votre rapport commence à s’actualiser à l’intervalle que vous avez défini. 

## <a name="determining-the-page-refresh-interval"></a>Détermination de l’intervalle d’actualisation de la page

Lorsque l’actualisation automatique de la page est activée, Power BI Desktop envoie en permanence des requêtes à votre source DirectQuery. Il y aura un délai entre l’envoi de la requête et l’obtention des données renvoyées. Par conséquent, pour des intervalles d’actualisation courts, vous devez vérifier que les requêtes renvoient correctement les données interrogées dans l’intervalle configuré. Si les données ne sont pas retournées dans l’intervalle, vous créez des situations où les visuels sont mis à jour moins souvent que ce qui est configuré.

En guise de meilleure pratique, l’intervalle d’actualisation doit être au moins identique à celui attendu pour le taux d’arrivée de nouvelles données :

* Si de nouvelles données arrivent à la source toutes les 20 minutes, votre intervalle d’actualisation ne peut pas être inférieur à 20 minutes. 

* Si de nouvelles données arrivent chaque seconde, l’intervalle doit être défini sur une seconde. 


Pour des intervalles d’actualisation inférieurs à une seconde, vous devez également tenir compte du type de la source de données de requête directe, de la charge créée par vos requêtes, de la distance entre les visionneuses de rapports et du centre de données de la capacité, etc. 

Vous pouvez estimer cela à l’aide de l’analyseur de performances dans Power BI Desktop, ce qui vous permet de vérifier si chaque requête visuelle a suffisamment de temps pour retourner le résultat de la source, et où les choses prennent du temps. En fonction des résultats de l’analyseur de performances, vous pouvez ajuster et apporter des modifications à la source de données, ou vous pouvez faire des essais avec d’autres visuels et mesures dans votre rapport.

L’image suivante montre les résultats d’une DirectQuery dans l’analyseur de performances :

![Résultats de l’analyseur de performances](media/desktop-automatic-page-refresh/automatic-page-refresh-03.png)

Examinons d’autres caractéristiques de cette source de données. 

1.  Les données arrivent avec un rythme de deux secondes. 
2.  L’analyseur de performances affiche un temps maximal de requête + affichage d’environ 4,9 secondes (4688 millisecondes). 
3.  La source de données est configurée pour gérer environ 1000 requêtes simultanées par seconde. 
4.  Environ 10 utilisateurs peuvent afficher le rapport simultanément.

Ainsi, les résultats sont les suivants :

* **5 visuels x 10 utilisateurs = environ 50 requêtes**

Ce calcul entraîne une charge bien supérieure à celle que la source de données peut prendre en charge. Les données arrivent à un rythme de deux secondes, ce qui doit être votre taux d’actualisation. Toutefois, étant donné que l’exécution de la requête prend environ cinq secondes, nous devons la définir sur plus de cinq secondes. 

Notez également que ce résultat peut différer lorsque vous publiez votre rapport sur le service, dans la mesure où le rapport utilisera l’instance Analysis Services hébergée dans le cloud. Vous souhaiterez peut-être ajuster vos taux d’actualisation en conséquence. 

Pour prendre en compte les requêtes et la cadence de l’actualisation, Power BI exécute uniquement la requête d’actualisation suivante lorsque toutes les requêtes d’actualisation restantes sont terminées. Par conséquent, même si l’intervalle d’actualisation est plus faible que le temps de traitement de vos requêtes, Power BI n’est actualisé qu’une fois les requêtes restantes terminées. 

Voyons ensuite comment vous pouvez potentiellement détecter et diagnostiquer les problèmes de performances en tant qu’administrateur de capacité. Vous pouvez également consulter la section **Forum aux questions sur l’actualisation automatique de la page**, plus loin dans cet article, pour voir des questions et des réponses sur les performances et la résolution des problèmes.

## <a name="automatic-page-refresh-in-the-power-bi-service"></a>Actualisation automatique de la page dans le service Power BI

Vous pouvez également définir des intervalles d’actualisation automatique de la page pour les rapports qui ont été créés dans Power BI Desktop et qui sont publiés dans le service Power BI. 

L’actualisation automatique de la page pour les rapports dans le service Power BI est configurée avec des étapes similaires à la configuration dans Power BI Desktop. Quand elle est configurée dans le service Power BI, l’actualisation automatique des pages prend aussi en charge le contenu [Power BI incorporé](developer/embedding.md). L’illustration suivante montre la configuration **d’actualisation de la page** pour le service Power BI :

![Actualisation automatique de la page dans le service Power BI](media/desktop-automatic-page-refresh/automatic-page-refresh-04.png)

1.  Curseur d’actualisation automatique de la page : active ou désactive l’actualisation de la page
2.  Valeur de l’intervalle d’actualisation de la page : valeur numérique de l’intervalle d’actualisation, doit être un nombre entier
3.  Unité d’intervalle d’actualisation de la page : l’unité de l’intervalle d’actualisation de la page

### <a name="page-refresh-intervals"></a>Intervalles d’actualisation de la page

Les intervalles d’actualisation de la page autorisés dans le service Power BI sont affectés par le type d’espace de travail du rapport. Cela s’applique à tous les rapports suivants :

* Publication d’un rapport dans un espace de travail pour lequel l’actualisation automatique de la page est activée
* Modification d’un intervalle d’actualisation de page se trouvant déjà dans un espace de travail
* Création d’un rapport directement dans le service

Power BI Desktop n’a aucune restriction pour l’intervalle d’actualisation ; son intervalle d’actualisation peut être aussi fréquent que chaque seconde. Toutefois, lorsque les rapports sont publiés sur le service Power BI, certaines restrictions s’appliquent et sont décrites dans les sections suivantes.

### <a name="restrictions-on-refresh-intervals"></a>Restrictions sur les intervalles d’actualisation

Dans le service Power BI, des restrictions d’actualisation automatique de la page s’appliquent en fonction de facteurs tels que l’espace de travail et l’utilisation ou non de services Premium.

Pour clarifier le fonctionnement, commençons par des informations générales sur les capacités et les espaces de travail :

Les **Capacités** sont un concept fondamental de Power BI ; elles représentent un ensemble de ressources (stockage, processeur et mémoire) utilisées pour héberger et distribuer du contenu Power BI. Les capacités sont partagées ou dédiées. Une **Capacité partagée** est partagée avec d’autres clients Microsoft, tandis qu’une **Capacité dédiée** est entièrement consacrée à un seul client. Les capacités dédiées sont présentées dans l’article [Gestion des capacités Premium](service-premium-capacity-manage.md).

Dans une capacité partagée, les charges de travail s’exécutent sur des ressources de calcul partagées avec d’autres clients. Étant donné que la capacité doit partager des ressources, des restrictions sont imposées pour s’assurer d’une *utilisation juste*, par exemple avec la définition d’une taille de modèle maximale (1 Go) et d’une fréquence d’actualisation quotidienne maximale (huit fois par jour).

Les **espaces de travail** Power BI résident dans des capacités et représentent des conteneurs de sécurité, de collaboration et de déploiement. Chaque utilisateur Power BI dispose d’un espace de travail personnel nommé **Mon espace de travail**. Des espaces de travail supplémentaires peuvent être créés pour activer la collaboration et le déploiement, et ceux-ci sont appelés **espaces de travail**. Par défaut, les espaces de travail, qui incluent également les espaces de travail personnels, sont créés dans une **capacité partagée**.

Voici quelques détails sur les deux scénarios d’espace de travail :

**Espaces de travail partagés** : pour les espaces de travail standard (les espaces de travail qui ne font pas partie d’une capacité Premium), l’actualisation automatique de la page a un intervalle minimal de 30 minutes (l’intervalle le plus bas autorisé).

**Espaces de travail Premium ** : la disponibilité de l’actualisation automatique de la page dans les espaces de travail Premium dépend des paramètres de charge de travail que votre administrateur Premium a configurés pour la capacité Power BI Premium. Il existe deux variables qui peuvent affecter votre capacité à configurer l’actualisation automatique de la page :

 1. *Activation/désactivation de la fonctionnalité* : Si votre administrateur de capacité a décidé de désactiver la fonctionnalité, vous ne pourrez pas configurer le type d’actualisation de page dans votre rapport publié.

 2. *Intervalle d’actualisation minimal* : Lors de l’activation de la fonctionnalité, votre administrateur de capacité doit configurer un intervalle d’actualisation minimal. Si votre intervalle est inférieur au minimum, le service Power BI remplace votre intervalle pour respecter l’intervalle minimal défini par votre administrateur de capacité.

Le tableau ci-dessous décrit en détail l’emplacement de cette fonctionnalité et les limites de chaque type de capacité et de [mode de stockage](service-dataset-modes-understand.md)

| Mode de stockage | Capacité dédiée | Capacité partagée |
| --- | --- | --- |
| Requête directe | **Pris en charge** – Oui. <br>**Intervalle minimal d'actualisation** : 1 seconde <br>**Remplacement par l’administrateur de capacité** : Oui. | **Pris en charge** – Oui. <br>**Intervalle minimal d'actualisation** : 30 minutes <br>**Remplacement par l’administrateur de capacité** : Non. |
| Importer | **Pris en charge** : Non. <br>**Intervalle minimal d'actualisation** : N/A. <br>**Remplacement par l’administrateur de capacité** : N/A. | **Pris en charge** : Non. <br>**Intervalle minimal d'actualisation** : N/A. <br>**Remplacement par l’administrateur de capacité** : N/A. |
| Mode mixte (DQ + autres) | **Pris en charge** – Oui. <br>**Intervalle minimal d'actualisation** : 1 seconde <br>**Remplacement par l’administrateur de capacité** : Oui. | **Pris en charge** – Oui. <br>**Intervalle minimal d'actualisation** : 30 minutes <br>**Remplacement par l’administrateur de capacité** : Non. |
| Live Connect AS | **Pris en charge** : Non. <br>**Intervalle minimal d'actualisation** : N/A. <br>**Remplacement par l’administrateur de capacité** : N/A. | **Pris en charge** : Non. <br>**Intervalle minimal d'actualisation** : N/A. <br>**Remplacement par l’administrateur de capacité** : N/A. |
| Live Connect PBI | **Pris en charge** : Non. <br>**Intervalle minimal d'actualisation** : N/A. <br>**Remplacement par l’administrateur de capacité** : N/A. | **Pris en charge** : Non. <br>**Intervalle minimal d'actualisation** : N/A. <br>**Remplacement par l’administrateur de capacité** : N/A. |

> [!NOTE]
> Lors de la publication de votre rapport avec actualisation automatique de la page de Power BI Desktop vers le service, vous devez fournir les informations d’identification de la source de données DirectQuery dans le menu de paramètres du jeu de données.

## <a name="considerations-and-limitations"></a>Considérations et limitations

Il y a quelques éléments à prendre en compte lors de l’utilisation de l’actualisation automatique de la page, dans Power BI Desktop ou dans le service Power BI.

* Les modes de stockage Importer, Connexion active et Push ne sont pas pris en charge pour l’actualisation automatique de la page.  
* Les modèles composites qui ont au moins une source de données DirectQuery sont pris en charge.
* Power BI Desktop n’a aucune restriction pour l’intervalle d’actualisation, qui peut être aussi fréquent que chaque seconde. Lorsque les rapports sont publiés sur le service Power BI, certaines restrictions s’appliquent, comme décrit précédemment dans ce document.

### <a name="performance-diagnostics"></a>Diagnostics des performances

L’actualisation automatique de la page est utile pour la surveillance des scénarios et l’exploration de données évoluant rapidement. Toutefois, cela peut parfois entraîner une charge excessive sur la capacité ou la source de données.

Pour éviter une charge excessive sur les sources de données, Power BI utilise les protections suivantes :

1. Toutes les requêtes d’actualisation automatique de la page s’exécutent avec une priorité **inférieure** pour s’assurer que les requêtes interactives (comme le chargement de la page et le filtrage croisé des visuels) restent prioritaires.
2. Si votre requête n’est pas terminée avant le prochain cycle d’actualisation, Power BI n’émet pas de nouvelles requêtes d’actualisation tant que la requête précédente n’est pas terminée. Par exemple, si vous avez un intervalle d’actualisation d’une seconde, et que vos requêtes prennent en moyenne quatre secondes, Power BI émet réellement une requête toutes les quatre secondes.

Il existe deux facteurs qui peuvent constituer des goulots d’étranglement des performances :

1. **La capacité :** La requête atteint d’abord la capacité Premium, qui replie et évalue la requête DAX générée à partir des visualisations de rapport dans les requêtes source.
2. **La source de données de requête directe :** Les requêtes traduites à l’étape précédente sont ensuite exécutées sur la source. Il s’agit de vos serveurs SQL Server, de vos sources SAP Hana, etc.

À l’aide de [l’application de mesures Premium](service-admin-premium-monitor-capacity.md) disponible pour les administrateurs, vous pouvez visualiser la quantité de capacité utilisée par les requêtes de faible priorité.

Les requêtes de faible priorité consistent en des requêtes d’actualisation automatique de la page et des requêtes d’actualisation du modèle. Il n’existe actuellement aucun moyen de faire la distinction entre les charges des requêtes d’actualisation automatique de page et celles d’actualisation de modèle.

Si vous remarquez que la capacité est surchargée avec des requêtes de faible priorité, vous pouvez prendre certaines mesures :

1. Demandez une référence SKU Premium plus grande.
2. Contactez le propriétaire du rapport et demandez-lui de réduire l’intervalle d’actualisation.
3. Dans le portail d’administration de la capacité, vous pouvez :
  1. Désactiver l’actualisation automatique de la page pour cette capacité
  2. Augmenter l’intervalle d’actualisation minimal, qui affectera tous les rapports sur cette capacité.


### <a name="frequently-asked-questions"></a>Forum Aux Questions

Cette section fournit des questions et des réponses courantes 

1. Je suis un auteur de rapport. J’ai défini l’intervalle d’actualisation de mon rapport sur 1 s sur le bureau, mais après la publication, mon rapport n’est pas actualisé dans le service.

    * Vérifiez que l’actualisation automatique de la page est activée pour la page. Étant donné que ce paramètre est propre à chaque page, vous devez vous assurer qu’il est activé pour chaque page du rapport que vous voulez actualiser.
    * Vérifiez que vous avez téléchargé sur un espace de travail avec une capacité Premium attachée, sans quoi votre intervalle d’actualisation sera verrouillé à 30 minutes.
    * Si votre rapport se trouve dans un espace de travail Premium, vérifiez auprès de votre administrateur qu’il a activé cette fonctionnalité pour la capacité attachée. En outre, assurez-vous que l’intervalle d’actualisation minimal pour la capacité est inférieur ou identique à celui de votre rapport.

2. Je suis administrateur de capacité. J’ai modifié les paramètres de l’intervalle d’actualisation automatique de la page, mais ils ne sont pas reflétés. En d’autres termes, les rapports ne sont toujours pas actualisés au rythme auquel ils devraient l’être ou ne s’actualisent pas, même si j’ai activé la fonctionnalité.

    * Les modifications apportées aux paramètres d’actualisation automatique de la page prennent jusqu’à 5 minutes pour se propager aux rapports.
    * Outre l’activation de l’actualisation automatique de la page pour la capacité, vous devez également l’activer pour les pages des rapports de votre choix.

3. Mon rapport fonctionne en mode mixte (DQ + Importation). Tous les visuels ne sont pas actualisés.

    * Si vos éléments visuels référencent des tables d’importation, ce comportement est attendu. L’actualisation automatique des pages n’est pas prise en charge pour l’importation.
    * Consultez la question 1 de cette section.

4. Mon rapport s’actualisait dans le service quand il s’est arrêté soudainement.

    * Essayez d’actualiser la page pour voir si le problème se résout de lui-même.
    * Consultez votre administrateur de capacité, car il peut avoir désactivé la fonctionnalité ou augmenté l’intervalle d’actualisation minimal (voir question 2)

5. Je suis un auteur de rapport. Mes visuels ne sont pas actualisés à la cadence que j’ai indiquée. Ils sont actualisés à un rythme plus lent.

    * Si l’exécution de vos requêtes prend du temps, l’intervalle d’actualisation sera retardé. L’actualisation automatique de la page attend la fin de l’exécution de toutes les requêtes avant d’en exécuter de nouvelles.
    * Votre administrateur de capacité a peut-être défini un intervalle d’actualisation minimal supérieur à celui que vous avez défini pour votre rapport. Contactez votre administrateur de capacité et demandez-lui de le réduire.

6. Les requêtes d’actualisation de page automatique sont-elles traitées à partir du cache ?

    * Non, toutes les requêtes d’actualisation automatique de la page contournent les données mises en cache.


## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations, consultez les articles suivants :

* [Utilisation de DirectQuery dans Power BI](desktop-directquery-about.md)
* [Utiliser l’analyseur de performances pour examiner les performances des éléments de rapport](desktop-performance-analyzer.md)
* [Déployer et gérer les capacités Power BI Premium](whitepaper-powerbi-premium-deployment.md)
* [Sources de données dans Power BI Desktop](desktop-data-sources.md)
* [Mettre en forme et combiner des données dans Power BI Desktop](desktop-shape-and-combine-data.md)
* [Se connecter à des classeurs Excel dans Power BI Desktop](desktop-connect-excel.md)   
* [Entrer des données directement dans Power BI Desktop](desktop-enter-data-directly-into-desktop.md)   
