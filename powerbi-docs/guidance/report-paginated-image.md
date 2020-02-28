---
title: Leitfaden zur Verwendung von Bildern für paginierte Berichte
description: Leitfaden zur Verwendung von Bildern für paginierte Berichte in Power BI
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.date: 02/16/2020
ms.author: v-pemyer
ms.openlocfilehash: 09fd2197cca31e083c0242b187d7e242244235eb
ms.sourcegitcommit: b22a9a43f61ed7fc0ced1924eec71b2534ac63f3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/21/2020
ms.locfileid: "77530370"
---
# <a name="image-use-guidance-for-paginated-reports"></a>Leitfaden zur Verwendung von Bildern für paginierte Berichte

Dieser Artikel richtet sich an Berichtsautoren, die [paginierte Berichte](../paginated-reports-report-builder-power-bi.md) in Power BI entwerfen. Er enthält Vorschläge für die Arbeit mit Bildern. Generell können in Berichtslayouts Grafiken wie Firmenlogos oder Fotos eingesetzt werden.

Bilder können an drei verschiedenen Speicherorten gespeichert werden:

- Im Bericht (eingebettet)
- Auf einem Webserver
- In einer Datenbank, die von einem Dataset abgerufen werden kann

Sie können dann in einer Vielzahl von Szenarios in Berichtslayouts verwendet werden:

- Freistehendes Logo oder Foto
- Mit Datenzeilen verknüpfte Fotos
- Hintergrund für bestimmte Berichtselemente:
  - Hauptteil des Berichts
  - Textfeld
  - Rechteck
  - Tablix-Datenbereich (Tabelle, Matrix oder Liste)

## <a name="suggestions"></a>Vorschläge

Wenn Sie die folgenden Vorschläge beherzigen, können Sie professionelle Berichtslayouts erstellen, einfach verwalten und die Berichtsleistung optimieren:

- **Verwenden Sie möglichst kleine Bilder:** Es wird empfohlen, möglichst kleine Bilder vorzubereiten, die aber immer noch scharf sind. Schaffen Sie einen Ausgleich zwischen Qualität und Größe. Verwenden Sie ggf. einen Editor für Grafiken (z. B. MS Paint), um die Bilddatei zu verkleinern.
- **Vermeiden Sie die Verwendung von eingebetteten Bildern:** Zum einen werden Berichtsdateien durch eingebettete Bilder größer. Dies kann dazu führen, dass Berichte langsamer gerendert werden. Zum anderen können eingebettete Bilder schnell zu mehr Verwaltungsaufwand führen, wenn Sie mehrere Berichtsbilder aktualisieren müssen (z. B. wenn ihr Unternehmenslogo geändert wird).
- **Verwenden Sie einen Webserverspeicher:** Webserver eignen sich gut zum Speichern von Bildern, insbesondere wenn es sich um Unternehmenslogos handelt, die der Unternehmenswebsite entnommen werden können. Seien Sie allerdings vorsichtig, wenn die Benutzer außerhalb Ihres Netzwerks auf die Berichte zugreifen. Achten Sie in diesem Fall darauf, dass die Bilder im Internet verfügbar sind.

    Wenn Bilder im Zusammenhang mit Ihren Daten stehen (z. B. Fotos Ihres Vertriebsteams), benennen Sie die Bilddateien, damit ein Berichtsausdruck dynamisch den URL-Pfad zu Ihrem Bild erstellen kann. Beispielsweise können Sie den Bildern Ihres Vertriebsteams die Personalnummern der einzelnen Teammitglieder zuordnen. Wenn Sie das Berichtsdatasets bereitstellen, wird die Personalnummer abgerufen. Sie können einen Ausdruck schreiben, um den vollständigen URL-Pfad der Bilder zu erstellen.
- **Verwenden Sie einen Datenbankspeicher:** Wenn in einer relationalen Datenbank Bilddaten gespeichert werden, sollten diese Bilddaten direkt aus Datenbanktabellen entnommen werden, insbesondere wenn sie nicht zu groß sind.
- **Verwenden Sie geeignete Hintergrundbilder:** Wenn Sie sich für die Verwendung von Hintergrundbildern entscheiden, achten Sie darauf, dass diese den Berichtsbenutzer nicht von den Berichtsdaten ablenken. 

    Achten Sie auch darauf, _im Wasserzeichenstil formatierte Bilder_ zu verwenden. Diese Bilder haben in der Regel einen transparenten Hintergrund oder dieselbe Hintergrundfarbe wie der Bericht. Außerdem werden schwache Farben verwendet. Häufig werden Bilder wie Unternehmenslogos oder Vertraulichkeitsbezeichnungen wie „Entwurf“ oder „Vertraulich“ im Wasserzeichenstil formatiert.

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zu diesem Artikel finden Sie in den folgenden Ressourcen:

- [Was sind paginierte Berichte in Power BI Premium? (Vorschau)](../paginated-reports-report-builder-power-bi.md)
- Haben Sie Fragen? [Stellen Sie Ihre Frage in der Power BI-Community.](https://community.powerbi.com/)
- Vorschläge? [Einbringen von Ideen zur Verbesserung von Power BI](https://ideas.powerbi.com/)
