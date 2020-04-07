---
title: 'Beispiel für Beschaffungsanalysen: Übersicht'
description: 'Analysebeispiel für Beschaffung für Power BI: Übersicht'
author: maggiesMSFT
ms.reviewer: amac
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 07/02/2019
ms.author: maggies
LocalizationGroup: Samples
ms.openlocfilehash: 8ee77485da03cb8e507d30d511c08aa869c3e4ba
ms.sourcegitcommit: 444f7fe5068841ede2a366d60c79dcc9420772d4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/30/2020
ms.locfileid: "80404669"
---
# <a name="procurement-analysis-sample-for-power-bi-take-a-tour"></a>Analysebeispiel für Beschaffung für Power BI: Übersicht

Das Beispielinhaltspaket für die Beschaffungsanalyse enthält ein Dashboard, einen Bericht und ein Dataset, die eine Analyse des Ausgabeverhaltens eines Fertigungsunternehmens für Lieferanten nach Kategorie und Standort darstellen. In diesem Beispiel untersuchen wir die folgenden Bereiche:

* Wer sind die Top-Lieferanten?
* Für welche Kategorien geben wir am meisten aus?
* Welche Lieferanten geben uns den größten Rabatt und wann?

![Dashboard für das Analysebeispiel für Beschaffung](media/sample-procurement/procurement1.png)

Dieses Beispiel ist Teil einer Reihe, die Ihnen die Verwendung von Power BI anhand geschäftsbezogener Daten, Berichte und Dashboards zeigt. Es wurde von [obviEnce](http://www.obvience.com/) mit echten Daten erstellt, die anonymisiert wurden. Die Daten sind in verschiedenen Formaten verfügbar: Inhaltspaket, Power BI Desktop-PBIX-Datei oder Excel-Arbeitsmappe. Weitere Informationen finden Sie unter [Welche Beispieldaten sind für die Verwendung mit Power BI verfügbar?](sample-datasets.md). 

In diesem Tutorial wird das Beschaffungsanalyse-Beispielinhaltspaket im Power BI-Dienst erörtert. Da die Berichtsoberfläche in Power BI Desktop und im Dienst ähnlich sind, können Sie das Tutorial auch anhand der PBIX-Beispieldatei in Power BI Desktop nachvollziehen. 

Sie benötigen keine Power BI-Lizenz, um die Beispiele in Power BI Desktop kennenzulernen. Wenn Sie nicht über eine Power BI Pro-Lizenz verfügen, können Sie das Beispiel im Power BI-Dienst in Ihrem Arbeitsbereich speichern. 

## <a name="get-the-sample"></a>Abrufen des Beispiels

Bevor Sie das Beispiel verwenden können, müssen Sie es zunächst als [Inhaltspaket](#get-the-content-pack-for-this-sample), [PBIX-Datei](#get-the-pbix-file-for-this-sample) oder [Excel-Arbeitsmappe](#get-the-excel-workbook-for-this-sample) herunterladen.

### <a name="get-the-content-pack-for-this-sample"></a>Abrufen des Inhaltspakets für dieses Beispiel

1. Öffnen Sie den Power BI-Dienst (app.powerbi.com), melden Sie sich an, und öffnen Sie den Arbeitsbereich, in dem Sie das Beispiel speichern möchten. 

    Wenn Sie nicht über eine Power BI Pro-Lizenz verfügen, können Sie das Beispiel in Ihrem Arbeitsbereich speichern.

2. Wählen Sie in der linken unteren Ecke **Daten abrufen** aus.

    ![„Daten abrufen“ auswählen](media/sample-datasets/power-bi-get-data.png)
3. Klicken Sie auf der daraufhin angezeigten Seite **Daten abrufen** auf **Beispiele**.

4. Wählen Sie **Analysebeispiel für Beschaffung** und dann **Verbinden** aus.  
  
   ![Verbindung mit Beispiel herstellen](media/sample-procurement/procurement1a.png)
   
5. Das Inhaltspaket wird in Power BI importiert, und dem aktuellen Arbeitsbereich werden ein neues Dashboard, ein neuer Bericht und ein neues Dataset hinzugefügt.
   
   ![Analysebeispiel für Beschaffung-Eintrag](media/sample-procurement/procurement-entry.png)
  
### <a name="get-the-pbix-file-for-this-sample"></a>Abrufen der PBIX-Datei für dieses Beispiel

Alternativ können Sie das Analysebeispiel für Beschaffung als [PBIX-Datei](https://download.microsoft.com/download/D/5/3/D5390069-F723-413B-8D27-5888500516EB/Procurement%20Analysis%20Sample%20PBIX.pbix) herunterladen, ein für Power BI Desktop entworfenes Dateiformat. 

### <a name="get-the-excel-workbook-for-this-sample"></a>Abrufen der Excel-Arbeitsmappe für dieses Beispiel

Wenn Sie sich die Datenquelle für dieses Beispiel ansehen möchten, dieses steht auch als [Excel-Arbeitsmappe](https://go.microsoft.com/fwlink/?LinkId=529784) zur Verfügung. Die Arbeitsmappe enthält Power View-Blätter, die Sie anzeigen und ändern können. Aktivieren Sie die Add-Ins für die Datenanalyse, um die Rohdaten anzuzeigen, und klicken Sie dann auf **Power Pivot > Verwalten**. Weitere Informationen zum Aktivieren der Add-Ins für Power View und Power Pivot finden Sie unter [Kennenlernen der Excel-Beispiele in Excel](sample-datasets.md#explore-excel-samples-inside-excel).


## <a name="spending-trends"></a>Ausgabentrends
Sehen Sie sich zunächst die Trends bei den Ausgaben nach Kategorie und Standort an.  

1. Öffnen Sie in dem Arbeitsbereich, in dem Sie das Beispiel gespeichert haben, die Registerkarte **Dashboards**, suchen Sie das Dashboard **Beschaffungs-Analysebeispiel** , und wählen Sie es aus. 
2. Wählen Sie die Dashboardkachel **Total Invoice by Country/Region** (Gesamtrechnung nach Land/Region) aus, wodurch die Seite **Ausgabenübersicht** des Berichts **Beschaffungs-Analysebeispiel** geöffnet wird.

    ![Seite „Ausgabenübersicht“](media/sample-procurement/procurement2.png)

Beachten Sie Folgendes:

* Im Liniendiagramm **Gesamtrechnung nach Monat und Kategorie**: Die Ausgaben sind für die Kategorie **Direkt** recht einheitlich, **Logistik** weist eine Spitze im Dezember auf, und **Sonstige** weist eine Spitze im Februar auf.
* In der Karte **Gesamtrechnung nach Land/Region**: Die meisten Ausgaben fallen in den USA an.
* Im Säulendiagramm **Gesamtrechnung nach Unterkategorie** sind **Hardware** und **Indirekte Waren und Dienstleistungen** die Kategorien mit den höchsten Ausgaben.
* Im Balkendiagramm **Total Invoice by Tier** (Gesamtrechnung nach Ebene) ist zu sehen, dass der größte Teil unseres Geschäfts mit unseren Lieferanten der 1. Ebene (Top 10) abgewickelt wird. Das ermöglicht uns die Pflege besserer Lieferantenbeziehungen.

## <a name="spending-in-mexico"></a>Ausgaben in Mexiko
Sehen Sie sich die Ausgabenbereiche für Mexiko an.

1. Wählen Sie in der Karte **Gesamtrechnung nach Land/Region** die Blase **Mexiko** aus. Beachten Sie, dass im Säulendiagramm **Gesamtrechnung nach Unterkategorie** der größte Teil in der Unterkategorie **Indirekte Waren und Dienstleistungen** anfällt.

   ![Auswahl von „Mexiko“ auf der Seite „Ausgabenübersicht“](media/sample-procurement/pbi_procsample_spendmexico.png)
2. Führen Sie einen Drilldown in die Spalte **Indirekte Waren und Dienstleistungen** aus:

   * Wählen Sie im Diagramm **Gesamtrechnung nach Unterkategorie** den Drilldownpfeil ![Drilldownpfeil](media/sample-procurement/pbi_drilldown_icon.png) in der oberen rechten Ecke des Diagramms aus.
   * Wählen Sie die Spalte **Indirekte Waren und Dienstleistungen** aus.

      Wie Sie sehen können, sind die bei weitem höchsten Ausgaben in der Unterkategorie **Vertrieb und Marketing**.
   * Wählen Sie in der Karte erneut **Mexiko** aus.

      Für Mexiko fallen die größten Ausgaben in der Unterkategorie **Wartung und Reparatur** an.

      ![Drilldown zu „Indirekte Waren und Dienstleistungen“ für Mexiko](media/sample-procurement/pbi_procsample_drill_mexico.png)
3. Wählen Sie den Aufwärtspfeil in der oberen linken Ecke des Diagramms aus, um wieder eine Ebene nach oben zu wechseln.
4. Wählen Sie den Drilldownpfeil erneut aus, um den Drilldown zu deaktivieren.  
5. Wählen Sie im oberen Navigationsbereich **Beschaffungs-Analysebeispiel** aus, um zu den Dashboards zurückzukehren.

## <a name="evaluate-different-cities"></a>Auswerten verschiedener Städte
Wir können Hervorhebung verwenden, um verschiedene Städte auszuwerten.

1. Wählen Sie die Dashboardkachel **Total Invoice, Discount % By Month** (Gesamtrechnung, Rabatt % nach Monat) aus, wodurch die Seite **Discount Analysis** (Rabattanalyse) des Berichts **Beschaffungs-Analysebeispiel** geöffnet wird.
2. Wählen Sie in der Treemap **Gesamtumsatz nach Stadt** abwechselnd die einzelnen Städte aus, um den Vergleich anzuzeigen. Beachten Sie, dass sich fast alle Rechnungen in Miami auf Lieferanten der Ebene 1 beziehen.

   ![Stadt im Vergleich zu Rabattprozentsatz nach Ebene](media/sample-procurement/pbi_procsample_miamitreemap2.png)

## <a name="vendor-discounts"></a>Lieferantenrabatte
Sehen Sie sich auch die von Lieferanten angebotenen Rabatte an sowie die Zeiträume, in denen die meisten Rabatte gelten:
* Unterscheiden sich die Rabatte jeden Monat, oder bleiben sie gleich?
* Werden in einigen Städten höhere Rabatte als in anderen eingeräumt?

![Seite „Rabattanalyse“](media/sample-procurement/procurement4.png)

### <a name="discount-by-month"></a>Rabatt nach Monat
Wenn wir uns das Kombinationsdiagramm **Gesamtrechnung und Rabatt in % nach Monat** ansehen, wird deutlich, dass Februar der Monat mit dem höchsten Wert und September der Monat mit dem geringsten Aufkommen ist. 

Sehen Sie sich den Rabattprozentsatz während dieser Monate an: Wenn das Volumen zunimmt, sinkt der Rabatt, und er steigt bei geringem Volumen. Je dringender wir den Rabatt benötigen, desto schlechter wird das Angebot.

![Gesamtrechnungsbetrag und Rabattprozentsatz nach Monat](media/sample-procurement/procurement5.png)

### <a name="discount-by-city"></a>Rabatt nach Stadt
Wir können uns auch den Rabatt nach Stadt ansehen. Wählen Sie im Treemap-Diagramm nacheinander die einzelnen Städte aus. Sie sehen dann, wie sich die anderen Diagramme ändern:

* Für St. Louis gab es bei der Gesamtrechnung im Februar eine große Spitze und einen Einbruch bei den Einsparungen durch Rabatte im April.
* Mexico City verfügt über den höchsten Rabattprozentsatz (11,05 %) und Atlanta über den niedrigsten (0,08 %).

![Rabattdiagramm für Mexico City](media/sample-procurement/procurement6.png)

### <a name="edit-the-report"></a>Bearbeiten des Berichts
Wählen Sie in der oberen linken Ecke **Bericht bearbeiten** aus, und führen Sie die Untersuchung in der Bearbeitungsansicht fort.

* Verfolgen Sie, wie die Seiten aufgebaut werden.
* Fügen Sie auf der Grundlage der gleichen Daten Seiten und Diagramme hinzu.
* Ändern Sie die Visualisierung für ein Diagramm, indem Sie beispielsweise das Treemap-Diagramm in ein Ringdiagramm ändern.
* Heften Sie Diagramme an Ihr Dashboard an.

## <a name="next-steps-connect-to-your-data"></a>Nächste Schritte: Herstellen einer Verbindung mit den Daten
In dieser Umgebung können Sie sicher experimentieren, da Sie die Änderungen nicht speichern müssen. Wenn Sie sie speichern, können Sie jederzeit wieder auf **Daten abrufen** klicken, um ein neues Exemplar dieses Beispiels herunterzuladen.

Wir hoffen, diese Tour hat Ihnen gezeigt, wie Power BI-Dashboards, das Fragen- und Antwortenmodul und Berichte Ihnen Einblicke in Beispieldaten geben können. Jetzt liegt es an Ihnen – stellen Sie Verbindungen mit Ihren eigenen Daten her. Mit Power BI können Sie Verbindungen mit einer Vielzahl von Datenquellen herstellen. Weitere Informationen finden Sie unter [Erste Schritte mit dem Power BI-Dienst](service-get-started.md).

