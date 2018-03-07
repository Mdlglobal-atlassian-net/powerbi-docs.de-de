---
title: "Ausführen von R-Skripts in Power BI Desktop"
description: "Ausführen von R-Skripts in Power BI Desktop"
services: powerbi
documentationcenter: 
author: davidiseminger
manager: kfile
backup: 
editor: 
tags: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 12/06/2017
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 1b8b6dc3932ec4bc1eddd24c91a81a0eaafae479
ms.sourcegitcommit: 88c8ba8dee4384ea7bff5cedcad67fce784d92b0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/24/2018
---
# <a name="run-r-scripts-in-power-bi-desktop"></a>Ausführen von R-Skripts in Power BI Desktop
Sie können R-Skripts direkt in **Power BI Desktop** ausführen und die resultierenden Datasets in ein Power BI Desktop-Datenmodell importieren.

## <a name="install-r"></a>Installieren von R
Damit Sie R-Skripts in Power BI Desktop ausführen können, müssen Sie **R** auf dem lokalen Computer installieren. **R** können Sie an vielen Stellen im Internet kostenlos herunterladen und installieren, u.a. von der [Revolution R Open-Downloadseite](https://mran.revolutionanalytics.com/download/) und aus dem [CRAN-Repository](https://cran.r-project.org/bin/windows/base/). Die aktuelle Version der R-Skripterstellung in Power BI Desktop unterstützt Unicode-Zeichen ebenso wie Leerzeichen (leere Zeichen) im Installationspfad.

## <a name="run-r-scripts"></a>Ausführen von R-Skripts
Mit nur wenigen Schritten in Power BI Desktop können Sie R-Skripts ausführen und ein Datenmodell erstellen, auf Basis dessen Sie Berichte erstellen und im Power BI-Dienst freigeben können. Die R-Skripterstellung in Power BI Desktop unterstützt jetzt Zahlenformate, die Dezimaltrennzeichen (.) und Kommas (,) verwenden.

### <a name="prepare-an-r-script"></a>Vorbereiten eines R-Skripts
Wenn Sie ein R-Skript in Power BI Desktop ausführen möchten, erstellen Sie das Skript in Ihrer lokalen R-Entwicklungsumgebung, und vergewissern Sie sich, dass es erfolgreich ausgeführt wird.

Zum Ausführen des Skripts in Power BI Desktop stellen Sie sicher, dass das Skript in einem neuen und unveränderten Arbeitsbereich erfolgreich ausgeführt wird. Dies bedeutet, dass alle Pakete und Abhängigkeiten explizit geladen und ausgeführt werden müssen. Zum Ausführen von abhängigen Skripts können Sie *source()* verwenden.

Beim Vorbereiten und Ausführen eines R-Skripts in Power BI Desktop müssen Sie einige Einschränkungen beachten:

* Es werden nur Datenrahmen importiert. Stellen Sie darum sicher, dass die nach Power BI zu importierenden Daten in einem Datenrahmen dargestellt werden.
* Spalten mit dem Typ „Komplex“ oder „Vektor“ werden nicht importiert. Sie werden in der erstellten Tabelle durch Fehlerwerte ersetzt.
* In Power BI Desktop werden nicht vorhandene Werte als NULL-Werte dargestellt.
* Wenn die Ausführung eines R-Skripts länger als 30 Minuten dauert, wird sie mit einem Timeout abgebrochen.
* Bei interaktiven Aufrufen in einem R-Skript, z. B. beim Warten auf eine Benutzereingabe, wird die Ausführung des Skripts angehalten.
* Wenn Sie das Arbeitsverzeichnis im R-Skript angeben, *müssen* Sie den vollständigen Pfad zu diesem Verzeichnis angeben – der relative Pfad genügt nicht.

### <a name="run-your-r-script-and-import-data"></a>Ausführen des R-Skripts und Importieren der Daten
1. In Power BI Desktop befindet sich der R-Skript-Datenconnector unter **Daten abrufen**. Zum Ausführen Ihres R-Skripts wählen Sie **Daten abrufen &gt; Mehr...** und anschließend **Sonstige &gt; R-Skript** aus, wie in der folgenden Abbildung dargestellt.
   
   ![](media/desktop-r-scripts/r-scripts-1.png)
2. Wenn R auf dem lokalen Computer installiert ist, wird die neueste installierte Version als R-Modul ausgewählt. Kopieren Sie Ihr Skript einfach in das Skriptfenster, und wählen Sie **OK**aus.
   
   ![](media/desktop-r-scripts/r-scripts-2.png)
3. Wenn R nicht installiert ist, nicht erkannt wird oder mehrere Installationen auf dem lokalen Computer vorhanden sind, erweitern Sie **R-Installationseinstellungen** , um Installationsoptionen anzuzeigen oder die Installation auszuwählen, mit der Sie das R-Skript ausführen möchten.
   
   ![](media/desktop-r-scripts/r-scripts-3.png)
   
   Wenn R installiert ist, jedoch nicht erkannt wird, können Sie dessen Speicherort explizit in dem Textfeld angeben, das angezeigt wird, wenn Sie **R-Installationseinstellungen**erweitern. In der Abbildung oben wird der Pfad *C:\Programme\R\R-3.2.0* explizit im Textfeld angegeben.
   
   Die R-Installationseinstellungen befinden sich zentral im Abschnitt „R-Skripterstellung“ des Dialogfelds „Optionen“. Um Ihre R-Installationseinstellungen festzulegen, wählen Sie **Datei > Optionen und Einstellungen** und dann **Optionen > R-Skripterstellung** aus. Wenn mehrere Installationen von R verfügbar sind, wird ein Dropdownmenü angezeigt, das Ihnen die Auswahl der gewünschten Installation ermöglicht.
   
   ![](media/desktop-r-scripts/r-scripts-4.png)
4. Wählen Sie **OK** aus, um das R-Skript auszuführen. Wenn das Skript erfolgreich ausgeführt wird, können Sie die resultierenden Datenrahmen auswählen, die Sie dem Power BI-Modell hinzufügen möchten.

### <a name="refresh"></a>Aktualisieren
Sie können ein R-Skript in Power BI Desktop aktualisieren. Wenn Sie ein R-Skript aktualisieren, führt Power BI Desktop das R-Skript in der Power BI Desktop-Umgebung erneut aus.

## <a name="next-steps"></a>Nächste Schritte
Betrachten Sie die folgenden zusätzlichen Informationen über R in Power BI.

* [Erstellen von visuellen R-Elementen in Power BI Desktop](desktop-r-visuals.md)
* [Verwenden einer externen R-IDE mit Power BI](desktop-r-ide.md)
