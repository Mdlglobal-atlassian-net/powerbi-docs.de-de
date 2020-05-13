---
title: Filtern und Freigeben eines Power BI-Berichts
description: Erfahren Sie, wie Sie einen Power BI-Bericht für Kollegen in Ihrer Organisation filtern und freigeben.
author: maggiesMSFT
ms.reviewer: lukaszp
featuredvideoid: 0tUwn8DHo3s
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 01/29/2020
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: 636aaf59a3a949b5b3571012d12cecc234e9763b
ms.sourcegitcommit: bfc2baf862aade6873501566f13c744efdd146f3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/13/2020
ms.locfileid: "83347951"
---
# <a name="filter-and-share-a-power-bi-report"></a>Filtern und Freigeben eines Power BI-Berichts
*Freigeben* ist eine gute Möglichkeit, einigen Personen Zugriff auf Ihre Dashboards und Berichte zu gewähren. Wie gehen Sie vor, wenn Sie eine gefilterte Version eines Berichts freigeben möchten? Vielleicht möchten Sie, dass der Bericht nur Daten für eine bestimmte Stadt, einen bestimmten Vertriebsmitarbeiter oder ein bestimmtes Jahr anzeigt. In diesem Artikel erfahren Sie, wie Sie einen Bericht filtern und anschließend die gefilterte Version freigeben. Ein gefilterter Bericht lässt sich auch freigeben, indem Sie [der Berichts-URL Abfrageparameter hinzuzufügen](service-url-filters.md). Bei beiden Möglichkeiten wird der Bericht gefiltert, wenn die Empfänger in das erste Mal öffnen. Sie können die gesetzten Filter auch entfernen.

![Gefilterter Bericht](media/service-share-reports/power-bi-share-filter-pane-report.png)

Zudem bietet Power BI [andere Möglichkeiten zum gemeinsamen Bearbeiten und Verteilen Ihrer Berichte](service-how-to-collaborate-distribute-dashboards-reports.md). Zum Freigeben benötigen Sie und die Empfänger eine [Power BI Pro-Lizenz](../fundamentals/service-features-license-type.md), oder es muss sich um Inhalte in einer [Premium-Kapazität](../admin/service-premium-what-is.md) handeln. 

## <a name="follow-along-with-sample-data"></a>Interaktives Beispiel

In diesem Artikel wird die Beispielvorlagen-App „Marketing und Sales“ (Marketing und Umsatz) verwendet. Möchten Sie es ausprobieren? 

1. Installieren Sie die [Beispielvorlagen-App „Marketing & Sales“](https://appsource.microsoft.com/product/power-bi/microsoft-retail-analysis-sample.salesandmarketingsample?tab=Overview).
2. Wählen Sie die App aus, und klicken Sie auf **App erkunden**.

   ![Erkunden von Beispieldaten](media/service-share-reports/power-bi-sample-explore-data.png)

3. Klicken Sie auf das Stiftsymbol, um den Arbeitsbereich zu öffnen, den Sie mit der App installiert haben.

    ![Stiftsymbol zum Bearbeiten der App](media/service-share-reports/power-bi-edit-pencil-app.png)

4. Klicken Sie in der Liste mit den Arbeitsbereichinhalten auf **Berichte**, und wählen Sie den Bericht **Sales and Marketing Sample PBIX** (Umsatz- und Marketingbeispiel PBIX) aus.

    ![Beispielbericht öffnen](media/service-share-reports/power-bi-open-sample-report.png)

    Jetzt können Sie die in diesem Artikel beschriebenen Aktionen selbst im Beispiel ausprobieren.

## <a name="set-a-filter-in-the-report"></a>Filtern eines Berichts

Öffnen Sie einen Bericht in der [Bearbeitungsansicht](../consumer/end-user-reading-view.md), und wenden Sie einen Filter an.

In diesem Beispiel filtern wir die Seite „YTD Category“ (Kategorie „Seit Jahresbeginn“) der Beispielvorlagen-App „Marketing & Sales“ so, dass Werte nur dort angezeigt werden, wo **Region** gleich **Central** (Mitte) ist. 
 
![Berichtsfilterbereich](media/service-share-reports/power-bi-share-report-filter.png)

Speichern Sie den Bericht.

## <a name="share-the-filtered-report"></a>Freigeben des gefilterten Berichts

1. Wählen Sie **Freigeben** aus.

   ![„Freigeben“ auswählen](media/service-share-reports/power-bi-share.png)

2. Deaktivieren Sie die Option **E-Mail-Benachrichtigung an Empfänger senden**, um stattdessen einen gefilterten Link verschicken zu können. Wählen Sie dann **Bericht mit aktuellen Filtern und Slicern freigeben** aus, und klicken Sie auf **Freigeben**.

    ![Bericht mit Filtern freigeben](media/service-share-reports/power-bi-share-with-filters.png)

4. Klicken Sie noch einmal auf **Freigeben**.

   ![„Freigeben“ auswählen](media/service-share-reports/power-bi-share.png)

5. Klicken Sie auf die Registerkarte **Zugriff** und anschließend auf **Freigegebene Berichtansichten verwalten**.

    ![Freigegebene Berichtansichten verwalten](media/service-share-reports/power-bi-manage-shared-report-views.png)

6. Klicken Sie mit der rechten Maustaste auf die gewünschte URL, und wählen Sie **Link kopieren** aus.

    ![Link zum gefilterten Bericht kopieren](media/service-share-reports/power-bi-copy-filtered-link.png)

7. Wenn Sie diesen Link freigeben, sehen Empfänger den gefilterten Bericht. 


## <a name="next-steps"></a>Weitere Schritte
* [Freigeben Ihrer Arbeit in Power BI](service-how-to-collaborate-distribute-dashboards-reports.md)
* [Freigeben eines Dashboards](service-share-dashboards.md)
* Weitere Fragen? [Wenden Sie sich an die Power BI-Community](https://community.powerbi.com/).
* Feedback? Anregungen nehmen wir auf der [Power BI-Communitywebsite](https://community.powerbi.com/) entgegen.
