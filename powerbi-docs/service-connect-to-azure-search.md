---
title: Herstellen einer Verbindung mit Azure Search mithilfe von Power BI
description: Azure Search für Power BI
author: SarinaJoan
ms.reviewer: maggiesMSFT
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: conceptual
ms.date: 08/29/2019
ms.author: sarinas
LocalizationGroup: Connect to services
ms.openlocfilehash: 511fb6674d84cc0d206fdb1807fcb9ebf9e41d30
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "73873100"
---
# <a name="connect-to-azure-search-with-power-bi"></a>Herstellen einer Verbindung mit Azure Search mithilfe von Power BI
Azure Search Traffic Analytics ermöglicht das Überwachen und Verstehen des Datenverkehrs zu Ihrem Azure Search-Dienst. Das Azure Search-Inhaltspaket für Power BI bietet detaillierte Einblicke in Ihre Suchdaten, einschließlich Suchen, Indizierung, Dienststatistiken und Latenz der letzten 30 Tage. Weitere Informationen finden Sie im [Azure-Blogbeitrag](https://azure.microsoft.com/blog/analyzing-your-azure-search-traffic/).

[!INCLUDE [include-short-name](./includes/service-deprecate-content-packs.md)]

Stellen Sie eine Verbindung mit dem [Azure Search-Inhaltspaket](https://app.powerbi.com/getdata/services/azure-search) für Power BI her.

## <a name="how-to-connect"></a>Herstellen der Verbindung
1. Wählen Sie unten im Navigationsbereich **Daten abrufen** aus.
   
   ![](media/service-connect-to-azure-search/pbi_getdata.png) 
2. Wählen Sie im Feld **Dienste** die Option **Abrufen**aus.
   
   ![](media/service-connect-to-azure-search/pbi_getservices.png) 
3. Wählen Sie **Azure Search** \> **Abrufen** aus.
   
   ![](media/service-connect-to-azure-search/azuresearch.png)
4. Geben Sie den Namen des Tabellenspeicherkontos an, in dem Ihre Azure Search-Analysen gespeichert werden.
   
   ![](media/service-connect-to-azure-search/params.png)
5. Wählen Sie **Schlüssel** als Authentifizierungsmechanismus aus, und geben Sie den Schlüssel Ihres Speicherkontos ein. Klicken Sie auf **Anmelden** , und starten Sie den Ladevorgang.
   
   ![](media/service-connect-to-azure-search/creds.png)
6. Nach Abschluss des Ladevorgangs werden im Navigationsbereich ein neues Dashboard, ein Bericht und ein Modell angezeigt. Wählen Sie das Dashboard aus, um die importierten Daten anzuzeigen.
   
    ![](media/service-connect-to-azure-search/dashboard2.png)

**Was nun?**

* Versuchen Sie, am oberen Rand des Dashboards [im Q&A-Feld eine Frage zu stellen](consumer/end-user-q-and-a.md).
* [Ändern Sie die Kacheln](service-dashboard-edit-tile.md) im Dashboard.
* [Wählen Sie eine Kachel aus](consumer/end-user-tiles.md), um den zugrunde liegenden Bericht zu öffnen.
* Zwar ist Ihr Dataset auf tägliche Aktualisierung festgelegt, jedoch können Sie das Aktualisierungsintervall ändern oder über **Jetzt aktualisieren** nach Bedarf aktualisieren.

## <a name="system-requirements"></a>Systemanforderungen
Das Azure Search-Inhaltspaket erfordert, dass Azure Search Traffic Analytics für das Konto aktiviert ist.

## <a name="troubleshooting"></a>Problembehandlung
Stellen Sie sicher, dass der Name des Speicherkontos zusammen mit dem Vollzugriffsschlüssel ordnungsgemäß angegeben wird. Der Name des Speicherkontos muss dem Konto entsprechen, das mit Azure Search Traffic Analytics konfiguriert ist.

## <a name="next-steps"></a>Nächste Schritte
[Was ist Power BI?](fundamentals/power-bi-overview.md)

[Grundlegende Konzepte für Designer im Power BI-Dienst](service-basic-concepts.md)

