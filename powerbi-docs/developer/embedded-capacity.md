---
title: Kapazität und SKUs in eingebetteten Power BI-Analysen
description: Grundlegendes zur Kapazität und den SKUs in Power BI Embedded Analytics
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 02/11/2020
ms.openlocfilehash: f8c3bdf3e3f92d570205551a97389def2921fe98
ms.sourcegitcommit: 17aad73762579d6822383b27b96b1b63f87f2d6f
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/14/2020
ms.locfileid: "77260455"
---
# <a name="capacity-and-skus-in-power-bi-embedded-analytics"></a>Kapazität und SKUs in eingebetteten Power BI-Analysen

Bei einem Wechsel in eine Produktionsumgebung benötigt Power BI Embedded Analytics eine dedizierte Kapazität (SKUs *A*, *EM* oder *P*), um eingebettete Power BI-Inhalte zu veröffentlichen.

Kapazität bezeichnet die dedizierte Gruppe von Ressourcen, die für eine bestimmte Verwendung reserviert ist. Damit können Sie Dashboards, Berichte und Datasets für Benutzer veröffentlichen, ohne separate Lizenzen für jeden einzelnen erwerben zu müssen. Außerdem bietet sie eine zuverlässige, beständige Leistung für Ihre gehosteten Inhalte.

>[!NOTE]
>Zum Veröffentlichen benötigen Sie ein Power BI Pro-Konto.

## <a name="what-is-embedded-analytics"></a>Was ist Embedded Analytics?

Power BI Embedded Analytics enthält zwei Lösungen:
* *Power BI Embedded:* ein Azure-Angebot
* Power BI-Einbettung im Rahmen von *Power BI Premium*: Office-Angebot

### <a name="power-bi-embedded"></a>Power BI Embedded

Power BI Embedded wurde für unabhängige Softwarehersteller und Entwickler entwickelt, die Visuals in ihre Anwendungen einbetten möchten.

In Anwendungen mit Power BI Embedded können Benutzer Inhalte verwenden, die in der Power BI Embedded-Kapazität gespeichert sind.

### <a name="power-bi-premium"></a>Power BI Premium

[Power BI Premium](../service-premium-what-is.md) ist auf Unternehmen zugeschnitten, die eine umfassende BI-Lösung mit einer zentralen Ansicht ihrer Organisation, ihrer Partner, Kunden und Zulieferer benötigen.

Power BI Premium ist ein SaaS-Produkt, das es Benutzern ermöglicht, Inhalte über mobile Apps, intern entwickelte Apps oder das Power BI-Portal (Power BI-Dienst) zu verwenden. So kann Power BI Premium sowohl eine Lösung für interne als auch für externe kundenseitige Anwendungen anbieten.

## <a name="capacity-and-skus"></a>Kapazität und SKUs

Jede Kapazität bietet verschiedene SKUs, und jede SKU bietet verschiedene Ressourcenebenen, was Speicher und Computeleistung angeht. Welchen SKU-Typ Sie benötigen, hängt vom Typ der Lösung ab, die Sie bereitstellen möchten.

Bevor Sie entscheiden, welche SKU Sie erwerben, lesen Sie bitte die Informationen in diesem Abschnitt.
* Lesen Sie auch den Artikel [Konfigurieren von Workloads in einer Premium-Kapazität](../service-admin-premium-workloads.md), um zu verstehen, welche Workloads in den einzelnen Ebenen unterstützt werden.
* Unter diesem Link erfahren Sie, wie Sie [Ihre Kapazität planen und testen](../service-premium-capacity-optimize.md#testing-approaches).

### <a name="power-bi-embedded-skus"></a>SKUs für Power BI Embedded

Power BI Embedded wird mit einer *A*-SKU ausgeliefert.
* [Welche Benutzerauslastung kann Ihre Power BI Embedded-Kapazität verarbeiten?](https://powerbi.microsoft.com/blog/power-bi-developer-community-june-july-update/#Capacity-Plan)
* [Erwerben von *A*-SKUs für Test- und andere Szenarios](../service-admin-premium-purchase.md#purchase-a-skus-for-testing-and-other-scenarios)

### <a name="power-bi-premium-skus"></a>Power BI Premium-SKUs

Power BI Premium bietet zwei SKUs: *P* und *EM*.
* [Abonnements und Lizenzierung](../service-premium-what-is.md#subscriptions-and-licensing)
* [Erwerben von Power BI Premium](../service-admin-premium-purchase.md)

### <a name="which-sku-should-i-use"></a>Welche SKU sollte ich verwenden?

Diese Tabelle enthält eine Übersicht der Features und ihrer erforderlichen Kapazität und SKU. 

</br>
<table>
<col width="20%">
<col width="20%">
<col width="20%">
<col width="20%">
<col width="20%">
<tbody>
<tr>
<td style="text-align: center"; colspan="2"><p><b>Feature</b></p></td>
<td style="text-align: center">
<p><b>Power BI Embedded</b></p>
</td>
<td style="text-align: center"; colspan="2">
<p><b>Power BI Premium</b></p>
</td>
</tr>
<tr>
<td><p><em>Was wird verwendet?</em><p></td>
<td><p><em>Was verwendet?</em><p></td>
<td style="text-align: center"><p><em>A-SKUs</br>(Azure)</em></p></td>
<td style="text-align: center"><p><em>EM-SKUs</br>(Office)</em></p></td>
<td style="text-align: center"><p><em>P-SKUs</br>(Office)</em></p></td>
</tr>
<tr>
<td>Einbetten von Artefakten aus dem Power BI-Arbeitsbereich</td>
<td>
</td>
<td style="text-align: center">✔</td>
<td style="text-align: center">✔</td>
<td style="text-align: center">✔</td>
</tr>
<tr>
<td rowspan="2">Power BI-Berichte</td>
<td>Eine eingebettete Anwendung für Ihre Organisation</br>(der Benutzer besitzt die Daten)</td>
<td style="text-align: center">✖</td>
<td style="text-align: center">✔</td>
<td style="text-align: center">✔</td>
</tr>
<tr>
<td>Eine eingebettete Anwendung für Ihre Kunden</br>(die App besitzt die Daten)</td>
<td style="text-align: center">✔</td>
<td style="text-align: center">✔</td>
<td style="text-align: center">✔</td>
</tr>
<tr>
<td rowspan="3">Power BI-Inhalt<br>(mit einer kostenlosen Power BI-Lizenz)</td>
<td>Power BI-Dienst</td>
<td style="text-align: center">✖</td>
<td style="text-align: center">✖</td>
<td style="text-align: center">✔</td>
</tr>
<tr>
<td>Power BI Mobile</td>
<td style="text-align: center">✖</td>
<td style="text-align: center">✖</td>
<td style="text-align: center">✔</td>
</tr>
<tr>
<td>MS Office-Apps</td>
<td style="text-align: center">✖</td>
<td style="text-align: center">✔</td>
<td style="text-align: center">✔</td>
</tr>
</tbody>
</table>

### <a name="capacity-considerations"></a>Überlegungen zur Kapazität

In der folgenden Tabelle werden die Zahlungs- und Nutzungsüberlegungen pro Kapazität aufgelistet.

</br>
<table>
<tbody>
<tr>
<td></td>
<td style="text-align: center;"><p><strong>Power BI Embedded</strong></p></td>
<td style="text-align: center;" colspan="2"><p><strong>Power BI Premium</strong></p></td>
</tr>
<tr>
<td><p><strong>Angebot</strong></p></td>
<td style="text-align: center;"><p>Azure</p></td>
<td style="text-align: center;" colspan="2"><p>Office</p></td>
</tr>
<tr>
<td><p><strong>SKU</strong></p></td>
<td style="text-align: center;"><p>A</p></td>
<td style="text-align: center;"><p>EM</p></td>
<td style="text-align: center;"><p>P</p></td>
</tr>
<tr>
<td><p><strong>Abrechnung</strong></td>
<td style="text-align: center;">Stündlich</td>
<td style="text-align: center;">Monatlich</td>
<td style="text-align: center;">Monatlich</td>
</tr>
<tr>
<td><p><strong>Vertragsbindung</strong></td>
<td style="text-align: center;">Ohne</td>
<td style="text-align: center;">Monatlich oder jährlich</td>
<td style="text-align: center;">Monatlich oder jährlich</td>
</tr>
<tr>
<td valign="top"><p><strong>Verwendung</strong></td>
<td style="text-align: center;">Azure-Ressourcen können:</br>- <a href="azure-pbie-scale-capacity.md">zentral hoch- oder herunterskaliert werden</a></br>- <a href="azure-pbie-pause-start.md">angehalten und fortgesetzt werden</a>
</td>
<td style="text-align: center;">Einbetten in Apps und in</br> Microsoft-Anwendungen</td>
<td style="text-align: center;">Einbetten in Apps und</br> in den Power BI-Dienst</td>
</tr>
</tbody>
</table>

### <a name="sku-memory-and-computing-power"></a>SKU-Speicher und Computeleistung

In der Tabelle unten sind die Ressourcen und Grenzen der einzelnen SKUs beschrieben.

| Kapazitätsknoten | Gesamtzahl an V-Kernen | Back-End-V-Kerne | RAM (GB) | Front-End-V-Kerne | DirectQuery/Live Connection (s) | Modell-Aktualisierungsparallelität |
| --- | --- | --- | --- | --- | --- | --- |
| EM1/A1 | 1 | 0,5 | 2.5 | 0,5 | 3,75 | 1 |
| EM2/A2 | 2 | 1 | 5 | 1 | 7,5 | 2 |
| EM3/A3 | 4 | 2 | 10 | 2 | 15 | 3 |
| P1/A4 | 8 | 4 | 25 | 4 | 30 | 6 |
| P2/A5 | 16 | 8 | 50 | 8 | 60 | 12 |
| P3/A6 | 32 | 16 | 100 | 16 | 120 | 24 |
| P4 | 64 | 32 | 200 | 32 | 240 | 48 |
| P5 | 128 | 64 | 400 | 64 | 480 | 96 |
| | | | | | | |

## <a name="next-steps"></a>Nächste Schritte

> [!div class="nextstepaction"]
>[Inhalte für Ihre Kunden einbetten](embed-sample-for-customers.md)

> [!div class="nextstepaction"]
>[Embed for your organization (Einbetten für Ihre Organisation)](embed-sample-for-your-organization.md)

> [!div class="nextstepaction"]
> [Embed from apps (Einbetten aus Apps)](embed-from-apps.md)