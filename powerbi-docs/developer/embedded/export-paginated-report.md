---
title: Exporter une API de rapports Power BI
description: Découvrez comment exporter un rapport paginé Power BI incorporé.
author: KesemSharabi
ms.author: kesharab
ms.topic: how-to
ms.service: powerbi
ms.subservice: powerbi-developer
ms.date: 04/05/2020
ms.openlocfilehash: ed3193e586dc05fe92d9c429584080ac80d86a17
ms.sourcegitcommit: eef4eee24695570ae3186b4d8d99660df16bf54c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85237166"
---
# <a name="export-paginated-report-to-file-preview"></a>Exporter un rapport paginé dans un fichier (préversion)

L’API `exportToFile` permet d’exporter un rapport paginé Power BI avec un appel REST. Les formats de fichier suivants sont pris en charge :
* **.pptx** (PowerPoint)
* **.pdf**
* **.xlsx** (Excel)
* **.dox** (Word)
* **.csv**
* **.xml**
* **.mhtml**
* **Image**
    * Lors de l’exportation vers une image, définissez le format de l’image par le biais du paramètre de format `OutputFormat`.
    * Les valeurs d’OutputFormat prises en charge sont les suivantes : .bmp, .emf, .gif, .jpeg, .png et .tiff (par défaut)

## <a name="usage-examples"></a>Exemples d'utilisation

Vous pouvez utiliser la fonctionnalité d’exportation de différentes manières. Voici quelques exemples :

* **Bouton Envoyer à l’impression** : dans votre application, créez un bouton qui, lorsque vous cliquez dessus, déclenche un travail d’exportation. Le travail peut exporter le rapport visualisé dans un fichier .pdf ou .pptx et, une fois qu’il est terminé, l’utilisateur peut recevoir le fichier sous forme de téléchargement. À l’aide de paramètres de rapport et de paramètres de format, vous pouvez exporter le rapport dans un état spécifique, y compris les données filtrées, les tailles de pages personnalisées et d’autres paramètres propres au format. Étant donné que l’API est asynchrone, la mise à disposition du fichier peut prendre un certain temps.

* **Pièce jointe d’e-mail** : envoyer un e-mail automatisé à intervalles définis, avec un rapport .pdf en pièce jointe. Ce scénario peut être utile si vous souhaitez automatiser l’envoi d’un rapport hebdomadaire aux dirigeants.

## <a name="using-the-api"></a>Utilisation de l’API

L’API est asynchrone. Lorsque l’API [exportToFile](https://docs.microsoft.com/rest/api/power-bi/reports/exporttofile) est appelée, elle déclenche un travail d’exportation. Après avoir déclenché un travail d’exportation, utilisez l’[interrogation](https://docs.microsoft.com/rest/api/power-bi/reports/getexporttofilestatus) pour suivre le travail jusqu’à ce qu’il soit terminé.

Une fois l’exportation terminée, l’appel de l’API d’interrogation retourne une [URL Power BI](https://docs.microsoft.com/rest/api/power-bi/reports/getfileofexporttofile) pour obtenir le fichier. L’URL sera disponible pendant 24 heures.

## <a name="supported-features"></a>Fonctionnalités prises en charge

### <a name="format-settings"></a>Paramètres de format

Spécifiez divers paramètres de format pour chaque format de fichier. Les propriétés et les valeurs prises en charge sont équivalentes aux [paramètres Informations sur l’appareil](../../paginated-reports/report-builder-url-parameters.md#report-commands-rdl) pour les paramètres d’URL de rapport paginé.

Voici deux exemples ; un pour exporter les quatre premières pages d’un rapport à l’aide de la taille de page de rapport vers un fichier .pptx, et un autre pour exporter la troisième page d’un rapport dans un fichier .jpeg.

**Exportation des quatre premières pages dans un fichier .pptx**

```json
{
      "format": "PPTX",
      "paginatedReportConfiguration":{
            "formatSettings":{
                  "UseReportPageSize": "true",
                  "StartPage": "1",
                  "EndPage": "4"
            }
      }
}
```

**Exportation de la troisième page dans un fichier .jpeg**

```json
{
      "format": "IMAGE",
      "paginatedReportConfiguration":{
            "formatSettings":{
                  "OutputFormat": "JPEG",
                  "StartPage": "3",
                  "EndPage": "3"
            }
      }
}
```

### <a name="report-parameters"></a>Paramètres de rapport

Vous pouvez utiliser l’API `exportToFile` pour exporter par programmation un rapport avec un jeu de paramètres de rapport. Cette opération s’effectue à l’aide des fonctionnalités de [paramètre de rapport](../../paginated-reports/paginated-reports-parameters.md).

Voici un exemple de définition de valeurs de paramètre de rapport.

```json
{
      "format": "PDF",
      "paginatedReportConfiguration":{
            "parameterValues":[
                  {"name": "State", "value": "WA"},
                  {"name": "City", "value": "Seattle"},
                  {"name": "City", "value": "Bellevue"},
                  {"name": "City", "value": "Redmond"}
            ]
      }
}
```

### <a name="authentication"></a>Authentification

Vous pouvez vous authentifier avec un utilisateur (ou un utilisateur maître) ou un [principal de service](embed-service-principal.md).

### <a name="row-level-security-rls"></a>Sécurité au niveau de la ligne (RLS)

Quand vous utilisez un jeu de données Power BI ayant la sécurité au niveau des lignes (SNL) définie comme source de données, vous pouvez exporter un rapport qui affiche uniquement les données visibles par certains utilisateurs. Par exemple, si vous exportez un rapport de ventes défini avec des rôles régionaux, vous pouvez filtrer programmatiquement le rapport de façon à n’afficher qu’une région précise.

Pour exporter à l’aide de la sécurité au niveau des lignes, vous devez disposer de l’autorisation de lecture sur le jeu de données Power BI que le rapport utilise comme source de données.

Voici un exemple de spécification d’un nom d’utilisateur effectif pour la sécurité au niveau des lignes.

```json
{
      "format": "PDF",
      "paginatedReportConfiguration":{
            "identities": [
                  {"username": "john@contoso.com"}            
            ]
      }
}
```

## <a name="code-examples"></a>Exemples de code

Vous pouvez télécharger le SDK d’API Power BI utilisé dans les exemples de code [ici](https://www.nuget.org/packages/Microsoft.PowerBI.Api).

Lorsque vous créez un travail d’exportation, il y a trois étapes à suivre :

1. Envoi d’une demande d’exportation.
2. Interrogation.
3. Obtention du fichier.

Cette section fournit des exemples pour chaque étape.

### <a name="step-1---sending-an-export-request"></a>Étape 1 : envoi d’une demande d’exportation

La première étape consiste à envoyer une demande de rapport. Dans cet exemple, une demande d’exportation est envoyée pour des valeurs de paramètres de plage de pages, de taille et de rapport spécifiques.

```csharp
private async Task<string> PostExportRequest(
    Guid reportId,
    Guid groupId)
{
    // For documentation purposes the export configuration is created in this method
    // Ordinarily, it would be created outside and passed in
    var paginatedReportExportConfiguration = new PaginatedReportExportConfiguration()
    {
        FormatSettings = new Dictionary<string, string>()
        {
            {"PageHeight", "14in"},
            {"PageWidth", "8.5in" },
            {"StartPage", "1"},
            {"EndPage", "4"}
        },
        ParameterValues = new List<ParameterValue>()
        {
            { new ParameterValue() {Name = "State", Value = "WA"} },
            { new ParameterValue() {Name = "City", Value = "Redmond"} }
        }
    };

    var exportRequest = new ExportReportRequest
    {
        Format = FileFormat.PDF,
        PaginatedReportExportConfiguration = paginatedReportExportConfiguration,
    };

    var export = await Client.Reports.ExportToFileInGroupAsync(groupId, reportId, exportRequest);

    // Save the export ID, you'll need it for polling and getting the exported file
    return export.Id;
}
```

### <a name="step-2---polling"></a>Étape 2 : interrogation

Après avoir envoyé une demande de rapport, utilisez l’interrogation pour savoir quand le fichier exporté que vous attendez est prêt.

```csharp
private async Task<Export> PollExportRequest(
    Guid reportId,
    Guid groupId,
    string exportId /* Get from the ExportToAsync response */,
    int timeOutInMinutes,
    CancellationToken token)
{
    Export exportStatus = null;
    DateTime startTime = DateTime.UtcNow;
    const int secToMillisec = 1000;
    do
    {
        if (DateTime.UtcNow.Subtract(startTime).TotalMinutes > timeOutInMinutes || token.IsCancellationRequested)
        {
            // Error handling for timeout and cancellations
            return null;
        }

        var httpMessage = 
            await Client.Reports.GetExportToFileStatusInGroupWithHttpMessagesAsync(groupId, reportId, exportId);
            
        exportStatus = httpMessage.Body;
        if (exportStatus.Status == ExportState.Running || exportStatus.Status == ExportState.NotStarted)
        {
            // The recommended waiting time between polling requests can be found in the RetryAfter header
            // Note that this header is only populated when the status is either Running or NotStarted
            var retryAfter = httpMessage.Response.Headers.RetryAfter;
            var retryAfterInSec = retryAfter.Delta.Value.Seconds;

            await Task.Delay(retryAfterInSec * secToMillisec);
        }
    }
    // While not in a terminal state, keep polling
    while (exportStatus.Status != ExportState.Succeeded && exportStatus.Status != ExportState.Failed);

    return exportStatus;
}
```

### <a name="step-3---getting-the-file"></a>Étape 3 : obtention du fichier

Une fois que l’interrogation retourne une URL, utilisez cet exemple pour accéder au fichier reçu.

```csharp
private async Task<ExportedFile> GetExportedFile(
    Guid reportId,
    Guid groupId,
    Export export /* Get from the GetExportStatusAsync response */)
{
    if (export.Status == ExportState.Succeeded)
    {
        var httpMessage = 
            await Client.Reports.GetFileOfExportToFileInGroupWithHttpMessagesAsync(groupId, reportId, export.Id);

        return new ExportedFile
        {
            FileStream = httpMessage.Body,
            ReportName = export.ReportName,
            FileExtension = export.ResourceFileExtension,
        };
    }

    return null;
}

public class ExportedFile
{
    public Stream FileStream;
    public string ReportName;
    public string FileExtension;
}
```

### <a name="end-to-end-example"></a>Exemple de bout en bout

Il s’agit d’un exemple de bout en bout pour l’exportation d’un rapport. Il comprend les étapes suivantes :
1. [Envoi de la demande d'exportation](#step-1---sending-an-export-request).
2. [Interrogation](#step-2---polling).
3. [Obtention du fichier](#step-3---getting-the-file).

```csharp
private async Task<ExportedFile> ExportPaginatedReport(
    Guid reportId,
    Guid groupId,
    int pollingtimeOutInMinutes,
    CancellationToken token)
{
    try
    {
        var exportId = await PostExportRequest(reportId, groupId);

        var export = await PollExportRequest(reportId, groupId, exportId, pollingtimeOutInMinutes, token);
        if (export == null || export.Status != ExportState.Succeeded)
        {
           // Error, failure in exporting the report
            return null;
        }

        return await GetExportedFile(reportId, groupId, export);
    }
    catch
    {
        // Error handling
        throw;
    }
}
```

## <a name="next-steps"></a>Étapes suivantes

Vérifiez comment incorporer du contenu pour vos clients et votre organisation :

> [!div class="nextstepaction"]
>[Exporter le rapport vers un fichier](export-to.md)

> [!div class="nextstepaction"]
>[Incorporer pour vos clients](embed-sample-for-customers.md)

> [!div class="nextstepaction"]
>[Incorporer pour votre organisation](embed-sample-for-your-organization.md)