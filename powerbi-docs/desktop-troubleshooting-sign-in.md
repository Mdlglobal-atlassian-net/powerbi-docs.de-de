---
title: Problembehandlung zu Problemen mit der Anmeldung bei Power BI Desktop
description: Lösungen für häufige Probleme mit der Anmeldung bei Power BI Desktop
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: troubleshooting
ms.date: 03/05/2020
ms.author: davidi
LocalizationGroup: Troubleshooting
ms.openlocfilehash: 299329cad78d831a3b77e55107e94a234d6f64b1
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "79133192"
---
# <a name="troubleshooting-sign-in-for-power-bi-desktop"></a>Problembehandlung zur Anmeldung bei Power BI Desktop
Möglicherweise treten manchmal Fehler auf, wenn Sie versuchen, sich bei **Power BI Desktop** anzumelden. Es gibt zwei Hauptgründe für Anmeldeprobleme: **Proxyauthentifizierungsfehler** und **Nicht-HTTPS-URL-Umleitungsfehler**. 

Der erste Schritt, um die Ursache Ihres Anmeldeproblems zu bestimmen, ist, dass Sie sich an Ihren Administrator wenden und ihm Diagnoseinformationen vorlegen, damit er die Ursache des Problems bestimmen kann. Indem der Administrator die in Verbindung mit Ihrem Anmeldeproblem im Einzelnen auftretenden Schwierigkeiten verfolgt, kann er bestimmen, welche der folgenden Fehler bei Ihnen vorliegen. 

Betrachten wir nun der Reihe nach diese einzelnen Schwierigkeiten. Am Ende dieses Artikels finden Sie eine Erörterung zum Aufzeichnen einer *Ablaufverfolgung* in Power BI Desktop, die die Problembehandlung erleichtern kann.


## <a name="proxy-authentication-required-error"></a>Fehler: Proxyauthentifizierung erforderlich

Der folgende Bildschirm zeigt ein Beispiel für den Fehler *Proxyauthentifizierung erforderlich*.

![Anmeldefehler durch Proxyauthentifizierungsfehler](media/desktop-troubleshooting-sign-in/desktop-tshoot-sign-in_01.png)

Die folgenden Ausnahmen in *Power BI Desktop*-Ablaufverfolgungsdateien sind mit diesem Fehler verknüpft:

* *Microsoft.PowerBI.Client.Windows.Services.PowerBIWebException*
* *HttpStatusCode: ProxyAuthenticationRequired*

Die wahrscheinlichste Ursache für diesen Fehler ist, dass ein Proxyauthentifizierungsserver in Ihrem Netzwerk die Webanforderungen von **Power BI Desktop** blockiert. 

Wenn in Ihrem Netzwerk ein Proxyauthentifizierungsserver verwendet wird, kann Ihr Administrator dieses Problem durch das Whitelisting der folgenden Domänen auf dem Proxyauthentifizierungsserver beheben:

* app.powerbi.com
* api.powerbi.com
* Domänen im Namespace *.analysis.windows.net

Für Kunden, die Teil einer Behördencloud sind, kann dieses Problem durch das Whitelisting der folgenden Domänen auf dem Proxyauthentifizierungsserver behandelt werden:

* app.powerbigov.us
* api.powerbigov.us
* Domänen im Namespace *.analysis.usgovcloudapi.net

## <a name="non-https-url-redirect-not-supported-error"></a>Fehler: Nicht-HTTPS-URL-Umleitung wird nicht unterstützt

Aktuelle Versionen von **Power BI Desktop** verwenden die aktuelle Version der Active Directory Authentication Library (ADAL), die keine Umleitung an nicht gesicherte URLs (nicht-HTTPS) zulässt. 

Die folgenden Ausnahmen in *Power BI Desktop*-Ablaufverfolgungsdateien sind mit diesem Fehler verknüpft:

* *Microsoft.IdentityModel.Clients.ActiveDirectory.AdalServiceException: Nicht-HTTPS-URL-Umleitung wird in Webansicht nicht unterstützt*
* *ErrorCode: non_https_redirect_failed*

Wenn *ErrorCode: non_https_redirect_failed* auftritt, bedeutet dies, dass mindestens eine Umleitungsseite oder ein Anbieter in der Umleitungskette kein HTTPS-geschützter Endpunkt ist, oder dass ein Zertifikatsaussteller einer oder mehrerer Umleitungen nicht zu den vertrauenswürdigen Stammzertifizierungsstellen des Geräts zählt. Alle Anbieter in einer Anmeldeumleitungskette müssen eine HTTPS-URL verwenden. Um dieses Problem zu behandeln, wenden Sie sich an Ihren Administrator, und fordern Sie an, dass gesicherte URLs für ihre Authentifizierungswebsites verwendet werden. 

## <a name="how-to-collect-a-trace-in-power-bi-desktop"></a>Gewusst wie: Sammeln einer Ablaufverfolgung in Power BI Desktop

Um eine Ablaufverfolgung in **Power BI Desktop** zu sammeln, gehen Sie folgendermaßen vor:

1. Aktivieren Sie die Ablaufverfolgung in **Power BI Desktop**, indem Sie zu **Datei > Optionen und Einstellungen > Optionen** wechseln und dann **Diagnose** aus den Optionen im linken Bereich auswählen. Aktivieren Sie im dann angezeigten Bereich das Kontrollkästchen neben **Ablaufverfolgung aktivieren**, wie in der folgenden Abbildung dargestellt. Möglicherweise müssen Sie **Power BI Desktop** neu starten.
   
   ![Aktivieren der Ablaufverfolgung in Power BI Desktop](media/desktop-troubleshooting-sign-in/desktop-tshoot-sign-in_02.png)

2. Führen Sie dann die Schritte aus, die den Fehler reproduzieren. Wenn der Fehler auftritt, fügt **Power BI Desktop** dem Ablaufverfolgungsprotokoll, das auf dem lokalen Computer verwaltet wird, Ereignisse hinzu.

3. Navigieren Sie zu dem Ordner „Traces“ auf dem lokalen Computer. Um diesen Ordner zu finden, wählen Sie den Link in **Diagnose** aus, wo Sie die Ablaufverfolgung aktiviert haben – *Ordner mit Absturzabbild/Überwachungen öffnen* in der vorherigen Abbildung. Häufig befindet er sich auf dem lokalen Computer an folgendem Speicherort:

    `C:\Users/<user name>/AppData/Local/Microsoft/Power BI Desktop/Traces`

Dieser Ordner enthält möglicherweise viele Ablaufverfolgungsdateien. Stellen Sie sicher, dass Sie nur die zuletzt verwendeten Dateien an Ihren Administrator senden, um die schnelle Identifikation des Fehlers zu erleichtern. 


## <a name="using-default-system-credentials-for-web-proxy"></a>Verwenden standardmäßiger Systemanmeldeinformationen für Webproxys

Von Power BI Desktop ausgegebene Webanforderungen verwenden keine Webproxyanmeldeinformationen. In Netzwerken, die einen Proxyserver verwenden, ist Power BI Desktop möglicherweise nicht in der Lage, erfolgreich Webanforderungen zu erstellen. 

Ab dem Power BI Desktop-Release für März 2020 können System- oder Netzwerkadministratoren die Verwendung von standardmäßigen Systemanmeldeinformationen für die Webproxyauthentifizierung zulassen. Administratoren können einen Registrierungseintrag namens **UseDefaultCredentialsForProxy** erstellen und den Wert auf „1“ (Eins) festlegen, um die Verwendung von standardmäßigen Systemanmeldeinformationen für die Webproxyauthentifizierung zu aktivieren.

Der Registrierungseintrag kann an einem der folgenden Speicherorte abgelegt werden:

`[HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node\Microsoft\Microsoft Power BI Desktop]`
`[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft Power BI Desktop]`

Es ist nicht erforderlich, dass sich der Registrierungseintrag an beiden Speicherorten befindet.

![Registrierungsschlüssel für die Verwendung von standardmäßigen Systemanmeldeinformationen](media/desktop-troubleshooting-sign-in/desktop-tshoot-sign-in-03.png)

Nachdem der Registrierungseintrag erstellt wurde (möglicherweise ist ein Neustart erforderlich), werden die in Internet Explorer definierten Proxyeinstellungen verwendet, wenn Power BI Desktop Webanforderungen stellt. 

Wie bei jeder Änderung an den Proxy- oder Anmeldeinformationseinstellungen bestehen auch beim Erstellen dieses Registrierungseintrags Sicherheitsrisiken, sodass Administratoren sicherstellen müssen, dass sie die Internet Explorer-Proxys ordnungsgemäß konfiguriert haben, bevor sie diese Funktion aktivieren.         

### <a name="limitations-and-considerations-for-using-default-system-credentials"></a>Einschränkungen und Überlegungen zur Verwendung von standardmäßigen Systemanmeldeinformationen

Es gibt eine Sammlung von Sicherheitsrisiken, die Administratoren vor dem Aktivieren dieser Funktion berücksichtigen sollten. 

Die folgenden Empfehlungen sollten beachtet werden, wenn diese Funktion für Clients aktiviert werden soll:

* Verwenden Sie nur **Negotiation** (Aushandlung) als Authentifizierungsschema für den Proxyserver, um sicherzustellen, dass der Client nur Proxyserver verwendet, die mit dem Active Directory-Netzwerk verknüpft sind. 
* Verwenden Sie nicht das **NTLM-Fallback** für Clients, die dieses Feature nutzen.
* Wenn sich Benutzer nicht in einem Netzwerk mit einem Proxy befinden und dieses aber Feature wie in diesem Abschnitt empfohlen aktiviert und konfiguriert ist, wird nicht versucht, den Proxyserver zu kontaktieren und die standardmäßigen Systemanmeldeinformationen zu verwenden.


[Verwenden standardmäßiger Systemanmeldeinformationen für Webproxys](#using-default-system-credentials-for-web-proxy)

