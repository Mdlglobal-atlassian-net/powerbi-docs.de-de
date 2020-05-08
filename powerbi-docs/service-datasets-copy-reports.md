---
title: Kopieren von Berichten aus anderen Apps oder Arbeitsbereichen (Vorschau) – Power BI
description: Erfahren Sie, wie Sie eine Kopie eines Berichts erstellen und in Ihrem eigenen Arbeitsbereich speichern.
author: maggiesMSFT
ms.reviewer: chbraun
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 01/16/2020
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: 8716a304e5b117c027d75db149ebcc8d95efebfe
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "76268869"
---
# <a name="copy-reports-from-other-workspaces-preview"></a>Kopieren von Berichten aus anderen Arbeitsbereichen (Vorschau)

Wenn Sie in einem Arbeitsbereich oder einer App einen Bericht gefunden haben, der Ihnen gefällt, können Sie eine Kopie davon erstellen und sie in einem anderen Arbeitsbereich speichern. Anschließend können Sie Ihre Kopie des Berichts ändern und Visuals und andere Elemente hinzufügen oder löschen. Sie brauchen sich nicht mit der Erstellung des Datenmodells abzugeben. Das wurde bereits für Sie erstellt. Und es ist viel einfacher, einen vorhandenen Bericht zu ändern, als einen von Grund auf neuen zu erstellen. Wenn Sie jedoch eine App aus Ihrem Arbeitsbereich erstellen, können Sie Ihre Kopie des Berichts manchmal nicht in der App veröffentlichen. Weitere Informationen finden Sie im Abschnitt [„Überlegungen und Einschränkungen“ im Artikel „Verwenden von Datasets in mehreren Arbeitsbereichen“](service-datasets-across-workspaces.md#considerations-and-limitations).

> [!NOTE]
> Selbst wenn sich der ursprüngliche Bericht in einem Arbeitsbereich in einer Premium-Kapazität befindet, benötigen Sie eine Pro-Lizenz, um eine Kopie zu erstellen.

## <a name="save-a-copy-of-a-report-in-a-workspace"></a>Speichern der Kopie eines Berichts in einem Arbeitsbereich

1. Navigieren Sie in einem Arbeitsbereich zur Listenansicht „Berichte“.

    ![Listenansicht „Berichte“](media/service-datasets-copy-reports/power-bi-report-list-view.png)

1. Wählen Sie unter **Aktionen** **Kopie speichern** aus.

    ![Speichern einer Kopie eines Berichts](media/service-datasets-copy-reports/power-bi-dataset-save-report-copy.png)

    Sie sehen nur das Symbol **Kopie speichern**, wenn sich der Bericht in einem Arbeitsbereich mit neuer Benutzeroberfläche befindet und Sie über die [Berechtigung „Erstellen“](service-datasets-build-permissions.md) verfügen. Selbst wenn Sie Zugriff auf den Arbeitsbereich haben, benötigen Sie für das Dataset die Berechtigung „Erstellen“.

3. Geben Sie dem Bericht in **Eine Kopie dieses Berichts speichern** einen Namen, und wählen Sie den Zielarbeitsbereich aus.

    ![Kopie speichern (Dialogfeld)](media/service-datasets-copy-reports/power-bi-dataset-save-report.png)

    Sie können den Bericht im aktuellen Arbeitsbereich oder einem anderen im Power BI-Dienst speichern. Sie sehen nur Arbeitsbereiche mit neuer Benutzeroberfläche, bei denen Sie Mitglied sind. 
  
4. Wählen Sie **Speichern**.

    Power BI erstellt automatisch eine Kopie des Berichts und einen Eintrag in der Liste der Datasets, wenn der Bericht auf einem Dataset außerhalb des Arbeitsbereichs basiert. Das Symbol für ein solches Dataset unterscheidet sich vom Symbol für Datasets im Arbeitsbereich: ![Symbol „Freigegebenes Dataset“](media/service-datasets-discover-across-workspaces/power-bi-shared-dataset-icon.png)
    
    Auf diese Weise können Mitglieder des Arbeitsbereichs erkennen, welche Berichte und Dashboards Datasets verwenden, die sich außerhalb des Arbeitsbereichs befinden. Der Eintrag zeigt Informationen über das Dataset und einige ausgewählte Aktionen an.

    ![Datasetaktionen](media/service-datasets-across-workspaces/power-bi-dataset-actions.png)

    Informationen zum Bericht und zum zugehörigen Dataset finden Sie im Abschnitt [Ihre Kopie des Berichts](#your-copy-of-the-report) des vorliegenden Artikels.

## <a name="copy-a-report-in-an-app"></a>Kopieren eines Berichts in eine App

1. Öffnen Sie in einer App den Bericht, den Sie kopieren möchten.
2. Wählen Sie in der Menüleiste **Weitere Optionen** ( **...** ) > **Kopie speichern** aus.

    ![Speichern einer Kopie des Berichts](media/service-datasets-copy-reports/power-bi-save-copy.png)

    Die Option **Kopie speichern** wird nur angezeigt, wenn sich der Bericht in einem Arbeitsbereich mit der neuen Benutzeroberfläche befindet und Sie über die [Berechtigung „Erstellen“](service-datasets-build-permissions.md) verfügen.

3. Benennen Sie den Bericht, und klicken Sie auf **Speichern**.

    ![Benennen Ihrer Kopie des Berichts](media/service-datasets-copy-reports/power-bi-save-report-from-app.png)

    Ihre Kopie wird automatisch in Ihrem Arbeitsbereich gespeichert.

4. Klicken Sie auf **Gehe zu Bericht**, um Ihre Kopie zu öffnen.

## <a name="your-copy-of-the-report"></a>Ihre Kopie des Berichts

Wenn Sie eine Kopie des Berichts speichern, erstellen Sie eine Liveverbindung zum Dataset, und Sie können die Oberfläche zur Berichterstellung öffnen und haben das gesamte Dataset zur Verfügung. 

![Bearbeiten Ihrer Kopie des Berichts](media/service-datasets-copy-reports/power-bi-edit-report-copy.png)

Sie haben keine Kopie des Datasets erstellt. Das Dataset befindet sich weiterhin an seinem ursprünglichen Speicherort. Sie können alle im Dataset enthaltenen Tabellen und Measures in Ihrem eigenen Bericht verwenden. Es gelten Einschränkungen durch Sicherheit auf Zeilenebene (Row-Level Security, RLS) für das Dataset, sodass Sie nur Daten sehen können, zu deren Anzeige Sie gemäß Ihrer RLS-Rolle berechtigt sind.

## <a name="view-related-datasets"></a>Zugehörige Datasets anzeigen

Wenn ein Bericht in einem Arbeitsbereich auf einem Dataset in einem anderen Arbeitsbereich basiert, müssen Sie möglicherweise mehr über das zugrunde liegende Dataset wissen.

1. Wählen Sie in der Listenansicht der Berichte **Verwandte Inhalte anzeigen** aus.

    ![„Verwandte Inhalte anzeigen“](media/service-datasets-copy-reports/power-bi-dataset-view-related.png)

1. Im Dialogfeld **Verwandte Inhalte** werden alle verwandten Elemente angezeigt. In dieser Liste sieht das Dataset aus wie jedes andere. Es lässt sich nicht feststellen, dass es in einem anderen Arbeitsbereich gespeichert ist. Dieses Problem ist bekannt.
 
    ![Verwandte Inhalte (Dialogfeld)](media/service-datasets-copy-reports/power-bi-dataset-related.png)

## <a name="delete-a-report-and-its-shared-dataset"></a>Löschen eines Berichts und seines freigegebenen Datasets

Sie können sich entscheiden, dass Sie den Bericht und sein zugehöriges freigegebenes Dataset nicht mehr im Arbeitsbereich benötigen.

1. Löschen Sie den Bericht. Wählen Sie in der Liste der Berichte im Arbeitsbereich das Symbol **Löschen** aus.

    ![Symbol „Bericht löschen“](media/service-datasets-across-workspaces/power-bi-datasets-delete-report.png)

2. In der Liste der Datasets können Sie sehen, dass es für die freigegebenen Datasets kein Symbol **Löschen** gibt. Aktualisieren Sie die Seite, oder wechseln Sie zu einer anderen Seite, und kehren Sie dann zurück. Das Dataset ist nicht mehr vorhanden. Überprüfen Sie andernfalls **Verwandte Inhalte anzeigen**. Es hat möglicherweise einen Bezug zu einer anderen Tabelle in Ihrem Arbeitsbereich.

    ![„Verwandte Inhalte anzeigen“](media/service-datasets-across-workspaces/power-bi-dataset-view-related-icon.png)

    > [!NOTE]
    > Durch das Löschen des freigegebenen Datasets in diesem Arbeitsbereich wird das Dataset nicht gelöscht. Es löscht nur den Verweis darauf.


## <a name="next-steps"></a>Weitere Schritte

- [Verwenden von Datasets in mehreren Arbeitsbereichen (Vorschau)](service-datasets-across-workspaces.md)
- Fragen? [Stellen Sie Ihre Frage in der Power BI-Community.](https://community.powerbi.com/)
