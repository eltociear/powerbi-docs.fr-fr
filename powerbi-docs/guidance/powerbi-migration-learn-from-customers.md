---
title: En savoir plus sur les migrations Power BI du client
description: Apprenez-en davantage des clients qui migrent vers Power BI.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 08/20/2020
ms.author: v-pemyer
ms.openlocfilehash: a725d2763d7d044220785c2f9727ee30f14bfd5d
ms.sourcegitcommit: 84e75a2cd92f4ba4e0c08ba296b981b79d6d0e82
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88803296"
---
# <a name="learn-from-customer-power-bi-migrations"></a>En savoir plus sur les migrations Power BI du client

Cet article, qui conclut la série sur la migration vers Power BI, dévoilent les principales leçons qu’ont tirées deux clients qui ont réussi à migrer vers Power BI.

## <a name="international-consumer-goods-company"></a>Société internationale de biens de consommation

Une société internationale de biens de consommation, qui vend des centaines de produits, a pris la décision en 2017 de suivre une stratégie donnant la priorité au cloud. L’un des principaux arguments en faveur de la sélection de Power BI comme plateforme décisionnelle est son intégration poussée à Azure et Microsoft 365.

### <a name="conduct-a-phased-migration"></a>Réaliser une migration échelonnée

En 2017, la société a commencé à utiliser Power BI. L’objectif organisationnel initial consistait à introduire Power BI sous forme d’outil décisionnel supplémentaire. Cette décision permettait aux auteurs de contenu, aux consommateurs et au service informatique de prendre le temps de s’adapter à de nouvelles façons d’exploiter le décisionnel. Elle leur permettait aussi d’acquérir des compétences dans Power BI.

Au cours du second semestre 2018, une annonce formelle a été faite pour déclarer Power BI comme l’outil décisionnel approuvé de l’organisation. En conséquence, tout le travail de développement décisionnel devait avoir lieu dans Power BI. La disponibilité de Power BI Premium a considérablement motivé cette décision. À cette époque, l’organisation déconseillait d’utiliser l’ancienne plateforme décisionnelle, et la planification de la transition commençait.

Vers la fin de 2019 a débuté la migration du contenu existant de l’ancienne plateforme décisionnelle vers Power BI. Certains utilisateurs précoces ont alors rapidement migré leur contenu. L’élan vers Power BI s’est encore accru au sein de toute l’organisation. Les propriétaires et auteurs de contenu ont ensuite été invités à se préparer à migrer entièrement vers Power BI d’ici la fin de 2020. L’organisation doit encore faire face à des difficultés liées aux compétences, aux délais et au financement, même si aucun de ses défis n’est lié à la plateforme de la technologie elle-même.

> [!IMPORTANT]
> Power BI était déjà couronné de succès et bien enraciné au sein de l’organisation quand il a été demandé aux unités commerciales d’intensifier formellement leurs efforts de migration afin d’abandonner l’ancienne plateforme décisionnelle.

### <a name="prepare-to-handle-varying-responses"></a>Préparer la gestion des réponses variables

Au sein de cette grande organisation décentralisée, les niveaux de réceptivité et d’empressement face à l’adoption de Power BI variaient considérablement. Au-delà de toute préoccupation de calendrier et de budget, pour certains employés, l’investissement dans l’acquisition de compétences pour maîtriser l’ancienne plateforme décisionnelle avait été énorme. C’est pourquoi l’annonce de la standardisation de Power BI n’a pas été bien accueillie par tout le monde. Étant donné que chaque unité commerciale dispose de son propre budget, il était possible pour certaines de remettre en cause une telle décision. Puisque les décisions concernant l’outil décisionnel étaient prises de manière centralisée, elles entraînaient des difficultés à gérer pour le parrain exécutif et les responsables du décisionnel.

> [!IMPORTANT]
> La communication avec les équipes dirigeantes au sein des unités commerciales s’avérait essentielle pour faire comprendre les avantages que tirerait l’organisation de la standardisation de Power BI. Une communication efficace s’est même avérée encore plus essentielle pendant toute la période de migration et à la veille de la date de mise hors service de l’ancienne plateforme décisionnelle.

### <a name="focus-on-the-bigger-picture"></a>Se concentrer sur la situation dans son ensemble

La société a découvert que, même si une partie des rapports migrés répliquaient étroitement la conception d’origine, tous n’étaient pas répliqués fidèlement dans Power BI. Cette découverte était attendue, puisque toutes les plateformes décisionnelles sont différentes. Elle a cependant mis au jour la nécessité d’adopter un autre état d’esprit pour la conception.

Des conseils ont été fournis aux auteurs de contenu : qu’ils se concentrent sur la création de rapports utilisables dans Power BI, au lieu d’essayer d’obtenir des réplicas exacts des anciens rapports. C’est pourquoi il est nécessaire que les experts techniques soient activement disponibles pendant le processus de migration à des fins de conseils et de validation. Des efforts ont été déployés pour tenir compte de l’objectif de conception des rapports et pour l’améliorer au besoin.

> [!IMPORTANT]
> Parfois, la meilleure approche consiste à intégrer des améliorations au cours de la migration. À d’autres moments, il est préférable d’obtenir exactement la même valeur qu’avant, sans apporter d’améliorations significatives, afin de ne pas compromettre la chronologie de la migration.

### <a name="cautiously-assess-priorities"></a>Évaluer avec prudence les priorités

Une analyse de l’ancienne plateforme décisionnelle a été menée pour en comprendre pleinement l’utilisation. L’ancienne plateforme décisionnelle comptait des milliers de rapports publiés, dont environ la moitié avait été consultée au cours de l’année précédente. Ce nombre se réduisait encore de moitié après l’évaluation des rapports considérés comme ayant une valeur ajoutée significative pour l’organisation. Ces rapports ont été classés comme prioritaires pour la migration.

> [!IMPORTANT]
> Il est très facile de surestimer l’importance réelle d’un rapport. S’agissant des rapports rarement utilisés, déterminez s’il est possible de les abandonner complètement. Parfois, ne rien faire s’avère moins coûteux et plus facile.

### <a name="cautiously-assess-complexity"></a>Évaluer avec prudence la complexité

Les estimations de temps des rapports prioritaires ont été compilées en fonction de niveaux d’efforts estimés : simple, moyen ou complexe. Même si le processus a l’air relativement simple, ne vous attendez pas à ce que les estimations de temps soient précises pour chacun des rapports. Vous risquez de constater qu’une estimation peut s’avérer largement inexacte. Par exemple, la société avait un rapport qu’elle jugeait très complexe. Elle obtenait une estimation de 50 jours pour sa conversion par les consultants. Pourtant, le remaniement du rapport dans Power BI s’est effectué en 50 heures environ.

> [!IMPORTANT]
> Bien que les estimations de temps soient souvent nécessaires pour obtenir financement et personnel, elles sont probablement les plus précieuses sous leur forme agrégée.

### <a name="decide-how-change-management-is-handled"></a>Déterminer la façon de gérer le changement

Avec un tel volume élevé de ressources décisionnelles, la gestion du changement pour les rapports appartenant à la société représentait un réel défi. Les rapports gérés par le service informatique l’ont été conformément aux pratiques de gestion du changement standard. En revanche, en raison du volume élevé, le pilotage central du changement pour le contenu appartenant à la société n’a pas été possible.

> [!IMPORTANT]
> D’autres responsabilités incombent aux unités commerciales dès lors qu’il est peu pratique de gérer le changement à partir d’une seule équipe centrale.

### <a name="create-an-internal-community"></a>Créer une communauté interne

La société a établi un centre d’excellence pour fournir des cours et ressources de formation internes. Le centre d’excellence sert également de groupe de consultants interne prêt à aider les auteurs de contenu à résoudre les problèmes techniques, franchir les obstacles et recommander les bonnes pratiques.

Il existe aussi une communauté Power BI interne, massivement couronnée de succès avec plus de 1 600 membres. Cette communauté est gérée dans Yammer. Les membres peuvent poser des questions en interne et recevoir des réponses conformes aux bonnes pratiques et respectant les contraintes de l’organisatino. Ce type d’interaction entre les utilisateurs permet d’alléger une grande partie de la charge qui incombe au centre d’excellence. Toutefois, c’est ce dernier qui supervise les questions et les réponses, s’impliquant dans les conversations, au besoin.

Cette communauté interne s’est développée sous la forme d’un réseau d’experts Power BI plus récent. Celui-ci comprend un nombre limité de spécialistes Power BI présélectionnés au sein de l’organisation. Ceux-ci sont des praticiens Power BI hautement qualifiés issus des unités commerciales, enthousiastes et activement désireux de résoudre les problèmes au sein de l’entreprise. Les membres du réseau d’experts Power BI sont censés respecter les bonnes pratiques et recommandations établies par le centre d’excellence. Ils aident la communauté Power BI interne plus large à les comprendre et à les mettre en œuvre. Même si le réseau d’experts Power BI collabore avec le centre d’excellence et peut recevoir une formation dédiée, il fonctionne indépendamment du centre d’excellence. Chaque expert Power BI peut définir ses paramètres de fonctionnement, en tenant compte des autres responsabilités et priorités de son rôle officiel.

> [!IMPORTANT]
> Définissez très précisément les fonctions du centre d’excellence, par exemple : adoption, gouvernance, conseils, bonnes pratiques, formation, support technique, voire même développement pratique. Même si un centre d’excellence s’avère incroyablement précieux, il peut être difficile d’en mesurer le retour sur investissement.

### <a name="monitor-migration-progress-and-success"></a>Superviser la progression et la réussite de la migration

Les indicateurs de performance clés (KPI) sont constamment supervisés pendant la migration vers Power BI. Ils aident la société à comprendre les tendances des métriques comme le nombre de consultations de rapports, le nombre de rapports actifs et les utilisateurs distincts par mois. L’utilisation accrue de Power BI se mesure en même temps que l’utilisation réduite de l’ancienne plateforme décisionnelle, avec l’objectif de parvenir à une relation inverse. Les cibles sont mises à jour chaque mois pour s’adapter aux changements. Si l’utilisation n’évolue pas au rythme souhaité, des goulots d’étranglement sont identifiés de sorte que des mesures appropriées soient prises.

> [!IMPORTANT]
> Créez un tableau de bord de la migration avec un décisionnel exploitable pour superviser la réussite de l’effort de migration.

## <a name="large-transportation-and-logistics-company"></a>Grande entreprise de transport et logistique

Une grande entreprise de transport et logistique nord-américaine investit activement dans la modernisation de son infrastructure de données et de ses systèmes analytiques.

### <a name="allow-a-period-of-gradual-growth"></a>Prévoir une période de croissance progressive

La société a commencé à utiliser Power BI en 2018. À la mi-2019, Power BI est devenu la plateforme de prédilection pour tous les nouveaux cas d’utilisation d’informatique décisionnelle. Ensuite, en 2020, la société s’est concentrée sur la suppression progressive de sa plateforme décisionnelle existante, en plus de développer un éventail personnalisé de solutions décisionnelles ASP.NET.

> [!IMPORTANT]
> Power BI comptait de nombreux utilisateurs actifs au sein de l’organisation avant de commencer à abandonner la plateforme et les solutions décisionnelles anciennes.

### <a name="balance-centralized-and-distributed-groups"></a>Équilibrer les groupes centralisés et distribués

Dans la société, il existe deux types d’équipes décisionnelles : une équipe décisionnelle centrale et des groupes d’analytique répartis dans toute l’organisation. L’équipe décisionnelle centrale a la responsabilité de la propriété de Power BI en tant que plateforme, mais le contenu ne lui appartient pas du tout. De cette façon, l’équipe décisionnelle centrale est un hub d’activation technique qui soutient les groupes d’analytique distribués.

Chacun des groupes d’analytique est dédié à une unité commerciale spécifique ou à une fonction de services partagés. Un petit groupe peut compter un seul analyste, tandis qu’un groupe plus large peut en compter entre 10 et 15.

> [!IMPORTANT]
> Les groupes d’analytique distribués comprennent des experts techniques qui connaissent bien les besoins métier quotidiens. Cette séparation permet à l’équipe décisionnelle centrale de se concentrer principalement sur l’activation technique et la prise en charge des services et outils décisionnels.

### <a name="focus-on-dataset-reusability"></a>Concentration sur la possibilité de réutilisation des jeux de données

Le recours à des solutions décisionnelles ASP.NET était un obstacle au développement de nouvelles solutions décisionnelles. L’ensemble de compétences nécessaires impliquait que le nombre d’auteurs de contenu libre-service était faible. Étant donné que Power BI est un outil bien plus accessible (particulièrement conçu pour l’informatique décisionnelle libre-service), il s’est rapidement propagé à toute l’organisation une fois mis en production.

L’autonomisation des analystes de données au sein de la société a entraîné des résultats positifs immédiats. En revanche, l’accent initial du développement de Power BI portait sur la visualisation. Même s’il a débouché sur des solutions décisionnelles précieuses, cet accent a engendré un grand nombre de fichiers Power BI Desktop, chacun doté d’une relation individuelle entre les rapports et leurs jeux de données. Ainsi, ont été produits de nombreux jeux de données et une grande duplication des données et de la logique métier. Pour réduire la duplication des données, de la logique et des efforts, la société a dispensé une formation et offert une assistance aux auteurs de contenu.

> [!IMPORTANT]
> Incluez des informations sur l’importance de la possibilité de réutiliser les données dans vos efforts de formation internes. Traitez les concepts importants le plus tôt possible.

### <a name="test-data-access-multiple-ways"></a>Tester l’accès aux données de plusieurs façons

La plateforme de l’entrepôt de données de la société est DB2. Au regard de la conception actuelle de l’entrepôt de données, la société a découvert que les modèles DirectQuery (plutôt que les modèles d’importation) répondaient mieux à ses besoins.

> [!IMPORTANT]
> Procédez à une preuve technique de concept pour évaluer le mode de stockage des modèles qui fonctionne le mieux. De plus, formez les modélisateurs de données sur les modes de stockage des modèles et leur possibilité de choisir un mode approprié à leur projet.

### <a name="educate-authors-about-premium-licensing"></a>Former les auteurs sur les licences Premium

Dans la mesure où il était plus facile de prendre en main Power BI (par rapport à leur ancienne plateforme décisionnelle), beaucoup d’utilisateurs précoces ne disposaient pas d’une licence pour l’outil décisionnel précédent. Comme prévu, le nombre d’auteurs de contenu a considérablement augmenté. Ces auteurs de contenu voulaient à juste titre partager leur contenu avec d’autres utilisateurs, ce qui s’est traduit par un besoin continu de licences Power BI Pro supplémentaires.

La société a investi massivement dans les espaces de travail Premium, notamment pour distribuer du contenu Power BI à de nombreux utilisateurs avec des licences Power BI gratuites. L’équipe du support technique travaille avec les auteurs de contenu pour veiller à ce qu’ils utilisent des espaces de travail Premium si besoin. Cela évite ainsi d’allouer inutilement des licences Power BI Pro quand un utilisateur a uniquement besoin de consommer du contenu.

> [!IMPORTANT]
> Souvent, des questions se posent sur les licences. Soyez prêt à former et aider les auteurs de contenu à traiter les questions liées aux licences. Vérifiez que les demandes de licences Power BI Pro par les utilisateurs sont justifiées.

### <a name="understand-the-data-gateways"></a>Comprendre les passerelles de données

Très tôt, la société disposait de nombreuses passerelles personnelles. L’utilisation d’un cluster de passerelles de données locales permet de faire supporter les efforts de gestion à l’équipe décisionnelle centrale, ce qui permet à la communauté des auteurs de contenu de se concentrer sur la production dudit contenu. L’équipe décisionnelle centrale a travaillé avec la communauté interne des utilisateurs de Power BI pour réduire le nombre de passerelles personnelles.

> [!IMPORTANT]
> Prévoyez de créer et gérer des passerelles de données locales. Déterminez qui est autorisé à installer et utiliser une passerelle personnelle et appliquez-y des stratégies de passerelle.

### <a name="formalize-your-support-plan"></a>Formaliser votre plan de support

Alors que l’adoption de Power BI augmentait au sein de l’organisation, la société a constaté qu’une approche multiniveau du support fonctionnait bien :

- **Couche 1 : au sein de l’équipe :** Les utilisateurs apprennent des autres et enseignent aux autres au jour le jour.
- **Couche 2 : communauté Power BI :** Les utilisateurs posent des questions à la communauté des équipes internes pour apprendre les uns des autres et communiquer des informations importantes.
- **Couche 3 : équipe décisionnelle centrale et centre d’excellence :** Les utilisateurs envoient des demandes d’aide par e-mail. Des sessions _pendant les heures de bureau_ sont tenues deux fois par semaine pour aborder collectivement les problèmes et partager des idées.

> [!IMPORTANT]
> Bien que les deux premières couches soient moins formelles, elles sont tout aussi importantes que la troisième couche de support. Les utilisateurs expérimentés ont tendance à s’appuyer principalement sur les personnes qu’ils connaissent, tandis que les utilisateurs plus récents (ou ceux qui jouent le rôle d’analyste de données unique pour une unité commerciale ou un service partagé) se réfèrent davantage à un support plus formel.

### <a name="invest-in-training-and-governance"></a>Investir dans la formation et la gouvernance

Au cours de l’année passée, l’entreprise a amélioré ses offres de formation interne et son programme de gouvernance des données. Le comité de gouvernance comprend les principaux membres de chacun des groupes d’analytique distribués, en plus du centre d’excellence.

Il existe à présent six cours Power BI internes dans son catalogue interne. Le cours [Dashboard in a Day](https://powerbi.microsoft.com/diad/) reste un cours qui plaît beaucoup aux débutants. Pour aider les utilisateurs à approfondir leurs compétences, une série de trois cours Power BI et deux cours DAX sont proposés.

L’une des plus importantes décisions en matière de gouvernance des données est liée à la gestion des capacités Premium. La société a choisi d’aligner sa capacité dédiée sur des domaines d’analytique clés dans les unités commerciales et les services partagés. Ainsi, en cas d’inefficacité, l’impact n’est ressenti que dans un domaine particulier, et les administrateurs décentralisés de la capacité ont la possibilité de gérer cette capacité comme bon leur semble.

> [!IMPORTANT]
> Faites attention à la façon dont les capacités Premium sont utilisées et à la façon dont les espaces de travail leur sont attribués.

## <a name="next-steps"></a>Étapes suivantes

Voici d’autres ressources utiles :

- [Transformation BI de Microsoft](center-of-excellence-microsoft-business-intelligence-transformation.md)
- [Livre blanc Planification d’un déploiement de Power BI en entreprise](https://aka.ms/PBIEnterpriseDeploymentWP)
- [Dashboard in a Day](https://powerbi.microsoft.com/diad/)
- Vous avez des questions ? [Essayez d’interroger la communauté Power BI](https://community.powerbi.com/)
- Vous avez des suggestions ? [Envoyez-nous vos idées pour améliorer Power BI](https://ideas.powerbi.com/)

Les partenaires Power BI expérimentés sont là pour aider votre organisation à mener à bien le processus de migration. Pour contacter un partenaire Power BI, accédez au [portail des partenaires Power BI](https://powerbi.microsoft.com/partners/).
