---
title: Was ist Microsoft Power BI Premium?
description: Power BI Premium bietet dedizierte Kapazitäten für Ihre Organisation, sodass Sie von verlässlicherer Leistung und größeren Datenmengen profitieren, ohne Benutzerlizenzen kaufen zu müssen.
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 03/26/2020
ms.custom: seodec18
LocalizationGroup: Premium
ms.openlocfilehash: f53f7a1e51ce1cb17c337569ba770ac2b5643d19
ms.sourcegitcommit: 8267a7383d6506dae42f87e4f4a2362b875b2911
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/27/2020
ms.locfileid: "80329668"
---
# <a name="what-is-power-bi-premium"></a>Was ist Power BI Premium?

Mit Power BI Premium erhalten Sie dedizierte und erweiterte Ressourcen für Ihre Organisation, sodass Benutzer in Ihrer Organisation den Power BI-Dienst mit besserer Leistung und Reaktionsfähigkeit nutzen können. Beispielsweise haben Sie und die Benutzer Ihrer Organisation mit einem Power BI Premium-Abonnement Zugriff auf Folgendes:

> [!div class="checklist"]
> * Größere Skalierung und Leistung
> * Flexibilität bei der Lizenzierung nach Kapazität
> * Vereinheitlichung von Self-Service- und Unternehmens-BI
> * Erweitern der lokalen BI mit Power BI-Berichtsserver
> * Unterstützung für Datenresidenz nach Region (Multi-Geo)
> * Teilen von Daten mit beliebigen Personen ohne Erwerb einer Benutzerlizenz


![Verwaltungsportal](media/service-premium-what-is/premium-admin-portal.png) 

Dieser Artikel stellt wichtige Funktionen in Power BI Premium vor. Wo es erforderlich ist, bieten Links zu weiteren Artikeln ausführlichere Informationen. Weitere Informationen zu Power BI Pro und Power BI Premium finden Sie auf der Website [Power BI – Preise](https://powerbi.microsoft.com/pricing/) im Abschnitt _Vergleich der Power BI-Funktionen_.

## <a name="subscriptions-and-licensing"></a>Abonnements und Lizenzierung

Power BI Premium ist ein Office 365-Abonnement auf Mandantenebene, das in zwei SKU-Familien (Stock Keeping Unit) erhältlich ist:

- **P**-SKUs (P1–P5) für Einbettungs- und Unternehmensfunktionen, die eine monatliche oder jährliche Verpflichtung erfordern, monatlich abgerechnet werden und eine Lizenz zur lokalen Installation von Power BI-Berichtsserver beinhalten.

- **EM**-SKUs (EM1–EM3) zum Einbetten für _Organisationen_, die eine jährliche Verpflichtung erfordern und monatlich abgerechnet werden. Die EM1- und EM2-SKUs sind nur über Volumenlizenzierungspläne erhältlich. Sie können sie nicht direkt erwerben.

Alternativ dazu können Sie auch ein **Power BI Embedded**-Abonnement in Azure erwerben. Es gibt eine einzige **A**-SKU-Familie (A1–A6), die keine Verpflichtung erfordert und pro Stunde abgerechnet wird. Diese wird für Power BI-Bezeichnungen in Anwendungen, Portalen und Websites oder als Möglichkeit zum Testen von P- oder EM-Funktionen genutzt. Alle SKUs bieten V-Kerne zum Erstellen von Kapazitäten, die EM-SKUs sind jedoch für Einbettung im kleineren Maßstab eingeschränkt. EM1-, EM2-, A1- und A2-SKUs mit weniger als vier V-Kernen können nicht in dedizierter Infrastruktur ausgeführt werden.

Zwar liegt der Schwerpunkt dieses Artikels auf den P-SKUs, viel vom Beschriebenen ist jedoch auch für die A-SKUs relevant. Im Gegensatz zu den Premium-Abonnement-SKUs, erfordern Azure-SKUs keine zeitliche Verpflichtung und werden stundenweise abgerechnet. Sie bieten uneingeschränkte Elastizität, die zentrales Hochskalieren, Herunterskalieren, Anhalten, Fortsetzen und Löschen ermöglicht. 

Azure Power BI Embedded liegt weitgehend außerhalb der Reichweite dieses Artikels, ist aber im Abschnitt [Testansätze](service-premium-capacity-optimize.md#testing-approaches) des Artikels „Optimieren von Premium-Kapazitäten“ als praktische und wirtschaftliche Option zum Testen und Messen von Workloads beschrieben. Weitere Informationen zu Azure-SKUs finden Sie in der [Dokumentation zu Azure Power BI Embedded](https://azure.microsoft.com/services/power-bi-embedded/).

### <a name="purchasing"></a>Erwerb

Power BI-Premium-Abonnements werden von Administratoren im Microsoft 365 Admin Center gekauft. Genauer gesagt können nur globale Office 365-Administratoren oder Abrechnungsadministratoren SKUs erwerben. Beim Kauf erhält der Mandant eine entsprechende Anzahl V-Kerne zur Zuweisung zu Kapazitäten, was als *V-Kern-Pooling* bezeichnet wird. Beispielsweise erhält der Mandant durch den Erwerb einer P3-SKU 32 V-Kerne. Weitere Informationen finden Sie unter [How to purchase Power BI Premium (Erwerben von Power BI Premium)](service-admin-premium-purchase.md).

## <a name="dedicated-capacities"></a>Dedizierte Kapazitäten

Mit Power BI Premium erhalten Sie *dedizierte Kapazitäten*. Im Gegensatz zu einer gemeinsam genutzten Kapazität, bei der die Workloads auf gemeinsam mit anderen Kunden genutzten Computerressourcen ausgeführt werden, ist eine dedizierte Kapazität für die ausschließliche Verwendung durch eine Organisation bestimmt. Sie ist isoliert und verfügt über dedizierte Computeressourcen, die verlässliche und konsistente Leistung für die gehosteten Inhalte zur Verfügung stellt. Beachten Sie, dass folgende Ressourcen in gemeinsam genutzten Kapazitäten gespeichert werden, nicht in Ihrer dedizierten Kapazität:

* Excel-Arbeitsmappen (es sei denn, die Daten werden zuerst in Power BI Desktop importiert)
* [Pushdatasets](/rest/api/power-bi/pushdatasets)
* [Streamingdatasets](service-real-time-streaming.md#set-up-your-real-time-streaming-dataset-in-power-bi)

Arbeitsbereiche befinden sich innerhalb von Kapazitäten. Jeder Power BI-Benutzer verfügt über einen persönlichen Arbeitsbereich, der als **Mein Arbeitsbereich** bezeichnet wird. Zusätzliche Arbeitsbereiche, auch als **Arbeitsbereiche** bezeichnet, können erstellt werden, um die Zusammenarbeit zu ermöglichen. Standardmäßig werden Arbeitsbereiche, einschließlich persönlicher Arbeitsbereiche, in der gemeinsam genutzten Kapazität erstellt. Wenn Sie über Premium-Kapazitäten verfügen, können sowohl zu „Meine Arbeitsbereiche“ als auch zu Arbeitsbereichen Premium-Kapazitäten zugewiesen werden.

### <a name="capacity-nodes"></a>Kapazitätsknoten

Wie im Abschnitt [Abonnements und Lizenzierung](#subscriptions-and-licensing) beschrieben, gibt es zwei SKU-Familien bei Power BI Premium: **EM** und **P**. Alle Power BI Premium-SKUs sind als *Kapazitätsknoten* erhältlich, von denen jeder eine festgelegte Menge an Ressourcen in Form von Prozessor, Arbeitsspeicher und Speicherplatz darstellt. Über Ressourcen hinaus bestehen für jede SKU Grenzwerte im Betrieb hinsichtlich der Anzahl der DirectQuery- und Live Connection-Verbindungenpro Sekunde und der Anzahl der parallelen Modellaktualisierungen.

Die Verarbeitung erfolgt mithilfe einer festgelegten Anzahl V-Kerne, die zu gleichen Teilen zwischen Back-End und Front-End aufgeteilt werden.

**Back-End-V-Kerne** sind für die Power BI-Kernfunktionalität zuständig, einschließlich Abfrageverarbeitung, Cacheverwaltung, das Ausführen von R-Diensten, die Verarbeitung natürlicher Sprache (Q&A) und das serverseitige Rendern von Berichten und Bildern. Back-End-V-Kernen wird eine festgelegte Menge Arbeitsspeicher zugewiesen, der hauptsächlich zum Hosten von Modellen verwendet wird, die auch als aktive Datasets bezeichnet werden.

Die **Front-End-V-Kerne** sind für den Webdienst, die Verwaltung von Dashboard und Berichtsdokumenten, die Zugriffsrechteverwaltung, Zeitplanung, APIs, Uploads und Downloads und allgemein für alles zuständig, das mit der Benutzererfahrung zusammenhängt.

Der Speicherplatz ist auf **100 TB pro Kapazitätsknoten** festgelegt.

Die Ressourcen und Grenzwerte der einzelnen Premium-SKUs (und A-SKU jeweils gleicher Größe) sind in der folgenden Tabelle beschrieben:

| Kapazitätsknoten | Gesamtzahl an V-Kernen | Back-End-V-Kerne | RAM (GB) | Front-End-V-Kerne | DirectQuery/Live Connection (s) | Modell-Aktualisierungsparallelität |
| --- | --- | --- | --- | --- | --- | --- |
| EM1/A1 | 1 | 0,5 | 3 | 0,5 | 3,75 | 1 |
| EM2/A2 | 2 | 1 | 5 | 1 | 7,5 | 2 |
| EM3/A3 | 4 | 2 | 10 | 2 | 15 | 3 |
| P1/A4 | 8 | 4 | 25 | 4 | 30 | 6 |
| P2/A5 | 16 | 8 | 50 | 8 | 60 | 12 |
| P3/A6 | 32 | 16 | 100 | 16 | 120 | 24 |
| P4 | 64 | 32 | 200 | 32 | 240 | 48 |
| P5 | 128 | 64 | 400 | 64 | 480 | 96 |
| | | | | | | |

> [!NOTE]
> Die Verwendung einer einzelnen größeren SKU (z. B. eine P2-SKU) ist möglicherweise der Kombination mehrerer kleinerer SKUs (z. B. zwei P1-SKUs) vorzuziehen. Mit P2 können Sie z. B. größere Modelle verwenden und erzielen eine bessere Parallelität.

### <a name="capacity-workloads"></a>Kapazitätsworkloads

Kapazitätsworkloads sind Dienste, die Benutzern zur Verfügung gestellt werden. Standardmäßig unterstützen Premium- und Azure-Kapazitäten nur die Workload für die Ausführung von Power BI-Abfragen. Die Dataset-Workload kann nicht deaktiviert werden. Zusätzliche Workloads können für [KI (Cognitive Services)](https://powerbi.microsoft.com/blog/easy-access-to-ai-in-power-bi-preview/), [Dataflows](service-dataflows-overview.md#dataflow-capabilities-on-power-bi-premium) und [paginierte Berichte](paginated-reports/paginated-reports-save-to-power-bi-service.md) aktiviert werden. Diese Workloads werden nur in Premium-Abonnements unterstützt. 

Jede zusätzliche Workload ermöglicht das Konfigurieren des maximalen Arbeitsspeichers (als Prozentsatz des gesamten verfügbaren Arbeitsspeichers) für die Verwendung durch die Workload. Die Standardwerte für den maximalen Arbeitsspeicher werden nach SKU bestimmt. Sie können die verfügbaren Ressourcen Ihrer Kapazität maximieren, indem Sie diese zusätzlichen Workloads nur bei Bedarf aktivieren. Und Sie können die Arbeitsspeichereinstellungen erst ändern, wenn Sie bestimmt haben, dass die Standardeinstellungen Ihre Anforderungen an Kapazitätsressourcen nicht erfüllen. Workloads können von Kapazitätsadministratoren für eine Kapazität mithilfe von **Kapazitätseinstellungen** im [Verwaltungsportal](service-admin-portal.md) oder mithilfe der [Kapazitäts-REST-APIs](https://docs.microsoft.com/rest/api/power-bi/capacities) aktiviert und konfiguriert werden.  

![Aktivieren von Workloads](media/service-admin-premium-workloads/admin-portal-workloads.png)

Weitere Informationen finden Sie unter [Konfigurieren von Workloads in einer Premium-Kapazität](service-admin-premium-workloads.md). 

### <a name="how-capacities-function"></a>Funktiosweise von Kapazitäten

Der Power BI-Dienst nutzt die Kapazitätsressourcen jederzeit optimal, ohne die der Kapazität auferlegten Grenzwerte zu überschreiten.

Kapazitätsvorgänge werden entweder als *interaktiv* oder *im Hintergrund* klassifiziert. Zu den interaktiven Vorgängen gehören Renderinganforderungen und das Reagieren auf Benutzerinteraktionen (Filtern, Q&A-Abfragen usw.). Im Allgemeinen wird beim Abfragen von Importmodellen die Arbeitsspeicherressource stärker genutzt, während das Abfragen von DirectQuery- und Live Connection-Modellen CPU-intensiv ist. Zu den Hintergrundvorgängen gehören die Aktualisierung von Datenflüssen und Importmodellen sowie das Cachen von Dashboardabfragen.

Es ist wichtig zu verstehen, dass interaktive Vorgänge immer Vorrang vor Hintergrundvorgängen haben, um die bestmögliche Benutzererfahrung sicherzustellen. Wenn nicht ausreichend Ressourcen vorhanden sind, werden Hintergrundvorgänge einer Warteschlange hinzugefügt, um bei freiwerdenden Ressourcen verarbeitet zu werden. Hintergrundvorgänge, wie Datasetaktualisierungen, können vom Power BI-Dienst im Vorgang angehalten und einer Warteschlange hinzugefügt werden.

Importmodelle müssen vollständig in den Arbeitsspeicher geladen werden, damit sie abgefragt oder aktualisiert werden können. Der Power BI-Dienst verwaltet den Arbeitsspeicherverbrauch mithilfe hoch entwickelter Algorithmen, um die maximale Nutzung des verfügbaren Arbeitsspeichers sicherzustellen, was zu Überbuchung der Kapazität führen kann: Eine Kapazität kann zwar viele Importmodelle speichern (bis zu 100 TB pro Premium-Kapazität), wenn der kombinierte Datenträgerspeicher den unterstützten Arbeitsspeicher jedoch überschreitet (und zusätzlicher Arbeitsspeicher für Abfragen und Aktualisierungen benötigt wird), können sie nicht alle zugleich in den Arbeitsspeicher geladen werden.

Importmodelle werden aus diesem Grund nach Bedarf in den Arbeitsspeicher geladen und aus diesem entfernt. Ein Importmodell wird geladen, wenn es abgefragt wird (interaktiver Vorgang) und sich noch nicht im Arbeitsspeicher befindet, oder wenn es aktualisiert werden soll (Hintergrundvorgang).

Das Entfernen eines Modells aus dem Arbeitsspeicher wird als *Entfernung* bezeichnet. Dies ist ein Vorgang, den Power BI – je nach Größe der Modelle – schnell ausführen kann. Wenn die Kapazität keinen Engpass beim Arbeitsspeicher erlebt, werden Modelle einfach in den Arbeitsspeicher geladen und verbleiben dort. Wenn jedoch nicht genügend Arbeitsspeicher zum Laden eines Modells zur Verfügung steht, muss der Power BI-Dienst zuerst Arbeitsspeicher freigeben. Er gibt Arbeitsspeicher frei, indem er inaktive Modelle erkennt; dazu sucht er Modelle, die innerhalb der letzten drei Minuten \[[1](#endnote-1)\] nicht verwendet wurden, und entfernt diese dann. Wenn keine inaktiven Modelle zum Entfernen vorhanden sind, versucht der Power BI-Dienst, Modelle zu entfernen, die für Hintergrundoperationen geladen wurden. Als letztes Mittel lässt er nach 30 Sekunden erfolgloser Versuche \[[1](#endnote-1)\] den interaktiven Vorgang fehlschlagen. In diesem Fall wird der Berichtsbenutzer über den Fehlschlag informiert und gleichzeitig ermutigt, es in Kürze noch einmal zu versuchen. In einigen Fällen können Modelle aufgrund von Dienstvorgängen aus dem Arbeitsspeicher entladen werden.

Es muss unbedingt betont werden, dass die Entfernung von Datasets ein normales und erwartetes Verhalten darstellt. Es zielt darauf ab, die Speicherauslastung durch Laden und Entladen von Modellen zu maximieren, deren kombinierte Größe den verfügbaren Arbeitsspeicher überschreiten kann. Dies ist beabsichtigt und für Benutzer des Berichts transparent. Hohe Entfernungsraten bedeuten nicht zwangsläufig, dass die Kapazität unzureichend mit Ressourcen ausgestattet ist. Dies kann jedoch zu einem Problem werden, wenn die Reaktionsfähigkeit auf Abfragen oder Aktualisierungen aufgrund hoher Entfernungsraten leidet.

Aktualisierungen von Importmodellen sind immer speicherintensiv, da die Modelle in den Arbeitsspeicher geladen werden müssen. Weiterer Speicher ist für die Verarbeitung erforderlich. Eine vollständige Aktualisierung kann ungefähr doppelt so viel Arbeitsspeicher in Anspruch nehmen, wie für das Modell erforderlich ist. Dadurch wird sichergestellt, dass das Modell auch während der Verarbeitung abgefragt werden kann, da Abfragen an das vorhandene Modell gesendet werden, bis die Aktualisierung abgeschlossen ist und die Daten des neuen Modells verfügbar sind. Inkrementelle Aktualisierungen erfordern weniger Arbeitsspeicher und können schneller abgeschlossen werden und so den Druck auf Kapazitätsressourcen deutlich verringern. Aktualisierungen von Modellen können außerdem CPU-intensiv sein, insbesondere solche mit komplexen Power Query-Transformationen oder berechneten Tabellen/Spalten, die komplex sind oder auf umfangreichen Tabelle basieren.

Für Aktualisierungen muss das Modell wie für Abfragen in den Arbeitsspeicher geladen werden. Bei unzureichendem Arbeitsspeicher versucht der Power BI-Dienst, inaktive Modelle zu entfernen, und wenn das nicht möglich ist (weil alle Modelle aktiv sind), wird der Aktualisierungsauftrag in die Warteschlange eingestellt. Aktualisierungen sind in der Regel CPU-intensiv, sogar mehr als Abfragen. Aus diesem Grund bestehen Kapazitätsgrenzen für die Anzahl der gleichzeitigen Aktualisierungen, die auf das 1,5-fache der Anzahl der V-Kerne im Back-End festgelegt ist (aufgerundet). Bei zu vielen gleichzeitigen Aktualisierungen wird eine geplante Aktualisierung in die Warteschlange eingestellt. Wenn diese Situationen eintreten, benötigt die Aktualisierung mehr Zeit bis zum Abschluss. Für Aktualisierungen bei Bedarf, wie sie etwa durch Benutzeranforderung oder einen API-Aufruf ausgelöst werden, wird die Ausführung dreimal versucht \[[1](#endnote-1)\]. Wenn dann immer noch nicht genügend Ressourcen verfügbar sind, schlägt die Aktualisierung fehl.

Abschnittshinweise:   
<a name="endnote-1"></a>\[1\] Änderungen vorbehalten.

### <a name="regional-support"></a>Regionsunterstützung

Beim Erstellen einer neuen Kapazität können globale Office 365-Administratoren und Power BI-Dienstadministratoren angeben, wo Arbeitsbereiche, die der Kapazität zugewiesen werden, sich befinden sollen. Dies wird als **Multi-Geo** bezeichnet. Mithilfe von Multi-Geo können Organisationen Anforderungen an die Datenresidenz erfüllen, indem sie Inhalte in Rechenzentren in einer bestimmten Region bereitstellen, auch wenn es sich dabei um eine andere Region als die des Office 365-Abonnements handelt. Weitere Informationen finden Sie unter [Multi-Geo-Unterstützung für Power BI Premium](service-admin-premium-multi-geo.md).

### <a name="capacity-management"></a>Kapazitätsmanagement

Das Verwalten von Premium-Kapazitäten umfasst das Erstellen oder Löschen von Kapazitäten, das Zuweisen von Administratoren, das Zuweisen von Arbeitsbereichen, das Konfigurieren von Workloads, das Überwachen und das Vornehmen von Anpassungen zum Optimieren der Kapazitätsleistung. 

Globale Office 365-Administratoren und Power BI-Dienstadministratoren können Premium-Kapazitäten aus verfügbaren V-Kernen erstellen oder vorhandene Premium-Kapazitäten ändern. Wenn eine Kapazität erstellt wird, werden die Größe und die geografische Region der Kapazität angegeben, und es wird mindestens ein Kapazitätsadministrator zugewiesen. 

Die meisten Verwaltungsaufgaben beim Erstellen von Kapazitäten finden im [Verwaltungsportal](service-admin-portal.md) statt.

![Verwaltungsportal](media/service-premium-what-is/premium-admin-portal.png)

Kapazitätsadministratoren können der Kapazität Arbeitsbereiche zuweisen, Benutzerberechtigungen verwalten und weitere Administratoren zuweisen. Kapazitätsadministratoren können außerdem Workloads konfigurieren, wobei sie Arbeitsspeicherzuteilungen anpassen und gegebenenfalls eine Kapazität neu starten, um den Betrieb für den Fall einer Kapazitätsüberlastung zurückzusetzen.

![Verwaltungsportal](media/service-premium-what-is/premium-admin-portal-mgmt.png)

Kapazitätsadministratoren können außerdem sicherstellen, dass eine Kapazität reibungslos ausgeführt wird. Sie können den Kapazitätsstatus direkt im Verwaltungsportal oder mithilfe der Premium-Kapazitäts-Metrik-App überwachen.

Weitere Informationen zum Erstellen von Kapazitäten, Zuweisen von Administratoren und Zuweisen von Arbeitsbereichen finden Sie unter [Verwalten von Premium-Kapazitäten](service-premium-capacity-manage.md). Weitere Informationen zu Rollen finden Sie unter [Administratorrollen im Zusammenhang mit Power BI](service-admin-administering-power-bi-in-your-organization.md#administrator-roles-related-to-power-bi).

### <a name="monitoring"></a>Monitoring

Durch Überwachen von Premium-Kapazitäten erhalten Administratoren ein Verständnis der Leistung ihrer Kapazitäten. Kapazitäten können mithilfe des Verwaltungsportals und der [Power BI Premium-Kapazitäts-Metrik-App](https://app.powerbi.com/groups/me/getapps/services/capacitymetrics) überwacht werden.

Die Überwachung im Portal bietet einen schnellen Überblick mit allgemeinen Metriken, die den Mittelwert der platzierten Auslastungen und der von Ihrer Kapazität genutzten Ressourcen über die vergangenen sieben Tage ausweisen. 

![Verwaltungsportal](media/service-premium-what-is/premium-admin-portal-health.png)

Die **Power BI Premium-Kapazitäts-Metrik-App** stellt ausführliche Informationen zur Leistung Ihrer Kapazitäten bereit. Die App bietet ein allgemeines Dashboard und ausführlichere Berichte.

![Metrik-App-Dashboard](media/service-admin-premium-monitor-capacity/app-dashboard.png)

Sie können im Dashboard der App auf eine Metrikzelle klicken, um einen tiefgreifenden Bericht zu öffnen. In Berichten stehen tiefgreifende Metriken und Filterfunktionen zur Verfügung, mit denen Sie Drilldowns zu den wichtigsten Informationen ausführen können, die Sie benötigen, um eine reibungslose Ausführung Ihrer Kapazitäten zu gewährleisten.

![Regelmäßig auftretende Spitzen bei den Indikatoren der Abfragewartezeit weisen auf eine potenzielle CPU-Sättigung hin](media/service-premium-capacity-scenarios/peak-query-wait-times.png)

Weitere Informationen zum Überwachen von Kapazitäten finden Sie unter [Überwachen im Power BI-Verwaltungsportal](service-admin-premium-monitor-portal.md) und [Überwachen mit der Power BI Premium-Kapazitäts-Metrik-App](service-admin-premium-monitor-capacity.md).

### <a name="optimizing-capacities"></a>Optimieren von Kapazitäten

Die optimale Nutzung Ihrer Kapazitäten ist kritisch, um Benutzern die erforderliche Leistung und Ihnen das Erzielen des bestmöglichen Nutzens aus Ihrer Investition in Premium zuzusichern. Durch Überwachen von Schlüsselmetriken können Administratoren bestimmen, wie sich Engpässe optimal beheben lassen, und die erforderlichen Aktionen ausführen. Weitere Informationen finden Sie unter [Optimieren von Premium-Kapazitäten](service-premium-capacity-optimize.md) und [Premium-Kapazitätsszenarien](service-premium-capacity-scenarios.md).

### <a name="capacities-rest-apis"></a>Kapazitäten-REST-APIs

Die Power BI REST-APIs beinhalten eine Sammlung von [Kapazitäts-APIs](https://docs.microsoft.com/rest/api/power-bi/capacities). Mit den APIs können Administratoren viele Aspekte Ihrer Premium-Kapazitäten programmgesteuert verwalten, darunter das Aktivieren und Deaktivieren von Workloads, das Zuweisen von Arbeitsbereichen zu einer Kapazität usw.

## <a name="large-datasets"></a>Große Datasets

Je nach der gewählten SKU unterstützt Power BI Premium das Hochladen von PBIX-Modelldateien (Power BI Desktop) bis zu einer Größe von maximal **10 GB**. Wenn es geladen ist, kann das Modell anschließend in einem Arbeitsbereich veröffentlicht werden, der einer Premium-Kapazität zugewiesen ist. Das Dataset kann dann bis zu einer Größe von **12 GB** aktualisiert werden.

### <a name="size-considerations"></a>Dimensionierungsaspekte

Große Datasets können ressourcenintensiv sein. Für Datasets mit mehr als 1 GB sollten Sie mindestens eine P1-SKU verwenden. Sie können zwar große Datasets in Arbeitsbereichen veröffentlichen, die von A-SKUs (bis A3) gestützt sind, aber Sie können diese Modelle nicht aktualisieren.

In der folgenden Tabelle werden die empfohlenen SKUs zum Hochladen oder Veröffentlichen der PBIX-Datei im Power BI-Dienst angezeigt:

   |SKU  |PBIX-Größe   |
   |---------|---------|
   |P1    | < 3 GB        |
   |P2    | < 6 GB        |
   |P3, P4, P5    | bis zu 10 GB   |

Die A4-SKU für Power BI Embedded entspricht der P1-SKU, A5 entspricht P2 und A6 entspricht P3. Beim Veröffentlichen von großen Datasets in A- und EM-SKUs werden möglicherweise Fehler zurückgegeben, die sich nicht auf den Fehler zur Begrenzung der Modellgröße in der gemeinsam genutzten Kapazität beziehen. Aktualisierungsfehler bei großen Datasets in A- und EM-SKUs verweisen häufig auf Timeouts.

Wenn Sie [große Modelle](service-premium-large-models.md) für ein Dataset aktivieren, gelten die Größenbeschränkungen für PBIX-Dateien auch für das Hochladen oder Veröffentlichen von Dateien. Wenn Datasets eine Kombination aus inkrementellen Aktualisierungen und großen Modellen verwenden, können sie jedoch deutlich über diesen Grenzwerten liegen. Bei großen Modellen wird die Größe des Datasets nur durch den Power BI Premium-Kapazitätsumfang beschränkt.

Ihre PBIX-Dateien stellen Daten in einem *stark komprimierten Zustand* dar. Die Daten werden in den meisten Fällen beim Laden in den Speicher größer, ebenso wie anschließend bei jeder Datenaktualisierung.

Die geplante Aktualisierung von großen Datasets kann lange dauern und ressourcenintensiv sein. Es ist wichtig, nicht zu viele sich überschneidende Aktualisierungen zu planen. Die Konfiguration von [inkrementeller Aktualisierung](service-premium-incremental-refresh.md) wird empfohlen, da sie schneller sowie zuverlässiger ist und weniger Ressourcen beansprucht.

Das erste Laden eines Berichts für große Datasets kann sehr lange dauern, wenn das Dataset längere Zeit nicht verwendet wurde. Der Ladevorgang wird bei Berichten mit längerer Ladezeit in einer Statusanzeige angezeigt.

Die Speicher- und Zeitkapazitäten für die einzelnen Abfragen sind bei Premium-Kapazität deutlich höher, es wird jedoch empfohlen, Visuals mit Filtern und Datenschnitten so einzuschränken, dass nur die benötigten Daten angezeigt werden.

## <a name="incremental-refresh"></a>Inkrementelle Aktualisierung

Die inkrementelle Aktualisierung stellt einen integralen Bestandteil von Besitz und Verwaltung großer Datasets in Power BI Premium dar. Die inkrementelle Aktualisierung hat viele Vorteile, z. B. erfolgen Aktualisierungen schneller, da nur Daten mit Änderungen aktualisiert werden müssen. Aktualisierungen sind zuverlässiger, weil es nicht notwendig ist, Verbindungen mit langer Ausführungsdauer mit flüchtigen Datenquellen herzustellen. Der Ressourcenverbrauch wird reduziert, da sich der Gesamtbedarf an Arbeitsspeicher und anderen Ressourcen durch weniger zu aktualisierende Daten verringert. Richtlinien für die inkrementelle Aktualisierung sind in **Power BI Desktop** definiert und werden bei der Veröffentlichung in einem Arbeitsbereich in einer Premium-Kapazität angewendet. 

![Details zur Aktualisierung](media/service-premium-incremental-refresh/refresh-details.png)

Weitere Informationen finden Sie unter [Inkrementelle Aktualisierung in Power BI Premium](service-premium-incremental-refresh.md).

## <a name="paginated-reports"></a>Paginierte Berichte

Paginierte Berichte, die in den SKUs P1–P3 und A4–A6 unterstützt werden, basieren auf der Technologie der Berichtsdefinitionssprache (Report Definition Language, RDL) in SQL Server Reporting Services. Trotz der Grundlage der RDL-Technologie sind sie nicht mit dem Power BI-Berichtsserver zu verwechseln, der eine herunterladbare Berichtsplattform darstellt, die lokal installiert werden kann und ebenfalls in Power BI Premium enthalten ist. Paginierte Berichte sind so formatiert, dass sie gut auf eine Seite passen, die gedruckt oder geteilt werden kann. Die Daten werden in einer Tabelle angezeigt, auch dann, wenn die Tabelle mehrere Seiten überspannt. Mithilfe der kostenlosen Windows Desktop-Anwendung [**Power BI-Berichts-Generators**](https://go.microsoft.com/fwlink/?linkid=2086513) können Benutzer paginierte Berichte verfassen und sie im Dienst veröffentlichen.

In Power BI Premium sind paginierte Berichte eine Workload, die im Verwaltungsportal für eine Kapazität aktiviert werden muss. Kapazitätsadministratoren können sie aktivieren und dann die Menge Arbeitsspeicher als Prozentsatz der Gesamtspeicherressoucen der Kapazität angeben. Im Gegensatz zu anderen Arten von Workloads führt Premium paginierte Berichte in einem abgeschlossenen Bereich innerhalb der Kapazität aus. Der für diesen Bereich angegebene maximale Arbeitsspeicher wird unabhängig davon belegt, ob die Workload aktiv ist oder nicht. Der Standardwert beträgt 20 %. 

Weitere Informationen finden Sie unter [Paginierte Berichte in Power BI Premium](paginated-reports/paginated-reports-report-builder-power-bi.md). Weitere Informationen zum Aktivieren der Workload Paginierte Berichte finden Sie unter [Konfigurieren von Workloads](service-admin-premium-workloads.md).

## <a name="power-bi-report-server"></a>Power BI-Berichtsserver
 
Der in Power BI Premium enthaltene Power BI-Berichtsserver ist ein *lokaler* Berichtsserver mit einem Webportal. Sie können eine lokale BI-Umgebung erstellen und Berichte hinter der Firewall Ihrer Organisation verteilen. Der Berichtsserver bietet den Benutzern Zugriff auf komplexe interaktive Berichte und die Berichterstellungsfunktionen von SQL Server Reporting Services für Unternehmen. Benutzer können visuelle Daten untersuchen und schnell Muster erkennen, um bessere Entscheidungen treffen zu können. Report Server bietet Governance zu Ihren Bedingungen. Falls und wenn die Zeit dafür kommt, macht Power BI-Berichtsserver die Migration in die Cloud einfach, wo Ihre Organisation den gesamten Funktionsumfang von Power BI Premium in vollem Umfang nutzen kann.

Weitere Informationen finden Sie unter [Power BI-Berichtsserver](report-server/get-started.md).

## <a name="unlimited-content-sharing"></a>Unbegrenztes Teilen von Inhalten

Mit Premium kann jeder Benutzer – innerhalb und außerhalb Ihrer Organisation – Ihre Power BI-Inhalte wie paginierte und interaktive Berichte anzeigen, ohne Einzellizenzen erwerben zu müssen. 

![Teilen von Inhalten](media/service-premium-what-is/premium-sharing.png)

Premium ermöglicht das weiträumige Verteilen von Inhalten durch Power BI Pro-Benutzer, und für Benutzer, die die Inhalte nur anzeigen, sind keine Pro-Lizenzen erforderlich. Pro-Lizenzen sind für Inhaltsersteller erforderlich. Ersteller stellen Verbindungen mit Datenquellen her, modellieren Daten und erstellen Berichte und Dashboards, die als Arbeitsbereichs-Apps verpackt werden. Benutzer ohne Pro-Lizenz haben als Viewer dennoch Zugriff auf einen Arbeitsbereich, der zur Power BI Premium-Kapazität gehört. 

Weitere Informationen finden Sie unter [Power BI-Lizenzierung](service-admin-licensing-organization.md).

## <a name="analysis-services-in-power-bi-premium-preview"></a>Analysis Services in Power BI Premium (Vorschau)

Hinter den Kulissen stützen sich Power BI Premium-Arbeitsbereiche und -Datasets auf die im Unternehmenseinsatz bewährte Microsoft **Analysis Services Vertipaq-Engine**. Analysis Services bietet Programmierbarkeit und Unterstützung für Clientanwendungen und Tools in Form von Clientbibliotheken und APIs, die das XMLA-Protokoll als offenen Standard unterstützen. Standardmäßig unterstützen Workloads für Power BI Premium-Kapazitätsdatasets *schreibgeschützte* Vorgänge aus Clientanwendungen von Microsoft und Drittanbietern sowie Tools über **XMLA-Endpunkte**. Kapazitätsadministratoren können sich auch dafür entscheiden, *Lese-/Schreibvorgänge* über den Endpunkt zu deaktivieren bzw. zuzulassen.

Bei Lesezugriff können Microsoft-Tools wie SQL Server Management Studio (SSMS) und SQL Server Profiler sowie Apps von Drittanbietern wie DAX Studio und Anwendungen zur Datenvisualisierung mithilfe von XMLA, DAX, MDX, DMVs und Trace-Ereignissen Verbindungen mit Premium-Datasets herstellen und diese abfragen. Bei Lese-/Schreibzugriff können Tools zur Unternehmensdatenmodellierung wie Visual Studio mit der Analysis Services-Projekterweiterung oder dem Editor für Open-Source-Tabellen als Dataset in einem Premium-Arbeitsbereich bereitgestellt werden. Und mit Tools wie SSMS können Administratoren die Tabular Model Scripting Language (TMSL) verwenden, um Metadatenänderungen und erweiterte Datenaktualisierungsszenarios zu schreiben. 

Weitere Informationen finden Sie unter [Konnektivität mit Datasets mithilfe des XMLA-Endpunkts](service-premium-connect-tools.md).

![SSMS](media/service-premium-what-is/connect-tools-ssms-dax.png)


## <a name="next-steps"></a>Nächste Schritte

> [!div class="nextstepaction"]
> [Verwalten von Premium-Kapazitäten](service-premium-capacity-manage.md)

Weitere Fragen? [Stellen Sie Ihre Frage in der Power BI-Community.](https://community.powerbi.com/)
