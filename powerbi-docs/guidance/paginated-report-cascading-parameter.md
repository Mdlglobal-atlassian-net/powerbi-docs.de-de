---
title: Verwenden von kaskadierenden URL-Parametern in paginierten Berichten
description: Leitfaden zum Entwerfen von paginierten Berichten mithilfe von kaskadierenden Parametern.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.date: 01/14/2020
ms.author: v-pemyer
ms.openlocfilehash: 90f501b257313c48cbef13517747ff83cd9ea9d1
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "78920786"
---
# <a name="use-cascading-parameters-in-paginated-reports"></a>Verwenden von kaskadierenden URL-Parametern in paginierten Berichten

Dieser Artikel richtet sich an Berichtsautoren, die [paginierte Berichte](../paginated-reports/paginated-reports-report-builder-power-bi.md) in Power BI entwerfen. Der Artikel enthält einige Szenarien für den Entwurf von kaskadierenden Parametern. Bei kaskadierenden Parametern handelt es sich um Berichtsparameter mit Abhängigkeiten. Wenn ein Berichtsbenutzer einen Parameterwert auswählt, wird dieser Wert verwendet, um verfügbare Werte für einen anderen Parameter festzulegen.

> [!NOTE]
> Dieser Artikel bietet keine Einführung zu kaskadierenden Parametern und deren Konfiguration. Wenn Sie mit dem Konzept der kaskadierenden Parameter nicht vertraut sind, empfiehlt es sich, zuerst den Artikel [Hinzufügen von kaskadierenden Parametern zu einem Bericht (Report Builder und SSRS)](/sql/reporting-services/report-design/add-cascading-parameters-to-a-report-report-builder-and-ssrs) zu lesen.

## <a name="design-scenarios"></a>Entwurfsszenarien

Für die Verwendung von kaskadierenden Parametern gibt es zwei Entwurfsszenarien. Diese können effektiv für Folgendes eingesetzt werden:

- Filtern _großer Mengen_ an Elementen
- Präsentieren _relevanter_ Elemente

### <a name="example-database"></a>Beispieldatenbank

Die Beispiele in diesem Artikel basieren auf einer Azure SQL-Datenbank. In der Datenbank werden Vertriebsvorgänge erfasst, und sie enthält verschiedene Tabellen mit Handelspartnern, Produkten und Verkaufsaufträgen.

Eine Tabelle namens **Reseller** speichert einen Datensatz für jeden Handelspartner und enthält mehrere Tausend Datensätze. Die Tabelle **Reseller** weist folgende Spalten auf:

- ResellerCode (Ganzzahl)
- ResellerName
- Country-Region
- State-Province
- Stadt
- PostalCode

Es gibt auch eine Tabelle namens **Sales** (Verkäufe). Diese Tabelle speichert Datensätze zu Verkaufsaufträgen und weist in der Spalte **ResellerCode** eine Fremdschlüsselbeziehung mit der Tabelle **Reseller** auf.

### <a name="example-requirement"></a>Beispielanforderung

Es gibt eine Anforderung, einen Bericht mit einem Handelspartnerprofil zu erstellen. Der Bericht muss so entworfen werden, dass er Informationen zu einem einzelnen Handelspartner anzeigt. Es ist nicht sinnvoll, dass Benutzer des Berichts einen Handelspartnercode eingeben, da Benutzer sich diesen selten merken.

## <a name="filter-large-sets-of-items"></a>Filtern großer Mengen an Elementen

Sehen wir uns in drei Beispielen an, wie sich große Mengen an verfügbaren Elementen – wie z. B. Handelspartner – eingrenzen lassen. Sie lauten wie folgt:

- [Filtern nach zugehörigen Spalten](#filter-by-related-columns)
- [Filtern nach Gruppierungsspalte](#filter-by-a-grouping-column)
- [Filtern nach Suchmuster](#filter-by-search-pattern)

### <a name="filter-by-related-columns"></a>Filtern nach zugehörigen Spalten

In diesem Beispiel interagiert der Berichtsbenutzer mit fünf Berichtsparametern. Der Benutzer muss folgende Parameter auswählen: „Country-Region“, „State-Province“, „City“ und „Postal Code“. Ein letzter Parameter listet Handelspartner auf, die sich am entsprechenden geografischen Standort befinden.

![Abbildung mit fünf Berichtsparametern: „Country-Region“, „State-Province“, „City“, „Postal Code“ und „Reseller“. Für die ersten vier sind Werte festgelegt, und die Liste „Reseller“ wird auf nur vier Elemente gefiltert.](media/paginated-report-cascading-parameter/filter-by-related-columns-example.png)

So können Sie kaskadierende Parameter entwickeln:

1. Erstellen Sie die fünf Berichtsparameter, und ordnen Sie sie in der richtigen Reihenfolge an.
2. Erstellen Sie mit der folgenden Abfrageanweisung das Dataset **CountryRegion**, das verschiedene Country-Region-Werte abruft:

    ```sql
    SELECT DISTINCT
      [Country-Region]
    FROM
      [Reseller]
    ORDER BY
      [Country-Region]
    ```

3. Erstellen Sie mit der folgenden Abfrageanweisung das Dataset **StateProvince**, das verschiedene State-Province-Werte für den ausgewählten Country-Region-Wert abruft:

    ```sql
    SELECT DISTINCT
      [State-Province]
    FROM
      [Reseller]
    WHERE
      [Country-Region] = @CountryRegion
    ORDER BY
      [State-Province]
    ```

4. Erstellen Sie mit der folgenden Abfrageanweisung das Dataset **City**, das verschiedene City-Werte für die ausgewählten State-Province- und Country-Region-Werte abruft:

    ```sql
    SELECT DISTINCT
      [City]
    FROM
      [Reseller]
    WHERE
      [Country-Region] = @CountryRegion
      AND [State-Province] = @StateProvince
    ORDER BY
      [City]
    ```

5. Setzen Sie dieses Muster fort, um das Dataset **PostalCode** zu erstellen.
6. Erstellen Sie mit der folgenden Abfrageanweisung das Dataset **Reseller**, um alle Handelspartner für die ausgewählten geografischen Werte abzurufen:

    ```sql
    SELECT
      [ResellerCode],
      [ResellerName]
    FROM
      [Reseller]
    WHERE
      [Country-Region] = @CountryRegion
      AND [State-Province] = @StateProvince
      AND [City] = @City
      AND [PostalCode] = @PostalCode
    ORDER BY
      [ResellerName]
    ```

7. Ordnen Sie für jedes Dataset mit Ausnahme des ersten die Abfrageparameter den entsprechenden Berichtsparametern zu.

> [!NOTE]
> Alle Abfrageparameter (die als Präfix das Symbol „@“ aufweisen) in diesen Beispielen können in SELECT-Anweisungen eingebettet oder an gespeicherte Prozeduren übergeben werden.
>
> Im Allgemeinen sind gespeicherte Prozeduren die bessere Wahl beim Entwurf. Der Grund hierfür ist, dass Abfragepläne für gespeicherte Prozeduren für eine schnellere Ausführung zwischengespeichert werden und dass gespeicherte Prozeduren bei Bedarf die Entwicklung einer ausgefeilteren Logik ermöglichen. Für relationale Datenquellen mit Gatewayzugriff wie SQL Server, Oracle und Teradata werden gespeicherte Prozeduren derzeit allerdings nicht unterstützt.
>
> Schließlich sollten Sie immer sicherstellen, dass geeignete Indizes vorhanden sind, um einen effizienten Datenabruf zu unterstützen. Andernfalls kann es lange dauern, bis die Berichtsparameter aufgefüllt sind, und die Datenbank kann überlastet werden. Weitere Informationen zur Indizierung für SQL Server finden Sie im [Leitfaden zur Architektur und zum Design von SQL Server-Indizes](/sql/relational-databases/sql-server-index-design-guide?view=sql-server-2017).

### <a name="filter-by-a-grouping-column"></a>Filtern nach Gruppierungsspalte

In diesem Beispiel interagiert der Berichtsbenutzer mit einem Berichtsparameter, um den ersten Buchstaben eines Handelspartners auszuwählen. Ein zweiter Parameter listet dann die Handelspartner auf, deren Namen mit dem ausgewählten Buchstaben beginnen.

![Abbildung mit zwei Berichtsparametern: „Group“ und „Reseller“. Der erste Parameterwert ist auf den Buchstaben A festgelegt, und die Liste „Reseller“ wird auf viele Elemente gefiltert, die mit diesem Buchstaben beginnen.](media/paginated-report-cascading-parameter/filter-by-grouping-column-example.png)

So können Sie kaskadierende Parameter entwickeln:

1. Erstellen Sie die Berichtsparameter **ReportGroup** und **Reseller**, und ordnen Sie sie in der richtigen Reihenfolge an.
2. Erstellen Sie mit der folgenden Abfrageanweisung das Dataset **ReportGroup**, um die ersten Buchstaben aller Handelspartner abzurufen:

    ```sql
    SELECT DISTINCT
      LEFT([ResellerName], 1) AS [ReportGroup]
    FROM
      [Reseller]
    ORDER BY
      [ReportGroup]
    ```

3. Erstellen Sie mit der folgenden Abfrageanweisung das Dataset **Reseller**, um alle Handelspartner abzurufen, deren Namen mit dem ausgewählten Buchstaben beginnen:

    ```sql
    SELECT
      [ResellerCode],
      [ResellerName]
    FROM
      [Reseller]
    WHERE
      LEFT([ResellerName], 1) = @ReportGroup
    ORDER BY
      [ResellerName]
    ```

4. Ordnen Sie den Abfrageparameter des Datasets **Reseller** dem entsprechenden Berichtsparameter zu.

Es ist effizienter, die Gruppierungsspalte der Tabelle **Reseller** hinzuzufügen. Wenn diese dauerhaft gespeichert und indiziert wird, liefert sie die besten Ergebnisse. Weitere Informationen finden Sie unter [Specify Computed Columns in a Table](/sql/relational-databases/tables/specify-computed-columns-in-a-table).

```sql
ALTER TABLE [Reseller]
ADD [ReportGroup] AS LEFT([ResellerName], 1) PERSISTED
```

Diese Vorgehensweise kann ein noch größeres Potenzial bieten. Sehen Sie sich das folgende Skript an, das eine neue Gruppierungsspalte hinzufügt, mit der Handelspartner nach _vordefinierten Buchstabenbereichen_ gefiltert werden können. Es erstellt auch einen Index, damit die von den Berichtsparametern benötigten Daten effizient abgerufen werden können.

```sql
ALTER TABLE [Reseller]
ADD [ReportGroup2] AS CASE
  WHEN [ResellerName] LIKE '[A-C]%' THEN 'A-C'
  WHEN [ResellerName] LIKE '[D-H]%' THEN 'D-H'
  WHEN [ResellerName] LIKE '[I-M]%' THEN 'I-M'
  WHEN [ResellerName] LIKE '[N-S]%' THEN 'N-S'
  WHEN [ResellerName] LIKE '[T-Z]%' THEN 'T-Z'
  ELSE '[Other]'
END PERSISTED
GO

CREATE NONCLUSTERED INDEX [Reseller_ReportGroup2]
ON [Reseller] ([ReportGroup2]) INCLUDE ([ResellerCode], [ResellerName])
GO
```

### <a name="filter-by-search-pattern"></a>Filtern nach Suchmuster

In diesem Beispiel interagiert der Berichtsbenutzer mit einem Berichtsparameter, um ein Suchmuster einzugeben. Ein zweiter Parameter listet dann die Handelspartner auf, deren Namen das Suchmuster enthält.

![Abbildung mit zwei Berichtsparametern: „Search“ und „Reseller“. Der erste Parameterwert ist auf den Text „red“ festgelegt, und die Liste „Reseller“ wird auf viele Elemente gefiltert, die diesen Text enthalten.](media/paginated-report-cascading-parameter/filter-by-search-pattern-example.png)

So können Sie kaskadierende Parameter entwickeln:

1. Erstellen Sie die Berichtsparameter **Search** und **Reseller**, und ordnen Sie sie in der richtigen Reihenfolge an.
2. Erstellen Sie mit der folgenden Abfrageanweisung das Dataset **Reseller**, um alle Handelspartner abzurufen, deren Namen den Suchtext enthalten:

    ```sql
    SELECT
      [ResellerCode],
      [ResellerName]
    FROM
      [Reseller]
    WHERE
      [ResellerName] LIKE '%' + @Search + '%'
    ORDER BY
      [ResellerName]
    ```

3. Ordnen Sie den Abfrageparameter des Datasets **Reseller** dem entsprechenden Berichtsparameter zu.

> [!TIP]
> Sie können dieses Design verbessern, um den Berichtsbenutzern eine bessere Steuerung zu bieten. Sie können es Benutzern ermöglichen, eigene Werte für den Musterabgleich zu definieren. Der Suchwert „red%“ beispielsweise filtert auf alle Handelspartner, deren Namen mit den Buchstaben „red“ _beginnen_.
>
> Weitere Informationen finden Sie unter [LIKE (Transact-SQL)](/sql/t-sql/language-elements/like-transact-sql?view=sql-server-ver15#using-the--wildcard-character).

So können Sie es Berichtsbenutzern ermöglichen, eigene Muster zu definieren.

```sql
WHERE
  [ResellerName] LIKE @Search
```

Benutzer, die sich nicht beruflich mit Datenbanken beschäftigen, kennen das Prozentzeichen (%) als Platzhalterzeichen häufig nicht. Sie sind eher mit dem Sternchen (*) vertraut. Durch Ändern der WHERE-Klausel können Sie es Benutzern ermöglichen, dieses Zeichen zu verwenden.

```sql
WHERE
  [ResellerName] LIKE SUBSTITUTE(@Search, '%', '*')
```

## <a name="present-relevant-items"></a>Präsentieren relevanter Elemente

In diesem Szenario können Sie Faktendaten verwenden, um verfügbare Werte zu begrenzen. Berichtsbenutzern werden Elemente angezeigt, für die eine Aktivität aufgezeichnet wurde.

In diesem Beispiel interagiert der Berichtsbenutzer mit drei Berichtsparametern. Die ersten beiden legen einen Datumsbereich für Verkaufsauftragsdaten fest. Der dritte Parameter listet die Handelspartner auf, die in diesem Zeitraum Aufträge erstellt haben.

![Abbildung mit drei Berichtsparametern: „Start Order Date“, „End Order Date“ und „Reseller“. Die beiden Datumsparameter sind auf Januar 2020 festgelegt, und die Liste „Reseller“ wird auf viele Elemente gefiltert. Diese Elemente repräsentieren Handelspartner, die im Lauf dieses Monats Aufträge platziert haben.](media/paginated-report-cascading-parameter/filter-relevant-items-example.png)

So können Sie kaskadierende Parameter entwickeln:

1. Erstellen Sie die Berichtsparameter **OrderDateStart**, **OrderDateEnd** und **Reseller**, und ordnen Sie sie in der richtigen Reihenfolge an.
2. Erstellen Sie mit der folgenden Abfrageanweisung das Dataset **Reseller**, um alle Handelspartner abzurufen, die in diesem Zeitraum Aufträge erstellt haben:

    ```sql
    SELECT DISTINCT
      [r].[ResellerCode],
      [r].[ResellerName]
    FROM
      [Reseller] AS [r]
    INNER JOIN [Sales] AS [s]
      ON [s].[ResellerCode] = [r].[ResellerCode]
    WHERE
      [s].[OrderDate] >= @OrderDateStart
      AND [s].[OrderDate] < DATEADD(DAY, 1, @OrderDateEnd)
    ORDER BY
      [r].[ResellerName]
    ```

## <a name="recommendations"></a>Empfehlungen

Es wird empfohlen, Berichte mit kaskadierenden Parametern zu entwerfen, wann immer dies möglich ist. Gründe:

- Diese Parameter bieten eine intuitive und nützliche Funktionalität für die Benutzer von Berichten.
- Sie sind effizient, weil sie kleinere Gruppen verfügbarer Werte abrufen.

Optimieren Sie Ihre Datenquellen mit folgenden Maßnahmen:

- Verwenden Sie nach Möglichkeit gespeicherte Prozeduren.
- Fügen Sie geeignete Indizes hinzu, um einen effizienten Datenabruf zu ermöglichen.
- Machen Sie Spaltenwerte – und sogar Zeilen – verfügbar, um kostspielige Auswertungen zur Abfragezeit zu vermeiden.

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zu diesem Artikel finden Sie in den folgenden Ressourcen:

- [Berichtsparameter im Power BI Report Builder](../paginated-reports/report-builder-parameters.md)
- [Hinzufügen von kaskadierenden Parametern zu einem Bericht (Report Builder und SSRS)](/sql/reporting-services/report-design/add-cascading-parameters-to-a-report-report-builder-and-ssrs)
- Haben Sie Fragen? [Stellen Sie Ihre Frage in der Power BI-Community.](https://community.powerbi.com/)
- Vorschläge? [Einbringen von Ideen zur Verbesserung von Power BI](https://ideas.powerbi.com)
