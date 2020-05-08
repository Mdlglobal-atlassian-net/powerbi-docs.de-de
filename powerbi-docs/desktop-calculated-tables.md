---
title: Verwenden von berechneten Tabellen in Power BI Desktop
description: Berechnete Tabellen in Power BI Desktop
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 01/02/2020
ms.author: davidi
LocalizationGroup: Model your data
ms.openlocfilehash: c72387d40ddf4b193481a37dbcb40695668eab66
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "75837340"
---
# <a name="create-calculated-tables-in-power-bi-desktop"></a>Erstellen von berechneten Tabellen in Power BI Desktop
In den meisten Fällen können Sie Tabellen erstellen, indem Sie Daten aus einer externen Datenquelle in das Modell importieren. Mit *berechneten Tabellen* können Sie jedoch neue Tabellen auf Grundlage der Daten, die Sie bereits in das Modell geladen haben, hinzufügen. Anstatt Werte abzufragen und aus einer Datenquelle in die Spalten Ihrer neuen Tabelle zu laden, erstellen Sie eine [DAX-Formel](/dax/index), um die Werte der Spalte zu definieren.

DAX ist eine Formelsprache für die Arbeit mit relationalen Daten wie etwa in Power BI Desktop. DAX beinhaltet eine Bibliothek aus über 200 Funktionen, Operatoren und Konstrukten, die eine enorme Flexibilität beim Erstellen von Formeln zum Berechnen von Ergebnissen für so ungefähr jede benötigte Datenanalyse verfügbar macht. Berechnete Tabellen sind am besten geeignet für Zwischenberechnungen und Daten, die als Teil des Modells gespeichert werden sollen, anstatt sie ad hoc oder als Abfrageergebnisse zu berechnen. Beispielsweise möchten Sie vielleicht zwei Tabellen *vereinen* oder *kreuzen*.

Genau so wie Power BI Desktop-Tabellen können auch berechnete Tabellen Beziehungen zu anderen Tabellen aufweisen. Spalten mit berechneten Tabellen weisen Datentypen sowie Formatierungen auf und können zu einer Datenkategorie gehören. Sie können Ihre Spalten nach Belieben benennen und sie Berichtsvisualisierungen hinzufügen, genau wie andere Felder. Berechnete Tabellen werden neu berechnet, wenn eine der Tabellen, aus denen sie Daten abrufen, aktualisiert wird.

## <a name="create-a-calculated-table"></a>Erstellen einer berechneten Tabelle

Sie erstellen berechnete Spalten mithilfe der Funktion **Neue Tabelle** in der Berichtsansicht oder der Datenansicht von Power BI Desktop.

Stellen Sie sich beispielsweise vor, Sie sind Personalmanager und verfügen über die Tabelle **Nordwest Employees** (Mitarbeiter im Nordwesten) und **Southwest Employees** (Mitarbeiter im Südwesten). Sie möchten die beiden Tabellen in einer einzelnen Tabelle namens **Western Region Employees** (Mitarbeiter der Region Westen) zusammenfassen.

**Northwest Employees**

 ![](media/desktop-calculated-tables/calctables_nwempl.png)

**Southwest Employees**

 ![](media/desktop-calculated-tables/calctables_swempl.png)

Wählen Sie in der Berichtsansicht oder Datenansicht von Power BI Desktop unter der Gruppe **Berechnungen** der Registerkarte **Modellierung** die Option **Neue Tabelle** aus. In der Datenansicht ist es etwas einfacher, da Sie Ihre neue berechnete Tabelle sofort anzeigen können.

 ![Neue Tabelle in der Datenansicht](media/desktop-calculated-tables/calctables_formulabarempty.png)

Geben Sie in der Bearbeitungsleiste folgende Formel ein:

```dax
Western Region Employees = UNION('Northwest Employees', 'Southwest Employees')
```

Es wird eine neue Tabelle mit dem Namen **Western Region Employees** erstellt. Diese Tabelle wird wie jede andere Tabelle auch im Bereich **Felder** angezeigt. Sie können Beziehungen zu anderen Tabellen herstellen, Measures sowie berechnete Spalten hinzufügen und wie bei anderen Tabellen auch die Felder zu Berichten hinzufügen.

 ![Neue berechnete Tabelle](media/desktop-calculated-tables/calctables_westregionempl.png)

 ![Neue Tabelle im Bereich „Felder“](media/desktop-calculated-tables/calctables_fieldlist.png)

## <a name="functions-for-calculated-tables"></a>Funktionen für berechnete Tabellen

Sie können die berechnete Spalte durch jeden beliebigen DAX-Ausdruck definieren, der eine Tabelle zurückgibt, auch einen einfachen Verweis zu einer anderen Tabelle. Beispiel:

```dax
New Western Region Employees = 'Western Region Employees'
```

Dieser Artikel bietet eine kurze Einführung in berechnete Tabellen. Sie können berechnete Tabellen zusammen mit DAX verwenden, um eine Vielzahl von analytischen Problemen zu lösen. Nachstehend finden Sie einige der gängigen DAX-Tabellenfunktionen, die Sie verwenden können:

* DISTINCT
* VALUES
* CROSSJOIN
* UNION
* NATURALINNERJOIN
* NATURALLEFTOUTERJOIN
* INTERSECT
* CALENDAR
* CALENDARAUTO

In der [DAX-Funktionsreferenz](/dax/dax-function-reference) finden Sie diese sowie weitere DAX-Funktionen, mit denen Tabellen zurückgeben werden.

