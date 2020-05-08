---
ms.openlocfilehash: 8dc488a47ac2b5b4e7980b7404b2722b1120b6ab
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/05/2020
ms.locfileid: "77464377"
---
## <a name="validate-the-roles-within-power-bi-desktop"></a>Valider les rôles dans Power BI Desktop
Après avoir créé vos rôles, vous pouvez tester les résultats de ces rôles dans Power BI Desktop.

1. Sous l’onglet **Modélisation**, sélectionnez **Afficher comme rôles**. 

    ![Sélectionner Afficher comme rôles](./media/rls-desktop-view-as-roles/powerbi-desktop-rls-view-as-roles.png)

    Dans la fenêtre **Afficher comme rôles** qui s’ouvre, vous voyez les rôles que vous avez créés.

    ![Fenêtre Afficher comme rôles](./media/rls-desktop-view-as-roles/powerbi-desktop-rls-view-as-roles-dialog.png)

3. Sélectionnez un rôle que vous avez créé, puis **OK** pour l’appliquer. 

   Le rapport affiche les données pertinentes pour ce rôle.

4. Vous pouvez également sélectionner **Autre utilisateur** et indiquer un utilisateur spécifique. 

    ![Sélectionner Autre utilisateur](./media/rls-desktop-view-as-roles/powerbi-desktop-rls-other-user.png)

   Il est préférable de fournir le nom d’utilisateur principal (UPN), celui-ci étant utilisé par le service Power BI et Power BI Report Server.

   Dans Power BI Desktop, **Autre utilisateur** montre des résultats différents uniquement si vous utilisez la sécurité dynamique basée sur vos expressions DAX. 

5. Sélectionnez **OK**. 

   Le rapport est affiché en fonction de ce que cet utilisateur peut voir.



