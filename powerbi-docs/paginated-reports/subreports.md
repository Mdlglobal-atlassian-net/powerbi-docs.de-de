---
title: Unterberichte in paginierten Power BI-Berichten
description: In diesem Artikel erfahren Sie mehr über unterstützte Datenquellen für paginierte Berichte im Power BI-Dienst und dazu, wie Sie eine Verbindung zu Datenquellen der Azure SQL-Datenbank herstellen.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.date: 04/29/2020
ms.openlocfilehash: 65d1401a66f8e670df1af3097f0e99fb6b647022
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "82615701"
---
# <a name="subreports-in-power-bi-paginated-reports"></a>Unterberichte in paginierten Power BI-Berichten

Ein *Unterbericht* ist ein Element für paginierte Berichte, in dem ein anderer paginierter Bericht innerhalb des Hauptteils eines paginierten Hauptberichts angezeigt wird. Grundsätzlich ist ein Unterbericht in einem Bericht mit einem Frame in einer Webseite vergleichbar. Er wird dazu verwendet, einen Bericht in einen Bericht einzubetten. Sie können jeden Bericht als Unterbericht verwenden. Sie speichern den Bericht, der als Unterbericht angezeigt wird, im selben Premium-Arbeitsbereich wie den übergeordneten Bericht. Sie können den übergeordneten Bericht zum Übergeben von Parametern an den Unterbericht einrichten. Ein Unterbericht kann in Datenbereichen wiederholt werden. Dabei wird ein Parameter zum Filtern von Daten in jeder Instanz des Unterberichts verwendet.  
  
 ![Unterbericht in einem paginierten Bericht](media/subreports/paginated-report-subreport.png "Unterbericht in paginiertem Bericht")  
  
 In dieser Abbildung stammen die im Hauptbericht "Verkaufsauftrag" angezeigten Kontaktinformationen eigentlich aus einem Unterbericht "Kontakte".  
  
Sie erstellen und ändern die Definitionsdateien von paginierten Berichten (RDL-Dateien) in Power BI Report Builder. Sie können Unterberichte, die in SQL Server Reporting Services gespeichert sind, in einen Premium-Arbeitsbereich im Power BI-Dienst hochladen. Die Hauptberichte und die Unterberichte müssen im selben Arbeitsbereich veröffentlicht werden. Installieren Sie [Power BI Report Builder](https://go.microsoft.com/fwlink/?linkid=2086513).
  
## <a name="work-with-report-builder-and-the-power-bi-service"></a>Arbeiten mit Report Builder (Berichts-Generator) und dem Power BI-Dienst

Power BI Report Builder kann mit paginierten Berichten auf Ihrem Computer (als lokale Berichte bezeichnet) oder mit Berichten im Power BI-Dienst arbeiten.  Wenn Sie Report Builder zum ersten Mal öffnen, werden Sie aufgefordert, sich bei Ihrem Power BI Konto anzumelden. Ist dies nicht der Fall, wählen Sie **Anmelden** in der oberen rechten Ecke aus.

:::image type="content" source="media/subreports/report-builder-sign-in.png" alt-text="Bei Power BI anmelden":::

Nachdem Sie sich angemeldet haben, wird die Option **Power BI-Dienst** in Power BI Report Builder für die Optionen **Öffnen** und **Speichern unter** im Menü **Datei** angezeigt. Wenn Sie die Option **Power BI-Dienst** auswählen, um einen Bericht zu speichern, erstellen Sie eine Liveverbindung zwischen Power BI Report Builder und dem Power BI-Dienst. 

:::image type="content" source="media/subreports/report-builder-subreport-open-service.png" alt-text="Aus dem Power BI-Dienst öffnen":::

## <a name="save-a-local-report-to-the-power-bi-service"></a>Speichern eines lokalen Berichts im Power BI-Dienst

Bevor Sie einem Hauptbericht einen Unterbericht hinzufügen können, erstellen Sie zunächst die beiden Berichte, und speichern Sie diese im selben Power BI Premium-Arbeitsbereich. 

1. Um einen vorhandenen lokalen Bericht zu öffnen, wählen Sie im Menü **Datei** den Befehl **Öffnen** > **Dieser PC** aus, und wählen Sie eine RDL-Datei aus.  

2. Wählen Sie im Menü **Datei** den Befehl **Speichern unter** > **Power BI-Dienst** aus.  Weitere Informationen finden Sie unter [Veröffentlichen eines paginierten Berichts im Power BI-Dienst](paginated-reports-save-to-power-bi-service.md).

    > [!NOTE]
    > Sie können auch einen Bericht hochladen, indem Sie in der Power BI-Dienst starten. Ausführliche Informationen finden Sie im selben Artikel [Veröffentlichen eines paginierten Berichts im Power BI-Dienst](paginated-reports-save-to-power-bi-service.md).

3. Wählen Sie im Dialogfeld **Speichern unter** einen Power BI Premium-Arbeitsbereich aus, in dem Sie paginierte Berichte speichern können.  Für einen Premium-Arbeitsbereich wird ein Diamantsymbol ![Premium-Diamantsymbol](media/subreports/report-builder-premium-diamond.png) neben seinem Namen angezeigt.

    :::image type="content" source="media/subreports/report-builder-subreport-save-as-service.png" alt-text="„Speichern unter“ für den Power BI-Dienst":::

4. Wählen Sie **Speichern**.

## <a name="add-a-subreport-to-a-report"></a>Hinzufügen eines Unterberichts zu einem Bericht

Nachdem Sie nun beide Berichte im selben Premium-Arbeitsbereich gespeichert haben, können Sie einen Bericht als Unterbericht zu dem anderen Bericht hinzufügen. Es gibt zwei Möglichkeiten, einen Unterbericht hinzuzufügen. 

1. Wählen Sie im Menüband **Einfügen** die Schaltfläche **Unterbericht** aus, oder klicken Sie mit der rechten Maustaste auf den Berichtszeichenbereich, und wählen Sie **Einfügen** > **Unterbericht** aus.

    :::image type="content" source="media/subreports/report-builder-insert-subreport.png" alt-text="Einen Unterbericht in einen Bericht einfügen":::

    Das Dialogfeld **Eigenschaften des Unterberichts** wird angezeigt.  

2. Wählen Sie die Schaltfläche **Durchsuchen** aus, navigieren Sie zu dem Bericht, den Sie als Unterbericht verwenden möchten, und geben Sie den Namen des Unterberichts im Textfeld **Name** an.

3. Konfigurieren Sie nach Bedarf weitere Eigenschaften, einschließlich [Parameter](#use-parameters-in-subreports).

## <a name="use-parameters-in-subreports"></a>Verwenden von Parametern in Unterberichten  
 Um Parameter vom übergeordneten Bericht an den Unterbericht zu übergeben, definieren Sie in dem Bericht, den Sie als Unterbericht verwenden, einen Berichtsparameter. Wenn Sie den Unterbericht im übergeordneten Bericht platzieren, können Sie den Berichtsparameter und einen Wert auswählen, der vom übergeordneten Bericht an den Berichtsparameter im Unterbericht übergeben wird.  
  
> [!NOTE]  
> Der für den Unterbericht ausgewählte Parameter ist ein *Berichtsparameter*, kein *Abfrageparameter*.  
  
 Ein Unterbericht kann im Hauptteil des Berichts oder in einem Datenbereich platziert werden. Wenn Sie einen Unterbericht in einem Datenbereich platzieren, wird der Unterbericht mit jeder Instanz der Gruppe oder Zeile im Datenbereich wiederholt. Sie können einen Wert aus der Gruppe oder Zeile an den Unterbericht übergeben. Verwenden Sie in der Wert-Eigenschaft des Unterberichts einen Feldausdruck für das Feld, das den Wert enthält, den Sie an den Unterberichtsparameter übergeben möchten.  
  
 Weitere Informationen zum Arbeiten mit Parametern und Unterberichten finden Sie unter [Hinzufügen eines Unterberichts und von Parametern](https://docs.microsoft.com/sql/reporting-services/report-design/add-a-subreport-and-parameters-report-builder-and-ssrs.md) in der SQL Server Reporting Services-Dokumentation.  

## <a name="preview-paginated-reports-in-report-builder"></a>Anzeigen der Vorschau eines paginierten Berichts im Berichts-Generator

Im Berichts-Generator können Sie sich eine Vorschau Ihres jeweiligen Berichts ansehen.

- Wählen Sie im Menüband **Start** den Befehl **Ausführen** aus. 

Da Berichts-Generator ein Entwurfstool ist, kann sich die Vorschau eines Berichts von der gerenderten Version des Berichts im Power BI-Dienst unterscheiden.

### <a name="notes-about-previewing"></a>Hinweise zum Anzeigen einer Vorschau

- Berichts-Generator speichert keine Anmeldeinformationen für Datenquellen, die in Berichten verwendet werden.  Berichts-Generator fordert Sie während einer Vorschau zur Eingabe jedes Satzes von Anmeldeinformationen auf.  
- Sind die Berichtsdatenquellen lokal gespeichert, müssen Sie ein Gateway konfigurieren, nachdem Sie den Bericht im Power BI-Arbeitsbereich gespeichert haben.
- Tritt im Berichts-Generator während einer Vorschau ein Fehler auf, wird eine generische Meldung zurückgegeben.  Ist es schwierig, den Fehler zu debuggen, sollten Sie den Bericht im Power BI-Dienst rendern.  

## <a name="considerations"></a>Überlegungen

### <a name="maintaining-the-connection"></a>Beibehalten der Verbindung

Berichts-Generator speichert die Verbindung zu Power BI nicht, wenn Sie die Datei schließen.  Es ist möglich, mit einem lokalen Hauptbericht mit Unterberichten zu arbeiten, die im Power BI-Arbeitsbereich gespeichert sind. Speichern Sie den Hauptbericht im Power BI-Arbeitsbereich, bevor Sie den Bericht schließen.  Wenn Sie dies nicht tun, erhalten Sie möglicherweise eine „nicht gefunden“-Meldung während der Vorschau, weil es keine Liveverbindung zum Power BI-Dienst gibt.  Wechseln Sie in diesem Fall zu einem Unterbericht, und wählen Sie dessen Eigenschaften aus.  Öffnen Sie den Unterbericht erneut aus dem Power BI-Dienst.  Dadurch wird die Verbindung wiederhergestellt, und alle anderen Unterberichte sollten verfügbar sein.

### <a name="renaming-a-subreport"></a>Umbenennen eines Unterberichts

Wenn Sie einen Unterbericht im Arbeitsbereich umbenennen, müssen Sie den Namensverweis im Hauptbericht korrigieren. Andernfalls wird der Unterbericht nicht gerendert. Der Hauptbericht wird weiterhin mit einer Fehlermeldung im Unterberichtselement gerendert.

## <a name="migrate-large-reports"></a>Migrieren von großen Berichten

Wenn Sie große Berichte zu Power BI migrieren, empfiehlt es sich, das [RdlMigration-Tool](../guidance/migrate-ssrs-reports-to-power-bi.md) zu verwenden.  Das RdlMigration-Tool wurde so aktualisiert, dass es doppelte Unterberichtsnamen verarbeiten kann.  Doppelte Unterberichtsnamen können auftreten, wenn mehrere Berichte denselben Namen haben, sich aber in unterschiedlichen Unterverzeichnissen befinden.  Wenn die Namen nicht eindeutig aufgelöst werden, wird nur der erste Unterbericht erkannt.

Wenn Sie Berichts-Generator verwenden möchten, um große Berichte zu migrieren, empfiehlt es sich, zuerst mit den Unterberichten zu arbeiten. Speichern Sie jeden der Unterberichte im Power BI-Arbeitsbereich, um doppelte Berichtsnamen zu vermeiden.

## <a name="share-reports-with-subreports"></a>Freigeben von Berichten mit Unterberichten

Wie bereits ausgeführt, müssen sich der Hauptbericht und die Unterberichte im selben Arbeitsbereich befinden. Andernfalls werden die Unterberichte nicht gerendert. Wenn Sie den Hauptbericht freigeben, müssen Sie auch die Unterberichte freigeben. Wenn Sie den Hauptbericht in einer App freigeben, müssen Sie auch die Unterberichte in diese App einschließen. Wenn Sie den Hauptbericht direkt für Benutzer oder Benutzergruppen freigeben, müssen Sie auch jeden Unterbericht für dieselben Benutzer oder Benutzergruppen freigeben.
  
## <a name="next-steps"></a>Nächste Schritte

[Troubleshooting von Unterberichten in paginierten Power BI-Berichten](subreports-troubleshoot.md)

[Anzeigen eines paginierten Berichts im Power BI-Dienst](../consumer/paginated-reports-view-power-bi-service.md)

Weitere Fragen? [Wenden Sie sich an die Power BI-Community](https://community.powerbi.com/)
