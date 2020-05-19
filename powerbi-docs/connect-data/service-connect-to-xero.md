---
title: Se connecter à Xero avec Power BI
description: Xero pour Power BI
author: paulinbar
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: conceptual
ms.date: 03/06/2020
ms.author: painbar
LocalizationGroup: Connect to services
ms.openlocfilehash: adb2f66b043b09ecb584870cf96f4c491960d59b
ms.sourcegitcommit: bfc2baf862aade6873501566f13c744efdd146f3
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83348433"
---
# <a name="connect-to-xero-with-power-bi"></a>Se connecter à Xero avec Power BI
Xero est un logiciel de comptabilité en ligne facile à utiliser, conçu spécifiquement pour les petites entreprises. Créez des visualisations attrayantes sur la base des informations financières de Xero avec cette application de modèle Power BI. Votre tableau de bord par défaut comprend plusieurs mesures liées aux petites entreprises, comme l’état de la trésorerie, les recettes et les dépenses, les tendances liées aux bénéfices, les délais moyens de paiement et le retour sur investissement.

Connectez-vous à [l’application de modèle Xero](https://app.powerbi.com/getdata/services/xero) pour Power BI ou obtenez plus d’informations sur l’intégration de [Xero et Power BI](https://help.xero.com/Power-BI).

## <a name="how-to-connect"></a>Comment se connecter

[!INCLUDE [powerbi-service-apps-get-more-apps](../includes/powerbi-service-apps-get-more-apps.md)]

3. Sélectionnez **Xero** \> **Obtenir maintenant**.
4. Dans **Installer cette application Power BI ?** , sélectionnez**Installer**.

    ![Installer Xero](media/service-connect-to-xero/power-bi-install-xero.png)

4. Dans le volet **Applications**, sélectionnez la vignette **Xero**.

   ![Sélectionner la vignette Xero](media/service-connect-to-xero/power-bi-start-xero.png)

6. Dans **Démarrer avec votre nouvelle application**, sélectionnez **Se connecter**.

    ![Démarrer avec votre nouvelle application](media/service-connect-to-zendesk/power-bi-new-app-connect-get-started.png)

4. Entrez le surnom de l’organisation associée à votre compte Xero. Peu importe le surnom, il s’agit principalement d’aider les utilisateurs avec plusieurs entreprises Xero à rester organisés. Pour plus d’informations, consultez [Recherche de paramètres](#FindingParams) plus loin dans cet article.

    ![Surnom de l’organisation](media/service-connect-to-xero/params.png)

5. Pour **Méthode d’authentification**, sélectionnez **OAuth**. Lorsque vous y êtes invité, connectez-vous à votre compte Xero et sélectionnez l’organisation à laquelle vous souhaitez vous connecter. Une fois la connexion terminée, sélectionnez **Connexion** pour démarrer le processus de chargement.
   
    ![Méthode d’authentification](media/service-connect-to-xero/creds.png)
   
    ![Welcome to Xero](media/service-connect-to-xero/creds2.png)
6. Après l’approbation, le processus d’importation démarre automatiquement. Une fois le processus terminé, un nouveau tableau de bord, un nouveau rapport et un nouveau modèle apparaissent dans le volet de navigation. Sélectionnez le tableau de bord pour afficher vos données importées.
   
     ![Tableau de bord Xero](media/service-connect-to-xero/power-bi-xero-dashboard.png)

**Et maintenant ?**

* Essayez de [poser une question dans la zone Q&R](../consumer/end-user-q-and-a.md) en haut du tableau de bord.
* [Modifiez les vignettes](../create-reports/service-dashboard-edit-tile.md) dans le tableau de bord.
* [Sélectionnez une vignette](../consumer/end-user-tiles.md) pour ouvrir le rapport sous-jacent.
* Même si une actualisation quotidienne de votre jeu de données est planifiée, vous pouvez modifier la planification de l’actualisation ou essayer d’actualiser le jeu de données sur demande à l’aide de l’option **Actualiser maintenant**.

## <a name="whats-included"></a>Ce qui est inclus
L’application de modèle pour tableau de bord comprend des vignettes et des mesures qui couvrent différents domaines, avec les rapports correspondants pour en savoir plus :  

| Zone | Vignettes du tableau de bord | Rapport |
| --- | --- | --- |
| Trésorerie |Flux de trésorerie quotidienne <br>Trésorerie entrante <br>Trésorerie sortante <br>Solde de clôture par compte <br>Solde de clôture aujourd’hui |Comptes bancaires |
| Client |Ventes facturées <br>Ventes facturées par client <br>Tendance de croissance des ventes facturées <br>Factures échues <br>Comptes client en attente <br>Comptes client en retard |Client <br>Inventaire |
| Fournisseur |Facturation des achats <br>Facturation des achats par fournisseur <br>Tendance de facturation des achats <br> Factures échues <br>Comptes fournisseur en attente <br>Comptes fournisseur en retard |Fournisseurs <br>Inventaire |
| Inventaire |Montant des ventes mensuelles par produit |Inventaire |
| Résultat |Résultat mensuel <br>Bénéfice net pour cet exercice <br>Bénéfice net pour ce mois <br>Principaux comptes de frais |Résultat |
| Bilan |Total actif <br>Total passif <br>Capitaux propres |Bilan |
| Santé |Ratio actuel <br>Pourcentage de marge brute <br> Retour sur le total des actifs <br>Ration passif total/capitaux propres |Santé <br>Glossaire et notes techniques |

Le jeu de données comprend également les tableaux suivants pour personnaliser vos rapports et vos tableaux de bord :  

* Adresses  
* Alertes  
* Relevé de compte quotidien  
* Relevés bancaires  
* Contacts  
* Notes de frais  
* Lignes de facturation  
* Factures  
* Éléments  
* Fin de mois  
* Organisation  
* Trial Balance  
* Comptes Xero

## <a name="system-requirements"></a>Configuration requise
Les rôles suivants sont nécessaires pour accéder à l’application de modèle Xero : « Standard + Rapports » ou « Advisor ».

<a name="FindingParams"></a>

## <a name="finding-parameters"></a>Recherche de paramètres
Indiquez le nom de l’organisation à suivre dans Power BI. Un nom spécifique permet de vous connecter à plusieurs organisations différentes. Vous ne pouvez pas vous connecter à la même organisation plusieurs fois, car cela affecte l’actualisation planifiée.   

## <a name="troubleshooting"></a>Résolution des problèmes
* Les utilisateurs Xero ont besoin des rôles suivants pour accéder à l’application de modèle Xero pour Power BI : « Standard + Rapports » ou « Advisor ». L’application de modèle s’appuie sur les autorisations utilisateur pour accéder aux données de rapports via Power BI.
* Lors du chargement, les vignettes du tableau de bord sont dans un état de chargement générique. Elles restent ainsi jusqu’à ce que la charge complète soit terminée. Si vous recevez une notification indiquant que le chargement est terminé alors que les vignettes sont toujours en cours de chargement, essayez d’actualiser les vignettes du tableau de bord en utilisant les points de suspension (...) en haut à droite de votre tableau de bord.
* Si votre application de modèle ne parvient pas à s’actualiser, vérifiez si vous êtes connecté plusieurs fois à la même organisation dans Power BI. Xero autorise une seule connexion active à une organisation et vous risquez de voir une erreur indiquant que vos informations d’identification ne sont pas valides si vous vous connectez à la même organisation plusieurs fois.  
* En cas de problème de connexion de l’application de modèle Xero pour Power BI, par exemple des messages d’erreur ou un temps de chargement prolongé, videz d’abord le cache et effacez les cookies et redémarrez le navigateur, puis reconnectez-vous à Power BI.  

Pour tout autre problème qui persiste, envoyez un ticket sur https://support.powerbi.com.

## <a name="next-steps"></a>Étapes suivantes
[Prise en main de Power BI](../fundamentals/service-get-started.md)

[Obtenir des données dans Power BI](service-get-data.md)
