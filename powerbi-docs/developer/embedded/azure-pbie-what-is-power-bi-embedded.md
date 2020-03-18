---
title: Power BI Embedded und Embedded Analytics in Azure | Microsoft-Dokumentation
description: Power BI Embedded ist als Embedded Analytics-Tool gedacht und soll die Nutzung von Power BI-Funktionen für unabhängige Softwarehersteller und Entwickler vereinfachen und ihnen dabei helfen, ihren Anwendungen schnell beeindruckende Visuals, Berichte und Dashboards hinzuzufügen. In diesem Artikel erfahren Sie mehr über Embedded Analytics-Software, Embedded Analytics-Tools sowie eingebettete Business Intelligence-Tools bei der Verwendung von Power BI Embedded.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: nishalit
ms.service: power-bi-embedded
ms.subservice: ''
ms.devlang: csharp, javascript
ms.topic: overview
ms.custom: seodec18
ms.date: 12/10/2018
ms.openlocfilehash: f04621fdfe7e6055d84fa4d2672c874837ff5ea4
ms.sourcegitcommit: a175faed9378a7d040a08ced3e46e54503334c07
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/18/2020
ms.locfileid: "79495272"
---
# <a name="what-is-power-bi-embedded-in-azure"></a>Was ist Power BI Embedded in Azure?

Power BI Embedded soll unabhängigen Softwareherstellern (Independent Software Vendor, ISV) und Entwicklern die Verwendung von Power BI-Funktionen mit Embedded Analytics erleichtern. Power BI Embedded vereinfacht die Power BI-Funktionen, indem es Ihnen dabei hilft, Ihren Anwendungen schnell beeindruckende Visuals, Berichte und Dashboards hinzuzufügen. Ähnlich wie Apps, die auf Microsoft Azure basieren, werden Dienste wie Machine Learning und IoT verwendet. Unabhängige Softwarehersteller ermöglichen ihren Kunden durch das benutzerfreundliche Durchsuchen von Daten in ihren Anwendungen schnelle, fundierte und kontextbezogene Entscheidungen zu treffen.

> [!VIDEO https://www.youtube.com/embed/iEHfUuoZseo]

Im Mai 2017 wurde die Konvergenz von Power BI- und Power BI Embedded-Diensten angekündigt. Die Konvergenz bietet eine API-Oberfläche, eine konsistente Reihe von Funktionen und Zugriff auf die neuesten Funktionen beider Dienste. Außerdem wurde ein kapazitätsbasiertes Preismodell eingeführt, das den Power BI-Verbrauch vereinfacht.

Mit Power BI Embedded sind unabhängige Softwarehersteller und Entwickler flexibler beim Einbetten von Intelligenz in ihre Anwendungen über die Power BI-APIs. Unabhängige Softwarehersteller und Entwickler können die Vorteile eines minimierten Entwicklungsaufwands nutzen, um eine schnellere Markteinführung und Differenzierung zu erreichen, indem sie die erstklassige Analyse-Engine von Microsoft in ihre App integrieren. Ebenso können sich Entwickler auf ihre Lösung konzentrieren, um Kundenanforderungen zu erfüllen, anstatt visuelle Analysefunktionen zu entwickeln. Darüber hinaus können Sie mit Power BI Embedded in den bekannten Entwicklungsumgebungen – Visual Studio und Azure – arbeiten, die Sie bereits verwenden.

Haben Sie eine vorhandene App mit eingebetteten Power BI-Inhalten mit Power BI Premium? Wenn Sie ein unabhängiger Softwarehersteller oder Entwickler sind, der Apps bereitstellt, oder einer Organisation angehören, die diese nutzt, ist keine Aktion erforderlich. Sie und Ihre Kunden können diese Apps ohne Unterbrechung weiterhin nutzen. Wenn Sie eine vorhandene App haben, die auf Power BI-Arbeitsbereichsammlungen basiert, und die Vorteile der konvergenten API-Oberfläche sowie der neuen kapazitätsbasierten Azure-SKUs nutzen möchten, lesen Sie die Dokumentation zur Migrationsanleitung.

## <a name="comparing-power-bi-embedded-with-power-bi-premium"></a>Vergleich: Power BI Embedded und Power BI Premium

**Power BI Embedded** richtet sich an unabhängige Softwareanbieter und Entwickler, die Anwendungen für Kunden entwickeln. Es kann als Business Intelligence-Drittanbieterdienst genutzt werden, um Anwendungsdaten zu visualisieren, anstatt diesen Dienst selbst zu erstellen. Power BI Embedded ist eine PaaS-Analyselösung (Platform as a Service), mit der Entwickler Berichte und Dashboards in eine Anwendung für ihre Kunden einbetten können. **Power BI Premium** hingegen ist eine SaaS-Analyselösung (Software-as-a-Service), die Ihrer Organisation eine zentrale Ansicht Ihrer wichtigsten Geschäftsdaten bietet. 

[Power BI Embedded](https://azure.microsoft.com/pricing/details/power-bi-embedded/) beruht auf nutzungsbasierter Bezahlung, während für [Power BI Premium](https://powerbi.microsoft.com/calculator/) eine monatliche Gebühr anfällt. In [diesem Video](https://www.youtube.com/watch?v=0y2oJikC6Xc&t=0s&list=PLv2BtOtLblH1dQPV49Ni12olDcUoW-GEl&index=3) erfahren Sie mehr über die Unterschiede.

## <a name="easy-to-use-tools"></a>Leicht zu bedienende Tools

Mit Power BI Embedded können Sie sich auf das konzentrieren, was Sie am besten können: das Entwickeln großartiger Anwendungen. Sie können mit Power BI Embedded mit bereits vorhandenen Tools und Fähigkeiten verwalten und entwickeln.

* [**Azure-Portal:** ](https://portal.azure.com/) eine webbasierte Anwendung zum Verwalten aller Azure-Dienste
* [**Visual Studio Code**](https://code.visualstudio.com/docs): ein kostenloser, herunterladbarer Open Source-Code-Editor für Windows, macOS und Linux, der Erweiterungen unterstützt
* [**Power BI Desktop**](https://powerbi.microsoft.com/desktop/): ein kostenloses, herunterladbares Tool zum Erstellen umfassender, interaktiver Berichte mit visuellen Analysen

Mithilfe der REST-API ermöglicht Power BI Embedded die Entwicklung mit jeder beliebigen Sprache.

## <a name="engage-with-the-power-bi-engineering-team"></a>Austausch mit dem Power BI-Technikteam

* [Communitys:](https://community.powerbi.com/) Stellen Sie Fragen zu Power BI.
* [Power BI Ideas:](https://ideas.powerbi.com) Fordern Sie Funktionen an und bewerten Sie diese.
* [Reddit:](https://www.reddit.com/r/PowerBI/) Tauschen Sie sich über Power BI aus.

## <a name="next-steps"></a>Nächste Schritte

In der [Preisübersicht](https://azure.microsoft.com/pricing/details/power-bi-embedded/) finden Sie weitere Informationen zu Kapazitätsknoten.

Weitere Informationen zum Erstellen einer Power BI Embedded-Kapazität finden Sie unter [Erstellen einer Power BI Embedded-Kapazität im Azure-Portal](azure-pbie-create-capacity.md).

Weitere Informationen zum Einbetten von Power BI-Inhalten finden Sie unter [Einbetten von Power BI-Berichten, -Dashboards oder -Kacheln](https://powerbi.microsoft.com/documentation/powerbi-developer-embedding-content/).
