---
ms.openlocfilehash: eb7cba03daee47f6772fc46be50419731b41765e
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "61193841"
---
## <a name="validate-the-roles-within-power-bi-desktop"></a>Valider les rôles dans Power BI Desktop
Après avoir créé vos rôles, vous pouvez tester les résultats de ces rôles dans Power BI Desktop.

1. Sélectionnez **Afficher comme rôles**. 

    ![](./media/rls-desktop-view-as-roles/powerbi-desktop-rls-view-as-roles.png)

    Dans **Afficher comme rôles**, vous voyez les rôles que vous avez créés.

    ![](./media/rls-desktop-view-as-roles/powerbi-desktop-rls-view-as-roles-dialog.png)

3. Sélectionnez un rôle que vous avez créé, puis **OK** pour appliquer ce rôle. Le rapport affiche les données pertinentes pour ce rôle. 

4. Vous pouvez également sélectionner **Autre utilisateur** et indiquer un utilisateur spécifique. Il est préférable de fournir le nom d’utilisateur principal (UPN), celui-ci étant utilisé par le service Power BI et Power BI Report Server.

    ![](./media/rls-desktop-view-as-roles/powerbi-desktop-rls-other-user.png)

1. Sélectionnez **OK** pour afficher le rapport en fonction de ce que cet utilisateur peut voir. 

Dans Power BI Desktop, **Autre utilisateur** affiche des résultats différents uniquement si vous utilisez la sécurité dynamique basée sur vos expressions DAX. 

