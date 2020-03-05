---
title: Migrieren von SQL Server Reporting Services-Berichten zu Power BI
description: Anleitung zur Unterstützung bei der Migration Ihrer SQL Server Reporting Services-Berichte (SSRS) zu Power BI.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 01/03/2020
ms.author: v-pemyer
ms.openlocfilehash: f8b7cc302cd4a26aa099f723f47865723dccb7c9
ms.sourcegitcommit: b59ec11a4a0a3d5be2e4d91548d637d31b3491f8
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2020
ms.locfileid: "78290634"
---
# <a name="migrate-sql-server-reporting-services-reports-to-power-bi"></a>Migrieren von SQL Server Reporting Services-Berichten zu Power BI

Dieser Artikel richtet sich an SQL Server Reporting Services-Berichtsautoren (SSRS) und Power BI-Administratoren. Er bietet Ihnen eine Anleitung zur Migration Ihrer [RDL](/sql/reporting-services/reports/report-definition-language-ssrs)-Berichte (Report Definition Language) zu Power BI.

> [!NOTE]
> Es ist nur möglich, RDL-Berichte zu migrieren. In Power BI werden RDL-Berichte als _paginierte Berichte_ bezeichnet.

Die Anleitung ist in vier Phasen unterteilt. Es wird empfohlen, vor der Migration Ihrer Berichte zunächst den gesamten Artikel zu lesen.

1. [Vorbereitung](#before-you-start)
1. [Phase der Migrationsvorbereitung](#pre-migration-stage)
1. [Migrationsphase](#migration-stage)
1. [Phase der Migrationsnachbereitung](#post-migration-stage)

Sie können die Migration ohne Ausfallzeiten auf Ihren SSRS-Servern oder ohne Unterbrechungen für Ihre Berichtsbenutzer durchführen. Es ist wichtig zu wissen, dass keine Daten oder Berichte entfernt werden müssen. Es bedeutet also, dass Sie Ihre aktuelle Umgebung beibehalten können, bis Sie bereit sind, die Anwendung außer Kraft zu setzen.

## <a name="before-you-start"></a>Bevor Sie beginnen

Bevor Sie mit der Migration beginnen, sollten Sie überprüfen, ob Ihre Umgebung bestimmte Voraussetzungen erfüllt. Wir beschreiben diese Voraussetzungen und stellen Ihnen auch ein hilfreiches Migrationstool vor.

### <a name="preparing-for-migration"></a>Vorbereitung auf die Migration

Wenn Sie die Migration Ihrer Berichte für Power BI vorbereiten, vergewissern Sie sich zunächst, dass Ihr Unternehmen über ein [Power BI Premium](../service-premium-what-is.md)-Abonnement verfügt. Dieses Abonnement ist erforderlich, um Ihre paginierten Berichte in Power BI zu hosten und auszuführen.

### <a name="supported-versions"></a>Unterstützte Versionen

Sie können SSRS-Instanzen migrieren, die lokal oder auf virtuellen Computern ausgeführt werden, die von Cloudanbietern wie Azure gehostet werden.

Die folgende Liste beschreibt die für die Migration zu Power BI unterstützten SQL Server-Versionen:

> [!div class="checklist"]
> - SQL Server 2012
> - SQL Server 2014
> - SQL Server 2016
> - SQL Server 2017
> - SQL Server 2019

Eine Migration vom Power BI-Berichtsserver ist ebenfalls möglich.

### <a name="migration-tool"></a>Migrationstool

Es wird empfohlen, dass Sie das [RDL-Migrationstool](https://github.com/microsoft/RdlMigration) verwenden, um Ihre Berichte vorzubereiten und zu migrieren. Dieses Tool wurde von Microsoft entwickelt, um Kunden bei der Migration von RDL-Berichten von ihren SSRS-Servern zu Power BI zu unterstützen. Es ist auf GitHub verfügbar und dokumentiert eine exemplarische End-to-End-Vorgehensweise des Migrationsszenarios.

Das Tool automatisiert die folgenden Aufgaben:

- Prüfung auf [nicht unterstützte Datenquellen](../paginated-reports-data-sources.md) und [nicht unterstützte Berichtsfeatures](../paginated-reports-faq.md#what-paginated-report-features-in-ssrs-arent-yet-supported-in-power-bi)
- Umwandlung beliebiger _freigegebener_ Ressourcen in _eingebettete_ Ressourcen:
  - Freigegebene **Datenquellen** werden zu eingebetteten Datenquellen
  - Freigegebene **Datasets** werden zu eingebetteten Datasets
- Veröffentlichung von Berichten (die Prüfungen bestehen) als paginierte Berichte in einem bestimmten Power BI-Arbeitsbereich (auf einer Premium-Kapazität)

Vorhandene Berichte werden nicht geändert oder entfernt. Nach Abschluss gibt das Tool eine Zusammenfassung aller abgeschlossenen Aktionen aus – erfolgreich oder nicht erfolgreich.

Im Laufe der Zeit wird das Tool möglicherweise von Microsoft verbessert. Die Community ist ebenfalls aufgefordert, ihren Beitrag zu leisten und zu dessen Verbesserung beizutragen.

## <a name="pre-migration-stage"></a>Phase der Migrationsvorbereitung

Nachdem Sie überprüft haben, dass Ihr Unternehmen die Voraussetzungen erfüllt, können Sie mit der Phase der _Migrationsvorbereitung_ beginnen. Diese Phase besteht aus drei Stufen:

1. Ermitteln
1. Bewerten
1. Vorbereiten

### <a name="discover"></a>Ermitteln

Das Ziel der Phase _Ermitteln_ ist es, Ihre vorhandenen SSRS-Instanzen zu identifizieren. Dieser Prozess umfasst die Überprüfung des Netzwerks, um alle SQL Server-Instanzen in Ihrem Unternehmen zu identifizieren.

Sie können das [Microsoft Assessment and Planning Toolkit](https://www.microsoft.com/download/details.aspx?id=7826) verwenden. Auch bekannt als „MAP Toolkit“, ermittelt und meldet es Ihre SQL Server-Instanzen, -Versionen und installierten Features. Es ist ein leistungsstarkes Tool zur Bestandsaufnahme, Bewertung und Berichterstellung, das Ihren Migrationsplanungsprozess vereinfachen kann.

### <a name="assess"></a>Bewerten

Nachdem Sie Ihre SSRS-Instanzen ermittelt haben, besteht das Ziel der _Bewerten_-Phase darin, alle SSRS-Berichte – oder Serverelemente – zu verstehen, die nicht migriert werden können.

Nur RDL-Berichte können von Ihren SSRS-Servern zu Power BI migriert werden. Jeder migrierte RDL-Bericht wird zu einem paginierten Bericht in Power BI.

Die folgenden SSRS-Elementtypen können jedoch nicht zu Power BI migriert werden:

- Freigegebene Datenquellen <sup>1</sup>
- Freigegebene Datasets <sup>1</sup>
- Ressourcen wie Bilddateien
- KPIs (SSRS 2016 oder höher – nur Enterprise Edition)
- Mobile Berichte (SSRS 2016 oder höher – nur Enterprise Edition)
- Berichtsmodelle (veraltet)
- Berichtsteile (veraltet)

<sup>1</sup> Das [RDL-Migrationstool](https://github.com/microsoft/RdlMigration) konvertiert automatisch freigegebene Datenquellen und freigegebene Datasets, sofern diese unterstützte Datenquellen verwenden.

Wenn Ihre RDL-Berichte auf Features angewiesen sind, die von [paginierten Power BI-Berichten noch nicht unterstützt werden](../paginated-reports-faq.md#what-paginated-report-features-in-ssrs-arent-yet-supported-in-power-bi), können Sie planen, sie als [Power BI-Berichte](../consumer/end-user-reports.md) neu zu entwickeln. Auch wenn Ihre RDL-Berichte migriert werden können, empfehlen wir Ihnen, die Aktualisierung als Power BI-Berichte in Betracht zu ziehen, wenn dies sinnvoll ist.

Wenn Ihre RDL-Berichte Daten aus _lokalen Datenquellen_ abrufen müssen, können sie nicht die Funktion „Einmaliges Anmelden“ (Single Sign-On, SSO) verwenden. Zurzeit wird beim Datenabruf aus diesen Quellen immer der Sicherheitskontext des _Benutzerkontos der Gatewaydatenquelle_ verwendet. SQL Server Analysis Services (SSAS) kann die Sicherheit auf Zeilenebene (row-level security, RLS) nicht pro Benutzer erzwingen.

Paginierte Berichte in Power BI sind im Allgemeinen für den **Druckvorgang** oder die **PDF-Erstellung** optimiert. Power BI-Berichte sind für **Recherche und Interaktivität** optimiert. Weitere Informationen finden Sie unter [Wann sollten paginierte Berichte in Power BI verwendet werden?](report-paginated-or-power-bi.md).

### <a name="prepare"></a>Vorbereiten

Das Ziel der Phase _Vorbereiten_ besteht darin, alles vorzubereiten. Sie umfasst die Einrichtung der Power BI-Umgebung, die Planung der Sicherung und Veröffentlichung Ihrer Berichte sowie Ideen für die Neuentwicklung von SSRS-Elementen, die nicht migriert werden können.

1. Stellen Sie sicher, dass die [Workload der paginierten Berichte](../service-admin-premium-workloads.md#paginated-reports) für Ihre Power BI Premium-Kapazität aktiviert ist und dass sie über ausreichend Arbeitsspeicher verfügt.
1. Überprüfen Sie die Unterstützung für Ihre [Berichtsdatenquellen](../paginated-reports-data-sources.md), und richten Sie ein [Power BI Gateway](../service-gateway-onprem.md) ein, um die Verbindungen mit beliebigen lokalen Datenquellen zu ermöglichen.
1. Machen Sie sich mit der Power BI-Sicherheit vertraut, und planen Sie, [wie Sie Ihre SSRS-Ordner und Berechtigungen](/sql/reporting-services/security/secure-folders) mit [Power BI-Arbeitsbereichen und Arbeitsbereichsrollen](../service-new-workspaces.md) reproduzieren.
1. Machen Sie sich mit der Power BI-Freigabe vertraut und planen Sie, wie Sie Inhalte durch die Veröffentlichung von [Power BI-Apps](../service-create-distribute-apps.md) verteilen werden.
1. Erwägen Sie die Verwendung von [freigegebenen Power BI-Datasets](../service-datasets-build-permissions.md) anstelle Ihrer freigegebenen SSRS-Datenquellen.
1. Verwenden Sie [Power BI Desktop](../desktop-what-is-desktop.md), um für Mobilgeräte optimierte Berichte zu entwickeln, möglicherweise unter Verwendung des [benutzerdefinierten visuellen Power KPI-Elements](https://appsource.microsoft.com/product/power-bi-visuals/WA104381083?tab=Overview) anstelle Ihrer mobilen SSRS-Berichte und -KPIs.
1. Bewerten Sie die Verwendung des integrierten Felds **UserID** in Ihren Berichten neu. Wenn Sie Berichtsdaten mit **UserID** sichern, müssen Sie sich bewusst sein, dass bei paginierten Berichten, die im Power BI-Dienst gehostet werden, der Benutzerprinzipalname (User Principal Name, UPN) zurückgegeben wird. So gibt das integrierte Feld z. B. statt des NT-Kontonamens _AW\mblythe_ eine Zeichenfolge ähnlich _m.blythe&commat;adventureworks.com_ zurück. Sie müssen die Datasetdefinitionen und möglicherweise die Quelldaten überarbeiten. Nach der Überarbeitung und Veröffentlichung empfiehlt es sich, Ihre Berichte gründlich zu testen, um sicherzustellen, dass die Datenberechtigungen wie erwartet funktionieren.
1. Bewerten Sie die Verwendung des integrierten Felds **ExecutionTime** in Ihren Berichten neu. Bei paginierten-Berichten, die im Power BI-Dienst gehostet sind, gibt das integrierte Feld das Datum und die Uhrzeit in der Zeitangabe _koordinierte Weltzeit (Coordinated Universal Time, UCT)_ an. Das kann Auswirkungen auf die Standardwerte für Berichtsparameter und auf die Bezeichnungen haben, die die Zeit der Berichtsausführung angeben. Letztere werden häufig in Fußzeilen von Berichten verwendet.
1. Vergewissern Sie sich, dass die Berichte keine Kartenvisualisierungen verwenden, wenn Ihre Datenquelle SQL Server (lokal) ist. Die Kartenvisualisierung hängt von räumlichen SQL Server-Datentypen ab, und diese werden vom Gateway nicht unterstützt. Weitere Informationen finden Sie unter [Leitfaden zum Datenabruf bei paginierten Berichten (komplexe SQL Server-Datentypen)](report-paginated-data-retrieval.md#sql-server-complex-data-types).
1. Stellen Sie sicher, dass Ihre Berichtsautoren [Power BI Report Builder](../report-builder-power-bi.md) installiert haben und dass spätere Versionen problemlos im gesamten Unternehmen verteilt werden können.

## <a name="migration-stage"></a>Migrationsphase

Nachdem Sie Ihre Power BI-Umgebung und -Berichte vorbereitet haben, sind Sie bereit für die _Migration_.

Es gibt zwei Migrationsoptionen: _manuell_ und _automatisiert_. Die manuelle Migration ist für eine kleine Anzahl von Berichten oder für Berichte geeignet, die vor der Migration geändert werden müssen. Die automatisierte Migration eignet sich für die Migration einer großen Anzahl von Berichten.

### <a name="manual-migration"></a>Manuelle Migration

Jeder mit der Berechtigung für den Zugriff auf die SSRS-Instanz und den Power BI-Arbeitsbereich kann Berichte manuell zu Power BI migrieren. Gehen Sie wie folgt vor:

1. Öffnen Sie das SSRS-Portal mit den Berichten, die Sie migrieren möchten.
1. Laden Sie jede Berichtsdefinition herunter, und speichern Sie die RDL-Dateien lokal.
1. Öffnen Sie _die neueste Version_ von Power BI Report Builder, und stellen Sie mit Ihren Azure AD-Anmeldeinformationen eine Verbindung mit dem Power BI-Dienst her.
1. Öffnen Sie die einzelnen Berichte in Power BI Report Builder, und gehen Sie dann folgendermaßen vor:
   1. Überprüfen Sie, ob alle Datenquellen und Datasets in die Berichtsdefinition eingebettet sind und ob sie [unterstützte Datenquellen](../paginated-reports-data-sources.md) sind.
   1. Zeigen Sie eine Vorschau des Berichts an, um sicherzustellen, dass er ordnungsgemäß gerendert wird.
   1. Wählen Sie die Option _Speichern unter_ und dann die Option _Power BI-Dienst_ aus.
   1. Wählen Sie den Arbeitsbereich aus, der den Bericht enthalten soll.
   1. Überprüfen Sie, ob der Bericht gespeichert wird. Wenn bestimmte Features im Berichtsentwurf noch nicht unterstützt werden, tritt beim Speichern ein Fehler auf. Sie werden über die entsprechenden Gründe informiert. Sie müssen dann den Berichtsentwurf überarbeiten und den Vorgang wiederholen.

### <a name="automated-migration"></a>Automatisierte Migration

Es gibt zwei Optionen für eine automatisierte Migration. Verwenden Sie Folgendes:

- RDL-Migrationstool
- Öffentlich verfügbare APIs für SSRS und Power BI

Das [RDL-Migrationstool](#migration-tool) wurde bereits in diesem Artikel beschrieben.

Sie können auch die öffentlich verfügbaren SSRS- und Power BI-APIs verwenden, um die Migration Ihrer Inhalte zu automatisieren. Während das RDL-Migrationstool bereits diese APIs nutzt, können Sie ein angepasstes Tool entwickeln, das genau Ihren Anforderungen entspricht.

Weitere Informationen zu den APIs finden Sie unter:

- [Referenz für Power BI-REST-API](../developer/rest-api-reference.md)
- [SQL Server Reporting Services-REST-APIs](/sql/reporting-services/developer/rest-api)

## <a name="post-migration-stage"></a>Phase der Migrationsnachbereitung

Nachdem Sie die Migration erfolgreich abgeschlossen haben, sind Sie bereit für die Phase der _Migrationsnachbereitung_. Diese Phase umfasst die Durchführung einer Reihe von Aufgaben nach der Migration, um sicherzustellen, dass alles ordnungsgemäß und effizient funktioniert.

### <a name="configure-data-sources"></a>Konfigurieren von Datenquellen

Nachdem Berichte zu Power BI migriert wurden, müssen Sie sicherstellen, dass ihre Datenquellen ordnungsgemäß eingerichtet sind. Dies kann die Zuweisung von Datenquellen an das Gateway und die [sichere Speicherung von Anmeldeinformationen für die Datenquellen](../paginated-reports-data-sources.md#azure-sql-database-authentication) umfassen. Diese Aktionen werden vom RDL-Migrationstool nicht durchgeführt.

### <a name="review-report-performance"></a>Überprüfen der Berichtsleistung

Es wird dringend empfohlen, dass Sie die folgenden Aktionen durchführen, um die bestmögliche Benutzererfahrung für Berichte sicherzustellen:

1. Testen Sie die Berichte in jedem [Browser, der von Power BI](../power-bi-browsers.md) unterstützt wird, um das ordnungsgemäße Rendern des Berichts zu bestätigen.
1. Führen Sie Tests durch, um die Renderingzeiten von Berichten in SSRS und Power BI zu vergleichen. Überprüfen Sie, ob Power BI-Berichte in annehmbarer Zeit gerendert werden.
1. Wenn Power BI-Berichte aufgrund von unzureichendem Arbeitsspeicher nicht gerendert werden können, weisen Sie der [Power BI Premium-Kapazität zusätzliche Ressourcen zu](../service-admin-premium-workloads.md#paginated-reports).
1. Wenn Sie Berichte mit langer Renderingzeit erstellen, sollten Sie in Erwägung ziehen, dass Power BI sie Ihren Berichtsbenutzern als [E-Mail-Abonnement mit Berichtsanlagen](../consumer/paginated-reports-subscriptions.md) zur Verfügung stellt.
1. Überprüfen Sie bei Power BI-Berichten, die auf Power BI-Datasets basieren, die Modellentwürfe, um sicherzustellen, dass sie vollständig optimiert sind.

### <a name="reconcile-issues"></a>Abstimmen von Problemen

Die Phase der Migrationsnachbereitung ist entscheidend für die Abstimmung aller Probleme, und dass Sie sich mit allen Leistungsproblemen befassen. Das Hinzufügen der Workload für paginierte Berichte zu einer Kapazität kann zu einer geringen Leistung beitragen – für paginierte Berichte _und andere in der Kapazität gespeicherte Inhalte_.

Weitere Informationen zu diesen Problemen, einschließlich bestimmter Schritte, um sie zu verstehen und zu mildern, finden Sie in den folgenden Artikeln:

- [Optimieren von Premium-Kapazitäten](../service-premium-capacity-optimize.md)
- [Überwachen von Premium-Kapazitäten über die App](../service-admin-premium-monitor-capacity.md)

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zu diesem Artikel finden Sie in den folgenden Ressourcen:

- [Was sind paginierte Berichte in Power BI Premium? (Vorschau)](../paginated-reports-report-builder-power-bi.md)
- [Leitfaden zum Datenabruf bei paginierten Berichten](report-paginated-data-retrieval.md)
- [Wann sollten paginierte Berichte in Power BI verwendet werden?](report-paginated-or-power-bi.md)
- [Paginierte Berichte in Power BI: häufig gestellte Fragen](../paginated-reports-faq.md)
- [Power BI Premium – Häufig gestellte Fragen (FAQ)](../service-premium-faq.md)
- [RDL-Migrationstool](https://github.com/microsoft/RdlMigration)
- Haben Sie Fragen? [Stellen Sie Ihre Frage in der Power BI-Community.](https://community.powerbi.com/)
- Vorschläge? [Einbringen von Ideen zur Verbesserung von Power BI](https://ideas.powerbi.com/)

Power BI-Partner stehen zur Verfügung, um Ihr Unternehmen bei der erfolgreichen Migration zu unterstützen. Wenn Sie einen Power BI-Partner hinzuziehen möchten, besuchen Sie das [Power BI-Partnerportal](https://powerbi.microsoft.com/partners/).
