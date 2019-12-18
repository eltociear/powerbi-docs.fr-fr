---
title: Soumettre un visuel Power BI à AppSource à l'aide du tableau de bord vendeur
description: Soumettre un visuel Power BI à AppSource à l'aide du tableau de bord vendeur
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.topic: conceptual
ms.subservice: powerbi-custom-visuals
ms.date: 12/03/2019
ms.openlocfilehash: 12ecde787bb268190f9b94a2db5992d5840080ac
ms.sourcegitcommit: 5bb62c630e592af561173e449fc113efd7f84808
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2019
ms.locfileid: "75002532"
---
# <a name="submit-a-power-bi-visual-to-appsource-using-seller-dashboard"></a>Soumettre un visuel Power BI à AppSource à l'aide du tableau de bord vendeur

Vous devez envoyer un e-mail avec les fichiers **pbiviz** et **pbix** à l’équipe Power BI avant la soumission à AppSource. L’équipe Power BI peut ainsi charger les fichiers sur le serveur de partage public. Sinon, le Store ne peut pas récupérer les fichiers. Vous devez envoyer les fichiers à chaque soumission d’un nouveau visuel Power BI, mises à jour d’un visuel existant et correctifs apportés aux soumissions rejetées.

>[!NOTE]
>[Le tableau de bord vendeur](https://docs.microsoft.com/office/dev/store/use-the-seller-dashboard-to-submit-to-the-office-store) va être supprimé. Il sera remplacé par l’[Espace partenaires](https://docs.microsoft.com/partner-center/). N'utilisez le tableau de bord vendeur que si une soumission de visuel Power BI est en cours. Si vous soumettez un nouveau visuel Power BI à AppSource, utilisez la [méthode de l’Espace partenaires](office-store.md#submitting-to-appsource).

### <a name="seller-dashboard-submission-process"></a>Processus de soumission dans le tableau de bord vendeur

Vous devez avoir un compte de développeur Office valide pour vous connecter au [Centre pour développeurs Office](https://dev.office.com/). Un compte de développeur Office doit être un compte Microsoft Live ID, par exemple hotmail.com ou outlook.com.

1. Accédez au [Centre de développement](https://sellerdashboard.microsoft.com/Application/Summary).

2. Sélectionnez **Ajouter une nouvelle application**.

    ![Ajouter une application](media/office-store/powerbi-custom-visual-add-an-app.png)

3. Sélectionnez **Visuel personnalisé Power BI**, puis **Suivant**.

4. Sélectionnez le signe **+** sous **Package d’application** et sélectionnez le fichier XML de package d’application que vous avez reçu de l’équipe Power BI à partir de la boîte de dialogue Ouvrir un fichier.

    ![Package d’application](media/office-store/powerbi-custom-visual-apppackage.png)

5. Vous devez recevoir une approbation indiquant qu’il s’agit d’un package d’application Power BI valide.

    ![Manifeste approuvé](media/office-store/powerbi-custom-visual-manifest-approved.png)

6. Remplissez les détails dans la fenêtre **Informations générales**.

   * *Titre de la soumission :* indiquez le nom qui sera donné à votre soumission dans le centre de développement.
   * *Version :* votre numéro de version est rempli automatiquement à partir du package de l’application complémentaire.
   * *Date de sortie (UTC) :* sélectionnez la date de publication de votre application dans le magasin. Si vous choisissez une date ultérieure, votre application n’est pas disponible dans le Store jusqu’à cette date.
   * *Catégorie :* la première catégorie est automatiquement remplie comme suit : « Visualisation des données + BI ». C’est la façon dont tous les visuels Power BI sont marqués. Pour aider les utilisateurs à rechercher facilement votre visuel, vous pouvez fournir jusqu'à deux catégories supplémentaires.
   * *Remarques relatives au test (facultatives) :* cette option est utile si vous souhaitez fournir des instructions pour les testeurs Microsoft
   * *Mon application fait appel à des solutions de chiffrement, prend en charge, contient ou utilise ce type de technologie :* gardez cette option désélectionnée.
   * *Ajouter ce complément au catalogue des compléments Office sur iPad :* gardez cette option désélectionnée.
7. Chargez le logo de votre visuel en sélectionnant le signe **+** sous **Logo de l’application**. Sélectionnez ensuite le fichier d’icône dans la boîte de dialogue Ouvrir un fichier. .png, .jpg, .jpeg et .gif sont les formats autorisés. Le fichier doit avoir une taille de 300 px (largeur) sur 300 px (hauteur) et ne doit pas dépasser 512 Ko.

    ![Logo de l'application](media/office-store/powerbi-custom-visual-app-logo.png)

8. Indiquez les informations requises dans **Documents de support**.

   * Lien vers les documents de support
   * Lien vers le document sur la confidentialité
   * Lien vers la vidéo
   * Contrat de Licence Utilisateur Final (CLUF)

       Vous devez charger un fichier CLUF. Il peut s’agir de votre propre fichier CLUF ou du fichier CLUF par défaut de l’Office Store pour les visuels Power BI. Pour utiliser le contrat CLUF par défaut, collez l’URL suivante dans la boîte de dialogue de chargement du fichier « Contrat de licence utilisateur final » du tableau de bord vendeur : [https://visuals.azureedge.net/app-store/Power BI - Default Custom Visual EULA.pdf](https://visuals.azureedge.net/app-store/Power%20BI%20-%20Default%20Custom%20Visual%20EULA.pdf).

9. Sélectionnez **Suivant** pour accéder à la page **Détails**.

10. Sélectionnez **Langue**, puis choisissez une langue dans la liste.

    ![Langue](media/office-store/powerbi-custom-visual-language.png)

11. Remplissez la description.

    * *Nom de l’application (pour cette langue) :* indiquez le nom de votre application tel qu’il doit apparaître dans la vitrine.
    * *Description courte :* entrez une courte description de votre application (100 caractères maximum), telle qu’elle doit apparaître dans la vitrine. Cette description s’affiche dans les pages de niveau supérieur avec le logo. Vous pouvez utiliser la description du package pbiviz.
    * *Description longue :* donnez une description plus détaillée de l’application. Les clients pourront la voir sur la page des détails de votre application. Si vous souhaitez laisser la communauté améliorer votre visuel en le rendant open source, fournissez le lien vers le référentiel public, en l’occurrence GitHub.

12. Chargez au moins une capture d’écran. Les formats .png, .jpg, .jpeg et .gif sont disponibles. Le format doit faire exactement 1366 px (largeur) x 768 px (hauteur). La taille de fichier ne peut pas être supérieure à 1 024 Ko. *Pour une utilisation optimale, ajoutez des bulles de texte pour expliquer la proposition de valeur des principales fonctionnalités affichées dans chaque capture d’écran.*

12. Si vous souhaitez ajouter d’autres langues, sélectionnez **Ajouter une langue** et répétez les étapes 10 et 11. Ajouter d’autres langues aide vos utilisateurs à afficher les détails du visuel personnalisé dans leur propre langue. Pour les langues non répertoriées, la première langue sélectionnée s’affiche par défaut.

13. Lorsque vous avez terminé l’ajout de langues, sélectionnez **Suivant** pour passer à la page **Bloquer l’accès**.

14. Si vous souhaitez empêcher les clients de pays ou régions spécifiques d’acheter votre application, activez la case à cocher et choisissez une option dans la liste.

15. Sélectionnez **Suivant** pour accéder à la page **Tarification**.

16. Actuellement, seuls les visuels *gratuits* sont pris en charge et les achats supplémentaires au sein du visuel (achat dans l’application) ne sont pas autorisés. Sélectionnez **Cette application est gratuite**.

    > [!NOTE]
    > Si vous sélectionnez une autre option ou que vous avez inséré du contenu de type Achat dans l’application dans le visuel soumis, la soumission est rejetée.

17. Vous pouvez maintenant sélectionner **Enregistrer comme brouillon** et envoyer le visuel plus tard, ou choisir **Envoyer pour approbation** pour envoyer le visuel personnalisé à l’Office Store.

## <a name="seller-dashboard-certification-submission-process"></a>Processus de soumission pour la certification dans le tableau de bord vendeur

Suivez les instructions de cette section afin de soumettre un visuel Power BI pour certification dans le tableau de bord vendeur. Utilisez cette méthode si vous avez déjà soumis un visuel Power BI à AppSource en utilisant le tableau de bord vendeur.

1. Envoyez un e-mail à l’équipe de support technique des visuels Power BI (pbicvsupport@microsoft.com). Dans l’e-mail, incluez les informations suivantes :
    * Titre : Demande de certification de visuel
    * Lien vers le dépôt GitHub où est hébergé le code source contrôlable de visu
    * [Respect des exigences](power-bi-custom-visuals-certified.md#certification-requirements)
    * Revue du code réussie

2. L’équipe de Microsoft en charge des visuels Power BI vous avertit quand votre visuel Power BI est certifié et ajouté à la [liste certifiée](power-bi-custom-visuals-certified.md#list-of-power-bi-visuals-that-have-been-certified). S’il est rejeté, un rapport des problèmes à résoudre vous est envoyé. Il incombe au développeur d’ouvrir et de maintenir ouverte une ligne de communication avec Microsoft, ainsi que de mettre à jour ses visuels certifiés au besoin.

## <a name="tracking-submission-status-and-usage"></a>Suivi de l’utilisation et de l’état de la soumission

Vous pouvez passer en revue les [stratégies de validation](https://dev.office.com/officestore/docs/validation-policies#13-power-bi-custom-visuals).

Après l’envoi de la soumission, vous pouvez afficher son état dans le [tableau de bord de l’application](https://sellerdashboard.microsoft.com/Application/Summary/).

## <a name="certify-your-visual"></a>Certifier votre visuel

Une fois votre visuel créé, vous pouvez le faire [certifier](../developer/power-bi-custom-visuals-certified.md).

## <a name="next-steps"></a>Étapes suivantes

[Développement d’un visuel personnalisé Power BI](visuals/custom-visual-develop-tutorial.md)  
[Visualisations dans Power BI](../visuals/power-bi-report-visualizations.md)  
[Visualisations personnalisées dans Power BI](../developer/power-bi-custom-visuals.md)  
[Faire certifier un visuel Power BI](../developer/power-bi-custom-visuals-certified.md)

D’autres questions ? [Essayez d’interroger la communauté Power BI](https://community.powerbi.com/)
