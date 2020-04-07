---
title: Lizenzoptionen für Power BI-Benutzer
description: Informationen zu den verschiedenen Lizenzoptionen und zu den Möglichkeiten herauszufinden, welche Lizenz Sie haben
author: mihart
ms.reviewer: lukasz
ms.custom: ''
ms.service: powerbi
ms.subservice: powerbi-consumer
ms.topic: how-to
ms.date: 03/25/2020
ms.author: mihart
LocalizationGroup: consumers
ms.openlocfilehash: 42417f272f1331c2ca5144978bb92ca189a13f93
ms.sourcegitcommit: bcc42e938fa28abe433287fecb9abb28c253b6bb
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/26/2020
ms.locfileid: "80302430"
---
# <a name="types-of-power-bi-licenses"></a>Lizenzoptionen für Power BI

[!INCLUDE[consumer-appliesto-ynnn](../includes/consumer-appliesto-ynnn.md)]

*Benutzer* verwenden den Power BI-Dienst zum Analysieren von Berichten und Dashboards, um fundierte Entscheidungen für ihr Unternehmen zu treffen. Wenn Sie schon Erfahrung im Umgang mit Power BI haben oder sich mit den *Designern* in Ihrem Unternehmen über dieses Tool unterhalten haben, ist Ihnen möglicherweise schon aufgefallen, dass es einige Features gibt, die nur mit bestimmten Lizenzen oder Abonnements funktionieren. 

In diesem Artikel werden die Unterschiede der folgenden Benutzerlizenzen und Organisationsabonnements sowie ihr kombinierter Einsatz erläutert: Free, Pro, Premium und Premium-Kapazität. Außerdem erfahren Sie, wie Sie herausfinden können, welche Lizenz- und Abonnementkombination Sie verwenden.  

![Diagramm, das zeigt, wie Lizenzen verbunden sind](media/end-user-license/power-bi-venn.png)

Zunächst werden die beiden verfügbaren Lizenzkategorien thematisiert: Benutzer- und Organisationsabonnements. Unser Ausgangspunkt sind die jeweils verfügbaren Standardfunktionen. Dann sehen wir uns an, wie der Power BI-Administrator und die Inhaltsbesitzer Rollen und Berechtigungen dazu nutzen können, die standardmäßig festgelegten Lizenz- und Abonnementfunktionen zu ändern. 

Beispiel: Auch wenn Ihre Lizenz bestimmte Aufgaben zulässt, wie den Export von Daten, Abfragen in natürlicher Sprache oder Veröffentlichung im Internet, kann Ihr Administrator Ihre Möglichkeiten einschränken. Wenn ein *Berichts-Designer* einem [Arbeitsbereich](end-user-workspaces.md) Inhalte zuweist, kann er Ihnen zudem eine Arbeitsbereichsrolle zuweisen. Die Rollen bestimmen, was Sie in diesem Arbeitsbereich tun können und was nicht. Der *Designer* kann die Grenzen Ihrer Lizenz mithilfe von Berechtigungseinstellungen weiter anpassen. Das ist alles gar nicht so einfach. Hoffentlich wird dieser Artikel die meisten, wenn nicht sogar alle Unklarheiten beseitigen.

## <a name="per-user-licenses"></a>Benutzerlizenzen
Der erste Lizenztyp ist eine **Benutzerlizenz**. Jeder Power BI-Dienstbenutzer verfügt entweder über eine Free- oder Pro-Lizenz. Bestimmte Features sind für Benutzer mit Pro-Lizenz reserviert.  

- Benutzer mit einer **Power BI Pro-Lizenz (ohne Premium-Abonnement)** können mit anderen Pro-Benutzern zusammenarbeiten, indem sie Inhalte erstellen und freigeben. Nur Benutzer mit einer Pro-Lizenz können Berichte veröffentlichen, Dashboards und Berichte abonnieren und mit Kollegen in Arbeitsbereichen zusammenarbeiten. 

    ![Abbildung von Pro-Benutzern](media/end-user-license/power-bi-pro.jpg)

    Power BI Pro wird als Einzelbenutzerlizenz bereitgestellt, die Benutzern das Lesen von und Interagieren mit Berichten und Dashboards ermöglicht, die andere im Power BI-Dienst veröffentlicht haben. Benutzer mit diesem Lizenztyp können Inhalte freigeben und mit anderen Power BI Pro-Benutzern zusammenarbeiten. Nur Power BI Pro-Benutzer können Inhalte veröffentlichen oder für andere Benutzer freigeben und Inhalte nutzen, die von anderen Benutzern erstellt wurden. Es sei denn, diese Inhalte werden in [Power BI Premium-Kapazität](#understanding-premium-and-premium-capacity) gehostet. (Weitere Informationen finden Sie unter [Power BI Premium-Kapazität](#understanding-premium-and-premium-capacity) weiter unten.) Pro-Lizenzen werden in der Regel von *Berichts-Designern* und Entwicklern verwendet. 


- **Eigenständige Power BI Free-Lizenzen (ohne Premium-Abonnement)** sind zwar auch sehr nützlich, eignen sich aber eher für die Einarbeitung in Power BI oder für Benutzer, die nur Inhalte für den eigenen Bedarf erstellen. Weitere Informationen finden Sie unter [ Registrieren für Power BI als Einzelperson](../service-self-service-signup-for-power-bi.md).   

    Eigenständige Benutzerlizenzen im Free-Tarif eignen sich ausgezeichnet für Benutzer, die Beispiele von Microsoft verwenden, um Power BI kennenzulernen. Benutzer mit eigenständiger Free-Lizenz können keine von anderen Benutzern freigegebenen Inhalte abrufen oder ihre eigenen Inhalte mit anderen Power BI-Benutzern teilen. 

    ![Abbildung eigenständiger Benutzer](media/end-user-license/power-bi-free-license.jpg)

    Alle Kunden mit einer eigenständigen Free-Lizenz können ein Upgrade auf eine [kostenlose Power BI Pro-Testlizenz](../service-self-service-signup-for-power-bi.md) durchführen. Die Testversion bietet Ihnen die gesamte Leistung und Funktionalität einer Power BI Pro-Benutzerlizenz.

    ![Einladung zum Ausführen der Pro-Testversion](media/end-user-license/power-bi-pro-trial.png)

- **Power BI Free-Lizenzen mit Premium-Abonnement**: Wenn eine Organisation über ein Premium-Abonnement verfügt, können Administratoren und Pro-Benutzer in *Premium-Kapazität* Arbeitsbereiche zuweisen und Free-Benutzern den Zugriff auf diese Arbeitsbereiche gewähren. Ein Arbeitsbereich in einer Premium-Kapazität ist ein Bereich, in dem Pro-Benutzer mit Free-Benutzern zusammenarbeiten und Informationen austauschen können, ohne dass die Free-Benutzer über Pro-Konten verfügen müssen. Innerhalb dieser Arbeitsbereiche verfügen Free-Benutzer über erweiterte Berechtigungen. Sie können zusammenarbeiten und Elemente freigeben, Daten exportieren, Inhalte abonnieren, mit Filtern interagieren und vieles mehr. 

Ist das soweit verständlich?  OK. Sehen wir uns das **Premium-Kapazität**-Konzept genauer an.

## <a name="understanding-premium-and-premium-capacity"></a>Grundlegendes zu Premium und Premium-Kapazität
Premium ist ein **Organisationsabonnement**. Stellen Sie sich für Premium vor, Sie fügen allen Power BI- **Benutzerlizenzen** in einer Organisation eine Ebene zusätzlicher Features und Funktionen hinzu. 

Wenn eine Organisation eine Premium-Lizenz erwirbt, weist der Administrator in der Regel allen Mitarbeitern, die Inhalte erstellen und freigeben, eine Pro-Lizenz zu. Außerdem weist der Administrator allen Benutzern, die die Inhalte verwenden, Free-Lizenzen zu. Die Pro-Benutzer erstellen [App-Arbeitsbereiche](end-user-workspaces.md) und fügen diesen Arbeitsbereichen Inhalte (Dashboards, Berichte, Apps) hinzu. Damit Free-Benutzer in diesen Arbeitsbereichen zusammenarbeiten können, speichert der Administrator oder Pro-Benutzer die Arbeitsbereiche in *Premium-Kapazität*. 

Wenn eine Organisation eine Premium-Lizenz erwirbt, wird ihr im Power BI-Dienst Kapazität exklusiv zugeteilt. Sie wird nicht von anderen Organisationen verwendet. Die Kapazität wird von dedizierter Hardware unterstützt, die von Microsoft vollständig verwaltet wird. Organisationen können wählen, ob sie die ihnen zugewiesene Kapazität auf breiter Basis nutzen oder ob sie bestimmten Arbeitsbereichen zuteilen. In einer Organisation können einer Kapazität alle Arbeitsbereiche oder nur eine Auswahl von Arbeitsbereichen zugewiesen sein. Sie können der Premium-Kapazität zugewiesene Arbeitsbereiche am Rautensymbol erkennen. ![Rautensymbol](media/end-user-license/power-bi-diamond.png).  Ein Arbeitsbereich in einer Premium-Kapazität ist ein Bereich, in dem Pro-Benutzer mit Free-Benutzern zusammenarbeiten und Informationen austauschen können, ohne dass die Free-Benutzer über Pro-Konten verfügen müssen. 

In Premium-Kapazität sind für Inhaltsdesigner weiterhin Pro-Lizenzen erforderlich. Designer erstellen App-Arbeitsbereiche, stellen Verbindungen mit Datenquellen her, modellieren Daten und erstellen Berichte und Dashboards, die direkt freigegeben oder verpackt und als Apps freigegeben werden. Benutzer ohne Pro-Lizenz können weiter auf einen App-Arbeitsbereich zugreifen, der sich in Power BI Premium befindet, solange sich dieser Arbeitsbereich in Premium-*Kapazität* befindet und der Besitzer des Arbeitsbereichs ihnen die Berechtigung dafür erteilt.

In der Abbildung unten stellt die linke Seite Pro-Benutzer dar, die Inhalte in App-Arbeitsbereichen erstellen und freigeben. 

- **Arbeitsbereich A** wurde in einer Organisation erstellt, die über kein Premium-Abonnement verfügt. 

- **Arbeitsbereich B** wurde in einer Organisation erstellt, die über ein Premium-Abonnement verfügt, obwohl dieser spezielle Arbeitsbereich nicht in Premium-Kapazität gespeichert wurde. Der Arbeitsbereich weist nicht das Diamantsymbol auf.

- **Arbeitsbereich C** wurde in einer Organisation mit Premium-Abonnement erstellt und in der Premium-Kapazität gespeichert. Dieser Arbeitsbereich weist ein Diamantsymbol auf.  

![Abbildung von Pro-Benutzern](media/end-user-license/power-bi-sharing-scenarios.jpg)

Der Power BI Pro-*Designer* kann mit anderen Pro-Benutzern, die einen der drei Arbeitsbereiche verwenden, zusammenarbeiten und Informationen mit ihnen teilen. Dies gilt, solange der Designer den Arbeitsbereich mit der gesamten Organisation gemeinsam nutzt oder den Pro-Benutzern Arbeitsbereichsrollen zuweist. 

Der Power BI Pro-Benutzer kann nur mit Free-Benutzern, die Arbeitsbereich C nutzen, zusammenarbeiten und Informationen teilen. Der Arbeitsbereich muss der Premium-Kapazität zugewiesen werden, damit Free-Benutzer auf den Arbeitsbereich zugreifen können. Innerhalb des Arbeitsbereichs weist der Designer den Beteiligen Rollen zu: *Administrator*, *Mitglied*, *Mitwirkender* oder *Anzeigender Benutzer*. Ihre Rolle bestimmt, welche Aktionen in Ihrem Arbeitsbereich möglich sind. Power BI-*Consumern* wird in der Regel die Rolle *Anzeigender Benutzer* zugewiesen. Weitere Informationen finden Sie unter [Arbeitsbereiche für Power BI-Consumer](end-user-workspaces.md).

## <a name="find-out-which-license-and-subscription-you-have"></a>Ermitteln Ihrer Lizenz und Ihres Abonnements
Es gibt mehrere Möglichkeiten, die Informationen zu Ihrer Power BI-Lizenz und zu Ihrem Abonnement abzurufen. 

Finden Sie zunächst heraus, welche **Benutzerlizenz** Ihnen zugewiesen ist.

- Bestimmte Versionen von Microsoft Office umfassen eine Power BI Pro-Lizenz.  Sie können herausfinden, ob Ihre Office-Version Power BI umfasst, indem Sie das [Office-Portal](https://portal.office.com/account) aufrufen und auf **Abonnements** klicken.

    Der erste Benutzer, Pradtanna, verfügt über eine Office 365 E5-Lizenz, die eine Power BI Pro-Lizenz umfasst.

    ![Registerkarte „Abonnements“ im Office-Portal](media/end-user-license/power-bi-license-office.png)

    Dieser zweite Benutzer, Zalan, verfügt über eine Power BI Free-Lizenz. 

    ![Registerkarte „Abonnements“ im Office-Portal](media/end-user-license/power-bi-license-free.png)

Überprüfen Sie als Nächstes, ob Ihr Konto auch zu einem Premium-Abonnement gehört. Alle oben genannten Benutzer, egal ob im Pro- oder im Free-Tarif, können einer Organisation mit Premium-Lizenz angehören.  Sehen wir uns den zweiten Benutzer, Zalan, genauer an.  

- Klicken Sie im Power BI-Dienst erst auf **Mein Arbeitsbereich** und dann in der oberen rechten Ecke auf das Zahnradsymbol. Klicken Sie auf **Persönlichen Speicher verwalten**.

    ![Anzeige des Einstellungsmenüs](media/end-user-license/power-bi-license-personal.png)

    Allen **Benutzerlizenzen**, ob im Pro- oder Free-Tarif, stehen 10 GB Speicherplatz in der Cloud zur Verfügung, der zum Hosten von Power BI-Berichten und Excel-Arbeitsmappen verwendet werden kann. Wenn mehr als 10 GB angezeigt werden, sind Sie Mitglied eines Organisationskontos mit Premium-Lizenz.

    ![Verwalten eines Speichers mit 100 GB](media/end-user-license/power-bi-free-capacity.png)

    Zur Erinnerung: Wir haben auf der Seite des Office-Portals herausgefunden, dass Zalan eine Benutzerlizenz für Power BI Free hat. Aber da seine Organisation ein Premium-Abonnement erworben hat, ist Zalan im Power BI-Dienst nicht auf 10 GB Speicher beschränkt, sondern kann 100 GB nutzen. Als *Consumer* in einer Organisation mit Premium-Lizenz hat Zalan, solange der *Designer* den Arbeitsbereich in Premium-Kapazität platziert, die Möglichkeit, freigegebene Inhalte anzuzeigen, mit Kollegen zusammenzuarbeiten, mit Apps zu arbeiten und vieles mehr. Der Berechtigungsumfang wird vom Power BI-Administrator und Inhaltsdesigner festgelegt. Beachten Sie, dass ein Pro-Benutzer bereits einen Arbeitsbereich für Zalan freigegeben hat. Das Diamantsymbol informiert ihn, dass dieser Arbeitsbereich in Premium-Kapazität gespeichert ist. 

   
## <a name="understanding-workspace-roles"></a>Grundlegendes zu Arbeitsbereichsrollen
Bislang haben wir Benutzerlizenzen, Premium-Abonnements, App-Arbeitsbereiche und die Premium-Kapazität kennengelernt. Als Nächstes beschäftigen wir uns mit *Arbeitsbereichsrollen*.

Da sich dieser Artikel an Power BI-*Consumer* richtet, haben wir folgendes Szenario:

-  Sie sind ein *Free*-Benutzer in einer Organisation mit Power BI Premium-Abonnement. 
- Ein Power BI Pro-Benutzer hat eine Sammlung von Dashboards und Berichten erstellt und diese Sammlung für Ihre gesamte Organisation als *App* veröffentlicht.  
- Apps befinden sich in *Arbeitsbereichen* und diese wiederum in der Premium-Kapazität.    
- Dieser App-Arbeitsbereich enthält ein Dashboard und zwei Berichte.
- Der Pro-Benutzer hat uns die Rolle **Anzeigender Benutzer** zugewiesen.

### <a name="the-viewer-role"></a>Die Rolle „Anzeigender Benutzer“
Mit Rollen können Power BI-*Designer* verwalten, wer was in einem Arbeitsbereich erledigen darf, sodass Teams zusammenarbeiten können. Eine dieser Rollen ist **Anzeigender Benutzer**. 

Wenn sich der Arbeitsbereich in einer Power BI Premium-Kapazität befindet, können Benutzer mit der Rolle „Anzeigender Benutzer“ auch dann auf den Arbeitsbereich zugreifen, wenn sie keine Power BI Pro-Lizenz besitzen. Da die Rolle „Anzeigender Benutzer“ jedoch nicht auf die zugrunde liegenden Daten zugreifen oder diese exportieren kann, lässt sich auf diese Weise sicher mit Dashboards, Berichten und Apps interagieren.

> [!TIP]
> Weitere Informationen zu den anderen Rollen (Administrator, Mitglied und Mitwirkender) finden Sie unter [Erstellen eines neuen Arbeitsbereichs](../service-new-workspaces.md).

## <a name="next-steps"></a>Nächste Schritte
[Bin ich ein Power BI-*Benutzer*?](end-user-consumer.md)    
[Weitere Informationen zu Arbeitsbereichen](end-user-workspaces.md)    
<!--[View Power BI features by license type](end-user-features.md) -->

