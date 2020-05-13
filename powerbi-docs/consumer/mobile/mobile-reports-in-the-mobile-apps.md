---
title: Durchsuchen von Berichten in den mobilen Power BI-Apps
description: Hier erfahren Sie, wie Sie in den mobilen Power BI-Apps auf Ihrem Telefon oder Tablet Berichte anzeigen und mit diesen interagieren. Sie erstellen Berichte im Power BI-Dienst oder in Power BI Desktop und interagieren anschließend in mobilen Apps mit diesen.
author: paulinbar
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-mobile
ms.topic: conceptual
ms.date: 05/05/2020
ms.author: painbar
ms.openlocfilehash: 48b13b73455d39eb7dc8cbf9df3e95408592f7f5
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/13/2020
ms.locfileid: "83279501"
---
# <a name="explore-reports-in-the-power-bi-mobile-apps"></a>Durchsuchen von Berichten in den mobilen Power BI-Apps
Gilt für:

| ![iPhone](././media/mobile-reports-in-the-mobile-apps/ios-logo-40-px.png) | ![iPad](././media/mobile-reports-in-the-mobile-apps/ios-logo-40-px.png) | ![Android-Smartphone](././media/mobile-reports-in-the-mobile-apps/android-logo-40-px.png) | ![Android-Tablet](././media/mobile-reports-in-the-mobile-apps/android-logo-40-px.png) | ![Windows 10-Geräte](./media/mobile-reports-in-the-mobile-apps/win-10-logo-40-px.png) |
|:---: |:---: |:---: |:---: |:---: |
| iPhones |iPads |Android-Telefone |Android-Tablets |Windows 10-Geräte |

>[!NOTE]
>Die Unterstützung für die mobile Power BI-App für **Smartphones mit Windows 10 Mobile** wird am 16. März 2021 eingestellt. [Weitere Informationen](https://go.microsoft.com/fwlink/?linkid=2121400)

Ein Power BI-Bericht ist eine interaktive Ansicht Ihrer Daten, und mit den darin enthaltenen Visuals werden unterschiedliche Ergebnisse und Erkenntnisse zu diesen Daten dargestellt. Das Anzeigen von Berichten in den mobilen Power BI-Apps ist der dritte Schritt in einem dreistufigen Prozess:

1. [Erstellen Sie Berichte in Power BI Desktop](../../create-reports/desktop-report-view.md). Sie können in Power BI Desktop sogar [einen Bericht für Telefone optimieren](mobile-apps-view-phone-report.md).
2. Veröffentlichen Sie diese Berichte im Power BI-Dienst [(https://powerbi.com)](https://powerbi.com) oder auf dem [Power BI-Berichtsserver](../../report-server/get-started.md).  
3. Anschließend können Sie in den mobilen Power BI-Apps mit den Berichten interagieren.

## <a name="open-a-power-bi-report-in-the-mobile-app"></a>Öffnen eines Power BI-Berichts in der mobilen App
Power BI-Berichte werden abhängig von ihrer Herkunft an verschiedenen Stellen in der mobilen App gespeichert. Sie können sich in „Apps“, „Für mich freigegeben“, „Arbeitsbereiche“ (einschließlich „Mein Arbeitsbereich“) oder auf einem Berichtsserver befinden. Manchmal müssen Sie einen Bericht in einem zugehörigen Dashboard suchen, und manchmal sind Berichte aufgelistet.

In Listen und Menüs finden Sie ein Symbol neben einem Berichtsnamen, an dem Sie erkennen können, dass es sich bei dem Element um einen Bericht handelt:

![Berichte in „Mein Arbeitsbereich“](./media/mobile-reports-in-the-mobile-apps/reports-my-workspace.png)

Es gibt zwei Symbole für Berichte in den mobilen Power BI-Apps:

* ![Berichtssymbol](./media/mobile-reports-in-the-mobile-apps/report-default-icon.png) Dieses Symbol gibt an, dass der Bericht in der App im Querformat angezeigt wird. Er sieht also wie im Browser aus.

* ![Symbol für Smartphonebericht](./media/mobile-reports-in-the-mobile-apps/report-phone-icon.png) Dieses Symbol gibt an, dass der Bericht mindestens eine für Smartphones optimierte Seite enthält, die im Hochformat angezeigt wird.

> [!NOTE]
> Wenn Sie Ihr Smartphone im Querformat halten, wird immer das Querformat angezeigt, auch wenn die Berichtsseite in einem Layout für Mobilgeräte vorliegt.

Tippen Sie auf **Weitere Optionen** (...) in der rechten oberen Ecke einer Kachel, und wählen Sie dann **Bericht öffnen** aus, um einen Bericht eines Dashboards abzurufen:
  
  ![Bericht öffnen](./media/mobile-reports-in-the-mobile-apps/power-bi-android-open-report-tile.png)
  
  Nicht alle Kacheln können als Berichte geöffnet werden. Beispielsweise werden für Kacheln, die durch Stellen einer Frage im Q&A-Feld erstellt wurden, keine Berichte geöffnet, wenn Sie auf die Kachel tippen.
  
## <a name="interact-with-reports"></a>Interagieren mit Berichten
Nachdem Sie einen Bericht in der App geöffnet haben, können Sie mit diesem arbeiten. Mit Ihrem Bericht und dessen Daten können Sie vieles tun. In der Fußzeile des Berichts finden Sie Aktionen, die Sie für den Bericht ausführen können. Wenn Sie auf die im Bericht angezeigten Daten tippen bzw. lange tippen, können Sie Slice-and-Dice für Daten ausführen.

### <a name="single-tap-versus-double-tap-interaction"></a>Interaktion durch einfaches Tippen im Vergleich zum Doppeltippen
Wenn Sie die mobile Power BI-App herunterladen, ist hierfür die Interaktion durch einfaches Tippen festgelegt. Wenn Sie also auf ein Visual tippen, um eine Aktion durchzuführen, z. B. ein Datenschnittelement auswählen, Elemente übergreifend hervorheben oder auf einen Link oder eine Schaltfläche klicken, wird durch das Tippen sowohl das Visual ausgewählt als auch die gewünschte Aktion ausgeführt.

Wenn Sie möchten, können Sie die App auf die Interaktion durch Doppeltippen umstellen. Bei der Interaktion durch Doppeltippen tippen Sie zuerst auf das Visual, das Sie auswählen möchten, und dann in das Visual, um Ihre gewünschte Aktion auszuführen.

Um zur Interaktion durch Doppeltippen oder zurück zur Interaktion durch einfaches Tippen zu wechseln, navigieren Sie zu den [App-Interaktionseinstellungen](./mobile-app-interaction-settings.md).

### <a name="single-select-versus-multi-select-mode-for-data-point-selection"></a>Einzelauswahlmodus im Vergleich mit Mehrfachauswahlmodus für die Datenpunktauswahl

In einem Bericht tippen Sie auf einen Datenpunkt, um ihn auszuwählen. Sie können entscheiden, ob Sie den Einzel- oder den Mehrfachauswahlmodus verwenden möchten. Wenn Sie im Einzelauswahlmodus auf einen Datenpunkt tippen, um ihn auszuwählen, ersetzt diese Auswahl jede zuvor von Ihnen getroffene Auswahl. Wenn Sie im Mehrfachauswahlmodus auf einen Datenpunkt tippen, um ihn auszuwählen, wird diese Auswahl Ihrer bereits bestehenden Auswahl *hinzugefügt*, und das kombinierte Ergebnis Ihrer sämtlichen Auswahlaktionen wird in allen Visuals des Berichts hervorgehoben.

Um die Auswahl eines ausgewählten Datenpunkts aufzuheben, tippen Sie ihn einfach erneut an.

Um zwischen dem Einzelauswahl- und dem Mehrfachauswahlmodus zu wechseln, navigieren Sie zu den [App-Interaktionseinstellungen](./mobile-app-interaction-settings.md).

### <a name="using-tap-and-long-tap"></a>Verwenden von Antippen und langem Antippen
Ein Tippen gleicht einem Mausklick. Wenn Sie den Bericht auf Grundlage eines Datenpunkts übergreifend hervorheben möchten, tippen Sie auf den Datenpunkt.
Wenn Sie auf einen Datenschnittwert tippen, wird der Wert ausgewählt und für den Rest des Berichts wird ein Datenschnitt anhand des Werts durchgeführt.
Wenn Sie auf einen Link, eine Schaltfläche oder ein Lesezeichen tippen, wird die vom Berichtsautor definierte Aktion ausgeführt.

Wahrscheinlich haben Sie bemerkt, dass ein Rahmen angezeigt wird, wenn Sie auf ein Visual tippen. In der oberen rechten Ecke des Rahmens werden **Weitere Optionen** (...) angezeigt. Wenn Sie auf diese Auslassungspunkte tippen, wird ein Menü mit Aktionen angezeigt, die Sie an diesem Visual vornehmen können:

![Visual und Menü](./media/mobile-reports-in-the-mobile-apps/report-visual-menu.png)

### <a name="tooltip-and-drill-actions"></a>QuickInfo und Drillaktionen
Wenn Sie einen Datenpunkt lange antippen (tippen und halten), wird eine QuickInfo mit den Werten angezeigt, die dieser Datenpunkt repräsentiert:

![QuickInfo](./media/mobile-reports-in-the-mobile-apps/report-tooltip.png)

Wenn der Berichtsautor die QuickInfo einer Berichtsseite konfiguriert hat, wird die standardmäßige QuickInfo durch die QuickInfo der Berichtsseite ersetzt:

![QuickInfo für Berichtsseiten](./media/mobile-reports-in-the-mobile-apps/report-page-tooltip.png)

> [!NOTE]
> QuickInfos für Berichte werden für Geräte mit Viewports mit mindestens 640x320 Pixeln unterstützt. Wenn Ihr Gerät kleiner ist, zeigt die App die standardmäßigen QuickInfos an.

Berichtsautoren können Hierarchien in den Daten und Beziehungen zwischen Berichtsseiten definieren. Die Hierarchie ermöglicht den Drilldown, Drillup und Drillthrough in eine andere Berichtsseite aus einem Visual und einem Wert. Wenn Sie also zusätzlich zur QuickInfo lange auf einen Wert tippen, werden in der Fußzeile die entsprechenden Drilloptionen angezeigt:

![Drillaktionen](./media/mobile-reports-in-the-mobile-apps/report-drill-actions.png)


Wenn Sie auf einen bestimmten Teil eines Visuals tippen und dann die Option *Drillthrough* auswählen, navigiert Power BI zu einer anderen Seite im Bericht mit dem angetippten Wert als Filter. Der Berichtsautor kann mindestens eine Drillthroughoption festlegen, durch die Sie auf eine andere Seite weitergeleitet werden. In diesem Fall können Sie entscheiden, für welche Option Sie einen Drillthrough durchführen möchten. Mit der Schaltfläche „Zurück“ gelangen Sie zurück zur vorherigen Seite.


Weitere Informationen finden Sie unter [Hinzufügen der Drillthroughfunktion in Power BI Desktop](../../create-reports/desktop-drillthrough.md).
   
   > [!IMPORTANT]
   > In mobilen Power BI-Apps werden Drillaktionen in Matrizen und Tabellenvisuals nur über Zellenwerte erlaubt, und nicht über Spalten oder Zeilenheader.
   
   
   
### <a name="using-the-actions-in-the-report-footer"></a>Verwenden der Aktionen in der Fußzeile des Berichts
Über die Fußzeile des Berichts können Sie verschiedene Aktionen für die aktuelle Berichtsseite oder dem gesamten Bericht ausführen. Die Fußzeile bietet schnellen Zugriff auf die am häufigsten verwendeten Aktionen. Sie können auf andere Aktionen zugreifen, indem Sie auf die Schaltfläche **Weitere Optionen** (...) tippen:

![Berichtsfußzeile](./media/mobile-reports-in-the-mobile-apps/report-footer.png)

Sie können die folgenden Aktionen über die Fußzeile ausführen:
* Zurücksetzen des Berichtsfilters und der übergreifenden Hervorhebungsauswahl in den ursprünglichen Zustand.
* Öffnen des Konversationsbereichs, um Kommentare anzuzeigen oder zum Bericht hinzuzufügen.
* Öffnen des Filterbereich, um den derzeit auf den Bericht angewendeten Filter anzuzeigen oder zu ändern.
* Auflisten aller Seiten des Berichts. Wenn Sie auf einen Seitennamen tippen, wird diese Seite geladen und angezeigt.
Sie können zwischen Berichtsseiten wechseln, indem Sie vom Rand des Bildschirms in die Mitte wischen.
* Anzeigen aller Berichtsaktionen.

#### <a name="all-report-actions"></a>Alle Berichtsaktionen
Wenn Sie im Bericht auf die Schaltfläche **Weitere Optionen** (...) tippen, werden alle Aktionen angezeigt, die Sie für einen Bericht ausführen können:


![Alle Berichtsaktionen](./media/mobile-reports-in-the-mobile-apps/power-bi-mobile-report-all-actions.png)

Einige der Aktionen können deaktiviert sein, da sie von den spezifischen Berichtsfunktionen abhängig sind.
Beispiel:

**Lesezeichen** wird nur angezeigt, wenn die Aktion [Lesezeichen](mobile-reports-in-the-mobile-apps.md#bookmarks) im Bericht festgelegt wurde. Sowohl persönlichen Lesezeichen, die Sie im Power BI-Dienst definieren können, als auch Lesezeichen, die vom Berichtersteller definiert wurden, werden angezeigt. Wenn eines der Lesezeichen als Standardlesezeichen definiert wurde, wird der Bericht beim Laden für diese Ansicht geöffnet.

**Anmerkung und Freigabe** kann deaktiviert sein, wenn in Ihrer Organisation eine [Intune-Schutzrichtlinie](https://docs.microsoft.com/intune/app-protection-policies) vorhanden ist, die die Freigabe über mobile Power BI-Apps untersagt.

**Einladen** ist nur aktiviert, wenn Sie über die Berechtigung verfügen, den Bericht für andere Benutzer freizugeben. Sie verfügen nur über Berechtigung, wenn Sie der Besitzer des Berichts sind oder der Besitzer Ihnen die Berechtigung zum Freigeben gewährt hat.

**Filter by current location** (Nach aktuellem Standort filtern) ist aktiviert, wenn der Berichtsautor den Bericht mit geografischen Daten kategorisiert hat. Weitere Informationen finden Sie unter [Identifizieren von geografischen Daten in einem Bericht](https://docs.microsoft.com/power-bi/desktop-mobile-geofiltering).

**Scan to filter the report by barcode** (Barcode zum Filtern des Berichts scannen) wird nur aktiviert, wenn das Dataset in Ihrem Bericht als **Barcode** markiert ist. Weitere Informationen finden Sie unter [Markieren von Barcodes in Power BI Desktop](https://docs.microsoft.com/power-bi/desktop-mobile-barcodes).

### <a name="bookmarks"></a>Lesezeichen

Die mobile Power BI-App unterstützt sowohl vom Berichtersteller definierte Berichtlesezeichen, als auch persönliche Lesezeichen, die Sie im Power BI-Dienst definieren können. Sie finden das Lesezeichenmenü unter **Weitere Optionen** (...) auf der [Symbolleiste „Berichtsaktionen“](mobile-reports-in-the-mobile-apps.md#all-report-actions).

Standardlesezeichen sind durch ein spezielles Symbol gekennzeichnet. Für persönliche Lesezeichen können Sie die Standardeinstellung festlegen, zurücksetzen oder ändern, indem Sie neben dem Lesezeichen, das Sie ändern möchten, auf **Weitere Optionen (...)** tippen und **Als Standard festlegen** oder **Standardwert löschen** auswählen.

![Lesezeichenmenü](./media/mobile-reports-in-the-mobile-apps/power-bi-mobile-report-bookmark-menu.png)

Wenn eine Lesezeichenansicht eines Berichts geöffnet ist, wird der Name des Lesezeichens am oberen Rand des Berichts angezeigt.

![Lesezeichenansicht](./media/mobile-reports-in-the-mobile-apps/power-bi-mobile-report-bookmark-title.png)

[Erfahren Sie mehr über Lesezeichen im Power BI-Dienst](https://docs.microsoft.com/power-bi/consumer/end-user-bookmarks).

## <a name="configure-your-experience-with-reports"></a>Konfigurieren von Berichten
Die mobile Power BI-App verfügt über eine Reihe von Einstellungen, mit denen Sie Ihren Bericht anpassen können. Derzeit ist Folgendes konfigurierbar:
* **Interaktionen mit Visuals in Berichten:** Sie können entweder die Interaktion durch einfaches Tippen oder Doppeltippen verwenden.
* **Methode für die Datenaktualisierung:** Sie können entscheiden, ob Berichtsdaten entweder über eine Schaltfläche oder eine Pulldownaktion aktualisiert werden.
* **Sichtbarkeit von Berichtsfußzeilen:** Fußzeilen können entweder angedockt und immer sichtbar oder dynamisch sein. Dynamische Fußzeilen werden basierend auf Ihren Aktionen ausgeblendet und wieder angezeigt, z. B. beim Scrollen.

Weitere Informationen zum Ändern dieser Einstellungen finden Sie unter [Konfigurieren der Einstellungen für Berichtsinteraktionen](./mobile-app-interaction-settings.md).


## <a name="next-steps"></a>Nächste Schritte
* [Anzeigen von und Interagieren mit Power BI-Berichten, die für das Smartphone optimiert sind](mobile-apps-view-phone-report.md)
* [Erstellen einer für Smartphones optimierten Version eines Berichts](../../create-reports/desktop-create-phone-report.md)
* Haben Sie Fragen? [Stellen Sie Ihre Frage in der Power BI-Community.](https://community.powerbi.com/)
