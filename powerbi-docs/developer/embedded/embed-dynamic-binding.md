---
title: Verbinden eines Berichts mit einem Dataset über die dynamische Bindung
description: Erfahren Sie, wie ein Bericht mithilfe von dynamischer Bindung eingebettet wird.
author: KesemSharabi
ms.author: kesharab
ms.topic: conceptual
ms.service: powerbi
ms.subservice: powerbi-developer
ms.date: 11/07/2019
ms.openlocfilehash: e2c59ba84700aaf83c4cc9d16d009696c42dfc54
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "80114587"
---
# <a name="connect-a-report-to-a-dataset-using-dynamic-binding"></a>Verbinden eines Berichts mit einem Dataset über die dynamische Bindung 

Sie können die dynamische Bindung verwenden, wenn ein Bericht mit einem Dataset verbunden ist. Die Verbindung zwischen dem Bericht und dem Dataset wird als *Bindung* bezeichnet. Wenn die Bindung nicht vorher, sondern während der Einbettung bestimmt wird, wird sie als dynamische Bindung bezeichnet.

Wenn Sie einen Power BI-Bericht mithilfe von *dynamischer Bindung* einbetten, können Sie denselben Bericht abhängig von den Anmeldeinformationen des Benutzers mit unterschiedlichen Datasets verbinden.

Dies bedeutet, dass Sie je nach Dataset, mit dem eine Verbindung hergestellt wurde, mit demselben Bericht unterschiedliche Informationen anzeigen können. Beispielsweise kann ein Bericht, in dem Werte zum Verkauf im Einzelhandel angezeigt werden, mit Datasets verschiedener Händler verbunden werden und unterschiedliche Ergebnisse liefern. Dies hängt davon ab, mit welchen Datasets der Händler der Bericht verknüpft ist.

Bericht und Dataset müssen sich dabei nicht im gleichen Arbeitsbereich befinden. Beide Arbeitsbereiche (der mit dem Bericht und der mit dem Dataset) müssen einer [Kapazität](azure-pbie-create-capacity.md) zugewiesen sein.

Stellen Sie im Rahmen des Einbettungsprozesses sicher, dass Sie ein *Token mit ausreichenden Berechtigungen generieren* und das *Konfigurationsobjekt anpassen*.

## <a name="generating-a-token-with-sufficient-permissions"></a>Erstellen eines Tokens mit ausreichenden Berechtigungen

Dynamische Bindung wird sowohl für das *Einbetten für Ihre Organisation* als auch für das *Einbetten für Ihre Kunden* unterstützt. In der folgenden Tabelle finden Sie Informationen zu beiden Szenarios.

|Scenario  |Datenbesitz  |Token  |Anforderungen  |
|---------|---------|---------|---------|
|*Einbetten für Ihre Organisation*    |Der Benutzer besitzt die Daten         |Zugriffstoken für Power BI-Benutzer         |Der Benutzer, dessen Azure AD-Token verwendet wird, muss über die erforderlichen Berechtigungen für alle Artefakte verfügen.         |
|*Einbetten für Ihre Kunden*     |Die App besitzt die Daten         |Zugriffstoken für Benutzer, die kein Power BI verwenden         |Es muss Berechtigungen sowohl für den Bericht als auch für das dynamisch gebundene Dataset umfassen. Verwenden Sie die [API zum Generieren eines Einbettungstokens für mehrere Elemente](embed-sample-for-customers.md#multiEmbedToken), um ein Einbettungstoken zu generieren, das mehrere Artefakte unterstützt.         |

## <a name="adjusting-the-config-object"></a>Anpassen des Konfigurationsobjekts
Fügen Sie dem Konfigurationsobjekt `datasetBinding` hinzu. Verwenden Sie das folgende Beispiel als Referenz.

```javascript
var config = {
    type: 'report',
    tokenType: models.TokenType.Embed,
    accessToken: accessToken,
    embedUrl: embedUrl,
    id: "reportId", // The wanted report id
    permissions: permissions,

    // -----  Adjustment required for dynamic binding ---- //
    datasetBinding: {
        datasetId: "notOriginalDatasetId",  // </The wanted dataset id
    }
    // ---- End of dynamic binding adjustment ---- //
};

// Get a reference to the embedded report HTML element
var embedContainer = $('#embedContainer')[0];

// Embed the report and display it within the div container
var report = powerbi.embed(embedContainer, config);
```

## <a name="next-steps"></a>Nächste Schritte

Wenn Sie gerade erst in das Einbetten in Power BI einsteigen, arbeiten Sie diese Tutorials durch, um zu erfahren, wie Sie Power BI-Inhalte einbetten können:
* [Tutorial: Einbetten von Power BI-Inhalten in eine Anwendung für Ihre Kunden](embed-sample-for-customers.md)
* [Tutorial: Einbetten von Power BI-Inhalten in eine Anwendung für Ihre Organisation](embed-sample-for-your-organization.md)