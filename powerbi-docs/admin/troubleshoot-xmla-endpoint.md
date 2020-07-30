---
title: Résolution des problèmes de connectivité de point de terminaison XMLA dans Power BI Premium (préversion)
description: Explique comment résoudre les problèmes de connectivité via le point de terminaison XMLA dans Power BI Premium.
author: minewiskan
ms.author: owend
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: troubleshooting
ms.date: 07/28/2020
ms.custom: seodec18, css_fy20Q4
LocalizationGroup: Premium
ms.openlocfilehash: 8a815f69d4f74ec925c3ac0cc8a84c2a13d80346
ms.sourcegitcommit: a254f6e2453656f6783690669be8e881934e15ac
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87363959"
---
# <a name="troubleshoot-xmla-endpoint-connectivity"></a>Résoudre les problèmes de connectivité des points de terminaison XMLA

Dans Power BI Premium, les points de terminaison XMLA s’appuient sur le protocole de communication Analysis Services natif pour accéder aux jeux de données Power BI. De ce fait, la résolution des problèmes de point de terminaison XMLA est pratiquement identique à celle d’une connexion Analysis Services classique. Il existe toutefois certaines différences concernant les dépendances propres à Power BI.

## <a name="before-you-begin"></a>Avant de commencer

Avant de résoudre les problèmes d’un scénario de point de terminaison XMLA, veillez à passer en revue les principes de base traités dans [Connectivité des jeux de données avec le point de terminaison XMLA](service-premium-connect-tools.md). Les cas d’utilisation de points de terminaison XMLA les plus courants sont couverts ici. D’autres guides de dépannage Power BI, notamment [Résolution des problèmes liés aux passerelles – Power BI](../connect-data/service-gateway-onprem-tshoot.md) et [Résolution des problèmes de la fonctionnalité Analyser dans Excel](../collaborate-share/desktop-troubleshooting-analyze-in-excel.md), peuvent également être utiles.

## <a name="enabling-the-xmla-endpoint"></a>Activation du point de terminaison XMLA

Le point de terminaison XMLA peut être activé à la fois sur la capacité Power BI Premium et sur la capacité Power BI Embedded. Sur les capacités plus petites, comme une capacité A1 comportant seulement 2,5 Go de mémoire, il se peut que vous rencontriez une erreur dans Paramètres de capacité lorsque vous tentez de définir le point de terminaison XMLA sur **Lecture/écriture**, puis que vous sélectionnez **Appliquer**. L’erreur indique : « Un problème s’est produit concernant les paramètres de votre charge de travail. Réessayez dans quelques instants. »

Vous pouvez essayer les opérations suivantes :

- Limitez la consommation de mémoire d’autres services sur la capacité, par exemple les dataflows, à 40 % ou moins, ou désactivez complètement les services inutiles.  
- Mettez à niveau la capacité en passant à une référence SKU supérieure. Par exemple, le passage d’une capacité A1 à une capacité A3 permet de résoudre ce problème de configuration sans avoir à désactiver de dataflows.

N’oubliez pas que vous devez aussi activer le paramètre [Exporter des données](service-premium-connect-tools.md#security) au niveau du locataire sur le portail d’administration Power BI. Ce paramètre est également requis pour la fonctionnalité Analyser dans Excel.

## <a name="establishing-a-client-connection"></a>Établissement d’une connexion cliente

Après avoir activé le point de terminaison XMLA, il est judicieux de tester la connectivité à un espace de travail sur la capacité. Pour plus d’informations, consultez [Connexion à un espace de travail Premium](service-premium-connect-tools.md#connecting-to-a-premium-workspace). Veillez également à lire la section [Exigences pour la connexion](service-premium-connect-tools.md#connection-requirements) pour obtenir des conseils et des informations utiles sur les limitations actuelles de la connectivité XMLA.

### <a name="connecting-with-a-service-principal"></a>Connexion avec un principal de service

Si vous avez activé les paramètres du locataire permettant aux principaux de service d’utiliser les API Power BI (cf. [Activation des principaux de service](service-premium-service-principal.md#enable-service-principals)), vous pouvez vous connecter à un point de terminaison XMLA à l’aide d’un principal de service. N’oubliez pas que le principal de service a besoin du même niveau d’autorisations d’accès au niveau de l’espace de travail ou du jeu de données que les utilisateurs standard.

Pour utiliser un principal de service, veillez à spécifier les informations d’identité de l’application dans la chaîne de connexion ainsi :

- `User ID=<app:appid@tenantid>`
- `Password=<application secret>`

Par exemple :

`Data Source=powerbi://api.powerbi.com/v1.0/myorg/Contoso;Initial Catalog=PowerBI_Dataset;User ID=app:91ab91bb-6b32-4f6d-8bbc-97a0f9f8906b@19373176-316e-4dc7-834c-328902628ad4;Password=6drX...;`

Si vous recevez l’erreur suivante :

« Connexion au jeu de données impossible en raison d’informations de compte incomplètes. Pour les principaux de service, veillez à spécifier l’ID de locataire avec l’ID d’application au format app:\<appId>@\<tenantId>, puis réessayez. »

Veillez à spécifier l’ID de locataire avec l’ID d’application au bon format.

Il est également possible d’indiquer l’ID d’application sans l’ID de locataire. Toutefois, vous devez dans ce cas remplacer l’alias `myorg` dans l’URL de la source de données par l’ID de locataire réel. Power BI peut alors localiser le principal de service dans le locataire approprié. Il est cependant recommandé d’utiliser l’alias `myorg` et de spécifier l’ID de locataire avec l’ID d’application dans le paramètre ID d’utilisateur.

### <a name="connecting-with-azure-active-directory-b2b"></a>Connexion avec Azure Active Directory B2B

Avec la prise en charge d’Azure Active Directory (Azure AD) B2B (interentreprises) dans Power BI, vous pouvez fournir aux utilisateurs invités externes un accès aux jeux de données via le point de terminaison XMLA. Vérifiez que le paramètre [Partage de contenu avec des utilisateurs externes](service-admin-portal.md#export-and-sharing-settings) est activé sur le portail d’administration Power BI. Pour plus d’informations, consultez [Distribution de contenu Power BI à des utilisateurs invités externes avec Azure AD B2B](service-admin-azure-ad-b2b.md).

## <a name="deploying-a-dataset"></a>Déploiement d’un jeu de données

Le déploiement d’un projet de modèle tabulaire dans Visual Studio (SSDT) sur un espace de travail Power BI Premium est très similaire au déploiement sur Azure Analysis Services, avec cependant quelques considérations supplémentaires à prendre en compte. Veillez à consulter la section [Déploiement de projets de modèle à partir de Visual Studio (SSDT)](service-premium-connect-tools.md#deploy-model-projects-from-visual-studio-ssdt) dans l’article Connectivité des jeux de données avec le point de terminaison XMLA.

### <a name="deploying-a-new-model"></a>Déploiement d’un modèle

Dans la configuration par défaut, Visual Studio tente de traiter le modèle dans le cadre de l’opération de déploiement consistant à charger les données dans le jeu de données à partir des sources de données. Comme le décrit [Déploiement de projets de modèle à partir de Visual Studio (SSDT)](service-premium-connect-tools.md#deploy-model-projects-from-visual-studio-ssdt), cette opération est susceptible d’échouer parce que les informations d’identification de la source de données ne peuvent pas être spécifiées dans le cadre de l’opération de déploiement. Si au contraire les informations d’identification de votre source de données ne sont définies pour aucun de vos jeux de données existants, vous devez indiquer les informations d’identification de la source dans les paramètres du jeu de données à l’aide de l’interface utilisateur Power BI (**Jeux de données** > **Paramètres** > **Informations d’identification de la source de données** > **Modifier les informations d’identification**). Une fois les informations d’identification de la source de données définies, Power BI peut les appliquer automatiquement à cette source de données pour un nouveau jeu de données, lorsque le déploiement des métadonnées a réussi et que le jeu de données a été créé.

Si Power BI ne parvient pas à lier votre nouveau jeu de données aux informations d’identification de la source de données, vous recevrez une erreur indiquant « Impossible de traiter la base de données. Motif : Échec de l’enregistrement des modifications sur le serveur. » avec le code d’erreur « DMTS_DatasourceHasNoCredentialError », comme indiqué ci-dessous :

:::image type="content" source="media/troubleshoot-xmla-endpoint/deploy-refresh-error.png" alt-text="Erreur de déploiement de modèle":::

Pour éviter l’échec du traitement, définissez **Options de déploiement** > **Options de traitement** sur **Ne pas traiter**, comme l’illustre l’image suivante. Visual Studio déploie alors uniquement les métadonnées. Vous pouvez ensuite configurer les informations d’identification de la source de données, puis cliquer sur **Actualiser maintenant** pour le jeu de données dans l’interface utilisateur Power BI. Pour plus d’informations sur la résolution des problèmes de traitement, consultez la section [Actualisation d’un jeu de données](#refreshing-a-dataset) plus loin dans cet article.

:::image type="content" source="media/troubleshoot-xmla-endpoint/do-not-process.png" alt-text="Option Ne pas traiter":::

### <a name="new-project-from-an-existing-dataset"></a>Nouveau projet à partir d’un jeu de données existant

Dans Visual Studio, il n’est pas possible de créer un projet tabulaire en important les métadonnées d’un jeu de données existant sur un espace de travail Power BI Premium. Toutefois, vous pouvez vous connecter au jeu de données à l’aide de SQL Server Management Studio, exporter les métadonnées par script et les réutiliser dans d’autres projets tabulaires.

## <a name="migrating-a-dataset-to-power-bi"></a>Migration d’un jeu de données vers Power BI

Il est recommandé de spécifier le niveau de compatibilité 1500 (au minimum) pour les modèles tabulaires. Ce niveau de compatibilité permet de gérer la plupart des fonctionnalités et des types de sources de données. Les niveaux de compatibilité ultérieurs présentent une compatibilité descendante avec les niveaux antérieurs.

### <a name="supported-data-providers"></a>Fournisseurs de données pris en charge

Au niveau de compatibilité 1500, Power BI prend en charge les types de sources de données suivants :

- Sources de données de fournisseur (héritées avec une chaîne de connexion dans les métadonnées du modèle).
- Sources de données structurées (introduites avec le niveau de compatibilité 1400).
- Déclarations Inline M de sources de données (à mesure que Power BI Desktop les déclare).

Il est recommandé d’utiliser des sources de données structurées, que Visual Studio crée par défaut dans le cadre du workflow Importer des données. Toutefois, si vous envisagez de migrer vers Power BI un modèle existant qui utilise une source de données de fournisseur, vérifiez que celle-ci s’appuie sur un fournisseur de données pris en charge, plus précisément, le pilote Microsoft OLE DB Driver pour SQL Server et les pilotes ODBC tiers. Dans le cas du pilote OLE DB Driver pour SQL Server, vous devez basculer la définition de la source de données vers le fournisseur de données .NET Framework pour SQL Server. En ce qui concerne les pilotes ODBC tiers qui risquent de ne pas être disponibles dans le service Power BI, vous devez basculer vers une définition de source de données structurées.

Il est également recommandé de remplacer le pilote Microsoft OLE DB Driver pour SQL Server (SQLNCLI11) par le fournisseur de données .NET Framework pour SQL Server dans les définitions de source de données SQL Server.

Le tableau suivant fournit un exemple de chaîne de connexion du fournisseur de données .NET Framework pour SQL Server remplaçant une chaîne de connexion correspondante pour le pilote OLE DB Driver pour SQL Server.

|OLE DB Driver pour SQL Server  |Fournisseur de données .NET Framework pour SQL Server   |
|---------|---------|
|`Provider=SQLNCLI11;Data Source=sqldb.database.windows.net;Initial Catalog=AdventureWorksDW;Trusted_Connection=yes;`    |   `Data Source=sqldb.database.windows.net;Initial Catalog=AdventureWorksDW2016;Integrated Security=SSPI;Encrypt=true;TrustServerCertificate=false`       |

### <a name="cross-referencing-partition-sources"></a>Référence croisée des sources de partition

Tout comme il existe plusieurs types de sources de données, il existe également plusieurs types de sources de partition qu’un modèle tabulaire peut inclure pour importer des données dans une table. Plus précisément, une partition peut utiliser une source de partition de requête ou une source de partition M, qui en retour peuvent faire référence à des sources de données de fournisseur ou à des sources de données structurées. Si dans Azure Analysis Services les modèles tabulaires prennent en charge les références croisées entre ces différents types de sources de données et de partitions, Power BI applique une relation plus stricte. Les sources de partition de requête doivent faire référence à des sources de données de fournisseur et les sources de partition M à des sources de données structurées. Les autres combinaisons ne sont pas acceptées dans Power BI. Si vous souhaitez migrer un jeu de données à référence croisée, le tableau suivant décrit les configurations prises en charge :  

|Paramètres   |Source de partition   |Commentaires   |Pris en charge dans Power BI Premium avec un point de terminaison XMLA   |
|---------|---------|---------|---------|
|Source de données de fournisseur      |   Source de partition de requête      |   Le moteur AS utilise la pile de connectivité basée sur cartouche pour accéder à la source de données.       |     Oui     |
|Source de données de fournisseur      |   Source de partition M       |   Le moteur AS convertit la source de données de fournisseur en source de données structurées générique, puis utilise le Moteur Mashup pour importer les données.       |    Non     |
|Source de données structurée      |     Source de partition de requête     |    Le moteur AS encapsule la requête native sur la source de la partition dans une expression M, puis utilise le Moteur Mashup pour importer les données.      |    Non     |
|Source de données structurée      |    Source de partition M      |     Le moteur AS utilise le Moteur Mashup pour importer les données.     |   Oui      |

## <a name="refreshing-a-dataset"></a>Actualisation d’un jeu de données

Les points de terminaison XMLA permettent d’effectuer des opérations d’actualisation sur les modèles tabulaires ainsi que sur les jeux de données créés dans Power BI Desktop. Pour prendre en charge ces derniers, veillez à spécifier le paramètre de format Stockage étendu. Ce paramètre est obligatoire pour effectuer un traitement ou d’autres opérations de lecture/écriture à l’aide du point de terminaison XMLA. Vous le trouverez dans Power BI Desktop sous Fonctionnalités en préversion. Après l’avoir défini, publiez à nouveau votre solution PBIX dans votre espace de travail Power BI Premium.  

Power BI retourne l’erreur suivante si vous effectuez une actualisation via le point de terminaison XMLA sur un modèle sans métadonnées étendues : « L’opération n’est prise en charge que sur un modèle dont la propriété "DefaultPowerBIDataSourceVersion" a la valeur "PowerBI_V3" dans Power BI Premium ».

### <a name="data-sources-and-impersonation"></a>Sources de données et emprunt d’identité

Les paramètres d’emprunt d’identité que vous pouvez définir pour les sources de données de fournisseur ne sont pas pertinents pour Power BI. Power BI utilise un autre mécanisme, qui s’appuie sur les paramètres du jeu de données pour gérer les informations d’identification de la source de données. Veillez donc à sélectionner **Compte de service** si vous créez une source de données de fournisseur.

:::image type="content" source="media/troubleshoot-xmla-endpoint/impersonate-services-account.png" alt-text="Emprunt d’identité d’un compte de service":::

### <a name="fine-grained-processing"></a>Traitement affiné

Lorsqu’une actualisation planifiée ou à la demande est déclenchée dans Power BI, Power BI actualise généralement l’ensemble du jeu de données. Il existe de nombreux cas où il est plus efficace d’effectuer des actualisations plus sélectives. Vous pouvez effectuer des tâches de traitement affinées dans SQL Server Management Studio (SSMS) comme indiqué ci-dessous, ou à l’aide d’outils ou de scripts tiers.

:::image type="content" source="media/troubleshoot-xmla-endpoint/process-tables.png" alt-text="Traitement des tables dans SSMS":::

### <a name="overrides-in-refresh-tmsl-command"></a>Remplacements dans la commande Refresh TMSL

Les remplacements dans la [commande Refresh (TMSL)](https://docs.microsoft.com/analysis-services/tmsl/refresh-command-tmsl) permettent aux utilisateurs de choisir une définition de requête de partition ou une définition de source de données différente pour l’opération d’actualisation. Les remplacements **ne sont pas pris en charge** dans Power BI Premium. Une erreur, « La liaison hors ligne n’est pas autorisée dans Power BI Premium. Pour plus d’informations, consultez « Prise en charge de la lecture/écriture XMLA » dans la documentation du produit. » est renvoyé.

## <a name="see-also"></a>Voir aussi

[Connectivité des jeux de données avec le point de terminaison XMLA](service-premium-connect-tools.md)   
[Automatisation des tâches d’espace de travail et de jeu de données Premium avec des principaux de service](service-premium-service-principal.md)   
[Résolution des problèmes de la fonctionnalité Analyser dans Excel](../collaborate-share/desktop-troubleshooting-analyze-in-excel.md)   
[Déploiement de solutions de modèle tabulaire](https://docs.microsoft.com/analysis-services/deployment/tabular-model-solution-deployment?view=power-bi-premium-current)
