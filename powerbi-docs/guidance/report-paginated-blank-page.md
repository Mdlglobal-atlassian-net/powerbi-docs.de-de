---
title: Vermeiden von leeren Seiten beim Drucken paginierter Berichte
description: Leitfaden zum Entwerfen paginierter Berichte, um leere Seiten beim Drucken zu vermeiden.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.date: 01/14/2020
ms.author: v-pemyer
ms.openlocfilehash: 349459b95a815a52665e50687554f81f90a9c81b
ms.sourcegitcommit: ced8c9d6c365cab6f63fbe8367fb33e6d827cb97
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/07/2020
ms.locfileid: "78920825"
---
# <a name="avoid-blank-pages-when-printing-paginated-reports"></a>Vermeiden von leeren Seiten beim Drucken paginierter Berichte

Dieser Artikel richtet sich an Berichtsautoren, die [paginierte Power BI-Berichte](../paginated-reports/paginated-reports-report-builder-power-bi.md) entwerfen. Er enthält Empfehlungen, wie Sie leere Seiten vermeiden, wenn Ihr Bericht in ein Format mit Seitenzahlangabe – wie PDF oder Microsoft Word – exportiert oder ausgedruckt wird.

## <a name="page-setup"></a>Seiteneinrichtung

Die Formateigenschaften für Berichtsseiten legen die Ausrichtung, die Abmessungen und die Ränder von Seiten fest. Sie können folgendermaßen auf diese Berichtseigenschaften zugreifen:

- Über die **Eigenschaftenseite** eines Berichts: Klicken Sie mit der rechten Maustaste auf den dunkelgrauen Bereich außerhalb der Berichtscanvas, und wählen Sie _Berichtseigenschaften_ aus.
- Über den [Bereich **Eigenschaften**](../paginated-reports/paginated-reports-report-design-view.md#4-properties-pane): Klicken Sie auf den dunkelgrauen Bereich außerhalb der Berichtscanvas, um das Berichtsobjekt auszuwählen. Stellen Sie sicher, dass der Bereich **Eigenschaften** geöffnet ist.

Die Seite **Seiteneinrichtung** der **Eigenschaftenseite** des Berichts bietet eine benutzerfreundliche Benutzeroberfläche, in der Sie die Eigenschaften zur Seiteneinrichtung anzeigen und aktualisieren können.

![Die Abbildung zeigt das Fenster mit den Berichtseigenschaften, die Seite zur Seiteneinrichtung ist hervorgehoben.](media/report-paginated-blank-page/report-page-setup-properties.png)

Stellen Sie sicher, dass alle Eigenschaften der Seitengröße richtig konfiguriert sind:

|Eigenschaft|Empfehlung|
|---------|---------|
|Seiteneinheiten|Wählen Sie die entsprechende Einheit aus: Zoll oder Zentimeter.|
|Ausrichtung|Wählen Sie die richtige Option aus: Hochformat oder Querformat.|
|Papierformat|Wählen Sie ein Papierformat aus, oder weisen Sie benutzerdefinierte Werte für Breite und Höhe zu.|
|Ränder|Legen Sie geeignete Werte für den linken, rechten, oberen und unteren Rand fest.|
|||

## <a name="report-body-width"></a>Breite des Berichtshauptteils

Die Eigenschaften für die Seitengröße bestimmen den für Berichtsobjekte verfügbaren Platz. Bei Berichtsobjekten kann es sich um Datenbereiche, Datenvisualisierungen oder andere Berichtselemente handeln.

Ein häufiger Grund für die Ausgabe leerer Seiten ist gegeben, wenn die Breite des Berichtshauptteils _den verfügbaren Platz auf der Seite überschreitet_.

Sie können die Breite des Berichtshauptteils nur über den Bereich **Eigenschaften** anzeigen und festlegen. Klicken Sie zuerst auf einen leeren Bereich im Hauptteil des Berichts.

![Die Abbildung zeigt den Eigenschaftenbereich, die Eigenschaft „Breite des Berichtshauptteils“ ist hervorgehoben.](media/report-paginated-blank-page/report-body-properties-width.png)

Stellen Sie sicher, dass der Wert für die Breite die verfügbare Seitenbreite nicht überschreitet. Nutzen Sie die folgende Formel:

```Report body width <= Report page width - (Left margin + Right margin)```

> [!NOTE]
> Sie können die Breite des Berichtshauptteils nicht verringern, wenn sich in dem Teil, den Sie entfernen möchten, bereits Berichtsobjekte befinden. Sie müssen diese Objekte zuerst neu positionieren oder ihre Größe ändern, bevor Sie die Breite ändern können.
>
> Darüber hinaus kann sich die Breite des Berichtshauptteils automatisch erhöhen, wenn Sie neue Objekte hinzufügen oder vorhandene Objekte neu positionieren oder deren Größe ändern. Der Berichts-Designer erhöht die Breite des Hauptteils immer, um Position und Größe der darin enthaltenen Objekte zu berücksichtigen.

## <a name="report-body-height"></a>Höhe des Berichtshauptteils

Leere Seiten können auch dann ausgegeben werden, wenn im Berichtshauptteil nach dem letzten Objekt überflüssiger Platz vorhanden ist.

Es empfiehlt sich, die Höhe des Hauptteils immer zu verringern, um Leerraum zu entfernen.

![Die Abbildung zeigt einen Berichtsentwurf. Der Platz unterhalb des Datenbereichs für „Tablix“ ist als unnötig gekennzeichnet.](media/report-paginated-blank-page/report-body-remove-trailing-space.png)

## <a name="page-break-options"></a>Seitenumbruchoptionen

Jeder Datenbereich und jede Datenvisualisierung verfügt über Seitenumbruchoptionen. Sie können auf der Eigenschaftenseite oder im Bereich **Eigenschaften** auf diese Optionen zugreifen.

Stellen Sie sicher, dass die Eigenschaft **Seitenumbruch hinzufügen nach** nicht aktiviert ist, wenn sie nicht benötigt wird.

![Die Abbildung zeigt ein Eigenschaftenfenster für „Tablix“. Die Eigenschaft „Seitenumbruch hinzufügen nach“ ist aktiviert.](media/report-paginated-blank-page/data-region-page-break-option-after.png)

## <a name="consume-container-whitespace"></a>ConsumeContainerWhitespace

Wenn das Problem mit leeren Seiten weiterhin auftritt, können Sie auch versuchen, die Eigenschaft **ConsumeContainerWhitespace** des Berichts zu deaktivieren. Diese kann nur im Bereich **Eigenschaften** festgelegt werden.

![Die Abbildung zeigt den Eigenschaftenbereich, die Eigenschaft „ConsumeContainerWhitespace“ ist hervorgehoben.](media/report-paginated-blank-page/report-properties-consumecontainerwhitespace.png)

Standardmäßig ist sie aktiviert. Sie legt fest, ob der Mindestleerraum in Containern – z. B. im Berichtshauptteil oder in einem Rechteck – genutzt werden soll. Nur Leerraum rechts neben und unter dem Inhalt ist betroffen.

## <a name="printer-paper-size"></a>Papierformat im Drucker

Wenn Sie den Bericht auf Papier ausdrucken, stellen Sie sicher, dass das richtige Papierformat im Drucker eingelegt ist. Das Format des physischen Papiers muss dem [Papierformat des Berichts](#page-setup) entsprechen.

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zu diesem Artikel finden Sie in den folgenden Ressourcen:

- [Was sind paginierte Berichte in Power BI Premium? (Vorschau)](../paginated-reports/paginated-reports-report-builder-power-bi.md)
- [Paginierung in paginierten Power BI-Berichten](../paginated-reports/paginated-reports-pagination.md)
- Haben Sie Fragen? [Stellen Sie Ihre Frage in der Power BI-Community.](https://community.powerbi.com/)
- Vorschläge? [Einbringen von Ideen zur Verbesserung von Power BI](https://ideas.powerbi.com)
