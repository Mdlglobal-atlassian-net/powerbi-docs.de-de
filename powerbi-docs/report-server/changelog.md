---
title: Änderungsprotokoll für Power BI-Berichtsserver
description: Dieses Änderungsprotokoll bezieht sich auf Power BI-Berichtsserver und enthält neue Elemente sowie Fehlerkorrekturen für jeden veröffentlichten Build.
ms.author: jaimeta
author: jtarquino
manager: kfile
ms.reviewer: maggies
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.topic: conceptual
ms.date: 03/31/2018
ms.openlocfilehash: 0aa1d964485297c5e0dae3f4a309cc0dd15b92b2
ms.sourcegitcommit: 90ad0572a92f640684cdc32c9a6478d299de9dc0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/10/2019
ms.locfileid: "68940902"
---
# <a name="changelog-for-power-bi-report-server"></a>Änderungsprotokoll für Power BI-Berichtsserver

Dieses Änderungsprotokoll bezieht sich auf Power BI-Berichtsserver und enthält neue Elemente sowie Fehlerkorrekturen für jeden veröffentlichten Build.

Ausführliche Informationen zu neuen Funktionen finden Sie unter [Neuerungen in Power BI-Berichtsserver](whats-new.md). 

## <a name="may-2019"></a>Mai 2019

- **Power BI-Berichtsserver**          
    - *Version 1.5.7074.36177 (Build 15.0.1102.371), Veröffentlichung: 21. Mai 2019*
        - Fehlerkorrekturen
            - Paginated Reports
                - Korrigiert: Dauerhaftes Aktivieren der Schriftarteinbettung in PDFs
                - Korrigiert: Festlegen von über https gesendeten Cookies als „Sicher“
                - Korrigiert: Probleme mit Popups aufgrund von Skriptfehlern
                - Korrigiert: Anzeigeprobleme bei mobilen Apps auf Android-Geräten
                - Korrigiert: Zeitnavigation des Mobilgeräteberichts zeigt die richtigen Wochennummern unabhängig vom Geschäftsjahr an
                - Hinzufügen der konfigurierbaren Eigenschaft „RestrictedResourceMimeTypeForUpload“, mit der Administratoren gesperrte MIME-Typen angeben können
         - Features
            - Hinzufügen des Supports für vertrauenswürdige Visuals zu PBIRS

- **Power BI Desktop (optimiert für Power BI-Berichtsserver)**
    - *Version: 2.69.5467.1801 (Mai 2019), Veröffentlichung: 21. Mai 2019*
        - Fehlerkorrekturen
            - Korrektur, dass Anmeldeinformationen während des Uploads von PBIX zu PBIRS nicht noch mal eingegeben werden müssen.
            - Korrigiert: Öffnen von Dokumenten mit „#“ im Dateinamen
            - Hinzufügen eines einfachen Links für die Rückwärtsnavigation im PBIRS-Auswahlfenster
            - Korrigiert: Anzeigen der Schaltfläche „Zurück“ im Modus „Hohe Kontraste“ in PBIRS, Anzeigen von Warnmeldungen für Visuals
            - Korrigiert: Benutzeroberfläche des Auswahlbereichs (Canvasskalierung)

    - *Version: 2.69.5467.5201 (Mai 2019), Veröffentlichung: 30. Juli 2019*
        - Fehlerkorrekturen
            - Korrektur für falsche Telemetrieprotokollierung

## <a name="january-2019"></a>Januar 2019

- **Power BI-Berichtsserver**          
    - *Version 1.4.7024.16477 (Build 15.0.1102.299), Veröffentlichung: 28. März 2019*
        - Fehlerkorrekturen
            - Power BI-Berichte
                - Korrigiert: Ein Problem mit Standardanmeldeinformationen bei direkter Abfrage für SAP HANA und SAP BW
                - Korrigiert: Datenaktualisierung für OData-Feed schlägt fehl. Fehler: „Datei oder Assembly 'Microsoft.OData.Core.NetFX35.V7' konnte nicht geladen werden.“

- **Power BI-Berichtsserver**            
    - *Version 1.4.6969.7395 (Build 15.0.1102.235), Veröffentlichung: 30. Januar 2019*
        - Fehlerkorrekturen
            - Power BI-Berichte
                - Korrigiert: Ein Problem mit Standardanmeldeinformationen bei direkter Abfrage
                - Korrigiert: Bidirektionale Beziehungen mit angewendeten Sicherheitsfiltern auf Zeilenebene
                - Korrigiert: Veraltete Daten nach Aktualisierung eines Modells in einer horizontal skalierten Umgebung
                - Korrigiert: Doppelte Bildlaufleiste für Tabelle/Matrix in Firefox Version 63 und höher
                - Korrigiert: Größe der Symbole +/- in Internet Explorer
            - Paginated Reports
                - Korrigiert: Ein Problem bei der Aktualisierung der Verwendung einer freigegebenen Datenquelle für einen Bericht

    - *Version 1.4.6960.38798 (Build 15.0.1102.222), Veröffentlichung: 22. Januar 2019*
        - Features
            - Power BI-Berichte 
                - Unterstützung der Sicherheit auf Zeilenebene
                - Erweitern und Reduzieren in den Zeilenüberschriften einer Matrix
                - Kopieren und Einfügen zwischen PBIX-Dateien
                - Intelligente Hinweise zur Ausrichtung
                - Unterstützung für den SAP BW 2.0-Connector
            - Administratoren
                - Können nun die Erweiterungen der Ressourcen einschränken, die auf den Berichtsserver hochgeladen werden können
                - Können nun die unterstützten Hyperlinkschemas einschränken
            - Programmierbarkeit
                - Neue Web-API: /PowerBIReports({Id})/DataModelRoles (GET)
                - Neue Web-API: /PowerBIReports({Id})/DataModelRoleAssignments (GET und PUT)
                - Weitere Informationen finden Sie im Artikel [Power BI Report Server REST API (REST-API für Power BI-Berichtsserver)](https://app.swaggerhub.com/apis/microsoft-rs/PBIRS/2.0).
        - Fehlerkorrekturen
            - Sicherheitsrisiko durch Einschleusung von HTML-Befehlen
            - Nach dem Exportieren ins PDF-Format wird kein Euro-Symbol angezeigt.
            - Durch das Speichern eines Kennworts mit mehreren Datenquellen in Power BI-Berichten wurden nicht geänderte Kennwörter ungültig
            - Visuals zeigen nach einem Leerlauf Fehler in der Power BI Mobile-App an.

- **Power BI Desktop (optimiert für Power BI-Berichtsserver)**
    - *Version: 2.65.5313.1562 (Januar 2019), Veröffentlichung: 30. Januar 2019*
        - Verknüpfungen und angeheftete Symbole bleiben auch nach der Deinstallation des Power BI-Berichtsservers erhalten
        - Korrigiert: Anheften des Power BI-Berichtsservers an das Startmenü führte zu einem schwarzen Symbol mit schwarzer Schrift

    - *Version: 2.65.5313.1421 (Januar 2019), Veröffentlichung: 22. Januar 2019* (neuer Build und neue Version)
        - Enthält Änderungen, die für die Verbindung mit dem Power BI-Berichtsserver (Januar 2019) erforderlich sind 
    - *Version: 2.65.5313.5141 (Januar 2019), Veröffentlichung: 31. Juli 2019* (neuer Build und neue Version)
        - Fehlerkorrekturen
            - Korrektur für falsche Telemetrieprotokollierung

## <a name="august-2018"></a>August 2018

- **Power BI-Berichtsserver**
    - *Version 1.3.6816.37243 (Build 15.0.2.557), Veröffentlichung: 30. August 2018*
        - Fehlerkorrekturen
            - Korrektur eines Fehlers, durch den der Server beim Upgrade von einer früheren Version des PBI-Berichtsservers eine Bindungsumleitung nicht aktualisiert und den Kunden Folgendes angezeigt wurde:      
            *`
            Failed to load expression host assembly. Details: Could not load file or assembly 'Microsoft.ReportingServices.ProcessingObjectModel, Version=2018.7.0.0, Culture=neutral, PublicKeyToken=89845dcd8080cc91' or one of its dependencies. The located assembly's manifest definition does not match the assembly reference. (Exception from HRESULT: 0x80131040) (rsErrorLoadingExprHostAssembly)
             `*
             
            - Ein Fehler in Bezug auf die Transparenz der Datenbeschriftung wurde korrigiert.
            
    - *Version 1.3.6801.38816 (Build 15.0.2.540), Veröffentlichung: 15. August 2018*
        - Features
            - Die Unterstützung von direkten SAP HANA SSO-Abfragen mit Kerberos ist nun für Power BI-Berichte verfügbar.
            - Im Release enthaltene benutzerdefinierte Visual-API: Version 1.13.0
            - Für benutzerdefinierte Visuals wird ein Fallback auf eine vorherige Version ausgeführt, die mit der aktuellen Version der Server-API (falls verfügbar) kompatibel ist.

- **Power BI Desktop (optimiert für Power BI-Berichtsserver)**
    - *Version: 2.61.5192.641 (August 2018), Veröffentlichung: 15. August 2018*
        - Enthält Änderungen, die für die Verbindung mit dem Power BI-Berichtsserver (August 2018) erforderlich sind         
    - *Version: 2.61.5192.7701 (August 2018), Veröffentlichung: 8. August 2019* (neuer Build und neue Version)
        - Fehlerkorrekturen
            - Korrektur für falsche Telemetrieprotokollierung
            
## <a name="march-2018"></a>März 2018

- **Power BI-Berichtsserver**
    - *Version 1.2.6690.34729 (Build 15.0.2.402), Veröffentlichung: 27. April 2018*
        - Fehlerkorrekturen
            - Aktivieren der Migration von SQL Server Reporting Services 2017-Katalogen
            - Für Power BI-Berichte (PBIX)
                - Berichte können aktualisiert werden, wenn ein Server für die Verwendung der benutzerdefinierten Authentifizierung konfiguriert ist.
                - Durch Ändern der Eigenschaften eines Berichts werden die Anmeldeinformationen der Datenquelle nicht zurückgesetzt.
            - Für paginierte Berichte (RDL)
                - Die Verwendung von `Lookup()` oder Ableitungsfunktionen wie `LookupSet()` und `MultiLookup()` in RDL-Ausdrücken führt nicht mehr zu `#Error`.
                - Verknüpfte Berichte behalten beim Drucken die Seitengröße des Zielberichts bei.
                - Abonnements können für verknüpfte Berichte erstellt werden, die kaskadierende Parameter verwenden.
                - Bei Verwendung von IE11 können die Standardwerte mehrwertiger Parameter geändert werden.
                - Die Übermittlungsoptionen für datengesteuerte Abonnements können bearbeitet werden.
                - Abonnements können angezeigt und bearbeitet werden, während das Abonnement ausgeführt wird.
                - Durch Festlegen von Anmeldeinformationen für Datenquellen werden ausdrucksbasierte Verbindungszeichenfolgen nicht entfernt.
            - Für KPIs
                - Trendlinien werden aktualisiert, wenn Daten aktualisiert werden.
            - Allgemeine Verbesserungen der Stabilität

    - *Version 1.2.6660.39920 (Build 15.0.2.389), Veröffentlichung: 28. März 2018*
        - Fehlerkorrekturen
            - Bei Power BI-Berichten (PBIX) funktioniert die Korrektur für den Datenexport für Power BI-Visuals nicht.
            - Bei Power BI-Berichten (PBIX) funktioniert die Korrektur für URL-Filter nicht.
            - Bei paginierten Berichten (RDL) funktioniert die Korrektur für die ordnungsgemäße Anzeige von Bildern in IE11 nicht, nachdem ein Upgrade auf die Power BI-Berichtsserverversion von März ausgeführt wurde.

    - *Version 1.2.6648.38132 (Build 15.0.2.378), Veröffentlichung: 19. März 2018*
        - Sicherheitsupdates
        - Verbesserungen in Bezug auf die Barrierefreiheit
        - Fehlerkorrekturen
            - Für paginierte Berichte (RDL): Fehlerkorrektur für Parameter, die in einem verknüpften Bericht sichtbar sind, der nach Bearbeitung seiner Eigenschaften wiederhergestellt wurde
            - Fehlerkorrektur für das Webportal mit benutzerdefinierter Formularauthentifizierung, die das Cookie für den variablen Ablauf ignoriert
            - Fehlerkorrektur für den Export in Word, wo eine ungleiche Zeilenhöhe erstellt wird, wenn der Zeileninhalt leer ist.
            - Für paginierte Berichte (RDL): Fehlerkorrektur für auf Ausdrücken basierende Verbindungszeichenfolge, die gelöscht wird, wenn wir die Anmeldeinformationen für die Datenquelle ändern
            - Fehlerkorrektur für die Möglichkeit, KPI mit Textwerten zu verwenden
            - Für paginierte Berichte (RDL): Fehlerkorrektur für die Möglichkeit, einem vorhandenen paginierten Bericht (RDL) ein neues Dataset zuzuweisen.
            - Andere Fehlerkorrekturen für Stabilität und Nutzbarkeit

- **Power BI Desktop (optimiert für Power BI-Berichtsserver)**
    - Version: 2.56.5023.1043 (März 2018), Veröffentlichung: 19. März 2018
        - Enthält Änderungen, die für die Verbindung mit Power BI-Berichtsserver (März 2018) erforderlich sind

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
    - *Version: 2.51.4885.3981 (Oktober 2017), Veröffentlichung: 10. April 2018*
        - Sicherheitsupdates

    - *Version: 2.51.4885.2501 (Oktober 2017), Veröffentlichung: 10. Januar 2018*
        - Sicherheitsupdates

    - *Version: 2.51.4885.1423 (Oktober 2017), Veröffentlichung: 17. November 2017*
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

    - *Build 14.0.600.301, Veröffentlichung: 11. Juli 2017*
        - Fehlerkorrekturen
            - Das `{{UserId}}`-Tag wird in die gespeicherten Anmeldeinformationen aufgelöst und nicht in den Benutzer, der den Bericht in Power BI-Berichte ausführt.
            - Einige Bilder werden in Berichten in Power BI-Berichtsserver nicht dargestellt.
            - Der Name eines Power BI-Berichts kann im Power BI-Berichtsserver nicht geändert werden.
            - Benutzerdefinierte Visuals können in der mobilen Power BI-App nicht geladen werden (Neuinstallation der mobilen App erforderlich, um den lokalen Cache zu löschen)

    - *Build 14.0.600.271, Veröffentlichung: 12. Juni 2017*
        - Erste Veröffentlichung von Power BI-Berichtsserver

- **Power BI Desktop (optimiert für Power BI-Berichtsserver)**
    - *Version: 2.47.4766.4901 (Juni 2017), Veröffentlichung: 10. Januar 2018*
        - Sicherheitsupdates

## <a name="next-steps"></a>Nächste Schritte

[Was ist der Microsoft Power BI-Berichtsserver?](get-started.md)
[Administratorübersicht](admin-handbook-overview.md)  
[Installieren von Power BI-Berichtsserver](install-report-server.md)  
[Herunterladen des Berichts-Generators](https://www.microsoft.com/download/details.aspx?id=53613)  
[Herunterladen der SQL Server Data Tools](http://go.microsoft.com/fwlink/?LinkID=616714)

Weitere Fragen? [Stellen Sie Ihre Frage in der Power BI-Community.](https://community.powerbi.com/)
