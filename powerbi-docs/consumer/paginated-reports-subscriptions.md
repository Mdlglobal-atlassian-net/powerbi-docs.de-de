---
title: Abonnieren von paginierten Berichten im Power BI-Dienst
description: In diesem Artikel erhalten Sie wichtige Informationen zum Abonnieren von paginierten Berichten im Power BI-Dienst.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.date: 12/03/2019
ms.openlocfilehash: d3813636010dcbf5c866248111755beb0dca99b8
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "74834630"
---
# <a name="subscribe-yourself-and-others-to-paginated-reports-in-the-power-bi-service"></a>Abonnieren von paginierten Berichten für sich selbst und andere im Power BI-Dienst 

Sie können jetzt im Power BI-Dienst E-Mail-Abonnements für paginierte Berichte für sich selbst und andere einrichten. Im Allgemeinen ist dieser Vorgang identisch mit dem [Abonnieren von Berichten und Dashboards im Power BI-Dienst](end-user-subscribe.md). In diesem Artikel werden Unterschiede und Überlegungen aufgeführt. 

Durch das Einrichten von Abonnements können Sie entscheiden, ob Sie die E-Mails täglich, wöchentlich, monatlich oder stündlich erhalten möchten. Sie können auch die Zeiten auswählen, zu denen das Abonnement ausgeführt werden soll. Insgesamt können Sie für jeden Bericht bis zu 24 verschiedene Abonnements einrichten. 

## <a name="considerations-for-paginated-report-subscriptions"></a>Überlegungen zu Abonnements von paginierten Berichten 

- Im Gegensatz zu Dashboards oder Power BI-Berichten enthält Ihr Abonnement eine Anlage mit der gesamten Berichtsausgabe.  Die folgenden Anlagetypen werden unterstützt: PDF, PowerPoint-Präsentation (.pptx), Excel-Arbeitsmappe (.xlsx), Word-Dokument (.docx), CSV-Datei und XML.

- Sie können im E-Mail-Text ein Vorschaubild des Berichts anzeigen.  Dies ist optional und kann sich je nach gewähltem Anhangformat leicht von der ersten Seite Ihres angehängten Berichtsdokuments unterscheiden. 

- Die maximale Größe der Anlage eines Berichts beträgt 25 MB. 

- Sie können paginierte Berichte für andere Benutzer abonnieren, die eine Verbindung mit irgendwelchen derzeit unterstützten Datenquellen herstellt (einschließlich Azure Analysis Services oder Power BI-Datasets). Bedenken Sie, dass die Anlage des Berichts die Daten basierend auf Ihren Berechtigungen widerspiegelt (wie SQL Server Reporting Services heute). 

- E-Mail-Abonnements können entweder mit den aktuell ausgewählten oder den Standardparametern für Ihren Bericht gesendet werden.  Sie können für jedes Abonnement, das Sie für Ihren Bericht erstellen, unterschiedliche Parameterwerte festlegen. 

- Wenn der Autor Ihres Berichts ausdrucksbasierte Parameter festgelegt hat (z.B. der Standardwert ist immer das heutige Datum), verwendet das Abonnement diesen als Standardwert. Sie können andere Parameterwerte ändern und die Verwendung aktueller Werte wählen. Wenn Sie diesen Wert jedoch nicht explizit ändern, verwendet das Abonnement den ausdrucksbasierten Parameter.

- Die Option **After Data Refresh** (Nach der Datenaktualisierung) steht für die Häufigkeit mit paginierten Berichten nicht zur Verfügung. Sie erhalten immer die aktuellen Werte der zugrunde liegenden Datenquelle. 

## <a name="next-steps"></a>Nächste Schritte

[Subscribe yourself and others to reports and dashboards in the Power BI service (Abonnieren von Berichten und Dashboards im Power BI-Dienst für sich selbst und andere)](../service-report-subscribe.md)

[Paginierte Berichte im Power BI-Dienst](end-user-paginated-report.md)

