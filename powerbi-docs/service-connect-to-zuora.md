---
title: Se connecter à Zuora avec Power BI
description: Zuora pour Power BI
services: powerbi
documentationcenter: ''
author: SarinaJoan
manager: kfile
backup: maggiesMSFT
editor: ''
tags: ''
qualityfocus: no
qualitydate: ''
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 10/16/2017
ms.author: sarinas
LocalizationGroup: Connect to services
ms.openlocfilehash: 2f7e4c666cf6ec3cb69424a3922f5feedd61bf89
ms.sourcegitcommit: 88c8ba8dee4384ea7bff5cedcad67fce784d92b0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/24/2018
---
# <a name="connect-to-zuora-with-power-bi"></a>Se connecter à Zuora avec Power BI
Zuora pour Power BI vous permet de visualiser des données importantes sur votre chiffre d’affaires, votre facturation et vos abonnements. Utilisez le tableau de bord et les rapports par défaut pour analyser les tendances d’utilisation, suivre la facturation et les paiements, et surveiller les revenus réguliers, ou personnalisez-les pour répondre à vos besoins uniques.

Connectez-vous à [Zuora](https://app.powerbi.com/getdata/services/Zuora) pour Power BI.

## <a name="how-to-connect"></a>Comment se connecter
1. Sélectionnez **Obtenir des données** en bas du volet de navigation gauche.

   ![](media/service-connect-to-zuora/getdata.png)
2. Dans la zone **Services** , sélectionnez **Obtenir**.

   ![](media/service-connect-to-zuora/services.png)
3. Sélectionnez **Zuora** \>  **Obtenir**.

   ![](media/service-connect-to-zuora/zuora.png)
4. Spécifiez l’URL de Zuora (en général, https://www.zuora.com). (en général, https://www.zuora.com). Consultez les détails sur la [recherche de ces paramètres](#FindingParams) ci-dessous.

   ![](media/service-connect-to-zuora/params.png)
5. Pour **Méthode d’authentification**, sélectionnez **Basic** et indiquez vos nom d’utilisateur et mot de passe (en respectant la casse), puis sélectionnez **Se connecter**.

    ![](media/service-connect-to-zuora/creds.png)
6. Après l’approbation, le processus d’importation démarre automatiquement. Une fois terminé, de nouveaux tableau de bord, rapport et modèle apparaîtront dans le volet de navigation. Sélectionnez le tableau de bord pour afficher vos données importées.

     ![](media/service-connect-to-zuora/dashboard.png)

**Et maintenant ?**

* Essayez de [poser une question dans la zone Q&R](power-bi-q-and-a.md) en haut du tableau de bord.
* [Modifiez les vignettes](service-dashboard-edit-tile.md) dans le tableau de bord.
* [Sélectionnez une vignette](service-dashboard-tiles.md) pour ouvrir le rapport sous-jacent.
* Même si une actualisation quotidienne de votre jeu de données est planifiée, vous pouvez modifier la planification de l’actualisation ou essayer d’actualiser le jeu de données sur demande à l’aide de l’option **Actualiser maintenant**.

## <a name="whats-included"></a>Ce qui est inclus
Le pack de contenu utilise l’API Zuora AQUA pour exploiter les tables suivantes :

| Tableaux |  |  |
| --- | --- | --- |
| Account |InvoiceItemAdjustment |Refund |
| AccountingCode |Payment |RevenueSchedule |
| AccountingPeriod |PaymentMethod |RevenueScheduleItem |
| BillTo |Product |Subscription |
| DateDim |ProductRatePlan |TaxationItem |
| Invoice |ProductRatePlanCharge |Utilisation |
| InvoiceAdjustment |RatePlan | |
| InvoiceItem |RatePlanCharge | |

Il inclut également ces mesures calculées :

| Mesure | Description | Pseudo-calcul |
| --- | --- | --- |
| Compte : Paiements |Totaux payés sur une période, en fonction de la date d’effet du paiement. |SUM (Payment.Amount) <br>WHERE<br>Payment.EffectiveDate =< TimePeriod.EndDate<br>AND    Payment.EffectiveDate >= TimePeriod.StartDate |
| Compte : Remboursements |Totaux de remboursement sur une période, en fonction de la date de remboursement. La quantité est signalée comme un nombre négatif. |-1*SUM(refund.amount)<br>WHERE<br>Refund.RefundDate =< TimePeriod.EndDate<br>AND    Refund.RefundDate >= TimePeriod.StartDate |
| Compte : Paiements nets |Paiements de compte plus remboursements de compte sur une période. |Account.Payments + Account.Refunds |
| Compte : Comptes actifs |Nombre de comptes actifs sur une période. Les abonnements doivent avoir commencé avant ou à la date de début de période. |COUNT (Account.AccountNumber)<br>WHERE<br>    Subscription.Status != "Expiré"<br>AND    Subscription.Status != "Brouillon"<br>AND    Subscription.SubscriptionStartDate <= TimePeriod.StartDate<br>AND    (Subscription.SubscriptionEndDate > TimePeriod.StartDate<br>OR<br>Subscription.SubscriptionEndDate = null) –evergreen subscription |
| Compte : Revenu récurrent moyen |Revenu récurrent mensuel (MRR) brut par compte actif sur une période. |MRR brut / Account.ActiveAccounts |
| Compte : Cancelled Subscriptions |Nombre de comptes qui ont annulé un abonnement sur une période donnée. |COUNT (Account.AccountNumber)<br>WHERE<br>Subscription.Status = "Annulé"<br>AND    Subscription.SubscriptionStartDate <= TimePeriod.StartDate<br>AND    Subscription.CancelledDate >= TimePeriod.StartDate |
| Compte : Erreurs de paiement |Valeur totale des erreurs de paiement. |SUM (Payment.Amount)<br>WHERE<br>Payment.Status = "Erreur" |
| Revenue Schedule Item: Recognized Revenue |Revenus totaux identifiés sur une période comptable. |SUM (RevenueScheduleItem.Amount)<br>WHERE<br>AccountingPeriod.StartDate = TimePeriod.StartDate |
| Abonnement : Nouveaux abonnements. |Nombre de nouveaux abonnements sur une période. |COUNT (Subscription.ID)<br>WHERE<br>Subscription.Version = "1"<br>AND    Subscription.CreatedDate <= TimePeriod.EndDate<br>AND    Subscription.CreatedDate >= TimePeriod.StartDate |
| Facture : Éléments de facturation |Montants totaux des éléments facturés sur une période. |SUM (InvoiceItem.ChargeAmount)<br>WHERE<br>    Invoice.Status = "Publié"<br>AND    Invoice.InvoiceDate <= TimePeriod.EndDate<br>AND    Invoice.InvoiceDate >= TimePeriod.StartDate |
| Facture : Éléments de taxation |Montants totaux de taxation sur une période. |SUM (TaxationItem.TaxAmount)<br>WHERE<br>Invoice.Status = "Publié"<br>AND    Invoice.InvoiceDate <= TimePeriod.EndDate<br>AND    Invoice.InvoiceDate >= TimePeriod.StartDate |
| Facture : Ajustements d’éléments de facturation |Montants totaux d’éléments de facturation sur une période. |SUM (InvoiceItemAdjustment.Amount) <br>WHERE<br>    Invoice.Status = "Publié"<br>AND    InvoiceItemAdjustment.AdjustmentDate <= TimePeriod.EndDate<br>AND    InvoiceItemAdjustment.AdjustmentDate >= TimePeriod.StartDate |
| Facture : Ajustements de facturation |Montants totaux d’ajustements de facturation sur une période. |SUM (InvoiceAdjustment.Amount) <br>WHERE<br>    Invoice.Status = "Publié"<br>AND    InvoiceAdjustment.AdjustmentDate <= TimePeriod.EndDate<br>AND    InvoiceAdjustment.AdjustmentDate >= TimePeriod.StartDate |
| Facture : facturation nette |Somme des éléments de facturation, de taxation, d’ajustements d’éléments facturation et d’ajustement de facturation sur une période. |Invoice.InvoiceItems + Invoice.TaxationItems + Invoice.InvoiceItemAdjustments + Invoice.InvoiceAdjustments |
| Facture : Soldes facture |Somme des soldes de facture publiés. |SUM (Invoice.Balance) <br>WHERE<br>    Invoice.Status = "Publié" |
| Facture : facturation brute |Somme des montants bruts de facture sur une période. |SUM (InvoiceItem.ChargeAmount) <br>WHERE<br>    Invoice.Status = "Publié"<br>AND    Invoice.InvoiceDate <= TimePeriod.EndDate<br>AND    Invoice.InvoiceDate >= TimePeriod.StartDate |
| Facture : Ajustements totaux |Somme des ajustements de facturation traité et des ajustements d’éléments de facturation associés à des factures publiées. |SUM (InvoiceAdjustment.Amount) <br>WHERE<br>    Invoice.Status = "Publié"<br>AND    InvoiceAdjustment.Status = "Processed"<br>+<br>SUM (InvoiceItemAdjustment.Amount) <br>WHERE<br>    Invoice.Status = "Publié"<br>AND    invoiceItemAdjustment.Status = "Processed" |
| Frais de plan de taux : MRR brut |Somme du revenu récurrent mensuel (MRR) à partir d’abonnement sur une période donnée. |SUM (RatePlanCharge.MRR) <br>WHERE<br>    Subscription.Status != "Expiré"<br>AND    Subscription.Status != "Brouillon"<br>AND    RatePlanCharge.EffectiveStartDate <= TimePeriod.StartDate<br>AND        RatePlanCharge.EffectiveEndDate > TimePeriod.StartDate<br>    OR    RatePlanCharge.EffectiveEndDate = null --evergreen subscription |

## <a name="system-requirements"></a>Configuration requise
Vous devez avoir accès à l’API Zuora.

<a name="FindingParams"></a>

## <a name="finding-parameters"></a>Recherche de paramètres
Indiquez l’URL que vous utilisez généralement pour vous connecter à vos données Zuora. Les options valides sont les suivantes :  

* https://www.zuora.com  
* https://www.apisandbox.zuora.com  
* URL correspondant à votre instance de service  

## <a name="troubleshooting"></a>Résolution des problèmes
Le pack de contenu Zuora extrait différents aspects de votre compte Zuora. Si vous n’utilisez pas certaines fonctionnalités, les vignettes/rapports correspondants peuvent être vides. Si vous vous heurtez à des problèmes lors du chargement, contactez le support technique dédié à Power BI.

## <a name="next-steps"></a>Étapes suivantes
[Prise en main de Power BI](service-get-started.md)

[Obtenir des données dans Power BI](service-get-data.md)
