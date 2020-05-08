---
title: Verwenden von DirectQuery in Power BI Desktop
description: Verwenden von DirectQuery („Liveverbindung“) in Power BI Desktop
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 02/13/2020
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: d8432ae10afab6cbf12c017a8f315fd55825212d
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "77427229"
---
# <a name="use-directquery-in-power-bi-desktop"></a>Verwenden von DirectQuery in Power BI Desktop
Wenn Sie mit *Power BI Desktop* eine Verbindung mit Ihrer Datenquelle herstellen, können Sie immer eine Kopie der Daten in Power BI Desktop importieren. Für einige Datenquellen steht hierzu eine weitere Möglichkeit zur Verfügung: das Herstellen einer direkten Verbindung mit der Datenquelle mithilfe von DirectQuery.

## <a name="supported-data-sources"></a>Unterstützte Datenquellen
Eine vollständige Auflistung der Datenquellen, die DirectQuery unterstützen, finden Sie unter [Von DirectQuery unterstützte Datenquellen](power-bi-data-sources.md).

## <a name="how-to-connect-using-directquery"></a>Herstellen einer Verbindung mithilfe von DirectQuery
Wenn Sie über die Option **Daten abrufen** eine Verbindung mit einer Datenquelle herstellen, die von DirectQuery unterstützt wird, können Sie im Dialogfeld „Verbindung“ auswählen, wie die Verbindung hergestellt werden soll. Klicken Sie beispielsweise in Power BI Desktop im Menüband **Start** auf die Option **Daten abrufen** > **SQL Server**. Im Dialogfeld **SQL Server-Datenbank** werden unter **Datenkonnektivitätsmodus** die Optionen **Import** und **DirectQuery** angezeigt:

![Optionen „Import“ und „DirectQuery“ im Dialogfeld „SQL Server-Datenbank“ in Power BI Desktop](media/desktop-use-directquery/directquery_sqlserverdb.png)

Die Optionen **Import** und **DirectQuery** weisen folgende Unterschiede auf:

- **Import**: Die ausgewählten Tabellen und Spalten werden in Power BI Desktop importiert. Beim Erstellen oder Interagieren mit einer Visualisierung verwendet Power BI Desktop die importierten Daten. Aktualisieren Sie die Daten, um zugrunde liegende Änderungen seit dem ersten Import oder der letzten Aktualisierung anzuzeigen. Dabei wird das vollständige Dataset noch mal importiert.

- **DirectQuery**: Es werden keine Daten in Power BI Desktop importiert oder kopiert. Bei relationalen Quellen werden die ausgewählten Tabellen und Spalten in der Liste **Felder** angezeigt. Bei mehrdimensionalen Datenquellen wie SAP Business Warehouse werden die Dimensionen und Measures für den ausgewählten Cube in der Liste **Felder** angezeigt. Beim Erstellen oder Interagieren mit einer Visualisierung fragt Power BI Desktop die zugrunde liegende Datenquelle ab. Dadurch werden immer aktuelle Daten angezeigt.

Bei Verwendung von DirectQuery sind viele Datenmodelle und Datentransformationen verfügbar, jedoch mit einigen Einschränkungen. Beim Erstellen oder Interagieren mit einer Visualisierung müssen Sie die zugrunde liegende Quelle abrufen. Die zum Aktualisieren der Visualisierung benötigte Zeit hängt von der Leistung der zugrunde liegenden Datenquelle ab. Wurden die für die Anforderung erforderlichen Daten kürzlich abgefragt, verwendet Power BI Desktop diese Daten, um die Visualisierung schneller anzeigen zu können. Klicken Sie im Menüband **Start** auf **Aktualisieren**, um alle Visualisierungen mit aktuellen Daten zu aktualisieren.

Eine ausführliche Beschreibung von DirectQuery finden Sie im Artikel [Power BI und DirectQuery](desktop-directquery-about.md). Weitere Informationen zu den Vorteilen, Einschränkungen sowie wichtigen Überlegungen bei der Verwendung von DirectQuery finden Sie in den folgenden Abschnitten.

## <a name="benefits-of-using-directquery"></a>Vorteile der Verwendung von DirectQuery
Die Verwendung von DirectQuery besitzt folgende Vorteile:

- Mithilfe von DirectQuery können Visualisierungen sehr großer Datasets erstellt werden, die Sie andernfalls unmöglich mit Vorabaggregation aller Daten importieren könnten.
- Änderungen an den zugrunde liegenden Daten können eine Aktualisierung der Daten erforderlich machen. Für einige Berichte, die stets aktuelle Daten anzeigen müssen, sind eventuell umfangreiche Datenübertragungen erforderlich, sodass das erneute Importieren von Daten nicht durchführbar ist. Im Gegensatz dazu werden in DirectQuery-Berichten immer aktuelle Daten verwendet.
- Die Einschränkung auf 1 GB für Datasets gilt *nicht* für DirectQuery.

## <a name="limitations-of-directquery"></a>Einschränkungen für DirectQuery
Derzeit bestehen bei der Verwendung von DirectQuery folgende Einschränkungen:

- Bei einer zu komplexen Abfrage im **Abfrage-Editor** tritt ein Fehler auf. Löschen Sie zur Behebung des Fehlers entweder den fraglichen Schritt im **Abfrage-Editor**, oder verwenden Sie anstelle von DirectQuery die Option *Import*. Für mehrdimensionale Datenquellen wie SAP Business Warehouse ist kein **Abfrage-Editor** verfügbar.

- Zeitintelligenzfunktionen sind in DirectQuery nicht verfügbar. Beispielsweise wird die spezifische Behandlung von Datumsspalten (wie Jahr, Quartal, Monat oder Tag) im DirectQuery-Modus nicht unterstützt.

- Um sicherzustellen, dass Abfragen, die an die zugrundeliegende Datenquelle gesendet werden, eine akzeptable Leistung aufweisen, werden für Measures standardmäßig DAX-Einschränkungen angewendet.

- Bei Verwendung von DirectQuery können maximal eine Million Zeilen mit Daten zurückgegeben werden, außer es wird eine Premium-Kapazität verwendet. Dies betrifft nicht Aggregationen oder Berechnungen, die zum Erstellen des mit DirectQuery zurückgegebenen Datasets verwendet werden. Die Begrenzung betrifft nur die zurückgegebenen Zeilen. Bei Premium-Kapazitäten kann eine maximale Zeilenanzahl festgelegt werden, wie in [diesem Beitrag](https://powerbi.microsoft.com/blog/five-new-power-bi-premium-capacity-settings-is-available-on-the-portal-preloaded-with-default-values-admin-can-review-and-override-the-defaults-with-their-preference-to-better-fence-their-capacity/) beschrieben. 

    Sie können beispielsweise 10 Millionen Zeilen mit der Abfrage aggregieren, die für die Datenquelle ausgeführt wird. Die Abfrage gibt die korrekten Ergebnisse dieser Aggregation mithilfe von DirectQuery an Power BI zurück, wenn die zurückgegebenen Power BI-Daten aus weniger als 1 Million Zeilen bestehen. Wenn mehr als eine Million Zeilen von DirectQuery zurückgegeben werden, gibt Power BI einen Fehler zurück (außer bei Premium-Kapazität, solange die Zeilenanzahl unterhalb der vom Administrator festgelegten Obergrenze liegt).

## <a name="important-considerations-when-using-directquery"></a>Wichtige Überlegungen bei der Verwendung von DirectQuery
Die folgenden drei Aspekte sollten Sie bei der Verwendung von DirectQuery berücksichtigen:

- **Leistung und Auslastung**: Alle DirectQuery-Anforderungen werden an die Quelldatenbank gesendet. Daher hängt die erforderliche Aktualisierungsdauer für das Visual davon ab, wie lange diese Back-End-Quelle für die Rückgabe der Ergebnisse der Abfrage (bzw. Abfragen) benötigt. Die empfohlene Antwortzeit (für die Rückgabe der angeforderten Daten) bei Verwendung von DirectQuery für Visuals beträgt fünf Sekunden oder weniger. Die maximale empfohlene Antwortzeit für Ergebnisse beträgt 30 Sekunden. Eine längere Zeitspanne stellt eine inakzeptable Beeinträchtigung der Benutzerfreundlichkeit des Berichts dar. Sobald ein Bericht im Power BI-Dienst veröffentlicht wurde, tritt für jede Abfrage, die länger als einige Minuten dauert, ein Timeout auf, und der Benutzer erhält eine Fehlermeldung.
  
    Auch sollte die Auslastung der Quelldatenbank basierend auf der Anzahl der Power BI-Benutzer berücksichtigt werden, die den veröffentlichten Bericht verwenden werden. Auch die Verwendung von **Sicherheit auf Zeilenebene** (Row Level Security, RLS) kann erhebliche Auswirkungen besitzen. Eine Dashboardkachel ohne RLS, die von mehreren Benutzern gemeinsam genutzt wird, führt zu einer einzelnen Datenbankabfrage. Die Verwendung von RLS für eine Dashboardkachel bedeutet jedoch in der Regel, dass für die Aktualisierung der Kachel eine Abfrage *pro Benutzer* erforderlich ist. Dadurch wird die Auslastung der Quelldatenbank deutlich erhöht und die Leistung möglicherweise beeinträchtigt.
  
    Power BI erstellt Abfragen, die so effizient wie möglich sind. In bestimmten Situationen ist die generierte Abfrage jedoch möglicherweise nicht effizient genug, um Aktualisierungsfehler zu verhindern. Ein Beispiel für eine solche Situation ist eine generierte Abfrage, die eine übermäßig große Anzahl von Zeilen aus der Back-End-Datenquelle abruft. In diesem Fall wird der folgende Fehler zurückgegeben:

    ```output
    The resultset of a query to external data source has exceeded
    ```
  
    Diese Situation kann bei einem einfachen Diagramm auftreten, das eine sehr hohe Kardinalitätsspalte enthält und für das die Aggregationsoption auf **Nicht zusammenfassen** festgelegt ist. Das Visual darf nur Spalten mit einer Kardinalität unter 1 Million enthalten, oder es müssen entsprechende Filter angewendet werden.

- **Sicherheit**: Alle Benutzer, die einen veröffentlichten Bericht verwenden, stellen automatisch eine Verbindung mit der Back-End-Datenquelle mithilfe der Anmeldeinformationen her, die nach der Veröffentlichung im Power BI-Dienst eingegeben wurden. Dies ist derselbe Vorgang wie bei importierten Daten: Für alle Benutzer werden dieselben Daten angezeigt, unabhängig von in der Back-End-Datenquelle definierten Sicherheitsregeln.

    Kunden, die mit DirectQuery-Quellen benutzerspezifische Sicherheit implementieren möchten, sollten entweder RLS verwenden oder für die Quelle die eingeschränkte Kerberos-Authentifizierung konfigurieren. Kerberos ist nicht für alle Quellen verfügbar. [Erfahren Sie mehr zu RLS](service-admin-rls.md). [Weitere Informationen zu Kerberos in DirectQuery](service-gateway-sso-kerberos.md).

- **Unterstützte Funktionen**: Nicht alle Funktionen in Power BI Desktop werden im DirectQuery-Modus unterstützt, oder es gelten bestimmte Einschränkungen. Zudem sind einige Funktionen des Power BI-Diensts (z. B. *Quick Insights*) nicht für Datasets verfügbar, die DirectQuery verwenden. Wenn Sie über die Verwendung von DirectQuery nachdenken, sollten Sie diese Funktionseinschränkungen berücksichtigen.

## <a name="publish-to-the-power-bi-service"></a>Veröffentlichen im Power BI-Dienst
Mit DirectQuery erstellte Berichte können im Power BI-Dienst veröffentlicht werden.

Wenn die verwendete Datenquelle kein **lokales Datengateway** benötigt (**Azure SQL-Datenbank**, **Azure SQL Data Warehouse** oder **Redshift**), ist die Eingabe von Anmeldeinformationen erforderlich, bevor der veröffentlichte Bericht im Power BI-Dienst angezeigt wird. Führen Sie die folgenden Schritte aus, um die Anmeldeinformationen bereitzustellen:

1. Melden Sie sich bei [Power BI](https://www.powerbi.com/) an.
2. Klicken Sie im Power BI-Dienst auf das Zahnradsymbol für **Einstellungen** und anschließend auf das Menüelement **Einstellungen**.

    ![Einstellungen im Power BI-Dienst](media/desktop-use-directquery/directquery_pbiservicesettings.png)

3. Klicken Sie im Power BI-Dienst auf der Seite **Einstellungen** auf die Registerkarte **Datasets** und dann auf das Dataset, das DirectQuery verwendet. Klicken Sie anschließend auf **Anmeldeinformationen bearbeiten**.

4. Fügen Sie die Anmeldeinformationen hinzu. Andernfalls tritt ein Fehler auf, wenn Sie einen veröffentlichten Bericht öffnen oder ein Dataset untersuchen, das mit einer DirectQuery-Verbindung erstellt wurde.

Wenn Sie eine Verbindung mit einer anderen Datenquelle als **Azure SQL-Datenbank**, **Azure SQL Data Warehouse**, **Redshift** oder **Snowflake Data Warehouse** herstellen möchten, die DirectQuery verwendet, installieren Sie ein **lokales Datengateway**, und registrieren Sie die Datenquelle. Weitere Informationen finden Sie unter [Was ist ein lokales Datengateway?](service-gateway-onprem.md).

## <a name="next-steps"></a>Nächste Schritte
Weitere Informationen zu DirectQuery finden Sie in den folgenden Ressourcen:

- [Verwendung von DirectQuery in Power BI](desktop-directquery-about.md)
- [Von DirectQuery unterstützte Datenquellen](power-bi-data-sources.md)
- [DirectQuery und SAP Business Warehouse (BW)](desktop-directquery-sap-bw.md)
- [DirectQuery und SAP HANA](desktop-directquery-sap-hana.md)
- [What is an on-premises data gateway? (Was ist ein lokales Datengateway?)](service-gateway-onprem.md)
