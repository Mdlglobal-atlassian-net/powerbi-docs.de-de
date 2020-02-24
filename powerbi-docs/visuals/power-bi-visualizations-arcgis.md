---
title: Interagieren mit einer ArcGIS-Karte, die für Sie freigegeben wurde
description: Verwenden eines ArcGIS Maps for Power BI-Visuals in der Leseansicht als Berichtsnutzer
author: mihart
ms.reviewer: willt, lukasz
featuredvideoid: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 11/18/2019
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: 59685b4c3ceab4b60cba92ec1d3924b902c1426a
ms.sourcegitcommit: 578d43aeb7cebf40f3caf03a614bc885cc039488
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/10/2020
ms.locfileid: "77115306"
---
# <a name="interact-with-arcgis-maps-in-power-bi"></a>Interagieren mit ArcGIS-Karten in Power BI
Dieses Thema ist für Personen verfasst, die ArcGIS-Karten im Power BI-Dienst, in Power BI Desktop oder in einer mobilen Power BI-App verwenden. Sobald ein Designer ein ArcGIS Maps for Power BI-Visual für Sie freigegeben hat, gibt es viele Möglichkeiten der Interaktion mit diesem Visual.  Weitere Informationen zum Erstellen einer ArcGIS-Karte finden Sie im [Tutorial zu ArcGIS Maps von ESRI](../visuals/power-bi-visualization-arcgis.md).

Die Kombination von ArcGIS Maps und Power BI bietet völlig neue Möglichkeiten der Kartendarstellung, die über die Darstellung von Punkten auf einer Karte weit hinausgeht. Berichts-Designer beginnen mit einer Karte und fügen Ebenen mit demografischen Daten an diese Karte an. Die Kombination von standortbasierten Datenebenen (z. B. Volkszählungsdaten) auf einer Karte mit räumlicher Analyse vermittelt ein tieferes Verständnis der Daten in den Visualisierungen.

> [!TIP]
> GIS steht für „Geoinformationssysteme“.
> 

Dieses ArcGIS Maps for Power BI-Visual zeigt die Umsätze im Vorjahr nach Stadt an und verwendet eine Straßenbasiskarte und eine durchschnittliche Referenzebene für das Haushaltseinkommen. Die Karte enthält zwei Stecknadeln (rot und gelb) und einen Fahrzeitradius (in Violett).

![ArcGIS-Karte, die die USA mit Blasen, Stecknadeln und Fahrtzeiten anzeigt](media/power-bi-visualizations-arcgis/power-bi-arcgis-esri.png)

> [!TIP]
> Besuchen Sie die [Seite von ESRI für Power BI](https://www.esri.com/powerbi), auf der Sie viele Beispiele und Kommentare von Kunden finden. Und besuchen Sie dann die [Seite für erste Schritte mit ArcGIS Maps for Power BI](https://doc.arcgis.com/en/maps-for-powerbi/get-started/about-maps-for-power-bi.htm) von Esri.
> 
> 

## <a name="user-consent"></a>Zustimmung des Benutzers

Wenn eine ArcGIS-Karte zum ersten Mal von einem Kollegen für Sie freigegeben wird, wird in Power BI eine Zustimmungsaufforderung angezeigt. ArcGIS Maps für Power BI wird von ESRI (https://www.esri.com) bereitgestellt, und die Verwendung von ArcGIS Maps für Power BI unterliegt den Nutzungsbedingungen und der Datenschutzrichtlinie von Esri. Power BI-Benutzer, die Visuals von ArcGIS Maps für Power BI verwenden möchten, müssen die Informationen im Zustimmungsdialogfeld akzeptieren.


## <a name="understand-the-layers"></a>Grundlegendes zu Ebenen

Ein ArcGIS Maps for Power BI-Visual kann verschiedene Arten von Ebenen mit demografischen Standortinformationen aufweisen.

### <a name="base-maps"></a>Grundkarten

Ausgangspunkt für ein ArcGIS Maps for Power BI-Visual ist eine Basiskarte. Stellen Sie sich die Basiskarten als Zeichenbereich für die Daten vor. Eine Basiskarte kann ein einfacher Zeichenbereich (dunkel oder hell) sein,

![Dunkelgraue Basiskarte](media/power-bi-visualizations-arcgis/power-bi-basemap-dark.png) 

oder ein Zeichenbereich mit Straßen- und Verkehrsinformationen. 

![Dunkelgraue Basiskarte](media/power-bi-visualizations-arcgis/power-bi-streets-basemap.png)  

Die Basiskarte wird vollständig auf den Zeichenbereich angewendet und automatisch aktualisiert, wenn Sie sie schwenken und vergrößern. Vergrößern Sie sie, um immer ausführlichere Straßen- und Verkehrsinformationen anzuzeigen. Wenn Sie von einem Kontinent zu einem anderen schwenken, bleibt der Detailgrad konstant. Hier wurde von Porto nach Peking (Beijing) geschwenkt.

![Straßenbasiskarte](media/power-bi-visualizations-arcgis/power-bi-basemap-pan.png)  

### <a name="reference-layers"></a>Referenzebenen

Ein Berichts-*Designer* kann eine Referenzebene hinzufügen. Referenzebenen werden von ESRI gehostet und bieten eine zusätzliche Ebene mit demografischen Informationen zu einem Standort. Das folgende Beispiel enthält eine Referenzebene für die Bevölkerungsdichte. Dunklere Farben stellen eine höhere Dichte dar.

![Karte der Region Orlando mit Darstellung der Bevölkerungsdichte](media/power-bi-visualizations-arcgis/power-bi-reference.png)  

### <a name="infographics"></a>Infografiken

Ein Berichts-*Designer* kann viele Infografikebenen hinzufügen. Infografiken sind einfache visuelle Indikatoren, die auf der rechten Seite des sichtbaren Canvas angezeigt werden. Infografiken werden von ESRI gehostet und bieten eine zusätzliche Ebene mit demografischen Informationen zu einem Standort. Im folgenden Beispiel werden drei Infografiken angewendet. Sie werden nicht auf der Karte selbst angezeigt, sondern auf Kartenelementen. Die Infografikkarten werden aktualisiert, wenn Sie die Bereiche in der Karte vergrößern, schwenken und auswählen.

![Karte der Region Orlando und Infografikkarten auf der rechten Seite des Canvas](media/power-bi-visualizations-arcgis/power-bi-infographics.png)  

### <a name="pins"></a>Markierungen

Stecknadeln geben genaue Orte an, z. B. eine Stadt oder eine Adresse. Manchmal verwenden Berichts-*Designer* Stecknadeln mit Fahrzeitradius. In diesem Beispiel werden Geschäfte innerhalb eines 50-Meilen-Radius von Charlotte, North Carolina, dargestellt.


![Fahrzeit um Charlotte, North Carolina](media/power-bi-visualizations-arcgis/power-bi-drive-times.png) 


## <a name="interact-with-an-arcgis-maps-for-power-bi-visual"></a>Interagieren mit einem ArcGIS Maps for Power BI-Visual
Welche Funktionen verfügbar sind, hängt davon ab, wie der Bericht für Sie und Ihren Power BI-Kontotyp freigegeben wurde. Wenden Sie sich an Ihren Systemadministrator, wenn Sie Fragen haben. ArcGIS Maps for Power BI-Visuals verhalten sich ähnlich wie andere Visuals in einem Bericht. Sie können [die Daten anzeigen, die zum Erstellen der Visualisierung verwendet werden](../consumer/end-user-show-data.md), die Karte im [Fokusmodus und im Vollbildmodus anzeigen](../consumer/end-user-focus.md), [Kommentare hinzufügen](../consumer/end-user-comment.md), [mit den Filtern interagieren](../consumer/end-user-report-filter.md), die vom Berichts-*Designer* festgelegt wurden, und vieles mehr. ArcGIS-Visuals können andere Visuals auf der Berichtsseite und umgekehrt kreuzfiltern.

Zeigen Sie mit der Maus auf Orte auf der Basiskarte (z. B. eine Blase), um QuickInfos anzuzeigen. Verwenden Sie außerdem die Auswahltools für ArcGIS-Visuals, um zusätzliche QuickInfos anzuzeigen und eine bestimmte Auswahl auf der Basiskarte oder der Referenzebene vorzunehmen.  

### <a name="selection-tools"></a>Auswahltools

ArcGIS Maps for Power BI unterstützt fünf Auswahlmodi. Es können maximal 250 Datenpunkte gleichzeitig ausgewählt werden.

![Screenshot aller drei Auswahltools](media/power-bi-visualizations-arcgis/power-bi-esri-selection-tools.png)

#### <a name="the-single-select-tool"></a>Das Einzelauswahltool

![Screenshot eines einzelnen Auswahltools](media/power-bi-visualizations-arcgis/power-bi-esri-selection-single2.png) 

Wählen Sie einen Datenpunkt, eine Blase, eine Stecknadel oder einen einzelnen Datenpunkt auf der Referenzebene aus. Power BI zeigt die Detailinformationen zur Auswahl in einer QuickInfo an. Mit der Einzelauswahl werden die anderen Visuals auf der Berichtsseite basierend auf Ihrer Auswahl kreuzgefiltert, und die Infografikkarten für den ausgewählten Bereich werden aktualisiert. 

Hier ist ein brauner Blasendatenpunkt aus der Basiskarte ausgewählt. In Power BI wird dann:
- die Auswahl aufgehoben,
- eine QuickInfo für den Datenpunkt angezeigt, 
- eine Aktualisierung der Infografikkarten ausgeführt, sodass nur Daten zur Auswahl angezeigt werden, und
- eine Kreuzhervorhebung des Säulendiagramms angezeigt.

![Screenshot der QuickInfo für die braune Blase](media/power-bi-visualizations-arcgis/power-bi-single-selects.png)

Wenn die Karte über eine Referenzebene verfügt, wählen Sie Standorte aus, um Details in einer QuickInfo anzuzeigen. Hier wurde Seneca County ausgewählt, und es werden Daten aus der Referenzebene (Bevölkerungsdichte) angezeigt, die der Berichts-*Designer* der Karte hinzugefügt hat. In diesem Beispiel enthält der Datenpunkt zwei verschiedene Countys, sodass unsere QuickInfo zwei Seiten aufweist. Jede Seite enthält ein Diagramm. Wählen Sie einen Balken im Diagramm aus, um weitere Details anzuzeigen. 

![Screenshot der QuickInfo für Seneca County](media/power-bi-visualizations-arcgis/power-bi-single-select-ref.png)

> [!TIP]
  > Zuweilen können Sie die Anzahl der QuickInfo-Seiten verringern, indem Sie einen bestimmten Ort auswählen.  Andernfalls werden möglicherweise mehrere QuickInfos gleichzeitig in Power BI angezeigt, wenn sich Standorte überlappen. Wählen Sie die Pfeile aus, um zwischen den QuickInfos zu wechseln.
  > 
  > ![QuickInfo, die drei Seiten zeigt](media/power-bi-visualizations-arcgis/power-bi-3-screens.png)

#### <a name="the-multi-select-tool"></a>Tool zur Mehrfachauswahl

![Tool zur Mehrfachauswahl](media/power-bi-visualizations-arcgis/power-bi-esri-selection-marquee2.png) 

Zeichnet ein Rechteck auf der Karte und wählt die darin enthaltenen Datenpunkte aus. Mit STRG können Sie mehrere rechteckige Bereiche auswählen. Durch die Mehrfachauswahl werden die Infografikkarten für den ausgewählten Bereich aktualisiert, und die anderen Visuals auf der Berichtsseite werden basierend auf Ihrer Auswahl mit einer Kreuzhervorhebung angezeigt.

![Tool zur Mehrfachauswahl](media/power-bi-visualizations-arcgis/power-bi-multi-select.png) 

#### <a name="the-reference-layer-tool"></a>Referenzebenentool

![Drittes Auswahltool für Begrenzungen](media/power-bi-visualizations-arcgis/power-bi-esri-selection-reference-layer2.png) 

Ermöglicht die Verwendung von Begrenzungen oder Polygonen in den Referenzebenen zum Auswählen von enthaltenen Datenpunkten. Es ist schwer zu erkennen, aber auf der Referenzebene ist ein gelber Umriss zu sehen. Im Gegensatz zum Einzelauswahltool wird keine QuickInfo dargestellt. Stattdessen erhalten Sie Daten zu Datenpunkten, die in den Begrenzungen dieses Umrisses enthalten sind. In diesem Beispiel enthält die Auswahl einen Datenpunkt, und zwar für ein Lindseys-Geschäft in Winston Salem.

![Referenzauswahltool](media/power-bi-visualizations-arcgis/power-bi-ref-tool.png) 

#### <a name="the-buffer-tool"></a>Puffertool

![Viertes Auswahltool für Puffer](media/power-bi-visualizations-arcgis/power-bi-esri-selection-4.png) 

Ermöglicht die Auswahl von Datenpunkten mithilfe einer Pufferebene. Verwenden Sie dieses Tool z. B. zum Auswählen eines Fahrzeitradius und zur Interaktion mit dem Rest des Berichts. Der Fahrzeitradius bleibt aktiv, und die Infografikkarten spiegeln weiterhin den Fahrzeitradius wider, aber durch die Auswahl anderer Datenpunkte auf der Karte werden die anderen Visuals auf der Berichtsseite kreuzgefiltert.

![Pufferauswahltool](media/power-bi-visualizations-arcgis/power-bi-buffer.png) 

#### <a name="the-find-similar-tool"></a>Ähnlichkeitssuchtool

![Fünftes Auswahltool für Ähnlichkeiten](media/power-bi-visualizations-arcgis/power-bi-esri-selection-reference5.png) 

Ermöglicht das Auffinden von Orten mit ähnlichen Attributen. Zuerst wählen Sie einen oder mehrere relevante Punkte oder Referenzorte aus, indem Sie bis zu fünf Dimensionen definieren, die Sie in der Analyse verwenden möchten. Die Ähnlichkeitssuche berechnet dann die 10 Orte auf Ihrer Karte, die den von Ihnen definierten Referenzorten am stärksten ähneln. Anschließend können Sie Infografikkarten verwenden, um mehr über die demografischen Informationen zu den einzelnen Ergebnissen zu erfahren. Sie können auch Fahrzeitbereiche erstellen, um einen Eindruck davon zu erhalten, was sich in der Entfernung der einzelnen Orte befindet, oder den Bericht mit dem Ähnlichkeitssuchtool selbst filtern, um weitere Erkenntnisse zu gewinnen. Die gesamte Berechnung erfolgt lokal auf Ihrem Computer, sodass sichergestellt ist, dass vertrauliche Daten geschützt sind.


## <a name="considerations-and-limitations"></a>Überlegungen und Einschränkungen
ArcGIS Maps für Power BI ist in den folgenden Diensten und Anwendungen verfügbar:

|Dienst/App  |Verfügbarkeit  |
|---------|---------|
|Power BI Desktop     |     Ja    |
|Power BI service (app.powerbi.com)     |    Ja     |
|Mobile Apps für Power BI     |  Ja      |
|Power BI-Webveröffentlichung     |  Nein       |
|Power BI Embedded     |     Nein    |
|Einbettung in den Power BI-Dienst (PowerBI.com)  | Nein |


## <a name="how-do-arcgis-maps-for-power-bi-work-together"></a>Wie interagieren ArcGIS Maps for Power BI miteinander?
ArcGIS Maps for Power BI werden von Esri bereitgestellt (https://www.esri.com) ). Die Verwendung von ArcGIS Maps for Power BI unterliegt den [Nutzungsbedingungen](https://go.microsoft.com/fwlink/?LinkID=8263222) und der [Datenschutzrichtlinie](https://go.microsoft.com/fwlink/?LinkID=826323) von Esri. Power BI-Benutzer, die Visualisierungen von ArcGIS Maps for Power BI verwenden möchten, müssen die Informationen im Zustimmungsdialogfeld akzeptieren (Details finden Sie unter „Benutzerzustimmung“).  Die Verwendung von ArcGIS Maps for Power BI unterliegt den Nutzungsbedingungen und der Datenschutzrichtlinie von Esri, auf die auch über das Zustimmungsdialogfeld verwiesen wird. Jeder Benutzer muss seine Zustimmung geben, bevor er ArcGIS Maps for Power BI zum ersten Mal verwendet. Sobald der Benutzer seine Zustimmung gegeben hat, werden die Daten, die an das Visual gebunden sind, zumindest für die Geocodierung an die Esri-Dienste gesendet. Das bedeutet, dass Informationen zum Standort in Längen- und Breitengrade umgewandelt werden, die auf einer Karte dargestellt werden können. Gehen Sie davon aus, dass alle Daten, die an die Datenvisualisierung gebunden sind, an die Esri-Dienste gesendet werden können. Esri stellt u.a. Dienste wie Basiskarten, räumliche Analysen und Geocodierung bereit. Die ArcGIS Maps for Power BI-Visualisierung interagiert mit diesen Diensten unter Verwendung einer SSL-Verbindung, die von einem Zertifikat geschützt wird, das von Esri bereitgestellt und verwaltet wird. Zusätzliche Informationen zu ArcGIS Maps for Power BI erhalten Sie auf der [ArcGIS Maps for Power BI-Produktseite](https://www.esri.com/powerbi) von Esri.

### <a name="power-bi-plus"></a>Power BI Plus

![Auswahl des Pluszeichens für Registrierung oder Anmeldung](media/power-bi-visualizations-arcgis/power-bi-plus.png)

Wenn sich ein Benutzer für ein Plus-Abonnement registriert, das von Esri über ArcGIS Maps for Power BI angeboten wurde, wird dadurch eine direkte Beziehung zu Esri hergestellt. Power BI sendet keine persönlichen Informationen über den Benutzer an Esri. Der Benutzer registriert sich für eine AAD-Anwendung, die von Esri bereitgestellt wird, und verwendet dabei seine eigene AAD-Identität. Außerdem vertraut er der Anwendung. Dadurch gibt er seine persönlichen Informationen direkt für Esri frei. Sobald der Benutzer Plus-Inhalte einem ArcGIS Maps for Power BI-Visual hinzufügt, benötigen auch andere Benutzer ein Plus-Abonnement von Esri, um den Inhalt anzeigen und bearbeiten zu können. 

Wenn Sie komplexe, technische Fragen zur Funktionsweise von ArcGIS Maps for Power BI haben, können Sie Esri über deren Supportwebsite kontaktieren.

## <a name="considerations-and-troubleshooting"></a>Zu beachtende Aspekte und Problembehandlung

**Die ArcGIS-Karte wird nicht angezeigt**    
In Diensten und Anwendungen, für die ArcGIS Maps für Power BI nicht verfügbar ist, wird statt der Visualisierung ein leeres Visual mit dem Power BI-Logo angezeigt.

**Auf der Karte werden nicht alle Informationen angezeigt**    
Bei der Geocodierung von Längengrad/Breitengrad auf der Karte werden bis zu 30.000 Datenpunkte angezeigt. Bei der Geocodierung von Datenpunkten wie z. B. Postleitzahlen oder Adressen werden nur die ersten 15.000 Datenpunkte geocodiert. Ortsnamen und Länder sind von dieser Geocodierung-Einschränkung auf 1500 Einträge nicht betroffen.

**Fallen Gebühren für die Verwendung von ArcGIS-Karten für Power BI an?**

ArcGIS Maps für Power BI ist für alle Power BI-Benutzer ohne zusätzliche Kosten verfügbar. Dies ist eine von **Esri** bereitgestellte Komponente, die den Nutzungsbedingungen und der Datenschutzrichtlinie von **Esri** unterliegt, wie weiter oben in diesem Artikel beschrieben. Wenn Sie ArcGIS **Plus** abonnieren, fallen Gebühren an.

**Ich erhalte eine Fehlermeldung, dass der Cache voll ist**

Dieses Verhalten ist bekannt und wird korrigiert.  Wählen Sie in der Zwischenzeit den in der Fehlermeldung angezeigten Link aus, um Anweisungen zum Leeren des Power BI-Caches zu erhalten.

**Kann ich meine ArcGIS-Karten offline anzeigen?**

Nein. Zum Anzeigen der Karten in Power BI ist eine Netzwerkverbindung erforderlich.

## <a name="next-steps"></a>Nächste Schritte
Hilfe erhalten: **Esri** bietet eine [umfassende Dokumentation](https://go.microsoft.com/fwlink/?LinkID=828772) zu den Funktionen von **ArcGIS-Karten für Power BI**.

In der [Power BI-Community finden Sie einen Thread zu **ArcGIS Maps für Power BI**](https://go.microsoft.com/fwlink/?LinkID=828771) mit aktuellen Informationen. Dort können Sie auch Fragen stellen und Probleme melden.


[Produktseite zu ArcGIS-Karten für Power BI](https://www.esri.com/powerbi)
