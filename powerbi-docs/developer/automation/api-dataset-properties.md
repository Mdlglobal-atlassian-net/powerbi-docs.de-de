---
title: Eigenschaften von Power BI-Datasets
description: Erfahren Sie mehr über die Eigenschaften von Power BI-Dataset-APIs
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 06/08/2018
ms.openlocfilehash: e74e390a5d228cb4a158d422cf0adab48b573cce
ms.sourcegitcommit: 87b7cb4a2e626711b98387edaa5ff72dc26262bb
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/10/2020
ms.locfileid: "79079667"
---
# <a name="dataset-properties"></a>Dataseteigenschaften

Die aktuelle Version 1 der Datasets-API erlaubt nur die Erstellung eines Datasets mit einem Namen und einer Sammlung von Tabellen. Jede Tabelle kann einen Namen und eine Sammlung von Spalten aufweisen. Jede Spalte besitzt einen Namen und einen Datentyp. Diese Eigenschaften werden insbesondere durch Unterstützung von Measures und Beziehungen zwischen Tabellen erweitert. Alle in dieser Version unterstützten Eigenschaften:

> [!IMPORTANT]
> Sie finden sie auf der Seite [Datasets Operation Groups (Dataset-Vorgangsgruppen)](https://docs.microsoft.com/rest/api/power-bi/datasets).

## <a name="dataset"></a>Dataset

Name  |Typ  |Beschreibung  |Schreibgeschützt  |Erforderlich
---------|---------|---------|---------|---------
ID     |  GUID       | Systemweit eindeutiger Bezeichner für das Dataset.        | True        | False        
name     | Zeichenfolge        | Benutzerdefinierter Name des Datasets.        | False        | True        
tables     | Table[]        | Eine Auflistung von Tabellen.        |  False       | False        
relationships     | Relationship[]        | Eine Auflistung von Beziehungen zwischen Tabellen.        | False        |  False  
defaultMode     | Zeichenfolge        | Legt mithilfe der Werte „Push“ und „Streaming“ fest, ob das Dataset gepusht, gestreamt oder sowohl gepusht als auch gestreamt wird.         | False        |  False

## <a name="table"></a>Tabelle

Name  |Typ  |Beschreibung  |Schreibgeschützt  |Erforderlich
---------|---------|---------|---------|---------
name     | Zeichenfolge        |  Benutzerdefinierter Name der Tabelle. Wird außerdem als Bezeichner der Tabelle verwendet.       | False        |  True       
columns     |  column[]       |  Eine Auflistung von Spalten.       | False        |  True       
measures     | measure[]        |  Eine Auflistung von Measures.       | False        |  False       
isHidden     | Boolescher Wert        | Wenn „true“, wird die Tabelle in Clienttools ausgeblendet.        | False        | False        

## <a name="column"></a>Column (Spalte)

Name  |Typ  |Beschreibung  |Schreibgeschützt  |Erforderlich
---------|---------|---------|---------|---------
name     |  Zeichenfolge        | Benutzerdefinierter Name der Spalte.        |  False       | True       
dataType     |  Zeichenfolge       |  Unterstützte [EDM-Datentypen](https://msdn.microsoft.com/library/ee382832.aspx) und Einschränkungen. Siehe [Datentypeinschränkungen](#data-type-restrictions).      |  False       | True        
formatString     | Zeichenfolge        | Eine Zeichenfolge, die beschreibt, wie der Wert für die Anzeige formatiert werden soll. Weitere Informationen zur Formatierung von Zeichenfolgen finden Sie unter [FORMAT_STRING-Inhalte](https://msdn.microsoft.com/library/ms146084.aspx).      | False        | False        
sortByColumn    | Zeichenfolge        |   Zeichenfolgenname einer Spalte in der gleichen Tabelle, die zum Sortieren der aktuellen Spalte verwendet werden soll.     | False        | False       
dataCategory     | Zeichenfolge        |  Zeichenfolgenwert, der als Datenkategorie verwendet werden soll, die die Daten in dieser Spalte beschreibt. Beispiele für häufig verwendete Werte: Address, City, Continent, Country, Image, ImageUrl, Latitude, Longitude, Organization, Place, PostalCode, StateOrProvince, WebUrl       |  False       | False        
isHidden    |  Boolescher Wert       |  Eigenschaft, die angibt, ob die Spalte ausgeblendet wird. Standardwert ist „false“.       | False        | False        
summarizeBy     | Zeichenfolge        |  Standardaggregationsmethode für die Spalte. Beispielwerte: default, none, sum, min, max, count, average, distinctCount     |  False       | False

## <a name="measure"></a>Measure

Name  |Typ  |Beschreibung  |Schreibgeschützt  |Erforderlich
---------|---------|---------|---------|---------
name     | Zeichenfolge        |  Benutzerdefinierter Name des Measures.       |  False       | True        
expression     | Zeichenfolge        | Ein gültiger DAX-Ausdruck.        | False        |  True       
formatString     | Zeichenfolge        |  Eine Zeichenfolge, die beschreibt, wie der Wert für die Anzeige formatiert werden soll. Weitere Informationen zur Formatierung von Zeichenfolgen finden Sie unter [FORMAT_STRING-Inhalte](https://msdn.microsoft.com/library/ms146084.aspx).       | False        | False        
isHidden     | Zeichenfolge        |  Wenn „true“, wird die Tabelle in Clienttools ausgeblendet.       |  False       | False       

## <a name="relationship"></a>Beziehung

Name  |Typ  |Beschreibung  |Schreibgeschützt  |Erforderlich 
---------|---------|---------|---------|---------
name     | Zeichenfolge        | Benutzerdefinierter Name der Beziehung. Wird außerdem als Bezeichner der Beziehung verwendet.        | False       | True        
crossFilteringBehavior     | Zeichenfolge        |    Die Filterrichtung der Beziehung: OneDirection (Standard), BothDirections, Automatic       | False        | False        
fromTable     | Zeichenfolge        | Name der Fremdschlüsseltabelle.        | False        | True         
fromColumn    | Zeichenfolge        | Name der Fremdschlüsselspalte.        | False        | True         
toTable    | Zeichenfolge        | Name der Primärschlüsseltabelle.        | False        | True         
toColumn     | Zeichenfolge        | Name der Primärschlüsselspalte.        | False        | True        

## <a name="data-type-restrictions"></a>Datentypeinschränkungen

Diese Einschränkungen gelten für die dataType-Eigenschaft.

Datentyp  |Einschränkungen  
---------|---------
Int64     |   Int64.MaxValue und Int64.MinValue sind nicht zulässig.      
Double     |  Die Werte Double.MaxValue und Double.MinValue sind nicht zulässig. NaN wird nicht unterstützt. +Infinity und -Infinity werden bei einigen Funktionen (z. B. Min, Max) nicht unterstützt.       
Boolescher Wert     |   „True“ oder „False“.
Datetime    |   Beim Laden von Daten werden Werte mit Bruchteilen von Tagen auf ganze Vielfache von 1/300 Sekunden (3,33 ms) quantisiert.      
Zeichenfolge     |  Derzeit werden bis zu 4000 Zeichen pro Zeichenfolgenwert zugelassen.
Dezimal|Genauigkeit=28, Skalierung=4

## <a name="example"></a>Beispiel
Das folgende Codebeispiel enthält eine Reihe dieser Eigenschaften:

```json
{

  "name": "PushAdvanced",

  "tables": [

    {

      "name": "Date",

      "columns": [

        {

          "name": "Date",

          "dataType": "dateTime",

          "formatString": "dddd\\, mmmm d\\, yyyy",

          "summarizeBy": "none"

        }

      ]

    },

    {

      "name": "sales",

      "columns": [

        {

          "name": "Date",

          "dataType": "dateTime",

          "formatString": "dddd\\, mmmm d\\, yyyy",

          "summarizeBy": "none"

        },

        {

          "name": "Sales",

          "dataType": "int64",

          "formatString": "0",

          "summarizeBy": "sum"

        }

      ],

      "measures": [

        {

          "name": "percent to forecast",

          "expression": "SUM(sales[Sales])/SUM(forecast[forecast])",

          "formatString": "0.00 %;-0.00 %;0.00 %"

        }

      ]

    },

    {

      "name": "forecast",

      "columns": [

        {

          "name": "date",

          "dataType": "dateTime",

          "formatString": "m/d/yyyy",

          "summarizeBy": "none"

        },

        {

          "name": "forecast",

          "dataType": "int64",

          "formatString": "0",

          "summarizeBy": "sum"

        }

      ]

    }

  ],

  "relationships": [

    {

      "name": "2ea345ce-b147-436e-8ac2-9d3c4d82af8d",

      "fromTable": "sales",

      "fromColumn": "Date",

      "toTable": "Date",

      "toColumn": "Date",

      "crossFilteringBehavior": "bothDirections"

    },

    {

      "name": "5d95f419-e589-4345-9581-6e70670b1bba",

      "fromTable": "forecast",

      "fromColumn": "date",

      "toTable": "Date",

      "toColumn": "Date",

      "crossFilteringBehavior": "bothDirections"

    }

  ]

}
```