---
title: Zwischenspeicherung von Abfragen in Power BI Premium
description: Zwischenspeicherung von Abfragen in Power BI Premium
author: KesemSharabi
ms.author: kesharab
ms.reviewer: bhmerc
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 10/04/2019
LocalizationGroup: ''
ms.openlocfilehash: bf9248b29c71f42de9fed53ee0148847a8f60d30
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "79488635"
---
# <a name="query-caching-in-power-bi-premiumembedded"></a>Zwischenspeicherung von Abfragen in Power BI Premium/Embedded

Organisationen mit Power BI Premium oder Power BI Embedded können von der *Zwischenspeicherung von Abfragen* profitieren, um Berichte, die einem Dataset zugeordnet sind, zu beschleunigen. Mit der Zwischenspeicherung von Abfragen wird die Premium/Embedded-Kapazität angewiesen, den lokalen Cachedienst zu verwenden, um Abfrageergebnisse zu verwalten und um zu vermeiden, dass die zugrunde liegende Datenquelle diese Ergebnisse berechnet.

> [!IMPORTANT]
> Die Zwischenspeicherung von Abfragen ist nur in Power BI Premium oder Power BI Embedded verfügbar. Sie kann nicht für LiveConnect-Datasets angewendet werden, die Azure Analysis Services oder SQL Server Analysis Services nutzen.

Zwischengespeicherte Abfrageergebnisse beziehen sich auf den Benutzer- und Datasetkontext und berücksichtigen Sicherheitsregeln. Derzeit führt der Dienst die Zwischenspeicherung von Abfragen nur für die erste Seite durch, auf die Sie gelangen. Abfragen werden also nicht zwischengespeichert, wenn Sie mit dem Bericht interagieren. Der Abfragecache respektiert [persönliche Lesezeichen](consumer/end-user-bookmarks.md#personal-bookmarks) und [persistente Filter](https://powerbi.microsoft.com/blog/announcing-persistent-filters-in-the-service/), sodass Abfragen, die von einem personalisierten Bericht generiert werden, im Cache gespeichert werden. [Dashboardkacheln](service-dashboard-tiles.md), die von denselben Abfragen unterstützt werden, profitieren ebenfalls davon, sobald die Abfrage zwischengespeichert wurde. Die Leistung wird ebenfalls optimiert, wenn regelmäßig auf ein Dataset zugegriffen wird und dieses nicht oft aktualisiert werden muss. Die Zwischenspeicherung von Abfragen kann zudem die Last auf Ihrer Premium/Embedded-Kapazität verringern, indem die Gesamtzahl der Abfragen reduziert wird.

Sie steuern das Zwischenspeicherungsverhalten für Abfragen für das Dataset im Power BI-Dienst über die Seite **Einstellungen**. Ihnen stehen drei mögliche Einstellungen zur Verfügung:

- **Kapazitätsstandard**: Zwischenspeicherung von Abfragen: Aus
- **Aus:** Die Zwischenspeicherung von Abfragen darf für dieses Dataset nicht verwendet werden.
- **Ein:** Sie können die Zwischenspeicherung von Abfragen für dieses Dataset verwenden.

    ![Dialogfeld „Zwischenspeicherung von Abfragen“](media/power-bi-query-caching/power-bi-query-3-options.png)

## <a name="considerations-and-limitations"></a>Überlegungen und Einschränkungen

- Wenn Sie die Einstellungen für die Zwischenspeicherung von **Ein** in **Aus** ändern, werden alle zuvor gespeicherten Abfrageergebnisse für das Dataset aus dem Kapazitätscache entfernt. Sie können die Zwischenspeicherung entweder explizit deaktivieren oder durch Wiederherstellen der Standardeinstellung für die Kapazität, die von einem Administrator auf **Aus** festgelegt wurde. Die Deaktivierung kann zu einer kurzen Verzögerung bei der nächsten Ausführung von Abfragen für Datasets führen, die von einem Bericht ausgeführt werden. Die Verzögerung wird ausgelöst, da Berichtabfragen bedarfsgesteuert ausgeführt werden und gespeicherte Ergebnisse nicht genutzt werden. Das erforderliche Dataset muss ggf. neu in den Arbeitsspeicher geladen werden, bevor Abfragen verarbeitet werden können.
- Wenn der Abfragecache aktualisiert wird, muss Power BI Abfragen anhand der zugrunde liegenden Datenmodelle ausführen, um die neuesten Ergebnisse zu erhalten. Wenn der Abfragecache für eine große Anzahl von Datasets aktiviert ist und die Premium/Embedded-Kapazität stark ausgelastet ist, kann es beim Aktualisieren des Caches zu Leistungseinbußen kommen. Die Verschlechterung resultiert aus dem erhöhten Volumen der ausgeführten Abfragen.

## <a name="next-steps"></a>Nächste Schritte

* [Was ist Power BI Premium?](service-premium-what-is.md)
* [Was ist Power BI Embedded in Azure?](developer/embedded/azure-pbie-what-is-power-bi-embedded.md)
