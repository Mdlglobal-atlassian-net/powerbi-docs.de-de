---
title: Bearbeiten einer Dashboardkachel
description: In diesem Tutorial erstellen Sie eine Kachel und heften sie an ein Dashboard an, und Sie lernen, wie Sie diese Dashboardkachel bearbeiten, indem Sie ihre Größe ändern, sie verschieben, umbenennen, anheften, löschen oder ihr einen Link hinzufügen.
author: maggiesMSFT
ms.reviewer: ''
featuredvideoid: lJKgWnvl6bQ
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 03/02/2018
ms.author: maggies
LocalizationGroup: Dashboards
ms.openlocfilehash: bdd2ec136ae741e15e0cb60d141c651cd5fb6749
ms.sourcegitcommit: 7e845812874b3347bcf87ca642c66bed298b244a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/13/2020
ms.locfileid: "79207595"
---
# <a name="edit-or-remove-a-dashboard-tile"></a>Bearbeiten oder Entfernen einer Dashboardkachel

## <a name="dashboard-owners-versus-dashboard-consumers"></a>*Dashboardbesitzer* und *Dashboardnutzer*
Wenn Sie ein Dashboard erstellen oder besitzen, stehen Ihnen viele Optionen zum Ändern des Aussehens und Verhaltens der Kacheln auf diesem Dashboard zur Verfügung. Verwenden Sie die folgenden Einstellungen und Strategien, um die Funktionen für die *Nutzung* des Dashboards durch Ihre Kollegen zu entwerfen.  Wird beim Auswählen einer Kachel der zugrunde liegende Bericht, eine benutzerdefinierte URL oder ein anderes Dashboard geöffnet? Vielleicht [fügen Sie eine Kachel hinzu, auf der ein Video oder Streamingdaten angezeigt werden](service-dashboard-add-widget.md)? Oder Sie möchten eventuell sogar [eine Kachel erstellen, die interaktive Slicer enthält](service-dashboard-pin-live-tile-from-report.md). Als *Ersteller* stehen Ihnen viele Optionen zur Verfügung. 

<iframe width="560" height="315" src="https://www.youtube.com/embed/lJKgWnvl6bQ" frameborder="0" allowfullscreen></iframe>

In diesem Artikel werden folgende Themen behandelt:

* [Erstellen einer Visualisierung und Anheften der Visualisierung an ein Dashboard](#create)
* [Verschieben einer Kachel](#move)
* [Ändern der Größe einer Kachel](#resize)
* [Umbenennen einer Kachel](#rename)
* [Hinzufügen eines Links zu einer Kachel](#hyperlink)
* [Anheften einer Kachel an ein anderes Dashboard](#different)
* [Löschen einer Kachel](#delete)
  
  > [!TIP]
  > Um die Visualisierung auf der Kachel selbst zu ändern, löschen Sie die Kachel, und fügen Sie eine neue [Dashboard-Kachel](consumer/end-user-tiles.md) hinzu.

  
## <a name="prerequisites"></a>Voraussetzungen
Um die Schritte des Tutorials durchzuführen, öffnen Sie den Power BI-Dienst (nicht Power BI Desktop), und [laden Sie das Analysebeispiel für IT-Ausgaben herunter](sample-it-spend.md). Wenn die Erfolgsmeldung angezeigt wird, wählen Sie **Zum Dashboard wechseln** aus.

- - -
<a name="create"></a>

## <a name="create-a-new-visualization-and-pin-it-to-the-dashboard"></a>Erstellen einer neuen Visualisierung und Anheften der Visualisierung an das Dashboard
1. Wählen Sie aus dem Dashboard „Analysebeispiel für IT-Ausgaben“ die Kachel „Betrag“ aus, um den Bericht zu öffnen.

    ![Kachel „Betrag“](media/service-dashboard-edit-tile/power-bi-amount-tile.png)

2. Öffnen Sie den Bericht in der Bearbeitungsansicht, indem Sie auf der oberen Menüleiste **Bericht bearbeiten** auswählen.

3. Fügen Sie eine neue Berichtsseite hinzu, indem Sie das Pluszeichen (+) am unteren Rand des Berichts auswählen.

    ![Pluszeichen](media/service-dashboard-edit-tile/power-bi-add-page.png)

4. Wählen Sie im Bereich „FELDER“ **Fakt > Betrag** und **Geschäftsbereich > Geschäftsbereich** aus.
 
5. Wählen Sie im Bereich „VISUALISIERUNGEN“ das Ringdiagrammsymbol aus, um die Visualisierung in ein Ringdiagramm zu konvertieren.

    ![Bereich „Visualisierungen“](media/service-dashboard-edit-tile/power-bi-donut-chart.png)

5. Wählen Sie das Anheftsymbol aus, und heften Sie das Ringdiagramm an das Dashboard „Analysebeispiel für IT-Ausgaben“ an.

   ![Zeigen Sie auf eine Kachel](media/service-dashboard-edit-tile/power-bi-pin.png)

6. Wenn die Erfolgsmeldung angezeigt wird, wählen Sie **Zum Dashboard wechseln** aus. Sie werden aufgefordert, die Änderungen zu speichern. Wählen Sie **Speichern**.

- - -
<a name="move"></a>

## <a name="move-the-tile"></a>Verschieben der Kachel
Suchen Sie die neue Kachel auf dem Dashboard. Wählen Sie die Kachel aus und halten Sie sie, um sie auf eine neue Position im Dashboardbereich zu ziehen.

- - -
<a name="resize"></a>

## <a name="resize-the-tile"></a>Ändern der Größe der Kachel
Sie können Kacheln in vielen unterschiedlichen Größen erstellen – von 1 x 1 Kacheleinheiten bis zu 5 x 5. Wählen Sie den Ziehpunkt (in der unteren rechten Ecke) aus, und ziehen Sie diesen, um die Größe der Kachel zu ändern.

![Video](media/service-dashboard-edit-tile/pbigif_resizetile4.gif)

- - -
## <a name="more-options--menu"></a>Menü **Weitere Optionen** (...)

1. Wählen Sie **Weitere Optionen** (...) in der rechten oberen Ecke der Kachel aus. 
   
   ![Kachel „Auslassungspunkte“](media/service-dashboard-edit-tile/power-bi-tile.png)

2. Zeigen Sie auf die Kachel „Konto“, und wählen Sie die Auslassungspunkte aus, um die Optionen anzuzeigen. Die verfügbaren Optionen variieren je nach Kacheltyp.  Beispielsweise unterscheiden sich die für eine Live-Kachel verfügbaren Optionen von den Optionen, die für eine Standardvisualisierungskachel verfügbar sind. Zudem verfügen Sie für ein Dashboard, das für Sie freigegeben wurde (Sie sind nicht der Besitzer), über weniger Optionen.

   ![Optionsmenü mit Auslassungspunkten](media/service-dashboard-edit-tile/power-bi-tile-menu-new.png)

3. Wählen Sie **Details bearbeiten** aus, um das Fenster „Kacheldetails“ zu öffnen. 

    Ändern Sie den Titel und das Standardverhalten der Kachel.  Sie können z.B. festlegen, dass bei Auswahl einer Kachel durch einen *Nutzer* nicht der zum Erstellen dieser Kachel verwendete Bericht, sondern ein neues Dashboard angezeigt wird.  
   


<a name="rename"></a>

### <a name="rename-the-tile"></a>Umbenennen der Kachel
Ändern Sie am oberen Rand des Fensters „Kacheldetails“ den **Titel** in **Ausgegebener Betrag**.

![Fenster „Kacheldetails“](media/service-dashboard-edit-tile/power-bi-tile-title.png)


<a name="hyperlink"></a>

### <a name="change-the-default-hyperlink"></a>Ändern des Standardhyperlinks
Standardmäßig gelangen Sie durch Auswählen einer Kachel zu dem Bericht, in dem die Kachel erstellt wurde, oder zu Q&A (sofern die Kachel in Q&A erstellt wurde). Um eine Webseite, ein anderes Dashboard oder einen anderen Bericht (in demselben Arbeitsbereich), einen SSRS-Bericht oder andere Onlineinhalte zu verlinken, fügen Sie einen benutzerdefinierten Link hinzu.

1. Wählen Sie unter der Überschrift „Funktionalität“ **Benutzerdefinierte Verknüpfung festlegen** aus.

2. Wählen Sie **Verknüpfung mit einem Dashboard oder Bericht im aktuellen Arbeitsbereich** aus, und wählen Sie dann in der Dropdownliste ein Dashboard aus.  In diesem Beispiel habe ich das Dashboard „Beispiel für Personalwesen“ ausgewählt. Wenn Ihr Arbeitsbereich dieses Beispiel noch nicht enthält, können Sie es hinzufügen und dann zu diesem Schritt zurückkehren, oder Sie können ein anderes Dashboard auswählen. 

    ![Dialog „Funktionalität“](media/service-dashboard-edit-tile/power-bi-custom-link.png)

3. Klicken Sie auf **Übernehmen**.

4. Auf der Kachel wird der neue Titel angezeigt.  Und wenn Sie die Kachel auswählen, wird in Power BI das Personalwesen-Dashboard geöffnet. 

    ![Kachel „Titel“](media/service-dashboard-edit-tile/power-bi-title.png)

<a name="different"></a>

### <a name="pin-the-tile-to-a-different-dashboard"></a>Heften Sie die Kachel an ein anderes Dashboard an.
1. Wählen Sie im Dropdownmenü mit den drei Punkten **Kachel anheften** ![Stecknadelsymbol](media/service-dashboard-edit-tile/pinnooutline.png) aus.
2. Entscheiden Sie, ob Sie ein Duplikat dieser Kachel an ein vorhandenes oder ein neues Dashboard anheften möchten. 
   
   ![Dialogfeld „An das Dashboard anheften“](media/service-dashboard-edit-tile/pbi_pintoanotherdash.png)
3. Wählen Sie **Anheften**aus.

<a name="delete"></a>

### <a name="delete-the-tile"></a>Löschen der Kachel
1. Wählen Sie im Dropdownmenü mit den drei Punkten **Kachel löschen** ![Symbol „Löschen“](media/service-dashboard-edit-tile/power-bi-delete-tile-icon.png) aus, um eine Kachel dauerhaft aus einem Dashboard zu entfernen. 

2. Durch Löschen einer Kachel wird nicht die zugrunde liegende Visualisierung gelöscht. Öffnen Sie den zugrunde liegenden Bericht, indem Sie die Kachel „Betrag“ auswählen. Öffnen Sie die letzte Seite im Bericht, um sich zu vergewissern, dass die ursprüngliche Visualisierung nicht aus dem Bericht gelöscht wurde. 

- - -
## <a name="next-steps"></a>Nächste Schritte
[Dashboardkacheln in Power BI](consumer/end-user-tiles.md)

[Dashboards in Power BI](consumer/end-user-dashboards.md)

[Grundlegende Konzepte für Designer im Power BI-Dienst](service-basic-concepts.md)

Weitere Fragen? [Wenden Sie sich an die Power BI-Community](https://community.powerbi.com/)

