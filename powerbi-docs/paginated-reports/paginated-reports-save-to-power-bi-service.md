---
title: Veröffentlichen eines paginierten Berichts im Power BI-Dienst
description: In diesem Tutorial lernen Sie, einen paginierten Bericht durch Hochgeladen von Ihrem lokalen Computer im Power BI-Dienst zu veröffentlichen.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.date: 05/04/2020
ms.openlocfilehash: a634844093f103c942b70cd81d93822ca240cf0a
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/13/2020
ms.locfileid: "83272026"
---
# <a name="publish-a-paginated-report-to-the-power-bi-service"></a>Veröffentlichen eines paginierten Berichts im Power BI-Dienst

In diesem Artikel erfahren Sie, wie Sie einen paginierten Bericht durch Hochgeladen von Ihrem lokalen Computer im Power BI-Dienst veröffentlichen. Sie können paginierte Berichte in Ihren Arbeitsbereich oder einen anderen Arbeitsbereich hochladen, sofern sich der Arbeitsbereich in einer Premium-Kapazität befindet. Suchen Sie nach dem Diamantsymbol ![Diamantsymbol in Power BI Premium-Kapazität](media/paginated-reports-save-to-power-bi-service/premium-diamond.png) neben dem Namen des Arbeitsbereichs. 

Wenn Sie eine lokale Berichtsdatenquelle verwenden, müssen Sie nach dem Hochladen des Berichts ein Gateway erstellen. Weitere Informationen hierzu finden Sie im Abschnitt [Erstellen eines Gateways](#create-a-gateway) im Verlauf dieses Artikels.

## <a name="add-a-workspace-to-a-premium-capacity"></a>Hinzufügen eines Arbeitsbereichs zu einer Premium-Kapazität

Wenn im Arbeitsbereich das Diamantsymbol ![Diamantsymbol in Power BI Premium-Kapazität](media/paginated-reports-save-to-power-bi-service/premium-diamond.png) neben dem Namen nicht angezeigt wird, müssen Sie den Arbeitsbereich einer Premium-Kapazität hinzufügen. 

1. Wählen Sie **Arbeitsbereiche**, die Auslassungspunkte ( **...** ) neben dem Arbeitsbereichsnamen und dann **Arbeitsbereich bearbeiten** aus.

    ![Auswählen von „Arbeitsbereich bearbeiten“](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-edit-workspace.png)

1. Erweitern Sie im Dialogfeld **Arbeitsbereich bearbeiten** **Erweitert**, und ziehen Sie **Dedizierte Kapazität** dann auf **Ein**.

    ![Auswählen von „Dedizierte Kapazität“](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-edit-workspace-dialog.png)

   Möglicherweise können Sie diese Einstellung nicht ändern. Wenn das der Fall ist, wenden Sie sich an Ihren Power BI Premium-Kapazitätsadministrator, damit er Ihnen die Berechtigung erteilt, Ihren Arbeitsbereich einer Premium-Kapazität hinzuzufügen.

## <a name="from-report-builder-publish-a-paginated-report"></a>Veröffentlichen eines paginierten Berichts über den Berichts-Generator

1. Erstellen Sie Ihren paginierten Bericht im Berichts-Generator, und speichern Sie ihn auf Ihrem lokalen Computer.

1. Klicken Sie im Menü **Datei** des Berichts-Generators auf **Speichern unter**.

    ![Datei > Speichern > Speichern unter](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-save-as.png)

    Wenn Sie noch nicht bei Power BI angemeldet sind, müssen Sie sich jetzt anmelden oder ein Konto erstellen. Klicken Sie in der oberen rechten Ecke des Berichts-Generators auf **Anmelden**, und führen Sie die Schritte durch.

2. Wählen Sie aus der Liste der Arbeitsbereiche einen Arbeitsbereich aus, neben dessen Namen sich ein Diamantsymbol ![Power BI Premium-Diamantsymbol](media/paginated-reports-save-to-power-bi-service/premium-diamond.png) befindet. Füllen Sie das Feld **Dateiname** aus, und klicken Sie auf **Speichern**. 

    ![Auswahl eines Premium-Arbeitsbereichs](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-select-workspace.png)

4. Öffnen Sie den Power BI-Dienst in einem Browser, und navigieren Sie zu dem Premium-Arbeitsbereich, in dem Sie den paginierten Bericht veröffentlicht haben. Auf der Registerkarte **Berichte** wird der Bericht angezeigt.

    ![Paginierter Bericht in der Berichtsliste](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-wwi-report.png)

5. Wählen Sie den paginierten Bericht aus, um diesen im Power BI-Dienst zu öffnen. Wenn er über Parameter verfügt, müssen Sie diese auswählen, bevor der Bericht angezeigt werden kann.

    ![Auswählen von Parametern](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-select-parameters.png)

6. Wenn Sie eine lokale Berichtsdatenquelle verwenden, finden Sie im Abschnitt [Erstellen eines Gateways](#create-a-gateway) weitere Informationen zum Zugriff auf Datenquellen.

## <a name="from-the-power-bi-service-upload-a-paginated-report"></a>Hochladen eines paginierten Berichts über den Power BI-Dienst

Sie können auch im Power BI-Dienst beginnen und dort einen paginierten Bericht hochladen.

1. Erstellen Sie Ihren paginierten Bericht im Berichts-Generator, und speichern Sie ihn auf Ihrem lokalen Computer.

1. Öffnen Sie den Power BI-Dienst in einem Browser, und navigieren Sie zu dem Premium-Arbeitsbereich, in dem Sie den Bericht veröffentlichen möchten. Achten Sie auf das Diamantsymbol ![Diamantsymbol in Power BI Premium-Kapazität](media/paginated-reports-save-to-power-bi-service/premium-diamond.png) neben dem Namen des Arbeitsbereichs. 

1. Wählen Sie **Daten abrufen** aus.

    ![„Daten abrufen“ in Power BI](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-get-data.png)

1. Wählen Sie im Feld **Dateien** die Option **Abrufen**aus.

    ![Abrufen von Dateien in Power BI](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-files-get.png)

1. Wählen Sie **Lokale Datei** aus, navigieren Sie zum paginierten Bericht, und wählen Sie **Öffnen** aus.

    ![Auswählen von „Lokale Datei“](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-local-file.png)

1. Wählen Sie **Weiter** > **Anmeldeinformationen bearbeiten** aus.

    ![Auswählen von „Anmeldeinformationen bearbeiten“](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-select-edit-credentials.png)

1. Konfigurieren Sie Ihre Anmeldeinformationen, und wählen Sie **Anmelden** aus.

    ![Anmeldeinformationen bearbeiten](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-credentials.png)

   Auf der Registerkarte **Berichte** wird der Bericht angezeigt.

    ![Paginierter Bericht in der Berichtsliste](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-wwi-report.png)

1. Wählen sie den Bericht aus, um ihn im Power BI-Dienst zu öffnen. Wenn er über Parameter verfügt, müssen Sie diese auswählen, bevor der Bericht angezeigt werden kann.
 
    ![Auswählen von Parametern](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-select-parameters.png)

6. Wenn Sie eine lokale Berichtsdatenquelle verwenden, finden Sie im Abschnitt [Erstellen eines Gateways](#create-a-gateway) weitere Informationen zum Zugriff auf Datenquellen.

## <a name="create-a-gateway"></a>Erstellen eines Gateways

Wie bei allen Power BI-Berichten müssen Sie im Falle einer lokalen Berichtsdatenquelle ein Gateway erstellen oder eine Verbindung mit diesem herstellen, um auf Daten zuzugreifen.

1. Wählen Sie neben dem Berichtsnamen **Verwalten** aus.

   ![Verwalten des paginierten Berichts](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-manage.png)

1. Im Power BI-Artikel [Was ist ein lokales Datengateway](../connect-data/service-gateway-onprem.md) finden Sie weitere Informationen und Anleitungen.



## <a name="next-steps"></a>Nächste Schritte

- [Anzeigen eines paginierten Berichts im Power BI-Dienst](../consumer/paginated-reports-view-power-bi-service.md)
- [Was sind paginierte Berichte in Power BI Premium? (Vorschau)](paginated-reports-report-builder-power-bi.md)
- [Tutorial: Einbetten paginierter Power BI-Berichte in eine Anwendung für Kunden](../developer/embed-paginated-reports-customers.md)


