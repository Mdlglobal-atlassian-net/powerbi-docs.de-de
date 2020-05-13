---
title: Leitfaden zur Problembehandlung bei Beziehungen
description: Hier finden Sie Informationen zur Problembehandlung bei Modellbeziehungen.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 03/02/2020
ms.author: v-pemyer
ms.openlocfilehash: 7ccff80391ed0625aac063af3bf7a86b83cd7e85
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/13/2020
ms.locfileid: "83278121"
---
# <a name="relationship-troubleshooting-guidance"></a>Leitfaden zur Problembehandlung bei Beziehungen

Dieser Artikel ist an Modellierer von Daten gerichtet, die mit Power BI Desktop arbeiten. Er bietet Informationen zur Behebung bestimmter Probleme, die bei der Entwicklung von Modellen und Berichten auftreten können.

[!INCLUDE [relationships-prerequisite-reading](includes/relationships-prerequisite-reading.md)]

## <a name="troubleshooting-checklist"></a>Checkliste zur Problembehandlung

Wenn ein Berichtsvisual für die Verwendung von Feldern aus zwei (oder mehr) Tabellen konfiguriert ist und nicht das richtige Ergebnis (oder gar kein Ergebnis) zeigt, liegt das Problem möglicherweise bei den Modellbeziehungen.

Arbeiten Sie in diesem Fall die folgende allgemeine Checkliste zur Problembehandlung durch. Sie können die Punkte der Checkliste nacheinander durchgehen, bis Sie das Problem identifiziert haben.

1. Ändern Sie das Visual in eine Tabelle oder Matrix, oder öffnen Sie den Bereich „Daten anzeigen“ – Probleme lassen sich leichter beheben, wenn Sie das Abfrageergebnis sehen können.
1. Wenn ein leeres Abfrageergebnis vorliegt, wechseln Sie zur Datenansicht, und überprüfen Sie, ob in den Tabellen Zeilen mit Daten geladen wurden.
1. Wechseln Sie zur Modellansicht – hier können Sie die Beziehungen und ihre Eigenschaften einfach und schnell erkennen.
1. Überprüfen Sie, ob zwischen den Tabellen Beziehungen vorhanden sind.
1. Überprüfen Sie, ob die Kardinalitätseigenschaften richtig konfiguriert sind. Diese könnten falsch sein, wenn eine n-Seite eindeutige Werte enthält und fälschlicherweise als 1-Seite konfiguriert wurde.
1. Überprüfen Sie, ob die Beziehungen aktiv sind (durchgezogene Linie).
1. Überprüfen Sie, ob die Filterrichtungen eine Weitergabe unterstützen (interpretieren Sie die Pfeilspitzen).
1. Überprüfen Sie, ob die richtigen Spalten in Beziehung gesetzt wurden – wählen Sie die Beziehung aus, oder halten Sie den Mauszeiger darauf, um die zugehörigen Spalten anzuzeigen.
1. Überprüfen Sie, ob die zugehörigen Spaltendatentypen übereinstimmen oder zumindest kompatibel sind. Es ist möglich, eine Textspalte mit einer ganzzahligen Spalte in Beziehung zu setzen, aber die Filter finden keine Übereinstimmungen, die weitergegeben werden können.
1. Wechseln Sie zur Datenansicht, und überprüfen Sie, ob in den zugehörigen Spalten übereinstimmende Werte gefunden werden können.

## <a name="troubleshooting-guide"></a>Handbuch zur Problembehandlung

Im Folgenden finden Sie eine Liste aller Probleme sowie mögliche Lösungen.

|Problem|Mögliche Ursachen|
|---------|---------|
|Das Visual zeigt kein Ergebnis an.|– In das Modell müssen noch Daten geladen werden.<br />– Im Filterkontext sind keine Daten vorhanden.<br />– Die Sicherheit auf Zeilenebene wird erzwungen.<br />– Beziehungen werden zwischen Tabellen nicht weitergegeben: _Befolgen Sie die oben aufgeführte Checkliste_.<br />– Die Sicherheit auf Zeilenebene wird erzwungen, aber eine bidirektionale Beziehung ist nicht für die Weitergabe aktiviert: Informationen hierzu finden Sie unter [Sicherheit auf Zeilenebene (RLS) mit Power BI Desktop](../create-reports/desktop-rls.md).|
|Das Visual zeigt für jede Gruppierung denselben Wert an. |– Es sind keine Beziehungen vorhanden.<br />– Beziehungen werden zwischen Tabellen nicht weitergegeben: _Befolgen Sie die oben aufgeführte Checkliste_.|
|Das Visual zeigt Ergebnisse an, diese sind aber nicht richtig.|– Das Visual ist falsch konfiguriert.<br />– Die Measurelogik ist falsch.<br />– Die Modelldaten müssen aktualisiert werden.<br />– Die Quelldaten sind falsch.<br />– Zwischen den Spalten wurde eine falsche Beziehung hergestellt (Beispiel: Die Spalte **ProductID** wurde der Spalte **CustomerID** zugeordnet).<br />– Es handelt sich um eine Beziehung zwischen zwei DirectQuery-Tabellen, und die 1-Seite einer Beziehung enthält doppelte Werte.|
|Es werden LEERE Gruppierungen oder Slicer- bzw. Filterelemente angezeigt, und die Quellspalten enthalten keine LEEREN Werte.|– Es handelt sich um eine starke Beziehung und die Spalte der n-Seite enthält Werte, die in der Spalte der 1-Seite nicht gespeichert sind: Informationen hierzu finden Sie unter [Modellieren von Beziehungen in Power BI Desktop (starke Beziehungen)](../transform-model/desktop-relationships-understand.md#strong-relationships).<br />– Es handelt sich um eine starke 1:1-Beziehung, und zugeordnete Spalten enthalten LEERE Werte: Informationen hierzu finden Sie unter [Modellieren von Beziehungen in Power BI Desktop (starke Beziehungen)](../transform-model/desktop-relationships-understand.md#strong-relationships).<br />– Eine Spalte der n-Seite einer inaktiven Beziehung enthält LEERE Werte oder Werte, die auf der 1-Seite nicht gespeichert sind.|
|Im Visual fehlen Daten.|– Es wurden falsche oder unerwartete Filter angewendet.<br />– Die Sicherheit auf Zeilenebene wird erzwungen.<br />– Es handelt sich um eine schwache Beziehung, und in zugeordneten Spalten befinden sich LEERE Werte, oder es liegen Datenintegritätsprobleme vor: Informationen hierzu finden Sie unter [Modellieren von Beziehungen in Power BI Desktop (schwache Beziehungen)](../transform-model/desktop-relationships-understand.md#weak-relationships).<br />– Es handelt sich um eine Beziehung zwischen zwei DirectQuery-Tabellen, die Beziehung ist so konfiguriert, dass [referenzielle Integrität vorausgesetzt wird](../transform-model/desktop-relationships-understand.md#assume-referential-integrity), aber es liegen Probleme mit der Datenintegrität vor (nicht übereinstimmende Werte in zugeordneten Spalten).|
|Die Sicherheit auf Zeilenebene wird nicht ordnungsgemäß erzwungen.|– Beziehungen werden zwischen Tabellen nicht weitergegeben: _Befolgen Sie die oben aufgeführte Checkliste_.<br />– Die Sicherheit auf Zeilenebene wird erzwungen, aber eine bidirektionale Beziehung ist nicht für die Weitergabe aktiviert: Informationen hierzu finden Sie unter [Sicherheit auf Zeilenebene (RLS) mit Power BI Desktop](../create-reports/desktop-rls.md).|
|||

## <a name="next-steps"></a>Weitere Schritte

Weitere Informationen zu diesem Artikel finden Sie in den folgenden Ressourcen:

- [Modellieren von Beziehungen in Power BI Desktop](../transform-model/desktop-relationships-understand.md)
- Fragen? [Stellen Sie Ihre Frage in der Power BI-Community.](https://community.powerbi.com/)
- Vorschläge? [Einbringen von Ideen zur Verbesserung von Power BI](https://ideas.powerbi.com/)
