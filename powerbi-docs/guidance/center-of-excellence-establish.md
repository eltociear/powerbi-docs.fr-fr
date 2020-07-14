---
title: Établir un centre d’excellence
description: Découvrez comment la mise en place d’un centre d’excellence a permis à Microsoft de créer une plateforme d’analytique et de données standardisée pour dégager des insights avec un modèle d’exploitation adapté, l’engagement des parties prenantes ainsi que des investissements partagés et dédiés.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 07/02/2020
ms.author: v-pemyer
ms.openlocfilehash: 9aab2afd9e3b4b86844c045ceb0346d57baa3e18
ms.sourcegitcommit: 561f6de3e4621d9d439dd54fab458ddca78ace2c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/03/2020
ms.locfileid: "85940032"
---
# <a name="establish-a-center-of-excellence"></a>Établir un centre d’excellence

Cet article s’adresse aux professionnels de l’informatique et aux responsables informatiques. Vous allez découvrir comment mettre en place un centre d’excellence dédié au décisionnel et à l’analytique dans votre organisation. Vous verrez également comment Microsoft a configuré le sien.

Certains pensent qu’un centre d’excellence est simplement un centre de support technique, ce qui est loin de la réalité.

En général, un centre d’excellence dédié au décisionnel et à l’analytique se compose d’une équipe de professionnels en charge de l’établissement et de la maintenance d’une plateforme décisionnelle. Cette équipe est également responsable de la création d’une source unique de vérité et de la définition d’un ensemble de métriques cohérentes à l’échelle de l’entreprise pour dégager des insights et accélérer leur production. Et pourtant, un centre d’excellence est un terme générique. Un centre d’excellence peut donc être implémenté et géré de différentes façons, et sa structure et son étendue peuvent varier d’une organisation à l’autre. Mais à la base, un centre d’excellence est avant tout une plateforme fiable conçue pour fournir des fonctionnalités adaptées de gestion de données et d’insights aux bonnes personnes et au bon moment. Dans l’idéal, il favorise également la promotion, la formation et le support. Chez Microsoft, le centre d’excellence repose sur la _[discipline au niveau de la base](center-of-excellence-microsoft-business-intelligence-transformation.md#discipline-at-the-core)_ et constitue notre plateforme décisionnelle et notre source unique de vérité.

Les organisations plus importantes peuvent compter plusieurs centres d’excellence. Dans ce cas, le centre d’excellence de base est _étendu_ avec des centres d’excellence satellites qui résident le plus souvent au niveau des services. Un centre d’excellence satellite se compose d’experts qui connaissent les taxonomies et les définitions et qui savent comment transformer des données de base en données logiques et utiles _pour leur service_. Les analystes de chaque service sont autorisés à accéder aux données de base et peuvent les utiliser en toute confiance dans leurs propres rapports. Ils peuvent ainsi créer des solutions qui s’appuient sur les dimensions, les faits et la logique métier soigneusement préparés des données de base. Parfois, ils peuvent également étendre ces données avec une logique métier et des jeux de données plus petits et propres à un service. Il est important de noter que les centres d’excellence satellites ne sont jamais déconnectés et qu’ils n’agissent pas de manière isolée. Chez Microsoft, les centres d’excellence satellites favorisent la _[flexibilité en périphérie](center-of-excellence-microsoft-business-intelligence-transformation.md#flexibility-at-the-edge)_ .

Pour que ce scénario étendu aboutisse, les services doivent « _payer pour participer_ ». Cela signifie qu’ils doivent investir financièrement dans le centre d’excellence de base. De cette façon, il n’y a aucun risque qu’ils ne reçoivent pas la part qu’ils méritent ou que leurs exigences passent au second plan.

Pour prendre en charge ce scénario, le centre d’excellence de base doit être mis à l’échelle pour répondre aux besoins des services financés. L’intégration de plusieurs jeux de données permet de réaliser des économies d’échelle. Chez Microsoft, il nous est rapidement apparu que le travail centralisé est plus économique et donne des résultats plus rapides. Chaque fois qu’un nouveau domaine est intégré, nous réalisons des économies d’échelle plus importantes qui nous permettent de tirer parti de l’ensemble de la plateforme et de contribuer à celle-ci, renforçant ainsi notre culture de données sous-jacente.

Prenons un exemple. Notre plateforme décisionnelle fournit des dimensions, des faits et une logique métier de base pour les services suivants : finances, ventes et marketing. Elle définit également des centaines d’indicateurs de performance clés (KPI). Un analyste Power Platform doit à présent préparer un tableau de bord pour la direction. Certains indicateurs de performance clés, comme le chiffre d’affaires et les pipelines, proviennent directement de la plateforme décisionnelle. D’autres, toutefois, sont basés sur des besoins plus granulaires, comme un indicateur de performance clé sur l’adoption par les utilisateurs d’une fonctionnalité spécifique à Power BI : les dataflows. L’analyste peut ainsi produire un [modèle composite](composite-model-guidance.md) Power BI pour intégrer les données de la plateforme décisionnelle de base aux données des services. Il ajoute ensuite une logique métier pour définir les indicateurs de performance clés de chaque service. Enfin, il crée un tableau de bord de direction basé sur le nouveau modèle, qui exploite les ressources du centre d’excellence à l’échelle de l’entreprise, ces ressources étant enrichies de connaissances et de données locales.

Il est important de noter que la répartition des responsabilités entre les centres d’excellence de base et satellites permet aux analystes de chaque service de se concentrer sur l’innovation plutôt que sur la gestion d’une plateforme de données. Par moments, il peut même y avoir une relation mutuellement bénéfique entre les centres d’excellence satellites et le centre d’excellence de base. Par exemple, un centre d’excellence satellite peut définir de nouvelles métriques qui, si elles ont fait leurs preuves dans leur service, peuvent se retrouver comme métriques de base qui profitent à toute l’entreprise. Elles sont alors accessibles au centre d’excellence de base qui les prend en charge.

## <a name="bi-platform"></a>Plateforme décisionnelle

Le centre d’excellence de votre organisation peut porter un nom différent, comme « équipe décisionnelle » ou « groupe décisionnel ». Mais peu importe le nom, c’est ce qu’il fait qui nous intéresse. Si vous ne disposez pas d’une équipe structurée, nous vous recommandons de former une équipe regroupant vos principaux experts en décisionnel pour établir votre plateforme décisionnelle.

Chez Microsoft, notre centre d’excellence a pour nom « BI Platform » (plateforme décisionnelle). Ce centre réunit de nombreux groupes de parties prenantes représentant différentes divisions au sein de l’entreprise, notamment la finance, les ventes et le marketing. Il est organisé pour exécuter des [capacités partagées](#shared-capabilities) et assurer des [remises dédiées](#dedicated-deliveries).

:::image type="content" source="media/center-of-excellence-establish/business-intelligence-platform-operating-model.png" alt-text="Le diagramme montre les capacités partagées et les remises dédiées qui sont décrites dans les sections suivantes.":::

### <a name="shared-capabilities"></a>Fonctionnalités partagées

Des capacités partagées sont nécessaires pour établir et exploiter la plateforme décisionnelle. Elles prennent en charge tous les groupes de parties prenantes qui financent la plateforme. Elles comprennent les équipes suivantes :

- **Ingénierie de la plateforme de base :** Notre plateforme décisionnelle a été conçue sous l’angle de l’ingénierie. Il s’agit en fait d’un ensemble de frameworks qui prennent en charge l’ingestion de données, le traitement visant à enrichir les données ainsi que la remise de ces données dans des modèles de données pouvant être consommés par les analystes. Les ingénieurs sont responsables de la conception et de l’implémentation techniques des fonctionnalités de la plateforme décisionnelle de base. Par exemple, ils conçoivent et implémentent les pipelines de données.
- **Infrastructure et hébergement :** Les ingénieurs informatiques sont chargés du provisionnement et de la gestion de tous les services Azure.
- **Support et opérations :** Cette équipe assure le bon fonctionnement de la plateforme. Le support s’occupe des besoins des utilisateurs, comme les autorisations d’accès aux données. Les opérations sont chargées de la bonne marche de la plateforme, veillent au respect des contrats de niveau de service (SLA) et communiquent les retards ou les échecs.
- **Gestion des versions :** Les gestionnaires de programmes techniques publient les changements. Ceux-ci vont des mises à jour apportées au framework de la plateforme aux demandes de changement visant les modèles de données. Cette équipe est la dernière ligne de défense pour vérifier que les changements n’entraînent aucun dysfonctionnement.

### <a name="dedicated-deliveries"></a>Remises dédiées

Il existe une équipe chargée des remises dédiées pour chaque groupe de parties prenantes. Elle se compose généralement d’un ingénieur de données, d’un ingénieur en analytique et d’un gestionnaire de programmes techniques, tous financés par le groupe de parties prenantes.

## <a name="bi-team-roles"></a>Rôles de l’équipe décisionnelle

Chez Microsoft, notre plateforme décisionnelle est gérée par des équipes scalables de professionnels. Les équipes sont alignées sur des ressources dédiées et partagées. Aujourd’hui, nous avons les rôles suivants :

- **Gestionnaires de programmes :** Les gestionnaires de programmes sont des ressources dédiées. Ils servent de contact principal entre l’équipe décisionnelle et les parties prenantes. Leur travail est convertir les exigences métier des parties prenantes en spécifications techniques. Ils gèrent également les priorités des livrables aux parties prenantes.
- **Responsables de base de données :** Cette ressource dédiée est responsable de l’intégration des nouveaux jeux de données dans l’entrepôt de données centralisé. L’intégration d’un jeu de données peut nécessiter la configuration de dimensions conformes, l’ajout d’une logique métier et d’attributs personnalisés, ainsi que l’application de noms et d’une mise en forme standard.
- **Responsables de l’analytique :** Les membres de cette ressource dédiée sont responsables de la conception et du développement de modèles de données. Ils s’efforcent d’appliquer une architecture cohérente en utilisant des noms et des mises en forme standard. L’optimisation des performances est un volet important de leur travail.
- **Opérations et infrastructure :** Les membres de cette ressource partagée sont chargés de gérer les travaux et les pipelines de données. Ils sont également responsables de la gestion des abonnements Azure, des capacités de Power BI, des machines virtuelles et des passerelles de données.
- **Support :** Les membres de cette ressource partagée sont chargés d’écrire la documentation, d’organiser la formation, de communiquer les changements relatifs au modèle de données et de répondre aux questions des utilisateurs.

## <a name="governance-and-compliance"></a>Gouvernance et conformité

Pour chaque groupe de parties prenantes, les chefs de projet fournissent une gouvernance et une supervision interprogrammes. Leur objectif principal est de garantir que les investissements en informatique génèrent de la valeur métier et atténuent les risques. Le comité directeur se réunit régulièrement pour passer en revue la progression et approuver les initiatives majeures.

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations sur cet article, consultez les ressources suivantes :

- [Architecture de la solution décisionnelle dans le centre d’excellence](center-of-excellence-business-intelligence-solution-architecture.md)
- Vous avez des questions ? [Essayez d’interroger la communauté Power BI](https://community.powerbi.com/)
- Vous avez des suggestions ? [Envoyez-nous vos idées pour améliorer Power BI](https://ideas.powerbi.com/)
