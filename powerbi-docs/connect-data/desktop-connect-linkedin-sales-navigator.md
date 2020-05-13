---
title: Herstellen einer Verbindung mit LinkedIn Sales Navigator in Power BI Desktop
description: Einfaches Herstellen einer Verbindung mit und Verwenden von Daten aus LinkedIn in Power BI Desktop
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 11/11/2019
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 5d6716c575418f8ef33a82b4c4a1f32647494c47
ms.sourcegitcommit: bfc2baf862aade6873501566f13c744efdd146f3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/13/2020
ms.locfileid: "83348687"
---
# <a name="connect-to-linkedin-sales-navigator-in-power-bi-desktop"></a>Herstellen einer Verbindung mit LinkedIn Sales Navigator in Power BI Desktop

In **Power BI Desktop** können Sie eine Verbindung mit **LinkedIn Sales Navigator** herstellen, um beim Suchen und Erstellen von Beziehungen wie bei jeder anderen Datenquelle in Power BI Desktop zu unterstützen und vorgefertigte Berichte über Ihren Fortschritt zu erstellen.

![Registerkarte „Usage“ (Verwendung) in LinkedIn Sales Navigator](media/desktop-connect-linkedin-sales-navigator/linkedin-sales-navigator-01.png)


Sie müssen über einen LinkedIn Sales Navigator Enterprise-Plan verfügen und im Sales Navigator-Vertrag entweder als Administrator oder Berichterstellungsbenutzer eingetragen sein, um mithilfe von **LinkedIn Sales Navigator** eine Verbindung mit LinkedIn-Daten herzustellen.

Das folgende Video enthält eine kurze Einführung und ein Tutorial zur Verwendung der Vorlagen-App für **LinkedIn Sales Navigator**, die [weiter unten in diesem Artikel](#using-the-linkedin-sales-navigator-template-app) ausführlich beschrieben wird. 

> [!VIDEO https://www.youtube.com/embed/ZqhmaiORLw0]

## <a name="connect-to-linkedin-sales-navigator"></a>Herstellen einer Verbindung mit LinkedIn Sales Navigator

Wählen Sie in Power BI Desktop im Menüband **Start** die Option **Daten abrufen** aus, um eine Verbindung mit den **LinkedIn Sales Navigator**-Daten herzustellen. Wählen Sie aus den Kategorien auf der linken Seite **Onlinedienste** aus, und scrollen Sie dann zu **LinkedIn Sales Navigator (Beta)** .

![Abrufen von Daten in Power BI Desktop](media/desktop-connect-linkedin-sales-navigator/linkedin-sales-navigator-02.png)

Sie werden darüber informiert, dass Sie eine Verbindung mit einem Drittanbieterconnector herstellen, der sich noch in der Entwicklung befindet. 

![Warnung vor Drittanbieterdienst](media/desktop-connect-linkedin-sales-navigator/linkedin-sales-navigator-03.png)

Wenn Sie **Weiter** auswählen, werden Sie dazu aufgefordert anzugeben, welche Daten Sie abrufen möchten.

![Eingabeaufforderung dazu, welche Informationen bereitgestellt werden sollen](media/desktop-connect-linkedin-sales-navigator/linkedin-sales-navigator-04.png)


Wählen Sie im angezeigten **LinkedIn Sales Navigator**-Fenster aus, welche Daten Sie zurückgeben möchten. Sie können hierzu in der ersten Dropdownliste entweder *All contacts* (Alle Kontakte) oder *Selected contacts* (Ausgewählte Kontakte) auswählen. Sie können dann das Start- und Enddatum angeben, um die abgerufenen Daten auf ein bestimmtes Zeitfenster zu beschränken.

Sobald Sie diese Informationen angegeben haben, stellt Power BI Desktop eine Verbindung mit den Daten her, die Ihrem LinkedIn Sales Navigator-Vertrag zugeordnet sind. Verwenden Sie dieselbe E-Mail-Adresse, die Sie für die Anmeldung bei LinkedIn Sales Navigator über die Website verwenden. 

![LinkedIn-Anmeldung](media/desktop-connect-linkedin-sales-navigator/linkedin-sales-navigator-05.png)

Wenn Sie erfolgreich eine Verbindung hergestellt haben, werden Sie über das Fenster **Navigator** zur Auswahl der Daten aus Ihrem LinkedIn Sales Navigator-Vertrag aufgefordert.

![Auswählen von Daten mit dem Navigator](media/desktop-connect-linkedin-sales-navigator/linkedin-sales-navigator-09.png)

Sie können mit Ihren LinkedIn Sales Navigator-Daten jeden beliebigen Bericht erstellen. Sie können zur Vereinfachung auch die PBIX-Datei für LinkedIn Sales Navigator herunterladen, die bereits Beispieldaten enthält. So können Sie sich mit den Daten und Berichten vertraut machen, ohne von Grund auf neu starten zu müssen.

Die PBIX-Datei können Sie unter folgendem Link herunterladen:
* [PBIX für LinkedIn Sales Navigator](service-template-apps-samples.md)

Zusätzlich zur PBIX-Datei verfügt LinkedIn Sales Navigator auch über eine Vorlagen-App, die Sie ebenfalls herunterladen und verwenden können. Im nächsten Abschnitt wird die Vorlagen-App ausführlich beschrieben.


## <a name="using-the-linkedin-sales-navigator-template-app"></a>Verwenden der Vorlagen-App für LinkedIn Sales Navigator

Sie können die **Vorlagen-App** verwenden, um die Verwendung von [LinkedIn Sales Navigator](service-template-apps-overview.md) so einfach wie möglich zu gestalten. Diese erstellt aus Ihren LinkedIn Sales Navigator-Daten automatisch einen vorgefertigten Bericht.

![Vorlagen-App für LinkedIn Sales Navigator](media/desktop-connect-linkedin-sales-navigator/linkedin-sales-navigator-10.png)

Wenn Sie die App herunterladen, können Sie auswählen, ob Sie eine Verbindung mit Ihren Daten herstellen oder die App mit Beispieldaten ausprobieren möchten. Sie können jederzeit zurückkehren und eine Verbindung mit ihren eigenen LinkedIn Sales Navigator-Daten herstellen, nachdem Sie die Beispieldaten verwendet haben. 

![Herstellen einer Verbindung mit LinkedIn Sales Navigator-Daten](media/desktop-connect-linkedin-sales-navigator/linkedin-sales-navigator-11.png)



Sie können die Vorlagen-App für **LinkedIn Sales Navigator** über folgenden Link herunterladen:
* [Vorlagen-App für LinkedIn Sales Navigator](https://appsource.microsoft.com/en-us/product/power-bi/pbi-contentpacks.linkedin_navigator)

Die Vorlagen-App bietet vier Registerkarten zur Unterstützung beim Analysieren und Teilen Ihrer Informationen:

* Verwendung
* Search
* InMail
* SSI

Auf der Registerkarte **Usage** (Verwendung) werden Ihre gesamten LinkedIn Sales Navigator-Daten angezeigt.

![Registerkarte „Usage“ (Verwendung) in LinkedIn Sales Navigator](media/desktop-connect-linkedin-sales-navigator/linkedin-sales-navigator-12.png)

Über die Registerkarte **Search** (Suche) können Sie die Suchergebnisse genauer betrachten:

![Registerkarte „Search“ (Suche) in LinkedIn Sales Navigator](media/desktop-connect-linkedin-sales-navigator/linkedin-sales-navigator-13.png)

Unter **InMail** erhalten Sie Einblicke in Ihre InMail-Verwendung, darunter die Anzahl gesendeter InMails, Annahmequoten sowie weitere hilfreiche Informationen:

![Registerkarte „InMail“ in LinkedIn Sales Navigator](media/desktop-connect-linkedin-sales-navigator/linkedin-sales-navigator-14.png)

Die Registerkarte **SSI** bietet zusätzliche Informationen zu Ihrem Social Selling Index (SSI):

![Registerkarte „SSI“ in LinkedIn Sales Navigator](media/desktop-connect-linkedin-sales-navigator/linkedin-sales-navigator-15.png)

Klicken Sie in der oberen rechten Ecke auf **App bearbeiten** (das Stiftsymbol) und anschließend im angezeigten Bildschirm auf **Ihre Daten verbinden**, um von den Beispieldaten zu Ihren eigenen Daten zu wechseln.

![Herstellen einer Verbindung mit ihren eigenen Daten](media/desktop-connect-linkedin-sales-navigator/linkedin-sales-navigator-16.png)

Von dort aus können Sie eine Verbindung mit Ihren eigenen Daten herstellen, indem Sie auswählen, wie viele Tage Daten Sie laden möchten. Sie können bis zu 365 Tage Daten laden. Sie müssen sich anmelden, indem Sie wieder dieselbe E-Mail-Adresse verwenden, die Sie für die Anmeldung bei LinkedIn Sales Navigator über die Website verwenden. 

![Anmelden](media/desktop-connect-linkedin-sales-navigator/linkedin-sales-navigator-17.png)

Die Vorlagen-App aktualisiert dann die Daten in der App mit Ihren Daten. Sie können auch eine geplante Aktualisierung einrichten, damit die Daten in Ihrer App so aktuell sind wie Sie es durch die Aktualisierungshäufigkeit angeben. 

Nachdem die Daten aktualisiert wurden, werden Ihnen in der App Ihre Daten angezeigt.

## <a name="getting-help"></a>Hilfe

Wenn beim Herstellen einer Verbindung mit Ihren Daten Probleme auftreten, können Sie sich unter https://www.linkedin.com/help/sales-navigator an den LinkedIn Sales Navigator-Support wenden. 

## <a name="next-steps"></a>Weitere Schritte
Sie können mithilfe von Power BI Desktop eine Verbindung mit Daten jeglicher Art herstellen. Weitere Informationen zu Datenquellen finden Sie in folgenden Ressourcen:

* [Was ist Power BI Desktop?](../fundamentals/desktop-what-is-desktop.md)
* [Datenquellen in Power BI-Desktop](desktop-data-sources.md)
* [Strukturieren und Kombinieren von Daten mit Power BI Desktop](desktop-shape-and-combine-data.md)
* [Verbinden mit Excel in Power BI Desktop](desktop-connect-excel.md)   
* [Eingeben von Daten direkt in Power BI Desktop](desktop-enter-data-directly-into-desktop.md)   
