---
title: 'Tutorial: Herstellen einer Verbindung mit lokalen Daten in SQL Server'
description: Erfahren Sie, wie Sie SQL Server als Gatewaydatenquelle verwenden und Daten aktualisieren.
author: arthiriyer
ms.reviewer: kayu
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: tutorial
ms.date: 07/15/2019
ms.author: arthii
LocalizationGroup: Gateways
ms.openlocfilehash: 100417202fca148be0e2e976ce0cd84167c803d9
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/13/2020
ms.locfileid: "83283506"
---
# <a name="refresh-data-from-an-on-premises-sql-server-database"></a>Aktualisieren von Daten aus einer lokalen SQL Server-Datenbank

In diesem Tutorial erfahren Sie, wie Sie ein Power BI-Dataset aus einer relationalen Datenbank aktualisieren, die sich lokal in Ihrem Netzwerk befindet. Hierfür wird in diesem Tutorial insbesondere eine SQL Server-Beispieldatenbank verwendet, auf die Power BI über ein lokales Datengateway zugreifen muss.

In diesem Tutorial führen Sie die folgenden Schritte aus:

> [!div class="checklist"]
> * Erstellen und Veröffentlichen einer Power BI Desktop-Datei (PBIX), die Daten aus einer lokalen SQL Server-Datenbank importiert
> * Konfigurieren der Datenquellen- und Dataseteinstellungen in Power BI für die SQL Server-Konnektivität über ein Datengateway
> * Konfigurieren eines Aktualisierungszeitplans, um sicherzustellen, dass Ihr Power BI-Dataset über aktuelle Daten verfügt
> * Durchführen einer bedarfsgesteuerten Aktualisierung Ihres Datasets
> * Überprüfen des Aktualisierungsverlaufs zur Analyse der Ergebnisse vergangener Aktualisierungszyklen
> * Bereinigen von Ressourcen durch Löschen der Artefakte, die in diesem Tutorial erstellt werden

## <a name="prerequisites"></a>Voraussetzungen

- Wenn Sie nicht bereits über ein Power BI-Abonnement verfügen, registrieren Sie sich zunächst für die [kostenlose Power BI-Testversion](https://app.powerbi.com/signupredirect?pbi_source=web).
- [Installieren Sie Power BI Desktop](https://powerbi.microsoft.com/desktop/) auf einem lokalen Computer.
- [Installieren Sie SQL Server](/sql/database-engine/install-windows/install-sql-server) auf einem lokalen Computer, und stellen Sie die [Beispieldatenbank aus einer Sicherung](https://github.com/Microsoft/sql-server-samples/releases/download/adventureworks/AdventureWorksDW2017.bak) wieder her. Weitere Informationen zu AdventureWorks finden Sie unter [AdventureWorks installation and configuration (AdventureWorks-Installation und -Konfiguration)](/sql/samples/adventureworks-install-configure).
- [Installieren Sie ein lokales Datengateway](service-gateway-onprem.md) auf demselben lokalen Computer, auf dem auch SQL Server installiert wurde (in der Produktionsumgebung würde es sich in der Regel um einen anderen Computer handeln).

> [!NOTE]
> Wenn Sie kein Gatewayadministrator sind und ein Gateway nicht selbst installieren möchten, kontaktieren Sie einen Gatewayadministrator in Ihrem Unternehmen. Dieser kann die Datenquellendefinition erstellen, die für die Verbindung Ihres Datasets mit Ihrer SQL Server-Datenbank erforderlich ist.

## <a name="create-and-publish-a-power-bi-desktop-file"></a>Erstellen und Veröffentlichen einer Power BI Desktop-Datei

Gehen Sie folgendermaßen vor, um mithilfe der AdventureWorksDW-Beispieldatenbank einen grundlegenden Power BI-Bericht zu erstellen. Veröffentlichen Sie den Bericht im Power BI-Dienst, um ein Dataset in Power BI zu erhalten, das Sie anschließend konfigurieren und aktualisieren können.

1. Klicken Sie in Power BI Desktop auf der Registerkarte **Start** auf **Daten abrufen** \> **SQL Server**.

2. Geben Sie im Dialogfeld **SQL Server-Datenbank** die Namen von **Server** und **Datenbank (optional)** ein, stellen Sie sicher, dass als **Datenkonnektivitätsmodus** die Option **Import** ausgewählt ist, und klicken Sie dann auf **OK**.

    ![SQL Server-Datenbank](./media/service-gateway-sql-tutorial/sql-server-database.png)

    In diesem Tutorial verwenden wir keine **erweiterten Optionen**, Sie können aber eine SQL-Anweisung angeben und andere Optionen wie beispielsweise die Verwendung von [SQL Server-Failover](/sql/database-engine/availability-groups/windows/failover-clustering-and-always-on-availability-groups-sql-server) festlegen.

    ![Erweiterte SQL Server-Optionen](media/service-gateway-sql-tutorial/sql-server-advanced-options.png)

3. Überprüfen Sie Ihre **Anmeldeinformationen**, und klicken Sie auf **Verbinden**.

    > [!NOTE]
    > Wenn die Authentifizierung nicht möglich ist, stellen Sie sicher, dass Sie die richtige Authentifizierungsmethode ausgewählt haben und ein Konto mit Datenbankzugriff verwenden. In Testumgebungen verwenden Sie möglicherweise die Datenbankauthentifizierung mit einem bestimmten Benutzernamen und Kennwort. In Produktionsumgebungen verwenden Sie in der Regel die Windows-Authentifizierung. Weitere Unterstützung erhalten Sie unter [Problembehandlung bei Aktualisierungsszenarios](refresh-troubleshooting-refresh-scenarios.md) oder von Ihrem Datenbankadministrator.

1. Wenn das Dialogfeld **Encryption Support** (Verschlüsselungsunterstützung) angezeigt wird, klicken Sie auf **OK**.

2. Klicken Sie im Dialogfeld **Navigator** auf die Tabelle **DimProduct** und anschließend auf **Laden**.

    ![Datenquellennavigator](./media/service-gateway-sql-tutorial/data-source-navigator.png)

3. Wählen Sie in der Power BI Desktop-Ansicht **Bericht** im Bereich **Visualisierungen** die Option **Gestapeltes Säulendiagramm** aus.

    ![Gestapeltes Säulendiagramm](./media/service-gateway-sql-tutorial/stacked-column-chart.png)

4. Wenn im Berichtszeichenbereich das Säulendiagramm ausgewählt ist, wählen Sie im Bereich **Felder** die Felder **EnglishProductName** und **ListPrice** aus.

    ![Bereich „Felder“](./media/service-gateway-sql-tutorial/fields-pane.png)

5. Ziehen Sie **EndDate** auf **Report level filters** (Filter auf Berichtsebene), und aktivieren Sie unter **Basic filtering** (Standardfilter) nur das Kontrollkästchen für **(Blank)** (Leer).

    ![Filter auf Berichtebene](./media/service-gateway-sql-tutorial/report-level-filters.png)

    Das Diagramm sollte nun wie folgt aussehen.

    ![Fertiges Säulendiagramm](./media/service-gateway-sql-tutorial/finished-column-chart.png)

    Beachten Sie, dass die fünf **Road-250**-Produkte mit dem höchsten Listenpreis aufgeführt sind. Dies wird sich ändern, wenn Sie später die Daten und den Bericht in diesem Tutorial aktualisieren.

6. Speichern Sie den Bericht unter dem Namen „AdventureWorksProducts.pbix“.

7. Klicken Sie auf der Registerkarte **Start** auf **Veröffentlichen** \> **Mein Arbeitsbereich** \> **Auswählen**. Melden Sie sich beim Power BI-Dienst an, wenn Sie dazu aufgefordert werden.

8. Wählen Sie auf dem Bildschirm **Success** (Vorgang erfolgreich) die Option **Open 'AdventureWorksProducts.pbix' in Power BI** („AdventureWorksProducts.pbix“ in Power BI öffnen) aus.

    [Veröffentlichen in Power BI](./media/service-gateway-sql-tutorial/publish-to-power-bi.png)

## <a name="connect-a-dataset-to-a-sql-server-database"></a>Verbinden eines Datasets mit einer SQL Server-Datenbank

Sie haben in Power BI Desktop eine direkte Verbindung mit Ihrer lokalen SQL Server-Datenbank hergestellt. Der Power BI-Dienst benötigt jedoch ein Datengateway, um als Brücke zwischen der Cloud und Ihrem lokalen Netzwerk zu agieren. Führen Sie die folgenden Schritte aus, um Ihre lokale SQL Server-Datenbank als Datenquelle zu einem Gateway hinzuzufügen und dann eine Verbindung zwischen Ihrem Dataset und dieser Datenquelle herzustellen.

1. Melden Sie sich bei Power BI an. Klicken Sie in der rechten oberen Ecke auf das Zahnradsymbol (Einstellungen) und anschließend auf **Einstellungen**.

    ![Power BI-Einstellungen](./media/service-gateway-sql-tutorial/power-bi-settings.png)

2. Wählen Sie auf der Registerkarte **Datasets** das Dataset **AdventureWorksProducts** aus, um über ein Datengateway eine Verbindung mit Ihrer lokalen SQL Server-Datenbank herzustellen.

3. Erweitern Sie **Gatewayverbindung**, und stellen Sie sicher, dass mindestens ein Gateway aufgeführt ist. Wenn Sie über kein Gateway verfügen, erfahren Sie über den Link zur Produktdokumentation im Abschnitt [Voraussetzungen](#prerequisites) oben, wie Sie ein Gateway installieren und konfigurieren können.

    ![Gatewayverbindung](./media/service-gateway-sql-tutorial/gateway-connection.png)

4. Erweitern Sie unter **Aktionen** die Umschaltfläche, um die Datenquellen anzuzeigen, und wählen Sie den Link **Zu Gateway hinzufügen** aus.

    ![Hinzufügen einer Datenquelle zum Gateway](./media/service-gateway-sql-tutorial/add-data-source-gateway.png)

    > [!NOTE]
    > Wenn Sie kein Gatewayadministrator sind und ein Gateway nicht selbst installieren möchten, kontaktieren Sie einen Gatewayadministrator in Ihrem Unternehmen. Dieser kann die Datenquellendefinition erstellen, die für die Verbindung Ihres Datasets mit Ihrer SQL Server-Datenbank erforderlich ist.

5. Geben Sie auf der Seite zur Verwaltung von **Gateways** auf der Registerkarte **Datenquelleneinstellungen** die folgenden Informationen ein, überprüfen Sie diese, und wählen Sie **Hinzufügen** aus.

    | Option | Werte |
    | --- | --- |
    | Datenquellenname | AdventureWorksProducts |
    | Datenquellentyp | SQL Server |
    | Server | Der Name Ihrer SQL Server-Instanz, z. B. SQLServer01 (muss mit der Angabe in Power BI Desktop übereinstimmen) |
    | Datenbank | Der Name Ihrer SQL Server-Datenbank, z. B. AdventureWorksDW (muss mit der Angabe in Power BI Desktop übereinstimmen) |
    | Authentifizierungsmethode | Windows oder Standard (in der Regel Windows) |
    | Benutzername | Das Benutzerkonto zum Herstellen der Verbindung mit SQL Server |
    | Password | Das Kennwort für das Konto zum Herstellen der Verbindung mit SQL Server |

    ![Datenquelleneinstellungen](./media/service-gateway-sql-tutorial/data-source-settings.png)

6. Erweitern Sie auf der Registerkarte **Datasets** nochmals den Bereich **Gatewayverbindung**. Wählen Sie das Datengateway aus, das Sie konfiguriert haben und dessen **Status** angibt, dass es auf dem Computer ausgeführt wird, auf dem Sie es erstellt haben. Klicken Sie anschließend auf **Apply** (Übernehmen).

    ![Aktualisieren der Gatewayverbindung](./media/service-gateway-sql-tutorial/update-gateway-connection.png)

## <a name="configure-a-refresh-schedule"></a>Konfigurieren eines Aktualisierungszeitplans

Nachdem Sie in Power BI nun lokal über ein Datengateway eine Verbindung zwischen Ihrem Dataset und Ihrer SQL Server-Datenbank hergestellt haben, konfigurieren Sie mithilfe der folgenden Schritte einen Aktualisierungszeitplan. Durch die Aktualisierung Ihres Datasets nach einem Zeitplan können Sie sicherstellen, dass Ihre Berichte und Dashboards über die aktuellen Daten verfügen.

1. Öffnen Sie im Navigationsbereich **Mein Arbeitsbereich** \> **Datasets**. Wählen Sie die Auslassungspunkte ( **. . .** ) für das Dataset **AdventureWorksProducts** aus, und klicken Sie dann auf **Zeitplanaktualisierung**.

    > [!NOTE]
    > Stellen Sie sicher, dass Sie die Auslassungspunkte für das Dataset **AdventureWorksProducts** und nicht die Auslassungspunkte für den Bericht mit dem gleichen Namen auswählen. Das Kontextmenü des Berichts **AdventureWorksProducts** umfasst nicht die Option **Zeitplanaktualisierung**.

2. Legen Sie im Bereich **Geplante Aktualisierung** unter **Halten Sie Ihre Daten aktuell** die Aktualisierung auf **On** (An) fest.

3. Wählen Sie ein geeignetes **Aktualisierungsintervall** aus (für dieses Beispiel **Täglich**), und klicken Sie dann unter **Uhrzeit** auf **Andere Uhrzeit hinzufügen**, um die gewünschte Aktualisierungszeit anzugeben (6:30 Uhr und 18:30 Uhr für dieses Beispiel).

    ![Konfigurieren von geplanten Aktualisierungen](./media/service-gateway-sql-tutorial/configure-scheduled-refresh.png)

    > [!NOTE]
    > Sie können bis zu acht tägliche Zeitfenster konfigurieren, wenn sich Ihr Dataset auf gemeinsam genutzter Kapazität befindet, oder 48 Zeitfenster in Power BI Premium.

4. Lassen Sie das Kontrollkästchen **Send refresh failure notification emails to me** (Benachrichtigungs-E-Mails zu Aktualisierungsfehlern an mich senden) aktiviert, und wählen Sie **Apply** (Übernehmen) aus.

## <a name="perform-an-on-demand-refresh"></a>Durchführen einer bedarfsgesteuerten Aktualisierung

Da Sie nun einen Aktualisierungszeitplan konfiguriert haben, aktualisiert Power BI Ihr Dataset zum nächsten geplanten Zeitpunkt (in einem Zeitfenster von 15 Minuten). Wenn Sie die Daten früher aktualisieren möchten, z.B. um Ihr Gateway und Ihre Datenquellenkonfiguration zu testen, führen Sie eine bedarfsgesteuerte Aktualisierung durch, indem Sie die Option **Jetzt aktualisieren** im Datasetmenü im Navigationsbereich verwenden. Bedarfsgesteuerte Aktualisierungen haben keinen Einfluss auf die nächste geplante Aktualisierungszeit, aber sie zählen bei der Beschränkung der täglichen Aktualisierungen, wie bereits im vorherigen Abschnitt erwähnt.

Simulieren Sie zur Veranschaulichung eine Änderung an den Beispieldaten, indem Sie die Tabelle „DimProduct“ in der Datenbank „AdventureWorksDW“ mithilfe von SQL Server Management Studio (SSMS) aktualisieren.

```sql

UPDATE [AdventureWorksDW].[dbo].[DimProduct]
SET ListPrice = 5000
WHERE EnglishProductName ='Road-250 Red, 58'

```

Führen Sie nun die folgenden Schritte aus, damit die aktualisierten Daten über die Gatewayverbindung zum Dataset gelangen und in den Berichten in Power BI erscheinen.

1. Wählen Sie im Power BI-Dienst im Navigationsbereich die Option **Mein Arbeitsbereich** aus, und erweitern Sie diese.

2. Wählen Sie unter **Datasets** die Auslassungspunkte ( **. . .** ) für das Dataset **AdventureWorksProducts** aus, und klicken Sie dann auf **Jetzt aktualisieren**.

    ![Jetzt aktualisieren](./media/service-gateway-sql-tutorial/refresh-now.png)

    Beachten Sie in der rechten oberen Ecke, dass sich Power BI darauf vorbereitet, die angeforderte Aktualisierung durchzuführen.

3. Klicken Sie auf **Mein Arbeitsbereich \> Berichte \> AdventureWorksProducts**. Die aktualisierten Daten wurden übertragen, und das Produkt mit dem höchsten Listenpreis ist nun **Road-250 Red, 58**.

    ![Aktualisiertes Säulendiagramm](./media/service-gateway-sql-tutorial/updated-column-chart.png)

## <a name="review-the-refresh-history"></a>Überprüfen des Aktualisierungsverlaufs

Sie sollten die Ergebnisse vergangener Aktualisierungszyklen im Aktualisierungsverlauf regelmäßig überprüfen. Datenbankanmeldeinformationen könnten abgelaufen sein, oder das ausgewählte Gateway könnte zum Zeitpunkt der geplanten Aktualisierung offline gewesen sein. Mithilfe der folgenden Schritte können Sie den Aktualisierungsverlauf untersuchen und auf Fehler überprüfen.

1. Klicken Sie in der Power BI-Benutzeroberfläche in der rechten oberen Ecke auf das Zahnradsymbol (Einstellungen) und anschließend auf **Einstellungen**.

2. Wechseln Sie zu **Datasets**, und wählen Sie das Dataset (z. B. **AdventureWorksProducts**) aus, das Sie untersuchen möchten.

3. Klicken Sie auf **Aktualisierungsverlauf**, um das Dialogfeld zum **Aktualisierungsverlauf** zu öffnen.

    ![Link „Aktualisierungsverlauf“](./media/service-gateway-sql-tutorial/refresh-history-link.png)

4. Beachten Sie auf der Registerkarte **Geplant** die vergangenen geplanten und bedarfsgesteuerten Aktualisierungen mit **Start-** und **Endzeiten** sowie dem **Status** **Abgeschlossen**, der angibt, dass Power BI diese Aktualisierungen erfolgreich durchgeführt hat. Bei fehlerhaften Aktualisierungen wird Ihnen die Fehlermeldung angezeigt, wodurch Sie die Fehlerdetails untersuchen können.

    ![Details des Aktualisierungsverlaufs](./media/service-gateway-sql-tutorial/refresh-history-details.png)

    > [!NOTE]
    > Die Registerkarte OneDrive ist nur für Datasets relevant, die mit Power BI Desktop-Dateien, Excel-Arbeitsmappen oder CSV-Dateien in OneDrive oder SharePoint Online verbunden sind. Weitere Informationen hierzu finden Sie unter [Aktualisieren von Daten in Power BI](refresh-data.md).

## <a name="clean-up-resources"></a>Bereinigen von Ressourcen

Wenn Sie die Beispieldaten nicht mehr verwenden möchten, löschen Sie die Datenbank in SQL Server Management Studio (SSMS). Wenn Sie die SQL Server-Datenquelle nicht mehr verwenden möchten, entfernen Sie die Datenquelle von Ihrem Datengateway. Erwägen Sie auch die Deinstallation des Datengateways, falls Sie es nur für dieses Tutorial installiert haben. Sie sollten ebenfalls das Dataset „AdventureWorksProducts“ und den Bericht „AdventureWorksProducts“ löschen, die von Power BI beim Hochladen der Datei „AdventureWorksProducts.pbix“ erstellt wurden.

## <a name="next-steps"></a>Weitere Schritte

In diesem Tutorial haben Sie erfahren, wie Sie Daten aus einer lokalen SQL Server-Datenbank in ein Power BI-Dataset importieren und wie Sie dieses Dataset nach einem Zeitplan bzw. bedarfsgesteuert aktualisieren, um die Berichte und Dashboards, die dieses Dataset verwenden, in Power BI auf dem neusten Stand zu halten. Nun können Sie mehr über das Verwalten von Datengateways und Datenquellen in Power BI erfahren. Sie sollten auch den konzeptionellen Artikel „Aktualisieren von Daten in Power BI“ lesen.

- [Verwalten eines lokalen Datengateways](/data-integration/gateway/service-gateway-manage)
- [Verwalten der Datenquelle – Import/Geplante Aktualisierung](service-gateway-enterprise-manage-scheduled-refresh.md)
- [Aktualisieren von Daten in Power BI](refresh-data.md)
