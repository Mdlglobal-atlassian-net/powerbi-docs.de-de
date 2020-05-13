---
title: 'Analysebeispiel für Lieferantenqualität für Power BI: Übersicht'
description: 'Analysebeispiel für Lieferantenqualität für Power BI: Übersicht'
author: maggiesMSFT
ms.reviewer: amac
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 07/19/2019
ms.author: maggies
LocalizationGroup: Samples
ms.openlocfilehash: 18827ef29282e33a1527be0812b3c0a6971201df
ms.sourcegitcommit: bfc2baf862aade6873501566f13c744efdd146f3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/13/2020
ms.locfileid: "83348710"
---
# <a name="supplier-quality-analysis-sample-for-power-bi-take-a-tour"></a>Analysebeispiel für Lieferantenqualität für Power BI: Übersicht

Dieses branchenspezifische Beispieldashboard und der zugrunde liegende Bericht legen den Schwerpunkt auf eine der typischen Herausforderungen einer Lieferkette: die Lieferantenqualitätsanalyse. In dieser Analyse sind hauptsächlich zwei Metriken von Interesse: die Gesamtzahl der Mängel und die Ausfallzeiten, die dadurch verursacht wurden. 

Dieses Beispiel hat zwei wichtige Ziele:

* Erkennen, welcher Lieferant die beste und welcher die schlechteste Qualität liefert.
* Ermitteln, welche Werke Mängel besser erkennen und zurückweisen, um Ausfallzeiten zu minimieren.

![Dashboard für das Analysebeispiel für die Anbieterqualität](media/sample-supplier-quality/supplier1.png)

Dieses Beispiel ist Teil einer Reihe, die Ihnen die Verwendung von Power BI anhand geschäftsbezogener Daten, Berichte und Dashboards zeigt. Es wurde von [obviEnce](http://www.obvience.com/) mit echten Daten erstellt, die anonymisiert wurden. Die Daten sind in verschiedenen Formaten verfügbar: Inhaltspaket, Power BI Desktop-PBIX-Datei oder Excel-Arbeitsmappe. Weitere Informationen finden Sie unter [Welche Beispieldaten sind für die Verwendung mit Power BI verfügbar?](sample-datasets.md). 

In diesem Tutorial wird das Inhaltspaket für das Analysebeispiel für die Anbieterqualität im Power BI-Dienst untersucht. Da die Berichtsoberfläche in Power BI Desktop und im Dienst ähnlich sind, können Sie das Tutorial auch anhand der PBIX-Beispieldatei in Power BI Desktop nachvollziehen. 

Sie benötigen keine Power BI-Lizenz, um die Beispiele in Power BI Desktop kennenzulernen. Wenn Sie nicht über eine Power BI Pro-Lizenz verfügen, können Sie das Beispiel im Power BI-Dienst in Ihrem Arbeitsbereich speichern. 

## <a name="get-the-sample"></a>Abrufen des Beispiels

Bevor Sie das Beispiel verwenden können, müssen Sie es zunächst als [Inhaltspaket](#get-the-content-pack-for-this-sample), [PBIX-Datei](#get-the-pbix-file-for-this-sample) oder [Excel-Arbeitsmappe](#get-the-excel-workbook-for-this-sample) herunterladen.

### <a name="get-the-content-pack-for-this-sample"></a>Abrufen des Inhaltspakets für dieses Beispiel

1. Öffnen Sie den Power BI-Dienst (app.powerbi.com), melden Sie sich an, und öffnen Sie den Arbeitsbereich, in dem Sie das Beispiel speichern möchten.

   Wenn Sie nicht über eine Power BI Pro-Lizenz verfügen, können Sie das Beispiel in Ihrem Arbeitsbereich speichern.

2. Wählen Sie in der linken unteren Ecke **Daten abrufen** aus.
   
   ![„Daten abrufen“ auswählen](media/sample-datasets/power-bi-get-data.png)
3. Klicken Sie auf der daraufhin angezeigten Seite **Daten abrufen** auf **Beispiele**.
   
4. Wählen Sie **Analysebeispiel für Lieferantenqualität** aus, und wählen Sie dann **Verbinden** aus.  
   
   ![Verbindung mit Beispiel herstellen](media/sample-supplier-quality/supplier16.png)

5. Das Inhaltspaket wird in Power BI importiert, und dem aktuellen Arbeitsbereich werden ein neues Dashboard, ein neuer Bericht und ein neues Dataset hinzugefügt.
   
   ![Eintrag für „Analysebeispiel für Lieferantenqualität“](media/sample-supplier-quality/supplier17.png)
  
### <a name="get-the-pbix-file-for-this-sample"></a>Abrufen der PBIX-Datei für dieses Beispiel

Alternativ können Sie das Analysebeispiel für Lieferantenqualität als [PBIX-Datei](https://download.microsoft.com/download/8/C/6/8C661638-C102-4C04-992E-9EA56A5D319B/Supplier-Quality-Analysis-Sample-PBIX.pbix) herunterladen, die zur Verwendung mit Power BI Desktop vorgesehen ist.

### <a name="get-the-excel-workbook-for-this-sample"></a>Abrufen der Excel-Arbeitsmappe für dieses Beispiel

Wenn Sie sich die Datenquelle für dieses Beispiel ansehen möchten, dieses steht auch als [Excel-Arbeitsmappe](https://go.microsoft.com/fwlink/?LinkId=529779) zur Verfügung. Die Arbeitsmappe enthält Power View-Blätter, die Sie anzeigen und ändern können. Aktivieren Sie die Add-Ins für die Datenanalyse, um die Rohdaten anzuzeigen, und klicken Sie dann auf **Power Pivot > Verwalten**. Weitere Informationen zum Aktivieren der Add-Ins für Power View und Power Pivot finden Sie unter [Kennenlernen der Excel-Beispiele in Excel](sample-datasets.md#explore-excel-samples-inside-excel).

## <a name="downtime-caused-by-defective-materials"></a>Ausfallzeiten durch Materialmängel
Analysieren Sie die Ausfallzeiten durch Materialmängel, und stellen Sie fest, welche Anbieter dafür verantwortlich sind.  

1. Wählen Sie auf dem Dashboard die Kachel **Gesamtanzahl der Mängel** oder die Kachel **Gesamtdauer der Downtime in Minuten** aus.

   ![Kachel auswählen, um den Bericht zu öffnen](media/sample-supplier-quality/supplier2.png)  

   Der Bericht „Analysebeispiel für Lieferantenqualität“ wird mit der Seite **Analyse der Ausfallzeiten** geöffnet.

   Beachten Sie, dass es 33 Millionen fehlerhafte Teile gibt, die eine Gesamtausfallzeit (Downtime) von 77.000 Minuten verursachen. Obwohl es für einige Materialien weniger fehlerhafte Teile gibt, können diese zu Verzögerungen führen, die zu weiteren Ausfallzeiten führen. Sehen Sie sich dazu die Berichtseite an.  
2. Ein Blick auf die Linie **Gesamtdauer der Downtime in Minuten** im Kombinationsdiagramm **Mängel und Ausfallzeiten (Min.) nach Materialtyp** zeigt, dass wellende Materialien die meisten Ausfallzeiten verursachen.  
3. Wählen Sie die Spalte **Corrugate** (Wellen) aus, um zu sehen, welche Werke am häufigsten von diesen Mängeln betroffen sind und welcher Lieferant verantwortlich ist.  

   ![Spalte „Corrugate“ (Wellen) auswählen](media/sample-supplier-quality/supplier3.png)  
4. Wählen Sie auf der Karte **Downtime (min) by Plant** (Ausfallzeiten (Min.) nach Hersteller) nacheinander einzelne Werke aus, um zu sehen, welche Hersteller oder Materialien für die Ausfallzeiten in diesem Werk verantwortlich sind.

### <a name="which-are-the-worst-suppliers"></a>Wer sind die schlechtesten Lieferanten?
 Wir möchten die acht schlechtesten Lieferanten finden und den Prozentsatz der durch sie verursachten Ausfallzeiten ermitteln. Dies lässt sich erreichen, indem Flächendiagramm **Ausfallzeiten (Min.) nach Hersteller** in eine Treemap geändert wird.  

1. Wählen Sie auf dem Bericht auf dessen Seite **Analyse der Ausfallzeiten** in der oberen linken Ecke die Option **Bericht bearbeiten** aus.  
2. Wählen Sie das Flächendiagramm **Ausfallzeiten (Min.) nach Hersteller** aus, und wählen Sie im Bereich **Visualisierungen** das Symbol **Treemap** aus.  

   ![Das Symbol „Treemap“ auswählen](media/sample-supplier-quality/supplier4.png)  

    In der Treemap wird das Feld **Hersteller** automatisch als **Gruppe** festgelegt.  

    ![Treemap „Ausfallzeiten (Min.) nach Hersteller“](media/sample-supplier-quality/supplier5.png)  

   Auf dieser Treemap sehen wir die acht wichtigsten Hersteller in den acht Blöcken auf der linken Seite der Treemap. Wir sehen auch, dass sie für knapp 50 % aller Ausfallzeiten in Minuten verantwortlich sind.  
3. Wählen Sie im oberen Navigationsbereich die Option **Analysebeispiel für Lieferantenqualität** aus, um zum Dashboard zurückzukehren.

### <a name="comparing-plants"></a>Werke vergleichen
Überprüfen Sie nun, welches Werk beim Umgang mit Materialmängeln besser abschneidet und somit niedrigere Ausfallzeiten verzeichnet.  

1. Wählen Sie auf dem Dasboard die Kartenkachel **Berichte zur Gesamtanzahl der Mängel nach Werk, Mängeltyp** aus.      

   ![Kachel „Berichte zur Gesamtanzahl der Mängel nach Werk und Mängeltyp“](media/sample-supplier-quality/supplier6.png)  

   Der Bericht wird auf der Seite **Analysebeispiel für Lieferantenqualität** geöffnet.  

2. Wählen Sie in der Legende der Kachel **Berichte zur Gesamtanzahl der Mängel nach Werk, Mängeltyp** den Kreis **Auswirkung** aus.  

    ![Auswirkung auswählen](media/sample-supplier-quality/supplier7.png)  

    Im Blasendiagramm sehen Sie, dass **Logistik** die problematischste Kategorie ist. Sie ist die größte Kategorie in Bezug auf Gesamtanzahl der Mängel, Mängelberichte und Ausfallzeiten in Minuten. Untersuchen Sie diese Kategorie genauer.  
3. Wählen Sie die **Logistik**-Blase im Blasendiagramm aus, und sehen Sie sich die Werke in Springfield und Naperville genauer an. Naperville scheint beim Umgang mit Mängeln erfolgreicher zu sein, da es eine Vielzahl an Reklamationen und eine geringe Auswirkung hat – Springfield verzeichnet hingegen einen hohen Wert bei der Auswirkung.  

   ![Logistik auswählen](media/sample-supplier-quality/supplier8.png)  
4. Wählen Sie im oberen Navigationsbereich die Option **Analysebeispiel für Lieferantenqualität** aus, um zum Dashboard zurückzukehren.

## <a name="which-material-type-is-best-managed"></a>Welcher Materialart schneidet am besten ab?
Der am besten verwaltete Materialtyp ist unabhängig von der Anzahl der Mängel der Typ mit den geringsten Ausfallzeiten oder gar keiner Beeinträchtigung.

1. Sehen wir uns im Dashboard die Kachel **Gesamte Mängel nach Materialart, Fehlerart** an.

   ![Kachel „Gesamtanzahl der Mängel nach Materialtyp, Mängeltyp“](media/sample-supplier-quality/supplier9.png)

   Es ist zu sehen, dass es für den Materialtyp **Raw Materials** (Rohmaterialien) zwar eine große Anzahl von Mängeln gibt, die meisten dieser Mängel jedoch entweder zurückgewiesen werden oder keine Auswirkung haben.

   Überprüfen Sie nun, ob dieser Materialtyp trotz der großen Anzahl von Mängeln tatsächlich nur geringe Ausfallzeiten verursacht.

2. Sehen wir uns im Dashboard die Kachel **Gesamtzahl der Mängel, gesamte Ausfallzeiten in Minuten nach Materialart** an.

   ![Kachel „Gesamtanzahl der Mängel, Gesamtdauer der Downtime in Minuten nach Materialtyp“](media/sample-supplier-quality/supplier10.png)

   Es scheint, dass Rohmaterialien gut im Griff sind: Obwohl es für sie mehr Mängel gibt, haben sie eine kleinere Gesamtdauer der Downtime in Minuten.

### <a name="compare-defects-to-downtime-by-year"></a>Mängel nach Ausfallzeiten pro Jahr vergleichen
1. Wählen Sie die Kartenkachel **Gesamtanzahl der Mängel, Gesamtdauer der Downtime in Minuten nach Materialtyp** aus, um den Bericht mit der Seite **Analyse der Lieferantenqualität** zu öffnen.
2. Auf dem Diagramm **Gesamtanzahl der Mängel nach Monat und Jahr** ist zu sehen, dass die Anzahl der Mängel für 2014 größer ist als für 2013.  

    ![Diagramm „Gesamtanzahl der Mängel nach Monat und Jahr“](media/sample-supplier-quality/supplier11.png)  
3. Führen mehr Mängel zwangsläufig zu mehr Ausfallzeiten? Stellen Sie Fragen über das Q&A-Feld, um das in Erfahrung zu bringen.  
4. Wählen Sie im oberen Navigationsbereich die Option **Analysebeispiel für Lieferantenqualität** aus, um zum Dashboard zurückzukehren.  
5. Da wir wissen, dass Rohmaterialien die höchste Anzahl von Mängeln haben, geben Sie dies in das Fragenfeld ein: *Anzeigen von Materialtypen, Jahr und Gesamtanzahl der Mängel* (show material types, year, and total defect qty).  

    2014 lagen mehr Mängel bei Rohmaterialien vor als 2013.  

    ![Q&A-Frage: Anzeigen von Materialtypen, Jahr und Gesamtanzahl der Mängel](media/sample-supplier-quality/supplier12.png)  
6. Ändern Sie nun die Frage in: _show material types, year, and total **downtime minutes**_ (Anzeigen von Materialtypen, Jahr und Gesamtdauer der Downtime in Minuten).  

   ![Q&A-Frage: Anzeigen von Materialtypen, Jahr und Gesamtdauer der Downtime in Minuten](media/sample-supplier-quality/supplier13.png)

   Sie sehen, dass die Ausfallzeiten für Rohmaterialien 2013 und 2014 etwa gleich waren, obwohl es 2014 mehr Mängel bei Rohmaterialien gegeben hat. Es scheint, dass mehr Mängel bei den Rohmaterialien im Jahr 2014 nicht zu deutlich höheren Ausfallzeiten geführt haben.

### <a name="compare-defects-to-downtime-month-to-month"></a>Mängel nach Ausfallzeit pro Monat vergleichen
Sehen Sie sich eine weitere Dashboardkachel zur Gesamtzahl der Mängel an.  

1. Wählen Sie **Q&A beenden** in der oberen linken Ecke aus, um zum Dashboard zurückzukehren.  

    Sehen Sie sich die Kachel **Gesamtanzahl der Mängel nach Monat, Jahr** genauer an. Auf der Kachel ist zu sehen, dass in der ersten Hälfte von 2014 genauso viele Mängel auftraten wie 2013, in der zweiten Hälfte von 2014 die Anzahl der Mängel jedoch deutlich anstieg.  

    ![Kachel „Gesamtanzahl der Mängel nach Monat, Jahr“](media/sample-supplier-quality/supplier14.png)  

    Prüfen Sie nun, ob durch den Anstieg der Mängel auch die Ausfallzeiten in Minuten angestiegen sind.  
2. Geben Sie in das Fragenfeld Folgendes ein: *Gesamtdauer der Downtime in Minuten nach Monat und Jahr als Liniendiagramm* (total downtime minutes by month and year as a line chart).  

   ![Q&A-Frage: Gesamtdauer der Downtime in Minuten nach Monat und Jahr als Liniendiagramm](media/sample-supplier-quality/supplier15.png)

   Abgesehen von einem Sprung der Ausfallzeiten im Juni und Oktober führte die Anzahl der Mängel nicht zu einer deutlich höheren Ausfallzeit. Dieses Ergebnis zeigt, dass Mängel gut bewältigt werden.  
3. Um dieses Diagramm an Ihr Dashboard anzuheften, wählen Sie das Stecknadelsymbol ![Stecknadelsymbol](media/sample-supplier-quality/pin.png) über dem Fragenfeld aus.  
4. Prüfen Sie zum Untersuchen der Monate mit Ausreißern die Ausfallzeiten in Minuten im Oktober nach Materialtyp, Werksstandort, Kategorie usw., indem Sie Fragen wie *Gesamte Downtime in Minuten im Oktober nach Werk* (total downtime minutes in October by plant) stellen. 
5. Wählen Sie **Q&A beenden** in der oberen linken Ecke aus, um zum Dashboard zurückzukehren.

## <a name="next-steps-connect-to-your-data"></a>Nächste Schritte: Herstellen einer Verbindung mit den Daten
In dieser Umgebung können Sie sicher experimentieren, da Sie die Änderungen nicht speichern müssen. Wenn Sie sie speichern, können Sie jederzeit wieder auf **Daten abrufen** klicken, um ein neues Exemplar dieses Beispiels herunterzuladen.

Wir hoffen, diese Tour hat Ihnen gezeigt, wie Power BI-Dashboards, das Fragen- und Antwortenmodul und Berichte Ihnen Einblicke in Beispieldaten geben können. Jetzt liegt es an Ihnen – stellen Sie Verbindungen mit Ihren eigenen Daten her. Mit Power BI können Sie Verbindungen mit einer Vielzahl von Datenquellen herstellen. Weitere Informationen finden Sie unter [Erste Schritte mit dem Power BI-Dienst](../fundamentals/service-get-started.md).
