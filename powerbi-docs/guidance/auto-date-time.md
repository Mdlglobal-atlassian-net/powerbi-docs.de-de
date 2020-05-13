---
title: Anleitung zur automatischen Angabe von Datum/Uhrzeit in Power BI Desktop
description: Leitfaden zur Verwendung der Option „Autom. Datum/Uhrzeit“ in Power BI Desktop.
author: peter-myers
manager: asaxton
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 10/23/2019
ms.author: v-pemyer
ms.openlocfilehash: a143a9b158d8a00fc129953a601f9e4c8f19875f
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/13/2020
ms.locfileid: "83279708"
---
# <a name="auto-datetime-guidance-in-power-bi-desktop"></a>Anleitung zur automatischen Angabe von Datum/Uhrzeit in Power BI Desktop

Dieser Artikel richtet sich an Datenmodellierer, die Importmodelle oder zusammengesetzte Modelle in Power BI Desktop entwickeln. Der Artikel enthält Anleitungen, Empfehlungen und Überlegungen zur Verwendung der Power BI Desktop-Option _Autom. Datum/Uhrzeit_ in bestimmten Situationen. Eine Übersicht und allgemeine Einführung in die Option _Autom. Datum/Uhrzeit_ finden Sie unter [Automatische Angabe von Datum/Uhrzeit in Power BI Desktop](../transform-model/desktop-auto-date-time.md).

Die Option _Autom. Datum/Uhrzeit_ liefert praktische, schnelle und leicht zu verwendende Zeitintelligenzfunktionen. Autoren von Berichten können beim Filtern, Gruppieren und für den Drilldown in Kalenderzeiträumen Zeitintelligenzfunktionen nutzen.

## <a name="considerations"></a>Überlegungen

Die folgende Auflistung enthält Überlegungen – und mögliche Einschränkungen – in Bezug auf die Option _Autom. Datum/Uhrzeit_.

- **Gilt für alle Tabellen oder keine**: Wenn die Option _Autom. Datum/Uhrzeit_ aktiviert ist, gilt sie für alle Datumsspalten (außer berechnete Spalten) in Importtabellen, die sich nicht auf der Seite &quot;n&quot; einer Beziehung befinden. Sie kann nicht für einzelne Spalten aktiviert oder deaktiviert werden.
- **Nur Kalenderzeiträume**: Die Spalten zu Jahr und Quartal beziehen sich auf Kalenderzeiträume. Das bedeutet, dass das Jahr am 1. Januar beginnt und am 31. Dezember endet. Es gibt keine Möglichkeit, Jahresbeginn und -ende anzupassen.
- **Anpassung**: Es ist nicht möglich, die Werte anzupassen, die zur Beschreibung von Zeiträumen verwendet werden. Darüber hinaus ist es nicht möglich, zusätzliche Spalten einzufügen, um andere Zeiträume wie z. B. Wochen zu beschreiben.
- **Jahresfilterung**: Die Werte der Spalten für **Quartal**, **Monat** und **Tag** enthalten keinen Wert für das Jahr. Die Spalte für den **Monat** beispielsweise enthält nur die Monatsnamen (Januar, Februar usw.). Die Werte sind nicht vollständig selbstbeschreibend, und in einigen Berichtsentwürfen wird der Kontext des Jahresfilters möglicherweise nicht mitgeteilt.

    Daher ist es wichtig, Filterungen oder Gruppierungen in der Spalte für das **Jahr** auszuführen. Beim Ausführen eines Drilldowns mithilfe der Hierarchie wird nach Jahr gefiltert, sofern die Ebene **Jahr** nicht absichtlich entfernt wurde. Wenn keine Filterung oder Gruppierung nach Jahr vorhanden ist, würde beispielsweise eine Gruppierung nach Monat Werte für diesen Monat über alle Jahre hinweg zusammenfassen.
- **Filterung nach Daten in einer einzelnen Tabellen**: Da jede Datumsspalte eine eigene (verborgene) Tabelle mit automatischer Datums-/Uhrzeitangabe erzeugt, ist es nicht möglich, einen Zeitfilter auf eine Tabelle anzuwenden und diesen an mehrere Modelltabellen weiterzugeben. Eine solche Filterung ist eine gängige Anforderung bei der Modellierung von Berichten für mehrere Themenbereiche (Faktentabellen) wie z. B. Vertrieb und Vertriebsbudget. Beim Verwenden der Option „Autom. Datum/Uhrzeit“ muss der Autor des Berichts Filter auf jede einzelne Datumsspalte anwenden.
- **Modellgröße**: Jede Datumsspalte, die eine verborgene Tabelle mit automatischer Datums-/Uhrzeitangabe erzeugt, erhöht die Modellgröße und verlängert zudem die Datenaktualisierung.
- **Andere Berichterstellungstools:** Es ist nicht möglich, mit automatischen Datums-/Uhrzeittabellen zu arbeiten, wenn Sie das Feature [In Excel analysieren](../collaborate-share/service-analyze-in-excel.md) verwenden oder die Verbindung zum Modell mit einem anderen Designer als dem Power BI-Berichts-Designer hergestellt haben.

## <a name="recommendations"></a>Empfehlungen

Es empfiehlt sich, die Option _Autom. Datum/Uhrzeit_ nur dann zu aktivieren, wenn Sie mit Kalenderzeiträumen arbeiten und Ihr Modell in Bezug auf die Uhrzeit keine komplexen Anforderungen enthält. Diese Option kann auch praktisch sein, wenn Sie Ad-hoc-Modelle erstellen, oder Durchsuchungs- oder Profilerstellungsfunktionen für Daten ausführen.

Wenn Ihre Datenquelle bereits eine Dimensionstabelle für Daten definiert, sollte diese Tabelle verwendet werden, um die Uhrzeit innerhalb Ihrer Organisation einheitlich zu definieren. Dies ist sicherlich der Fall, wenn es sich bei Ihrer Datenquelle um ein Data Warehouse handelt. Andernfalls können Sie Datumstabellen in Ihrem Modell mithilfe der DAX-Funktionen [CALENDAR](/dax/calendar-function-dax) oder [CALENDARAUTO](/dax/calendarauto-function-dax) generieren. Dann können Sie berechnete Spalten hinzufügen, um die bekannten Anforderungen an Uhrzeitfilterung und -gruppierung zu unterstützen. Mit einem solchen Entwurf ist es ggf. möglich, eine einzelne Datumstabelle zu erstellen, die an alle Faktentabellen weitergegeben wird. So können Sie möglicherweise eine einzelne Tabelle erhalten, auf die Sie Uhrzeitfilter anwenden können. Weitere Informationen zum Erstellen von Datumstabellen finden Sie im Artikel [Festlegen und Verwenden von Datumstabellen in Power BI Desktop](../transform-model/desktop-date-tables.md).

Wenn die automatische Angabe von Datum und Uhrzeit für Ihre Projekte nicht relevant ist, empfiehlt es sich, die globale Option _Autom. Datum/Uhrzeit_ zu deaktivieren. So wird sichergestellt, dass die Option _Autom. Datum/Uhrzeit_ durch neue von Ihnen erstellte Power BI Desktop-Dateien nicht aktiviert wird.

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zu diesem Artikel finden Sie in den folgenden Ressourcen:

- [Automatische Angabe von Datum/Uhrzeit in Power BI Desktop](../transform-model/desktop-auto-date-time.md)
- [Festlegen und Verwenden von Datumstabellen in Power BI Desktop](../transform-model/desktop-date-tables.md)
- Haben Sie Fragen? [Stellen Sie Ihre Frage in der Power BI-Community.](https://community.powerbi.com/)
- Vorschläge? [Einbringen von Ideen zur Verbesserung von Power BI](https://ideas.powerbi.com/)
