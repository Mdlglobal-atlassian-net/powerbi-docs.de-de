---
title: Planen von Berichten im Berichts-Generator von Power BI
description: Mit dem Power BI Report Builder können Sie viele Arten von paginierten Berichten erstellen. Die Grundlage für einen hilfreichen und einfach verständlichen Bericht ist seine vorherige Planung.
ms.date: 07/25/2019
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.assetid: 79113505-1ce8-4f8c-9260-d861838f7813
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 30ab632d11befd34ff9a234e441b345c696fb54d
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "78922986"
---
# <a name="planning-a-report-in-power-bi-report-builder"></a>Planen von Berichten im Berichts-Generator von Power BI

Mit dem Power BI Report Builder können Sie viele Arten von paginierten Berichten erstellen. Sie können beispielsweise Berichte erstellen, in denen eine Zusammenfassung von oder detaillierte Informationen zu Umsatzdaten, Marketing- und Umsatztrends, Funktionsberichte oder Dashboards angezeigt werden. Sie können auch Berichte erstellen, die Text im Rich Text Format (RTF) nutzen, z. B. für Verkaufsaufträge, Produktkataloge oder Serienbriefe. Alle diese Berichte werden mithilfe verschiedener Kombinationen derselben grundlegenden Bausteine im Berichts-Generator erstellt. Die Grundlage für einen hilfreichen und einfach verständlichen Bericht ist seine vorherige Planung. Diese Dinge sollten Sie berücksichtigen, bevor Sie loslegen:  
  
## <a name="in-what-format-do-you-want-the-report-to-appear"></a>In welchem Format soll der Bericht angezeigt werden?
  
Berichte können online in einem Browser gerendert werden, z. B. über das Power BI-Portal, oder in andere Formate exportiert werden, z. B. Excel, Word oder PDF. Die endgültige Form des Berichts ist ein wichtiger Gesichtspunkt, weil nicht alle Funktionen in sämtlichen Exportformaten verfügbar sind. 
  
## <a name="in-what-structure-do-you-want-to-present-the-data"></a>In welcher Struktur sollen die Daten angezeigt werden?
  
Sie können Daten als Tabelle, Matrix (ähnlich eines Kreuztabellen- oder PivotTable-Berichts), Diagramm, als Freiformstrukturen oder einer beliebigen Kombination dieser Möglichkeiten anzeigen lassen. Weitere Informationen finden Sie unter [Tables, Matrices, and Lists in Power BI Report Builder (Tabellen, Matrizen und Listen im Berichts-Generator in Power BI)](report-builder-tables-matrices-lists.md).  
  
## <a name="how-do-you-want-your-report-to-look"></a>Wie soll Ihr Bericht aussehen?
  
Der Berichts-Generator stellt viele Berichtselemente zur Verfügung, die Sie Ihrem Bericht hinzufügen können, z. B. um die Lesbarkeit zu vereinfachen, wichtige Informationen hervorzuheben oder die Zielgruppe beim Navigieren im Bericht zu unterstützen. Wenn Sie wissen, wie der Bericht aussehen soll, können Sie bestimmen, ob Sie Berichtselemente wie Textfelder, Rechtecke, Bilder und Linien benötigen. Möglicherweise sollen auch Elemente angezeigt oder ausgeblendet werden, soll eine Dokumentstruktur hinzugefügt, sollen Drillthroughberichte oder Unterberichte aufgenommen oder Links zu anderen Berichten erstellt werden.   
  
## <a name="should-the-data-be-filtered"></a>Sollten die Daten gefiltert werden?
  
Vielleicht möchten Sie auch, dass der Bericht nur bestimmte Benutzer oder bestimmte Speicherorte abdeckt, oder möglicherweise auch nur einen bestimmten Zeitraum. Zum Filtern der Berichtsdaten verwenden Sie Parameter, um nur die gewünschten Daten abzurufen und anzuzeigen. Weitere Informationen finden Sie unter [Report parameters in Power BI Report Builder (Berichtsparameter im Berichts-Generator von Power BI)](paginated-reports-parameters.md).  
  
## <a name="do-you-need-to-create-calculations"></a>Müssen Berechnungen erstellt werden? 
  
Manchmal enthalten Ihre Datenquelle und Datasets nicht genau die Felder, die Sie für den Bericht benötigen. In dieser Situation müssen Sie möglicherweise eigene berechnete Felder erstellen. Beispielsweise möchten Sie vielleicht den Preis pro Einheit mit der Menge multiplizieren, um den Umsatz eines einzelnen Artikels zu erhalten. Ausdrücke werden auch verwendet, um bedingte Formatierung und andere erweiterte Funktionen bereitzustellen. Weitere Informationen finden Sie unter [Ausdrücke im Berichts-Generator von Power BI](report-builder-expressions.md).  
  
## <a name="do-you-want-to-hide-report-items-initially"></a>Sollen Berichtselemente anfangs ausgeblendet sein?
  
Überlegen Sie sich, ob Sie möchten, dass Berichtselemente ausgeblendet werden, einschließlich Datenbereichen und Gruppen und Spalten, wenn der Bericht das erste Mal ausgeführt wird. Beispiel: Sie können anfänglich eine zusammenfassende Tabelle darstellen und danach einen Drilldown auf die detaillierten Daten durchführen. 
  
## <a name="how-are-you-going-to-deliver-your-report"></a>Wie soll Ihr Bericht zugestellt werden?  
  
Sie können Ihren Bericht auf Ihrem lokalen Computer speichern und mit der Arbeit daran fortfahren oder ihn lokal zu Ihrer eigenen Information ausführen. Um den Bericht jedoch mit anderen Benutzern zu teilen, müssen Sie ihn in Power BI speichern. Durch das Speichern in Power BI können andere ihn jederzeit ausführen. Alternativ können Sie ein Abonnement und eine E-Mail-Zustellung des Berichts an andere Personen einrichten. Wenn Sie möchten, können Sie den Bericht in einem bestimmten Exportformat zustellen lassen. 
  
## <a name="next-steps"></a>Weitere Schritte

- [Was sind paginierte Berichte in Power BI Premium? (Vorschau)](paginated-reports-report-builder-power-bi.md)
