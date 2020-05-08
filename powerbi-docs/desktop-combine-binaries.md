---
title: Kombinieren von (binären) Dateien in Power BI Desktop
description: Einfaches Kombinieren von (binären) Datenquellen in Power BI Desktop
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 01/13/2020
ms.author: davidi
LocalizationGroup: Transform and shape data
ms.openlocfilehash: 07381461375ea7b9707b91c807e92cdb85c1d440
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "76161094"
---
# <a name="combine-files-binaries-in-power-bi-desktop"></a>Kombinieren von (binären) Dateien in Power BI Desktop

Ein sehr effizienter Ansatz zum Importieren von Daten in **Power BI Desktop** ist folgender: Wenn Sie mehrere Dateien mit demselben Schema verfügen, kombinieren Sie diese in einer einzigen logischen Tabelle. Dieser beliebte Ansatz wurde vereinfacht und erweitert.

Wählen Sie **Daten abrufen** und anschließend **Datei** > **Ordner** aus, und klicken Sie dann auf **Verbinden**, um mit dem Kombinieren von Dateien aus demselben Ordner zu beginnen.

![Verbindung mit Ordnerdatei, Dialogfeld „Daten abrufen“, Power BI Desktop](media/desktop-combine-binaries/combine-binaries_1.png)

Geben Sie den Ordnerpfad ein, klicken Sie auf **OK**, und wählen Sie dann **Daten transformieren** aus, um die Dateien des Ordners im Power Query-Editor anzuzeigen.

## <a name="combine-files-behavior"></a>Verhalten beim Kombinieren von Dateien

Um binäre Dateien im Power Query-Editor zu kombinieren, wählen Sie **Inhalt** (die erste Spaltenbezeichnung) und anschließend **Start** > **Dateien kombinieren** aus. Alternativ können Sie einfach auf das Symbol **Dateien kombinieren** neben **Inhalt** klicken.

![Befehl „Dateien kombinieren“, Power Query-Editor, Power BI Desktop](media/desktop-combine-binaries/combine-binaries_2a.png)

Die Transformation *Dateien kombinieren* weist das folgende Verhalten auf:

* Die Transformation „Dateien kombinieren“ analysiert jede Eingabedatei und bestimmt das richtige zu verwendende Dateiformat, z. B. *Text*, *Excel-Arbeitsmappe* oder *JSON-Datei*.
* Die Transformation ermöglicht Ihnen die Auswahl eines bestimmten Objekts aus der ersten Datei, z. B. einer Excel-Arbeitsmappe, das extrahiert werden soll.
  
  ![Dialogfeld „Dateien kombinieren“, Power Query-Editor, Power BI Desktop](media/desktop-combine-binaries/combine-binaries_3.png)
* Die Transformation „Dateien kombinieren“ führt automatisch die folgenden Aktionen aus:
  
  * Erstellen einer Musterabfrage, die alle erforderlichen Extraktionsschritte in einer einzelnen Datei ausführt.
  * Erstellen einer *Funktionsabfrage*, die die Datei-/Binäreingabe in die *Musterabfrage* parametrisiert. Die Musterabfrage und die Funktionsabfrage werden verknüpft, sodass Änderungen an der Musterabfrage in der Funktionsabfrage wiedergegeben werden.
  * Anwenden der *Funktionsabfrage* mit Eingabebinärdateien auf die ursprüngliche Abfrage (z. B. auf die *Ordner*-Abfrage). Die Transformation wendet die Funktionsabfrage für Binäreingaben auf jede Zeile an und erweitert dann die resultierende Datenextraktion als Spalten der obersten Ebene.

    ![Ergebnisse der Transformation „Dateien kombinieren“, Power Query-Editor, Power BI Desktop](media/desktop-combine-binaries/combine-binaries_4.png)

> [!NOTE]
> Der Umfang Ihrer Auswahl in einer Excel-Arbeitsmappe beeinflusst das Verhalten von kombinierten Binärdateien. Beispielsweise können Sie ein bestimmtes Arbeitsblatt auswählen, um das Arbeitsblatt zu kombinieren, oder Sie können den Stamm auswählen, um die vollständige Datei zu kombinieren. Wenn Sie einen Ordner auswählen, werden die in diesem Ordner gefundenen Dateien kombiniert. 

Mit dem Verhalten von „Dateien kombinieren“ können Sie alle Dateien in einem bestimmten Ordner problemlos kombinieren, solange sie den gleichen Dateityp und die gleiche Struktur (z. B. die gleichen Spalten) aufweisen.

Außerdem können Sie einfach zusätzliche Transformations- oder Extraktionsschritte anwenden, indem Sie die automatisch erstellte Musterabfrage ändern. Dabei müssen Sie keine Schritte der Funktionsabfrage ändern und keine zusätzlichen Schritte für sie erstellen. Alle Änderungen an der Musterabfrage werden automatisch in der verknüpften Funktionsabfrage generiert.

## <a name="next-steps"></a>Nächste Schritte

Sie können mit Power BI Desktop eine Verbindung mit einer Vielzahl von Datenquellen herstellen. Weitere Informationen zu Datenquellen finden Sie in folgenden Ressourcen:

* [Was ist Power BI Desktop?](desktop-what-is-desktop.md)
* [Datenquellen in Power BI Desktop](desktop-data-sources.md)
* [Strukturieren und Kombinieren von Daten mit Power BI Desktop](desktop-shape-and-combine-data.md)
* [Verbinden mit CSV-Dateien in Power BI Desktop](desktop-connect-csv.md)
* [Eingeben von Daten direkt in Power BI Desktop](desktop-enter-data-directly-into-desktop.md)
