---
title: Herstellen einer Verbindung mit einer Amazon Redshift-Datenbank in Power BI Desktop
description: Einfaches Verbinden mit und Verwenden von einer Amazon Redshift-Datenbank in Power BI Desktop
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/08/2019
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: de172db743573e82700db9cf32c59d13c35aebc2
ms.sourcegitcommit: bfc2baf862aade6873501566f13c744efdd146f3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/13/2020
ms.locfileid: "83347630"
---
# <a name="connect-to-an-amazon-redshift-database-in-power-bi-desktop"></a>Herstellen einer Verbindung mit einer Amazon Redshift-Datenbank in Power BI Desktop
In **Power BI Desktop** können Sie eine Verbindung mit einer **Amazon Redshift**-Datenbank herstellen und die zugrunde liegenden Daten wie alle anderen Datenquellen in Power BI Desktop verwenden.

## <a name="connect-to-an-amazon-redshift-database"></a>Herstellen einer Verbindung mit einer Amazon Redshift-Datenbank
Klicken Sie in Power BI Desktop im Menüband **Start** auf die Option **Daten abrufen**, um eine Verbindung mit einer **Amazon Redshift**-Datenbank herzustellen. Wählen Sie in den Kategorien auf der linken Seite **Datenbank** aus. Anschließend wird **Amazon Redshift** angezeigt.

![](media/desktop-connect-redshift/connect_redshift_3.png)

Geben Sie im angezeigten Fenster **Amazon Redshift** den Namen des **Amazon Redshift**-Servers und der Amazon Redshift-Datenbank in das Feld ein, oder fügen Sie sie ein. Im Feld *Server* können Benutzer auch einen Port im folgenden Format eingeben: *ServerURL:Port*

![](media/desktop-connect-redshift/connect_redshift_4.png)

Wenn Sie dazu aufgefordert werden, geben Sie Ihren Benutzernamen und Ihr Kennwort ein. Sie sollten den Servernamen verwenden, der exakt mit dem SSL-Zertifikat übereinstimmt, um Fehler zu vermeiden. 

![](media/desktop-connect-redshift/connect_redshift_5.png)

Nachdem die Verbindung erfolgreich hergestellt wurde, wird das Fenster **Navigator** mit den auf dem Server verfügbaren Daten angezeigt. Aus diesen können Sie ein oder mehrere Elemente auswählen, die importiert und in **Power BI Desktop** verwendet werden sollen.

![](media/desktop-connect-redshift/connect_redshift_6.png)

Sobald Sie im Fenster **Navigator** eine Auswahl vornehmen, können Sie die Daten **laden** oder **bearbeiten**.

* Wenn Sie die Option zum **Laden** von Daten ausgewählt haben, werden Sie aufgefordert, hierzu den Modus *importieren* oder *DirectQuery* zu verwenden. Weitere Informationen finden Sie in diesem [Artikel, in dem DirectQuery erläutert wird](desktop-use-directquery.md).
* Wenn Sie die Option zum **Bearbeiten** der Daten ausgewählt haben, wird der **Abfrage-Editor** angezeigt. In diesem können Sie alle Arten von Transformationen und Filtern auf die Daten anwenden, von denen viele auf die zugrunde liegende **Amazon Redshift**-Datenbank selbst angewendet werden (sofern unterstützt).

## <a name="next-steps"></a>Weitere Schritte
Sie können mithilfe von Power BI Desktop eine Verbindung mit Daten jeglicher Art herstellen. Weitere Informationen zu Datenquellen finden Sie in folgenden Ressourcen:

* [Was ist Power BI Desktop?](../fundamentals/desktop-what-is-desktop.md)
* [Datenquellen in Power BI-Desktop](desktop-data-sources.md)
* [Strukturieren und Kombinieren von Daten mit Power BI Desktop](desktop-shape-and-combine-data.md)
* [Verbinden mit Excel in Power BI Desktop](desktop-connect-excel.md)   
* [Eingeben von Daten direkt in Power BI Desktop](desktop-enter-data-directly-into-desktop.md)   
