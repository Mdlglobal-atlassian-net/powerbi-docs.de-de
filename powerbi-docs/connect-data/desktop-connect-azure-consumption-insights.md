---
title: Herstellen einer Verbindung mit Azure Consumption Insights-Daten in Power BI Desktop
description: Einfaches Herstellen einer Verbindung mit Azure und Erhalten von Einblicken in Verbrauch und Verwendung mithilfe von Power BI Desktop
author: davidiseminger
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 10/14/2019
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 5cc566798d53a29ef1f205c34d7e97d9331a164d
ms.sourcegitcommit: bfc2baf862aade6873501566f13c744efdd146f3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/13/2020
ms.locfileid: "83347974"
---
# <a name="connect-to-azure-consumption-insights-data-in-power-bi-desktop"></a>Herstellen einer Verbindung mit Azure Consumption Insights-Daten in Power BI Desktop

Mithilfe von Power BI Desktop können Sie eine Verbindung mit Azure herstellen und detaillierte Daten zur Nutzung des Azure-Diensts in Ihrer Organisation abrufen. Auf der Grundlage dieser Daten können Sie benutzerdefinierte Berichte und Measures erstellen, die Ihnen dabei helfen, Ihre Azure-Ausgaben zu analysieren und besser nachzuvollziehen.

> [!NOTE]
> Microsoft Azure Consumption Insights (Beta) wird nur eingeschränkt unterstützt. Verwenden Sie für neue Funktionen den [Azure Cost Management-Connector für Power BI](desktop-connect-azure-cost-management.md).

## <a name="connect-with-azure-consumption-insights"></a>Herstellen einer Verbindung mit Azure Consumption Insights

Mit Azure Consumption Insights können Sie eine Verbindung mit Azure Enterprise Agreement-Abrechnungskonten herstellen.

In diesem Abschnitt erfahren Sie, wie Sie die Daten, die Sie benötigen, mithilfe des Azure Enterprise-Connectors migrieren können. Außerdem erhalten Sie Informationen zur Zuordnung der *Spalten zur Nutzung* in der **Azure Consumption Insights**-API.

Damit Sie den **Azure Consumption Insights**-Connector verwenden können, benötigen Sie Zugriff auf die Enterprise-Features im Azure-Portal.

So verwenden Sie den **Azure Consumption Insights**-Connector in **Power BI Desktop**: 

1. Klicken Sie im Menüband **Start** auf **Daten abrufen**.

1. Klicken Sie in den Kategorien auf der linken Seite auf **Onlinedienste**.  

1. Klicken Sie auf **Microsoft Azure Consumption Insights (Beta)** . 

1. Wählen Sie **Verbinden** aus.

   ![](media/desktop-connect-azure-consumption-insights/azure-consumption-insights_01b.png)

   Geben Sie in das daraufhin angezeigte Dialogfeld Ihre **Azure-Registrierungsnummer** ein.

   ![](media/desktop-connect-azure-consumption-insights/azure-consumption-insights_02.png)

   * Sie finden Ihre Registrierungsnummer im [Azure Enterprise-Portal](https://ea.azure.com) an der in der folgenden Abbildung dargestellten Position:

  ![](media/desktop-connect-azure-consumption-insights/azure-consumption-insights_08.png)

   Diese Version des Connectors unterstützt nur Enterprise-Registrierungen über https://ea.azure.com. Registrierungen in China werden derzeit nicht unterstützt.

   Geben Sie anschließend Ihren *Zugriffsschlüssel* an, um die Verbindung herzustellen.

   ![](media/desktop-connect-azure-consumption-insights/azure-consumption-insights_03.png)

   * Sie finden den Zugriffsschlüssel für die Registrierung im [Azure Enterprise-Portal](https://ea.azure.com).

  ![](media/desktop-connect-azure-consumption-insights/azure-consumption-insights_09.png)

Sobald Sie Ihren *Zugriffsschlüssel* angegeben und auf **Verbinden** geklickt haben, wird ein **Navigatorfenster** geöffnet, in dem neun verfügbare Tabellen angezeigt werden:

| Tabelle        | Beschreibung |
|------------- | -------------------------------------------------------------|
| **Budgets** | Budgetdetails zur Anzeige der tatsächlichen Kosten oder Nutzung im Vergleich zu vorhandenen Budgetzielen |
| **MarketPlace** | Die nutzungsbasierten Azure Marketplace-Gebühren |
| **PriceSheets** | Die geltenden Preise für eine Registrierung nach Verbrauchseinheit |
| **RICharges** | Die Gebühren für Ihre reservierten Instanzen in den letzten 24 Monaten |
| **RIRecommendations_Single** | Kaufempfehlungen für reservierte Instanzen, die auf Ihren Nutzungstrends für ein einzelnes Abonnement in den letzten sieben, 30 oder 60 Tagen basieren |
| **RIRecommendations_Shared** | Kaufempfehlungen für reservierte Instanzen, die auf Ihren Nutzungstrends für all Ihre Abonnement in den letzten sieben, 30 oder 60 Tagen basieren |
| **RIUsage** | Ausführliche Informationen zum Verbrauch für Ihre vorhandenen reservierten Instanzen im letzten Monat |
| **Summaries** | Eine monatliche Übersicht über Salden, neue Käufe, Gebühren für den Azure Marketplace-Dienst, Anpassungen und Überschreitungsgebühren |
| **UsageDetails** | Eine Aufgliederung der verbrauchten Mengen und geschätzte Registrierungsgebühren |

Sie können neben jeder Tabelle ein Kontrollkästchen aktivieren, um eine Vorschau anzuzeigen. Sie können eine oder mehrere Tabellen auswählen, indem Sie das Kontrollkästchen neben dem Tabellennamen aktivieren, und dann **Laden** wählen.

![](media/desktop-connect-azure-consumption-insights/azure-consumption-insights_04b.png)

> [!NOTE]
> Die Tabellen *Summaries* und *PriceSheets* sind nur für den API-Schlüssel auf Registrierungsebene verfügbar. Standardmäßig sind die Daten für die Tabellen *UsageDetails* und *PriceSheets* die Daten des aktuellen Monats. Die Tabellen *Summaries* und *Marketplace* sind nicht auf den aktuellen Monat beschränkt.
>
>

Wenn Sie **Laden** auswählen, werden die Daten in **Power BI Desktop** geladen.

![](media/desktop-connect-azure-consumption-insights/azure-consumption-insights_05.png)

Nachdem die von Ihnen ausgewählten Daten geladen wurden, werden im Bereich **Felder** die von Ihnen ausgewählten Tabellen und Felder angezeigt.

![](media/desktop-connect-azure-consumption-insights/azure-consumption-insights_06.png)

## <a name="using-azure-consumption-insights"></a>Verwenden von Azure Consumption Insights
Damit Sie den **Azure Consumption Insights**-Connector verwenden können, benötigen Sie Zugriff auf die Enterprise-Features im Azure-Portal.

Sobald Sie erfolgreich mit dem **Azure Consumption Insights**-Connector Daten geladen haben, können Sie mithilfe des **Abfrage-Editors** eigene benutzerdefinierte Measures und Spalten erstellen. Sie können auch Visuals, Berichte und Dashboards für die Freigabe im **Power BI-Dienst** erstellen.

Mithilfe einer leeren Abfrage können Sie eine Beispielsammlung für benutzerdefinierte Azure-Abfragen abrufen. Dafür gibt es zwei Möglichkeiten: 

In **Power BI Desktop**: 

1. Klicken Sie auf das Menüband **Start** 
2. Klicken Sie auf **Daten abrufen** > **Leere Abfrage** 

Oder im **Abfrage-Editor**: 

1. Klicken Sie mit der rechten Maustaste auf der linken Seite auf den Bereich **Abfragen**. 
2. Klicken Sie im daraufhin angezeigten Menü auf **Neue Abfrage > Leere Abfrage**.

Geben Sie Folgendes in die **Bearbeitungsleiste** ein:

    = MicrosoftAzureConsumptionInsights.Contents

Auf der folgenden Abbildung sehen Sie ein Beispiel für eine Sammlung, die daraufhin angezeigt wird.

![](media/desktop-connect-azure-consumption-insights/azure-consumption-insights_07.png)

Sie haben die folgenden Möglichkeiten, wenn Sie mit Berichten arbeiten und Abfragen erstellen:

* Verwenden Sie zum Definieren der Anzahl von Monaten ab dem aktuellen Datum *numberOfMonth*.
  * Verwenden Sie einen Wert zwischen 1 und 36. Geben Sie die Anzahl der Monate ab dem aktuellen Datum an, für die Sie einen Import durchführen möchten. Es wird empfohlen, nicht mehr als die Daten von 12 Monaten abzurufen. Durch diese Beschränkung werden Einschränkungen für Power BI-Abfrageimporte und Schwellenwerte für Datenvolumen vermieden.
* Verwenden Sie *startBillingDataWindow* und *endBillingDataWindow*, um einen Zeitraum von Monaten in einem historischen Zeitfenster zu definieren.
* *numberOfMonth* darf nicht zusammen mit *startBillingDataWindow* oder *endBillingDataWindow* verwendet werden.

## <a name="migrate-from-the-azure-enterprise-connector"></a>Migrieren des Azure Enterprise-Connectors

Einige Kunden haben Visuals mithilfe des *Azure Enterprise-Connectors (Beta)* erstellt. Dieser Connector wird mit der Zeit durch den **Azure Consumption Insights**-Connector ersetzt. Der neue Connector verfügt über Features und Erweiterungen, die Folgendes umfassen:

* Zusätzliche verfügbare Datenquellen für *Saldozusammenfassung* und *Marketplace-Einkäufe*
* Neue und verbesserte Parameter, z.B. *startBillingDataWindow* und *endBillingDataWindow*
* Bessere Leistung und Reaktionsfähigkeit

In den nächsten Schritten wird gezeigt, wie Sie zum **Azure Consumption Insights-Connector** wechseln können. Dabei wird Ihre bisherige Arbeit im Zusammenhang mit der Erstellung benutzerdefinierter Dashboards und Berichte bewahrt.

### <a name="step-1-connect-to-azure-using-the-new-connector"></a>Schritt 1: Mithilfe des neuen Connectors eine Verbindung mit Azure herstellen
Der erste Schritt ist die Verwendung des **Azure Consumption Insights**-Connectors, der weiter oben in diesem Artikel ausführlich beschrieben wird. Wählen Sie in diesem Schritt im Menüband **Start** von **Power BI Desktop** die Option **Daten abrufen > Leere Abfrage** aus.

### <a name="step-2-create-a-query-in-advanced-editor"></a>Schritt 2: Erstellen einer Abfrage im Erweiterten Editor
Klicken Sie im **Abfrage-Editor** im Abschnitt **Abfrage** des Menübands **Start** auf die Option **Erweiterter Editor**. Geben Sie im daraufhin angezeigten Fenster **Erweiterter Editor** die folgende Abfrage ein:

    let    
        enrollmentNumber = "100",
        optionalParameters = [ numberOfMonth = 6, dataType="DetailCharges" ],
        data = MicrosoftAzureConsumptionInsights.Contents(enrollmentNumber, optionalParameters)   
    in     
        data

![](media/desktop-connect-azure-consumption-insights/azure-consumption-insights_10.png)

Sie müssen den Wert *enrollmentNumber* durch Ihre Registrierungsnummer ersetzen. Diese Nummer finden Sie im [Azure Enterprise-Portal](https://ea.azure.com). Der Parameter *numberOfMonth* gibt die Anzahl der Monate vor dem aktuellen Datum an, die Sie einbeziehen möchten. Verwenden Sie für den aktuellen Monat 0 (null).

Sobald Sie im Fenster **Erweiterter Editor** auf **Fertig** geklickt haben, wird die Vorschau aktualisiert, und in der Tabelle werden Daten aus der angegebenen Zeitspanne angezeigt. Wählen Sie **Schließen und übernehmen** aus, und kehren Sie zum Abfrage-Editor zurück.

### <a name="step-3-move-measures-and-custom-columns-to-the-new-report"></a>Schritt 3: Measures und benutzerdefinierte Spalten in den neuen Bericht verschieben
Anschließend müssen Sie alle benutzerdefinierten Spalten oder Measures, die Sie erstellt haben, in die neue Detailtabelle verschieben. Gehen Sie wie folgt vor.

1. Öffnen Sie Editor (oder einen anderen Text-Editor).
2. Wählen Sie das Measure aus, das Sie verschieben möchten, kopieren Sie den Text aus dem Feld *Formel*, und fügen Sie ihn in Editor ein.

   ![](media/desktop-connect-azure-consumption-insights/azure-consumption-insights_11.png)
3. Benennen Sie *Abfrage1* mit dem Namen der ursprünglichen Detailtabelle um.
4. Wenn Sie neue Tabellenmeasures und benutzerdefinierte Spalten erstellen möchten, klicken Sie erst mit der rechten Maustaste auf die Tabelle und anschließend mit der linken auf **Neues Measure**. Anschließend können Sie Ihre gespeicherten Measures und Spalten ausschneiden und einfügen, um sie fertig zu stellen.

### <a name="step-4-relink-tables-that-had-relationships"></a>Schritt 4: Erneutes Verknüpfen von Tabellen mit früheren Beziehungen
Viele Dashboards verfügen über zusätzliche Tabellen, die zum Nachschlagen und Filtern verwendet werden, wie z.B. Datumstabellen oder Tabellen, die für benutzerdefinierte Projekte genutzt werden. Die meisten verbleibenden Probleme werden durch das Wiederherstellen dieser Beziehungen gelöst. Dazu gehen Sie wie folgt vor.

- Wählen Sie auf der Registerkarte **Modellierung** in **Power BI Desktop** die Option **Beziehungen verwalten** aus, um ein neues Fenster zu öffnen, in dem Sie Beziehungen im Modell verwalten können. Verknüpfen Sie Ihre Tabellen nach Bedarf erneut.

    ![](media/desktop-connect-azure-consumption-insights/azure-consumption-insights_12.png)

### <a name="step-5-verify-your-visuals-and-adjust-field-formatting-as-needed"></a>Schritt 5: Die Visuals überprüfen und die Feldformatierung nach Bedarf anpassen
Die meisten Ihrer ursprünglichen Visuals, Tabellen und Drilldowns sollten jetzt wie erwartet funktionieren. Einige kleinere Anpassungen sind jedoch möglicherweise erforderlich, um das Erscheinungsbild genau zu formatieren. Nehmen Sie sich etwas Zeit, um sich alle Dashboards und Visuals anzusehen und sicherzustellen, dass diese wie gewünscht aussehen.

## <a name="using-the-azure-consumption-and-insights-aci-api-to-get-consumption-data"></a>Abrufen von Verbrauchsdaten mithilfe der ACI-API (Azure Consumption and Insights)
Azure stellt auch die [**ACI-API (Azure Consumption and Insights)** ](https://azure.microsoft.com/blog/announcing-general-availability-of-consumption-and-charge-apis-for-enterprise-azure-customers/) bereit. Mit der ACI-API können Sie eigene benutzerdefinierte Lösungen zum Sammeln, Dokumentieren und Visualisieren von Azure-Verbrauchsinformationen erstellen.

### <a name="mapping-names-and-usage-details-between-the-portal-the-connector-and-the-api"></a>Zuordnen von Namen und Nutzungsdetails zwischen dem Portal, dem Connector und der API
Die Spalten- und Detailnamen im Azure-Portal sind in der API und im Connector ähnlich, aber nicht immer identisch. Zur Verdeutlichung finden Sie in der folgenden Tabelle Zuordnungsinformationen. Es wird außerdem angegeben, ob die Spalte veraltet ist. Weitere Informationen und Begriffsdefinitionen finden Sie im [Wörterbuch zu Abrechnungsdaten in Azure](https://docs.microsoft.com/azure/billing/billing-enterprise-api-usage-detail).

| Spaltenname im ACI-Connector/Inhaltspaket | ACI-API-Spaltenname | EA-Spaltenname | Veraltet/aus Gründen der Abwärtskompatibilität vorhanden |
| --- | --- | --- | --- |
| AccountName |accountName |Account Name |Nein |
| AccountId |accountId | |Ja |
| AcccountOwnerId |accountOwnerEmail |AccountOwnerId |Nein |
| AdditionalInfo |additionalInfo |AdditionalInfo |Nein |
| AdditionalInfold | | |Ja |
| Verbrauchte Menge |consumedQuantity |Verbrauchte Menge |Nein |
| Genutzter Dienst |consumedService |Genutzter Dienst |Nein |
| ConsumedServiceId |consumedServiceId | |Ja |
| Cost |cost |ExtendedCost |Nein |
| Kostenstelle |costCenter |Kostenstelle |Nein |
| Datum |Datum |Datum |Nein |
| Tag | |Tag |Nein |
| DepartmentName |departmentName |Department Name |Nein |
| DepartmentID |departmentId | |Ja |
| Instanzen-ID | | |Ja |
| InstanceId |instanceId |Instanzen-ID |Nein |
| Standort | | |Ja |
| Kategorie für Messung |meterCategory |Kategorie für Messung |Nein |
| Messungs-ID | | |Ja |
| Meter Name |meterName |Meter Name |Nein |
| Messbereich |meterRegion |Messbereich |Nein |
| Unterkategorie für Messung |meterSubCategory |Unterkategorie für Messung |Nein |
| MeterId |meterId |Messungs-ID |Nein |
| Month | |Month |Nein |
| Product |product |Product |Nein |
| ProductId |productId | |Ja |
| Resource Group |resourceGroup |Resource Group |Nein |
| Ressourcenspeicherort |resourceLocation |Ressourcenspeicherort |Nein |
| ResourceGroupId | | |Ja |
| ResourceLocationId |resourceLocationId | |Ja |
| ResourceRate |resourceRate |ResourceRate |Nein |
| ServiceAdministratorId |serviceAdministratorId |ServiceAdministratorId |Nein |
| ServiceInfo1 |serviceInfo1 |ServiceInfo1 |Nein |
| ServiceInfo1Id | | |Ja |
| ServiceInfo2 |serviceInfo2 |ServiceInfo2 |Nein |
| ServiceInfo2Id | | |Ja |
| Dienstbezeichner speichern |storeServiceIdentifier |Dienstbezeichner speichern |Nein |
| StoreServiceIdentifierId | | |Ja |
| Subscription Name |subscriptionName |Subscription Name |Nein |
| Tags |tags |Tags |Nein |
| TagsId | | |Ja |
| Maßeinheit |unitOfMeasure |Maßeinheit |Nein |
| Jahr | |Jahr |Nein |
| SubscriptionId |subscriptionId |SubscriptionId |Ja |
| SubscriptionGuid |subscriptionGuid |SubscriptionGuid |Nein |


## <a name="next-steps"></a>Nächste Schritte

Es gibt viele verschiedene Datenquellen, mit denen Sie über Power BI Desktop eine Verbindung herstellen können. Weitere Informationen finden Sie in den folgenden Artikeln:

* [Herstellen einer Verbindung mit den Daten von Azure Cost Management in Power BI Desktop](desktop-connect-azure-cost-management.md)
* [Was ist Power BI Desktop?](../fundamentals/desktop-what-is-desktop.md)
* [Datenquellen in Power BI Desktop](desktop-data-sources.md)
* [Strukturieren und Kombinieren von Daten mit Power BI Desktop](desktop-shape-and-combine-data.md)
* [Verbinden mit Excel in Power BI Desktop](desktop-connect-excel.md)   
* [Eingeben von Daten direkt in Power BI Desktop](desktop-enter-data-directly-into-desktop.md)   
