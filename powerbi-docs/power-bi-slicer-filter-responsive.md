---
title: Erstellen eines dynamischen Datenschnitts mit anpassbarer Größe in Power BI
description: Hier erfahren Sie, wie Sie einen dynamischen Datenschnitt erstellen, dessen Größe Sie an Ihren Bericht anpassen können.
author: maggiesMSFT
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 04/06/2020
ms.author: maggies
LocalizationGroup: Create reports
ms.openlocfilehash: 2feb20907bbcffcb8aa395705b34604ebbedb682
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "81006501"
---
# <a name="create-a-responsive-slicer-you-can-resize-in-power-bi"></a>Erstellen eines dynamischen Datenschnitts mit anpassbarer Größe in Power BI

[!INCLUDE [applies-to](includes/applies-to.md)] [!INCLUDE [yes-desktop](includes/yes-desktop.md)] [!INCLUDE [yes-service](includes/yes-service.md)]

Bei dynamischen Datenschnitten kann die Größe an einen Bericht angepasst werden. Sie können dynamische Datenschnitte in verschiedenen Größen und Formen anzeigen, von horizontal über quadratisch zu vertikal. Dabei werden die Werte im Datenschnitt automatisch neu angeordnet. In Power BI Desktop und im Power BI-Dienst können Sie horizontale Datenschnitte und Datums-/Bereichsdatenschnitte als dynamisch konfigurieren. Datums-/Bereichsdatenschnitte verfügen außerdem über optimierte Touchbereiche und können daher ganz einfach mit einem Fingertippen geändert werden. Sie können dynamische Datenschnitte beliebig klein oder groß erstellen. Sie werden automatisch angepasst, um perfekt in Berichte sowohl im Power BI-Dienst und auch in den mobilen Power BI-Apps zu passen. 

![Verschiedene Formen eines dynamischen Datenschnitts](media/power-bi-slicer-filter-responsive/power-bi-slicer-filter-responsive-0-slicer.gif)

## <a name="create-a-slicer"></a>Erstellen von Slicern

Der erste Schritt beim Erstellen eines dynamischen Datenschnitts besteht darin, einen einfachen Datenschnitt zu erstellen. 

1. Wählen Sie im Bereich **Visualisierungen** das ![Datenschnittsymbol](media/power-bi-slicer-filter-responsive/power-bi-slicer-filter-responsive-0-slicer-icon.png)**Datenschnittsymbol** aus.
2. Ziehen Sie das Feld, das gefiltert werden soll, auf **Feld**.

    ![Feld im Datenschnitt hinzufügen](media/power-bi-slicer-filter-responsive/power-bi-slicer-filter-responsive-1-create.png)

## <a name="convert-to-a-horizontal-slicer"></a>Konvertieren in einen horizontalen Datenschnitt

1. Wählen Sie einen Datenschnitt aus. Wählen Sie dann im Bereich **Visualisierungen** den Abschnitt **Format** aus.
2. Erweitern Sie den Abschnitt **Allgemein**, und wählen Sie dann unter **Ausrichtung** die Option **Horizontal** aus.

    ![Datenschnitt auf „Horizontal“ festlegen](media/power-bi-slicer-filter-responsive/power-bi-slicer-filter-responsive-2-horizontal.png) 

1.  Sie möchten den Datenschnitt wahrscheinlich breiter machen, um weitere Werte anzuzeigen.

     ![Datenschnitt verbreitern](media/power-bi-slicer-filter-responsive/power-bi-slicer-filter-responsive-3-wider.png)

## <a name="make-it-responsive-and-experiment-with-it"></a>Hinzufügen der Dynamik und Testen

Dieser Schritt ist einfach. 

1. Stellen Sie direkt unter **Ausrichtung** im Abschnitt **Allgemein** der Registerkarte **Format** den Schalter **Dynamisch** auf **Ein**.  

    ![Der Datenschnitt ist jetzt dynamisch.](media/power-bi-slicer-filter-responsive/power-bi-slicer-filter-responsive-4-responsive-on.png)

1. Jetzt können Sie damit etwas experimentieren. Ziehen Sie die Ecken, um ihn kurz, lang, breit oder schmal anzuzeigen. Wenn Sie ihn sehr klein anzeigen, sehen Sie nur ein Filtersymbol.

    ![Sehr kleiner Datenschnitt als Filtersymbol](media/power-bi-slicer-filter-responsive/power-bi-slicer-filter-responsive-5-mini-icon.png)

## <a name="add-it-to-a-phone-report-layout"></a>Hinzufügen zu einem Berichtslayout für Smartphones

In Power BI Desktop können Sie ein Telefonlayout für jede Seite eines Berichts erstellen. Wenn eine Seite über ein Telefonlayout verfügt, wird sie auf Mobiltelefonen im Hochformat angezeigt. Andernfalls müssen Sie sie im Querformat anzeigen. 

1. Wählen Sie im Menü **Ansicht** die Option **Telefonlayout** aus.

     ![Symbol „Telefonlayout“, Menü „Ansicht“](media/power-bi-slicer-filter-responsive/power-bi-slicer-filter-responsive-6-phone-layout-button.png)
    
1. Ziehen Sie alle Visuals, die der Telefonbericht enthalten soll, in das Raster. Ziehen Sie den dynamischen Datenschnitt auf die gewünschte Größe – in diesem Fall nur ein Filtersymbol.

    ![Datenschnitt zum Telefonberichtslayout hinzufügen](media/power-bi-slicer-filter-responsive/power-bi-slicer-filter-responsive-7-phone-slicer-icon.png)

Weitere Informationen zum Erstellen von [für mobile Power BI-Apps optimierten Berichten](desktop-create-phone-report.md).

## <a name="make-a-time-or-range-slicer-responsive"></a>Hinzufügen von Dynamik für Zeit- oder Berichtsdatenschnitte

Sie können die gleichen Schritte ausführen, um einen Kachel- oder Berichtsdatenschnitt als dynamischen Datenschnitt zu konfigurieren. Wenn Sie **Dynamisch** auf **Ein** festlegen, werden Sie verschiedene Dinge bemerken:

- Bei Visuals wird die Reihenfolge der Eingabefelder abhängig von der Größe des Zeichenbereichs optimiert. 
- Die Anzeige von Datenelementen wird optimiert, damit der Datenschnitt abhängig vom verfügbaren Platz im Zeichenbereich so benutzerfreundlich wie möglich ist. 
- Durch neue, runde Ziehpunkte an den Schiebereglern werden Touchinteraktionen optimiert. 
- Wenn ein Visual zu klein wird, um noch nützlich zu sein, wird sie stattdessen als Symbol dargestellt, das den Typ des Visuals zeigt. Tippen Sie auf das Symbol, um die Visualisierung im Fokusmodus zu öffnen und damit zu interagieren. Hierdurch wird Platz auf der Berichtsseite gespart, ohne dabei Funktionalität zu verlieren.

## <a name="next-steps"></a>Weitere Schritte

- [Slicer im Power BI-Dienst](visuals/power-bi-visualization-slicers.md)
- Weitere Fragen? [Stellen Sie Ihre Frage in der Power BI-Community.](https://community.powerbi.com/)