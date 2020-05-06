---
title: Query Folding-Anleitung für Power BI Desktop
description: Anleitung für Query Folding mit Power Query in Power BI Desktop
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 11/09/2019
ms.author: v-pemyer
ms.openlocfilehash: e8123bba9f68305e1944dbfb280b5255e4fb9b48
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "75622160"
---
# <a name="query-folding-guidance-in-power-bi-desktop"></a>Query Folding-Anleitung für Power BI Desktop

Dieser Artikel richtet sich an Datenmodellierer, die Modelle in Power BI Desktop entwickeln. Darin lernen Sie bewährte Methoden kennen, wann und wie das Query Folding mit Power Query eingesetzt werden sollte.

Als _Query Folding_ wird die Fähigkeit einer Power Query-Abfrage bezeichnet, eine einzelne Abfrageanweisung zum Abrufen und Transformieren von Quelldaten zu generieren. Weitere Informationen finden Sie im Artikel [Query Folding mit Power Query](/power-query/power-query-folding).

## <a name="guidance"></a>Leitfaden

Der Leitfaden für Query Folding unterscheidet sich je nach Modellmodus.

Für eine Tabelle mit dem Speichermodus **DirectQuery** oder **Dual** muss die Power Query-Abfrage das Query Folding unterstützen.

Für eine **Importtabelle** ist Query Folding möglich. Wenn die Abfrage auf einer relationalen Quelle basiert und eine einzelne SELECT-Anweisung erstellt werden kann, wird _die bestmögliche Leistung bei der Datenaktualisierung_ erzielt, indem ein Query Folding sichergestellt wird. Wenn die Mashup-Engine von Power Query weiterhin zum Verarbeiten von Transformationen benötigt wird, sollten Sie den Arbeitsaufwand so gering wie möglich halten, insbesondere bei großen Datasets.

In der folgenden Liste finden Sie eine konkrete Anleitung.

- **Delegieren eines größtmöglichen Anteils an der Verarbeitung an die Datenquelle:** Wenn es nicht möglich ist, ein Query Folding für alle Schritte einer Power Query-Abfrage durchzuführen, ermitteln Sie den Schritt, der ein Query Folding verhindert. Verschieben Sie nachfolgende Schritte nach Möglichkeit an eine höhere Position in der Sequenz, damit sie beim Query Folding einbezogen werden können. Die Mashup-Engine von Power Query ist möglicherweise so intelligent, dass Ihre Abfrageschritte beim Generieren der Quellabfrage neu angeordnet werden.

    Wenn für eine relationale Datenquelle der Schritt, der das Query Folding verhindert, in einer einzelnen SELECT-Anweisung oder innerhalb der prozeduralen Logik einer gespeicherten Prozedur erreicht werden kann, sollten Sie die Verwendung einer nativen SQL-Abfrageanweisung in Betracht ziehen. Weitere Informationen dazu finden Sie in den folgenden Abschnitten.

- **Verwenden einer nativen SQL-Abfrage:** Wenn eine Power Query-Abfrage Daten aus einer relationalen Quelle abruft, kann für einige Quellen eine native SQL-Abfrage verwendet werden. Die Abfrage kann eine beliebige gültige Anweisung sein, einschließlich der Ausführung einer gespeicherten Prozedur. Wenn die Anweisung mehrere Resultsets generiert, wird nur das erste zurückgegeben. In der Anweisung können Parameter deklariert werden, und es wird empfohlen, die M-Funktion [Value.NativeQuery](/powerquery-m/value-nativequery) zu verwenden. Diese Funktion wurde dafür entwickelt, Parameterwerte sicher und bequem zu übergeben. Es ist wichtig, zu verstehen, dass die Mashup-Engine von Power Query kein Query Folding für nachfolgende Abfrageschritte durchführen kann. Deshalb sollten Sie die gesamte Transformationslogik (oder den größtmöglichen Teil) in die native Abfrageanweisung einschließen.

    Es gibt zwei wesentliche Aspekte, die Sie bei der Verwendung nativer SQL-Abfragen beachten müssen:

    - Für eine DirectQuery-Modelltabelle muss als Abfrage eine SELECT-Anweisung verwendet werden, und diese darf keine allgemeinen Tabellenausdrücke oder gespeicherte Prozeduren enthalten.
    - Für inkrementelle Aktualisierungen können keine SQL-Abfragen verwendet werden. Die Mashup-Engine von Power Query müsste in diesem Fall alle Quellzeilen abrufen und anschließend Filter anwenden, um inkrementelle Änderungen zu ermitteln.

    > [!IMPORTANT]
    > Eine native SQL-Abfrage kann potenziell mehr leisten als nur Daten abzurufen. Es kann eine beliebige gültige Anweisung ausgeführt werden (möglicherweise auch mehrmals) – einschließlich von Anweisungen, die Daten ändern oder löschen. Es ist wichtig, das Prinzip der geringsten Privilegien anzuwenden. So ist sichergestellt, dass das für den Datenbankzugriff verwendete Konto nur Leserechte für die erforderlichen Daten besitzt.

- **Vorbereiten und Transformieren von Daten in der Quelle:** Wenn Sie feststellen, dass für bestimmte Power Query-Abfrageschritte kein Query Folding möglich ist, können Sie die Transformationen möglicherweise in der Datenquelle anwenden. Sie könnten für die Transformation zum Beispiel eine Datenbankansicht schreiben, die Quelldaten logisch transformiert. Eine andere Möglichkeit wäre, Daten vorzubereiten und zu materialisieren, bevor sie in Power BI abgefragt werden. Ein relationales Data Warehouse ist ein hervorragendes Beispiel für vorbereitete Daten, da es üblicherweise aus vorab integrierten Quellen von Organisationsdaten besteht.

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zu diesem Artikel finden Sie in den folgenden Ressourcen:

- Konzeptartikel zum [Query Folding](/power-query/power-query-folding) in Power Query
- [Inkrementelle Aktualisierung in Power BI Premium](../service-premium-incremental-refresh.md)
- Haben Sie Fragen? [Stellen Sie Ihre Frage in der Power BI-Community.](https://community.powerbi.com/)
