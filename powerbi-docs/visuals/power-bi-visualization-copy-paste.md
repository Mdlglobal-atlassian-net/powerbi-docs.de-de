---
title: Kopieren und Einfügen einer Visualisierung in Power BI
description: Kopieren und Einfügen einer Visualisierung in Power BI
author: mihart
ms.reviewer: maggie tsang
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 04/13/2020
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: 03ce7f2a8ccd2c453521d28d172ffb25c1bb28bf
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "81440311"
---
# <a name="copy-and-paste-a-report-visualization"></a>Kopieren und Einfügen einer Berichtsvisualisierung

[!INCLUDE[consumer-appliesto-yyyn](../includes/consumer-appliesto-yyyn.md)]

In diesem Artikel werden zwei verschiedene Möglichkeiten zum Kopieren und Einfügen eines Visuals behandelt. 
* das Kopieren eines Visuals in einen Bericht und das Einfügen auf einer anderen Berichtsseite (erfordert Bearbeitungsberechtigungen für den Bericht)

* das Kopieren eines Visuals im Bildformat aus Power BI in die Zwischenablage und das Einfügen in andere Anwendungen

## <a name="copy-and-paste-within-the-same-report"></a>Kopieren und Einfügen innerhalb desselben Berichts
Visuals in Power BI-Berichten können von einer Seite im Bericht auf dieselbe oder eine andere Seite desselben Berichts kopiert werden. 

Zum Kopieren und Einfügen einer Visualisierung benötigen Sie Bearbeitungsberechtigungen für den Bericht. Öffnen Sie hierzu im Power BI-Dienst den Bericht in der [Bearbeitungsansicht](../consumer/end-user-reading-view.md). 

Visualisierungen auf *Dashboards* können nicht in Power BI-Berichte oder andere Dashboards kopiert und eingefügt werden.

1. Öffnen Sie einen Bericht, der mindestens eine Visualisierung enthält.  

2. Wählen Sie die Visualisierung aus und verwenden Sie **STRG + C** zum Kopieren und **STRG + V** zum Einfügen.      

   ![Kurzes Video, das Kopieren und Einfügen zeigt](media/power-bi-visualization-copy-paste/copypasteviznew.gif)


## <a name="copy-a-visual-as-an-image-to-your-clipboard"></a>Kopieren eines Visuals im Bildformat in die Zwischenablage

Hatten Sie jemals Bedarf, ein Bild eines Power BI-Berichts oder -Dashboards freizugeben? Nun können Sie das Visual kopieren und in eine beliebige andere Anwendung einfügen, die das Einfügen unterstützt. 

Wenn Sie ein statisches Bild eines Visuals kopieren, erhalten Sie eine Kopie des Visuals zusammen mit den Metadaten. Dies umfasst u. a.:
* einen Link zum Power BI-Bericht oder -Dashboard
* den Titel des Berichts oder Dashboards
* ggf. einen Hinweis, dass das Bild vertrauliche Informationen enthält
* einen Zeitstempel für die letzte Aktualisierung
* auf das Visual angewendete Filter

### <a name="copy-from-a-dashboard-tile"></a>Kopieren von einer Dashboardkachel

1. Navigieren Sie zu dem Dashboard, aus dem Sie Inhalte kopieren möchten.

2. Klicken Sie in der oberen rechten Ecke des Visuals auf **Weitere Optionen (...)** und dann auf **Visual als Bild kopieren**. 

    ![Option „Visual als Bild kopieren“ wird angezeigt](media/power-bi-visualization-copy-paste/power-bi-copy-dashboard.png)

3. Wenn das Dialogfeld **Ihr Visual ist zum Kopieren bereit.** angezeigt wird, wählen Sie **In Zwischenablage kopieren** aus.

    ![Dialogfeld mit Option „In Zwischenablage kopieren“](media/power-bi-visualization-copy-paste/power-bi-copied.png)

4. Wenn das Visual bereit ist, fügen Sie es in eine andere Anwendung ein, indem Sie **STRG+V** drücken oder rechtsklicken und „Einfügen“ auswählen. Auf dem folgenden Screenshot haben wir das Visual in Microsoft Word eingefügt. 

    ![In Outlook eingefügtes Visual](media/power-bi-visualization-copy-paste/power-bi-paste-word.png)

### <a name="copy-from-a-report-visual"></a>Kopieren aus einem Berichtsvisual 

1. Navigieren Sie zu dem Bericht, aus dem Sie Inhalte kopieren möchten.

2. Klicken Sie in der oberen rechten Ecke des Visuals auf das Symbol für **Visual als Bild kopieren**. 

    ![Option „Visual als Bild kopieren“ wird angezeigt](media/power-bi-visualization-copy-paste/power-bi-copy-icon.png)

3. Wenn das Dialogfeld **Ihr Visual ist zum Kopieren bereit.** angezeigt wird, wählen Sie **In Zwischenablage kopieren** aus.

    ![Dialogfeld mit Option „In Zwischenablage kopieren“](media/power-bi-visualization-copy-paste/power-bi-copied.png)


4. Wenn das Visual bereit ist, fügen Sie es in eine andere Anwendung ein, indem Sie **STRG+V** drücken oder rechtsklicken und „Einfügen“ auswählen. Auf dem folgenden Screenshot haben wir das Visual in eine E-Mail eingefügt.

    ![In Outlook eingefügtes Visual](media/power-bi-visualization-copy-paste/power-bi-copy-email.png)

5. Wenn eine Datenvertraulichkeitsbezeichnung auf den Bericht angewendet ist, wird eine Warnung angezeigt, wenn Sie auf das Kopiersymbol klicken.  

    ![Warnung zu vertraulichen Daten](media/power-bi-visualization-copy-paste/power-bi-sensitive.png)

    Zudem wird die Vertraulichkeitsbezeichnung den Metadaten unterhalb des eingefügten Visuals hinzugefügt. 

    ![Visual mit Bezeichnung für vertrauliche Informationen](media/power-bi-visualization-copy-paste/power-bi-confidential.png)

### <a name="manage-use-of-copying-a-visual-as-an-image"></a>Konfiguration der Kopieroption für Visuals im Bildformat
Wenn Sie der Inhaltsbesitzer oder ein Administrator des Mandanten sind, können Sie festlegen, ob ein Visual als Bild aus einem Bericht oder Dashboard kopiert werden kann.

#### <a name="disable-copy-as-an-image-for-a-specific-visual"></a>Deaktivieren der Kopieroption für Bilder für bestimmte Visuals
Wenn Sie nicht möchten, dass Benutzer ein bestimmtes Visual kopieren können, können Sie das Kopiersymbol aus diesem visuellen Element entfernen.
1. Wählen Sie das Farbrollersymbol aus, um den Bereich „Formatierung“ zu öffnen. 

1. Öffnen Sie die Karte **Visual formatting** (Visualformatierung).
1. Scrollen Sie nach unten zu **Visualheader**, erweitern Sie die Karte, und deaktivieren Sie **Kopiersymbol**.

    ![Farbroller und Kopiersymbol ausgewählt](media/power-bi-visualization-copy-paste/power-bi-visual-header.png)

1. Wenn Sie den Einstellung **Visualheader** nicht finden können, aktivieren Sie die Option für moderne Visualheader unter **Berichtseinstellungen**. 

    ![Ausgewählte Option für moderne Visualheader](media/power-bi-visualization-copy-paste/power-bi-use-modern.png)

1. Speichern Sie die Änderungen. Wiederholen Sie die Freigabe oder Veröffentlichung nach Bedarf.

#### <a name="disable-copy-as-an-image-for-a-group-of-users"></a>Deaktivieren der Kopieroption für Bilder für bestimmte Benutzergruppen

Wenn Sie der Inhaltsbesitzer oder ein Administrator des Mandanten sind, können Sie festlegen, wer Visuals kopieren darf. Mit dieser Einstellung wird *Visual als Bild kopieren* für alle Inhalte deaktiviert, auf die der Benutzer im Power BI-Mandanten zugreift.
  
1. Navigieren Sie zum Verwaltungsportal.

1. Wählen Sie unter **Mandanteneinstellungen** die Option **Einstellungen für Export und Freigabe** aus. 

    ![Kopieren und Einfügen von Visuals aktivieren](media/power-bi-visualization-copy-paste/power-bi-enable.png)

1. Deaktivieren Sie die Option **Copy and paste visuals** (Visuals kopieren und einfügen) für die gewünschten Benutzergruppen. 

1. Speichern Sie die Änderungen. Die ausgewählten Benutzergruppen können die Option **Visual als Bild kopieren** in Power BI generell nicht mehr nutzen. 
  

## <a name="considerations-and-troubleshooting"></a>Zu beachtende Aspekte und Problembehandlung

   ![Kopiersymbol nicht verfügbar](media/power-bi-visualization-copy-paste/power-bi-copy-grey.png)


F: Warum ist das Kopiersymbol in einem Visual deaktiviert?    
A: Wir unterstützen derzeit native Power BI-Visuals und zertifizierte Visuals. Bestimmte Visuals werden nur eingeschränkt unterstützt, darunter: 
- ESRI-Visuals und andere Kartenvisuals 
- Python-Visuals 
- R-Visuals 
- PowerApps 
- Nicht zertifizierte benutzerdefinierte Visuals Unter [So lassen Sie sich ein Power BI-Visual zertifizieren](../developer/visuals/power-bi-custom-visuals-certified.md) finden Sie weitere Informationen dazu, wie Ihr benutzerdefiniertes Visual unterstützt wird. 


F: Warum wird mein Visual nicht ordnungsgemäß eingefügt?    
A: Es bestehen Einschränkungen für das Kopieren eines Visuals als Bild, z. B.: 
- Für benutzerdefinierte Visuals 
    - Visuals mit angewendeten Designs und Farbschemas 
    - Kachelskalierung beim Einfügen 
    - Benutzerdefinierte Visuals mit Animationen 
- Kopiereinschränkungen 
    - Kürzlich angepinnte Dashboardkacheln können nicht kopiert werden. 
    - Benutzer können nicht zu Inhalten mit OData-Filtern und fixierten Inhalten wie persönlichen Lesezeichen weitergeleitet werden. 
- Anwendungen mit eingeschränkter Unterstützung für das Einfügen von Inhalten mit HTML-Formatierung aus der Zwischenablage können ggf. nicht alle Inhalte rendern, die aus dem Visual kopiert wurden. 



## <a name="next-steps"></a>Nächste Schritte
Weitere Informationen zu [Visualisierungen in Power BI-Berichten](power-bi-report-visualizations.md)

Weitere Fragen? [Wenden Sie sich an die Power BI-Community](https://community.powerbi.com/)

