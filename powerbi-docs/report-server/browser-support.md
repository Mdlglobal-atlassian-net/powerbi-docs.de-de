---
title: Browserunterstützung für Power BI-Berichtsserver
description: Erfahren Sie mehr über die Browserversionen, die zum Verwalten und Anzeigen von Power BI-Berichtsserver und Berichts-Viewer-Steuerelementen unterstützt werden.
author: maggiesMSFT
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.topic: conceptual
ms.date: 10/24/2018
ms.author: maggies
ms.openlocfilehash: 5a2ca653a06efbde161899602536b05c8f6ab666
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "64769778"
---
# <a name="browser-support-for-power-bi-report-server"></a>Browserunterstützung für Power BI-Berichtsserver
Erfahren Sie mehr über die Browserversionen, die zum Verwalten und Anzeigen von Power BI-Berichtsserver und Berichts-Viewer-Steuerelementen unterstützt werden.

## <a name="browser-requirements-for-the-web-portal"></a>Browseranforderungen für das Webportal
Es folgt die aktuelle Liste der vom Webportal unterstützten Browser.

**Microsoft Windows**  
*Windows 7, 8.1, 10; Windows Server 2008 R2, 2012, 2012 R2*

* Microsoft Edge (+)
* Microsoft Internet Explorer 11
* Google Chrome (+)
* Mozilla Firefox (+)

**Apple OS X**  
*OS X 10.9-10.11*

* Apple Safari (+)
* Google Chrome (+)
* Mozilla Firefox (+)

**Apple iOS**  
*iPhone und iPad mit iOS 10*

* Apple Safari (+)

**Google Android**  
*Smartphones und Tablets mit Android 4.4 (KitKat) oder höher*

* Google Chrome (+)
  
  **(+)**  Neueste veröffentliche Version

## <a name="browser-requirements-for-the-report-viewer-web-control-2015"></a>Browseranforderungen für das Berichts-Viewer-Steuerelement (2015)
Es folgt die aktuelle Liste der vom Berichts-Viewer-Steuerelement unterstützten Browser. Der Berichts-Viewer unterstützt die Anzeige von Berichten über das Webportal.

**Microsoft Windows**  
*Windows 7, 8.1, 10; Windows Server 2008 R2, 2012, 2012 R2*

* Microsoft Edge (+)
* Microsoft Internet Explorer 11
* Google Chrome (+)
* Mozilla Firefox (+)

**Apple OS X**  
*OS X 10.9-10.11*

* Apple Safari (+)
  
  **(+)**  Neueste veröffentliche Version

### <a name="authentication-requirements"></a>Authentifizierungsanforderungen
Browser unterstützen spezifische Authentifizierungsschemas, die vom Berichtsserver verarbeitet werden müssen, damit die Clientanforderung erfolgreich ist. In der folgenden Tabelle sind die Standardauthentifizierungstypen aufgeführt, die von den einzelnen Browsern unter einem Windows-Betriebssystem unterstützt werden.

| **Browsertyp** | **Unterstützt** | **Browserstandard** | **Serverstandard** |
| --- | --- | --- | --- |
| **Microsoft Edge** (+) |Aushandeln, Kerberos, NTLM, Standard |Aushandeln |Ja. Die Standardauthentifizierungseinstellungen funktionieren mit Edge. |
| **Microsoft Internet Explorer** |Aushandeln, Kerberos, NTLM, Standard |Aushandeln |Ja. Die Standardauthentifizierungseinstellungen funktionieren mit Internet Explorer. |
| **Google Chrome**(+) |Aushandeln, NTLM, Standard |Aushandeln |Ja. Die Standardauthentifizierungseinstellungen funktionieren mit Chrome. |
| **Mozilla Firefox**(+) |NTLM, Standard |NTLM |Ja. Die Standardauthentifizierungseinstellungen funktionieren mit Firefox. |
| **Apple Safari**(+) |NTLM, Standard |Standard |Ja. Die Standardauthentifizierungseinstellungen funktionieren mit Safari. |

 **(+)**  Neueste veröffentliche Version

### <a name="script-requirements-for-viewing-reports"></a>Skriptanforderungen zum Anzeigen von Berichten
Um den Berichts-Viewer verwenden zu können, konfigurieren Sie Ihren Browser für das Ausführen von Skripts.

Wenn die Skripterstellung nicht aktiviert ist, wird bei Öffnen eines Berichts eine Fehlermeldung ähnlich der folgenden angezeigt:

```
Your browser does not support scripts or has been configured to not allow scripts to run. Click here to view this report without scripts
```

 Wenn Sie den Bericht ohne Skriptunterstützung anzeigen möchten, wird der Bericht als HTML ohne Berichts-Viewer-Funktionen wie Berichtssymbolleiste und Dokumentstruktur gerendert.

> [!NOTE]
> Die Berichtssymbolleiste ist Teil der HTML-Viewer-Komponente. Standardmäßig wird die Symbolleiste am oberen Rand jedes Berichts angezeigt, der in einem Browserfenster gerendert wird. Der Berichts-Viewer stellt Funktionen bereit, so beispielsweise die Möglichkeit, den Bericht nach Informationen zu durchsuchen, zu einer bestimmten Seite zu scrollen und die Seitengröße für Anzeigezwecke anzupassen. Weitere Informationen zur Berichtssymbolleiste oder zum HTML-Viewer finden Sie unter [HTML-Viewer und die Berichtssymbolleiste](https://docs.microsoft.com/sql/reporting-services/html-viewer-and-the-report-toolbar).
> 
> 

## <a name="browser-support-for-report-viewer-web-server-controls-in-visual-studio"></a>Browserunterstützung für Webserver-Steuerelemente des Berichts-Viewers in Visual Studio
Das Webserver-Steuerelement des Berichts-Viewers wird verwendet, um Berichtsfunktionen in eine ASP.NET-Webanwendung einzubetten. Weitere Informationen zum Abrufen des Berichts-Viewer-Steuerelements finden Sie unter [Integrieren von Reporting Services mithilfe von Berichts-Viewer-Steuerelementen: Erste Schritte](https://docs.microsoft.com/sql/reporting-services/application-integration/integrating-reporting-services-using-reportviewer-controls-get-started).

Verwenden Sie einen Browser mit aktivierter Skriptunterstützung. Wenn der Browser keine Skripts ausführen kann, können Sie den Bericht nicht anzeigen.

**Microsoft Windows**  
*Windows 7, 8.1, 10; Windows Server 2008 R2, 2012, 2012 R2*

* Microsoft Edge (+)
* Microsoft Internet Explorer 11
* Google Chrome (+)
* Mozilla Firefox (+)
  
  **(+)**  Neueste veröffentliche Version

## <a name="next-steps"></a>Nächste Schritte
[Administratorübersicht](admin-handbook-overview.md)  
[Installieren von Power BI-Berichtsserver](install-report-server.md)  
[Herunterladen des Berichts-Generators](https://www.microsoft.com/download/details.aspx?id=53613)  
[Herunterladen der SQL Server Data Tools](http://go.microsoft.com/fwlink/?LinkID=616714)

Weitere Fragen? [Stellen Sie Ihre Frage in der Power BI-Community.](https://community.powerbi.com/)

