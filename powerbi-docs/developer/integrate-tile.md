---
title: "Intégrer une vignette Power BI dans une application pour votre organisation"
description: "Procédure pas à pas d’intégration d’une vignette à une application, exemple de code"
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
ms.topic: get-started-article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 12/19/2017
ms.author: maghan
ms.openlocfilehash: fd33908f907ffac6cbff765e01e4a4321d399ca8
ms.sourcegitcommit: 6e693f9caf98385a2c45890cd0fbf2403f0dbb8a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/30/2018
---
# <a name="integrate-a-tile-into-an-app-user-owns-data"></a>Intégrer une vignette dans une application (l’utilisateur possède les données)
Découvrez comment intégrer (ou incorporer) une vignette dans une application web en utilisant des appels d’API REST, ainsi que l’API JavaScript Power BI, lorsque l’incorporation s’adresse à votre organisation.

![Vignette incorporée dans une application web](media/integrate-tile/powerbi-embedded-tile.png)

Pour vous familiariser avec cette procédure pas à pas, vous avez besoin d’un compte **Power BI**. Si vous n’avez pas de compte, vous pouvez [demander gratuitement un compte Power BI](../service-self-service-signup-for-power-bi.md) ou vous pouvez créer votre propre [locataire Azure Active Directory](create-an-azure-active-directory-tenant.md) à des fins de test.

> [!NOTE]
> Vous souhaitez plutôt incorporer une vignette pour vos clients, à l’aide d’un jeton d’incorporation ? Consultez [Intégrer un tableau de bord, une vignette ou un rapport dans votre application pour vos clients](embed-sample-for-customers.md).
> 
> 

Pour intégrer une vignette à une application web, vous utilisez l’API REST **Power BI** ou le SDK Power BI C# et un **jeton d’accès** d’autorisation Azure Active Directory (AD) pour obtenir une vignette. Vous chargez ensuite la vignette en utilisant le même jeton d’accès. L’API **Power BI** fournit un accès par programme à certaines ressources **Power BI**. Pour plus d’informations, consultez [Vue d’ensemble de l’API REST Power BI](https://msdn.microsoft.com/library/dn877544.aspx) et [API JavaScript Power BI](https://github.com/Microsoft/PowerBI-JavaScript).

## <a name="download-the-sample"></a>Télécharger l’exemple
Cet article explique le code utilisé dans l’[exemple d’intégration d’application web de vignette](https://github.com/Microsoft/PowerBI-Developer-Samples/tree/master/User%20Owns%20Data/integrate-tile-web-app) sur GitHub. Pour suivre cette procédure pas à pas, vous pouvez télécharger l’exemple.

## <a name="step-1---register-an-app-in-azure-ad"></a>Étape 1 - Inscrire une application dans Azure AD
Vous devez inscrire votre application avec Azure AD afin d’effectuer des appels d’API REST. Pour plus d’informations, consultez [Inscrire une application Azure AD pour incorporer du contenu Power BI](register-app.md).

Si vous avez téléchargé [l’exemple d’intégration d’application web de vignette](https://github.com/Microsoft/PowerBI-Developer-Samples/tree/master/User%20Owns%20Data/integrate-tile-web-app), utilisez **l’ID client** et la **Clé secrète client** que vous obtenez après inscription pour que l’exemple puisse s’authentifier sur Azure AD. Pour configurer l’exemple, modifiez l’**ID client** et le **secret du client** dans le fichier *cloud.config*.

![](media/integrate-tile/powerbi-embed-dashboard-register-app4.png)

## <a name="step-2---get-an-access-token-from-azure-ad"></a>Étape 2 : obtenir un jeton d’accès à partir d’Azure AD
Dans votre application, vous devez d’abord obtenir un **jeton d’accès**, à partir d’Azure AD, avant de pouvoir effectuer des appels d’API REST Power BI. Pour plus d’informations, consultez [Authentifier des utilisateurs et obtenir un jeton d’accès Azure AD pour votre application Power BI](get-azuread-access-token.md).

## <a name="step-3---get-a-tile"></a>Étape 3 : obtenir une vignette
Pour obtenir une vignette **Power BI**, vous utilisez l’opération [Get Tiles](https://msdn.microsoft.com/library/mt465741.aspx) qui récupère une liste de vignettes **Power BI** à partir d’un tableau de bord donné. Dans la liste des vignettes, vous pouvez obtenir un ID de vignette et une URL incorporée.

Vous devez d’abord récupérer un ID de tableau de bord avant de pouvoir obtenir la vignette. Pour plus d’informations sur la récupération d’un tableau de bord, consultez [Intégrer un tableau de bord à une application (l’utilisateur possède les données)](integrate-dashboard.md).

### <a name="get-tiles-using-an-access-token"></a>Obtenir des vignettes à l’aide d’un jeton d’accès
En utilisant le **jeton d’accès** récupéré à l’[Étape 2](#step-2-get-an-access-token-from-azure-ad), vous pouvez appeler l’opération [Get Tiles](https://msdn.microsoft.com/library/mt465741.aspx). L’opération [Get Tiles](https://msdn.microsoft.com/library/mt465741.aspx) renvoie une liste de vignettes. Vous ne pouvez récupérer qu’une seule vignette dans cette liste. Voici une méthode C# complète pour obtenir une vignette. 

Pour effectuer l’appel d’API REST, vous devez inclure un en-tête d’*autorisation* au format *Porteur {jeton d’accès}*.

#### <a name="get-tiles-with-the-rest-api"></a>Obtenir des vignettes avec l’API REST
**Default.aspx.cs**

```
using Newtonsoft.Json;

//Get a tile from a dashboard. In this sample, you get the first tile.
protected void GetTile(string dashboardId, int index)
{
    //Configure tiles request
    System.Net.WebRequest request = System.Net.WebRequest.Create(
        String.Format("{0}Dashboards/{1}/Tiles",
        baseUri,
        dashboardId)) as System.Net.HttpWebRequest;

    request.Method = "GET";
    request.ContentLength = 0;
    request.Headers.Add("Authorization", String.Format("Bearer {0}", accessToken.Value));

    //Get tiles response from request.GetResponse()
    using (var response = request.GetResponse() as System.Net.HttpWebResponse)
    {
        //Get reader from response stream
        using (var reader = new System.IO.StreamReader(response.GetResponseStream()))
        {
            //Deserialize JSON string
            PBITiles tiles = JsonConvert.DeserializeObject<PBITiles>(reader.ReadToEnd());

            //Sample assumes at least one Dashboard with one Tile.
            //You could write an app that lists all tiles in a dashboard
            if (tiles.value.Length > 0)
                tileEmbedUrl.Text = tiles.value[index].embedUrl;
        }
    }
}

//Power BI Tiles used to deserialize the Get Tiles response.
public class PBITiles
{
    public PBITile[] value { get; set; }
}
public class PBITile
{
    public string id { get; set; }
    public string title { get; set; }
    public string embedUrl { get; set; }
}
```

#### <a name="get-tiles-using-the-net-sdk"></a>Obtenir des vignettes à l’aide du Kit de développement logiciel (SDK) .NET
Le SDK .NET permet de récupérer une liste de tableaux de bord au lieu d’appeler directement l’API REST.

```
using Microsoft.IdentityModel.Clients.ActiveDirectory;
using Microsoft.PowerBI.Api.V2;
using Microsoft.PowerBI.Api.V2.Models;

var tokenCredentials = new TokenCredentials(<ACCESS TOKEN>, "Bearer");

// Create a Power BI Client object. It will be used to call Power BI APIs.
using (var client = new PowerBIClient(new Uri(ApiUrl), tokenCredentials))
{
    // Get a list of dashboards your "My Workspace"
    ODataResponseListDashboard tiles = client.Dashboards.GetDashboards();

    // Get a list of dashboards from a group (app workspace)
    ODataResponseListDashboard dashboards = client.Dashboards.GetDashboardsInGroup(groupId);

    Dashboard dashboard = dashboards.Value.FirstOrDefault();

    // Get the first tile from the above dashbaord
    ODataResponseListTile tiles = client.Dashboards.GetTiles(dashboard.Id);

    Tile tile = tiles.Value.FirstOrDefault();
}
```

## <a name="step-4---load-a-tile-using-javascript"></a>Étape 4 - Charger une vignette à l’aide de JavaScript
JavaScript permet de charger une vignette dans un élément div sur votre page web.

**Default.aspx**

```
<!-- Embed Tile-->
<div> 
    <asp:Panel ID="PanelEmbed" runat="server" Visible="true">
        <div>
            <div><b class="step">Step 3</b>: Embed a tile</div>

            <div>Enter an embed url for a tile from Step 2 (starts with https://):</div>
            <input type="text" id="tb_EmbedURL" style="width: 1024px;" />
            <br />
            <input type="button" id="bEmbedTileAction" value="Embed Tile" />
        </div>

        <div id="tileContainer"></div>
    </asp:Panel>
</div>
```

**Site.master**

```
window.onload = function () {
    // client side click to embed a selected tile.
    var el = document.getElementById("bEmbedTileAction");
    if (el.addEventListener) {
        el.addEventListener("click", updateEmbedTile, false);
    } else {
        el.attachEvent('onclick', updateEmbedTile);
    }

    // handle server side post backs, optimize for reload scenarios
    // show embedded tile if all fields were filled in.
    var accessTokenElement = document.getElementById('MainContent_accessTokenTextbox');
    if (accessTokenElement !== null) {
        var accessToken = accessTokenElement.value;
        if (accessToken !== "")
            updateEmbedTile();
    }
};

// update embed tile
function updateEmbedTile() {

    // check if the embed url was selected
    var embedUrl = document.getElementById('tb_EmbedURL').value;
    if (embedUrl === "")
        return;

    // get the access token.
    accessToken = document.getElementById('MainContent_accessTokenTextbox').value;

    // Embed configuration used to describe the what and how to embed.
    // This object is used when calling powerbi.embed.
    // You can find more information at https://github.com/Microsoft/PowerBI-JavaScript/wiki/Embed-Configuration-Details.
    var config = {
        type: 'tile',
        accessToken: accessToken,
        embedUrl: embedUrl
    };

    // Grab the reference to the div HTML element that will host the tile.
    var tileContainer = document.getElementById('tileContainer');

    // Embed the tile and display it within the div container.
    var tile = powerbi.embed(tileContainer, config);

    // tile.on will add an event handler which prints to Log window.
    tile.on("error", function (event) {
        var logView = document.getElementById('logView');
        logView.innerHTML = logView.innerHTML + "Error<br/>";
        logView.innerHTML = logView.innerHTML + JSON.stringify(event.detail, null, "  ") + "<br/>";
        logView.innerHTML = logView.innerHTML + "---------<br/>";
    });
}
```

Si vous avez téléchargé et exécuté [l’exemple d’intégration d’application web de vignette](https://github.com/Microsoft/PowerBI-Developer-Samples/tree/master/User%20Owns%20Data/integrate-tile-web-app), l’exemple se présente comme ci-dessous.

![Vignette incorporée dans une application web](media/integrate-tile/powerbi-embedded-tile.png)

## <a name="working-with-groups-app-workspaces"></a>Utilisation des groupes (espaces de travail d’application)
Pour incorporer une vignette à partir d’un groupe, obtenez la liste de toutes les vignettes disponibles dans le tableau de bord d’un groupe en utilisant l’appel d’API REST suivant. Pour plus d’informations sur cet appel d’API REST, consultez [Obtenir des vignettes](https://msdn.microsoft.com/library/mt465741.aspx). Vous devez avoir l’autorisation requise dans le groupe pour que la requête puisse retourner les résultats.

```
https://api.powerbi.com/v1.0/myorg/groups/{groupId}/dashboards/{dashboard_id}/tiles
```

L’API ci-dessus retourne la liste des vignettes disponibles. Chaque vignette a une propriété EmbedUrl qui est déjà créée pour prendre en charge l’incorporation de groupe.

```
https://app.powerbi.com/embed?dashboardId={dashboard_id}&tileId={tile_id}&groupId={group_id}
```

## <a name="next-steps"></a>Étapes suivantes
[Incorporation de vignette](https://github.com/Microsoft/PowerBI-JavaScript/wiki/Tile-Embed) sur le wiki PowerBI-JavaScript

[API JavaScript Power BI](https://github.com/Microsoft/PowerBI-JavaScript).

Exemple [integrate-tile-web-app](https://github.com/Microsoft/PowerBI-Developer-Samples/tree/master/User%20Owns%20Data/integrate-tile-web-app) sur GitHub.

D’autres questions ? [Essayez d’interroger la communauté Power BI](http://community.powerbi.com/)

