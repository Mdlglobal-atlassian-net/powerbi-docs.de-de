---
title: Einrichten des Drillthroughfeatures in Power BI-Berichten
description: Hier erfahren Sie, wie Sie auf einer neuen Berichtsseite in Power BI-Berichten Drilldowns in Daten ausführen.
author: maggiesMSFT
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 03/12/2020
ms.author: maggies
LocalizationGroup: Create reports
ms.openlocfilehash: 9f017a4e93e76d91949b3cc3e12ef0c652664a91
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/13/2020
ms.locfileid: "83281436"
---
# <a name="set-up-drill-through-in-power-bi-reports"></a>Einrichten des Drillthroughfeatures in Power BI-Berichten
Mit einem *Drillthrough* können Sie in Power BI-Berichten eine Seite erstellen, die sich auf eine bestimmte Entität konzentriert, z. B. auf einen Lieferanten, einen Kunden oder einen Hersteller. Wenn Ihre Berichtsleser einen Drillthrough verwenden möchten, klicken sie mit der rechten Maustaste auf einen Datenpunkt auf anderen Berichtsseiten und führen einen Drillthrough zu der fokussierten Seite aus, um Details abzurufen, die entsprechend diesem Kontext gefiltert sind. Sie können auch eine [Schaltfläche erstellen, die einen Drilltrough in Details ausführt](desktop-drill-through-buttons.md), wenn auf sie geklickt wird.

Sie können das Drillthroughfeature in Ihren Berichten in Power BI Desktop oder im Power BI-Dienst einrichten.

![Verwenden des Drillthroughfeatures](media/desktop-drillthrough/power-bi-drill-through-right-click.png)

## <a name="set-up-the-drill-through-destination-page"></a>Einrichten der Zielseite für Drillthroughs
1. Für die Einrichtung des Drillthroughfeatures erstellen Sie eine Berichtsseite mit den Visuals, die Sie für den Entitätstyp benötigen, für den Sie das Drillthroughfeature bereitstellen möchten. 

    Angenommen, Sie möchten einen Drillthrough für Hersteller ausführen. In diesem Fall können Sie eine Drillthroughseite mit Visuals erstellen, die z. B. den Gesamtumsatz, die Summe der versandten Einheiten, den Umsatz nach Kategorie oder den Umsatz nach Region anzeigen. Das heißt, wenn Sie einen Drillthrough für diese Seite ausführen, gelten die Visuals spezifisch für den ausgewählten Hersteller.

2. Ziehen Sie dann auf der Drillthroughseite im Bereich **Visualisierungen** im Abschnitt **Felder** das Feld, für das Sie das Drillthroughfeature aktivieren möchten, in den Bereich **Drillthroughfilter**.

    ![Drillthroughbereich](media/desktop-drillthrough/drillthrough_02.png)

    Wenn Sie dem Bereich **Drillthroughfilter** ein Feld hinzufügen, wird in Power BI automatisch ein *Zurück*-Schaltflächenvisual erstellt. Das Visual wird zur Schaltfläche in veröffentlichten Berichten. Benutzer, die Ihren Bericht im Power BI-Dienst nutzen, kehren mithilfe dieser Schaltfläche zu der Ausgangsberichtsseite zurück.

    ![Drillthroughabbildung](media/desktop-drillthrough/drillthrough_03.png)

> [!IMPORTANT]
> Sie können einen Drillthrough zu einer Seite im selben Bericht konfigurieren und ausführen. Sie können jedoch keinen Drillthrough zu einer Seite in einem anderen Bericht ausführen.  



## <a name="use-your-own-image-for-a-back-button"></a>Verwenden eines eigenen Bildes für die Schaltfläche „Zurück“    
 Da die Schaltfläche „Zurück“ ein Bild ist, können Sie das Bild dieses Visuals durch ein beliebiges Bild ersetzen. Das Visual wird weiterhin als Schaltfläche „Zurück“ fungieren, sodass die Berichtsleser zur vorherigen Seite zurückkehren können. 

Führen Sie die folgenden Schritte aus, um ein eigenes Bild für die Schaltfläche „Zurück“ zu verwenden:

1. Wählen Sie auf der Registerkarte **Start** die Option **Bild** aus. Suchen Sie dann Ihr Bild, und platzieren Sie es auf der Drillthroughseite.

2. Wählen Sie Ihr neues Bild auf der Drillthroughseite aus. Legen Sie im Bereich **Bild formatieren** den Schieberegler **Aktion** auf **Ein** und dann **Typ** auf **Zurück** fest. Jetzt funktioniert das Bild als Schaltfläche „Zurück“.

    ![Laden des Bilds und Festlegen des Typs auf „Zurück“](media/desktop-drillthrough/drillthrough_05.png)

    
     Jetzt können Benutzer mit der rechten Maustaste auf einen Datenpunkt in Ihrem Bericht klicken, um ein Kontextmenü aufzurufen, das das Drillthroughfeature für diese Seite unterstützt. 

    ![Drillthroughmenü](media/desktop-drillthrough/drillthrough_04.png)

    Wenn Berichtsleser einen Drillthrough ausführen, wird die Seite gefiltert, um Informationen zum Datenpunkt anzuzeigen, auf den mit der rechten Maustaste geklickt wurde. Angenommen, sie klicken mit der rechten Maustaste auf einen Datenpunkt für den Hersteller Contoso und wählen die Drillthroughfunktion aus. Die Drillthroughseite, auf die sie wechseln, wird nach Contoso gefiltert.

## <a name="pass-all-filters-in-drill-through"></a>Übergeben aller Filter an Drillthrough

Sie können alle angewendeten Filter an das Drillthroughfenster übergeben. Sie können z. B. nur eine bestimmte Produktkategorie auswählen und die dafür gefilterten Visuals auswählen und führen dann einen Drillthrough aus. Es interessiert Sie vielleicht, wie dieser Drillthrough mit all diesen angewendeten Filtern aussieht.

Damit alle angewendeten Filter beibehalten werden, legen Sie im Bereich **Visualisierungen** im Abschnitt **Drillthrough** die Option **Alle Filter beibehalten** auf **Ein** fest. 

![Alle Filter beibehalten](media/desktop-drillthrough/drillthrough_06.png)

Beim anschließenden Drillthrough für ein Visual können Sie sehen, welche Filter angewendet wurden, weil auf das Quellvisual temporäre Filter angewendet wurden. Im Abschnitt **Drillthrough** des Bereichs **Visualisierung** werden diese vorübergehenden Filter kursiv dargestellt. 

![Vorübergehende Filter in Kursivschrift](media/desktop-drillthrough/drillthrough_07.png)

Obwohl Sie dafür auch die QuickInfoseiten verwenden können, wäre diese verwirrend, da es dann den Anschein hätte, dass die QuickInfo nicht ordnungsgemäß funktioniert. Deswegen wird nicht empfohlen, mit QuickInfos zu arbeiten.

## <a name="add-a-measure-to-drill-through"></a>Hinzufügen eines Measures zu einem Drillthrough

Sie können alle Filter an das Drillthroughfenster übergeben und zusätzlich ein Measure oder eine zusammengefasste numerische Spalte dem Drillthroughbereich hinzufügen. Ziehen Sie das Drillthroughfeld auf die Karte **Drillthrough**, um es anzuwenden. 

![Hinzufügen eines Measures zu einem Drillthrough](media/desktop-drillthrough/drillthrough_08.png)

Wenn Sie ein Measure oder eine zusammengefasste numerische Spalte hinzufügen, können Sie einen Drillthrough für die Seite ausführen, wenn das Feld im Bereich *Wert* eines Visuals verwendet wird.

Das ist bereits alles, was Sie über das Verwenden des Drillthroughfeatures in Berichten wissen müssen. Das Feature bietet eine hervorragende Möglichkeit, eine erweiterte Ansicht der Entitätsinformationen zu erhalten, die Sie für den Drillthroughfilter auswählen.

## <a name="next-steps"></a>Weitere Schritte

Folgende Artikel könnten Sie ebenfalls interessieren:

* [Verwenden der berichtsübergreifenden Drillthroughfunktion in Power BI](desktop-cross-report-drill-through.md)
* [Verwenden von Slicern in Power BI Desktop](../visuals/power-bi-visualization-slicers.md)
