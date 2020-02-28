---
title: Hinzufügen von Links (URLs) zu einer Tabelle oder Matrix
description: In diesem Thema erfahren Sie, wie einer Tabelle Links (URLs) hinzugefügt werden. Sie verwenden Power BI Desktop, um einem Dataset Links (URLs) hinzuzufügen. Dann können Sie diese Links entweder in Power BI Desktop oder im Power BI-Dienst zu Ihren Berichtstabellen und Matrizen hinzufügen.
author: maggiesMSFT
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 02/13/2020
ms.author: maggies
LocalizationGroup: Visualizations
ms.openlocfilehash: f8a49780804449296194d7adb8091f7f0c5748fe
ms.sourcegitcommit: d6a48e6f6e3449820b5ca03638b11c55f4e9319c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/18/2020
ms.locfileid: "77427804"
---
# <a name="add-hyperlinks-urls-to-a-table-or-matrix"></a>Hinzufügen von Links (URLs) zu einer Tabelle oder Matrix
In diesem Thema erfahren Sie, wie einer Tabelle Links (URLs) hinzugefügt werden. Sie verwenden Power BI Desktop, um einem Dataset Links (URLs) hinzuzufügen. Sie können diese Links entweder in Power BI Desktop oder im Power BI-Dienst zu Ihren Berichtstabellen und Matrizen hinzufügen. Anschließend können Sie die URL oder ein Linksymbol anzeigen oder eine andere Spalte als Linktext formatieren.

![Tabelle mit Links](media/power-bi-hyperlinks-in-tables/power-bi-url-link-text.png)

Es ist ebenfalls möglich, Links im Power BI-Dienst und in Power BI Desktop in [Textfeldern in Berichten](service-add-hyperlink-to-text-box.md) zu erstellen. Und im Power BI-Dienst können Sie Links zu [Kacheln in Dashboards](service-dashboard-edit-tile.md) und zu [Textfeldern in Dashboards](service-dashboard-add-widget.md) hinzufügen. 


## <a name="format-a-url-as-a-hyperlink-in-power-bi-desktop"></a>Formatieren einer URL als Link in Power BI Desktop

Sie können ein Feld mit URLs in Power BI Desktop als Links formatieren, nicht jedoch im Power BI-Dienst erstellen. Sie können außerdem [Links in Power Pivot für Excel formatieren](#create-a-table-or-matrix-hyperlink-in-excel-power-pivot), bevor Sie die Arbeitsmappe in Power BI importieren.

1. Wenn der Link in Power BI Desktop nicht bereits als Feld mit Link in Ihrem Dataset vorhanden ist, fügen Sie ihn als [benutzerdefinierte Spalte](desktop-common-query-tasks.md) hinzu.

    > [!NOTE]
    > Im DirectQuery-Modus kann keine Spalte erstellt werden.  Wenn die Daten jedoch bereits URLs enthalten, können Sie diese in Hyperlinks umwandeln.

2. Wählen Sie die Spalte in der Datenansicht oder der Berichtsansicht aus. 

3. Wählen Sie auf der Registerkarte **Modellierung** **Datenkategorie** > **Web-URL** aus.
   
    ![Dropdownliste „Datenkategorie“](media/power-bi-hyperlinks-in-tables/power-bi-format-web-url.png)

    > [!NOTE]
    > URLs müssen mit bestimmten Präfixen beginnen. Die vollständige Liste finden Sie unter [Zu beachtende Aspekte und Problembehandlung](#considerations-and-troubleshooting) in diesem Artikel.

## <a name="create-a-table-or-matrix-with-a-hyperlink"></a>Erstellen einer Tabelle oder Matrix mit einem Link

1. Nachdem Sie einen [Link als URL formatiert](#format-a-url-as-a-hyperlink-in-power-bi-desktop) haben, wechseln Sie zur Berichtsansicht.
2. Erstellen Sie eine Tabelle oder Matrix mit dem Feld, das Sie als Web-URL kategorisiert haben. Die Links werden blau und unterstrichen angezeigt.

    ![Blaue und unterstrichene Links](media/power-bi-hyperlinks-in-tables/power-bi-url-blue-underline.png)


## <a name="display-a-hyperlink-icon-instead-of-a-url"></a>Anzeigen eines Linksymbols anstelle einer URL

Wenn keine lange URL in einer Tabelle angezeigt werden soll, können Sie stattdessen ein Linksymbol ![Linksymbol](media/power-bi-hyperlinks-in-tables/power-bi-hyperlink-icon.png) anzeigen lassen. 

> [!NOTE]
> Symbole können nicht in Matrizen angezeigt werden.
   
1. Erstellen Sie zunächst [eine Tabelle mit einem Link](#create-a-table-or-matrix-with-a-hyperlink).

2. Wählen Sie die Tabelle aus, um sie zu aktivieren.

    Wählen Sie das Symbol **Format** ![Farbrollensymbol](media/power-bi-hyperlinks-in-tables/power-bi-paintroller.png) aus, um die Registerkarte für die Formatierung zu öffnen.

    Erweitern Sie **Werte**, suchen Sie das **URL-Symbol**, und aktivieren Sie es mit **Ein**.

    ![URL-Symbol aktivieren](media/power-bi-hyperlinks-in-tables/power-bi-url-icon-on.png)

1. (Optional) [Veröffentlichen Sie den Bericht](desktop-upload-desktop-files.md) aus Power BI Desktop im Power BI-Dienst. Wenn Sie den Bericht im Power BI-Dienst öffnen, funktionieren die Links auch hier.

## <a name="format-link-text-as-a-hyperlink"></a>Formatieren von Linktext als Link

Sie können auch ein anderes Feld in einer Tabelle als Link formatieren und keine Spalte für die URL einrichten. In diesem Fall formatieren Sie die Spalte nicht als Web-URL.

> [!NOTE]
> In einer Matrix können Sie kein anderes Feld als Link formatieren.

1. Wenn nicht bereits ein Feld mit einem Link in Ihrem Dataset vorhanden ist, verwenden Sie Power BI Desktop, um es als [benutzerdefinierte Spalte](desktop-common-query-tasks.md) hinzuzufügen. Wie bereits erwähnt: Im DirectQuery-Modus kann keine Spalte erstellt werden.  Wenn die Daten jedoch bereits URLs enthalten, können Sie diese in Hyperlinks umwandeln.

2. Wählen Sie in der Datenansicht oder der Berichtsansicht die Spalte aus, die die URL enthält. 

3. Wählen Sie auf der Registerkarte **Modellierung** die Option **Datenkategorie** aus. Sorgen Sie dafür, dass die Spalte als **Nicht kategorisiert** formatiert ist.

2. Erstellen Sie in der Berichtsansicht eine Tabelle oder Matrix mit der URL-Spalte und der Spalte, die Sie als Linktext formatieren möchten.

3. Wählen Sie bei ausgewählter Tabelle das Symbol **Format** ![Farbrollensymbol](media/power-bi-hyperlinks-in-tables/power-bi-paintroller.png) aus, um die Registerkarte für die Formatierung zu öffnen.

4. Erweitern Sie **Bedingte Formatierung**, und stellen Sie sicher, dass der Name im Feld die Spalte ist, die Sie als Linktext verwenden möchten. Suchen Sie die Option **Web-URL**, und aktivieren Sie sie mit **Ein**.

    ![Bedingte Formatierung, Web-URL](media/power-bi-hyperlinks-in-tables/power-bi-format-conditional-web-url.png)

    > [!NOTE]
    > Wenn die Option **Web-URL** nicht angezeigt wird, stellen Sie sicher, dass die Spalte, die den Link enthält, im Dropdownfeld **Datenkategorie** *nicht* als **Web-URL**formatiert ist.

5. Wählen Sie im Dialogfeld **Web-URL** unter **Basierend auf Feld** das Feld aus, das die URL enthält, und klicken Sie auf **OK**.

    ![Dialogfeld „Web-URL“](media/power-bi-hyperlinks-in-tables/power-bi-format-web-url-dialog.png)

    Jetzt wird der Text in dieser Spalte als Link formatiert.

    ![Als Link formatierter Text](media/power-bi-hyperlinks-in-tables/power-bi-url-link-text.png)

1. (Optional) [Veröffentlichen Sie den Bericht](desktop-upload-desktop-files.md) aus Power BI Desktop im Power BI-Dienst. Wenn Sie den Bericht im Power BI-Dienst öffnen, funktionieren die Links auch hier.

## <a name="create-a-table-or-matrix-hyperlink-in-excel-power-pivot"></a>Erstellen eines Tabellen- oder Matrix-Hyperlinks in Power Pivot für Excel

Sie können Ihren Power BI-Tabellen und -Matrizen auch Hyperlinks hinzufügen, indem Sie die Hyperlinks im Dataset erstellen, bevor Sie das betreffende Dataset aus Power BI importieren bzw. eine Verbindung damit herstellen. In diesem Beispiel wird eine Excel-Arbeitsmappe verwendet.

1. Öffnen Sie die Arbeitsmappe in Excel.
2. Wählen Sie die Registerkarte **PowerPivot** und anschließend **Verwalten**.
   
   ![Öffnen von PowerPivot in Excel](media/power-bi-hyperlinks-in-tables/createhyperlinkinpowerpivot2.png)
1. Wenn PowerPivot geöffnet wird, wählen Sie die Registerkarte **Erweitert** aus.
   
   ![Registerkarte „PowerPivot – Erweitert“](media/power-bi-hyperlinks-in-tables/createhyperlinkinpowerpivot3.png)
4. Platzieren Sie den Cursor in der Spalte, die die URLs enthält, die in Links in Power BI-Tabellen umgewandelt werden sollen.
   
   > [!NOTE]
   > URLs müssen mit bestimmten Präfixen beginnen. Eine vollständige Liste finden Sie unter [Zu beachtende Aspekte und Problembehandlung](#considerations-and-troubleshooting).
   > 
   
5. Wählen Sie in der Gruppe **Berichtseigenschaften** die Dropdownliste **Datenkategorie** und wählen Sie dann **Web-URL**aus. 
   
   ![Dropdownliste „Datenkategorie“ in Excel](media/power-bi-hyperlinks-in-tables/createhyperlinksnew.png)

6. Stellen Sie aus dem Power BI-Dienst oder Power BI Desktop eine Verbindung mit dieser Arbeitsmappe her, oder importieren Sie sie.
7. Erstellen Sie eine Tabellenvisualisierung, die das URL-Feld enthält.
   
   ![Erstellen einer Tabelle in Power BI mit URL-Feld](media/power-bi-hyperlinks-in-tables/hyperlinksintables.gif)

## <a name="considerations-and-troubleshooting"></a>Zu beachtende Aspekte und Problembehandlung

URLs müssen folgendermaßen beginnen:
- http
- https
- -mailto
- file
- ftp
- news
- telnet

F: Kann ich eine benutzerdefinierte URL als Link in einer Tabelle oder Matrix verwenden?    
A: Nein. Sie können ein Linksymbol verwenden. Wenn Sie benutzerdefinierten Text für Ihre Links benötigen und die Liste der URLs kurz ist, sollten Sie stattdessen ein Textfeld verwenden.


## <a name="next-steps"></a>Nächste Schritte
[Visualisierungen in Power BI-Berichten](visuals/power-bi-report-visualizations.md)

[Grundlegende Konzepte für Designer im Power BI-Dienst](service-basic-concepts.md)

Weitere Fragen? [Wenden Sie sich an die Power BI-Community](https://community.powerbi.com/)

