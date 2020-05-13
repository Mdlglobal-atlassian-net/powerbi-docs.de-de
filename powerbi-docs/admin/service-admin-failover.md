---
title: Power BI-FAQ zur Hochverfügbarkeit und Notfallwiederherstellung sowie zu Failovers
description: Informationen zur Hochverfügbarkeit und zum Bereitstellen von Geschäftskontinuität und Notfallwiederherstellung für Benutzer des Power BI-Diensts
author: kfollis
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 02/20/2020
ms.author: kfollis
LocalizationGroup: Administration
ms.openlocfilehash: 3dd50d4f57b3146135cde5e91062ed3b2a0eecc1
ms.sourcegitcommit: bfc2baf862aade6873501566f13c744efdd146f3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/13/2020
ms.locfileid: "83128559"
---
# <a name="power-bi-high-availability-failover-and-disaster-recovery-faq"></a>Power BI-FAQ zur Hochverfügbarkeit und Notfallwiederherstellung sowie zu Failovers

In diesem Artikel erhalten Sie Informationen zur Hochverfügbarkeit und zum Bereitstellen von Geschäftskontinuität und Notfallwiederherstellung für Benutzer des Power BI-Diensts. Nach dem Lesen sollten Sie einen besseren Überblick darüber haben, wie Hochverfügbarkeit erreicht wird, unter welchen Umständen Power BI ein Failover ausführt und was in diesem Fall von dem Dienst zu erwarten ist.

## <a name="what-does-high-availability-mean-for-power-bi"></a>Was bedeutet „Hochverfügbarkeit“ in Bezug auf Power BI?

Power BI ist ein vollständig verwalteter SaaS-Dienst (Software-as-a-Service).  Dieser wurde von Microsoft so entwickelt, dass er bei Infrastrukturfehlern nicht an Stabilität verliert und Benutzer immer auf ihre Berichte zugreifen können.  Er wird von einer [SLA von 99,9 %](https://www.microsoftvolumelicensing.com/DocumentSearch.aspx?Mode=3&DocumentTypeId=37) unterstützt.

## <a name="what-is-a-power-bi-failover"></a>Was ist ein Power BI-Failover?

Power BI verwaltet mehrere Instanzen jeder einzelnen Komponente in Azure-Rechenzentren (auch bekannt als „Regionen“), um die Geschäftskontinuität zu garantieren. Wenn es zu Ausfällen oder zu einem Problem kommt und nicht auf Power BI zugegriffen werden kann oder der Dienst für eine bestimmte Region nicht mehr funktionsfähig ist, führt Power BI für alle seine Komponenten in der betreffenden Region ein Failover auf eine Sicherheitsinstanz durch. Durch das Failover wird die Verfügbarkeit und Funktionsfähigkeit der Power BI-Dienstinstanz in einer neuen Region wiederhergestellt. Wie im [Microsoft Trust Center](https://www.microsoft.com/TrustCenter/CloudServices/business-application-platform/data-location) erwähnt, wird dafür in der Regel derselbe geografische Standort verwendet.

Bei einem Failover unterstützt die Power BI-Dienstinstanz nur _Lesevorgänge_. D. h., die folgenden Vorgänge werden nicht unterstützt: Aktualisierungen, Vorgänge zum Veröffentlichen von Berichten, Änderungen am Dashboard oder in Berichten sowie andere Vorgänge, bei denen Power BI-Metadaten geändert werden müssen (z. B. das Einfügen eines Kommentars in einen Bericht).  Lesevorgänge wie das Anzeigen von Dashboards und Berichten (die nicht auf DirectQuery- oder Live Connect-Vorgängen auf lokalen Datenquellen basieren) funktionieren normal.

## <a name="how-are-backup-instances-kept-in-sync-with-my-data"></a>Wie werden meine Daten auf Sicherungsinstanzen synchronisiert?

Alle Power BI-Dienstkomponenten synchronisieren ihre Sicherungsinstanzen regelmäßig. Ziel ist es, alle 15 Minuten eine Point-in-Time-Synchronisierung für jeglichen in Power BI hochgeladenen oder geänderten Inhalt durchzuführen. Wenn es zu einem Failover kommen sollte, verwendet Power BI die [georedundante Replikation für Azure Storage](/azure/storage/common/storage-redundancy-grs) und die [georedundante Replikation für Azure SQL](/azure/sql-database/sql-database-active-geo-replication), um zu garantieren, dass Sicherungsinstanzen in anderen Regionen vorhanden sind und im Falle eines Failovers verwendet werden können.

## <a name="where-are-the-failover-clusters-located"></a>Wo befinden sich die Failovercluster?

Die Sicherungsinstanzen befinden sich an dem geografischen Standort (geografischer Raum), den Sie bei der Anmeldung Ihrer Organisation für Power BI ausgewählt haben, es sei denn, im [Microsoft Trust Center](https://www.microsoft.com/TrustCenter/CloudServices/business-application-platform/data-location) werden andere Angaben gemacht. Ein geografischer Raum kann mehrere Regionen umfassen, und Microsoft kann in jeder dieser Regionen innerhalb eines bestimmten geografischen Raums Daten replizieren, um die Datenresilienz zu garantieren. Microsoft repliziert keine Kundendaten außerhalb dieses geografischen Raums und verschiebt sie auch nicht. Eine Karte mit den für Power BI zur Verfügung stehenden geografischen Räumen und den jeweiligen Regionen finden Sie im [Microsoft Trust Center](https://www.microsoft.com/TrustCenter/CloudServices/business-application-platform/data-location).

## <a name="how-does-microsoft-decide-to-failover"></a>Wie entscheidet Microsoft, ob ein Failover durchgeführt werden muss?

Möglicherweise ist ein Failover erforderlich, wenn:

- bei unseren internen und externen Überwachungstests Probleme mit der Verfügbarkeit oder der Funktionsfähigkeit gefunden werden. Diese Probleme können aufgrund von Ausfällen entstehen, die bei Power BI-Komponenten oder mindestens einem Dienst in einer Region ermittelt werden, von dem Power BI abhängig ist.
- das Central Operations Team von Microsoft Azure uns über einen bedenklichen Ausfall in einer Region informiert.

In beiden Fällen entscheiden sich die Mitglieder des Executive Teams von Power BI für ein Failover. Die Entscheidung erfolgt also nicht automatisch. Das Failover wird hingegen automatisch ausgeführt.

## <a name="how-do-i-know-power-bi-is-now-in-failover-mode"></a>Woher weiß ich, dass sich Power BI gerade im Failovermodus befindet?

Dann wird eine Benachrichtigung auf der Supportseite von Power BI veröffentlicht ([https://powerbi.microsoft.com/support/](https://powerbi.microsoft.com/support/)). Diese enthält Informationen zu den wichtigsten Vorgängen, die während des Failovers nicht ausgeführt werden können, z. B. das Veröffentlichen, Aktualisieren, Erstellen und Duplizieren von Dashboards sowie das Ändern von Berechtigungen.

## <a name="how-long-does-it-take-power-bi-to-fail-over"></a>Wie lange dauert ein Power BI-Failover?

Es dauert ungefähr 15 Minuten, bis Power BI wieder betriebsbereit ist, wenn festgestellt wird, dass ein Failover erforderlich ist. Wie lange es dauert, bis die Notwendigkeit eines Failovers erkannt wird, hängt von dem jeweiligen Szenario ab, das unterbrochen wird. 

Nachdem ein Failover durchgeführt wurde, verwendet Power BI die Georeplikation für Azure Storage, um das Failover durchzuführen. Solche Replikationen haben in der Regel einen Rückgabepunkt von 15 Minuten. [Azure Storage garantiert diesen Zeitrahmen allerdings nicht](https://docs.microsoft.com/azure/storage/common/storage-redundancy) durch eine SLA, weshalb auch Power BI keinen festen Zeitrahmen garantieren kann. 


## <a name="when-does-my-power-bi-instance-return-to-the-original-region"></a>Wann wird meine Power BI-Instanz wieder in der ursprünglichen Region ausgeführt?

Power BI-Dienstinstanzen werden wieder in der ursprünglichen Region ausgeführt, wenn das Problem gelöst wurde, das das Failover ausgelöst hat. Besuchen Sie die Supportseite für Power BI: Wenn das Problem behoben wurde, entfernt das Power BI-Team die Failoverbenachrichtigung. Dann sollten alle Vorgänge wieder normal ausgeführt werden können.

## <a name="am-i-responsible-for-the-availability-of-my-power-bi-solution"></a>Bin ich für die Verfügbarkeit meiner Power BI-Lösung verantwortlich?

Wenn die in Ihrer Organisation verwendete Power BI-Lösung eins der folgenden Elemente umfasst, müssen Sie Maßnahmen ergreifen, um die Hochverfügbarkeit der Lösung zu gewährleisten:

- Wenn Ihre Organisation Power BI Premium verwendet, müssen Sie sicherstellen, dass die Premium-Kapazität an den Ladungsbedarf Ihrer Bereitstellung angepasst ist.  Das [Whitepaper zur Planung und Bereitstellung von Power BI Premium](https://aka.ms/Premium-Capacity-Planning-Deployment) und die [Power BI Premium Capacity Metrics-App](service-admin-premium-monitor-capacity.md) können Ihnen bei der Planung und beim Erfüllen der Anforderungen helfen. Es werden regelmäßig neue Hilfefeatures zur Metrics-Apps und dem Administratorportal in Power BI hinzugefügt.
- Wenn Ihre Organisation über das lokale Datengateway auf lokale Datenquellen zugreift, müssen Sie dieses [wie in diesem Artikel beschrieben](/data-integration/gateway/service-gateway-high-availability-clusters) einrichten, um die Hochverfügbarkeit zu unterstützen. Egal, ob Sie Berichte im Importmodus aktualisieren oder über DirectQuery oder Live Connect auf Daten(modelle) zugreifen: Beachten Sie die in diesem Artikel aufgeführten Anweisungen.

## <a name="will-gateways-function-when-in-failover-mode"></a>Funktionieren Gateways im Failovermodus?

Nein. Daten, die von lokalen Datenquellen benötigt werden (alle Berichte und Dashboards, die auf DirectQuery und Live Connect basieren) funktionieren während eines Failovers nicht. Die Gatewaykonfiguration ändert sich allerdings nicht: Wenn die Power BI-Instanz wieder in ihren ursprünglichen Zustand zurückkehrt, funktionieren die Gateways wieder normal.
