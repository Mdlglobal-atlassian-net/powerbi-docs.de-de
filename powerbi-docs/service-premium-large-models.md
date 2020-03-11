---
title: Große Modelle in Power BI Premium (Vorschauversion)
description: Mit dem Feature für große Modelle können Datasets in Power BI Premium mehr als 10 GB groß werden.
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 03/03/2020
LocalizationGroup: Premium
ms.openlocfilehash: 2c984abaec40028fb01affa8ff7bf0bf87cdd616
ms.sourcegitcommit: d55d3089fcb3e78930326975957c9940becf2e76
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/04/2020
ms.locfileid: "78260874"
---
# <a name="large-models-in-power-bi-premium-preview"></a>Große Modelle in Power BI Premium (Vorschauversion)

Power BI-Datasets können Daten für eine optimierte Abfrageleistung in einem stark komprimierten In-Memory-Cache speichern. Dadurch wird bei großen Datasets eine schnellere Benutzerinteraktion ermöglicht. Mit dem Feature für große Modelle können Datasets in Power BI Premium mehr als 10 GB groß werden. Die Größe des Datasets ist durch die Power BI Premium-Kapazität beschränkt. Dies ist mit der Funktionsweise von Modellgrößenbeschränkungen in Azure Analysis Services vergleichbar. Weitere Informationen zu Kapazitätsgrößen in Power BI Premium finden Sie unter „Kapazitätsknoten“. Sie können große Modelle für alle Premium P- und eingebettete A-SKUs einrichten. Sie funktionieren jedoch nur mit den [neuen Arbeitsbereichen](service-create-the-new-workspaces.md).

Große Modelle haben keinen Einfluss auf die PBIX-Uploadgröße. Diese ist weiterhin auf 10 GB beschränkt. Stattdessen werden Datasets bei der Aktualisierung im Dienst über 10 GB hinaus vergrößert. Mit der inkrementellen Aktualisierung können Sie ein Dataset so konfigurieren, dass es größer als 10 GB wird.

## <a name="enable-large-models"></a>Aktivieren von großen Modellen

Führen Sie die folgenden Schritte aus, um ein Dataset zu erstellen, das größer als 10 GB wird:

1. Erstellen Sie ein Dataset in Power BI Desktop, und konfigurieren Sie eine [inkrementelle Aktualisierung](service-premium-incremental-refresh.md).

1. Veröffentlichen Sie das Dataset im Power BI Premium-Dienst.

1. Aktivieren Sie das Dataset für große Modelle, indem Sie die unten aufgeführten PowerShell-Cmdlets ausführen. Durch diese Cmdlets speichert Power BI das Dataset in Azure Files Premium, sodass die maximale Größe von 10 GB nicht erzwungen wird.

1. Starten Sie eine Aktualisierung, um historische Daten basierend auf der Richtlinie für die inkrementelle Aktualisierung zu laden. Bei der ersten Aktualisierung kann das Laden der historischen Daten einige Zeit in Anspruch nehmen. Nachfolgende Aktualisierungen sollten dann schneller gehen, da Sie inkrementell ausgeführt werden.

### <a name="powershell-cmdlets"></a>PowerShell-Cmdlets

Aktivieren Sie in der aktuellen Version der großen Modelle über PowerShell-Cmdlets, dass das Dataset in Files Premium gespeichert wird. Zum Ausführen der PowerShell-Cmdlets benötigen Sie Berechtigungen als Kapazitäts- und Arbeitsbereichadministrator.

1. Suchen Sie die Dataset-ID (GUID). Die ID finden Sie auf der Registerkarte **Datasets** des Arbeitsbereichs unter den Dataseteinstellungen in der URL.

    ![Dataset-GUID](media/service-premium-large-models/dataset-guid.png)

1. Installieren Sie in der Eingabeaufforderung für den PowerShell-Administrator das Modul [MicrosoftPowerBIMgmt](/powershell/module/microsoftpowerbimgmt.data/).

    ```powershell
    Install-Module -Name MicrosoftPowerBIMgmt
    ```

1. Führen Sie die folgenden Cmdlets aus, um sich anzumelden und den Speichermodus des Datasets zu überprüfen.

    ```powershell
    Login-PowerBIServiceAccount

    (Get-PowerBIDataset -Scope Organization -Id <Dataset ID> -Include actualStorage).ActualStorage
    ```

    Es sollte die folgende Antwort ausgegeben werden. Als Speichermodus ist „ABF“ (Analysis Services-Sicherungsdatei) ausgewählt. Das ist die Standardeinstellung.

    ```
    Id                   StorageMode

    --                   -----------

    <Dataset ID>         Abf
    ```

1. Führen Sie die folgenden Cmdlets aus, um den Speichermodus auf Files Premium festzulegen, und überprüfen Sie es. Die Konvertierung in Files Premium kann einige Sekunden in Anspruch nehmen.

    ```powershell
    Set-PowerBIDataset -Id <Dataset ID> -TargetStorageMode PremiumFiles

    (Get-PowerBIDataset -Scope Organization -Id <Dataset ID> -Include actualStorage).ActualStorage
    ```

    Es sollte die folgende Antwort ausgegeben werden. Der Speichermodus ist jetzt auf Files Premium festgelegt.

    ```
    Id                   StorageMode
    
    --                   -----------
    
    <Dataset ID>         PremiumFiles
    ```

Sie können den Status der Dataset-Konvertierungen in und aus Files Premium mithilfe des [Get-PowerBIWorkspaceMigrationStatus](/powershell/module/microsoftpowerbimgmt.workspaces/get-powerbiworkspacemigrationstatus)-Cmdlets überprüfen.

## <a name="dataset-eviction"></a>Entfernen von Datasets

Power BI verwendet die dynamische Speicherverwaltung, um inaktive Datasets aus dem Arbeitsspeicher zu entfernen. Power BI entfernt Datasets, sodass zur Bearbeitung von Benutzeranfragen andere Datasets geladen werden können. Durch die dynamische Speicherverwaltung ist es möglich, dass die Summe der Datasetgrößen erheblich größer als der für die Kapazität verfügbare Arbeitsspeicher sein kann, ein einzelnes Dataset muss jedoch in den Arbeitsspeicher passen. Weitere Informationen zur dynamischen Speicherverwaltung finden Sie unter [Funktionsweise von Kapazitäten](service-premium-what-is.md#how-capacities-function).

Sie sollten berücksichtigen, welche Auswirkung die Entfernung auf große Modelle hat. Obwohl das Dataset relativ schnell geladen wird, kann es für die Benutzer zu einer spürbaren Verzögerung kommen, wenn sie darauf warten müssen, dass große entfernte Datasets neu geladen werden. Aus diesem Grund ist das Feature für große Modelle in seiner jetzigen Form in erster Linie für Kapazitäten vorgesehen, die für Enterprise BI-Anforderungen dediziert sind, und nicht für solche, die mit Self-Service-BI-Anforderungen kombiniert sind. Bei Kapazitäten, die für Enterprise BI-Anforderungen dediziert sind, kommt es wesentlich seltener vor, dass Datasets entfernt werden und neu geladen werden müssen. Kapazitäten für Self-Service-BI können andererseits viele kleine Datasets enthalten, die häufiger in den oder aus dem Arbeitsspeicher geladen werden.

## <a name="checking-dataset-size"></a>Überprüfen der Datasetgröße

Nach dem Laden historischer Daten können Sie [SSMS](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms) über den [XMLA-Endpunkt](service-premium-connect-tools.md) verwenden, um die geschätzte Datasetgröße im Fenster „Modelleigenschaften“ zu überprüfen.

![Geschätzte Datasetgröße](media/service-premium-large-models/estimated-dataset-size.png)

Sie können die Größe des Datasets ebenfalls überprüfen, indem Sie die folgenden DMV-Abfragen aus SSMS ausführen. Wenn Sie die Spalten DICTIONARY\_SIZE und USED\_SIZE aus der Ausgabe addieren, erhalten Sie die Datasetgröße in Bytes.

```sql
SELECT * FROM SYSTEMRESTRICTSCHEMA
($System.DISCOVER_STORAGE_TABLE_COLUMNS,
 [DATABASE_NAME] = '<Dataset Name>') //Sum DICTIONARY_SIZE (bytes)

SELECT * FROM SYSTEMRESTRICTSCHEMA
($System.DISCOVER_STORAGE_TABLE_COLUMN_SEGMENTS,
 [DATABASE_NAME] = '<Dataset Name>') //Sum USED_SIZE (bytes)
```

## <a name="limitations-and-considerations"></a>Einschränkungen und Überlegungen

Berücksichtigen Sie bei der Verwendung großer Modelle die folgenden Einschränkungen:

- **Verwenden eigener Verschlüsselungsschlüssel – BYOK-Verschlüsselung**: Für Files Premium aktivierte Datasets werden nicht durch [BYOK](service-encryption-byok.md) verschlüsselt.
- **Multi-Geo-Unterstützung**: Für Files Premium aktivierte Datasets schlagen bei Kapazitäten fehl, bei denen [Multi-Geo](service-admin-premium-multi-geo.md) ebenfalls aktiviert ist.

- **Herunterladen von Dateien in Power BI Desktop**: Wenn ein Dataset in Files Premium gespeichert wird, tritt beim Herunterladen als [PBIX](service-export-to-pbix.md)-Datei ein Fehler auf.
- **Unterstützte Regionen**: Große Modelle werden in allen Azure-Regionen unterstützt, die Storage Premium-Dateien unterstützen. Weitere Informationen finden Sie unter [Verfügbare Produkte nach Region](https://azure.microsoft.com/global-infrastructure/services/?products=storage) und in der Tabelle im nachfolgenden Abschnitt.


## <a name="availability-in-regions"></a>Verfügbarkeit nach Region

Große Modelle in Power BI sind nur in bestimmten Azure-Regionen verfügbar, die [Azure Files Storage Premium](https://docs.microsoft.com/azure/storage/files/storage-files-planning#file-share-performance-tiers) unterstützen.

In der folgenden Liste sind Regionen aufgeführt, in denen große Modelle in Power BI verfügbar sind. In Regionen, die nicht in der folgenden Liste enthalten sind, werden große Modelle nicht unterstützt:


|Azure-Region  |Abkürzung der Azure-Region  |
|---------|---------|
|Australien, Osten     | australiaeast        |
|Australien, Südosten     | australiasoutheast        |
|USA, Mitte     | centralus        |
|Asien, Osten     | eastasia        |
|USA, Osten     | eastus        |
|USA, Osten 2     | eastus2        |
|Japan, Osten     | japaneast        |
|Japan, Westen     | japanwest        |
|Südkorea, Mitte     | koreacentral        |
|Südkorea, Süden     | koreasouth        |
|USA, Norden-Mitte     | northcentralus        |
|Europa, Norden     | northeurope        |
|USA, Süden-Mitte     | southcentralus        |
|Asien, Südosten     | southeastasia        |
|Vereinigtes Königreich, Süden     | uksouth        |
|Vereinigtes Königreich, Westen     | ukwest        |
|Europa, Westen     | westeurope        |
|USA, Westen     | westus        |
|USA, Westen 2     | westus2        |



## <a name="next-steps"></a>Nächste Schritte

Über die folgenden Links können Sie auf nützliche Informationen für die Arbeit mit großen Modellen zugreifen:

* [Azure Files Storage Premium](https://docs.microsoft.com/azure/storage/files/storage-files-planning#file-share-performance-tiers)
* [Konfigurieren von Multi-Geo-Unterstützung für Power BI Premium](service-admin-premium-multi-geo.md)
* [Verwenden eigener Verschlüsselungsschlüssel für Power BI](service-encryption-byok.md)
* [Funktionsweise von Kapazitäten](service-premium-what-is.md#how-capacities-function)
* [Inkrementelle Aktualisierung](service-premium-incremental-refresh.md)