---
title: Conseils relatifs au déploiement d’une passerelle de données pour Power BI
description: Familiarisez-vous avec les meilleures pratiques et considérations relatives au déploiement d’une passerelle pour Power BI.
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: conceptual
ms.date: 07/15/2019
ms.author: mblythe
LocalizationGroup: Gateways
ms.openlocfilehash: 4351804330982b32582c4c782ef7c2fa0e92f197
ms.sourcegitcommit: 277fadf523e2555004f074ec36054bbddec407f8
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/16/2019
ms.locfileid: "68271721"
---
# <a name="guidance-for-deploying-a-data-gateway-for-power-bi"></a>Conseils relatifs au déploiement d’une passerelle de données pour Power BI

[!INCLUDE [gateway-rewrite](includes/gateway-rewrite.md)]

Cet article fournit des conseils et indications sur le déploiement d’une passerelle de données pour Power BI dans votre environnement réseau.

Pour plus d’informations sur le téléchargement, l’installation, la configuration et la gestion de la passerelle de données locale, consultez [Qu’est-ce qu’une passerelle de données locale ?](/data-integration/gateway/service-gateway-onprem). Vous pouvez également en savoir plus sur la passerelle de données locale et Power BI en consultant le [blog Microsoft Power BI](https://powerbi.microsoft.com/blog/) et le site de la [Communauté Microsoft Power BI](https://community.powerbi.com/).

## <a name="installation-considerations-for-the-on-premises-data-gateway"></a>Éléments à prendre en compte lors de l’installation de la passerelle de données locale

Avant d’installer la passerelle de données locale pour votre service cloud Power BI, vous devez garder à l’esprit quelques considérations, qui sont décrites dans les sections suivantes.

### <a name="number-of-users"></a>Nombre d’utilisateurs

Le nombre d’utilisateurs qui utilisent un rapport par le biais de la passerelle est l’un des principaux critères à prendre en compte pour déterminer où installer la passerelle. Posez-vous les questions suivantes :

* Les utilisateurs utilisent-ils ces rapports à différents moments de la journée ?
* Quels types de connexions utilisent-ils (mode DirectQuery ou Importer) ?
* Tous les utilisateurs utilisent-ils le même rapport ?

Si tous les utilisateurs accèdent quotidiennement à un rapport donné au même moment, vous devez installer la passerelle sur un ordinateur capable de gérer toutes ces requêtes (reportez-vous aux sections suivantes pour en savoir plus sur les compteurs de performances et sur la configuration minimale requise).

Dans la mesure où **Power BI** n’autorise qu’*une* seule passerelle par *rapport*, même si un rapport repose sur plusieurs sources de données, toutes ces sources doivent transiter par une passerelle unique. Toutefois, si un tableau de bord repose sur *plusieurs* rapports, vous pouvez dédier une passerelle à chaque rapport contributeur afin de répartir la charge entre les différents rapports qui contribuent à ce tableau de bord.

### <a name="connection-type"></a>Type de connexion

**Power BI** propose deux types de connexion : **DirectQuery** et **Importer**. Certaines sources de données ne prennent pas en charge ces deux types de connexion, et vous pouvez être amené à choisir l’un plutôt que l’autre pour différentes raisons (exigences de sécurité, performances, limites de données, taille des modèle de données, etc.). Pour en savoir plus sur les type de connexions et sur les sources de données prises en charge, consultez la [liste des types de sources de données disponibles](service-gateway-data-sources.md#list-of-available-data-source-types).

Selon le type de connexion, l’utilisation de la passerelle peut être différente. Par exemple, dans la mesure du possible, vous devez tenter de séparer les sources de données **DirectQuery** des sources de données **Actualisation planifiée** (si elles se trouvent dans des rapports différents et qu’elles peuvent être séparées). Vous éviterez ainsi la mise en file d’attente de milliers de requêtes DirectQuery dans la passerelle au moment de l’actualisation matinale planifiée d’un modèle de données volumineux utilisé pour le tableau de bord principal de l’entreprise. Voici les éléments à prendre en compte pour les deux types de sources de données :

* Pour l’**Actualisation planifiée** : selon la taille de vos requêtes et le nombre d’actualisations quotidiennes, vous pouvez vous en tenir à la configuration matérielle minimale recommandée ou procéder à une mise à niveau vers un ordinateur plus performant. Si une requête donnée n’est pas traitée, des transformations interviennent sur l’ordinateur passerelle, d’où la nécessité de disposer d’une mémoire RAM suffisante sur celui-ci.

* Pour **DirectQuery** : une requête est envoyée chaque fois qu’un utilisateur ouvre le rapport ou examine des données. Par conséquent, si vous savez que plus de 1 000 utilisateurs risquent d’accéder simultanément aux données, veillez à ce que les composants matériels de votre ordinateur soient suffisamment robustes et fiables. Dans le cadre d’une connexion **DirectQuery**, un nombre accru de cœurs d’UC offre un meilleur débit.

La configuration requise pour un ordinateur sur lequel vous effectuez l’installation est disponible dans la section sur la [configuration requise pour l’installation](/data-integration/gateway/service-gateway-install#requirements) de la passerelle de données locale.

### <a name="location"></a>Emplacement

L’emplacement d’installation de la passerelle peut avoir un impact significatif sur les performances de vos requêtes. Par conséquent, veillez à ce que votre passerelle, les emplacements de vos sources de données et le locataire Power BI soient aussi proches que possible les uns des autres afin de minimiser les temps de réponse du réseau. Pour déterminer l’emplacement de votre locataire Power BI, dans le service Power BI, sélectionnez l’icône **?** en haut à droite de l’écran, puis choisissez **À propos de Power BI**.

![Déterminer l’emplacement de votre locataire Power BI](media/service-gateway-deployment-guidance/powerbi-gateway-deployment-guidance_02.png)

Si vous envisagez d’utiliser la passerelle Power BI avec Azure Analysis Services, vérifiez aussi que les régions de données sont identiques. Pour plus d’informations sur la définition des régions de données pour plusieurs services, regardez [cette vidéo](https://guyinacube.com/2018/01/power-bi-azure-analysis-services-gateway-data-region/).

## <a name="next-steps"></a>Étapes suivantes

* [Configuration des paramètres de proxy](/data-integration/gateway/service-gateway-proxy)  
* [Résoudre les problèmes liés aux passerelles - Power BI](service-gateway-onprem-tshoot.md)  
* [Questions fréquentes (FAQ) sur la passerelle de données locale - Power BI](service-gateway-power-bi-faq.md)  

D’autres questions ? [Posez vos questions à la communauté Power BI](http://community.powerbi.com/)

