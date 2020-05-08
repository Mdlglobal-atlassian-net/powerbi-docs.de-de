---
title: Hardware- und Softwareanforderungen für die Installation von Power BI-Berichtsserver
description: In diesem Artikel werden die Mindestanforderungen an die Hardware und Software zum Installieren und Ausführen von Power BI-Berichtsserver aufgeführt.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.topic: conceptual
ms.date: 02/20/2020
ms.openlocfilehash: 20b41762f7b38bd4ed26add97abb4eec1da0c000
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "77558564"
---
# <a name="hardware-and-software-requirements-for-installing-power-bi-report-server"></a>Hardware- und Softwareanforderungen für die Installation von Power BI-Berichtsserver

In diesem Artikel werden die Mindestanforderungen an die Hardware und Software zum Installieren und Ausführen von Power BI-Berichtsserver aufgeführt.

## <a name="processor-memory-and-operating-system-requirements"></a>Prozessor-, Arbeitsspeicher- und Betriebssystemanforderungen

| Komponente | Anforderung |
| --- | --- |
| .NET Framework |4,7<br><br>Über [Microsoft .NET Framework 4.7 (Webinstaller) für Windows](https://support.microsoft.com/en-us/kb/3186500) können Sie .NET Framework manuell installieren.<br/><br/> Weitere Informationen, Empfehlungen und Anleitungen zu .NET Framework 4.7 finden Sie im [Handbuch für die Bereitstellung von .NET Framework für Entwickler](https://docs.microsoft.com/dotnet/framework/deployment/deployment-guide-for-developers).<br/><br/>Windows 8.1 und Windows Server 2012 R2 erfordern die Installation von [KB2919355](https://support.microsoft.com/kb/2919355) vor der Installation von .NET Framework 4.7. |
| Festplatte |Power BI-Berichtsserver erfordert mindestens 1 GB verfügbaren Speicherplatz auf der Festplatte.<br><br>Außerdem ist zusätzlicher Speicherplatz auf dem Datenbankserver erforderlich, der die Berichtsserver-Datenbank hostet. |
| Memory |**Minimum:** 1GB<br/><br/> **Empfohlen:** Mindestens 4 GB |
| Prozessorgeschwindigkeit |**Minimum:** x64-Prozessor, 1,4 GHz<br/><br/> **Empfohlen:** 2,0 GHz oder schneller |
| Prozessortyp |x64-Prozessor: AMD Opteron, AMD Athlon 64, Intel Xeon mit Intel EM64T-Unterstützung, Intel Pentium IV mit EM64T-Unterstützung |
| Betriebssystem |Windows Server 2019 Datacenter<br><br>Windows Server 2019 Standard<br><br>Windows Server 2016 Datacenter<br><br>Windows Server 2016 Standard<br><br>Windows Server 2012 R2 Datacenter<br><br>Windows Server 2012 R2 Standard<br><br>Windows Server 2012 R2 Essentials<br><br>Windows Server 2012 R2 Foundation<br><br>Windows Server 2012 Datacenter<br><br>Windows Server 2012 Standard<br><br>Windows Server 2012 Essentials<br><br>Windows Server 2012 Foundation<br><br>Windows 10 Home<br><br>Windows 10 Professional<br><br>Windows 10 Enterprise<br><br>Windows 8.1<br><br>Windows 8.1 Pro<br><br>Windows 8.1 Enterprise<br><br>Windows 8<br><br>Windows 8 Pro<br><br>Windows 8 Enterprise |

> [!NOTE]
> Die Installation von Power BI-Berichtsserver wird nur für x64-Prozessoren unterstützt.


## <a name="database-server-version-requirements"></a>Anforderungen an die Version des Datenbankservers

Als Host der Berichtsserver-Datenbanken wird SQL Server verwendet. Die Instanz der SQL Server-Datenbank-Engine kann eine lokale oder Remoteinstanz sein. Die folgenden unterstützten Versionen der SQL Server-Datenbank-Engine können als Host der Berichtsserver-Datenbanken verwendet werden:

* Verwaltete Azure SQL-Instanz (Power BI-Berichtsserver-Version und Januar 2020 und höher)
* SQL Server 2019
* SQL Server 2017
* SQL Server 2016
* SQL Server 2014
* SQL Server 2012

Wenn Sie die Berichtsserver-Datenbank auf einem Remotecomputer erstellen, müssen Sie die Verbindung für die Verwendung eines Domänenbenutzerkontos oder Dienstkontos mit Netzwerkzugriff konfigurieren. Wenn Sie eine Remoteinstanz von SQL Server verwenden möchten, sollten Sie sorgfältig überlegen, welche Anmeldeinformationen der Berichtsserver zum Herstellen der Verbindung mit der SQL Server-Instanz verwenden soll. Weitere Informationen finden Sie unter [Konfigurieren einer Verbindung mit der Berichtsserver-Datenbank](https://docs.microsoft.com/sql/reporting-services/install-windows/configure-a-report-server-database-connection-ssrs-configuration-manager).

## <a name="considerations"></a>Überlegungen

Power BI-Berichtsserver installiert Standardwerte zum Konfigurieren der Haupteinstellungen, die für die Inbetriebnahme eines Berichtsservers erforderlich sind. Es bestehen folgende Anforderungen:

* Für Microsoft Power BI-Berichtsserver werden die folgenden Sprachen unterstützt: Englisch, Deutsch, Spanisch, Japanisch, Italienisch, Französisch, Russisch, vereinfachtes Chinesisch, traditionelles Chinesisch, Portugiesisch (Brasilien), Koreanisch.
* Eine SQL Server-Datenbank-Engine muss nach dem Setup und vor der Konfiguration der Datenbank für den Berichtsserver verfügbar sein. Die Instanz der Datenbank-Engine hostet die Berichtsserver-Datenbank, die der Konfigurations-Manager für Reporting Services erstellt. Die Datenbank-Engine ist für das eigentliche Setup nicht erforderlich.
* Unter [Von den SQL Server-Editionen unterstützte Reporting Services-Features](https://docs.microsoft.com/sql/reporting-services/reporting-services-features-supported-by-the-editions-of-sql-server-2016) werden Unterschiede zwischen den Editionen von SQL Server beschrieben.
* Das Benutzerkonto zum Ausführen von Setup muss Mitglied der lokalen Gruppe „Administratoren“ sein.
* Das Benutzerkonto für den Konfigurations-Manager für Reporting Services benötigt die Berechtigung für den Zugriff auf und das Erstellen von Datenbanken in der Instanz der Datenbank-Engine, die die Berichtsserver-Datenbanken hostet.
* Setup muss die Standardwerte verwenden können, um die URLs zu reservieren, die Zugriff auf den Berichtsserver und das Webportal gewähren. Zu diesen Werten gehören Port 80, ein Platzhalter und Namen der virtuellen Verzeichnisse im Format **ReportServer** und **Reports**.

## <a name="read-only-domain-controller-rodc"></a>Schreibgeschützter Domänencontroller (RODC)

 Sie können den Berichtsserver in einer Umgebung installieren, die über einen schreibgeschützten Domänencontroller (RODC) verfügt. Reporting Services benötigt jedoch Zugriff auf einen Domänencontroller mit Lese-/Schreibzugriff, um ordnungsgemäß zu funktionieren. Wenn Reporting Services nur Zugriff auf einen schreibgeschützten Domänencontroller hat, können beim Verwalten des Diensts Fehler auftreten.

## <a name="power-bi-reports-and-analysis-services-live-connections"></a>Power BI-Berichte und Analysis Services-Liveverbindungen

Sie können eine Liveverbindung für tabellarische oder mehrdimensionale Instanzen verwenden. Ihr Server mit Analysis Services benötigt die richtige Version und Edition, um ordnungsgemäß zu funktionieren.

| **Serverversion** | **Erforderliche SKU** |
| --- | --- |
| 2012 SP1 CU4 oder höher |Business Intelligence und Enterprise SKU |
| 2014 |Business Intelligence und Enterprise SKU |
| 2016 und höher |Standard-SKU oder höher |

## <a name="next-steps"></a>Weitere Schritte

[Was ist der Power BI-Berichtsserver?](get-started.md)  
[Administratorübersicht](admin-handbook-overview.md)  
[Installieren von Power BI-Berichtsserver](install-report-server.md)  
[Herunterladen des Berichts-Generators](https://www.microsoft.com/download/details.aspx?id=53613)  
[Download der neuesten SQL Server-Datatools](https://go.microsoft.com/fwlink/?LinkID=616714)

Weitere Fragen? [Stellen Sie Ihre Frage in der Power BI-Community.](https://community.powerbi.com/)
