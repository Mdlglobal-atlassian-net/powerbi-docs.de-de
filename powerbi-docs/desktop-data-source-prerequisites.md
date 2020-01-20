---
title: Voraussetzungen für Power BI-Datenquellen
description: Voraussetzungen für Power BI-Datenquellen
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/08/2019
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: d118cae8cd4b6fbd95066b15819b1e798c8bbe0f
ms.sourcegitcommit: 97597ff7d9ac2c08c364ecf0c729eab5d59850ce
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/09/2020
ms.locfileid: "75761316"
---
# <a name="power-bi-data-source-prerequisites"></a>Voraussetzungen für Power BI-Datenquellen
Power BI unterstützt für jeden Datenanbieter einer bestimmten Anbieterversion auf Objekten. Weitere Informationen zu den für Power BI verfügbaren Datenquellen finden Sie unter [Datenquellen](desktop-data-sources.md). Diese Anforderungen sind in der folgenden Tabelle beschrieben.

| Datenquellen- | Anbieter | Minimale Anbieterversion | Minimale Datenquellenversion | Unterstützte Datenquellenobjekte | Download-Link |
| --- | --- | --- | --- | --- | --- |
| SQL Server |ADO.net (in .Net Framework integriert) |.NET Framework 3.5 (ausschließlich) |SQL Server 2005 und höher |Tabellen/Ansichten, skalare Funktionen, Tabellenfunktionen |In .NET Framework 3.5 oder höher enthalten |
| Zugriff |Microsoft Access-Datenbank-Engine (ACE) |ACE 2010 SP1 |Keine Einschränkung |Tabellen/Ansichten |[Downloadlink](https://go.microsoft.com/fwlink/?linkid=285987&clcid=0x409) |
| Excel (nur XLS-Dateien) (siehe Hinweis 1) |Microsoft Access-Datenbank-Engine (ACE) |ACE 2010 SP1 |Keine Einschränkung |Tabellen, Arbeitsblätter |[Downloadlink](https://go.microsoft.com/fwlink/?linkid=285987&clcid=0x409) |
| Oracle (siehe Hinweis 2) |ODP.NET |ODAC 11.2 Version 5 (11.2.0.3.20) |9.x und höher |Tabellen/Ansichten |[Downloadlink](https://go.microsoft.com/fwlink/?linkid=272376&clcid=0x409) |
| | System.Data.OracleClient (in .NET Framework integriert) |.NET Framework 3.5 |9.x und höher |Tabellen/Ansichten |In .NET Framework 3.5 oder höher enthalten |
| IBM DB2 |ADO.NET-Client von IBM (Teil des Treiberpakets des IBM-Datenservers) |10.1 |9.1+ |Tabellen/Ansichten |[Downloadlink](https://go.microsoft.com/fwlink/?linkid=274911&clcid=0x409) |
| MySQL |Connector/Net |6.6.5 |5.1 |Tabellen/Ansichten, skalare Funktionen |[Downloadlink](https://go.microsoft.com/fwlink/?linkid=278885&clcid=0x409) |
| PostgreSQL |NPGSQL ADO.NET-Anbieter |2.0.12 |7.4 |Tabellen/Ansichten |[Downloadlink](https://go.microsoft.com/fwlink/?linkid=282716&clcid=0x409) |
| Teradata |.NET-Datenanbieter für Teradata |14+ |12+ |Tabellen/Ansichten |[Downloadlink](https://go.microsoft.com/fwlink/?linkid=278886&clcid=0x409) |
| SAP Sybase SQL Anywhere |iAnywhere.Data.SQLAnywhere für .NET 3.5 |16+ |16+ |Tabellen/Ansichten |[Downloadlink](https://go.microsoft.com/fwlink/?linkid=324846) |

>[!NOTE]
>Excel-Dateien mit der Erweiterung „.xlsx“ erfordern keine eigene Anbieterinstallation.

>[!NOTE]
>Oracle-Anbieter benötigen außerdem Oracle-Clientsoftware (Version 8.1.7 und höher).
> 
> 

