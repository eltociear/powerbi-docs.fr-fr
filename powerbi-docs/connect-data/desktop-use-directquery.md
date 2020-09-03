---
title: Utilisation de DirectQuery dans Power BI Desktop
description: Utiliser DirectQuery (connexion active) dans Power BI Desktop
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: how-to
ms.date: 08/28/2020
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: b31ddb3e3881f9002affcae9106b9e14bf85a964
ms.sourcegitcommit: 70a892df1a0c196db58bf9165b3aa31b26bbe149
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/29/2020
ms.locfileid: "89092311"
---
# <a name="use-directquery-in-power-bi-desktop"></a>Utilisation de DirectQuery dans Power BI Desktop
Avec *Power BI Desktop*, quand vous vous connectez à une source de données, vous pouvez toujours importer une copie des données dans Power BI Desktop. Pour certaines sources de données, une autre approche est possible : vous connecter directement à la source de données à l’aide de DirectQuery.

## <a name="supported-data-sources"></a>Sources de données prises en charge
Pour obtenir la liste complète des sources données compatibles avec DirectQuery, consultez [Sources de données prises en charge par DirectQuery](power-bi-data-sources.md).

## <a name="how-to-connect-using-directquery"></a>Connexion à l’aide de DirectQuery
Quand vous utilisez **Obtenir des données** pour vous connecter à une source de données prise en charge par DirectQuery, la boîte de dialogue de connexion vous permet de sélectionner la manière dont vous souhaitez vous connecter. Par exemple, dans Power BI Desktop, sous le ruban **Accueil**, sélectionnez **Obtenir des données** > **SQL Server**. Dans la boîte de dialogue **SQL Server Database**, **Mode de connectivité des données** présente les options **Importer** et **DirectQuery** :

![Options Importer et DirectQuery, boîte de dialogue SQL Server Database, Power BI Desktop](media/desktop-use-directquery/directquery_sqlserverdb.png)

Voici les différences entre l’option **Importer** et l’option **DirectQuery** :

- **Importer** : Les tables et colonnes sélectionnées sont importées dans Power BI Desktop. Lorsque vous créez une visualisation ou interagissez avec elle, Power BI Desktop utilise les données importées. Pour voir les changements des données sous-jacentes depuis l’importation initiale ou la dernière actualisation, vous devez actualiser les données, ce qui implique de réimporter le jeu de données complet.

- **DirectQuery** : Aucune donnée n’est importée ou copiée dans Power BI Desktop. Pour des sources relationnelles, les tables et colonnes sélectionnées apparaissent dans la liste **Champs**. Pour des sources multidimensionnelles telles que SAP Business Warehouse, les dimensions et mesures du cube sélectionné s’affichent dans la liste **Champs**. Quand vous créez une visualisation ou interagissez avec elle, Power BI Desktop interroge la source de données sous-jacente afin de toujours afficher des données à jour.

De nombreuses transformations et modélisations des données sont disponibles avec DirectQuery, mais certaines limitations s’appliquent. Quand vous créez ou utilisez une visualisation, vous devez interroger la source sous-jacente. La durée de l’actualisation de la visualisation varie selon les performances de la source de données sous-jacente. Si les données à utiliser pour exécuter la requête ont récemment été demandées, Power BI Desktop utilise les données récentes pour afficher plus vite la visualisation. Si vous sélectionnez **Actualiser** dans le ruban **Accueil**, toutes les visualisations sont actualisées avec les données les plus récentes.

L’article [Power BI et DirectQuery](desktop-directquery-about.md) décrit DirectQuery en détail. Pour plus d’informations sur les avantages, les limitations et d’autres considérations importantes en rapport avec l’utilisation de DirectQuery, consultez les sections suivantes.

## <a name="benefits-of-using-directquery"></a>Avantages de l’utilisation de DirectQuery
Il y a plusieurs avantages à utiliser DirectQuery :

- DirectQuery vous permet de créer des visualisations sur des jeux de données très volumineux, qu’il serait autrement impossible d’importer au préalable dans leur totalité avec une pré-agrégation.
- La modification des données sous-jacentes peut nécessiter une actualisation des données. Pour certains rapports, l’affichage des données actualisées peut nécessiter le transfert de grandes quantités de données, empêchant la réimportation des données. En revanche, les rapports DirectQuery utilisent toujours les données les plus récentes.
- La limitation de la taille des jeux de données à 1 Go ne s’applique *pas* à DirectQuery.

## <a name="limitations-of-directquery"></a>Limitations de DirectQuery
Il existe actuellement quelques limitations à l’utilisation de DirectQuery :

- Si la requête de l’**Éditeur de requête** est trop complexe, une erreur se produit. Pour corriger cette erreur, supprimez l’étape problématique dans l’**Éditeur de requête** ou *importez* les données au lieu d’utiliser DirectQuery. Pour des sources multidimensionnelles comme SAP Business Warehouse, aucun **Éditeur de requête** n’est disponible.

- DirectQuery ne fournit pas de fonctionnalités Time Intelligence. Par exemple, le mode DirectQuery ne prend pas en charge le traitement spécial des colonnes de date (année, trimestre, mois ou jour, par exemple).

- Les tables calculées et les colonnes calculées qui font référence à une table DirectQuery à partir d’une source de données avec authentification unique (SSO) ne sont pas prises en charge dans le service Power BI.

- Des limitations sont imposées aux expressions DAX autorisées dans les mesures pour garantir des performances acceptables aux requêtes envoyées à la source de données sous-jacente.

- Il existe une limite d’un million de lignes pour les sources cloud. Les sources locales sont quant à elles limitées à une charge utile définie : environ 4 Mo par ligne (selon l’algorithme de compression propriétaire) ou 16 Mo de données pour l’intégralité du visuel. Certaines limites peuvent être levées si vous utilisez la capacité Premium. Cette limite ne s’applique pas aux agrégations ou calculs utilisés pour créer le jeu de données retourné à l’aide de DirectQuery. Elle s’applique uniquement aux lignes retournées. Les capacités Premium peuvent définir des limites de lignes maximales, comme le décrit [ce billet](https://powerbi.microsoft.com/blog/five-new-power-bi-premium-capacity-settings-is-available-on-the-portal-preloaded-with-default-values-admin-can-review-and-override-the-defaults-with-their-preference-to-better-fence-their-capacity/). 

    Par exemple, vous pouvez agréger 10 millions de lignes avec une requête exécutée sur la source de données. La requête retourne avec précision les résultats de cette agrégation à Power BI à l’aide de DirectQuery si les données Power BI retournées représentent moins de un million de lignes. Si DirectQuery retourne plus d’un million de lignes, Power BI retourne une erreur (sauf avec la capacité Premium, si le nombre de lignes est inférieur à la limite définie par l’administrateur).


## <a name="important-considerations-when-using-directquery"></a>Considérations importantes concernant l’utilisation de DirectQuery
Si vous utilisez DirectQuery, prenez en considération les trois points suivants :

- **Performances et charge** : toutes les requêtes DirectQuery étant envoyées à la base de données source, le délai d’actualisation des visuels dépend du temps que cette source back-end met pour retourner les résultats de chaque requête. Si vous utilisez DirectQuery pour les visuels, le temps de réponse recommandé (avec le retour des données demandées) est de cinq secondes ou moins, avec un temps de réponse maximal recommandé de 30 secondes. Si le temps de réponse est plus long, l’expérience d’un utilisateur utilisant le rapport devient d’une médiocrité pratiquement inacceptable. Une fois qu’un rapport est publié sur le service Power BI, toute requête prenant plus de quelques minutes expire, et l’utilisateur reçoit un message d’erreur.
  
    La charge sur la base de données source doit également être prise en considération, en fonction du nombre d’utilisateurs de Power BI qui utiliseront le rapport publié. L’utilisation de la **sécurité au niveau des lignes** (SNL) peut également avoir un impact significatif. En effet, si une vignette de tableau de bord sans sécurité au niveau des lignes est partagée par plusieurs utilisateurs, une seule requête est envoyée à la base de données. Toutefois, quand la sécurité au niveau des lignes est appliquée à une vignette de tableau de bord, l’actualisation de la vignette nécessite généralement une requête *par utilisateur*, ce qui augmente considérablement la charge sur la base de données source et peut potentiellement impacter les performances.
  
    Power BI crée des requêtes aussi efficaces que possible. Cependant, dans certaines situations, la requête générée peut ne pas être suffisamment efficace pour éviter une actualisation qui échoue. C’est le cas, par exemple, quand une requête générée extrait un trop grand nombre de lignes à partir de la source de données back-end. L’erreur suivante est retournée :

    ```output
    The resultset of a query to external data source has exceeded
    ```
  
    Cette situation peut se produire avec un simple graphique qui comprend une colonne de la cardinalité très élevée, avec l’option d’agrégation définie sur **ne pas résumer**. Le visuel doit avoir uniquement des colonnes avec une cardinalité inférieure à un million ou il doit appliquer les filtres appropriés.

- **Sécurité** : par défaut, tous les utilisateurs qui consomment un rapport publié se connectent à la source de données back-end en utilisant les informations d’identification entrées après la publication sur le service Power BI. C’est le même processus pour des données importées : tous les utilisateurs voient les mêmes données, quelles que soient les règles de sécurité définies dans la source back-end.

    Les clients qui souhaitent une sécurité par utilisateur implémentée avec des sources DirectQuery doivent utiliser la sécurité au niveau des lignes ou configurer l’authentification Kerberos contrainte par rapport à la source. Kerberos n’est pas disponible pour toutes les sources. [En savoir plus sur RLS](../admin/service-admin-rls.md). [Découvrez plus d’informations sur Kerberos dans DirectQuery](service-gateway-sso-kerberos.md).

- **Fonctionnalités prises en charge** : certaines fonctionnalités dans Power BI Desktop ne sont pas prises en charge en mode DirectQuery, ou leur prise en charge est limitée. De plus, certaines fonctionnalités du service Power BI (comme *Quick Insights*) ne sont pas disponibles pour les jeux de données qui utilisent DirectQuery. Pour déterminer si vous avez intérêt à utiliser DirectQuery, tenez compte de ces limitations de fonctionnalités.

> [!NOTE]
> Lors de l’utilisation de DirectQuery avec Azure SQL Database et une adresse IP privée, une passerelle locale est nécessaire. 

## <a name="publish-to-the-power-bi-service"></a>Publication sur le service Power BI
Les rapports créés à l’aide de DirectQuery peuvent être publiés sur le service Power BI.

Si la source de données utilisée n’a pas besoin de la **passerelle de données locale** (**Azure SQL Database**, **Azure SQL Data Warehouse** ou **Redshift**), vous devez fournir les informations d’identification avant que le service Power BI affiche le rapport publié. Suivez ces instructions pour fournir les informations d’identification :

1. Connectez-vous à [Power BI](https://www.powerbi.com/).
2. Dans le service Power BI, sélectionnez l’icône d’engrenage **Paramètres** , puis choisissez l’élément de menu **Paramètres**.

    ![Paramètres, service Power BI](media/desktop-use-directquery/directquery_pbiservicesettings.png)

3. Dans la page **Paramètres** du service Power BI, sélectionnez l’onglet **Jeux de données**, choisissez le jeu de données qui utilise DirectQuery, puis sélectionnez **Modifier les informations d’identification**.

4. Ajoutez les informations d’identification. Si vous ne fournissez pas ces informations, une erreur se produit lorsque vous ouvrez un rapport publié ou explorez un jeu de données créé avec une connexion DirectQuery.

Pour créer une connexion de données à des sources de données utilisant DirectQuery autres que **Azure SQL Database**, **Azure SQL Data Warehouse**, **Redshift** ou **Snowflake Data Warehouse**, installez une **passerelle de données locale** et inscrivez la source de données. Pour plus d’informations, consultez [Qu’est-ce qu’une passerelle de données locale ?](service-gateway-onprem.md)

## <a name="next-steps"></a>Étapes suivantes
Pour plus d’informations sur DirectQuery, consultez les ressources suivantes :

- [Utilisation de DirectQuery dans Power BI](desktop-directquery-about.md)
- [Sources de données prises en charge par DirectQuery](power-bi-data-sources.md)
- [DirectQuery et SAP Business Warehouse (BW)](desktop-directquery-sap-bw.md)
- [DirectQuery et SAP HANA](desktop-directquery-sap-hana.md)
- [Qu’est-ce qu’une passerelle de données locale ?](service-gateway-onprem.md)
