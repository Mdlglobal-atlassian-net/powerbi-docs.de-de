---
title: Problembehandlung für die Berichtsleistung in Power BI
description: Leitfaden zur Problembehandlung und Leistungsdiagnose für langsame Berichte in Power BI
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 04/15/2020
ms.author: v-pemyer
ms.openlocfilehash: dd3be575946502a886bbf2b89e2a1844f4046ea7
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/13/2020
ms.locfileid: "83276948"
---
# <a name="troubleshoot-report-performance-in-power-bi"></a>Problembehandlung für die Berichtsleistung in Power BI

Dieser Artikel enthält Anweisungen, mit denen Entwickler und Administratoren Probleme mit langsamen Berichten behandeln können. Die Inhalte gelten für Power BI-Berichte und paginierte Power BI-Berichte.

Berichtsbenutzer können melden, dass Berichte langsam geladen werden oder langsam aktualisiert werden, wenn Slicer oder andere Features genutzt werden. Wenn Berichte in einer Premium-Kapazität gehostet werden, können langsame Berichte auch über die [Metrik-App in Power BI Premium](../admin/service-admin-premium-monitor-capacity.md) ermittelt werden. Diese App unterstützt Sie dabei, die Integrität und die Kapazität Ihres Power BI Premium-Abonnements zu überwachen.

## <a name="follow-flowchart-steps"></a>Befolgen der Flussdiagrammschritte

Verwenden Sie das folgende Flussdiagramm, um die Ursache für langsamen Leistung nachzuvollziehen und zu entscheiden, welche Maßnahmen ergriffen werden sollen.

:::image type="content" source="media/report-performance-troubleshoot/flowchart.png" alt-text="Abbildung: Flussdiagramm, das im Artikeltext ausführlich beschrieben wird" border="true":::

Das Flussdiagramm enthält sechs Terminatoren, die die zu ergreifende Maßnahme beschreiben:

|Abschlusszeichen|Aktion(en)|
|---------|---------|
|![Terminator 1 des Flussdiagramms:](media/common/icon-01-red-30x30.png)|Verwalten der Kapazität<br />Skalieren der Kapazität |
|![Terminator 2 des Flussdiagramms:](media/common/icon-02-red-30x30.png)|Aktivität der Kapazität während gewöhnlicher Berichtsnutzung untersuchen|
|![Terminator 3 des Flussdiagramms:](media/common/icon-03-red-30x30.png)|Architektur ändern<br />Wechsel zu Azure Analysis Services in Betracht ziehen<br />Lokales Gateway überprüfen|
|![Terminator 4 des Flussdiagramms:](media/common/icon-04-red-30x30.png)|Wechsel zu Azure Analysis Services in Betracht ziehen<br />Wechsel zu Power BI Premium in Betracht ziehen|
|![Terminator 5 des Flussdiagramms:](media/common/icon-05-red-30x30.png)|Leistungsanalyse in Power BI Desktop verwenden<br />Bericht, Modell oder DAX optimieren|
|![Terminator 6 des Flussdiagramms:](media/common/icon-06-red-30x30.png)|Supportticket öffnen|

## <a name="take-action"></a>Ausführen einer Aktion

Zuerst sollten Sie überprüfen, ob der langsame Bericht in einer Premium-Kapazität gehostet wird.

### <a name="premium-capacity"></a>Premium-Kapazität

Wenn der Bericht in einer Premium-Kapazität gehostet wird, verwenden Sie die **Metrik-App in Power BI Premium**, um zu bestimmen, ob die hostende Kapazität häufig ihre Ressourcen überschreitet. Das wäre im Fall der CPU gegeben, wenn diese regelmäßig 80 % überschreitet. Beim Arbeitsspeicher wäre das der Fall, wenn die [Metrik für aktiven Arbeitsspeicher](../admin/service-premium-metrics-app.md#the-active-memory-metric) den Wert 50 überschreitet. Wenn die Ressourcen ihre Grenzen erreichen, sollten Sie die [Kapazität verwalten oder skalieren](../admin/service-admin-premium-manage.md) (Terminator 1 des Flussdiagramms). Wenn ausreichend Ressourcen verfügbar sind, untersuchen Sie Aktivitäten der Kapazität während der gewöhnlichen Berichtsnutzung (Terminator 2 des Flussdiagramms).

### <a name="shared-capacity"></a>Gemeinsam genutzte Kapazität

Wenn der Bericht in einer gemeinsam genutzten Kapazität gehostet wird, kann die Integrität der Kapazität nicht überwacht werden. Sie müssen einen anderen Diagnoseansatz auswählen.

Überprüfen Sie zunächst, ob die langsame Leistung zu bestimmten Zeiten am Tag oder im Monat auftritt. Wenn dies der Fall ist und viele Benutzer den Bericht zu diesen Zeiten öffnen, sollten Sie diese beiden Möglichkeiten in Betracht ziehen:

- Erhöhen Sie den Abfragedurchsatz, indem Sie das Dataset zu [Azure Analysis Services](/azure/analysis-services/analysis-services-overview) oder zu einer Premium-Kapazität (Terminator 4 des Flussdiagramms) migrieren.
- Mit der [Leistungsanalyse](../create-reports/desktop-performance-analyzer.md) in Power BI Desktop können Sie die Leistung für jedes Ihrer Berichtselemente ermitteln, z. B. für Visuals und DAX-Formeln. Sie eignet sich insbesondere, um zu bestimmen, ob die Leistung durch eine Abfrage oder beim Rendern eines Visuals beeinträchtigt wird (Terminator 5 des Flussdiagramms).

Wenn Sie feststellen, dass kein Zeitmuster vorhanden ist, sollten Sie als Nächstes überprüfen, ob die langsame Leistung nur in einer bestimmten Geografie oder Region auftritt. Wenn das der Fall ist, ist die Datenquelle wahrscheinlich weit entfernt und die Netzwerkkommunikation deshalb langsam. Versuchen Sie in diesem Fall Folgendes:

- Ändern Sie die Architektur mithilfe von [Azure Analysis Services](/azure/analysis-services/analysis-services-overview) (Terminator 3 des Flussdiagramms).
- Optimieren Sie die [Leistung des lokalen Datengateways](/data-integration/gateway/service-gateway-performance) (Terminator 3 des Flussdiagramms).

Wenn Sie feststellen, dass es kein Zeitmuster gibt _und_ die langsame Leistung in allen Regionen auftritt, sollten Sie überprüfen, ob die langsame Leistung auf bestimmten Geräten, Clients oder in bestimmten Webbrowsern auftritt. Wenn das nicht der Fall ist, verwenden Sie wie zuvor beschrieben die [Leistungsanalyse](../create-reports/desktop-performance-analyzer.md) in Power BI Desktop, um den Bericht oder das Modell zu optimieren (Terminator 5 des Flussdiagramms).

Wenn Sie feststellen, dass bestimmte Geräte, Clients oder Webbrowser zur langsamen Leistung beitragen, sollten Sie über die [Power BI-Supportseite](https://powerbi.microsoft.com/support/) ein Supportticket öffnen (Terminator 6 des Flussdiagramms).

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zu diesem Artikel finden Sie in den folgenden Ressourcen:

- [Dokumentation zum Power BI-Leitfaden](index.yml)
- [Überwachen der Berichtsleistung](monitor-report-performance.md)
- [Leistungsanalyse](../create-reports/desktop-performance-analyzer.md)
- Whitepaper: [Planning a Power BI Enterprise Deployment](https://go.microsoft.com/fwlink/?linkid=2057861)
- Haben Sie Fragen? [Stellen Sie Ihre Frage in der Power BI-Community.](https://community.powerbi.com/)
- Vorschläge? [Einbringen von Ideen zur Verbesserung von Power BI](https://ideas.powerbi.com/)
