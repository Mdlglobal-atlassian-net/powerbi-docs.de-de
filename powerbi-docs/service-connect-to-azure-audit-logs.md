---
title: "Herstellen einer Verbindung mit Azure-Überwachungsprotokollen mithilfe von Power BI"
description: "Azure-Überwachungsprotokolle für Power BI"
services: powerbi
documentationcenter: 
author: SarinaJoan
manager: kfile
backup: maggiesMSFT
editor: 
tags: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 02/06/2018
ms.author: sarinas
ms.openlocfilehash: 1116da997123b29313a7614a3911f4b24c577dd8
ms.sourcegitcommit: c24e5d7bd1806e0d637e974b5143ab5125298fc6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/19/2018
---
# <a name="connect-to-azure-audit-logs-with-power-bi"></a>Herstellen einer Verbindung mit Azure-Überwachungsprotokollen mithilfe von Power BI
Mit dem Azure-Überwachungsprotokoll-Inhaltspaket können Sie die in den Überwachungsprotokollen gespeicherten Informationen analysieren und visualisieren. Power BI ruft Ihre Daten ab und erstellt ein Standard-Dashboard sowie Berichte basierend auf diesen Daten.

Stellen Sie eine Verbindung mit dem [Azure-Überwachungsprotokoll-Inhaltspaket](https://app.powerbi.com/getdata/services/azure-audit-logs) her, oder informieren Sie sich über die [Integration von Azure-Überwachungsprotokollen](https://powerbi.microsoft.com/integrations/azure-audit-logs) in Power BI.

## <a name="how-to-connect"></a>Herstellen der Verbindung
1. Wählen Sie unten im linken Navigationsbereich **Daten abrufen** aus.  
   
    ![](media/service-connect-to-azure-audit-logs/getdata.png)
2. Wählen Sie im Feld **Dienste** die Option **Abrufen**aus.  
   
    ![](media/service-connect-to-azure-audit-logs/services.png) 
3. Wählen Sie **Azure-Überwachungsprotokolle**  >  **Abrufen** aus.  
   
   ![](media/service-connect-to-azure-audit-logs/azureauditlogs.png)
4. Wenn Sie dazu aufgefordert werden, geben Sie Ihre **Azure-Abonnement-ID**ein. Informationen zum Suchen Ihrer [Abonnement-ID](#FindingParams) finden Sie weiter unten.   
   
    ![](media/service-connect-to-azure-audit-logs/parameters.png)
5. Wählen Sie als **Authentifizierungsmethode** die Option **oAuth2** \> **Anmelden** aus.
   
    ![](media/service-connect-to-azure-audit-logs/creds.png)
6. Geben Sie die Anmeldeinformationen für Ihr Konto ein, um den Anmeldevorgang abzuschließen.
   
    ![](media/service-connect-to-azure-audit-logs/login.png)
7. Power BI ruft Ihre Azure-Überwachungsprotokolldaten ab und erstellt für Sie ein gebrauchsfertiges Dashboard und einen Bericht. 
   
    ![](media/service-connect-to-azure-audit-logs/dashboard.png)

**Was nun?**

* Versuchen Sie, am oberen Rand des Dashboards [im Q&A-Feld eine Frage zu stellen](power-bi-q-and-a.md).
* [Ändern Sie die Kacheln](service-dashboard-edit-tile.md) im Dashboard.
* [Wählen Sie eine Kachel aus](service-dashboard-tiles.md), um den zugrunde liegenden Bericht zu öffnen.
* Ihr Dataset ist auf eine tägliche Aktualisierung festgelegt. Sie können jedoch das Aktualisierungsintervall ändern oder es über **Jetzt aktualisieren** nach Bedarf aktualisieren.

## <a name="system-requirements"></a>Systemanforderungen
Das Azure-Überwachungsprotokolle-Inhaltspaket erfordert Zugriff auf Überwachungsprotokolle im Azure-Portal. Weitere Informationen finden Sie [hier](https://azure.microsoft.com/documentation/articles/insights-debugging-with-events/).

<a name="FindingParams"></a>

## <a name="finding-parameters"></a>Suchen von Parametern
Es gibt zwei einfache Möglichkeiten, Ihre Abonnement-ID zu suchen.

1. Über „https://portal.azure.com“ &gt; „Durchsuchen“ &gt; „Abonnements“ &gt; „Abonnement-ID“
2. Über „https://manage.windowsazure.com“ &gt; „Einstellungen“ &gt; „Abonnement-ID“

Ihre Abonnement-ID besteht aus einer langen Abfolge von Zahlen und Zeichen, ähnlich wie in dem Beispiel in Schritt 4 oben. 

## <a name="troubleshooting"></a>Problembehandlung
Wenn ein Fehler aufgrund der Anmeldeinformationen oder beim Versuch der Aktualisierung aufgrund ungültiger Anmeldeinformationen angezeigt wird, löschen Sie alle Instanzen der Azure-Überwachungsprotokolle, und stellen Sie die Verbindung erneut her.

## <a name="next-steps"></a>Nächste Schritte
[Erste Schritte mit Power BI](service-get-started.md)  
[Power BI – Grundkonzepte](service-basic-concepts.md)  
