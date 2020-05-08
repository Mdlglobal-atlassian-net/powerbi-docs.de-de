---
title: 'Schnellstart: Herstellen einer Verbindung mit Daten in Power BI Desktop'
description: Herstellen einer Verbindung mit den in Power BI Desktop verfügbaren Datenquellen
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: quickstart
ms.date: 01/10/2020
ms.author: davidi
LocalizationGroup: quickstart
ms.openlocfilehash: 5aed52ec232d3e603d69bfe93640187401279ff6
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "75885241"
---
# <a name="quickstart-connect-to-data-in-power-bi-desktop"></a>Schnellstart: Herstellen einer Verbindung mit Daten in Power BI Desktop

In dieser Schnellstartanleitung stellen Sie über Power BI Desktop eine Verbindung mit Daten her. Darin besteht der erste Schritt beim Erstellen von Datenmodellen und Berichten.

![Power BI Desktop](media/desktop-what-is-desktop/what-is-desktop_01.png)

Wenn Sie noch nicht bei Power BI registriert sind, müssen Sie sich zuerst für eine [kostenlose Testversion registrieren](https://app.powerbi.com/signupredirect?pbi_source=web).

## <a name="prerequisites"></a>Voraussetzungen

Zum Ausführen der Schritte in diesem Artikel benötigen Sie folgende Ressourcen:

* Laden Sie die kostenlose Anwendung Power BI Desktop auf Ihren lokalen Computer herunter, und installieren Sie diese. Sie können Power BI Desktop [direkt](https://powerbi.microsoft.com/desktop) oder über den [Microsoft Store](https://aka.ms/pbidesktopstore) herunterladen.
* [Laden Sie diese Excel-Beispielarbeitsmappe herunter](https://go.microsoft.com/fwlink/?LinkID=521962), und erstellen Sie den Ordner *C:\PBID-qs*, in dem Sie die Excel-Datei speichern können. Bei den späteren Schritten in dieser Schnellstartanleitung wird davon ausgegangen, dass die heruntergeladene Excel-Arbeitsmappe an diesem Speicherort gespeichert ist.
* Bei vielen Datenconnectors in Power BI Desktop muss Internet Explorer 10 oder höher für die Authentifizierung verwendet werden.

## <a name="launch-power-bi-desktop"></a>Starten von Power BI Desktop

Nachdem Sie Power BI Desktop installiert haben, starten Sie die Anwendung, sodass sie auf Ihrem lokalen Computer ausgeführt wird. Ein Tutorial für Power BI wird angezeigt. Befolgen Sie das Tutorial, oder schließen Sie das Dialogfeld, um mit einer leeren Canvas zu beginnen. Auf der Canvas erstellen Sie Visuals und Berichte aus Ihren Daten.

![Power BI Desktop mit leerer Canvas](media/desktop-quickstart-connect-to-data/qs-connect-data_01.png)

## <a name="connect-to-data"></a>Herstellen einer Datenverbindung

Mit Power BI Desktop können Sie Verbindungen mit verschiedenen Arten von Daten herstellen. Diese umfassen Standarddatenquellen wie Microsoft Excel-Dateien. Sie können eine Verbindung mit Onlinediensten herstellen, die unterschiedlichste Datentypen enthalten, z. B. Salesforce, Microsoft Dynamics, Azure Blob Storage und viele weitere.

Wählen Sie zum Herstellen einer Verbindung mit Daten im Menüband **Start** den Eintrag **Daten abrufen** aus.

![„Daten abrufen“ im Menüband „Start“](media/desktop-quickstart-connect-to-data/qs-connect-data_02.png)

Das Fenster **Daten abrufen** wird geöffnet. In diesem können Sie aus den vielen verschiedenen Datenquellen auswählen können, mit denen Power BI Desktop eine Verbindung herstellen kann. In diesem Schnellstart verwenden Sie die Excel-Arbeitsmappe, die Sie unter [Voraussetzungen](#prerequisites) heruntergeladen haben.

![Alle Quellen unter „Daten abrufen“](media/desktop-quickstart-connect-to-data/qs-connect-data_03.png)

Da es sich bei der Datenquelle um eine Excel-Datei handelt, wählen Sie im Fenster **Daten abrufen** die Option **Excel** aus und klicken dann auf **Verbinden**.

Power BI fordert Sie dazu auf, den Speicherort der Excel-Datei anzugeben, mit der Sie eine Verbindung herstellen möchten. Die heruntergeladene Datei heißt *Financial Sample*. Wählen Sie diese Datei aus, und klicken Sie auf **Öffnen**.

![Financial Sample-Daten abrufen](media/desktop-quickstart-connect-to-data/qs-connect-data_04.png)

Power BI Desktop lädt die Arbeitsmappe, liest den Inhalt und zeigt im Fenster **Navigator** die in der Datei verfügbaren Daten an. In diesem Fenster können Sie die Daten auswählen, die in Power BI Desktop geladen werden sollen. Wählen Sie die Tabellen aus, indem Sie die Kontrollkästchen neben jeder Tabelle aktivieren, die Sie importieren möchten. Importieren Sie beide verfügbaren Tabellen.

![Daten im Fenster „Navigator“ auswählen](media/desktop-quickstart-connect-to-data/qs-connect-data_05.png)

Nachdem Sie Ihre Auswahl getroffen haben, klicken Sie auf **Laden**, um die Daten in Power BI Desktop zu importieren.

## <a name="view-data-in-the-fields-pane"></a>Anzeigen von Daten im Bereich „Felder“

Nachdem Sie die Tabellen geladen haben, werden die Daten im Bereich **Felder** angezeigt. Sie können jede Tabelle erweitern, indem Sie auf den Pfeil neben dem Tabellennamen klicken. In der folgenden Abbildung ist die Tabelle *financials* erweitert, und jedes Feld wird angezeigt.

![Abrufen von Daten](media/desktop-quickstart-connect-to-data/qs-connect-data_06.png)

Und das ist auch schon alles! Sie haben in Power BI Desktop eine Verbindung mit Daten hergestellt, diese Daten geladen und können jetzt alle verfügbaren Felder in diesen Tabellen anzeigen.

## <a name="next-steps"></a>Weitere Schritte

In Power BI Desktop können Sie nach dem Herstellen einer Verbindung mit Daten verschiedene Aufgaben ausführen. Sie können beispielsweise Visuals und Berichte erstellen. Sehen Sie sich folgende Ressourcen an, um loszulegen:

* [Erste Schritte mit Power BI Desktop](desktop-getting-started.md)
