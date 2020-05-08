---
title: Anpassen von QuickInfos in Power BI Desktop
description: Erstellen Sie benutzerdefinierte QuickInfos für Visualisierungen mithilfe von Drag & Drop.
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 01/15/2020
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: 93177ac56bc2d8ecfe4b85f4ab66daef6bf0f0f3
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "76161009"
---
# <a name="customize-tooltips-in-power-bi-desktop"></a>Anpassen von QuickInfos in Power BI Desktop

QuickInfos sind eine elegante Methode zum Bereitstellen von kontextbezogenen Informationen und Details zu Datenpunkten in einer Visualisierung. Die folgende Abbildung zeigt eine QuickInfo zu einem Diagramm in Power BI Desktop.

![Standard-QuickInfo](media/desktop-custom-tooltips/custom-tooltips-1.png)

Wenn eine Visualisierung erstellt wird, werden in der Standard-QuickInfo der Wert und die Kategorie Datenpunkts angezeigt. Es gibt viele Fälle, in denen es hilfreich ist, die QuickInfo-Informationen anzupassen. So können Sie etwa mehr Kontext und zusätzliche Informationen für die Benutzer bereitzustellen, die das Visual anzeigen. Mit QuickInfos können Sie zusätzliche Datenpunkte angeben, die als Teil der QuickInfo angezeigt werden.

## <a name="how-to-customize-tooltips"></a>Anpassen von QuickInfos

Zum Erstellen einer benutzerdefinierten QuickInfo ziehen Sie im Bereich **Felder** unter **Visualisierungen** ein Feld in den Bucket **QuickInfos**, wie in der folgenden Abbildung gezeigt. In der folgenden Abbildung wurden drei Felder im Bucket **QuickInfos** eingefügt.

![Hinzufügen von QuickInfo-Feldern](media/desktop-custom-tooltips/custom-tooltips-2.png)

Wenn QuickInfos zu **QuickInfos** hinzugefügt wurden und der Benutzer auf einen Datenpunkt in der Visualisierung zeigt, werden die Werte für diese Felder angezeigt.

![Benutzerdefinierte QuickInfo](media/desktop-custom-tooltips/custom-tooltips-3.png)

## <a name="customizing-tooltips-with-aggregation-or-quick-measures"></a>Anpassen von QuickInfos mit Aggregationen oder Quickmeasures

Sie können eine QuickInfo weiter anpassen, indem Sie eine Aggregationsfunktion oder ein *Quickmeasure* auswählen. Klicken Sie auf den Pfeil neben dem Bucket **QuickInfos**. Wählen Sie anschließend eine der verfügbaren Optionen aus.

![QuickInfo mit Quickmeasure](media/desktop-custom-tooltips/custom-tooltips-4.png)

Es gibt viele Methoden zum Anpassen von QuickInfos mit beliebigen Feldern in Ihrem Dataset, um schnell Informationen und Einblicke für die Benutzer bereitzustellen, die Ihre Dashboards oder Berichte anzeigen.
