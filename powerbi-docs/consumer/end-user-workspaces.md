---
title: Organisieren von Inhalten in Arbeitsbereichen
description: In diesem Artikel erhalten Sie Informationen zu Arbeitsbereichen und Arbeitsbereichsrollen.
author: mihart
ms.reviewer: lukaszp
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 04/22/2020
ms.author: mihart
LocalizationGroup: Consumers
ms.openlocfilehash: 801b5cf5400bbe1cc0487eef596ea3d1cdc5fb1e
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "82120161"
---
# <a name="collaborate-in-workspaces"></a>Zusammenarbeiten in Arbeitsbereichen

 In *Arbeitsbereichen* können Sie mit Kollegen an bestimmten Inhalten zusammenarbeiten. Arbeitsbereiche werden von Power BI-*Designern* erstellt und enthalten Sammlungen von Dashboards und Berichten. Anschließend kann der Designer diese Sammlung in einer *App* bündeln und sie an die gesamte Organisation oder an bestimmte Personen oder Gruppen verteilen. 

 Alle Personen, die den Power BI-Dienst nutzen, verfügen auch über **Mein Arbeitsbereich**.  Bei „Mein Arbeitsbereich“ handelt es sich um Ihre persönliche Sandbox, in der Sie Inhalte für sich selbst erstellen können.

 Ihre Arbeitsbereiche werden auf der **Startseite** von Power BI angezeigt, oder indem Sie auf **Arbeitsbereich** oder **Mein Arbeitsbereich** im linken Navigationsbereich klicken.

 ![Navigationsbereich mit den zwei Arten von Arbeitsbereichen](media/end-user-workspaces/power-bi-home.png)

## <a name="types-of-workspaces"></a>Typen von Arbeitsbereichen
Unter **Mein Arbeitsbereich** werden alle Inhalte gespeichert, deren Besitzer Sie sind und die Sie erstellt haben. Betrachten Sie ihn als persönlichen Sandkasten oder Arbeitsbereich für eigene Inhalte. Bei vielen Power BI-*Anwendern* bleibt der Bereich **Mein Arbeitsbereich** immer leer, da das Erstellen neuer Inhalte nicht zu ihren Aufgaben gehört. *Anwender* nutzen die Daten, die von anderen erstellt wurden, um Geschäftsentscheidungen zu treffen. Falls Sie doch Inhalte erstellen möchten, lesen Sie stattdessen die Artikel zum [Erstellen von Berichten und Dashboards in Power BI](../create-reports/index.yml).

**App-Arbeitsbereiche** enthalten den gesamten Inhalt der jeweiligen App. Wenn *Designer* eine App erstellen, bündeln sie alle Inhalte, die für die Nutzung der App erforderlich sind. Zu den Inhalten gehören Dashboards, Berichte und Datasets. Nicht alle App-Arbeitsbereiche enthalten diese drei Elemente. Sie können auch nur ein Dashboard, jeweils drei Elemente oder 20 Berichte enthalten. Alles hängt davon ab, was der *Designer* in der App bündelt. In der Regel enthalten die App-Arbeitsbereiche von *Consumern* jedoch keine Datasets.

Im App-Arbeitsbereich „Fig sales“ unten sind drei Berichte und ein Dashboard enthalten. 

![Navigationsbereich mit den zwei Arten von Arbeitsbereichen](media/end-user-workspaces/power-bi-app-workspace.png)

## <a name="roles-in-the-workspaces"></a>Rollen in den Arbeitsbereichen

Rollen bestimmen, wofür Sie in einem Arbeitsbereich berechtigt sind, sodass Teams zusammenarbeiten können.  Bei Gewährung des Zugriffs auf einen neuen Arbeitsbereich fügen *Designer* Einzelpersonen oder Gruppen einer der Arbeitsbereichsrollen hinzu: **Anzeigender Benutzer**, **Mitglied**, **Mitwirkender** oder **Administrator**. 


Als Power BI-*Consumer* interagieren Sie in der Regel in Arbeitsbereichen mithilfe der Rolle **Anzeigender Benutzer**. Ein *Designer* könnten Ihnen jedoch auch die Rolle **Mitglied** oder **Mitwirkender** zuweisen. Die Rolle „Anzeigender Benutzer“ ermöglicht Ihnen die Anzeige von und Interaktion mit Inhalten (Dashboards, Berichte, Apps), die von anderen Personen erstellt und für Sie freigegeben wurden. Da die Rolle „Anzeigender Benutzer“ keinen Zugriff auf das zugrunde liegende Dataset hat, handelt es sich hierbei um eine sichere Möglichkeit, mit Inhalten zu interagieren, ohne sich dabei Sorgen machen zu müssen, dass die zugrunde liegenden Daten „verletzt“ werden.


Eine detaillierte Liste der Möglichkeiten, die Ihnen als *Consumer* im Rahmen der Rolle „Anzeigender Benutzer“ zur Verfügung stehen, finden Sie unter [Power BI-Featureliste für Anwender und andere Benutzer mit kostenlosen Lizenzen](end-user-features.md).


### <a name="workspace-roles"></a>Arbeitsbereichsrollen
Folgende Rollen sind verfügbar: Administrator, Mitglied, Mitwirkender und Betrachter. Für alle diese Funktionen außer Anzeigen und Interaktion ist eine Power BI Pro-Lizenz erforderlich.

|Funktionalität   | Administrator  | Mitglied  | Mitwirkender  | Viewer |
|---|---|---|---|---|
| Den Arbeitsbereich aktualisieren und löschen.  | X  |   |   |   | 
| Personen hinzufügen/entfernen (einschließlich anderer Administratoren).  | X  |   |   |   |
| Mitglieder oder andere Benutzer mit niedrigeren Berechtigungen hinzufügen.  |  X | X  |   |   |
| Apps veröffentlichen und aktualisieren. |  X | X  |   |   |
| Elemente und Apps freigeben<sup>1</sup> |  X | X  |   |   |
| Anderen erlauben, Elemente erneut freizugeben<sup>1</sup> |  X | X  |   |   |
| Apps auf der Startseite von Kollegen unter „Empfohlen“ anzeigen lassen |  X | X  |   |   |
| Dashboards und Berichte auf der Startseite von Kollegen unter „Empfohlen“ anzeigen lassen |  X | X  | X |   |
| Inhalte im Arbeitsbereich erstellen, bearbeiten und löschen.  |  X | X  | X  |   |
| Berichte im Arbeitsbereich veröffentlichen und Inhalt löschen.  |  X | X  | X  |   |
| Erstellen Sie einen Bericht in einem anderen Arbeitsbereich basierend auf einem Dataset in diesem Arbeitsbereich.<sup>1</sup> |  X | X  | X  |   |
| Kopieren Sie einen Bericht. | X | X | X |  |
| Anzeigen eines Elements und Interagieren mit einem Element.<sup>2</sup> |  X | X  | X  | X  |
| Lesen von in Arbeitsbereichs-Datenflüssen gespeicherten Daten | X | X | X | X |

1. Mitwirkende und Mitglieder können Elemente in einem Arbeitsbereich freigeben, wenn sie über die entsprechenden Berechtigungen für erneute Freigabe verfügen.

2. Auch wenn Sie nicht über eine Power BI Pro-Lizenz verfügen, können Sie Elemente im Power BI-Dienst anzeigen und mit ihnen interagieren, wenn sich die Elemente in einem Arbeitsbereich in einer Premium-Kapazität befinden.

## <a name="licensing-workspaces-and-capacity"></a>Lizenzierung, Arbeitsbereiche und Kapazität
Die Lizenzierung spielt auch eine Rolle bei der Bestimmung dessen, wofür Sie in einem Arbeitsbereich berechtigt sind und wofür nicht. Für viele Features ist für Benutzer eine Power BI *Pro*-Lizenz erforderlich. Die meisten *Consumer* arbeiten mit einer *Free*-Lizenz. 

Wenn Sie über eine Free-Lizenz verfügen und der Arbeitsbereich in einer *Premium-Kapazität* gespeichert ist, können Sie die Inhalte in diesem Arbeitsbereich anzeigen und mit ihnen interagieren. Arbeitsbereiche und Apps, die in einer Premium-Kapazität gespeichert sind, werden durch ein Diamantsymbol gekennzeichnet.

![Ausgewählte Option „Arbeitsbereiche“](media/end-user-workspaces/power-bi-diamond.png) Weitere Informationen finde Sie unter [Verwenden des Power BI-Diensts als Anwender](end-user-license.md).



## <a name="next-steps"></a>Nächste Schritte
* [Apps in Power BI](end-user-apps.md)    

* Haben Sie Fragen? [Stellen Sie Ihre Frage in der Power BI-Community.](https://community.powerbi.com/)

