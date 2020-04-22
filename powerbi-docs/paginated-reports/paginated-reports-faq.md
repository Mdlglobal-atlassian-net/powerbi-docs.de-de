---
title: 'Paginierte Berichte in Power BI: Häufig gestellte Fragen'
description: Dieser Artikel behandelt häufig gestellte Fragen zu paginierten Berichten. Diese Berichte sind umfassend formatiert und pixelgenau, somit eignet sich ihre Ausgabe ideal zum Drucken und Erstellen von PDFs.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.date: 04/21/2020
ms.openlocfilehash: dcf154105b8940bd400fbb4e630a1d1cfd00ddf0
ms.sourcegitcommit: 8775168ed916c517c57c696ebe45699e638b86e8
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "81766292"
---
# <a name="paginated-reports-in-power-bi-faq"></a>Paginierte Berichte in Power BI: Häufig gestellte Fragen 

Dieser Artikel behandelt häufig gestellte Fragen zu paginierten Berichten. Diese Berichte sind umfassend formatiert und pixelgenau, somit eignet sich ihre Ausgabe ideal zum Drucken und Erstellen von PDFs. Sie werden als „paginiert“ bezeichnet, weil sie so formatiert sind, dass sie gut auf mehrere Seiten passen. Paginierte Berichte basieren auf der RDL-Berichtstechnologie von SQL Server Reporting Services (SSRS). 

In diesem Artikel werden viele häufig gestellte Fragen zu paginierten Berichten in Power BI Premium und zum Berichts-Generator beantwortet, dem eigenständigen Tool zum Erstellen von paginierten Berichten. Sie benötigen eine Power BI Pro-Lizenz, um einen Bericht im Dienst zu veröffentlichen. Sie können paginierte Berichte unter „Mein Arbeitsbereich“ oder in anderen Arbeitsbereichen veröffentlichen und freigeben, solange sich der Arbeitsbereich in einer Power BI Premium-Kapazität befindet. 

## <a name="administration"></a>Verwaltung

### <a name="what-size-premium-capacity-do-i-need-for-paginated-reports"></a>Welche Premium-Kapazitätsgröße benötige ich für paginierte Berichte?

Die Workload der paginierten Berichte ist für die SKUs P1–P3 verfügbar.  Sie können sie auch mit den SKUs A4–A6 für Einbettungs- oder Entwicklungs-/Testszenarien verwenden.

### <a name="what-is-the-maximum-memory-threshold-i-can-put-for-paginated-reports-in-my-capacity"></a>Was ist der Maximalwert für den Arbeitsspeicher, den ich in meiner Kapazität für paginierte Berichte festlegen kann?

Sie können bis zu 100 % des Arbeitsspeichers für diese Workload verwenden.

### <a name="how-does-user-access-work-for-paginated-reports"></a>Wie funktioniert der Benutzerzugriff auf paginierte Berichte?

Der Benutzerzugriff auf paginierte Berichte entspricht dem Benutzerzugriff auf alle anderen Inhalte im Power BI-Dienst. 

### <a name="how-do-i-turn-onoff-my-paginated-reports-workload"></a>Wie aktiviere/deaktiviere ich die Workload paginierter Berichte?

Der Kapazitätsadministrator kann die Workload paginierter Berichte im Portal für Kapazitätsadministratoren aktivieren bzw. deaktivieren.  Standardmäßig ist die Workload für alle von Ihnen erstellten neuen Kapazitäten aktiviert, verbraucht aber erst dann Arbeitsspeicher, wenn Sie Ihren ersten paginierten Bericht hochladen.  

### <a name="how-can-i-monitor-usage-of-paginated-reports-in-my-tenant"></a>Wie kann ich die Verwendung von paginierten Berichten in meinem Mandanten überwachen?

Die Office 365-Überwachungsprotokolle vermerken die detaillierte Verwendung dieses Berichtstyps bei folgenden Ereignissen: 

- Anzeigen des Power BI-Berichts
- Löschen des Power BI-Berichts
- Erstellen des Power BI-Berichts
- Downloaded Power BI report (Power BI-Bericht herunterladen)

Das Feld „ReportType“ hat den Wert „PaginatedReport“, um paginierte Berichte von Power BI-Berichten zu unterscheiden.

Darüber hinaus stellen Überwachungsprotokolle die folgenden Ereignisse für paginierte Berichte zur Verfügung:

- Binden von Power BI-Datasets an Gateways
- Untersuchen von Power BI-Datenquellen
- TakeOverDataset

### <a name="can-i-monitor-this-workload-through-the-premium-capacity-monitoring-app"></a>Kann ich diese Workload in der App zum Überwachen der Premium-Kapazität überwachen?

Ja, Überwachung ist als neue Registerkarte mit den gleichen relevanten Details wie für Ihre Power BI-Datasets verfügbar.

### <a name="do-i-need-a-pro-license-to-create-and-publish-paginated-reports"></a>Benötige ich eine Pro-Lizenz, um paginierte Berichte zu erstellen und zu veröffentlichen?

Sie können paginierte Berichte ohne Pro-Lizenz in „Mein Arbeitsbereich“ hochladen, sofern er sich in einer Premium-Kapazität befindet.  Für andere Arbeitsbereiche benötigen Sie eine Pro-Lizenz, um dort Inhalte zu erstellen und zu veröffentlichen. Wir empfehlen Ihnen, Power BI Report Builder auch ohne Pro-Lizenz herunterzuladen und zu verwenden, aber Sie können die von Ihnen erstellten paginierten Berichte nicht ohne Lizenz veröffentlichen. 

### <a name="what-if-i-have-a-paginated-report-in-a-workspace-and-the-paginated-report-workload-is-turned-off"></a>Was geschieht, wenn sich ein paginierter Bericht in einem Arbeitsbereich befindet und die Workload des paginierten Berichts deaktiviert ist?

Sie erhalten eine Fehlermeldung und können Ihren Bericht erst wieder anzeigen, wenn die Workload wieder aktiviert ist. Sie können den Bericht nach wie vor aus dem Arbeitsbereich löschen.

### <a name="what-is-the-default-memory-for-each-of-the-premium-skus-that-support-paginated-reports"></a>Wie lautet der Standardarbeitsspeicher für die jeweilige Premium-SKU, die paginierte Berichte unterstützen?

Der Standardarbeitsspeicher der jeweiligen Premium-SKU für paginierte Berichte lautet:

- **P1/A4**: 20 % Standard, mindestens 10 %
- **P2/A5**: 20 % Standard, mindestens 5 %
- **P3/A6**: 20 % Standard, mindestens 2,5 %

Power BI-Mandantenadministratoren können den standardmäßigen maximalen Arbeitsspeicherprozentsatz im Verwaltungsportal bearbeiten. Weitere Informationen finden Sie im Abschnitt zu Workloads **Paginierte Berichte** unter **Power BI Premium** auf der Registerkarte **Kapazitätseinstellungen**.

:::image type="content" source="media/paginated-reports-faq/paginated-reports-capacity-settings.png" alt-text="Registerkarte mit Kapazitätseinstellungen zu paginierten Berichten":::

## <a name="general"></a>Allgemein

### <a name="when-should-i-use-a-paginated-report-vs-a-power-bi-report"></a>Wofür sollte ich einen paginierten und wofür einen Power BI-Bericht verwenden?

Paginierte Berichte sind die ideal Wahl, wenn Sie eine umfassend formatierte und pixelgenaue Ausgabe für den Druck oder die PDF-Erstellung benötigen.  Ein gutes Beispiel dafür ist eine Gewinn- und Verlustrechnung.  

Power BI-Berichte sind ideal zum Untersuchen und Interagieren.  Ein gutes Beispiel für einen Power BI-Bericht ist beispielsweise ein Vertriebsbericht. Hier können mehrere Vertriebsmitarbeiter die Daten im selben Bericht nach bestimmten Regionen/Branchen/Kunden aufteilen und dann sehen, wie sich die Zahlen verändern.

Weitere Informationen finden Sie unter [Wann sollten paginierte Berichte in Power BI verwendet werden?](../guidance/report-paginated-or-power-bi.md).

### <a name="the-documentation-says-power-bi-report-builder-is-the-preferred-authoring-tool-can-i-create-paginated-reports-in-sql-server-data-tools-for-power-bi"></a>Laut Dokumentation ist der Power BI-Berichts-Generator das bevorzugte Erstellungstool. Kann ich paginierte Berichte auch mit SQL Server Data Tools für Power BI erstellen?

Ja, doch Power BI ermöglicht das Hochladen von jeweils nur einem einzelnen Element, sodass viele Szenarios, für die Ersteller SQL Server Data Tools (SSDT) verwenden, noch nicht unterstützt werden. Weiter unten finden Sie die vollständige [Liste der nicht unterstützten Funktionen](#what-paginated-report-features-in-ssrs-arent-yet-supported-in-power-bi).  

### <a name="what-versions-of-report-builder-do-you-support"></a>Welche Versionen des Berichts-Generators werden unterstützt?

Wir haben den Power BI Report Builder als primäres Tool für die Erstellung paginierter Berichte im Power BI-Dienst veröffentlicht. Installieren Sie den [Power BI-Berichts-Generator aus dem Microsoft Download Center](https://go.microsoft.com/fwlink/?linkid=2086513).

### <a name="how-do-i-move-existing-reports-i-have-saved-in-sql-server-reporting-services-to-power-bi"></a>Wie verschiebe ich vorhandene Berichte, die ich in SQL Server Reporting Services gespeichert habe, zu Power BI?

Ein Projekt auf GitHub unterstützt jetzt das Migrieren von Inhalt von SQL Server Reporting Services zu Power BI.  Details anzeigen und das Tool hier herunterladen: [https://github.com/microsoft/RdlMigration](https://github.com/microsoft/RdlMigration)

### <a name="can-i-open-reports-and-publish-directly-to-the-service"></a>Kann ich Berichte öffnen und direkt im Dienst veröffentlichen?

Ja. Wir haben Unterstützung für das Öffnen von Berichten und deren direkte Veröffentlichung im Dienst vom Power BI Report Builder aus hinzugefügt.

### <a name="what-paginated-report-features-in-ssrs-arent-yet-supported-in-power-bi"></a>Welche Funktionen von paginierten Berichten in SSRS werden in Power BI noch nicht unterstützt?

Paginierte Berichte unterstützen derzeit nicht die folgenden Elemente:

- Freigegebene Datenquellen
- Freigegebene Datasets
- Drillthrough und Durchklicken zu anderen Berichten
- Verknüpfte Berichte
- Benutzerdefinierte Schriftarten

Sie erhalten eine Fehlermeldung, wenn Sie versuchen, eine Datei hochzuladen, die über eine nicht unterstützte Funktion im Power BI-Dienst verfügt – mit Ausnahme von Umschalten/Sortieren.

### <a name="what-data-sources-do-you-support-currently-for-paginated-reports"></a>Welche Datenquellen werden derzeit für paginierte Berichte unterstützt?

Eine Liste der Datenquellen finden Sie im Artikel [Unterstützte Datenquellen für paginierte Power BI-Berichte](paginated-reports-data-sources.md). 

### <a name="what-authentication-methods-do-you-support"></a>Welche Authentifizierungsmethoden werden unterstützt?

Wir unterstützen SSO für Azure Analysis Services, Azure SQL-Datenbank und Power BI-Datenquellen.  Darüber hinaus wird OAuth für Azure SQL-Datenbank und Azure Analysis Services unterstützt.  Für andere Datenquellen müssen Sie derzeit einen Benutzernamen und ein Kennwort mit der Datenquelle im Portal oder Gateway speichern.  

### <a name="can-i-use-a-power-bi-dataset-as-a-data-source-for-my-paginated-report"></a>Kann ich ein Power BI-Dataset als Datenquelle für meinen paginierten Bericht verwenden?

Ja, wir unterstützen Power BI-Datasets als Datenquellen für Ihre paginierten Berichte.

### <a name="can-i-use-stored-procedures-through-the-gateway"></a>Kann ich gespeicherte Prozeduren über das Gateway verwenden?

Ja, gespeicherte Prozeduren über das Gateway werden für SQL Server-Datenquellen unterstützt, einschließlich solcher, die Parameter verwenden.

### <a name="what-export-formats-are-available-for-my-report-in-the-power-bi-service"></a>Welche Exportformate sind für meinen Bericht in Power BI verfügbar?

Sie können in Microsoft Excel, Microsoft Word, Microsoft PowerPoint sowie in die Formate PDF, CSV, XML und MHTML exportieren.

### <a name="can-i-print-paginated-reports"></a>Kann ich paginierte Berichte drucken?

Ja, Drucken steht für paginierte Berichte zur Verfügung, einschließlich einer neuen, verbesserten Seitenansichts-Benutzeroberfläche. 

### <a name="are-e-mail-subscriptions-available-for-paginated-reports"></a>Sind E-Mail-Abonnements für paginierte Berichte verfügbar?

Ja, E-Mail-Abonnements werden für paginierte Berichte vollständig unterstützt, und dies beinhaltet Unterstützung für sechs verschiedene Dateiformate und Parameterwerte.

### <a name="can-i-run-custom-code-in-my-report"></a>Kann ich in meinem Bericht benutzerdefinierten Code ausführen?

Ja, das Ausführen von Code in Berichten wird – wie in SSRS – unterstützt.

### <a name="can-i-use-power-bi-embedded-to-embed-my-paginated-reports-into-an-app-im-hosting"></a>Kann ich mit Power BI Embedded meine paginierten Berichte in eine App einbetten, die ich hoste?

Das Einbetten von SaaS, einschließlich der Unterstützung für sicheres Einbetten, ist bereits verfügbar. Informationen zur PaaS-Einbettung finden Sie im Tutorial [Einbetten paginierter Power BI-Berichte in eine Anwendung für Kunden](../developer/embed-paginated-reports-customers.md).

### <a name="can-i-drill-through-from-a-power-bi-report-to-a-paginated-report"></a>Kann ich einen Drillthrough von einem Power BI-Bericht zu einem paginierten Bericht ausführen?

Ja, dies kann erreicht werden, indem Sie URL-Parameter für Ihre paginierten Berichte benutzen.

### <a name="can-i-share-my-paginated-report-content-through-a-power-bi-app"></a>Kann ich Inhalte meines paginierten Berichts mit einer Power BI-App freigeben?

Ja, die Bereitstellung paginierter Berichte mit Apps aus den Arbeitsbereichen v1 und v2 wird unterstützt. 

### <a name="will-other-report-specific-features-in-power-bi-like-pinning-to-report-tiles-to-dashboards-work-with-paginated-reports"></a>Werden andere berichtsspezifische Funktionen in Power BI, z.B. das Anheften von Berichtskacheln an Dashboards, mit paginierten Berichten funktionieren?

Es ist geplant, dass Berichte so weit wie möglich die gleichen wichtigen Funktionen im Dienst unterstützen.  Obwohl das Erstellungstool sich unterscheidet, ist das Ziel, dass Endbenutzer diesen Bericht einfach als einen weiteren Bericht in ihrer Liste im Portal betrachten. Denn es geht nicht darum, wie der Bericht erstellt wurde, sondern darum, dass die Anforderungen der Benutzer erfüllt werden.  Ein gutes Beispiel für diese Featureparität ist die geplante Kommentarunterstützung. Obwohl sich die Funktionsweise des Features in den Berichten ggf. etwas unterscheidet, können Sie Kommentare in beiden verwenden.

### <a name="is-there-a-report-viewer-control-for-paginated-reports-in-the-power-bi-service"></a>Gibt es in Power BI ein Berichtanzeige-Steuerelement für paginierte Berichte?

Nein, derzeit ist kein Berichtanzeige-Steuerelement verfügbar.

### <a name="can-you-search-for-paginated-reports-from-the-new-home-experience-in-the-power-bi-service"></a>Kann ich auf der neuen Power BI-Startseite nach paginierten Berichten suchen?

Ja, Sie können jetzt auf der Startseite nach Ihren paginierten Berichten suchen.  Sie werden auch in anderen Bereichen der neuen Startseite angezeigt.

## <a name="next-steps"></a>Nächste Schritte

- [Installieren des Power BI-Berichts-Generators aus dem Microsoft Download Center](https://go.microsoft.com/fwlink/?linkid=2086513)
- [Tutorial: Erstellen eines paginierten Berichts](paginated-reports-quickstart-aw.md)
