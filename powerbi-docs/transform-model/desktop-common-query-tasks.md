---
title: Durchführen allgemeiner Abfrageaufgaben in Power BI Desktop
description: Durchführen allgemeiner Abfrageaufgaben in Power BI Desktop
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 01/09/2020
ms.author: davidi
LocalizationGroup: Transform and shape data
ms.openlocfilehash: a9386620bf5fad436b81156870dbc38d919c7910
ms.sourcegitcommit: bfc2baf862aade6873501566f13c744efdd146f3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/13/2020
ms.locfileid: "83348733"
---
# <a name="perform-common-query-tasks-in-power-bi-desktop"></a>Durchführen allgemeiner Abfrageaufgaben in Power BI Desktop

Im Fenster „Power Query-Editor“ von Power BI Desktop stehen verschiedene häufig verwendete Aufgaben zur Auswahl bereit. Im vorliegenden Artikel werden diese gängigen Aufgaben vorgestellt. Zudem finden Sie Links zu weiteren Informationen.

Zu den vorgestellten allgemeinen Abfrageaufgaben zählen folgende:

* Verbinden mit Daten
* Strukturieren und Kombinieren von Daten
* Gruppieren von Zeilen
* Pivot-Spalten
* Erstellen benutzerdefinierter Spalten
* Abfrageformeln

Zum Ausführen dieser Aufgaben verwenden wir einige Datenverbindungen. Diese Daten sind für Sie zum Download verfügbar. Wenn Sie die Schritte selbst ausführen möchten, können Sie auch eine Verbindung zu diesen Daten herstellen.

Die erste Datenquelle ist eine [Excel-Arbeitsmappe](https://download.microsoft.com/download/5/7/0/5701F78F-C3C2-450C-BCCE-AAB60C31051D/PBI_Edu_ELSi_Enrollment_v2.xlsx), die Sie herunterladen und lokal speichern können. Die zweite Datenquelle ist eine Webressource, die auch in weiteren Artikeln zu Power BI Desktop verwendet wird:

<https://www.bankrate.com/retirement/best-and-worst-states-for-retirement/>

Die allgemeinen Abfrageaufgaben beginnen mit den Schritten, die zum Verbinden mit diesen beiden Datenquellen erforderlich sind.

## <a name="connect-to-data"></a>Verbinden mit Daten

Um eine Verbindung mit Daten in Power BI Desktop herzustellen, wählen Sie **Start** und anschließend **Daten abrufen** aus. Power BI Desktop zeigt ein Menü mit den am häufigsten verwendeten Datenquellen an. Um eine vollständige Liste der Datenquellen anzuzeigen, mit denen Power BI Desktop eine Verbindung herstellen kann, klicken Sie unten im Menü auf **Mehr**. Weitere Informationen finden Sie unter [Datenquellen in Power BI Desktop](../connect-data/desktop-data-sources.md).

![Menü der am häufigsten verwendeten Datenquellen, Schaltfläche „Daten abrufen“, Power BI Desktop](media/desktop-common-query-tasks/commonquerytasks_getdata.png)

Um zu starten, wählen Sie **Excel** aus, geben Sie die zuvor erwähnte Excel-Arbeitsmappe an, und klicken Sie dann auf **Öffnen**. Die Abfrage prüft die Arbeitsmappe und zeigt dann die gefundenen Daten im Dialogfeld **Navigator** an, nachdem Sie eine Tabelle ausgewählt haben.

![Excel-Datenquelle, Dialogfeld „Navigator“, Option „Daten abrufen“, Power BI Desktop](media/desktop-common-query-tasks/commonquerytasks_navigator.png)

Sie können **Daten transformieren** auswählen, um die Abfrage anzupassen, oder die Daten *modellieren*, bevor Sie sie in Power BI Desktop laden. Die Bearbeitung ist besonders nützlich, wenn Sie mit großen Datensätzen arbeiten, die Sie vor dem Laden verkleinern möchten.

Die Verbindungsherstellung mit anderen Datentypen ist genauso einfach. Wir möchten auch eine Verbindung mit einer Webressource herstellen. Klicken Sie auf **Daten abrufen** > **Mehr**, und wählen Sie dann **Andere** > **Web** > **Verbinden** aus.

![Datenquelle „Web“, Dialogfeld „Daten abrufen“, Power BI Desktop](media/desktop-common-query-tasks/commonquerytasks_getdata_other.png)

Das Fenster **Aus dem Web** wird geöffnet, in dem Sie die URL der Webseite eingeben können.

![Dialogfeld „Aus dem Web“, Datenquelle „Web“, Dialogfeld „Daten abrufen“, Power BI Desktop](media/desktop-common-query-tasks/datasources_fromwebbox.png)

Wählen Sie **OK** aus. Wie zuvor überprüft Power BI Desktop die Daten der Webseite und zeigt im Dialogfeld **Navigator** Vorschauoptionen an. Wenn Sie eine Tabelle auswählen, wird eine Vorschau der Daten angezeigt.

Andere Datenverbindungen funktionieren ähnlich. Falls für eine Datenverbindung eine Authentifizierung erforderlich ist, fordert die Power BI Query Sie auf, die entsprechenden Abmeldeinformationen einzugeben.

Das Verbinden mit Daten in Power BI Desktop wird unter [Verbinden mit Daten in Power BI Desktop](../connect-data/desktop-connect-to-data.md) Schritt für Schritt erläutert.

## <a name="shape-and-combine-data"></a>Strukturieren und Kombinieren von Daten

Mit dem Power Query-Editor können Sie ganz einfach Daten strukturieren und kombinieren. Dieser Abschnitt enthält einige Beispiele zum Strukturieren von Daten. Eine ausführliche Erläuterung zum Strukturieren und Kombinieren von Daten finden Sie unter [Strukturieren und Kombinieren von Daten mit Power BI Desktop](../connect-data/desktop-shape-and-combine-data.md).

Im vorherigen Abschnitt haben wir Verbindungen mit zwei Datasets hergestellt: mit einer Excel-Arbeitsmappe und einer Webressource. Nachdem die Daten im Power Query-Editor geladen wurden, wählen Sie die Abfrage der Webseite aus den verfügbaren Abfragen im Bereich **Abfragen** aus, wie hier gezeigt:

![Bereich „Abfragen“, Power Query-Editor, Power BI Desktop](media/desktop-common-query-tasks/commonquerytasks_querypaneloaded.png)

Beim Strukturieren von Daten wird eine Datenquelle in die Struktur und das Format transformiert, die bzw. das Ihren Anforderungen entspricht.

Im Power Query-Editor sind im Menüband und in den Kontextmenüs (Rechtsklick) zahlreiche Befehle verfügbar. Wenn Sie beispielsweise mit der rechten Maustaste auf eine Spalte klicken, wird ein Kontextmenü geöffnet, über das Sie die Spalte löschen können. Sie könnten aber auch zuerst eine Spalte auswählen und dann im Menüband auf der Registerkarte **Start** auf die Schaltfläche **Spalten entfernen** klicken.

![Befehl „Spalten entfernen“, Power Query-Editor, Power BI Desktop](media/desktop-common-query-tasks/commonquerytasks_removecolumns.png)

Sie können die Daten in dieser Abfrage auf vielfältige Weise anpassen. Sie können im oberen oder unteren Bereich eine beliebige Anzahl von Zeilen entfernen. Oder Sie fügen Spalten hinzu, teilen Spalten, ersetzen Werte und führen weitere Anpassungen durch. Mithilfe dieser Features können Sie den Power Query-Editor anweisen, die Daten gemäß Ihren Anforderungen zu modellieren.

## <a name="group-rows"></a>Gruppieren von Zeilen

Im Power Query-Editor können Sie Werte aus mehreren Zeilen in einem Einzelwert zusammenfassen bzw. gruppieren. Dies kann beispielsweise hilfreich sein, wenn Sie die Anzahl angebotener Produkte, die Gesamtumsätze oder die Anzahl von Schülern/Studenten zusammenfassen möchten.

In diesem Beispiel gruppieren Sie die Zeilen in einem Dataset mit den Anmeldungszahlen von Schülern/Studenten. Die Daten stammen aus der Excel-Arbeitsmappe. Diese wurden im Power Query-Editor angepasst, um nur die benötigten Spalten anzuzeigen. Außerdem wurde die Tabelle umbenannt, und es wurden einige weitere Transformationen durchgeführt.

Finden wir heraus, wie viele Bildungsträger in jedem Bundesstaat vorhanden sind. (Hierzu können Schulbezirke, weitere Bildungseinrichtungen wie z. B. regionale Dienstbezirke und andere gehören.) Wählen Sie die Spalte **Agency ID - NCES Assigned \[District\] Latest available year** und dann die Schaltfläche **Gruppieren nach** auf der Registerkarte **Transformieren** oder **Start** im Menüband aus. (**Gruppieren nach** ist auf beiden Registerkarten verfügbar.)

![Dialogfeld „Gruppieren nach“, Power Query-Editor, Power BI Desktop](media/desktop-common-query-tasks/commonquerytasks_groupby.png)

Das Dialogfeld **Gruppieren nach** wird geöffnet. Wenn im Power Query-Editor Zeilen gruppiert werden, wird eine neue Spalte erstellt, in die die Ergebnisse des Vorgangs **Gruppieren nach** eingefügt werden. Sie können den Vorgang **Gruppieren nach** auf folgende Weise anpassen:

1. Die nicht benannte Dropdownliste gibt die zu gruppierende Spalte an. Der Power Query-Editor legt diesen Wert standardmäßig auf die ausgewählte Spalte fest, aber Sie können stattdessen eine beliebige Spalte in der Tabelle auswählen.
2. **Name der neuen Spalte**: Der Power Query-Editor schlägt auf Basis des zum Gruppieren der Spalte ausgeführten Vorgangs einen Namen für die zu gruppierende Spalte vor. Sie können den Namen der neuen Spalte jedoch beliebig ändern.
3. **Operation:** Sie können den Vorgang auswählen, den der Power Query-Editor anwendet, z. B. **Summe**, **Median** oder **Eindeutige Zeilen zählen**. Der Standardwert lautet **Zeilen zählen**.
4. **Gruppierung hinzufügen** und **Aggregation hinzufügen**: Diese Schaltfläche sind nur verfügbar, wenn Sie die Option **Erweitert** auswählen. Sie können in einem einzigen Vorgang Gruppierungsoperationen (**Gruppieren nach**-Aktionen) für viele Spalten durchführen und mithilfe dieser Schaltflächen mehrere Aggregationen erstellen. Der Power Query-Editor erstellt basierend auf Ihrer Auswahl in diesem Dialogfeld eine neue Spalte, bei der Vorgänge auf mehrere Spalten angewendet werden.

Wählen Sie **Gruppierungen hinzufügen** oder **Aggregation hinzufügen** aus, um weitere Gruppierungen oder Aggregationen zu einem **Gruppieren nach**-Vorgang hinzuzufügen. Um eine Gruppierung oder eine Aggregation zu entfernen, klicken Sie auf die Auslassungszeichen ( **...** ) rechts neben der Zeile und dann auf **Löschen**. Führen Sie testweise den Vorgang **Gruppieren nach** mit den Standardwerten aus, um zu sehen, was passiert.

![Dialogfeld „Gruppieren nach“, Power Query-Editor, Power BI Desktop](media/desktop-common-query-tasks/commonquerytasks_groupbynumbered.png)

Bei Auswahl von **OK** führt die Abfrage den Vorgang **Gruppieren nach** aus und gibt die Ergebnisse zurück. Sehen Sie sich das an! In Ohio, Illinois, Texas und Kalifornien gibt es mehr als tausend Bildungsträger.

![Spalte „Anzahl“, Vorgang „Gruppieren nach“, Power Query-Editor, Power BI Desktop](media/desktop-common-query-tasks/commonquerytasks_groupedresult.png)

Und mit dem Power Query-Editor können Sie jederzeit den zuletzt durchgeführten Anpassungsvorgang entfernen. Klicken Sie hierzu im Bereich **Abfrageeinstellungen** unter **Angewendete Schritte** einfach auf das **X** neben dem zuletzt abgeschlossenen Schritt. Also los! Experimentieren Sie! Wenn Ihnen die Ergebnisse nicht gefallen, machen Sie den Schritt einfach rückgängig. Fahren Sie so fort, bis der Power Query-Editor Ihre Daten wie gewünscht strukturiert hat.

## <a name="pivot-columns"></a>Pivot-Spalten

Sie können Pivot-Spalten und eine Tabelle erstellen, die für jeden eindeutigen Wert in einer Spalte aggregierte Werte enthält. Um beispielsweise herauszufinden, wie viele verschiedene Produkte die einzelnen Produktkategorien enthalten, können Sie im Handumdrehen eine Tabelle für genau diesen Zweck erstellen.

Betrachten wir dazu ein Beispiel. Die folgende Tabelle **Products_by_Categories** wurde so strukturiert, dass nur eindeutige Produkte (nach Namen) und die zugehörige Produktkategorie angezeigt werden. Um eine neue Tabelle zu erstellen, die die Anzahl von Produkten in jeder Kategorie (anhand der Spalte **CategoryName**) zeigt, markieren Sie die Spalte und wählen dann **Transformieren** > **Spalte pivotieren** aus.

![Befehl „Spalte pivotieren“, Power Query-Editor, Power BI Desktop](media/desktop-common-query-tasks/pivotcolumns_pivotbutton.png)

Das Dialogfeld **Spalte pivotieren** wird geöffnet und zeigt an, welche Spaltenwerte zum Erstellen neuer Spalten verwendet werden (1). (Wenn nicht der gewünschte Spaltenname für **CategoryName** angezeigt wird, wählen Sie diesen aus der Dropdownliste aus.) Wenn Sie **Erweiterte Optionen** aufklappen (2), können Sie die Funktion auswählen, die auf die aggregierten Werte angewendet wird (3).

![Dialogfeld „Spalte pivotieren“, Power Query-Editor, Power BI Desktop](media/desktop-common-query-tasks/pivotcolumns_pivotdialog.png)

Bei Auswahl von **OK** zeigt die Abfrage die Tabelle gemäß den Anweisungen zur Transformation an, die im Dialogfeld **Spalte pivotieren** angegeben wurden.

![Ergebnis von „Spalte pivotieren“, Power Query-Editor, Power BI Desktop](media/desktop-common-query-tasks/pivotcolumns_pivotcomplete.png)

## <a name="create-custom-columns"></a>Erstellen benutzerdefinierter Spalten

Im Power Query-Editor können Sie benutzerdefinierte Formeln erstellen, die auf mehrere Spalten in Ihrer Tabelle angewendet werden. Anschließend können Sie die Ergebnisse solcher Formeln in einer neuen (benutzerdefinierten) Spalte platzieren. Der Power Query-Editor macht es Ihnen einfach, benutzerdefinierte Spalten zu erstellen.

Laden Sie die Daten aus der Excel-Arbeitsmappe in den Power Query-Editor. Wechseln Sie im Menüband zur Registerkarte **Spalte hinzufügen**, und wählen Sie dann **Benutzerdefinierte Spalte** aus.

![Befehl „Benutzerdefinierte Spalte hinzufügen“, Power Query-Editor, Power BI Desktop](media/desktop-common-query-tasks/commonquerytasks_customcolumn.png)

Das folgende Dialogfeld wird angezeigt. In diesem Beispiel erstellen wir eine benutzerdefinierte Spalte namens *Percent ELL*, die den Prozentsatz aller Schüler/Studenten berechnet, die als „English Language Learners (ELL)“ eingestuft werden (d. h. die englische Sprache erlernen).

![Dialogfeld „Benutzerdefinierte Spalte“, Power Query-Editor, Power BI Desktop](media/desktop-common-query-tasks/customcolumn_addcustomcolumndialog.png)

Wie bei jedem anderen angewendeten Schritt im Power Query-Editor können Sie den Schritt löschen, wenn die neue benutzerdefinierte Spalte nicht die gesuchten Daten liefert. Klicken Sie hierzu im Bereich **Abfrageeinstellungen** unter **Angewendete Schritte** einfach auf das **X** neben dem Schritt **Benutzerdefinierte Spalte hinzugefügt**.

![Angewendete Schritte, Bereich „Abfrageeinstellungen“, Power Query-Editor, Power BI Desktop](media/desktop-common-query-tasks/customcolumn_addedappliedstep.png)

## <a name="query-formulas"></a>Abfrageformeln

Sie können die Schritte bearbeiten, die vom Power Query-Editor generiert werden. Sie können außerdem benutzerdefinierte Formeln erstellen, mit denen Sie eine Verbindung mit Ihren Daten herstellen und diese präziser gestalten können. Jedes Mal, wenn der Power Query-Editor eine Aktion für die Daten ausführt, wird die mit der Aktion verbundene Formel in der Bearbeitungsleiste angezeigt. Zum Anzeigen der Bearbeitungsleiste aktivieren Sie im Menüband auf der Registerkarte **Ansicht** das Kontrollkästchen **Bearbeitungsleiste**.

![Option „Bearbeitungsleiste“, Power Query-Editor, Power BI Desktop](media/desktop-common-query-tasks/queryformulas_formulabar.png)

Der Power Query-Editor zeichnet alle angewendeten Abfrageschritte als Text auf, den Sie anzeigen oder ändern können. Sie können den Text für eine beliebige Abfrage über **Erweiterter Editor** anzeigen oder ändern. Wählen Sie einfach **Ansicht** und dann **Erweiterter Editor** aus.

![Befehl „Erweiterter Editor“, Power Query-Editor, Power BI Desktop](media/desktop-common-query-tasks/queryformulas_advancededitorbutton.png)

Hier sehen Sie den **Erweiterter Editor**, in dem die Abfrageschritte der Abfrage **USA\_StudentEnrollment** angezeigt werden. Diese Schritte werden in der Power Query-Formelsprache erstellt, die häufig auch nur *M* genannt wird. Weitere Informationen finden Sie unter [Informationen zu Power Query-Formeln](https://support.office.com/article/learn-about-power-query-formulas-6bc50988-022b-4799-a709-f8aafdee2b2f). Um die Sprachspezifikation selbst anzuzeigen, wechseln Sie zu [Power Query M-Sprachspezifikation](/powerquery-m/power-query-m-language-specification).

![Dialogfeld „Erweiterter Editor“, Power Query-Editor, Power BI Desktop](media/desktop-common-query-tasks/queryformulas_advancededitor.png)

Power BI Desktop stellt einen umfangreichen Satz Formelkategorien bereit. Weitere Informationen und eine vollständige Referenz aller Power Query-Editor-Formeln finden Sie in der [Power Query M-Funktionsreferenz](/powerquery-m/power-query-m-function-reference).

## <a name="next-steps"></a>Nächste Schritte

Mit Power BI Desktop können Sie vielfältige Aufgaben ausführen. Weitere Informationen zu den Funktionen und Möglichkeiten finden Sie in den folgenden Ressourcen:

* [Was ist Power BI Desktop?](../fundamentals/desktop-what-is-desktop.md)
* [Übersicht zu Abfragen mit Power BI Desktop](desktop-query-overview.md)
* [Datenquellen in Power BI Desktop](../connect-data/desktop-data-sources.md)
* [Verbinden mit Daten in Power BI Desktop](../connect-data/desktop-connect-to-data.md)
* [Strukturieren und Kombinieren von Daten mit Power BI Desktop](../connect-data/desktop-shape-and-combine-data.md)
