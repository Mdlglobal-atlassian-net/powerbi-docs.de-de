---
title: Verwenden von Schaltflächen in Power BI
description: Sie können in Power BI-Berichten Schaltflächen hinzufügen, sodass das Verhalten Ihrer Berichte Apps ähnelt und sie von Benutzern noch einfacher verwendet werden können.
author: maggiesMSFT
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 03/12/2020
ms.author: maggies
LocalizationGroup: Create reports
ms.openlocfilehash: c703a4b67b642af5199413e80ff1e140905a2338
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "81439823"
---
# <a name="use-buttons-in-power-bi"></a>Verwenden von Schaltflächen in Power BI
Durch das Verwenden von **Schaltflächen** in Power BI können Sie Berichte erstellen, die sich ähnlich wie Apps verhalten, und dadurch eine interaktive Umgebung erstellen, sodass die Benutzer auf Power BI-Elemente zeigen, klicken oder auf andere Weise mit diesen interagieren können. Sie können in Berichten in **Power BI Desktop** und im **Power BI-Dienst** Schaltflächen hinzufügen. Wenn Sie Ihre Berichte im Power BI-Dienst freigeben, können Benutzer sie ähnlich wie Apps verwenden.

![Schaltflächen in Power BI](media/desktop-buttons/power-bi-buttons.png)

## <a name="create-buttons-in-reports"></a>Erstellen von Schaltflächen in Berichten

### <a name="create-a-button-in-power-bi-desktop"></a>Erstellen einer Schaltfläche in Power BI Desktop

Klicken Sie für das Erstellen einer Schaltfläche in **Power BI Desktop** auf das Menüband **Einfügen** und dann auf **Schaltflächen**. Dadurch wird ein Dropdownmenü angezeigt, aus dem Sie aus mehreren Optionen wie in der folgenden Abbildung dargestellt eine Schaltfläche auswählen können. 

![Hinzufügen einer Schaltfläche in Power BI Desktop](media/desktop-buttons/power-bi-button-dropdown.png)

### <a name="create-a-button-in-the-power-bi-service"></a>Erstellen einer Schaltfläche im Power BI-Dienst

Öffnen Sie einen Bericht in der Bearbeitungsansicht, um im **Power BI-Dienst** eine Schaltfläche zu erstellen. Klicken Sie oben in der Menüleiste auf **Schaltflächen**. Daraufhin wird ein Dropdownmenü angezeigt, aus dem Sie aus einer Sammlung von Optionen wie im folgenden Bild gezeigt eine Schaltfläche auswählen können. 

![Hinzufügen eines Schaltflächensteuerelements im Power BI-Dienst](media/desktop-buttons/power-bi-button-service-dropdown.png)

## <a name="customize-a-button"></a>Anpassen einer Schaltfläche

Unabhängig davon, ob Sie die Schaltfläche in Power BI Desktop oder im Power BI-Dienst erstellen, unterscheidet sich der restliche Prozess nicht. Wenn Sie die Schaltfläche im Zeichenbereich des Berichts auswählen, zeigt der Bereich **Visualisierungen** Ihnen die Anpassungsmöglichkeiten der Schaltfläche an, um diese an Ihre Anforderungen anzupassen. Sie können beispielsweise den **Schaltflächentext** aktivieren oder deaktivieren, indem Sie den Schieberegler auf dieser Karte des Bereichs **Visualisierungen** bewegen. Sie können unter anderem das Symbol, die Füllung und den Titel der Schaltfläche ändern sowie die Aktion, die durchgeführt wird, wenn der Benutzer in einem Bericht auf die Schaltfläche klickt.

![Formatieren einer Schaltfläche in einem Power BI-Bericht](media/desktop-buttons/power-bi-button-properties.png)

## <a name="set-button-properties-when-idle-hovered-over-or-selected"></a>Festlegen der Schaltflächeneigenschaften im Normalzustand, wenn darauf gezeigt wird oder wenn sie ausgewählt werden

Schaltflächen in Power BI können drei Zustände aufweisen: der Normalzustand (wenn nicht auf diese gezeigt wird und sie nicht ausgewählt sind), wenn darauf gezeigt oder wenn sie ausgewählt wird (häufig als *angeklickt* bezeichnet). Viele der Karten im Bereich **Visualisierungen** können auf Grundlage dieser drei Zustände geändert werden. Dadurch können Sie Ihre Schaltflächen flexibel anpassen.

Mithilfe folgender Karten im Bereich **Visualisierungen** können Sie die Formatierung oder das Verhalten einer Schaltfläche auf Grundlage der drei Zustände anpassen:

* Schaltflächentext
* Symbol
* Gliederung
* Füllung

Erweitern Sie eine dieser Karten, und klicken Sie auf das Dropdownmenü, das im oberen Bereich der Karte angezeigt wird, um auszuwählen, wie die Schaltfläche für jeden Zustand angezeigt werden soll. Auf der folgenden Abbildung wird veranschaulicht, wie die erweiterte Karte **Symbol** aussieht. Dabei zeigt das ausgewählte Dropdownmenü die drei Zustände an.

![Drei Zustände einer Schaltfläche in einem Power BI-Bericht](media/desktop-buttons/power-bi-button-format.png)


## <a name="select-the-action-for-a-button"></a>Auswählen der Aktion für eine Schaltfläche

Sie können auswählen, welche Aktion durchgeführt wird, wenn ein Benutzer auf eine Schaltfläche in Power BI klickt. Sie können über die Karte **Aktion** im Bereich **Visualisierungen** auf die Optionen für Schaltflächenaktionen zugreifen.

![Aktionen für eine Schaltfläche in Power BI](media/desktop-buttons/power-bi-button-action.png)

Folgende Optionen sind für Schaltflächenaktionen verfügbar:

- Wenn der Benutzer auf **Zurück** klickt, wird zur vorherigen Seite des Berichts zurückgekehrt. Dies ist hilfreich für Drillthroughseiten.
- Wenn der Benutzer auf **Lesezeichen** klickt, wird die Berichtsseite angezeigt, die einem für den aktuellen Bericht definierten Lesezeichen zugeordnet ist. Weitere Informationen finden Sie unter [Erstellen von Lesezeichen zum Teilen von Erkenntnissen und Erstellen von Präsentationen in Power BI Desktop](desktop-bookmarks.md). 
- **Drillthrough (Vorschau)** navigiert den Benutzer zu einer Drillthroughseite, die entsprechend einer vorgenommenen Auswahl gefiltert ist, ohne dass Lesezeichen verwendet werden. Weitere Informationen finden Sie unter [Erstellen einer Drillthroughschaltfläche in Power BI (Vorschau)](desktop-drill-through-buttons.md).
- Die **Seitennavigation** navigiert den Benutzer auf eine andere Seite im Bericht, ebenfalls ohne dass dafür Lesezeichen verwendet werden. Im Abschnitt [Erstellen einer Seitennavigation](#create-page-navigation) dieses Artikels finden Sie weitere Informationen.
- **Q&A** öffnet ein Fenster mit dem **Q&A-Explorer**. 

Für bestimmte Schaltflächen gibt es eine Standardaktion, die automatisch ausgewählt wird. Der Schaltflächentyp **Q&A** wählt beispielsweise automatisch **Q&A** als Standardaktion aus. Weitere Informationen zum **Q&A-Explorer** finden Sie in [diesem Blogbeitrag](https://powerbi.microsoft.com/blog/power-bi-desktop-april-2018-feature-summary/#Q&AExplorer).

Sie können die Schaltflächen testen, die Sie für Ihren Bericht erstellen, indem Sie *STRG+Klick* auf die Schaltfläche anwenden, die Sie verwenden möchten. 

### <a name="create-page-navigation"></a>Erstellen einer Seitennavigation

Mit dem **Aktionstyp** **Seitennavigation** können Sie schnell eine komplette Navigation erstellen, ohne dass Sie dafür Lesezeichen speichern oder verwalten müssen.

Erstellen Sie eine Schaltfläche mit dem Aktionstyp **Seitennavigation**, und wählen Sie die **Zielseite** aus, um eine Seitennavigationsschaltfläche einzurichten.

![Aktion „Seitennavigation“](media/desktop-buttons/power-bi-page-navigation.png)

Sie können schnell einen benutzerdefinierten Navigationsbereich erstellen. Sie müssen somit keine Lesezeichen bearbeiten und verwalten, wenn Sie ändern möchten, welche Seiten in Ihrem Navigationsbereich angezeigt werden sollen.

![Erstellen einer Navigationsseite](media/desktop-buttons/power-bi-build-navigation-pane.png)

Außerdem können Sie die QuickInfo bedingt formatieren. Dies ist auch für andere Schaltflächenarten möglich.

## <a name="next-steps"></a>Weitere Schritte
Weitere Informationen zu Features, die Schaltflächen ähneln oder mit diesen interagieren, finden Sie in den folgenden Artikeln:

* [Verwenden der Drillthroughfunktion in Power BI Desktop](desktop-drillthrough.md)
* [Verwenden von Lesezeichen zum Teilen von Erkenntnissen und zum Erstellen von Präsentationen in Power BI](desktop-bookmarks.md)

