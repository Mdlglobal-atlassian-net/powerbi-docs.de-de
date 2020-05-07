---
title: 'Kontrollieren der Verwendung von Datasets in mehreren Arbeitsbereichen (Vorschau): Power BI'
description: Erfahren Sie, wie der Informationsfluss im Power BI-Mandanten eingeschränkt werden kann.
author: maggiesMSFT
ms.reviewer: chbraun
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 05/31/2019
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: d1ad29bebc148d9f30e8d22240dd149787251a0a
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "73872585"
---
# <a name="control-the-use-of-datasets-across-workspaces-preview"></a>Kontrollieren der Verwendung von Datasets in mehreren Arbeitsbereichen (Vorschau)

Das übergreifende Verwenden von Datasets in Arbeitsbereichen ist ein leistungsfähiges Verfahren, die Datenkultur und die Demokratisierung von Daten in einer Organisation zu stärken. Trotzdem möchten Sie als Power BI-Administrator manchmal den Informationsfluss in Ihrem Power BI-Mandanten einschränken. Mit der Mandanteneinstellung **Verwenden von Datasets in mehreren Arbeitsbereichen** können Sie die Wiederverwendung von Datasets entweder vollständig unterbinden oder mithilfe von Sicherheitsgruppen einschränken.

![Power BI-Administrator-Arbeitsbereichseinstellungen](media/service-datasets-admin-across-workspaces/power-bi-admin-workspace-settings.png)

Dies sind die Auswirkungen für Berichtersteller, wenn Sie diese Einstellung deaktivieren:

- Die Schaltfläche zum Kopieren von Berichten zwischen Arbeitsbereichen steht nicht zur Verfügung. 
- In einem Bericht, der auf einem freigegebenen Dataset basiert, ist die Schaltfläche **Bericht bearbeiten** nicht verfügbar.
- Im Power BI-Dienst zeigt die Ermittlungsoberfläche nur Datasets im aktuellen Arbeitsbereich an.
- In Power BI Desktop zeigt die Ermittlungsoberfläche nur Datasets aus Arbeitsbereichen an, in denen Sie Mitglied sind.
- Wenn in Power BI Desktop Benutzer eine PBIX-Datei mit einer Liveverbindung zu einem Dataset außerhalb von Arbeitsbereichen öffnen, bei denen sie Mitglied sind, sehen sie eine Fehlermeldung, die sie auffordert, eine Verbindung mit einem anderen Dataset herzustellen.

## <a name="provide-a-link-for-the-certification-process"></a>Bereitstellen eines Links für den Zertifizierungsprozess

Als Mandantenadministrator können Sie eine URL für den Link **Weitere Informationen** auf der Einstellungsseite **Unterstützung** angeben.  Dieser Link kann auf Dokumentation zu Ihrem Zertifizierungsprozess verweisen. Wenn Sie kein Ziel für den Link **Weitere Informationen** angeben, verweist er standardmäßig auf den Artikel [Dataset-Zertifizierung](service-datasets-certify.md).

![Dataset-Zertifizierung „Weitere Informationen“](media/service-datasets-certify-promote/power-bi-dataset-learn-more-certification.png)

## <a name="next-steps"></a>Weitere Schritte

- [Verwenden von Datasets in mehreren Arbeitsbereichen (Vorschau)](service-datasets-across-workspaces.md)
- Fragen? [Stellen Sie Ihre Frage in der Power BI-Community.](https://community.powerbi.com/)
