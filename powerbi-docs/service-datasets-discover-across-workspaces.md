---
title: 'Erstellen von Berichten auf Grundlage von Datasets aus anderen Arbeitsbereichen (Vorschau): Power BI'
description: Erfahren Sie, wie Sie ein Dataset mit Benutzern in der gesamten Organisation teilen können. Dann können diese in ihren eigenen Arbeitsbereichen Berichte erstellen, die auf Ihrem Dataset basieren.
author: maggiesMSFT
ms.reviewer: chbraun
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 07/03/2019
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: 371507eb86e1b68225e9d66ee3a1363b0e163d4f
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "73877174"
---
# <a name="create-reports-based-on-datasets-from-different-workspaces-preview"></a>Erstellen von Berichten auf Grundlage von Datasets aus anderen Arbeitsbereichen (Vorschau)

Erfahren Sie, wie Sie in Ihren eigenen Arbeitsbereichen Berichte erstellen können, die auf Datasets in anderen Arbeitsbereichen basieren. Um einen Bericht auf einem vorhandenen Dataset aufzubauen, können Sie von Power BI Desktop oder vom Power BI-Dienst, Ihrem „Mein Arbeitsbereich“ oder einer [neuen Arbeitsbereichs-Benutzeroberfläche](service-create-the-new-workspaces.md) ausgehen.

- Im Power BI-Dienst: **Daten abrufen** > **Veröffentlichte Datasets**.
- In Power BI Desktop: **Daten abrufen** > **Power BI-Datasets**.

    ![Herstellen einer Verbindung mit einem vorhandenen Dataset](media/service-datasets-across-workspaces/power-bi-connect-dataset-pk.png)
   
In beiden Fällen beginnt die Oberfläche zur Datasetermittlung in diesem Dialogfeld, **Dataset für Berichterstellung auswählen**. Sie sehen alle Datasets, auf die Sie Zugriff haben, unabhängig von deren Speicherort:

![Auswählen eines Datasets](media/service-datasets-across-workspaces/power-bi-select-dataset.png)

Sie bemerken, dass das erste die Bezeichnung **Höher gestuft** aufweist. Wir kommen später unter [Suchen eines empfohlenen Datasets](#find-an-endorsed-dataset) weiter unten in diesem Artikel dazu.

Die Datasets, die in dieser Liste angezeigt werden, erfüllen mindestens eine der folgenden Bedingungen:

- Das Dataset befindet sich in einem der Arbeitsbereiche mit der neuen Arbeitsbereichsoberfläche, und Sie sind Mitglied des betreffenden Arbeitsbereichs. Weitere Informationen finden Sie unter [Überlegungen und Einschränkungen](service-datasets-across-workspaces.md#considerations-and-limitations).
- Sie besitzen die Erstellungsberechtigung für das Dataset, das sich in einem Arbeitsbereich mit der neuen Arbeitsbereichsoberfläche befindet.
- Das Dataset ist in Ihrem „Mein Arbeitsbereich“.

> [!NOTE]
> Wenn Sie ein kostenloser Benutzer sind, sehen Sie nur Datasets in Ihrem „Mein Arbeitsbereich“ und Datasets für die Sie die Erstellungsberechtigung besitzen und die sich in Arbeitsbereichen der Premium-Kapazität befinden.

Wenn Sie auf **Erstellen** klicken, stellen Sie eine Liveverbindung mit dem Dataset her, und die Oberfläche zur Berichterstellung wird geöffnet und stellt das Dataset in vollem Umfang zur Verfügung. Sie haben keine Kopie des Datasets erstellt. Das Dataset befindet sich weiterhin an seinem ursprünglichen Speicherort. Sie können alle im Dataset enthaltenen Tabellen und Measures zum Erstellen Ihres eigenen Berichts verwenden. Es gelten Einschränkungen durch Sicherheit auf Zeilenebene (Row-Level Security, RLS) für das Dataset, sodass Sie nur Daten sehen können, zu deren Anzeige Sie gemäß Ihrer RLS-Rolle berechtigt sind.

Sie können den Bericht im aktuellen Arbeitsbereich im Power BI-Dienst speichern oder ihn von Power BI Desktop aus in einem Arbeitsbereich veröffentlichen. Power BI erstellt automatisch einen Eintrag in der Liste der Datasets, wenn der Bericht auf einem Dataset basiert, das außerhalb des Arbeitsbereichs liegt. Das Symbol für ein solches Dataset unterscheidet sich vom Symbol für Datasets im Arbeitsbereich: ![Symbol „Freigegebenes Dataset“](media/service-datasets-discover-across-workspaces/power-bi-shared-dataset-icon.png)

Auf diese Weise können Mitglieder des Arbeitsbereichs erkennen, welche Berichte und Dashboards Datasets verwenden, die sich außerhalb des Arbeitsbereichs befinden. Der Eintrag zeigt Informationen über das Dataset und einige ausgewählte Aktionen an.

![Datasetaktionen](media/service-datasets-across-workspaces/power-bi-dataset-actions.png)

## <a name="find-an-endorsed-dataset"></a>Suchen eines empfohlenen Datasets

Es gibt zwei Arten von empfohlenen Datasets. Datasetbesitzer können ein Dataset, das sie Ihnen empfehlen möchten, *höher stufen*. Außerdem kann der Power BI-Mandantenadministrator Experten in Ihrer Organisation benennen, die Datasets für die allgemeine Verwendung *zertifizieren* können. Sowohl für höher gestufte als auch für zertifizierte Datasets werden *Badges* angezeigt, die Sie bei der Suche nach einem Dataset und in der Liste der Datasets in einem Arbeitsbereich sehen können. Der Name der Person, die ein Dataset zertifiziert hat, wird während der Datasetermittlung in einer QuickInfo angezeigt; zeigen Sie mit der Maus auf die Bezeichnung **Zertifiziert**, dann sehen Sie den Namen.

- Im Power BI-Dienst: **Daten abrufen** > **Veröffentlichte Datasets**.
- In Power BI Desktop: **Daten abrufen** > **Power BI-Datasets**.

    Im Dialogfeld **Dataset auswählen** werden empfohlene Datasets standardmäßig oben in der Liste angezeigt. 

    ![Höher gestuftes Dataset](media/service-datasets-certify-promote/power-bi-dataset-promoted.png)

## <a name="next-steps"></a>Nächste Schritte

- [Verwenden von Datasets in mehreren Arbeitsbereichen (Vorschau)](service-datasets-across-workspaces.md)
- Haben Sie Fragen? [Stellen Sie Ihre Frage in der Power BI-Community.](https://community.powerbi.com/)
