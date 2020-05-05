---
title: Tipps zur Leistung
description: Erstellen eines leistungsstarken Power BI-Visuals
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: how-to
ms.date: 04/20/2020
ms.openlocfilehash: 7ebc02b2c459517957425e78438e12e89dc2e1bb
ms.sourcegitcommit: 1059c6222458f189fb5301dcb689dad2b2c00bc1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/28/2020
ms.locfileid: "82196558"
---
# <a name="how-to-build-a-high-performance-power-bi-visual"></a>Erstellen eines leistungsstarken Power BI-Visuals
In diesem Artikel werden Verfahren behandelt, mit denen Entwickler eine hohe Leistung beim Rendern von Visuals erzielen können. 

Niemand möchte, dass ein Visual viel Zeit beim Rendern beansprucht, und das Nutzen der gesamten Leistung des Codes ist beim Rendern wichtig. 

> [!NOTE]
> Mit fortlaufenden Verbesserungen und Erweiterungen der Plattform werden ständig neue Versionen der API veröffentlicht. Es wird empfohlen, dass Sie immer die aktuelle Version verwenden, um die Plattform und Features der Power BI-Visuals optimal zu nutzen.
>
> Seit der neuesten **Version 2.1** wurden die Ladezeiten von Power BI-Visuals um durchschnittlich 20 % verbessert.

## <a name="power-bi-visual-performance-tips"></a>Tipps zur Leistung von Power BI-Visuals
Im Folgenden finden Sie einige Empfehlungen, mit denen Sie die optimale Leistung von Visuals erzielen können. 

### <a name="use-user-timing-api"></a>Verwenden der User Timing-API
Die **User Timing-API** zum Messen der JavaScript-Leistung Ihrer App kann Sie bei der Entscheidung unterstützen, welche Teile des Skripts optimiert werden müssen.

Weitere Informationen finden Sie unter [User Timing-API](https://msdn.microsoft.com/library/hh772738(v=vs.85).aspx).

### <a name="review-animation-loops"></a>Überprüfen von Animationsschleifen
Werden unveränderte Elemente von der Animationsschleife neu gezeichnet? 

 - Problem: Beim Zeichnen von Elementen, die nicht von Frame zu Frame verändert werden, wird Zeit verschwendet.

 - Lösung: Frames sollten selektiv aktualisiert werden. 
 
Beim Animieren statischer Visualisierungen ist es verlockend, den Zeichencode in eine einzelne Aktualisierungsfunktion zu schreiben und diesen wiederholt mit neuen Daten für jede Iteration der Animationsschleife aufzurufen.

Stattdessen sollten Sie das folgende Aktualisierungsmuster berücksichtigen und eine Visualkonstruktormethode zum Einzeichnen statischer Elemente verwenden, damit die Aktualisierungsfunktion nur Visualisierungselemente zeichnen muss, die sich ändern. 

   > [!TIP]
   > In Achsen und Legenden finden sich häufig ineffiziente Animationsschleifen.

### <a name="cache-dom-nodes"></a>Zwischenspeichern von DOM-Knoten 
Wenn ein Knoten oder eine Liste von Knoten vom DOM abgerufen wird, müssen Sie entscheiden, ob sie diese in späteren Berechnungen wiederverwenden können (in manchen Fällen sogar in der nächsten Iteration der Schleife). Sofern Sie keine zusätzlichen Knoten im relevanten Bereich hinzufügen oder entfernen, können Sie die Gesamteffizienz Ihrer Anwendung verbessern, indem Sie sie zwischenspeichern.

Beschränken Sie den DOM-Zugriff auf ein Mindestmaß, um sicherzustellen, dass Ihr Code schnell ist und nicht den Browser verlangsamt. 

- Vorher: 

   ```javascript
   public update(options: VisualUpdateOptions) { 
       let axis = $(".axis"); 
   }
   ```

- Nachher: 

   ```javascript
   public constructor(options: VisualConstructorOptions) { 
       this.$root = $(options.element); 
       this.xAxis = this.$root.find(".xAxis"); 
   } 
 
   public update(options: VisualUpdateOptions) { 
       let axis = this.axis; 
   }
   ```

### <a name="avoid-dom-manipulation"></a>Vermeiden der DOM-Bearbeitung 
Beschränken Sie die DOM-Bearbeitung so weit wie möglich.  Einfügevorgänge wie `prepend()`, `append()` und `after()` sind zeitaufwändig und sollten nur verwendet werden, wenn sie erforderlich sind.

Zum Beispiel:

  ```javascript
  for (let i=0; i<1000; i++) { 
      $('#list').append('<li>'+i+'</li>');
  }
  ```

Das obige Beispiel könnte beschleunigt werden, indem `html()` verwendet und die Liste im Voraus erstellt wird: 

  ```javascript
  let list = ''; 
  for (let i=0; i<1000; i++) { 
      list += '<li>'+i+'</li>'; 
  } 

  $('#list').html(list); 
  ```

### <a name="reconsider-jquery"></a>Überdenken von JQuery

Indem Sie Ihre JS-Frameworks und Ihre Verwendung von nativem JavaScript nach Möglichkeit einschränken, können Sie die verfügbare Bandbreite erhöhen und den Verarbeitungsmehraufwand reduzieren. Dadurch können Sie auch Kompatibilitätsprobleme mit älteren Browsern einschränken. 

Weitere Informationen und Beispiele für Alternativen für Funktionen wie `show`, `hide`, `addClass` und mehr von JQuery finden Sie unter [youmightnotneedjquery.com](http://youmightnotneedjquery.com/).  

### <a name="use-canvas-or-webgl"></a>Verwenden von Canvas oder WebGL 
Ziehen Sie für die wiederholte Verwendung von Animationen die Verwendung von **Canvas** oder **WebGL** anstelle von SVG in Betracht. Im Gegensatz zu SVG wird die Leistung bei diesen Optionen von der Größe anstelle der Inhalte bestimmt. 

Weitere Informationen über die Unterschiede finden Sie unter [SVG vs Canvas: How to Choose (SVG im Vergleich zu Canvas: Auswahl)](https://msdn.microsoft.com/library/gg193983(v=vs.85).aspx). 

### <a name="use-requestanimationframe-instead-of-settimeout"></a>Verwenden von requestAnimationFrame anstelle von setTimeout 
Wenn Sie [requestAnimationFrame](https://www.w3.org/TR/animation-timing/) zum Aktualisieren Ihrer angezeigten Animationen verwenden, werden Ihre Animationsfunktionen aufgerufen, **bevor** der Browser eine neue Zeichnung aufruft.

Weitere Informationen finden Sie in diesem [Beispiel](https://testdrive-archive.azurewebsites.net/Graphics/RequestAnimationFrame/Default.html) zur flüssigen Animation mit `requestAnimationFrame`.

## <a name="next-steps"></a>Nächste Schritte

Erfahren Sie mehr über Optimierungsverfahren im [Optimierungsleitfaden für Power BI](/power-bi/guidance/power-bi-optimization).
