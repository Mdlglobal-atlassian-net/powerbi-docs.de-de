---
title: Ausführen von R-Skripts in Power BI Desktop
description: Ausführen von R-Skripts in Power BI Desktop
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 01/14/2020
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 358a61c13418bd29a9e83ed7029e8b90f9a5988e
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "76161525"
---
# <a name="run-r-scripts-in-power-bi-desktop"></a>Ausführen von R-Skripts in Power BI Desktop

Sie können R-Skripts direkt in Power BI Desktop ausführen und die resultierenden Datasets in ein Power BI Desktop-Datenmodell importieren.

## <a name="install-r"></a>Installieren von R

Damit Sie R-Skripts in Power BI Desktop ausführen können, müssen Sie R auf dem lokalen Computer installieren. Sie können R über zahlreiche Webseiten im Internet kostenlos herunterladen und installieren, u. a. aus dem [Microsoft R Application Network](https://mran.revolutionanalytics.com/download/) und aus dem [CRAN-Repository](https://cran.r-project.org/bin/windows/base/). Das aktuelle Release unterstützt Unicode-Zeichen und Leerzeichen im Installationspfad.

## <a name="run-r-scripts"></a>Ausführen von R-Skripts

Sie können R-Skripts in nur wenigen Schritten in Power BI Desktop ausführen und ein Datenmodell erstellen. Mit dem Datenmodell können Sie Berichte erstellen und diese im Power BI-Dienst freigeben. Die R-Skripterstellung in Power BI Desktop unterstützt jetzt Zahlenformate, die Dezimaltrennzeichen (.) und Kommas (,) verwenden.

### <a name="prepare-an-r-script"></a>Vorbereiten eines R-Skripts

Wenn Sie ein R-Skript in Power BI Desktop ausführen möchten, erstellen Sie das Skript in Ihrer lokalen R-Entwicklungsumgebung, und vergewissern Sie sich, dass es erfolgreich ausgeführt wird.

Zum Ausführen des Skripts in Power BI Desktop stellen Sie sicher, dass das Skript in einem neuen und unveränderten Arbeitsbereich erfolgreich ausgeführt wird. Diese Voraussetzung bedeutet, dass alle Pakete und Abhängigkeiten explizit geladen und ausgeführt werden müssen. Zum Ausführen von abhängigen Skripts können Sie `source()` verwenden.

Beim Vorbereiten und Ausführen eines R-Skripts in Power BI Desktop müssen einige Einschränkungen beachtet werden:

* Es werden nur Datenrahmen importiert. Stellen Sie deshalb sicher, dass die nach Power BI zu importierenden Daten in einem Datenrahmen dargestellt werden.
* Spalten mit dem Typ „Komplex“ oder „Vektor“ werden nicht importiert und in der erstellten Tabelle durch Fehlerwerte ersetzt.
* In Power BI Desktop werden `N/A`-Werte in `NULL`-Werte übersetzt.
* Wenn die Ausführung eines R-Skripts länger als 30 Minuten dauert, wird ein Timeout ausgelöst.
* Bei interaktiven Aufrufen in einem R-Skript, z. B. beim Warten auf eine Benutzereingabe, wird die Ausführung des Skripts angehalten.
* Wenn Sie das Arbeitsverzeichnis im R-Skript angeben, *müssen* Sie den vollständigen Pfad zu diesem Verzeichnis angeben – der relative Pfad genügt nicht.

### <a name="run-your-r-script-and-import-data"></a>Ausführen des R-Skripts und Importieren der Daten

Jetzt können Sie Ihr R-Skript zum Importieren von Daten in Power BI Desktop ausführen:

1. Wählen Sie in Power BI Desktop **Daten abrufen** und dann **Andere** > **R-Skript** aus, und klicken Sie dann auf **Verbinden**:

    ![Verbindung mit R-Skript, Kategorie „Andere“, Dialogfeld „Daten abrufen“, Power BI Desktop](media/desktop-r-scripts/r-scripts-1.png)

2. Wenn R auf Ihrem lokalen Computer installiert ist, kopieren Sie Ihr Skript einfach in das Skriptfenster, und klicken Sie auf **OK**. Die neueste installierte Version wird als Ihre R-Engine angezeigt.

    ![Dialogfeld „R-Skript“, Power BI Desktop](media/desktop-r-scripts/r-scripts-2.png)

3. Wählen Sie **OK** aus, um das R-Skript auszuführen. Wenn das Skript erfolgreich ausgeführt wird, können Sie die resultierenden Datenrahmen auswählen, die Sie dem Power BI-Modell hinzufügen möchten.

Sie können steuern, welche R-Installation zur Skriptausführung verwendet wird. Wählen Sie zum Festlegen Ihrer R-Installationseinstellungen **Datei** > **Optionen und Einstellungen** > **Optionen** aus, und klicken Sie dann auf **R-Skripterstellung**. Unter **Optionen für R-Skripts** zeigt die Dropdownliste **Erkannte R-Basisverzeichnisse** Ihre aktuelle R-Installationsauswahl an. Wenn die gewünschte R-Installation nicht angezeigt wird, wählen Sie **Andere** aus, und wechseln Sie dann in **R-Basisverzeichnis festlegen** zu Ihrem bevorzugten R-Installationsorder.

![Optionen für R-Skripts, Dialogfeld „Optionen“, Power BI Desktop](media/desktop-r-scripts/r-scripts-4.png)

### <a name="refresh"></a>Vorschau

Sie können ein R-Skript in Power BI Desktop aktualisieren. Wenn Sie ein R-Skript aktualisieren, führt Power BI Desktop das R-Skript in der Power BI Desktop-Umgebung erneut aus.

## <a name="next-steps"></a>Weitere Schritte

Betrachten Sie die folgenden zusätzlichen Informationen über R in Power BI.

* [Erstellen von Power BI-Visualisierungen mithilfe von R](desktop-r-visuals.md)
* [Verwenden einer externen R-IDE mit Power BI](desktop-r-ide.md)
