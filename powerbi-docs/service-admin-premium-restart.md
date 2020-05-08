---
title: Neustarten einer Power BI Premium-Kapazität
description: Erfahren Sie, wie Sie eine Power BI Premium-Kapazität zum Beheben von Leistungsproblemen neu starten.
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 03/12/2020
LocalizationGroup: Premium
ms.openlocfilehash: ccc14cb041c5131d2cb06a8ad362b7054bcde857
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "80464692"
---
# <a name="restart-a-power-bi-premium-capacity"></a>Neustarten einer Power BI Premium-Kapazität

Als Power BI-Administrator müssen Sie eine Premium-Kapazität möglicherweise neu starten. In diesem Artikel wird erläutert, wie Sie eine Kapazität neu starten. Ferner wird auf einige Fragen zum Neustart und zur Leistung eingegangen.

## <a name="why-does-power-bi-provide-this-option"></a>Warum stellt Power BI diese Option bereit?

Power BI bietet Benutzern die Möglichkeit, komplexe Analysen großer Datenmengen auszuführen. Leider können Benutzer u. a. durch das Überladen des Power BI-Diensts mit Aufträgen, das Schreiben zu komplexer Abfragen und das Erstellen von Zirkelbezügen Leistungsprobleme verursachen.

Durch die gemeinsam genutzte Kapazität von Power BI wird durch das Festlegen von Grenzwerten für Dateigrößen, das Aktualisieren von Zeitplänen und weitere Aspekte des Diensts ein gewisser Schutz vor Fällen wie diesen geboten. In einer Power BI Premium-Kapazität werden hingegen die meisten dieser Grenzwerte angehoben. Infolgedessen kann ein einzelner Bericht mit einem ungültigen DAX-Ausdruck oder ein sehr komplexes Modell signifikante Leistungsprobleme verursachen. Der Bericht kann bei der Verarbeitung alle in der Kapazität verfügbaren Ressourcen nutzen. 

Power BI verbessert kontinuierlich den Schutz von Benutzern der Premium-Kapazität vor solchen Problemen. Auch Administratoren stehen Tools zur Verfügung, damit diese analysieren können, wann und aus welchem Grund Kapazitäten ausgelastet sind. Weitere Informationen finden Sie in unserer [kurzen Trainingssitzung](https://www.youtube.com/watch?v=UgsjMbhi_Bk&feature=youtu.be) und unserer [längeren Trainingssitzung](https://www.microsoft.com/businessapplicationssummit/video/BAS2018-2174). Gleichzeitig müssen Sie wesentliche Probleme entschärfen können, wenn diese auftreten. Die schnellste Möglichkeit zum Beheben dieser Probleme besteht in einem Neustart der Kapazität.

## <a name="is-the-restart-process-safe-will-i-lose-any-data"></a>Ist der Neustartprozess sicher? Gehen meine Daten verloren?

Alle gespeicherten Daten, Definitionen, Berichte und Dashboards in Ihrer Kapazität bleiben nach dem Neustart vollständig intakt. Wenn Sie eine Kapazität neu starten, werden aktuell ausgeführte geplante und Ad-hoc-Aktualisierungen in den meisten Fällen vorübergehend von der Aktualisierungs-Engine angehalten. Dann werden sie neu gestartet, basierend auf der in Power BI integrierten Logik für Aktualisierungs- bzw. Wiederholungsvorgänge. Der Dienst versucht, alle betroffenen Aktualisierungen neu auszuführen, sobald die Kapazität wieder verfügbar ist. Während dem Neustartprozess ändert sich der Aktualisierungstatus auf der Benutzeroberfläche möglicherweise nicht. 

Nicht gespeicherte von Benutzern vorgenommene Änderungen werden bei einem Neustartprozess nicht gespeichert. Benutzer sollten nach Abschluss des Neustarts ihren Browser aktualisieren.

## <a name="how-do-i-restart-a-capacity"></a>Wie starte ich eine Kapazität neu?

Führen Sie die folgenden Schritte aus, um eine Kapazität neu zu starten.

1. Navigieren Sie im Power BI-Verwaltungsportal auf der Registerkarte **Kapazitätseinstellungen** zu Ihrer Kapazität. 

1. Fügen Sie das **Featureflag** *CapacityRestart* zu Ihrer Kapazitäts-URL hinzu: `https://app.powerbi.com/admin-portal/capacities/<YourCapacityId>?capacityRestartButton=true`.

1. Wählen Sie unter **Erweiterte Einstellungen** > **CAPACITY RESTART** (Neustart der Kapazität) die Option **Restart capacity** (Kapazität neu starten) aus.

    ![Kapazität neu starten](media/service-admin-premium-restart/restart-capacity.png)

1. Wählen Sie im Dialogfeld **Capacity restart** (Neustart der Kapazität) den Eintrag **Yes, restart capacity** (Ja, Kapazität neu starten) aus.

    ![Neustart bestätigen](media/service-admin-premium-restart/confirm-restart.png)

## <a name="how-can-i-prevent-issues-from-happening-in-the-future"></a>Wie kann ich solche Probleme in Zukunft verhindern?

Sie können Probleme am besten verhindern, indem Sie die Benutzer über die effiziente Datenmodellierung informieren. Weitere Informationen finden Sie in unserer [Trainingssitzung](https://www.microsoft.com/businessapplicationssummit/video/BAS2018-2170).

Zudem wird Ihnen die [Überwachung Ihrer Kapazitäten](service-admin-premium-monitor-capacity.md) in regelmäßigen Zeitabständen empfohlen, um nach Trends zu suchen, die auf zugrunde liegende Probleme hinweisen. Für die Überwachungs-App und weitere Tools sind regelmäßige Releases geplant, damit Sie Ihre Kapazitäten effektiver überwachen und verwalten können.

## <a name="next-steps"></a>Weitere Schritte

[Was ist Power BI Premium?](service-premium-what-is.md)

Weitere Fragen? [Stellen Sie Ihre Frage in der Power BI-Community.](https://community.powerbi.com/)
