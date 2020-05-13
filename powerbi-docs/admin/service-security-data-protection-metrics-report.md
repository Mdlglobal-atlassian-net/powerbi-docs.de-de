---
title: Bericht zu Datenschutzmetriken
description: Erfahren Sie mehr über den Bericht zu Datenschutzmetriken.
author: paulinbar
manager: rkarlin
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 03/11/2020
ms.author: painbar
LocalizationGroup: Data from files
ms.openlocfilehash: e16acffd683b14eb48a6e21ddc456caeac25efc3
ms.sourcegitcommit: bfc2baf862aade6873501566f13c744efdd146f3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/13/2020
ms.locfileid: "83131998"
---
# <a name="data-protection-metrics-report-preview"></a>Bericht zu Datenschutzmetriken (Vorschau)

## <a name="what-is-the-data-protection-metrics-report"></a>Was genau ist der Bericht zu Datenschutzmetriken?
Der Bericht zu Datenschutzmetriken ist ein dedizierter Bericht, den [Power BI-Administratoren](../admin/service-admin-role.md) verwenden können, um die Verwendung und Annahme von Datenvertraulichkeitsbezeichnungen in ihrem Mandanten zu überwachen und zu verfolgen.

![Bericht zu Datenschutzmetriken](./media/service-security-data-protection-metrics-report/protection-metrics-seven-days-1.png)
 
Der Bericht enthält Folgendes:
* Ein gestapeltes Säulendiagramm (100 %), das die tägliche Verwendung der Vertraulichkeitsbezeichnung im Mandanten für die letzten 7, 30 oder 90 Tage anzeigt. Mithilfe dieses Diagramms können Sie sehr einfach die relative Verwendung der verschiedenen Bezeichnungstypen im Laufe der Zeit verfolgen.
* Ringdiagramme, die den aktuellen Zustand der Verwendung von Vertraulichkeitsbezeichnungen im Mandanten für Dashboards, Berichte, Datasets und Dataflows zeigen.
* Ein Link zum Cloud App Security-Portal, wo Power BI-Warnungen, gefährdete Benutzer, Aktivitätsprotokolle und andere Informationen verfügbar sind. Weitere Informationen finden Sie unter [Verwenden von Microsoft Cloud App Security-Steuerelementen in Power BI (Vorschauversion)](./service-security-using-microsoft-cloud-app-security-controls.md).

Der Bericht wird alle 24 Stunden aktualisiert.

## <a name="viewing-the-data-protection-metrics-report"></a>Anzeigen des Berichts zu Datenschutzmetriken

Sie müssen über eine [Power BI-Administratorrolle](../admin/service-admin-role.md) verfügen, um den Bericht zu öffnen und anzuzeigen.
Navigieren Sie zu **Einstellungen > Verwaltungsportal**, um den Bericht anzuzeigen, und wählen Sie **Schutzmetriken (Vorschau)** aus.

![Verwaltungsportal für Schutzmetriken](./media/service-security-data-protection-metrics-report/protection-metrics-admin-portal.png)
 
 
Wenn Sie den Bericht zu Datenschutzmetriken zum ersten Mal öffnen, kann das Laden des Berichts einige Sekunden dauern. Ein Bericht und ein Dataset mit dem Titel **Datenschutzmetriken (automatisch generiert)** werden in Ihrer privaten Umgebung unter „Mein Arbeitsbereich“ erstellt. Es wird empfohlen, den Bericht nicht hier anzusehen, weil es sich nicht um den vollständigen Bericht handelt. Sehen Sie sich den Bericht stattdessen wie oben beschrieben im Verwaltungsportal an.

> [!CAUTION]
> Ändern Sie auf jeden Fall den Bericht oder das Dataset nicht, da von Zeit zu Zeit neue Versionen des Berichts herausgebracht werden und alle Änderungen, die Sie am ursprünglichen Bericht vorgenommen haben, überschrieben werden, wenn Sie auf die neue Version aktualisieren.

## <a name="report-updates"></a>Berichtsaktualisierungen

Verbesserte Versionen des Berichts zu Datenschutzmetriken werden in regelmäßigen Abständen veröffentlicht. Wenn Sie den Bericht öffnen und eine neue Version verfügbar ist, werden Sie gefragt, ob Sie die neue Version öffnen möchten. Wenn Sie mit „Ja“ bestätigen, wird die neue Version des Berichts geladen und die alte Version überschrieben. Alle Änderungen, die Sie am alten Bericht und/oder Dataset vorgenommen haben, gehen verloren. Sie können sich dafür entscheiden, die neue Version nicht zu öffnen, aber in diesem Fall werden Sie nicht von den Verbesserungen der neuen Version profitieren. 
## <a name="notes-and-considerations"></a>Hinweise und Überlegungen
* Damit der Bericht zu Datenschutzmetriken erfolgreich erstellt werden kann, muss [Information Protection](./service-security-enable-data-sensitivity-labels.md) bei Ihrem Mandanten aktiviert sein, und [Vertraulichkeitsbezeichnungen sollten angewendet worden sein](../collaborate-share/service-security-apply-data-sensitivity-labels.md). 
* Ihre Organisation muss über die entsprechende [Cloud App Security-Lizenz](https://docs.microsoft.com/power-bi/admin/service-security-using-microsoft-cloud-app-security-controls#microsoft-cloud-app-security-licensing) verfügen, um auf Informationen zu Cloud App Security zugreifen zu können.
* Wenn Sie sich entscheiden, Informationen aus dem Bericht zu Datenschutzmetriken für einen Benutzer freizugeben, der kein Power BI-Administrator ist, beachten Sie, dass dieser Bericht vertrauliche Informationen über Ihre Organisation enthält.
* Der Bericht zu Datenschutzmetriken ist ein besonderer Bericht und wird nicht in den Listen „Für mich freigegeben“, „Zuletzt geöffnet“ und „Favoriten“ angezeigt.
* Der Bericht zu Datenschutzmetriken steht [externen Benutzern (Azure Active Directory B2B-Gastbenutzern)](../admin/service-admin-azure-ad-b2b.md) nicht zur Verfügung.
## <a name="next-steps"></a>Weitere Schritte
* [Datenschutz in Power BI (Vorschauversion)](./service-security-data-protection-overview.md)
* [Verwenden von Microsoft Cloud App Security-Steuerelementen in Power BI (Vorschauversion)](./service-security-using-microsoft-cloud-app-security-controls.md)
* [Grundlegendes zur Dienstadministratorrolle in Power BI](../admin/service-admin-role.md)
* [Aktivieren von Vertraulichkeitsbezeichnungen für Daten in Power BI](./service-security-enable-data-sensitivity-labels.md)