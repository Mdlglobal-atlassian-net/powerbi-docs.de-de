---
title: Verwenden von What-if-Parametern zum Visualisieren von Variablen
description: Hier erfahren Sie, wie Sie Ihre eigene What-if-Variable erstellen, um Variablen in Power BI-Berichten zu visualisieren.
author: davidiseminger
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 01/21/2020
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: 8a72bc43bcceae6e676728934ceec81c8cb27d04
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "76539399"
---
# <a name="create-and-use-what-if-parameters-to-visualize-variables-in-power-bi-desktop"></a>Erstellen und Verwenden von Was-wäre-wenn-Parametern zum Visualisieren von Variablen in Power BI Desktop

Ab dem *Power BI Desktop*-Release von August 2018 können Sie *What-if*-Variablen für Ihre Berichte erstellen, mit Variablen als Slicer interagieren und unterschiedliche wichtige Werte in den Berichten visualisieren und quantifizieren.

![Die Option „Neuer Parameter“](media/desktop-what-if/what-if_01.png)

Erstellen Sie einen *What-if*-Parameter in der Registerkarte **Modellierung** in Power BI Desktop. Wenn Sie diese Option auswählen, wird ein Dialogfeld angezeigt, in dem Sie den Parameter konfigurieren können.

## <a name="creating-a-what-if-parameter"></a>Erstellen eines What-if-Parameters

Wählen Sie zum Erstellen eines What-if-Parameters **Neuer Parameter** aus der Registerkarte **Modellierung** in Power BI Desktop aus. In der folgenden Abbildung wurde ein Parameter mit dem Namen *Discount percentage* (Rabattprozentsatz) erstellt und der dazugehörige Datentyp auf **Dezimalzahl** festgelegt. Der **Mindestwert** ist Null. Der **Maximalwert** ist 0,50 (50 Prozent). Außerdem wurde **Inkrement** auf 0,05 bzw. fünf Prozent festgelegt. Um diesen Betrag wird der Parameter angepasst, wenn in einem Bericht eine Interaktion mit ihm erfolgt.

![Werte für What-if-Parameter](media/desktop-what-if/what-if_02.png)

> [!NOTE]
> Stellen Sie bei Dezimalzahlen sicher, dass Sie dem Wert eine Null (0) voranstellen, also 0,50 und nicht ,50. Andernfalls wird die Zahl nicht ausgewertet, und die Schaltfläche **OK** kann nicht ausgewählt werden.
> 
> 

Durch Aktivieren des Kontrollkästchens **Slicer zu dieser Seite hinzufügen** wird mit dem What-if-Parameter automatisch ein Slicer auf der aktuellen Berichtsseite hinzugefügt.

![Neue Slicer auf der aktuellen Berichtsseite](media/desktop-what-if/what-if_03.png)

Durch das Erstellen eines What-if-Parameters wird auch ein Measure erstellt, mit dem Sie den aktuellen Wert des What-if-Parameters visualisieren können.

![Ein für What-if-Parameter erstelltes Measure](media/desktop-what-if/what-if_04.png)

Beachten Sie auf jeden Fall, dass nach dem Erstellen eines What-if-Parameters sowohl der Parameter als auch das Measure Teil des Modells werden. Sie sind somit im gesamten Bericht verfügbar und können auf anderen Berichtsseiten verwendet werden. Da diese auch Teil des Modells sind, können Sie den Slicer von der Berichtsseite löschen. Wenn Sie diesen zurückhaben möchten, nehmen Sie einfach den What-if-Parameter aus der Liste **Felder**, ziehen Sie diesen in den Zeichenbereich, und ändern Sie dann das Visual in einen Slicer.

## <a name="using-a-what-if-parameter"></a>Verwenden eines What-if-Parameters

Nun wird ein einfaches Beispiel für die Verwendung eines What-if-Parameters erstellt. Im vorherigen Abschnitt wurde der What-if-Parameter bereits erstellt. Jetzt wird dieser verwendet, indem ein neues Measure erstellt wird, dessen Wert sich mit dem Schieberegler anpasst.

![Hinzufügen eines neuen Measures mit dem Parameter](media/desktop-what-if/what-if_05.png)

Das neue Measure ist einfach der Gesamtumsatz, auf den der Rabatt angewendet wird. Sie können komplexe und interessante Measures erstellen, mit denen die Benutzer Ihrer Berichte die Variable des What-if-Parameters visualisieren können. Sie können z.B. einen Bericht erstellen, mit dem Vertriebsmitarbeiter die Vergütung, die sie beim Erreichen bestimmter Umsatzziele oder -prozentwerte erhalten, oder die Erhöhung von Rabatten aufgrund höherer Umsätze anzeigen können.

Geben Sie die Measureformel in die Bearbeitungsleiste ein, und benennen Sie die Formel mit *Sales after Discount* (Auftragsrabatt).

![Definition von Sales after Discount (Auftragsrabatt)](media/desktop-what-if/what-if_06.png)

Anschließend erstellen wir ein Säulendiagramm-Visual mit **OrderDate** auf der Achse und mit **SalesAmount** und dem gerade erstellten Measure **Sales after Discount** (Auftragsrabatt) als Werte.

![Visualisierung für SalesAmount](media/desktop-what-if/what-if_07.png)

Wenn wir dann den Schieberegler bewegen, stellen wir fest, dass die Spalte **Sales after Discount** (Auftragsrabatt) den ermäßigten Umsatzbetrag wiedergibt.

![Interagieren des Schiebereglers mit der Visualisierung](media/desktop-what-if/what-if_08.png)

Das war schon alles. Sie können What-if-Parameter in allen möglichen Situationen verwenden. Diese Parameter ermöglichen den Benutzern von Berichten die Interaktion mit verschiedenen Szenarios, die Sie in Ihren Berichten erstellen.
