---
title: Transformation BI de Microsoft
description: Découvrez comment Microsoft a réussi à instaurer une culture basée sur les données pour la prise de décisions métier. Décrit la stratégie et la vision de Microsoft en matière de décisionnel.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 07/02/2020
ms.author: v-pemyer
ms.openlocfilehash: 18dc88404b84e786bfee0a15ac169a6e0c1496e4
ms.sourcegitcommit: 561f6de3e4621d9d439dd54fab458ddca78ace2c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/03/2020
ms.locfileid: "85940009"
---
# <a name="microsofts-bi-transformation"></a>Transformation BI de Microsoft

Cet article s’adresse aux professionnels de l’informatique et aux responsables informatiques. Vous allez découvrir notre stratégie et notre vision en matière de décisionnel grâce auxquelles nous pouvons traiter nos données comme des ressources et les exploiter en permanence. Vous verrez également comment nous avons réussi à instaurer une culture de prise de décision métier basée sur les données avec Power BI.

Voici tout d’abord quelques informations générales : aujourd’hui, l’explosion des données affecte les clients et les entreprises à une vitesse vertigineuse. Pour réussir dans cet environnement gourmand en données, il est nécessaire d’avoir dans son équipe des analystes et des dirigeants capables de convertir d’énormes quantités de données en insights succincts. Les outils de décisionnel développés par Microsoft ont révolutionné la façon dont nous explorons en interne nos données et obtenons les insights nécessaires pour stimuler les changements dans l’entreprise.

Dans cette optique, comment votre organisation peut-elle également révolutionner la façon dont elle utilise les données ? Pour vous aider à comprendre, nous allons vous présenter le parcours suivi par Microsoft pour transformer son approche décisionnelle.

## <a name="microsoft-journey"></a>Le parcours de Microsoft

Il y a plusieurs années, la culture d’entreprise de Microsoft encourageait les individus à s’approprier entièrement les données et les insights. D’ailleurs, toute tentative de normalisation des processus se heurtait à une forte résistance culturelle. C’est donc la culture d’entreprise qui a engendré des problèmes liés à la création de rapports et à l’analytique. Voici une description plus précise des problèmes occasionnés :

- Incohérences au niveau des définitions de données, des hiérarchies, des métriques et des indicateurs de performance clés (KPI). Par exemple, chaque pays avait sa propre façon de créer des rapports sur les nouveaux revenus. À défaut de cohérence, la confusion régnait.
- 75 % du temps de travail des analystes consacré à la collecte et à la compilation des données.
- 78 % des rapports créés dans un environnement hors connexion.
- Plus de 350 outils et systèmes financiers centralisés.
- Environ 30 millions de dollars dépensés annuellement dans des « applications fictives ».

Ces problèmes nous ont incités à réfléchir à la manière d’améliorer les choses. Le service des finances et d’autres équipes internes ont reçu le soutien de la direction pour transformer le processus d’examen des activités, ce qui a conduit à la création d’une plateforme décisionnelle unifiée comme source unique de vérité. (Nous examinerons en détail notre plateforme décisionnelle plus loin dans cet article.) Ces innovations ont permis de transformer les processus d’examen des activités : de vues tabulaires denses en visuels plus simples et plus pertinents, axés sur des thèmes métier clés.

Comment sommes-nous arrivés à ce résultat ? En adoptant une approche décisionnelle et centralisée gérée par le service informatique et en l’étendant au moyen d’une solution décisionnelle libre-service (SSBI). Cette approche repose sur deux principes : la _discipline au niveau de la base_ et la _flexibilité en périphérie_.

### <a name="discipline-at-the-core"></a>Discipline au niveau de la base

La discipline au niveau de la base signifie que le service informatique garde le contrôle en organisant une seule source de données de référence. L’adoption d’une approche décisionnelle d’entreprise normalisée et la définition de taxonomies et de hiérarchies d’indicateurs de performance clés font partie de cette discipline. Plus important encore, les autorisations de données sont appliquées de manière centralisée pour garantir que nos employés ne peuvent lire que les données dont ils ont besoin.

Tout d’abord, nous avons compris que notre transformation décisionnelle n’était pas un problème technologique. Pour réussir, nous avons appris à définir d’abord le succès, puis à le traduire en métriques clés. La mise en place de définitions cohérentes à travers nos données était très importante et ne peut être assez soulignée.

Notre transformation n’a pas eu lieu d’un seul coup. Nous avons donné la priorité à la remise d’une carte de performance pour les filiales comprenant environ 30 indicateurs de performance clés. Ensuite, sur plusieurs années, nous avons progressivement élargi le nombre et la profondeur des domaines, puis nous avons développé des hiérarchies d’indicateurs de performance clés plus complexes. Aujourd’hui, nous pouvons regrouper les indicateurs de performance clés de niveau inférieur au niveau du client dans des indicateurs plus élevés au niveau de l’entreprise. Nous avons désormais plus de 2 000 indicateurs de performance clés en tout ; chaque indicateur est une mesure clé du succès et est aligné sur les objectifs de l’entreprise. À présent, dans toute l’entreprise, les rapports d’entreprise et les solutions SSBI présentent des indicateurs de performance clés bien définis, cohérents et sécurisés.

### <a name="flexibility-at-the-edge"></a>Flexibilité en périphérie

En périphérie, nos analystes financiers, commerciaux et marketing sont plus flexibles et plus agiles. Ils peuvent désormais analyser les données plus rapidement. Officiellement, ce scénario fait appel à l’_informatique décisionnelle libre-service_ ou SSBI. Nous savons maintenant qu’un indicateur de performance clés géré présente des _avantages mutuels_ pour le service informatique et les analystes. Plus important encore, nous avons constaté des optimisations en favorisant la normalisation, la connaissance et la réutilisation de nos données et solutions décisionnelles. Et, en tant qu’entreprise, nous avons pu dégager plus de valeur synergiquement en identifiant le juste équilibre entre le décisionnel centralisé et le décisionnel libre-service.

### <a name="our-solution"></a>Notre solution

**Starlight** est le nom que nous avons donné à notre plateforme interne d’analytique et d’unification des données. Celle-ci prend en charge les services des finances, des ventes, du marketing et de l’ingénierie. Sa mission est de fournir une plateforme de données fiable, partagée et scalable. Entièrement créée par le service des finances, la plateforme est toujours en opération et fonctionne avec les produits Microsoft les plus récents.

L’**indicateur de performance clés Lake** n’est pas un lac de données Azure. Il s’agit en fait d’un modèle tabulaire qui repose sur la technologie Starlight et qui est hébergé dans Azure IaaS à l’aide de Microsoft SQL Server Analysis Services. Le modèle tabulaire fournit des données provenant de plus de 100 sources internes et définit de nombreuses hiérarchies et indicateurs de performance clés. Son objectif est de permettre la création de rapports et l’analyse des performances métier sur plusieurs équipes (finance, marketing et ventes). Pour y parvenir, il obtient des insights opportuns, précis et performants grâce à des modèles unifiés provenant de sources pertinentes.

Son premier déploiement s’est avéré passionnant, car il a produit des avantages immédiats et mesurables. La première version a permis de centraliser les plateformes décisionnelles C+E des finances et du marketing. Puis, au cours des six dernières années, il a été élargi pour consolider d’autres solutions d’insights métier. Aujourd’hui, il continue à évoluer et à alimenter nos revues d’activité au niveau global et commercial, ainsi que nos rapports standard et notre décisionnel libre-service. Son adoption a été multipliée par 5 depuis sa sortie, bien au-delà de nos attentes initiales.

Voici un résumé des principaux avantages :

- Il alimente notre carte de performance des filiales, les revues d’activité dans le monde entier ainsi que les rapports et l’analytique des finances, du marketing et des ventes.
- Il prend en charge l’analytique libre-service, ce qui permet aux analystes de découvrir des insights masqués dans les données.
- Il stimule la création de rapports et la caractérisation analytique dans divers domaines : rémunération incitative, analyse du marketing et des opérations, métriques relatives aux performances des ventes, évaluations de la direction et processus de planification annuel.
- Il génère des rapports et des informations analytiques dynamiques et automatisés à partir d’une _source unique de vérité_.

L’**indicateur de performance clés Lake** est une grande réussite. Il est souvent présenté à nos clients pour leur montrer une utilisation efficace de nos dernières technologies. Ce n’est pas surprenant, mais il trouve un écho chez bon nombre d’entre eux.

#### <a name="how-it-works"></a>Fonctionnement

La plateforme Starlight gère le flux des données, de l’acquisition au traitement jusqu’à la publication :

1. L’intégration fiable et agile des données se déroule de manière planifiée et consolide les données de plus de 100 sources brutes disparates. Parmi les systèmes de données sources, citons les bases de données relationnelles, Azure Data Lake Storage et les bases de données Azure Synapse. Les domaines couvrent la finance, le marketing, les ventes et l’ingénierie.
2. Une fois en préproduction, les données sont harmonisées et enrichies à l’aide des données de référence et de la logique métier. Elles sont ensuite chargées dans les tables de l’entrepôt de données. Le modèle tabulaire est ensuite actualisé.
3. Les analystes de l’entreprise utilisent Excel et Power BI pour dégager des insights et des informations analytiques à partir du modèle tabulaire. Il permet également aux propriétaires de mettre en œuvre des définitions de métrique pour leur propre entreprise. Si nécessaire, la mise à l’échelle est réalisée à l’aide d’Azure IaaS avec équilibrage de charge.

## <a name="deliver-success"></a>Réussir

On peut dire avec humour que chacun a sa propre version de la vérité. Mais pour certaines organisations, c’est malheureusement une réalité. Ainsi, quand des individus cherchent à s’approprier entièrement les données et les insights, les organisations se retrouvent avec plusieurs versions de la vérité. Pour ces organisations, cette approche non gérée est rarement source de réussite.

C’est pourquoi nous pensons que vous avez besoin d’un _centre d’excellence_. Un centre d’excellence est une équipe centrale responsable de l’établissement de métriques et de définitions à l’échelle de l’entreprise, et de bien d’autres choses. C’est également une fonction métier qui organise les personnes, les processus et les composants technologiques en un ensemble complet de compétences et de fonctionnalités métier.

Preuves à l’appui, nous pensons qu’un centre d’excellence complet et fiable est essentiel pour générer de la valeur et maximiser le succès d’une entreprise. Il peut inclure des initiatives de changement, des processus standard, des rôles, des recommandations, des bonnes pratiques, du support, de la formation, etc.

Nous vous invitons à lire les articles de cette série consacrée au centre d’excellence pour en savoir plus. Nous allons vous aider à découvrir comment votre organisation peut s’ouvrir aux changements pour parvenir au succès.

## <a name="next-steps"></a>Étapes suivantes

Dans l’[article suivant de cette série](center-of-excellence-establish.md), découvrez comment la mise en place d’un centre d’excellence a permis à Microsoft de créer une plateforme d’analytique et de données normalisée pour dégager des insights à partir de ses données.

Pour plus d’informations sur cet article, consultez les ressources suivantes :

- [Établir un centre d’excellence](center-of-excellence-establish.md)
- Vous avez des questions ? [Essayez d’interroger la communauté Power BI](https://community.powerbi.com/)
- Vous avez des suggestions ? [Envoyez-nous vos idées pour améliorer Power BI](https://ideas.powerbi.com/)
