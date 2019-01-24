---
ms.openlocfilehash: 0ef0f2e250c61f11cc6418635a8e132242201072
ms.sourcegitcommit: 2c49a7cee9c77f46830ddfa59fdedbf30186d389
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54488968"
---
## <a name="validate-the-roles-within-power-bi-desktop"></a>Valider les rôles dans Power BI Desktop
Après avoir créé vos rôles, vous pouvez tester les résultats de ces rôles dans Power BI Desktop.

1. Sélectionnez **Afficher comme rôles**. 

    ![](./media/rls-desktop-view-as-roles/powerbi-desktop-rls-view-as-roles.png)

    Dans **Afficher comme rôles**, vous voyez les rôles que vous avez créés.

    ![](./media/rls-desktop-view-as-roles/powerbi-desktop-rls-view-as-roles-dialog.png)

3. Sélectionnez un rôle que vous avez créé, puis  **OK** pour appliquer ce rôle. Le rapport affiche les données pertinentes pour ce rôle. 

4. Vous pouvez également sélectionner **Autre utilisateur** et indiquer un utilisateur spécifique. Il est préférable de fournir le nom d’utilisateur principal (UPN), celui-ci étant utilisé par le service Power BI et Power BI Report Server.

    ![](./media/rls-desktop-view-as-roles/powerbi-desktop-rls-other-user.png)

1. Sélectionnez  **OK** pour afficher le rapport en fonction de ce que cet utilisateur peut voir. 

Dans Power BI Desktop, **Autre utilisateur** affiche des résultats différents uniquement si vous utilisez la sécurité dynamique basée sur vos expressions DAX. 

