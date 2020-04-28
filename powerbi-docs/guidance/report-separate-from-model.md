---
title: Trennen von Berichten und Modellen in Power BI Desktop
description: Leitfaden zum Trennen von Berichten und Modellen in Power BI Desktop
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 04/11/2020
ms.author: v-pemyer
ms.openlocfilehash: dad451da460abed65a69990394522f268d7f21cd
ms.sourcegitcommit: 5ece366fceee9832724dae40eacf8755e1d85b04
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2020
ms.locfileid: "81525253"
---
# <a name="separate-reports-from-models-in-power-bi-desktop"></a>Trennen von Berichten und Modellen in Power BI Desktop

Wenn Sie eine neue Power BI Desktop-Lösung erstellen besteht einer der ersten Schritte in der Datenbeschaffung. Die Datenbeschaffung kann zu zwei deutlich unterschiedlichen Ergebnissen führen. Folgendes ist möglich:

- Sie können eine [Liveverbindung](../desktop-report-lifecycle-datasets.md) mit einem bereits veröffentlichten Modell herstellen, bei dem es sich um ein Power BI-Dataset oder ein remote gehostetes Analysis Services-Modell handeln kann.
- Sie können mit der Entwicklung eines neuen Modells beginnen, bei dem es sich entweder um ein Importmodell, ein DirectQuery-Modell oder ein zusammengesetztes Modell handeln kann.

In diesem Artikel wird das zweite Szenario behandelt. Er bietet Entscheidungshilfen, ob ein Bericht und ein Modell in einer einzigen Power BI Desktop-Datei kombiniert werden sollten.

## <a name="single-file-solution"></a>Lösung mit einer einzelnen Datei

Eine _Lösung mit einer einzelnen Datei_ funktioniert gut, wenn nur ein einzelner Bericht auf Grundlage des Modells vorhanden ist. In diesem Fall ist es wahrscheinlich, dass sowohl das Modell als auch der Bericht von derselben Person stammen. Wir definieren das als _persönliche BI-Lösung_, obwohl der Bericht für andere freigegeben werden könnte. Solche Lösungen können Berichte für bestimmte Rollen oder einmalige Bewertungen einer geschäftlichen Herausforderung sein. Diese werden häufig als _Ad-hoc-Berichte_ beschrieben.

:::image type="content" source="media/report-separate-from-model/single-file-solution.png" alt-text="Eine einzelne Datei enthält ein Modell und einen Bericht, die von derselben Person entwickelt wurden." border="true":::

## <a name="separate-report-files"></a>Separate Berichtsdateien

Es ist in folgenden Fällen sinnvoll, die Modell- und Berichtsentwicklung in separate Power BI Desktop-Dateien aufzuteilen:

- wenn es sich bei den Datenmodellierern und Berichtsautoren um verschiedene Personen handelt
- wenn bekannt ist, dass das Modell jetzt oder zukünftig als Quelle für mehrere Berichte eingesetzt wird

:::image type="content" source="media/report-separate-from-model/separate-report-files.png" alt-text="Es gibt drei PBIX-Dateien. Die erste enthält nur ein Modell. Die beiden anderen enthalten nur Berichte und stellen eine Liveverbindung mit dem Modell her, das im Power BI-Dienst gehostet wird. Die Berichte werden von unterschiedlichen Personen entwickelt." border="true":::

Datenmodellierer können weiterhin die Power BI Desktop-Features für die Berichterstellung verwenden, um Ihre Modellentwürfe zu testen und zu validieren. Allerdings sollten sie den Bericht direkt nach der Veröffentlichung der Datei im Power BI-Dienst aus dem Arbeitsbereich entfernen. Sie müssen außerdem daran denken, den Bericht jedes Mal zu entfernen, wenn das Dataset überschrieben oder erneut veröffentlicht wird.

### <a name="preserve-the-model-interface"></a>Beibehalten der Modellschnittstelle

Manchmal sind Modelländerungen unvermeidlich. Datenmodellierer müssen darauf achten, dass die Modellschnittstelle weiterhin funktioniert. Andernfalls kann die Funktionsweise von abhängigen Berichtsvisuals oder Dashboardkacheln beeinträchtigt werden. Fehlerhafte Visuals werden als Fehler angezeigt und können für Berichtsautoren und Anwender frustrierend sein. Schlimmer noch: Sie können das Vertrauen in die Daten schmälern.

Gehen Sie bei Modelländerungen daher sorgfältig vor. Vermeiden Sie nach Möglichkeit die folgenden Änderungen:

- das Umbenennen von Tabellen, Spalten, Hierarchien, Hierarchieebenen oder Measures
- das Ändern von Spaltendatentypen
- das Ändern von Measureausdrücken, sodass diese einen anderen Datentyp zurückgeben
- Das Verschieben von Measures in eine andere Hometabelle, da sonst berichtsbezogene Measures nicht mehr funktionieren könnten, die Measures mit ihrem Hometabellennamen vollständig qualifizieren. Es wird nicht empfohlen, DAX-Ausdrücke mithilfe von vollqualifizierten Measurenamen zu schreiben. Weitere Informationen finden Sie unter [DAX: Spalten- und Measureverweise](dax-column-measure-references.md).

Das Hinzufügen neuer Tabellen, Spalten, Hierarchien, Hierarchieebenen oder Measures ist mit einer Ausnahme kein Problem: Es ist möglich, dass ein neuer Measurename mit einem berichtsbezogenen Measurenamen in Konflikt steht. Es wird empfohlen, dass Berichtsautoren beim Definieren von Measures in ihren Berichten eine Benennungskonvention anwenden, um Konflikte zu vermeiden. Sie können berichtsbezogenen Measurenamen einen Unterstrich oder andere Zeichen voranstellen.

Wenn Sie Breaking Changes an Ihren Modellen vornehmen müssen, empfehlen wir Ihnen Folgendes:

- Sehen Sie sich [ähnliche Inhalte für das Dataset](../consumer/end-user-related.md#view-related-content-for-a-dataset) im Power BI-Dienst an.
- Untersuchen Sie die Ansicht [Datenherkunft](../collaborate-share/service-data-lineage.md) im Power BI-Dienst gründlich.

Beide Optionen ermöglichen es Ihnen, alle zugehörigen Berichte und Dashboards schnell zu identifizieren. Die Ansicht „Datenherkunft“ ist wahrscheinlich die bessere Wahl, da Sie dort schnell und einfach die Kontaktperson für jedes zugehörige Element ermitteln können. Tatsächlich handelt es sich um einen Hyperlink, der eine E-Mail-Nachricht öffnet, die an den Kontakt gerichtet ist.

Es wird empfohlen, dass Sie sich an den Besitzer jedes zugehörigen Artefakts wenden, damit diese über alle geplanten Breaking Changes Bescheid wissen. Auf diese Weise können sie sich darauf vorbereiten, ihre Berichte zu korrigieren und erneut zu veröffentlichen, um Ausfallzeiten und Unzufriedenheit auf Anwenderseite zu minimieren.

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zu diesem Artikel finden Sie in den folgenden Ressourcen:

- [Herstellen einer Verbindung mit Datasets im Power BI-Dienst über Power BI Desktop](../desktop-report-lifecycle-datasets.md)
- [Anzeigen zugehöriger Inhalte im Power BI-Dienst](../consumer/end-user-related.md)
- [Datenherkunft](../collaborate-share/service-data-lineage.md)
- Haben Sie Fragen? [Stellen Sie Ihre Frage in der Power BI-Community.](https://community.powerbi.com/)
- Vorschläge? [Einbringen von Ideen zur Verbesserung von Power BI](https://ideas.powerbi.com/)
