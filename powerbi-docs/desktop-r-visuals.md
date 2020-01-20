---
title: Créer des éléments visuels Power BI avec R
description: Avec Power BI Desktop, vous pouvez utiliser le moteur R pour visualiser vos données.
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 11/04/2019
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: 69295657702f995786379b18d3ad1ed3641bcbb8
ms.sourcegitcommit: b68a47b1854588a319a5a2d5d6a79bba2da3a4e6
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2020
ms.locfileid: "75729807"
---
# <a name="create-power-bi-visuals-using-r"></a>Créer des éléments visuels Power BI avec R
Power BI Desktop vous permet d’utiliser *R* pour visualiser vos données. [R](https://mran.revolutionanalytics.com/documents/what-is-r) est un langage et un environnement pour le calcul de statistiques et les graphiques.

## <a name="install-r"></a>Installer R
Par défaut, Power BI Desktop n’inclut pas, ne déploie pas ou n’installe pas le moteur R. Pour exécuter des scripts R dans Power BI Desktop, vous devez installer R séparément sur votre ordinateur local. Vous pouvez télécharger et installer R gratuitement à partir de nombreux emplacements, dont la [page de téléchargement Revolution Open](https://mran.revolutionanalytics.com/download/) et le [Référentiel CRAN](https://cran.r-project.org/bin/windows/base/). La version actuelle des scripts R dans Power BI Desktop prend en charge les caractères Unicode ainsi que les espaces (caractères vides) dans le chemin d’installation.

## <a name="enable-r-visuals-in-power-bi-desktop"></a>Activer les visuels R dans Power BI Desktop
Une fois que vous avez installé R, Power BI Desktop l’active automatiquement. Pour vérifier que Power BI Desktop a activé R à l’emplacement approprié, procédez comme suit : 

1. Dans le menu Power BI Desktop, sélectionnez **Fichier** > **Options et paramètres** > **Options**. 

2. Sur le côté gauche de la page **Options**, sous **Global**, sélectionnez **Script R**. 

3. Sous **Options de script R**, vérifiez que votre installation R locale est spécifiée dans **Répertoires de base R détectés** et qu’elle reflète correctement l’installation R locale que vous voulez que Power BI Desktop utilise. Dans l’image suivante, le chemin de l’installation locale de R est **C:\Program Files\R Open\R-3.5.3\\** .
   
   ![Page Options de script R](media/desktop-r-visuals/r-visuals-2.png)

Après avoir vérifié votre installation R, vous pouvez commencer à créer des visuels R.

## <a name="create-r-visuals-in-power-bi-desktop"></a>Créer des visuels R dans Power BI Desktop
1. Sélectionnez l’icône **Visuel R** dans le volet **Visualisation** pour ajouter un visuel R.
   
   ![Icône Visuel R dans le volet Visualisation](media/desktop-r-visuals/r-visuals-3.png)

2. Dans la boîte de dialogue **Activer les éléments visuels de script** qui s’affiche, sélectionnez **Activer**.

   ![Activer les visuels de script](media/desktop-r-visuals/r-visuals-10.png)

   Quand vous ajoutez un visuel R à un rapport, Power BI Desktop effectue les modifications suivantes :
   
   - Une image de visuel R apparaît sous forme d’espace réservé sur le canevas de rapport.
   
   - L’**Éditeur de script R** s’affiche dans la partie inférieure du volet central.
   
   ![Éditeur de script R](media/desktop-r-visuals/r-visuals-4.png)

3. Dans la section **Valeurs** du volet **Visualisation**, faites glisser les champs du volet **Champs** que vous voulez consommer dans votre script R, comme vous le feriez avec n’importe quel autre visuel Power BI Desktop. Vous pouvez aussi sélectionner les champs directement dans le volet **Champs**.
    
    Seuls les champs que vous avez ajoutés à la section **Valeurs** sont disponibles pour votre script R. Vous pouvez ajouter de nouveaux champs ou supprimer les champs inutiles de la section **Champs** pendant que vous travaillez sur votre script R dans l’**Éditeur de scripts R**. Power BI Desktop détecte automatiquement les champs que vous avez ajoutés ou supprimés.
   
   > [!NOTE]
   > Le type d’agrégation par défaut pour les éléments visuels R est *Ne pas résumer*.
   > 
   > 
   
4. Vous pouvez à présent utiliser les données sélectionnées pour créer un tracé : 

    - Quand vous sélectionnez des champs, l’**Éditeur de script R** génère du code de liaison au script R pour ces champs dans la section grise située en haut du volet de l’éditeur.
    - Si vous supprimez un champ, l’**Éditeur de script R** supprime automatiquement le code de prise en charge pour ce champ.
   
   Dans l’exemple présenté dans l’image suivante, trois champs sont sélectionnés : hp, gear et drat. Suite à ces sélections, l’Éditeur de script R a génère du code de liaison, qui peut être résumé comme suit :
   
   * Créez un dataframe appelé **jeu de données**, qui se compose des différents champs sélectionnés par l’utilisateur.
   * L’agrégation par défaut est *Ne pas synthétiser*.
   * À l’instar des visuels de table, les champs sont regroupés et les lignes en double n’apparaissent qu’une fois.
   
   ![Code de l’Éditeur de script R](media/desktop-r-visuals/r-visuals-5.png)
   
   > [!TIP]
   > Dans certains cas, il peut être dans votre intérêt de ne pas avoir recours au regroupement automatique ou bien d’afficher toutes les lignes, notamment les doublons. Dans ce cas, ajoutez un champ d’index à votre jeu de données. De cette façon, toutes les lignes sont considérées comme étant uniques, ce qui empêche le regroupement.
   > 
   > 
   
   Le dataframe généré est appelé **jeu de données** et vous accédez aux colonnes sélectionnées par leurs noms respectifs. Par exemple, vous pouvez accéder au champ « gear » en ajoutant *dataset$gear* à votre script R. Pour les champs avec des espaces ou des caractères spéciaux, utilisez des guillemets simples.

5. Une fois le dataframe généré automatiquement par les champs que vous avez sélectionnés, vous pouvez écrire un script R dont Power BI Desktop trace le résultat sur le périphérique R par défaut. Une fois le script terminé, sélectionnez **Exécuter le script** sur le côté droit de la barre de titre de l’**Éditeur de script R**.
   
    Quand vous sélectionnez **Exécuter le script**, Power BI Desktop identifie le tracé et le présente sur le canevas. Le processus étant exécuté sur l’installation locale de R, vérifiez que les packages R nécessaires sont installés.
   
   Power BI Desktop retrace le visuel lorsque l’un des événements suivants se produit :
   
   * Vous sélectionnez **Exécuter le script**  dans la barre de titre de l’**Éditeur de script R**.
   * Une modification des données se produit en raison de l’actualisation, du filtrage ou de la mise en surbrillance de données.

     L’image suivante montre un exemple de code de tracé de corrélation, qui représente les corrélations entre les attributs de différents types de voitures.

     ![Exemple de code de tracé de corrélation](media/desktop-r-visuals/r-visuals-6.png)

6. Pour obtenir une vue agrandie des visualisations, réduisez l’**Éditeur de script R**. Comme pour d’autres visuels dans Power BI Desktop, vous pouvez appliquer un filtre croisé au tracé de corrélation en sélectionnant une section spécifique (comme les voitures de sport) dans le visuel en anneau (le visuel circulaire à droite).

    ![Vue de visualisation agrandie](media/desktop-r-visuals/r-visuals-7.png)

7. Modifiez le script R pour personnaliser le visuel et mettre à profit toute la puissance de R en ajoutant des paramètres à la commande de traçage.

    La commande de traçage d’origine est :

    ```
    corrplot(M, method = "color",  tl.cex=0.6, tl.srt = 45, tl.col = "black")
    ```

    Modifiez le script R afin que la commande de traçage soit la suivante :

    ```
    corrplot(M, method = "circle", tl.cex=0.6, tl.srt = 45, tl.col = "black", type= "upper", order="hclust")
    ```

    Le visuel R trace donc à présent des cercles, en considérant seulement la moitié supérieure, et réorganise la matrice pour mettre en cluster les attributs corrélés.

    ![Tracé en cercles du visuel R](media/desktop-r-visuals/r-visuals-8.png)

    Quand vous exécutez un script R qui génère une erreur, un message d’erreur s’affiche sur le canevas à la place du tracé du visuel R. Pour obtenir plus d’informations sur l’erreur, sélectionnez **Voir les détails** dans l’erreur du visuel R.

    ![Erreur de visuel R](media/desktop-r-visuals/r-visuals-9.png)

## <a name="r-scripts-security"></a>Sécurité des scripts R 
Les visuels R sont créés à partir de scripts R, qui peuvent contenir du code présentant des risques pour la sécurité ou la confidentialité. Quand un utilisateur tente d’afficher un visuel R ou d’interagir avec ce dernier pour la première fois, un message d’avertissement de sécurité lui est présenté. Activez les éléments visuels R seulement si vous faites confiance à l’auteur et à la source ou après avoir examiné et compris le script R.


## <a name="known-limitations"></a>Limites connues
Les visuels R dans Power BI Desktop ont les limitations suivantes :

* Tailles des données : Les données utilisées par un visuel R pour le traçage sont limitées à 150 000 lignes. Si plus de 150 000 lignes sont sélectionnées, seules les 150 000 premières lignes sont utilisées et un message s’affiche sur l’image.

* Résolution : tous les visuels R sont affichés dans une résolution de 72 ppp.

* Temps de calcul : Si un calcul visuel R dépasse cinq minutes, il provoque une erreur de délai d’expiration.

* Relations : Comme avec d’autres visuels Power BI Desktop, si des champs de données provenant de différentes tables sans aucune relation définie entre elles sont sélectionnés, une erreur se produit.

* Actualisations : Les éléments visuels R sont actualisés lors de la mise à jour, du filtrage et de la mise en surbrillance des données. Toutefois, l’image elle-même n’est pas interactive et ne peut pas être la source du filtrage croisé.

* Mises en surbrillance : Les visuels R répondent si vous mettez en surbrillance d’autres visuels, mais vous ne pouvez pas sélectionner des éléments dans le visuel R pour appliquer un filtre croisé à d’autres éléments.

* Périphériques d’affichage : Seuls les tracés représentés sur le périphérique d’affichage R par défaut R s’affichent correctement sur le canevas. Évitez d’utiliser explicitement un autre périphérique d’affichage R.

* Installations RRO : Dans cette version, la version 32 bits de Power BI Desktop n’identifie pas automatiquement les installations RRO : vous devez donc définir manuellement le chemin du répertoire d’installation R dans **Options et paramètres** > **Options** > **Script R**.

## <a name="next-steps"></a>Étapes suivantes
Pour plus d’informations sur R dans Power BI, consultez les articles suivants :

* [Exécution de scripts R dans Power BI Desktop](desktop-r-scripts.md)
* [Utiliser un IDE R externe avec Power BI](desktop-r-ide.md)

