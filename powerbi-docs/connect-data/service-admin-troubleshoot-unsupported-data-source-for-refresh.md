---
title: Problembehandlung bei nicht unterstützter Datenquelle für die Aktualisierung
description: Problembehandlung bei nicht unterstützter Datenquelle für die Aktualisierung
author: maggiesMSFT
ms.reviewer: kayu
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: troubleshooting
ms.date: 05/08/2020
ms.author: maggies
ms.custom: seodec18
LocalizationGroup: Troubleshooting
ms.openlocfilehash: 50eb4f0fd50c49a39363093ea600922c61ebfab4
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/13/2020
ms.locfileid: "83324124"
---
# <a name="troubleshooting-unsupported-data-source-for-refresh"></a>Problembehandlung bei nicht unterstützter Datenquelle für die Aktualisierung
Bei der Konfiguration eines Datasets für die planmäßige Aktualisierung kann ein Fehler angezeigt werden.

        You cannot schedule refresh for this dataset because it gets data from sources that currently don’t support refresh.

Dies geschieht, wenn die innerhalb von Power BI-Desktop verwendete Datenquelle für die Aktualisierung nicht unterstützt wird. Sie müssen die von Ihnen verwendete Datenquelle suchen und mit der Liste der unterstützten Datenquellen unter [Aktualisieren von Daten in Power BI](refresh-data.md) vergleichen. 

## <a name="find-the-data-source"></a>Suchen der Datenquelle
Wenn Sie unsicher sind, welche Datenquelle verwendet wurde, können Sie diese suchen, indem Sie die folgenden Schritte in Power BI Desktop ausführen.  

1. Vergewissern Sie sich in Power BI Desktop, dass Sie sich im **Berichtsbereich** befinden.  
   ![Power BI Desktop-Berichtsbereich](media/service-admin-troubleshoot-unsupported-data-source-for-refresh/tshoot-report-pane.png)
2. Wählen Sie im Menüband die Option **Abfragen bearbeiten** aus.  
   ![Abfragen bearbeiten](media/service-admin-troubleshoot-unsupported-data-source-for-refresh/tshoot-edit-queries.png)
3. Wählen Sie **Erweiterter Editor**aus.  
   ![Erweiterter Editor](media/service-admin-troubleshoot-unsupported-data-source-for-refresh/tshoot-advanced-editor.png)
4. Notieren Sie sich den für die Datenquelle aufgeführten Anbieter.  In diesem Beispiel ist der Anbieter Active Directory.  
   ![Datenquellenanbieter](media/service-admin-troubleshoot-unsupported-data-source-for-refresh/tshoot-provider.png)
5. Vergleichen Sie den Anbieter mit der Liste der unterstützten Datenquellen, die in [Power BI-Datenquellen](power-bi-data-sources.md) gefunden wurden.

> [!NOTE]
> Weitere Informationen zu Aktualisierungsproblemen im Zusammenhang mit dynamischen Datenquellen, einschließlich Datenquellen, die manuell erstellte Abfragen einschließen, finden Sie unter [Aktualisieren von dynamischen Datenquellen](refresh-data.md#refresh-and-dynamic-data-sources).


## <a name="next-steps"></a>Nächste Schritte
[Datenaktualisierung](refresh-data.md)  
[Power BI Gateway – Personal](service-gateway-personal-mode.md)  
[On-premises data gateway (Lokales Datengateway)](service-gateway-onprem.md)  
[Problembehandlung beim lokalen Datengateway](service-gateway-onprem-tshoot.md)  
[Problembehandlung für Power BI Gateway – Personal](service-admin-troubleshooting-power-bi-personal-gateway.md)  

Weitere Fragen? [Stellen Sie Ihre Frage in der Power BI-Community.](https://community.powerbi.com/)
