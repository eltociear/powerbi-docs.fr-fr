---
title: Notes de publication de Power BI Report Server
description: "L’API REST fournit un accès par programme aux objets dans un catalogue Power BI Report Server."
services: powerbi
documentationcenter: 
author: markingmyname
manager: kfile
backup: 
editor: 
tags: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 11/01/2017
ms.author: maghan
ms.openlocfilehash: 554270d3b7bdbd3de88a7d5865dae8cdf226a6b2
ms.sourcegitcommit: 6e693f9caf98385a2c45890cd0fbf2403f0dbb8a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/30/2018
---
# <a name="develop-with-the-rest-apis-for-power-bi-report-server"></a>Développer avec les API REST pour Power BI Report Server
Power BI Report Server prend en charge les API Representational State Transfer (REST). Les API REST sont des points de terminaison de service qui prennent en charge un ensemble d’opérations HTTP (méthodes) qui fournissent un accès en création, récupération, mise à jour ou suppression aux ressources à l’intérieur d’un serveur de rapports.

L’API REST fournit un accès par programme aux objets dans un catalogue Power BI Report Server. Ces objets sont, par exemple, des dossiers, des rapports, des indicateurs de performance clés, des sources de données, des jeux de données, des plans d’actualisation, des abonnements et bien plus encore. L’API REST vous permet, par exemple, de parcourir l’arborescence des dossiers, de découvrir le contenu d’un dossier, ou de télécharger une définition de rapport. Elle permet également de créer, mettre à jour et supprimer des objets. Des exemples d’utilisation d’objets sont le téléchargement d’un rapport, l’exécution d’un plan d’actualisation, la suppression d’un dossier et ainsi de suite.

## <a name="components-of-a-rest-api-requestresponse"></a>Composants d’une requête-réponse d’API REST
Une paire requête-réponse (ou demande/réponse) d’API REST peut être divisée en cinq composants :

* L’**URI de demande**, qui comprend : `{URI-scheme} :// {URI-host} / {resource-path} ? {query-string}`. Bien que l’URI de demande soit incluse dans l’en-tête de message de demande, nous l’appelons séparément ici, car la plupart des langages ou infrastructures requiert que vous le passiez séparément du message de demande.
  
  * URI scheme (schéma d’URI) : indique le protocole utilisé pour transmettre la demande. Par exemple, `http` ou `https`.
  * URI host (hôte d’URI) : spécifie le nom de domaine ou l’adresse IP du serveur sur lequel le point de terminaison de service REST est hébergé, tel que `myserver.contoso.com`.
  * Resource path (chemin d’accès de la ressource) : spécifie la ressource ou collection de ressources, qui peut inclure plusieurs segments que le service utilise dans la détermination de la sélection de ces ressources. Par exemple : `CatalogItems(01234567-89ab-cdef-0123-456789abcdef)/Properties` peut être utilisé pour obtenir les propriétés spécifiées pour l’élément CatalogItem.
  * Query string (chaîne de requête, facultatif) : fournit des paramètres simples supplémentaires, tels que les critères de sélection de ressource ou de version de l’API.
* Champs de message d’en-tête de requête HTTP :
  
  * [Méthode HTTP](https://www.w3.org/Protocols/rfc2616/rfc2616-sec9.html) obligatoire (également appelée opération ou verbe), indiquant au service le type d’opération que vous demandez. Les API REST de Reporting Services prennent en charge les méthodes DELETE, GET, HEAD, PUT, POST et PATCH.
  * Champs d’en-tête supplémentaires facultatifs, tels que requis par l’URI et la méthode HTTP spécifiés.
* Champs de **corps de message de requête** HTTP facultatifs, pour prendre en charge l’URI et l’opération HTTP. Par exemple, les opérations POST contiennent des objets encodés MIME qui sont transmis en tant que paramètres complexes. Pour les opérations POST ou PUT, le type d’encodage MIME pour le corps doit être spécifié également dans l’en-tête de demande `Content-type`. Certains services requièrent que vous utilisiez un type MIME spécifique, tel que `application/json`.
* Champs d’**en-tête de message de réponse** HTTP :
  
  * [Code d’état HTTP](http://www.w3.org/Protocols/HTTP/HTRESP.html), dans la plage des codes de réussite 2xx aux codes d’erreur 4xx ou 5xx. Un code d’état défini par le service peut également être retourné, comme indiqué dans la documentation de l’API.
  * Champs d’en-tête supplémentaires facultatifs, comme requis pour prendre en charge de réponse de la demande, tel un en-tête de réponse `Content-type`.
* Champs de **corps du message de réponse** HTTP facultatifs :
  
  * Des objets de réponse encodés MIME sont renvoyés dans le corps de la réponse HTTP, telle une réponse d’une méthode GET qui retourne des données. En règle générale, ces objets sont retournés dans un format structuré tel que JSON ou XML, comme indiqué par l’en-tête de réponse `Content-type`.

## <a name="api-documentation"></a>Documentation de l’API
Une API REST moderne appelle une documentation moderne sur l’API. L’API REST repose sur la spécification OpenAPI (aussi appelée spécification Swagger), et une documentation est disponible sur [SwaggerHub](https://app.swaggerhub.com/apis/microsoft-rs/PBIRS/2.0). Au-delà de la documentation de l’API, SwaggerHub aide à générer une bibliothèque cliente dans le langage choisi : JavaScript, TypeScript, c#, Java, Python, Ruby et bien plus encore.

## <a name="testing-api-calls"></a>Test des appels d’API
Un outil pour tester les messages de requête-réponse HTTP est [Fiddler](http://www.telerik.com/fiddler). Fiddler est un site proxy de débogage web gratuit capable d’intercepter vos demandes REST, ce qui facilite le diagnostic des messages de requête-réponse HTTP.

## <a name="next-steps"></a>Étapes suivantes
Passez en revue les API disponibles sur de [SwaggerHub](https://app.swaggerhub.com/apis/microsoft-rs/PBIRS/2.0).

Des exemples sont disponibles sur [GitHub](https://github.com/Microsoft/Reporting-Services). L’exemple inclut une application HTML5 reposant sur TypeScript, React et Webpack ainsi qu’un exemple PowerShell.

D’autres questions ? [Essayez d’interroger la communauté Power BI](https://community.powerbi.com/)

