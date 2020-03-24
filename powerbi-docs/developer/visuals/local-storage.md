---
title: API für lokalen Speicher in Power BI-Visuals
description: In diesem Artikel wird beschrieben, wie Sie die Power BI-Visuals-API verwenden, um Zugriff auf den lokalen Browserspeicher zu erhalten.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: rkarlin
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: reference
ms.date: 01/21/2019
ms.openlocfilehash: e2cb11ea9be85916e6b5557e7933f6a6b5a7159a
ms.sourcegitcommit: 6bbc3d0073ca605c50911c162dc9f58926db7b66
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/14/2020
ms.locfileid: "79380592"
---
# <a name="local-storage-api"></a>API für lokalen Speicher

Die API für lokalen Speicher ist eine API, die ein Visual nutzen kann, um beim Host das Speichern oder Laden von Daten aus dem Gerätespeicher anzufordern. Sie ist dahingehend isoliert, dass der Speicherzugriff zwischen verschiedenen Visualtypen getrennt wird.

## <a name="sample"></a>Beispiel

Wenn das benutzerdefinierte Visual bei jedem Aufruf der Aktualisierungsmethode einen Zähler erhöhen soll, der Zählerwert aber gleichzeitig beibehalten und nicht bei jedem Visualstart zurückgesetzt werden soll:

```typescript
export class Visual implements IVisual {
        // ...
        private updateCountName: string = 'updateCount';
        private updateCount: number;
        private storage: ILocalVisualStorageService;
        // ...

        constructor(options: VisualConstructorOptions) {
            // ...
            this.storage = options.host.storageService;
            // ...

            this.storage.get(this.updateCountName).then(count =>
            {
                this.updateCount = +count;
            })
            .catch(() =>
            {
                this.updateCount = 0;
                this.storage.set(this.updateCountName, this.updateCount.toString());
            });
            // ...
        }

        public update(options: VisualUpdateOptions) {
            // ...
            this.updateCount++;
            this.storage.set(this.updateCountName, this.updateCount.toString());
            // ...
        }
}
```

## <a name="known-limitations-and-issues"></a>Bekannte Einschränkungen und Probleme

Die API für lokalen Speicher ist standardmäßig nicht für Power BI-Visuals aktiviert. Wenn Sie die API für Ihr Power BI-Visual aktivieren möchten, senden Sie eine Anfrage an das Supportteam für Power BI-Visuals (`pbicvsupport@microsoft.com`).  
**Bitte beachten Sie, dass Ihr Visual in [AppSource](https://appsource.microsoft.com/en-us/marketplace/apps?product=power-bi-visuals) verfügbar und [zertifiziert](https://powerbi.microsoft.com/en-us/documentation/powerbi-custom-visuals-certified/) sein sollte.**
