---
title: API zum Exportieren von Power BI-Berichten
description: Erfahren Sie, wie Sie einen eingebetteten paginierten Power BI-Bericht exportieren.
author: KesemSharabi
ms.author: kesharab
ms.topic: conceptual
ms.service: powerbi
ms.subservice: powerbi-developer
ms.date: 04/05/2020
ms.openlocfilehash: acb13a70ea4693f447b70aa59da07cd91639de25
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "81268763"
---
# <a name="export-paginated-report-to-file-preview"></a>Exportieren des paginierten Berichts in eine Datei (Vorschau)

Die API `exportToFile` ermöglicht das Exportieren eines paginierten Power BI-Berichts mithilfe eines REST-Aufrufs. Die folgenden Dateiformate werden unterstützt:
* **.pptx** (PowerPoint)
* **.pdf**
* **.xlsx** (Excel)
* **.dox** (Word)
* **.csv**
* **.xml**
* **.mhtml**
* **Bild**
    * Legen Sie beim Exportieren eines Bilds das Bildformat über die `OutputFormat`-Formateinstellung fest.
    * Die unterstützten OutputFormat-Werte sind: .bmp, .emf, .gif, .jpeg, .png oder .tiff (Standard).

## <a name="usage-examples"></a>Anwendungsbeispiele

Sie können das Exportfeature auf unterschiedlichste Weise verwenden. Hier sind einige Beispiele angegeben:

* **Schaltfläche zum Drucken**: Erstellen Sie eine Schaltfläche in Ihrer Anwendung, die einen Exportauftrag auslöst, wenn darauf geklickt wird. Der Auftrag kann den angezeigten Bericht als PDF- oder PPTX-Datei exportieren. Nach Abschluss des Auftrags kann der Benutzer die Datei als Download erhalten. Mit Berichtsparametern und Formateinstellungen können Sie den Bericht in einem bestimmten Zustand exportieren, einschließlich gefilterter Daten, benutzerdefinierter Seitengrößen und weiteren formatspezifischen Einstellungen. Da die API asynchron ausgeführt wird, kann es einige Zeit dauern, bis die Datei verfügbar ist.

* **E-Mail-Anlage**: Hiermit können E-Mails mit angefügtem Bericht im PDF-Format in festgelegten Intervallen gesendet werden. Dieses Szenario kann hilfreich sein, wenn Sie das Senden wöchentlicher Berichte an Vorgesetzte automatisieren möchten.

## <a name="using-the-api"></a>Verwenden der API

Die API wird asynchron ausgeführt. Wenn die API [exportToFile](https://docs.microsoft.com/rest/api/power-bi/reports/exporttofile) aufgerufen wird, löst sie einen Exportauftrag aus. Verwenden Sie nach dem Auslösen des Exportauftrags einen [Abrufvorgang](https://docs.microsoft.com/rest/api/power-bi/reports/getexporttofilestatus), um den Auftrag bis zum Abschluss nachzuverfolgen.

Wenn der Export abgeschlossen ist, gibt der API-Aufruf für den Abrufvorgang eine [Power BI-URL](https://docs.microsoft.com/rest/api/power-bi/reports/getfileofexporttofile) zurück, unter der die Datei heruntergeladen werden kann. Die URL ist 24 Stunden lang verfügbar.

## <a name="supported-features"></a>Unterstützte Features

### <a name="format-settings"></a>Formateinstellungen

Geben Sie eine Auswahl von Formateinstellungen für jedes Dateiformat an. Die unterstützten Eigenschaften und Werte entsprechen den [Parametern für Geräteinformationen](../../paginated-reports/report-builder-url-parameters.md#report-commands-rdl) für Parameter für paginierte Berichts-URLs.

Im Folgenden finden Sie zwei Beispiele, eines zum Exportieren der ersten vier Seiten eines Berichts mithilfe der Berichtsseitengröße in eine PPTX-Datei, das andere Beispiel zum Exportieren der dritten Seite eines Berichts in eine JPEG-Datei.

**Exportieren der ersten vier Seiten in eine PPTX-Datei**

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

**Exportieren der dritten Seite in eine JPEG-Datei**

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

### <a name="report-parameters"></a>Berichtsparameter

Sie können die `exportToFile`-API verwenden, um einen Bericht programmgesteuert mit mehreren Berichtsparametern zu exportieren. Dieser Export erfolgt über die Eigenschaften der [Berichtsparameter](../../paginated-reports/paginated-reports-parameters.md).

Hier sehen Sie ein Beispiel zum Festlegen der Berichtsparameterwerte.

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

### <a name="authentication"></a>Authentication

Die Authentifizierung kann mit einem Benutzer (oder einem Hauptbenutzer) oder einem [Dienstprinzipal](embed-service-principal.md) erfolgen.

### <a name="row-level-security-rls"></a>Sicherheit auf Zeilenebene

Wenn Sie ein Power BI-Dataset verwenden, für das als Datenquelle die Sicherheit auf Zeilenebene (Row Level Security, RLS) definiert ist, können Sie einen Bericht exportieren, der Daten darstellt, die nur für bestimmte Benutzer sichtbar sind. Wenn Sie beispielsweise einen Umsatzbericht exportieren, der mit regionalen Rollen definiert ist, können Sie den Bericht programmgesteuert filtern, sodass nur eine bestimmte Region angezeigt wird.

Zum Exportieren mit RLS müssen Sie über Leseberechtigungen für das Power BI-Dataset verfügen, das der Bericht als Datenquelle verwendet.

Nachstehend sehen Sie ein Beispiel für die Bereitstellung eines effektiven Benutzernamens für RLS.

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

## <a name="code-examples"></a>Codebeispiele

Das SDK der Power BI-API, das in den Codebeispielen verwendet wird, kann [hier](https://www.nuget.org/packages/Microsoft.PowerBI.Api) heruntergeladen werden.

Beim Erstellen eines Exportauftrags müssen drei Schritte ausgeführt werden:

1. Senden einer Exportanforderung
2. Abrufvorgang
3. Herunterladen der Datei

Der folgende Abschnitt enthält Beispiele für jeden Schritt.

### <a name="step-1---sending-an-export-request"></a>Schritt 1: Senden einer Exportanforderung

Der erste Schritt besteht darin, eine Exportanforderung zu senden. In diesem Beispiel wird eine Exportanforderung für einen bestimmten Seitenbereich, eine bestimmte Seitengröße sowie für Berichtsparameter gesendet.

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

### <a name="step-2---polling"></a>Schritt 2: Abrufvorgang

Nachdem Sie die Exportanforderung gesendet haben, verwenden Sie einen Abrufvorgang, um zu ermitteln, wann die Datei bereit sein wird.

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

### <a name="step-3---getting-the-file"></a>Schritt 3: Herunterladen der Datei

Sobald der Abrufvorgang eine URL zurückgibt, verwenden Sie dieses Beispiel, um die empfangene Datei herunterzuladen.

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

### <a name="end-to-end-example"></a>Vollständiges Beispiel

Hier finden Sie ein vollständiges Beispiel für den Export eines Berichts. Das Beispiel umfasst die folgenden Phasen:
1. [Senden einer Exportanforderung](#step-1---sending-an-export-request)
2. [Abrufvorgang](#step-2---polling)
3. [Herunterladen der Datei](#step-3---getting-the-file)

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

## <a name="next-steps"></a>Weitere Schritte

Sehen Sie sich an, wie Sie Inhalte für Ihre Kunden und Ihre Organisation einbetten:

> [!div class="nextstepaction"]
>[Exportieren eines Berichts in eine Datei](export-to.md)

> [!div class="nextstepaction"]
>[Inhalte für Ihre Kunden einbetten](embed-sample-for-customers.md)

> [!div class="nextstepaction"]
>[Embed for your organization (Einbetten für Ihre Organisation)](embed-sample-for-your-organization.md)