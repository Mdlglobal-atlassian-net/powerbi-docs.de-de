---
title: Embedded Analytics mit Power BI
description: Power BI bietet APIs zum Verwenden von Embedded Analytics für Ihre Dashboards und Berichte in Anwendungen. In diesem Artikel erfahren Sie mehr über das Einbetten mit Power BI in einer PaaS-Umgebung und in einer SaaS-Umgebung unter Verwendung von Embedded Analytics-Software, Embedded Analytics-Tools oder eingebetteten Business Intelligence-Tools.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: overview
helpviewer_keywords:
- embedded analytics
- embedding
- Power BI embedding
- app owns data
- user owns data
- Power BI APIs
ms.custom: seodec18
ms.date: 05/15/2019
ms.openlocfilehash: ade60bf8b786f70002f0af0672acf951348fee49
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "80487841"
---
# <a name="embedded-analytics-with-power-bi"></a>Embedded Analytics mit Power BI

Der Power BI-Dienst (SaaS) und der Power BI Embedded-Dienst in Azure (PaaS) verfügen über APIs zum Einbetten Ihrer Dashboards und Berichte. Beim Einbetten von Inhalten erhalten Sie so Zugriff auf die neuesten Power BI-Features, wie etwa Dashboards, Gateways und Arbeitsbereiche.

Sie können mit dem [Einbettungssetuptool](https://aka.ms/embedsetup) schnell eine Beispielanwendung herunterladen und mit der Arbeit beginnen.

Wählen Sie die am besten für Sie geeignete Lösung aus:

* Das [Einbetten für Ihre Organisation](embedding.md#embedding-for-your-organization) ermöglicht Ihnen das Erweitern des Power BI-Diensts. Implementieren Sie zu diesem Zweck die Lösung [Einbetten für Ihre Organisation](https://aka.ms/embedsetup/UserOwnsData).
* Das [Einbetten für Ihre Kunden](embedding.md#embedding-for-your-customers) bietet die Möglichkeit, Dashboards und Berichte für Benutzer einzubetten, die nicht über ein Konto für Power BI verfügen. Implementieren Sie zu diesem Zweck die Lösung [Einbetten für Ihre Kunden](https://aka.ms/embedsetup/AppOwnsData).

![PBIE-Beispiel](media/embedding/what-can-you-do-02.png)

## <a name="use-apis"></a>Verwenden von APIs

Beim Einbetten von Power BI-Inhalten gibt es hauptsächlich zwei Szenarien:
- Einbetten für Benutzer in Ihrer Organisation (die über Power BI-Lizenzen verfügen). 
 
- Einbetten für Ihre Benutzer und für Kunden, ohne dass Power BI-Lizenzen erforderlich sind. 

Die [Power BI-REST-API](https://docs.microsoft.com/rest/api/power-bi/) unterstützt beide Szenarien.

Für Kunden und Benutzer ohne Power BI-Lizenzen können Sie Dashboards und Berichte in Ihre benutzerdefinierte Anwendung einbetten und dabei für Ihre Organisation und Ihre Kunden die gleiche API verwenden. Ihre Kunden sehen die von der Anwendung verwalteten Daten. Ferner haben die Power BI-Benutzer Ihrer Organisation zusätzliche Möglichkeiten zum Anzeigen *ihrer Daten*  direkt in Power BI oder im Kontext der eingebetteten Anwendung. Sie können alle Funktionen der JavaScript- und REST-APIs für das Einbetten nutzen.

Sehen Sie sich für ein besseres Verständnis der Funktionsweise von Einbettung das [JavaScript-Einbettungsbeispiel ](https://microsoft.github.io/PowerBI-JavaScript/demo/) an.

## <a name="embedding-for-your-organization"></a>Einbetten für Ihre Organisation

Das **Einbetten für Ihre Organisation** ermöglicht Ihnen das Erweitern des Power BI-Diensts. Bei dieser Art von Einbettung müssen Sie die Benutzer Ihrer Anwendung beim Power BI-Dienst anmelden, um die Inhalte anzuzeigen. Nachdem sich ein Benutzer in Ihrer Organisation angemeldet hat, hat er nur Zugriff auf Dashboards und Berichte, deren Eigentümer er ist oder die für ihn im Power BI-Dienst freigegeben wurden.

Beispiele für das Einbetten für Ihre Organisation umfassen interne Anwendungen wie [SharePoint Online](https://powerbi.microsoft.com/blog/integrate-power-bi-reports-in-sharepoint-online/), [Microsoft Teams-Integration (Administratorrechte erforderlich)](https://powerbi.microsoft.com/blog/power-bi-teams-up-with-microsoft-teams/) und [Microsoft Dynamics](https://docs.microsoft.com/dynamics365/customer-engagement/basics/add-edit-power-bi-visualizations-dashboard).

Informationen zum Einbetten für Ihre Organisation finden Sie im [Tutorial: Einbetten von Power BI-Inhalten in eine Anwendung für Ihre Organisation](embed-sample-for-your-organization.md).

Self-Service-Funktionen wie Bearbeiten, Speichern usw. stehen bei der Einbettung für Power BI-Benutzer über die [JavaScript-API](https://github.com/Microsoft/PowerBI-JavaScript) zur Verfügung.

Sie können sich mit dem [Einbettungssetuptool](https://aka.ms/embedsetup/UserOwnsData) vertraut machen, um den Einstieg zu beschleunigen und eine Beispielanwendung herunterzuladen, die sie durch die Integration eines Berichts für Ihre Organisation führt.

## <a name="embedding-for-your-customers"></a>Einbetten für Ihre Kunden

Das **Einbetten für Ihre Kunden** bietet die Möglichkeit, Dashboards und Berichte für Benutzer einzubetten, die nicht über ein Power BI-Konto verfügen. Diese Art von Einbettung wird auch als *Power BI Embedded* bezeichnet.

[Power BI Embedded](azure-pbie-what-is-power-bi-embedded.md) ist ein **Microsoft Azure**-Dienst, mit dem unabhängige Softwarehersteller (ISVs) und Entwickler Visuals, Berichte und Dashboards schnell einbetten können. Diese Einbettung erfolgt mithilfe eines kapazitätsbasierten, stündlich gemessenen Modells.

![Flussdiagramm des Einbettens für Ihre Kunden](media/embedding/powerbi-embed-flow.png)

Power BI Embedded bietet Vorteile für unabhängige Softwarehersteller, Entwickler und Kunden. Beispielsweise können unabhängige Softwarehersteller mit Power BI Desktop kostenlos Visuals erstellen. Außerdem können sie eine schnellere Markteinführung erreichen, indem sie den Entwicklungsaufwand für visuelle Analysen minimieren und sich durch differenzierte Datenerfahrung von der Konkurrenz abheben. Darüber hinaus können unabhängige Softwarehersteller eine Gebühr für den mit Embedded Analytics geschaffenen Mehrwert erheben.

Mit Power BI Embedded müssen Ihre Kunden gar nichts über Power BI wissen. Sie können zwei verschiedene Methoden zum Erstellen einer einbetteten Anwendung verwenden:
- Power BI Pro-Konto 
- Dienstprinzipal 

Das Power BI Pro-Konto fungiert als Hauptkonto Ihrer Anwendung (stellen Sie es sich als Proxykonto vor). Mit diesem Konto können Sie Einbettungstoken generieren, die Zugriff auf die Power BI-Dashboards und Berichte Ihrer Anwendung bieten.

Der [Dienstprinzipal](embed-service-principal.md) kann Power BI-Inhalte mithilfe eines Tokens **nur für Anwendungen** in eine Anwendung einbetten. Es ermöglicht außerdem das Generieren von Einbettungstoken, die Zugriff auf die Power BI-Dashboards und Berichte Ihrer Anwendung bieten.

Entwickler, die Power BI Embedded verwenden, können sich auf das Erstellen der Kernfunktionen ihrer Anwendung konzentrieren, statt Zeit für die Entwicklung von Visuals und Analysen aufzuwenden. Sie können die Anforderungen von Kundenberichten und Dashboards schnell erfüllen und problemlos mit vollständig dokumentierten APIs und SDKs einbetten. Durch das benutzerfreundliche Durchsuchen von Daten in Apps ermöglichen unabhängige Softwarehersteller ihren Kunden schnelle und datengesteuerte Entscheidungen – von jedem Gerät aus und kontextbezogen.

> [!IMPORTANT]
> Zwar ist für das Einbetten der Power BI-Dienst erforderlich, Ihre Kunden benötigen jedoch kein Power BI-Konto, um die eingebetteten Inhalte Ihrer Anwendung anzuzeigen. 

Wenn Sie bereit sind, in eine Produktionsumgebung zu wechseln, muss Ihr Arbeitsbereich einer dedizierten Kapazität zugeordnet werden. Power BI Embedded in Microsoft Azure bietet [dedizierte Kapazitäten](azure-pbie-create-capacity.md), die von Ihren Anwendungen genutzt werden können.

Ausführliche Informationen zum Einbetten finden Sie unter [Einbetten von Power BI-Inhalten](embed-sample-for-customers.md).

## <a name="next-steps"></a>Nächste Schritte

Nun können Sie mit der Einbettung von Power BI-Inhalten in eine Anwendung oder Power BI-Inhalten für Ihre Kunden loslegen.

> [!div class="nextstepaction"]
> [Embed for your organization (Einbetten für Ihre Organisation)](embed-sample-for-your-organization.md)

> [!div class="nextstepaction"]
> [Was ist Power BI Embedded?](azure-pbie-what-is-power-bi-embedded.md)

> [!div class="nextstepaction"]
>[Inhalte für Ihre Kunden einbetten](embed-sample-for-customers.md)

Weitere Fragen? [Stellen Sie Ihre Frage in der Power BI-Community.](https://community.powerbi.com/)
