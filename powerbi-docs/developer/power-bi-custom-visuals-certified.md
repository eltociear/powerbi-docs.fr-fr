---
title: Visuels Power BI certifiés
description: Exigences à respecter et procédure à suivre pour faire une demande de certification d’un visuel personnalisé, et liste des visuels Power BI certifiés.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
featuredvideoid: ''
ms.service: powerbi
ms.topic: conceptual
ms.subservice: powerbi-custom-visuals
ms.date: 03/08/2020
ms.openlocfilehash: eb42816c5281cb07a20968a3d7aa7411318c3d55
ms.sourcegitcommit: 87b7cb4a2e626711b98387edaa5ff72dc26262bb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/10/2020
ms.locfileid: "79041475"
---
# <a name="get-a-power-bi-visual-certified"></a>Obtenir un visuel Power BI certifié

Les visuels Power BI certifiés sont des visuels Power BI [d’AppSource](https://appsource.microsoft.com/en-us/marketplace/apps?page=1&product=power-bi-visuals) conformes aux [exigences de code](#certification-requirements) de l’équipe Microsoft Power BI. Ces visuels sont testés pour vérifier qu’ils n’accèdent pas à des services ou ressources externes, et qu’ils suivent les modèles et instructions de codage sécurisé.

Un visuel Power BI certifié offre davantage de fonctionnalités. Par exemple, vous pouvez [exporter vers PowerPoint](../consumer/end-user-powerpoint.md) ou afficher le visuel dans les e-mails reçus quand un utilisateur [s’abonne aux pages du rapport](../consumer/end-user-subscribe.md).

Le processus de certification est facultatif. Les visuels Power BI non certifiés ne sont pas nécessairement des visuels Power BI non sécurisés. Certains visuels Power BI ne sont pas certifiés parce qu’ils ne sont pas conformes à une ou plusieurs [exigences de certification](https://docs.microsoft.com/power-bi/power-bi-custom-visuals-certified?#certification-requirements), par exemple un visuel Power BI de type carte se connectant à un service externe ou un visuel Power BI utilisant des bibliothèques commerciales.

> [!NOTE]
> Microsoft n’est pas l’auteur des visuels Power BI de tiers. Pour vérifier le fonctionnement des visuels de tiers, contactez directement leur auteur.

## <a name="certification-requirements"></a>Critères de certification

Votre visuel Power BI doit être conforme aux exigences listées dans cette section pour que vous puissiez le faire [certifier](#get-a-power-bi-visual-certified). 

### <a name="general-requirements"></a>Conditions générales

Votre visuel Power BI doit être approuvé par le tableau de bord vendeur ou l’Espace partenaires. Il est recommandé que le visuel Power BI se trouve déjà dans [AppSource](https://appsource.microsoft.com/marketplace/apps?page=1&product=power-bi-visuals). Pour savoir comment publier un visuel Power BI sur AppSource, consultez [Publier des visuels Power BI sur l’Espace partenaires](office-store.md).

Avant de faire une demande de certification pour votre visuel Power BI, vérifiez qu’il est conforme aux [instructions sur les visuels Power BI](./guidelines-powerbi-visuals.md).

Lorsque vous envoyez votre visuel Power BI, vérifiez que le package compilé correspond exactement au package envoyé.

### <a name="code-repository-requirements"></a>Exigences relatives au référentiel de code

Bien qu’il ne soit pas nécessaire de partager publiquement votre code dans GitHub, l’équipe Power BI doit avoir accès au référentiel de code pour pouvoir l’examiner. La meilleure solution consiste à fournir le code source (JavaScript ou TypeScript) dans GitHub.

Le référentiel doit contenir les éléments suivants :
* Code pour un seul élément visuel Power BI. Il ne peut pas contenir le code de plusieurs visuels Power BI ou du code sans rapport.
* Une branche nommée **certification** (obligatoirement en minuscules). Le code source de cette branche doit correspondre au package soumis. Ce code ne peut être mis à jour que lors du processus d’envoi suivant, si vous envoyez à nouveau votre visuel Power BI.

Si votre visuel Power BI utilise des packages npm privés ou des sous-modules GIT, vous devez fournir l’accès aux référentiels supplémentaires contenant ce code.

Pour comprendre l’aspect d’un référentiel visuel Power BI, examinez le référentiel GitHub sur le [Graphique à barres exemple des éléments visuels Power BI](https://github.com/microsoft/PowerBI-visuals-sampleBarChart).

### <a name="file-requirements"></a>Exigences relatives aux fichiers

Utilisez la dernière version de l’API pour écrire le visuel Power BI.

Le référentiel doit comporter les fichiers suivants :
* **.gitignore** - Ajoutez `node_modules`, `.tmp` et  `dist` à ce fichier. Le code ne peut pas inclure les dossiers *node_modules*, *.tmp* or *dist*.
* **capabilities.json** : si vous soumettez une version plus récente de votre visuel Power BI dont les propriétés ont été modifiées dans ce fichier, vérifiez qu’elles ne bloquent pas les rapports pour les utilisateurs existants.
* **pbiviz.json** 
* **package.json**. Le package suivant doit être installé dans le visuel :
   * ["tslint"](https://www.npmjs.com/package/tslint) - Version 5.18.0 ou ultérieure
   * ["typescript"](https://www.npmjs.com/package/typescript) - Version 3.0.0 ou ultérieure
   * ["tslint-microsoftcontrib"](https://www.npmjs.com/package/tslint-microsoft-contrib) - Version 6.2.0 ou ultérieure
   * Le fichier doit contenir une commande pour exécuter linter -  `"lint": "tslint -c tslint.json -p tsconfig.json"`
* **package-lock.json**
* **tsconfig.json**

### <a name="command-requirements"></a>Exigences relatives aux commandes

Vérifiez que les commandes suivantes ne retournent aucune erreur.

* `npm install`
* `pbiviz package`
* `npm audit` : ne doit retourner aucun avertissement de niveau élevé ou modéré.
* [TSlint de Microsoft](https://www.npmjs.com/package/tslint-microsoft-contrib) avec [la configuration requise](https://github.com/microsoft/PowerBI-visuals-sampleBarChart/blob/master/tslint.json). Cette commande ne doit retourner aucune erreur Lint.

### <a name="compiling-requirements"></a>Exigences relatives à la compilation

Utilisez la dernière version de [powerbi-visuals-tools](https://www.npmjs.com/package/powerbi-visuals-tools) pour écrire le visuel Power BI.

Vous devez compiler votre visuel Power BI avec `pbiviz package`. Si vous utilisez vos propres scripts de build, fournissez une commande de build personnalisée `npm run package`.



### <a name="source-code-requirements"></a>Exigences relatives au code source

Vérifiez que vous suivez la liste des stratégies de [certification supplémentaires des visuels Power BI](https://docs.microsoft.com/legal/marketplace/certification-policies#1200-power-bi-visuals-additional-certification). Si votre envoi ne suit pas ces instructions, l’e-mail de rejet de l’Espace partenaires comportera les numéros de stratégie indiqués dans ce lien.

Suivez les exigences relatives au code ci-dessous pour vérifier que votre code est conforme aux stratégies de certification Power BI.  

**Obligatoire**
* N’utilisez que des composants OSS consultables par le public, comme des bibliothèques publiques JavaScript ou TypeScript.
* Le code doit prendre en charge [l’API d’événements de rendu](./visuals/event-service.md).
* Vérifiez que le DOM est correctement manipulé. Utilisez l’assainissement pour la saisie ou les données utilisateur avant de les ajouter au DOM.
* Utilisez [l’exemple de rapport](https://github.com/Microsoft/PowerBI-visuals/raw/gh-pages/assets/reports/large_data.pbix) comme jeu de données de test.

**Non autorisé**
* Accès à des services ou ressources externes. Par exemple, aucune requête HTTP/S ou WebSocket ne peut accéder à des services à l’extérieur de Power BI.
* Usage de `innerHTML` ou de `D3.html(user data or user input)`.
* Erreurs ou exceptions JavaScript dans la console du navigateur pour les données d’entrée.
* Code arbitraire ou dynamique, comme `eval()`, utilisation non sécurisée de `settimeout()`, de `requestAnimationFrame()`, de `setinterval(user input function)` et de la saisie ou des données utilisateur.
* Fichiers ou projets JavaScript minifiés.

## <a name="submitting-a-power-bi-visual-for-certification"></a>Soumission d'un visuel Power BI pour certification

Vous pouvez demander à l'équipe Power BI de certifier votre visuel Power BI via l’Espace partenaires.

>[!TIP]
>Le processus de certification Power BI peut prendre du temps. Si vous créez un nouveau visuel Power BI, nous vous recommandons de publier votre visuel Power BI via l’Espace partenaires avant de demander une certification Power BI. Cela évite ainsi tout retard dans la publication de votre visuel.

Pour demander la certification Power BI :

1. Connectez-vous à l’Espace partenaires.
2. Sur la **page Vue d’ensemble**, choisissez votre visuel Power BI, puis accédez à la page de configuration du **produit**.
3. Cochez la case **Demander la certification Power BI**.
4. Sur la page **Vérifier et publier**, dans la zone de texte **Remarques pour la certification**, fournissez un lien vers le code source et les informations d'identification requises pour y accéder.

### <a name="private-repository-submission-process"></a>Processus d’envoi du référentiel privé

Si vous utilisez un référentiel privé tel que GitHub pour envoyer votre élément visuel Power BI pour certification, suivez les instructions de cette section.
1. Créez un nouveau compte pour l’équipe de validation.
2. Configurez [l’authentification à deux facteurs](https://help.github.com/github/authenticating-to-github/securing-your-account-with-two-factor-authentication-2fa) pour votre compte.
3. [Générez un nouvel ensemble de codes de récupération](https://help.github.com/github/authenticating-to-github/configuring-two-factor-authentication-recovery-methods#generating-a-new-set-of-recovery-codes).
4. Lorsque vous envoyez votre élément visuel Power BI, fournissez les éléments suivants :
    * un lien web vers le référentiel
    * des informations d'identification pour la connexion (y compris le mot de passe)
    * des codes de récupération
    * des autorisations en lecture seule sur notre compte ([pbicvsupport](https://github.com/pbicvsupport))

## <a name="certified-power-bi-visual-badges"></a>Badges visuels Power BI certifiés

Une fois qu’un visuel Power BI est certifié, il obtient un badge désigné qui indique qu’il est certifié.

### <a name="certified-power-bi-visuals-in-appsource"></a>Visuels Power BI certifiés dans AppSource

* Lorsque vous recherchez en ligne des [visuels Power BI dans AppSource](https://appsource.microsoft.com/marketplace/apps?product=power-bi-visuals), un petit badge jaune sur la carte du visuel indique qu’il s’agit d’un visuel Power BI certifié.

    ![Visuel Power BI certifié - AppSource](media/power-bi-custom-visuals-certified/certified-visual-yellow-small.png)

* Après avoir cliqué sur la carte du visuel Power BI dans AppSource, un badge jaune intitulé *Certifié PBI* indique que ce visuel Power BI est certifié.

    ![Visuel Power BI certifié - Page d’application](media/power-bi-custom-visuals-certified/certified-visual-yellow-big.png)

### <a name="certified-power-bi-visuals-in-the-power-bi-interface"></a>Visuels Power BI certifiés dans l’interface Power BI

* Lorsque vous importez un visuel Power BI à partir de Power BI (Desktop ou service), un badge bleu indique que le visuel Power BI est certifié.

    ![Visuel Power BI certifié - Interface Power BI](media/power-bi-custom-visuals-certified/certified-visual-blue.png)

* Vous pouvez afficher uniquement les visuels Power BI certifiés, en sélectionnant l’option de filtre *Certifié Power BI*. 

## <a name="next-steps"></a>Étapes suivantes

* Si vous êtes un développeur web qui souhaite créer ses propres visuels Power BI et les ajouter à  [Microsoft AppSource](https://appsource.microsoft.com), commencez par le tutoriel  [Développement d'un visuel Power BI](visuals/custom-visual-develop-tutorial.md).

* Pour plus d’informations sur les visuels, consultez [Questions fréquentes sur les visuels certifiés](power-bi-custom-visuals-faq.md#certified-power-bi-visuals).

* [Développement d’un visuel personnalisé Power BI](../developer/custom-visual-develop-tutorial.md)

* [Sélection de visuels personnalisés de Microsoft sur YouTube](https://www.youtube.com/playlist?list=PL1N57mwBHtN1vIjfvuBIzZllrmKo-Vz6x)

* [Visualisations dans Power BI](../visuals/power-bi-report-visualizations.md)

* [Visualisations personnalisées dans Power BI](power-bi-custom-visuals.md)

* [Publier des visuels Power BI dans Microsoft AppSource](../developer/office-store.md)

* D’autres questions ? [Posez vos questions à la communauté Power BI](https://community.powerbi.com/)