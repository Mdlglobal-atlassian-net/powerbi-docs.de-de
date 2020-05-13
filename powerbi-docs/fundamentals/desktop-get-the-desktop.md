---
title: Power BI Desktop erwerben
description: Herunterladen und Installieren von Power BI Desktop
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 01/29/2020
ms.author: davidi
LocalizationGroup: Get started
ms.openlocfilehash: b2094b2438966bd2da88de032fd7b7979065746b
ms.sourcegitcommit: bfc2baf862aade6873501566f13c744efdd146f3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/13/2020
ms.locfileid: "83359379"
---
# <a name="get-power-bi-desktop"></a>Power BI Desktop erwerben
In Power BI Desktop können Sie erweiterte Abfragen, Modelle und Berichte erstellen, die Daten visualisieren. Mit Power BI Desktop können Sie Datenmodelle entwerfen, Berichte erstellen und Ihre Arbeit durch die Veröffentlichung im Power BI-Dienst freigeben. Power BI Desktop steht als kostenloser Download zur Verfügung.

Sie können Power BI Desktop auf zwei Arten erhalten, die jeweils in den folgenden Abschnitten beschrieben werden:

* [Installation als App aus dem Microsoft Store](#install-as-an-app-from-the-microsoft-store)
* [Direktes Herunterladen, als ausführbare Datei, die Sie herunterladen und auf dem Computer installieren](#download-power-bi-desktop-directly)

Mit beiden Methoden erhalten Sie auf Ihrem Computer die neueste Version von Power BI Desktop. Es sind jedoch einige Unterschiede zu beachten, die in den folgenden Abschnitten beschrieben werden.

## <a name="install-as-an-app-from-the-microsoft-store"></a>Installation als App aus dem Microsoft Store
Es gibt mehrere Möglichkeiten, auf die neueste Version von Power BI Desktop aus dem Microsoft Store zuzugreifen. 

1. Verwenden Sie eine der folgenden Optionen, um die Seite **Power BI Desktop** vom Microsoft Store zu öffnen:

   - Öffnen Sie einen Browser, und wechseln Sie direkt zur [Power BI Desktop-Seite](https://aka.ms/pbidesktopstore) vom Microsoft Store.

    - Wählen Sie im [Power BI-Dienst](https://docs.microsoft.com/power-bi/service-get-started) in der oberen rechten Ecke das Symbol **Herunterladen** aus, und wählen Sie dann **Power BI Desktop** aus.

      ![Power BI Desktop aus dem Power BI-Dienst herunterladen](media/desktop-get-the-desktop/getpbid_downloads.png)

   - Wechseln Sie zur [Produktseite von Power BI Desktop](https://powerbi.microsoft.com/desktop/), und wählen Sie dann **Kostenloser Download** aus.
  
2. Sobald Sie sich auf der Seite **Power BI Desktop** vom Microsoft Store befinden, wählen Sie **Installieren** aus.

     ![Herunterladen von Power BI Desktop aus dem Microsoft Store](media/desktop-get-the-desktop/getpbid_04.png)

Das Installieren von Power BI Desktop aus dem Microsoft Store bietet einige Vorteile:

* **Automatische Updates**: Windows lädt automatisch im Hintergrund die neueste Version herunter, sobald diese verfügbar ist, sodass ihre Version immer auf dem neuesten Stand ist.
* **Kleinere Downloads**: Durch den Microsoft Store wird sichergestellt, dass in den einzelnen Updates nur geänderte Komponenten auf Ihren Computer heruntergeladen werden, was zu kleineren Downloads für jedes Update führt.
* **Keine Administratorberechtigung erforderlich:** Wenn Sie das Paket direkt herunterladen und installieren, müssen Sie Administrator sein, damit die Installation erfolgreich abgeschlossen wird. Wenn Sie Power BI Desktop aus dem Microsoft Store abrufen, ist *keine* Administratorberechtigung erforderlich.
* **Rollout durch IT möglich**: Über den Microsoft Store für Unternehmen kann Power BI Desktop leichter für alle Benutzer in der Organisation bereitgestellt werden (per *Rollout*).

* **Sprachenerkennung**: Die Microsoft Store-Version umfasst alle unterstützten Sprachen und überprüft bei jedem Start, welche Sprache auf dem Computer verwendet wird. Diese Sprachunterstützung wirkt sich auch auf die Lokalisierung von Modellen aus, die in Power BI Desktop erstellt werden. Beispielsweise entsprechen integrierte Datumshierarchien der Sprache, die in Power BI Desktop beim Erstellen der PBIX-Datei verwendet wird.

Die folgenden Aspekte und Einschränkungen gelten, wenn Sie Power BI Desktop aus dem Microsoft Store installieren:

* Wenn Sie den SAP-Connector verwenden, müssen Sie möglicherweise die SAP-Treiberdateien in den Ordner *Windows\System32* verschieben.
* Beim Installieren von Power BI Desktop aus dem Microsoft Store werden keine Benutzereinstellungen aus der EXE-Version kopiert. Sie müssen möglicherweise eine neue Verbindung mit Ihren aktuellen Datenquellen herstellen und die Anmeldeinformationen für Ihre Datenquellen neu eingeben. 

> [!NOTE]
> Die Power BI-Berichtsserver-Version von Power BI Desktop ist eine eigene Installation und unterscheidet sich von den in diesem Artikel behandelten Versionen. Informationen über die Berichtsserver-Version von Power BI Desktop finden Sie im Artikel [Erstellen eines Power BI-Berichts für Power BI-Berichtsserver](../report-server/quickstart-create-powerbi-report.md).
> 
> 

## <a name="download-power-bi-desktop-directly"></a>Direktes Herunterladen von Power BI Desktop
  
  Wählen Sie auf der Seite [Download Center](https://www.microsoft.com/download/details.aspx?id=58494) die Option **Herunterladen** aus, um die ausführbare Datei von Power BI Desktop aus dem Download Center herunterzuladen. Geben Sie dann eine 32-Bit- oder 64-Bit-Installationsdatei an, die heruntergeladen werden soll.

  ![Die Installationsdatei für Power BI Desktop angeben](media/desktop-get-the-desktop/download-desktop-exe.png)

### <a name="install-power-bi-desktop-after-downloading-it"></a>Installieren von Power BI Desktop nach dem Herunterladen
Nachdem Sie den Download abgeschlossen haben, werden Sie aufgefordert, die Installationsdatei auszuführen.

Seit dem Release im Juli 2019 enthält das Installationspaket für Power BI Desktop nur noch eine EXE-Datei mit allen unterstützten Sprachen mit einer separaten EXE-Datei für die Versionen mit 32-Bit und 64-Bit. Die MSI-Pakete werden ab dem Release von September 2019 eingestellt, sodass die EXE-Datei für die Installation erforderlich ist. Dieser Ansatz vereinfacht insbesondere für Administratoren die Verteilung und Installation sowie Updates. Sie können auch Befehlszeilenparameter verwenden, um den Installationsvorgang anzupassen. Dies wird im Abschnitt [Verwenden von Befehlszeilenoptionen bei der Installation](#using-command-line-options-during-installation) beschrieben.

Sobald Sie das Installationspaket gestartet haben, wird Power BI Desktop als Anwendung installiert und auf dem Desktop ausgeführt.

![Das Setup von Power BI Desktop ausführen](media/desktop-get-the-desktop/designer_gsg_install.png)

> [!NOTE]
> Das Installieren der heruntergeladenen Version (MSI-Paket, veraltet) von Power BI Desktop und der Version aus dem Microsoft Store auf demselben Computer (auch als *parallele* Installation bezeichnet) wird nicht unterstützt. Deinstallieren Sie Power BI Desktop manuell, bevor Sie den Download aus dem Microsoft Store starten.
> 

## <a name="using-power-bi-desktop"></a>Verwenden von Power BI Desktop
Wenn Sie Power BI Desktop starten, wird ein Willkommensbildschirm angezeigt.

![Begrüßungsbildschirm von Power BI Desktop](media/desktop-get-the-desktop/getpbid_05.png)

Wenn Sie Power BI Desktop zum ersten Mal verwenden (d. h. wenn die Installation kein Upgrade ist), werden Sie aufgefordert, ein Formular auszufüllen oder sich beim Power BI-Dienst anzumelden, bevor Sie den Vorgang fortsetzen können.

Von dort aus können Sie damit beginnen, Datenmodelle oder Berichte zu erstellen und diese im Power BI-Dienst mit anderen Personen zu teilen. Weitere Informationen zu den ersten Schritten mit Power BI Desktop finden Sie im Abschnitt [Nächste Schritte](#next-steps).

## <a name="minimum-requirements"></a>Mindestanforderungen
Die folgende Liste zeigt die Mindestanforderungen zur Ausführung von Power BI Desktop:

* Windows 7/Windows Server 2008 R2 oder höher
* .NET 4.5
* Internet Explorer 10 oder höher
* Arbeitsspeicher (RAM): Mindestens 1 GB freier Arbeitsspeicher, 1,5 GB oder mehr empfohlen.
* Bildschirm: Mindestens 1440 × 900 oder 1600 × 900 (16:9) empfohlen. Geringere Auflösungen, z. B. 1024 × 768 oder 1280 × 800, werden nicht empfohlen, da zum Anzeigen bestimmter Steuerelemente (z. B. das Schließen des Startbildschirms) eine höhere Auflösung erforderlich ist.
* Windows-Anzeigeeinstellungen: Wenn Sie Ihre Anzeigeeinstellungen so konfigurieren, dass die Größe von Text, Apps und anderen Elementen auf mehr als 100 % geändert wird, sind einige Dialogfelder, mit denen Sie interagieren müssen, um weiterhin Power BI Desktop zu verwenden, möglicherweise nicht sichtbar. Wenn dieses Problem auftritt, überprüfen Sie die Anzeigeeinstellungen in Windows, indem Sie zu **Einstellungen** > **System** > **Anzeige** navigieren, und setzen Sie die Anzeigeeinstellungen mithilfe des Schiebereglers auf 100 % zurück.
* CPU: 32-Bit- oder 64-Bit-x86-Prozessor mit 1 Gigahertz (GHz) oder schneller empfohlen

## <a name="considerations-and-limitations"></a>Überlegungen und Einschränkungen

Wir möchten, dass Sie nur die besten Erfahrungen mit Power BI Desktop machen. Sollte einmal ein Problem mit Power BI Desktop auftreten, finden Sie in diesem Abschnitt Lösungen oder Vorschläge, wie sich diese Probleme beheben lassen. 

### <a name="using-command-line-options-during-installation"></a>Verwenden von Befehlszeilenoptionen bei der Installation 

Bei der Installation von Power BI Desktop können Sie Eigenschaften und Optionen mit Befehlszeilenschaltern festlegen. Diese Einstellungen sind besonders nützlich für Administratoren, die die Installation von Power BI Desktop in Organisationen verwalten oder unterstützen. Die folgenden Optionen können für MSI- und EXE-Installationen verwendet werden. 


|Befehlszeilenoption  |Verhalten  |
|---------|---------|
|-q, -quiet, -s, -silent     |Installation im Hintergrund         |
|-passive     |Während der Installation ist nur die Statusanzeige sichtbar.         |
|-norestart     |Die Anforderung zum Neustart des Computers wird unterdrückt.         |
|-forcerestart     |Der Computer wird nach der Installation ohne Eingabeaufforderung neu gestartet.         |
|-promptrestart     |Wenn ein Neustart des Computers erforderlich ist, wird dem Benutzer eine Eingabeaufforderung angezeigt (Standardeinstellung).         |
|-l<>, -log<>     |Die Installation wird protokolliert, und die zugehörigen Daten werden in eine Datei geschrieben, die zwischen <> angegeben wird.         |
|-uninstall     |Power BI Desktop wird deinstalliert.         |
|-repair     |Die Installation wird repariert (oder installiert, falls die Anwendung noch nicht installiert wurde).         |
|-package, -update     |Power BI Desktop wird installiert (Standardeinstellung, falls „-uninstall“ oder „-repair“ nicht angegeben wird).         |

Sie können auch die folgenden Syntaxparameter verwenden, die Sie mit der Syntax *property = value* angegeben haben:

|Parameter  |Bedeutung  |
|---------|---------|
|ACCEPT_EULA     |Erfordert den Wert 1 zum automatischen Akzeptieren der EULA.         |
|ENABLECXP     |Der Wert 1 wird im Programm für Benutzerfreundlichkeit registriert, das Telemetriedaten zur Nutzung des Produkts erfasst.         |
|INSTALLDESKTOPSHORTCUT     |Mit dem Wert 1 wird dem Desktop eine Verknüpfung hinzugefügt.         |
|INSTALLLOCATION     |Dateipfad zu dem Speicherort, an dem die Installation erfolgen soll.         |
|LANGUAGE     |Der Gebietsschemacode, z. B. „en-US“, „de-DE“, „pr-BR“, um die Standardsprache der Anwendung zu erzwingen. Wenn Sie keine Sprache angeben, wird Power BI Desktop in der Sprache des Windows-Betriebssystems angezeigt. Sie können diese Einstellung im Dialogfeld **Optionen** ändern.         |
|REG_SHOWLEADGENDIALOG     |Der Wert 0 deaktiviert die Anzeige des Dialogfelds, das angezeigt wird, bevor Sie sich bei Power BI Desktop angemeldet haben.         |
|DISABLE_UPDATE_NOTIFICATION     |Mit dem Wert 1 werden Updatebenachrichtigungen deaktiviert.         |


Beispielsweise können Sie Power BI Desktop mit den folgenden Optionen und Parametern ohne Benutzeroberfläche unter Verwendung der Sprache „Deutsch“ installieren: 

```-quiet LANG=de-DE ACCEPT_EULA=1```

### <a name="installing-power-bi-desktop-on-remote-machines"></a>Installieren von Power BI Desktop auf Remotecomputern

Wenn Sie Power BI Desktop für Ihre Benutzer mit einem Tool bereitstellen, das eine Windows Installer-Datei (MSI-Datei) erfordert, können Sie die MSI-Datei aus der Power BI Desktop-Installer-EXE-Datei extrahieren. Verwenden Sie ein Drittanbietertool, z. B. das WiX Toolset.

> [!NOTE]
> Da es sich um ein Drittanbieterprodukt handelt, könnten sich die Optionen des WiX Toolsets ohne vorherige Ankündigung ändern. Entnehmen Sie der Dokumentation die aktuellen Informationen, und kontaktieren Sie die Benutzermailingliste, um Hilfe zu erhalten.

1. Installieren Sie auf dem Computer, auf dem Sie den Power BI Desktop-Installer heruntergeladen haben, die neueste Version des [WiX Toolsets](https://wixtoolset.org/).
2. Öffnen Sie ein Befehlszeilenfenster als Administrator, und navigieren Sie zu dem Ordner, in dem Sie das WiX Toolset installiert haben.
3. Führen Sie den folgenden Befehl aus: 
    
    ```Dark.exe <path to Power BI Desktop installer> -x <output folder>```

    Beispiel:

    ``` Dark.exe C:\PBIDesktop_x64.exe -x C:\output```

    Der Ausgabeordner enthält einen Ordner mit dem Namen *AttachedContainer*, der die MSI-Dateien enthält.

Das Upgrade einer Installation von einer EXE- zu einer MSI-Datei, die Sie aus einer EXE-Datei extrahiert haben, wird nicht unterstützt.   Um dieses Upgrade vorzunehmen, müssen Sie zunächst Ihre vorhandene ältere Version von Power BI Desktop deinstallieren.

### <a name="issues-when-using-previous-releases-of-power-bi-desktop"></a>Probleme bei der Verwendung von früheren Versionen von Power BI Desktop

Bei einigen Benutzern kann eine Fehlermeldung angezeigt werden, die der folgenden ähnelt, wenn sie eine veraltete Version von Power BI Desktop verwenden: 

*Die gespeicherte Datenbank konnte nicht im Modell wiederhergestellt werden*. 

In der Regel können Sie dieses Problem beheben, indem Sie Power BI Desktop auf die aktuelle Version aktualisieren.

### <a name="disabling-notifications"></a>Deaktivieren von Benachrichtigungen
Es empfiehlt sich, ein Update auf die neueste Version von Power BI Desktop auszuführen, um von neuen Features, Verbesserungen bei Leistung und Stabilität sowie weiteren Vorteilen zu profitieren. In einigen Organisationen ist es aber möglicherweise nicht erwünscht, dass Benutzer bei jeder neuen Version ein Update ausführen. Sie können Benachrichtigungen deaktivieren, indem Sie mithilfe der folgenden Schritte die Registrierung ändern:

1. Navigieren Sie im Registrierungs-Editor zu **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft Power BI Desktop**.
2. Erstellen Sie im Schlüssel einen neuen **REG_DWORD**-Eintrag mit dem folgenden Namen: **DisableUpdateNotification**.
3. Legen Sie den Wert dieses neuen Eintrags auf **1** fest.
4. Starten Sie Ihren Computer neu, damit die Änderung wirksam wird.

### <a name="power-bi-desktop-loads-with-a-partial-screen"></a>Power BI Desktop lädt mit einer Teilanzeige

Unter bestimmten Umständen, beispielsweise bei einigen Konfigurationen der Bildschirmauflösung, werden Power BI Desktop-Inhalte nicht vollständig geladen, und stattdessen werden große schwarze Bereiche angezeigt. Dieses Problem ist in der Regel die Folge von Betriebssystemupdates, die sich auf die Anzeige von Elementen auswirken, und liegt nicht an der Inhaltsdarstellung durch Power BI Desktop. Gehen Sie folgendermaßen vor, um das Problem zu beheben:

1. Klicken Sie auf **Start**, und geben Sie in der angezeigten Suchleiste das Wort *unscharf* ein.
2. Wählen Sie im daraufhin angezeigten Dialogfeld diese Option aus: **Windows das Beheben von unscharfen Apps überlassen**.
3. Starten Sie Power BI Desktop neu.

Dieses Problem wird möglicherweise mit der Veröffentlichung nachfolgender Windows-Updates behoben. 
 

## <a name="next-steps"></a>Nächste Schritte
Nachdem Sie Power BI Desktop installiert haben, lesen Sie die folgenden Artikel, damit Sie direkt loslegen können:

* [Was ist Power BI Desktop?](desktop-what-is-desktop.md)
* [Abfrageübersicht in Power BI Desktop](../transform-model/desktop-query-overview.md)
* [Datenquellen in Power BI Desktop](../connect-data/desktop-data-sources.md)
* [Verbinden mit Daten in Power BI Desktop](../connect-data/desktop-connect-to-data.md)
* [Strukturieren und Kombinieren von Daten in Power BI Desktop](../connect-data/desktop-shape-and-combine-data.md)
* [Allgemeine Abfrageaufgaben in Power BI Desktop](../transform-model/desktop-common-query-tasks.md)   
