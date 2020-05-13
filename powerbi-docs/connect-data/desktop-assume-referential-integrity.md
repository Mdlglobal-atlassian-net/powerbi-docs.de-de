---
title: Einstellung „Referenzielle Integrität voraussetzen“ in Power BI Desktop
description: Erfahren Sie, wie mit DirectQuery in Power BI Desktop die referenzielle Integrität vorausgesetzt werden kann.
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/07/2019
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 93848fc2629c123f34cebcb317a91928b336be98
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/13/2020
ms.locfileid: "83301124"
---
# <a name="apply-the-assume-referential-integrity-setting-in-power-bi-desktop"></a>Anwenden der Einstellung „Referenzielle Integrität voraussetzen“ in Power BI Desktop
Wenn Sie mithilfe von **DirectQuery** eine Verbindung mit einer Datenquelle herstellen, können Sie die Option **Referenzielle Integrität voraussetzen** verwenden, um die Ausführung effizienterer Abfragen der Datenquelle zu ermöglichen. Diese Funktion beinhaltet einige Anforderungen an die zugrunde liegenden Daten und ist nur bei Verwendung von **DirectQuery** verfügbar.

Durch Festlegen von **Referenzielle Integrität voraussetzen** können bei Abfragen der Datenquelle **INNER JOIN**anstelle von **OUTER JOIN**-Anweisungen verwendet werden. Hierdurch wird die Effizienz der Abfragen verbessert.

![](media/desktop-assume-referential-integrity/assume-referential-integrity_1.png)

## <a name="requirements-for-using-assume-referential-integrity"></a>Anforderungen für die Verwendung von „Referenzielle Integrität voraussetzen“
Hierbei handelt es sich um eine erweiterte Einstellung, die nur aktiviert wird, wenn mit **DirectQuery** eine Verbindung mit den Daten hergestellt wird. Die folgenden Anforderungen müssen erfüllt werden, damit **Referenzielle Integrität voraussetzen** ordnungsgemäß funktioniert:

* Daten in der Spalte **Von** der Beziehung sind nie *NULL* oder *leer*.
* Für jeden Wert in der Spalte **Von** ist ein entsprechender Wert in der Spalte **Zu** vorhanden.

In diesem Kontext ist die Spalte **Von** das *n* in einer *1:n*-Beziehung oder die Spalte in der ersten Tabelle einer *1:1*-Beziehung.

## <a name="example-of-using-assume-referential-integrity"></a>Beispiel für die Verwendung von „Referenzielle Integrität voraussetzen“
Im folgenden Beispiel wird das Verhalten von **Referenzielle Integrität voraussetzen** bei der Verwendung in Datenverbindungen veranschaulicht. Im Beispiel wird eine Verbindung mit einer Datenquelle hergestellt, die eine Tabelle **Orders**, eine Tabelle **Products** und eine Tabelle **Depots** enthält.

1. Beachten Sie in der folgenden Abbildung mit den Tabellen **Orders** und **Products**, dass die referenzielle Integrität zwischen **Orders[ProductID]** und **Products[ProductID]** vorhanden ist. Die Spalte **[ProductID]** in der Tabelle **Orders** ist nie *NULL*, und jeder Wert ist auch in der Tabelle **Products** vorhanden. Daher sollte **Referenzielle Integrität voraussetzen** festgelegt werden, um effizientere Abfragen zu ermöglichen (durch die Verwendung dieser Einstellung werden die in Visualisierungen angezeigten Werte nicht geändert).
   
   ![](media/desktop-assume-referential-integrity/assume-referential-integrity_2.png)
2. Beachten Sie in der nächsten Abbildung, dass zwischen **Orders[DepotID]** und **Depots[DepotID]** keine referenzielle Integrität vorhanden ist, da **DepotID** für einige *Orders* gleich *NULL* ist. Daher sollte **Referenzielle Integrität voraussetzen***nicht* festgelegt werden.
   
   ![](media/desktop-assume-referential-integrity/assume-referential-integrity_3.png)
3. Schließlich besteht in den folgenden Tabellen keine referenzielle Integrität zwischen **Orders[CustomerID]** und **Customers[CustID]** . **CustomerID** enthält einige Werte (in diesem Fall *CustX*), die nicht in der Tabelle *Customers* enthalten sind. Daher sollte **Referenzielle Integrität voraussetzen***nicht* festgelegt werden.
   
   ![](media/desktop-assume-referential-integrity/assume-referential-integrity_4.png)

## <a name="setting-assume-referential-integrity"></a>Festlegen von „Referenzielle Integrität voraussetzen“
Um dieses Feature auszuwählen, aktivieren Sie das Kontrollkästchen neben **Referenzielle Integrität voraussetzen**, wie in der folgenden Abbildung dargestellt.

![](media/desktop-assume-referential-integrity/assume-referential-integrity_1.png)

Bei Auswahl dieser Option wird die Einstellung anhand der Daten überprüft, um sicherzustellen, dass weder *NULL* noch nicht übereinstimmende Zeilen vorhanden sind. *Aber* bei einer sehr großen Anzahl von Werten ist die Überprüfung keine Garantie dafür, dass keine Probleme mit der referenziellen Integrität auftreten.

Darüber hinaus wird die Überprüfung während der Bearbeitung der Beziehung durchgeführt und spiegelt daher *nicht* die nachfolgenden Änderungen an den Daten wider.

## <a name="what-happens-if-you-incorrectly-set-assume-referential-integrity"></a>Was geschieht, wenn Sie „Referenzielle Integrität voraussetzen“ fälschlicherweise festlegen?
Wenn Sie **Referenzielle Integrität voraussetzen** festlegen, obwohl Probleme mit der referenziellen Integrität in den Daten vorliegen, führt dies nicht zu Fehlern. Die Folge sind allerdings deutliche Inkonsistenzen in den Daten. Bei der Beziehung mit der oben beschriebenen Tabelle **Depots** hätte dies zum Beispiel folgende Auswirkungen:

* Ein visuelles Element, in dem die gesamte *Bestellmenge* angezeigt wird, würde den Wert 40 anzeigen.
* Ein visuelles Element, in dem der Gesamtwert für *Bestellmenge nach Depotstadt* angezeigt wird, würde lediglich den Gesamtwert *30* anzeigen, da die Bestell-ID 1, deren **DepotID** gleich *NULL* ist, nicht eingeschlossen wäre.

## <a name="next-steps"></a>Weitere Schritte
Weitere Informationen zu [DirectQuery](desktop-use-directquery.md)

Weitere Informationen zu [Beziehungen in Power BI](../transform-model/desktop-create-and-manage-relationships.md)

Weitere Informationen zur [Beziehungsansicht in Power BI Desktop](../transform-model/desktop-relationship-view.md).
