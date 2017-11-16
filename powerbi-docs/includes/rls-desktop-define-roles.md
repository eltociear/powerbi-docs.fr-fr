## <a name="define-roles-and-rules-within-power-bi-desktop"></a>Définir les rôles et les règles dans Power BI Desktop
Vous pouvez définir des rôles et des règles dans Power BI Desktop. Lorsque vous publiez sur Power BI, les définitions de rôles sont elles aussi publiées.

Si vous souhaitez utiliser la sécurité dynamique, vous devez activer dans la version préliminaire le filtrage croisé dans les deux directions pour DirectQuery. Ceci permet d’appliquer un filtrage croisé et d’appliquer le filtre de sécurité dans les deux sens.

![](./media/rls-desktop-define-roles/powerbi-desktop-preview-bi-directional-directquery.png)

Pour définir les rôles de sécurité, vous pouvez procéder comme suit.

1. Importez les données dans votre rapport Power BI Desktop ou configurez une connexion DirectQuery.
   
   > [!NOTE]
   > Vous ne pouvez pas définir les rôles Power BI Desktop pour les connexions actives Analysis Services. Vous devez le faire dans le modèle Analysis Services.
   > 
   > 
2. Sélectionnez l’onglet **Modélisation**.
3. Sélectionnez **Gérer les rôles**.
   
   ![](./media/rls-desktop-define-roles/powerbi-desktop-security.png)
4. Sélectionnez **Créer**.
   
   ![](./media/rls-desktop-define-roles/powerbi-desktop-security-create-role.png)
5. Donnez un nom au rôle. 
6. Sélectionnez la table à laquelle vous souhaitez appliquer une règle DAX.
7. Entrez les expressions DAX. Cette expression doit renvoyer vrai ou faux. Par exemple : [ID d’entité] = « Valeur ».
   
   > [!NOTE]
   > Vous pouvez utiliser *username()* dans cette expression. N’oubliez pas que *username()* est au format *DOMAINE\nom_utilisateur* dans Power BI Desktop. Dans le service Power BI, il est au format UPN de l’utilisateur. Vous pouvez également utiliser *userprincipalname()*, qui renvoie systématiquement l’utilisateur au format de son nom d’utilisateur principal.
   > 
   > 
   
   ![](./media/rls-desktop-define-roles/powerbi-desktop-security-create-rule.png)
8. Après avoir créé l’expression DAX, vous pouvez activer la case à cocher au-dessus de la zone d’expression pour valider l’expression.
   
   ![](./media/rls-desktop-define-roles/powerbi-desktop-security-validate-dax.png)
9. Sélectionnez **Enregistrer**.

Vous ne pouvez pas affecter d’utilisateurs à un rôle au sein de Power BI Desktop. Cette opération se fait dans le service Power BI. Dans Power BI Desktop, vous pouvez activer la sécurité dynamique en utilisant les fonctions DAX *username()* ou *userprincipalname()* et en configurant les relations appropriées.

