---
title: "Änderungsprotokoll für Power BI-Berichtsserver"
description: "Dieses Änderungsprotokoll bezieht sich auf Power BI-Berichtsserver und enthält neue Elemente sowie Fehlerkorrekturen für jeden veröffentlichten Build."
services: powerbi
documentationcenter: 
author: jtarquino
manager: jonhp
backup: maggies
editor: 
tags: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 12/11/2017
ms.author: tankas
ms.openlocfilehash: deff79bba0f7f191a8343629300c725f3150e509
ms.sourcegitcommit: a44c29bbc220ecb1ed80810cb1e7df0db8ea611a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/12/2018
---
# <a name="changelog-for-power-bi-report-server"></a>Änderungsprotokoll für Power BI-Berichtsserver

Dieses Änderungsprotokoll bezieht sich auf Power BI-Berichtsserver und enthält neue Elemente sowie Fehlerkorrekturen für jeden veröffentlichten Build.

Ausführliche Informationen zu neuen Funktionen finden Sie unter [Neuerungen in Power BI-Berichtsserver](whats-new.md).

## <a name="october-2017"></a>Oktober 2017

- **Power BI-Berichtsserver**
    - *Version 1.1.6582.41691 (Build 14.0.600.442), Veröffentlichung: 10. Januar 2018*
        - Sicherheitsupdates
        - Fehlerkorrekturen
            - Es wurde ein Fehler behoben, bei dem „Model.GetParameters “ den Wert 400 zurückgegeben hat.
            - Es wurde ein Fehler beim Festlegen von freigegebenen Datasets für vorhandene paginierte Berichte (RDL) behoben.
            - Der Fehler „ExecutionNotFoundException“ beim Exportieren eines Berichts mit verschiedenen Parametern in das PDF-Format wurde behoben.

    - *Version 1.1.6551.5155 (Build 14.0.600.438), Veröffentlichung: 11. Dezember 2017*
        - Fehlerkorrekturen
            - Fehler beim Speichern von Daten nach der Aktualisierung bei bestimmten Power BI Desktop-Berichten.

    - *Version 1.1.6530.30789 (Build 14.0.600.437), Veröffentlichung: 17. November 2017*
        - Fehlerkorrekturen
            - Korrektur für Standardauthentifizierungsszenarien 
            - Korrektur des Problems, dass im Portal auf der Zeitplanseite für Abonnements, Cacheaktualisierungspläne und Verlaufsmomentaufnahmen keine Wochentage ausgewählt werden konnten
            - Korrektur des Problems bei paginierten Berichten (RDL), dass Werte ohne Farben und Schriftarten nicht ordnungsgemäß ausgegeben werden, wenn in Ausdrücken die CanGrow-Eigenschaft für Textfelder auf „false“ festgelegt ist
            - Korrektur des Problems bei Power BI-Berichten (PBIX), dass durch das Hinzufügen von Legenden zu einem Liniendiagramm ein leeres Visual gerendert wird

    - *Version 1.1.6514.9163 (Build 14.0.600.434), Veröffentlichung: 1. November 2017*
        - Fehlerkorrekturen
            - Korrektur von Problemen bei der Zuverlässigkeit des Uploads von PBIX-Berichten mit mehr als 500 MB
            - Korrektur des Problems beim Laden von Daten für PBIX-Berichte mit mehr als 1 GB

    - *Version 1.1.6513.3500 (Build 14.0.600.433), Veröffentlichung: 31. Oktober 2017*
        - Features
            - Unterstützung von eingebetteten Datenmodellen
            - Anzeigen von Excel-Arbeitsmappen (bei aktivierter Office Online Server-Integration)
            - Geplante Datenaktualisierung (PBIX)
            - Unterstützung von direkten Abfragen
            - Unterstützung von großen Dateien (bis zu 2 GB)
            - Öffentliche REST-API
            - Unterstützung von freigegebenen Datasets in Power BI Desktop (über oData)
            - Unterstützung von URL-Parametern für PBIX-Dateien
            - Verbesserungen in Bezug auf die Barrierefreiheit

- **Power BI Desktop (optimiert für Power BI-Berichtsserver)**
    - *Version: 2.51.4885.2501 (Oktober 2017), Veröffentlichung: 10. Januar 2018*
        - Sicherheitsupdates

    - *Version: 2.51.4885.1423 (Oktober 2017), Veröffentlichung: 17. Oktober 2017*
        - Fehlerkorrekturen
            - Korrektur des Problems, dass die 32-Bit-Version von Power BI Desktop unter x86- Betriebssystemen nicht ausgeführt wird
            - Korrektur für Power BI-Berichte (PBIX), damit die Gitternetzlinien der X-Achse angezeigt werden
            - Weitere Korrekturen geringfügiger Fehler

    - *Version: 2.51.4885.1041 (Oktober 2017), Veröffentlichung: 31. Oktober 2017*
        - Features
            - Enthält Änderungen, die für die Verbindung mit Power BI-Berichtsserver (Oktober 2017) erforderlich sind

## <a name="june-2017"></a>Juni 2017

- **Power BI-Berichtsserver**
    - *Build 14.0.600.309, Veröffentlichung: 10. Januar 2018*
        - Sicherheitsupdates

    - *Build 14.0.600.305, Veröffentlichung: 19. September 2017*  
        - Fehlerkorrekturen
            - Aktualisierung auf das neueste [Websteuerelement für Bing Karten](https://msdn.microsoft.com/library/mt712542.aspx)

    - *Build 14.0.600.301, Veröffentlichung: 11. July 2017*
        - Fehlerkorrekturen
            - Das {{UserId}}-Tag wird in die gespeicherten Anmeldeinformationen aufgelöst und nicht in den Benutzer, der den Bericht in Power BI-Berichten ausführt.
            - Einige Bilder werden in Berichten in Power BI-Berichtsserver nicht dargestellt.
            - Der Name eines Power BI-Berichts kann im Power BI-Berichtsserver nicht geändert werden.
            - Benutzerdefinierte Visuals können in der mobilen Power BI-App nicht geladen werden (Neuinstallation der mobilen App erforderlich, um den lokalen Cache zu löschen)

    - *Build 14.0.600.271, Veröffentlichung: 12. June 2017*
        - Erste Veröffentlichung von Power BI-Berichtsserver

- **Power BI Desktop (optimiert für Power BI-Berichtsserver)**
    - *Version: 2.47.4766.4901 (Juni 2017), Veröffentlichung: 10. Januar 2018*
        - Sicherheitsupdates

## <a name="next-steps"></a>Nächste Schritte

[Benutzerhandbuch](user-handbook-overview.md)  
[Administratorhandbuch](admin-handbook-overview.md)  
[Schnellstart: Installieren von Power BI-Berichtsserver](quickstart-install-report-server.md)  
[Installieren des Berichts-Generators](https://docs.microsoft.com/sql/reporting-services/install-windows/install-report-builder)  
[Herunterladen der SQL Server Data Tools](http://go.microsoft.com/fwlink/?LinkID=616714)

Weitere Fragen? [Stellen Sie Ihre Frage in der Power BI-Community.](https://community.powerbi.com/)