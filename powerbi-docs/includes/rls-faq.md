## <a name="faq"></a>FORUM AUX QUESTIONS
**Question :** Que se passe-t-il si j’ai précédemment créé des rôles/règles pour un jeu de données dans le service Power BI ? Continuent-ils de fonctionner si je ne fais rien ?  
**Réponse :** Non. Les éléments visuels ne sont pas rendus correctement. Vous devez recréer les rôles/règles dans Power BI Desktop, puis les publier sur le service Power BI.

**Question :** Puis-je créer ces rôles pour des sources de données Analysis Services ?  
**Réponse :** Oui si vous avez importé les données dans Power BI Desktop. Si vous utilisez une connexion active, vous n’êtes pas en mesure de configurer la sécurité au niveau des lignes (RLS) au sein du service Power BI. Celle-ci se définit localement dans le modèle Analysis Services.

**Question :** Puis-je utiliser la sécurité au niveau des lignes pour limiter les colonnes ou les mesures accessibles par mes utilisateurs ?  
**Réponse :** non. Si un utilisateur a accès à une ligne particulière de données, il peut voir toutes les colonnes de données pour cette ligne.

**Question :** La sécurité au niveau des lignes m’autorise-t-elle à masquer les données détaillées tout en accédant aux données résumées dans les visuels ?  
**Réponse :** Non, vous sécurisez les lignes de données individuelles, mais les utilisateurs peuvent toujours voir les détails ou les données résumées.

