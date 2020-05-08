---
title: 'Tutorial: Erstellen eines Machine Learning-Modells in Power BI'
description: In diesem Tutorial erstellen Sie ein Machine Learning-Modell in Power BI.
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.custom: connect-to-services
ms.topic: tutorial
ms.date: 03/29/2019
ms.author: davidi
LocalizationGroup: Connect to services
ms.openlocfilehash: 78b29a4e71e75793e168da25987b3e9c4a8b13f4
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "73877022"
---
# <a name="tutorial-build-a-machine-learning-model-in-power-bi"></a>Tutorial: Erstellen eines Machine Learning-Modells in Power BI

In diesem Tutorialartikel verwenden Sie **Automatisiertes maschinelles Lernen** zum Erstellen und Anwenden eines binären Vorhersagemodells in Power BI. Das Tutorial enthält Anleitungen zum Erstellen eines Power BI-Dataflows und zum Verwenden der im Dataflow definierten Entitäten, um ein Machine Learning-Modell direkt in Power BI zu trainieren und zu überprüfen. Wir verwenden dieses Modell dann zur Bewertung neuer Daten, um Vorhersagen zu generieren.

Zunächst erstellen Sie ein Machine Learning-Modell für die binäre Vorhersage der Kaufabsichten von Onlinekunden auf Basis eines Satzes ihrer Onlinesitzungsattribute. Für diese Übung wird ein Benchmark-Machine Learning-Dataset verwendet. Sobald ein Modell trainiert ist, generiert Power BI automatisch einen Überprüfungsbericht, in dem die Modellergebnisse erläutert werden. Sie können dann den Überprüfungsbericht auswerten und das Modell zur Bewertung auf die Daten anwenden.

Dieses Tutorial umfasst folgende Schritte:
> [!div class="checklist"]

> * Erstellen eines Dataflows mit den Eingabedaten
> * Erstellen und Trainieren eines Machine Learning-Modells
> * Auswerten des Modellüberprüfungsberichts
> * Anwenden des Modells auf eine Dataflowentität
> * Verwenden der bewerteten Ausgabe des Modells in einem Power BI-Bericht

## <a name="create-a-dataflow-with-the-input-data"></a>Erstellen eines Dataflows mit den Eingabedaten

Der erste Teil dieses Tutorials besteht darin, einen Dataflow mit Eingabedaten zu erstellen. Dieser Vorgang erfordert einige Schritte, wie in den folgenden Abschnitten beschrieben, beginnend mit dem Erfassen der Daten.

### <a name="get-data"></a>Daten abrufen

Der erste Schritt beim Erstellen eines Dataflows besteht darin, dass Sie Ihre Datenquellen bereithalten. In unserem Fall verwenden wir ein Machine Learning-Dataset aus einer Reihe von Onlinesitzungen, wobei es in einigen davon zum Kauf kam. Das Dataset enthält eine Reihe von Attributen zu diesen Sitzungen, die wir zum Trainieren unseres Modells verwenden.

Sie können das Dataset von der UC Irvine-Website herunterladen. Auch dies steht für den Zweck dieses Tutorials über den folgenden Link zur Verfügung: [online_shoppers_intention.csv](https://raw.githubusercontent.com/santoshc1/PowerBI-AI-samples/master/Tutorial_AutomatedML/online_shoppers_intention.csv).

### <a name="create-the-entities"></a>Erstellen der Entitäten

Melden Sie sich beim Power BI-Dienst an, und navigieren Sie zu einem Arbeitsbereich Ihrer dedizierten Kapazität, in dem KI aktiviert ist, um die Entitäten in Ihrem Dataflow zu erstellen.

Wenn Sie noch keinen Arbeitsbereich haben, können Sie einen erstellen, indem Sie im Power BI-Dienst im Navigationsbereichsmenü **Arbeitsbereiche** und im dann angezeigten Bereich am unteren Rand **Arbeitsbereich erstellen** auswählen. Daraufhin wird rechts ein Bereich zur Eingabe der Details des Arbeitsbereichs geöffnet. Geben Sie einen Namen für den Arbeitsbereich ein, und wählen Sie **Erweitert** aus. Bestätigen Sie mithilfe des Optionsfelds „Dedizierte Kapazität“, dass der Arbeitsbereich dedizierte Kapazität verwendet und einer Instanz mit dedizierter Kapazität zugewiesen ist, für die die KI-Vorschau aktiviert ist. Klicken Sie auf **Speichern**.

![Arbeitsbereich erstellen](media/service-tutorial-build-machine-learning-model/tutorial-machine-learning-model-01.png)

Sobald der Arbeitsbereich erstellt ist, können Sie unten rechts im Begrüßungsbildschirm **Überspringen** auswählen, wie in der folgenden Abbildung gezeigt.

![Überspringen, wenn Sie über einen Arbeitsbereich verfügen](media/service-tutorial-build-machine-learning-model/tutorial-machine-learning-model-02.png)

 Wählen Sie die Schaltfläche **Erstellen** oben rechts im Arbeitsbereich und dann die Schaltfläche **Dataflow** aus.

![Erstellen des Dataflows](media/service-tutorial-build-machine-learning-model/tutorial-machine-learning-model-03.png)

Wählen Sie **Neue Entitäten hinzufügen** aus. Damit wird ein **Power Query**-Editor im Browser gestartet.

![Hinzufügen einer neuen Entität](media/service-tutorial-build-machine-learning-model/tutorial-machine-learning-model-04.png)

Wählen Sie **Text-/CSV-Datei** als Datenquelle aus, wie in der folgenden Abbildung dargestellt.

![Ausgewählte Text-/CSV-Datei](media/service-tutorial-build-machine-learning-model/tutorial-machine-learning-model-05.png)

Fügen Sie auf der Seite **Mit einer Datenquelle verbinden**, die als Nächstes angezeigt wird, den folgenden Link zur Datei _online_shoppers_intention.csv_ in das Feld **Dateipfad oder URL** ein, und wählen Sie dann **Weiter** aus.

`https://raw.githubusercontent.com/santoshc1/PowerBI-AI-samples/master/Tutorial_AutomatedML/online_shoppers_intention.csv`

![Dateipfad](media/service-tutorial-build-machine-learning-model/tutorial-machine-learning-model-06.png)

Der Power Query-Editor zeigt eine Vorschau der Daten aus der CSV-Datei an. Sie können die Abfrage in einen benutzerfreundlicheren Namen umbenennen, indem Sie den Wert im Feld „Name“ im rechten Bereich ändern. Beispielsweise könnten Sie den Abfragenamen in _Onlinebesucher_ ändern.

![Ändern in einen benutzerfreundlichen Namen](media/service-tutorial-build-machine-learning-model/tutorial-machine-learning-model-07.png)

Power Query leitet automatisch den Spaltentyp ab. Sie können den Spaltentyp ändern, indem Sie auf das Symbol „Attributtyp“ am oberen Rand der Spaltenüberschrift klicken. In diesem Beispiel ändern wir den Typ der Spalte „Revenue“ (Umsatz) in „TRUE/FALSE“.

![Ändern des Datentyps](media/service-tutorial-build-machine-learning-model/tutorial-machine-learning-model-08.png)

Wählen Sie die Schaltfläche **Speichern und schließen** aus, um den Power Query-Editor zu schließen. Geben Sie einen Namen für den Dataflow an, und wählen Sie dann wie in der folgenden Abbildung veranschaulicht im Dialogfeld die Option **Speichern** aus.

![Speichern des Dataflows](media/service-tutorial-build-machine-learning-model/tutorial-machine-learning-model-09.png)

## <a name="create-and-train-a-machine-learning-model"></a>Erstellen und Trainieren eines Machine Learning-Modells

Wählen Sie zum Hinzufügen eines Machine Learning-Modells die Schaltfläche **ML-Modell anwenden** in der Liste **Aktionen** für die Basisentität aus, die die Trainingsdaten und Bezeichnungsinformationen enthält, und wählen Sie dann **Machine Learning-Modell hinzufügen** aus.

![Machine Learning-Modell hinzufügen](media/service-tutorial-build-machine-learning-model/tutorial-machine-learning-model-10.png)

Der erste Schritt beim Erstellen unseres Machine Learning-Modells besteht darin, die Verlaufsdaten zu identifizieren, einschließlich des Ergebnisfelds, das Sie vorhersagen möchten. Das Modell wird erstellt, indem es aus diesen Daten lernt.

Im Fall des Datasets, das wir verwenden, ist dies das Feld **Revenue**. Wählen Sie **Revenue** (Umsatz) als Wert für „Ergebnisfeld“ aus, und wählen Sie dann **Weiter** aus.

![Auswählen von Verlaufsdaten](media/service-tutorial-build-machine-learning-model/tutorial-machine-learning-model-11.png)

Als Nächstes müssen wir den Typ des zu erstellenden Machine Learning-Modells auswählen. Power BI analysiert die Werte im Ergebnisfeld, das Sie identifiziert haben, und schlägt die Machine Learning-Modelltypen vor, die erstellt werden können, um dieses Feld vorherzusagen.

Da wir in diesem Fall ein binäres Ergebnis vorhersagen, nämlich ob ein Benutzer einen Einkauf durchführt oder nicht, wird die binäre Vorhersage empfohlen. Da wir daran interessiert sind, Benutzer vorherzusagen, die einen Kauf tätigen werden, wählen Sie „TRUE“ als Umsatzergebnis aus, an dem Sie am meisten interessiert sind. Zusätzlich können Sie benutzerfreundliche Bezeichnungen für die Ergebnisse angeben, die im automatisch generierten Bericht verwendet werden, der die Ergebnisse der Modellüberprüfung zusammenfasst. Wählen Sie dann „Weiter“ aus.

![Ausgewählte binäre Vorhersage](media/service-tutorial-build-machine-learning-model/tutorial-machine-learning-model-12.png)

Als Nächstes führt Power BI eine vorläufige Überprüfung einer Stichprobe der Daten durch und schlägt die Eingaben vor, die genauere Vorhersagen liefern können. Wenn Power BI kein Feld empfiehlt, wird daneben eine Erklärung angezeigt. Sie haben die Möglichkeit, die Auswahl so zu ändern, dass nur die Felder einbezogen werden, die vom Modell untersucht werden sollen. Alternativ können Sie auch alle Felder auswählen, indem Sie das Kontrollkästchen neben dem Entitätsnamen aktivieren. Wählen Sie **Weiter** aus, um die Eingaben zu akzeptieren.

![Auswählen von „Weiter“](media/service-tutorial-build-machine-learning-model/tutorial-machine-learning-model-13.png)

Im letzten Schritt müssen wir unserem Modell einen Namen geben. Nennen Sie das Modell _Vorhersage der Kaufabsicht_. Sie können entscheiden, ob Sie die Trainingszeit verkürzen möchten, um schnelle Ergebnisse zu erzielen, oder ob Sie die Trainingszeit verlängern möchten, um das beste Modell zu erhalten. Wählen Sie dann **Speichern und trainieren** aus, um mit dem Training des Modells zu beginnen.

![Speichern des Modells](media/service-tutorial-build-machine-learning-model/tutorial-machine-learning-model-14.png)

Der Trainingsprozess beginnt mit der Stichprobenentnahme und Normalisierung ihrer Verlaufsdaten sowie dem Aufteilen Ihres Datasets in zwei neue Entitäten _Purchase Intent Prediction Training Data_ (Trainingsdaten für Kaufabsichtsvorhersage) und _Purchase Intent Prediction Testing Data_ (Testdaten für Kaufabsichtsvorhersage).

Abhängig von der Größe des Datasets kann der Trainingsprozess einige Minuten bis zu der im vorherigen Bildschirm ausgewählten Trainingszeit dauern. An diesem Punkt können Sie das Modell auf der Registerkarte **Machine Learning-Modelle** des Dataflows sehen. Der Status „Bereit“ zeigt an, dass das Modell in eine Warteschlange eingereiht wurde oder gerade trainiert wird.

Sie können über den Status des Dataflows feststellen, ob das Modell trainiert und überprüft wird. Dieser wird als laufende Datenaktualisierung auf der Registerkarte **Dataflows** des Arbeitsbereichs angezeigt.

![Bereit zum Training](media/service-tutorial-build-machine-learning-model/tutorial-machine-learning-model-15.png)

Sobald das Modelltraining abgeschlossen ist, wird für den Dataflow eine aktualisierte Aktualisierungszeit angezeigt. Sie können überprüfen, ob das Modell trainiert ist, indem Sie zur Registerkarte **Machine Learning-Modelle** im Dataflow navigieren. Für das von Ihnen erstellte Modell sollte der Status **Trainiert** angezeigt werden, und die Zeitangabe **Zuletzt trainiert** sollte jetzt aktualisiert sein.

![Zuletzt trainiert](media/service-tutorial-build-machine-learning-model/tutorial-machine-learning-model-16.png)

## <a name="review-the-model-validation-report"></a>Auswerten des Modellüberprüfungsberichts
Wählen Sie in der Registerkarte „Machine Learning-Modelle“ die Schaltfläche „Trainingsbericht anzeigen“ in der Spalte „Aktionen“ für das Modell aus, um den Modellüberprüfungsbericht auszuwerten. In diesem Bericht wird beschrieben, wie das Machine Learning-Modell wahrscheinlich durchgeführt wird.

Wählen Sie auf der Seite **Modellleistung** des Berichts **top predictors** (wichtigste Vorhersagen) aus, um die wichtigsten Vorhersagen für das Modell anzuzeigen. Sie können eine der Vorhersagen auswählen, um zu sehen, wie die Ergebnisverteilung mit dieser Vorhersage verknüpft ist.

![Modellleistung](media/service-tutorial-build-machine-learning-model/tutorial-machine-learning-model-17.png)

Sie können den **Wahrscheinlichkeitsschwellenwert**-Slicer auf der Seite „Modellleistung“ verwenden, um seine Auswirkung auf die Genauigkeit und den Abruf des Modells zu untersuchen.

![Wahrscheinlichkeitsschwellenwert](media/service-tutorial-build-machine-learning-model/tutorial-machine-learning-model-18.png)

Die anderen Seiten des Berichts beschreiben die statistischen Leistungsmetriken für das Modell.

Der Bericht enthält auch eine Seite mit Trainingsdetails, die die verschiedenen ausgeführten Iterationen beschreibt, wie Features aus den Eingaben extrahiert und welche Hyperparameter für das endgültige Modell verwendet wurden.

## <a name="apply-the-model-to-a-dataflow-entity"></a>Anwenden des Modells auf eine Dataflowentität

Wählen Sie oben im Bericht die Schaltfläche **Modell anwenden** aus, um dieses Modell aufzurufen. Im Dialogfeld **Anwenden** können Sie die Zielentität angeben, die die Quelldaten enthält, auf die das Modell angewendet werden soll.

![Modell anwenden](media/service-tutorial-build-machine-learning-model/tutorial-machine-learning-model-19.png)

Nach Aufforderung müssen Sie den Dataflow **Aktualisieren**, um eine Vorschau der Ergebnisse Ihres Modells anzuzeigen.

Die Anwendung des Modells erzeugt zwei neue Entitäten mit dem Suffix **erweiterter <Modellname>** und **Erklärungen zu erweitertem <Modellnamen>** . In diesem Fall wird durch das Anwenden des Modells auf die **Onlinebesucher**-Entität **Online Visitors enriched Purchase Intent Prediction** (erweiterte Vorhersage der Kaufabsicht von Onlinebesuchern) erstellt, die die vorhergesagte Ausgabe des Modells einschließt, und **Online Visitors enriched Purchase Intent Prediction explanations** (Erklärungen der erweiterten Vorhersagen der Kaufabsicht von Onlinebesuchern), die die wichtigsten datensatzspezifischen Einflussfaktoren für die Vorhersage enthalten. 

Wenn Sie ein binäres Vorhersagemodell anwenden, werden vier Spalten mit dem vorhergesagten Ergebnis, der Wahrscheinlichkeitsbewertung, den wichtigsten datensatzspezifischen Einflussfaktoren für die Vorhersage und dem Erklärungsindex hinzugefügt, wobei jeweils der angegebene Spaltenname vorangestellt wird.  

![Drei Ergebnisspalten](media/service-tutorial-build-machine-learning-model/tutorial-machine-learning-model-20.png)

Sobald die Dataflowaktualisierung abgeschlossen ist, können Sie die **Online Visitors enriched Purchase Intent Prediction**-Entität (erweiterte Vorhersage der Kaufabsicht von Onlinebesuchern) auswählen, um die Ergebnisse anzuzeigen.

![Anzeigen der Ergebnisse](media/service-tutorial-build-machine-learning-model/tutorial-machine-learning-model-21.png)

## <a name="using-the-scored-output-from-the-model-in-a-power-bi-report"></a>Verwenden der bewerteten Ausgabe des Modells in einem Power BI-Bericht

Wenn Sie die bewertete Ausgabe Ihres Machine Learning-Modells verwenden möchten, können Sie mit dem Dataflows-Connector eine Verbindung mit Ihrem Dataflow über den Power BI-Desktop herstellen. Mit der **Online Visitors enriched Purchase Intent Prediction**-Entität (erweiterte Vorhersage der Kaufabsicht von Onlinebesuchern) können Sie jetzt die Vorhersagen aus dem Modell in Power BI-Berichte einbinden.

## <a name="next-steps"></a>Nächste Schritte

In diesem Tutorial haben Sie mithilfe der folgenden Schritte ein binäres Vorhersagemodell in Power BI erstellt und angewendet:

* Erstellen eines Dataflows mit den Eingabedaten
* Erstellen und Trainieren eines Machine Learning-Modells
* Auswerten des Modellüberprüfungsberichts
* Anwenden des Modells auf eine Dataflowentität
* Verwenden der bewerteten Ausgabe des Modells in einem Power BI-Bericht

Weitere Informationen zur Machine Learning-Automatisierung in Power BI finden Sie unter [Automatisiertes Machine Learning in Power BI](service-machine-learning-automated.md).
