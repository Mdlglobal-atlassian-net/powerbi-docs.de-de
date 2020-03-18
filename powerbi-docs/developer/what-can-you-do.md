---
title: Welche Möglichkeiten bietet Power BI Entwicklern?
description: Power BI bietet eine Vielzahl von Möglichkeiten für Entwickler. Dies reicht vom Einbetten bis hin zu benutzerdefinierten Visuals und dem Streamen von Datasets.
author: KesemSharabi
ms.author: kesharab
ms.topic: overview
ms.service: powerbi
ms.subservice: powerbi-developer
ms.custom: mvc
ms.date: 03/15/2019
ms.openlocfilehash: 4e8ce6d9a892abf3e24ecae6dee1e3ea23504d31
ms.sourcegitcommit: 87b7cb4a2e626711b98387edaa5ff72dc26262bb
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/10/2020
ms.locfileid: "79041353"
---
# <a name="what-can-developers-do-with-power-bi"></a>Welche Möglichkeiten bietet Power BI Entwicklern?

Entwicklern stehen verschiedene Optionen zur Verfügung, um Power BI-Inhalte in Anwendungen einzuschließen. Als Entwickler können Sie diese Optionen verwenden, darunter **Einbetten mit Power BI**, **benutzerdefinierte Visuals** und **Übertragen von Daten per Push in Power BI**.

## <a name="embedding-power-bi-content"></a>Einbetten von Power BI-Inhalt

Der Power BI-Dienst (SaaS) und der Power BI Embedded-Dienst in Azure (PaaS) verfügen über APIs zum Einbetten Ihrer Dashboards und Berichte. Dies bedeutet, dass Sie auf die neuesten Power BI-Features, z.B. Dashboards, Gateways und Arbeitsbereich, zugreifen können, wenn Sie Inhalte einbetten.

Sie können mit dem [Einbettungssetuptool](https://aka.ms/embedsetup) schnell eine Beispielanwendung herunterladen und mit der Arbeit beginnen.

Wählen Sie die am besten für Sie geeignete Lösung aus:

* Das [Einbetten für Ihre Kunden](embedding.md#embedding-for-your-customers) bietet die Möglichkeit, Dashboards und Berichte für Benutzer einzubetten, die nicht über ein Konto für Power BI verfügen. Führen Sie die Lösung [Einbetten für Ihre Kunden](https://aka.ms/embedsetup/AppOwnsData) aus.

* Das [Einbetten für Ihre Organisation](embedding.md#embedding-for-your-organization) ermöglicht Ihnen das Erweitern des Power BI-Diensts. Führen Sie die Lösung [Einbetten für Ihre Organisation](https://aka.ms/embedsetup/UserOwnsData) aus.

![PBIE-Beispiel](media/what-can-you-do/what-can-you-do-02.png)

Weitere Informationen zum Einbetten mit Power BI finden Sie unter [Einbetten mit Power BI](embedding.md).

## <a name="developing-custom-visuals"></a>Entwickeln von benutzerdefinierten Visuals

Sie können benutzerdefinierte Visuals in Power BI verwenden, um einen eindeutigen Typ von Visual zu erstellen, der auf Sie oder Ihr Unternehmen zugeschnitten ist. Diese benutzerdefinierten Visuals werden häufig von Entwicklern erstellt. Sie werden erstellt, wenn die zahlreichen in Power BI inbegriffenen Visuals nicht ganz Ihren Anforderungen entsprechen.

Mit benutzerdefinierten Visuals können Sie Ihre eigenen Visuals für die Verwendung in Power BI-Berichten erstellen. Benutzerdefinierte Visuals werden in TypeScript geschrieben, einer Sprache, die auf JavaScript aufsetzt. TypeScript unterstützt einige erweiterte Features und frühzeitigen Zugriff auf ES6/ES7-Funktionen. Stile für Visuals werden mit Cascading Stylesheets (CSS) angewendet. Zur Vereinfachung wird der Less-Vorcompiler verwendet, der einige erweiterte Features unterstützt, darunter Schachtelung, Variablen, Bedingungen und Schleifen. Wenn Sie diese Features nicht verwenden möchten, können Sie einfachen CSS-Code in der Less-Datei schreiben.

![CV-Beispiel](media/what-can-you-do/powerbi-custom-visual-store.png)

Weitere Informationen zur Entwicklung von benutzerdefinierten Visuals finden Sie unter [Entwickeln eines benutzerdefinierten Visuals für Power BI](visuals/custom-visual-develop-tutorial.md).

## <a name="using-api-automation"></a>Mithilfe der API-Automatisierung

Power BI zeigt interaktive Dashboards an und kann aus vielen unterschiedlichen Datenquellen in Echtzeit erstellt und aktualisiert werden. Sie können mit jeder Programmiersprache, die REST-Aufrufe unterstützt, Apps erstellen, die sich in Echtzeit in ein Power BI-Dashboard integrieren lassen. Sie können auch Power BI-Kacheln und -Berichte in Apps integrieren.

Entwickler können auch eigene Datenvisualisierungen erstellen, die in interaktiven Berichten und mit Dashboards verwendet werden können.

![Beispiel für das Übertragen von Daten per Push](media/what-can-you-do/powerbi-push-data.png)

Einige Aktionen, die Sie mit Power BI-APIs durchführen können, finden Sie unter [Welche Möglichkeiten bietet die Power BI-API für Entwickler?](automation/overview-of-power-bi-rest-api.md)?

## <a name="next-steps"></a>Nächste Schritte

[Einbetten mit Power BI](embedding.md)  

[Entwickeln eines benutzerdefinierten Visuals für Power BI](https://microsoft.github.io/PowerBI-visuals/docs/step-by-step-lab/developing-a-power-bi-custom-visual/)

[Welche Möglichkeiten bietet die Power BI-API für Entwickler?](automation/overview-of-power-bi-rest-api.md)

[Power BI Developer Center](https://powerbi.microsoft.com/developers/)