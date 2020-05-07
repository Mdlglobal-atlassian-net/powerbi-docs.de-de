---
title: Hinzufügen externer Bibliotheken zu Power BI-Visuals
description: In diesem Artikel wird beschrieben, wie Sie in Power BI-Visuals externe Bibliotheken verwenden.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 02/24/2020
ms.openlocfilehash: 9df111e7545c43fe9b75784b1a95df4f37fd01e7
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "80114127"
---
# <a name="adding-external-libraries"></a>Hinzufügen von externen Bibliotheken

In diesem Artikel wird beschrieben, wie Sie in Power BI-Visuals externe Bibliotheken verwenden. Sie erfahren, wie Sie mithilfe des Codes des Power BI-Visuals externe Bibliotheken installieren, importieren und aufrufen können.

## <a name="javascript-libraries"></a>JavaScript-Bibliotheken

1. Installieren Sie mithilfe eines beliebigen Paket-Managers wie *npm* oder *yarn* eine externe JavaScript-Bibliothek.
2. Importieren Sie die erforderlichen Module mithilfe der externen Bibliothek in die Quelldateien.

>[!NOTE]
>Wenn Sie Ihrer JavaScript-Bibliothek Typisierungen hinzufügen möchten und Intellisense und Sicherheit zur Kompilierzeit wünschen, stellen Sie sicher, dass Sie das passende Paket installieren.

### <a name="installing-the-d3-library"></a>Installieren der d3-Bibliothek

Dies ist ein Beispiel der Installation der [d3-Bibliothek](https://www.npmjs.com/package/d3) und des Pakets [@types/d3](https://www.npmjs.com/package/@types/d3), für die [npm](https://www.npmjs.com/) verwendet wird.

Ein vollständiges Beispiel finden Sie im Code [Power BI-Visualisierungen](https://github.com/microsoft/powerbi-visuals-gantt/blob/master/src/gantt.ts#L29).

1. Installieren Sie die Pakete *d3* und *d3 types*.

    ```powershell
    npm install d3@5 --save
    npm install @types/d3@5 --save
    ```

2. Importieren Sie die *d3-* Bibliothek in die Dateien, von denen Sie verwendet wird, z. B. `visual.ts`.

    ```typescript
    import * as d3 from "d3";
    ```

## <a name="css-framework"></a>CSS-Framework

1. Installieren Sie mithilfe eines beliebigen Paket-Managers wie *npm* oder *yarn* ein externes CSS-Framework.
2. Fügen Sie in die Datei `.less` des Visuals die Anweisung `import` ein.

### <a name="installing-bootstrap"></a>Installieren von bootstrap

Dies ist ein Beispiel für die Installation von [bootstrap](https://www.npmjs.com/package/bootstrap) mithilfe von [npm](https://www.npmjs.com/).

Ein vollständiges Beispiel finden Sie im Code [Power BI-Visualisierungen](https://github.com/Microsoft/powerbi-visuals-sankey/blob/c8200da56913cd8b253be949a35fad0f4472b6de/style/visual.less#L32).

1. Installieren Sie das Paket *bootstrap*.

    ```powershell
    npm install bootstrap --save
    ```

2. Fügen Sie in `import` die Anweisung `visual.less` hinzu.

    ```less
    @import (less) "node_modules/bootstrap/dist/css/bootstrap.css";
    ```
