---
title: Herstellen einer Verbindung mit einer Oracle-Datenbank
description: Erforderliche Schritte und Downloads zum Verbinden von Oracle mit Power BI Desktop
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 04/24/2020
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: a118cd0874410e538ca8329e0b8c0ed1bdb430b7
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "82149595"
---
# <a name="connect-to-an-oracle-database"></a>Herstellen einer Verbindung mit einer Oracle-Datenbank
Für die Herstellung einer Verbindung mit einer Oracle-Datenbank muss auf dem Computer, auf dem Power BI Desktop ausgeführt wird, die richtigen Oracle-Clientsoftware installiert sein. Welche Oracle-Clientsoftware Sie verwenden, hängt davon ab, welche Version von Power BI Desktop Sie installiert haben: 32-Bit oder 64-Bit.

Unterstützte Oracle-Versionen: 
- Oracle 9 und höher
- Oracle-Clientsoftware, Version 8.1.7 und höher

> [!NOTE]
> Wenn Sie eine Oracle-Datenbank für den Power BI-Berichtsserver konfigurieren möchten, finden Sie im Artikel [Oracle-Verbindungstyp ((Berichts-Generator und Power BI-Berichtsserver) | Microsoft-Dokumentation)](https://docs.microsoft.com/sql/reporting-services/report-data/oracle-connection-type-ssrs?view=sql-server-ver15) weitere Informationen. 


## <a name="determining-which-version-of-power-bi-desktop-is-installed"></a>Ermitteln der installierten Version von Power BI Desktop
Wählen Sie **Datei** > **Hilfe** > **Info** aus, und überprüfen Sie dann die Zeile **Version**, um zu bestimmen, welche Version von Power BI Desktop installiert ist. In der folgenden Abbildung ist eine 64-Bit-Version von Power BI Desktop installiert:

![Power BI Desktop-Version](media/desktop-connect-oracle-database/connect-oracle-database_1.png)

## <a name="installing-the-oracle-client"></a>Installieren des Oracle-Clients
- Laden Sie den [32-Bit-Oracle-Client](https://www.oracle.com/technetwork/topics/dotnet/utilsoft-086879.html) für die 32-Bit-Version von Power BI Desktop herunter, und installieren Sie ihn.

- Laden Sie den [64-Bit-Oracle-Client](https://www.oracle.com/technetwork/database/windows/downloads/index-090165.html) für die 64-Bit-Version von Power BI Desktop herunter, und installieren Sie ihn.

## <a name="connect-to-an-oracle-database"></a>Herstellen einer Verbindung mit einer Oracle-Datenbank
Nachdem Sie den entsprechenden Oracle-Clienttreiber installiert haben, können Sie eine Verbindung mit einer Oracle-Datenbank herstellen. Gehen Sie wie folgt vor, um die Verbindung herzustellen:

1. Klicken Sie auf der Registerkarte **Start** auf **Daten abrufen**. 

2. Wählen Sie im angezeigten Fenster **Daten abrufen** die Option **Mehr** aus (falls erforderlich), dann **Datenbank** > **Oracle-Datenbank**, und anschließend **Verbinden**.
   
   ![Verbindung „Oracle-Datenbank“](media/desktop-connect-oracle-database/connect-oracle-database_2.png)
2. Geben Sie im daraufhin angezeigten Dialogfeld **Oracle-Datenbank** den Namen des **Servers** ein, und wählen Sie **OK** aus. Wenn eine SID erforderlich ist, legen Sie sie über folgendes Format fest: *Servername/SID*, wobei *SID* dem eindeutigen Namen der Datenbank entspricht. Wenn das Format *Servername/SID* nicht funktioniert, verwenden Sie *Servername/Dienstname*, wobei *Dienstname* der beim Herstellen der Verbindung verwendete Alias ist.


   ![Oracle-Servername eingeben](media/desktop-connect-oracle-database/connect-oracle-database_3.png)

   > [!TIP]
   > Wenn Sie während dieses Schritts Probleme mit der Verbindung haben, verwenden Sie versuchsweise das folgenden Format im Feld **Server**: *(DESCRIPTION=(ADDRESS=(PROTOCOL=TCP)(HOST=host_name)(PORT=port_num))(CONNECT_DATA=(SERVICE_NAME=service_name)))*
   
3. Wenn Sie Daten mithilfe einer nativen Datenbankabfrage importieren möchten, fügen Sie Ihre Abfrage in das Feld **SQL-Anweisung** ein. Dieses wird angezeigt, wenn Sie im Dialogfeld **Oracle-Datenbank** die **Erweiterten Optionen** einblenden.
   
   ![„Erweiterte Optionen“ erweitern](media/desktop-connect-oracle-database/connect-oracle-database_4.png)
4. Nachdem Sie die erforderlichen Informationen in das Dialogfeld **Oracle-Datenbank** eingegeben haben (einschließlich aller optionalen Informationen wie SID oder nativer Datenbankabfrage), wählen Sie **OK** aus, um die Verbindung herzustellen.
5. Wenn für die Anmeldung bei der Oracle-Datenbank Anmeldeinformationen erforderlich sind, geben Sie diese bei Aufforderung in das Dialogfeld ein.


## <a name="troubleshooting"></a>Problembehandlung

Wenn Sie Power BI Desktop aus dem Microsoft Store heruntergeladen haben, können Sie möglicherweise aufgrund eines Problems mit dem Oracle-Treiber keine Verbindung zu Oracle-Datenbanken herstellen. Wenn dieses Problem auftritt, wird die folgende Fehlermeldung zurückgegeben: *Object reference not set* (Der Objektverweis ist nicht festgelegt). Führen Sie einen der folgenden Schritte aus, um das Problem zu beheben:

* Laden Sie Power BI Desktop aus dem [Download Center](https://www.microsoft.com/download/details.aspx?id=58494) herunter, anstatt vom Microsoft Store.

* Wenn Sie die Version aus dem Microsoft Store verwenden möchten: Kopieren Sie auf Ihrem lokalen Computer die Datei „oraons.dll“ von _12.X.X\client_X_ nach _12.X.X\client_X\bin_, wobei _X_ die Version und Verzeichnisnummern darstellt.

Wenn Ihnen im Power BI Gateway beim Herstellen einer Verbindung mit einer Oracle-Datenbank die Fehlermeldung *Object reference not set* (Der Objektverweis ist nicht festgelegt) angezeigt wird, befolgen Sie die Anweisungen im Artikel [Verwalten der Datenquelle – Oracle](service-gateway-onprem-manage-oracle.md).

Wenn Sie den Power BI-Berichtsserver verwenden möchten, finden Sie im Artikel [Oracle-Verbindungstyp ((Berichts-Generator und Power BI-Berichtsserver) | Microsoft-Dokumentation)](https://docs.microsoft.com/sql/reporting-services/report-data/oracle-connection-type-ssrs?view=sql-server-ver15) eine Anleitung.