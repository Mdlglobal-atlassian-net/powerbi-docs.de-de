---
title: Ermöglichen, dass Benutzer visuelle Elemente in einem Bericht personalisieren können
description: Bieten Sie Berichtslesern die Möglichkeit, ihre eigene Ansicht eines Berichts zu erstellen, ohne ihn zu bearbeiten.
author: maggiesMSFT
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 04/09/2020
ms.author: maggies
LocalizationGroup: Reports
ms.openlocfilehash: abc936c6ea4b61e4837e05fbde110e5159296815
ms.sourcegitcommit: a199dda2ab50184ce25f7c9a01e7ada382a88d2c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/06/2020
ms.locfileid: "82867114"
---
# <a name="let-users-personalize-visuals-in-a-report"></a>Ermöglichen, dass Benutzer visuelle Elemente in einem Bericht personalisieren können

[!INCLUDE [applies-to](../includes/applies-to.md)] [!INCLUDE [yes-desktop](../includes/yes-desktop.md)] [!INCLUDE [yes-service](../includes/yes-service.md)]

Wenn Sie einen Bericht für eine breite Zielgruppe freigeben, möchten einige der Benutzer möglicherweise etwas andere Ansichten bestimmter visueller Elemente (Visuals) sehen. Vielleicht möchten sie das tauschen, was auf der Achse steht, den visuellen Typ ändern oder der QuickInfo etwas hinzufügen. Es ist schwierig, ein visuelles Element zu erstellen, das die Anforderungen aller Benutzer erfüllt. Mit dieser neuen Funktion können Sie Ihre Anwender in die Lage versetzen, visuelle Elemente zu untersuchen und zu personalisieren. Sie können das jeweilige visuelle Element auf gewünschte Weise anpassen und als Lesezeichen speichern, um zu ihm zurückzukehren. Sie müssen keine Berechtigung zum Bearbeiten des Bericht haben oder sich an den Berichtsautor wenden, um eine Änderung zu veranlassen.

:::image type="content" source="media/power-bi-personalize-visuals/power-bi-personalize-visual.png" alt-text="Personalisieren eines visuellen Elements":::
 
## <a name="what-report-consumers-can-change"></a>Was Berichtsanwender ändern können

Dieses Feature ermöglicht es Anwendern, über eine Ad-hoc-Untersuchung von visuellen Elementen in einem Power BI-Bericht weitere Einblicke zu gewinnen. Das Feature eignet sich ideal für Berichtersteller, die grundlegende Untersuchungsszenarios für die Leser ihrer Berichte ermöglichen möchten. Nachfolgend sind Änderungen aufgeführt, die von Berichtslesern vorgenommen werden können:

- Ändern des Visualisierungstyps
- Austauschen eines Measures oder einer Dimension
- Hinzufügen oder Entfernen einer Legende
- Vergleichen von mehreren Measures
- Ändern von Aggregationen usw.

Diese Funktionalität ermöglicht nicht nur neue Auswertungsfunktionen. Sie eröffnet für Anwender auch Möglichkeiten, ihre Änderungen erfassen und freigeben zu können:

- Erfassen ihrer Änderungen
- Freigeben ihrer Änderungen
- Zurücksetzen aller Änderungen, die sie an einem Bericht vorgenommen haben
- Zurücksetzen aller Änderungen, die sie an einem visuellen Element vorgenommen haben
- Löschen ihrer letzten Änderungen

## <a name="turn-on-the-preview-feature"></a>Aktivieren des Vorschaufeatures

Da sich dieses Feature in der Vorschauphase befindet, müssen Sie zuerst den Featureschalter aktivieren. Öffnen Sie **Datei** > **Optionen und Einstellungen** > **Optionen**. Vergewissern Sie sich, dass unter **Globale** Einstellungen > **Featurevorschau** die Option **Visuals personalisieren** aktiviert ist.

:::image type="content" source="media/power-bi-personalize-visuals/power-bi-preview-personalize-visual.png" alt-text="„Visuals personalisieren“ aktivieren":::

Möglicherweise müssen Sie Power BI Desktop neu starten, um das Feature in den Einstellungen für die aktuelle Datei zu sehen.

## <a name="enable-personalization-in-a-report"></a>Aktivieren von Personalisierung in einem Bericht

Nachdem Sie den Vorschauschalter aktiviert haben, müssen Sie ihn speziell für die Berichte aktivieren, für die Anwender in der Lage sein sollen, visuelle Elemente (Visuals) personalisieren zu können.

Dieses Feature können Sie entweder in Power BI Desktop oder im Power BI-Dienst aktivieren.

### <a name="in-power-bi-desktop"></a>Power BI Desktop

Um das Feature in Power BI Desktop zu aktivieren, wechseln Sie zu **Datei** > **Optionen und Einstellungen** > **Optionen** > **Aktuelle Datei** > **Berichtseinstellungen**. Stellen Sie sicher, dass **Visuals personalisieren (Vorschau)** aktiviert ist.

:::image type="content" source="media/power-bi-personalize-visuals/power-bi-report-settings-personalize-visual.png" alt-text="Aktivieren von Personalisierung in einem Bericht":::

### <a name="in-the-power-bi-service"></a>Im Power BI-Dienst

Um das Feature stattdessen im Power BI-Dienst zu aktivieren, wechseln Sie zu **Einstellungen** für Ihren Bericht.

:::image type="content" source="media/power-bi-personalize-visuals/power-bi-report-service-settings-personalize-visual.png" alt-text="Berichtseinstellungen im Power BI-Dienst":::

Aktivieren Sie **Visuals personalisieren (Vorschau)**  > **Speichern**.

:::image type="content" source="media/power-bi-personalize-visuals/power-bi-report-service-personalize-visual.png" alt-text="„Visuals personalisieren“ im Dienst aktivieren":::

## <a name="select-visuals-that-can-be-personalized"></a>Auswählen von visuellen Elementen, die personalisiert werden können

Wenn Sie diese Einstellung für einen bestimmten Bericht aktivieren, können standardmäßig alle visuellen Elemente in diesem Bericht personalisiert werden. Wenn Sie nicht möchten, dass alle visuellen Elemente personalisiert werden können, aktivieren oder deaktivieren Sie die Einstellung pro visuellem Element.

Wählen Sie das visuelle Element aus > wählen Sie **Format** im Bereich **Visualisierungen** aus > erweitern Sie **Visualheader**.

:::image type="content" source="media/power-bi-personalize-visuals/power-bi-format-visual-header-personalize.png" alt-text="„Visualheader“ auswählen":::
 
Verschieben Sie **Visual personalisieren** >  **Ein** oder **Aus**.

:::image type="content" source="media/power-bi-personalize-visuals/power-bi-format-visual-personalize-on-off.png" alt-text="Schieberegler „Visual personalisieren“ aktivieren oder deaktivieren":::

## <a name="personalize-visuals-in-the-power-bi-service"></a>Personalisieren von visuellen Elementen (Visuals) im Power BI-Dienst

Durch Personalisierung eines visuellen Elements können Ihre Anwender Ihre Daten auf viele Arten untersuchen, ohne die Leseansicht des Berichts zu verlassen. Die folgenden Beispiele zeigen verschiedene Arten, wie Benutzer eine Visualisierung ändern können, um deren Anforderungen zu erfüllen. 

1. Öffnen Sie einen Bericht in der Leseansicht im Power BI-Dienst.

2. Wählen Sie in der oberen rechten Ecke des visuellen Elements das Symbol **Dieses Visual personalisieren** ![Symbol für „Dieses Visual personalisieren“](media/power-bi-personalize-visuals/power-bi-personalize-visual-icon.png) aus. 

### <a name="change-the-visualization-type"></a>Ändern des Visualisierungstyps

Sie können die Visualisierung in einer anderen Darstellung anzeigen, indem Sie den **Visualisierungstyp** ändern.

:::image type="content" source="media/power-bi-personalize-visuals/power-bi-personalize-change-visual-type.png" alt-text="Visualisierungstyp ändern":::
 
### <a name="swap-out-a-measure-or-dimension"></a>Austauschen eines Measures oder einer Dimension
Sie können ein Measure oder eine Dimension auf der X-Achse ersetzen, indem Sie das Feld auswählen, das Sie ersetzen möchten, und dann ein anderes Measure oder eine andere Dimension auswählen.

:::image type="content" source="media/power-bi-personalize-visuals/power-bi-personalize-change-axis.png" alt-text="Ändern der Achse":::
 
### <a name="add-or-remove-a-legend"></a>Hinzufügen oder Entfernen einer Legende
Durch Hinzufügen einer Legende können Sie ein visuelles Element auf Basis einer Kategorie farblich codieren. Sie können die kategorische Farbcodierung deaktivieren, indem Sie im Bereich **Personalisieren** den Inhalt des Felds **Legende** löschen. 

:::image type="content" source="media/power-bi-personalize-visuals/power-bi-personalize-change-legend.png" alt-text="Die Legende hinzufügen oder entfernen":::

### <a name="compare-two-or-more-different-measures"></a>Vergleichen von mehreren unterschiedlichen Measures
Sie können Werte für verschiedene Measures vergleichen und gegenüberstellen, indem Sie das +-Symbol verwenden, um mehrere Measures für ein visuelles Element hinzuzufügen.

:::image type="content" source="media/power-bi-personalize-visuals/power-bi-personalize-compare-measures.png" alt-text="Measures vergleichen":::

### <a name="change-aggregations"></a>Ändern von Aggregationen
Sie können das Berechnen eines Measures ändern, indem Sie die Aggregation im Bereich **Personalisieren** ändern.

:::image type="content" source="media/power-bi-personalize-visuals/power-bi-personalize-change-aggregation.png" alt-text="Aggregationen ändern":::

### <a name="capture-changes"></a>Erfassen von Änderungen 
Erfassen Sie Ihre Änderungen mithilfe persönlicher Lesezeichen, damit Sie zu Ihrer personalisierten Ansicht zurückkehren können. 

:::image type="content" source="media/power-bi-personalize-visuals/power-bi-personalize-bookmark.png" alt-text="Ein Lesezeichen erstellen":::
 
Sie können das Lesezeichen auch als Standardansicht festlegen.

### <a name="share-changes"></a>Freigeben von Änderungen 
Wenn Sie die Berechtigungen für Lesen und erneutes Freigeben haben, können Sie beim Freigeben des Berichts festlegen, dass Ihre Änderungen einbezogen werden sollen.

:::image type="content" source="media/power-bi-personalize-visuals/power-bi-personalize-share-changes.png" alt-text="Änderungen freigeben":::
 
### <a name="reset-all-your-changes-to-a-report"></a>Zurücksetzen aller Änderungen, die an einem Bericht vorgenommen wurden

Wählen Sie **Auf Standardwert zurücksetzen** aus, um alle Änderungen, die Sie am Bericht vorgenommen haben, zu entfernen und den Bericht auf die Ansicht zurückzusetzen, in der der Autor ihn zuletzt gespeichert hat.

:::image type="content" source="media/power-bi-personalize-visuals/power-bi-personalize-reset-all.png" alt-text="Alle Änderungen zurücksetzen":::
 
### <a name="reset-all-your-changes-to-a-visual"></a>Zurücksetzen aller Änderungen, die an einem visuellen Element vorgenommen wurden

Wählen Sie **Dieses Visual zurücksetzen** aus, um alle Änderungen, die Sie an einem bestimmten visuellen Element vorgenommen haben, zu entfernen und das Element auf die Ansicht zurückzusetzen, in der der Autor es zuletzt gespeichert hat.

:::image type="content" source="media/power-bi-personalize-visuals/power-bi-personalize-reset-visual.png" alt-text="Alle Änderungen an visuellen Elementen zurücksetzen":::
 
### <a name="clear-recent-changes"></a>Löschen der letzten Änderungen

Wählen Sie das Radierersymbol aus, um alle letzten Änderungen zu löschen, die Sie vorgenommen haben, seit Sie den Bereich **Personalisieren** geöffnet hatten.  

:::image type="content" source="media/power-bi-personalize-visuals/power-bi-personalize-revert-changes.png" alt-text="Die letzten Änderungen zurücknehmen":::

## <a name="limitations-and-known-issues"></a>Einschränkungen und bekannte Probleme

Derzeit gibt es für das Feature einige Einschränkungen, die zu beachten sind.

- Dieses Feature wird für Einbettungsszenarios nicht unterstützt, wozu auch Veröffentlichung im Web gehört.
- Benutzeruntersuchungen bleiben nicht automatisch erhalten. Sie müssen Ihre Ansicht als persönliches Lesezeichen speichern, um Ihre Änderungen zu erfassen.
- Sie können visuelle Elemente nicht ändern, wenn Sie mit den mobilen Power BI-Apps arbeiten. Jeder visuelle Änderung, die Sie im Power BI-Dienst in einem persönlichen Lesezeichen speichern, wird jedoch in den mobilen Apps berücksichtigt.

Es gibt auch einige bekannte Probleme, an deren Beseitigung wir derzeit arbeiten:

- Ein Hinzufügen von Hierarchie wird nicht unterstützt. Sie müssen die einzelnen untergeordneten Elemente hinzufügen.
- Eine Datumshierarchie kann nicht in ein Datum oder umgekehrt geändert werden. 
- Mit persönlichen Lesezeichen erhalten Sie möglicherweise Ergebnisse, die sich je nach der Sequenz, die Sie auswählen, geringfügig unterscheiden. Abweichungen sind möglich, da nicht der vollständige Status des Berichts, sondern nur die Änderungen erfasst werden, die vorgenommen wurden. Die Problemumgehung besteht darin, **Auf Standardwert zurücksetzen** und dann das Lesezeichen auszuwählen, das Sie anzeigen möchten. 

## <a name="next-steps"></a>Nächste Schritte

Probieren Sie die neue Personalisierungsumgebung für visuelle Elemente (Visuals) aus. Senden Sie uns auf der [Power BI Ideas-Website](https://ideas.powerbi.com/forums/265200-power-bi) Feedback zu diesem Feature, und lassen Sie uns wissen, wie wir es weiter verbessern können. 

Weitere Fragen? [Wenden Sie sich an die Power BI-Community](https://community.powerbi.com/)

