---
title: Eingebettete Datenquellen für paginierte Berichte im Power BI-Dienst
description: In diesem Artikel erfahren Sie, wie eine eingebettete Datenquelle in einem paginierten Bericht im Power BI-Dienst erstellt und geändert wird.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.date: 03/02/2020
ms.openlocfilehash: 1d7b355987163ede2c70a4052e98ec02522db751
ms.sourcegitcommit: d65da4738f011beec8f4423085cbd483511cdfb0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/03/2020
ms.locfileid: "78237889"
---
# <a name="create-an-embedded-data-source-for-paginated-reports-in-the-power-bi-service"></a>Erstellen einer eingebetteten Datenquelle für paginierte Berichte im Power BI-Dienst

In diesem Artikel erfahren Sie, wie eine eingebettete Datenquelle für einen paginierten Bericht im Power BI-Dienst erstellt und geändert wird. Sie definieren eine eingebettete Datenquelle in einem einzelnen Bericht und verwenden sie nur in diesem Bericht. Derzeit sind für paginierte Berichte, die im Power BI-Dienst veröffentlicht werden, eingebettete Datasets und eingebettete Datenquellen erforderlich. Sie können eine Verbindung mit folgenden Datenquellen herstellen:

- Azure Analysis Services
- Azure SQL-Datenbank 
- Azure SQL Data Warehouse
- SQL Server
- SQL Server Analysis Services
- Oracle 
- Teradata 

Verwenden Sie für folgende Datenquellen die Option der [SQL Server Analysis Services-Verbindung](service-premium-connect-tools.md):

- Power BI Premium-Datasets

Paginierte Berichte stellen über ein [Power BI-Gateway](service-gateway-onprem.md) eine Verbindung mit lokalen Datenquellen her. Sie richten Sie das Gateway ein, nachdem Sie den Bericht im Power BI-Dienst veröffentlicht haben.

Ausführlichere Informationen finden Sie unter [Berichtsdaten im Power BI-Berichts-Generator](report-builder-data.md).

## <a name="create-an-embedded-data-source"></a>Erstellen einer eingebetteten Datenquelle
  
1. Öffnen Sie den Power BI-Berichts-Generator.

1. Wählen Sie auf der Symbolleiste im Berichtsdatenbereich **Neu** > **Datenquelle**. Das Dialogfeld **Datenquelleneigenschaften** wird geöffnet.

    ![Neue Datenquelle](media/paginated-reports-embedded-data-source/power-bi-paginated-new-data-source.png)
  
2.  Geben Sie im Textfeld **Name** einen Namen für die Datenquelle ein, oder übernehmen Sie den Standardnamen.  
  
3.  Wählen Sie **In meinem Bericht eingebettete Verbindung verwenden**.  
  
1.  Wählen Sie in der Liste **Verbindungstyp auswählen** einen Datenquellentyp aus. 

1.  Geben Sie mit einer der folgenden Methoden eine Verbindungszeichenfolge an:  
  
    -   Geben Sie die Verbindungszeichenfolge direkt im Textfeld **Verbindungszeichenfolge** ein. 
  
     -   Wählen Sie **Erstellen**, um das Dialogfeld **Verbindungseigenschaften** für die Datenquelle zu öffnen, die Sie in Schritt 2 ausgewählt haben.  
  
        Füllen Sie die Felder im Dialogfeld **Verbindungseigenschaften** dem Typ der Datenquelle entsprechend aus. Verbindungseigenschaften umfassen den Typ der Datenquelle, den Namen der Datenquelle und die zu verwendenden Anmeldeinformationen. Klicken Sie nach Angabe der Werte in diesem Dialogfeld auf **Verbindung testen**, um sicherzustellen, dass die Datenquelle verfügbar ist und die angegebenen Anmeldeinformationen richtig sind.  
  
4.  Wählen Sie **Anmeldeinformationen** aus.  
  
     Geben Sie die Anmeldeinformationen für diese Datenquelle ein. Der Besitzer der Datenquelle wählt den Typ der Anmeldeinformationen aus, die unterstützt werden. Weitere Informationen finden Sie unter [Angeben von Anmelde- und Verbindungsinformationen für Berichtsdatenquellen](https://docs.microsoft.com/sql/reporting-services/report-data/specify-credential-and-connection-information-for-report-data-sources).
  
5.  Wählen Sie **OK** aus.  
  
     Die Datenquelle wird im Berichtsdatenbereich angezeigt.  
     
## <a name="limitations-and-considerations"></a>Einschränkungen und Überlegungen

Für paginierte Berichte, die eine Verbindung mit Power BI-Datasets herstellen, gelten die Regeln für freigegebene Datasets in Power BI mit geringen Änderungen.  Halten Sie sich an folgende Regeln, um Benutzern paginierte Berichte mit Power BI-Datasets richtig anzuzeigen und sicherzustellen, dass die Sicherheit auf Zeilenebene (Row Level Security, RLS) aktiviert ist und für Ihre Besucher erzwungen wird:

### <a name="classic-apps-and-workspaces"></a>Klassische Apps und Arbeitsbereiche

- RDL-Datei im selben Arbeitsbereich wie das Dataset (derselbe Besitzer): Unterstützt
- RDL-Datei in einem anderen Arbeitsbereich als das Dataset (derselbe Besitzer): Unterstützt
- Freigegebene RDL-Datei: Jedem Benutzer, dem der Bericht angezeigt wird, muss auf Datasetebene die Leseberechtigung zugewiesen sein.
- Freigegebene App: Jedem Benutzer, dem der Bericht angezeigt wird, muss auf Datasetebene die Leseberechtigung zugewiesen sein.
- RDL-Datei im selben Arbeitsbereich wie das Dataset (anderer Benutzer): Unterstützt
- RDL-Datei in einem anderen Arbeitsbereich als das Dataset (anderer Benutzer): Jedem Benutzer, dem der Bericht angezeigt wird, muss auf Datasetebene die Leseberechtigung zugewiesen sein.
- Sicherheit auf Rollenebene: Jedem Benutzer, dem der Bericht angezeigt wird, muss auf Datasetebene die Leseberechtigung zugewiesen sein, um diese zu erzwingen.

### <a name="new-experience-apps-and-workspaces"></a>Neue Apps und Arbeitsbereiche

- RDL-Datei im selben Arbeitsbereich wie das Dataset: Unterstützt
- RDL-Datei in einem anderen Arbeitsbereich als das Dataset (derselbe Besitzer): Unterstützt
- Freigegebene RDL-Datei: Jedem Benutzer, dem der Bericht angezeigt wird, muss auf Datasetebene die Leseberechtigung zugewiesen sein.
- Freigegebene App: Jedem Benutzer, dem der Bericht angezeigt wird, muss auf Datasetebene die Leseberechtigung zugewiesen sein.
- RDL-Datei im selben Arbeitsbereich wie das Dataset (anderer Benutzer) – Unterstützt
- RDL-Datei in einem anderen Arbeitsbereich als das Dataset (anderer Benutzer): Jedem Benutzer, dem der Bericht angezeigt wird, muss auf Datasetebene die Leseberechtigung zugewiesen sein.
- Sicherheit auf Rollenebene: Jedem Benutzer, dem der Bericht angezeigt wird, muss auf Datasetebene die Leseberechtigung zugewiesen sein, um diese zu erzwingen.

## <a name="next-steps"></a>Nächste Schritte

- [Erstellen eines eingebetteten Datasets für einen paginierten Bericht im Power BI-Dienst](paginated-reports-create-embedded-dataset.md)
- [Was sind paginierte Berichte in Power BI Premium? (Vorschau)](paginated-reports-report-builder-power-bi.md)
