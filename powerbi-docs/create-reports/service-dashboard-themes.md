---
title: Verwenden von Dashboarddesigns im Power BI-Dienst
description: Erfahren Sie, wie Sie eine benutzerdefinierte Farbpalette verwenden und auf das gesamte Dashboard im Power BI-Dienst anwenden können.
author: maggiesMSFT
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 08/22/2018
ms.author: maggies
LocalizationGroup: Create reports
ms.openlocfilehash: e2793fe56df462fd5f1bd1c266b75ad14fd9b375
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/13/2020
ms.locfileid: "83311382"
---
# <a name="use-dashboard-themes-in-power-bi-service"></a>Verwenden von Dashboarddesigns im Power BI-Dienst
Mit **Dashboarddesigns** können Sie einem Dashboard ein Farbschema zuweisen (Unternehmensfarben, Farben der Jahreszeit oder beliebige andere Farben). Wenn Sie ein **Dashboarddesigns** zuweisen, verwenden alle Visualisierungen des Dashboards die Farben des gewünschten Farbschemas (mit wenigen Ausnahmen, siehe unten).

![Beispieldashboard mit Design](media/service-dashboard-themes/power-bi-full-dashboard-theme.png)

Wenn Sie die Farben der Berichtsvisuals auf dem Dashboard ändern, wirkt sich das nicht auf die Visuals im Bericht aus. Wenn Sie Kacheln eines Berichts anheften, [auf die bereits ein Berichtsdesign angewendet wurde](desktop-report-themes.md), können Sie sich entscheiden, ob Sie das aktuelle Design beibehalten oder das Dashboarddesign verwenden möchten.


## <a name="prerequisites"></a>Voraussetzungen
* Um die Schritte selbst nachzuvollziehen, öffnen Sie das [Dashboard zum Sales and Marketing sample](sample-datasets.md).


## <a name="how-dashboard-themes-work"></a>Funktionsweise von Dashboarddesigns
Öffnen Sie zunächst ein Dashboard, das Sie erstellt haben (oder das Sie bearbeiten dürfen) und das Sie anpassen möchten. Klicken Sie auf **Weitere Optionen** (...) und dann auf **Dashboarddesign**. 

![Option „Dashboarddesign“](media/service-dashboard-themes/power-bi-dashboard-theme.png)

Wählen Sie im sich öffnenden Dashboardbereich ein vordefiniertes Design aus.  Im Beispiel unten wurde **Dunkel** ausgewählt.

![Option „Hell“ ausgewählt](media/service-dashboard-themes/power-bi-theme-menu.png)

![Option „Dunkel“ angewendet](media/service-dashboard-themes/power-bi-theme-dark.png)

## <a name="create-a-custom-theme"></a>Erstellen eines benutzerdefinierten Designs

Das Standarddesign für Power BI-Dashboards ist **Hell**. Wenn Sie die Farben anpassen oder Ihr eigenes Design erstellen möchten, klicken Sie im Dropdownmenü auf **Benutzerdefiniert**. 

![„Benutzerdefiniert“ im Dropdownmenü wählen](media/service-dashboard-themes/power-bi-theme-custom.png)

Erstellen Sie anhand der benutzerdefinierten Optionen Ihr eigenes Dashboarddesign. Wenn Sie ein Hintergrundbild hinzufügen möchten, wird empfohlen, dass dieses mindestens eine Auflösung von 1920×1080 aufweist. Um ein Bild als Hintergrund zu verwenden, laden Sie das Bild auf eine öffentliche Website hoch, kopieren die URL und fügen sie in das Feld **Bild-URL** ein. 

### <a name="using-json-themes"></a>Verwenden von JSON-Designs
Alternativ können Sie ein benutzerdefiniertes Design erstellen, indem Sie eine JSON-Datei hochladen, in der die Einstellungen für alle Farben, die Sie auf Ihrem Dashboard verwenden möchten, enthalten sind. In Power BI Desktop verwenden Berichtsersteller JSON-Dateien, um [Designs für Berichte zu erstellen](desktop-report-themes.md). Die gleichen JSON-Dateien können für Dashboards hochgeladen werden, oder Sie können den [Designkatalog](https://community.powerbi.com/t5/Themes-Gallery/bd-p/ThemesGallery) in der Power BI-Community durchsuchen und JSON-Dateien von dort hochladen. 

![Designkatalog](media/service-dashboard-themes/power-bi-theme-gallery.png)

Sie können Ihr benutzerdefiniertes Design auch als JSON-Datei speichern und mit anderen Dashboarderstellern teilen. 

### <a name="use-a-theme-from-the-theme-gallery"></a>Verwenden eines Designs aus dem Designkatalog

Genauso wie bei den benutzerdefinierten und integrierten Optionen werden die Farben automatisch auf alle Kacheln auf dem Dashboard angewendet, wenn ein Design hochgeladen wird. 

1. Zeigen Sie auf ein Design, und klicken Sie auf **Bericht anzeigen**.

    ![Bericht anzeigen](media/service-dashboard-themes/power-bi-choose-theme.png)

2. Scrollen Sie nach unten, und suchen Sie den Link zur JSON-Datei.  Klicken Sie auf das Downloadsymbol, und speichern Sie die Datei.

    ![JSON-Datei „Spring Day“](media/service-dashboard-themes/power-bi-theme-json.png)

3. Kehren Sie zum Power BI-Dienst zurück, und wählen Sie im Fenster „Dashboarddesign“ **JSON-Schema hochladen** aus.

    ![JSON-Schema hochladen](media/service-dashboard-themes/power-bi-upload-theme.png)

4. Navigieren Sie zum Speicherort der gespeicherten JSON-Designdatei, und klicken Sie auf **Öffnen**.

5. Klicken Sie auf der Seite „Dashboarddesign“ auf **Speichern**. Das neue Design wird auf Ihr Dashboard angewendet.

    ![Angewendetes neues Design](media/service-dashboard-themes/power-bi-json.png)

## <a name="considerations-and-limitations"></a>Überlegungen und Einschränkungen

* Wenn das Design Ihres Berichts vom Dashboarddesign abweicht, können Sie auswählen, ob für die Visualisierung das aktuelle Design oder das Dashboarddesign verwendet werden soll, um trotz verschiedener Quellen einheitliche Visualisierungen zu erzielen. Wenn Sie eine Kachel auf einem Dashboard anheften, wählen Sie **Aktuelles Design beibehalten** aus, um das Berichtsdesign beizubehalten. Das Visual auf dem Dashboard behält das Berichtsdesign mit Einstellung für die Transparenz bei. 

    Sie sehen Optionen für das **Kacheldesign** nur dann, wenn Sie einen Bericht in Power BI Desktop erstellt, [ein Berichtsdesign hinzugefügt](desktop-report-themes.md), und dann den Bericht im Power BI-Dienst veröffentlicht haben. 

    ![„Aktuelles Design beibehalten“ ausgewählt](media/service-dashboard-themes/power-bi-keep-current.png)

    Heften Sie die Kachel erneut an, und wählen Sie **Use dashboard theme** (Dashboarddesign verwenden) aus.

    ![Zieldesign verwenden](media/service-dashboard-themes/power-bi-use-destination.png)

* Dashboarddesigns können nicht auf angeheftete Live-Berichtsseiten, iframe-Kacheln, SSRS-Kacheln oder Bilder angewendet werden.
* Dashboarddesigns können auf mobilen Geräten angezeigt werden. Ein Dashboarddesign können Sie allerdings nur im Power BI-Dienst erstellen. 
* Benutzerdefinierte Dashboarddesigns können nur auf angeheftete Kacheln aus Berichten angewendet werden. 

