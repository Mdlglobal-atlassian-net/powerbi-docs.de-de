---
title: Verwenden von Dataflows mit lokalen Datenquellen
description: Erfahren Sie, wie Sie lokale Daten in Dataflows verwenden.
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 01/08/2020
ms.author: davidi
LocalizationGroup: Data from files
ms.openlocfilehash: 1008cf34cd09d8039107794e10dcef845ec35110
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/13/2020
ms.locfileid: "83322422"
---
# <a name="using-dataflows-with-on-premises-data-sources"></a>Verwenden von Dataflows mit lokalen Datenquellen

Mit **Dataflows** können Sie eine Sammlung von Daten aus verschiedenen Quellen erstellen, bereinigen, transformieren und anschließend im Power BI-Speicher laden. Beim Erstellen von Dataflows sollten Sie lokale Datenquellen verwenden. In diesem Artikel werden die Anforderung zum Erstellen von Dataflows und die Erfordernis erläutert, dass Ihr **Enterprise-Gateway** konfiguriert werden muss, um diese Verbindungen zu aktivieren.

![Dataflows und Gateways](media/service-dataflows-onpremises-gateways/onpremises-gateways_01.png)

## <a name="configuring-an-enterprise-gateway-for-use-with-dataflows"></a>Konfigurieren eines Enterprise-Gateways für die Verwendung mit Dataflows

Um einen Dataflow mit einem Gateway zu erstellen, muss der Benutzer der Administrator des Enterprise-Gateway sein oder der Administrator muss die Datenquelle, die er verwenden möchte, für den Benutzer freigegeben haben. 


> [!NOTE]
> Dataflows werden nur unter Verwendung von Enterprise-Gateways unterstützt.

## <a name="using-an-on-premises-data-source-in-a-dataflow"></a>Verwendung einer lokalen Datenquelle in einem Dataflow

Wenn Sie einen Dataflow erstellen, wählen Sie eine lokale Datenquelle aus der Liste der Datenquellen aus, wie in der folgenden Abbildung dargestellt wird.

![Auswählen einer lokalen Datenquelle](media/service-dataflows-onpremises-gateways/onpremises-gateways_02a.png)

Nachdem Sie Ihre Auswahl getroffen haben, werden Sie aufgefordert, die Verbindungsdetails für das Enterprise-Gateway bereitzustellen, die für den Zugriff auf die lokalen Daten verwendet werden. Sie müssen das Gateway selbst auswählen und Anmeldeinformationen für das ausgewählte Gateway angeben.

![Bereitstellen von Verbindungsdetails](media/service-dataflows-onpremises-gateways/onpremises-gateways_03.png)

## <a name="monitoring-your-gateway"></a>Überwachen des Gateways

Sie können Ihr Enterprise-Gateway für einen Dataflow auf die gleiche Weise überwachen, auf die Sie Gateways für ein Dataset überwachen.

Auf dem Bildschirm der Datafloweinstellungen in Power BI können Sie den Gatewaystatus eines Dataflows überwachen und dem Dataflow ein Gateway zuweisen, wie in der folgenden Abbildung dargestellt wird.

![Überwachen des Gateways](media/service-dataflows-onpremises-gateways/onpremises-gateways_01.png)

## <a name="changing-a-gateway"></a>Ändern eines Gateways

Sie können das Enterprise-Gateway, das für einen bestimmten Dataflow verwendet wird, auf zwei Arten ändern:

1. **Über das Erstellungstool**: Sie können mit dem Erstellungstool für Dataflows das Gateway ändern, das all Ihren Abfragen zugewiesen ist.

    > [!NOTE]
    > Der Dataflow sucht über das neue Gateway nach den erforderlichen Datenquellen oder erstellt diese. Falls dies nicht möglich ist, können Sie das Gateway erst ändern, wenn alle benötigten Dataflows über das ausgewählte Gateway verfügbar sind.

2. **Über den Einstellungsbildschirm**: Sie können das zugewiesene Gateway mit dem Einstellungsbildschirm für den Dataflow im Power BI-Dienst ändern.

Weitere Informationen zu Enterprise-Gateways finden Sie unter [Lokales Datengateway](../connect-data/service-gateway-onprem.md).

## <a name="considerations-and-limitations"></a>Überlegungen und Einschränkungen

Es gibt einige bekannte Einschränkungen zur Verwendung von Enterprise-Gateways und Dataflows:

* Jeder Dataflow kann nur ein Gateway verwenden. Daher sollten alle Abfragen über das gleiche Gateway konfiguriert werden.
* Eine Änderung des Gateways wirkt sich auf den gesamten Dataflow aus.
* Wenn mehrere Gateways erforderlich sind, wird empfohlen, mehrere Dataflows zu erstellen (eines für jedes Gateway) und die Compute- oder Entitätsverweisfunktionen zur Datenvereinheitlichung zu verwenden.
* Dataflows werden nur unter Verwendung von Enterprise-Gateways unterstützt. Persönliche Gateways stehen nicht in Dropdownlisten oder auf Einstellungsbildschirmen zur Auswahl zur Verfügung.


## <a name="next-steps"></a>Weitere Schritte

Dieser Artikel enthält Informationen zur Verwendung einer lokalen Datenquelle für Dataflows und zur Verwendung und Konfiguration von Gateways, um auf diese Daten zuzugreifen. Die folgenden Artikel können ebenfalls hilfreich sein:

* [Self-Service-Datenaufbereitung in Power BI (Vorschau)](service-dataflows-overview.md)
* [Erstellen und Verwenden von Dataflows in Power BI](service-dataflows-create-use.md)
* [Using computed entities on Power BI Premium (Verwenden berechneter Entitäten in Power BI Premium)](service-dataflows-computed-entities-premium.md)
* [Developer resources for Power BI dataflows (Entwicklerressourcen für Power BI-Datenflüsse)](service-dataflows-developer-resources.md)

Weitere Informationen zu Power Query und zur geplanten Aktualisierung finden Sie in den folgenden Artikeln:
* [Abfrageübersicht in Power BI Desktop](desktop-query-overview.md)
* [Konfigurieren geplanter Aktualisierungen](../connect-data/refresh-scheduled-refresh.md)

Weitere Informationen zum Common Data Model finden Sie im Übersichtsartikel:
* [Was ist das Common Data Model?](https://docs.microsoft.com/powerapps/common-data-model/overview)
