---
title: Deaktivieren der Hintergrundaktualisierung in Power Query
description: Hier erfahren Sie, wann Sie die Hintergrundaktualisierung in Power Query deaktivieren sollen.
author: peter-myers
manager: asaxton
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 09/26/2019
ms.author: v-pemyer
ms.openlocfilehash: 59cb62a9186da03a265fc3a8711d7275c3772af3
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "75623059"
---
# <a name="disable-power-query-background-refresh"></a>Deaktivieren der Hintergrundaktualisierung in Power Query

Dieser Artikel ist an Modellierer von Import-Daten gerichtet, die mit Power BI Desktop arbeiten.

Wenn Power Query Daten importiert, werden standardmäßig bis zu 1000 Zeilen mit Vorschaudaten für jede Abfrage zwischengespeichert. Die Datenvorschau hilft Ihnen, eine schnelle Vorschau der Quelldaten und der Transformationsergebnisse für jeden Schritt Ihrer Abfragen zu erhalten. Die Daten werden separat auf der Festplatte und nicht in der Power BI Desktop-Datei gespeichert.

Wenn Ihre Power BI Desktop-Datei jedoch viele Abfragen enthält, kann das Abrufen und Speichern von Vorschaudaten die Zeit für eine Aktualisierung verlängern.

## <a name="recommendation"></a>Empfehlung

Sie erreichen eine schnellere Aktualisierung, indem Sie die Power BI Desktop-Datei so einstellen, dass der Vorschaucache  _im Hintergrund aktualisiert wird_. In Power BI Desktop aktivieren Sie diese durch Auswählen von _Datei > Optionen und Einstellungen > Optionen_. Wählen Sie dann die _Seite zum Laden von Daten_ aus. Sie können dann die Option **Download der Datenvorschau im Hintergrund zulassen** aktivieren. Beachten Sie, dass diese Option nur für die aktuelle Datei festgelegt werden kann.

![Optionen der Hintergrunddaten in Power BI Desktop](media/power-query-background-refresh/power-query-options-background-data.png)

Die Aktivierung der Hintergrundaktualisierung kann dazu führen, dass die Vorschaudaten veraltet werden. In diesem Fall gibt der Power Query-Editor folgende Warnung aus:

![Warnung des Power Query-Editors über veraltete Vorschaudaten](media/power-query-background-refresh/power-query-preview-data-old.png)

Es ist immer möglich, den Vorschaucache zu aktualisieren. Sie können diesen für eine einzelne Abfrage oder für alle Abfragen aktualisieren, indem Sie den Befehl **Vorschau aktualisieren** verwenden. Sie finden diesen im Menüband **Home** des Power Query-Editor-Fensters.

![Power Query-Editor-Befehle zum Aktualisieren der Vorschaudaten](media/power-query-background-refresh/power-query-refresh-preview-data.png)

## <a name="next-steps"></a>Weitere Schritte

Weitere Informationen zu diesem Artikel finden Sie in den folgenden Ressourcen:

- [Power Query-Dokumentation](/power-query/)
- Fragen? [Stellen Sie Ihre Frage in der Power BI-Community.](https://community.powerbi.com/)
