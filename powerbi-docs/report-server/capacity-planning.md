---
title: Leitfaden zur Kapazitätsplanung für Power BI-Berichtsserver
description: Dieses Dokument bietet einen Leitfaden zur Kapazitätsplanung für Power BI-Berichtsserver anhand der Ergebnisse von Auslastungstests mit verschiedenen Arbeitsauslastungen.
author: parthsha
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.topic: conceptual
ms.date: 3/5/2018
ms.author: parshah
ms.openlocfilehash: 8b30089fe04c832734bd418cc58fabb7b574a082
ms.sourcegitcommit: dc18209dccb6e2097a92d87729b72ac950627473
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/27/2020
ms.locfileid: "80361766"
---
# <a name="capacity-planning-guidance-for-power-bi-report-server"></a>Leitfaden zur Kapazitätsplanung für Power BI-Berichtsserver
Power BI-Berichtsserver ist eine Lösung für Self-Service-BI und Enterprise-Berichterstellung, die Kunden lokal hinter der Firewall bereitstellen können. Sie kombiniert die interaktiven Berichte von Power BI Desktop mit der lokalen Serverplattform von SQL Server Reporting Services. Aufgrund der starken und zunehmenden Verwendung von Analysen und Berichten in Unternehmen kann die Budgetplanung für die Hardwareinfrastruktur und die erforderlichen Softwarelizenzen für die Skalierung auf eine hohe Benutzeranzahl eine Herausforderung sein. Dieses Dokument bietet einen Leitfaden zur Kapazitätsplanung für Power BI-Berichtsserver anhand der Ergebnisse zahlreicher Auslastungstests mit verschiedenen Arbeitsauslastungen eines Berichtsservers. Die Berichte, Abfragen und Verwendungsmuster in einem Unternehmen weisen große Unterschiede auf. Jedoch lassen sich die in diesem Dokument vorgestellten Ergebnisse zusammen mit den tatsächlich verwendeten Tests und einer ausführlichen Beschreibung ihrer Ausführung immer als Orientierungshilfe bei der anfänglichen Planung der Bereitstellung von Power BI-Berichtsserver nutzen.

## <a name="executive-summary"></a>Kurzfassung
Wir haben zwei unterschiedliche Typen von Arbeitsauslastungen von Power BI-Berichtsserver ausgeführt. Jede Arbeitsauslastung bestand aus dem Rendern unterschiedlicher Typen von Berichten sowie dem Ausführen verschiedener Webportalvorgänge. 

* Bei der Workload „Power BI-Bericht – stark“ war der am häufigsten (60 % der Zeit ausgeführte) ausgeführte Vorgang das Rendern von Power BI-Berichten.
* Bei der Workload „Paginierter Bericht – stark“ war der am häufigsten ausgeführte Vorgang das Rendern paginierter Berichte.

In der folgenden Tabelle wird die maximale Anzahl von Benutzern angegeben, die Power BI-Berichtsserver mit einer Zuverlässigkeit von mindestens 99 % bewältigen kann, wenn die Topologie von Power BI-Berichtsserver vier Server umfasst und davon ausgegangen wird, dass zu keinem Zeitpunkt mehr als 5 % der Benutzer gleichzeitig auf einen Berichtsserver zugreifen. 

| Arbeitsauslastung | 8 Kerne/32 GB RAM | 16 Kerne/64 GB RAM |
| --- | --- | --- |
| **Power BI-Bericht – stark** (> 60 %) |1\.000 Benutzer |3\.000 Benutzer |
| **Paginierter Bericht (RDL) – stark** (> 60 %) |2\.000 Benutzer |3\.200 Benutzer |

Bei jeder Ausführung war die CPU die am stärksten belastete Ressource. Aus diesem Grund führt eine höhere Anzahl von Kernen für Power BI-Berichtsserver zu einer höheren Zuverlässigkeit des Systems als die Erhöhung des Arbeitsspeichers oder Festplattenspeichers. 

## <a name="test-methodology"></a>Testmethodik
Die verwendete Testtopologie basierte auf Microsoft Azure Virtual Machines statt auf anbieterspezifischer physischer Hardware. Alle Computer wurden in Regionen in den USA gehostet. Dies entspricht der allgemeinen Tendenz, dass Hardwarevirtualisierung sowohl lokal als auch in der öffentlichen Cloud erfolgt. 

### <a name="power-bi-report-server-topology"></a>Topologie von Power BI-Berichtsserver
Die Bereitstellung von Power BI-Berichtsserver umfasste die folgenden virtuellen Computer:

* Active Directory-Domänencontroller: Dieser wurde von der SQL Server-Datenbank-Engine, von SQL Server Analysis Services und von Power BI-Berichtsserver benötigt, um alle Anforderungen sicher zu authentifizieren.
* SQL Server-Datenbank-Engine und SQL Server Analysis Services: Dort wurden alle Datenbanken für die Berichte gespeichert, die beim Rendern der Berichte verwendet wurden.
* Power BI-Berichtsserver
* Power BI-Berichtsserver-Datenbank. Die Berichtsserver-Datenbank wird auf einem anderen Computer als Power BI-Berichtsserver gehostet, damit es zu keinen Konflikten mit der SQL Server-Datenbank-Engine im Hinblick auf Arbeitsspeicher, CPU-, Netzwerk- und Datenträgerressourcen kommt.

![](media/capacity-planning/report-server-topology.png)

In Anhang 1.1, „Topologie von Power BI-Berichtsserver“ und Anhang 1.2, „Konfiguration des virtuellen Power BI-Berichtsserver-Computers“ finden Sie genaue Informationen zur Konfiguration der einzelnen virtuellen Computer in der Topologie.

### <a name="tests"></a>Tests
Die in den Auslastungstests verwendeten Tests sind in einem GitHub-Projekt mit dem Namen [Reporting Services LoadTest](https://github.com/Microsoft/Reporting-Services-LoadTest) (in englischer Sprache) öffentlich verfügbar. Mit diesem Tool können Benutzer die Eigenschaften von SQL Server Reporting Services und Power BI-Berichtsserver im Hinblick auf Leistung, Zuverlässigkeit, Skalierbarkeit und Wiederherstellbarkeit untersuchen. Dieses Projekt besteht aus vier Gruppen von Testfällen:

* Tests, die das Rendern von Power BI-Berichten simulieren,
* Tests, die das Rendern von mobilen Berichten simulieren,
* Tests, die das Rendern von kleinen und großen paginierten Berichten simulieren, und 
* Tests, die das Ausführen verschiedener Typen von Webportalvorgängen simulieren. 

Alle Tests wurden so entworfen, dass sie einen End-to-End-Vorgang (z.B. das Rendern eines Berichts, das Erstellen einer neuen Datenquelle usw.) ausführen. Zu diesem Zweck führen die Tests eine oder mehrere Webanforderungen an den Berichtsserver (über APIs) aus. In der Praxis muss ein Benutzer möglicherweise einige zwischengeschaltete Vorgänge ausführen, um einen dieser End-to-End-Vorgänge abzuschließen. Beispiel: Zum Rendern eines Berichts muss der Benutzer zum Webportal wechseln, zu dem Ordner navigieren, in dem sich der Bericht befindet, und dann auf den Bericht klicken, um ihn zu rendern. In den Tests werden nicht alle Vorgänge ausgeführt, die zum vollständigen Ausführen einer End-to-End-Aufgabe erforderlich sind, jedoch erzeugen sie einen Großteil der Last, die der Power BI-Berichtsserver unter realen Bedingungen bewältigen muss. Sie können das GitHub-Projekt erkunden, um mehr über die unterschiedlichen Typen der verwendeten Berichte und die Vielfalt der ausgeführten Vorgänge zu erfahren.  

> [!NOTE]
> Das Tool wird nicht offiziell von Microsoft unterstützt, das Produktteam trägt jedoch zum Projekt bei und beantwortet Fragen von anderen Mitwirkenden.

### <a name="workloads"></a>Workloads
Beim Testen werden zwei Workloadprofile verwendet: „Power BI-Bericht – stark“ und „Paginierter Bericht – stark“. In der folgenden Tabelle wird die Verteilung der für den Berichtsserver ausgeführten Anforderungen beschrieben.

| Aktivität | Power BI-Bericht – stark, Häufigkeit des Vorkommens | Paginierter Bericht – stark, Häufigkeit des Vorkommens |
| --- | --- | --- |
| **Rendern von Power BI-Berichten** |60 % |10 % |
| **Rendern von paginierten Berichten (RDL)** |30 % |60 % |
| **Rendern von mobilen Berichten** |5 % |20 % |
| **Webportalvorgänge** |5 % |10 % |

### <a name="user-load"></a>Benutzerlast
In jedem Testlauf wurden die Tests basierend auf der in einer der beiden Arbeitsauslastungen angegebenen Häufigkeit ausgeführt. Die Tests wurden mit 20 gleichzeitigen Benutzeranforderungen an den Berichtsserver gestartet. Die Benutzerlast wurde dann schrittweise erhöht, bis die Zuverlässigkeit unter den Zielwert von 99 % sank.

## <a name="results"></a>Ergebnisse
### <a name="concurrent-user-capacity"></a>Bewältigte Anzahl gleichzeitiger Benutzer
Wie bereits erwähnt, wurden die Tests mit 20 Benutzern, die gleichzeitig Anforderungen an den Berichtsserver senden, gestartet. Die Anzahl von gleichzeitigen Benutzern wurde dann schrittweise erhöht, bis 1 % aller Anforderungen fehlschlugen. Die Ergebnisse in der folgenden Tabelle geben die Anzahl gleichzeitiger Benutzeranforderungen an, die der Server unter Spitzenlast mit einer Fehlerrate von weniger als 1 % verarbeiten kann.

| Arbeitsauslastung | 8 Kerne/32 GB | 16 Kerne/64 GB |
| --- | --- | --- |
| **Power BI-Bericht – stark** |50 gleichzeitige Benutzer |150 gleichzeitige Benutzer |
| **Paginierter Bericht – stark** |100 gleichzeitige Benutzer |160 gleichzeitige Benutzer |

### <a name="total-user-capacity"></a>Gesamte Benutzerkapazität
Wir haben bei Microsoft eine Produktionsbereitstellung von Power BI-Berichtsserver, die von mehreren Teams verwendet wurde. Wenn wir die tatsächliche Nutzung dieser Umgebung analysieren, stellen wir fest, dass die Anzahl von gleichzeitigen Benutzern zu einem beliebigen Zeitpunkt (auch während der täglichen Spitzenlast) in der Regel nicht höher als 5 % der gesamten Benutzeranzahl ist. Mit diesem Verhältnis von 5 % gleichzeitiger Benutzer als Maßstab extrapolierten wir die gesamte Benutzeranzahl, die von Power BI-Berichtsserver mit einer Zuverlässigkeit von 99 % bewältigt werden kann.

| Arbeitsauslastung | 8 Kerne/32 GB | 16 Kerne/64 GB |
| --- | --- | --- |
| **Power BI-Bericht – stark** |1\.000 Benutzer |3\.000 Benutzer |
| **Paginierter Bericht – stark** |2\.000 Benutzer |3\.200 Benutzer |

### <a name="view-results"></a>Anzeigen der Ergebnisse
Wählen Sie einen Bericht aus, um die Ergebnisse des Auslastungstests anzuzeigen.

| Arbeitsauslastung | 8 Kerne/32 GB | 16 Kerne/64 GB |
| --- | --- | --- |
| **Power BI-Bericht – stark** |[Ansicht – 8 Kerne](https://msit.powerbi.com/view?r=eyJrIjoiMDhhNGY4NGQtNGRhYy00Yzk4LTk2MzAtYzFlNWI5NjBkMGFiIiwidCI6IjcyZjk4OGJmLTg2ZjEtNDFhZi05MWFiLTJkN2NkMDExZGI0NyIsImMiOjV9) |[Ansicht – 16 Kerne](https://msit.powerbi.com/view?r=eyJrIjoiNDBiODk1OGUtYTAyOC00MzVhLThmZmYtNzVjNTFjNzMwYzkwIiwidCI6IjcyZjk4OGJmLTg2ZjEtNDFhZi05MWFiLTJkN2NkMDExZGI0NyIsImMiOjV9) |
| **Paginierter Bericht – stark** |[Ansicht – 8 Kerne](https://msit.powerbi.com/view?r=eyJrIjoiNDFiZWYzMTktZGIxNS00MzcwLThjODQtMmJkMGRiZWEzNjhlIiwidCI6IjcyZjk4OGJmLTg2ZjEtNDFhZi05MWFiLTJkN2NkMDExZGI0NyIsImMiOjV9) |[Ansicht – 16 Kerne](https://msit.powerbi.com/view?r=eyJrIjoiOTU0YjJkYTgtNDg4Yy00NzlhLWIwMGYtMzg4YWI2MjNmOTZjIiwidCI6IjcyZjk4OGJmLTg2ZjEtNDFhZi05MWFiLTJkN2NkMDExZGI0NyIsImMiOjV9) |

<iframe width="640" height="360" src="https://msit.powerbi.com/view?r=eyJrIjoiMDhhNGY4NGQtNGRhYy00Yzk4LTk2MzAtYzFlNWI5NjBkMGFiIiwidCI6IjcyZjk4OGJmLTg2ZjEtNDFhZi05MWFiLTJkN2NkMDExZGI0NyIsImMiOjV9" frameborder="0" allowFullScreen="true"></iframe>

<iframe width="640" height="360" src="https://msit.powerbi.com/view?r=eyJrIjoiNDBiODk1OGUtYTAyOC00MzVhLThmZmYtNzVjNTFjNzMwYzkwIiwidCI6IjcyZjk4OGJmLTg2ZjEtNDFhZi05MWFiLTJkN2NkMDExZGI0NyIsImMiOjV9" frameborder="0" allowFullScreen="true"></iframe>

<iframe width="640" height="360" src="https://msit.powerbi.com/view?r=eyJrIjoiNDFiZWYzMTktZGIxNS00MzcwLThjODQtMmJkMGRiZWEzNjhlIiwidCI6IjcyZjk4OGJmLTg2ZjEtNDFhZi05MWFiLTJkN2NkMDExZGI0NyIsImMiOjV9" frameborder="0" allowFullScreen="true"></iframe>

<iframe width="640" height="360" src="https://msit.powerbi.com/view?r=eyJrIjoiOTU0YjJkYTgtNDg4Yy00NzlhLWIwMGYtMzg4YWI2MjNmOTZjIiwidCI6IjcyZjk4OGJmLTg2ZjEtNDFhZi05MWFiLTJkN2NkMDExZGI0NyIsImMiOjV9" frameborder="0" allowFullScreen="true"></iframe>

## <a name="summary"></a>Zusammenfassung
Bei jeder Ausführung der Auslastungstests war die CPU zum Zeitpunkt der Spitzenlast des Computers, auf dem Power BI-Berichtsserver ausgeführt wird, die am stärksten belastete Ressource. Deshalb sollte als Erstes die Anzahl der Kerne erhöht werden. Alternativ dazu können Sie horizontal hochskalieren, indem Sie in der Topologie weitere Server hinzufügen, die Power BI-Berichtsserver hosten.

Die in diesem Dokument beschriebenen Ergebnisse wurden aus dem Ausführen eines bestimmten Satzes von Berichten, die einen bestimmen Satz von Daten verwenden, abgeleitet, wobei die Ausführung auf eine bestimmte Weise wiederholt wurde. Dies ist eine nützliche Orientierungshilfe, beachten Sie jedoch, dass die Auslastung in Ihrer Umgebung von Ihren Berichten, Abfragen, Verwendungsmustern und der Bereitstellung von Power BI-Berichtsserver abhängt.

## <a name="appendix"></a>Anhang
### <a name="1-topology"></a>1 Topologie
**1.1 Topologie von Power BI-Berichtsserver**

Um sich ausschließlich auf das Verhalten von Power BI-Berichtsserver bei unterschiedlichen Konfigurationen zu konzentrieren, war die VM-Konfiguration für jeden Typ von Computer (mit Ausnahme des Computers, auf dem der Power BI-Berichtsserver gehostet wird) die gleiche. Jeder Computer wurde als virtueller Computer der zweiten Generation (Dv2-Serie) mit Storage Premium-Datenträgern bereitgestellt. Ausführliche Informationen zu jeder VM-Größe finden Sie im [Abschnitt „Allgemein“](https://azure.microsoft.com/pricing/details/virtual-machines/windows/).

| Typ des virtuellen Computers | Prozessor | Arbeitsspeicher | Azure VM-Größe |
| --- | --- | --- | --- |
| **Active Directory-Domänencontroller** |2 Kerne |7 GB |Standard_DS2_v2 |
| **SQL Server-Datenbank-Engine und Analysis Services** |16 Kerne |56 GB |Standard_DS5_v2 |
| **Berichtsserver-Datenbank** |16 Kerne |56 GB |Standard_DS5_v2 |

**1.2 Konfiguration des virtuellen Power BI-Berichtsserver-Computers** 

Für den virtuellen Computer, der Power BI-Berichtsserver hostet, wurden unterschiedliche Konfigurationen von Prozessor und Arbeitsspeicher verwendet. Im Gegensatz zu anderen virtuellen Computern wurde dieser Computer als virtueller Computer der dritten Generation (Dv3-Serie) mit Storage Premium-Datenträgern bereitgestellt. Ausführliche Informationen zu dieser VM-Größe finden Sie im [Abschnitt „Allgemein“](https://azure.microsoft.com/pricing/details/virtual-machines/windows/.).

| Virtueller Computer | Prozessor | Arbeitsspeicher | Azure VM-Größe |
| --- | --- | --- | --- |
| **Power BI-Berichtsserver (klein)** |8 Kerne |32 GB |Standard_D8S_v3 |
| **Power BI-Berichtsserver (groß)** |16 Kerne |64 GB |vStandard_D16S_v3 |

### <a name="2-run-the-loadtest-tool"></a>2 Ausführen des Tools LoadTest
Wenn Sie das Tool LoadTest von Reporting Services für Ihre Power BI-Berichtsserver-Bereitstellung oder eine Microsoft Azure-Bereitstellung von Power BI-Berichtsserver ausführen möchten, führen Sie die folgenden Schritte aus.

1. Klonen Sie das Reporting Services LoadTest-Projekt von GitHub (https://github.com/Microsoft/Reporting-Services-LoadTest).  
2. Das Projektverzeichnis enthält eine Projektmappendatei mit dem Namen „RSLoadTests.sln“. Öffnen Sie diese Datei in Visual Studio 2015 oder höher.
3. Bestimmen Sie, ob dieses Tool für Ihre Bereitstellung von Power BI-Berichtsserver oder für eine Bereitstellung von Power BI-Berichtsserver in Microsoft Azure ausgeführt werden soll. Wenn Sie es für Ihre eigene Bereitstellung ausführen möchten, fahren Sie mit Schritt 5 fort.
4. Befolgen Sie die Anweisungen unter https://github.com/Microsoft/Reporting-Services-LoadTest#create-a-sql-server-reporting-services-load-environment-in-azure, um eine Power BI-Berichtsserver-Umgebung in Azure zu erstellen.
5. Sobald Sie mit der Bereitstellung der Umgebung fertig sind, befolgen Sie die Anweisungen unter https://github.com/Microsoft/Reporting-Services-LoadTest#load-test-execution, um die Tests auszuführen.

Weitere Fragen? [Stellen Sie Ihre Frage in der Power BI-Community.](https://community.powerbi.com/)
