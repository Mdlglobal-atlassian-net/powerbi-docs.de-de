---
title: Verwenden einer externen R-IDE mit Power BI
description: Sie können eine externe IDE starten und mit Power BI verwenden.
author: davidiseminger
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/08/2019
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 127778b5edae9670a009ee74554a5abe1039f186
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/13/2020
ms.locfileid: "83290567"
---
# <a name="use-an-external-r-ide-with-power-bi"></a>Verwenden einer externen R-IDE mit Power BI
Mit **Power BI Desktop** können Sie eine externe R-IDE (Integrated Development Environment, integrierte Entwicklungsumgebung) zum Erstellen und Optimieren von R-Skripts verwenden und diese Skripts dann in Power BI nutzen.

![](media/desktop-r-ide/r-ide_1a.png)

## <a name="enable-an-external-r-ide"></a>Aktivieren einer externen R-IDE
Vor der Veröffentlichung dieser Funktion mussten Sie zum Erstellen und Ausführen von R-Skripts den R-Skript-Editor in **Power BI Desktop** verwenden. Mit dieser Version können Sie die externe R-IDE aus **Power BI Desktop** starten. Ihre Daten werden automatisch importiert und in der R-IDE angezeigt. Dort können Sie das Skript in der externen R-IDE ändern und dann wieder in **Power BI Desktop** einfügen, um visuelle Power BI-Objekte und -Berichte zu erstellen.

Ab der **Power BI Desktop**-Version von September 2016 (Version 2.39.4526.362) können Sie angeben, welche R-IDE Sie verwenden möchten. Diese wird dann automatisch in **Power BI Desktop** gestartet.

### <a name="requirements"></a>Anforderungen
Um dieses Feature verwenden zu können, müssen Sie eine **R-IDE** auf dem lokalen Computer installieren. Die R-Engine ist in **Power BI Desktop** nicht enthalten und wird nicht bereitgestellt oder installiert. Sie müssen daher **R** separat auf dem lokalen Computer installieren. Sie können die zu verwendende R-IDE-R auswählen. Dabei stehen Ihnen die folgenden Optionen zur Verfügung:

* Sie können Ihre bevorzugte R-IDE installieren. Viele sind kostenlos, z. B. über die [R Open-Downloadseite](https://mran.revolutionanalytics.com/download/) und das [CRAN-Repository](https://cran.r-project.org/bin/windows/base/).
* **Power BI Desktop** unterstützt auch [R Studio](https://www.rstudio.com/) und **Visual Studio 2015** mit den Editoren [*R-Tools für Visual Studio*](/visualstudio/rtvs).
* Sie können auch eine andere **R-IDE** installieren und sie durch **Power BI Desktop** starten lassen. Führen Sie dazu einen der folgenden Schritte aus:
  
  * Verknüpfen Sie **R**-Dateien mit der externen IDE, die von **Power BI Desktop** gestartet werden soll.
  * Sie können die EXE-Datei angeben, die von **Power BI Desktop** gestartet werden soll, indem Sie im Abschnitt *Optionen für R-Skript* des Dialogfelds **Optionen** die Option **Sonstige** angeben. Sie öffnen das Dialogfeld **Optionen**, indem Sie **Datei > Optionen und Einstellungen > Optionen** auswählen.
    
    ![](media/desktop-r-ide/r-ide_1b.png)

Wenn Sie mehrere R-IDEs installiert haben, können Sie angeben, welche gestartet werden soll, indem Sie sie im Dialogfeld *Optionen* in der Dropdownliste **Erkannte R-IDEs** auswählen.

**Power BI Desktop** startet standardmäßig **R Studio** als externe R-IDE, wenn sie auf dem lokalen Computer installiert ist. Wenn **R Studio** nicht installiert ist und Sie über **Visual Studio 2015** mit **R-Tools für Visual Studio** verfügen, wird stattdessen diese IDE gestartet. Wenn keine dieser R-IDEs installiert ist, wird die mit den **R**-Dateien verknüpfte Anwendung gestartet.

Und wenn keine Verknüpfung mit **R**-Dateien vorhanden ist, können Sie im Abschnitt *Wechseln Sie zu Ihrer bevorzugten R-IDE* des Dialogfelds **Optionen** einen Pfad zu einer benutzerdefinierten IDE angeben. Sie können auch eine andere R-IDE starten, indem Sie in **Power BI Desktop** neben dem Pfeilsymbol **R-IDE starten** das Zahnradsymbol **Einstellungen** auswählen.

## <a name="launch-an-r-ide-from-power-bi-desktop"></a>Starten einer R-IDE aus Power BI Desktop
Führen Sie zum Starten einer R-IDE aus **Power BI Desktop** die folgenden Schritte aus:

1. Laden Sie Daten in **Power BI Desktop**.
2. Wählen Sie einige Felder im Bereich **Felder** aus, mit denen Sie arbeiten möchten. Wenn Sie noch keine visuellen Skriptelemente aktiviert haben, werden Sie hierzu aufgefordert.
   
   ![](media/desktop-r-ide/r-ide_3.png)
3. Wenn visuelle Skriptelemente aktiviert wurden, können Sie ein visuelles R-Element im Bereich **Visualisierungen** auswählen. Hiermit wird ein leeres visuelles R-Element erstellt, das die Ergebnisse des Skripts anzeigen kann. Der Bereich **R-Skript-Editor** wird ebenfalls angezeigt.
   
   ![](media/desktop-r-ide/r-ide_4.png)
4. Jetzt können Sie die Felder auswählen, die Sie in Ihrem R-Skript verwenden möchten. Wenn Sie ein Feld auswählen, wird im Feld **R-Skript-Editor** automatisch Skriptcode auf Grundlage der ausgewählten Felder erstellt. Sie können das R-Skript direkt im Bereich **R-Skript-Editor** erstellen (oder einfügen), oder Sie lassen ihn leer.
   
   ![](media/desktop-r-ide/r-ide_5.png)
   
   > [!NOTE]
   > Der Standardaggregationstyp für R-Visuals lautet *Nicht zusammenfassen*.
   > 
   > 
5. Starten Sie jetzt die R-IDE direkt aus **Power BI Desktop** starten. Wählen Sie die Schaltfläche **R-IDE starten** rechts auf der Titelleiste des **R-Skript-Editors** aus, wie unten dargestellt.
   
   ![](media/desktop-r-ide/r-ide_6.png)
6. Die angegebene R-IDE wird von Power BI Desktop gestartet, wie in der folgenden Abbildung dargestellt (in dieser Abbildung ist die Standard-R-IDE **RStudio**).
   
   ![](media/desktop-r-ide/r-ide_7.png)
   
   > [!NOTE]
   > **Power BI Desktop** fügt die ersten drei Zeilen des Skripts hinzu, damit Ihre Daten aus **Power BI Desktop** importiert werden können, wenn Sie das Skript ausführen.
   > 
   > 
7. Im Bereich **R-Skript-Editor** in **Power BI Desktop** erstellten Skripts werden ab Zeile 4 in der R-IDE angezeigt. Jetzt können Sie Ihr eigenes R-Skript in der R-IDE erstellen. Sobald das R-Skript in der R-IDE fertig ist, müssen Sie es kopieren und wieder im Bereich **R-Skript-Editor** in **Power BI Desktop** einfügen, *ohne* die ersten drei Zeilen des Skripts, die von **Power BI Desktop** automatisch generiert wurden. Kopieren Sie die ersten drei Zeilen des Skripts nicht wieder in **Power BI Desktop**, diese Zeilen wurden nur zum Importieren der Daten aus **Power BI Desktop** in die R-IDE benötigt.

### <a name="known-limitations"></a>Bekannte Einschränkungen
Für das Starten einer R-IDE direkt aus Power BI Desktop gelten einige Einschränkungen:

* Das automatische Exportieren eines Skripts aus der R-IDE in **Power BI Desktop** wird nicht unterstützt.
* Der **R Client**-Editor (RGui.exe) wird nicht unterstützt, da der Editor selbst das Öffnen von Dateien nicht unterstützt.

## <a name="next-steps"></a>Weitere Schritte
Betrachten Sie die folgenden zusätzlichen Informationen über R in Power BI.

* [Ausführen von R-Skripts in Power BI Desktop](desktop-r-scripts.md)
* [Erstellen von Power BI-Visualisierungen mithilfe von R](../create-reports/desktop-r-visuals.md)
