---
title: "Intégrer un rapport Power BI dans une application pour votre organisation"
description: "Découvrez comment intégrer (ou incorporer) un rapport dans une application web à l’aide des API REST Power BI."
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
ms.date: 10/05/2017
ms.author: maghan
ms.openlocfilehash: 9ed341eb4428795bb4714ae8f1a34fd11c1bcbcd
ms.sourcegitcommit: 6e693f9caf98385a2c45890cd0fbf2403f0dbb8a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/30/2018
---
# <a name="integrate-a-report-into-an-app-for-your-organization"></a>Intégrer un rapport dans une application pour votre organisation
Découvrez comment intégrer (ou incorporer) un rapport dans une application web en utilisant des appels d’API REST, ainsi que l’API JavaScript Power BI, lorsque l’incorporation s’adresse à votre organisation.

![Exemple de rapport incorporé](media/integrate-report/powerbi-embedded-report.png)

Pour vous familiariser avec cette procédure pas à pas, vous avez besoin d’un compte **Power BI**. Si vous n’avez pas de compte, vous pouvez [demander gratuitement un compte Power BI](../service-self-service-signup-for-power-bi.md) ou vous pouvez créer votre propre [locataire Azure Active Directory](create-an-azure-active-directory-tenant.md) à des fins de test.

> [!NOTE]
> Vous souhaitez plutôt incorporer un rapport pour vos clients, à l’aide d’un jeton d’incorporation ? Consultez [Intégrer un tableau de bord, une vignette ou un rapport dans votre application pour vos clients](embed-sample-for-customers.md).
> 
> 

Pour intégrer un rapport à une application web, vous utilisez l’API REST **Power BI** ou le SDK Power BI C# et un **jeton d’accès** d’autorisation Azure Active Directory (AD) pour obtenir un rapport. Vous chargez ensuite le rapport en utilisant le même jeton d’accès. L’API **Power BI** fournit un accès par programme à certaines ressources **Power BI**. Pour plus d’informations, consultez [Vue d’ensemble de l’API REST Power BI](https://msdn.microsoft.com/library/dn877544.aspx) et [API JavaScript Power BI](https://github.com/Microsoft/PowerBI-JavaScript).

## <a name="download-the-sample"></a>Télécharger l’exemple
Cet article explique le code utilisé dans l’[exemple d’intégration d’application web de rapport](https://github.com/Microsoft/PowerBI-Developer-Samples/tree/master/User%20Owns%20Data/integrate-report-web-app) sur GitHub. Pour suivre cette procédure pas à pas, vous pouvez télécharger l’exemple.

## <a name="step-1---register-an-app-in-azure-ad"></a>Étape 1 - Inscrire une application dans Azure AD
Vous devez inscrire votre application avec Azure AD afin d’effectuer des appels d’API REST. Pour plus d’informations, consultez [Inscrire une application Azure AD pour incorporer du contenu Power BI](register-app.md).

Si vous avez téléchargé [l’exemple d’intégration d’application web de rapport](https://github.com/Microsoft/PowerBI-Developer-Samples/tree/master/User%20Owns%20Data/integrate-report-web-app), utilisez **l’ID client** et la **Clé secrète client** que vous obtenez après inscription pour que l’exemple puisse s’authentifier sur Azure AD. Pour configurer l’exemple, modifiez l’**ID client** et le **secret du client** dans le fichier *cloud.config*.

![](media/integrate-report/powerbi-embed-dashboard-register-app4.png)

## <a name="step-2---get-an-access-token-from-azure-ad"></a>Étape 2 : obtenir un jeton d’accès à partir d’Azure AD
Dans votre application, vous devez d’abord obtenir un **jeton d’accès**, à partir d’Azure AD, avant de pouvoir effectuer des appels d’API REST Power BI. Pour plus d’informations, consultez [Authentifier des utilisateurs et obtenir un jeton d’accès Azure AD pour votre application Power BI](get-azuread-access-token.md).

## <a name="step-3---get-a-report"></a>Étape 3 : obtenir un rapport
Pour obtenir un rapport **Power BI**, vous utilisez l’opération [Obtenir des rapports](https://msdn.microsoft.com/library/mt634543.aspx) opération qui obtient une liste de rapports **Power BI**. Dans la liste des rapports, vous pouvez obtenir un ID de rapport.

### <a name="get-reports-using-an-access-token"></a>Obtenir des rapports à l’aide d’un jeton d’accès
En utilisant le **jeton d’accès** récupéré à l’[Étape 2](#step-2-get-an-access-token-from-azure-ad), vous pouvez appeler l’opération [Get Reports](https://msdn.microsoft.com/library/mt634543.aspx). L’opération [Obtenir des rapports](https://msdn.microsoft.com/library/mt634543.aspx) renvoie une liste de rapports. Vous ne pouvez récupérer qu’un seul rapport dans cette liste. Voici une méthode C# complète pour obtenir un rapport. 

Pour effectuer l’appel d’API REST, vous devez inclure un en-tête d’*autorisation* au format *Porteur {jeton d’accès}*.

#### <a name="get-reports-with-the-rest-api"></a>Obtenir des rapports avec l’API REST
**Default.aspx.cs**

```
using Newtonsoft.Json;

//Get a Report. In this sample, you get the first Report.
protected void GetReport(int index)
{
    //Configure Reports request
    System.Net.WebRequest request = System.Net.WebRequest.Create(
        String.Format("{0}/Reports",
        baseUri)) as System.Net.HttpWebRequest;

    request.Method = "GET";
    request.ContentLength = 0;
    request.Headers.Add("Authorization", String.Format("Bearer {0}", accessToken.Value));

    //Get Reports response from request.GetResponse()
    using (var response = request.GetResponse() as System.Net.HttpWebResponse)
    {
        //Get reader from response stream
        using (var reader = new System.IO.StreamReader(response.GetResponseStream()))
        {
            //Deserialize JSON string
            PBIReports Reports = JsonConvert.DeserializeObject<PBIReports>(reader.ReadToEnd());

            //Sample assumes at least one Report.
            //You could write an app that lists all Reports
            if (Reports.value.Length > 0)
            {
                var report = Reports.value[index];

                txtEmbedUrl.Text = report.embedUrl;
                txtReportId.Text = report.id;
                txtReportName.Text = report.name;
            }
        }
    }
}

//Power BI Reports used to deserialize the Get Reports response.
public class PBIReports
{
    public PBIReport[] value { get; set; }
}
public class PBIReport
{
    public string id { get; set; }
    public string name { get; set; }
    public string webUrl { get; set; }
    public string embedUrl { get; set; }
}
```

#### <a name="get-reports-using-the-net-sdk"></a>Obtenir des rapports à l’aide du Kit de développement logiciel (SDK) .NET
Le SDK .NET permet de récupérer une liste de rapports au lieu d’appeler directement l’API REST.

```
using Microsoft.IdentityModel.Clients.ActiveDirectory;
using Microsoft.PowerBI.Api.V2;
using Microsoft.PowerBI.Api.V2.Models;

var tokenCredentials = new TokenCredentials(<ACCESS TOKEN>, "Bearer");

// Create a Power BI Client object. It will be used to call Power BI APIs.
using (var client = new PowerBIClient(new Uri(ApiUrl), tokenCredentials))
{
    // Get the first report all reports in that workspace
    ODataResponseListReport reports = client.Reports.GetReports();

    Report report = reports.Value.FirstOrDefault();

    var embedUrl = report.EmbedUrl;
}
```

## <a name="step-4---load-a-report-using-javascript"></a>Étape 4 - Charger un rapport à l’aide de JavaScript
JavaScript permet de charger un rapport dans un élément div sur votre page web.

**Default.aspx**

```
<!-- Embed Report-->
<div> 
    <asp:Panel ID="PanelEmbed" runat="server" Visible="true">
        <div>
            <div><b class="step">Step 3</b>: Embed a report</div>

            <div>Enter an embed url for a report from Step 2 (starts with https://):</div>
            <input type="text" id="tb_EmbedURL" style="width: 1024px;" />
            <br />
            <input type="button" id="bEmbedReportAction" value="Embed Report" />
        </div>

        <div id="reportContainer"></div>
    </asp:Panel>
</div>
```

**Site.master**

```
window.onload = function () {
    // client side click to embed a selected report.
    var el = document.getElementById("bEmbedReportAction");
    if (el.addEventListener) {
        el.addEventListener("click", updateEmbedReporte, false);
    } else {
        el.attachEvent('onclick', updateEmbedReport);
    }

    // handle server side post backs, optimize for reload scenarios
    // show embedded report if all fields were filled in.
    var accessTokenElement = document.getElementById('MainContent_accessTokenTextbox');
    if (accessTokenElement !== null) {
        var accessToken = accessTokenElement.value;
        if (accessToken !== "")
            updateEmbedReport();
    }
};

// update embed report
function updateEmbedReport() {

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
        type: 'report',
        accessToken: accessToken,
        embedUrl: embedUrl
    };

    // Grab the reference to the div HTML element that will host the report.
    var reportContainer = document.getElementById('reportContainer');

    // Embed the report and display it within the div container.
    var report = powerbi.embed(reportContainer, config);

    // report.on will add an event handler which prints to Log window.
    report.on("error", function (event) {
        var logView = document.getElementById('logView');
        logView.innerHTML = logView.innerHTML + "Error<br/>";
        logView.innerHTML = logView.innerHTML + JSON.stringify(event.detail, null, "  ") + "<br/>";
        logView.innerHTML = logView.innerHTML + "---------<br/>";
    });
}
```

Si vous avez téléchargé et exécuté [l’exemple d’intégration d’application web de rapport](https://github.com/Microsoft/PowerBI-Developer-Samples/tree/master/User%20Owns%20Data/integrate-report-web-app), l’exemple se présente comme ci-dessous.

![Exemple de rapport incorporé](media/integrate-report/powerbi-embedded-report.png)

## <a name="working-with-groups-app-workspaces"></a>Utilisation des groupes (espaces de travail d’application)
Pour incorporer un rapport à partir d’un groupe, obtenez la liste de tous les rapports disponibles dans le tableau de bord d’un groupe en utilisant l’appel d’API REST suivant. Pour plus d’informations sur cet appel d’API REST, consultez [Obtenir des rapports](https://msdn.microsoft.com/library/mt634543.aspx). Vous devez avoir l’autorisation requise dans le groupe pour que la requête puisse retourner les résultats.

```
https://api.powerbi.com/v1.0/myorg/groups/{group_id}/reports
```

L’API ci-dessus retourne la liste des rapports disponibles. Chaque rapport a une propriété EmbedUrl qui est déjà créée pour prendre en charge l’incorporation de groupe.

```
https://app.powerbi.com/reportEmbed?reportId={report_id}&groupId={group_id}
```

## <a name="next-steps"></a>Étapes suivantes
Vous pouvez examiner un exemple d’application sur GitHub. Pour en savoir plus, consultez l’[exemple d’intégration d’application web de rapport](https://github.com/Microsoft/PowerBI-Developer-Samples/tree/master/User%20Owns%20Data/integrate-report-web-app).

Pour en savoir plus sur l’API JavaScript, consultez [API JavaScript Power BI](https://github.com/Microsoft/PowerBI-JavaScript).

D’autres questions ? [Essayez d’interroger la communauté Power BI](http://community.powerbi.com/)

