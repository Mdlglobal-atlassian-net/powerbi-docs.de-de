---
title: Erstellen eines paginierten Berichts mit einem freigegebenen Power BI-Dataset – Power BI Report Builder
description: Erstellen Sie einen paginierten Bericht in Power BI Report Builder basierend auf einem freigegebenen Power BI-Dataset.
ms.date: 02/12/2020
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 717627e171df6a0843453a72b54ec591a7fd5a19
ms.sourcegitcommit: ced8c9d6c365cab6f63fbe8367fb33e6d827cb97
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/07/2020
ms.locfileid: "78923193"
---
# <a name="create-a-paginated-report-based-on-a-power-bi-shared-dataset"></a>Erstellen eines paginierten Berichts basierend auf einem freigegebenen Power BI-Dataset

Sie können ein Dataset, das Sie in Power BI Desktop erstellt haben, als Datenquelle für paginierte Berichte des Power BI-Berichts-Generators verwenden. Stellen Sie sich dieses Szenario vor: Sie haben einen Power BI-Bericht in Power BI Desktop erstellt. Sie haben viel Zeit damit verbracht, das Datenmodell zu entwerfen, und haben dann einen schönen Power BI-Bericht mit allen möglichen tollen visuellen Elementen erstellt. Ihr Bericht enthält eine Matrix mit vielen Zeilen, sodass Sie scrollen müssen, um alle Zeilen anzuzeigen. Die Leser Ihres Berichts wünschen einen Bericht, den sie drucken können und in dem alle Zeilen aus dieser Matrix enthalten sind. Ein paginierter Power BI-Bericht ist dafür geeignet: Drucken Sie eine Tabelle oder Matrix, die über mehrere Seiten verteilt ist, mit Kopf- und Fußzeilen und einem perfekten Seitenlayout, das Sie entworfen haben. Dieser Bericht ergänzt den Power BI Desktop-Bericht. Sie möchten, dass beide Berichte auf genau denselben Daten basieren, ohne Abweichungen, also verwenden Sie dasselbe Dataset.

![Power BI Desktop- und paginierter Berichts-Generator-Bericht](media/report-builder-shared-datasets/power-bi-desktop-report-builder-arrow-26-pgs.png)

Der Datensatz muss sich nicht in einem Arbeitsbereich in einer Premium-Kapazität befinden, und Sie müssen kein Mitglied dieses Arbeitsbereichs sein. Sie müssen lediglich die [Erstellungsberechtigung](../service-datasets-build-permissions.md) für das Dataset haben. Um Ihren paginierten Bericht veröffentlichen zu können, benötigen Sie eine Power BI Pro-Lizenz. Außerdem benötigen Sie mindestens eine „Mitwirkender“-Rolle für einen Arbeitsbereich in einer Premium-Kapazität.

## <a name="what-you-need"></a>Voraussetzung

Im folgenden finden Sie eine Liste der Elemente, die Sie benötigen oder nicht benötigen, um ein freigegebenes Dataset im Power BI Berichts-Generator zu verwenden.

- Power BI-Berichts-Generator. [Laden Sie den Power BI-Berichts-Generator herunter, und installieren Sie ihn](https://go.microsoft.com/fwlink/?linkid=2086513).
- Um auf ein Power BI-Dataset zugreifen zu können, benötigen Sie die Erstellungsberechtigung für das Dataset. Erfahren Sie mehr über [Erstellungsberechtigung](../service-datasets-build-permissions.md).
- Sie benötigen keine Power BI Pro-Lizenz, um im Berichts-Generator einen paginierten Bericht zu erstellen. 
- Sie benötigen eine Power BI Pro-Lizenz, um Ihren paginierten Bericht veröffentlichen zu können. Außerdem benötigen Sie mindestens eine „Mitwirkender“-Rolle für einen Arbeitsbereich in einer Premium-Kapazität. 
- Optional: Wenn Sie den Schritten in diesem Artikel folgen möchten, laden Sie die Power BI Desktop-Datei [Retail Analysis Sample PBIX.pbix](https://download.microsoft.com/download/9/6/D/96DDC2FF-2568-491D-AAFA-AFDD6F763AE3/Retail%20Analysis%20Sample%20PBIX.pbix) herunter, öffnen Sie die Datei in Power BI Desktop, und fügen Sie eine Tabelle mit vielen Spalten hinzu. Deaktivieren Sie im Bereich **Format** die Option **Gesamt**. Veröffentlichen Sie die Datei dann in einem Arbeitsbereich im Power BI-Dienst.

    ![Gesamt aus](media/report-builder-shared-datasets/power-bi-desktop-totals-off.png)

## <a name="connect-to-the-power-bi-dataset"></a>Herstellen einer Verbindung mit dem Power BI-Dataset

1. Öffnen Sie den Power BI-Berichts-Generator.
1. Wählen Sie **Anmelden** in der oberen rechten Ecke des Berichts-Generators aus, um sich bei Ihrem Power BI-Konto anzumelden.
1. Wählen Sie im Bereich „Berichtsdaten“ den Befehl **Neu** > **Power BI-Datasetverbindung** aus.

    ![Neues Dataset im Bereich „Berichtsdaten“](media/report-builder-shared-datasets/power-bi-report-builder-new-dataset.png)

    > [!NOTE]
    > Sie können die Datenquelle oder das Dataset für ein Power BI-Dataset nicht mit dem Tabellen-, Matrix-oder Diagramm-Assistenten des Berichts-Generators erstellen. Nachdem Sie die Datenquelle oder das Dataset erstellt haben, können Sie den jeweiligen Assistenten verwenden, um auf Basis der Datenquelle oder des Datasets Tabellen, Matrizen oder Diagramme zu erstellen.

1. Suchen Sie nach dem Dataset oder dem Arbeitsbereich, in dem sich das Dataset befindet, und wählen Sie **Auswählen** aus.
    Der Berichts-Generator füllt den Datasetnamen aus.

    ![Dataset auswählen](media/report-builder-shared-datasets/power-bi-report-builder-select-dataset.png)
    
1. Das Dataset wird im Bereich „Berichtsdaten“ unter „Datenquellen“ aufgelistet.

    ![Dataset im Bereich „Berichtsdaten“ unter „Datenquellen“](media/report-builder-shared-datasets/power-bi-report-builder-data-source.png)

    Es sei daran erinnert, dass Sie im selben paginierten Bericht Verbindungen mit mehreren Power BI-Datasets und anderen Datenquellen herstellen können.


## <a name="get-the-dax-query-for-the-dataset"></a>Abrufen der DAX-Abfrage für das Dataset

Sollen die Daten im Power BI-Bericht und in Ihrem Berichts-Generator-Bericht identisch sein, reicht es nicht aus, eine Verbindung mit dem Dataset herzustellen. Sie benötigen auch die Abfrage, die auf diesem Dataset basiert.

### <a name="video-get-the-dax-query"></a>Video: Abrufen der DAX-Abfrage

Im folgenden Video zeigt Chris Finlan, wie Sie den für den paginierten Bericht benötigten DAX erhalten.

<iframe width="400" height="450" src="https://www.youtube.com/embed/NfoOK4QRkhI" frameborder="0" allowfullscreen></iframe>

### <a name="steps-to-get-the-dax-query"></a>Schritte zum Abrufen der DAX-Abfrage

Dies sind die erforderlichen Schritte zum Abrufen der Abfrage.

1. Öffnen Sie den Power BI-Bericht (PBIX-Datei) in Power BI Desktop.
1. Vergewissern Sie sich, dass es in Ihrem Bericht eine Tabelle gibt, die alle Daten enthält, die Sie in Ihrem paginierten-Bericht benötigen. Die Tabelle muss diese beiden Anforderungen erfüllen:
    - Es muss sich um eine flache Tabelle und nicht um eine Matrix oder ein anderes Visual handeln. Konvertieren Sie das Element jetzt in eine Tabelle, wenn es sich nicht um eine Tabelle handelt. Führen Sie dann die folgenden Schritte der Leistungsanalyse aus, und konvertieren Sie sie anschließend wieder ins gewünschte Visual.
    - Verwenden Sie *vordefinierte Measures* für Ihre numerischen Felder. Neben diesen befindet sich ein Taschenrechnersymbol. Informieren Sie sich über das [Erstellen von Measures](../desktop-measures.md). 

        ![Taschenrechnersymbol](media/report-builder-shared-datasets/power-bi-measure-icon.png)

1. Wählen Sie auf dem Menüband **Ansicht** die Option **Performance Analyzer** aus.

    ![Performance Analyzer (Leistungsanalyse) öffnen](media/report-builder-shared-datasets/power-bi-performance-analyzer.png)

1. Wählen Sie im Bereich **Performance Analyzer** die Option **Aufzeichnung starten** aus, und wählen Sie dann **Visuals aktualisieren** aus.

    ![Visuals aktualisieren](media/report-builder-shared-datasets/power-bi-performance-analyzer-refresh-visuals.png)

1. Erweitern Sie das Pluszeichen **(+** ) neben dem Tabellennamen, und wählen **Abfrage kopieren** aus. Die Abfrage ist die DAX-Formel, die Sie für das Dataset im Power BI-Berichts-Generator benötigen.

    ![Abfrage kopieren](media/report-builder-shared-datasets/power-bi-performance-analyzer-copy-query.png)

## <a name="create-the-dataset-with-the-query"></a>Erstellen des Datasets mit der Abfrage

1. Wechseln Sie zurück zum Power BI-Berichts-Generator.
1. Klicken Sie unter **Datenquellen** mit der rechten Maustaste auf das Dataset, und wählen Sie **Dataset hinzufügen** aus.

    ![Dataset hinzufügen](media/report-builder-shared-datasets/power-bi-report-builder-add-dataset.png)

1. Geben Sie dem Dataset in den „Dataseteigenschaften“ einen Namen, und wählen Sie **Abfrage-Designer** aus.

4. Wählen Sie **DAX** aus, und deaktivieren Sie das Symbol **Entwurfsmodus**.

    ![Abfrage-Designer des Berichts-Generators](media/report-builder-shared-datasets/power-bi-report-builder-query-designer.png)

1. Fügen Sie in das obere Feld die Abfrage ein, die Sie aus Power BI Desktop kopiert haben.

1. Wählen Sie **Abfrage ausführen** (das rote Ausrufezeichen, !) aus, um sich zu vergewissern, dass die Abfrage funktioniert. 

    ![Abfrage ausführen](media/report-builder-shared-datasets/power-bi-report-builder-run-query.png)

    Die Ergebnisse der Abfrage werden im unteren Feld angezeigt.

    ![Abfrageergebnisse](media/report-builder-shared-datasets/power-bi-report-builder-query-results.png)

1. Wählen Sie **OK** aus.

    Ihre Abfrage wird im Bereich **Abfrage** des Dialogfelds **Dataseteigenschaften** angezeigt.

    ![Dialogfeld „Dataseteigenschaften“](media/report-builder-shared-datasets/power-bi-report-builder-dataset-properties.png)

1. Wählen Sie **OK** aus.

    Nun wird das neue Dataset mit einer Liste seiner Felder im Bereich „Berichtsdaten“ angezeigt.

    ![Dataset im Bereich „Berichtsdaten“](media/report-builder-shared-datasets/power-bi-report-builder-dataset.png)

## <a name="create-a-table-in-the-report"></a>Erstellen einer Tabelle im Bericht

Eine schnelle Möglichkeit zum Erstellen einer Tabelle besteht darin, den Tabellen-Assistenten zu verwenden.

1. Wählen Sie auf dem Menüband **Einfügen** die Option **Tabelle** > **Tabellen-Assistent** aus.

    ![Tabellen-Assistenten starten](media/report-builder-shared-datasets/power-bi-report-builder-table-wizard.png)

1. Wählen Sie das Dataset aus, das Sie mit der DAX-Abfrage erstellt haben, und wählen Sie **Weiter** aus.

    ![Dataset auswählen](media/report-builder-shared-datasets/power-bi-report-builder-choose-dataset.png)

1. Um eine flache Tabelle zu erstellen, wählen Sie die gewünschten Felder in **Verfügbare Felder** aus. Sie können mehrere Felder gleichzeitig auswählen, indem Sie das erste gewünschte Feld auswählen, die UMSCHALTTASTE gedrückt halten und das letzte Feld auswählen.

    ![Mehrere Felder auswählen](media/report-builder-shared-datasets/power-bi-report-builder-select-fields.png)

1. Ziehen Sie die Felder in das Feld **Werte**, und wählen Sie **Weiter** aus.

    ![Tabellen-Assistent](media/report-builder-shared-datasets/power-bi-report-builder-value-fields.png)

1. Wählen Sie die gewünschten Layoutoptionen aus, und wählen Sie **Weiter** aus.

1. Wählen Sie **Fertig stellen**aus.
    Die Tabelle wird in der Entwurfsansicht angezeigt.

    ![Berichtsentwurfsansicht](media/report-builder-shared-datasets/power-bi-report-builder-design-view.png)

1. Wählen Sie **Zum Hinzufügen eines Titels klicken** aus, und fügen Sie einen Titel hinzu.

1. Wählen Sie **Ausführen** aus, um eine Vorschau Ihres Berichts anzuzeigen.

    ![Berichtsvorschau](media/report-builder-shared-datasets/power-bi-report-builder-preview.png)

1. Wählen Sie **Drucklayout** aus, um zu sehen, wie der gedruckte Bericht aussieht. 

    Dieses Berichtslayout erfordert einige Arbeit. Es hat 54 Seiten, weil die Spalten und Ränder dazu führen, dass die Tabelle zwei Seiten breit ist.

    ![Drucklayout des Berichts](media/report-builder-shared-datasets/power-bi-report-builder-print-layout-2-p1-p2.png)

## <a name="format-the-report"></a>Formatieren des Berichts

Sie haben mehrere Formatierungsoptionen, um zu bewirken, dass die Tabelle auf eine Seite passt. 

1. Sie können die Seitenränder im Bereich „Eigenschaften“ verkleinern. Wenn der Bereich „Eigenschaften“ nicht angezeigt wird, aktivieren Sie auf dem Menüband **Ansicht** das Kontrollkästchen **Eigenschaften**.

1. Wählen Sie den Bericht, nicht die Tabelle oder den Titel aus.
1. Erweitern Sie im Bereich **Berichtseigenschaften** unter **Seite** die Option **Ränder**, und ändern Sie jeden Rand in **1,91 cm**.

    ![Festlegen von Seitenrändern](media/report-builder-shared-datasets/power-bi-report-builder-page-margins.png)

1. Sie können auch Spalten schmaler machen. Wählen Sie den Spaltenrand aus, und ziehen Sie die rechte Seite nach links.

    ![Spaltenbreite festlegen](media/report-builder-shared-datasets/power-bi-report-builder-column-width.png)

1. Eine weitere Option ist sicherzustellen, dass die Zahlenwerte ordentlich formatiert sind. Wählen Sie eine Zelle mit einem Zahlenwert aus. 
    > [!TIP]
    > Sie können mehrere Zellen gleichzeitig formatieren, indem Sie die UMSCHALTTASTE gedrückt halten, während Sie die anderen Zellen auswählen.

    ![Mehrere Zellen auswählen](media/report-builder-shared-datasets/power-bi-report-builder-select-cells.png)

1. Ändern Sie auf dem Menüband **Home** im Abschnitt **Zahl** das Format **Standard** in ein numerisches Format, etwa **Währung**.

    ![Zahlenformat festlegen](media/report-builder-shared-datasets/power-bi-report-builder-number-format.png)

1. Ändern Sie den **Platzhalter**-Stil in **Beispielwerte**, damit Sie die Formatierung in der Zelle sehen können. 

    ![Beispielwerte anzeigen](media/report-builder-shared-datasets/power-bi-report-builder-sample-values.png)

1. Verringern Sie ggf. im Abschnitt **Zahl** die Dezimalstellen, um weiteren Platz zu sparen.

### <a name="getting-rid-of-blank-pages"></a>Entfernen von leeren Seiten

Auch wenn Sie die Ränder und die Tabellenspalten schmaler gemacht haben, kann es vorkommen, dass weiterhin jede weitere Seite leer ist. Warum? Der Grund liegt in der Mathematik. 

Wenn Sie die Seitenränder, die Sie festgelegt haben, und die Breite des *Textes* des Berichts addieren, muss die Gesamtbreite kleiner sein als die Breite des Berichtsformats.

Angenommen, Ihr Bericht liegt im Format 21 cm x 29,7 cm vor, und Sie haben jeden Seitenrand auf 1,91 cm festgelegt. Die beiden Ränder ergeben zusammen 3,82 cm, sodass der Text schmaler als 17,18 cm sein muss.

1. Wählen Sie den rechten Rand der Berichtsentwurfsfläche aus, und ziehen Sie ihn, sodass er kleiner ist als die gewünschte Zahl auf dem Lineal. 

    > [!TIP]
    > Sie können ihn genauer in den **Textkörper**-Eigenschaften festlegen. Legen Sie unter **Größe** die Eigenschaft **Breite** fest.

    ![Textkörpergröße festlegen](media/report-builder-shared-datasets/power-bi-report-builder-body-size.png)

1. Wählen Sie **Ausführen** aus, um den Bericht in der Vorschau anzuzeigen, und vergewissern Sie sich, dass die leeren Seiten entfernt wurden. Dieser Bericht hat jetzt nur 26 Seiten anstelle der ursprünglichen 54. Der Vorgang war erfolgreich.

    ![Keine leeren Seiten drucken](media/report-builder-shared-datasets/power-bi-report-builder-print-26-pgs.png)

## <a name="limitations-and-considerations"></a>Einschränkungen und Überlegungen 

- Für Datasets, für die eine Liveverbindung mit Analysis Services verwendet wird, können Sie eine direkte Verbindung herstellen, indem Sie die zugrunde liegende Analysis Services-Verbindung anstelle eines freigegebenen Datasets verwenden.
- Datasets mit der Empfehlung „Höher gestuft“ oder „Zertifiziert“ werden in der Liste der verfügbaren Datasets angezeigt, sind jedoch nicht als solche gekennzeichnet. 
- Sie können im „App Owns Data“-Szenario keine paginierten Berichte einbetten, die auf in Power BI freigegebenen Datasets basieren.

## <a name="next-steps"></a>Nächste Schritte

- [Was sind paginierte Berichte in Power BI Premium? (Vorschau)](paginated-reports-report-builder-power-bi.md)