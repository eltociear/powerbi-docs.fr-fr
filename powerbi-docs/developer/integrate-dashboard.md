---
title: "Intégrer un tableau de bord dans une application pour votre organisation"
description: "Découvrez comment intégrer (ou incorporer) un tableau de bord dans une application web à l’aide des API REST Power BI."
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
ms.date: 02/13/2018
ms.author: maghan
ms.openlocfilehash: e85b745798fd33ffbb5061f4c156054d2218bfb1
ms.sourcegitcommit: 2ceea44d3606c15b57142c37649c9d481ec4becc
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/15/2018
---
# <a name="integrate-a-dashboard-into-an-app-for-your-organization"></a>Intégrer un tableau de bord dans une application pour votre organisation
Découvrez comment intégrer (ou incorporer) un tableau de bord dans une application web en utilisant des appels d’API REST, ainsi que l’API JavaScript Power BI, lorsque l’incorporation s’adresse à votre organisation.

![Tableau de bord incorporé](media/integrate-dashboard/powerbi-embed-dashboard.png)

Pour vous familiariser avec cette procédure pas à pas, vous avez besoin d’un compte **Power BI**. Si vous n’avez pas de compte, vous pouvez [demander gratuitement un compte Power BI](../service-self-service-signup-for-power-bi.md) ou vous pouvez créer votre propre [locataire Azure Active Directory](create-an-azure-active-directory-tenant.md) à des fins de test.

> [!NOTE]
> Vous souhaitez plutôt incorporer un tableau de bord pour vos clients, à l’aide d’un jeton d’incorporation ? Consultez [Intégrer un tableau de bord, une vignette ou un rapport dans votre application pour vos clients](embed-sample-for-customers.md).
> 
> 

Pour intégrer un tableau de bord à une application web, vous utilisez l’API REST **Power BI** ou le SDK Power BI C# et un **jeton d’accès** d’autorisation Azure Active Directory (AD) pour obtenir un tableau de bord. Vous chargez ensuite le tableau de bord en utilisant le même jeton d’accès. L’API **Power BI** fournit un accès par programme à certaines ressources **Power BI**. Pour plus d’informations, consultez [Vue d’ensemble de l’API REST Power BI](https://msdn.microsoft.com/library/dn877544.aspx) et [API JavaScript Power BI](https://github.com/Microsoft/PowerBI-JavaScript).

## <a name="download-the-sample"></a>Télécharger l’exemple
Cet article explique le code utilisé dans l’[exemple d’intégration d’application web de tableau de bord](https://github.com/Microsoft/PowerBI-Developer-Samples/tree/master/User%20Owns%20Data/integrate-dashboard-web-app) sur GitHub. Pour suivre cette procédure pas à pas, vous pouvez télécharger l’exemple.

## <a name="step-1---register-an-app-in-azure-ad"></a>Étape 1 - Inscrire une application dans Azure AD
Vous devez inscrire votre application avec Azure AD afin d’effectuer des appels d’API REST. Pour plus d’informations, consultez [Inscrire une application Azure AD pour incorporer du contenu Power BI](register-app.md).

Si vous avez téléchargé l’[exemple d’intégration de tableau de bord](https://github.com/Microsoft/PowerBI-Developer-Samples/tree/master/User%20Owns%20Data/integrate-dashboard-web-app), vous utilisez l’**ID client** et le **secret du client** que vous obtenez, après votre inscription, pour que l’exemple puisse s’authentifier auprès d’Azure AD. Pour configurer l’exemple, modifiez l’**ID client** et le **secret du client** dans le fichier *cloud.config*.

![](media/integrate-dashboard/powerbi-embed-dashboard-register-app4.png)

## <a name="step-2---get-an-access-token-from-azure-ad"></a>Étape 2 : obtenir un jeton d’accès à partir d’Azure AD
Dans votre application, vous devez d’abord obtenir un **jeton d’accès**, à partir d’Azure AD, avant de pouvoir effectuer des appels d’API REST Power BI. Pour plus d’informations, consultez [Authentifier des utilisateurs et obtenir un jeton d’accès Azure AD pour votre application Power BI](get-azuread-access-token.md).

## <a name="step-3---get-a-dashboard"></a>Étape 3 : obtenir un tableau de bord
Pour obtenir un tableau de bord **Power BI**, vous utilisez l’opération [Obtenir des tableaux de bord](https://msdn.microsoft.com/library/mt465739.aspx) opération qui obtient une liste de tableaux de bord **Power BI**. Dans la liste des tableaux de bord, vous pouvez obtenir un ID de tableau de bord.

![](media/integrate-dashboard/powerbi-embed-dashboard-get-dashboards.png)

### <a name="get-dashboards-using-an-access-token"></a>Obtenir des tableaux de bord avec un jeton d’accès
En utilisant le **jeton d’accès** récupéré à l’[Étape 2](#step-2-get-an-access-token-from-azure-ad), vous pouvez appeler l’opération [Get Dashboards](https://msdn.microsoft.com/library/mt465739.aspx). L’opération [Obtenir des tableaux de bord](https://msdn.microsoft.com/library/mt465739.aspx) renvoie la liste des tableaux de bord. Vous ne pouvez récupérer qu’un seul tableau de bord dans cette liste. Voici une méthode C# complète pour obtenir un tableau de bord. 

Pour effectuer l’appel d’API REST, vous devez inclure un en-tête d’*autorisation* au format *Porteur {jeton d’accès}*.

#### <a name="get-dashboards-with-the-rest-api"></a>Obtenir des tableaux de bord avec l’API REST
**Default.aspx.cs**

```
protected void getDashboardsButton_Click(object sender, EventArgs e)
{
    string responseContent = string.Empty;

    //Configure dashboards request
    System.Net.WebRequest request = System.Net.WebRequest.Create(String.Format("{0}dashboards", baseUri)) as System.Net.HttpWebRequest;
    request.Method = "GET";
    request.ContentLength = 0;
    request.Headers.Add("Authorization", String.Format("Bearer {0}", authResult.AccessToken));

    //Get dashboards response from request.GetResponse()
    using (var response = request.GetResponse() as System.Net.HttpWebResponse)
    {
        //Get reader from response stream
        using (var reader = new System.IO.StreamReader(response.GetResponseStream()))
        {
            responseContent = reader.ReadToEnd();

            //Deserialize JSON string
            PBIDashboards PBIDashboards = JsonConvert.DeserializeObject<PBIDashboards>(responseContent);

            if (PBIDashboards != null)
            {
                var gridViewDashboards = PBIDashboards.value.Select(dashboard => new {
                    Id = dashboard.id,
                    DisplayName = dashboard.displayName,
                    EmbedUrl = dashboard.embedUrl
                });

                this.GridView1.DataSource = gridViewDashboards;
                this.GridView1.DataBind();
            }
        }
    }
}

//Power BI Dashboards used to deserialize the Get Dashboards response.
public class PBIDashboards
{
    public PBIDashboard[] value { get; set; }
}
public class PBIDashboard
{
    public string id { get; set; }
    public string displayName { get; set; }
    public string embedUrl { get; set; }
    public bool isReadOnly { get; set; }
}
```

#### <a name="get-dashboards-using-the-net-sdk"></a>Obtenir des tableaux de bord à l’aide du SDK .NET
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
    ODataResponseListDashboard dashboards = client.Dashboards.GetDashboards();

    // Get a list of dashboards from a group (app workspace)
    ODataResponseListDashboard dashboards = client.Dashboards.GetDashboardsInGroup(groupId);

    Dashboard dashboard = dashboards.Value.FirstOrDefault();

    var embedUrl = dashboard.EmbedUrl
}
```

## <a name="step-4---load-a-dashboard-using-javascript"></a>Étape 4 - Charger un tableau de bord à l’aide de JavaScript
Vous pouvez utiliser JavaScript pour charger un tableau de bord dans un élément div sur votre page web.

**Default.aspx**

```
<!-- Embed Dashboard-->
<div> 
    <asp:Panel ID="PanelEmbed" runat="server" Visible="true">
        <div>
            <div><b class="step">Step 3</b>: Embed a dashboard</div>

            <div>Enter an embed url for a dashboard from Step 2 (starts with https://):</div>
            <input type="text" id="tb_EmbedURL" style="width: 1024px;" />
            <br />
            <input type="button" id="bEmbedDashboardAction" value="Embed Dashboard" />
        </div>

        <div id="dashboardContainer"></div>
    </asp:Panel>
</div>
```

**Site.master**

```
window.onload = function () {
    // client side click to embed a selected dashboard.
    var el = document.getElementById("bEmbedDashboardAction");
    if (el.addEventListener) {
        el.addEventListener("click", updateEmbedDashboard, false);
    } else {
        el.attachEvent('onclick', updateEmbedDashboard);
    }

    // handle server side post backs, optimize for reload scenarios
    // show embedded dashboard if all fields were filled in.
    var accessTokenElement = document.getElementById('MainContent_accessTokenTextbox');
    if (accessTokenElement !== null) {
        var accessToken = accessTokenElement.value;
        if (accessToken !== "")
            updateEmbedDashboard();
    }
};

// update embed dashboard
function updateEmbedDashboard() {

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
        type: 'dashboard',
        accessToken: accessToken,
        embedUrl: embedUrl
    };

    // Grab the reference to the div HTML element that will host the dashboard.
    var dashboardContainer = document.getElementById('dashboardContainer');

    // Embed the dashboard and display it within the div container.
    var dashboard = powerbi.embed(dashboardContainer, config);

    // dashboard.on will add an event handler which prints to Log window.
    dashboard.on("tileClicked", function (event) {
        var logView = document.getElementById('logView');
        logView.innerHTML = logView.innerHTML + "Tile Clicked<br/>";
        logView.innerHTML = logView.innerHTML + JSON.stringify(event.detail, null, "  ") + "<br/>";
        logView.innerHTML = logView.innerHTML + "---------<br/>";
    });

    // dashboard.on will add an event handler which prints to Log window.
    dashboard.on("error", function (event) {
        var logView = document.getElementById('logView');
        logView.innerHTML = logView.innerHTML + "Error<br/>";
        logView.innerHTML = logView.innerHTML + JSON.stringify(event.detail, null, "  ") + "<br/>";
        logView.innerHTML = logView.innerHTML + "---------<br/>";
    });
}
```

Si vous avez téléchargé et exécuté l’[exemple d’intégration de tableau de bord](https://github.com/Microsoft/PowerBI-Developer-Samples/tree/master/User%20Owns%20Data/integrate-dashboard-web-app), l’exemple se présente comme ci-dessous.

![](media/integrate-dashboard/powerbi-embed-dashboard.png)

## <a name="tile-clicked-events"></a>Événements relatifs à une vignette sur laquelle un utilisateur a cliqué
Dans l’exemple ci-dessus, vous avez peut-être remarqué que vous pouvez gérer les événements quand un utilisateur clique sur la vignette du tableau de bord. Pour plus d’informations sur les événements, consultez [Gestion des événements dans l’API JavaScript](https://github.com/Microsoft/PowerBI-JavaScript/wiki/Handling-Events).

```
// dashboard.on will add an event handler which prints to Log window.
dashboard.on("tileClicked", function (event) {
    var logView = document.getElementById('logView');
    logView.innerHTML = logView.innerHTML + "Tile Clicked<br/>";
    logView.innerHTML = logView.innerHTML + JSON.stringify(event.detail, null, "  ") + "<br/>";
    logView.innerHTML = logView.innerHTML + "---------<br/>";
});

// dashboard.on will add an event handler which prints to Log window.
dashboard.on("error", function (event) {
    var logView = document.getElementById('logView');
    logView.innerHTML = logView.innerHTML + "Error<br/>";
    logView.innerHTML = logView.innerHTML + JSON.stringify(event.detail, null, "  ") + "<br/>";
    logView.innerHTML = logView.innerHTML + "---------<br/>";
});
```

Si vous avez téléchargé et exécuté l’[exemple d’intégration de tableau de bord](https://github.com/Microsoft/PowerBI-Developer-Samples/tree/master/PowerBI.com%20Integrate/integrate-dashboard-web-app), le fait de cliquer sur une vignette génère du texte sous le tableau de bord. Le texte ressemble à ce qui suit. Cela vous permet de journaliser le fait qu’un utilisateur a cliqué sur une vignette, puis de diriger l’utilisateur vers l’emplacement adéquat.

```
Tile Clicked
{ "event": "TileClick", "reportEmbedUrl": "", "navigationUrl": "https://app.powerbi.com/dashboards/fcff76f9-15ff-4a8e-8242-275ac9c25b90/qna?q=count%20of%20new%20hires%20from%20July%202014%20to%20December%202014", "tileId": "0e99b45c-9b53-4920-b239-cee7d37d2369" }
---------
Tile Clicked
{ "event": "TileClick", "reportEmbedUrl": "https://app.powerbi.com/reportEmbed?reportId=ab199308-80b1-4626-9823-43a84623bd9c", "navigationUrl": "https://app.powerbi.com/reports/ab199308-80b1-4626-9823-43a84623bd9c/ReportSection1", "tileId": "ffc30447-674a-4511-944f-79e182d719de", "pageName": "ReportSection1" }
---------
```

## <a name="working-with-groups-app-workspaces"></a>Utilisation des groupes (espaces de travail d’application)
Pour incorporer un tableau de bord à partir d’un groupe (espace de travail d’application), obtenez la liste de tous les tableaux de bord disponibles au sein d’un groupe à l’aide de l’appel d’API REST suivant. Pour plus d’informations sur cet appel d’API REST, consultez [Obtenir des tableaux de bord](https://msdn.microsoft.com/library/mt465739.aspx). Vous devez avoir l’autorisation requise dans le groupe pour que la requête puisse retourner les résultats.

```
https://api.powerbi.com/v1.0/myorg/groups/{groupId}/dashboards
```

L’API ci-dessus renvoie la liste des tableaux de bord disponibles. Chaque tableau de bord a une propriété EmbedUrl qui est déjà créée pour prendre en charge l’incorporation de groupe.

```
https://app.powerbi.com/dashboardEmbed?dashboardId={dashboardId}&groupId={groupId}
```

## <a name="limitations"></a>Limites
* Les utilisateurs finaux qui accèdent aux tableaux de bord incorporés doivent avoir un compte Power BI et une autorisation d’accès au tableau de bord. Ils sont propriétaires du tableau de bord ou le tableau de bord a été partagé avec l’utilisateur.
* La fonctionnalité Questions et réponses n’est actuellement pas prise en charge dans les tableaux de bord incorporés.
* Voici une limitation temporaire : quand vous partagez un tableau de bord avec des groupes de sécurité, l’utilisateur doit tout d’abord accéder aux tableaux de bord dans PowerBI.com avant de les voir incorporés.

## <a name="next-steps"></a>Étapes suivantes
Vous pouvez examiner un exemple d’application sur GitHub. Les exemples ci-dessus sont basés sur cet exemple. Pour en savoir plus, consultez l’[exemple d’intégration d’application web de tableau de bord](https://github.com/Microsoft/PowerBI-Developer-Samples/tree/master/User%20Owns%20Data/integrate-dashboard-web-app).

Pour en savoir plus sur l’API JavaScript, consultez [API JavaScript Power BI](https://github.com/Microsoft/PowerBI-JavaScript).

D’autres questions ? [Essayez d’interroger la communauté Power BI](http://community.powerbi.com/)

