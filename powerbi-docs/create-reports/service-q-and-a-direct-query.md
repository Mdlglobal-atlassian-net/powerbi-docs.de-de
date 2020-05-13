---
title: Verwenden von Q&A mit Liveverbindungen in Power BI
description: Dokumentation für die Verwendung von Power BI Q&A-Abfragen in natürlicher Sprache mit Liveverbindungen mit Analysis Services-Daten und dem lokalen Datengateway.
author: maggiesMSFT
ms.reviewer: mihart
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 10/16/2018
ms.author: maggies
LocalizationGroup: Ask questions of your data
ms.openlocfilehash: 3544a5330a21036e0ddecb351fd67b424ca6ebc7
ms.sourcegitcommit: bfc2baf862aade6873501566f13c744efdd146f3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/13/2020
ms.locfileid: "83348871"
---
# <a name="enable-qa-for-live-connections-in-power-bi"></a>Aktivieren von Q&A für Liveverbindungen in Power BI
## <a name="what-is-the-on-premises-data-gateway--what-is-a-live-connection"></a>Was ist das lokale Datengateway?  Was ist eine Liveverbindung?
Sie können Datasets in Power BI importieren oder eine Liveverbindung zu den Daten herstellen. Über eine Liveverbindung verwendete Datasets werden häufig als „lokal“ bezeichnet. Die Liveverbindungen werden mit einem [Gateway](../connect-data/service-gateway-onprem.md) verwaltet, und die Übermittlung der Daten und Abfragen erfolgt über Liveabfragen.

## <a name="qa-for-on-premises-data-gateway-datasets"></a>Q&A für Datasets mit Zugriff über das lokale Datengateway
Wenn Sie F&A mit Datasets verwenden möchten, auf die Sie über ein Gateway zugreifen, müssen Sie die Datasets zuerst aktivieren.

Nach der Aktivierung erstellt Power BI einen Index für Ihre Datenquelle und lädt eine Teilmenge der Daten in Power BI hoch, um das Stellen von Fragen zu ermöglichen. Das Erstellen des anfänglichen Index kann mehrere Minuten dauern. Dieser wird anschließend von Power BI verwaltet und bei Datenänderungen automatisch aktualisiert. Das F&A-Feature verhält sich mit diesen Datasets genauso wie mit in Power BI veröffentlichten Daten. In beiden Fällen wird der vollständige in F&A verfügbare Feature-Satz unterstützt.

Wenn Sie in Power BI Fragen stellen, ermittelt F&A die beste Visualisierung bzw. den besten Bericht, um Ihre Fragen mithilfe eines Index Ihres Datasets zu beantworten. Nachdem die bestmögliche Antwort ermittelt wurde, ruft Q&A mithilfe von DirectQuery Livedaten aus der Datenquelle über das Gateway ab, um Diagrammen und Grafiken zu füllen. Dadurch zeigt Power BI Q&A stets die aktuellen Daten direkt aus der zugrunde liegenden Datenquelle an.

Da Power BI F&A die Text- und Schemawerte aus Ihrer Datenquelle verwenden, um zu ermitteln, wie das zugrunde liegende Modell für Antworten abgefragt werden soll, ist bei Suchen nach speziellen neuen oder gelöschten Textwerten (wie Fragen im Zusammenhang mit einem neu hinzugefügten Textdatensatz für einen Kunden) wichtig, dass der Index die aktuellen Werte enthält. Power BI aktualisiert den Text- und Schemaindex automatisch innerhalb von 60 Minuten nach einer Datenänderung.

Weitere Informationen finden Sie unter:

* Was ist das [lokale Datengateway](../connect-data/service-gateway-onprem.md)?
* [Power BI Q&A für Nutzer](../consumer/end-user-q-and-a.md)

## <a name="enable-qa"></a>Aktivieren von F&A
Nachdem Sie das Datengateway eingerichtet haben, stellen Sie aus Power BI eine Verbindung mit Ihren Daten her.  Erstellen Sie ein Dashboard mit Ihren lokalen Daten oder laden Sie eine PBIX-Datei hoch, die lokale Daten verwendet.  Möglicherweise enthalten Ihre Dashboards, Berichte und Datasets auch bereits lokale Daten, die für Sie freigegeben wurden.

1. Klicken Sie rechts oben auf das Zahnradsymbol ![Zahnradsymbol](media/service-q-and-a-direct-query/power-bi-cog.png) und dann auf **Einstellungen**.
   
   ![Einstellungsmenü](media/service-q-and-a-direct-query/powerbi-settings.png)
2. Wählen Sie **Datasets**, und wählen Sie das für Q&A aktivierte Dataset aus.
   
   ![Anzeige „Datasets“ im Menü „Einstellungen“](media/service-q-and-a-direct-query/power-bi-q-and-a-settings.png)
3. Erweitern Sie **Q&A**, aktivieren Sie das Kontrollkästchen **Q&A für dieses Dataset aktivieren**, und wählen Sie **Anwenden**.
   
    ![Erweiterter Q&A-Bereich](media/service-q-and-a-direct-query/power-bi-qna-dataset-direct-query.png)

## <a name="what-data-is-cached-and-how-is-privacy-protected"></a>Welche Daten werden zwischengespeichert, und wie werden Daten geschützt?
Wenn Sie F&A für Ihre lokalen Daten aktivieren, wird eine Teilmenge der Daten im Dienst zwischengespeichert. Durch die Zwischenspeicherung wird eine akzeptable Leistung von Q&A sichergestellt. Werte, die länger als 24 Zeichen sind, werden in Power BI nicht zwischengespeichert. Wenn Sie F&A deaktivieren (durch Deaktivieren von **Turn on Q&A for this dataset**) oder Ihr Dataset löschen, wird der Cache innerhalb weniger Stunden gelöscht.

## <a name="considerations-and-troubleshooting"></a>Zu beachtende Aspekte und Problembehandlung
Die Funktion weist einige Einschränkungen auf:

* Das Feature ist zunächst nur für tabellarische SQL Server 2016 Analysis Services-Datenquellen verfügbar. Das Feature wurde für die Zusammenarbeit mit tabellarischen Daten optimiert. Die Q&A-Funktion wird noch nicht für mehrere Dimensionen unterstützt. Im Lauf der Zeit werden weitere vom lokalen Datengateway unterstützte Datenquellen eingeführt.
* Die in SQL Server Analysis Services definierte vollständige Unterstützung der Sicherheit auf Zeilenebene steht nicht von Beginn an zur Verfügung. Bei der Eingabe von Fragen in Q&A können durch die „automatische Vervollständigung“ Zeichenfolgenwerte angezeigt werden, auf die der Benutzer keinen Zugriff hat. Die im Modell definierte Sicherheit auf Zeilenebene wird jedoch für Berichts- und Diagrammvisualisierungen respektiert, wobei keine zugrunde liegenden numerischen Daten angezeigt werden können. Optionen zum Steuern dieses Verhalten werden in kommenden Updates veröffentlicht.
* Die Sicherheit auf Objektebene wird nicht unterstützt. Q&A berücksichtigt die Sicherheit auf Objektebene nicht und kann Tabellen- oder Spaltennamen für Benutzer offenlegen, die keinen Zugriff darauf haben. Sie sollten die Sicherheit auf Zeilenebene aktivieren, um sicherzustellen, dass Datenwerte angemessen gesichert sind. 
* Liveverbindungen werden nur mit dem lokalen Datengateway unterstützt. Daher kann dieses Feature nicht mit dem persönlichen Gateway verwendet werden.

## <a name="next-steps"></a>Weitere Schritte

- [Lokales Datengateway](../connect-data/service-gateway-onprem.md)  
- [Verwalten Ihrer Datenquelle – Analysis Services](../connect-data/service-gateway-enterprise-manage-ssas.md)  
- [Grundlegende Konzepte für Designer im Power BI-Dienst](../fundamentals/service-basic-concepts.md)  
- [Übersicht über Power BI Q&A](../consumer/end-user-q-and-a.md)  

Weitere Fragen? [Stellen Sie Ihre Frage in der Power BI-Community.](https://community.powerbi.com/)
