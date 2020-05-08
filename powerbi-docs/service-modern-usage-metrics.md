---
title: Überwachen von Metriken mit der neuen Arbeitsbereichsfunktion
description: In diesem Artikel erfahren Sie, wie Sie Nutzungsmetriken in der neuen Arbeitsbereichsfunktion für Power BI-Dashboards und -Berichte verwenden.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
featuredvideoid: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 01/22/2020
LocalizationGroup: Dashboards
ms.openlocfilehash: d3f359ad4c968407dff143458b65954844f9a22d
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "76829280"
---
# <a name="monitor-usage-metrics-in-the-new-workspace-experience"></a>Überwachen von Metriken mit der neuen Arbeitsbereichsfunktion

Wenn Sie wissen, wie Ihre Inhalte verwendet werden, können Sie die Relevanz veranschaulichen und Prioritäten setzen. Die Nutzungsmetriken können z.B. zeigen, dass einer Ihrer Berichte täglich durch eine Vielzahl von Mitarbeitern in der Organisation verwendet wird oder dass ein von Ihnen erstelltes Dashboard überhaupt nicht angezeigt wird. Diese Art von Feedback ist für Ihre Arbeit von großem Wert.

Wenn Sie Berichte in den neuen Arbeitsbereichen erstellen, verfügen Sie über Zugriff über verbesserte Berichte zu Nutzungsmetriken, anhand denen Sie ermitteln können, wie die Berichte in Ihrer Organisation verwendet werden und wer sie verwendet. Außerdem können Sie allgemeine Leistungsprobleme identifizieren. Die verbesserten Nutzungsberichte der neuen Arbeitsbereichsfunktion ersetzen die vorherigen Berichte zu Nutzungsmetriken, die unter [Überwachen von Nutzungsmetriken für Power BI-Dashboards und Berichte](service-usage-metrics.md) dokumentiert wurden.

![Neuer Bericht zu Nutzungsmetriken](media/service-modern-usage-metrics/power-bi-modern-usage-metrics.png)

> [!NOTE]
> Sie können im Power BI-Dienst nur Berichte zu Nutzungsmetriken ausführen. Wenn Sie jedoch einen Bericht zu Nutzungsmetriken speichern oder diesen an ein Dashboard anheften, können Sie diesen Bericht auf mobilen Geräten öffnen und damit interagieren.

## <a name="prerequisites"></a>Voraussetzungen

- Sie benötigen eine Power BI Pro-Lizenz, um auf Nutzungsmetrikdaten zuzugreifen. Allerdings erfasst das Feature „Nutzungsmetriken“ Informationen zur Nutzung durch alle Benutzer, unabhängig davon, welche Lizenz ihnen zugewiesen ist.
- Der Bericht muss sich in einem neuen Arbeitsbereich befinden, und Sie müssen über Bearbeitungszugriff auf diesen Bericht verfügen, um auf die verbesserten Nutzungsmetriken für einen Bericht zuzugreifen.
- Außerdem muss Ihr Power BI-Administrator die Nutzungsmetriken für Inhaltsersteller aktiviert haben. Möglicherweise hat Ihr Power BI-Administrator darüber hinaus das Erfassen von Daten pro Benutzer in den Nutzungsmetriken aktiviert. Erfahren Sie mehr über das [Aktivieren dieser Optionen im Verwaltungsportal](service-admin-portal.md#control-usage-metrics).

## <a name="create--view-an-improved-usage-metrics-report"></a>Erstellen und Anzeigen von Berichten mit verbesserten Nutzungsmetriken

Ausschließlich Benutzer mit den Berechtigungen „Administrator“, „Mitglied“ oder „Mitwirkender“ können Berichte mit verbesserten Nutzungsmetriken anzeigen. Anzeigeberechtigungen sind unzureichend. Wenn Sie mindestens über die Rolle „Mitwirkender“ für einen neuen Arbeitsbereich verfügen, in dem sich Ihr Bericht befindet, können Sie folgendermaßen die verbesserten Nutzungsmetriken anzeigen:

1. Öffnen Sie den Arbeitsbereich, der den Bericht enthält, dessen Nutzungsmetriken Sie analysieren möchten.
2. Öffnen Sie über die Inhaltsliste des Arbeitsbereichs das Kontextmenü des Berichts, und wählen Sie dann **Bericht zu Nutzungsmetriken anzeigen** aus. Alternativ öffnen Sie den Bericht, dann das Kontextmenü, und wählen Sie anschließend **Nutzungsmetriken** aus.

    ![Nutzungsmetriken anzeigen](media/service-modern-usage-metrics/power-bi-modern-view-usage-metrics.png)

1. Wenn Sie erstmals so vorgehen, erstellt Power BI den Bericht zu den Nutzungsmetriken und lässt Sie wissen, wenn er bereit ist.

    ![Bericht zu Nutzungsmetriken ist bereit](media/service-modern-usage-metrics/power-bi-modern-usage-metrics-ready.png)

1. Wählen Sie **Nutzungsmetriken anzeigen** aus, um die Ergebnisse anzuzeigen.
2. Wenn Sie dies zum ersten Mal tun, öffnet Power BI möglicherweise den alten Bericht zu Nutzungsmetriken. Schalten Sie „Neuer Nutzungsbericht aus“ in der oberen rechten Ecke in **Neuer Nutzungsbericht ein** um, um den Bericht mit verbesserten Nutzungsmetriken anzuzeigen.

    ![Zum neuen Bericht zu Nutzungsmetriken wechseln](media/service-modern-usage-metrics/power-bi-modern-usage-metrics-on.png)

    > [!NOTE]
    > Die Option für den neuen Bericht zu Nutzungsmetriken wird nur angezeigt, wenn Ihr Bericht sich in einem neuen Arbeitsbereich befindet. Alte Arbeitsbereiche stellen keine Berichte zu verbesserten Nutzungsmetriken bereit.

## <a name="about-the-improved-usage-metrics-report"></a>Informationen zu Berichten mit verbesserten Nutzungsmetriken

Wenn Sie den Bericht mit verbesserten Nutzungsmetriken anzeigen, indem Sie die obigen Anweisungen befolgen, generiert Power BI einen vorgefertigten Bericht mit Nutzungsmetriken zu diesem Inhalt für die letzten 30 Tage. Dieser Bericht sieht ganz ähnlich aus wie die Power BI-Berichte, die Sie bereits kennen. Je nachdem, wie Ihre Endbenutzer Zugriff erhalten haben, über das Web, eine mobile App usw., können Sie Datenschnitte anlegen. So wie sich Ihre Berichte entwickeln, wird sich auch der Bericht zu Nutzungsmetriken entwickeln, der täglich mit neuen Daten aktualisiert wird.

> [!NOTE]
> Berichte zu Nutzungsmetriken werden nicht unter „Zuletzt verwendet“, „Arbeitsbereiche“, „Favoriten“ oder in anderen Inhaltslisten angezeigt. Sie können nicht zu Apps hinzugefügt werden. Wenn Sie eine Kachel aus einem Nutzungsmetrikbericht an ein Dashboard anheften, können Sie dieses Dashboard nicht zu einer App hinzufügen.

### <a name="usage-metrics-report-dataset"></a>Dataset für den Bericht zu Nutzungsmetriken

Der Bericht mit verbesserten Nutzungsmetriken nutzt das Dataset für den Bericht zu Nutzungsmetriken, das automatisch von Power BI erstellt wird, wenn Sie den Bericht mit verbesserten Nutzungsmetriken zum ersten Mal starten. Power BI aktualisiert dieses Dataset dann täglich. Sie können den Aktualisierungszeitplan zwar nicht ändern, aber Sie können die Anmeldeinformationen ändern, die Power BI zum Aktualisieren der Nutzungsmetrikdaten verwendet. Dies kann zum Fortsetzen der geplanten Aktualisierung erforderlich sein, wenn die Anmeldeinformationen abgelaufen sind oder Sie den Benutzer entfernt haben, der den Bericht zu Nutzungsmetriken ursprünglich über den Arbeitsbereich gestartet hat, in dem sich das Dataset befindet.

### <a name="usage-metrics-report-pages"></a>Seiten des Berichts zu Nutzungsmetriken

Der Bericht mit verbesserten Nutzungsmetriken enthält die folgenden Berichtsseiten:

- **Berichtsnutzung:** Auf dieser Seite werden Informationen zu Berichtsaufrufen und Berichtsbetrachter angezeigt, z. B. wie viele Benutzer den Bericht nach Datum angezeigt haben.
- **Berichtsleistung:** Zeigt die üblichen Berichtsöffnungszeiten nach Verwendungsmethode und Browserart an.
- **Häufig gestellte Fragen:** Bietet Antworten zu häufig gestellten Fragen, z. B. „Was ist ein „Betrachter“ und was ist eine „Anzeige“?

### <a name="which-metrics-are-reported"></a>Welche Metriken werden gemeldet?

| **Seite** | **Metrik** | **Beschreibung** |
| --- | --- | --- |
| Melden der Nutzung | Berichtsaufrufe | Jedes Mal, wenn jemand einen Bericht öffnet, wird ein Berichtsaufruf aufgezeichnet. Beachten Sie, dass sich die Definition eines Aufrufs von der Definition in vorherigen Berichten zu Nutzungsmetriken unterscheidet. Das Wechseln zwischen Berichtsseiten wird nicht mehr als zusätzlicher Aufruf gezählt. |
| Melden der Nutzung | Eindeutige Aufrufer | Ein Aufrufer ist jemand, der den Bericht mindestens einmal während des Zeitraums geöffnet hat (basierend auf dem Azure Active Directory-Benutzerkonto). |
| Melden der Nutzung | Aufruftrend | Der Aufruftrend zeigt, wie sich die Anzahl der Aufrufe mit der Zeit ändert. Er vergleicht die erste Hälfte des ausgewählten Zeitraums mit der zweiten Hälfte. |
| Melden der Nutzung | Datenschnitt nach Datum | Sie können den Zeitraum auf der Seite „Berichtsnutzung“ ändern, um Trends beispielsweise Woche für Woche oder nach zwei Wochen zu berechnen. In der unteren linken Ecke der Berichtsnutzungsseite können Sie das früheste und späteste Datum sehen, für das Nutzungsdaten zum ausgewählten Bericht verfügbar sind. |
| Melden der Nutzung | Rank | Dieser Rang zeigt je nach Aufrufanzahl an, wie beliebt der Bericht im Vergleich zu allen anderen Berichten der Organisation ist.   |
| Melden der Nutzung | Berichtsaufrufe pro Tag | Diese Metrik gibt die Gesamtanzahl der Aufrufe pro Tag an. |
| Melden der Nutzung | Berichtsaufrufer pro Tag | Diese Metrik zeigt die Gesamtanzahl der verschiedenen Benutzer an, die den Bericht aufgerufen haben (basierend auf dem Azure Active Directory-Benutzerkonto). |
| Melden der Nutzung | Verteilungsmethode | Diese Metrik gibt an, wie Benutzer den Zugriff auf den Bericht erhalten haben, z. B. weil sie Mitglieder eines Arbeitsbereichs sind, weil der Bericht für sie freigegeben wurde oder weil sie eine App installiert haben. |
| Melden der Nutzung | Datenschnitt nach Plattform | Diese Metrik gibt an, ob der Zugriff auf den Bericht über den Power BI-Dienst (powerbi.com), Power BI Embedded oder ein Mobilgerät erfolgt ist. |
| Melden der Nutzung | Benutzer mit Berichtsaufrufen | Diese Metrik zeigt eine Liste der Benutzer nach der Anzahl an Aufrufen an, die den Bericht geöffnet haben. |
| Melden der Nutzung | Seiten | Wenn der Bericht mehr als eine Seite hat, segmentieren Sie den Bericht anhand der Seiten, die aufgerufen wurden. Wenn Sie eine Listenoption für „Blank“ sehen, bedeutet dies, dass vor Kurzem eine Berichtsseite hinzugefügt wurde (innerhalb von 24 Stunden wird der tatsächliche Name der neuen Seite in der Datenschnittliste angezeigt) bzw. dass Berichtsseiten gelöscht wurden. „Blank“ erfasst derartige Situationen. |
| Berichtsleistung | Durchschnittliche Zeit zum Öffnen | Die durchschnittliche Zeit zum Öffnen eines Berichts entspricht dem 50. Perzentil für die Zeit, die es dauert, den Bericht zu öffnen. Anders ausgedrückt, beschreibt diese Metrik die Zeit, in der 50 % der Aktionen zum Öffnen des Berichts ausgeführt werden. Auf der Seite „Berichtsleistung“ wird die durchschnittliche Zeit zum Öffnen von Berichten nach Verwendungsmethode und Browserart aufgeführt.   |
| Berichtsleistung | Öffnungszeittrend | Der Öffnungszeittrend zeigt, wie sich die Leistung beim Öffnen von Berichten mit der Zeit ändert. Dabei werden die Öffnungszeiten für den Bericht aus der ersten Hälfte des ausgewählten Zeitraums mit den Zeiten aus der zweiten Hälfte verglichen. |
| Berichtsleistung | Datenschnitt nach Datum | Sie können den Zeitraum auf der Seite „Berichtsleistung“ ändern, um Trends beispielsweise Woche für Woche oder nach zwei Wochen zu berechnen. In der unteren linken Ecke der Berichtsleistungsseite können Sie das früheste und späteste Datum sehen, für das Nutzungsdaten zum ausgewählten Bericht verfügbar sind. |
| Berichtsleistung | Tägliche Leistung | Diese Metrik berechnet die Leistung für 10 %, 50 % und 90 % der Aktionen zum Öffnen von Berichten für jeden einzelnen Tag. |
| Berichtsleistung | 7-tägige Leistung | Diese Metrik berechnet die Leistung für 10 %, 50 % und 90 % der Aktionen zum Öffnen von Berichten für jeden der letzten 7 Tage. |
| Berichtsleistung | Verwendungsmethode | Diese Metrik gibt an, wie Benutzer den Bericht geöffnet haben, z. B. über den Power BI-Dienst (powerbi.com), Power BI Embedded oder ein Mobilgerät. |
| Berichtsleistung | Browsers | Diese Metrik gibt an, welchen Browser Benutzer zum Öffnen des Berichts verwenden, z. B. Firefox, Microsoft Edge und Google Chrome. |

## <a name="update-usage-metrics-report-credentials"></a>Aktualisieren der Anmeldeinformationen für einen Bericht zu Nutzungsmetriken

Mit der folgenden Vorgehensweise können Sie ein Dataset für einen Bericht zu Nutzungsmetriken übernehmen und die Anmeldeinformationen aktualisieren.

1. Öffnen Sie den Arbeitsbereich, der den Bericht enthält, dessen Dataset für den Bericht zu Nutzungsmetriken Sie aktualisieren möchten.
2. Klicken Sie in der schwarzen Kopfzeile oben auf das Symbol **Einstellungen**, und wählen Sie dann **Einstellungen** aus.

    ![„Einstellungen“ auswählen](media/service-modern-usage-metrics/power-bi-settings-settings.png)

3. Wechseln Sie zur Registerkarte **Datasets**.

1. Wählen Sie das Dataset für den Bericht zu Nutzungsmetriken aus. 

    ![Wählen Sie das Dataset für die Nutzungsmetriken aus.](media/service-modern-usage-metrics/power-bi-select-usage-metrics.png)
    
    Wenn Sie nicht der aktuelle Besitzer des Datasets sind, müssen Sie den Besitz übernehmen, um die Anmeldeinformationen für die Datenquelle ändern zu können. 
    
5. Klicken Sie auf **Übernehmen**, und klicken Sie im daraufhin geöffneten Dialogfeld **DataSet-Einstellungen übernehmen** noch mal auf **Übernehmen**.

1. Wählen Sie unter **Anmeldeinformationen für die Datenquelle** die Option **Anmeldeinformationen bearbeiten** aus.

    ![Anmeldeinformationen bearbeiten](media/service-modern-usage-metrics/power-bi-usage-metrics-edit-credentials.png)

2. Klicken Sie im Dialogfeld **Configure Usage Metrics Report** (Bericht zu Nutzungsmetriken konfigurieren) auf **Anmelden**.

    ![Auf Anmelden klicken](media/service-modern-usage-metrics/power-bi-modern-usage-metrics-configure.png)

1. Schließen Sie den Anmeldevorgang ab, und achten Sie darauf, dass eine Benachrichtigung angezeigt wird, die bestätigt, dass die Datenquelle erfolgreich aktualisiert wurde.

    > [!NOTE]
    > Das Dataset für den Bericht zu Nutzungsmetriken enthält Nutzungsdaten für die letzten 30 Tage. Es kann bis zu 24 Stunden dauern, bis neue Nutzungsdaten importiert werden. Sie können keine manuelle Aktualisierung über die Power BI-Benutzeroberfläche auslösen.


## <a name="disable-usage-metrics-reports"></a>Deaktivieren der Berichte zu Nutzungsmetriken

Berichte zu Nutzungsmetriken sind ein Feature, das Power BI- oder Office 365-Administratoren aktivieren oder deaktivieren können. Administratoren können präzise steuern, welche Benutzer Zugang zu Nutzungsmetriken haben. In der Standardeinstellung sind diese für alle Benutzer in der Organisation auf EIN festgelegt. Details zu diesen Einstellungen finden Sie unter [Steuern von Nutzungsmetriken](service-admin-portal.md#control-usage-metrics) im Artikel zum Verwaltungsportal.

> [!NOTE]
> Nur Administratoren für den Power BI-Mandanten können die Einstellungen des Verwaltungsportals und die Bearbeitungseinstellungen sehen.

## <a name="exclude-user-information-from-usage-metrics-reports"></a>Ausschließen von Benutzerinformationen auf Berichten zu Nutzungsmetriken

Die benutzerspezifischen Daten sind standardmäßig für die Nutzungsmetriken aktiviert, und die Kontoinformationen des Inhaltsnutzers sind im Bericht zu den Nutzungsmetriken enthalten. Wenn Administratoren diese Informationen für manche oder alle Benutzer nicht freigeben möchten, können sie Benutzerinformationen aus dem Nutzungsbericht ausschließen, indem sie „Benutzerbezogene Daten in Nutzungsmetriken für Inhaltsersteller“ in den Mandanteneinstellungen des Power BI-Verwaltungsportals für bestimmte Sicherheitsgruppen oder die gesamte Organisation deaktivieren.

1. Erweitern Sie hierzu die Option **Benutzerbezogene Daten in Nutzungsmetriken für Inhaltsersteller** unter **Überwachungs- und Nutzungseinstellungen** auf der Registerkarte **Mandanteneinstellungen** im Verwaltungsportal, und wählen Sie dann die Option **Deaktivieren** aus.

2. Entscheiden Sie, ob Sie **Alle vorhandenen benutzerbezogenen Daten im aktuellen Inhalt von Nutzungsmetriken löschen** möchten, und klicken Sie dann auf **Anwenden**.

    ![Benutzerbezogene Metriken deaktivieren](media/service-modern-usage-metrics/power-bi-admin-disable-per-user-metrics.png)

Wenn Benutzerinformationen ausgeschlossen werden, bezeichnet der Nutzungsbericht Benutzer als „Unnamed“ (Unbenannt).

Beim Deaktivieren von Nutzungsmetriken für die gesamte Organisation können Administratoren mit der Option „Alle vorhandenen Inhalte von Nutzungsmetriken löschen“ alle vorhandenen Berichte und Dashboardkacheln löschen, die mit den Berichten der Nutzungsmetriken erstellt wurden. Durch diese Option wird jeglicher Zugriff auf Nutzungsmetriken für alle Benutzer der Organisation entfernt, die diese möglicherweise bereits nutzen. Das Löschen vorhandener Inhalte von Nutzungsmetriken kann nicht rückgängig gemacht werden.

> [!NOTE]
> Nur Administratoren für den Power BI-Mandanten können das Verwaltungsportal anzeigen und die Einstellung „Benutzerbezogene Daten in Nutzungsmetriken für Inhaltsersteller“ konfigurieren.

## <a name="customize-the-usage-metrics-report"></a>Anpassen des Berichts zu Nutzungsmetriken

Ihnen stehen mehrere Optionen zum Untersuchen der Berichtsdaten oder zum Erstellen Ihrer eigenen Berichte für das zugrunde liegende Dataset zur Verfügung:

- **[Kopieren des Berichts](#create-a-copy-of-the-usage-report) im Power BI-Dienst:**   Verwenden Sie die Option **Kopie speichern**, um eine separate Instanz des Berichts zu Nutzungsmetriken zu erstellen, die Sie entsprechend Ihrer spezifischen Anforderungen anpassen können.
- **[Herstellen einer Verbindung mit dem Dataset](#create-a-new-usage-report-in-power-bi-desktop) mit einem neuen Bericht:**   Wie zuvor im Abschnitt [Dataset für den Bericht zu Nutzungsmetriken](#usage-metrics-report-dataset) erläutert, trägt das Dataset in allen Arbeitsbereichen den Namen „Bericht zu Nutzungsmetriken“. Sie können Power BI Desktop zum Erstellen von benutzerdefinierten Berichten zu Nutzungsmetriken auf dem zugrunde liegenden Dataset verwenden.
- **[Verwenden von „In Excel analysieren“](#analyze-usage-data-in-excel):**   Sie können die Features für PivotTables, Diagramme und Datenschnitte in Microsoft Excel 2010 SP1 oder höher nutzen, um die Power BI-Nutzungsdaten zu analysieren. Erfahren Sie mehr über das Feature [In Excel analysieren](service-analyze-in-excel.md).

### <a name="create-a-copy-of-the-usage-report"></a>Erstellen einer Kopie des Nutzungsberichts

Wenn Sie eine Kopie des schreibgeschützten, vordefinierten Nutzungsberichts erstellen, erstellt Power BI eine bearbeitbare Instanz des Berichts. Auf den ersten Blick sieht sie genau gleich aus. Allerdings können Sie den Bericht jetzt in der Bearbeitungsansicht öffnen, neue Visualisierungen, Seiten und Filter hinzufügen, vorhandene Visualisierungen ändern oder löschen usw. Power BI speichert den neuen Bericht im aktuellen Arbeitsbereich.

1. Klicken Sie im neuen Bericht zu Nutzungsmetriken auf das Menü **Weitere Optionen** (...), und wählen Sie dann auf **Kopie speichern**.

    ![Speichern einer Kopie des Berichts](media/service-modern-usage-metrics/power-bi-modern-usage-metrics-save.png)

2. Geben Sie im Dialogfeld **Bericht speichern** einen Namen ein, und klicken Sie dann auf **Speichern**.

    Power BI erstellt einen bearbeitbaren Power BI-Bericht, der im aktuellen Arbeitsbereich gespeichert wird, und öffnet die Kopie des Berichts. 

3. Klicken Sie auf das Menü **Weitere Optionen** (...), und klicken Sie dann auf **Bearbeiten**, um zur Bearbeitungsansicht zu wechseln. 

    Sie können beispielsweise die Filter ändern, neue Seiten hinzufügen, neue Visualisierungen erstellen, die Schriftarten und Farben formatieren usw.

1. Der neue Bericht wird auf der Registerkarte „Berichte“ im aktuellen Arbeitsbereich gespeichert und zur Inhaltsliste „Zuletzt verwendet“ hinzugefügt.

    ![Der neue Bericht auf der Registerkarte „Berichte“](media/service-modern-usage-metrics/power-bi-modern-usage-metrics-new-report.png)

### <a name="create-a-new-usage-report-in-power-bi-desktop"></a>Erstellen eines neuen Nutzungsberichts in Power BI Desktop

Sie können einen neuen Nutzungsbericht in Power BI Desktop basierend auf dem Dataset für den Bericht zu Nutzungsmetriken erstellen. Sie müssen beim Power BI-Dienst in Power BI Desktop angemeldet sein, um eine Verbindung mit dem Dataset für den Bericht zu Nutzungsmetriken herstellen und Ihren eigenen Bericht erstellen zu können. 

1. Öffnen Sie Power BI Desktop.

2. Wenn Sie nicht beim Power BI-Dienst angemeldet sind, wählen Sie im Menü **Datei** die Option **Anmelden** aus.

1. Klicken Sie im Menüband **Home** auf **Daten abrufen**, um eine Verbindung zum Dataset für den Bericht zu Nutzungsmetriken herzustellen.

4. Klicken Sie im linken Bereich auf **Power Platform**, und wählen Sie dann **Power BI-Datasets** > **Verbindung herstellen** aus.

    ![Daten abrufen > Power Platform](media/service-modern-usage-metrics/power-bi-desktop-get-data.png)

1. Scrollen Sie zum gewünschten Dataset, oder geben Sie *Bericht zu Nutzungsmetriken* in das Suchfeld ein. 

6. Überprüfen Sie in der Spalte „Arbeitsbereich“, ob Sie das richtige Dataset auswählen, und klicken Sie dann auf **Erstellen**. 

    ![Dataset für den Bericht zu Nutzungsmetriken auswählen](media/service-modern-usage-metrics/power-bi-desktop-select-usage-metrics.png)

7. Überprüfen Sie die Liste „Felder“ in Power BI Desktop, die Ihnen Zugriff auf die Tabellen, Spalten und Measures im ausgewählten Dataset gewährt.

    ![Felderliste des Berichts zu Nutzungsmetriken anzeigen](media/service-modern-usage-metrics/power-bi-desktop-fields-list.png)

1. Sie können nun benutzerdefinierte Nutzungsberichte erstellen und freigeben, die alle auf demselben Dataset für den Bericht zu Nutzungsmetriken basieren.

### <a name="analyze-usage-data-in-excel"></a>Analysieren der Nutzungsdaten in Excel

Wenn Sie eine Verbindung mit den Nutzungsdaten in Excel herstellen, können Sie PivotTables erstellen, die die vordefinierten Measures verwenden. Beachten Sie beim Herstellen einer Verbindung mit einem Power BI-Dataset, dass Excel-PivotTables keine Drag & Drop-Aggregation von numerischen Feldern unterstützen.

1. [Erstellen Sie zunächst eine Kopie des Berichts zu Nutzungsmetriken](#create-a-copy-of-the-usage-report), wenn Sie dies noch nicht getan haben. 

2. Öffnen Sie den neuen Bericht zu Nutzungsmetriken, klicken Sie auf das Menü **Weitere Optionen** (...), und klicken Sie dann auf **In Excel analysieren**.

    ![In Excel analysieren](media/service-modern-usage-metrics/power-bi-export-excel.png)

1. Wenn das Dialogfeld **Sie benötigen zunächst einige Excel-Updates** angezeigt wird, klicken Sie auf **Herunterladen**, und installieren Sie die neuesten Updates für die Power BI-Konnektivität, oder klicken Sie auf **Ich habe diese Updates bereits installiert**.

    ![Excel-Updates](media/service-modern-usage-metrics/power-bi-excel-updates.png)

    > [!NOTE]
    > In einigen Organisationen gelten möglicherweise Gruppenrichtlinienregeln, durch die eine Installation der erforderlichen Updates für „In Excel analysieren“ für Excel verhindert wird. Wenn Sie die Updates nicht installieren können, wenden Sie sich an Ihren Administrator.

1. Klicken Sie in dem Browserdialogfeld, das Sie fragt, was Sie mit der ODC-Datei des Berichts zu Nutzungsmetriken tun möchten, auf **Öffnen**.

    ![ODC-Datei öffnen](media/service-modern-usage-metrics/power-bi-open-odc-file.png)

1. Power BI startet Excel. Überprüfen Sie den Dateinamen und Pfad der ODC-Datei, und klicken Sie dann auf **Zulassen**.

    ![Excel-Sicherheitshinweis](media/service-modern-usage-metrics/power-bi-excel-security-notice.png)

1. Da Excel nun mit einer leeren PivotTable geöffnet wurde, können Sie Felder auf die Felder „Zeilen“, „Spalten“, „Filter“ und „Werte“ ziehen und benutzerdefinierte Ansichten Ihrer Nutzungsdaten erstellen.

    ![PivotTable in Excel](media/service-modern-usage-metrics/power-bi-pivottable-excel.png)

## <a name="usage-metrics-in-national-clouds"></a>Verwenden von Metriken in nationalen Clouds

Power BI ist in separaten nationalen Clouds verfügbar. Diese Clouds bieten das gleiche Maß an Sicherheit, Datenschutz, Konformität und Transparenz wie die globale Version von Power BI, kombiniert mit einem eindeutigen Modell für lokale Vorschriften zur Dienstbereitstellung, Datenresidenz, Zugriff und Kontrolle. Aufgrund dieses einzigartigen Modells für regionale Regelungen sind Nutzungsmetriken nicht in nationalen Clouds verfügbar. Weitere Informationen finden Sie in den [Informationen zu den nationalen Clouds](https://powerbi.microsoft.com/clouds/).

## <a name="considerations-and-limitations"></a>Überlegungen und Einschränkungen

Es ist wichtig zu verstehen, dass Unterschiede beim Vergleichen des Berichts mit verbesserten Nutzungsmetriken mit seinem Vorgänger auftreten können. Die Nutzungsmetriken des Berichts basieren nun auf Aktivitätsdaten, die vom Power BI-Dienst erfasst werden. Die vorherigen Versionen des Berichts zu Nutzungsmetriken nutzten Telemetriedaten vom Client, die nicht immer mit den Nutzungsmetriken übereinstimmen, die vom Dienst erfasst werden. Außerdem verwendet der verbesserte Bericht zu Nutzungsmetriken eine andere Definition für „Aufrufe“. Ein Aufruf ist ein Ereignis, bei dem ein Bericht geöffnet wird, das jedes Mal vom Dienst aufgezeichnet wird, wenn jemand einen Bericht öffnet. Das Wechseln zwischen Berichtsseiten wird nicht mehr als zusätzlicher Aufruf gezählt.

> [!NOTE]
> Da der verbesserte Bericht zu Nutzungsmetriken Aktivitätsdaten nutzt, die vom Power BI-Dienst erfasst werden, stimmen die Nutzungsmetriken nun mit den aggregierten Anzahlen von Aktivität in Überwachungs- und Aktivitätsprotokollen überein. Unter- und Überberechnung von Aktivitäten aufgrund von inkonsistenten Netzwerkverbindungen, Werbeblockern oder anderen clientseitigen Problemen, beeinträchtigen die Anzahl der Aufrufer und Aufrufe nicht mehr.

Neben den oben genannten Unterschieden zwischen den alten und den verbesserten Berichten zu Nutzungsmetriken sollten Sie die folgenden Einschränkungen des Vorschaurelease berücksichtigen:

- Dashboardnutzungsmetriken nutzen immer noch die alte Version der Berichte zu Nutzungsmetriken.
- Verbesserte Berichte zu Nutzungsmetriken sind nur für Berichte in den neuen Arbeitsbereichen verfügbar. Berichte in alten Arbeitsbereichen unterstützen nur die vorherige Version der Berichte zu Nutzungsmetriken.
- Berichtleistungsmetriken basieren auf Telemetriedaten vom Client. Bestimmte Arten von Aufrufen werden nicht von den Leistungsmessungen berücksichtigt. Wenn ein Benutzer beispielsweise in einer E-Mail auf einen Link zu einem Bericht klickt, wird dieser Aufruf in der Berichtsnutzung berücksichtigt, jedoch gibt es kein Ereignis für die Leistungsmetriken.
- Berichtsleistungsmetriken sind für paginierte Berichte nicht verfügbar. Die Registerkarte „Seiten“ auf der Seite „Berichtsnutzung“ und die Diagramme auf der Seite „Berichtsleistung“ zeigen keine Daten für diese Arten von Berichten.
- Die Benutzermaskierung funktioniert bei Verwendung von geschachtelten Gruppen nicht wie erwartet. Wenn Ihre Organisation die Einstellung „Benutzerbezogene Daten in Nutzungsmetriken für Inhaltsersteller“ in den Mandanteneinstellungen des Power BI-Verwaltungsportals deaktiviert hat, können nur die Mitglieder auf der obersten Ebene maskiert werden. Mitglieder von Untergruppen sind weiterhin sichtbar.
- Die Initialisierung des Datasets für den Bericht zu Nutzungsmetriken kann einige Minuten dauern, was zu einem leeren Bericht zu Nutzungsmetriken führt, weil die Power BI-Benutzeroberfläche nicht wartet, bis die Aktualisierung abgeschlossen ist. Überprüfen Sie den Aktualisierungsverlauf in den Einstellungen des Datasets für den Bericht zu Nutzungsmetriken, um zu überprüfen, ob der Aktualisierungsvorgang erfolgreich abgeschlossen wurde.
- Die Initialisierung des Datasets für den Bericht zu Nutzungsmetriken kann aufgrund einer Zeitüberschreitung beim Aktualisieren fehlschlagen. Anweisungen zum Lösen dieses Problems finden Sie unten im Abschnitt „Problembehandlung“.

## <a name="frequently-asked-questions"></a>Häufig gestellte Fragen

Neben den oben genannten Überlegungen und Einschränkungen können sich die folgenden Fragen und Antworten zu Nutzungsmetriken für Benutzer und Administratoren als nützlich erweisen:

**F:** Ich kann für einen Bericht keine Nutzungsmetriken ausführen.

**A:** Sie können nur Nutzungsmetriken für Berichte sehen, die Sie besitzen oder für die Sie über Bearbeitungsberechtigungen verfügen.

**F:** Warum wird die Option „Neuer Nutzungsbericht ein“ nicht in der oberen rechten Ecke meines bestehenden Berichts zu Nutzungsmetriken angezeigt?

**A:** Der verbesserte Bericht zu Nutzungsmetriken ist nur für Berichte in den neuen Arbeitsbereichen verfügbar.

**F:** Welcher Zeitraum wird vom Bericht abgedeckt?

**A:** Der Nutzungsbericht basiert auf den Aktivitätsdaten der letzten 30 Tage, mit Ausnahme der Aktivitäten des aktuellen Tags. Sie können den Zeitraum mithilfe des Datenschnitts nach Datum auf der Berichtnutzungsseite eingrenzen, um beispielsweise nur die Daten der letzten Woche zu analysieren.

**F:** Wann werden die aktuellsten Aktivitätsdaten angezeigt?

**A:** Der Nutzungsbericht umfasst Aktivitätsdaten bis zum letzten vollen Tag basierend auf der UTC-Zeitzone. Die im Bericht gezeigten Daten hängen außerdem von der Aktualisierungszeit des Datasets ab. Power BI aktualisiert das Dataset einmal pro Tag.

**F:** Die Daten scheinen nicht aktuell zu sein.

**A:** Beachten Sie, dass es bis zu 24 Stunden dauern kann, bis neue Aktivitätsdaten im Nutzungsbericht angezeigt werden.

**F:** Aus welcher Datenquelle stammen die Nutzungsdaten?

**A:** Das Dataset für den Bericht zu Nutzungsmetriken importiert Daten aus einem internen Power BI-Speicher für Nutzungsmetriken mithilfe eines benutzerdefinierten Datenconnectors für Nutzungsmetriken. Sie können die Anmeldeinformationen für den Datenconnector für Nutzungsmetriken auf der Seite mit den Einstellungen für das Dataset für den Bericht zu Nutzungsmetriken ändern.

**F:** Wie stelle ich eine Verbindung mit den Daten her? Oder wie ändere ich den Standardbericht?

**A:** Sie können eine Kopie eines schreibgeschützten, vorgefertigten Nutzungsberichts erstellen. Die Kopie des Berichts stellt eine Verbindung mit demselben Dataset her und ermöglicht Ihnen die Bearbeitung der Berichtsdetails.

**F:** Was ist ein „Aufrufer“ und was ist ein „Aufruf“?

**A:** Ein Aufrufer ist jemand, der den Bericht mindestens einmal während des Zeitraums geöffnet hat. Ein Aufruf ist ein Ereignis, bei dem ein Bericht geöffnet wurde. Jedes Mal, wenn jemand einen Bericht öffnet, wird ein Berichtsaufruf aufgezeichnet.

Beachten Sie, dass sich die Definition eines Aufrufs von der Definition in vorherigen Berichten zu Nutzungsmetriken unterscheidet. Das Wechseln zwischen Berichtsseiten wird nicht mehr als zusätzlicher Aufruf gezählt.

**F:** Wie wird der „Aufruftrend“ berechnet?

**A:** Der Aufruftrend zeigt, wie sich die Anzahl der Aufrufe mit der Zeit ändert. Er vergleicht die erste Hälfte des ausgewählten Zeitraums mit der zweiten Hälfte. Sie können den Zeitraum mithilfe des Datenschnitts nach Datum auf der Seite „Berichtsnutzung“ ändern, um Trends beispielsweise Woche für Woche oder nach zwei Wochen zu berechnen.

**F:** Was bedeuten „Verteilung“ und „Plattform“?

**A:** Die Verteilung gibt an, wie Aufrufer den Zugriff auf einen Bericht erhalten haben: durch direkte Freigabe, über Arbeitsbereichszugriff oder über eine App.

Die Plattform gibt an, welche Technologie ein Aufrufer verwendet hat, um einen Bericht zu öffnen: powerbi.com, Power BI Mobile oder Power BI Embedded.

**F:** Wie funktioniert die Rangfolge für die Berichte?

**A:** Dieser Rang zeigt je nach Aufrufanzahl an, wie beliebt der Bericht im Vergleich zu allen anderen Berichten der Organisation ist.

**F:** Was sind „Unnamed Users“ (Unbenannte Benutzer)?

**A:** Ihre Organisation kann Benutzerinformationen aus dem Nutzungsbericht ausschließen. In diesem Fall bezeichnet der Nutzungsbericht Benutzer als „Unnamed“ (Unbenannt).

**F:** Was ist die „durchschnittliche Zeit zum Öffnen eines Berichts“?

**A:** Die durchschnittliche Zeit zum Öffnen eines Berichts entspricht dem 50. Perzentil für die Zeit, die es dauert, den Bericht zu öffnen. Anders ausgedrückt, beschreibt diese Metrik die Zeit, in der 50 % der Aktionen zum Öffnen des Berichts ausgeführt werden. Auf der Seite „Berichtsleistung“ wird die durchschnittliche Zeit zum Öffnen von Berichten nach Verwendungsmethode und Browserart aufgeführt.

**F:** Wie wird der „Öffnungszeittrend“ berechnet?

**A:** Der Öffnungszeittrend zeigt, wie sich die Leistung beim Öffnen von Berichten mit der Zeit ändert. Dabei werden die Öffnungszeiten für den Bericht aus der ersten Hälfte des ausgewählten Zeitraums mit den Zeiten aus der zweiten Hälfte verglichen. Sie können den Zeitraum mithilfe des Datenschnitts nach Datum auf der Seite „Berichtsleistung“ ändern, um Trends beispielsweise Woche für Woche oder nach zwei Wochen zu berechnen.

**F:**  In der alten Version des Berichts zu Nutzungsmetriken gibt es vier Berichte, aber die neue Version zeigt nur drei an.

**A:**  Der verbesserte Bericht zu Nutzungsmetriken enthält nur Berichte, die in den letzten 30 Tagen geöffnet wurden, während die alte Version 90 Tage abdeckt. Wenn ein Bericht nicht im verbesserten Bericht zu Nutzungsmetriken enthalten ist, wurde dieser vermutlich nicht in den letzten 30 Tagen verwendet.

## <a name="troubleshoot-delete-the-dataset"></a>Problembehandlung: Dataset löschen

Wenn Sie Probleme bei der Datenkonsistenz oder der Aktualisierung vermuten, könnte es sinnvoll sein, das vorhandene Dataset für den Bericht zu Nutzungsmetriken zu löschen. Anschließend können Sie „Nutzungsmetriken anzeigen“ noch mal ausführen, um ein neues Dataset mit den zugehörigen verbesserten Berichten zu Nutzungsmetriken zu generieren. Führen Sie die folgenden Schritte aus.

### <a name="delete-the-dataset"></a>Dataset löschen

1. Öffnen Sie den Arbeitsbereich, der den Bericht enthält, dessen Dataset für den Bericht zu Nutzungsmetriken Sie zurücksetzen möchten.

2. Klicken Sie in der schwarzen Kopfzeile oben auf das Symbol **Einstellungen**, und wählen Sie dann **Einstellungen** aus.

    ![„Einstellungen“ auswählen](media/service-modern-usage-metrics/power-bi-settings-settings.png)

3. Wechseln Sie zur Registerkarte **Datasets**, und wählen Sie das Dataset für den Bericht zu Nutzungsmetriken aus. 

    ![Dataset für Nutzungsmetriken](media/service-modern-usage-metrics/power-bi-settings-usage-report-dataset.png)

5. Kopieren Sie die IDs des Arbeitsbereichs und Datasets aus der URL, die in der Adressleiste Ihres Browsers angezeigt wird.

    ![URL des Datasets für Nutzungsmetriken](media/service-modern-usage-metrics/power-bi-usage-metrics-url.png)

1. Rufen Sie [https://docs.microsoft.com/rest/api/power-bi/datasets/deletedatasetingroup](https://docs.microsoft.com/rest/api/power-bi/datasets/deletedatasetingroup) in Ihrem Browser auf, und klicken Sie auf **Jetzt testen**.

    ![DELETE-Befehl für das Dataset testen](media/service-modern-usage-metrics/power-bi-delete-dataset-try-it.png)

1. Melden Sie sich bei Power BI an, fügen Sie die Arbeitsbereichs-ID in das Textfeld **groupId** und die Dataset-ID in das Textfeld **datasetId** ein, und klicken Sie dann auf **Ausführen**. 

    ![REST-API testen](media/service-modern-usage-metrics/power-bi-rest-api-try-it.png)

1. Überprüfen Sie, ob der Dienst unter der Schaltfläche **Ausführen** den Antwortcode **200** zurückgibt. Dieser Code gibt an, dass das Dataset und die zugehörigen Berichte zu Nutzungsmetriken erfolgreich gelöscht wurden.

    ![Antwortcode 200](media/service-modern-usage-metrics/power-bi-response-code-200.png)

### <a name="create-a-fresh-usage-metrics-report"></a>Erstellen eines neuen Berichts zu Nutzungsmetriken

1. Im Power BI-Dienst wird das Dataset nun nicht mehr angezeigt.

    ![Kein Bericht zu Nutzungsmetriken vorhanden](media/service-modern-usage-metrics/power-bi-no-usage-metrics-dataset.png)

2. Wenn der Bericht zu Nutzungsmetriken immer noch in der Berichtsliste angezeigt wird, aktualisieren Sie die Seite.

3. [Erstellen Sie einen neuen Bericht zu Nutzungsmetriken](#create--view-an-improved-usage-metrics-report).

## <a name="next-steps"></a>Nächste Schritte

[Verwalten von Power BI im Verwaltungsportal](service-admin-portal.md)

Weitere Fragen? [Wenden Sie sich an die Power BI-Community](https://community.powerbi.com/)
