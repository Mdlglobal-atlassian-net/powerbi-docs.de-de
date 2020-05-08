---
title: Paginierte Berichte im Power BI-Dienst
description: Dokumentation zu paginierten Berichten und dem Anzeigen im Power BI-Dienst
author: mihart
ms.reviewer: chris finlan
ms.service: powerbi
ms.subservice: powerbi-consumer
ms.topic: conceptual
ms.date: 03/11/2020
ms.author: mihart
LocalizationGroup: Common tasks
ms.openlocfilehash: c4c21dc0f02e547cd7319d789a3eb66cce1f4b88
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "79377349"
---
# <a name="paginated-reports-in-the-power-bi-service"></a>Paginierte Berichte im Power BI-Dienst

[!INCLUDE[consumer-appliesto-yyny](../includes/consumer-appliesto-yyny.md)]

Sie haben sich grundlegende Kenntnisse im Umgang mit [Power BI-Berichten](end-user-reports.md) angeeignet, und dies sind die Berichtstypen, auf die Sie am wahrscheinlichsten stoßen. Es gibt jedoch noch einen anderen Berichtstyp, der als *paginierter Bericht* bezeichnet wird. *Berichts-Designer* können paginierte Berichte in einem Arbeitsbereich in einer Premium-Kapazität oder einer App aus diesem Arbeitsbereich für Sie freigeben. 

## <a name="what-is-a-paginated-report"></a>Was ist ein paginierter Bericht?

Diese Berichte werden als *paginiert* bezeichnet, weil sie so formatiert sind, dass sie gut auf eine gedruckte Seite passen. Ein Vorteil besteht darin, dass sie alle Daten in einer Tabelle anzeigen, selbst wenn sich die Tabelle über mehrere Seiten erstreckt. Paginierte Berichte werden gelegentlich auch als „pixel perfect“ bezeichnet, da *Berichts-Designer* das Layout der Berichtsseite genau steuern können.

Wenn *Berichts-Designer* einen paginierten Bericht erstellen, erstellen sie tatsächlich eine *Berichtsdefinition*. Sie enthält keine Daten. Sie gibt an, wo die Daten bereitstehen, welche Daten abzurufen sind und wie die Daten angezeigt werden sollen. Bei Ausführung des Berichts legt der Berichtsprozessor die Berichtsdefinition zugrunde, ruft die Daten ab und kombiniert sie mit dem Berichtslayout, um den Bericht zu generieren. In manchen Fällen zeigt der Bericht Standarddaten an. Sie müssen ggf. Parameter eingeben, bevor der Bericht Daten anzeigen kann. 

   ![Parameter für den Bericht](./media/end-user-paginated-report/power-bi-report-parameters.png)

Das entspricht in der Regel dem Umfang der Interaktion, bei der die Parameter festgelegt werden. Wenn Sie in Ihrem Unternehmen in der Abrechnungsabteilung tätig sind, können Sie mit paginierten Berichten beispielsweise Rechnungen erstellen oder drucken. Als Vertriebsleiter können Sie mithilfe von paginierten Berichten Bestellungen nach Geschäft oder Vertriebsmitarbeiter anzeigen. 

Dieser einfache paginierte Bericht generiert den Gewinn nach Jahr, nachdem Sie den Parameter **Jahr** ausgewählt haben. 

![Einfacher Parameterbericht](./media/end-user-paginated-report/power-bi-report-simple.png)

Im Vergleich zu paginierten Berichten sind Power BI-Berichte viel interaktiver. Power BI-Berichte ermöglichen die Ad-hoc-Berichterstellung und unterstützen viele weitere Arten von Visuals einschließlich Power BI-Visuals.

## <a name="identify-a-paginated-report"></a>Identifizieren eines paginierten Berichts

In den Inhaltslisten und auf der Startseite „Home“ können paginierte Berichte durch das ![Symbol für paginierten Bericht](media/end-user-paginated-report/power-bi-report-icon.png) identifiziert werden.  Ein paginierter Bericht kann direkt für Sie oder als Teil einer [Power BI-App](end-user-apps.md) freigegeben werden. Wenn der Ihnen der *Berichts-Designer* Berechtigungen erteilt hat, können Sie den paginierten Bericht nochmals freigeben und andere abonnieren.

![Berichtsliste mit unterschiedlichen Symbolen](./media/end-user-paginated-report/power-bi-report-list.png)

## <a name="interact-with-a-paginated-report"></a>Interagieren mit einem paginierten Bericht

Die Interaktion mit einem paginierten Bericht unterscheidet sich von der Interaktion mit anderen Berichten. Sie können z. B. drucken, Lesezeichen einfügen, exportieren und kommentieren. Die Interaktivität ist dabei allerdings geringer. Häufig erfordern paginierte Berichte Eingaben, um den Zeichenbereich für den Bericht aufzufüllen.  Im Bericht werden Standarddaten angezeigt, und Sie können Parameter eingeben, um unterschiedliche Daten anzuzeigen.

### <a name="print-a-paginated-report"></a>Drucken eines paginierten Berichts

*Paginierte* Berichte sind so formatiert, dass sie gut auf eine Seite passen und gedruckt werden können. Im Browser wird das angezeigt, das Sie sehen, wenn Sie drucken. Wenn der Bericht eine lange Tabelle beinhaltet, wird die gesamte Tabelle auch dann gedruckt, wenn sie mehrere Seiten umfasst. 

Paginierte Berichte können viele Seiten umfassen. Dieser Bericht umfasst beispielsweise 563 Seiten. Jede Seite ist genau strukturiert, mit einer Seite pro Rechnung und sich wiederholenden Kopf- und Fußzeilen. Wenn Sie diesen Bericht drucken, werden zwischen den Rechnungen Seitenumbrüche angezeigt.

   ![Seite 1 eines paginierten Berichts für Tailspin Toys](./media/end-user-paginated-report/power-bi-paginated-500.png)


### <a name="navigate-the-paginated-report"></a>Navigieren im paginierten Bericht

In diesem Bericht zu Bestellungen gibt es drei Parameter: Geschäftstyp, Handelspartner und Bestellnummer. 

![Bericht mit drei Parametern](./media/end-user-paginated-report/power-bi-parameter.png)

Geben Sie neue Werte für die drei Parameter ein, und klicken Sie auf **B anzeigen**, um die angezeigten Informationen zu ändern. Hier haben wir **Specialty bike shop**, **Alpine Ski House** und Bestellnummer **SO46085** ausgewählt. Wenn Sie auf **Bericht anzeigen** klicken, wird der Zeichenbereich des Berichts mit dieser neuen Bestellung aktualisiert.

![Ändern der Parameter](./media/end-user-paginated-report/power-bi-order.png)

Die neue Bestellung wird mit den ausgewählten Parametern angezeigt. 

![Neue Bestellung](./media/end-user-paginated-report/power-bi-new-order.png)

Einige paginierte Berichte umfassen möglicherweise viele Seiten.  Verwenden Sie die Steuerelemente für die Seiten, um durch den Bericht zu navigieren. 

![Steuerelemente für Seiten](./media/end-user-paginated-report/power-bi-page.png)

### <a name="export-the-paginated-report"></a>Exportieren des paginierten Berichts
Sie verfügen über eine Vielzahl von Optionen zum Exportieren von paginierten Berichten einschließlich PDF, Word, XML, PowerPoint, Excel usw. Beim Exportieren wird der Großteil der Formatierungen, wenn möglich, beibehalten. Paginierte Berichte, die in Excel, Word, PowerPoint, MHTML oder das PDF-Format exportiert werden, behalten z. B. die Formatierung „pixel perfect“ bei. 

![Neue Bestellung](./media/end-user-paginated-report/power-bi-exporting.png)

![Vier verschiedene Exporttypen](./media/end-user-paginated-report/power-bi-four.png)

### <a name="subscribe-to-the-paginated-report"></a>Abonnieren des paginierten Berichts
Wenn Sie einen paginierten Bericht abonnieren, sendet Power BI eine E-Mail mit dem Bericht als Anlage. Durch das Einrichten Ihres Abonnements können Sie entscheiden, ob Sie die E-Mails stündlich, täglich, wöchentlich oder monatlich erhalten möchten. Das Abonnement enthält eine Anlage mit der gesamten Berichtsausgabe mit einer Größe von bis zu 25 MB. Exportieren Sie den gesamten Bericht, oder wählen Sie die Parameter im Voraus aus. Wählen Sie aus vielen unterschiedlichen Anlagentypen einschließlich Excel, PDF, PowerPoint usw. aus.  

![Formate beim Abonnieren von Berichten](./media/end-user-paginated-report/power-bi-export-list.png)

## <a name="considerations-and-troubleshooting"></a>Zu beachtende Aspekte und Problembehandlung

- Ein paginierter Bericht kann leer sein, bis Sie Parameter auswählen und auf **Bericht anzeigen** klicken.

- Wenn Sie über keine paginierten Berichte verfügen, kann dies daran liegen, dass niemand diese Art von Bericht für Sie freigegeben hat. Dies kann auch bedeuten, dass der Systemadministrator paginierte Berichte nicht für Sie aktiviert hat. 

 

## <a name="next-steps"></a>Nächste Schritte
- [Power BI-Berichte](end-user-reports.md)
- Weitere Fragen? Wenden Sie sich an die [Power BI-Community](https://community.powerbi.com/).

