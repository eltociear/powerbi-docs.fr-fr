---
title: "Désactivation des paramètres de confidentialité"
description: "Comment activer la combinaison rapide au sein de la passerelle personnelle pour désactiver les paramètres de confidentialité pour l’actualisation."
services: powerbi
documentationcenter: 
author: davidiseminger
manager: kfile
backup: 
editor: 
tags: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: powerbi
ms.date: 12/06/2017
ms.author: davidi
ms.openlocfilehash: 1e68f7df5214e038df8bcd1584acb815c0af98bf
ms.sourcegitcommit: 70e9239e375ae03744fb9bc122d5fc029fb83469
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="disable-privacy-setting-in-power-bi-gateway---personal"></a>Désactivation du paramètre de confidentialité dans Power BI Gateway - Personal
> [!NOTE]
> Une nouvelle version de la passerelle de données locale, appelée **Passerelle de données locale (mode personnel)** est disponible pour Power BI. L’article suivant décrit la précédente version de la passerelle personnelle, appelée **Power BI Gateway - Personal**, qui sera supprimée et cessera de fonctionner après le 31 juillet 2017. Pour plus d’informations sur la nouvelle version de la passerelle personnelle, notamment sur son installation, consultez l’article [**Passerelle de données locale (mode personnel)**](service-gateway-personal-mode.md). Le regroupement rapide, également décrit dans cet article, est toujours disponible dans la nouvelle version de la passerelle personnelle.
> 
> 

Vous pouvez recevoir l’erreur suivante en fonction des paramètres de confidentialité de vos sources de données lorsque vous utilisez la passerelle personnelle.

> *Une erreur s’est produite pendant le traitement des données du jeu de données.*
> 
> *[Impossible de combiner des données] &lt;partie de requête&gt;/&lt;…&gt;/&lt;…&gt; accède à des sources de données dont les niveaux de confidentialité ne peuvent pas être utilisés ensemble. Reconstruisez cette combinaison de données.*
> 
> 

Pour résoudre cette erreur, vous pouvez activer l’option **Combinaison rapide**. L’option **Combinaison rapide** permet d’ignorer les paramètres de confidentialité autorisant la combinaison des différentes sources de données.

> [!NOTE]
> Les niveaux de confidentialité ne sont pas pris en compte lors de la combinaison de données. Cela pourrait exposer des données sensibles ou confidentielles à une autre source de données lors de la combinaison de données.
> 
> 

## <a name="what-is-fast-combine"></a>Qu’est-ce que la combinaison rapide ?
Pour plus d’informations sur les niveaux de confidentialité et la combinaison rapide, vous pouvez consulter [Niveaux de confidentialité](https://support.office.com/en-us/article/Privacy-levels-Power-Query-CC3EDE4D-359E-4B28-BC72-9BEE7900B540). Par défaut, le niveau de confidentialité est défini sur privé, ce qui peut entraîner l’erreur mentionnée ci-dessus. Cela résulte du fait qu’un niveau de confidentialité privé a pour effet d’isoler la source de données d’autres sources. Un exemple de situation où cela serait problématique est celui d’une requête paramétrable obtenant des entrées d’une autre source de données.

L’activation de la combinaison rapide a pour effet d’ignorer le niveau de confidentialité privé et d’autoriser l’exécution.

## <a name="turn-on-fast-combine"></a>Activation de la combinaison rapide
Les étapes suivantes permettent d’activer le regroupement rapide pour votre passerelle personnelle. La passerelle de données locale n’a pas ce paramètre.

1. Ouvrez **ConnectorConfig.xml**.  Ce fichier peut se trouver dans deux emplacements sur votre ordinateur.  Si vous êtes administrateur de l’ordinateur, l’emplacement est le suivant.
   
    <pre><code>C:\Program Files\Power BI Personal Gateway\1.0\Configurator\Connector</code></pre>
   
    Si vous n’êtes pas un administrateur, l’emplacement est le suivant.
   
    <pre><code>C:\Users\[username]\AppData\Local\Power BI Personal Gateway\1.0\Configurator\Connector</code></pre>
    
2. Ajoutez l’élément **&lt;EnableFastCombine&gt;** avec la valeur « True » au fichier de configuration. L’ajout de cet élément active la **combinaison rapide** .
   
   <pre><code>&lt;EnableFastCombine&gt;true&lt;/EnableFastCombine&gt;</code></pre>
   
   ![](media/refresh-enable-fast-combine/configfile.png)
3. Fermez puis rouvrez l’écran de configuration de la passerelle.
4. Un état s’affiche, vous informant que la combinaison rapide est activée.
   
   ![](media/refresh-enable-fast-combine/fastcombineenabled.png)

## <a name="turn-off-fast-combine"></a>Désactivation de la combinaison rapide
1. Ouvrez **ConnectorConfig.xml**.  Ce fichier peut se trouver dans deux emplacements sur votre ordinateur.  Si vous êtes administrateur de l’ordinateur, l’emplacement est le suivant.
   
    <pre><code>C:\Program Files\Power BI Personal Gateway\1.0\Configurator\Connector</code></pre>
   
    Si vous n’êtes pas un administrateur, l’emplacement est le suivant.
   
    <pre><code>C:\Users\[username]\AppData\Local\Power BI Personal Gateway\1.0\Configurator\Connector</code></pre>

2. Supprimez l’élément **&lt;EnableFastCombine&gt;** du fichier de configuration. La suppression de cet élément désactive la **combinaison rapide** .
3. Fermez puis rouvrez l’écran de configuration de la passerelle.
4. Vous ne voyez plus d’état indiquant que vous savez que la **combinaison rapide** est activée.

## <a name="next-steps"></a>Étapes suivantes
[Passerelle de données locale (mode personnel) - nouvelle version de la passerelle personnelle](service-gateway-personal-mode.md)
[Niveaux de confidentialité](https://support.office.com/en-us/article/Privacy-levels-Power-Query-CC3EDE4D-359E-4B28-BC72-9BEE7900B540)  
[Tâches courantes relatives aux requêtes dans Power BI Desktop](desktop-common-query-tasks.md)  
D’autres questions ? [Posez vos questions à la communauté Power BI](http://community.powerbi.com/)

