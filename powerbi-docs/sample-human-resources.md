---
title: 'Beispiel für das Personalwesen: Übersicht'
description: 'Beispiel für Personalwesen für Power BI: Übersicht'
author: maggiesMSFT
ms.reviewer: amac
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 07/05/2019
ms.author: maggies
LocalizationGroup: Samples
ms.openlocfilehash: 8124a80f471e33ebbd140a30d6a49e2a762206ee
ms.sourcegitcommit: 444f7fe5068841ede2a366d60c79dcc9420772d4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/30/2020
ms.locfileid: "80404111"
---
# <a name="human-resources-sample-for-power-bi-take-a-tour"></a>Beispiel für Personalwesen für Power BI: Übersicht

Das Beispielinhaltspaket Personalwesen enthält ein Dashboard, einen Bericht und ein Dataset für eine Personalabteilung. In diesem Beispiel verwendet die Personalabteilung dasselbe Berichtsmodell für unterschiedliche Unternehmen, auch wenn diese sich nach Branche oder Größe unterscheiden. Die Untersuchungen in diesem Beispiel betreffen Neueinstellungen, aktive Mitarbeiter und ehemalige Mitarbeiter. Es zielt darauf ab, Trends in der Einstellungsstrategie aufzudecken. Hauptsächlich sollen folgende Erkenntnisse gewonnen werden:

* Wen wir einstellen
* Tendenzen unserer Personalgewinnungsstrategie
* Trends bei freiwilligem Ausscheiden

![Dashboard für das Personalwesenbeispiel](media/sample-human-resources/hr1.png)

Dieses Beispiel ist Teil einer Reihe, die Ihnen die Verwendung von Power BI anhand geschäftsbezogener Daten, Berichte und Dashboards zeigt. Es wurde von [obviEnce](http://www.obvience.com/) mit echten Daten erstellt, die anonymisiert wurden. Die Daten sind in verschiedenen Formaten verfügbar: Inhaltspaket, Power BI Desktop-PBIX-Datei oder Excel-Arbeitsmappe. Weitere Informationen finden Sie unter [Welche Beispieldaten sind für die Verwendung mit Power BI verfügbar?](sample-datasets.md). 

In diesem Tutorial wird das Personalwesen-Beispielinhaltspaket im Power BI-Dienst erörtert. Da die Berichtsoberfläche in Power BI Desktop und im Dienst ähnlich sind, können Sie das Tutorial auch anhand der PBIX-Beispieldatei in Power BI Desktop nachvollziehen. 

Sie benötigen keine Power BI-Lizenz, um die Beispiele in Power BI Desktop kennenzulernen. Wenn Sie nicht über eine Power BI Pro-Lizenz verfügen, können Sie das Beispiel im Power BI-Dienst in Ihrem Arbeitsbereich speichern. 

## <a name="get-the-sample"></a>Abrufen des Beispiels

Bevor Sie das Beispiel verwenden können, müssen Sie es zunächst als [Inhaltspaket](#get-the-content-pack-for-this-sample), [PBIX-Datei](#get-the-pbix-file-for-this-sample) oder [Excel-Arbeitsmappe](#get-the-excel-workbook-for-this-sample) herunterladen.

### <a name="get-the-content-pack-for-this-sample"></a>Abrufen des Inhaltspakets für dieses Beispiel

1. Öffnen Sie den Power BI-Dienst (app.powerbi.com), melden Sie sich an, und öffnen Sie den Arbeitsbereich, in dem Sie das Beispiel speichern möchten.

   Wenn Sie nicht über eine Power BI Pro-Lizenz verfügen, können Sie das Beispiel in Ihrem Arbeitsbereich speichern.

2. Wählen Sie in der linken unteren Ecke **Daten abrufen** aus.
   
   ![„Daten abrufen“ auswählen](media/sample-datasets/power-bi-get-data.png)
3. Klicken Sie auf der daraufhin angezeigten Seite **Daten abrufen** auf **Beispiele**.
   
4. Wählen Sie **Beispiel für das Personalwesen** aus, und wählen Sie dann **Verbinden**.  
   
   ![Verbindung mit Beispiel herstellen](media/sample-human-resources/pbi_hr_sample_connect.png)

5. Das Inhaltspaket wird in Power BI importiert, und dem aktuellen Arbeitsbereich werden ein neues Dashboard, ein neuer Bericht und ein neues Dataset hinzugefügt.
   
   ![Eintrag „Beispiel für das Personalwesen“](media/sample-human-resources/hr-sample-entry.png)
  
### <a name="get-the-pbix-file-for-this-sample"></a>Abrufen der PBIX-Datei für dieses Beispiel

Alternativ können Sie das Beispiel für das Personalwesen als [PBIX-Datei](https://download.microsoft.com/download/6/9/5/69503155-05A5-483E-829A-F7B5F3DD5D27/Human%20Resources%20Sample%20PBIX.pbix) herunterladen, ein für Power BI Desktop entworfenes Dateiformat.

### <a name="get-the-excel-workbook-for-this-sample"></a>Abrufen der Excel-Arbeitsmappe für dieses Beispiel

Wenn Sie sich die Datenquelle für dieses Beispiel ansehen möchten, dieses steht auch als [Excel-Arbeitsmappe](https://go.microsoft.com/fwlink/?LinkId=529780) zur Verfügung. Die Arbeitsmappe enthält Power View-Blätter, die Sie anzeigen und ändern können. Aktivieren Sie die Add-Ins für die Datenanalyse, um die Rohdaten anzuzeigen, und klicken Sie dann auf **Power Pivot > Verwalten**. Weitere Informationen zum Aktivieren der Add-Ins für Power View und Power Pivot finden Sie unter [Kennenlernen der Excel-Beispiele in Excel](sample-datasets.md#explore-excel-samples-inside-excel).

## <a name="new-hires"></a>Neue Mitarbeiter
Betrachten Sie zunächst die Neueinstellungen.

1. Wählen Sie im Arbeitsbereich die Registerkarte **Dashboards** aus, und öffnen Sie das Dashboard **Beispiel für das Personalwesen**.
2. Wählen Sie im Dashboard die Kachel **Anzahl der Neueinstellungen, Neueinstellungen im gleichen Zeitraum des Vorjahres, % Veränderung der Aktiven im Jahresvergleich nach Monat** aus.  

   ![Kachel „Anzahl der Neueinstellungen“](media/sample-human-resources/hr2.png)  

   Der Beispielbericht „Personalwesen“ wird auf der Seite **Neueinstellungen** geöffnet.  

   ![Seite „Neueinstellungen“](media/sample-human-resources/hr3.png)

3. Sehen Sie sich diese interessanten Elemente an:

    * Das Kombinationsdiagramm **Anzahl der Neueinstellungen, Neueinstellungen GZVJ und % Aktive im Jahresvergleich – Veränderung nach Monat** zeigt, dass wir in jedem Monat des laufenden Jahres mehr Mitarbeiter als im Vorjahr eingestellt haben. In einigen Monaten erheblich mehr Mitarbeiter.
    * Beachten Sie im Kombinationsdiagramm **New Hire Count and Active Employee Count by Region and Ethnicity** (Anzahl der Neueinstellungen und der aktiven Mitarbeiter nach Region und ethnischer Gruppe), dass weniger Personen in der Region **Osten** eingestellt werden.
    * Das Wasserfalldiagramm **New Hires YoY Var by Age Group** (Abweichung der Neueinstellungen im Jahresvergleich nach Altersgruppe) zeigt, dass vor allem jüngere Menschen eingestellt werden. Die Ursache dieses Trends könnte sein, dass die Stellen häufig Teilzeitstellen sind.
    * Das Kreisdiagramm **Anzahl der Neueinstellungen nach Geschlecht** zeigt eine ziemlich gleichmäßige Verteilung.

    Gewinnen Sie weitere Erkenntnisse? Beispielsweise eine Region, in der die Verteilung nach Geschlecht nicht gleichmäßig ist. 

4. Wählen Sie in den Diagrammen die verschiedenen Altersgruppen und Geschlechter aus, um die Beziehungen zwischen Alter, Geschlecht, Region und ethnischer Gruppe zu untersuchen.

5. Wählen Sie im oberen Navigationsbereich **Beispiel für das Personalwesen** aus, um zum Dashboard zurückzukehren.

   ![Rückkehr zum Dashboard](media/sample-human-resources/power-bi-breadcrumbs.png)

## <a name="compare-currently-active-and-former-employees"></a>Vergleichen der derzeit aktiven und ehemaligen Mitarbeiter
Sehen Sie sich die Daten für die derzeit aktiven Mitarbeiter und die Mitarbeiter an, die nicht mehr für das Unternehmen arbeiten.

1. Wählen Sie auf dem Dashboard die Kachel **Anzahl der aktiven Mitarbeiter nach Altersgruppen** aus.

   ![Anzahl der aktiven Mitarbeiter nach Kachel „Altersgruppe“](media/sample-human-resources/pbi_hr_sample_activepie.png)

   Der Beispielbericht „Personalwesen“ wird auf der Seite **Aktive Mitarbeiter i. Vgl. zu Trennungen** geöffnet.  

   ![Seite „Aktive Mitarbeiter i. Vgl. zu Trennungen“](media/sample-human-resources/hr5.png)

 2. Sehen Sie sich diese interessanten Elemente an:

    * In den beiden Kombinationsdiagrammen auf der linken Seite wird die Veränderung Jahr über Jahr für aktive und ausgeschiedene Mitarbeiter angezeigt. Aufgrund von vermehrten Einstellungen haben wir in diesem Jahr mehr aktive, aber auch mehr ausgeschiedene Mitarbeiter als im letzten Jahr.
    * Im August hatten wir im Vergleich zu den anderen Monaten mehr ausgeschiedene Mitarbeiter. Wählen Sie die verschiedenen Altersgruppen, Geschlechter oder Regionen aus, um festzustellen, ob Ausreißer vorhanden sind.
    * Wenn wir uns die Kreisdiagramme ansehen, fällt auf, dass in Bezug auf die aktiven Mitarbeiter nach Geschlecht und Altersgruppe eine relativ gleichmäßige Verteilung besteht. Wählen Sie verschiedene Altersgruppen aus, um die Geschlechtsverteilung nach Alter anzuzeigen. Liegt für jede Altersgruppe eine gleichmäßige Verteilung nach Geschlecht vor?

## <a name="reasons-for-separation"></a>Gründe für das Ausscheiden
Sehen Sie sich den Bericht in der Bearbeitungsansicht an. Sie können die Kreisdiagramme so ändern, dass sie Daten ausgeschiedener Mitarbeiter anstelle der Daten aktiver Mitarbeiter anzeigen.

1. Wählen Sie in der oberen linken Ecke **Bericht bearbeiten** aus.

2. Wählen Sie das Kreisdiagramm **Anzahl der aktiven Mitarbeiter nach Altersgruppen** aus.

3. Wählen Sie unter **Felder** **Mitarbeiter** aus, um die Tabelle **Mitarbeiter** zu erweitern. Deaktivieren Sie **Anzahl der aktiven Mitarbeiter**, um das Feld zu entfernen.

4. Wählen Sie **Anzahl der Ausgeschiedenen** in der Tabelle **Mitarbeiter** aus, um dieses Element dem Bereich **Werte** im Bereich **Feld** hinzuzufügen.

5. Aktivieren Sie im Zeichenbereich für den Bericht im Balkendiagramm **Anzahl der Trennungen nach Trennungsgrund** den Balken **Freiwillig**. 

   Dieser Balken hebt in den anderen Visualisierungen im Bericht die Mitarbeiter hervor, die freiwillig ausgeschieden sind.

6. Wählen Sie im Kreisdiagramm **Anzahl der Trennungen nach Altersgruppe** das Segment „50+“ aus.

7. Sehen Sie sich das Liniendiagramm unten rechts an. Dieses Diagramm wird gefiltert, um freiwillig ausgeschiedene Mitarbeiter anzuzeigen.  

   ![Trennungen der Mitarbeiter über 50](media/sample-human-resources/pbi_hr_sample_sepsover50.png)

   Beachten Sie den Trend in der Altersgruppe 50+. In der zweiten Jahreshälfte schieden vermehrt Mitarbeiter mit mehr als 50 Jahren freiwillig aus. Dieser Trend kann anhand von weiteren Daten genauer untersucht werden.

8. Sie können die gleichen Schritte auch für das Kreisdiagramm **Anzahl der aktiven Mitarbeiter nach Geschlecht** ausführen und es von aktiven Mitarbeitern in Trennungen ändern. Sehen Sie sich die Daten zum freiwilligen Ausscheiden nach Geschlecht an, um nach weiteren Erkenntnissen zu suchen.

9. Wählen Sie im oberen Navigationsbereich **Beispiel für das Personalwesen** aus, um zum Dashboard zurückzukehren. Wenn Sie möchten, können Sie die vorgenommen Änderungen speichern.

## <a name="bad-hires"></a>Fehleinstellungen
Als Letztes untersuchen wir den Bereich der Fehleinstellungen. Bei Fehleinstellungen handelt es sich um Mitarbeiter, die weniger als 60 Tage im Unternehmen tätig waren. Wir stellen schnell ein, aber stellen wir auch gute Kandidaten ein?

1. Wählen Sie die Dashboardkachel **Fehleinstellungen in % aktiver Mitarbeiter nach Altersgruppe** aus. Der Bericht öffnet Registerkarte drei, **Fehleinstellungen**.

   ![Kachel „Fehleinstellungen unter aktiven Mitarbeitern in Prozent nach Altersgruppe“](media/sample-human-resources/hr7.png)  
2. Wählen Sie im Datenschnitt **Region** auf der linken Seite **Nordwesten** und im Ringdiagramm **Anzahl der Fehleinstellungen nach Geschlecht** **Männlich** aus. Sehen Sie sich die anderen Diagramme auf der Seite **Fehleinstellungen** an. Beachten Sie, dass es mehr männliche als weibliche Fehleinstellungen gibt und viele Fehleinstellungen der Gruppe A.

   ![Fehleinstellungen im Nordwesten](media/sample-human-resources/pbi_hr_sample_badhirespage.png)  

3. Wenn Sie sich das Ringdiagramm **Anzahl der Fehleinstellungen nach Geschlecht** ansehen und verschiedene Regionen im Datenschnitt **Region** auswählen, werden Sie feststellen, dass die Region „Osten“ die einzige Region mit mehr weiblichen als männlichen Fehleinstellungen ist.  

4. Wählen Sie den Namen des Dashboards aus dem oberen Navigationsbereich aus, um zum Dashboard zurückzukehren.

## <a name="ask-a-question-in-the-dashboard-qa-box"></a>Stellen einer Frage im Q&A-Feld des Dashboards
Im Dashboard können Sie im [Q&A-Fragenfeld](power-bi-tutorial-q-and-a.md) eine Frage zu Ihren Daten in natürlicher Sprache stellen. Q&A erkennt die eingegebenen Wörter und schließt, wo in Ihrem Dataset eine Antwort zu finden ist.

1. Wählen Sie das Q&A-Fragefeld aus. Beachten Sie: Noch bevor Sie mit der Eingabe beginnen, zeigt Q&A Vorschläge für die Formulierung Ihrer Frage an.

   ![Vorschläge im Q&A-Feld](media/sample-human-resources/pbi_hr_sample_qabox.png)

2. Sie können einen dieser Vorschläge auswählen oder eingeben: *Altersgruppe, Geschlecht und Fehleinstellungen im gleichen Vorjahreszeitraum für Region „Osten“ anzeigen*.  

   ![Antworten im Q&A-Feld](media/sample-human-resources/pbi_hr_sample_qa_answer.png)

   Beachten Sie, dass die meisten der weiblichen Fehleinstellungen jünger als 30 Jahre sind.

## <a name="next-steps-connect-to-your-data"></a>Nächste Schritte: Herstellen einer Verbindung mit den Daten
In dieser Umgebung können Sie sicher experimentieren, da Sie die Änderungen nicht speichern müssen. Wenn Sie sie speichern, können Sie jederzeit wieder auf **Daten abrufen** klicken, um ein neues Exemplar dieses Beispiels herunterzuladen.

Wir hoffen, diese Tour hat Ihnen gezeigt, wie Power BI-Dashboards, das Fragen- und Antwortenmodul und Berichte Ihnen Einblicke in Beispieldaten geben können. Jetzt liegt es an Ihnen – stellen Sie Verbindungen mit Ihren eigenen Daten her. Mit Power BI können Sie Verbindungen mit einer Vielzahl von Datenquellen herstellen. Weitere Informationen finden Sie unter [Erste Schritte mit dem Power BI-Dienst](service-get-started.md).
