---
title: Utilisation de SAP BW Connector dans Power BI Desktop
description: Utilisation de SAP BW Connector dans Power BI Desktop
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/08/2019
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: f55245fc037f48622bb636e961f59c796f267646
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2019
ms.locfileid: "73879777"
---
# <a name="use-the-sap-bw-connector-in-power-bi-desktop"></a>Utilisation de SAP BW Connector dans Power BI Desktop
Avec Power BI Desktop, vous pouvez accéder aux données **SAP BusinessWarehouse (BW)** .

Pour plus d’informations sur comment les clients SAP peuvent tirer profit de la connexion de Power BI à leurs systèmes SAP Business Warehouse (BW) existants, consultez le [livre blanc Power BI et SAP BW](https://aka.ms/powerbiandsapbw). Pour plus d’informations sur l’utilisation de DirectQuery avec SAP BW, consultez l’article [DirectQuery et SAP Business Warehouse (BW)](desktop-directquery-sap-bw.md).

À compter de la version de juin 2018 de **Power BI Desktop** (généralement disponible avec la version d’octobre 2018), vous pouvez utiliser le connecteur SAP BW avec une implémentation qui présente des améliorations significatives au niveau des performances et des fonctionnalités. Cette version mise à jour du connecteur SAP BW a été développée par Microsoft et s’appelle **Implementation 2.0**. Vous pouvez sélectionner la version 1 (v1) du **connecteur SAP BW** ou le **connecteur SAP Implementation 2.0**. Les sections suivantes décrivent l’installation de chacune des versions. Vous pouvez choisir l’un ou l’autre de ces connecteurs au moment de vous connecter à SAP BW à partir de Power BI Desktop.

Nous vous suggérons d’utiliser le **connecteur SAP Implementation 2.0** autant que possible.

## <a name="installation-of-version-1-of-the-sap-bw-connector"></a>Installation de la version 1 du connecteur SAP BW
Nous recommandons d’utiliser le connecteur SAP Implementation 2.0 autant que possible (voir les instructions dans la section suivante). Cette section décrit l’installation de la version 1 du **connecteur SAP BW**, que vous pouvez installer en effectuant les étapes d’installation suivantes :

1. Installez la bibliothèque **SAP NetWeaver** sur votre ordinateur local. Vous pouvez obtenir la bibliothèque **SAP NetWeaver** auprès de votre administrateur SAP ou directement depuis le [Centre de téléchargement de logiciels SAP](https://support.sap.com/swdc). Étant donné que le **Centre de téléchargement de logiciels SAP** modifie sa structure fréquemment, des informations plus spécifiques sur la navigation dans ce site ne sont pas disponibles. La bibliothèque **SAP NetWeaver** est généralement incluse dans l’installation des outils du client SAP.
   
   Vous pouvez rechercher *Note SAP n° 1025361* pour obtenir l’emplacement de téléchargement de la version la plus récente. Vérifiez que l’architecture de la bibliothèque **SAP NetWeaver** (32 ou 64 bits) correspond à votre installation de **Power BI Desktop**, puis installez tous les fichiers inclus dans le **Kit de développement logiciel (SDK) SAP NetWeaver RFC** conformément à la note SAP.
2. La boîte de dialogue **Obtenir des données** comporte une entrée pour **SAP Business Warehouse Application Server** et **SAP Business Warehouse Message Server** dans la catégorie **Base de données**.
   
   ![Obtenir les options de données pour SAP](media/desktop-sap-bw-connector/sap_bw_2a.png)

## <a name="installation-of-implementation-20-sap-connector"></a>Installation du connecteur SAP Implementation 2.0

**Implementation 2.0** du connecteur SAP nécessite le connecteur SAP .NET 3.0. Vous pouvez [télécharger le connecteur SAP .NET 3.0](https://support.sap.com/en/product/connectors/msnet.html) depuis le site web de SAP via le lien suivant :

* [Connecteur SAP .NET 3.0](https://support.sap.com/en/product/connectors/msnet.html)

L’accès au téléchargement nécessite un superutilisateur valide. Les clients sont invités à contacter leur équipe SAP Basis pour obtenir le connecteur SAP .NET 3.0. 

Le connecteur est fourni en version 32 bits et 64 bits, et les utilisateurs *doivent* choisir la version qui correspond à leur installation de Power BI Desktop. À l’heure où nous écrivons cet article, le site web liste deux versions (pour .NET Framework 4.0) :

* Connecteur SAP pour Microsoft .NET 3.0.20.0 pour Windows 32 bits (x 86) en tant que fichier zip (6.896 Ko), 16 janvier 2018
* Connecteur SAP pour Microsoft .NET 3.0.20.0 pour Windows 64 bits (x 64) en tant que fichier zip (7.180 Ko), 16 janvier 2018

Lors de l’installation, dans la fenêtre **Étapes d’installation facultatives**, veillez à sélectionner l’option *Installer les assemblys dans le GAC* comme indiqué dans l’image suivante.

![Étapes d’installation SAP facultatives](media/desktop-sap-bw-connector/sap_bw_2b.png)

> [!NOTE]
> La première version de l’implémentation de SAP BW nécessitait les DLL Netweaver ; si vous utilisez le connecteur SAP Implementation 2.0, et pas la première version, les DLL Netweaver ne sont pas nécessaires.


## <a name="version-1-sap-bw-connector-features"></a>Fonctionnalités du connecteur SAP BW version 1
Le **connecteur SAP BW** version 1 dans Power BI Desktop vous permet d’importer des données à partir de vos cubes **SAP Business Warehouse Server** ou d’utiliser DirectQuery. 

Pour en savoir plus sur **SAP BW Connector** et sur son utilisation avec DirectQuery, consultez l’article [DirectQuery et SAP Business Warehouse (BW)](desktop-directquery-sap-bw.md).

Pour pouvoir vous connecter, vous devez spécifier un *Serveur*, un *Numéro de système* et un *ID client*.

![Paramètres de connexion du serveur SAP](media/desktop-sap-bw-connector/sap_bw_3a.png)

Vous pouvez également spécifier deux autres **options avancées** : le code de langue et une instruction MDX personnalisée à exécuter sur le serveur spécifié.

![informations de connexion supplémentaires](media/desktop-sap-bw-connector/sap_bw_4a.png)

Si aucune instruction MDX n’a été spécifiée, la fenêtre **Navigator** qui s’affiche présente la liste des cubes disponibles sur le serveur, avec l’option d’accès et de sélection des éléments dans les cubes disponibles, notamment les dimensions et les mesures. Power BI expose les requêtes et les cubes exposés par les [BAPI OLAP BW Open Analysis Interface](https://help.sap.com/saphelp_nw70/helpdata/en/d9/ed8c3c59021315e10000000a114084/content.htm).

Lorsque vous sélectionnez un ou plusieurs éléments sur le serveur, un aperçu de la table de sortie est créé en conséquence.

![Aperçu de la table SAP](media/desktop-sap-bw-connector/sap_bw_5.png)

La fenêtre **Navigator** fournit également un certain nombre d’**Options d’affichage** qui vous permettent d’effectuer les opérations suivantes :

* **Affichage *Uniquement les éléments sélectionnés* ou *Tous les éléments* (affichage par défaut) :** cette option est utile pour la vérification de l’ensemble final d’éléments sélectionnés. Une approche alternative à cet affichage consiste à sélectionner les *Noms de colonne* dans la zone *Aperçu*.
* **Activer les aperçus de données (comportement par défaut) :** vous pouvez également contrôler si les aperçus de données doivent être affichés dans cette boîte de dialogue. La désactivation des aperçus de données réduit le nombre des appels serveur car les données jusqu’alors requises pour les aperçus deviennent inutiles.
* **Noms techniques :** SAP BW prend en charge la notion de *noms techniques* pour les objets d’un cube. Les noms techniques permettent à un propriétaire de cube d’exposer des *noms conviviaux* pour des objets du cube et non pas uniquement des *noms physiques* pour ces objets.

![Fenêtre du navigateur](media/desktop-sap-bw-connector/sap_bw_6.png)

Après avoir sélectionné tous les objets nécessaires dans le **navigateur**, vous pouvez décider quoi faire, en sélectionnant un des boutons suivants dans la partie inférieure de la fenêtre **Navigator** :

* **Charger** déclenche le chargement de groupes de lignes pour la table de sortie vers le modèle de données Power BI Desktop, puis propose l’affichage **Rapport** pour vous permettre de visualiser les données ou d’apporter d’autres modifications à l’aide des affichages **Données** ou **Relations**.
* **Modifier** affiche **l’éditeur de requête**, dans lequel vous pouvez effectuer la transformation des données supplémentaires et le filtrage des étapes avant que l’ensemble de lignes soit inséré dans le modèle de données Power BI Desktop.

Outre le fait que vous pouvez importer des données à partir de cubes **SAP BW**, n’oubliez pas que vous pouvez également importer des données à partir d’une large gamme d’autres sources de données dans Power BI Desktop, puis les combiner dans un rapport unique. Cela présente toutes sortes de scénarios intéressant de génération de rapports et d’analyse sur les données **SAP BW**.

## <a name="using-implementation-20-sap-bw-connector"></a>Utilisation du connecteur SAP BW Implementation 2.0

Vous devez créer une nouvelle connexion pour utiliser Implementation 2.0 du connecteur SAP BW. Pour créer une nouvelle connexion, effectuez les étapes suivantes.

1. À partir de la fenêtre **Obtenir les données**, sélectionnez **Serveur d’applications SAP Business Warehouse** ou **Serveur de messages SAP Business Warehouse**.

2. Vous est présentée la boîte de dialogue de nouvelle connexion, qui permet de sélectionner l’implémentation. La sélection de **Implementation 2.0**, comme montré dans l’image suivante, permet de bénéficier des options Mode d’exécution, Taille du lot et Activer les structures caractéristiques.

    ![Boîte de dialogue Connexion SAP](media/desktop-sap-bw-connector/sap_bw_7.png)

3. Sélectionnez **OK** et l’expérience de **Navigator** devient tout de suite identique à celle décrite dans la section précédente pour le connecteur SAP BW version 1. 

### <a name="new-options-for-implementation-20"></a>Nouvelles options pour Implementation 2.0 

Implementation 2.0 prend en charge les options suivantes :

1. **ExecutionMode** : Spécifie l’interface MDX utilisée pour exécuter des requêtes sur le serveur. Les options valides sont les suivantes :

        a. SapBusinessWarehouseExecutionMode.BasXml
        b. SapBusinessWarehouseExecutionMode.BasXmlGzip
        c. SapBusinessWarehouseExecutionMode.DataStream

    La valeur par défaut de cette option est SapBusinessWarehouseExecutionMode.BasXmlGzip.

    L’utilisation de *SapBusinessWarehouseExecutionMode.BasXmlGzip* peut améliorer les performances quand la latence est élevée pour les jeux de données volumineux.

2. **BatchSize** : Spécifie le nombre maximal de lignes qui seront récupérées à la fois lors de l’exécution d’une instruction MDX. Un petit nombre de lignes se traduit par plus d’appels au serveur lors de la récupération d’un jeu de données volumineux. Un grand nombre de lignes peut améliorer les performances, mais peut entraîner des problèmes de mémoire sur le serveur SAP BW. La valeur par défaut est 50 000 lignes.

3. **EnableStructures** : Valeur logique indiquant si les structures caractéristiques sont reconnues. La valeur par défaut de cette option est false. Affecte la liste des objets pouvant être sélectionnés. Non pris en charge en mode de requête natif.

L’option **ScaleMeasures** a été dépréciée dans cette implémentation. Le comportement est maintenant le même que la définition *ScaleMeasures = false*, qui affiche toujours des valeurs non ajustées.

### <a name="additional-improvements-for-implementation-20"></a>Améliorations supplémentaires pour Implementation 2.0 

La liste à puces ci-dessous décrit quelques-unes des améliorations supplémentaires qui accompagnent la nouvelle implémentation :

* Amélioration des performances
* Possibilité de récupérer plusieurs millions de lignes de données et d’ajuster le paramètre de la taille de lot.
* Possibilité de basculer entre les modes d’exécution.
* Prise en charge pour le mode compressé. Particulièrement utile pour les connexions à latence élevée ou les jeux de données volumineux.
* Amélioration de la détection des variables de date
* [Expérimental] Exposer la date (ABAP type DAT) et les dimensions de temps (ABAP type TIM) respectivement comme dates et heures, au lieu de valeurs texte.
* Meilleure gestion des exceptions. Les erreurs qui se produisent dans les appels BAPI sont maintenant signalées.
* Pliage de colonnes dans les modes BasXml et BasXmlGzip. Par exemple, si la requête MDX générée récupère 40 colonnes, alors que la sélection actuelle n’en a besoin que de 10, cette demande passe au serveur pour récupérer un jeu de données plus petit.


### <a name="changing-existing-reports-to-use-implementation-20"></a>Changement des rapports existants pour utiliser Implementation 2.0 

Le changement des rapports existants pour utiliser **Implementation 2.0** est possible uniquement en mode Importation et nécessite les étapes manuelles suivantes.

1. Ouvrez un rapport existant, sélectionnez **Modifier les requêtes** dans le ruban, puis sélectionnez la requête SAP Business Warehouse que vous souhaitez mettre à jour.

2. Cliquez avec le bouton droit sur la requête et sélectionnez **Éditeur avancé**.

3. Dans l’**Éditeur avancé**, changez l’appel de SapBusinessWarehouse.Cubes comme suit : 

    a. Déterminez si la requête contient déjà un enregistrement d’option, tel que ce qui est montré dans l’exemple suivant :

    ![extrait de la requête](media/desktop-sap-bw-connector/sap_bw_9.png)

    b. Dans ce cas, ajoutez l’option Implementation 2.0 et supprimez l’option ScaleMeasures, le cas échéant, comme indiqué :

    ![extrait de la requête](media/desktop-sap-bw-connector/sap_bw_10.png)

    c. Si la requête n’inclut pas déjà un enregistrement d’options, ajoutez-en un. Par exemple, si elle a :

    ![extrait de la requête](media/desktop-sap-bw-connector/sap_bw_11.png)

    d. Remplacez simplement par :

    ![extrait de la requête](media/desktop-sap-bw-connector/sap_bw_12.png)

4. Nous avons fait tout notre possible pour rendre le connecteur SAP BW Implementation 2.0 compatible avec la version 1 du connecteur SAP BW. Toutefois, il peut y avoir des différences en raison des différents modes d’exécution MDX SAP BW. Pour résoudre les incohérences, essayez de basculer entre les modes d’exécution.

## <a name="troubleshooting"></a>Résolution des problèmes
Cette section décrit des scénarios de dépannage (et des solutions) lors de l’utilisation du connecteur **SAP BW**.

1. Les données numériques de **SAP BW** retournent des décimales au lieu de virgules. Par exemple, 1,000,000 est retourné en tant que 1.000.000.
   
   **SAP BW** retourne des données décimales avec un caractère *,* (virgule) ou *.* (point) comme séparateur décimal. Pour spécifier l’option que **SAP BW** doit utiliser comme séparateur décimal, le pilote utilisé par **Power BI Desktop** effectue un appel à *BAPI_USER_GET_DETAIL*. Cet appel retourne une structure appelée **DEFAULTS**, qui a un champ appelé *DCPFM* qui stocke *Decimal Format Notation*. Elle prend l’une des trois valeurs suivantes :
   
       ‘ ‘ (space) = Decimal point is comma: N.NNN,NN
       'X' = Decimal point is period: N,NNN.NN
       'Y' = Decimal point is N NNN NNN,NN
   
   Les clients qui ont signalé ce problème ont constaté que l’appel à *BAPI_USER_GET_DETAIL* échoue pour un utilisateur particulier (qui affiche des données incorrectes), avec un message d’erreur semblable au suivant :
   
       You are not authorized to display users in group TI:
           <item>
               <TYPE>E</TYPE>
               <ID>01</ID>
               <NUMBER>512</NUMBER>
               <MESSAGE>You are not authorized to display users in group TI</MESSAGE>
               <LOG_NO/>
               <LOG_MSG_NO>000000</LOG_MSG_NO>
               <MESSAGE_V1>TI</MESSAGE_V1>
               <MESSAGE_V2/>
               <MESSAGE_V3/>
               <MESSAGE_V4/>
               <PARAMETER/>
               <ROW>0</ROW>
               <FIELD>BNAME</FIELD>
               <SYSTEM>CLNTPW1400</SYSTEM>
           </item>
   
   Pour résoudre cette erreur, les utilisateurs doivent demander à leur administrateur SAP d’accorder à l’utilisateur SAPBW utilisé dans Power BI le droit d’exécuter *BAPI_USER_GET_DETAIL*. Il est également important de vérifier que l’utilisateur a la valeur *DCPFM* requise, comme décrit précédemment dans cette solution de dépannage.
   
2. **Connectivité pour les requêtes SAP BEx**
   
   Vous pouvez effectuer des requêtes **BEx** dans Power BI Desktop en activant une propriété spécifique, comme illustré dans l’image suivante :
   
   ![](media/desktop-sap-bw-connector/sap_bw_8.png)
   
3. La fenêtre **Navigator** n’affiche pas d’aperçu des données, mais un message d’erreur *référence d’objet non définie sur une instance d’un objet* à la place.
   
   Les utilisateurs SAP doivent accéder à des modules de fonction BAPI spécifiques pour obtenir les métadonnées et récupérer des données à partir d’InfoProviders de SAP BW. Il s’agit des tables suivantes :
   * BAPI_MDPROVIDER_GET_CATALOGS
   * BAPI_MDPROVIDER_GET_CUBES
   * BAPI_MDPROVIDER_GET_DIMENSIONS
   * BAPI_MDPROVIDER_GET_HIERARCHYS
   * BAPI_MDPROVIDER_GET_LEVELS
   * BAPI_MDPROVIDER_GET_MEASURES
   * BAPI_MDPROVIDER_GET_MEMBERS
   * BAPI_MDPROVIDER_GET_VARIABLES
   * BAPI_IOBJ_GETDETAIL

   Pour résoudre ce problème, vérifiez que l’utilisateur a accès aux différents modules *MDPROVIDER*, ainsi qu’à *BAPI_IOBJ_GETDETAIL*. Pour résoudre ce problème ou des problèmes similaires, sélectionnez *Activer le traçage* dans la fenêtre *Diagnostics* dans les *Options* de Power BI Desktop. Tentez de récupérer des données à partir de SAP BW pendant que le traçage est actif et examinez le fichier de traçage pour plus de détails.

## <a name="sap-bw-connection-support"></a>Prise en charge des connexions SAP BW

Le tableau suivant détaille la prise en charge actuelle de SAP BW.



|Produit  |Mode  |Authentification  |Connecteur  |Bibliothèque SNC  |Pris en charge  |
|---------|---------|---------|---------|---------|---------|
|Power BI Desktop     |N'importe quel(le)         | Utilisateur / mot de passe  | Serveur d’applications | N/A  | Oui  |
|Power BI Desktop     |N'importe quel(le)         | Windows          | Serveur d’applications | sapcrypto + gsskrb5/gx64krb5  | Oui  |
|Power BI Desktop     |N'importe quel(le)         | Windows par le biais de l’emprunt d’identité | Serveur d’applications | sapcrypto + gsskrb5/gx64krb5  | Oui  |
|Power BI Desktop     |N'importe quel(le)         | Utilisateur / mot de passe        | Serveur de messages | N/A  | Oui  |
|Power BI Desktop     |N'importe quel(le)         | Windows        | Serveur de messages | sapcrypto + gsskrb5/gx64krb5  | Oui  |
|Power BI Desktop     |N'importe quel(le)         | Windows par le biais de l’emprunt d’identité | Serveur de messages | sapcrypto + gsskrb5/gx64krb5  | Oui  |
|Power BI Gateway     |Importer      | Identique à Power BI Desktop |         |   |   |
|Power BI Gateway     |DirectQuery | Utilisateur / mot de passe        | Serveur d’applications | N/A  | Oui  |
|Power BI Gateway     |DirectQuery | Windows par le biais de l’emprunt d’identité (utilisateur fixe, pas d’authentification SSO) | Serveur d’applications | sapcrypto + gsskrb5/gx64krb5  | Oui  |
|Power BI Gateway     |DirectQuery | Utiliser SSO via Kerberos pour l’option des requêtes DirectQuery | Serveur d’applications | sapcrypto + gsskrb5/gx64krb5   | Oui  |
|Power BI Gateway     |DirectQuery | Utilisateur / mot de passe        | Serveur de messages | N/A  | Oui  |
|Power BI Gateway     |DirectQuery | Windows par le biais de l’emprunt d’identité (utilisateur fixe, pas d’authentification SSO) | Serveur de messages | sapcrypto + gsskrb5/gx64krb5  | Oui  |
|Power BI Gateway     |DirectQuery | Utiliser SSO via Kerberos pour l’option des requêtes DirectQuery | Serveur de messages | gsskrb5/gx64krb5  | Non  |
|Power BI Gateway     |DirectQuery | Utiliser SSO via Kerberos pour l’option des requêtes DirectQuery | Serveur de messages | sapcrypto  | Oui  |



## <a name="next-steps"></a>Étapes suivantes
Pour plus d’informations sur SAP et DirectQuery, consultez les ressources suivantes :

* [DirectQuery et SAP HANA](desktop-directquery-sap-hana.md)
* [DirectQuery et SAP Business Warehouse (BW)](desktop-directquery-sap-bw.md)
* [DirectQuery dans Power BI](desktop-directquery-about.md)
* [Sources de données prises en charge par DirectQuery](desktop-directquery-data-sources.md)
* [Livre blanc Power BI et SAP BW](https://aka.ms/powerbiandsapbw)
