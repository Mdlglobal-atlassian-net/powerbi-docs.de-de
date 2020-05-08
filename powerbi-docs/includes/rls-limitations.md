---
author: davidiseminger
ms.service: powerbi
ms.topic: include
ms.date: 01/31/2020
ms.author: davidi
ms.openlocfilehash: b67025de5e2a70876a31fd42e22c9572403288fa
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "77464387"
---
## <a name="limitations"></a>Einschränkungen

Hier finden Sie aktuelle Einschränkungen für die Sicherheit auf Zeilenebene für Cloudmodelle:

* Wenn Sie bereits Rollen und Regeln im Power BI-Dienst definiert haben, müssen Sie diese in Power BI Desktop neu erstellen.

* Sie können Sicherheit auf Zeilenebene (Row Level Security, RLS) nur auf den mithilfe von Power BI Desktop erstellten Datasets definieren. Wenn Sie RLS für mit Excel erstellte Datasets aktivieren möchten, müssen Sie Ihre Dateien zunächst in PBIX-Dateien (Power BI Desktop) konvertieren. [Erfahren Sie mehr](../desktop-import-excel-workbooks.md).

* Es werden nur Import- und DirectQuery-Verbindungen unterstützt. Live-Verbindungen zu Analysis Services werden im lokalen Modell verarbeitet.

## <a name="known-issues"></a>Bekannte Probleme

Wenn Sie versuchen, einen Bericht in Power BI Desktop zu veröffentlichen, der zuvor bereits veröffentlicht wurde, erhalten Sie eine Fehlermeldung. Dieses Problem ist bekannt. Das Szenario sieht folgendermaßen aus:

1. Anna verfügt über ein Dataset, das im Power BI-Dienst veröffentlicht und für RLS konfiguriert wurde.

1. Anna aktualisiert den Bericht in Power BI Desktop und veröffentlicht ihn erneut.

1. Anna erhält eine Fehlermeldung.

**Problemumgehung:** Veröffentlichen Sie die Power BI Desktop-Datei erneut im Power BI-Dienst, bis dieses Problem behoben ist. Sie erreichen dies, indem Sie auf **Daten abrufen** > **Dateien** klicken.
