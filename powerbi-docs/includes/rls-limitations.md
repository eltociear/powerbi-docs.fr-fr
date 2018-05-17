## <a name="limitations"></a>Limites
Voici une liste des limites actuelles pour la sécurité au niveau des lignes sur les modèles cloud.

* Si vous aviez des rôles et des règles définis dans le service Power BI, vous devez les recréer dans Power BI Desktop.
* Vous pouvez définir la sécurité au niveau des lignes uniquement sur les jeux de données créés à l’aide du client Power BI Desktop. Pour activer la sécurité au niveau des lignes pour les jeux de données créés avec Excel, vous devez d’abord convertir vos fichiers au format PBIX. [En savoir plus](../desktop-import-excel-workbooks.md)
* Seules les connexions ETL et DirectQuery sont prises en charge. Les connexions actives à Analysis Services sont gérées dans le modèle local.
* Le moteur Questions et réponses et Cortana ne sont pour l’instant pas pris en charge avec la sécurité au niveau des lignes. La zone d’entrée de Q&R n’est pas disponible pour les tableaux de bord si la sécurité au niveau des lignes est configurée sur tous les modèles. Cela est prévu, mais aucune date n’est disponible pour l’instant.
* Le partage externe n’est actuellement pas pris en charge avec les jeux de données qui utilisent la sécurité au niveau des lignes.
* Pour un modèle donné, vous pouvez attribuer jusqu’à 1 000 principaux Azure AD (c’est-à-dire des utilisateurs individuels ou des groupes de sécurité) aux rôles de sécurité. Pour attribuer un grand nombre d’utilisateurs à des rôles, préférez les groupes de sécurité aux utilisateurs individuels.

## <a name="known-issues"></a>Problèmes connus
Il existe un problème connu : un message d’erreur s’affiche quand vous tentez de publier à partir de Power BI Desktop un élément publié précédemment. Le scénario est le suivant.

1. Anne possède un jeu de données publié sur le service Power BI et a configuré la sécurité au niveau des lignes.
2. Anna met à jour le rapport dans Power BI Desktop et le publie une nouvelle fois.
3. Anna reçoit une erreur.

**Solution de contournement :** publiez à nouveau le fichier Power BI Desktop à partir du service Power BI jusqu'à ce que ce problème soit résolu. Pour cela, sélectionnez **Obtenir des données** > **Fichiers**. 

