---
title: Utiliser la fonctionnalité Questions et réponses avec des connexions actives dans Power BI
description: Documentation sur l’utilisation de requêtes en langage naturel dans Questions et réponses Power BI avec des connexions actives vers des données Analysis Services et la passerelle de données locale.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: mihart
ms.service: powerbi
ms.subservice: pbi-reports-dashboards
ms.topic: how-to
ms.date: 05/29/2020
LocalizationGroup: Ask questions of your data
ms.openlocfilehash: 4e64121fdac63abe22d77818a0f91a860cac316f
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2020
ms.locfileid: "96388146"
---
# <a name="enable-qa-for-live-connections-in-power-bi"></a>Activer la fonctionnalité Questions et réponses pour les connexions actives dans Power BI

Vous pouvez importer des jeux de données dans Power BI ou vous pouvez créer une *connexion active* à ceux-ci. Les jeux de données d’une connexion active sont souvent locaux. Si c’est le cas, vous gérez les connexions actives en utilisant une [passerelle](../connect-data/service-gateway-onprem.md). Les données et les recherches sont envoyées et retournent leurs résultats via des requêtes actives.

> [!NOTE]
> Les connexions actives prennent également en charge les jeux de données Azure Analysis Services, qui ne nécessitent pas de passerelle.

## <a name="qa-for-on-premises-data-gateway-datasets"></a>Questions et réponses pour les jeux de données de la passerelle de données locale
Si vous souhaitez utiliser les Q&R avec des jeux de données auxquels vous accédez par le biais d’une passerelle, vous devez d’abord les activer.

Une fois activé, Power BI crée un index de votre source de données et charge un sous-ensemble de ces données dans Power BI pour permettre de poser des questions. L’opération de création de l’index initial peut prendre plusieurs minutes et Power BI effectue la maintenance et la mise à jour de l’index automatiquement à mesure que vos données évoluent. L’utilisation des Q&R avec ces jeux de données entraîne le même comportement qu’avec les données publiées sur Power BI. L’ensemble complet des fonctionnalités disponibles dans Questions et réponses est pris en charge dans les deux cas.

Lorsque vous posez des questions dans Power BI, les Q&R déterminent le meilleur visuel de construction ou de feuille de rapport à utiliser pour répondre à votre question à l’aide d’un index de votre jeu de données. Après avoir déterminé la meilleure réponse potentielle, les Q&R utilisent DirectQuery pour extraire des données actives à partir de la source de données à travers la passerelle pour remplir des graphiques et des diagrammes. De cette façon, Questions et réponses Power BI affiche toujours les données les plus récentes, directement à partir de la source de données sous-jacente.

Comme les Q&R Power BI utilisent des valeurs de texte et le schéma à partir de votre source de données pour déterminer comment interroger le modèle sous-jacent, les recherches de valeurs de texte spécifiques nouvelles ou supprimées (par exemple, en demandant un nom de client associé à un enregistrement de texte nouvellement ajouté) doivent pouvoir s’appuyer sur un index mis à jour avec les valeurs les plus récentes. Power BI met automatiquement à jour l’index de texte et de schéma dans une fenêtre de 60 minutes.

Pour plus d’informations, consultez :

* Qu’est-ce que la [passerelle de données locale](../connect-data/service-gateway-onprem.md) ?
* [Q&R Power BI pour les consommateurs](../consumer/end-user-q-and-a.md)

## <a name="enable-qa"></a>Activer les Q&R
Une fois que vous avez configuré la passerelle de données, connectez-vous à vos données à partir de Power BI.  Créez un tableau de bord à l’aide de vos données locales ou téléchargez un fichier .pbix qui utilise des données locales.  Vous pouvez également disposer déjà des données locales dans des tableaux de bord, des rapports et des jeux de données qui ont été partagés avec vous.

1. En haut à droite de Power BI, sélectionnez l’icône de roue dentée ![icône d’engrenage](media/service-q-and-a-direct-query/power-bi-cog.png), puis choisissez **Paramètres**.
   
   ![menu Paramètres](media/service-q-and-a-direct-query/powerbi-settings.png)
2. Sélectionnez **Jeux de données**, puis choisissez le jeu de données à activer pour les Q&R.
   
   ![écran Jeux de données du menu Paramètres](media/service-q-and-a-direct-query/power-bi-q-and-a-settings.png)
3. Développez **Questions et réponses**, cochez la case **Activer Questions et réponses pour ce jeu de données** et choisissez **Appliquer**.
   
    ![Zone Questions et réponses développée](media/service-q-and-a-direct-query/power-bi-qna-dataset-direct-query.png)

## <a name="what-data-is-cached-and-how-is-privacy-protected"></a>Quelles sont les données mises en cache et quelle est la politique de confidentialité ?
Lorsque vous activez les Q&R pour vos données locales, un sous-ensemble de données est mis en cache dans le service. Cette mise en cache garantit à Questions et réponses des performances raisonnables. Power BI exclut les valeurs dépassant 24 caractères de la mise en cache. Le cache est supprimé après quelques heures une fois les Q&R désactivées en décochant la case permettant **d’activer les Q&R pour ce jeu de données**, ou lorsque vous supprimez votre jeu de données.

## <a name="considerations-and-troubleshooting"></a>Considérations et résolution des problèmes
La fonctionnalité présente certaines limitations :

* Initialement, la fonctionnalité n’est disponible que pour les sources de données tabulaires SQL Server 2016 Analysis Services. La fonctionnalité est optimisée pour travailler avec des données tabulaires. L’expérience de Questions et réponses n’est pas encore prise en charge pour les données multidimensionnelles. D’autres sources de données prises en charge par la passerelle de données locale seront déployées au fil du temps.
* La prise en charge complète de la sécurité au niveau des lignes définie dans SQL Server Analysis Services n’est pas disponible initialement. Lorsque vous posez des questions dans Questions et réponses, la « saisie semi-automatique » des questions peut afficher des valeurs de chaînes auxquelles un utilisateur n’a pas accès. Toutefois, la sécurité au niveau des lignes définie dans le modèle est respectée pour les rapports et graphiques visuels. Aucune donnée numérique sous-jacente ne peut donc être exposée. Des options permettant de contrôler ce comportement seront disponibles dans des prochaines mises à jour.
* La sécurité au niveau objet (OLS) n’est pas prise en charge. Questions et réponses ne respecte pas la sécurité au niveau objet et peut révéler les noms de tables ou de colonnes aux utilisateurs qui n’y ont pas accès. Vous avez tout intérêt à activer la sécurité au niveau des lignes (RLS) de façon à sécuriser aussi les valeurs de données. 
* Les connexions actives sont uniquement prises en charge avec la passerelle de données locale. Par conséquent, cette fonctionnalité ne peut pas être utilisée avec la passerelle personnelle.

## <a name="next-steps"></a>Étapes suivantes

- [On-premises data gateway (Passerelle de données locale)](../connect-data/service-gateway-onprem.md)  
- [Gérer votre source de données - Analysis Services](../connect-data/service-gateway-enterprise-manage-ssas.md)  
- [Fondamentaux pour les concepteurs dans le service Power BI](../fundamentals/service-basic-concepts.md)  
- [Présentation de Questions et réponses dans Power BI](../consumer/end-user-q-and-a.md)  

D’autres questions ? [Essayez d’interroger la communauté Power BI](https://community.powerbi.com/)
