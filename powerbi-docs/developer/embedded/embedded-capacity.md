---
title: Capacité et références SKU dans l’analytique incorporée de Power BI
description: Comprenez la capacité et les références SKU dans l’analytique incorporée de Power BI.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 05/17/2020
ms.openlocfilehash: 4102ed7307c9b7be40fb682befc4056094cbe6ad
ms.sourcegitcommit: 4ac9447d1607dfca2e60948589f36a3d64d31cb4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/29/2020
ms.locfileid: "92916932"
---
# <a name="capacity-and-skus-in-power-bi-embedded-analytics"></a>Capacité et références SKU dans l’analytique incorporée de Power BI

En basculant en mode production, l’analytique incorporée de Power BI nécessite une capacité (référence SKU *A* , *EM* ou *P* ) pour la publication de contenu Power BI incorporé.

La capacité est un ensemble dédié de ressources réservées à une utilisation exclusive. Elle vous permet de publier des tableaux de bord, des rapports et des jeux de données pour les utilisateurs sans avoir à acheter des licences par utilisateur. De plus, le niveau de performance qu’elle offre pour votre contenu est fiable et homogène.

>[!NOTE]
>Pour la publication, vous aurez besoin d’un compte Power BI Pro.

## <a name="what-is-embedded-analytics"></a>Qu’est-ce que l’analytique incorporée ?

L’analytique incorporée de Power BI comporte deux solutions :
* *Power BI Embedded* – Offre Azure
* Incorporation de Power BI dans *Power BI Premium* – Offre Office

### <a name="power-bi-embedded"></a>Power BI Embedded

Power BI Embedded s’adresse aux éditeurs de logiciels indépendants et aux développeurs qui souhaitent incorporer des visuels dans leurs applications.

Les applications qui utilisent Power BI Embedded permettent aux utilisateurs de consommer le contenu stocké dans la capacité Power BI Embedded.

### <a name="power-bi-premium"></a>Power BI Premium

[Power BI Premium](../../admin/service-premium-what-is.md) s’adresse aux grandes entreprises qui souhaitent une solution de décisionnel complète leur permettant de visualiser au même emplacement les informations concernant leur organisation, leurs partenaires, leurs clients et leurs fournisseurs.

Power BI Premium est un produit SaaS qui permet aux utilisateurs de consommer du contenu via des applications mobiles, des applications développées en interne ou sur le portail Power BI (service Power BI). Power BI Premium offre ainsi une solution pour les applications internes et externes à destination des clients.

## <a name="capacity-and-skus"></a>Capacité et références SKU

Chaque capacité propose plusieurs références SKU qui offrent chacune différents niveaux de ressources pour la mémoire et la puissance de calcul. Le type de référence SKU dont vous avez besoin dépend du type de solution que vous souhaitez déployer.

Pour comprendre les charges de travail qui sont prises en charge pour chaque niveau, consultez l’article [Configurer des charges de travail dans une capacité Premium](../../admin/service-admin-premium-workloads.md)

Utilisez ces liens pour planifier et tester votre capacité :
* [Planification de la capacité](embedded-capacity-planning.md)
* [Approches de test](../../admin/service-premium-capacity-optimize.md#testing-approaches)

### <a name="power-bi-embedded-skus"></a>Références SKU Power BI Embedded

Power BI Embedded est fourni avec une référence SKU [*A*](../../admin/service-admin-premium-purchase.md#purchase-a-skus-for-testing-and-other-scenarios).

### <a name="power-bi-premium-skus"></a>Références SKU Power BI Premium

Power BI Premium propose deux références SKU : *P* et *EM*.
* [Comprendre les différences entre les références SKU *P* et *EM*](../../admin/service-premium-what-is.md#subscriptions-and-licensing)
* [Acheter une référence SKU Premium](../../admin/service-admin-premium-purchase.md)

### <a name="which-sku-should-i-use"></a>Quelle référence SKU acheter ?

Le tableau ci-dessous présente un résumé des fonctionnalités, la capacité qu’elles nécessitent et la référence SKU que chacune d’elles exige.

Dans ce tableau, une application personnalisée fait référence à une application web créée à l’aide de l’analytique incorporée. Quand vous incorporez dans une application web personnalisée en tant que développeur (à l’aide des kits de développement logiciel (SDK) JavaScript ou .NET, ou les API REST), vous avez la possibilité de contrôler et personnaliser l’expérience utilisateur. Cette fonctionnalité n’est pas disponible lorsque vous utilisez d’autres options d’incorporation, comme le service Power BI et Power BI Mobile.

| Scénario | Azure   | Office          |
|----------|---------|-----------------|
|          | (SKU A) | (SKU P et EM) |
|[Incorporer pour vos clients](embed-sample-for-customers.md)</br>(l’application est propriétaire des données)     |✔        |✔        |
|[Incorporer pour votre organisation](embed-sample-for-your-organization.md)</br>(l’utilisateur est propriétaire des données)     |✖        |✔         |
|Applications Microsoft 365</br>(anciennement appelées applications Office 365)<ul><li>[Incorporer dans Teams](../../collaborate-share/service-embed-report-microsoft-teams.md)</li><li>[Incorporer dans SharePoint](../../collaborate-share/service-embed-report-spo.md)</li></ul>     |✖        |✔        |
|[Incorporation d’URL sécurisée](../../collaborate-share/service-embed-secure.md)</br>(incorporation depuis le service Power BI)     |✖        |✔        |

>[!NOTE]
>* Une [licence Power BI Pro](../../admin/service-admin-purchasing-power-bi-pro.md) est nécessaire pour la publication de contenu dans un espace de travail d’application Power BI.
>* Seul le **SKU P** permet aux utilisateurs Power BI gratuits de consommer des applications et du contenu partagé Power BI dans le service Power BI.

### <a name="capacity-considerations"></a>Considérations relatives à la capacité

Le tableau ci-dessous liste les éléments à prendre en considération pour le paiement et l’utilisation, par capacité.

</br>
<table>
<tbody>
<tr>
<td></td>
<td style="text-align: center;"><p><strong>Power BI Embedded</strong></p></td>
<td style="text-align: center;" colspan="2"><p><strong>Power BI Premium</strong></p></td>
</tr>
<tr>
<td><p><strong>Offer</strong></p></td>
<td style="text-align: center"><p>Azure</p></td>
<td style="text-align: center" colspan="2"><p>Office</p></td>
</tr>
<tr>
<td><p><strong>Référence (SKU)</strong></p></td>
<td style="text-align: center"><p>A</p></td>
<td style="text-align: center"><p>EM</p></td>
<td style="text-align: center"><p>P</p></td>
</tr>
<tr>
<td><p><strong>Billing</strong></td>
<td style="text-align: center">Toutes les heures</td>
<td style="text-align: center">Mensuelle</td>
<td style="text-align: center">Mensuelle</td>
</tr>
<tr>
<td><p><strong>Avec engagement</strong></td>
<td style="text-align: center">Aucune</td>
<td style="text-align: center">Annuel</td>
<td style="text-align: center">Mensuel ou annuel</td>
</tr>
<tr>
<td valign="top"><p><strong>Utilisation</strong></td>
<td style="text-align: center">Les ressources Azure peuvent faire l’objet des opérations suivantes :<li><a href="azure-pbie-scale-capacity.md">Scale-up ou scale down</a></li><li><a href="azure-pbie-pause-start.md">Suspension et reprise</a>
</td></li>
<td style="text-align: center">Incorporer dans les applications et dans</br> les applications Microsoft</td>
<td style="text-align: center">Incorporer dans les applications et</br> dans le service Power BI</td>
</tr>
</tbody>
</table>

### <a name="sku-memory-and-computing-power"></a>Mémoire et puissance de calcul des références SKU

Le tableau ci-dessous décrit les ressources et les limites de chaque référence SKU.

| Nœuds de capacité | Total des v-cores | Cœurs virtuels backend | RAM (Go) | Cœurs virtuels frontend | DirectQuery/Connexions actives (par seconde) | Parallélisme des actualisations de modèles |
| --- | --- | --- | --- | --- | --- | --- |
| EM1/A1 | 1 | 0,5 | 2.5 | 0,5 | 3,75 | 1 |
| EM2/A2 | 2 | 1 | 5 | 1 | 7,5 | 2 |
| EM3/A3 | 4 | 2 | 10 | 2 | 15 | 3 |
| P1/A4 | 8 | 4 | 25 | 4 | 30 | 6 |
| P2/A5 | 16 | 8 | 50 | 8 | 60 | 12 |
| P3/A6 | 32 | 16 | 100 | 16 | 120 | 24 |
| P4 | 64 | 32 | 200 | 32 | 240 | 48 |
| P5 | 128 | 64 | 400 | 64 | 480 | 96 |
| | | | | | | |

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
>[Incorporer pour vos clients](embed-sample-for-customers.md)

> [!div class="nextstepaction"]
>[Incorporer pour votre organisation](embed-sample-for-your-organization.md)

> [!div class="nextstepaction"]
> [Incorporer à partir d’applications](embed-from-apps.md)