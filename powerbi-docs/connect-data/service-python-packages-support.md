---
title: Découvrez quels packages Python sont pris en charge
description: Packages Python pris et non pris en charge dans Power BI
author: otarb
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 06/26/2020
ms.author: otarb
LocalizationGroup: Connect to data
ms.openlocfilehash: b1dc77d2ebf0803430ceeace7e14bfa62a6d2a60
ms.sourcegitcommit: e8b12d97076c1387088841c3404eb7478be9155c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85785205"
---
# <a name="create-visuals-by-using-python-packages-in-the-power-bi-service"></a>Créer des visuels en utilisant des packages Python dans le service Power BI
Vous pouvez utiliser le puissant [langage de programmation Python](https://www.python.org/) pour créer des visuels dans le service Power BI. De nombreux packages Python sont pris en charge dans le service Power BI et bien plus encore sont pris en charge tout le temps.

Les sections suivantes présentent un tableau contenant les packages Python pris en charge dans Power BI, classés par ordre alphabétique. 

## <a name="request-support-for-a-new-python-package"></a>Demander la prise en charge d’un nouveau package Python
Les packages Python pris en charge pour le **service Power BI** se trouvent dans la section suivante intitulée **Packages pris en charge**. Si vous souhaitez demander la prise en charge d’un package Python introuvable dans cette liste, envoyez votre demande sur le site [Power BI Ideas](https://ideas.powerbi.com).

## <a name="requirements-and-limitations-of-python-packages"></a>Spécifications et limitations des packages Python
Il existe quelques spécifications et limitations concernant les packages Python :

* Runtime Python actuel : Python 3.7.7.
* Le service Power BI, pour l’essentiel, prend en charge les packages Python avec des licences logicielles gratuites et open source comme GPL-2, GPL-3, MIT+, etc.
* Le service Power BI prend en charge les packages publiés dans PyPI. Le service ne prend pas en charge les packages Python privés ou personnalisés. Les utilisateurs doivent, si possible, mettre leurs packages privés à disposition sur le site PyPI avant de demander leur mise à disposition dans le service Power BI.
* Pour les visuels Python dans **Power BI Desktop**, vous pouvez installer n’importe quel package, notamment des packages Python personnalisés.
* Pour des raisons de confidentialité et de sécurité, les packages Python qui fournissent des requêtes client-serveur dans le service via le web ne sont pas pris en charge. La mise en réseau est bloquée lors de ces tentatives.
* Le processus d’approbation visant à inclure un nouveau package Python implique un certain nombre de dépendances. Certaines dépendances qui doivent être installées dans le service ne sont pas prises en charge.

## <a name="python-packages-that-are-supported-in-power-bi"></a>Packages Python pris en charge dans Power BI
Le tableau suivant indique les packages **pris en charge** dans le service Power BI.


|        Package        |   Version   |                                   Lien                                   |
|-----------------------|-------------|--------------------------------------------------------------------------|
|matplotlib|3.2.1|https://pypi.org/project/matplotlib|
|numpy|1.18.4|https://pypi.org/project/numpy|
|pandas|1.0.1|https://pypi.org/project/pandas|
|scikit-learn|0.23.0|https://pypi.org/project/scikit-learn|
|scipy|1.4.1|https://pypi.org/project/scipy|
|s  eaborn|0.10.1|https://pypi.org/project/seaborn|
|statsmodels|0.11.1|https://pypi.org/project/statsmodels|
|xgboost|1.1.0|https://pypi.org/project/xgboost|

## <a name="next-steps"></a>Étapes suivantes
Pour en savoir plus sur Python dans Power BI, consultez les articles suivants :

* [Créer des visuels Power BI avec Python](desktop-python-visuals.md)
* [Exécution de scripts Python dans Power BI Desktop](desktop-python-scripts.md)
* [Utilisation de Python dans l’Éditeur de requête](desktop-python-in-query-editor.md)
