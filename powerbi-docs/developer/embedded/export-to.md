---
title: Exporter une API de rapports Power BI
description: Découvrez comment exporter un rapport Power BI incorporé
author: KesemSharabi
ms.author: kesharab
ms.topic: conceptual
ms.service: powerbi
ms.subservice: powerbi-developer
ms.date: 03/24/2020
ms.openlocfilehash: 472797cf30d6b88a59af5b3846e9b710bf4607c7
ms.sourcegitcommit: 81407c9ccadfa84837e07861876dff65d21667c7
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/13/2020
ms.locfileid: "81267500"
---
# <a name="export-power-bi-report-to-file-preview"></a>Exporter un rapport Power BI vers un fichier (préversion)

L’API `exportToFile` permet d’exporter un rapport Power BI avec un appel REST. Les formats de fichier suivants sont pris en charge :
* **.pptx** (PowerPoint)
* **.pdf**
* **.png**
    * Lors de l’exportation vers un fichier .png, un rapport de plusieurs pages est comprimé dans un fichier .zip.
    * Chaque fichier contenu dans le fichier .zip représente une page du rapport
    * Les noms des pages sont les mêmes que les valeurs de retour des API [Obtenir des pages](https://docs.microsoft.com/rest/api/power-bi/reports/getpages) ou [Obtenir des pages dans le groupe](https://docs.microsoft.com/rest/api/power-bi/reports/getpagesingroup)

## <a name="usage-examples"></a>Exemples d'utilisation

Vous pouvez utiliser la fonctionnalité d’exportation de différentes manières. Voici quelques exemples :

* **Bouton Envoyer à l’impression** : dans votre application, créez un bouton qui, lorsque vous cliquez dessus, déclenche un travail d’exportation. Le travail peut exporter le rapport visualisé dans un fichier .pdf ou .pptx et, une fois qu’il est terminé, l’utilisateur peut recevoir le fichier sous forme de téléchargement. À l’aide de signets, vous pouvez exporter le rapport dans un état spécifique, y compris des filtres configurés, des segments et des paramètres supplémentaires. Étant donné que l’API est asynchrone, la mise à disposition du fichier peut prendre un certain temps.

* **Pièce jointe d’e-mail** : envoyer un e-mail automatisé à intervalles définis, avec un rapport .pdf en pièce jointe. Ce scénario peut être utile si vous souhaitez automatiser l’envoi d’un rapport hebdomadaire aux dirigeants.

## <a name="using-the-api"></a>Utilisation de l’API

Avant d’utiliser l’API, vérifiez que les [paramètres de locataire administrateurs](../../service-admin-portal.md#tenant-settings) suivants sont activés :
* **Exporter les rapports comme présentations PowerPoint ou documents PDF** : activé par défaut.
* **Exporter des rapports en tant que fichiers image** : nécessaire uniquement pour les fichiers *.png*, et désactivé par défaut.

L’API est asynchrone. Lorsque l’API [exportToFile](https://docs.microsoft.com/rest/api/power-bi/reports/exporttofile) est appelée, elle déclenche un travail d’exportation. Après avoir déclenché un travail d’exportation, utilisez l’[interrogation](https://docs.microsoft.com/rest/api/power-bi/reports/getexporttofilestatus) pour suivre le travail jusqu’à ce qu’il soit terminé.

Pendant l’interrogation, l’API retourne un nombre qui représente la quantité de travail effectué. Le travail dans chaque travail d’exportation est calculé en fonction du nombre de pages du rapport. Toutes les pages ont le même poids. Si, par exemple, vous exportez un rapport de 10 pages et que l’interrogation retourne 70, cela signifie que l’API a traité sept des 10 pages du travail d’exportation.

Une fois l’exportation terminée, l’appel de l’API d’interrogation retourne une [URL Power BI](https://docs.microsoft.com/rest/api/power-bi/reports/getfileofexporttofile) pour obtenir le fichier. L’URL sera disponible pendant 24 heures.

## <a name="supported-features"></a>Fonctionnalités prises en charge

### <a name="selecting-which-pages-to-print"></a>Sélection des pages à imprimer

Spécifiez les pages à imprimer en fonction de la valeur de retour [Obtenir des pages](https://docs.microsoft.com/rest/api/power-bi/reports/getpages) ou [Obtenir des pages dans le groupe](https://docs.microsoft.com/rest/api/power-bi/reports/getpagesingroup). Vous pouvez également spécifier l’ordre des pages que vous exportez.

### <a name="bookmarks"></a>Signets

 Vous pouvez utiliser l’API `exportToFile` pour exporter programmatiquement un rapport dans un état spécifique après lui avoir appliqué des filtres. Pour ce faire, utilisez les fonctionnalités [Signets](../../consumer/end-user-bookmarks.md). Pour exporter un rapport à l’aide de signets, utilisez l’[API JavaScript de signets](https://github.com/Microsoft/PowerBI-JavaScript/wiki/Bookmarks).

 Par exemple, vous pouvez utiliser la méthode de signet `capturedBookmark.state` pour capturer les modifications apportées par un utilisateur spécifique à un rapport, puis l’exporter dans son état actuel.

[Les signets personnels](../../consumer/end-user-bookmarks.md#personal-bookmarks) et [les filtres persistants](https://powerbi.microsoft.com/blog/announcing-persistent-filters-in-the-service/) ne sont pas pris en charge.

### <a name="authentication"></a>Authentification

Vous pouvez vous authentifier avec un utilisateur (ou un utilisateur maître) ou un [principal de service](embed-service-principal.md).

### <a name="row-level-security-rls"></a>Sécurité au niveau de la ligne (RLS)

La [Sécurité au niveau de la ligne (RLS)](embedded-row-level-security.md) permet d’exporter un rapport mentionnant des données qui ne sont accessibles qu’à certains utilisateurs. Par exemple, si vous exportez un rapport de ventes défini avec des rôles régionaux, vous pouvez filtrer programmatiquement le rapport de façon à n’afficher qu’une région précise.

Pour exporter avec RLS, vous devez disposer des autorisations suivantes :
* Écrire et partager à nouveau des autorisations pour le jeu de données auquel le rapport est connecté
* Si le rapport se trouve dans un espace de travail v1, vous devez être l’administrateur de l’espace de travail.
* Si le rapport se trouve dans un espace de travail v2, vous devez être membre de l’espace de travail ou administrateur.

### <a name="data-protection"></a>Protection des données

Les formats .pdf et .pptx prennent en charge les [étiquettes de sensibilité](../../admin/service-security-data-protection-overview.md#sensitivity-labels-in-power-bi). Si vous exportez un rapport doté d’une étiquette de sensibilité au format .pdf ou .pptx, le fichier exporté affiche le rapport avec son étiquette de sensibilité.

Un rapport avec une étiquette de sensibilité ne peut pas être exporté au format .pdf ou .pptx à l’aide d’un [principal de service](embed-service-principal.md).

### <a name="localization"></a>Localisation

Lorsque vous utilisez l’API `exportToFile`, vous pouvez transmettre la valeur locale souhaitée. Les paramètres de localisation affectent la façon dont le rapport est affiché, par exemple en modifiant la mise en forme en fonction de la valeur locale sélectionnée.

## <a name="concurrent-requests"></a>Demandes simultanées

`exportToFile` prend en charge les demandes de travaux d’exportation simultanées. Le tableau ci-dessous indique le nombre de travaux que vous pouvez exécuter en même temps, en fonction de la référence SKU sur laquelle votre rapport réside. Les demandes simultanées font référence aux pages du rapport. Par exemple, 20 pages dans une demande d’exportation sur une référence SKU A6 seront traitées simultanément. Ceci prendra à peu près le même temps que l’envoi de 20 demandes d’exportation d’une page chacune.

Un travail dépassant le nombre de demandes simultanées ne se termine pas. Par exemple, si vous exportez trois pages dans une référence SKU A1, le premier travail s’exécute et les deux derniers attendent les deux cycles d’exécution suivants.

|Référence SKU Azure  |Référence SKU Office  |Nombre maximal de pages de rapport simultanées  |
|-----------|------------|-----------|
|A1         |EM1         |1          |
|A2         |EM2         |2          |
|A3         |EM3         |3          |
|A4         |P1          |6          |
|A5         |P2          |12         |
|A6         |P3          |24         |

## <a name="limitations"></a>Limites

* Le rapport que vous exportez doit résider sur une capacité Premium ou Embedded.
* Le jeu de données du rapport que vous exportez doit résider sur une capacité Premium ou Embedded.
* Pour la préversion publique, le nombre de pages de rapport Power BI exportées par heure est limité à 50 par capacité.
* Les rapports exportés ne peuvent pas dépasser une taille de fichier de 250 Mo.
* Lors de l’exportation en tant que fichier .png, les étiquettes de sensibilité ne sont pas prises en charge.
* Un rapport avec une étiquette de sensibilité ne peut pas être exporté au format .pdf ou .pptx à l’aide d’un [principal de service](embed-service-principal.md).
* 30 pages peuvent être incluses dans un rapport exporté. Si le rapport contient plus de pages, l’API retourne une erreur et le travail d’exportation est annulé.
* [Les signets personnels](../../consumer/end-user-bookmarks.md#personal-bookmarks) et [les filtres persistants](https://powerbi.microsoft.com/blog/announcing-persistent-filters-in-the-service/) ne sont pas pris en charge.
* Les visuels Power BI répertoriés ci-dessous ne sont pas pris en charge. Lorsqu’un rapport contenant ces visuels est exporté, les parties du rapport contenant ces visuels ne sont pas rendues et un symbole d’erreur s’affiche.
    * Visuels Power BI non certifiés
    * Visuels R
    * PowerApps
    * Visuels Python
    * Visio

## <a name="code-examples"></a>Exemples de code

Lorsque vous créez un travail d’exportation, il y a trois étapes à suivre :

1. Envoi d’une demande d’exportation.
2. Interrogation.
3. Obtention du fichier.

Cette section fournit des exemples pour chaque étape.

### <a name="step-1---sending-an-export-request"></a>Étape 1 : envoi d’une demande d’exportation

La première étape consiste à envoyer une demande de rapport. Dans cet exemple, une demande d’exportation est envoyée pour une page spécifique.

```csharp
/////// Export sample ///////
private async Task<string> PostExportRequest(
    Guid reportId,
    Guid groupId,
    FileFormat format,
    IList<string> pageNames = null /* Get the page names from the GetPages API */)
{
    var powerBIReportExportConfiguration = new PowerBIReportExportConfiguration
    {
        Settings = new ExportReportSettings
        {
            Locale = "en-us",
        },
        // Note that page names differ from the page display names.
        // To get the page names use the GetPages API.
        Pages = pageNames?.Select(pn => new ExportReportPage(Name = pn)).ToList(),
    };
    var exportRequest = new ExportReportRequest
    {
        Format = format,
        PowerBIReportConfiguration = powerBIReportExportConfiguration,
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
    const int c_secToMillisec = 1000;
    do
    {
        if (DateTime.UtcNow.Subtract(startTime).TotalMinutes > timeOutInMinutes || token.IsCancellationRequested)
        {
            // Error handling for timeout and cancellations 
            return null;
        }
        var httpMessage = await Client.Reports.GetExportToFileStatusInGroupWithHttpMessagesAsync(groupId, reportId, exportId);
        exportStatus = httpMessage.Body;
        // You can track the export progress using the PercentComplete that's part of the response
        SomeTextBox.Text = string.Format("{0} (Percent Complete : {1}%)", exportStatus.Status.ToString(), exportStatus.PercentComplete);
        if (exportStatus.Status == ExportState.Running || exportStatus.Status == ExportState.NotStarted)
        {
            // The recommended waiting time between polling requests can be found in the RetryAfter header
            // Note that this header is only populated when the status is either Running or NotStarted
            var retryAfter = httpMessage.Response.Headers.RetryAfter;
            var retryAfterInSec = retryAfter.Delta.Value.Seconds;
            await Task.Delay(retryAfterInSec * c_secToMillisec);
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
        var fileStream = await Client.Reports.GetFileOfExportToFileAsync(groupId, reportId, export.Id);
        return new ExportedFile
        {
            FileStream = fileStream,
            FileSuffix = export.ResourceFileExtension,
        };
    }
    return null;
}
public class ExportedFile
{
    public Stream FileStream;
    public string FileSuffix;
}
```

### <a name="end-to-end-example"></a>Exemple de bout en bout

Il s’agit d’un exemple de bout en bout pour l’exportation d’un rapport. Il comprend les étapes suivantes :
1. [Envoi de la demande d'exportation](#step-1---sending-an-export-request).
2. [Interrogation](#step-2---polling).
3. [Obtention du fichier](#step-3---getting-the-file).

```csharp
private async Task<ExportedFile> ExportPowerBIReport(
    Guid reportId,
    Guid groupId,
    FileFormat format,
    int pollingtimeOutInMinutes,
    CancellationToken token,
    IList<string> pageNames = null /* Get the page names from the GetPages API */)
{
    try
    {
        var exportId = await PostExportRequest(reportId, groupId, format, pageNames);
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
>[Exporter un rapport paginé dans un fichier](export-paginated-report.md)

> [!div class="nextstepaction"]
>[Incorporer pour vos clients](embed-sample-for-customers.md)

> [!div class="nextstepaction"]
>[Incorporer pour votre organisation](embed-sample-for-your-organization.md)
