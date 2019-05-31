---
title: Se connecter à Xero avec Power BI
description: Xero pour Power BI
author: SarinaJoan
manager: kfile
ms.reviewer: maggiesMSFT
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: conceptual
ms.date: 10/16/2017
ms.author: sarinas
LocalizationGroup: Connect to services
ms.openlocfilehash: d09936f2cce1d7835efdb82929d9e8eed2291163
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "61156312"
---
# <a name="connect-to-xero-with-power-bi"></a>Se connecter à Xero avec Power BI
Xero est un logiciel de comptabilité en ligne facile à utiliser, conçu spécifiquement pour les petites entreprises. Créez des visualisations attrayantes sur la base des informations financières de Xero avec ce pack de contenu Power BI. Votre tableau de bord par défaut comprend plusieurs mesures liées aux petites entreprises, comme l’état de la trésorerie, les recettes et les dépenses, les tendances liées aux bénéfices, les jours débiteur et le retour sur investissement.

Connectez-vous au [pack de contenu Xero](https://app.powerbi.com/getdata/services/xero) pour Power BI ou obtenez plus d’informations sur l’intégration de [Xero et Power BI](https://help.xero.com/Power-BI).

## <a name="how-to-connect"></a>Comment se connecter
1. Sélectionnez **Obtenir des données** en bas du volet de navigation gauche.
   
   ![](media/service-connect-to-xero/getdata.png)
2. Dans la zone **Services**, sélectionnez **Obtenir**.
   
   ![](media/service-connect-to-xero/services.png)
3. Sélectionnez **Xero** \>  **Obtenir**.
   
   ![](media/service-connect-to-xero/connect.png)
4. Entrez le surnom de l’organisation associée à votre compte Xero. Peu importe le surnom, il s’agit principalement d’aider les utilisateurs avec plusieurs entreprises Xero à rester organisés. Passez en revue les détails [ci-dessous](#FindingParams).
   
   ![](media/service-connect-to-xero/params.png)
5. Dans **Méthode d’authentification**, sélectionnez **OAuth**. Lorsque vous y êtes invité, connectez-vous à votre compte Xero et sélectionnez l’organisation à laquelle vous souhaitez vous connecter. Une fois la connexion terminée, sélectionnez **Connexion** pour démarrer le processus de chargement.
   
    ![](media/service-connect-to-xero/creds.png)
   
    ![](media/service-connect-to-xero/creds2.png)
6. Après l’approbation, le processus d’importation démarre automatiquement. Une fois terminé, de nouveaux tableau de bord, rapport et modèle apparaîtront dans le volet de navigation. Sélectionnez le tableau de bord pour afficher vos données importées.
   
     ![](media/service-connect-to-xero/dashboard.png)

**Et maintenant ?**

* Essayez de [poser une question dans la zone Q&R](consumer/end-user-q-and-a.md) en haut du tableau de bord.
* [Modifiez les vignettes](service-dashboard-edit-tile.md) dans le tableau de bord.
* [Sélectionnez une vignette](consumer/end-user-tiles.md) pour ouvrir le rapport sous-jacent.
* Même si une actualisation quotidienne de votre jeu de données est planifiée, vous pouvez modifier la planification de l’actualisation ou essayer d’actualiser le jeu de données sur demande à l’aide de l’option **Actualiser maintenant**.

## <a name="whats-included"></a>Ce qui est inclus
Le pack de contenu pour tableau de bord comprend des vignettes et des mesures qui couvrent différents domaines, avec les rapports correspondants pour en savoir plus :  

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
* Bilan de vérification  
* Comptes Xero

## <a name="system-requirements"></a>Configuration requise
Les rôles suivants sont nécessaires pour accéder au pack de contenu Xero : « Standard + Rapports » ou « Advisor ».

<a name="FindingParams"></a>

## <a name="finding-parameters"></a>Recherche de paramètres
Indiquez le nom de l’organisation à suivre dans Power BI. Cela vous permet de vous connecter à plusieurs organisations différentes. Notez que vous ne pouvez pas vous connecter à la même organisation plusieurs fois, car cela affecte l’actualisation planifiée.   

## <a name="troubleshooting"></a>Résolution des problèmes
* Les utilisateurs Xero ont besoin des rôles suivants pour accéder au pack de contenu Xero pour Power BI : « Standard + Rapports » ou « Advisor ». Le pack de contenu s’appuie sur les autorisations utilisateur pour accéder aux données de rapports via Power BI.  
* Si vous recevez une erreur après le chargement pendant un certain temps, vérifiez au bout de combien de temps ce message d’erreur s’est affiché. Notez que le jeton d’accès fourni par Xero est uniquement valide pendant 30 minutes. Par conséquent, les comptes échouent s’ils contiennent plus de données que le volume pouvant être chargé dans ce laps de temps. Nous travaillons activement pour améliorer cette situation.
* Lors du chargement, les vignettes du tableau de bord sont dans un état de chargement générique. Cet état ne change pas jusqu’à la fin du chargement. Si vous recevez une notification indiquant que le chargement est terminé alors que les vignettes sont toujours en cours de chargement, essayez d’actualiser les vignettes du tableau de bord en utilisant les points de suspension (...) en haut à droite de votre tableau de bord.
* Si votre pack de contenu ne parvient pas à s’actualiser, vérifiez si vous êtes connecté plusieurs fois à la même organisation dans Power BI. Xero autorise une seule connexion active à une organisation et vous risquez de voir une erreur indiquant que vos informations d’identification ne sont pas valides si vous vous connectez à la même organisation plusieurs fois.  
* En cas de problème de connexion du pack de contenu Xero pour Power BI, par exemple des messages d’erreur ou un temps de chargement prolongé, videz d’abord le cache et effacez les cookies et redémarrez le navigateur, puis reconnectez-vous à Power BI.  

Pour tout autre problème qui persiste, envoyez un ticket sur http://support.powerbi.com.

## <a name="next-steps"></a>Étapes suivantes
[Prise en main de Power BI](service-get-started.md)

[Obtenir des données dans Power BI](service-get-data.md)

