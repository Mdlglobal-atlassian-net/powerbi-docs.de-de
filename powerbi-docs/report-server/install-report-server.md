---
title: Installieren von Power BI-Berichtsserver
description: Erfahren Sie, wie Power BI-Berichtsserver installiert wird.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.topic: conceptual
ms.date: 01/16/2020
ms.openlocfilehash: 0b57ec084477955086b3d1bb0acd0a3139d325c6
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "76160602"
---
# <a name="install-power-bi-report-server"></a>Installieren von Power BI-Berichtsserver

Erfahren Sie, wie Power BI-Berichtsserver installiert wird.

## <a name="download-power-bi-report-server"></a>Power BI-Berichtsserver herunterladen

Klicken Sie auf der Seite [Lokale Berichterstellung mit Power BI-Berichtsserver](https://powerbi.microsoft.com/report-server/) auf **Kostenlose Testversion herunterladen**.

Wenn Sie die Datei „PowerBIReportServer.exe“ ausführen, wählen Sie die kostenlose Testversion aus oder geben Ihren Product Key ein. Weitere Details erhalten Sie im Verlauf dieses Artikels.

## <a name="before-you-install"></a>Vor der Installation

Vor der Installation von Power BI-Berichtsserver wird empfohlen, dass Sie die [Hardware- und Softwareanforderungen für die Installation von Power BI-Berichtsserver](system-requirements.md) lesen.

 > [!IMPORTANT]
 > Während Sie den Power BI-Berichtsserver in einer Umgebung mit schreibgeschütztem Domänencontroller (RODC) installieren können, benötigt der Power BI-Berichtsserver Zugang zu einem Domänencontroller mit Lese-/Schreibzugriff, um wie vorgesehen zu funktionieren. Wenn der Power BI-Berichtsserver nur Zugang zu einem RODC hat, treten beim Verwalten des Diensts möglicherweise Fehlermeldungen auf.

### <a name="power-bi-report-server-product-key"></a>Produktschlüssel für den Power BI-Berichtsserver

Sie können den Product Key für Power BI-Berichtsserver aus zwei verschiedenen Quellen abrufen:

- Power BI Premium
- SQL Server Enterprise Software Assurance (SA)

Weitere Details erhalten Sie im Verlauf dieses Artikels.

#### <a name="power-bi-premium"></a>Power BI Premium

Wenn Sie Power BI Premium erworben haben, haben Sie auf der Registerkarte **Premium-Einstellungen** im Power BI-Verwaltungsportal Zugriff auf den Product Key Ihres Power BI-Berichtsservers. Das Verwaltungsportal steht nur globalen Administratoren oder Benutzern zur Verfügung, denen die Administratorrolle für den Power BI-Dienst zugewiesen wurde.

![Premium-Einstellungen](../report-server/media/install-report-server/pbirs-product-key.png "Schlüssel für den Power BI-Berichtsserver in den Premium-Einstellungen")

Wenn Sie auf **Schlüssel für Power BI-Berichtsserver** klicken, wird ein Dialogfeld mit Ihrem Product Key angezeigt. Diesen können Sie kopieren und bei der Installation verwenden.

![Product Key](../report-server/media/install-report-server/pbirs-product-key-dialog.png "Produktschlüssel für den Power BI-Berichtsserver")

#### <a name="sql-server-enterprise-software-assurance-sa"></a>SQL Server Enterprise Software Assurance (SA)

Wenn Sie über einen SQL Server Enterprise SA-Vertrag verfügen, können Sie Ihren Product Key im [Volume Licensing Service Center](https://www.microsoft.com/Licensing/servicecenter/) abrufen.

## <a name="install-your-report-server"></a>Installieren eines Berichtsservers

Die Installation von Power BI-Berichtsserver selbst ist einfach. Zum Installieren der Dateien müssen nur einige Schritte ausgeführt werden.

Zum Zeitpunkt der Installation ist kein Server mit der SQL Server-Datenbank-Engine erforderlich. Sie müssen Reporting Services nach der Installation konfigurieren.

1. Bestimmen Sie den Speicherort der Datei „PowerBIReportServer.exe“, und starten Sie das Installationsprogramm.

2. Wählen Sie **Power BI-Berichtsserver installieren** aus.

    ![Installieren von Power BI-Berichtsserver](media/install-report-server/pbireportserver-install.png)
3. Wählen Sie eine zu installierende Edition aus, und klicken Sie dann auf **Weiter**.

    ![Wählen einer Edition](media/install-report-server/pbireportserver-choose-edition.png)

    Wählen Sie entweder die Evaluierungs- oder die Developer-Edition aus.

    ![Edition 2](media/install-report-server/pbireportserver-choose-edition2.png)

    Andernfalls geben Sie den Product Key ein, den Sie entweder durch den Power BI-Dienst oder das Volume Licensing Service Center erhalten haben. Weitere Informationen zum Abrufen Ihres Product Keys finden Sie oben im Abschnitt [Before you install](#before-you-install) (Vor der Installation).
4. Lesen und akzeptieren Sie die Lizenz- und Geschäftsbedingungen, und klicken Sie dann auf **Weiter**.

    ![Lizenzbedingungen](media/install-report-server/pbireportserver-eula.png)
5. Es muss eine Datenbank-Engine zum Speichern der Berichtsserver-Datenbank zur Verfügung stehen. Klicken Sie auf **Weiter**, um nur den Berichtsserver zu installieren.

    ![Nur Dateien installieren](media/install-report-server/pbireportserver-install-files-only.png)
6. Geben Sie den Installationsspeicherort für den Berichtsserver an. Klicken Sie auf **Installieren**, um den Vorgang fortzusetzen.

    ![Angeben des Installationspfads](media/install-report-server/pbireportserver-install-file-path.png)

    Der Standardpfad lautet „C:\Program Files\Microsoft Power BI Report Server“.

7. Wählen Sie nach erfolgreicher Installation **Berichtsserver konfigurieren** aus, um den Konfigurations-Manager für Reporting Services zu starten.

    ![Konfigurieren des Berichtsservers](media/install-report-server/pbireportserver-configure.png)

## <a name="configure-your-report-server"></a>Konfigurieren des Berichtsservers

Nach Auswahl von **Berichtsserver konfigurieren** beim Setup wird der Konfigurations-Manager für Reporting Services angezeigt. Weitere Informationen finden Sie unter [Konfigurations-Manager für Reporting Services](https://docs.microsoft.com/sql/reporting-services/install-windows/reporting-services-configuration-manager-native-mode).

Zum Abschließen der ersten Konfiguration von Reporting Services müssen Sie [eine Berichtsserver-Datenbank erstellen](https://docs.microsoft.com/sql/reporting-services/install-windows/ssrs-report-server-create-a-report-server-database). Ein SQL Server-Datenbankserver ist erforderlich, um diesen Schritt abzuschließen.

### <a name="creating-a-database-on-a-different-server"></a>Erstellen einer Datenbank auf einem anderen Server

Wenn Sie die Berichtsserver-Datenbank auf einem Datenbankserver auf einem anderen Computer erstellen, ändern Sie das Dienstkonto für den Berichtsserver in Anmeldeinformationen, die auf dem Datenbankserver erkannt werden. 

Standardmäßig verwendet der Berichtsserver das virtuelle Dienstkonto. Wenn Sie versuchen, eine Datenbank auf einem anderen Server zu erstellen, wird möglicherweise der folgenden Fehler zum Schritt „Anwenden von Verbindungsrechten“ angezeigt.

`System.Data.SqlClient.SqlException (0x80131904): Windows NT user or group '(null)' not found. Check the name again.`

Sie können das Dienstkonto entweder in „Netzwerkdienst“ oder „Domänenkonto“ ändern, um den Fehler zu umgehen. Bei Ändern des Dienstkontos in „Netzwerkdienst“ gelten Rechte im Kontext des Computerkontos für den Berichtsserver.

![Konfigurieren des Dienstkontos für den Berichtsserver](media/install-report-server/pbireportserver-configure-account.png)

Weitere Informationen finden Sie unter [Configure the report server service account (Konfigurieren des Dienstkontos für den Berichtsserver)](https://docs.microsoft.com/sql/reporting-services/install-windows/configure-the-report-server-service-account-ssrs-configuration-manager).

## <a name="windows-service"></a>Windows-Dienst

Ein Windows-Dienst wird als Teil der Installation erstellt. Dieser wird als **Power BI-Berichtsserver** angezeigt. Der Dienstname lautet **PowerBIReportServer**.

![Report Server-Windows-Dienst](media/install-report-server/pbireportserver-windows-service.png)

![Eigenschaften des Windows-Diensts „Berichtsserver“](media/install-report-server/pbireportserver-windows-service2.png)

## <a name="default-url-reservations"></a>Standardmäßige URL-Reservierungen

URL-Reservierungen bestehen aus einem Präfix, Hostnamen, Port und virtuellen Verzeichnis:

| Teil | Beschreibung |
| --- | --- |
| Präfix |Das Standardpräfix ist HTTP. Wenn Sie zuvor ein SSL-Zertifikat (Secure Sockets Layer) installiert haben, versucht das Setup, die URL-Reservierungen mit dem Präfix HTTPS zu erstellen. |
| Hostname |Der Standardhostname ist ein Platzhalter (+). Dieses gibt an, dass der Berichtsserver eine beliebige HTTP-Anforderung an den angegebenen Port für einen beliebigen Hostnamen akzeptiert, der für den Computer steht, einschließlich `https://<computername>/reportserver`, `https://localhost/reportserver` oder `https://<IPAddress>/reportserver.`. |
| Port |Der Standardport ist 80. Wenn Sie einen anderen Port als 80 verwenden, müssen Sie diesen explizit der URL hinzufügen, sobald Sie das Webportal in einem Browserfenster öffnen. |
| Virtuelles Verzeichnis |Standardmäßig werden virtuelle Verzeichnisse im Format „ReportServer“ für den Berichtsserver-Webdienst und „Reports“ für das Webportal erstellt. Für den Report Server-Webdienst heißt das standardmäßige virtuelle Verzeichnis **reportserver**. Für das Webportal heißt das standardmäßige virtuelle Verzeichnis **reports**. |

Ein Beispiel der vollständigen URL-Zeichenfolge kann folgendermaßen aussehen:

* `https://+:80/reportserver`: Ermöglicht den Zugriff auf den Berichtsserver.
* `https://+:80/reports` bietet Zugriff auf das Webportal.

## <a name="firewall"></a>Firewall

Wenn Sie von einem Remotecomputer aus auf den Berichtsserver zugreifen möchten, achten Sie darauf, dass Firewallregeln konfiguriert wurden, sofern eine Firewall vorhanden ist.

Öffnen Sie den TCP-Port, den Sie für Ihre Webdienst-URL und die Webportal-URL konfiguriert haben. Standardmäßig werden beide für TCP-Port 80 konfiguriert.

## <a name="additional-configuration"></a>Zusätzliche Konfiguration

* Informationen zum Konfigurieren der Integration in den Power BI-Dienst, damit Sie Berichtselemente an ein Power BI-Dashboard anheften können, finden Sie unter [Integrieren in den Power BI-Dienst](https://docs.microsoft.com/sql/reporting-services/install-windows/power-bi-report-server-integration-configuration-manager).
* Informationen zum Konfigurieren von E-Mail für die Abonnementverarbeitung finden Sie unter [E-Mail-Einstellungen](https://docs.microsoft.com/sql/reporting-services/install-windows/e-mail-settings-reporting-services-native-mode-configuration-manager) und [E-Mail-Übermittlung in Reporting Services](https://docs.microsoft.com/sql/reporting-services/subscriptions/e-mail-delivery-in-reporting-services).
* Informationen zum Konfigurieren des Webportals, damit Sie auf einem Berichtscomputer darauf zugreifen können, um Berichte anzuzeigen und zu verwalten, finden Sie unter [Konfigurieren einer Firewall für den Berichtsserverzugriff](https://docs.microsoft.com/sql/reporting-services/report-server/configure-a-firewall-for-report-server-access) und [Konfigurieren eines Berichtsservers für die Remoteverwaltung](https://docs.microsoft.com/sql/reporting-services/report-server/configure-a-report-server-for-remote-administration).
* Ausführliche Informationen zum Festlegen von Systemeigenschaften für Berichtsserver in SQL Server Management Studio finden Sie unter [Servereigenschaften (Seite „Erweitert“)](https://docs.microsoft.com/sql/reporting-services/tools/server-properties-advanced-page-reporting-services). Sofern nicht anders angegeben, gilt die Option sowohl für den Power BI-Berichtsserver als auch für SQL Server Reporting Services.

## <a name="next-steps"></a>Weitere Schritte

[Administratorübersicht](admin-handbook-overview.md)  
[Ermitteln des Product Key für den Berichtsserver](find-product-key.md)  
[Installieren von für Power BI-Berichtsserver optimiertem Power BI Desktop](install-powerbi-desktop.md)  
[Verify a Reporting Services installation (Überprüfen einer Reporting Services-Installation)](https://docs.microsoft.com/sql/reporting-services/install-windows/verify-a-reporting-services-installation)  
[Konfigurieren des Dienstkontos für den Berichtsserver](https://docs.microsoft.com/sql/reporting-services/install-windows/configure-the-report-server-service-account-ssrs-configuration-manager)  
[Konfigurieren von Berichtsserver-URLs](https://docs.microsoft.com/sql/reporting-services/install-windows/configure-report-server-urls-ssrs-configuration-manager)  
[Konfigurieren einer Verbindung mit der Berichtsserver-Datenbank](https://docs.microsoft.com/sql/reporting-services/install-windows/configure-a-report-server-database-connection-ssrs-configuration-manager)  
[Initialisieren eines Berichtsservers](https://docs.microsoft.com/sql/reporting-services/install-windows/ssrs-encryption-keys-initialize-a-report-server)  
[Konfigurieren von SSL-Verbindungen für einen Berichtsserver](https://docs.microsoft.com/sql/reporting-services/security/configure-ssl-connections-on-a-native-mode-report-server)  
[Konfigurieren von Windows-Dienstkonten und -Berechtigungen](https://docs.microsoft.com/sql/database-engine/configure-windows/configure-windows-service-accounts-and-permissions)  
[Browserunterstützung für Power BI-Berichtsserver](browser-support.md)

Weitere Fragen? [Stellen Sie Ihre Frage in der Power BI-Community.](https://community.powerbi.com/)