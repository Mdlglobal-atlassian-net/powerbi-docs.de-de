---
title: Berichte im Power BI-Dienst
description: Berichte im Power BI-Dienst (für Kunden)
author: mihart
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-consumer
ms.topic: conceptual
ms.date: 09/05/2019
ms.author: mihart
LocalizationGroup: Reports
ms.openlocfilehash: 3f6f534b71ba6d8e8798418275c4758a95fc6fb5
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/09/2019
ms.locfileid: "73851226"
---
# <a name="reports-in-power-bi"></a>Berichte in Power BI

[!INCLUDE [power-bi-service-new-look-include](../includes/power-bi-service-new-look-include.md)]

Ein Power BI-Bericht stellt eine Ansicht eines Datasets aus verschiedenen Perspektiven dar, wobei die aus dem Dataset gewonnenen verschiedenen Ergebnisse und Erkenntnisse als Visuals angezeigt werden.  Ein Bericht kann ein einzelnes Visual, aber auch mehrere mit Visuals gefüllte Seiten enthalten. Abhängig von Ihrem Aufgabengebiet sind Sie möglicherweise jemand, der Berichte *entwirft*. Sie können auch jemand sein, der Berichte *nutzt* oder verwendet. Dieser Artikel richtet sich an *Consumer*.

![Screenshot: Berichtsseite](./media/end-user-reports/power-bi-report.png)

A. Dieser Bericht umfasst sechs Seiten (bzw. Registerkarten). Sie sehen hier die Seite **Stimmung**.    
B. Diese Seite enthält fünf verschiedene Visuals und einen Seitentitel.    
C. Im Bereich *Filter* wird ein Filter angezeigt, der auf alle Berichtseiten angewendet wird. Klicken Sie auf den Pfeil ( **>** ), um den Filterbereich zu reduzieren.    
D. Das Power BI-Banner zeigt den Namen des Berichts und das Datum der letzten Aktualisierung an. Wählen Sie den Pfeil aus, um ein Menü zu öffnen, in dem auch der Name des Berichtsbesitzers angezeigt wird.    
E. Die Aktionsleiste enthält Aktionen, die Sie für diesen Bericht ausführen können.  Beispielsweise können Sie einen Kommentar hinzufügen, ein Lesezeichen anzeigen oder Daten aus dem Bericht exportieren.  Wählen Sie **Weitere Optionen** (...) aus, um eine Liste der zusätzlichen Berichtsfunktionen anzuzeigen.    

Wenn Sie noch nicht mit Power BI vertraut sind, können Sie sich mithilfe des Artikels [Basic concepts for the Power BI service consumers (Grundkonzepte für Benutzer des Power BI-Diensts)](end-user-basic-concepts.md) eine gute Grundlage schaffen. Berichte können auf mobilen Geräten angezeigt, freigegeben und kommentiert werden. Weitere Informationen finden Sie unter [Explore reports in the Power BI mobile apps (Untersuchen von Berichten in mobilen Power BI-Apps)](mobile/mobile-reports-in-the-mobile-apps.md).

## <a name="advantages-of-reports"></a>Vorteile von Berichten

Bei Power BI basiert ein Bericht auf einem einzelnen Dataset. *Berichts-Designer* erstellen die Visuals in einem Bericht, die wertvolle Informationen darstellen. Diese Visuals sind nicht statisch.  Sie werden aktualisiert, wenn sich die zugrunde liegenden Daten ändern. Sie können mit den Visuals und Filtern interagieren, während Sie die Daten durchsuchen, um sich Erkenntnisse und Antworten zu beschaffen. Ähnlich wie Dashboards bieten auch Berichte zahlreiche Möglichkeiten für die Interaktion und Anpassung.

### <a name="safely-interact-with-content"></a>Sicheres Interagieren mit Inhalten

Während Sie mit den Inhalten interagieren und sie durchsuchen, indem Sie sie filtern, segmentieren, abonnieren und exportieren, können Sie die Berichte nicht beschädigt werden. Ihre Aktionen wirken sich nicht auf das zugrundeliegende Dataset oder die ursprünglichen freigegebenen Inhalte aus. Dies gilt für Dashboards, Berichte und Apps.

> [!NOTE]
> Beachten Sie, dass Sie Ihre Daten nicht beeinträchtigen können. Power BI ist ein hervorragendes Tool zum Untersuchen und Experimentieren, ohne dass Sie sich sorgen müssen, dass Sie etwas kaputt machen.

### <a name="save-your-changes-or-revert-to-the-default-settings"></a>Speichern Ihrer Änderungen oder Wiederherstellen der Standardeinstellungen

Das bedeutet nicht, dass Sie Ihre Änderungen nicht speichern können. Das können Sie, jedoch wirken sich die gespeicherten Änderungen nur auf Ihre Ansicht des Inhalts aus. Klicken Sie auf **Auf Standardwert zurücksetzen**, um die ursprüngliche Standardansicht wiederherzustellen.

![Screenshot des Symbols „Auf Standardwert zurücksetzen“.](./media/end-user-reports/power-bi-reset.png)

## <a name="dashboards-versus-reports"></a>Vergleich: Dashboards und Berichte

[Dashboards](end-user-dashboards.md) werden oft mit Berichten verwechselt, weil es sich bei einem Dashboard ebenfalls um eine Canvas handelt, die Visuals enthält. Es gibt aber einige wichtige Unterschiede.  

| **Eigenschaften** | **Dashboards** | **Berichte** |
| --- | --- | --- |
| Seiten |Eine Seite |Eine oder mehrere Seiten |
| Datenquellen |Ein oder mehrere Berichte und ein oder mehrere Datasets pro Dashboard |Ein Dataset pro Bericht |
| Filterung |Keine Filter, keine Slices |Viele Filter, Hervorhebungen und Slices |
| Benachrichtigungen festlegen |Kann Ihnen Benachrichtigungen per E-Mail senden, wenn das Dashboard bestimmte Bedingungen erfüllt |Nein |
| Feature |Kann ein Dashboard als Favorit festlegen |Ein ausgewählter Bericht kann nicht erstellt werden. |
| Zugrunde liegende Dataset-Tabellen und Felder sichtbar |Nein. Kann Daten exportieren, aber keine Dataset-Tabellen und Felder im Dashboard selbst einsehen |Ja. Kann Dataset-Tabellen, Felder und Werte einsehen, für die Sie über die Berechtigungen verfügen |
| Anpassung |Nein  |Kann filtern, exportieren, verwandte Inhalte anzeigen, Lesezeichen hinzufügen, QR-Codes generieren, in Excel analysieren und mehr |

<!--| Available in Power BI Desktop |No |Yes, can create and view reports in Desktop |
| Pinning |Can pin existing visuals (tiles) only from current dashboard to your other dashboards |Can pin visuals (as tiles) to any of your dashboards. Can pin entire report pages to any of your dashboards. | -->

## <a name="report-designers-and-report-consumers"></a>Berichts-Designer und Berichtsnutzer

Abhängig von Ihrem Aufgabengebiet sind Sie möglicherweise ein *Designer*, der Berichte für die eigene Benutzung oder für Kollegen erstellt. Dann sollten Sie wissen, wie Berichte erstellt und freigegeben werden.

Oder Sie sind ein *Berichtsnutzer*, der Berichte von anderen erhält. Dann sollten Sie wissen, wie Sie mit Berichten interagieren können, und sie verstehen. Wenn Sie *Berichtsnutzer* sind, sollten Sie den folgenden Links folgen:

* Beginnen Sie mit einer [Tour des Power BI-Diensts](end-user-basic-concepts.md), um zu erfahren, wo Sie Berichte und Berichtstools finden.
* Erfahren Sie, wie Sie [einen Bericht öffnen](end-user-report-open.md), und lernen Sie alle [für Consumer verfügbaren Interaktionen](end-user-reading-view.md) kennen.
* Machen Sie sich mit Berichten vertraut, indem Sie sich eine Tour durch eines unserer [Beispiele](../sample-tutorial-connect-to-the-samples.md) ansehen.  
* Informationen dazu, welches Dataset ein Bericht verwendet und welche Dashboards Visuals aus dem Bericht anzeigen (*Pins*), finden Sie unter [Anzeigen verwandter Inhalte im Power BI-Dienst](end-user-related.md).

> [!TIP]
> Wenn Sie die gesuchten Informationen hier nicht finden, verwenden Sie das Inhaltsverzeichnis auf der linken Seite, um alle Artikel zu *Berichten* zu durchsuchen.

## <a name="next-steps"></a>Nächste Schritte

[Öffnen und Anzeigen eines Berichts](end-user-report-open.md)    
[Dashboards im Power BI-Dienst](end-user-dashboards.md)