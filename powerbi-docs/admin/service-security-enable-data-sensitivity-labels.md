---
title: Activer les étiquettes de sensibilité des données dans Power BI
description: Découvrir comment activer les étiquettes de sensibilité des données dans Power BI
author: paulinbar
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 10/25/2019
ms.author: painbar
LocalizationGroup: Data from files
ms.openlocfilehash: 024e04bd309080b5b31e43bde7c783255bfc3dba
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2019
ms.locfileid: "73851064"
---
# <a name="enable-data-sensitivity-labels-in-power-bi-preview"></a>Activer les étiquettes de sensibilité des données dans Power BI (préversion)

Quand les [étiquettes de sensibilité des données Microsoft Information Protection](https://docs.microsoft.com/microsoft-365/compliance/sensitivity-labels) sont activées dans Power BI, les conditions suivantes s’appliquent :

* Certains utilisateurs et groupes de sécurité d’une organisation peuvent classifier et [appliquer des étiquettes de sensibilité](../designer/service-security-apply-data-sensitivity-labels.md) à leurs tableaux de bord, rapports, jeux de données et dataflows Power BI (ci-après dénommés *ressources*).
* Tous les membres de l’organisation peuvent voir ces étiquettes.

Les étiquettes de sensibilité des données favorisent la protection des données en faisant en sorte que les auteurs et consommateurs Power BI prennent conscience de la sensibilité des données, tout en leur fournissant des informations sur ce que signifie la classification et sur la façon dont les données correspondantes doivent être gérées.

Quand des données Power BI qui ont une étiquette de sensibilité des données sont exportées vers un fichier Excel, PowerPoint ou PDF, leur étiquette de sensibilité des données leur est associée. Cela signifie qu’un utilisateur qui ne dispose pas de l’autorisation d’accéder à des données étiquetées, en raison de stratégies d’étiquettes de sensibilité, ne peut pas ouvrir les fichiers *en dehors* de Power BI (dans les applications Excel, PowerPoint ou PDF).

L’activation des étiquettes de sensibilité des données nécessite une licence Azure Information Protection. Pour plus d’informations, consultez [Gestion des licences](#licensing).

## <a name="enable-data-sensitivity-labels"></a>Activer les étiquettes de sensibilité des données

Pour activer l’utilisation des étiquettes de sensibilité des données Microsoft Information Protection dans Power BI, accédez au portail d’administration Power BI, ouvrez le volet Paramètres du locataire et recherchez la section Information Protection.

![Rechercher la section Information Protection](media/service-security-enable-data-sensitivity-labels/enable-data-sensitivity-labels-01.png)

Dans la section **Information Protection**, effectuez les étapes suivantes :
1.  Activez le bouton bascule **Activer les étiquettes de confidentialité Microsoft Information Protection**, puis appuyez sur **Appliquer**. Cette étape rend *uniquement* les étiquettes de sensibilité visibles pour l’ensemble de votre organisation ; elle n’applique aucune étiquette. Pour définir qui peut appliquer ces étiquettes dans Power BI, vous devez effectuer l’étape 2.
2.  Définissez qui peut appliquer et changer les étiquettes de sensibilité dans les ressources Power BI. Cette étape implique trois actions :
    1.  Activez le bouton bascule **Définir des étiquettes de confidentialité pour le contenu et les données Power BI**.
    2.  Sélectionnez le ou les groupes de sécurité appropriés. Par défaut, toutes les personnes de votre organisation peuvent appliquer des étiquettes de sensibilité. Toutefois, vous pouvez choisir d’activer le paramétrage des étiquettes de sensibilité uniquement pour des utilisateurs ou des groupes de sécurité spécifiques. Si vous avez sélectionné l’ensemble de l’organisation ou des groupes de sécurité particuliers, vous pouvez exclure des sous-ensembles spécifiques d’utilisateurs ou de groupes de sécurité.
    * Quand les étiquettes de sensibilité sont activées pour l’ensemble de l’organisation, les exceptions sont généralement des groupes de sécurité.
    * Quand les étiquettes de sensibilité sont activées uniquement pour des utilisateurs ou des groupes de sécurité spécifiques, les exceptions sont généralement des utilisateurs spécifiques.  
    Cette approche permet d’empêcher certains utilisateurs d’appliquer des étiquettes de sensibilité dans Power BI, même s’ils appartiennent à un groupe disposant des autorisations nécessaires.
    
    3. Appuyez sur **Appliquer**.

![Activer les étiquettes de sensibilité](media/service-security-enable-data-sensitivity-labels/enable-data-sensitivity-labels-02.png)

> [!IMPORTANT]
> Seuls les utilisateurs Power BI Pro qui disposent d’autorisations *créer* et *modifier* sur la ressource et qui font partie du groupe de sécurité approprié défini dans cette section peuvent définir et modifier les étiquettes de sensibilité. Les utilisateurs qui ne font pas partie de ce groupe ne peuvent pas définir ou modifier l’étiquette. 


## <a name="considerations-and-limitations"></a>Considérations et limitations

Power BI utilise les étiquettes de sensibilité Microsoft Information Protection. Par conséquent, si un message d’erreur s’affiche lors d’une tentative d’activation des étiquettes de sensibilité, cela peut être dû à l’une des raisons suivantes :

* Vous ne disposez pas de [licence](#licensing) Azure Information Protection.
* Les étiquettes de sensibilité n’ont pas été migrées vers la version de Microsoft Information Protection prise en charge par Power BI. Découvrez des informations supplémentaires sur la [migration des étiquettes de sensibilité](https://docs.microsoft.com/azure/information-protection/configure-policy-migrate-labels).
* Aucune étiquette de sensibilité Microsoft Information Protection n’a été définie dans l’organisation. De plus, pour pouvoir être utilisée, une étiquette doit faire partie d’une stratégie publiée. [Apprenez-en davantage sur les étiquettes de sensibilité](https://docs.microsoft.com/Office365/SecurityCompliance/sensitivity-labels). Vous pouvez également visiter le [Centre de sécurité et de conformité Microsoft](https://sip.protection.office.com/sensitivity?flight=EnableMIPLabels) pour savoir comment définir des étiquettes et publier des stratégies pour votre organisation.

## <a name="licensing"></a>Licensing

* Pour voir ou appliquer des étiquettes Microsoft Information Protection dans Power BI, les utilisateurs doivent disposer d’une licence Azure Information Protection Premium P1 ou Premium P2. Vous pouvez acheter Microsoft Azure Information Protection en autonome ou par le biais de l’une des suites de licences Microsoft. Pour plus d’informations, consultez les [tarifs Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection/).
* Les utilisateurs qui doivent appliquer des étiquettes sur des ressources Power BI doivent disposer d’une licence Power BI Pro.


## <a name="next-steps"></a>Étapes suivantes

L’objectif de cet article était d’expliquer comment activer les étiquettes de sensibilité des données dans Power BI. Les articles suivants fournissent plus de détails sur la protection des données dans Power BI. 

* [Vue d’ensemble de la protection des données dans Power BI](service-security-data-protection-overview.md)
* [Appliquer des étiquettes de sensibilité des données dans Power BI](../designer/service-security-apply-data-sensitivity-labels.md)
* [Utilisation de contrôles Microsoft Cloud App Security dans Power BI](service-security-using-microsoft-cloud-app-security-controls.md)