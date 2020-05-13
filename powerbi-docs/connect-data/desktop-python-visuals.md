---
title: Erstellen von Power BI-Visuals mithilfe von Python in Power BI Desktop
description: Erstellen von Power BI-Visualisierungen mithilfe von Python
author: otarb
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 04/03/2020
ms.author: otarb
LocalizationGroup: Create reports
ms.openlocfilehash: 72c285fd57af21fcb3d1a4568a5ff2e83016072f
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/13/2020
ms.locfileid: "83291901"
---
# <a name="create-power-bi-visuals-by-using-python"></a>Erstellen von Power BI-Visualisierungen mithilfe von Python

Mit *Power BI Desktop* können Sie Python zum Visualisieren Ihrer Daten verwenden.

## <a name="prerequisites"></a>Voraussetzungen

Bearbeiten Sie das Tutorial [Ausführen von Python-Skripts in Power BI Desktop](desktop-python-scripts.md). Verwenden Sie dafür das folgende Python-Skript:

```python
import pandas as pd 
df = pd.DataFrame({ 
    'Fname':['Harry','Sally','Paul','Abe','June','Mike','Tom'], 
    'Age':[21,34,42,18,24,80,22], 
    'Weight': [180, 130, 200, 140, 176, 142, 210], 
    'Gender':['M','F','M','M','F','M','M'], 
    'State':['Washington','Oregon','California','Washington','Nevada','Texas','Nevada'],
    'Children':[4,1,2,3,0,2,0],
    'Pets':[3,2,2,5,0,1,5] 
}) 
print (df) 
```

Im Artikel [Ausführen von Python-Skripts in Power BI Desktop](desktop-python-scripts.md) wird erläutert, wie Sie Python auf Ihrem lokalen Computer installieren und für die Python-Skripterstellung in Power BI Desktop aktivieren können. In diesem Tutorial werden Daten aus dem obigen Skript verwendet, um die Erstellung von Python-Visuals zu veranschaulichen.

## <a name="create-python-visuals-in-power-bi-desktop"></a>Erstellen von visuellen Python-Elementen in Power BI Desktop

1. Klicken Sie im Bereich **Visualisierungen** auf das Symbol **Python-Visual**.

   ![Die Option „Python“ in „Visualisierungen“](media/desktop-python-visuals/python-visuals-2.png)

1. Klicken Sie im daraufhin angezeigten Dialogfeld **Visuelle Skriptelemente aktivieren** auf **Aktivieren**.

    Wenn Sie einem Bericht ein Python-Visual hinzufügen, führt Power BI Desktop die folgenden Aktionen aus:

    - Auf der Berichtzeichnungsfläche wird ein Platzhalterbild für ein visuelles Python-Element angezeigt.

    - Am unteren Rand des mittleren Bereichs wird der **Python-Skript-Editor** angezeigt.

    ![Ausführen eines Skripts im Python-Skript-Editor](media/desktop-python-visuals/python-visuals-3.png)

1. Ziehen Sie als Nächstes die Felder **Age** (Alter), **Children** (Kinder), **Fname** (Vorname), **Gender** (Geschlecht), **Pets** (Haustiere), **State** (Staat) und **Weight** (Gewicht) in den Abschnitt **Werte**, in dem die Meldung **Hier Datenfelder hinzufügen** angezeigt wird.

    ![Ziehen auf „Hier Datenfelder hinzufügen“](media/desktop-python-visuals/python-visuals-15.png)

   Ihr Python-Skript kann nur Felder verwenden, die dem Abschnitt **Werte** hinzugefügt wurden. Während Sie an Ihrem Python-Skript arbeiten, können Sie Felder zum Abschnitt **Werte** hinzufügen oder aus diesem entfernen. Power BI Desktop erkennt Änderungen an Feldern automatisch.

   > [!NOTE]
   > Der Standardaggregationstyp für visuelle Python-Elemente lautet *Nicht zusammenfassen*.
   > 
   > 

1. Jetzt können Sie die Daten verwenden, die Sie zum Erstellen einer Zeichnung ausgewählt haben.

    Wenn Sie Felder auswählen oder entfernen, wird im Python-Skript-Editor automatisch Unterstützungscode generiert bzw. aus diesem entfernt. 

    Basierend auf Ihrer Auswahl generiert der Python-Skript-Editor den folgenden Bindungscode.

    - Der Editor hat mit den von Ihnen hinzugefügten Feldern einen *Dataset*-Datenrahmen erstellt.
    - Die Standardaggregation lautet *Nicht zusammenfassen*.
    - Ähnlich wie bei Tabellenvisualisierungen werden Felder gruppiert und doppelte Zeilen nur einmal angezeigt.

    ![Python-Skript-Editor nur mit Kommentaren](media/desktop-python-visuals/python-visuals-10.png)

     > [!TIP]
     > In bestimmten Fällen sind Gruppierungen möglicherweise nicht erwünscht, oder es sollen alle Zeilen angezeigt werden, einschließlich doppelter Zeilen. Dann können Sie Ihrem Dataset ein Indexfeld hinzufügen, sodass alle Zeilen als eindeutig betrachtet werden und keine Gruppierung erfolgt.

   Sie können auf Spalten im Dataset zugreifen, indem Sie deren Namen verwenden. Beispielsweise können Sie für den Zugriff auf das Feld für das Alter den Code `dataset["Age"]` in Ihr Python-Skript schreiben.

1. Mit dem Datenrahmen, der anhand der von Ihnen ausgewählten Felder automatisch generiert wurde, können Sie ein Python-Skript schreiben, mit dem Diagramme auf dem Python-Standardgerät ausgegeben werden. Sobald das Skript vollständig ist, sollten Sie auf der Titelleiste des **Python-Skript-Editors** auf **Ausführen** klicken.

   Power BI Desktop zeichnet das Visual neu, wenn eines der folgenden Ereignisse eintritt:

   - Wenn Sie auf der Titelleiste des **Python-Skript-Editors** **Ausführen** auswählen.
   - Bei jedem Ändern der Daten durch Aktualisieren, Filtern oder Hervorheben von Daten.

   Wenn Sie ein Python-Skript ausführen, das einen Fehler auslöst, wird das Python-Visual nicht gezeichnet, und es wird eine Fehlermeldung in der Canvas angezeigt. Sie können Fehlerdetails abrufen, indem Sie in der Meldung auf **Details anzeigen** klicken.

   Um eine größere Ansicht der Visualisierungen zu erhalten, können Sie den **Python-Skript-Editor**minimieren.

Im Folgenden erfahren Sie, wie Sie Visuals erstellen können.

## <a name="create-a-scatter-plot"></a>Erstellen eines Punktdiagramms

Wir wollen nun ein Punktdiagramm erstellen, um zu überprüfen, ob eine Korrelation zwischen dem Alter und dem Gewicht besteht.

1. Geben Sie unter **Paste or type your script code here** (Hier Ihren Skriptcode einfügen oder eingeben) den folgenden Code ein:

   ```python
   import matplotlib.pyplot as plt 
   dataset.plot(kind='scatter', x='Age', y='Weight', color='red')
   plt.show() 
   ```  

   Der Bereich des Python-Skript-Editors sollte nun wie folgt aussehen:

   ![Python-Skript-Editor mit Befehlen](media/desktop-python-visuals/python-visuals-11.png)

   Die Bibliothek **Matplotlib** wird importiert, um die Visuals zu zeichnen und zu erstellen.

1. Wenn Sie auf die Schaltfläche **Skript ausführen** klicken, wird der Platzhalter für das Python-Visual durch das folgende Punktdiagramm ersetzt.

   ![Durch das Python-Skript generierte Visualisierung](media/desktop-python-visuals/python-visuals-12.png)

## <a name="create-a-line-plot-with-multiple-columns"></a>Erstellen eines Liniendiagramms mit mehreren Spalten

 Im Folgenden wird erläutert, wie Sie ein Liniendiagramm zu jeder Person erstellen, an dem die Anzahl der Kinder und Haustiere abgelesen werden können. Entfernen Sie den Code unter **Paste or type your script code here** (Hier Ihren Skriptcode einfügen oder eingeben), oder kommentieren Sie ihn aus, und geben Sie den folgenden Python-Code ein:

 ```python
 import matplotlib.pyplot as plt 
ax = plt.gca() 
dataset.plot(kind='line',x='Fname',y='Children',ax=ax) 
dataset.plot(kind='line',x='Fname',y='Pets', color='red', ax=ax) 
plt.show() 
```

Wenn Sie auf die Schaltfläche **Skript ausführen** klicken, wird das folgende Liniendiagramm mit mehreren Spalten generiert.

![Liniendiagramm mit mehreren Spalten aus dem Python-Skript](media/desktop-python-visuals/python-visuals-13.png)

## <a name="create-a-bar-plot"></a>Erstellen eines Balkendiagramms

Zuletzt wollen wir ein Balkendiagramm zum Alter jeder Person erstellen. Entfernen Sie den Code unter **Paste or type your script code here** (Hier Ihren Skriptcode einfügen oder eingeben), oder kommentieren Sie ihn aus, und geben Sie den folgenden Python-Code ein:

```python
import matplotlib.pyplot as plt 
dataset.plot(kind='bar',x='Fname',y='Age') 
plt.show() 
```

Wenn Sie auf die Schaltfläche **Skript ausführen** klicken, wird das folgende Balkendiagramm erstellt:

![Balkendiagramm aus dem Python-Skript](media/desktop-python-visuals/python-visuals-14.png) 

## <a name="security"></a>Sicherheit

> [!IMPORTANT] 
> **Sicherheit von Python-Skripts:** Visuelle Python-Elemente werden aus Python-Skripts erstellt, die Code mit Sicherheits- oder Datenschutzrisiken enthalten können. Wenn ein Benutzer ein visuelles Python-Element zum ersten Mal aufruft oder damit interagiert, wird eine Sicherheitswarnmeldung angezeigt. Aktivieren Sie visuelle Python-Elemente nur dann, wenn Sie dem Autor und der Quelle vertrauen, oder wenn Sie die zugehörigen Python-Skripts überprüft und nachvollzogen haben.
>  

## <a name="more-information-about-plotting-with-matplotlib-pandas-and-python"></a>Weitere Informationen zum Zeichnen mit Matplotlib, Pandas und Python

Dieses Tutorial soll Ihnen den Einstieg in die Erstellung von Visuals mit Python in Power BI Desktop erleichtern. Die vielen Optionen und Funktionen zum Erstellen von visuellen Berichten mithilfe von Python, Pandas und der Bibliothek Matplotlib können in diesem Rahmen nur grob vorgestellt werden. Es gibt noch viele weitere Informationen. Hier finden Sie einige Links, die Ihnen beim Start helfen:

- Dokumentation auf der [Matplotlib](https://matplotlib.org/)-Website. 
- [Matplotlib Tutorial: A Basic Guide to Use Matplotlib with Python (Matplotlib-Tutorial: Basisanleitung zur Verwendung von Matplotlib mit Python)](https://www.datasciencelearner.com/matplotlib-tutorial-complete-guide-to-use-matplotlib-with-python/) 
- [Matplotlib Tutorial – Python Matplotlib Library with Examples (Matplotlib-Tutorial: Matplotlib-Bibliothek für Python mit Beispielen)](https://www.edureka.co/blog/python-matplotlib-tutorial/) 
- [Pandas API Reference (API-Referenz für Pandas)](https://pandas.pydata.org/pandas-docs/stable/reference/index.html) 
- [Python-Visualisierungen im Power BI-Dienst](https://powerbi.microsoft.com/blog/python-visualizations-in-power-bi-service/) 
- [Erstellen von Python-Visuals in Power BI](https://www.absentdata.com/how-to-user-python-and-power-bi/)

## <a name="known-limitations"></a>Bekannte Einschränkungen

Bei Python-Visuals in Power BI Desktop gelten einige Einschränkungen:

- Einschränkungen bei der Datengröße. Die vom Python-Visual zum Zeichnen verwendeten Daten sind auf 150.000 Zeilen beschränkt. Bei Auswahl von mehr als 150.000 Zeilen werden nur die oberen 150.000 Zeilen verwendet, und im Bild wird eine Meldung angezeigt. Darüber hinaus gilt für die Eingabedaten eine Maximalgröße von 250 MB. 
- Auflösung. Alle Python-Visuals werden mit 72 dpi angezeigt.
- Einschränkung bei der Berechnungszeit. Wenn die Berechnung eines Python-Visuals länger als fünf Minuten dauert, wird die Ausführung aufgrund der Zeitüberschreitung abgebrochen, was zu einem Fehler führt.
- Beziehungen. Wie bei anderen Power BI Desktop-Visuals tritt ein Fehler auf, wenn Datenfelder aus unterschiedlichen Tabellen ausgewählt werden, zwischen denen keine Beziehung definiert ist.
- Visuelle Python-Elemente werden aktualisiert, wenn Daten aktualisiert, gefiltert oder hervorgehoben werden. Das Bild selbst ist jedoch nicht interaktiv und kann nicht als Quelle für die Kreuzfilterung verwendet werden.
- Python-Visuals reagieren auf das Hervorheben anderer Visuals. Sie können jedoch nicht auf Elemente in den Python-Visuals klicken, um eine Kreuzfilterung für andere Elemente durchzuführen.
- Nur auf dem Python-Standardanzeigegerät erzeugte Zeichnungen werden im Zeichenbereich ordnungsgemäß angezeigt. Verwenden Sie nicht explizit ein anderes Python-Anzeigegerät.
- Python-Visuals unterstützen das Umbenennen von Eingabespalten nicht. Spalten werden nach Ihrem ursprünglichen Namen bei der Skriptausführung bezeichnet.

## <a name="next-steps"></a>Nächste Schritte

Betrachten Sie die folgenden zusätzlichen Informationen über Python in Power BI.

- [Ausführen von Python-Skripts in Power BI Desktop](desktop-python-scripts.md)
- [Verwenden einer externen Python-IDE mit Power BI](desktop-python-ide.md)

