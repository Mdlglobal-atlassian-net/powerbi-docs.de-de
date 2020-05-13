---
title: Erstellen eines Berichts in einer SharePoint-Liste
description: In diesem Tutorial wird gezeigt, wie Sie die Daten in den SharePoint-Listen in einen Power BI-Bericht transformieren.
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: tutorial
ms.date: 01/10/2020
ms.author: davidi
LocalizationGroup: Visualizations
ms.openlocfilehash: 4fd350ae5d4a916e6753f7cd66e1fca52137efd5
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/13/2020
ms.locfileid: "83288658"
---
# <a name="create-a-report-on-a-sharepoint-list"></a>Erstellen eines Berichts in einer SharePoint-Liste

Viele Teams und Organisationen verwenden Listen in SharePoint Online, um Daten zu speichern, da sie einfach einzurichten sind und leicht für Benutzer aktualisiert werden können.  In manchen Fällen können Benutzer Daten anhand eines Diagramms deutlich besser verstehen, als wenn sie sich die Liste ansehen. In diesem Tutorial wird gezeigt, wie Sie die Daten in den SharePoint-Listen in einen Power BI-Bericht transformieren.

Sehen Sie sich dieses fünfminütige Videotutorial an, oder führen Sie einen Bildlauf nach unten durch, um eine Schritt-für-Schritt-Anleitung zu erhalten.

<iframe width="400" height="450" src="https://www.youtube.com/embed/OZO3x2NF8Ak" frameborder="0" allowfullscreen></iframe>

## <a name="part-1-connect-to-your-sharepoint-list"></a>Teil 1: Verbinden mit SharePoint-Listen

1. Laden Sie [Power BI Desktop](https://powerbi.microsoft.com/desktop/) herunter, und installieren Sie die Anwendung, wenn Sie dies noch nicht getan haben.
2. Öffnen Sie Power BI Desktop, und wählen Sie auf der Registerkarte „Start“ des Menübands **Daten abrufen** > **Mehr**aus.
3. Wählen Sie **Onlinedienste** und anschließend **SharePoint Online-Liste** aus.  

    <img src="media/desktop-sharepoint-online-list/desktop-sharepoint-online-list-getdata.png" alt="get data" width="350"/>

4. Wählen Sie **Verbinden** aus.
4. Suchen Sie die Adresse (auch als URL bezeichnet) der SharePoint Online-Website, die die Liste enthält.  Sie können in der Regel über eine Seite in SharePoint Online die Adresse der Website abrufen, indem Sie im Navigationsbereich **Start** oder das Symbol für die Website am oberen Rand auswählen. Kopieren Sie anschließend die Adresse aus der Adressleiste des Webbrowsers.

   Sehen Sie sich ein Video zu diesem Schritt an:
   <iframe width="400" height="300" src="https://www.youtube.com/embed/OZO3x2NF8Ak?start=48&end=90" frameborder="0" allowfullscreen></iframe>

5. Fügen Sie die Adresse in Power BI Desktop in das Feld **Website-URL** im Dialogfeld „Öffnen“ ein.

6. Ein SharePoint-Zugriffsbildschirm wie in der folgenden Abbildung wird möglicherweise nicht angezeigt.  Wenn keiner angezeigt wird, fahren Sie mit Schritt 10 fort.  Wenn einer angezeigt wird, wählen Sie links auf der Seite **Microsoft-Konto** aus.

    <img src="media/desktop-sharepoint-online-list/desktop-sharepoint-online-list-auth1.png" alt="choose Microsoft account" width="500"/>

7. Wählen Sie **Anmelden** aus, und geben Sie den Benutzernamen und das Kennwort ein, mit denen Sie sich bei Microsoft Office 365 anmelden.

    <img src="media/desktop-sharepoint-online-list/desktop-sharepoint-online-list-auth2.png" alt="sign in" width="500"/>

8. Wenn Sie die Anmeldung abgeschlossen haben, wählen Sie **Verbinden** aus.

9. Aktivieren Sie auf der linken Seite des Navigators das Kontrollkästchen neben der SharePoint-Liste, mit der Sie eine Verbindung herstellen möchten.

    <img src="media/desktop-sharepoint-online-list/desktop-sharepoint-online-list-select-list.png" alt="get data" width="450"/>

10. Wählen Sie **Laden** aus.  Power BI lädt die Listendaten in einen neuen Bericht.

## <a name="part-2-create-a-report"></a>Teil 2: Erstellen eines Berichts

1. Wählen Sie auf der linken Seite das Symbol **Daten** aus, um zu überprüfen, ob die Daten der SharePoint-Liste geladen wurden.

2. Stellen Sie sicher, dass in den Listenspalten mit Zahlen das Summen- oder Sigma-Symbol rechts im **Bereich „Felder“** angezeigt wird.  Wählen Sie für jede Spalte ohne Symbol die Spaltenüberschrift in der Tabellenansicht aus, klicken Sie auf die Registerkarte **Modellierung**, und ändern Sie dann den **Datentyp** abhängig von den Daten in **Dezimalzahl** bzw. **Ganzzahl**.  Wenn Sie aufgefordert werden, die Änderung zu bestätigen, wählen Sie **Ja** aus.  Wenn die Zahl in einem speziellen Format (z. B. Währung) angegeben wird, können Sie diese Option auch auswählen, indem Sie das **Format** festlegen.

   Sehen Sie sich ein Video zu diesem Schritt an:
   <iframe width="400" height="300" src="https://www.youtube.com/embed/OZO3x2NF8Ak?start=147&end=204" frameborder="0" allowfullscreen></iframe>

3. Wählen Sie auf der linken Seite das Symbol **Bericht** aus.
4. Wählen Sie die Spalten aus, die Sie visualisieren möchten, indem Sie im Bereich **Felder** auf der rechten Seite auf das Kontrollkästchen klicken.

   Sehen Sie sich ein Video zu diesem Schritt an:
   <iframe width="400" height="300" src="https://www.youtube.com/embed/OZO3x2NF8Ak?start=215&end=252" frameborder="0" allowfullscreen></iframe>

5. Ändern Sie ggf. den visuellen Typ.
6. Sie können mehrere Visualisierungen im gleichen Bericht erstellen, indem Sie die Auswahl des vorhandenen visuellen Elements aufheben und dann im Bereich **Felder** die Kontrollkästchen für weitere Spalten auswählen.
7. Wählen Sie **Speichern** aus, um den Bericht zu speichern.
