---
title: Verwalten des Datenspeichers in Ihren Arbeitsbereichen
description: Hier erfahren Sie, wie Sie den Datenspeicher in Ihrem individuellen oder allgemeinen Arbeitsbereich verwalten, um sicherzustellen, dass Sie weiterhin Berichte und Datasets veröffentlichen können.
author: maggiesMSFT
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 02/25/2020
ms.author: maggies
LocalizationGroup: Administration
ms.openlocfilehash: a29d1b4403487a92bfbd1e56d7be4cde5b39f70e
ms.sourcegitcommit: bfc2baf862aade6873501566f13c744efdd146f3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/13/2020
ms.locfileid: "83344340"
---
# <a name="manage-data-storage-in-power-bi-workspaces"></a>Verwalten des Datenspeichers in Power BI-Arbeitsbereichen

Hier erfahren Sie, wie Sie den Datenspeicher in Ihrem individuellen oder allgemeinen Arbeitsbereich so verwalten, dass Sie weiterhin Berichte und Datasets veröffentlichen können.

## <a name="capacity-limits"></a>Kapazitätsgrenzen

Speicherbegrenzungen im Arbeitsbereich hängen sowohl für „Mein Arbeitsbereich“ als auch für einen App-Arbeitsbereich davon ab, ob es sich um [gemeinsam genutzte oder Premium-Kapazität](../fundamentals/service-basic-concepts.md#capacities) handelt.

### <a name="shared-capacity-limits"></a>Beschränkungen bei gemeinsam genutzter Kapazität
Für Arbeitsbereiche mit gemeinsam genutzter Kapazität gilt Folgendes: 

- Es gilt eine Speicherbeschränkung von 100 GB pro Arbeitsbereich.
- Der Gesamtverbrauch für App-Arbeitsbereiche darf das Speicherlimit des Mandanten (10 GB multipliziert mit der die Anzahl von Pro-Lizenzen im Mandanten) nicht überschreiten.

### <a name="premium-capacity-limits"></a>Beschränkungen bei Premium-Kapazität
Für Arbeitsbereiche mit Premium-Kapazität gilt Folgendes:
- Es gilt eine Beschränkung von 100 TB pro Premium-Kapazität.
- Es gibt keine benutzerspezifische Speicherbeschränkung.

Informieren Sie sich über weitere Funktionen des [Power BI-Preismodells](https://powerbi.microsoft.com/pricing).

## <a name="whats-included-in-storage"></a>Was ist im Speicher enthalten?

Ihr Datenspeicher umfasst die eigenen Datasets und Excel-Berichte sowie die Elemente, die andere Benutzer für Sie freigegeben haben. Datasets sind alle Datenquellen, die Sie hochgeladen haben oder mit denen eine Verbindung hergestellt wurde. Zu diesen Datenquellen zählen die Dateien in Power BI Desktop und die von Ihnen verwendeten Excel-Arbeitsmappen. Folgende Elemente sind ebenfalls in der Datenkapazität enthalten:

* Excel-Bereiche, die an Dashboards angeheftet sind
* Lokale Reporting Services-Visualisierungen, die an Power BI-Dashboards angeheftet sind.
* Hochgeladene Bilder.

Die Größe des freigegebenen Dashboards hängt von den angehefteten Elementen ab. Wenn Sie beispielsweise Elemente aus zwei Berichten anheften, die auf zwei verschiedenen Datasets basieren, wird die Größe von beiden Datasets bestimmt.

<a name="manage"/>

## <a name="manage-items-you-own"></a>Verwalten Ihrer eigenen Elemente

Prüfen Sie den in Ihrem Power BI-Konto genutzten Datenspeicher, und verwalten Sie das Konto.

1. Wechseln Sie im linken Navigationsbereich zu **Mein Arbeitsbereich**, um den eigenen Speicher zu verwalten.
   
    ![Mein Arbeitsbereich](media/service-admin-manage-your-data-storage-in-power-bi/pbi_myworkspace.png)

2. Wählen Sie das Zahnradsymbol ![Zahnradsymbol](media/service-admin-manage-your-data-storage-in-power-bi/pbi_gearicon.png) in der rechten oberen Ecke \> **Persönlichen Speicher verwalten** aus.
   
    Die obere Leiste zeigt, wie viel Ihres Speicherlimits Sie verwendet haben.
   
    ![Speicherbegrenzung verwalten](media/service-admin-manage-your-data-storage-in-power-bi/pbi_persnlstorage.png)
   
    Die Datasets und Berichte werden auf zwei Registerkarten unterteilt:
   
    **In meinem Besitz:** Sie haben diese Berichte und Datasets in Ihr Power BI-Konto hochgeladen, darunter Dienstdatasets wie Salesforce und Dynamics CRM.  

    **Im Besitz anderer Benutzer:** Andere Benutzer haben diese Berichte und Datasets für Sie freigegeben.
1. Wählen Sie das Papierkorbsymbol aus, um ein Dataset oder einen Bericht zu löschen ![Papierkorbsymbol](media/service-admin-manage-your-data-storage-in-power-bi/pbi_deleteicon.png).

Bedenken Sie, dass Sie oder andere Benutzer über Berichte und Dashboards verfügen können, die auf einem Dataset basieren. Wenn Sie das Dataset löschen, funktionieren diese Berichte und Dashboards nicht mehr.

## <a name="manage-your-workspace"></a>Verwalten Ihres Arbeitsbereichs
1. Wählen Sie den Pfeil neben **Arbeitsbereiche** \> und den Namen des Arbeitsbereichs aus.
   
    ![Einen Arbeitsbereich auswählen](media/service-admin-manage-your-data-storage-in-power-bi/pbi_groupworkspaces.png)
2. Wählen Sie das Zahnradsymbol ![Zahnradsymbol](media/service-admin-manage-your-data-storage-in-power-bi/pbi_gearicon.png) in der rechten oberen Ecke \> **Gruppenspeicher verwalten** aus.
   
    Die obere Leiste zeigt, wie viel des Speicherlimits der Gruppe verwendet wurde.
   
    ![Den Speicher des Arbeitsbereichs verwalten](media/service-admin-manage-your-data-storage-in-power-bi/pbi_groupstorage.png)
   
    Die Datasets und Berichte werden auf zwei Registerkarten unterteilt:
   
    **In unserem Besitz:** Sie oder ein anderer Benutzer haben diese Berichte und Datasets in das Power BI-Konto der Gruppe hochgeladen, darunter Dienstdatasets wie Salesforce und Dynamics CRM.

    **Im Besitz anderer Benutzer:** Andere Benutzer haben diese Berichte und Datasets für Ihre Gruppe freigegeben.

3. Wählen Sie das Papierkorbsymbol aus, um ein Dataset oder einen Bericht zu löschen ![Papierkorbsymbol](media/service-admin-manage-your-data-storage-in-power-bi/pbi_deleteicon.png).
   
   > [!NOTE]
   > Bedenken Sie, dass Sie oder andere Benutzer in der Gruppe über Berichte und Dashboards verfügen können, die auf einem Dataset basieren. Wenn Sie das Dataset löschen, funktionieren diese Berichte und Dashboards nicht mehr.
   
   Jedes Mitglied eines Arbeitsbereichs, das über eine der Rollen „Administrator“, „Mitglied“ oder „Mitwirkender“ verfügt, ist zum Löschen von Datasets und Berichten im Arbeitsbereich berechtigt.

## <a name="dataset-limits"></a>Dataset-Beschränkungen
Es besteht eine Beschränkung von 1 GB pro Dataset, das in Power BI importiert wird. Wenn Sie sich für die Excel-Benutzeroberfläche entschieden haben, anstatt die Daten zu importieren, beträgt die Obergrenze für das Dataset 250 MB.

## <a name="what-happens-when-you-reach-a-limit"></a>Was geschieht, wenn Sie einen Grenzwert erreichen?
Wenn Sie den Grenzwert der Datenkapazität erreichen, werden entsprechende Hinweise des Diensts angezeigt. 

Wenn Sie das Zahnradsymbol ![Zahnradsymbol](media/service-admin-manage-your-data-storage-in-power-bi/pbi_gearicon.png)auswählen, sehen Sie einen roten Balken, der angibt, dass Sie Ihren Grenzwert der Datenkapazität überschritten haben.

![Speicherlimit wurde erreicht](media/service-admin-manage-your-data-storage-in-power-bi/manage-storage-limit.png)

Dieser Grenzwert wird auch unter **Persönlichen Speicher verwalten** angezeigt.

 ![Verwalten des persönlichen Speichers, Speicherbegrenzung erreicht](media/service-admin-manage-your-data-storage-in-power-bi/manage-storage-limit2.png)

 Wenn Sie versuchen, eine Aktion auszuführen, bei der einer der Grenzwerte erreicht wird, wird Ihnen eine entsprechende Meldung angezeigt. Sie können Ihren Speicher [verwalten](#manage), um die Speichermenge zu verringern und den Grenzwert zu unterschreiten.

 ![Ihr Speicherlimit wurde überschritten](media/service-admin-manage-your-data-storage-in-power-bi/powerbi-pro-over-limit.png)

 ## <a name="next-steps"></a>Nächste Schritte

 Weitere Fragen? [Stellen Sie Ihre Frage in der Power BI-Community.](https://community.powerbi.com/)
