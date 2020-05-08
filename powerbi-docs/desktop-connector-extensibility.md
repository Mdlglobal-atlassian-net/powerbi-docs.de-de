---
title: Connectorerweiterbarkeit in Power BI
description: Connectorerweiterbarkeit, Funktionen, Sicherheitseinstellungen und zertifizierte Connectors
author: cpopell
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 01/02/2020
ms.author: gepopell
LocalizationGroup: Connect to data
ms.openlocfilehash: b604ade56335e65b25501eb9fe3d3c2fd185a6f0
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "75761393"
---
# <a name="connector-extensibility-in-power-bi"></a>Connectorerweiterbarkeit in Power BI

In Power BI können Sie mithilfe von vorhandenen Connectors und generischen Datenquellen, wie ODBC, OData, OLE DB, Web, CSV, XML und JSON, eine Verbindung mit Daten herstellen. Alternativ dazu können Entwickler auch neue Datenquellen mit benutzerdefinierten Datenerweiterungen aktivieren, die *benutzerdefinierte Connectors* genannt werden. Einige benutzerdefinierte Connectors werden von Microsoft zertifiziert und als *zertifizierte Connectors* verteilt.

Wenn Sie nicht zertifizierte benutzerdefinierte Connectors verwenden möchten, die von Ihnen oder einem Drittanbieter entwickelt wurden, müssen Sie die Sicherheitseinstellungen in Power BI Desktop so anpassen, dass Erweiterungen ohne Überprüfung oder Warnung geladen werden können. Sie sollten diese Sicherheitseinstellung nur verwenden, wenn Sie den benutzerdefinierten Connectors hundertprozentig vertrauen, da der Code Anmeldeinformationen verarbeitet (und diese beispielsweise über HTTP sendet) und Datenschutzebenen ignorieren kann.

Eine andere Möglichkeit besteht darin, dass Entwickler die Connectors mit einem Zertifikat signieren und die Informationen bereitstellen, die für eine Verwendung ohne Änderung der Sicherheitseinstellungen erforderlich sind. Weitere Informationen finden Sie unter [Vertrauenswürdige Connectors von Drittanbietern](desktop-trusted-third-party-connectors.md).

## <a name="custom-connectors"></a>Benutzerdefinierte Connectors

Nicht zertifizierte benutzerdefinierte Connectors können zahlreiche Funktionen bereitstellen – von kleinen unternehmenskritischen APIs bis hin zu großen branchenspezifischen Diensten, für die Microsoft keinen Connector veröffentlicht hat. Viele dieser Connectors werden vom Anbieter verteilt. Wenn Sie einen bestimmten Datenconnector benötigen, wenden Sie sich an den Anbieter. 

Wenn Sie einen nicht zertifizierten benutzerdefinierten Connector verwenden möchten, legen Sie die Connectordatei mit der Endung *.pq*, *.pqx*, *.m* oder *.mez* im Ordner *\[Dokumente]\\Power BI Desktop\\Benutzerdefinierte Connectors* ab. Erstellen Sie den Ordner, falls er noch nicht vorhanden ist.

Führen Sie die folgenden Schritte aus, um die Sicherheitseinstellungen für Datenerweiterungen anzupassen:

Klicken Sie in Power BI Desktop auf **Datei** > **Optionen und Einstellungen** > **Optionen** > **Sicherheit**.

Wählen Sie unter **Datenerweiterungen** die Option **(Nicht empfohlen) Alle Erweiterungen ohne Überprüfung oder Warnung laden** aus. Klicken Sie auf **OK**, und starten Sie Power BI Desktop neu. 

![Nicht zertifizierte benutzerdefinierte Connectors in den Sicherheitsoptionen für Datenerweiterungen zulassen](media/desktop-connector-extensibility/data-extension-security-1.png)

Die Standardeinstellung der Power BI Desktop-Sicherheitseinstellung für Datenerweiterungen lautet **(Empfohlen) Nur das Laden von durch Microsoft zertifizierten und anderen vertrauenswürdigen Drittanbietererweiterungen zulassen**. Sind bei dieser Einstellung nicht zertifizierte benutzerdefinierte Connectors auf Ihrem System vorhanden, wird beim Start von Power BI Desktop das Dialogfeld **Nicht zertifizierte Connectors** mit einer Liste der Connectors angezeigt, die nicht sicher geladen werden können.

![Dialogfeld „Nicht zertifizierte Connectors“](media/desktop-connector-extensibility/data-extension-security-2.png)

Zur Fehlerbehebung können Sie entweder Ihre Sicherheitseinstellung für **Datenerweiterungen** ändern oder die nicht zertifizierten Connectors aus dem Ordner *Benutzerdefinierte Connectors* entfernen.

## <a name="certified-connectors"></a>Zertifizierte Connectors

Eine begrenzte Teilmenge von Datenerweiterungen gilt als *zertifiziert*. Microsoft verteilt die Connectors zwar, ist aber nicht für deren Leistung oder den Erhalt ihrer Funktionalität verantwortlich. Verantwortlich für die Wartung und Unterstützung des Connectors ist der Drittanbieterentwickler, der ihn erstellt hat. 

Zertifizierte Connectors von Drittanbietern werden in Power BI Desktop im Dialogfeld **Daten abrufen** neben generischen und allgemeinen Connectors aufgelistet. Zur Verwendung von zertifizierten Connectors müssen Sie die Sicherheitseinstellungen nicht anpassen.

Wenn Sie einen benutzerdefinierten Connector zertifizieren möchten, bitten Sie den Anbieter, sich an dataconnectors@microsoft.com zu wenden.
