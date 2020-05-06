---
title: Löschen eines Dashboards, eines Berichts, einer Arbeitsmappe, eines Datasets oder eines Arbeitsbereichs
description: Erfahren Sie, wie Sie beliebige Elemente aus Power BI löschen können.
author: maggiesMSFT
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 09/11/2018
ms.author: maggies
LocalizationGroup: Common tasks
ms.openlocfilehash: 0ccc32a18098673034e7f37b92f8edb5636ef21d
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "73872543"
---
# <a name="delete-almost-anything-in-power-bi-service"></a>Löschen beliebiger Elemente aus dem Power BI-Dienst
In diesem Artikel wird erläutert, wie Sie ein Dashboard, einen Bericht, eine Arbeitsmappe, ein Dataset, eine App, eine Visualisierung oder einen Arbeitsbereich im Power BI-Dienst löschen.

## <a name="delete-a-dashboard"></a>Löschen eines Dashboards
Dashboards können entfernt werden. Beim Entfernen des Dashboards werden nicht das zugrunde liegende Dataset und keine mit diesem Dashboard verknüpften Berichte gelöscht.

* Wenn Sie der Besitzer des Dashboards sind, können Sie es entfernen. Wenn Sie das Dashboard für Kollegen freigegeben haben und es aus Ihrem Power BI-Arbeitsbereich entfernen, wird es auch aus dem Power BI-Arbeitsbereich der Kollegen entfernt.
* Wenn ein Dashboard für Sie freigegeben ist und Sie es nicht mehr länger anzeigen möchten, können Sie es entfernen.  Das Entfernen eines Dashboards entfernt es nicht aus dem Power BI-Arbeitsbereich aller anderen Personen.
* Wenn ein Dashboard zu einem [organisationsbezogenen Inhaltspaket](service-organizational-content-pack-disconnect.md) gehört, ist die einzige Möglichkeit zum Entfernen das Entfernen des verknüpften Datasets.

### <a name="to-delete-a-dashboard"></a>So löschen Sie ein Dashboard
1. Wählen Sie im Arbeitsbereich die Registerkarte **Dashboards** aus.
2. Suchen Sie das zu löschende Dashboard, und klicken Sie auf „Löschen“. ![Symbol „Löschen“](media/service-delete/power-bi-delete-icon.png).

    ![Video](media/service-delete/power-bi-delete-dash.gif)

## <a name="delete-a-report"></a>Löschen eines Berichts
Keine Sorge, das Löschen eines Berichts löscht nicht das Dataset, auf dem der Bericht basiert.  Und alle Visualisierungen, die Sie aus dem Bericht angeheftet haben, sind auch sicher – sie bleiben auf dem Dashboard, bis Sie sie einzeln löschen.

### <a name="to-delete-a-report"></a>So löschen Sie einen Bericht
1. Wählen Sie in Ihrem Arbeitsbereich die Registerkarte **Berichte** aus.
2. Suchen Sie den zu löschenden Bericht, und wählen Sie das Symbol „Löschen“ aus.   ![Symbol „Löschen“](media/service-delete/power-bi-delete-icon.png).   

    ![Registerkarte „Berichte“ eines Arbeitsbereichs](media/service-delete/power-bi-delete-reportnew.png)
3. Bestätigen Sie den Löschvorgang.

   ![Dialogfeld „Bericht löschen“](media/service-delete/power-bi-delete-report.png)

   > [!NOTE]
   > Ist der Bericht Teil eines [Inhaltspakets](service-organizational-content-pack-introduction.md), können Sie ihn mit dieser Methode nicht löschen.  Siehe [Entfernen der Verbindung mit einem organisationsbezogenen Inhaltspaket in Power BI](service-organizational-content-pack-disconnect.md).
   >
   >

## <a name="delete-a-workbook"></a>Löschen einer Arbeitsmappe
Arbeitsmappen können entfernt werden. Durch das Entfernen einer Arbeitsmappe werden jedoch auch alle Berichte und Dashboardkacheln, die Daten aus dieser Arbeitsmappe enthalten, entfernt.

Wenn die Arbeitsmappe auf OneDrive for Business gespeichert ist, wird Sie durch das Löschen aus Power BI nicht aus OneDrive gelöscht.

### <a name="to-delete-a-workbook"></a>So löschen Sie eine Arbeitsmappe
1. Wählen Sie in Ihrem Arbeitsbereich die Registerkarte **Arbeitsmappen** aus.
2. Suchen Sie die zu löschende Arbeitsmappe, und wählen Sie das Symbol zum Löschen  ![Symbol „Löschen“](media/service-delete/power-bi-delete-report2.png) klicken.

    ![Registerkarte „Arbeitsmappe“](media/service-delete/power-bi-delete-workbooknew.png)
3. Bestätigen Sie den Löschvorgang.

   ![Dialogfeld „Arbeitsmappe entfernen“](media/service-delete/power-bi-delete-confirm.png)

## <a name="delete-a-dataset"></a>Löschen eines Datasets
Datasets können gelöscht werden. Durch das Löschen eines Datasets werden jedoch auch alle Berichte und Dashboardkacheln, die Daten aus diesem Dataset enthalten, gelöscht.

Wenn ein Dataset einem oder mehreren [organisationsbezogenen Inhaltspaketen](service-organizational-content-pack-disconnect.md) angehört, kann es nur gelöscht werden, indem Sie es aus den Inhaltspaketen, in denen es verwendet wird, entfernen, warten, bis es verarbeitet wurde, und dann erneut versuchen, es zu löschen.

### <a name="to-delete-a-dataset"></a>So löschen Sie ein Dataset
1. Wählen Sie in Ihrem Arbeitsbereich die Registerkarte **Datasets** aus.
2. Suchen Sie das zu löschende Dataset, und wählen Sie **Weitere Optionen** (...) aus.  

    ![Registerkarte „Datasets“](media/service-delete/power-bi-delete-datasetnew.png)
3. Wählen Sie in der Dropdownliste **Löschen** aus.

   ![Das Menü mit Auslassungspunkten (...)](media/service-delete/power-bi-delete-datasetnew2.png)
4. Bestätigen Sie den Löschvorgang.

   ![Dialogfeld „Dashboard löschen“](media/service-delete/power-bi-delete-dataset-confirm.png)

## <a name="delete-a-workspace"></a>Löschen eines Arbeitsbereichs
> [!WARNING]
> Wenn Sie einen Arbeitsbereich erstellen, erstellen Sie eine Office 365-Gruppe. Und wenn Sie einen Arbeitsbereich löschen, löschen Sie die entsprechende Office 365-Gruppe. Dies bedeutet, dass die Gruppe auch aus anderen Office 365-Produkten, z.B. SharePoint und Microsoft-Teams, gelöscht wird.
>
>

Wenn Sie der Ersteller eines Arbeitsbereichs sind, können Sie ihn löschen. Beim Löschen des App-Arbeitsbereichs wird auch die zugeordnete App für alle Gruppenmitglieder gelöscht und aus AppSource entfernt, sofern Sie die App für die gesamte Organisation veröffentlicht haben. Das Löschen eines Arbeitsbereichs unterscheidet sich vom Verlassen eines Arbeitsbereichs.

### <a name="to-delete-a-workspace---if-you-are-an-admin"></a>So löschen Sie als Administrator einen Arbeitsbereich
1. Wählen Sie im Navigationsbereich **Arbeitsbereiche** aus.

2. Wählen Sie **Weitere Optionen** (...) rechts neben dem zu löschenden Arbeitsbereich und dann **Arbeitsbereich bearbeiten** aus.

    ![Arbeitsbereiche](media/service-delete/power-bi-delete-workspace.png)

3. Wählen Sie im Fenster **Arbeitsbereich bearbeiten** die Option **Arbeitsbereich löschen** > **Löschen** aus.

    ![Arbeitsbereich löschen](media/service-delete/power-bi-delete-workspace2.png)

### <a name="to-remove-a-workspace-from-your-list"></a>So entfernen Sie einen Arbeitsbereich aus der Liste
Wenn Sie einem Arbeitsbereich nicht mehr als Mitglied angehören möchten, können Sie ihn ***verlassen***. Er wird dann aus der Liste entfernt. Wenn Sie einen Arbeitsbereich verlassen, bleibt er für alle anderen Mitglieder des Arbeitsbereichs erhalten.  

> [!IMPORTANT]
> Wenn Sie der einzige Administrator des Arbeitsbereichs sind, können Sie ihn in Power BI nicht verlassen.
>
>

1. Wechseln Sie zu dem Arbeitsbereich, den Sie entfernen möchten.

2. Wählen Sie in der rechten oberen Ecke **Weitere Optionen** (...) und dann **Arbeitsbereich verlassen** > **Verlassen** aus.

      ![Arbeitsbereich verlassen](media/service-delete/power-bi-leave-workspace.png)

   > [!NOTE]
   > Die in der Dropdownliste angezeigten Optionen hängen davon ab, ob Sie Administrator oder Mitglied des Arbeitsbereichs sind.
   >
   >

## <a name="delete-or-remove-an-app"></a>Löschen oder Entfernen einer App
Apps können problemlos von der Seite mit der Liste der Apps entfernt werden. Jedoch kann nur ein App-Administrator eine App endgültig löschen.

### <a name="remove-an-app-from-your-app-list-page"></a>Entfernen einer App von der Seite mit der Liste der Apps
Wenn Sie eine App von der Seite mit der Liste der Apps löschen, wird sie nicht für andere Mitglieder gelöscht.

1. Wählen Sie im Navigationsbereich **Apps** aus, um die Seite mit der Liste der Apps zu öffnen.
2. Zeigen Sie auf die zu löschende App, und wählen Sie das Symbol „Löschen“ ![](media/service-delete/power-bi-delete-report2.png) aus.

   ![Apps auswählen](media/service-delete/power-bi-delete-app.png)

   Wenn Sie eine App versehentlich entfernen, stehen Ihnen mehrere Optionen zur Verfügung, um sie wieder zu erhalten.  Sie können den Ersteller der App bitten, sie erneut zu senden, Sie können die ursprüngliche E-Mail mit dem Link zur App suchen, Sie können in der [Mitteilungszentrale](service-notification-center.md) überprüfen, ob die Benachrichtigung für die App noch aufgeführt ist, oder Sie können [AppSource](consumer/end-user-apps.md) für Ihre Organisation überprüfen.

## <a name="considerations-and-troubleshooting"></a>Zu beachtende Aspekte und Problembehandlung
In diesem Artikel wird das Löschen der Grundkomponenten des Power BI-Diensts beschrieben. Es gibt jedoch noch weitere Komponenten in Power BI, die Sie löschen können.  

* [Entfernen eines ausgewählten Dashboards](service-dashboard-featured.md)
* [Entfernen eines Dashboards aus den Favoriten](service-dashboard-favorite.md)
* [Löschen einer Berichtsseite](service-delete.md)
* [Löschen einer Dashboardkachel](service-dashboard-edit-tile.md)
* [Löschen einer Berichtsvisualisierung](service-delete.md)

Weitere Fragen? [Wenden Sie sich an die Power BI-Community](https://community.powerbi.com/)
