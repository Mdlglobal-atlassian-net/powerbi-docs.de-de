---
title: Stichprobenentnahme für visuelle Linienelemente mit hoher Dichte in Power BI
description: Stichprobenentnahme für visuelle Linienelemente mit hoher Dichte in Power BI
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/08/2019
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: 344b041b8cca3e6ed4be1f40c0e783df18315679
ms.sourcegitcommit: 6bbc3d0073ca605c50911c162dc9f58926db7b66
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/14/2020
ms.locfileid: "79378591"
---
# <a name="high-density-line-sampling-in-power-bi"></a>Stichprobenentnahme für visuelle Linienelemente mit hoher Dichte in Power BI
Ab dem im Juni 2017 veröffentlichten Release von **Power BI Desktop** und Updates des **Power BI-Diensts** steht ein neuer Stichprobenalgorithmus zur Verfügung, der die Visuals verbessert, die Daten mit hoher Dichte stichprobenartig entnehmen. Sie können z. B. ein Liniendiagramm aus den Verkaufsergebnissen Ihres Einzelhandelsgeschäfts erstellen, auch wenn jedes Geschäft mehr als zehntausend Verkaufsbelege jährlich verzeichnet. Ein Liniendiagramm mit derartigen Verkaufsinformationen entnimmt stichprobenartig Daten (wählen Sie eine aussagekräftige Darstellung dieser Daten, um zu veranschaulichen, wie die Verkaufszahlen über die Zeit hinweg variieren) aus den Daten jedes Geschäfts und erstellt ein Mehrfachliniendiagramm, das die zugrunde liegenden Daten veranschaulicht. Dies ist eine gängige Methode für das Visualisieren von Daten mit hoher Dichte. Die Stichprobenentnahme von Daten mit hoher Dichte von Power BI Desktop wurde verbessert. Dies wird in diesem Artikel ausführlicher beschrieben.

![](media/desktop-high-density-sampling/high-density-sampling_01.png)

> [!NOTE]
> Der in diesem Artikel beschriebene Algorithmus zur **Stichprobenentnahme mit hoher Dichte** ist in **Power BI Desktop** und in **Power BI-Dienst** verfügbar.

## <a name="how-high-density-line-sampling-works"></a>So funktioniert die Strichprobenentnahme für visuelle Linienelemente mit hoher Dichte
Früher hat **Power BI** eine Sammlung von Beispieldatenpunkten im vollständigen Bereich der zugrunde liegenden Daten auf deterministische Weise ausgewählt. Es kann z.B. sein, dass für Daten mit hoher Dichte in einer Visualisierung eines Kalenderjahrs 350 Beispieldatenpunkte angezeigt werden, die jeweils ausgewählt wurden, um sicherzustellen, dass der vollständige Datenbereich im Visual dargestellt wird. Um dies besser zu verstehen, können Sie sich vorstellen, dass ein Aktienkurs über ein Jahr aufgezeichnet und 365 Datenpunkte ausgewählt wurden, um eine Liniendiagrammvisualisierung zu erstellen (also ein Datenpunkt pro Tag).

In diesem Fall gibt es allein am Tag mehrere Werte für den Aktienkurs. Natürlich gibt es ein Tageshoch und -tief, aber diese können zu jedem Zeitpunkt am Tag während der Öffnung des Börsenmarkts auftreten. Für Linienstichproben mit hoher Dichte erhalten Sie eine repräsentative Momentaufnahme der zugrunde liegenden Daten (der Preis um 10:30 Uhr und um 12:00 Uhr), wenn das zugrunde liegenden Datenbeispiel an jedem Tag um 10:30 Uhr und 12:00 Uhr entnommen wurde. Allerdings wird dadurch nicht gewährleistet, dass das tatsächliche Tageshoch und -tief des Aktienkurses (an diesem Tag) für diesen repräsentativen Datenpunkt erfasst wird. In dieser und in anderen Situationen ist die Stichprobenentnahme für die zugrunde liegenden Daten repräsentativ. Allerdings werden die wichtigsten Punkte nicht immer erfasst (in diesem Fall wären dies das Tageshoch und -tief gewesen).

Definitionsgemäß werden Stichproben von Daten mit hoher Dichte entnommen, um schnell Visualisierungen zu erstellen, die auf Interaktivität reagieren. Zu viele Datenpunkte in einem Visual können dieses verlangsamen und die Sichtbarkeit von Trends beeinträchtigen. Das Erstellen des Algorithmus zur Stichprobenentnahme hängt davon ab, wie die Daten entnommen werden, um die beste Visualisierung zu bieten. Durch den verbesserten Algorithmus in Power BI Desktop werden Reaktionsfähigkeit, Darstellung und die Erhaltung von wichtigen Punkten in jedem Zeitsegment optimal miteinander vereint.

## <a name="how-the-new-line-sampling-algorithm-works"></a>So funktioniert der neue Algorithmus für die Strichprobenentnahme für visuelle Linienelemente mit hoher Dichte
Der neue Algorithmus für Linienstichproben mit hoher Dichte steht für Visuals mit Liniendiagrammen und Flächendiagrammen mit fortlaufender X-Achse zur Verfügung.

Für ein Visual mit hoher Dichte teilt **Power BI** Ihre Daten auf intelligente Weise in hochauflösende Blöcke ein und wählt anschließend wichtige Punkte für jeden Block aus. Dieses Aufteilen von hochauflösenden Daten wurde so optimiert, dass sich das entstehende Diagramm optisch nicht von einem Diagramm unterscheidet, für das alle zugrunde liegenden Datenpunkte geladen wurden – und zudem ist es deutlich schneller und interaktiver.

### <a name="minimum-and-maximum-values-for-high-density-line-visuals"></a>Mindest- und Höchstwerte für visuelle Linienelemente mit hoher Dichte
Für jedes visuelle Element gelten die folgenden visuellen Einschränkungen:

* Die maximale Anzahl von Datenpunkten, die in den meisten Visuals *angezeigt* werden können, beträgt **3.500**, unabhängig von der Anzahl der zugrunde liegenden Datenpunkte oder -reihen (weitere Informationen finden Sie unter den *Ausnahmen* in der folgenden Aufzählung). Bei 10 Reihen mit jeweils 350 Datenpunkten hat das visuelle Element deshalb die Höchstgrenze an Datenpunkten erreicht. Wenn Sie eine Reihe haben, kann diese bis zu 3.500 Datenpunkte haben, wenn der neue Algorithmus dies für die beste Stichprobenentnahme für die zugrunde liegenden Daten hält.

* Jedes visuelle Element kann maximal **60 Reihen** enthalten. Wenn Sie mehr als 60 Reihen haben, teilen Sie die Daten auf, und erstellen Sie mehrere Visuals mit jeweils höchstens 60 Reihen. Es wird empfohlen, einen **Datenschnitt** zu verwenden, um nur Segmente der Daten anzuzeigen (nur bestimmte Reihen). Wenn Sie z.B. alle Unterkategorien in der Legende anzeigen, können Sie einen Datenschnitt verwenden, um nach der übergeordneten Kategorie auf der gleichen Berichtseite zu filtern.

Die maximale Anzahl von Datenlimits ist für die folgenden Arten von Visuals höher, die *Ausnahmen* vom Datenpunktlimit 3.500 sind:

* Maximal **150.000** Datenpunkte für R-Visuals.
* **30 000 Datenpunkte** für Power BI-Visuals
* **10.000** Datenpunkte für Punktdiagramme (Standardeinstellung 3.500)
* **3.500** für alle anderen Visuals

Durch diese Parameter wird sichergestellt, dass die Visuals in Power BI Desktop sehr schnell gerendert werden und weiter auf Interaktion von Benutzern reagieren können. Zudem wird sichergestellt, dass diese keinen unnötigen Rechenmehraufwand auf dem Computer verursachen, der das Visual rendert.

### <a name="evaluating-representative-data-points-for-high-density-line-visuals"></a>Auswerten von repräsentativen Datenpunkten für visuelle Linienelemente mit hoher Dichte
Wenn die Anzahl von zugrunde liegenden Datenpunkten die der maximalen Datenpunkte übersteigt, die im Visual dargestellt werden können, wird der sogenannte *Diskretisierungsvorgang* gestartet. Dabei werden Blöcke der zugrunde liegenden Daten in *bins* genannte Gruppen aufgeteilt, die dann iterativ optimiert werden.

Der Algorithmus erstellt so viele Gruppen wie möglich, um dem visuellen Element die höchstmögliche Granularität zu bieten. Innerhalb jeder Gruppierung sucht der Algorithmus den Mindest- und Höchstdatenwert, um sicherzustellen, dass relevante und aussagekräftige Werte (z.B. Ausreißer) erfasst und im visuellen Element angezeigt werden. Auf Grundlage der Ergebnisse der Diskretisierung und der anschließenden Auswertung der Daten durch Power BI wird die Mindestauflösung der X-Achse für das Visual bestimmt, um die höchstmögliche Granularität für das Visual zu gewährleisten.

Wie bereits erwähnt, ist die minimale Granularität für jede Reihe 350 Punkte, das Maximum für die meisten Visuals ist 3.500, wobei die *Ausnahmen* in den vorherigen Abschnitten aufgeführt wurden.

Jede Gruppierung wird durch zwei Datenpunkte dargestellt, die im visuellen Element die repräsentativen Datenpunkte der Gruppierung werden. Die Datenpunkte sind einfach nur die Höchst- und Tiefwerte für diese Gruppe. Wenn Sie Höchst- oder Tiefwerte auswählen, stellt der Gruppierungsprozess sicher, dass jeder relevante Höchstwert oder aussagekräftige Tiefwert im visuellen Element erfasst und gerendert wird.

Dies scheint auf den ersten Blick ein sehr hoher Analyseaufwand zu sein, um sicherzustellen, dass vereinzelte Ausreißer erfasst und ordnungsgemäß im Visual dargestellt werden. Deshalb gibt es jetzt den neuen Algorithmus und den neuen Diskretisierungsvorgang.

## <a name="tooltips-and-high-density-line-sampling"></a>QuickInfos und Stichprobenentnahme für visuelle Linienelemente mit hoher Dichte
Beachten Sie, dass der Diskretisierungsvorgang, der die Mindest- und Höchstwerte in einer gegebenen Gruppe erfasst und darstellt, sich darauf auswirken kann, wie QuickInfos Daten anzeigen, wenn Sie mit der Maus auf Datenpunkte zeigen. Wir sehen uns noch mal unser Beispiel zu Aktienkursen an, um zu erläutern, wie und warum dies passiert.

Angenommen, Sie erstellen ein Visual auf der Grundlage von Aktienkursen, und Sie vergleichen zwei unterschiedliche Aktien miteinander, die beide die **Stichprobenentnahme mit hoher Dichte** verwenden. Die zugrunde liegenden Daten für jede Reihe haben viele Datenpunkte (möglicherweise erfassen Sie den Aktienkurs für jede Sekunde am Tag). Der Algorithmus für Linienstichproben mit hoher Dichte führt die Diskretisierung für jede Reihe einzeln durch.

Nehmen wir weiterhin an, dass der Preis der ersten Aktie um 12:02 Uhr steigt und zehn Sekunden später wieder schnell absinkt. Das ist ein wichtiger Datenpunkt. Wenn die Gruppierung für diese Aktie durchgeführt wird, ist das Tageshoch um 12:02 Uhr der repräsentative Datenpunkt für diese Gruppe.

Bei der zweiten Aktie gab es um 12:02 Uhr allerdings weder ein Tageshoch noch ein Tagestief in der Gruppe, die diesen Zeitpunkt enthält. Das Tageshoch oder -tief der Gruppe, die 12:02 Uhr enthält, kann drei Minuten später aufgetreten sein. Wenn Sie in dieser Situation beim Erstellen den Liniendiagramms auf 12:02 zeigen, sehen Sie einen Wert in QuickInfos für die erste Aktie (weil er um 12:02 gestiegen ist und dieser Wert als der höchste Datenpunkt der Gruppe ausgewählt wurde). Allerdings sehen Sie um 12:02 Uhr *keine* Werte in QuickInfos für die zweite Aktie. Dies liegt daran, dass die zweite Aktie weder ein Tageshoch noch -tief für die Gruppe hatte, die 12:02 Uhr enthalten hat. Deshalb können für die zweite Aktie für 12:02 Uhr keine Daten angezeigt werden, und deshalb werden auch keine QuickInfo-Daten angezeigt.

Dies tritt mit QuickInfos häufig auf. Möglicherweise stimmen die Höchst- und Tiefwerte einer Gruppe nicht genau mit den gleichmäßig skalierten Wertpunkten der X-Achse überein, und deshalb wird der Wert nicht von QuickInfos angezeigt.  

## <a name="how-to-turn-on-high-density-line-sampling"></a>So aktivieren Sie die Strichprobenentnahme für visuelle Linienelemente mit hoher Dichte
Standardmäßig ist der neue Algorithmus **eingeschaltet**. Um diese Einstellung zu ändern, wechseln Sie in den Bereich **Formatierung** auf der Karte **Allgemein**. Am unteren Rand sehen Sie einen Schieberegler mit dem Namen **Stichprobenentnahme mit hoher Dichte**. Um den Algorithmus zu deaktivieren, schieben Sie ihn auf **off** (aus).

![](media/desktop-high-density-sampling/high-density-sampling_02.png)

## <a name="considerations-and-limitations"></a>Überlegungen und Einschränkungen
Der neue Algorithmus für Linienstichproben mit hoher Dichte ist eine wichtige Verbesserung in Power BI. Es gibt jedoch einige Aspekte, die Sie berücksichtigen sollten, wenn Sie mit Werten und Daten mit hoher Dichte arbeiten.

* Aufgrund der erhöhten Granularität und des erweiterten Gruppierungsprozesses, zeigt **QuickInfos** möglicherweise nur dann einen Wert an, wenn repräsentative Daten nach dem Cursor übereinstimmen. Weitere Informationen finden Sie im Abschnitt *QuickInfos und Linienstichproben mit hoher Dichte* dieses Artikels.
* Wenn die Größe einer allgemeinen Datenquelle zu groß ist, eliminiert der neue Algorithmus Reihen (Legendenelemente), um sie an das Maximum an importieren Daten anzupassen.
  
  * In diesem Fall ordnet der Algorithmus Legendenreihen alphabetisch und durchläuft die Liste von Legendenelementen von oben nach unten in alphabetischer Reihenfolge, bis das Maximum an importierten Daten erreicht ist. Danach werden keine weiteren Reihen mehr importiert.
* Wenn ein zugrunde liegendes Dataset mehr als 60 Reihe hat (die Höchstzahl an Reihen, wie zuvor beschrieben), ordnet der neue Algorithmus die Reihen alphabetisch und löscht Reihen, die nach der 60. alphabetischen Reihe stehen.
* Wenn die Werte in den Daten nicht vom Typ *numeric* oder *date/time* sind, verwendet Power BI nicht den neuen Algorithmus, sondern den vorherigen Algorithmus (Stichprobenentnahme ohne hohe Dichte).
* Die Einstellung **Show Items with no data** (Elemente ohne Daten anzeigen) wird vom neuen Algorithmus nicht unterstützt.
* Der neue Algorithmus wird nicht unterstützt, wenn Sie die Liveverbindung zu einem Modell verwenden, das in SQL Server Analysis Services (Version 2016 oder früher) gehostet wird. Er wird aber in Modellen unterstützt, die in **Power BI** oder Azure Analysis Services gehostet werden.

## <a name="next-steps"></a>Nächste Schritte
Informationen über die Stichprobenentnahme mit hoher Dichte in Punktdiagrammen finden Sie im folgenden Artikel.

* [Stichprobenentnahme mit hoher Dichte in Power BI-Punktdiagrammen](desktop-high-density-scatter-charts.md)

