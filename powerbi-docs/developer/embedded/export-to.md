---
title: API zum Exportieren von Power BI-Berichten
description: Erfahren Sie, wie Sie einen eingebetteten Power BI-Bericht exportieren.
author: KesemSharabi
ms.author: kesharab
ms.topic: how-to
ms.service: powerbi
ms.subservice: powerbi-developer
ms.date: 03/01/2020
ms.openlocfilehash: eb08eb2ed8ecead4e5a2437cafced6194f05acbe
ms.sourcegitcommit: a175faed9378a7d040a08ced3e46e54503334c07
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/18/2020
ms.locfileid: "79492305"
---
# <a name="export-report-to-file-preview"></a>Exportieren eines Berichts in eine Datei (Vorschau)

Die API `exportToFile` ermöglicht das Exportieren eines Power BI-Berichts mithilfe eines REST-Aufrufs. Die folgenden Dateiformate werden unterstützt:
* **PPTX** (PowerPoint)
* **PDF**
* **PNG**
    * Beim Exportieren in eine PNG-Datei wird ein Bericht mit mehreren Seiten in eine ZIP-Datei komprimiert.
    * Jede Datei in der PNG-ZIP-Datei repräsentiert eine Berichtsseite.
    * Die Seitennamen entsprechen den Rückgabewerten der APIs [Seiten abrufen](https://docs.microsoft.com/rest/api/power-bi/reports/getpages) bzw. [Seiten in Gruppe abrufen](https://docs.microsoft.com/rest/api/power-bi/reports/getpagesingroup).

## <a name="usage-examples"></a>Anwendungsbeispiele

Sie können das Exportfeature auf unterschiedlichste Weise verwenden. Hier sind einige Beispiele angegeben:

* **Schaltfläche zum Drucken**: Erstellen Sie eine Schaltfläche in Ihrer Anwendung, die einen Exportauftrag auslöst, wenn darauf geklickt wird. Der Auftrag kann den angezeigten Bericht als PDF- oder PPTX-Datei exportieren. Nach Abschluss des Auftrags kann der Benutzer die Datei als Download erhalten. Mithilfe von Lesezeichen lässt sich der Bericht in einem bestimmten Zustand exportieren, einschließlich konfigurierter Filter, Slicer und weiterer Einstellungen. Da die API asynchron ausgeführt wird, kann es einige Zeit dauern, bis die Datei verfügbar ist.

* **E-Mail-Anlage**: Hiermit können E-Mails mit angefügtem Bericht im PDF-Format in festgelegten Intervallen gesendet werden. Dieses Szenario kann hilfreich sein, wenn Sie das Senden wöchentlicher Berichte an Vorgesetzte automatisieren möchten.

## <a name="using-the-api"></a>Verwenden der API

Bevor Sie die API verwenden, vergewissern Sie sich, dass die folgenden [Mandanteneinstellungen für den Administrator](../../service-admin-portal.md#tenant-settings) aktiviert sind:
* **Berichte als PowerPoint-Präsentationen oder PDF-Dokumente exportieren**: standardmäßig aktiviert.
* **Berichte als Bilddateien exportieren**: nur für das PNG-Format erforderlich und standardmäßig deaktiviert.

Die API wird asynchron ausgeführt. Wenn die API [exportToFile](https://docs.microsoft.com/rest/api/power-bi/reports/exporttofile) aufgerufen wird, löst sie einen Exportauftrag aus. Verwenden Sie nach dem Auslösen des Exportauftrags einen [Abrufvorgang](https://docs.microsoft.com/rest/api/power-bi/reports/getexporttofilestatus), um den Auftrag bis zum Abschluss nachzuverfolgen.

Während des Abrufvorgangs gibt die API eine Zahl zurück, die den Umfang an abgeschlossenen Aufgaben darstellt. Die Aufgaben in jedem Exportauftrag werden basierend auf der Anzahl der Seiten im Bericht berechnet. Alle Seiten weisen dieselbe Gewichtung auf. Wenn Sie beispielsweise einen Bericht mit 10 Seiten exportieren und der Abrufvorgang die Zahl 70 zurückgibt, hat die API 7 der 10 Seiten im Exportauftrag verarbeitet.

Wenn der Export abgeschlossen ist, gibt der API-Aufruf für den Abrufvorgang eine [Power BI-URL](https://docs.microsoft.com/rest/api/power-bi/reports/getfileofexporttofile) zurück, unter der die Datei heruntergeladen werden kann. Die URL ist 24 Stunden lang verfügbar.

## <a name="supported-features"></a>Unterstützte Features

### <a name="selecting-which-pages-to-print"></a>Auswählen der zu druckenden Seiten

Geben Sie anhand des Rückgabewerts von [Seiten abrufen](https://docs.microsoft.com/rest/api/power-bi/reports/getpages) oder [Seiten in Gruppe abrufen](https://docs.microsoft.com/rest/api/power-bi/reports/getpagesingroup) an, welche Seiten gedruckt werden sollen. Sie können auch die Reihenfolge der Seiten angeben, die Sie exportieren möchten.

### <a name="bookmarks"></a>Lesezeichen

 Sie können die `exportToFile`-API verwenden, um einen Bericht programmgesteuert in einem bestimmten Zustand zu exportieren, nachdem Sie Filter darauf angewendet haben. Dies erfolgt über die verschiedenen Funktionen von [Lesezeichen](../../consumer/end-user-bookmarks.md). Um einen Bericht anhand von Lesezeichen zu exportieren, verwenden Sie die [JavaScript-API für Lesezeichen](https://github.com/Microsoft/PowerBI-JavaScript/wiki/Bookmarks).

 Sie können z. B. die `capturedBookmark.state`-Methode eines Lesezeichens verwenden, um die Änderungen zu erfassen, die ein bestimmter Benutzer an einem Bericht vorgenommen hat, und den Bericht dann im aktuellen Zustand zu exportieren.

[Persönliche Lesezeichen](../../consumer/end-user-bookmarks.md#personal-bookmarks) und [permanente Filter](https://powerbi.microsoft.com/blog/announcing-persistent-filters-in-the-service/) werden nicht unterstützt.

### <a name="authentication"></a>Authentifizierung

Die Authentifizierung kann nur mit einem Benutzer (oder einem Hauptbenutzer) erfolgen. [Dienstprinzipale](embed-service-principal.md) werden derzeit nicht unterstützt.

### <a name="row-level-security-rls"></a>Sicherheit auf Zeilenebene

Mit [Sicherheit auf Zeilenebene](embedded-row-level-security.md) (Row-Level Security, RLS) können Sie einen Bericht mit Daten exportieren, die nur für bestimmte Benutzer sichtbar sind. Wenn Sie beispielsweise einen Umsatzbericht exportieren, der mit regionalen Rollen definiert ist, können Sie den Bericht programmgesteuert filtern, sodass nur eine bestimmte Region angezeigt wird.

Zum Exportieren mit RLS benötigen Sie die folgenden Berechtigungen:
* Berechtigungen zum Schreiben und erneuten Freigeben für das Dataset, mit dem der Bericht verknüpft ist.
* Wenn sich der Bericht in einem Arbeitsbereich der Version 1 befindet, müssen Sie Administrator des Arbeitsbereichs sein.
* Wenn sich der Bericht in einem Arbeitsbereich der Version 2 befindet, müssen Sie Mitglied oder Administrator des Arbeitsbereichs sein.

### <a name="data-protection"></a>Datenschutz

Die Formate PDF und PPTX unterstützen [Vertraulichkeitsbezeichnungen](../../admin/service-security-data-protection-overview.md#sensitivity-labels-in-power-bi). Wenn Sie einen Bericht mit einer Vertraulichkeitsbezeichnung in eine PDF- oder PPTX-Datei exportieren, zeigt die exportierte Datei den Bericht mit der Vertraulichkeitsbezeichnung an.

### <a name="localization"></a>Lokalisierung

Wenn Sie die `exportToFile`-API verwenden, können Sie Ihr gewünschtes Gebietsschema übergeben. Die Lokalisierungseinstellungen wirken sich auf die Anzeige des Berichts aus. Beispielsweise ändert sich die Formatierung basierend auf dem ausgewählten Gebietsschema.

## <a name="concurrent-requests"></a>Gleichzeitige Anforderungen

`exportToFile` unterstützt gleichzeitige Anforderungen für Exportaufträge. Die folgende Tabelle zeigt die Anzahl von Aufträgen, die Sie gleichzeitig ausführen können – je nach SKU, in der sich Ihr Bericht befindet. Gleichzeitige Anforderungen beziehen sich auf Berichtsseiten. Ein Beispiel: 20 Seiten in einer Exportanforderung in einer A6-SKU werden gleichzeitig verarbeitet. Dieser Vorgang dauert etwa so lange wie das Senden von 20 Exportanforderungen mit jeweils einer Seite.

Ein Auftrag, bei dem die Anzahl gleichzeitiger Anforderungen überschritten ist, wird nicht abgeschlossen. Wenn Sie beispielsweise drei Seiten in einer A1-SKU exportieren, wird der erste Auftrag ausgeführt, und die beiden anderen warten auf die nächsten beiden Ausführungszyklen.

|Azure-SKU  |Office-SKU  |Maximale Anzahl von gleichzeitigen Berichtsseiten  |
|-----------|------------|-----------|
|A1         |EM1         |1          |
|A2         |EM2         |2          |
|A3         |EM3         |3          |
|A4         |P1          |6          |
|A5         |P2          |12         |
|A6         |P3          |24         |

## <a name="limitations"></a>Einschränkungen

* Der Bericht, den Sie exportieren möchten, muss sich in Premium- oder Embedded-Kapazität befinden.
* Das Dataset des Berichts, den Sie exportieren möchten, muss sich in Premium- oder Embedded-Kapazität befinden.
* Für die öffentliche Vorschau ist die Anzahl der pro Stunde exportierten Power BI-Berichtsseiten pro Kapazität auf 50 begrenzt.
* Exportierte Berichte dürfen eine Dateigröße von 250 MB nicht überschreiten.
* Beim Exportieren in das PNG-Format werden Vertraulichkeitsbezeichnungen nicht unterstützt.
* [Dienstprinzipale](embed-service-principal.md) werden nicht unterstützt.
* Ein exportierter Bericht darf maximal 30 Seiten umfassen. Wenn der Bericht mehr Seiten enthält, gibt die API einen Fehler zurück, und der Exportauftrag wird abgebrochen.
* [Persönliche Lesezeichen](../../consumer/end-user-bookmarks.md#personal-bookmarks) und [permanente Filter](https://powerbi.microsoft.com/blog/announcing-persistent-filters-in-the-service/) werden nicht unterstützt.
* Paginierte Berichte werden derzeit nicht unterstützt.
* Die unten aufgeführten Power BI-Visuals werden nicht unterstützt. Wenn ein Bericht mit diesen Visuals exportiert wird, werden die Teile des Berichts, die diese Visuals enthalten, nicht gerendert, und es wird ein Fehlersymbol angezeigt.
    * Nicht zertifizierte Power BI-Visuals
    * R-Visuals
    * PowerApps
    * Python-Visuals
    * Visio

## <a name="code-examples"></a>Codebeispiele

Beim Erstellen eines Exportauftrags müssen drei Schritte ausgeführt werden:

1. Senden einer Exportanforderung
2. Abrufvorgang
3. Herunterladen der Datei

Der folgende Abschnitt enthält Beispiele für jeden Schritt.

### <a name="step-1---sending-an-export-request"></a>Schritt 1: Senden einer Exportanforderung

Der erste Schritt besteht darin, eine Exportanforderung zu senden. In diesem Beispiel wird eine Exportanforderung für eine bestimmte Seite gesendet.

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

### <a name="step-3---getting-the-file"></a>Schritt 3: Herunterladen der Datei

Sobald der Abrufvorgang eine URL zurückgibt, verwenden Sie dieses Beispiel, um die empfangene Datei herunterzuladen.

```csharp
private readonly IDictionary<string, string> mediaTypeToSuffix = new Dictionary<string, string>
    {
        { "image/png", "png" },
        { "application/zip", "zip" },
        { "application/pdf", "pdf" },
        { "application/vnd.openxmlformats-officedocument.presentationml.presentation", "pptx" },
    };

private async Task<ExportedFile> GetExportedFile(
    Guid reportId,
    Guid groupId,
    Export export /* Get from the GetExportStatusAsync response */)
    {
        if (export.Status == ExportState.Succeeded)
        {
            var httpMessage = await Client.Reports.GetFileOfExportToFileInGroupWithHttpMessagesAsync(groupId, reportId, export.Id);
            var mediaType = httpMessage.Response.Content.Headers.ContentType.ToString().ToLower();

            if (!mediaTypeToSuffix.TryGetValue(mediaType, out string fileSuffix))
            {
                // Handle unexpected errors
            }
            else
            {
                return new ExportedFile
                {
                    FileStream = httpMessage.Body,
                    FileSuffix = fileSuffix,
                };
            }
        }

        return null;
    }

public class ExportedFile
{
    public Stream FileStream;
    public string FileSuffix;
}
```

### <a name="end-to-end-example"></a>Vollständiges Beispiel

Hier finden Sie ein vollständiges Beispiel für den Export eines Berichts. Das Beispiel umfasst die folgenden Phasen:
1. [Senden einer Exportanforderung](#step-1---sending-an-export-request)
2. [Abrufvorgang](#step-2---polling)
3. [Herunterladen der Datei](#step-3---getting-the-file)

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

## <a name="next-steps"></a>Nächste Schritte

Sehen Sie sich an, wie Sie Inhalte für Ihre Kunden und Ihre Organisation einbetten:

> [!div class="nextstepaction"]
>[Inhalte für Ihre Kunden einbetten](embed-sample-for-customers.md)

> [!div class="nextstepaction"]
>[Embed for your organization (Einbetten für Ihre Organisation)](embed-sample-for-your-organization.md)
