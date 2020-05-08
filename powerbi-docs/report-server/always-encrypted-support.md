---
title: Always Encrypted dans Power BI Report Server
description: Cet article présente la prise en charge d’Always Encrypted dans Power BI Report Server lors de l’utilisation des types de sources de données Microsoft SQL Server et Microsoft Azure SQL Database.
author: maggiesMSFT
ms.reviewer: cfinlan
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.topic: conceptual
ms.date: 01/22/2020
ms.author: maggies
ms.openlocfilehash: f8d711bba8dc7570f2d470554fd1d971639bbb7b
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/05/2020
ms.locfileid: "76710203"
---
# <a name="always-encrypted-in-power-bi-report-server"></a>Always Encrypted dans Power BI Report Server

Cet article présente la prise en charge d’Always Encrypted dans Power BI Report Server lors de l’utilisation des types de sources de données Microsoft SQL Server et Microsoft Azure SQL Database. Pour plus d’informations sur les fonctionnalités d’Always Encrypted dans SQL Server, consultez l’article [Always Encrypted](https://docs.microsoft.com/sql/relational-databases/security/encryption/always-encrypted-database-engine).

## <a name="always-encrypted-user-isolation"></a>Isolation des utilisateurs dans Always Encrypted

Pour le moment, Power BI Report Server ne limite pas l’accès aux colonnes Always Encrypted dans les rapports dès lors qu’un utilisateur a accès au rapport.  Par conséquent, si le serveur a reçu l’accès aux clés de chiffrement de colonne via la clé principale de colonne, les utilisateurs ont accès à toutes les colonnes pour les rapports auxquels ils peuvent accéder.

## <a name="always-encrypted-column-usage"></a>Utilisation des colonnes Always Encrypted

### <a name="key-storage-strategies"></a>Stratégies de stockage des clés

|Stockage  |Prise en charge  |
|---------|---------|
|Magasin de certificats Windows | Oui |
|Azure Key Vault | Non |
| CNG (Cryptography Next Generation) | Non |

### <a name="certificate-storage-and-access"></a>Stockage et accès des certificats

Le compte qui nécessite l’accès au certificat est le compte de service. Le certificat doit être stocké dans le magasin de certificats de l’ordinateur local. Pour plus d’informations, consultez :

- [Configurer le compte de service Report Server](https://docs.microsoft.com/sql/reporting-services/install-windows/configure-the-report-server-service-account-ssrs-configuration-manager) (Configuration Manager)
- La section [Mise à disposition des certificats pour les applications et les utilisateurs](https://docs.microsoft.com/sql/relational-databases/security/encryption/create-and-store-column-master-keys-always-encrypted#making-certificates-available-to-applications-and-users) dans l’article SQL Server « Créer et stocker des clés principales de colonne pour Always Encrypted ».

### <a name="column-encryption-strategy"></a>Stratégie de chiffrement des colonnes

Dans Power BI Report Server, la stratégie de chiffrement des colonnes peut être *déterministe* ou *aléatoire*. Le tableau suivant indique les différences en fonction de la stratégie qu’elle utilise.

|Utilisation  |Déterministe  |Aléatoire  |
|---------|---------|---------|
|Peut être lu tel quel dans les résultats d’une requête, par exemple des instructions SELECT. | Oui  | Oui  |
|Peut être utilisé en tant que Group by (Regrouper par) entité dans la requête. | Oui | Non |
|Peut être utilisé comme champ d’agrégation, excepté pour COUNT et DISTINCT. | Non, excepté pour COUNT et DISTINCT | Non |
|Peut être utilisé comme paramètre de rapport | Oui | Non |

Découvrez plus d’informations sur [Chiffrement déterministe ou aléatoire](https://docs.microsoft.com/sql/relational-databases/security/encryption/always-encrypted-database-engine#selecting--deterministic-or-randomized-encryption).

### <a name="parameter-usage"></a>Utilisation des paramètres

L’utilisation des paramètres s’applique uniquement au chiffrement déterministe.

**Paramètre monovaleur**.  Vous pouvez utiliser un paramètre monovaleur sur une colonne Always Encrypted.

**Paramètre multivaleur** Vous ne pouvez pas utiliser un paramètre multivaleur avec plusieurs valeurs sur une colonne Always Encrypted.

**Paramètres en cascade**. Vous pouvez utiliser des paramètres en cascade avec Always Encrypted si *toutes* les conditions suivantes sont vraies :

- Toutes les colonnes Always Encrypted doivent être Always Encrypted avec une stratégie déterministe.
- Tous les paramètres utilisés sur des colonnes Always Encrypted sont des paramètres à valeur unique.
- Toutes les comparaisons SQL utilisent l’opérateur Égal à (=).

## <a name="datatype-support"></a>Prise en charge des types de données

| Type de données SQL | Prend en charge la lecture du champ | Prend en charge l’utilisation en tant qu’élément Group by | Agrégations prises en charge (COUNT, DISTINCT, MAX, MIN, SUM, etc.) | Prend en charge le filtrage via l’égalité avec des paramètres | Notes |
| --- | --- | --- | --- | --- | --- |
| int | Oui | Oui | COUNT, DISTINCT | Oui, en tant qu’entier (Integer) |   |
| float | Oui | Oui | COUNT, DISTINCT | Oui, en tant que flottant (Float) |   |
| nvarchar | Oui | Oui | COUNT, DISTINCT | Oui, en tant que texte (Text) | Le chiffrement déterministe doit utiliser un classement de colonne avec un ordre de tri binaire 2 pour les colonnes de type caractère. Pour plus d’informations, consultez l’article SQL Server [Always Encrypted](https://docs.microsoft.com/sql/relational-databases/security/encryption/always-encrypted-database-engine#selecting--deterministic-or-randomized-encryption) article.  |
| varchar | Oui | Oui | COUNT, DISTINCT | Non |   |
| decimal | Oui | Oui | COUNT, DISTINCT | Non |   |
| numeric | Oui | Oui | COUNT, DISTINCT | Non |   |
| datetime | Oui | Oui | COUNT, DISTINCT | Non |   |
| datetime2 | Oui | Oui | COUNT, DISTINCT | Oui, en tant que date/heure (Date/Time) | Pris en charge si la colonne n’a pas de précision à la milliseconde (en d’autres termes, pas datetime2(0)) |

## <a name="aggregation-alternatives"></a>Alternatives de l’agrégation

Actuellement, les seules agrégations prises en charge sur les colonnes Always Encrypted déterministes sont celles qui utilisent directement l’opérateur Égal à (=). Cette limitation de SQL Server est due à la nature des colonnes Always Encrypted. Les utilisateurs doivent effectuer l’agrégation au sein du rapport au lieu de le faire dans la base de données.

## <a name="always-encrypted-in-connection-strings"></a>Always Encrypted dans les chaînes de connexion

Vous devez activer Always Encrypted dans la chaîne de connexion pour une source de données SQL Server. Découvrez plus d’informations sur l’activation d’[Always Encrypted dans les requêtes d’application](https://docs.microsoft.com/sql/relational-databases/security/encryption/develop-using-always-encrypted-with-net-framework-data-provider#enabling-always-encrypted-for-application-queries).

## <a name="next-steps"></a>Étapes suivantes

[Always Encrypted](https://docs.microsoft.com/sql/relational-databases/security/encryption/always-encrypted-database-engine) dans SQL Server et Azure SQL Database

D’autres questions ? [Essayez d’interroger la communauté Power BI](https://community.powerbi.com/)

