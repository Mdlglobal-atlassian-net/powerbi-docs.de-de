---
title: Problembehandlung bei geschachtelten Werten im Power BI-Dienst, die als Text zurückgegeben werden
description: Hier erfahren Sie, wie Sie Probleme mit geschachtelten Werten beheben können, die in eine Zeichenfolge konvertiert werden, wenn falsche Datenschutzeinstellungen für die Datenquelle verwendet werden.
author: cpopell
ms.reviewer: ''
ms.custom: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: troubleshooting
ms.date: 6/4/2019
ms.author: gepopell
LocalizationGroup: Reports
ms.openlocfilehash: ab40ca9c415dacf52f4d82eb2c157d57aef92f93
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/13/2020
ms.locfileid: "83332772"
---
# <a name="troubleshooting-nested-values-returned-as-text-in-power-bi-service"></a>Problembehandlung bei geschachtelten Werten im Power BI-Dienst, die als Text zurückgegeben werden

## <a name="cause"></a>Ursache

Bisher kam es vor, dass ein Power BI-Bericht auf dem Desktop problemlos aktualisiert werden konnte, es im Power BI-Dienst aber zu Problemen kam, und eine Fehlermeldung wie „Der Wert „[Table]“ kann nicht in den Typ „Table“ konvertiert werden.“ ausgegeben wurde. Einer der Gründe für diesen Fehler ist der, dass geschachtelte, nicht-skalare Werte (z.B. Tabellen, Datensätze, Listen und Funktionen) automatisch in Textwerte konvertiert werden (z.B. „[Table]“ oder „[Record]“), wenn die Datenschutzfirewall eine Datenquelle puffert.

Da der Power BI-Dienst es nun unterstützt, Datenschutzebenen festzulegen (oder die Firewall komplett zu deaktivieren), können solche Fehler vermieden werden, indem die [Datenschutzeinstellungen für die Datenquelle im Power BI-Dienst als nicht privat konfiguriert](https://powerbi.microsoft.com/blog/privacy-levels-for-cloud-data-sources/) werden.

Wenn die Firewall z. B. eine verschachtelte Tabelle oder Liste oder einen verschachtelten Datensatz puffert, wird in Power BI ab Juni der folgende Fehler ausgegeben, anstatt solche Werte automatisch in Text zu konvertieren: 

`We cannot return a value of type Table in this context`

## <a name="effect-on-loadrefresh"></a>Auswirkungen auf das Laden/Aktualisieren

Während die Änderung von der Firewallpufferung motiviert ist, wirkt sie sich auch auf das Laden/Aktualisieren aus. Damit mit dem Firewall-Pufferungsverhalten umgegangen werden kann, musste auch das Verhalten des Ladens z. B. von geschachtelten Tabellen oder Datensätzen in das Power BI-Modell und das Excel-Datenmodell in Microsoft Power Query für Excel geändert werden. Bisher wurden geschachtelte Tabellen oder Datensätze als Textwerte geladen (z. B. „[Table]“ oder „[Record]“). Sie werden nun als Fehler behandelt, was zu einem NULL-Wert in der geladenen Tabelle und einer Erhöhung der Fehlerzahlen bei den geladenen Ergebnissen führt.

Da diese Fehler nur während des Ladens/Aktualisierens auftreten, werden sie im Power Query-Editor nicht angezeigt.

### <a name="before"></a>Vorher

- Laden/Aktualisieren ohne Fehlern
- Die geladene Tabelle enthält z. B. „[Table]“ oder „[Record]“
 

### <a name="after"></a>Nachher

- Laden/Aktualisieren mit Fehlern
- Die geladene Tabelle enthält NULL-Werte (anstelle von z. B. „[Table]“ oder „[Record]“)
 

## <a name="resolution"></a>Lösung

Laden Sie eine Spalte, die nicht-skalare Werte enthält (z. B. Tabellen, Listen, Datensätze)?
Wenn dies der Fall ist, sollten Sie diese Fehler beseitigen können, indem Sie die Spalte entfernen.
Wenn Sie die Spalte nicht entfernen können, sollten Sie das alte Verhalten replizieren können, indem Sie eine benutzerdefinierte Spalte hinzufügen und eine Logik wie im folgenden Beispiel verwenden:

`if [MyColumn] is table then "[Table]" else if [MyColumn] is record then "[Record]" else if [MyColumn] is list then "[List]" else if [MyColumn] is function then "[Function]" else [MyColumn]`

Tritt das Problem auch in Power BI Desktop auf, wenn Sie alle Datenschutzeinstellungen für Ihre Datenquelle auf privat festlegen?
Ist dies der Fall, sollten Sie den Fehler lösen können, indem Sie [die entsprechenden Datenschutzeinstellungen für die Datenquelle](https://powerbi.microsoft.com/blog/privacy-levels-for-cloud-data-sources/) im Power BI-Dienst auf nicht privat festlegen.
