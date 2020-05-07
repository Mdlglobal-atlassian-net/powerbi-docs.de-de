---
title: PowerShell-Cmdlets, REST-APIs und das .NET SDK für Administratoren
description: Erfahren Sie, wie Sie Power BI mit Skripts und durch das Programmieren von APIs verwalten können.
author: kfollis
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 09/09/2019
ms.author: kfollis
LocalizationGroup: Administration
ms.openlocfilehash: b4f4227a53a87cd831962bc5c944a569531b8232
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "74699864"
---
# <a name="powershell-cmdlets-rest-apis-and-net-sdk-for-power-bi-administration"></a>PowerShell-Cmdlets, REST-APIs und das .NET SDK für die Power BI-Verwaltung
Mit Power BI können Administratoren für häufige Tasks mit PowerShell-Cmdlets Skripts erstellen. Außerdem stellt es REST-APIs zur Verfügung und bietet ein .NET SDK zum Entwickeln von Verwaltungslösungen. In diesem Thema finden Sie eine Liste von Cmdlets und dazugehörigen SDK-Methoden und REST-API-Endpunkten. Weitere Informationen finden Sie unter:

- [PowerShell-Download](https://www.powershellgallery.com/packages/MicrosoftPowerBIMgmt/) und [PowerShell-Dokumentation](https://docs.microsoft.com/powershell/power-bi/overview?view=powerbi-ps)
- [REST-API-Dokumentation](https://docs.microsoft.com/rest/api/power-bi/admin)
- [.NET SDK-Download](https://www.nuget.org/packages/Microsoft.PowerBI.Api/)

> Die nachstehenden Cmdlets müssen mit `-Scope Organization` aufgerufen werden, damit sie für den Mandanten für die Verwaltung ausgeführt werden.

| **Name des Cmdlet** | **Aliase** | **SDK-Methode** | **REST-API-Endpunkt** | **Description** (Beschreibung) |
| --- | --- | --- | --- | --- |
| `Get-PowerBIDatasource` | – | `Datasets_GetDataSourcesAsAdmin` | /v1.0/myorg/admin/datasets/{datasetkey}/datasources | Ruft die Datenquellen eines angegebenen Datasets ab |
| `Get-PowerBIDataset` | – | `Datasets_GetDatasetsAsAdmin` | /v1.0/myorg/admin/datasets | Ruft die Liste aller Datasets im Power BI-Mandanten ab |
| `Get-PowerBIWorkspace` | `Get-PowerBIGroup` | `Groups_GetGroupsAsAdmin` | /v1.0/myorg/admin/groups | Ruft die Liste aller Arbeitsbereiche im Power BI-Mandanten ab |
| `Add-PowerBIWorkspaceUser` | `Add-PowerBIGroupUser` | `Groups_AddUserAsAdmin` | /v1.0/myorg/admin/groups/{groupId}/users | Fügt einen Benutzer einem angegeben Arbeitsbereich als Mitglied hinzu |
| `Remove-PowerBIWorkspaceUser` | `Remove-PowerBIGroupUser` | `Groups_DeleteUserAsAdmin` | /v1.0/myorg/admin/groups/{groupId}/users/{user} | Entfernt die Mitgliedschaft eines Benutzers aus einem angegebenen Arbeitsbereich |
| `Restore-PowerBIWorkspace` |`Restore-PowerBIGroup` | `Groups_RestoreDeletedGroupAsAdmin` | /v1.0/myorg/admin/groups/{groupId}/restore | Stellt einen gelöschten Arbeitsbereich wieder her |
| `Set-PowerBIWorkspace` |`Set-PowerBIGroup` | `Groups_UpdateGroupAsAdmin` | /v1.0/myorg/admin/groups/{groupId} | Aktualisiert die Eigenschaften eines angegebenen Arbeitsbereichs |
| `Get-PowerBIDataset -WorkspaceId` | – | `Groups_GetDatasetsAsAdmin` | /v1.0/myorg/admin/groups/{group\_id}/datasets | Ruft die Datasets in einem Arbeitsbereich ab |
| `Get-PowerBIReport` | – | `Reports_GetReportsAsAdmin` | /v1.0/myorg/admin/reports | Ruft die Liste aller Berichte im Power BI-Mandanten ab |
| `Get-PowerBIDashboard` | – | `Dashboards_GetDashboardsAsAdmin` | /v1.0/myorg/admin/dashboards | Ruft die Liste aller Dashboard im Power BI-Mandanten ab |
| `Get-PowerBIDashboard -WorkspaceId` | – | `Groups_GetDashboardsAsAdmin` | /v1.0/myorg/admin/groups/{group\_id}/dashboards | Ruft die Dashboards in einem angegebenen Arbeitsbereich ab |
| `Get-PowerBITile` | `Get-PowerBIDashboardTile` | `Dashboards_GetTilesAsAdmin` | /v1.0/myorg/admin/dashboards/{dashboard\_id}/tiles | Ruft die Kacheln eines angegebenen Dashboards ab |
| `Get-PowerBIReport` | – | `Groups_GetReportsAsAdmin` | /v1.0/myorg/admin/groups/{group\_id}/reports | Ruft die Berichte in einem angegebenen Arbeitsbereich ab |
| `Get-PowerBIImport` | – | `Imports_GetImportsAsAdmin` | /v1.0/myorg/admin/imports | Ruft die Liste aller Importe im Power BI-Mandanten ab |
| `Connect-PowerBIServiceAccount` | `Login-PowerBI` &  `Login-PowerBIServiceAccount` | – | – | Anmelden bei Power BI und Starten einer Sitzung |
| `Disconnect-PowerBIServiceAccount` | `Logout-PowerBI` & `Logout-PowerBIServiceAccount` | – | – | Abmelden von Power BI und Beenden der laufenden Sitzung |
| `Invoke-PowerBIRestMethod`| – | – | – | Senden willkürlicher REST-API-Aufrufe an Power BI |
| `Get-PowerBIAccessToken`| – | – | – | Abrufen des Power BI-Zugriffschlüssels in einer Sitzung |
| `Resolve-PowerBIError`| – | – | – | Abrufen ausführlicher Fehlerinformationen zu Cmdlet-Aufrufen, die mit einem Fehler abgeschlossen wurden |
