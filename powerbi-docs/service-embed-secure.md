---
title: Einbetten eines Berichts in ein sicheres Portal oder eine sichere Website
description: Mit dem Power BI-Feature zum Einbetten können Benutzer Berichte mühelos in interne Webportale sicher einbetten.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: lukaszp
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 01/30/2020
LocalizationGroup: Share your work
ms.openlocfilehash: 019a3af81cd3661307fd9de6d0577ac58a11ae6a
ms.sourcegitcommit: ced8c9d6c365cab6f63fbe8367fb33e6d827cb97
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/07/2020
ms.locfileid: "78919795"
---
# <a name="embed-a-report-in-a-secure-portal-or-website"></a>Einbetten eines Berichts in ein sicheres Portal oder eine sichere Website

Mit der neuen Option **Einbetten** für Power BI-Berichte können Sie Berichte ohne großen Aufwand und sicher in interne Webportale einbetten. Diese Portale können **cloudbasiert** sein oder **lokal gehostet** werden (z. B. SharePoint 2019). Bei eingebetteten Berichten werden alle Elementberechtigungen und Anforderungen an die Datensicherheit über [Sicherheit auf Zeilenebene](service-admin-rls.md) berücksichtigt. Diese Option ermöglicht das Einbetten in beliebige Portale, die URL oder iFrame akzeptieren, ohne Programmieraufwand. 

Die Option **Einbetten** unterstützt [URL-Filter](service-url-filters.md) und URL-Einstellungen. Sie ermöglicht eine Integration in Portale mit geringem Programmieraufwand, für die nur grundlegende HTML- und JavaScript-Kenntnisse benötigt werden.

## <a name="how-to-embed-power-bi-reports-into-portals"></a>**Einbetten** von Power BI-Berichten in Portale

1. Sie finden die neue Option **Einbetten** im Power BI-Dienst im Menü **Datei** für Berichte.

    ![Dropdownoption für das sichere Einbetten](media/service-embed-secure/secure-embed-drop-down-menu.png)

2. Klicken Sie auf die Option **Einbetten**, um ein Dialogfeld mit einem Link und einem iFrame zu öffnen, die Sie zum sicheren Einbetten des Berichts verwenden können.

    ![Dialogfeld für die Option „Einbetten“](media/service-embed-secure/secure-embed-code-dialog.png)

3. Unabhängig davon, ob ein Benutzer eine Berichts-URL direkt öffnet oder einen eingebetteten Bericht in einem Webportal öffnet, ist eine Authentifizierung für den Zugriff auf den Bericht erforderlich. Die folgende Anzeige wird angezeigt, wenn ein Benutzer sich in seiner Browsersitzung nicht bei Power BI angemeldet hat. Wenn dieser Benutzer auf **Anmelden** klickt, kann ein neues Browserfenster oder eine Registerkarte geöffnet werden. Weisen Sie die Benutzer an, Popupblocker zu überprüfen, wenn ihnen keine Anmeldeaufforderung angezeigt wird.

    ![Anmelden, um den Bericht anzuzeigen](media/service-embed-secure/secure-embed-sign-in.png)

4. Nachdem sich der Benutzer angemeldet hat, wird der Bericht mit den Daten geöffnet. Anschließend kann er zwischen den Seiten navigieren und Filter festlegen. Nur Benutzer mit Leseberechtigung können den Bericht in Power BI anzeigen. Alle Regeln der [Sicherheit auf Zeilenebene](service-admin-rls.md) werden ebenfalls angewendet. Schließlich muss der Benutzer ordnungsgemäß lizenziert sein, d.h., er benötigt eine Power BI Pro-Lizenz oder der Bericht muss sich in einem Arbeitsbereich in einer Power BI Premium-Kapazität befinden. Jedes Mal, wenn der Benutzer ein neues Browserfenster öffnet, muss er sich neu anmelden. Sobald er jedoch ein mal angemeldet ist, werden andere Berichte automatisch geladen.

    ![Einbetten des Berichts](media/service-embed-secure/secure-embed-report.png)

5. Wenn ein iFrame verwendet wird, müssen Sie möglicherweise die **Höhe** und **Breite** anpassen, damit es auf die Webseite Ihres Portals passt.

    ![Festlegen von Höhe und Breite](media/service-embed-secure/secure-embed-size.png)

## <a name="granting-report-access"></a>Gewähren des Zugriffs auf einen Bericht

Wenn Sie die Option **Einbetten** verwenden, erhalten Benutzer nicht automatisch die Berechtigung zum Anzeigen des Berichts. Die Leseberechtigungen werden im Power BI-Dienst festgelegt.

Im Power BI-Dienst können Sie eingebettete Berichte für Benutzer freigeben, die Zugriff benötigen. Wenn Sie eine Office 365-Gruppe verwenden, können Sie Benutzer als Mitglieder des Arbeitsbereichs aufführen. Weitere Informationen dazu finden Sie unter [Verwalten Ihres Arbeitsbereichs in Power BI und Office 365](service-manage-app-workspace-in-power-bi-and-office-365.md).

## <a name="licensing"></a>Lizenzierung

Benutzer, die den eingebetteten Bericht anzeigen möchten, benötigen entweder eine Power BI Pro-Lizenz, oder der Inhalt muss sich in einem Arbeitsbereich in einer [Power BI Premium-Kapazität (EM oder P SKU)](service-admin-premium-purchase.md) befinden.

## <a name="customize-your-embed-experience-using-url-settings"></a>Anpassen der Darstellung des eingebetteten Berichts über URL-Einstellungen

Sie können die Benutzeroberfläche mithilfe der Eingabeeinstellungen der Einbettungs-URL anpassen. Im bereitgestellten iFrame können Sie die **src**-Einstellungen der URL aktualisieren.

| Eigenschaft  | Beschreibung  |  |  |  |
|--------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---|---|---|
| pageName  | Sie können den Abfragezeichenfolgenparameter **pageName** verwenden, um festzulegen, welche Berichtsseite geöffnet werden soll. Diesen Wert finden Sie am Ende der Berichts-URL, wenn Sie einen Bericht wie im Folgenden gezeigt im Power BI-Dienst anzeigen. |  |  |  |
| URL-Filter  | Sie können [URL-Filter](service-url-filters.md) in der Einbettungs-URL verwenden, die Sie aus der Benutzeroberfläche von Power BI abgerufen haben, um die eingebetteten Inhalte zu filtern. Auf diese Weise lassen sich Integrationen mit geringem Programmieraufwand erstellen, für die nur grundlegende Kenntnisse in HTML und JavaScript erforderlich sind.  |  |  |  |

## <a name="set-which-page-opens-for-an-embedded-report"></a>Festlegen der geöffneten Seite für einen eingebetteten Bericht 

Den Wert **pageName** finden Sie am Ende der Berichts-URL, wenn Sie einen Bericht im Power BI-Dienst anzeigen.

1. Öffnen Sie den Bericht über den Power BI-Dienst in Ihrem Webbrowser, und kopieren Sie dann die URL aus der Adressleiste.

    ![Berichtsabschnitt](media/service-embed-secure/secure-embed-report-section.png)

2. Hängen Sie die Einstellung **pageName** an die URL an.

    ![Anhängen von pageName](media/service-embed-secure/secure-embed-append-page-name.png)

## <a name="filter-report-content-using-url-filters"></a>Filtern der Berichtsinhalte mit URL-Filtern 

Sie können [URL-Filter](service-url-filters.md) verwenden, um verschiedene Berichtsansichten bereitzustellen. Beispielsweise wird der Bericht mit der unten aufgeführten URL so gefiltert, dass Daten für die Energiebranche angezeigt werden.

Die Kombination von **pageName** und [URL-Filter](service-url-filters.md) erlaubt besonders ausgefeilte Funktionen. Mit einfachem HTML und JavaScript lassen sich verschiedene Benutzeroberflächen gestalten.

Beispielsweise sehen Sie hier eine Schaltfläche, die Sie zu einer HTML-Seite hinzufügen können:

```html
<button class="textLarge" onclick='show("ReportSection", "Energy");' style="display: inline-block;">Show Energy</button>
```

Wenn auf diese Schaltfläche geklickt wird, wird eine Funktion aufgerufen, durch die das iFrame mit einer aktualisierten URL versehen wird, die den Filter für Energiebranchen enthält.

```javascript
function show(pageName, filterValue)

{

var newUrl = baseUrl + "&pageName=" + pageName;

if(null != filterValue && "" != filterValue)

{

newUrl += "&$filter=Industries/Industry eq '" + filterValue + "'";

}

//Assumes there’s an iFrame on the page with id=”iFrame”

var report = document.getElementById("iFrame")

report.src = newUrl;

}
```

![Filtern](media/service-embed-secure/secure-embed-filter.png)

Sie können beliebig viele Schaltflächen hinzufügen, um mit geringem Programmieraufwand eine individuelle Benutzeroberfläche zu erstellen. 

## <a name="considerations-and-limitations"></a>Überlegungen und Einschränkungen

* Paginierte Berichte werden mit sicheren Einbettungsszenarios unterstützt, und paginierte Berichte mit URL-Parametern werden ebenfalls unterstützt. Weitere Informationen finden Sie unter [Übergeben eines Berichtsparameters in einer URL für einen paginierten Bericht in Power BI](paginated-reports/report-builder-url-pass-parameters.md).

* Externe Gastbenutzer mit Azure B2B (Business-to-Business) werden nicht unterstützt.

* Das sichere Einbetten kann für Berichte verwendet werden, die im Power BI-Dienst veröffentlicht wurden.

* Der Benutzer muss sich anmelden, um den Bericht anzuzeigen, wenn er ein neues Browserfenster öffnet.

* Bei einigen Browsern müssen Sie die Seite nach der Anmeldung aktualisieren, insbesondere bei Verwendung des InPrivate- oder Inkognitomodus.

* Die Verwendung nicht unterstützter Browserversionen führt möglicherweise zu Problemen. Power BI unterstützt [diese Browser](power-bi-browsers.md).

* Der klassische SharePoint-Server wird nicht unterstützt, da dieser eine niedrigere Version als Internet Explorer 11 oder das Aktivieren des Kompatibilitätsansichtsmodus erfordert.

* Einmaliges Anmelden wird unterstützt, wenn Sie die [Option In SharePoint Online einbetten](service-embed-report-spo.md) verwenden oder über die Einbettungsmethode [Benutzer ist Besitzer der Daten](developer/embed-sample-for-your-organization.md) eine benutzerdefinierte Integration erstellen. 

* Die Funktion zur automatischen Authentifizierung, die von der Option **Einbetten** unterstützt wird, kann nicht mit der Power BI-JavaScript-API verwendet werden. Verwenden Sie zum Einbetten mit der Power BI-JavaScript-API die Einbettungsmethode [Benutzer ist Besitzer der Daten](developer/embed-sample-for-your-organization.md). 

* Die Lebensdauer des Authentifizierungstokens wird basierend auf Ihren AAD-Einstellungen gesteuert. Wenn das Authentifizierungstoken abläuft, muss der Benutzer seinen Browser aktualisieren, um ein aktualisiertes Authentifizierungstoken zu erhalten. Die Standardlebensdauer beträgt eine Stunde. Sie kann in Ihrer Organisation aber auch kürzer oder länger sein.

## <a name="next-steps"></a>Nächste Schritte

* [Freigeben Ihrer Arbeit in Power BI](service-how-to-collaborate-distribute-dashboards-reports.md)

* [Filtern eines Berichts mithilfe von Abfragezeichenfolgenparametern in der URL](service-url-filters.md)

* [Einbetten mit dem Berichts-Webpart in SharePoint Online](service-embed-report-spo.md)

* [Veröffentlichen im Web aus Power BI](service-publish-to-web.md)
