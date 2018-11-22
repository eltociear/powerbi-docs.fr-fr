---
title: Passerelle de données locale
description: Voici une vue d’ensemble de la passerelle de données locale pour Power BI. Vous pouvez utiliser cette passerelle pour travailler avec les sources de données DirectQuery. Vous pouvez également utiliser cette passerelle pour actualiser les jeux de données cloud avec les données locales.
author: mgblythe
ms.author: mblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
LocalizationGroup: Gateways
ms.date: 06/05/2018
ms.openlocfilehash: 8bdb249543d8d6b5b0cb7d75e3295adc751e5ab1
ms.sourcegitcommit: a13abdb5a6c0c6a397b328ec2d68788ce3afa866
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2018
ms.locfileid: "52268340"
---
# <a name="on-premises-data-gateway"></a>Passerelle de données locale

La passerelle de données locale agit comme un pont, assurant un transfert de données rapide et sûr entre les données locales (les données qui ne sont pas dans le cloud) et les services Power BI, Microsoft Flow, Logic Apps et PowerApps.

Vous pouvez utiliser une seule passerelle avec différents services en même temps. Si vous utilisez Power BI ainsi que PowerApps, il est possible d’utiliser une seule passerelle pour les deux. Elle dépend du compte que vous utilisez pour vous connecter.

> [!NOTE]
> La passerelle de données locale implémente la compression de données et le chiffrement du transport dans tous les modes.

<!-- Shared Requirements Include -->
[!INCLUDE [gateway-onprem-requirements-include](./includes/gateway-onprem-requirements-include.md)]

### <a name="limitations-of-analysis-services-live-connections"></a>Limitations des connexions actives Analysis Services

Vous pouvez utiliser une connexion active à des instances tabulaires ou multidimensionnelles.

| **Version du serveur** | **Référence (SKU) requise** |
| --- | --- |
| 2012 SP1 CU4 ou version ultérieure |Business Intelligence et Enterprise |
| 2014 |Business Intelligence et Enterprise |
| 2016 |Référence (SKU) standard ou version ultérieure |

* Les fonctionnalités de mise en forme au niveau de la cellule et les fonctions de traduction ne sont pas prises en charge.
* Actions et jeux nommés ne sont pas exposés à Power BI, mais vous pouvez toujours vous connecter à des cubes multidimensionnels qui contiennent également les propriétés Actions ou Jeux nommés et créer des rapports et des éléments visuels.

<!-- Shared Install steps Include -->
[!INCLUDE [gateway-onprem-datasources-include](./includes/gateway-onprem-datasources-include.md)]

## <a name="download-and-install-the-on-premises-data-gateway"></a>Télécharger et installer la passerelle de données locale

Pour télécharger la passerelle, sélectionnez **Passerelle de données** dans le menu Téléchargements. Téléchargez la [passerelle de données locale](http://go.microsoft.com/fwlink/?LinkID=820925).

Notez que vous mettez à jour la passerelle de données locale en la réinstallant, comme cela est décrit dans cette section. Tant que vous installez une version plus récente de la passerelle, vos paramètres existants sont conservés. Si vous installez la même version, il la traite comme une réinstallation complète et vos paramètres ne sont pas conservés.

![](media/service-gateway-onprem/powerbi-download-data-gateway.png)

<!-- Shared Install steps Include -->
[!INCLUDE [gateway-onprem-install-include](./includes/gateway-onprem-install-include.md)]

## <a name="install-the-gateway-in-personal-mode"></a>Installer la passerelle en mode personnel

> [!NOTE]
> La version personnelle de la passerelle fonctionne uniquement avec Power BI.

Une fois la passerelle personnelle installée, vous devez lancer l’Assistant de configuration **Power BI Gateway - Personal**.

![](media/service-gateway-onprem/personal-gateway-launch-configuration.png)

Vous devez ensuite vous connecter à Power BI pour inscrire la passerelle auprès du service cloud.

![](media/service-gateway-onprem/personal-gateway-signin.png)

Vous devez également fournir le nom d’utilisateur Windows et le mot de passe avec lesquels le service Windows s’exécutera. Vous pouvez spécifier un autre compte Windows à partir du vôtre. Le service de passerelle s’exécute à l’aide de ce compte.

![](media/service-gateway-onprem/personal-gateway-windows-service.png)

Une fois l’installation terminée, vous devez accéder à vos jeux de données dans Power BI et vérifier que les informations d’identification ont été entrées pour vos sources de données locales.

<a name="credentials"></a>

## <a name="storing-encrypted-credentials-in-the-cloud"></a>Stockage d’informations d’identification chiffrées dans le cloud

Lorsque vous ajoutez une source de données à la passerelle, vous devez fournir les informations d’identification associées. Toutes les requêtes à la source de données sont exécutées à l’aide de ces informations d’identification. Les informations d’identification sont chiffrées en toute sécurité, à l’aide d’un chiffrage asymétrique de sorte qu’elles ne soient pas déchiffrées dans le cloud, avant qu’elles soient stockées dans le cloud. Les informations d’identification sont envoyées à l’ordinateur exécutant la passerelle en local, où elles sont déchiffrées lorsque les sources de données sont consultées.

<!-- Account and Port information -->
[!INCLUDE [gateway-onprem-accounts-ports-more](./includes/gateway-onprem-accounts-ports-more.md)]

<!-- How the gateway works -->
[!INCLUDE [gateway-onprem-how-it-works-include](./includes/gateway-onprem-how-it-works-include.md)]

## <a name="limitations-and-considerations"></a>Considérations et limitations

* [Azure Information Protection](https://docs.microsoft.com/microsoft-365/enterprise/protect-files-with-aip
) n’est pas pris en charge pour l’instant.
* L’[accès en ligne](https://products.office.com/en-us/access) n’est pas pris en charge pour l’instant.
* Les scripts R sont pris en charge seulement si la passerelle s’exécute en mode personnel.

## <a name="tenant-level-administration"></a>Administration au niveau locataire

Actuellement, les administrateurs de locataires n’ont aucun endroit où ils peuvent gérer toutes les passerelles que les autres utilisateurs ont installées et configurées.  Si vous êtes administrateur de locataires, nous vous recommandons de demander aux utilisateurs de votre organisation de vous ajouter comme administrateur pour chaque passerelle qu’ils installent. Vous pourrez ainsi gérer toutes les passerelles de votre organisation en utilisant la page Paramètres de la passerelle ou les [commandes PowerShell](https://docs.microsoft.com/power-bi/service-gateway-high-availability-clusters#powershell-support-for-gateway-clusters). 

## <a name="enabling-outbound-azure-connections"></a>Activation des connexions Azure sortantes

La passerelle de données locale s’appuie sur le Azure Service Bus pour la connectivité cloud et établit des connexions sortantes correspondantes avec sa région Azure associée. Par défaut, il s’agit de l’emplacement de votre locataire Power BI. Consultez [Où est situé mon locataire Power BI ?](https://powerbi.microsoft.com/en-us/documentation/powerbi-admin-where-is-my-tenant-located/)
Si un pare-feu bloque les connexions sortantes, vous devez le configurer de façon à autoriser les connexions sortantes de la passerelle de données locale avec la région Azure associée. Pour plus d’informations sur les plages d’adresses IP de chaque centre de données Azure, consultez [Plages d’adresses IP des centres de données Microsoft Azure](https://www.microsoft.com/download/details.aspx?id=41653).
> [!NOTE]
> Les plages d’adresses IP peuvent changer au fil du temps, veillez donc à télécharger les informations les plus récentes de façon régulière. 

## <a name="troubleshooting"></a>Résolution des problèmes

Si vous rencontrez des difficultés lors de l’installation et de la configuration d’une passerelle, consultez [Résolution des problèmes liés à la passerelle de données locale](service-gateway-onprem-tshoot.md). Si vous pensez que vous rencontrez un problème avec votre pare-feu, consultez la section [pare-feu ou proxy](service-gateway-onprem-tshoot.md#firewall-or-proxy) dans l’article de résolution des problèmes.

Si vous pensez que vous rencontrez des problèmes de proxy avec la passerelle, consultez [Configuration des paramètres de proxy pour les passerelles Power BI](service-gateway-proxy.md).

## <a name="next-steps"></a>Étapes suivantes

[Gérer votre source de données - Analysis Services](service-gateway-enterprise-manage-ssas.md)  
[Gérer votre source de données - SAP HANA](service-gateway-enterprise-manage-sap.md)  
[Gérer votre source de données - SQL Server](service-gateway-enterprise-manage-sql.md)  
[Gérer votre source de données - Oracle](service-gateway-onprem-manage-oracle.md)  
[Gérer votre source de données - Importation/actualisation planifiée](service-gateway-enterprise-manage-scheduled-refresh.md)  
[Informations approfondies sur la passerelle de données locale](service-gateway-onprem-indepth.md)  
[Passerelle de données locale (mode personnel) - nouvelle version de la passerelle personnelle](service-gateway-personal-mode.md)  
[Configuration des paramètres de proxy de la passerelle de données locale](service-gateway-proxy.md)  

D’autres questions ? [Posez vos questions à la communauté Power BI](http://community.powerbi.com/)
