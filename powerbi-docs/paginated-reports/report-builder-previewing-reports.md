---
title: Berichtsvorschau im Power BI-Berichts-Generator
description: Beim Erstellen eines paginierten Berichts mit dem Berichts-Generator ist es hilfreich, eine Vorschau des Berichts anzuzeigen, um sicherzustellen, dass auch das Gewünschte angezeigt wird.
ms.date: 06/06/2019
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.assetid: ba6b5bdd-d8c6-4aa8-ba32-3a10b11969d4
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: afbc31e3ece8bc72ad52bb2fe7c3d871b2f68e1b
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "78922940"
---
# <a name="previewing-reports-in-power-bi-report-builder"></a>Berichtsvorschau im Power BI-Berichts-Generator
  Beim Erstellen eines paginierten Berichts mit dem Berichts-Generator ist es hilfreich, eine Vorschau des Berichts anzuzeigen, um sicherzustellen, dass auch das Gewünschte angezeigt wird. Klicken Sie auf **Run** (Ausführen), um eine Vorschau Ihres Berichts anzuzeigen. Es wird eine Vorschau des Berichts angezeigt.  
  
 Der Berichts-Generator verbessert die Vorschaufunktion, indem er Bearbeitungssitzungen verwendet, wenn eine Verbindung zu einem Berichtsserver besteht. In der Bearbeitungssitzung wird ein Datencache erstellt, und das Dataset im Cache wird für das wiederholte Anzeigen einer Berichtsvorschau verfügbar gemacht. Sie interagieren nicht direkt mit einer Bearbeitungssitzung. Wenn Sie jedoch wissen, wann das zwischengespeicherte Dataset aktualisiert wird, kann dies die Leistung verbessern, wenn Sie die Vorschau eines Berichts anzeigen und einschätzen können, warum ein Bericht schneller oder langsamer gerendert wird.  

  
> [!NOTE]  
> Es gibt einige Unterschiede zwischen dem Anzeigen der Vorschau im Berichts-Generator und in einem Browser. Das Kalendersteuerelement (das hinzugefügt wird, wenn Sie einen Date/Time-Parameter im Bericht angegeben haben) unterscheidet sich z. B. zwischen Berichts-Generator und Browser. 
  
## <a name="improving-preview-performance"></a>Verbessern der Vorschauleistung  
 Je nachdem, wie Sie einen Bericht erstellen und aktualisieren, wirkt sich dies unterschiedlich auf das Rendern der Berichtsvorschau aus. Wenn Sie die Vorschau eines Berichts, der von einem Serververweis abhängt, zum ersten Mal anzeigen, wird eine Bearbeitungssitzung erstellt, und die Daten, die beim Ausführen eines Berichts verwendet werden, werden einem Datencache hinzugefügt, der gespeichert wird. Wenn Sie Änderungen am Bericht vornehmen, die sich nicht auf die Daten auswirken, wird die zwischengespeicherte Kopie der Daten vom Bericht verwendet. Das bedeutet, dass sich die Daten nicht bei jedem erneuten Anzeigen der Berichtsvorschau verändern. Wenn Sie die Daten aktualisieren möchten, klicken Sie auf **Refresh** (Aktualisieren) im Menüband.  
  
 Durch die folgenden Aktionen wird der Cache aktualisiert, was sich auf die Rendergeschwindigkeit auswirkt, wenn Sie die Berichtsvorschau beim nächsten Mal anzeigen:  
  
-   Hinzufügen, Ändern und Löschen eines Datasets. Das zwischengespeicherte Dataset enthält alle Datasets, die ein Bericht verwendet. Änderungen an einem Dataset machen das zwischengespeicherte Dataset ungültig. Dazu gehören Änderungen des Namens, der Abfrage oder der Felder im Dataset.  
  
    > [!NOTE]  
    >  Wenn das Dataset viele Felder enthält, die Sie mit hoher Wahrscheinlichkeit nicht verwenden werden, sollten Sie in Erwägung ziehen, diese Felder aus dem Dataset zu entfernen. Obwohl dies eine neue Bearbeitungssitzung erstellt und die erste Vorschau des Bericht langsamer erzeugt wird, ist das kleinere zwischengespeichertes Dataset für die Leistung des Berichtsservers insgesamt nützlich.  
  
-   Hinzufügen, Ändern oder Löschen einer Datenquelle. Dies schließt das Ändern des Namens oder der Eigenschaften der Datenquelle, der Datenerweiterung der Datenquelle sowie der Eigenschaften der Verbindung mit der Datenquelle ein.  
  
-   Ändern der Datenquelle des Berichts.  
  
-   Ändern der Sprache des Berichts.  
  
-   Ändern der Assemblys oder des benutzerdefinierten Codes des Berichts.  
  
-   Hinzufügen, Ändern oder Löschen der Abfrageparameter oder Parameterwerte im Bericht.  
  
 Änderungen des Berichtslayouts und der Datenformatierung wirken sich nicht auf das zwischengespeicherte Dataset aus. Sie können die folgenden Aktionen ausführen, ohne dass das zwischengespeicherte Dataset aktualisiert wird:  
  
-   Hinzufügen oder Entfernen von Datenbereichen wie z. B. Tabellen, Matrizen oder Diagrammen.  
  
-   Hinzufügen oder Löschen von Berichtsspalten. Alle Felder im Dataset können im Bericht verwendet werden. Wenn Sie Felder im Bericht hinzufügen oder löschen, wirkt sich dies nicht auf das Dataset aus.  
  
-   Ändern der Reihenfolge von Feldern in Tabellen oder Matrizen.  
  
-   Hinzufügen, Ändern oder Löschen von Zeilen- und Spaltengruppen.  
  
-   Hinzufügen, Ändern und Löschen von Formatierungen von Datenwerten in Feldern.  
  
-   Hinzufügen, Ändern und Löschen von Bildern, Linien oder Textfeldern.  
  
-   Ändern von Seitenumbrüchen.  
  
Die Bearbeitungssitzung wird erstellt, wenn Sie die Berichtsvorschau zum ersten Mal anzeigen. Standardmäßig besteht eine Bearbeitungssitzung für 7200 Sekunden (zwei Stunden). Jedes Mal, wenn Sie den Bericht ausführen, wird die Sitzung auf zwei Stunden zurückgesetzt. Wenn die Bearbeitungssitzung abläuft, wird der Datencache gelöscht. Wenn die Bearbeitungssitzung abläuft, wird automatisch eine neue erstellt, wenn Sie die Berichtsvorschau das nächste Mal anzeigen.
  
Standardmäßig kann der Datencache bis zu fünf Datasets enthalten. Wenn Sie viele verschiedene Kombinationen von Parameterwerten verwenden, kann es sein, dass der Bericht mehr Daten benötigt. Dann muss der Cache aktualisiert werden, und der Bericht wird beim nächsten Anzeigen der Vorschau langsamer gerendert. 
  
## <a name="concurrency-of-report-updates"></a>Parallelität von Berichtsaktualisierungen  
Wenn Sie einen Bericht aktualisieren und dann im Power BI-Dienst speichern, zeigen Sie davor oft eine Vorschau des Berichts an. Wenn Sie einen Bericht aktualisieren, kann es sein, dass jemand zur selben Zeit den Bericht aktualisiert und speichert. Der zuletzt gespeicherte Bericht ist die Berichtsversion, die zukünftig zum Anzeigen und Aktualisieren verfügbar ist. Das bedeutet, dass die Version des Berichts, die Sie in der Vorschau gesehen haben, nicht unbedingt mit der Version des Berichts beim nächsten Öffnen übereinstimmt. Sie können den Bericht über die Option **Save As** (Speichern unter) im Menü des Berichts-Generators unter einem neuen Namen speichern.  
  
## <a name="external-report-items"></a>Externe Berichtselemente  
 Es kann sein, dass Ihr Bericht Elemente wie z. B. externe Bilder enthält, die separat vom Bericht gespeichert werden. Da diese Elemente separat gespeichert werden, kann es sein, dass diese ein einen anderen Speicherort verschoben oder gelöscht werden. In diesem Fall kann der Bericht möglicherweise nicht in der Vorschau angezeigt werden. Sie können der Bericht entweder mit dem neuen Speicherort des Elements aktualisieren, das gelöschte Element durch ein anderes ersetzen oder den Verweis auf das Element gänzlich aus dem Bericht entfernen.  
  
## <a name="next-steps"></a>Weitere Schritte

- [Was sind paginierte Berichte in Power BI Premium? (Vorschau)](paginated-reports-report-builder-power-bi.md)
  
