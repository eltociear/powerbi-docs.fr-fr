---
title: Résoudre les problèmes de connexion dans Power BI Desktop
description: Solutions aux problèmes courants de connexion à Power BI Desktop
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 11/28/2018
ms.author: davidi
LocalizationGroup: Troubleshooting
ms.openlocfilehash: f8ceeddea7a8a9b7a63043cc7e91269da570790b
ms.sourcegitcommit: 2ae660a7b70fce23eb58b159d049eca44a664f2c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/30/2018
ms.locfileid: "52670987"
---
# <a name="troubleshooting-sign-in-for-power-bi-desktop"></a>Résoudre les problèmes liés à la connexion dans Power BI Desktop
Il est possible que vous rencontriez des erreurs lorsque vous tentez de vous connecter à **Power BI Desktop**. Il existe deux raisons principales aux problèmes de connexion : les **erreurs d’authentification de proxy** et les **erreurs de redirection d’URL non HTTPS**. 

Pour déterminer l’origine de votre problème de connexion, la première étape consiste à contacter votre administrateur et à lui fournir des informations de diagnostic afin qu’il puisse identifier la cause du problème. En suivant les problèmes liés à votre souci de connexion, les administrateurs peuvent déterminer quelles erreurs parmi les suivantes s’appliquent à votre cas. 

Jetons un œil à chacune de ces erreurs. À la fin de cet article, vous trouverez une discussion sur la capture d’une *trace* dans Power BI Desktop, qui peut aider à repérer la résolution des problèmes.


## <a name="proxy-authentication-required-error"></a>Erreur Authentification de proxy requise

L’écran suivant montre un exemple de l’erreur *Authentification de proxy requise*.

![Erreur de connexion pour l’authentification de proxy](media/desktop-troubleshooting-sign-in/desktop-tshoot-sign-in_01.png)

Les exceptions suivantes dans les fichier de trace *Power BI Desktop* sont associées à cette erreur :

* *Microsoft.PowerBI.Client.Windows.Services.PowerBIWebException*
* *HttpStatusCode: ProxyAuthenticationRequired*

Lorsque cette erreur se produit, la raison la plus probable est qu’un serveur d’authentification de proxy sur votre réseau ne bloque pas les requêtes web émises par **Power BI Desktop**. 

Si votre réseau utilise un serveur d’authentification de proxy, votre administrateur peut résoudre ce problème en autorisant les domaines suivants sur le serveur d’authentification de proxy :

* app.powerbi.com
* api.powerbi.com
* domaines dans l’espace de noms *.analysis.windows.net

Pour les clients qui font partie d’un cloud de gouvernement, la résolution de ce problème peut être effectué en autorisant les domaines suivants sur le serveur d’authentification de proxy :

* app.powerbigov.us
* api.powerbigov.us
* domaines dans l’espace de noms *.analysis.usgovcloudapi.net

## <a name="non-https-url-redirect-not-supported-error"></a>Erreur Redirection d’URL non HTTPS non prise en charge

Les versions actuelles de **Power BI Desktop** utilisent la version actuelle d’ADAL (Active Directory Authentication Library), qui n’autorise pas la redirection vers les URL non sécurisées (non HTTPS). 

Les exceptions suivantes dans les fichier de trace *Power BI Desktop* sont associées à cette erreur :

* *Microsoft.IdentityModel.Clients.ActiveDirectory.AdalServiceException : la redirection vers une URL non HTTPS n’est pas prise en charge dans webview*
* *ErrorCode: non_https_redirect_failed*

Si l’erreur *ErrorCode: non_https_redirect_failed* se produit, cela signifie qu’un(e) ou plusieurs fournisseurs ou pages de redirection dans la chaîne de redirection n’est pas un point de terminaison HTTPS protégé, ou qu’un émetteur de certificat d’une ou plusieurs redirections ne fait pas partie des racines de confiance de l’appareil. Tous les fournisseurs d’une chaîne de redirection de la connexion doivent utiliser une URL HTTPS. Pour résoudre ce problème, contactez votre administrateur et demandez-lui d’utiliser des URL sécurisées pour ses sites d’authentification. 

## <a name="how-to-collect-a-trace-in-power-bi-desktop"></a>Comment recueillir une trace dans Power BI Desktop

Pour recueillir une trace dans **Power BI Desktop**, procédez comme suit :

1. Activez le traçage dans **Power BI Desktop** en accédant à **Fichier > Options et paramètres > Options**, puis sélectionnez **Diagnostics** parmi les options dans le volet gauche. Dans le volet qui s’affiche, cochez la case en regard de l’option **Activer le traçage**, comme illustré dans l’image suivante. Vous devrez peut-être redémarrer **Power BI Desktop**.
   
   ![Activer le traçage dans Power BI Desktop](media/desktop-troubleshooting-sign-in/desktop-tshoot-sign-in_02.png)

2. Puis, suivez les étapes pour reproduire l’erreur. Lorsque celle-ci se produit, **Power BI Desktop** ajoute des événements dans le journal de suivi, qui est conservé sur l’ordinateur local.

3. Accédez au dossier Traces sur votre ordinateur local. Vous trouverez ce dossier en sélectionnant le lien dans **Diagnostics** où vous avez activé le traçage, indiqué en tant que *Ouvrir le dossier de vidage sur incident/traces* dans l’image précédente. Souvent, vous trouverez ce dossier sur l’ordinateur local à l’emplacement suivant :

    `C:\Users/<user name>/AppData/Local/Microsoft/Power BI Desktop/Traces`

Ce dossier peut contenir de nombreux fichiers de trace. Assurez-vous d’envoyer uniquement les fichiers récents à votre administrateur afin de faciliter l’identification rapide de l’erreur. 

