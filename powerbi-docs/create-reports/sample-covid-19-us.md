---
title: Beispiel zur Nachverfolgung von COVID-19-Daten für US-Behörden auf bundesstaatlicher und kommunaler Ebene
description: Laden Sie den Beispielbericht mit US-Daten zur COVID-19-Pandemie auf bundesstaatlicher und kommunaler Ebene herunter, und ändern Sie ihn.
author: LukaszPawlowski-MS
ms.reviewer: ''
ms.custom: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 04/06/2020
ms.author: lukaszp
LocalizationGroup: Samples
ms.openlocfilehash: 66e76c21e7d5171d24ff1518745a35947aa7ca42
ms.sourcegitcommit: e7fda395b47e404c61e961a60816b7a1b0182759
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/08/2020
ms.locfileid: "80979774"
---
# <a name="covid-19-tracking-sample-for-us-state-and-local-governments"></a>Beispiel zur Nachverfolgung von COVID-19-Daten für US-Behörden auf bundesstaatlicher und kommunaler Ebene

Mithilfe des vom Power BI-Team erstellten Beispiels zur Nachverfolgung von COVID-19-Daten können bundesstaatliche und kommunale Behörden in den USA einen interaktiven Bericht zu COVID-19 veröffentlichen oder anpassen. Mit Power BI Desktop können COVID-19-Daten analysiert und visualisiert werden, um die Menschen einer Stadt, eines Countys, eines Bundesstaats oder des gesamten Landes zu informieren. Über die Power BI-Webveröffentlichung können die Behörden den Bericht dann öffentlich freigeben und so die Bürger informieren. In diesem Artikel lernen Sie verschiedene Optionen kennen, wie Sie interaktive Power BI-Visualisierungen in einer Veröffentlichung, einem Blog oder auf einer Website verwenden.

:::image type="content" source="media/sample-covid-19-us/covid-19-us-tracking-sample.png" alt-text="Beispiel für COVID-19-Daten aus den USA":::

In diesem Artikel wird Folgendes behandelt:

- Kopieren von Einbettungscode und Platzieren auf Ihrer eigenen Website 
- Vornehmen von Anpassungen, wie z. B. dem Anzeigen eines bestimmten US-Bundesstaats
- Veröffentlichen im Power BI-Dienst
- Veröffentlichen im Web 
- Kombinieren der Daten mit Daten aus einer anderen Quelle 

## <a name="prerequisites"></a>Voraussetzungen

Vor der Verwendung von Power BI sind folgende Schritte erforderlich:

- Laden Sie die kostenlose App [Power BI Desktop](https://powerbi.microsoft.com/desktop/) herunter.
- Registrieren Sie sich beim [Power BI-Dienst](https://powerbi.microsoft.com/get-started/).

## <a name="option-1-pre-built-embed-code"></a>Option 1: Verwenden von vorgefertigtem Einbettungscode

Microsoft hat den Beispielbericht veröffentlicht und einen Einbettungscode für die Webveröffentlichung erstellt. Mithilfe des Einbettungscodes können Sie das gesamte Beispiel einbetten (einschließlich der Anzeige aller Bundesstaaten) und anschließend auf Ihrer Website einen Drilldown zur Ebene eines Bundesstaats oder eines Countys ausführen. Lesen Sie vor dem Veröffentlichen der Daten die [Haftungsausschlüsse](#disclaimers) weiter unten in diesem Artikel.

Wenn Sie die interaktive Grafik auf Ihrer Website einbinden möchten, kopieren Sie den folgenden Einbettungscode, und fügen Sie ihn an der Stelle ein, an der die Grafik auf Ihrer Webseite angezeigt werden soll.  

```
<iframe width="1600" height="900" src="https://app.powerbi.com/view?r=eyJrIjoiMmI2ZjExMzItZTcwNy00YmUwLWFlMTAtYTUxYzVjODZmYjA5IiwidCI6ImMxMzZlZWMwLWZlOTItNDVlMC1iZWFlLTQ2OTg0OTczZTIzMiIsImMiOjF9" frameborder="0" allowFullScreen="true"></iframe>
```

Der Einbettungscode ist ein iFrame-Element im HTML-Format, das Sie in eine beliebige HTML-Seite einfügen können. Passen Sie die Breite und Höhe des iFrame-Elements entsprechend Ihrer Website an. Der Beispielbericht wurde im Format 16:9 erstellt. Wählen Sie daher eine Größe aus, bei der dieses Seitenverhältnis beibehalten wird. Bei korrekter Implementierung wird die Grafik ohne einen grauen Rahmen angezeigt. Vor der Durchführung dieser Anpassungen ist es hilfreich, die [Tipps und Tricks für die iFrame-Höhe und -Breite](../service-publish-to-web.md#tips-and-tricks-for-iframe-height-and-width) zu lesen.

## <a name="option-2-customize-the-sample-power-bi-file"></a>Option 2: Anpassen der Power BI-Beispieldatei

Die Power BI-Datei enthält die Daten und die interaktive Grafik im PBIX-Dateiformat, das Sie in Power BI Desktop bearbeiten können.  

Eine typische Anpassung besteht etwa darin, den Bericht so zu filtern, dass nur ein bestimmter Bundesstaat angezeigt wird. Anschließend können Sie für den angepassten Bericht Ihren eigenen Einbettungscode für die Webveröffentlichung erstellen.

USAFacts stellt die Daten im Rahmen einer Creative Commons-Lizenz bereit, für die eine Namensnennung erforderlich ist. Lesen Sie vor dem Veröffentlichen dieser Daten die [Haftungsausschlüsse](#disclaimers).

Laden Sie zunächst die PBIX-Datei [hier](https://go.microsoft.com/fwlink/?linkid=2125058) herunter.

### <a name="update-your-report"></a>Filtern des Berichts 

1. Falls Sie dies noch nicht getan haben, laden Sie die neueste Version der kostenlosen App [Power BI Desktop](https://powerbi.microsoft.com/desktop/) herunter. 

2. Falls Sie dies noch nicht getan haben, laden Sie die [PBIX-Datei](https://go.microsoft.com/fwlink/?linkid=2125058) herunter, und öffnen Sie diese in Power BI Desktop.

3. Wenn Sie einen bestimmten Bundesstaat anzeigen möchten, klicken Sie auf den Pfeil, um den Bereich „Filter“ zu erweitern.

    :::image type="content" source="media/sample-covid-19-us/power-bi-covid-19-filters-pane.png" alt-text="Erweitern des Bereichs „Filter“":::

4. Wählen Sie den gewünschten Bundesstaat aus. 

    :::image type="content" source="media/sample-covid-19-us/power-bi-covid-19-filter-selection.png" alt-text="Auswählen eines Bundesstaats":::

5. Klicken Sie zum Speichern der Datei auf **Datei** > **Speichern**. 

### <a name="refresh-your-report"></a>Aktualisieren des Berichts 

1. Klicken Sie auf die Schaltfläche **Aktualisieren**.

    :::image type="content" source="media/sample-covid-19-us/power-bi-desktop-refresh-button.png" alt-text="Schaltfläche „Aktualisieren“":::

2. Klicken Sie auf **Anonym** > **Verbinden**. 

    :::image type="content" source="media/sample-covid-19-us/power-bi-covid-19-azure-blob.png" alt-text="Auswählen von „Anonym“":::

 
3. Wird das Dialogfeld „Datenschutzebenen“ angezeigt, wählen Sie die Option **Datenschutzebenen ignorieren** aus, und klicken Sie anschließend auf **Speichern**. 

    :::image type="content" source="media/sample-covid-19-us/power-bi-covid-19-privacy-levels.png" alt-text="Auswählen der Datenschutzebenen":::

### <a name="publish-your-report-to-the-power-bi-service"></a>Veröffentlichen des Berichts im Power BI-Dienst

Nachdem Sie den Bericht Ihren Vorstellungen entsprechend angepasst haben, [führen Sie die in diesem Artikel beschriebenen Schritte aus](../desktop-upload-desktop-files.md), um den Bericht im Power BI-Dienst zu veröffentlichen.

### <a name="configure-scheduled-refresh"></a>Konfigurieren von geplanten Aktualisierungen

Damit die Daten in Ihrem Bericht immer aktuell sind, können Sie nach der Veröffentlichung des Berichts [geplante Aktualisierungen konfigurieren](../refresh-scheduled-refresh.md).

Wählen Sie bei der Konfiguration die folgenden Optionen aus:

1. Authentifizierungsmethode für Datenquellen-Anmeldeinformationen: Anonym
2. Datenschutzebene für diese Datenquelle: Öffentlich

Wenn Sie die Aktualisierungseinstellung testen möchten, wählen Sie die Option [Jetzt aktualisieren](../refresh-data.md#data-refresh) des Datasetelements aus.

Die aktualisierten Daten werden bei jeder Zeitplanausführung geladen. Die von USAFacts bereitgestellten Daten werden möglicherweise seltener aktualisiert als in Ihrem Aktualisierungszeitplan definiert. Den Zeitpunkt der letzten Aktualisierung der Daten finden Sie auf der [Website von USAFacts](https://usafacts.org/visualizations/coronavirus-covid-19-spread-map/). 

Wenn Sie den angepassten Bericht auf Ihrer Website veröffentlichen möchten, sollten Sie die Häufigkeit der geplanten Aktualisierungen so konfigurieren, dass sie mindestens der Aktualisierungshäufigkeit der Daten von USAFacts entspricht. Da die Daten auf der Website von USAFacts möglicherweise zu unterschiedlichen Uhrzeiten aktualisiert werden, sollten Sie mehrere geplante Aktualisierungen täglich konfigurieren. 

### <a name="create-a-publish-to-web-embed-code"></a>Erstellen eines Einbettungscodes für die Webveröffentlichung 

Führen Sie zur Einbettung des angepassten Berichts auf Ihrer Website die Schritte aus, die im Artikel [Erstellen von Einbettungscode für die Webveröffentlichung](../service-publish-to-web.md#how-to-use-publish-to-web) beschrieben werden.

Nach der Veröffentlichung des Einbettungscodes können Sie mithilfe des iFrame-Elements im Bestätigungsdialogfeld die Einbettung in Ihre Website vornehmen.

Wenn Sie in Power BI Desktop Änderungen an Ihrem Bericht vornehmen, können Sie den vorhandenen Bericht im Power BI-Dienst veröffentlichen und ersetzen. Der Einbettungscode wird dabei nicht geändert. Änderungen am Bericht oder aktualisierte Daten werden nach etwa einer Stunde auf Ihrer Website angezeigt. 

## <a name="option-3-mash-up-data-from-another-source"></a>Option 3: Kombinieren der Daten mit Daten aus einer anderen Quelle 

Sie können die Daten in diesem Bericht auch mit Daten aus einer anderen Quelle kombinieren. Das folgende Beispiel basiert auf Daten der [Johns-Hopkins-Universität](https://github.com/CSSEGISandData/COVID-19). Lesen Sie vor dem Veröffentlichen der Daten die [Haftungsausschlüsse](#disclaimers) weiter unten in diesem Artikel.

1. Klicken Sie auf **Daten abrufen** > **Web**.

    :::image type="content" source="media/sample-covid-19-us/power-bi-desktop-get-data.png" alt-text="Schaltfläche „Daten abrufen“":::

2. Geben Sie die folgende URL ein:

    ```
    https://raw.githubusercontent.com/CSSEGISandData/COVID-19/master/csse_covid_19_data/csse_covid_19_time_series/time_series_covid19_confirmed_global.csv
    ```

    :::image type="content" source="media/sample-covid-19-us/power-bi-covid-19-from-web.png" alt-text="Auswählen von Daten aus dem Web":::

3. Wählen Sie **OK** aus. 

    > [!NOTE]
    > Der von der Johns-Hopkins-Universität veröffentlichte Link kann sich ändern. Aktuelle Informationen hierzu finden Sie auf der [GitHub-Seite der Johns-Hopkins-Universität](https://github.com/CSSEGISandData/COVID-19).

4. Klicken Sie auf **Laden**, um das Dataset für die Gesamtzahl der weltweit bestätigten Fälle zu laden.  

    :::image type="content" source="media/sample-covid-19-us/power-bi-covid-19-load-data.png" alt-text="Laden von Daten aus dem Web":::

    Weitere Informationen zum Laden von Daten aus dem Web finden Sie im Artikel [Verbinden mit Webseiten von Power BI Desktop](../desktop-connect-to-web.md).
    
Anschließend können Sie die Daten mit Power BI Desktop visualisieren. Führen Sie zuletzt die unter **Option 2:** [Veröffentlichen des Berichts im Power BI-Dienst](#publish-your-report-to-the-power-bi-service) beschriebenen Schritte aus, um den Bericht zu veröffentlichen und einen benutzerdefinierten Einbettungscode zu erstellen. 

## <a name="option-4-use-the-covid-19-us-tracking-template-app"></a>Option 4: Verwenden der Vorlagen-App zur Nachverfolgung von COVID-19 in den USA

Für eine weitere Option hat das Power BI-Team die *Vorlagen-App* zur Nachverfolgung von COVID-19 in den USA erstellt, mit der Sie sofort loslegen können. Vorlagen-Apps sind Bündel von Berichten, Dashboards und Datasets für eine bestimmte Datenquelle. Sie laden diese aus AppSource herunter, verwenden sie oder passen sie nach Ihren Anforderungen an und verteilen sie an Ihre Kollegen. 

Diese Vorlagen-App für die Nachverfolgung von COVID-19 in den USA enthält einen vorgefertigten Bericht aus COVID-19-Metriken, den Sie so verwenden, direkt im Power BI-Dienst personalisieren oder herunterladen können, um andere Datenquellen hinzuzufügen, falls gewünscht. Informieren Sie sich über die Installation der [Vorlagen-App zur Nachverfolgung von COVID-19 in den USA](../connect-data/service-connect-to-covid-19-tracking.md), und legen Sie sofort los.

## <a name="about-the-data-source-for-this-report"></a>Informationen zur Datenquelle für diesen Bericht
In diesem interaktiven Bericht werden Daten der CDC (Centers for Disease Control and Prevention, Seuchenschutzbehörde der USA) sowie öffentlicher Gesundheitsbehörden auf bundesstaatlicher und kommunaler Ebene gesammelt. Daten auf Countyebene werden durch direkten Verweis auf bundesstaatliche und kommunale Behörden bestätigt (Link).

Die Daten werden von USAFacts bereitgestellt. Aufgrund unterschiedlicher Aktualisierungsintervalle sind diese Daten möglicherweise nicht mit den genauen Zahlen identisch, die von Regierungsorganisationen oder Nachrichtenagenturen veröffentlicht werden. Weitere Informationen sowie die Möglichkeit zum Herunterladen der Daten finden Sie auf der [Website von USAFacts](https://usafacts.org/visualizations/coronavirus-covid-19-spread-map/). 

## <a name="disclaimers"></a>Haftungsausschlüsse

Dieser Bericht und alle Daten werden „wie besehen“, „mit allen möglichen Mängeln“ und ohne jegliche Gewährleistung bereitgestellt. Microsoft gewährt keine ausdrücklichen Gewährleistungen oder Garantien und schließt ausdrücklich sämtliche stillschweigenden Gewährleistungen der Handelsüblichkeit, Eignung für einen bestimmten Zweck und Nichtverletzung von Rechten Dritter aus.

Die Daten von USAFacts sind im Rahmen einer Creative Commons-Lizenz verfügbar. Wenn Sie die Daten verwenden möchten, nennen Sie USAFacts als Datenanbieter, und verweisen Sie zurück zur Website von USAFacts. Informationen zur exakten Vorgehensweise bei der Namensnennung finden Sie auf der Webseite von USAFacts im Abschnitt **#MadewithUSAFacts** des Artikels [Coronavirus in the United States: Mapping the COVID-19 outbreak in the states and counties](https://usafacts.org/visualizations/coronavirus-covid-19-spread-map/).

Die Daten der Johns-Hopkins-Universität sind urheberrechtlich geschützt durch 2020 Johns Hopkins University, alle Rechte vorbehalten. Die veröffentlichten Daten dürfen ausschließlich zu Bildungs- und Forschungszwecken verwendet werden. Die vollständigen Nutzungsbedingungen der Daten, die im Beispiel für die Kombination mit anderen Daten angezeigt werden, finden Sie [hier](https://github.com/CSSEGISandData/COVID-19/blob/master/README.md). Weitere Informationen finden Sie auf der [Website der Johns-Hopkins-Universität](https://coronavirus.jhu.edu/map-faq.html).

## <a name="next-steps"></a>Nächste Schritte

[Abrufen von Beispielen für Power BI](../sample-datasets.md)