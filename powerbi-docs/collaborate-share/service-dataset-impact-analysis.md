---
title: Dataset-Auswirkungsanalyse (Vorschau)
description: Visualisieren und analysieren Sie nachgelagerte Auswirkungen von Änderungen an Datasets.
author: paulinbar
ms.reviewer: ''
ms.service: powerbi
ms.topic: conceptual
ms.date: 04/13/2020
ms.author: painbar
LocalizationGroup: ''
ms.openlocfilehash: 016c555c6df65a45a9d429c25db93110022d9d8f
ms.sourcegitcommit: 81407c9ccadfa84837e07861876dff65d21667c7
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/13/2020
ms.locfileid: "81268027"
---
# <a name="dataset-impact-analysis-preview"></a>Dataset-Auswirkungsanalyse (Vorschau)

Wenn Sie Änderungen an einem Dataset vornehmen oder in Betracht ziehen, solche Änderungen vorzunehmen, ist es wichtig, dass Sie die Auswirkungen dieser Änderungen auf nachgeschaltete Berichte und Dashboards, die von diesem Dataset abhängig sind, abschätzen können. Die **Dataset-Auswirkungsanalyse** stellt Informationen bereit, die Ihnen bei dieser Einschätzung helfen können.
* Sie zeigt Ihnen, wie viele Arbeitsbereiche, Berichte und Dashboards möglicherweise von Ihrer Änderung betroffen sind, und lässt Sie einfach zu den Arbeitsbereichen navigieren, in denen sich die betroffenen Berichte und Dashboards befinden, sodass Sie diese weiter untersuchen können.
* Sie zeigt die Anzahl von einzelnen Besuchern und Aufrufen für die potenziell betroffenen Elemente an. Diese Informationen helfen Ihnen dabei, die Gesamtauswirkungen der Änderung auf das entsprechende nachgeschaltete Element zu ermitteln. So ist es beispielsweise wahrscheinlich wichtiger, die Auswirkungen einer Änderung auf einen Bericht mit 20.000 einzelnen Viewern zu untersuchen als die auf einen Bericht mit drei Viewern.
* Sie bietet eine einfache Möglichkeit, die entsprechenden Personen über eine Änderung zu benachrichtigen, die Sie vorgenommen haben oder in Betracht ziehen.

Die Dataset-Auswirkungsanalyse kann einfach aus der [Datenherkunftsansicht](service-data-lineage.md) heraus gestartet werden.

## <a name="identifying-shared-datasets"></a>Identifizieren freigegebener Datasets

Sie können die Dataset-Auswirkungsanalyse sowohl für freigegebene als auch für nicht freigegebene Datasets durchführen. Sie ist allerdings besonders nützlich für arbeitsbereichsübergreifend freigegebene Datasets, bei denen es deutlich schwieriger ist, sich ein klares Bild von den nachgeschalteten Abhängigkeiten zu verschaffen, als bei nicht freigegebenen Datasets, bei denen sich alle Abhängigkeiten im selben Arbeitsbereich wie das Dataset selbst befinden.

In der Herkunftsansicht können Sie freigegebene und nicht freigegebene Datasets anhand des links oben auf der Karte des Datasets angezeigten Symbols unterscheiden.

![Symbole für freigegebene und nicht freigegebene Datasets](media/service-dataset-impact-analysis/shared-unshared-icon.png)

## <a name="perform-dataset-impact-analysis"></a>Durchführen der Dataset-Auswirkungsanalyse

Sie können die Auswirkungsanalyse für jedes Dataset im Arbeitsbereich durchführen, unabhängig davon, ob es sich um ein freigegebenes Dataset handelt oder nicht. Sie können keine Auswirkungsanalyse für externe Datasets durchführen, die in der Herkunftsansicht zwar angezeigt werden, sich tatsächlich aber in einem anderen Arbeitsbereich befinden. Wenn Sie eine Auswirkungsanalyse für ein externes Dataset durchführen möchten, müssen Sie hierfür zum Quellarbeitsbereich navigieren.

Klicken Sie auf der Datasetkarte auf die Schaltfläche „Auswirkungsanalyse“, um eine Dataset-Auswirkungsanalyse durchzuführen.

![Schaltfläche für die Dataset-Auswirkungsanalyse](media/service-dataset-impact-analysis/open-analysis-pane-button.png)

Der Seitenbereich „Auswirkungsanalyse“ wird geöffnet.

![Seitenbereich für die Dataset-Auswirkungsanalyse](media/service-dataset-impact-analysis/service-impact-analysis-pane.png)

* In der **Auswirkungszusammenfassung** wird die Anzahl von potenziell betroffenen Arbeitsbereichen, Berichten und Dashboards angezeigt sowie die Gesamtzahl von Aufrufen für alle nachgeschalteten Berichte und Dashboards, die mit dem Dataset verbunden sind.
* Mit dem Link bei **Notify contacts** (Kontakte benachrichtigen) wird ein Dialogfeld geöffnet, in dem Sie eine Nachricht zu Änderungen, die Sie an diesem Dataset vornehmen, erstellen und an die Kontaktlisten der betroffenen Arbeitsbereiche senden können. 
* In der **Nutzungsaufschlüsselung** wird für jeden Arbeitsbereich die Gesamtzahl von Aufrufen für die darin enthaltenen potenziell betroffenen Berichte und Dashboards angezeigt und für jeden Bericht und jedes Dashboard die jeweilige Gesamtzahl von Viewern und Aufrufen.
   * Viewer: Hier wird die Anzahl von einzelnen Benutzern angezeigt, die einen Bericht oder ein Dashboard aufgerufen haben.
   * Views: Hier wird die Anzahl von Aufrufen für einen Bericht oder ein Dashboard angezeigt.

Die Nutzungsmetriken beziehen sich auf die letzten 30 Tage, den aktuellen Tag ausgenommen. Die jeweilige Anzahl beinhaltet die Nutzung über verwandte Apps. Die Metriken helfen Ihnen dabei, die Nutzung von Datasets im Mandanten zu verstehen und die Auswirkungen abzuschätzen, die Änderungen an Ihrem Dataset möglicherweise haben.

## <a name="notify-contacts"></a>Benachrichtigen von Kontakten

Wenn Sie eine Änderung an einem Dataset vorgenommen haben oder in Betracht ziehen, eine Änderung vorzunehmen, sollten Sie die betroffenen Benutzer kontaktieren, um diese darüber zu informieren. Wenn Sie Kontakte benachrichtigen, wird eine E-Mail an die [Kontaktlisten](../service-create-the-new-workspaces.md#workspace-contact-list) aller betroffenen Arbeitsbereiche gesendet. Ihr Name wird in der E-Mail angezeigt, sodass die Kontakte Sie finden und in einem neuen E-Mail-Thread antworten können. 

1. Klicken Sie im Seitenbereich „Auswirkungsanalyse“ auf **Notify contacts** (Kontakte benachrichtigen). Das Dialogfeld „Notify contacts“ (Kontakte benachrichtigen) wird geöffnet.

   ![Dialogfeld „Notify contacts“ (Kontakte benachrichtigen)](media/service-dataset-impact-analysis/notify-contacts-dialog.png)

1. Geben Sie im Textfeld Details zur Änderung an.
1. Wenn die Nachricht fertig ist, klicken Sie auf **Senden**.

> [!NOTE]
> Das Benachrichtigen von Kontakten ist nicht verfügbar, wenn sich das Dataset, für das Sie die Auswirkungsanalyse durchführen, in einem klassischen Arbeitsbereich befindet.

## <a name="privacy"></a>Datenschutz

Sie können nur dann eine Auswirkungsanalyse für ein Dataset durchführen, wenn Sie über Schreibberechtigungen für dieses Dataset verfügen. Im Seitenbereich „Auswirkungsanalyse“ werden nur die tatsächlichen Namen von Arbeitsbereichen, Berichten und Dashboards angezeigt, auf die Sie Zugriff haben. Für Elemente, auf die Sie keinen Zugriff haben, wird **Eingeschränkter Zugriff** angezeigt. Der Grund hierfür ist, dass einige Namen von Elementen möglicherweise personenbezogene Informationen enthalten.

Auch wenn Sie auf manche Arbeitsbereiche nicht zugreifen können, werden dennoch zusammengefasste Nutzungsmetriken für diese Arbeitsbereiche angezeigt, und Ihre Nachrichten über „Notify contacts“ (Kontakte benachrichtigen) erreichen auch die Kontaktlisten dieser Arbeitsbereiche.

## <a name="impact-analysis-from-power-bi-desktop"></a>Auswirkungsanalyse aus Power BI Desktop

Wenn Sie in Power BI Desktop eine Änderung an einem Dataset vornehmen und es dann erneut im Power BI-Dienst veröffentlichen, wird Ihnen in einer Benachrichtigung angezeigt, wie viele Arbeitsbereiche, Berichte und Dashboards potenziell von dieser Änderung betroffen sind, und Sie werden darum gebeten, zu bestätigen, dass Sie das aktuell veröffentlichte Dataset durch das von Ihnen geänderte ersetzen möchten. Diese Benachrichtigung enthält auch einen Link zur vollständigen Dataset-Auswirkungsanalyse im Power BI-Dienst. Dort finden Sie weitere Informationen und können Maßnahmen ergreifen, um die durch Ihre Änderung verursachten Risiken zu mindern.

![Benachrichtigung zur Dataset-Auswirkungsanalyse in Power BI Desktop](media/service-dataset-impact-analysis/service-dataset-impact-analysis-desktop-warning.png)

> [!NOTE]
> Die in der Benachrichtigung angezeigten Informationen weisen nur auf potenzielle Auswirkungen hin. Sie sind nicht unbedingt ein Indikator dafür, dass etwas beschädigt wurde. Oft haben Änderungen an Datasets keine negativen Auswirkungen auf nachgeschaltete Berichte und Dashboards. Dennoch wird diese Benachrichtigung angezeigt, die Sie über potenzielle Auswirkungen aufklärt.
>
>In dieser Benachrichtigung wird die Anzahl von Arbeitsbereichen nur angezeigt, wenn mehr als ein Arbeitsbereich betroffene Berichte und Dashboards enthält.

## <a name="limitations"></a>Einschränkungen

* Nutzungsmetriken werden derzeit für klassische und persönliche Arbeitsbereiche nicht unterstützt.

## <a name="next-steps"></a>Nächste Schritte

* [Einführung in die Verwendung von Datasets in mehreren Arbeitsbereichen (Vorschau)](../service-datasets-across-workspaces.md)
* [Datenherkunft](service-data-lineage.md)
