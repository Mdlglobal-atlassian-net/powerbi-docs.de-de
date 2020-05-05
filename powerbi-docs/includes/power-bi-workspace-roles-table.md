---
title: Power BI-Arbeitsbereichsrollen
description: Tabelle mit Power BI-Arbeitsbereichsrollen
services: powerbi
author: maggiesMSFT
ms.service: powerbi
ms.topic: include
ms.date: 04/23/2020
ms.author: maggies
ms.custom: include file
ms.openlocfilehash: 9a6ca5abf3c26af876666ef45fe7ae192e69f2a3
ms.sourcegitcommit: 9ec2c608b90bf651df613f0714addd251a885039
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/24/2020
ms.locfileid: "82120347"
---
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
| Einen Bericht kopieren<sup>2</sup> | X | X | X |  |
| Ein Element anzeigen und mit ihm interagieren<sup>3</sup> |  X | X  | X  | X  |
| Lesen von in Arbeitsbereichs-Datenflüssen gespeicherten Daten | X | X | X | X |

1. Mitwirkende und Zuschauer können Elemente in einem Arbeitsbereich freigeben, wenn sie über die entsprechenden Berechtigungen verfügen.
2. Sie benötigen eine Erstellungsberechtigung für das Dataset, um einen Bericht zu kopieren und einen Bericht in einem anderen Arbeitsbereich basierend auf einem Dataset in diesem Arbeitsbereich zu erstellen. Für Datasets in diesem Arbeitsbereich haben die Personen mit den Rollen „Administrator“, „Mitglied“ und „Mitwirkender“ über ihre Arbeitsbereichsrolle die Erstellungsberechtigung.
3. Auch wenn Sie nicht über eine Power BI Pro-Lizenz verfügen, können Sie Elemente im Power BI-Dienst anzeigen und mit ihnen interagieren, wenn sich die Elemente in einem Arbeitsbereich in einer Premium-Kapazität befinden.

