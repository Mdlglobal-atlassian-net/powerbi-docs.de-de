---
title: Verwenden von Python im Power BI-Abfrage-Editor
description: Verwenden von Python im Abfrage-Editor von Power BI Desktop für erweiterte Analysen
author: otarb
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 06/18/2018
ms.author: otarb
LocalizationGroup: Connect to data
ms.openlocfilehash: 69490226fabc4e3022fbe2571fa062ec50aabdf5
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/13/2020
ms.locfileid: "83291648"
---
# <a name="use-python-in-query-editor"></a>Verwenden von Python im Abfrage-Editor
Sie können **Python**, eine häufig von Statistikern, Business Analysten und Datenanalysten verwendete Programmiersprache, im **Abfrage-Editor** von Power BI Desktop verwenden. Dank der Integration von Python in den **Abfrage-Editor** können Sie mithilfe von Python Daten bereinigen, erweiterte Datenstrukturierung und Analysen in Datasets ausführen, einschließlich der Ergänzung fehlender Daten, Prognosen und Clustering, um nur einige der Möglichkeiten zu nennen. **Python** ist eine leistungsfähige Sprache, die im **Abfrage-Editor** zum Erstellen des Datenmodells und Erzeugen von Berichten verwendet werden kann.

## <a name="installing-python"></a>Installieren von Python
Damit Sie **Python** im **Abfrage-Editor** von Power BI Desktop verwenden können, müssen Sie **Python** auf dem lokalen Computer installieren. **Python** können Sie an vielen Stellen im Internet kostenlos herunterladen und installieren, u.a. von der [Offiziellen Python-Downloadseite](https://www.python.org/) und aus [Anaconda](https://anaconda.org/anaconda/python/).

## <a name="using-python-in-query-editor"></a>Verwenden von Python im Abfrage-Editor
Um die Verwendung von **Python** im **Abfrage-Editor** zu veranschaulichen, wird dieses Beispiel aus einem Aktiendataset verwendet. Dieses basiert auf einer CSV-Datei, die Sie [hier herunterladen](https://download.microsoft.com/download/F/8/A/F8AA9DC9-8545-4AAE-9305-27AD1D01DC03/EuStockMarkets_NA.csv) können, um die Vorgehensweise nachzuvollziehen. Dieses Beispiel umfasst die folgenden Schritte:

1. Laden Sie zunächst die Daten in **Power BI Desktop**. Laden Sie in diesem Beispiel die Datei *EuStockMarkets_NA.csv*, und wählen Sie in **Power BI Desktop** aus dem Menüband **Home** die Option **Daten abrufen > CSV** aus.
   
   ![](media/desktop-python-in-query-editor/python-in-query-editor-1.png)
2. Wählen Sie die Datei aus und dann **Öffnen** aus. Anschließend wird die CSV-Datei im Dialogfeld **CSV-Datei** angezeigt.
   
   ![](media/desktop-python-in-query-editor/python-in-query-editor-2.png)
3. Nachdem die Daten geladen wurden, werden sie in Power BI Desktop im Bereich **Felder** angezeigt.
   
   ![](media/desktop-python-in-query-editor/python-in-query-editor-3.png)
4. Öffnen Sie den **Abfrage-Editor**, indem Sie in **Power BI Desktop** auf der Registerkarte **Start** die Option **Abfragen bearbeiten** auswählen.
   
   ![](media/desktop-python-in-query-editor/python-in-query-editor-4.png)
5. Wählen Sie auf der Registerkarte **Transformieren** die Option **Python-Skript ausführen** aus. Der Editor **Python-Skript ausführen** wird angezeigt (im nächsten Schritt dargestellt). Beachten Sie, dass in Zeile 15 und 20 Daten fehlen. Dies trifft auch für andere Zeilen zu, die in der folgenden Abbildung nicht dargestellt sind. In den folgenden Schritten wird gezeigt, wie Python diese Zeilen für Sie ausfüllt.
   
   ![](media/desktop-python-in-query-editor/python-in-query-editor-5.png)
6. Geben Sie für dieses Beispiel folgenden Skriptcode ein:
   
    ```python
       import pandas as pd
       completedData = dataset.fillna(method='backfill', inplace=False)
       dataset["completedValues"] =  completedData["SMI missing values"]
   ```

   > [!NOTE]
   > In der Python-Umgebung muss das Paket *pandas* installiert sein, damit der oben gezeigte Skriptcode ordnungsgemäß ausgeführt wird. Führen Sie zum Installieren des Pakets „pandas“ in der Python-Installation den folgenden Befehl aus: |      > pip install pandas
   > 
   > 
   
   Wenn der Code in das Dialogfeld **Python-Skript ausführen** eingefügt wird, sieht er folgendermaßen aus:
   
   ![](media/desktop-python-in-query-editor/python-in-query-editor-5b.png)
7. Nach dem Klicken auf **OK** wird im **Abfrage-Editor** ein Hinweis zum Datenschutz angezeigt.
   
   ![](media/desktop-python-in-query-editor/python-in-query-editor-6.png)
8. Für die ordnungsgemäße Ausführung von Python-Skripts im Power BI-Dienst müssen alle Datenquellen auf *Öffentlich* festgelegt werden. Weitere Informationen zu den Datenschutzeinstellungen und deren Bedeutung finden Sie unter [Sicherheitsstufen](../admin/desktop-privacy-levels.md).
   
   ![](media/desktop-python-in-query-editor/python-in-query-editor-7.png)
   
   Im Bereich **Felder** wird eine neue Spalte mit dem Namen *completedValues* angezeigt. Beachten Sie, dass einige Datenelemente fehlen, z.B. in Zeile 15 und 18. Im nächsten Abschnitt sehen Sie, wie dies von Python behandelt wird.
   

Mit einigen wenigen Zeilen Python-Skript konnte der **Abfrage-Editor** die fehlenden Werte anhand eines Vorhersagemodells einfügen.

## <a name="creating-visuals-from-python-script-data"></a>Erstellen von visuellen Elementen aus Python-Skript-Daten
Wir können jetzt ein visuelles Element erstellen, um zu sehen, wie der Python-Skript-Code mithilfe des Pakets *pandas* die fehlenden Werte eingefügt hat, wie in der folgenden Abbildung dargestellt:

![](media/desktop-python-in-query-editor/python-in-query-editor-8.png)

Wenn das visuelle Element und alle weiteren visuellen Elemente, die Sie möglicherweise mit **Power BI Desktop** erstellen möchten, vollständig erstellt wurden, können Sie die **Power BI Desktop**-Datei (eine PBIX-Datei) speichern und anschließend das Datenmodell, einschließlich der in ihm enthaltenen Python-Skripts, im Power BI-Dienst verwenden.

> [!NOTE]
> Möchten Sie eine fertige PBIX-Datei nach Abschluss dieser Schritte sehen? Dann können Sie die vollständige **Power BI Desktop**-Datei, die in diesen Beispielen verwendet wurde, [hier](https://download.microsoft.com/download/A/B/C/ABCF5589-B88F-49D4-ADEB-4A623589FC09/Complete%20Values%20with%20Python%20in%20PQ.pbix) herunterladen.

Nachdem Sie die PBIX-Datei in den Power BI-Dienst hochgeladen haben, sind einige zusätzliche Schritte erforderlich, um die Datenaktualisierung (im Dienst) und das Aktualisieren der visuellen Elemente im Dienst zu aktivieren (zum Aktualisieren der visuellen Elemente erfordern die Daten Zugriff auf Python). Die zusätzlichen Schritte lauten wie folgt:

* **Aktivieren geplanter Aktualisierungen für das Dataset** – Informationen zum Aktivieren geplanter Aktualisierungen für die Arbeitsmappe, die das Dataset mit Python-Skripts enthält, finden Sie unter [Konfigurieren geplanter Aktualisierungen](refresh-scheduled-refresh.md). Dort finden Sie auch Informationen über **Personal Gateway**.
* **Installieren von Personal Gateway** – Auf dem Computer, auf dem sich die Datei befindet und auf dem Python installiert ist, muss **Personal Gateway** installiert sein. Der Power BI-Dienst benötigt Zugriff auf die Arbeitsmappe und muss alle aktualisierten visuellen Elemente erneut rendern. Weitere Informationen zum [Installieren und Konfigurieren von Personal Gateway](service-gateway-personal-mode.md)

## <a name="limitations"></a>Einschränkungen
Für Abfragen, die im **Abfrage-Editor** erstellte Python-Skripts enthalten, gelten einige Einschränkungen:

* Alle Python-Datenquelleneinstellungen müssen auf *Öffentlich* festgelegt sein, und alle anderen Schritte einer im **Abfrage-Editor** erstellten Abfrage müssen ebenfalls öffentlich sein. Um zu den Datenquelleneinstellungen zu gelangen, wählen Sie in **Power BI Desktop** die Option **Datei > Optionen und Einstellungen > Datenquelleneinstellungen** aus.
  
  ![](media/desktop-python-in-query-editor/python-in-query-editor-9.png)
  
  Wählen Sie im Dialogfeld **Datenquelleneinstellungen** die Datenquelle(n) aus. Wählen Sie anschließend **Berechtigungen bearbeiten** aus, und stellen Sie sicher, dass die **Datenschutzebene** auf *Öffentlich* festgelegt ist.
  
  ![](media/desktop-python-in-query-editor/python-in-query-editor-10.png)    
* Um geplante Aktualisierungen der visuellen Python-Elemente oder des Datasets zu ermöglichen, müssen Sie **Geplante Aktualisierung** aktivieren, und auf dem Computer, auf dem sich die Arbeitsmappe und die Python-Installation befinden, muss **Personal Gateway** installiert sein. Weitere Informationen zu beiden Features finden Sie im vorherigen Abschnitt dieses Artikels, der Links zu weiteren Informationen über jedes dieser Features enthält.
* Geschachtelte Tabellen (Tabellen von Tabellen) werden derzeit nicht unterstützt. 

Python und benutzerdefinierte Abfragen bieten Ihnen unzählige Möglichkeiten – Sie können Daten analysieren und genau so strukturieren, wie sie dargestellt werden sollen.
