---
title: Veröffentlichen aus Power BI Desktop
description: Veröffentlichen aus Power BI Desktop
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 01/15/2020
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: 3a67c36b2594696e1c576693cc5808eb0227c1c7
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/13/2020
ms.locfileid: "83333485"
---
# <a name="publish-datasets-and-reports-from-power-bi-desktop"></a>Veröffentlichen von Datasets und Berichten aus Power BI Desktop
Wenn Sie eine Power BI Desktop-Datei für den Power BI-Dienst veröffentlichen, veröffentlichen Sie die Daten im Modell in Ihrem Power BI-Arbeitsbereich. Dasselbe gilt für alle Berichte, die Sie in der Ansicht **Bericht** erstellt haben. Ein neues Dataset mit dem gleichen Namen und die jeweiligen Berichte werden im Navigationsbereich Ihres Arbeitsbereichs angezeigt.

Das Veröffentlichen aus Power BI Desktop hat die gleiche Auswirkung wie die Verwendung der Funktion zum **Abrufen von Daten** in Power BI, um eine Verbindung mit einer Power BI Desktop-Datei herzustellen und diese hochzuladen.

> [!NOTE]
> Alle Änderungen, die Sie in Power BI am Bericht vornehmen, werden nicht in der ursprünglichen Power BI Desktop-Datei gespeichert. Dazu zählen auch das Hinzufügen, Löschen oder Ändern von Visualisierungen in Berichten.
> 
> 

## <a name="to-publish-a-power-bi-desktop-dataset-and-reports"></a>So veröffentlichen Sie ein Power BI Desktop-Dataset und die zugehörigen Berichte
1. Wählen Sie in Power BI Desktop die Optionen **Datei** \> **Veröffentlichen** \> **In Power BI veröffentlichen** aus, oder klicken Sie im Menüband auf **Veröffentlichen**.  

   ![Schaltfläche „Veröffentlichen“](media/desktop-upload-desktop-files/pbid_publish_publishbutton.png)

2. Melden Sie sich bei Power BI an.
3. Wählen Sie die Zieladresse aus.

   ![Wählen Sie ein Veröffentlichungsziel aus.](media/desktop-upload-desktop-files/pbid_publish_select_destination.png)

Wenn die Veröffentlichung abgeschlossen ist, erhalten Sie einen Link zu Ihrem Bericht. Klicken Sie darauf, um den Bericht auf Ihrer Power BI-Website zu öffnen.

![Dialogfeld „Veröffentlichung erfolgreich“](media/desktop-upload-desktop-files/pbid_publish_success.png)

## <a name="republish-or-replace-a-dataset-published-from-power-bi-desktop"></a>Erneutes Veröffentlichen oder Ersetzen eines über Power BI Desktop veröffentlichten Datasets
Wenn Sie eine Power BI Desktop-Datei veröffentlichen, werden das Dataset und alle in Power BI Desktop erstellten Berichte auf Ihre Power BI-Website hochgeladen. Wenn Sie Ihre Power BI Desktop-Datei noch mal veröffentlichen, wird das Dataset auf der Power BI-Website durch das aktualisierte Dataset aus der Power BI Desktop-Datei ersetzt.

Der Vorgang ist unkompliziert, jedoch sollten Sie über folgende Punkte Bescheid wissen:

* Das Veröffentlichen kann fehlschlagen, wenn Sie in Power BI bereits über zwei oder mehr Datasets verfügen, die den gleichen Namen wie die Power BI Desktop-Datei haben. Stellen Sie sicher, dass in Power BI nur ein Dataset mit dem gleichen Namen vorhanden ist. Sie können die Datei auch umbenennen und veröffentlichen, um ein neues Dataset mit dem gleichen Namen wie die Datei zu erstellen.
* Wenn Sie eine Spalte oder ein Measure umbenennen oder löschen, können Fehler für Visualisierungen auftreten, die in Power BI bereits mit diesem Feld vorhanden sind. 
* Power BI ignoriert einige Formatänderungen vorhandener Spalten. Beispiel: Sie ändern das Format einer Spalte von 0,25 in 25 %.
* Angenommen, für das in Power BI vorhandene Dataset ist ein Aktualisierungszeitplan konfiguriert. Wenn Sie der Datei neue Datenquellen hinzufügen und sie dann noch mal veröffentlichen, müssen Sie sich vor der nächsten geplanten Aktualisierung in den Datenquellen anmelden.
* Wenn Sie ein aus Power BI Desktop veröffentlichtes Dataset noch mal veröffentlichen und einen Aktualisierungszeitplan festgelegt haben, wird nach der erneuten Veröffentlichung eine Aktualisierung des Datasets initiiert. 

