---
title: Ermöglichen, dass Benutzer visuelle Elemente in einem Bericht personalisieren können
description: Bieten Sie Berichtslesern die Möglichkeit, ihre eigene Ansicht eines Berichts zu erstellen, ohne ihn zu bearbeiten.
author: maggiesMSFT
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 05/09/2020
ms.author: maggies
LocalizationGroup: Reports
ms.openlocfilehash: ab232d4e5b6d17e7f20ed8a41875ca47693eb285
ms.sourcegitcommit: 21b06e49056c2f69a363d3a19337374baa84c83f
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/15/2020
ms.locfileid: "83407587"
---
# <a name="let-users-personalize-visuals-in-a-report"></a>Ermöglichen, dass Benutzer visuelle Elemente in einem Bericht personalisieren können

[!INCLUDE [applies-to](../includes/applies-to.md)] [!INCLUDE [yes-desktop](../includes/yes-desktop.md)] [!INCLUDE [yes-service](../includes/yes-service.md)]

Wenn Sie einen Bericht für eine breite Zielgruppe freigeben, möchten einige der Benutzer möglicherweise etwas andere Ansichten bestimmter visueller Elemente (Visuals) sehen. Vielleicht möchten sie das tauschen, was auf der Achse steht, den visuellen Typ ändern oder der QuickInfo etwas hinzufügen. Es ist schwierig, ein visuelles Element zu erstellen, das die Anforderungen aller Benutzer erfüllt. Mit dieser neuen Funktion können Sie Ihre Anwender in die Lage versetzen, visuelle Elemente zu untersuchen und zu personalisieren. Sie können das jeweilige visuelle Element auf gewünschte Weise anpassen und als Lesezeichen speichern, um zu ihm zurückzukehren. Sie müssen keine Berechtigung zum Bearbeiten des Bericht haben oder sich an den Berichtsautor wenden, um eine Änderung zu veranlassen.

:::image type="content" source="media/power-bi-personalize-visuals/power-bi-personalize-visual.png" alt-text="Personalisieren eines visuellen Elements":::
 
## <a name="what-report-consumers-can-change"></a>Was Berichtsanwender ändern können

Dieses Feature ermöglicht es Anwendern, über eine Ad-hoc-Untersuchung von visuellen Elementen in einem Power BI-Bericht weitere Einblicke zu gewinnen. Informationen für Endbenutzer zur Verwendung dieses Features finden Sie unter [Personalisieren von Visuals in einem Bericht](../consumer/end-user-personalize-visuals.md). Es eignet sich hervorragend für Berichtersteller, die einfache Untersuchungsszenarios für die Leser ihrer Berichte aktivieren möchten. Nachfolgend sind Änderungen aufgeführt, die von Berichtslesern vorgenommen werden können:

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

[Personalisieren von Visuals in einem Bericht](../consumer/end-user-personalize-visuals.md)     

Probieren Sie die neue Personalisierungsumgebung für visuelle Elemente (Visuals) aus. Senden Sie uns auf der [Power BI Ideas-Website](https://ideas.powerbi.com/forums/265200-power-bi) Feedback zu diesem Feature, und lassen Sie uns wissen, wie wir es weiter verbessern können. 

Weitere Fragen? [Wenden Sie sich an die Power BI-Community](https://community.powerbi.com/)
