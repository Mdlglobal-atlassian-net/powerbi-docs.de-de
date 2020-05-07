---
title: Q&A in Power BI Embedded
description: Power BI Embedded bietet Ihnen eine Möglichkeit, Q&A in eine Anwendung zu integrieren, sodass Ihre Benutzer in natürlicher Sprache Fragen stellen können.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 11/20/2017
ms.openlocfilehash: 5a3a7b91b0c97a75923876caff205ffb9abfce70
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "80114380"
---
# <a name="qa-in-power-bi-embedded"></a>Q&A in Power BI Embedded

Power BI Embedded bietet Ihnen eine Möglichkeit, Q&A in eine Anwendung zu integrieren, sodass Ihre Benutzer Fragen in natürlicher Sprache stellen können und sofort Antworten in Form von Visuals wie Diagrammen oder Graphs erhalten.

![Interaktive Q&A-Frage in einem eingebetteten Rahmen](media/qanda/embedded-qanda.gif)

Es gibt zwei Modi für das Einbetten von Q&A in die Anwendung: **interaktiv** und **auf Ergebnisse beschränkt**. Im **interaktiven** Modus können Sie Fragen eingeben und diese innerhalb der Visuals anzeigen lassen. Wenn Sie über eine gespeicherte Frage oder eine festgelegte Frage verfügen, die angezeigt werden soll, können Sie den **auf Ergebnisse beschränkten** Modus verwenden, um die Frage in Ihre Einbettungskonfiguration einzugeben.

Im Folgenden wird der JavaScript-Code veranschaulicht.

```javascript
// Embed configuration used to describe the what and how to embed.
// This object is used when calling powerbi.embed within the JavaScript API.
// You can find more information at https://github.com/Microsoft/PowerBI-JavaScript/wiki/Embed-Configuration-Details.
var config= {
    type: 'qna',
    tokenType:   models.TokenType.Embed | models.TokenType.Aad,
    accessToken: access token value,
    embedUrl:    https://app.powerbi.com/qnaEmbed (groupId to be appended as query parameter if required),
    datasetIds:  array of requested data set ids (at the moment we support only one dataset),
    viewMode:    models.QnaMode.Interactive | models.QnaMode.ResultOnly,
    question:    optional parameter for Explore mode (QnaMode.Interactive) and mandatory for Render Result mode (QnaMode.ResultOnly)
};

// Get a reference to the embedded QNA HTML element
var qnaContainer = $('#qnaContainer')[0];

// Embed the QNA and display it within the div container.
var qna = powerbi.embed(qnaContainer, config);
```

## <a name="set-question"></a>Festgelegte Frage

Wenn Sie den **Ergebnismodus** mit einer festgelegten Frage verwendet haben, können Sie weitere Fragen in den Rahmen einfügen und sofort beantworten lassen, wobei das vorherige Ergebnis ersetzt wird. Ein neues Visual wird für die neue Frage gerendert.

Ein Beispiel für eine solche Verwendung ist eine Liste mit häufig gestellten Fragen. Der Benutzer kann die Fragen durcharbeiten und die Antworten im selben eingebetteten Teil erhalten.

**Codeausschnitt für JS-SDK-Verwendung:**  

```javascript
// Get a reference to the embedded Q&A HTML element
var qnaContainer = $('#qnaContainer')[0];

// Get a reference to the embedded Q&A.
qna = powerbi.get(qnaContainer);

qna.setQuestion("This year sales")
    .then(function (result) {
        …….
    })
    .catch(function (errors) {
        …….
    });
```

## <a name="visual-rendered-event"></a>visualRendered-Ereignis

Für den **interaktiven** Modus kann die Anwendung mit einem Datenänderungsereignis benachrichtigt werden, wenn sich das gerenderte Visual ändert, um auf die aktualisierte Eingabeabfrage während ihrer Eingabe zu verweisen.

Durch Überwachen des *visualRendered*-Ereignisses können Sie Fragen für die spätere Verwendung speichern. 

**Codeausschnitt für JS-SDK-Verwendung:**  

```javascript
// Get a reference to the embedded Q&A HTML element
var qnaContainer = $('#qnaContainer')[0];

// Get a reference to the embedded Q&A.
qna = powerbi.get(qnaContainer);

// qna.off removes a given event listener if it exists.
qna.off("visualRendered");

// qna.on will add an event listener.
qna.on("visualRendered", function(event) {
     …….
});
```

## <a name="embed-token"></a>Einbettungstoken

Erstellen Sie ein Einbettungstoken aus einem Dataset, um ein Q&A-Teil zu starten. Weitere Informationen finden Sie im Artikel mit Vorgängen zum [Generieren eines Tokens](https://docs.microsoft.com/rest/api/power-bi/embedtoken).

## <a name="next-steps"></a>Weitere Schritte

Um sich mit der Q&A-Einbettung vertraut zu machen, sehen Sie sich das [JavaScript-Einbettungsbeispiel](https://microsoft.github.io/PowerBI-JavaScript/demo/) an.

Weitere Fragen? [Stellen Sie Ihre Frage in der Power BI-Community.](https://community.powerbi.com/)
