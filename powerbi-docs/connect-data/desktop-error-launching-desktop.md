---
title: Beheben von Problemen beim Starten von Power BI Desktop
description: Beheben von Problemen beim Starten von Power BI Desktop
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 01/14/2020
ms.author: davidi
LocalizationGroup: Troubleshooting
ms.openlocfilehash: 67c83f2cc0eb81e90f447961ed178a04e97e050e
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/13/2020
ms.locfileid: "83292085"
---
# <a name="troubleshoot-opening-power-bi-desktop"></a>Problembehandlung beim Öffnen von Power BI Desktop

In Power BI Desktop können Benutzer, die frühere Versionen des *lokalen Power BI-Datengateways* installiert haben und ausführen, am Start von Power BI Desktop gehindert werden. Der Grund hierfür sind Einschränkungen durch eine administrative Richtlinie, die vom lokalen Power BI-Datengateway auf Named Pipes auf dem lokalen Computer angewendet wird.

## <a name="resolve-issues-with-the-on-premises-data-gateway-and-power-bi-desktop"></a>Beheben von Problemen mit dem lokalen Datengateway und Power BI Desktop

Sie haben drei Möglichkeiten, das Problem mit dem lokalen Datengateway zu beheben, damit Power BI Desktop geöffnet werden kann:

### <a name="resolution-1-install-the-latest-version-of-power-bi-on-premises-data-gateway"></a>Lösung 1: Installieren der neuesten Version des lokalen Datengateways von Power BI

Die neueste Version des lokalen Power BI-Datengateways wendet keine Named Pipe-Einschränkungen auf dem lokalen Computer an, sodass Power BI Desktop ordnungsgemäß geöffnet werden kann. Wenn Sie das lokale Power BI-Datengateway weiterhin verwenden müssen, besteht die empfohlene Lösung darin, es zu aktualisieren. Laden Sie die [neueste Version des lokalen Power BI-Datengateways](https://go.microsoft.com/fwlink/?LinkId=698863) herunter. Der Link ist ein direkter Downloadlink zur ausführbaren Installationsdatei.

### <a name="resolution-2-uninstall-or-stop-the-power-bi-on-premises-data-gateway-microsoft-service"></a>Lösung 2: Deinstallieren oder Beenden des Windows-Diensts für das lokale Power BI-Datengateway

Sie können das lokale Power BI-Datengateway deinstallieren, wenn Sie es nicht länger benötigen. Alternativ können Sie den Microsoft-Dienst für das lokale Power BI-Datengateway beenden. Hierdurch wird die Richtlinieneinschränkung entfernt und das Öffnen von Power BI Desktop ermöglicht.

### <a name="resolution-3-run-power-bi-desktop-with-administrator-privilege"></a>Lösung 3: Ausführen von Power BI Desktop mit Administratorrechten

Alternativ können Sie Power BI Desktop als Administrator starten, wodurch auch Power BI Desktop erfolgreich geöffnet werden kann. Es gilt jedoch weiter die Empfehlung, die neueste Version des lokalen Power BI-Datengateways zu installieren, wie bereits beschrieben.

Power BI Desktop wurde als Mehrprozessarchitektur entwickelt, und einige dieser Prozesse kommunizieren mithilfe von Windows-Named Pipes. Möglicherweise gibt es andere Prozesse, bei denen Konflikte mit diesen Named Pipes auftreten können. Die häufigste Ursache für solche Konflikte sind Sicherheitseinstellungen. Hierzu gehören beispielsweise Situationen, in denen Antivirussoftware oder Firewalls die Pipes möglicherweise blockieren oder den Datenverkehr an einem bestimmten Port umleiten. Das Öffnen von Power BI Desktop mit Administratorrechten kann dieses Problem lösen. Wenn Sie Power BI Desktop nicht mit Administratorrechten öffnen können, lassen Sie durch Ihren Administrator feststellen, welche Sicherheitsregeln die ordnungsgemäße Kommunikation von Named Pipes verhindern. Nehmen Sie Power BI Desktop und die zugehörigen Unterprozesse anschließend in die Whitelist auf.

## <a name="resolve-issues-when-connecting-to-sql-server"></a>Beheben von Problemen bei der Verbindungsherstellung mit SQL Server

Wenn Sie versuchen, eine Verbindung mit einer SQL Server-Datenbank herzustellen, wird Ihnen möglicherweise eine Fehlermeldung ähnlich der folgenden angezeigt:

`"An error happened while reading data from the provider:`\
`'Could not load file or assembly 'System.EnterpriseServices, Version=4.0.0.0, Culture=neutral, PublicKeyToken=xxxxxxxxxxxxx' or one of its dependencies.`\
`Either a required impersonation level was not provided, or the provided impersonation level is invalid. (Exception from HRESULT: 0x80070542)'"`

Sie können dieses Problem häufig lösen, indem Sie Power BI Desktop als Administrator öffnen, bevor Sie die SQL Server-Verbindung herstellen.

Nachdem Sie Power BI Desktop als Administrator geöffnet und die Verbindung eingerichtet haben, werden die benötigten DLLs ordnungsgemäß registriert. Danach ist es nicht mehr notwendig, Power BI Desktop als Administrator zu öffnen.

## <a name="get-help-with-other-launch-issues"></a>Anfordern von Hilfe bei weiteren Startproblemen

Wir sind bestrebt, Probleme im Zusammenhang mit Power BI Desktop möglichst umfassend abzudecken. Wir erweitern unsere Artikel regelmäßig um Lösungen für Probleme, die viele Kunden betreffen.

Wenn das Problem beim Starten von Power BI Desktop nicht mit dem lokalen Datengateway zusammenhängt, oder wenn das Problem durch die oben genannten Lösungsvorschläge nicht behoben wird, können Sie beim *Power BI-Support* (<https://support.powerbi.com>) einen Supportfall melden, um Unterstützung bei der Identifikation und Lösung Ihres Problems anzufordern.

Sollten Sie in Zukunft auf andere Probleme mit Power BI Desktop stoßen, ist es hilfreich, die Ablaufverfolgung zu aktivieren und Protokolldateien zu sammeln. Protokolldateien können dazu beitragen, das Problem zu isolieren und zu identifizieren. Aktivieren Sie die Ablaufverfolgung, klicken Sie nacheinander auf **Datei** > **Optionen und Einstellungen** > **Optionen**, wählen Sie **Diagnose** aus, und klicken Sie dann auf **Ablaufverfolgung aktivieren**. Power BI Desktop muss ausgeführt werden, damit diese Option festgelegt werden kann, aber sie ist hilfreich für zukünftige Probleme im Zusammenhang mit dem Öffnen von Power BI Desktop.
