---
title: Was ist Power BI Desktop?
description: Hier erhalten Sie Informationen zu Power BI Desktop und seiner Verwendung.
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: overview
ms.date: 12/16/2019
ms.author: davidi
LocalizationGroup: Get started
ms.openlocfilehash: bd95dfcc5d621b5ae4988e187d7cc6d9478feb58
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "75731127"
---
# <a name="what-is-power-bi-desktop"></a>Was ist Power BI Desktop?

*Power BI Desktop* ist eine kostenlose Anwendung, die Sie auf Ihrem lokalen Computer installieren und die es Ihnen ermöglicht, eine Verbindung mit Ihren Daten herzustellen und diese zu transformieren und zu visualisieren. Mit Power BI Desktop können Sie eine Verbindung mit vielen unterschiedlichen Datenquellen herstellen und diese in einem Datenmodell kombinieren. Dieser Vorgang wird oft als *Modellierung* bezeichnet. Mit dem Datenmodell können Sie Visuals und Sammlungen von Visuals erstellen, die Sie in Form von Berichten für andere Personen innerhalb Ihrer Organisation freigeben können. Die meisten Benutzer, die an Business Intelligence-Projekten arbeiten, verwenden Power BI Desktop zum Erstellen von Berichten und nutzen dann den *Power BI-Dienst*, um ihre Berichte für andere Personen freizugeben.

![Power BI Desktop](media/desktop-what-is-desktop/what-is-desktop_01.png)

Die häufigsten Verwendungsmöglichkeiten für Power BI Desktop sind folgende:

* Verbinden mit Daten
* Transformieren und Bereinigen von Daten zum Erstellen eines Datenmodells
* Erstellen von Visuals wie Diagrammen oder Graphen, die visuelle Darstellungen der Daten bieten
* Erstellen von Berichten, bei denen es sich um Sammlungen von Visuals handelt, auf einer oder mehreren Berichtsseiten
* Freigeben von Berichten für andere Personen über den Power BI-Dienst

Personen, die für solche Aufgaben zuständig sind, werden häufig als *Datenanalysten* (oder einfach *Analysten*) oder als Business Intelligence-Experten (oder *Berichtersteller*) bezeichnet. Allerdings arbeiten auch viele Menschen, die sich selbst nicht als Analyst oder Berichtersteller bezeichnen würden, mit Power BI Desktop, um interessante Berichte zu erstellen, Daten aus verschiedenen Quellen abzurufen und Datenmodelle zu erstellen, die sie für Kollegen und Organisationen freigeben können.

In Power BI Desktop sind drei Ansichten verfügbar, die Sie auf der linken Seite der Canvas auswählen können. Die folgenden Ansichten (die in dieser Reihenfolge angezeigt werden) sind verfügbar:
* **Report** (Bericht): Hier erstellen Sie Berichte und Visuals und werden den größten Teil Ihrer Erstellungszeit verbringen.
* **Daten**: Hier werden Tabellen, Measures und andere Daten angezeigt, die in dem mit Ihrem Bericht verknüpften Datenmodell verwendet werden. Zudem werden hier die Daten für eine optimale Nutzung im Berichtsmodell transformiert.
* **Modell**: Hier können Sie die Beziehungen zwischen den Tabellen in Ihrem Datenmodell anzeigen und verwalten.

Die folgende Abbildung zeigt die drei Ansichten, die links neben der Canvas angezeigt werden:

![Sichten in Power BI Desktop](media/desktop-what-is-desktop/what-is-desktop-07.png)
 

## <a name="connect-to-data"></a>Verbinden mit Daten
Der erste Schritt bei der Verwendung von Power BI Desktop besteht darin, eine Verbindung mit Daten herzustellen. Mit Power BI Desktop können Sie eine Verbindung mit vielen verschiedenen Datenquellen herstellen. 

Gehen Sie folgendermaßen vor, um eine Verbindung mit Daten herzustellen:

1. Klicken Sie im Menüband **Start** auf **Daten abrufen** > **Mehr**. 

   Das Fenster **Daten abrufen** wird geöffnet, in dem die Kategorien angezeigt werden, mit denen Power BI Desktop eine Verbindung herstellen kann.

   ![Abrufen von Daten in Power BI Desktop](media/desktop-what-is-desktop/what-is-desktop_02.png)

2. Wenn Sie einen Datentyp auswählen, werden Sie aufgefordert, Informationen einzugeben, wie z.B. URL und Anmeldeinformationen, die erforderlich sind, damit Power BI Desktop in Ihrem Namen eine Verbindung mit der Datenquelle herstellen kann.

   ![Herstellen einer Verbindung mit einer SQL Server-Datenbank in Power BI Desktop](media/desktop-what-is-desktop/what-is-desktop_03.png)

3. Nachdem Sie eine Verbindung mit mindestens einer Datenquelle hergestellt haben, sollten Sie die Daten so transformieren, dass sie für Sie von Nutzen sind.

## <a name="transform-and-clean-data-create-a-model"></a>Transformieren und Bereinigen von Daten und Erstellen eines Modells

In Power BI Desktop können Sie Daten mit dem integrierten [Power Query-Editor](https://docs.microsoft.com/power-bi/desktop-query-overview) bereinigen und transformieren. Mit dem Power Query-Editor können Sie Änderungen an Ihren Daten vornehmen, wie beispielsweise den Datentyp ändern, Spalten entfernen oder Daten aus mehreren Quellen kombinieren. Sie können sich den Vorgang wie das Herstellen einer Tonskulptur vorstellen: Sie beginnen mit einem großen Block Ton (bzw. Daten), nehmen an einigen Stellen Material weg und fügen an anderen Stellen welches hinzu, bis die Form (bzw. Struktur der Daten) Ihren Wünschen entspricht. 

Gehen Sie folgendermaßen vor, um den Power Query-Editor zu starten:

- Klicken Sie im Menüband **Start** auf **Abfragen bearbeiten** > **Abfragen bearbeiten**.

   Das Fenster des **Power Query-Editors** wird geöffnet.

   ![Power Query-Editor in Power BI Desktop](media/desktop-getting-started/designer_gsg_editquery.png)

Jeder Transformationsschritt an den Daten (wie das Umbenennen einer Tabelle, das Transformieren eines Datentyps oder das Löschen einer Spalte) wird im Power Query-Editor erfasst. Bei jeder Verbindung dieser Abfrage mit der Datenquelle werden diese Schritte ausgeführt, damit die Daten stets Ihren Angaben entsprechend strukturiert werden.

Die folgende Abbildung zeigt das Fenster des **Power Query-Editors** für eine Abfrage, die strukturiert und in ein Modell umgewandelt wurde.

 ![Fenster des Power Query-Editors](media/desktop-getting-started/shapecombine_querysettingsfinished.png)

Sobald Ihre Daten in der von Ihnen gewünschten Form vorliegen, können Sie Visuals erstellen. 

## <a name="create-visuals"></a>Erstellen von visuellen Elementen 

Sobald Sie über ein Datenmodell verfügen, können Sie *Felder* auf die Berichtscanvas ziehen, um *Visuals* zu erstellen. Ein Visual ist die grafische Darstellung der Daten in Ihrem Modell. In Power BI Desktop stehen viele verschiedene Arten von Visuals zur Auswahl bereit. Das folgende Visual zeigt ein einfaches Säulendiagramm. 

![Ein Visual in Power BI Desktop](media/desktop-what-is-desktop/what-is-desktop_04.png)

Gehen Sie folgendermaßen vor, um ein Visual zu erstellen oder zu ändern: 

- Klicken Sie im Bereich **Visualisierungen** auf das Visualsymbol. 

   ![Bereich „Visualisierungen“ in Power BI Desktop](media/desktop-what-is-desktop/what-is-desktop_05.png)

   Wenn Sie in der Berichtscanvas bereits ein Visual ausgewählt haben, wird dieses in den von Ihnen ausgewählten Typ geändert. 

   Ist in der Canvas kein Visual ausgewählt, wird entsprechend Ihrer Auswahl ein neues Visual erstellt.


## <a name="create-reports"></a>Erstellen von Berichten

Häufig soll auch eine Sammlung von Visuals erstellt werden, die verschiedene Aspekte der Daten zeigt, mit denen das Modell in Power BI Desktop erstellt wurde. Eine Sammlung von Visuals in einer einzigen Power BI Desktop-Datei wird als *Bericht* bezeichnet. Ein Bericht kann eine oder mehrere Seiten umfassen, ebenso wie eine Excel-Datei aus einem oder mehreren Arbeitsblättern bestehen kann. 

Mit Power BI Desktop können Sie komplexe, visuell aufbereitete Berichte erstellen und dabei Daten aus mehreren Quellen in einem Bericht zusammenfügen, den Sie dann für andere Personen in Ihrer Organisation freigeben.

Die folgende Abbildung zeigt die erste Seite eines Power BI Desktop-Berichts mit der Bezeichnung **Overview (Übersicht)** , die auf der Registerkarte im unteren Bereich des Bilds angezeigt wird. 

![Beispiel eines Power BI Desktop-Berichts](media/desktop-what-is-desktop/what-is-desktop_01.png)

## <a name="share-reports"></a>Freigeben von Berichten

Sobald ein Bericht für andere Personen freigegeben werden kann, können Sie den Bericht im Power BI-Dienst *veröffentlichen* und so allen Benutzern mit einer Power BI-Lizenz in Ihrer Organisation zur Verfügung stellen. 

Gehen Sie folgendermaßen vor, um einen Power BI Desktop-Bericht zu veröffentlichen: 

1. Klicken Sie im Menüband **Start** auf die Option **Veröffentlichen**.

   ![Veröffentlichen eines Berichts aus Power BI Desktop](media/desktop-what-is-desktop/what-is-desktop_06.png)

   Power BI Desktop stellt über Ihr Power BI-Konto eine Verbindung mit dem Power BI-Dienst her. 

2. Sie werden von Power BI dazu aufgefordert, den Ort innerhalb des Power BI-Diensts auszuwählen, an dem der Bericht freigegeben werden soll, wie etwa Ihr Arbeitsbereich, ein Teamarbeitsbereich oder ein anderer Bereich im Power BI-Dienst. 

   Sie müssen über eine Power BI-Lizenz verfügen, um Berichte im Power BI-Dienst freizugeben.


## <a name="next-steps"></a>Nächste Schritte

Laden Sie zunächst die Anwendung herunter, und installieren Sie diese, um mit Power BI Desktop zu beginnen. Es gibt zwei Möglichkeiten, Power BI Desktop abzurufen:

* [Abrufen von Power BI Desktop aus dem Windows Store](https://aka.ms/pbidesktopstore)
* [Herunterladen von Power BI Desktop aus dem Web](https://docs.microsoft.com/power-bi/desktop-get-the-desktop#download-power-bi-desktop-directly)

