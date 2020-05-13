---
title: Hinzufügen einer Spalte aus einem Beispiel in Power BI Desktop
description: Schnelles Erstellen einer neuen Spalte in Power BI Desktop mit bereits vorhandenen Spalten als Beispiele
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 01/16/2019
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: b10bbaa4158e6c5392cb6ed937c54bdbb5d555d2
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/13/2020
ms.locfileid: "83295328"
---
# <a name="add-a-column-from-examples-in-power-bi-desktop"></a>Hinzufügen einer Spalte aus Beispielen in Power BI Desktop
Mithilfe der Funktion *Spalte aus Beispielen hinzufügen* im Power Query-Editor können Sie ganz einfach neue Spalten zu Ihrem Datenmodell hinzufügen, indem Sie mindestens einen Beispielwert für die neuen Spalten bereitstellen. Sie können die neuen Spaltenbeispiele aus einer Auswahl erstellen oder basierend auf allen vorhandenen Spalten in der Tabelle Eingaben bereitstellen.

![](media/desktop-add-column-from-example/add-column-from-example_01.png)

Mithilfe der Funktion *Spalte aus Beispielen hinzufügen* können Sie schnell und einfach neue Spalten erstellen, was besonders in folgenden Situationen hilfreich ist:

- Sie wissen, welche Daten Ihre neue Spalte enthalten soll, sind sich aber nicht sicher, welche Transformation oder Sammlung von Transformationen zum gewünschten Ergebnis führen.
- Sie wissen bereits, welche Transformationen Sie benötigen, sind sich aber nicht sicher, mit welcher Benutzeroberflächenoption sie ausgelöst werden.
- Sie wissen genau, welche Transformationen Sie mit einem Ausdruck vom Typ *Benutzerdefinierte Spalte* in der Sprache *M* benötigen, aber mindestens einer dieser Ausdrücke steht über die Benutzeroberfläche nicht zur Verfügung.

Es ist einfach und unkompliziert, eine Spalte aus einem Beispiel hinzuzufügen. Im nächsten Abschnitten erfahren Sie, wie das geht.

## <a name="add-a-new-column-from-examples"></a>Hinzufügen einer neuen Spalte aus Beispielen

Sie können Beispieldaten auf Wikipedia herunterladen, indem Sie auf der Registerkarte **Start** im Menüband von Power BI Desktop auf **Daten abrufen** > **Web** klicken. 

![Daten aus dem Web abrufen](media/desktop-add-column-from-example/add-column-from-example_02.png)

Fügen Sie die folgende URL in das Dialogfeld ein, das angezeigt wird, und klicken Sie auf **OK**: 

*https:\//wikipedia.org/wiki/List_of_states_and_territories_of_the_United_States*

Wählen Sie im Dialogfeld **Navigator** die Tabelle **States of the United States of America** (US-Bundesstaaten) aus, und klicken Sie dann auf **Daten transformieren**. Dann wird die Tabelle im Power Query-Editor geöffnet.

Wenn Sie bereits geladene Daten aus Power BI Desktop öffnen möchten, klicken Sie im Menüband unter der Registerkarte **Start** auf **Abfragen bearbeiten**. Dann werden die Daten im Power Query-Editor geöffnet. 

![„Abfragen bearbeiten“ in Power BI Desktop](media/desktop-add-column-from-example/add-column-from-example_05.png)

Sobald die Beispieldaten im Power Query-Editor geöffnet wurden, klicken Sie erst auf dem Menüband auf die Registerkarte **Spalte hinzufügen** und anschließend auf **Spalte aus Beispielen**. Klicken Sie auf das Symbol **Spalte aus Beispielen**, um die Spalte aus allen vorhandenen Spalten zu erstellen, oder öffnen Sie das Dropdownmenü, um zwischen den Optionen **Aus allen Spalten** und **Aus Auswahl** auszuwählen. Wählen Sie für diese exemplarische Vorgehensweise **Aus allen Spalten** aus.

![„Spalte aus Beispielen hinzufügen“ auswählen](media/desktop-add-column-from-example/add-column-from-example_03.png)

## <a name="add-column-from-examples-pane"></a>Der Bereich „Spalte aus Beispielen hinzufügen“
Wenn Sie auf **Spalte hinzufügen** > **Aus Beispielen** klicken, wird der Bereich **Spalte aus Beispielen hinzufügen** oberhalb der Tabelle geöffnet. Dann wird die neue **Spalte 1** rechts neben den bereits vorhanden Spalten angezeigt. Möglicherweise müssen Sie scrollen, um alle Spalten zu sehen. Wenn Sie Ihre Beispielwerte in die leeren Zellen von **Spalte 1** eingeben, erstellt Power BI passende Regeln und Transformationen für Ihre Beispiele, um die restliche Spalte auszufüllen.

Dabei wird **Spalte aus Beispielen** ebenfalls als **Angewendeter Schritt** im Bereich **Abfrageeinstellungen** angezeigt. Der Power Query-Editor erfasst wie gewohnt Ihre Transformationsschritte und wendet sie in der angegebenen Reihenfolge auf die Abfrage an.

![Der Bereich „Spalte aus Beispielen hinzufügen“](media/desktop-add-column-from-example/add-column-from-example_04.png)

Wenn Sie Ihr Beispiel in die neue Spalte eingeben, liefert Power BI auf der Grundlage der erstellten Transformationen eine Vorschau der fertigen Spalte. Ein Beispiel: Wenn Sie in die erste Zeile *Alabama* eingegeben, entspricht dies dem Wert **Alabama** in der ersten Spalte der Tabelle. Sobald Sie die EINGABETASTE drücken, füllt Power BI den Rest der neuen Spalte basierend auf dem ersten Spaltenwert aus und nennt die Spalte **Name & postal abbreviation[12] - Copy** (Namen und offizielles Staatenkürzel – Kopie).

Wechseln Sie nun zur Zeile **Massachusetts[E]** der neuen Spalte, und löschen Sie die Zeichen **[E]** aus der Zeichenfolge. Power BI erkennt die Änderung und verwendet das Beispiel, um eine Transformation zu erstellen. Power BI beschreibt die Transformationen im Bereich **Spalte aus Beispielen hinzufügen** und benennt die Spalte in **Text vor Trennzeichen** um. 

![Aus Beispielen transformierte Spalten](media/desktop-add-column-from-example/add-column-from-example_06.png)

Wenn Sie weitere Beispiele angeben, ergänzt der Power Query-Editor die Transformationen entsprechend. Wenn Sie mit dem Ergebnis zufrieden sind, klicken Sie auf **OK**, damit Ihre Änderungen übernommen werden. 

Sie können die neue Spalte beliebig umbenennen. Doppelklicken Sie dafür auf die Spaltenüberschrift, oder klicken Sie mit der rechten Maustaste auf diese, und wählen Sie **Umbenennen** aus. 

Im Folgenden Video wird die Option **Spalten aus Beispielen** unter Verwendung der Beispieldatenquelle näher veranschaulicht. 

[Power BI Desktop: Spalte aus Beispielen hinzufügen](https://www.youtube.com/watch?v=-ykbVW9wQfw) 

## <a name="list-of-supported-transformations"></a>Liste der unterstützten Transformationen
Wenn die Funktion **Spalte aus Beispielen hinzufügen** verwendet wird, sind zwar viele, aber nicht alle Transformationen verfügbar. Im Folgenden werden die unterstützten Transformationen aufgelistet:

**Allgemein**

- Bedingte Spalte

**Verweis**
  
- Verweis auf eine bestimmte Spalte, einschließlich Kürzungs-, Bereinigungs- und Groß-/Kleinschreibungstransformation

**Texttransformationen**

- Kombinieren (unterstützt das Kombinieren von Literalzeichenfolgen und vollständigen Spaltenwerten)
- Ersetzen
- Länge
- Extrahieren   
  - Erste Zeichen
  - Letzte Zeichen
  - Bereich
  - Text vor Trennzeichen
  - Text nach Trennzeichen
  - Text zwischen Trennzeichen
  - Länge
  - Zeichen entfernen
  - Zeichen beibehalten

> [!NOTE]
> Bei allen *Texttransformationen* wird der potenzielle Bedarf für die Anwendung einer Kürzungs-, Bereinigungs- oder Groß-/Kleinschreibungstransformation auf den Wert berücksichtigt.

**Datumstransformationen**

- Tag
- Tag der Woche
- Name des Wochentags
- Tag des Jahres
- Month
- Name Monat
- Quartal des Jahres
- Woche des Monats
- Woche des Jahres
- Jahr
- Alter
- Jahresbeginn
- Jahresende
- Monatsbeginn
- Monatsende
- Quartalsbeginn
- Tage des Monats
- Quartalsende
- Wochenbeginn
- Wochenende
- Tag des Monats
- Tagesbeginn
- Tagesende

**Uhrzeittransformationen**

- Hour
- Minute
- Second  
- In Ortszeit

> [!NOTE]
> Bei allen *Datums-* und *Uhrzeittransformationen* wird der potenzielle Bedarf für eine Konvertierung des Spaltenwerts in *Date*, *Time* oder *DateTime* berücksichtigt.

**Zahlentransformationen** 

- Absoluter Wert
- Arkuskosinus
- Arkussinus
- Arkustangens
- In eine Zahl umwandeln
- Kosinus
- Cube
- Dividieren
- Exponent
- Fakultät
- Ganzzahldivision
- Gerade
- Ungerade
- Ln
- Logarithmus zur Basis 10
- Modulo
- Multiplizieren
- Abrunden
- Aufrunden
- Vorzeichen
- Sin
- Quadratwurzel
- Quadrat
- Subtrahieren
- Summe
- Tangens
- Zuordnen von Buckets/Bereiche

