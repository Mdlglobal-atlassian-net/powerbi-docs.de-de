---
title: 'Drittanbieterdienst: Facebook-Connector für Power BI Desktop'
description: 'Drittanbieterdienst: Facebook-Connector für Power BI Desktop'
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 02/20/2020
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 882cddf7728a27e78056a35c14fde20f00678e33
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "77527700"
---
# <a name="use-the-facebook-connector-for-power-bi-desktop"></a>Verwenden des Facebook-Connectors für Power BI Desktop
Der Facebook-Connector in **Power BI Desktop** ist abhängig von der Graph-API von Facebook. Daher können Funktionen und Verfügbarkeit im Laufe der Zeit variieren.

Sie können sich ein [Lernprogramm über den Facebook-Connector für Power BI Desktop](desktop-tutorial-facebook-analytics.md) anschauen.

> [!IMPORTANT]
> **Hinweis zur Veraltung des Facebook-Datenconnectors:** Das Importieren und Aktualisieren von Daten aus Facebook in Excel funktioniert ab April 2020 nicht mehr ordnungsgemäß. Bis dahin können Sie den Facebook-Connector *Abrufen und Transformieren (Power Query)* verwenden. Nach diesem Datum können Sie keine Verbindung mit Facebook herstellen, und es wird eine Fehlermeldung angezeigt. Sie sollten vorhandene *„Abrufen und Transformieren“-Abfragen (Power Query)* , die den Facebook-Connector verwenden, so schnell wie möglich überarbeiten oder entfernen, um unerwartete Ergebnisse zu vermeiden.


Facebook hat Version 1.0 seiner Graph-API am 30. April 2015 eingestellt. Die Graph-API wird von Power BI im Hintergrund für den Facebook-Connector verwendet, damit Sie sich mit Ihren Daten verbinden und diese analysieren können.

Abfragen, die vor dem 30. April 2015 erstellt wurden, funktionieren möglicherweise nicht mehr oder geben weniger Daten zurück. Nach dem 30. April 2015 nutzt Power BI Version 2.8 in allen Aufrufen an die Facebook-API. Wenn Ihre Abfrage vor dem 30. April 2015 erstellt wurde und Sie sie seitdem nicht verwendet haben, müssen Sie die Authentifizierung wahrscheinlich erneut durchführen, um den neuen Satz an Berechtigungen zu genehmigen, den wir abfragen.

Obwohl wir versuchen, gemäß allen Änderungen Updates zu veröffentlichen, könnte die API so abgeändert werden, dass sich dies auf die Ergebnisse der generierten Abfragen auswirkt. In einigen Fällen könnten bestimmte Abfragen nicht mehr unterstützt werden. Aufgrund dieser Abhängigkeit können wir die Ergebnisse Ihrer Abfragen nicht garantieren, wenn Sie diesen Connector verwenden.

Weitere Informationen über die Änderung in der Facebook-API stehen Ihnen [hier](https://developers.facebook.com/docs/apps/changelog#v2_0) zur Verfügung.

