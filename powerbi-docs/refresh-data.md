---
title: Aktualisieren von Daten in Power BI
description: Dieser Artikel beschreibt die Datenaktualisierungsfeatures von Power BI und ihre Abhängigkeiten auf konzeptioneller Ebene.
author: maggiesMSFT
ms.reviewer: kayu
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 10/14/2019
ms.author: maggies
LocalizationGroup: Data refresh
ms.openlocfilehash: 810077e8c651d3d6faf91eecb6fd320c24a69d2f
ms.sourcegitcommit: a175faed9378a7d040a08ced3e46e54503334c07
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/18/2020
ms.locfileid: "79488796"
---
# <a name="data-refresh-in-power-bi"></a>Aktualisieren von Daten in Power BI

Mit Power BI können Sie schnell Einblicke in Daten gewinnen und diesen Einblicken entsprechende Aktionen veranlassen, aber Sie müssen sicherstellen, dass die Daten in Ihren Power BI-Berichten und -Dashboards aktuell sind. Zu wissen, wie die Daten aktualisiert werden, kann oftmals dafür entscheidend sein, genaue Ergebnisse zu erhalten.

Dieser Artikel beschreibt die Datenaktualisierungsfeatures von Power BI und ihre Abhängigkeiten auf konzeptioneller Ebene. Darüber hinaus werden Ihnen Best Practices und Tipps zur Vermeidung häufig auftretender Aktualisierungsprobleme vorgestellt. Der Inhalt bietet Ihnen eine Grundlage, den Ablauf der Datenaktualisierung besser zu verstehen. Gezielte schrittweise Anweisungen zum Konfigurieren der Datenaktualisierung finden Sie in den Tutorials und Anleitungen, die am Ende dieses Artikels im Abschnitt „Nächste Schritte“ aufgeführt sind.

## <a name="understanding-data-refresh"></a>Grundlegendes zur Datenaktualisierung

Wenn Sie Daten aktualisieren, muss Power BI die zugrunde liegenden Datenquellen abfragen, möglicherweise die Quelldaten in ein Dataset geladen und dann alle Visualisierungen in Ihren Berichten oder Dashboards aktualisieren, die auf dem aktualisierten Dataset basieren. Der gesamte Prozess besteht je nach den Speichermodi Ihrer Datasets aus mehreren Phasen, wie in den folgenden Abschnitten erläutert.

Um zu verstehen, wie Power BI Ihre Datasets, Berichte und Dashboards aktualisiert, müssen Sie die folgenden Konzepte kennen:

- **Speichermodi und Datasettypen**: Für die von Power BI unterstützten Speichermodi und Datasettypen gelten unterschiedliche Aktualisierungsanforderungen. Sie können zwischen dem erneuten Importieren von Daten in Power BI, um etwaige aufgetretene Änderungen anzuzeigen, oder dem direkten Abfragen der Daten an der Quelle wählen.
- **Power BI-Aktualisierungstypen**: Unabhängig von den Besonderheiten des jeweiligen Datasets kann die Kenntnis der verschiedenen Aktualisierungstypen Ihnen erleichtern, zu verstehen, wie Power BI während eines Aktualisierungsvorgangs vorgehen könnte. Außerdem erleichtert die Kombination dieser Details mit Speichermoduskenntnissen Ihnen das Verständnis der genauen Vorgehensweise von Power BI, wenn Sie **Jetzt aktualisieren** für ein Dataset auswählen.

### <a name="storage-modes-and-dataset-types"></a>Speichermodi und Datasettypen

Ein Power BI-Dataset kann in einem der folgenden Modi für den Zugriff auf Daten aus einer Vielzahl von Datenquellen eingesetzt werden. Weitere Informationen erhalten Sie unter [Storage mode in Power BI Desktop (Speichermodus in Power BI Desktop)](desktop-storage-mode.md).

- Import-Modus
- DirectQuery-Modus
- LiveConnect-Modus
- Pushmodus

Das folgende Diagramm veranschaulicht basierend auf dem Speichermodus die unterschiedlichen Datenflüsse. Der wichtigste Punkt ist, dass nur die Datasets im Import-Modus eine Quelldatenaktualisierung erfordern. Sie benötigen die Aktualisierung, weil nur dieser Datasettyp Daten aus ihren Datenquellen importiert, und die importierten Daten könnten auf regulärer oder Ad-hoc-Basis aktualisiert werden. DirectQuery-Datasets und mit Analysis Services verbundene Datasets im LiveConnect-Modus importieren keine Daten, sondern fragen bei jeder Benutzerinteraktion die zugrunde liegende Datenquelle ab. Datasets im Pushmodus greifen nicht direkt auf Datenquellen zu, sondern erwarten, dass Sie die Daten zu Power BI pushen. Die Anforderungen an die Aktualisierung von Datasets variieren je nach Speichermodus/Datasettyp.

![Speichermodi und Datasettypen](media/refresh-data/storage-modes-dataset-types-diagram.png)

#### <a name="datasets-in-import-mode"></a>Datasets im Import-Modus

Power BI importiert die Daten aus den ursprünglichen Datenquellen in das Dataset. Power BI-Berichts- und Dashboardabfragen, die an das Dataset gesendet werden, geben Ergebnisse aus den importierten Tabellen und Spalten zurück. Sie könnten ein solches Dataset als eine zeitpunktgenaue Kopie betrachten. Da Power BI die Daten kopiert, müssen Sie das Dataset aktualisieren, um Änderungen aus den zugrunde liegenden Datenquellen zu holen.

Da Power BI die Daten zwischenspeichert, können die Größen der Datasets im Import-Modus erheblich sein. Die maximalen Datasetgrößen pro Kapazität können Sie der folgenden Tabelle entnehmen. Bleiben Sie weit unter den maximalen Datasetgrößen, um Aktualisierungsprobleme zu vermeiden, die auftreten könnten, wenn Ihre Datasets während eines Aktualisierungsvorgangs mehr als die maximal verfügbaren Ressourcen benötigen.

| Kapazitätstyp | Maximale Datasetgröße |
| --- | --- |
| Gemeinsam genutzt, A1, A2 oder A3 | 1 GB |
| A4 oder P1 | 3GB |
| A5 oder P2 | 6 GB |
| A6 oder P3 | 10 GB |
| | |

#### <a name="datasets-in-directqueryliveconnect-mode"></a>Datasets im DirectQuery-/LiveConnect-Modus

Power BI importiert Daten nicht über Verbindungen, die im DirectQuery-/LiveConnect-Modus betrieben werden. Stattdessen gibt das Dataset Ergebnisse aus der zugrunde liegenden Datenquelle zurück, wenn ein Bericht oder ein Dashboard das Dataset abfragt. Power BI transformiert die Abfragen und leitet sie an die Datenquelle weiter.

Obwohl DirectQuery-Modus und LiveConnect-Modus insofern ähnlich sind, dass Power BI die Abfragen an die Quelle weiterleitet, ist es wichtig zu beachten, dass Power BI Abfragen im LiveConnect-Modus nicht transformieren muss. Die Abfragen gehen direkt an die Analysis Services-Instanz, die die Datenbank hostet, ohne Ressourcen auf gemeinsam genutzter oder Premium-Kapazität zu verbrauchen.

Da Power BI die Daten nicht importiert, müssen Sie keine Datenaktualisierung durchführen. Power BI führt jedoch weiterhin Kachelaktualisierungen und möglicherweise Berichtsaktualisierungen durch, wie im nächsten Abschnitt über Aktualisierungstypen beschrieben. Eine Kachel ist ein visueller Bericht, der an ein Dashboard angeheftet ist, und die Aktualisierung der Kachel des Dashboards erfolgt etwa jede Stunde, sodass die Kacheln die neuesten Ergebnisse anzeigen. Sie können den Zeitplan in den Dataseteinstellungen ändern, wie im folgenden Screenshot gezeigt, oder eine Aktualisierung des Dashboards manuell erzwingen, indem Sie die Option **Jetzt aktualisieren** verwenden.

![Aktualisierungszeitplan](media/refresh-data/refresh-schedule.png)

> [!NOTE]
> Der Abschnitt **Geplante Cacheaktualisierung** auf der Registerkarte **Datasets** ist für Datasets im Import-Modus nicht verfügbar. Diese Datasets erfordern keine separate Kachelaktualisierung, da Power BI die Kacheln bei jeder geplanten oder bedarfsgesteuerten Datenaktualisierung automatisch aktualisiert.

#### <a name="push-datasets"></a>Pushdatasets

Pushdatasets enthalten keine formale Definition einer Datenquelle, sodass Sie keine Datenaktualisierung in Power BI durchführen müssen. Sie aktualisieren sie, indem Sie Ihre Daten über einen externen Dienst oder Prozess wie z.B. Azure Stream Analytics in das Dataset pushen. Dies ist eine gängige Methode für Analysen in Echtzeit mit Power BI. Power BI führt weiterhin Cacheaktualisierungen für alle Kacheln durch, die auf einem Pushdataset verwendet werden. Eine ausführliche exemplarische Vorgehensweise finden Sie unter [Tutorial: Stream Analytics und Power BI: Ein Dashboard zur Echtzeitanalyse von Streamingdaten](/azure/stream-analytics/stream-analytics-power-bi-dashboard).

> [!NOTE]
> Für den Pushmodus gelten mehrere Einschränkungen, wie in [Einschränkungen für Power BI-REST-API](developer/automation/api-rest-api-limitations.md) dokumentiert.

### <a name="power-bi-refresh-types"></a>Power BI-Aktualisierungstypen

Ein Power BI-Aktualisierungsvorgang kann aus mehreren Aktualisierungstypen bestehen, einschließlich Datenaktualisierung, OneDrive-Aktualisierung, Aktualisierung von Abfragecaches, Kachelaktualisierung und Aktualisierung visueller Berichtselemente. Power BI bestimmt zwar automatisch die erforderlichen Aktualisierungsschritte für ein bestimmtes Dataset, aber Sie sollten wissen, wie sie zur Komplexität und Dauer eines Aktualisierungsvorgangs beitragen. Eine Kurzübersicht finden Sie in der folgenden Tabelle.

| Speichermodus | Datenaktualisierung | OneDrive-Aktualisierung | Abfragecaches | Kachelaktualisierung | Visuelle Berichtselemente |
| --- | --- | --- | --- | --- | --- |
| Importieren | Geplant und bedarfsgesteuert | Ja, für verbundene Datasets | Wenn auf Premium-Kapazität aktiviert | Automatisch und bedarfsgesteuert | Nein |
| DirectQuery | Nicht zutreffend | Ja, für verbundene Datasets | Wenn auf Premium-Kapazität aktiviert | Automatisch und bedarfsgesteuert | Nein |
| LiveConnect | Nicht zutreffend | Ja, für verbundene Datasets | Wenn auf Premium-Kapazität aktiviert | Automatisch und bedarfsgesteuert | Ja |
| Push | Nicht zutreffend | Nicht zutreffend | Nicht praktisch | Automatisch und bedarfsgesteuert | Nein |
| | | | | | |

#### <a name="data-refresh"></a>Datenaktualisierung

Für Power BI-Benutzer bedeutet die Aktualisierung von Daten in der Regel den Import von Daten aus den ursprünglichen Datenquellen in ein Dataset, entweder basierend auf einem Aktualisierungszeitplan oder bedarfsgesteuert. Sie können mehrere tägliche Aktualisierungen des Datasets durchführen, was notwendig sein kann, wenn sich die zugrunde liegenden Quelldaten häufig ändern. Power BI begrenzt Datasets auf gemeinsam genutzter Kapazität auf acht tägliche Aktualisierungen. Wenn das Dataset sich auf einer Premium-Kapazität befindet, können Sie in den Dataseteinstellungen bis zu 48 Aktualisierungen pro Tag planen. Weitere Informationen finden Sie unter [Konfigurieren von geplanten Aktualisierungen](#configure-scheduled-refresh) weiter unten in diesem Artikel.

Es ist auch wichtig, darauf hinzuweisen, dass die Beschränkung der gemeinsamen Kapazität für tägliche Aktualisierungen sowohl für geplante als auch für API-Aktualisierungen gilt. Sie können auch eine bedarfsgesteuerte Aktualisierung auslösen, indem Sie **Jetzt aktualisieren** im Datasetmenü auswählen, wie der folgende Screenshot zeigt. Bedarfsgesteuerte Aktualisierungen sind nicht in der Aktualisierungseinschränkung enthalten. Beachten Sie auch, dass Datasets in einer Premium-Kapazität keine Einschränkungen für API-Aktualisierungen enthalten. Wenn Sie daran interessiert sind, eine eigene Aktualisierungslösung mithilfe der Power BI-REST-API zu erstellen, lesen Sie [Datasets – Dataset aktualisieren](/rest/api/power-bi/datasets/refreshdataset).

![Jetzt aktualisieren](media/refresh-data/refresh-now.png)

> [!NOTE]
> Datenaktualisierungen müssen auf gemeinsam genutzter Kapazität in weniger als 2 Stunden abgeschlossen werden. Wenn Ihre Datasets längere Aktualisierungsvorgänge erfordern, ziehen Sie in Betracht, das Dataset auf eine Premium-Kapazität zu verschieben. Auf Premium beträgt die maximale Aktualisierungsdauer 5 Stunden.

#### <a name="onedrive-refresh"></a>OneDrive-Aktualisierung

Wenn Sie Ihre Datasets und Berichte auf der Grundlage einer Power BI Desktop-Datei, einer Excel-Arbeitsmappe oder einer durch Trennzeichen getrennten Datei (CSV, Comma Separated Value) auf OneDrive oder SharePoint Online erstellt haben, führt Power BI eine andere Art der Aktualisierung durch, die als OneDrive-Aktualisierung bekannt ist. Weitere Informationen finden Sie unter [Abrufen von Daten aus Dateien für Power BI](service-get-data-from-files.md).

Im Gegensatz zu einer Datasetaktualisierung, in der Power BI Daten aus einer Datenquelle in ein Dataset importiert, synchronisiert die OneDrive-Aktualisierung Datasets und Berichte mit ihren Quelldateien. Standardmäßig prüft Power BI etwa stündlich, ob ein Dataset, das mit einer Datei auf OneDrive oder SharePoint Online verbunden ist, synchronisiert werden muss.

> [!IMPORTANT]
> Gehen Sie bei der Behandlung der Dateiverwaltung auf OneDrive umsichtig vor. Wenn Sie eine OneDrive-Datei als Datenquelle festlegen, verweist Power BI beim Ausführen der Aktualisierung auf die Element-ID der Datei, was in bestimmten Szenarien zu Problemen führen kann. Stellen Sie sich das Szenario vor, in dem Sie über eine Masterdatei _A_ sowie eine Kopie _B_ dieser Datei für die Produktion verfügen und Sie konfigurieren die OneDrive-Aktualisierung für Datei B. Wenn Sie dann Datei A über Datei B _kopieren_, wird durch den Kopiervorgang die alte Datei B gelöscht und eine neue Datei B mit einer anderen Element-ID erstellt, sodass die OneDrive-Aktualisierung nicht mehr funktioniert. Stattdessen sollten Sie Datei B hochladen und ersetzen, wodurch diese dieselbe Element-ID beibehält.

Sie können die Datei an einen anderen Speicherort verschieben (z. B. mittels Drag & Drop), dann funktioniert die Aktualisierung weiterhin, da PBI die fileID nach wie vor kennt. Wenn Sie diese Datei jedoch an einen anderen Speicherort kopieren, werden eine neue Instanz der Datei und eine neue fileID erstellt. Daher ist der Verweis auf die Power BI-Datei nicht mehr gültig, und die Aktualisierung schlägt fehl.

Um vergangene Synchronisationszyklen zu überprüfen, überprüfen Sie die Registerkarte OneDrive im Aktualisierungsverlauf. Der folgende Screenshot zeigt einen vollständigen Synchronisierungszyklus für ein Beispieldataset.

![Verlauf aktualisieren](media/refresh-data/refresh-history.png)

Wie der obige Screenshot zeigt, hat Power BI diese OneDrive-Aktualisierung als **Geplante** Aktualisierung identifiziert, aber es ist nicht möglich, das Aktualisierungsintervall zu konfigurieren. Sie können die OneDrive-Aktualisierung nur in den Einstellungen des Datasets deaktivieren. Das Deaktivieren der Aktualisierung ist nützlich, wenn Sie nicht möchten, dass Ihre Datasets und Berichte in Power BI Änderungen aus den Quelldateien automatisch übernehmen.

Beachten Sie, dass die Seite mit den Dataseteinstellungen nur die Abschnitte **Anmeldeinformationen für OneDrive** und **OneDrive-Aktualisierung**  anzeigt, wenn das Dataset mit einer Datei in OneDrive oder SharePoint Online verbunden ist, wie im folgenden Screenshot gezeigt. Datasets, die nicht mit einer Quellendatei in OneDrive oder SharePoint Online verbunden sind, werden nicht in diesen Abschnitten angezeigt.

![Anmeldeinformationen für OneDrive und OneDrive-Aktualisierung](media/refresh-data/onedrive-credentials-refresh.png)

Wenn Sie die OneDrive-Aktualisierung für ein Dataset deaktivieren, können Sie Ihr Dataset bei Bedarf immer noch synchronisieren, indem Sie **Jetzt aktualisieren** im Datasetmenü auswählen. Im Rahmen der bedarfsgesteuerten Aktualisierung prüft Power BI, ob die Quelldatei auf OneDrive oder SharePoint Online neuer ist als das Dataset in Power BI und synchronisiert das Dataset, falls dies der Fall ist. **Verlauf aktualisieren** listet diese Aktivitäten als bedarfsgesteuerte Aktualisierungen auf der **OneDrive**-Registerkarte auf.

Beachten Sie, dass die OneDrive-Aktualisierung keine Daten aus den ursprünglichen Datenquellen pullt. Die OneDrive-Aktualisierung aktualisiert einfach die Ressourcen in Power BI mit den Metadaten und Daten aus der PBIX-, XLSX- oder CSV-Datei, wie das folgende Diagramm veranschaulicht. Um sicherzustellen, dass das Dataset immer die über die neuesten Daten aus den Datenquellen verfügt, löst Power BI eine Datenaktualisierung auch im Rahmen einer bedarfsgesteuerten Aktualisierung aus. Sie können dies in **Aktualisierungsverlauf** überprüfen, wenn Sie zur **Geplant**-Registerkarte wechseln.

![OneDrive-Aktualisierungsdiagramm](media/refresh-data/onedrive-refresh-diagram.png)

Wenn Sie OneDrive-Aktualisierung für ein mit OneDrive oder SharePoint Online verbundenes Dataset aktiviert lassen und die Datenaktualisierung auf Basis eines Zeitplans ausführen möchten, stellen Sie sicher, dass Sie den Zeitplan konfigurieren, sodass Power BI die Datenaktualisierung nach der OneDrive-Aktualisierung durchführt. Wenn Sie beispielsweise einen eigenen Dienst oder Prozess erstellt haben, um die Quelldatei in OneDrive oder SharePoint Online jede Nacht um 1:00 Uhr zu aktualisieren, könnten Sie die geplante Aktualisierung für 2:30 Uhr konfigurieren, um Power BI genügend Zeit zu geben, die Aktualisierung von OneDrive abzuschließen, bevor die Datenaktualisierung gestartet wird.

#### <a name="refresh-of-query-caches"></a>Aktualisieren von Abfragecaches

Wenn sich Ihr Dataset auf einer Premium-Kapazität befindet, könnten Sie die Leistung aller zugehörigen Berichte und Dashboards verbessern, indem Sie die Zwischenspeicherung von Abfragen aktivieren, wie im folgenden Screenshot gezeigt. Mit der Zwischenspeicherung von Abfragen wird die Premium-Kapazität angewiesen, den lokalen Cachedienst zu verwenden, um Abfrageergebnisse zu verwalten und um zu vermeiden, dass die zugrunde liegende Datenquelle diese Ergebnisse berechnet. Weitere Informationen finden Sie unter [Zwischenspeicherung von Abfragen in Power BI Premium](power-bi-query-caching.md).

![Zwischenspeicherung von Abfragen](media/refresh-data/query-caching.png)

Nach einer Datenaktualisierung sind jedoch zuvor zwischengespeicherte Abfrageergebnisse nicht mehr gültig. Power BI verwirft diese zwischengespeicherten Ergebnisse und muss sie neu erstellen. Aus diesem Grund ist die Zwischenspeicherung von Abfragen für Berichte und Dashboards, die mit Datasets verknüpft sind, die Sie sehr oft aktualisieren, z.B. 48 Mal pro Tag, möglicherweise nicht so nützlich.

#### <a name="tile-refresh"></a>Kachelaktualisierung

Power BI verwaltet einen Cache für jedes visuelle Kachelelement auf Ihren Dashboards und aktualisiert proaktiv die Kachelcaches, wenn sich Daten ändern. D.h., die Kachelaktualisierung erfolgt automatisch nach einer Datenaktualisierung. Dies gilt sowohl für geplante als auch bedarfsgesteuerte Aktualisierungsvorgänge. Sie können eine Kachelaktualisierung auch erzwingen, indem Sie **Weitere Optionen** (...) oben rechts in einem Dashboard auswählen und dann **Dashboardkacheln aktualisieren** auswählen.

![Dashboardkacheln aktualisieren](media/refresh-data/refresh-dashboard-tiles.png)

Da es automatisch geschieht, können Sie die Aktualisierung von Kacheln als einen wesentlichen Bestandteil der Datenaktualisierung betrachten. Unter anderem könnten Sie feststellen, dass die Aktualisierungsdauer mit der Anzahl der Kacheln steigt. Der Aufwand für die Aktualisierung der Kachel kann erheblich sein.

Standardmäßig verwaltet Power BI für jede Kachel einen einzelnen Cache, aber wenn Sie dynamische Sicherheit verwenden, um den Datenzugriff auf der Grundlage von Benutzerrollen einzuschränken, wie im Artikel [Sicherheit auf Zeilenebene (Row-Level Security; RLS) mit Power BI](service-admin-rls.md) beschrieben, dann muss Power BI für jede Rolle und jede Kachel einen Cache verwalten. Die Anzahl der Kachelcaches multipliziert mit der Anzahl der Rollen.

Die Situation kann noch komplizierter werden, wenn Ihr Dataset eine Liveverbindung mit einem Analysis Services-Datenmodell mit RLS verwendet, wie im Tutorial [Dynamische Sicherheit auf Zeilenebene mit dem tabellarischen Modell von Analysis Services](desktop-tutorial-row-level-security-onprem-ssas-tabular.md) beschrieben. In dieser Situation muss Power BI für jede Kachel und jeden Benutzer, der jemals das Dashboard aufgerufen hat, einen Cache verwalten und aktualisieren. Es ist nicht ungewöhnlich, dass der Kachelaktualisierungsteil einer solchen Datenaktualisierung die Zeit, die benötigt wird, um die Daten von der Quelle abzurufen, bei weitem übersteigt. Weitere Details zur Kachelaktualisierung finden Sie unter [Problembehandlung für Kachelfehler](refresh-troubleshooting-tile-errors.md).

#### <a name="refresh-of-report-visuals"></a>Aktualisieren von visuellen Berichtselementen

Dieser Aktualisierungsprozess ist weniger wichtig, da er nur für Liveverbindungen mit Analysis Services relevant ist. Für diese Verbindungen speichert Power BI den letzten Zustand der visuellen Berichtselemente zwischen, sodass Power BI beim erneuten Betrachten des Berichts nicht das tabellarische Modell von Analysis Services abfragen muss. Wenn Sie mit dem Bericht interagieren, z.B. durch Ändern eines Berichtsfilters, fragt Power BI das tabellarische Modell ab und aktualisiert die visuellen Berichtselemente automatisch. Wenn Sie den Verdacht haben, dass ein Bericht veraltete Daten anzeigt, können Sie auch die Schaltfläche „Aktualisieren“ des Berichts auswählen, um eine Aktualisierung aller visuellen Berichtselemente auszulösen, wie der folgende Screenshot veranschaulicht.

![Aktualisieren visueller Berichtselemente](media/refresh-data/refresh-report-visuals.png)

## <a name="review-data-infrastructure-dependencies"></a>Überprüfen von Infrastrukturabhängigkeiten

Unabhängig von den Speichermodi kann keine Datenaktualisierung erfolgreich sein, wenn die zugrunde liegenden Datenquellen nicht zugänglich sind. Die drei wichtigsten Datenzugriffsszenarien sind:

- Ein Dataset verwendet lokale Datenquellen
- Ein Dataset verwendet Datenquellen in der Cloud
- Ein Dataset verwendet sowohl Daten aus lokalen als auch Cloudquellen

### <a name="connecting-to-on-premises-data-sources"></a>Herstellen der Verbindung mit lokalen Datenquellen

Wenn Ihr Dataset eine Datenquelle verwendet, auf die Power BI nicht über eine direkte Netzwerkverbindung zugreifen kann, müssen Sie eine Gatewayverbindung für dieses Dataset konfigurieren, bevor Sie einen Aktualisierungszeitplan aktivieren oder eine bedarfsgesteuerte Datenaktualisierung durchführen können. Weitere Informationen zu Datengateways und deren Funktionsweise finden Sie unter [Was sind lokale Datengateways?](service-gateway-onprem.md).

Sie haben folgende Optionen:

- Auswahl eines Enterprisedatengateways mit der erforderlichen Datenquellendefinition
- Bereitstellen eines persönlichen Datengateways

> [!NOTE]
> Eine Liste der Datenquellentypen, die ein Datengateway erfordern, finden Sie im Artikel [Verwalten der Datenquelle – Import/Geplante Aktualisierung](service-gateway-enterprise-manage-scheduled-refresh.md).

#### <a name="using-an-enterprise-data-gateway"></a>Verwenden eines Enterprisedatengateways

Microsoft empfiehlt, anstelle eines persönlichen Gateways ein Enterprisedatengateway zu verwenden, um ein Dataset mit einer lokalen Datenquelle zu verbinden. Stellen Sie sicher, dass das Gateway ordnungsgemäß konfiguriert ist, was bedeutet, dass das Gateway über die neuesten Updates und alle erforderlichen Datenquellendefinitionen verfügt. Eine Datenquellendefinition stellt Power BI die Verbindungsinformationen für eine bestimmte Quelle zur Verfügung, einschließlich Verbindungsendpunkten, Authentifizierungsmodus und Anmeldeinformationen. Weitere Informationen zum Verwalten von Datenquellen auf einem Gateway finden Sie unter [Verwalten der Datenquelle – Import/Geplante Aktualisierung](service-gateway-enterprise-manage-scheduled-refresh.md).

Das Herstellen einer Verbindung eines Datasets mit einem Enterprisegateway ist relativ unkompliziert, wenn Sie ein Gatewayadministrator sind. Mit Administratorberechtigungen können Sie das Gateway sofort aktualisieren und ggf. fehlende Datenquellen hinzufügen. In der Tat können Sie eine fehlende Datenquelle Ihrem Gateway direkt auf der Seite mit den Dataseteinstellungen hinzufügen. Erweitern Sie die Umschaltfläche, um die Datenquellen anzuzeigen, und wählen Sie den Link **Zu Gateway hinzufügen** aus, wie im folgenden Screenshot gezeigt. Wenn Sie kein Gatewayadministrator sind, müssen Sie sich an einen Gatewayadministrator wenden, um die erforderliche Datenquellendefinition hinzuzufügen.

> [!NOTE]
> Nur Gatewayadministratoren können Datenquellen zu Gateways hinzufügen. Stellen Sie auch sicher, dass Ihr Gatewayadministrator Ihr Benutzerkonto zur Liste der Benutzer mit Berechtigungen für die Verwendung der Datenquelle hinzufügt. Auf der Seite mit Dataseteinstellungen können Sie nur ein Enterprise-Gateway mit einer entsprechenden Datenquelle verwenden, für die Sie über Berechtigungen verfügen.

![Zu Gateway hinzufügen](media/refresh-data/add-to-gateway.png)

Achten Sie darauf, dass Sie Ihrer Datenquelle die richtige Datenquellendefinition zuordnen. Wie Sie im obigen Screenshot sehen, können Gatewayadministratoren mehrere Definitionen für ein Gateway erstellen, das mit derselben Datenquelle verbunden ist, jeweils mit anderen Anmeldeinformation. Im gezeigten Beispiel würde ein Datasetbesitzer in der Vertriebsabteilung z. B. die Datenquellendefinition AdventureWorksProducts-Sales auswählen, und ein Datasetbesitzer in der Supportabteilung würde das Dataset der Datenquellendefinition AdventureWorksProducts-Support zuordnen. Wenn die Namen der Datenquellendefinitionen nicht intuitiv sind, wenden Sie sich an den Gatewayadministrator, um herauszufinden, welche Definition Sie wählen sollten.

> [!NOTE]
> Ein Dataset kann nur eine einzelne Gatewayverbindung verwenden. D.h., es ist nicht möglich, über mehrere Gatewayverbindungen auf lokale Datenquellen zuzugreifen. Daher müssen Sie alle erforderlichen Datenquellendefinitionen dem gleichen Gateway hinzufügen.

#### <a name="deploying-a-personal-data-gateway"></a>Bereitstellen eines persönlichen Datengateways

Wenn Sie keinen Zugriff auf ein Enterprisedatengateway haben und die einzige Person sind, die Datasets verwaltet, sodass Sie keine Datenquellen mit anderen teilen müssen, können Sie ein Datengateway im persönlichen Modus bereitstellen. Wählen Sie im Abschnitt **Gatewayverbindung** unter **Sie haben keine persönlichen Gateways installiert** die Option **Jetzt installieren** aus. Das persönliche Datengateway hat mehrere Einschränkungen, wie in [Lokales Datengateway (persönlicher Modus)](service-gateway-personal-mode.md) dokumentiert.

Im Gegensatz zu einem Enterprisedatengateway müssen Sie einem persönlichen Gateway keine Datenquellendefinitionen hinzufügen. Verwalten Sie stattdessen die Datenquellenkonfiguration mithilfe des Abschnitts **Datenquellen-Anmeldeinformationen** in den Dataseteinstellungen, wie im folgenden Screenshot veranschaulicht.

![Konfigurieren von Datenquellen-Anmeldeinformationen für ein Gateway](media/refresh-data/configure-data-source-credentials-gateway.png)

> [!NOTE]
> Das persönliche Datengateway unterstützt keine Datasets im DirectQuery-/LiveConnect-Modus. Auf der Seite mit den Dataseteinstellungen werden Sie möglicherweise aufgefordert, es zu installieren, aber wenn Sie nur ein persönliches Gateway haben, können Sie keine Gatewayverbindung konfigurieren. Stellen Sie sicher, dass Sie über ein Enterprisedatengateway zur Unterstützung dieser Typen von Datasets verfügen.

### <a name="accessing-cloud-data-sources"></a>Zugriff auf Clouddatenquellen

Datasets, die Clouddatenquellen wie z.B. Azure SQL-Datenbank verwenden, erfordern kein Datengateway, wenn Power BI eine direkte Netzwerkverbindung mit der Quelle herstellen kann. Dementsprechend können Sie die Konfiguration dieser Datenquellen verwalten, indem Sie den Abschnitt **Datenquellen-Anmeldeinformationen** in den Dataseteinstellungen verwenden. Wie der folgende Screenshot zeigt, müssen Sie keine Gatewayverbindung konfigurieren.

![Konfigurieren von Datenquellen-Anmeldeinformationen ohne Gateway](media/refresh-data/configure-data-source-credentials.png)

### <a name="accessing-on-premises-and-cloud-sources-in-the-same-source-query"></a>Zugreifen auf lokale und Cloudquellen in der gleichen Quellabfrage

Ein Dataset kann Daten aus mehreren Quellen abrufen und diese Quellen können lokal sein oder sich in der Cloud befinden. Wie bereits erwähnt, kann ein Dataset nur eine einzelne Gatewayverbindung verwenden. Während Clouddatenquellen nicht unbedingt ein Gateway benötigen, ist ein Gateway erforderlich, wenn ein Dataset in einer einzigen Mashupabfrage sowohl mit lokalen als auch mit Clouddatenquellen eine Verbindung herstellt. In diesem Szenario muss Power BI für die Clouddatenquellen ebenfalls ein Gateway verwenden. Das folgende Diagramm veranschaulicht, wie solch ein Dataset auf seine Datenquellen zugreift.

![Cloud- und lokale Datenquellen](media/refresh-data/cloud-on-premises-data-sources-diagram.png)

> [!NOTE]
> Wenn ein Dataset separate Mashupabfragen verwendet, um eine Verbindung mit lokalen und Cloudquellen herzustellen, verwendet Power BI eine Gatewayverbindung, um die lokalen Quellen zu erreichen, und eine direkte Netzwerkverbindung mit den Cloudquellen. Wenn eine Mashupabfrage Daten aus lokalen und Cloudquellen zusammenführt oder anhängt, wechselt Power BI auch für die Cloudquellen zur Gateway-Verbindung.

Power BI-Datasets sind beim Zugriff auf Quelldaten und deren Abruf von Power Query abhängig. Die folgende Mashupauflistung zeigt ein einfaches Beispiel einer Abfrage, die Daten aus einer lokalen Quelle und einer Cloudquelle zusammenführt.

```
Let

    OnPremSource = Sql.Database("on-premises-db", "AdventureWorks"),

    CloudSource = Sql.Databases("cloudsql.database.windows.net", "AdventureWorks"),

    TableData1 = OnPremSource{[Schema="Sales",Item="Customer"]}[Data],

    TableData2 = CloudSource {[Schema="Sales",Item="Customer"]}[Data],

    MergedData = Table.NestedJoin(TableData1, {"BusinessEntityID"}, TableData2, {"BusinessEntityID"}, "MergedData", JoinKind.Inner)

in

    MergedData
```

Es gibt zwei Möglichkeiten, ein Datengateway zur Unterstützung des Zusammenführens oder Anfügens von Daten aus lokalen und Cloudqellen zu konfigurieren:

- Fügen Sie dem Datengateway zusätzlich zu den lokalen Datenquellen eine Datenquellendefinition für die Cloudquelle hinzu.
- Aktivieren Sie das Kontrollkästchen **Aktualisierung der Clouddatenquellen des Benutzers über diesen Gatewaycluster zulassen**.

![Aktualisieren über Gatewaycluster](media/refresh-data/refresh-gateway-cluster.png)

Wenn Sie das Kontrollkästchen **Allow user's cloud data sources to refresh through this gateway cluster in the gateway configuration** (Aktualisierung der Clouddatenquellen des Benutzers über diesen Gatewaycluster in der Gatewaykonfiguration zulassen) wie im obigen Screenshot aktivieren, kann Power BI die Konfiguration verwenden, die der Benutzer unter **Datenquellen-Anmeldeinformationen** in den Dataseteinstellungen für die Cloudquelle definiert hat. Dies kann dazu beitragen, den Aufwand für die Gatewaykonfiguration zu reduzieren. Wenn Sie hingegen eine größere Kontrolle über die Verbindungen haben möchten, die Ihr Gateway herstellt, sollten Sie dieses Kontrollkästchen nicht aktivieren. In diesem Fall müssen Sie Ihrem Gateway für jede Cloudquelle, die Sie unterstützen möchten, eine explizite Datenquellendefinition hinzufügen. Sie können auch das Kontrollkästchen aktivieren und einem Gateway explizite Datenquellendefinitionen für Ihre Cloudquellen hinzufügen. In diesem Fall verwendet das Gateway die Datenquellendefinitionen für alle übereinstimmenden Quellen.

### <a name="configuring-query-parameters"></a>Konfigurieren der Abfrageparameter

Die Mashup oder M-Abfragen, die Sie mithilfe von Power Query erstellen, können in der Komplexität von trivialen Schritten bis zu parametrisierten Konstrukten variieren. Die folgende Auflistung enthält eine kleine Beispielmashupabfrage, die zwei Parameter namens _SchemaName_ und _TableName_ verwendet, um auf eine bestimmte Tabelle in einer AdventureWorks-Datenbank zuzugreifen.

```
let

    Source = Sql.Database("SqlServer01", "AdventureWorks"),

    TableData = Source{[Schema=SchemaName,Item=TableName]}[Data]

in

    TableData
```

> [!NOTE]
> Abfrageparameter werden nur für Datasets im Import-Modus unterstützt. Der DirectQuery-/LiveConnect-Modus unterstützt keine Abfrageparameterdefinitionen.

Um sicherzustellen, dass ein parametrisiertes Dataset auf die richtigen Daten zugreift, müssen Sie die Mashupabfrageparameter in den Dataseteinstellungen konfigurieren. Sie können die Parameter auch programmgesteuert mithilfe der [Power BI-REST-API](/rest/api/power-bi/datasets/updateparametersingroup) aktualisieren. Der folgende Screenshot zeigt die Benutzeroberfläche zum Konfigurieren der Abfrageparameter für ein Dataset, das die oben genannte Mashupabfrage verwendet.

![Konfigurieren der Abfrageparameter](media/refresh-data/configure-query-parameters.png)

> [!NOTE]
> Power BI unterstützt derzeit keine parametrisierten Datenquellendefinitionen, auch bekannt als dynamische Datenquellen. Beispielsweise können Sie die Datenzugriffsfunktion „Sql.Database("SqlServer01", "AdventureWorks")“ nicht parametrisieren. Wenn Ihr Dataset auf dynamischen Datenquellen basiert, teilt Ihnen Power BI das Erkennen unbekannter oder nicht unterstützter Datenquellen mit. Sie müssen die Parameter in Ihren Datenzugriffsfunktionen durch statische Werte ersetzen, wenn Sie möchten, dass Power BI die Datenquellen identifizieren und eine Verbindung mit ihnen herstellen kann. Weitere Informationen finden Sie unter [Problembehandlung bei nicht unterstützter Datenquelle für die Aktualisierung](service-admin-troubleshoot-unsupported-data-source-for-refresh.md).

## <a name="configure-scheduled-refresh"></a>Konfigurieren von geplanten Aktualisierungen

Das Einrichten der Konnektivität zwischen Power BI und Ihren Datenquellen ist bei weitem die anspruchsvollste Aufgabe beim Konfigurieren einer Datenaktualisierung. Die restlichen Schritte sind relativ einfach und beinhalten das Festlegen des Aktualisierungszeitplans und das Aktivieren von Benachrichtigungen über Aktualisierungsfehler. Schrittweise Anweisungen finden Sie in der Schrittanleitung [Konfigurieren geplanter Aktualisierungen](refresh-scheduled-refresh.md).

### <a name="setting-a-refresh-schedule"></a>Festlegen eines Aktualisierungszeitplans

In dem Bereich **geplante Aktualisierung** definieren Sie das Aktualisierungsintervall und Aktualisierungszeitfenster für ein Dataset. Wie bereits erwähnt, können Sie bis zu acht Zeitfenster täglich konfigurieren, wenn sich Ihr Dataset auf gemeinsam genutzter Kapazität befindet, oder 48 Zeitfenster in Power BI Premium. Der folgende Screenshot zeigt einen Aktualisierungszeitplan im Zwölf-Stunden-Intervall.

![Konfigurieren von geplanten Aktualisierungen](media/refresh-data/configure-scheduled-refresh.png)

Nachdem Sie einen Aktualisierungszeitplan konfiguriert haben, werden Sie auf der Seite mit den Dataseteinstellungen über die nächste Aktualisierungszeit informiert, wie im obigen Screenshot dargestellt. Wenn Sie die Daten früher aktualisieren möchten, z.B. um Ihr Gateway und Ihre Datenquellenkonfiguration zu testen, führen Sie eine bedarfsgesteuerte Aktualisierung durch, indem Sie die Option **Jetzt aktualisieren** im Datasetmenü im Navigationsbereich verwenden. Bedarfsgesteuerte Aktualisierungen wirken sich nicht auf den nächsten geplanten Aktualisierungszeitpunkt aus.

Beachten Sie auch, dass die konfigurierte Aktualisierungszeit möglicherweise nicht genau der Zeitpunkt ist, zu dem Power BI den nächsten geplanten Prozess startet. Power BI startet geplante Aktualisierungen auf bestmögliche Weise. Das Ziel ist, die Aktualisierung innerhalb von 15 Minuten des geplanten Zeitfensters zu starten, aber es kann zu einer Verzögerung von bis zu einer Stunde kommen, wenn der Dienst die benötigten Ressourcen nicht früher zuweisen kann.

> [!NOTE]
> Power BI deaktiviert Ihren Aktualisierungszeitplan nach vier aufeinander folgenden Fehlern oder wenn der Dienst einen nicht behebbaren Fehler erkennt, der ein Konfigurationsupdate erfordert, wie beispielsweise ungültige oder abgelaufene Anmeldeinformationen. Es ist nicht möglich, den Schwellenwert von aufeinander folgenden Fehlern zu ändern.

### <a name="getting-refresh-failure-notifications"></a>Abrufen von Benachrichtigungen bei Aktualisierungsfehlern

Standardmäßig sendet Power BI Benachrichtigungen über Aktualisierungsfehler per E-Mail an den Datasetbesitzer, sodass der Besitzer rechtzeitig handeln kann, wenn Aktualisierungsprobleme auftreten. Power BI sendet Ihnen auch eine Benachrichtigung, wenn der Dienst Ihren Zeitplan aufgrund aufeinander folgender Fehler deaktiviert. Microsoft empfiehlt Ihnen, das Kontrollkästchen **Benachrichtigungs-E-Mails zu Aktualisierungsfehlern an mich senden** aktiviert zu lassen.

Außerdem empfiehlt es sich, mithilfe des Textfelds **Email these users when the refresh fails** (Diese Benutzer bei Aktualisierungsfehlern per E-Mail benachrichtigen) weitere Empfänger anzugeben. Zusätzlich zum Besitzer des Datasets erhalten auch die angegebenen Empfänger Benachrichtigungen über Aktualisierungsfehler. Dabei kann es sich um einen Kollegen handeln, der während Ihres Urlaubs Ihre Datasets verwaltet. Es kann sich auch um den E-Mail-Alias Ihres Supportteams handeln, das sich für Ihre Abteilung oder Organisation um Probleme bei der Aktualisierung kümmert. Das Senden von Benachrichtigungen bezüglich Aktualisierungsfehler an den Besitzer des Datasets und an weitere Personen hilft dabei, dass Probleme rechtzeitig bemerkt und behoben werden können.

Beachten Sie, dass Power BI Benachrichtigungen nicht nur zu Aktualisierungsfehlern sendet, sondern auch, wenn der Dienst eine geplante Aktualisierung aufgrund von Inaktivität stoppt. Wenn zwei Monate lang kein Benutzer ein auf dem Dataset basierendes Dashboard oder einen Bericht aufgerufen hat, betrachtet Power BI das Dataset als inaktiv. In dieser Situation sendet Power BI eine E-Mail an den Datasetbesitzer, um mitzuteilen, dass der Dienst den Aktualisierungszeitplan für das Dataset angehalten hat. Der folgende Screenshot enthält ein Beispiel für eine solche Benachrichtigung.

![E-Mail für angehaltene Aktualisierung](media/refresh-data/email-paused-refresh.png)

Um die geplante Aktualisierung fortzusetzen, rufen Sie einen Bericht oder ein Dashboard auf, der bzw. das mit diesem Dataset erstellt wurde, oder aktualisieren Sie das Dataset manuell mit der Option **Jetzt aktualisieren**.

### <a name="checking-refresh-status-and-history"></a>Überprüfung von Aktualisierungsstatus und Verlauf

Zusätzlich zu den Fehlerbenachrichtigungen sollten Sie Ihre Datasets in regelmäßigen Abständen auf Aktualisierungsfehler überprüfen. Eine schnelle Möglichkeit ist die Anzeige der Liste der Datasets in einem Arbeitsbereich. Für Datasets mit Fehlern wird ein kleines Warnungssymbol angezeigt. Wählen Sie das Warnungssymbol aus, um zusätzliche Informationen zu erhalten, wie im folgenden Screenshot dargestellt. Weitere Informationen zur Problembehandlung spezifischer Aktualisierungsfehler finden Sie unter [Problembehandlung für Aktualisierungsszenarios](refresh-troubleshooting-refresh-scenarios.md).

![Aktualisierungsstatuswarnung](media/refresh-data/refresh-status-warning.png)

Das Warnungssymbol dient dazu, aktuelle Probleme mit dem Dataset anzuzeigen, aber es ist auch eine gute Idee, den Aktualisierungsverlauf gelegentlich zu überprüfen. Wie der Name schon sagt, ermöglicht Ihnen der Aktualisierungsverlauf, den Erfolgs- oder Fehlerstatus vergangener Synchronisierungszyklen zu überprüfen. So könnte beispielsweise ein Gatewayadministrator einen abgelaufenen Satz von Datenbankanmeldeinformationen aktualisiert haben. Wie Sie im folgenden Screenshot sehen können, zeigt der Aktualisierungsverlauf an, wann eine betroffene Aktualisierung wieder funktioniert hat.

![Meldungen zum Aktualisierungsverlauf](media/refresh-data/refresh-history-messages.png)

> [!NOTE]
> Sie finden einen Link zur Anzeige des Aktualisierungsverlaufs in den Dataseteinstellungen. Sie können den Aktualisierungsverlauf auch programmgesteuert mithilfe der [Power BI-REST-API](/rest/api/power-bi/datasets/getrefreshhistoryingroup) abrufen. Indem Sie eine benutzerdefinierte Lösung verwenden, können Sie den Aktualisierungsverlauf von mehreren Datasets zentral überwachen.

## <a name="automatic-page-refresh"></a>Automatische Seitenaktualisierung

Die automatische Seitenaktualisierung funktioniert auf Berichtsseitenebene und ermöglicht Berichtsautoren, ein Aktualisierungsintervall für Visuals auf einer Seite festzulegen, das nur aktiv ist, wenn die Seite genutzt wird. Die automatische Seitenaktualisierung ist nur für DirectQuery-Datenquellen verfügbar. Das mindestens erforderliche Aktualisierungsintervall hängt davon ab, in welchem Typ von Arbeitsbereich der Bericht veröffentlicht wird und welche Administratoreinstellungen für Premium-Arbeitsbereiche und [eingebettete Arbeitsbereiche](developer/embedded/embedding.md) gelten.

Weitere Informationen zur automatischen Seitenaktualisierung finden Sie im Artikel [Automatische Seitenaktualisierung](desktop-automatic-page-refresh.md).

## <a name="best-practices"></a>Bewährte Methoden

Die regelmäßige Überprüfung des Aktualisierungsverlaufs Ihrer Datasets ist eine der wichtigsten Best Practices, die Sie anwenden können, um sicherzustellen, dass Ihre Berichte und Dashboards aktuelle Daten verwenden. Wenn Sie Probleme feststellen, beheben Sie sie umgehend, und informieren Sie gegebenenfalls die Datenquellenbesitzer und Gatewayadministratoren.

Beachten Sie außerdem die folgenden Empfehlungen, um zuverlässige Datenaktualisierungsprozesse für Ihre Datasets einzurichten und aufrechtzuerhalten:

- Planen Sie Ihre Aktualisierungen für Zeiten mit geringerer Auslastung ein, insbesondere, wenn Sie Power BI Premium für Ihre Datasets verwenden. Wenn Sie die Aktualisierungszyklen für Ihre Datasets auf ein breiteres Zeitfenster verteilen, können Sie dazu beitragen, Spitzen zu vermeiden, die sonst die verfügbaren Ressourcen überfordern könnten. Verzögerungen beim Start eines Aktualisierungszyklus sind ein Indikator für die Überlastung der Ressourcen. Wenn eine Premium-Kapazität vollständig ausgeschöpft ist, könnte Power BI sogar einen Aktualisierungszyklus überspringen.
- Beachten Sie die Aktualisierungsgrenzwerte. Wenn sich die Quelldaten häufig ändern oder das Datenvolumen beträchtlich ist, sollten Sie den DirectQuery-/LiveConnect-Modus anstelle des Import-Modus verwenden, wenn die erhöhte Last an der Quelle und die Auswirkungen auf die Abfrageleistung akzeptabel sind. Vermeiden Sie die ständige Aktualisierung eines Import-Modus-Datasets. Der DirectQuery-/LiveConnect-Modus hat jedoch mehrere Einschränkungen, wie z.B. ein Limit von einer Million Zeilen für die Rückgabe von Daten und ein Reaktionszeitlimit von 225 Sekunden für die Ausführung von Abfragen, wie in [Verwenden von DirectQuery in Power BI Desktop](desktop-use-directquery.md) dokumentiert. Diese Einschränkungen könnten dazu führen, dass Sie dennoch den Import-Modus verwenden müssen. Erwägen Sie bei sehr großen Datenvolumen die Verwendung von [Aggregationen in Power BI Desktop (Vorschauversion)](desktop-aggregations.md).
- Stellen Sie sicher, dass Ihre Datasetaktualisierungszeit nicht die maximale Aktualisierungsdauer überschreitet. Verwenden Sie Power BI Desktop, um die Aktualisierungsdauer zu überprüfen. Wenn es mehr als 2 Stunden dauert, sollten Sie das Dataset zu Power BI Premium verschieben. Ihr Dataset ist auf gemeinsam genutzter Kapazität möglicherweise nicht aktualisierbar. Erwägen Sie auch für Datasets, die größer als 1GB sind, oder deren Aktualisierung mehrere Stunden dauert, die Verwendung der [inkrementellen Aktualisierung in Power BI Premium](service-premium-incremental-refresh.md).
- Optimieren Sie Ihre Datasets so, dass sie nur die Tabellen und Spalten enthalten, die in Ihren Berichten und Dashboards verwendet werden. Optimieren Sie Ihre Mashupabfragen, und vermeiden Sie nach Möglichkeit dynamische Datenquellendefinitionen und aufwändige DAX-Berechnungen. Vermeiden Sie insbesondere DAX-Funktionen, die jede Zeile einer Tabelle testen, wegen des hohen Speicherverbrauchs und des Verarbeitungsaufwands.
- Wenden Sie die gleichen Datenschutzeinstellungen wie in Power BI Desktop an, um sicherzustellen, dass Power BI effiziente Quellabfragen generieren kann. Beachten Sie, dass Power BI Desktop keine Datenschutzeinstellungen veröffentlicht. Sie müssen die Einstellungen in den Datenquellendefinitionen nach dem Veröffentlichen Ihres Datasets manuell erneut anwenden.
- Begrenzen Sie die Anzahl der visuellen Elemente auf Ihren Dashboards, insbesondere wenn Sie [Sicherheit auf Zeilenebene (Row-Level Security; RLS) mit Power BI](service-admin-rls.md) verwenden. Wie bereits zuvor in diesem Artikel erläutert, kann eine übermäßige Anzahl von Dashboardkacheln die Aktualisierungsdauer erheblich erhöhen.
- Verwenden Sie eine zuverlässige Enterprisedatengateway-Bereitstellung, um eine Verbindung Ihrer Datasets mit lokalen Datenquellen herzustellen. Wenn Sie gatewaybezogene Fehler bei der Aktualisierung feststellen, wenn das Gateway z.B. nicht verfügbar oder überlastet ist, besprechen Sie dies mit Gatewayadministratoren, um entweder einem bestehenden Cluster zusätzliche Gateways hinzuzufügen oder einen neuen Cluster bereitzustellen (zentral hochskalieren oder horizontal hochskalieren).
- Verwenden Sie separate Datengateways für Importdatasets und DirectQuery-/LiveConnect-Datasets, damit die Datenimporte während der geplanten Aktualisierung nicht die Leistung von Berichten und Dashboards auf DirectQuery-/LiveConnect-Datasets beeinträchtigen, die bei jeder Benutzerinteraktion die Datenquellen abfragen.
- Stellen Sie sicher, dass Power BI Benachrichtigungen über Aktualisierungsfehler an Ihre Mailbox senden kann. Spamfilter könnten die E-Mail-Nachrichten blockieren oder in einen separaten Ordner verschieben, in dem Sie sie möglicherweise nicht sofort bemerken.


## <a name="next-steps"></a>Nächste Schritte

[Konfigurieren geplanter Aktualisierungen](refresh-scheduled-refresh.md)  
[Tools zur Problembehandlung von Aktualisierungsproblemen](service-gateway-onprem-tshoot.md)  
[Problembehandlung bei Aktualisierungsszenarios](refresh-troubleshooting-refresh-scenarios.md)  

Weitere Fragen? [Stellen Sie Ihre Frage in der Power BI-Community.](https://community.powerbi.com/)
