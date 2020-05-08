---
title: Herunterladen eines Berichts aus dem Power BI-Dienst in Power BI Desktop (Vorschau)
description: Herunterladen eines Berichts aus dem Power BI-Dienst in eine Power BI Desktop-Datei
author: maggiesMSFT
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 04/01/2020
ms.author: maggies
LocalizationGroup: Reports
ms.openlocfilehash: 15a4d88ac9de5d50caeb975afa8ad1758246031f
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "80551083"
---
# <a name="download-a-report-from-the-power-bi-service-to-power-bi-desktop-preview"></a>Herunterladen eines Berichts aus dem Power BI-Dienst in Power BI Desktop (Vorschau)
In Power BI Desktop können Sie einen Bericht (*PBIX*-Datei) von Ihrem lokalen Computer aus über den Power BI-Dienst veröffentlichen. Mit Power BI-Berichten können Sie auch andersherum vorgehen: Sie können auch einen Bericht aus dem Power BI-Dienst in Power BI Desktop herunterladen. Die Erweiterung für einen Power BI-Bericht ist in beiden Fällen „.pbix“.

Es sind einige Einschränkungen zu berücksichtigen, die in diesem Artikel unter [Zu beachtende Aspekte und Problembehandlung](#considerations-and-troubleshooting) erläutert werden.

![Dropdownliste mit Dateien](media/service-export-to-pbix/power-bi-file-export.png)

## <a name="download-the-report-as-a-pbix-file"></a>Herunterladen des Berichts als PBIX-Datei

Sie können nur Berichte herunterladen, die nach dem 23. November 2016 [mit Power BI Desktop erstellt](/learn/modules/publish-share-power-bi/2-publish-reports) und seitdem aktualisiert wurden. Wenn er vor diesem Zeitpunkt erstellt wurde, ist die Menüoption **Bericht herunterladen** im Power BI-Dienst ausgegraut.

Gehen Sie zum Herunterladen der PBIX-Datei folgendermaßen vor:

1. Öffnen Sie im Power BI-Dienst den Bericht, den Sie in der [Bearbeitungsansicht](https://docs.microsoft.com/power-bi/service-interact-with-a-report-in-editing-view) herunterladen möchten.

2. Wählen Sie im oberen Navigationsbereich **Datei > Bericht herunterladen** aus.
   
3. Während der Bericht heruntergeladen wird, zeigt ein Statusbanner den Fortschritt an. Wenn die Datei bereit ist, werden Sie gefragt, wo Sie die PBIX-Datei speichern möchten. Der Standardname der Datei stimmt mit dem Titel des Berichts überein.
   
4. Falls noch nicht erfolgt, installieren Sie [Power BI Desktop](desktop-get-the-desktop.md), und öffnen Sie dann die PBIX-Datei in Power BI Desktop.
   
    Wenn Sie den Bericht in Power BI Desktop öffnen, werden Sie möglicherweise in einer Warnmeldung darüber informiert, dass einige im Bericht aus dem Power BI-Dienst verfügbare Features in Power BI Desktop nicht verfügbar sind.
   
    ![Dialogfeld „Warnung“](media/service-export-to-pbix/power-bi-export-to-pbix_2.png)

5. Der Berichts-Editor in Power BI Desktop und der Berichts-Editor im Power BI-Dienst sind ähnlich.  
   
    ![Berichts-Editor in Power BI Desktop](media/service-export-to-pbix/power-bi-desktop.png)

## <a name="considerations-and-troubleshooting"></a>Zu beachtende Aspekte und Problembehandlung
Beim Herunterladen einer PBIX-Datei aus dem Power BI-Dienst sind einige wichtige Überlegungen und Einschränkungen zu beachten.

* Sie müssen über Bearbeitungszugriff auf den Bericht verfügen, um die Datei herunterladen zu können.
* Der Bericht muss mit Power BI Desktop erstellt und im Power BI-Dienst *veröffentlicht* worden sein, oder die PBIX-Datei muss in den Power BI-Dienst *hochgeladen* worden sein.
* Die Berichte müssen nach dem 23. November 2016 veröffentlicht oder aktualisiert worden sein. Vorher veröffentlichte Berichte können nicht heruntergeladen werden.
* Diese Funktion kann nicht für Berichte und Inhaltspakete genutzt werden, die ursprünglich im Power BI-Dienst erstellt wurden.
* Verwenden Sie immer die neueste Version von Power BI Desktop, wenn Sie heruntergeladene Dateien öffnen. Heruntergeladene PBIX-Dateien werden in nicht aktuellen Versionen von Power BI Desktop möglicherweise nicht geöffnet.
* Wenn Ihr Administrator die Möglichkeit zum Herunterladen von Daten deaktiviert hat, ist dieses Feature im Power BI-Dienst nicht sichtbar.
* Datasets mit inkrementeller Aktualisierung können nicht in eine PBIX-Datei heruntergeladen werden.
* Wenn Sie einen Power BI-Bericht auf Grundlage eines Datasets in einem Arbeitsbereich erstellen und in einem anderen Arbeitsbereich veröffentlichen, können Sie und Ihre Benutzer ihn nicht herunterladen. Die Downloadfunktion wird zurzeit in diesem Szenario nicht unterstützt.

## <a name="next-steps"></a>Nächste Schritte
Sehen Sie sich das **Guy in a Cube**-Kurzvideo (in englischer Sprache) zu diesem Feature an:

<iframe width="560" height="315" src="https://www.youtube.com/embed/ymWqU5jiUl0" frameborder="0" allowfullscreen></iframe>

Weitere Informationen, die bei der Verwendung des Power BI-Diensts hilfreich sein können, finden Sie in diesen Artikeln:

* [Berichte in Power BI](consumer/end-user-reports.md)
* [Grundlegende Konzepte für Designer im Power BI-Dienst](service-basic-concepts.md)

Nachdem Sie Power BI Desktop installiert haben, lesen Sie den folgenden Artikel, damit Sie direkt loslegen können:

* [Erste Schritte mit Power BI Desktop](desktop-getting-started.md)

Weitere Fragen? [Wenden Sie sich an die Power BI-Community](https://community.powerbi.com/).

