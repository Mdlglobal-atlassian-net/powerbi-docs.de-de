---
title: Verwenden der berichtsübergreifenden Drillthroughfunktion in Power BI Desktop
description: Erfahren Sie, wie Sie einen Drillthrough von einem Bericht zu einem anderen in Power BI Desktop durchführen.
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 01/16/2019
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: e500cb29bcc4472c59e7e8215fc0a7e7e728ea0d
ms.sourcegitcommit: 02342150eeab52b13a37b7725900eaf84de912bc
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2020
ms.locfileid: "76538836"
---
# <a name="use-cross-report-drillthrough-in-power-bi"></a>Verwenden der berichtsübergreifenden Drillthroughfunktion in Power BI

Mit der *berichtsübergreifenden Drillthroughfunktion* in Power BI können Sie kontextbezogen im selben Power BI-Arbeitsbereich oder in derselben Power BI-App von einem Bericht zu einem anderen wechseln. Mit der berichtsübergreifenden Drillthroughfunktion können Sie zwei oder mehr Berichte mit ähnlichen Inhalten verknüpfen und den Filterkontext zusammen mit der berichtsübergreifenden Verknüpfung übergeben. 

Um einen berichtsübergreifenden Drillthrough zu initiieren, wählen Sie einen Datenpunkt in einem *Quellvisual* eines *Quellberichts* aus, und klicken Sie dann im Kontextmenü auf das Ziel des berichtsübergreifenden **Drillthroughs**. 

![Berichtsübergreifende Drillthroughoption in Power BI](media/desktop-cross-report-drill-through/cross-report-drill-through-01.png)

Durch die Drillthroughaktion wird die *Zielseite* im *Zielbericht* geöffnet. 

![Zielseite des berichtsübergreifenden Drillthroughs in Power BI Desktop](media/desktop-cross-report-drill-through/cross-report-drill-through-01a.png)

In diesem Artikel erfahren Sie, wie Sie berichtsübergreifende Drillthroughs für Power BI-Berichte einrichten und verwenden.

> [!NOTE]
> Die berichtsübergreifende Drillthroughfunktion kann nicht mit einzeln freigegebenen Berichten aus dem Bereich [Für mich freigegeben](service-share-dashboards.md#share-a-dashboard-or-report) unter **Mein Arbeitsbereich** verwendet werden. Für einen berichtsübergreifenden Drillthrough müssen Sie in dem Arbeitsbereich auf die Berichte zugreifen, von dem aus sie freigegeben wurden.

## <a name="enable-cross-report-drillthrough"></a>Aktivieren des berichtsübergreifenden Drillthroughs

Zum Aktivieren des berichtsübergreifenden Drillthroughs müssen zuerst die Datenmodelle für die Quell- und Zielberichte überprüft werden. Obwohl die Schemas in den einzelnen Berichten nicht identisch sein müssen, müssen die Felder, die übergeben werden sollen, in beiden Datenmodellen vorhanden sein. Die Namen der Felder und die Namen der Tabellen, zu denen sie gehören, müssen gleich sein. Die Zeichenfolgen müssen übereinstimmen, auch was die Groß-/Kleinschreibung betrifft.

Wenn Sie z. B. einen Filter für das Feld **Bundesstaat** innerhalb der Tabelle **US-Bundesstaaten** übergeben möchten, müssen beide Modelle über eine Tabelle namens **US-Bundesstaaten** verfügen, die das Feld **Bundesstaat** enthält. Andernfalls müssen Sie den Feld- oder Tabellennamen im zugrunde liegenden Modell aktualisieren. Das einfache Aktualisieren des Anzeigennamens der Felder funktioniert für berichtsübergreifende Drillthroughs nicht ordnungsgemäß.

Nachdem Sie Ihre Modelle überprüft haben, aktivieren Sie den Quellbericht, um einen berichtsübergreifenden Drillthrough durchzuführen. 

1. Öffnen Sie in Power BI Desktop **Datei** > **Optionen und Einstellungen** > **Optionen**. 
1. Wählen Sie links im Fenster im Navigationsbereich **Optionen** unten den Abschnitt **Aktuelle Datei** und dann **Berichtseinstellungen** aus. 
1. Aktivieren Sie rechts unten unter **Berichtsübergreifender Drillthrough** das Kontrollkästchen **Gestatten Sie, dass Visuals in diesem Bericht Drillthroughziele aus anderen Berichten verwenden**. 
1. Wählen Sie **OK** aus. 
   
   ![Aktiveren der berichtsübergreifenden Drillthroughfunktion in Power BI Desktop](media/desktop-cross-report-drill-through/cross-report-drill-through-02.png)

Sie können die berichtsübergreifende Drillthroughfunktion auch über den Power BI-Dienst aktivieren.
1. Wählen Sie im Power BI-Dienst den Arbeitsbereich aus, der die Ziel-und Quellberichte enthält.
1. Wählen Sie in der Liste der Arbeitsbereiche neben dem Namen des Quellberichts das Symbol **Weitere Optionen** und dann **Einstellungen** aus. 
1. Aktivieren Sie unten im Bereich **Einstellungen** unter **Berichtsübergreifender Drillthrough** das Kontrollkästchen **Gestatten Sie, dass Visuals in diesem Bericht Drillthroughziele aus anderen Berichten verwenden**, und klicken Sie auf **Speichern**.
   
   ![Verwenden der berichtsübergreifenden Drillthroughfunktion im Power BI-Dienst](media/desktop-cross-report-drill-through/cross-report-drill-through-02a.png)

## <a name="set-up-a-cross-report-drillthrough-target"></a>Einrichten der Zielseite für den berichtsübergreifenden Drillthrough

Das Einrichten der Zielseite für einen berichtsübergreifenden Drillthrough ähnelt dem Einrichten eines Drillthroughs innerhalb eines Berichts. Durch das Aktivieren des Drillthroughs auf der Zielseite können andere Visuals auf die Drillthroughseite zugreifen. Wie Sie einen Drillthrough innerhalb eines einzelnen Berichts erstellen, erfahren Sie unter [Verwenden der Drillthroughfunktion in Power BI Desktop](desktop-drillthrough.md).

Sie können die Zielseite für einen berichtsübergreifenden Drillthrough in Power BI Desktop oder im Power BI-Dienst einrichten. 
1. Bearbeiten Sie die Zieldatei, und wählen Sie auf der Zielseite des Zielberichts im Bereich **Visualisierungen** den Bereich **Felder** aus. 
1. Legen Sie unter **Drillthrough** den Umschalter **Berichtsübergreifend** auf **On** (Ein) fest. 
1. Ziehen Sie die Felder, die Sie als Drillthroughziele verwenden möchten, in den Bereich **Drillthroughfelder hier hinzufügen**. Wählen Sie für jedes Feld aus, ob Sie einen Drillthrough zulassen möchten, wenn das Feld als Kategorie verwendet oder wie ein Measure zusammengefasst wird. 
1. Wählen Sie aus, ob Sie alle Filter für das Visual beibehalten möchten (**Alle Filter beibehalten**). Wenn keiner der auf das Quellvisual angewendeten Filter an das Zielvisual übergeben werden soll, wählen Sie **Aus** aus.
   
   ![Bereich „Visualisierungen“ mit hervorgehobenen Drillthroughoptionen](media/desktop-cross-report-drill-through/cross-report-drill-through-03.png)
   
1. Wenn Sie die Seite nur für den berichtsübergreifenden Drillthrough verwenden, sollten Sie die Schaltfläche **Zurück** löschen, die der Oberfläche automatisch hinzugefügt wird. Die Schaltfläche **Zurück** funktioniert jedoch nur für die Navigation innerhalb von Berichten. 
1. Nachdem Sie die Zielseite konfiguriert haben, speichern Sie den Bericht, wenn Sie sich im Power BI-Dienst befinden, oder speichern und veröffentlichen Sie den Bericht, wenn Sie Power BI Desktop verwenden.

Fertig! Ihre Berichte sind bereit für einen berichtsübergreifenden Drillthrough. 

## <a name="use-cross-report-drillthrough"></a>Verwenden des berichtsübergreifenden Drillthrough

Um einen berichtsübergreifenden Drillthrough auszuführen, wählen Sie den Quellbericht im Power BI-Dienst und dann ein Visual aus, das das Drillthroughfeld so verwendet, wie Sie es beim Einrichten der Zielseite angegeben haben. Klicken Sie dann mit der rechten Maustaste auf einen Datenpunkt, um das Kontextmenü des Visuals zu öffnen, klicken Sie auf **Drillthrough**, und wählen Sie das Drillthroughziel aus. Berichtsübergreifende Drillthroughziele sind nach dem Schema **Seitenname [Berichtsname]** formatiert.

![Berichtsübergreifende Drillthroughoption in Power BI](media/desktop-cross-report-drill-through/cross-report-drill-through-01.png)

Dann sehen Sie die Ergebnisse auf der Zielseite des berichtsübergreifenden Drillthroughs, so wie Sie sie beim Erstellen des Ziels eingerichtet haben. Die Ergebnisse werden den Drillthrougheinstellungen gemäß gefiltert.

![Zielseite des berichtsübergreifenden Drillthroughs in Power BI Desktop](media/desktop-cross-report-drill-through/cross-report-drill-through-01a.png)

> [!IMPORTANT]
> Power BI speichert Ziele des berichtsübergreifenden Drillthroughs zwischen. Wenn Sie Änderungen vornehmen, sollten Sie Ihren Browser unbedingt aktualisieren, wenn die erwarteten Drillthroughziele nicht angezeigt werden. 

Wenn Sie **Alle Filter beibehalten** auf **On** (Ein) festgelegt haben, kann der Filterkontext aus dem Quellvisual Folgendes enthalten: 

- Filter auf Berichts-, Seiten- und Visualebene, die sich auf das Quellvisual auswirken. 
- Kreuzfilterung und übergreifende Hervorhebung, die sich auf das Quellvisual auswirken. 
- Datenschnitte und Synchronisierungsdatenschnitte auf der Seite
- URL-Parameter

Wenn der Zielbericht für den Drillthrough geöffnet wird, wendet Power BI nur Filter für Felder an, für die genaue Zeichenfolgenübereinstimmungen für Feldname und Tabellenname gefunden werden. 

Power BI wendet keine dauerhaften Filter aus dem Zielbericht an, dafür jedoch Ihr persönliches Standardlesezeichen, wenn Sie über eines verfügen. Wenn Ihr persönliches Standardlesezeichen z. B. einen Filter auf Berichtsebene für *Land/Region = USA* enthält, wendet Power BI diesen Filter an, bevor der Filterkontext aus dem Quellvisual angewendet wird. 

Für den berichtsübergreifenden Drillthrough übergibt Power BI den Filterkontext an die Standardseiten des Zielberichts. Power BI übergibt den Filterkontext nicht für QuickInfo-Seiten, da QuickInfo-Seiten auf Basis des Quellvisuals gefiltert werden, das die QuickInfo aufruft.

Wenn Sie nach der berichtsübergreifenden Drillthroughaktion zum Quellbericht zurückkehren möchten, verwenden Sie die Schaltfläche **Zurück** des Browsers. 

## <a name="next-steps"></a>Nächste Schritte

Folgende Artikel könnten Sie ebenfalls interessieren:

- [Datenschnitte in Power BI](visuals/power-bi-visualization-slicers.md)
- [Verwenden der Drillthroughfunktion in Power BI Desktop](desktop-drillthrough.md)

