---
title: Base de référence de la sécurité Azure pour Power BI
description: La base de référence de la sécurité Power BI fournit des procédures et des ressources pour l’implémentation des recommandations de sécurité spécifiées dans le benchmark de sécurité Azure.
author: mbaldwin
ms.author: margoc
ms.service: powerbi
ms.subservice: pbi-security
ms.topic: conceptual
ms.date: 11/20/2020
ms.custom: subject-security-benchmark
ms.openlocfilehash: 9e7aefba7a2e47fbf5249feaab3ac56057ac867c
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2020
ms.locfileid: "96386260"
---
# <a name="azure-security-baseline-for-power-bi"></a>Base de référence de la sécurité Azure pour Power BI

Cette base de référence de la sécurité applique les instructions du [Benchmark de sécurité Azure version 2.0](https://docs.microsoft.com/azure/security/benchmarks/overview) à Power BI. Le benchmark de sécurité Azure fournit des recommandations sur la façon dont vous pouvez sécuriser vos solutions cloud sur Azure. Le contenu est regroupé selon les **contrôles de sécurité** définis par le Benchmark de sécurité Azure et les instructions associées applicables à Power BI. Les **contrôles** non applicables à Power BI ont été exclus.

Pour voir comment Power BI correspond intégralement au Benchmark de sécurité Azure, consultez le [fichier de correspondance complet de la base de référence de la sécurité Power BI](https://github.com/MicrosoftDocs/SecurityBenchmarks/tree/master/Azure%20Offer%20Security%20Baselines).

## <a name="network-security"></a>Sécurité réseau

*Pour plus d’informations, consultez [Benchmark de sécurité Azure : sécurité réseau](/azure/security/benchmarks/security-controls-v2-network-security).*

### <a name="ns-3-establish-private-network-access-to-azure-services"></a>NS-3 : Établir un accès réseau privé aux services Azure

**Instructions** : Power BI prend en charge la connexion de votre locataire Power BI à un point de terminaison de liaison privée et la désactivation de l’accès Internet public.

- [Liaisons privées pour accéder à Power BI](https://docs.microsoft.com/power-bi/admin/service-security-private-links)

**Supervision d’Azure Security Center** : Non applicable

**Responsabilité** : Partagé

## <a name="identity-management"></a>Gestion des identités

*Pour plus d’informations, consultez [Benchmark de sécurité Azure : Gestion des identités](/azure/security/benchmarks/security-controls-v2-identity-management).*

### <a name="im-1-standardize-azure-active-directory-as-the-central-identity-and-authentication-system"></a>IM-1 : Normaliser Azure Active Directory comme système d’authentification et d’identité central

**Instructions** : Power BI est intégré à Azure Active Directory (Azure AD), qui est le service de gestion des identités et des accès par défaut d’Azure. Vous devez vous aligner sur Azure AD pour la gouvernance de la gestion des identités et des accès dans votre organisation.

La sécurisation d’Azure AD doit être d’une priorité élevée dans les pratiques de sécurité cloud de votre organisation. Azure AD fournit un score d'identité sécurisée pour vous aider à évaluer la sécurité des identités par rapport aux recommandations de Microsoft en matière de meilleures pratiques. Utilisez le score pour évaluer avec précision votre configuration par rapport aux meilleures pratiques recommandées et apporter des améliorations à votre posture de sécurité.

Remarque : Azure AD prend en charge les identités externes qui permettent aux utilisateurs sans compte Microsoft de se connecter à leurs applications et ressources avec leur identité externe.

- [Locataires dans Azure Active Directory](https://docs.microsoft.com/azure/active-directory/develop/single-and-multi-tenant-apps)

- [Création et configuration d’une instance Azure AD](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-access-create-new-tenant)

- [Utilisez des fournisseurs d'identité externes pour l’application](https://docs.microsoft.com/azure/active-directory/b2b/identity-providers)

- [Qu’est-ce que le degré de sécurisation Identity Secure Score dans Azure Active Directory](https://docs.microsoft.com/azure/active-directory/fundamentals/identity-secure-score)

**Supervision d’Azure Security Center** : Non applicable

**Responsabilité** : Customer

### <a name="im-2-manage-application-identities-securely-and-automatically"></a>IM-2 : Gérer les identités d’application de façon sécurisée et automatique

**Instructions** : Power BI et Power BI Embedded prennent en charge l’utilisation des principaux de service. Stockez les informations d’identification du principal de service utilisées pour le chiffrement ou l’accès à Power BI dans un coffre de clés, affectez des stratégies d’accès appropriées au coffre et passez régulièrement en revue les autorisations d’accès.

Automatiser les tâches d’espace de travail Premium et de jeu de données avec des principaux de service https://docs.microsoft.com/power-bi/admin/service-premium-service-principal

**Supervision d’Azure Security Center** : Non applicable

**Responsabilité** : Customer

### <a name="im-3-use-azure-ad-single-sign-on-sso-for-application-access"></a>IM-3 : Utiliser l’authentification unique Azure AD pour l’accès aux applications

**Instructions** : Power BI utilise Azure Active Directory pour fournir une gestion des identités et des accès aux ressources Azure, aux applications cloud et aux applications locales. Cela inclut les identités d’entreprise, comme les employés, ainsi que les identités externes, comme les partenaires et les fournisseurs. Cela permet à l’authentification unique de gérer et sécuriser l’accès aux données et ressources de votre organisation localement et dans le cloud. Connectez l’ensemble de vos utilisateurs, applications et appareils à Azure AD pour un accès transparent et sécurisé, ainsi qu’une visibilité et un contrôle accrus.

- [Comprendre l’authentification unique des applications avec Azure AD](https://docs.microsoft.com/azure/active-directory/manage-apps/what-is-single-sign-on)

**Supervision d’Azure Security Center** : Non applicable

**Responsabilité** : Customer

### <a name="im-4-use-strong-authentication-controls-for-all-azure-active-directory-based-access"></a>IM-4 : Utiliser des contrôles d’authentification renforcés pour tous les accès basés sur Azure Active Directory

**Instructions** : Power BI est intégré à Azure AD, qui prend en charge des contrôles d’authentification forts via l’authentification multifacteur (MFA) et des méthodes sans mot de passe fort.
- Authentification multifacteur : activez l’authentification multifacteur Azure AD et suivez les recommandations relatives à la gestion des identités et des accès d’Azure Security Center pour les bonnes pratiques de configuration de votre authentification multifacteur. L’authentification multifacteur peut être appliquée à tous les utilisateurs, à des utilisateurs sélectionnés ou au niveau de chaque utilisateur en fonction des conditions de connexion et des facteurs de risque.
- Authentification sans mot de passe : trois options d’authentification par mot de passe sont disponibles : Windows Hello Entreprise, l’application Microsoft Authenticator et des méthodes d’authentification locales, comme des cartes à puce.

Pour les administrateurs et les utilisateurs avec privilèges, vérifiez que le niveau d’authentification forte le plus élevé est utilisé, puis déployez la stratégie d’authentification forte appropriée pour les autres utilisateurs.

Remarque : L’authentification multifacteur peut être appliquée seulement pour les comptes d’utilisateur activés dans Azure AD. Les principaux de service Power BI ne prennent pas en charge l’utilisation de l’authentification multifacteur.

- [Guide pratique pour activer l’authentification MFA dans Azure](https://docs.microsoft.com/azure/active-directory/authentication/howto-mfa-getstarted)

- [Introduction aux options d’authentification sans mot de passe pour Azure Active Directory](https://docs.microsoft.com/azure/active-directory/authentication/concept-authentication-passwordless)

**Supervision d’Azure Security Center** : Non applicable

**Responsabilité** : Customer

### <a name="im-5-monitor-and-alert-on-account-anomalies"></a>IM-5 : Surveiller et alerter en cas d’anomalies de compte

**Instructions** : Définissez des stratégies de détection des anomalies dans Microsoft Cloud App Security qui peuvent être délimitées de façon indépendante, afin qu’elles s’appliquent seulement aux utilisateurs et aux groupes que vous voulez inclure. Ces stratégies de détection des anomalies peuvent aider à détecter et à surveiller les anomalies de comportement liées aux utilisateurs qui accèdent à Power BI et qui l’utilisent.

- [Utilisation de contrôles Microsoft Cloud App Security dans Power BI](https://docs.microsoft.com/power-bi/admin/service-security-using-microsoft-cloud-app-security-controls)

**Supervision d’Azure Security Center** : Non applicable

**Responsabilité** : Customer

### <a name="im-6-restrict-azure-resource-access-based-on-conditions"></a>IM-6 : Restreindre l’accès aux ressources Azure en fonction des conditions

**Instructions** : Power BI prend en charge l’accès conditionnel Azure AD pour un contrôle d’accès plus précis en fonction des conditions définies par l’utilisateur, comme le fait que les connexions utilisateur depuis certaines plages d’adresses IP doivent utiliser l’authentification multifacteur pour la connexion. Une stratégie de gestion granulaire des sessions d’authentification peut également être utilisée dans différents cas d’usage.

- [Présentation de l’accès conditionnel Azure](https://docs.microsoft.com/azure/active-directory/conditional-access/overview)

- [Stratégies d’accès conditionnel courantes](https://docs.microsoft.com/azure/active-directory/conditional-access/concept-conditional-access-policy-common)

- [Configurer la gestion des sessions d’authentification avec l’accès conditionnel](https://docs.microsoft.com/azure/active-directory/conditional-access/howto-conditional-access-session-lifetime)

- [Utilisation de contrôles Microsoft Cloud App Security dans Power BI](https://docs.microsoft.com/power-bi/admin/service-security-using-microsoft-cloud-app-security-controls)

**Supervision d’Azure Security Center** : Non applicable

**Responsabilité** : Customer

### <a name="im-7-eliminate-unintended-credential-exposure"></a>IM-7 : Éliminer l’exposition involontaire des informations d’identification

**Instructions** : Pour les applications Power BI Embedded, il est recommandé d’implémenter le scanneur d’informations d’identification pour identifier les informations d’identification présentes dans votre code. Le moteur d’analyse des informations d’identification encourage également le déplacement des informations d’identification découvertes vers des emplacements plus sécurisés, tels qu’Azure Key Vault.

Stockez les clés de chiffrement ou les informations d’identification du principal de service utilisées pour le chiffrement ou l’accès à Power BI dans un coffre de clés, affectez des stratégies d’accès appropriées au coffre et passez régulièrement en revue les autorisations d’accès.
 
Pour GitHub, vous pouvez utiliser la fonctionnalité native d’analyse de secret pour identifier les informations d’identification ou d’autres formes de secrets dans le code.

- [Apporter vos propres clés de chiffrement pour Power BI](https://docs.microsoft.com/power-bi/admin/service-encryption-byok)

 
Comment configurer les informations d’identification
- [Scanneur](https://secdevtools.azurewebsites.net/helpcredscan.html) 

- [Analyse du secret GitHub](https://docs.github.com/github/administering-a-repository/about-secret-scanning)

**Supervision d’Azure Security Center** : Non applicable

**Responsabilité** : Partagé

## <a name="privileged-access"></a>Accès privilégié

*Pour plus d’informations, consultez [Benchmark de sécurité Azure : Accès privilégié](/azure/security/benchmarks/security-controls-v2-privileged-access).*

### <a name="pa-1-protect-and-limit-highly-privileged-users"></a>PA-1 : Protéger et limiter les utilisateurs disposant de privilèges élevés

**Instructions** : Pour réduire les risques et suivre le principe du moindre privilège, il est recommandé de réserver à un petit nombre de personnes l’appartenance au groupe des administrateurs Power BI. Les utilisateurs disposant de ces autorisations privilégiées peuvent potentiellement accéder à toutes les fonctionnalités de gestion de l’organisation et les modifier. Les administrateurs généraux, via Microsoft 365 ou Azure Active Directory, ont implicitement des droits d’administrateur également dans le service Power BI.

Power BI a les comptes disposant de privilèges élevés suivants :
- Administrateur général
- Administrateur de la facturation
- Administrateur de licences
- Administrateur des utilisateurs
- Administrateur Power BI
- Administrateur de capacité Power BI Premium
- Administrateur de capacité Power BI Embedded

Power BI prend en charge les stratégies de session dans Azure AD pour activer les stratégies d’accès conditionnel et router les sessions utilisées dans Power BI via le service Cloud App Security.

Activez l’accès privilégié juste-à-temps (JIT) pour les comptes d’administrateur Power BI en utilisant Privileged Access Management de Microsoft 365.

- [Rôles d’administrateur liés à Power BI](https://docs.microsoft.com/power-bi/admin/service-admin-administering-power-bi-in-your-organization#administrator-roles-related-to-power-bi)

- [Privileged Access Management de Microsoft 365](https://docs.microsoft.com/microsoft-365/compliance/privileged-access-management-overview?view=o365-worldwide&amp;preserve-view=true)

- [Contrôles Cloud App Security dans Power BI](https://docs.microsoft.com/power-bi/admin/service-security-using-microsoft-cloud-app-security-controls)

**Supervision d’Azure Security Center** : Non applicable

**Responsabilité** : Customer

### <a name="pa-2-restrict-administrative-access-to-business-critical-systems"></a>PA-2 : Limiter l’accès administratif aux systèmes critiques de l’entreprise

**Instructions** : Limitez le nombre de comptes ou de rôles à privilèges élevés avec un accès élevé à Power BI.

Vous pouvez activer l’accès privilégié juste-à-temps (JIT) en utilisant les instructions de Privileged Access Management de Microsoft 365 disponibles [ici](https://docs.microsoft.com/microsoft-365/compliance/privileged-access-management-overview?view=o365-worldwide&amp;preserve-view=true).

Pour plus d’informations, consultez la page 183 du document sur le déploiement de Power BI en entreprise disponible[ici](https://aka.ms/PBIEnterpriseDeploymentWP).

**Supervision d’Azure Security Center** : Non applicable

**Responsabilité** : Customer

### <a name="pa-3-review-and-reconcile-user-access-regularly"></a>PA-3 : Examiner et rapprocher régulièrement les accès utilisateur

**Instructions** : En tant qu’administrateur de service Power BI, vous pouvez analyser l’utilisation de toutes les ressources Power BI au niveau du locataire à l’aide de rapports personnalisés basés sur le journal d’activité de Power BI. Vous pouvez télécharger les activités à l’aide d’une API REST ou d’une applet de commande PowerShell. Vous pouvez aussi filtrer les données d’activité par plage de dates, par utilisateur et par type d’activité.

Vous devez remplir ces conditions requises pour accéder au journal d’activité de Power BI :
- Être administrateur général ou administrateur de service Power BI.
- Avoir installé les [applets de commande de gestion Power BI](https://www.powershellgallery.com/packages/MicrosoftPowerBIMgmt) localement ou utiliser les applets de commande de gestion Power BI dans Azure Cloud Shell.

Une fois ces conditions satisfaites, vous pouvez appliquer les instructions ci-dessous pour suivre l’activité des utilisateurs dans Power BI :

- [Suivre l’activité des utilisateurs dans Power BI](https://docs.microsoft.com/power-bi/admin/service-admin-auditing)

**Supervision d’Azure Security Center** : Non applicable

**Responsabilité** : Customer

### <a name="pa-4-set-up-emergency-access-in-azure-ad"></a>PA-4 : Configurer l’accès d’urgence dans Azure AD

**Instructions** : Power BI est intégré à Azure Active Directory et à Microsoft 365 pour la gestion de ses ressources. Pour empêcher le verrouillage accidentel de votre locataire Microsoft 365 ou de votre organisation Azure AD, configurez un compte d’accès d’urgence pour l’accès dès lors que les comptes d’administration normaux ne peuvent pas être utilisés. Les comptes d’accès d’urgence sont généralement hautement privilégiés et ne doivent pas être attribués à des personnes spécifiques. Les comptes d’accès d’urgence sont limités à des cas d’urgence ou à des scénarios « de secours » où il est impossible d’utiliser des comptes d’administration normaux.

Vous devez vous assurer que les informations d’identification (telles que le mot de passe, le certificat ou la carte à puce) des comptes d’accès d’urgence restent sécurisées et connues des seules personnes autorisées à les utiliser en cas d’urgence.

- [Gérer des comptes d’accès d’urgence dans Azure AD](https://docs.microsoft.com/azure/active-directory/users-groups-roles/directory-emergency-access)

- [Protéger vos comptes Microsoft 365](https://docs.microsoft.com/microsoft-365/campaigns/m365-campaigns-protect-admin-accounts)

**Supervision d’Azure Security Center** : Non applicable

**Responsabilité** : Customer

### <a name="pa-6-use-privileged-access-workstations"></a>PA-6 : Utiliser des stations de travail d’accès privilégié

**Conseils** : Les stations de travail sécurisées et isolées sont extrêmement importantes pour la sécurité des rôles sensibles comme les administrateurs, développeurs et opérateurs de service critique. Utilisez des stations de travail utilisateur hautement sécurisées et/ou Azure Bastion pour les tâches d’administration liées à la gestion de Power BI. Utilisez Azure Active Directory, Microsoft Defender Advanced Threat Protection (MDATP) et/ou Microsoft Intune pour déployer une station de travail utilisateur sécurisée et gérée pour les tâches d’administration. Les stations de travail sécurisées peuvent être gérées de manière centralisée pour appliquer une configuration sécurisée, notamment une authentification forte, des lignes de base logicielles et matérielles et un accès réseau et logique restreint.

Comprendre l’accès privilégié
- [Stations de travail](https://docs.microsoft.com/azure/active-directory/devices/concept-azure-managed-workstation)

- [Déployer une station de travail d’accès privilégié](https://docs.microsoft.com/azure/active-directory/devices/howto-azure-managed-workstation)

**Supervision d’Azure Security Center** : Non applicable

**Responsabilité** : Customer

## <a name="data-protection"></a>Protection des données

*Pour plus d’informations, consultez [Benchmark de sécurité Azure : protection des données](/azure/security/benchmarks/security-controls-v2-data-protection).*

### <a name="dp-1-discovery-classify-and-label-sensitive-data"></a>DP-1 : Découvrir, classifier et étiqueter des données sensibles

**Instructions** : Utilisez des étiquettes de confidentialité Microsoft Information Protection sur vos rapports, tableaux de bord, jeux de données et dataflows pour protéger votre contenu sensible contre les accès non autorisés aux données et contre les fuites de données.

Utilisez des étiquettes de confidentialité Microsoft Information Protection pour classifier et étiqueter vos rapports, tableaux de bord, jeux de données et dataflows dans le service Power BI, et pour protéger votre contenu sensible contre les accès non autorisés aux données et les fuites de données quand du contenu est exporté depuis le service Power BI vers des fichiers Excel, PowerPoint et PDF.

- [Guide pratique pour appliquer des étiquettes de sensibilité dans Power BI](https://docs.microsoft.com/power-bi/admin/service-security-apply-data-sensitivity-labels)

**Supervision d’Azure Security Center** : Non applicable

**Responsabilité** : Customer

### <a name="dp-2-protect-sensitive-data"></a>DP-2 : Protection des données sensibles

**Instructions** : Power BI s’intègre aux étiquettes de confidentialité Microsoft Information Protection pour la protection des données sensibles. Pour plus d’informations, consultez [Étiquettes de confidentialité Microsoft Information Protection dans Power BI](https://docs.microsoft.com/power-bi/admin/service-security-sensitivity-label-overview)

Power BI permet aux utilisateurs du service d’apporter leur propre clé pour protéger les données au repos. Pour plus d’informations, consultez [Apporter vos propres clés de chiffrement pour Power BI](https://docs.microsoft.com/power-bi/admin/service-encryption-byok).

Les clients ont la possibilité de conserver des sources de données localement et de tirer parti de Direct Query ou de Live Connect avec une passerelle de données locale pour réduire l’exposition des données au service cloud. Pour plus d’informations, consultez [Qu’est-ce qu’une passerelle de données locale ?](https://docs.microsoft.com/data-integration/gateway/service-gateway-onprem)

Power BI prend en charge la sécurité au niveau des lignes. Pour plus d’informations, consultez [Sécurité au niveau des lignes avec Power BI](https://docs.microsoft.com/power-bi/admin/service-admin-rls). Notez que la sécurité au niveau des lignes peut être appliquée même à des sources Direct Query, auquel cas le fichier PBIX agit comme proxy d’activation de la sécurité.

**Supervision d’Azure Security Center** : Non applicable

**Responsabilité** : Customer

### <a name="dp-3-monitor-for-unauthorized-transfer-of-sensitive-data"></a>DP-3 : Détection des transferts non autorisés de données sensibles

**Instructions** : Ce contrôle peut être partiellement effectué en utilisant la prise en charge de Microsoft Cloud App Security pour Power BI.

En utilisant Cloud App Security avec Power BI, vous pouvez protéger vos rapports, données et services Power BI contre les fuites non intentionnelles ou les violations. Cloud App Security vous permet de créer des stratégies d’accès conditionnel pour les données de votre organisation, à l’aide de contrôles de session en temps réel dans Azure Active Directory (Azure AD) qui contribuent de garantir la sécurité de vos analytiques Power BI. Une ces stratégies définies, les administrateurs peuvent superviser l’accès et l’activité des utilisateurs, effectuer une analyse des risques en temps réel et définir des contrôles spécifiques aux étiquettes.

Utilisation
- [Contrôles Microsoft Cloud App Security dans Power BI](https://docs.microsoft.com/power-bi/admin/service-security-using-microsoft-cloud-app-security-controls)

**Supervision d’Azure Security Center** : Non applicable

**Responsabilité** : Customer

### <a name="dp-4-encrypt-sensitive-information-in-transit"></a>DP-4 : Chiffrement des informations sensibles en transit

**Instructions** : Veillez à ce que, pour le trafic HTTP, les clients et les sources de données qui se connectent à vos ressources Power BI puissent négocier TLS v1.2 ou ultérieur.

- [Mise en œuvre de l’utilisation de la version TLS](https://docs.microsoft.com/power-bi/admin/service-admin-power-bi-security#enforcing-tls-version-usage)

- [Informations sur la sécurité TLS](https://docs.microsoft.com/security/engineering/solving-tls1-problem)

**Supervision d’Azure Security Center** : Non applicable

**Responsabilité** : Customer

### <a name="dp-5-encrypt-sensitive-data-at-rest"></a>DP-5 : Chiffrement des données sensibles au repos

**Instructions** : Power BI chiffre les données au repos et in-process. Par défaut, Power BI utilise des clés managées par Microsoft pour chiffrer vos données. Les organisations peuvent choisir d’utiliser leurs propres clés pour le chiffrement du contenu utilisateur au repos sur Power BI, des images de rapport vers les jeux de données importés dans les capacités Premium.

- [Utiliser BYOK dans Power BI](https://docs.microsoft.com/power-bi/admin/service-encryption-byok)

**Supervision d’Azure Security Center** : Non applicable

**Responsabilité** : Partagé

## <a name="asset-management"></a>Gestion des ressources

*Pour plus d’informations, consultez [Benchmark de sécurité Azure : Gestion des ressources](/azure/security/benchmarks/security-controls-v2-asset-management).*

### <a name="am-1-ensure-security-team-has-visibility-into-risks-for-assets"></a>AM-1 : S’assurer que l’équipe de sécurité a une visibilité sur les risques pour les ressources

**Instructions** : Utilisez Azure Sentinel avec vos journaux d’audit Office Power BI afin de donner à votre équipe de sécurité une visibilité sur les risques pour vos ressources Power BI.

- [Connecter des journaux Office 365 à Azure Sentinel](https://docs.microsoft.com/azure/sentinel/connect-office-365)

**Supervision d’Azure Security Center** : Non applicable

**Responsabilité** : Customer

### <a name="am-2-ensure-security-team-has-access-to-asset-inventory-and-metadata"></a>AM-2 : S’assurer que l’équipe de sécurité a accès à l’inventaire des ressources et aux métadonnées

**Instructions** : Veillez à ce que les équipes de sécurité aient accès à un inventaire continuellement mis à jour des ressources Power BI Embedded. Les équipes de sécurité ont souvent besoin de cet inventaire pour évaluer l’exposition potentielle de leur organisation à des risques émergents, et en tant qu’entrée pour des améliorations de sécurité continues. 

Azure Resource Graph peut rechercher et découvrir toutes les ressources Power BI Embedded dans vos abonnements.  

Organisez logiquement les ressources en fonction de la taxonomie de votre organisation à l’aide de balises, ainsi que d’autres métadonnées dans Azure (nom, description et catégorie).  

- [Procédure pour créer des requêtes avec l’Explorateur Azure Resource Graph](https://docs.microsoft.com/azure/governance/resource-graph/first-query-portal)

- [Guides de décision concernant le nommage et l’étiquetage des ressources](https://docs.microsoft.com/azure/cloud-adoption-framework/decision-guides/resource-tagging/?toc=/azure/azure-resource-manager/management/toc.json)

**Supervision d’Azure Security Center** : Non applicable

**Responsabilité** : Customer

### <a name="am-3-use-only-approved-azure-services"></a>AM-3 : Utiliser des services Azure approuvés uniquement

**Instructions** : Power BI prend en charge les déploiements basés sur Azure Resource Manager pour Power BI Embedded, et vous pouvez limiter le déploiement de ses ressources via Azure Policy en utilisant une définition de stratégie personnalisée.

Utilisez Azure Policy pour auditer et limiter les services que les utilisateurs peuvent approvisionner dans votre environnement. Utilisez Azure Resource Graph pour interroger et découvrir des ressources dans leurs abonnements. Vous pouvez également utiliser Azure Monitor pour créer des règles afin de déclencher des alertes lorsqu’un service non approuvé est détecté.

- [Guide pratique pour configurer et gérer Azure Policy](https://docs.microsoft.com/azure/governance/policy/tutorials/create-and-manage)

Comment refuser un type de ressource spécifique avec
- [Azure Policy](https://docs.microsoft.com/azure/governance/policy/samples/built-in-policies#general)

Comment créer des requêtes avec Azure
- [Explorateur Resource Graph](https://docs.microsoft.com/azure/governance/resource-graph/first-query-portal)

**Supervision d’Azure Security Center** : Non applicable

**Responsabilité** : Customer

## <a name="logging-and-threat-detection"></a>Journalisation et détection des menaces

*Pour plus d’informations, consultez [Benchmark de sécurité Azure : Journalisation et détection des menaces](/azure/security/benchmarks/security-controls-v2-logging-threat-protection).*

### <a name="lt-2-enable-threat-detection-for-azure-identity-and-access-management"></a>LT-2 : Activer la détection des menaces pour la gestion des identités et des accès Azure

**Instructions** : Transférez tous les journaux de Power BI à votre serveur SIEM, qui peut être utilisé pour configurer des détections de menaces personnalisées. En outre, utilisez des contrôles Microsoft Cloud App Security (MCAS) dans Power BI pour activer la détection d’anomalies en utilisant le guide disponible [ici](https://docs.microsoft.com/power-bi/admin/service-security-using-microsoft-cloud-app-security-controls).

- [Suivre les activités utilisateur dans Power BI](https://docs.microsoft.com/power-bi/admin/service-admin-auditing)

**Supervision d’Azure Security Center** : Non applicable

**Responsabilité** : Customer

### <a name="lt-3-enable-logging-for-azure-network-activities"></a>LT-3 : Activer la journalisation pour les activités réseau Azure

**Instructions** : Power BI est une offre SaaS complètement managée, et la configuration du réseau sous-jacent et la journalisation sont de la responsabilité de Microsoft. Pour les clients qui utilisent des liens privés, il est possible de configurer la journalisation et la supervision.

- [Journalisation et supervision Private Link](https://docs.microsoft.com/azure/private-link/private-link-overview#logging-and-monitoring)

**Supervision d’Azure Security Center** : Non applicable

**Responsabilité** : Partagé

### <a name="lt-4-enable-logging-for-azure-resources"></a>LT-4 : Activer la journalisation pour les ressources Azure

**Instructions** : Power BI propose deux options pour suivre l’activité utilisateur : Le journal d’activité de Power BI et le journal d’audit unifié. Ces journaux contiennent tous deux une copie complète des données d’audit de Power BI, mais ils ont plusieurs différences importantes qui sont résumées ci-dessous.
 
Journal d’audit unifié :

 
- Inclut les événements de SharePoint Online, Exchange Online, Dynamics 365 et d’autres services en plus des événements d’audit de Power BI.

 
- Seuls les utilisateurs ayant les autorisations Journaux d’audit ou Journaux d’audit en affichage seul, comme les administrateurs généraux et les auditeurs, ont accès à ce journal.

 
- Les administrateurs généraux et les auditeurs peuvent faire des recherches dans le journal d’audit unifié en utilisant le Centre de sécurité Microsoft 365 et le Centre de conformité Microsoft 365.

 
- Les administrateurs généraux et les auditeurs peuvent télécharger des entrées du journal d’audit en utilisant les API et les applets de commande de gestion de Microsoft 365.

 
- Conserve les données d’audit pendant 90 jours.

 
- Conserve les données d’audit même si le locataire est déplacé vers une autre région Azure.
 
Journal d’activité de Power BI :

 
- Inclut uniquement les événements d’audit de Power BI.

 
 
- Les administrateurs généraux et les administrateurs du service Power BI y ont accès.

 
- Il n’existe pas encore d’interface utilisateur permettant d’effectuer des recherches dans le journal d’activité.

 
- Les administrateurs généraux et les administrateurs du service Power BI peuvent télécharger des entrées du journal d’activité en utilisant une API REST Power BI et une applet de commande de gestion.

 
- Conserve les données d’activité pendant 30 jours.

 
- Ne conserve pas les données d’activité quand le client est déplacé vers une autre région Azure.

- [Données d’audit de Power BI](https://docs.microsoft.com/power-bi/admin/service-admin-auditing#operations-available-in-the-audit-and-activity-logs)

- [Journal d’activité de Power BI](https://docs.microsoft.com/power-bi/admin/service-admin-auditing#use-the-activity-log)

- [Journal d’audit de Power BI](https://docs.microsoft.com/power-bi/admin/service-admin-auditing#use-the-audit-log)

**Supervision d’Azure Security Center** : Non applicable

**Responsabilité** : Partagé

### <a name="lt-5-centralize-security-log-management-and-analysis"></a>LT-5 : Centraliser la gestion et l’analyse des journaux de sécurité

**Instructions** : Power BI centralise les journaux à deux endroits : le journal d’activité de Power BI et le journal d’audit unifié. Ces journaux contiennent tous deux une copie complète des données d’audit de Power BI, mais ils ont plusieurs différences importantes qui sont résumées ci-dessous.
 

Journal d’audit unifié :

- Inclut les événements de SharePoint Online, Exchange Online, Dynamics 365 et d’autres services en plus des événements d’audit de Power BI.

- Seuls les utilisateurs ayant des autorisations Journaux d’audit ou Journaux d’audit en affichage seul, comme les administrateurs généraux et les auditeurs, ont accès à ce journal.

- Les administrateurs généraux et les auditeurs peuvent faire des recherches dans le journal d’audit unifié à l’aide du Centre de sécurité Microsoft 365 et du Centre de conformité Microsoft 365.

- Les administrateurs généraux et les auditeurs peuvent télécharger des entrées du journal d’audit à l’aide d’API et d’applets de commande de gestion Microsoft 365.

- Conserve les données d’audit pendant 90 jours.

- Conserve les données d’audit, même si le locataire est déplacé vers une autre région Azure.

 

Journal d’activité de Power BI :

- Inclut uniquement les événements d’audit de Power BI.

- Les administrateurs généraux et les administrateurs de service Power BI ont accès à ce journal.

- Il n’existe pas encore d’interface utilisateur permettant d’effectuer des recherches dans le journal d’activité.

- Les administrateurs généraux et les administrateurs de service Power BI peuvent télécharger des entrées du journal d’activité à l’aide d’une API REST Power BI et d’une applet de commande de gestion.

- Conserve les données d’activité pendant 30 jours.

- Ne conserve pas les données d’activité lorsque le client est déplacé vers une autre région Azure.

- [Données d’audit de Power BI](https://docs.microsoft.com/power-bi/admin/service-admin-auditing#operations-available-in-the-audit-and-activity-logs)

- [Journal d’activité de Power BI](https://docs.microsoft.com/power-bi/admin/service-admin-auditing#use-the-activity-log)

- [Journal d’audit de Power BI](https://docs.microsoft.com/power-bi/admin/service-admin-auditing#use-the-audit-log)

**Supervision d’Azure Security Center** : Non applicable

**Responsabilité** : Customer

### <a name="lt-6-configure-log-storage-retention"></a>LT-6 : Configurer la rétention du stockage des journaux

**Instructions** : Configurez vos stratégies de conservation du stockage pour vos journaux d’audit Office en fonction de vos besoins en matière de conformité, de réglementation et métier.

- [Stratégies de conservation du journal d’audit Office](https://docs.microsoft.com/microsoft-365/compliance/audit-log-retention-policies)

**Supervision d’Azure Security Center** : Non applicable

**Responsabilité** : Customer

## <a name="incident-response"></a>Réponse aux incidents

*Pour plus d’informations, consultez [Benchmark de sécurité Azure : réponse aux incidents](/azure/security/benchmarks/security-controls-v2-incident-response).*

### <a name="ir-1-preparation--update-incident-response-process-for-azure"></a>IR-1 : Préparation – mettre à jour le processus de réponse aux incidents pour Azure

**Conseils** : Assurez-vous que votre organisation dispose de processus pour répondre aux incidents de sécurité, qu’elle a mis à jour ces processus pour Azure et qu’elle les exerce régulièrement pour garantir la préparation.

- [Implémenter la sécurité dans l’environnement de l’entreprise](https://docs.microsoft.com/azure/cloud-adoption-framework/security/security-top-10#4-process-update-incident-response-ir-processes-for-cloud)

- [Guide de référence sur les réponses aux incidents](https://docs.microsoft.com/microsoft-365/downloads/IR-Reference-Guide.pdf)

**Supervision d’Azure Security Center** : Non applicable

**Responsabilité** : Customer

### <a name="ir-2-preparation--setup-incident-notification"></a>IR-2 : Préparation – configurer la notification d’incident

**Conseils** : Configurez les coordonnées des personnes à contacter en cas d’incident de sécurité dans Azure Security Center. Microsoft utilisera ces coordonnées afin de vous contacter si le Microsoft Security Response Center (MSRC) découvre que vos données ont été consultées de manière illégale ou par un tiers non autorisé. Vous avez également la possibilité de personnaliser les alertes et les notifications d’incidents dans différents services Azure en fonction de vos besoins en matière de réponse aux incidents. 

- [Comment définir le contact de sécurité d’Azure Security Center](https://docs.microsoft.com/azure/security-center/security-center-provide-security-contact-details)

**Supervision d’Azure Security Center** : Non applicable

**Responsabilité** : Customer

### <a name="ir-3-detection-and-analysis--create-incidents-based-on-high-quality-alerts"></a>IR-3 : Détection et analyse – créer des incidents en fonction d’alertes de haute qualité

**Instructions** : Veillez à avoir un processus de création d’alertes de bonne qualité et de mesure de la qualité des alertes. Cela vous permet de tirer les leçons des incidents passés et de classer par ordre de priorité les alertes pour les analystes, afin qu’ils ne perdent pas de temps sur les faux positifs.

Surveillez les alertes liées à Power BI dans Microsoft Cloud App Security. Vous pouvez créer des alertes de bonne qualité en vous basant sur l’expérience des incidents passés, sur les sources validées par la communauté, et sur des outils conçus pour générer et nettoyer les alertes en fusionnant et en mettant en corrélation différentes sources de signaux.

- [Surveiller les alertes dans Cloud App Security](https://docs.microsoft.com/cloud-app-security/monitor-alerts)

**Supervision d’Azure Security Center** : Non applicable

**Responsabilité** : Customer

### <a name="ir-4-detection-and-analysis--investigate-an-incident"></a>IR-4 : Détection et analyse – enquêter sur un incident

**Conseils** : Créez un guide de réponse aux incidents pour votre organisation. Exécutez des exercices pour tester les fonctionnalités de réponse aux incidents de vos systèmes de façon régulière. Identifiez les points faibles et les lacunes, et révisez le plan en fonction des besoins.

Assurez-vous qu’il existe des plans de réponse aux incidents écrits qui définissent tous les rôles du personnel, ainsi que les phases de gestion des incidents, depuis la détection jusqu’à la revue une fois l’incident terminé.

- [Vue d’ensemble des incidents dans Protection Microsoft contre les menaces](https://docs.microsoft.com/microsoft-365/security/mtp/incidents-overview)

**Supervision d’Azure Security Center** : Non applicable

**Responsabilité** : Customer

### <a name="ir-5-detection-and-analysis--prioritize-incidents"></a>IR-5 : Détection et analyse – classer par ordre de priorité les incidents

**Conseils** : Donnez aux analystes le contexte sur lequel les incidents doivent se concentrer en premier lieu en fonction de la gravité de l’alerte et de la sensibilité des ressources. 

 
Protection Microsoft contre les menaces applique une analytique des corrélations, et regroupe toutes les alertes et recherches associées provenant de différents produits en un seul incident. Protection Microsoft contre les menaces déclenche également des alertes uniques sur les activités qui peuvent être identifiées seulement comme malveillantes en raison de la visibilité de bout en bout de Protection Microsoft contre les menaces sur tous les actifs et toute la suite de produits. En procédant ainsi, Protection Microsoft contre les menaces donne une représentation du scénario d’attaque le plus large, permettant à un analyste des opérations de sécurité de comprendre et de gérer les menaces complexes dans toute l’organisation.

- [Hiérarchiser les incidents dans Protection Microsoft contre les menaces](https://docs.microsoft.com/microsoft-365/security/mtp/incident-queue?view=o365-worldwide&amp;preserve-view=true)

**Supervision d’Azure Security Center** : Non applicable

**Responsabilité** : Customer

### <a name="ir-6-containment-eradication-and-recovery--automate-the-incident-handling"></a>IR-6 : Confinement, éradication et récupération – automatiser la gestion des incidents

**Conseils** : Automatisez les tâches manuelles répétitives pour accélérer le temps de réponse et réduire la charge de travail des analystes. Les tâches manuelles sont plus longues à exécuter, ce qui ralentit chaque incident et réduit le nombre d’incidents qu’un analyste peut traiter. Les tâches manuelles augmentent également la fatigue des analystes, ce qui accroît le risque d’erreur humaine entraînant des retards et dégrade la capacité des analystes à se concentrer efficacement sur des tâches complexes.  
 
Utilisez les fonctionnalités d’automatisation des workflows dans Protection Microsoft contre les menaces pour déclencher automatiquement des recherches et des remédiations en réponse à des alertes de sécurité entrantes. 
 
- [Recherche et réponse automatisées dans Protection Microsoft contre les menaces](https://docs.microsoft.com/microsoft-365/security/mtp/mtp-autoir)

**Supervision d’Azure Security Center** : Non applicable

**Responsabilité** : Customer

## <a name="posture-and-vulnerability-management"></a>Gestion de la posture et des vulnérabilités

*Pour plus d’informations, consultez [Benchmark de sécurité Azure : Gestion de la posture et des vulnérabilités](/azure/security/benchmarks/security-controls-v2-vulnerability-management).*

### <a name="pv-1-establish-secure-configurations-for-azure-services"></a>PV-1 : Établir des configurations sécurisées pour les services Azure 

**Instructions** : Configurez votre service Power BI avec les paramètres appropriés à votre organisation et à votre attitude en matière de sécurité. Les paramètres d’accès au service et au contenu ainsi que la sécurité de l’espace de travail et de l’application doivent être soigneusement pris en compte. Consultez Power BI Security and Data Protection (Sécurité et protection des données Power BI) dans le livre blanc Power BI Enterprise Deployment (Déploiement de Power BI dans l’entreprise).

- [Livre blanc sur le déploiement dans l’entreprise](https://aka.ms/PBIEnterpriseDeploymentWP)

**Supervision d’Azure Security Center** : Non applicable

**Responsabilité** : Customer

### <a name="pv-2-sustain-secure-configurations-for-azure-services"></a>PV-2 : Supporter des configurations sécurisées pour les services Azure

**Instructions** : Surveillez votre instance de Power BI en utilisant les API REST d’administration de Power BI.

- [API REST d’administration de Power BI](https://docs.microsoft.com/rest/api/power-bi/admin)

- [Livre blanc sur le déploiement de Power BI en entreprise](https://aka.ms/PBIEnterpriseDeploymentWP)

**Supervision d’Azure Security Center** : Non applicable

**Responsabilité** : Customer

### <a name="pv-8-conduct-regular-attack-simulation"></a>PV-8 : Effectuer une simulation d’attaque régulière

**Conseils** : Selon les besoins, effectuez un test d’intrusion ou des activités Red Team sur vos ressources Azure et résolvez tous les problèmes de sécurité critiques détectés.

Suivez les règles d’engagement de pénétration du cloud Microsoft pour vous assurer que vos tests d’intrusion sont conformes aux stratégies de Microsoft. Utilisez la stratégie et l’exécution de Red Teaming de Microsoft ainsi que les tests d’intrusion de site actif sur l’infrastructure cloud, les services et les applications gérés par Microsoft.

- [Test d’intrusion dans Azure](https://docs.microsoft.com/azure/security/fundamentals/pen-testing)

- [Règles d’engagement des tests d’intrusion](https://www.microsoft.com/msrc/pentest-rules-of-engagement?rtc=1)

- [Microsoft Cloud Red Teaming](https://gallery.technet.microsoft.com/Cloud-Red-Teaming-b837392e)

**Supervision d’Azure Security Center** : Non applicable

**Responsabilité** : Partagé

## <a name="backup-and-recovery"></a>Sauvegarde et récupération

*Pour plus d’informations, consultez [Benchmark de sécurité Azure : Sauvegarde et récupération](/azure/security/benchmarks/security-controls-v2-backup-recovery).*

### <a name="br-3-validate-all-backups-including-customer-managed-keys"></a>BR-3 : Valider toutes les sauvegardes, y compris les clés gérées par le client

**Instructions** : Si vous utilisez la fonctionnalité Bring Your Own Key (BYOK) dans Power BI, vous devez vérifier périodiquement que vous pouvez accéder à vos clés gérées par le client et les restaurer.

- [BYOK dans Power BI](https://docs.microsoft.com/power-bi/admin/service-encryption-byok)

**Supervision d’Azure Security Center** : Non applicable

**Responsabilité** : Customer

### <a name="br-4-mitigate-risk-of-lost-keys"></a>BR-4 : Atténuer les risques liés aux clés perdues

**Instructions** : Si vous utilisez la fonctionnalité Bring Your Own Key (BYOK) dans Power BI, vous devez vérifier que le coffre de clés contrôlant vos clés gérées par le client est configuré avec les instructions de la documentation de BYOK dans Power BI ci-dessous. Activez la suppression réversible et la protection contre la purge dans Azure Key Vault pour protéger les clés contre une suppression accidentelle ou malveillante.

- [BYOK dans Power BI](https://docs.microsoft.com/power-bi/admin/service-encryption-byok)

- [Guide pratique pour activer la suppression réversible et la protection contre la purge dans Key Vault](https://docs.microsoft.com/azure/storage/blobs/storage-blob-soft-delete?tabs=azure-portal)

Pour les ressources de clé de passerelle, vérifiez que vous suivez les instructions de la documentation des clés de récupération de passerelle ci-dessous.

- [Clé de récupération de la passerelle de données locale](https://docs.microsoft.com/data-integration/gateway/service-gateway-recovery-key)

**Supervision d’Azure Security Center** : Non applicable

**Responsabilité** : Customer

## <a name="governance-and-strategy"></a>Gouvernance et stratégie

*Pour plus d’informations, consultez [Benchmark de sécurité Azure : Gouvernance et stratégie](/azure/security/benchmarks/security-controls-v2-governance-strategy).*

### <a name="gs-1-define-asset-management-and-data-protection-strategy"></a>GS-1 : Définir la stratégie de gestion des ressources et de protection des données 

**Conseils** : Veillez à documenter et à communiquer une stratégie claire pour la surveillance et la protection continues des systèmes et des données. Hiérarchisez la découverte, l’évaluation, la protection et la surveillance des données et systèmes critiques de l’entreprise. 

Cette stratégie doit inclure les recommandations, stratégies et normes documentées pour les éléments suivants : 

-   Norme de classification des données en fonction des risques pour l’entreprise

-   Visibilité de l’organisation de sécurité sur les risques et l’inventaire des actifs 

-   Approbation de l’organisation de sécurité pour les services Azure en vue de leur utilisation 

-   Sécurité des ressources tout au long de leur cycle de vie

-   Stratégie de contrôle d’accès requise conformément à la classification des données organisationnelles

-   Utilisation des fonctionnalités de protection des données Azure natives et de tiers

-   Exigences de chiffrement des données pour les cas d’utilisation en transit et au repos

-   Normes de chiffrement appropriées

Pour plus d’informations, consultez les références suivantes :
- [Recommandation d’architecture de sécurité Azure - Stockage, données et chiffrement](https://docs.microsoft.com/azure/architecture/framework/security/storage-data-encryption?toc=/security/compass/toc.json&amp;bc=/security/compass/breadcrumb/toc.json)

- [Notions de base de la sécurité Azure - Sécurité, chiffrement et stockage des données Azure](https://docs.microsoft.com/azure/security/fundamentals/encryption-overview)

- [Cloud Adoption Framework - Meilleures pratiques en matière de chiffrement et de sécurité des données Azure](https://docs.microsoft.com/azure/security/fundamentals/data-encryption-best-practices?toc=/azure/cloud-adoption-framework/toc.json&amp;bc=/azure/cloud-adoption-framework/_bread/toc.json)

- [Benchmark de sécurité Azure - Gestion des ressources](https://docs.microsoft.com/azure/security/benchmarks/security-benchmark-v2-asset-management)

- [Benchmark de sécurité Azure - Protection des données](https://docs.microsoft.com/azure/security/benchmarks/security-benchmark-v2-data-protection)

**Supervision d’Azure Security Center** : Non applicable

**Responsabilité** : Customer

### <a name="gs-2-define-enterprise-segmentation-strategy"></a>GS-2 : Définir la stratégie de segmentation d'entreprise 

**Conseils** : Établissez une stratégie à l'échelle de l'entreprise pour segmenter l'accès aux ressources à l'aide d'une combinaison de contrôles d'identité, de réseau, d'application, d'abonnement, de groupe de gestion et autres.

Trouvez le bon équilibre entre la nécessité de séparation sur le plan de la sécurité et la nécessité d'exécuter quotidiennement les systèmes qui doivent communiquer entre eux et accéder aux données.

Veillez à ce que la stratégie de segmentation soit implémentée de manière cohérente pour tous les types de contrôle, y compris pour les modèles d'identité, d'accès et de sécurité du réseau, les modèles d'autorisation/d'accès aux applications et les contrôles des processus humains.

- [Aide relative à la stratégie de segmentation dans Azure (vidéo)](https://docs.microsoft.com/security/compass/microsoft-security-compass-introduction#azure-components-and-reference-model-2151)

- [Aide relative à la stratégie de segmentation dans Azure (document)](https://docs.microsoft.com/security/compass/governance#enterprise-segmentation-strategy)

- [Aligner la segmentation du réseau avec la stratégie de segmentation d’entreprise](https://docs.microsoft.com/security/compass/network-security-containment#align-network-segmentation-with-enterprise-segmentation-strategy)

**Supervision d’Azure Security Center** : Non applicable

**Responsabilité** : Customer

### <a name="gs-3-define-security-posture-management-strategy"></a>GS-3 : Définir la stratégie de gestion de la posture de la sécurité

**Conseils** : Mesurez et atténuez en permanence les risques liés à vos ressources individuelles et à l’environnement dans lequel elles sont hébergées. Priorisez les ressources à valeur élevée et les surfaces d’attaque hautement exposées, comme les applications publiées, les points d’entrée et de sortie du réseau, les points de terminaison utilisateur et administrateur, etc.

- [Benchmark de sécurité Azure - Gestion de la posture et des vulnérabilités](https://docs.microsoft.com/azure/security/benchmarks/security-benchmark-v2-posture-vulnerability-management)

**Supervision d’Azure Security Center** : Non applicable

**Responsabilité** : Customer

### <a name="gs-4-align-organization-roles-responsibilities-and-accountabilities"></a>GS-4 : Aligner les rôles et les responsabilités de l’organisation

**Conseils** : Veillez à documenter et à communiquer une stratégie claire pour les rôles et les responsabilités de votre organisation de sécurité. Veillez à définir clairement les responsabilités pour les décisions relatives à la sécurité, à former tout le monde au modèle de responsabilité partagée et à former les équipes techniques à la technologie permettant de sécuriser le cloud.

- [Meilleures pratiques pour la sécurité Azure 1 – Personnes : Former les équipes pour le parcours vers la sécurité dans le cloud](https://docs.microsoft.com/azure/cloud-adoption-framework/security/security-top-10#1-people-educate-teams-about-the-cloud-security-journey)

- [Meilleures pratiques pour la sécurité Azure 2 – Personnes : Former les équipes pour les technologies de sécurité dans le cloud](https://docs.microsoft.com/azure/cloud-adoption-framework/security/security-top-10#2-people-educate-teams-on-cloud-security-technology)

- [Meilleures pratiques pour la sécurité Azure 3 – Processus : Affecter les responsabilités pour les décisions de sécurité dans le cloud](https://docs.microsoft.com/azure/cloud-adoption-framework/security/security-top-10#4-process-update-incident-response-ir-processes-for-cloud)

**Supervision d’Azure Security Center** : Non applicable

**Responsabilité** : Customer

### <a name="gs-5-define-network-security-strategy"></a>GS-5 : Définir la stratégie de sécurité réseau

**Conseils** : Établissez une approche de sécurité réseau Azure dans le cadre de la stratégie de contrôle d’accès de sécurité globale de votre organisation.  

Cette stratégie doit inclure les recommandations, stratégies et normes documentées pour les éléments suivants : 

-   Responsabilité centralisée pour la gestion et la sécurité du réseau

-   Modèle de segmentation de réseau virtuel aligné avec la stratégie de segmentation de l’entreprise

-   Stratégie de correction dans différents scénarios de menaces et d’attaques

-   Stratégie de périphérie d’Internet et d’entrée et de sortie

-   Stratégie de cloud hybride et d’interconnexion locale

-   Artefacts de sécurité réseau à jour (par exemple diagrammes réseau, architecture de réseau de référence)

Pour plus d’informations, consultez les références suivantes :
- [Meilleures pratiques pour la sécurité Azure 11 – Architecture. Stratégie de sécurité unifiée unique](https://docs.microsoft.com/azure/cloud-adoption-framework/security/security-top-10#11-architecture-establish-a-single-unified-security-strategy)

- [Benchmark de sécurité Azure – Sécurité réseau](https://docs.microsoft.com/azure/security/benchmarks/security-benchmark-v2-network-security)

- [Vue d’ensemble de la sécurité réseau d’Azure](https://docs.microsoft.com/azure/security/fundamentals/network-overview)

- [Stratégie d’architecture de réseau d’entreprise](https://docs.microsoft.com/azure/cloud-adoption-framework/ready/enterprise-scale/architecture)

**Supervision d’Azure Security Center** : Non applicable

**Responsabilité** : Customer

### <a name="gs-6-define-identity-and-privileged-access-strategy"></a>GS-6 : Définir une stratégie d’accès privilégié et d’identité

**Conseils** : Établissez une approche d’identité Azure et d’accès privilégié dans le cadre de la stratégie de contrôle d’accès de sécurité globale de votre organisation.  

Cette stratégie doit inclure les recommandations, stratégies et normes documentées pour les éléments suivants : 

-   Un système centralisé d’identité et d’authentification et son interconnexion avec d’autres systèmes d’identité internes et externes

-   Méthodes d’authentification fortes dans différents cas d’usage et différentes conditions

-   Protection des utilisateurs disposant de privilèges élevés

-   Surveillance et gestion des activités anormales des utilisateurs  

-   Vérification de l’identité et de l’accès des utilisateurs et processus de rapprochement

Pour plus d’informations, consultez les références suivantes :

- [Benchmark de sécurité Azure - Gestion des identités](https://docs.microsoft.com/azure/security/benchmarks/security-benchmark-v2-identity-management)

- [Benchmark de sécurité Azure - Accès privilégié](https://docs.microsoft.com/azure/security/benchmarks/security-benchmark-v2-privileged-access)

- [Meilleures pratiques pour la sécurité Azure 11 – Architecture. Stratégie de sécurité unifiée unique](https://docs.microsoft.com/azure/cloud-adoption-framework/security/security-top-10#11-architecture-establish-a-single-unified-security-strategy)

- [Vue d’ensemble de la sécurité et de la gestion des identités Azure](https://docs.microsoft.com/azure/security/fundamentals/identity-management-overview)

**Supervision d’Azure Security Center** : Non applicable

**Responsabilité** : Customer

### <a name="gs-7-define-logging-and-threat-response-strategy"></a>GS-7 : Définir la stratégie de journalisation et de réponse aux menaces

**Conseils** : Établissez une stratégie de journalisation et de réponse aux menaces pour détecter et corriger rapidement les menaces tout en répondant aux exigences de conformité. En priorité, fournissez aux analystes des alertes de bonne qualité et des expériences homogènes afin qu’ils puissent se concentrer sur les menaces plutôt que sur l’intégration et les étapes manuelles. 

Cette stratégie doit inclure les recommandations, stratégies et normes documentées pour les éléments suivants : 

-   Rôle et responsabilités de l’organisation d’opérations de sécurité (SecOP) 

-   Un processus de réponse aux incidents bien défini, aligné avec NIST ou autre cadre réglementaire du secteur 

-   Capture et rétention des journaux pour prendre en charge la détection des menaces, la réponse aux incidents et les besoins de conformité

-   Visibilité centralisée des informations de corrélation sur les menaces, avec SIEM, les fonctionnalités Azure natives et d’autres sources 

-   Plan de communication et de notification avec vos clients, fournisseurs et les parties publiques pertinentes

-   Utilisation de plateformes Azure natives et tierces pour la gestion des incidents, comme la journalisation et la détection des menaces, les investigations et la correction et l’éradication des attaques

-   Processus de gestion des incidents et des activités postérieures aux incidents, comme les leçons apprises et la rétention des preuves

Pour plus d’informations, consultez les références suivantes :

- [Benchmark de sécurité Azure - Journalisation et détection des menaces](https://docs.microsoft.com/azure/security/benchmarks/security-benchmark-v2-logging-threat-detection)

- [Benchmark de sécurité Azure - Réponse aux incidents](https://docs.microsoft.com/azure/security/benchmarks/security-benchmark-v2-incident-response)

- [Meilleures pratiques pour la sécurité Azure 4 - Processus. Mise à jour des processus de réponse aux incidents pour le cloud](https://docs.microsoft.com/azure/cloud-adoption-framework/security/security-top-10#4-process-update-incident-response-ir-processes-for-cloud)

- [Guide pour le cadre d’adoption d’Azure, la journalisation et la prise de décision pour les rapports](https://docs.microsoft.com/azure/cloud-adoption-framework/decision-guides/logging-and-reporting/)

- [Mise à l’échelle, gestion et surveillance d’entreprise Azure](https://docs.microsoft.com/azure/cloud-adoption-framework/ready/enterprise-scale/management-and-monitoring)

**Supervision Azure Security Center** : Non applicable

**Responsabilité** : Customer

## <a name="next-steps"></a>Étapes suivantes

- Consultez [Vue d’ensemble d’Azure Security Benchmark V2](/azure/security/benchmarks/overview)
- En savoir plus sur les [bases de référence de la sécurité Azure](/azure/security/benchmarks/security-baselines-overview)
