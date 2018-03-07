---
title: "Verwalten von Kapazitäten in Power BI Premium und Power BI Embedded"
description: "Erfahren Sie, wie Sie Power BI Premium verwalten und den Zugriff auf Inhalte für Ihre gesamte Organisation aktivieren können."
services: powerbi
documentationcenter: 
author: markingmyname
manager: kfile
backup: 
editor: 
tags: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 10/10/2017
ms.author: maghan
LocalizationGroup: Premium
ms.openlocfilehash: c94cbdbeaf6c7186b21a22c318a4195dbc509da3
ms.sourcegitcommit: 88c8ba8dee4384ea7bff5cedcad67fce784d92b0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/24/2018
---
# <a name="manage-capacities-within-power-bi-premium-and-power-bi-embedded"></a>Verwalten von Kapazitäten in Power BI Premium und Power BI Embedded
Hier erfahren Sie, wie Sie Power BI Premium- und Power BI Embedded-Kapazitäten verwalten können, um dedizierte Ressourcen für Ihre Inhalte bereitzustellen.

![Bildschirm für Power BI-Kapazitätseinstellungen](media/service-admin-premium-manage/premium-capacity-management.png)

Kapazität ist der Kern von Power BI Premium und Power BI Embedded.

## <a name="what-is-capacity"></a>Was ist Kapazität?
Kapazität bezeichnet die Gruppe von Ressourcen, die für die ausschließliche Verwendung durch Sie reserviert ist. Wenn Sie über Kapazität verfügen, können Sie Dashboards, Berichte und Datasets für Benutzer in Ihrer Organisation veröffentlichen, ohne Lizenzen für diese erwerben zu müssen. Außerdem gewährleistet sie eine zuverlässige, beständige Leistung für die in der Kapazität gehosteten Inhalte.

Kapazität ist für die Endbenutzer vollkommen transparent. Diese verwenden Power BI oder Ihre Anwendung weiterhin wie gewohnt. Die Endbenutzer müssen nicht wissen, dass Teile des Inhalts (oder der gesamte Inhalt) in Ihrer dedizierten Kapazität gehostet werden. Für Ihre Benutzer hat sich nichts verändert.

[!INCLUDE [powerbi-premium-illustration](./includes/powerbi-premium-illustration.md)]

Weitere Informationen finden Sie unter [What is Power BI Premium? (Was ist Power BI Premium?)](service-premium.md).

## <a name="purchase-capacity"></a>Erwerben von Kapazität
Damit Sie von dedizierter Kapazität profitieren können, müssen Sie im Office 365 Admin Center ein Abonnement von Power BI Premium erwerben oder im Microsoft Azure-Portal eine Power BI Embedded-Ressource erstellen. Weitere Informationen finden Sie in den folgenden Artikeln:

* **Power BI Premium:** [Erwerben von Power BI Premium](service-admin-premium-purchase.md)
* **Power BI Embedded:** demnächst verfügbar.

Wenn Sie Power BI Premium-SKUs erwerben, erhält Ihr Mandant die entsprechende Anzahl von V-Kernen zur Verwendung in Kapazitäten, die ausgeführt werden. Beispielsweise erhält der Mandant durch den Erwerb einer Power BI Premium P3-SKU 32 V-Kerne.

## <a name="capacity-admins"></a>Kapazitätsadministrator
> [!NOTE]
> Kapazitätsadministratoren für Power BI Embedded-Kapazität werden im Microsoft Azure-Portal definiert.
> 
> 

Wenn Sie einer Kapazität als Kapazitätsadministrator zugewiesen werden, haben Sie die volle Kontrolle über die Kapazität und deren Verwaltungsfeatures. Sie können über das Power BI-Verwaltungsportal weitere Kapazitätsadministratoren hinzufügen (nur in Power BI Premium) oder Benutzern Kapazitätszuweisungsberechtigungen erteilen. Sie können eine Massenzuweisung von Arbeitsbereichen zu einer Kapazität durchführen und sich Nutzungsmetriken einer Kapazität anzeigen lassen.

Jede Kapazität verfügt über ihre eigenen Administratoren. Wenn Sie einen Kapazitätsadministrator für eine Kapazität definieren, erhält dieser dadurch nicht Zugriff auf alle Kapazitäten in Ihrer Organisation. Kapazitätsadministratoren haben nicht standardmäßig Zugriff auf alle Power BI-Administrationsbereiche, z.B. Nutzungsmetriken, Überwachungsprotokolle oder Mandanteneinstellungen. Kapazitätsadministratoren sind auch nicht berechtigt, neue Kapazitäten einzurichten oder die SKU vorhandener Kapazitäten zu ändern. Nur globale Administratoren oder Power BI-Dienstadministratoren haben Zugriff auf diese Elemente.

Alle globalen Office 365-Administratoren und Power BI-Administratoren sind automatisch Kapazitätsadministratoren von Power BI Premium- und Power BI Embedded-Kapazität.

## <a name="managing-capacity"></a>Verwalten einer Kapazität
Nachdem Sie in Office 365 Kapazitätsknoten erworben haben, müssen Sie eine neue Kapazität einrichten. Dieser Vorgang wird über das [Power BI-Verwaltungsportal](service-admin-portal.md) ausgeführt. Im Verwaltungsportal gibt es den Bereich **Kapazitätseinstellungen**. Dort können Sie Premium-Kapazitäten Ihrer Organisation von Power BI verwalten.

![Kapazitätseinstellungen im Verwaltungsportal](media/service-admin-premium-manage/admin-portal-premium.png)

Durch Auswahl von **Kapazitätseinstellungen** gelangen Sie zum Kapazitätsverwaltungsbildschirm für Power BI Premium.

### <a name="setting-up-a-new-capacity-power-bi-premium"></a>Einrichten einer neuen Kapazität (Power BI Premium)
Die Anzahl der verwendeten und die Anzahl der zum Erstellen von Kapazitäten verfügbaren V-Kerne werden angezeigt. Die Anzahl der für Ihre Organisation verfügbaren V-Kerne basiert auf den Premium-SKUs, die Sie erworben haben. Wenn Sie beispielsweise eine P3- und eine P2-SKU erwerben, sind 48 Kerne verfügbar – 32 aus P3 und 16 aus P2.

![Verwendete und verfügbare V-Kerne für Power BI Premium](media/service-admin-premium-manage/admin-portal-v-cores.png)

Wenn Sie verfügbare V-Kerne haben, können Sie Ihre neue Kapazität mit den folgenden Schritten einrichten.

1. Klicken Sie auf **Set up new capacity** (Neue Kapazität einrichten).
2. **Benennen** Sie Ihre Kapazität.
3. Legen Sie einen Kapazitätsadministrator fest.
   
    Kapazitätsadministratoren müssen nicht Administratoren von Power BI oder globale Administratoren von Office 365 sein. Weitere Informationen finden Sie unter [Power BI Premium capacity admins (Kapazitätsadministratoren von Power BI Premium)](#capacity-admins).
4. Wählen Sie den Kapazitätsumfang aus. Die verfügbaren Optionen hängen von der Anzahl der verfügbaren V-Kerne ab. Sie können keine Option mit einer Anzahl wählen, die größer als die verfügbare Anzahl ist.
   
    ![Verfügbare Premium-Kapazitätsumfänge](media/service-admin-premium-manage/premium-capacity-size.png)
5. Klicken Sie auf **Einrichten**.

![Einrichten einer neuen Kapazität](media/service-admin-premium-manage/set-up-capacity.png)

Die Kapazität wird Kapazitätsadministratoren sowie Administratoren von Power BI und globale Administratoren von Office 365 im Verwaltungsportal angezeigt.

### <a name="capacity-settings"></a>Kapazitätseinstellungen
Sie können auf der Verwaltungsseite für Premium-Kapazitäten unter „Actions“ (Aktionen) auf das **Zahnradsymbol (Einstellungen)** klicken. Dort können Sie eine Kapazität umbenennen oder löschen. Außerdem können Sie die jeweiligen Dienstadministratoren, die SKU/Größe und Region der Kapazität sehen.

![Kapazitätsaktionen im Kapazitätsverwaltungsbereich](media/service-admin-premium-manage/capacity-actions.png)

![Kapazitätseinstellungen](media/service-admin-premium-manage/capacity-settings.png)

![Schaltflächen zum Löschen und Anwenden für Kapazitätseinstellungen in Power BI Premium](media/service-admin-premium-manage/capacity-settings-delete.png)

> [!NOTE]
> Power BI Embedded-Kapazitätseinstellungen werden im Microsoft Azure-Portal verwaltet.
> 
> 

### <a name="change-capacity-size-power-bi-premium"></a>Ändern des Kapazitätsumfangs (Power BI Premium)
Power BI-Administratoren und globale Office 365-Administratoren ändern den Power BI Premium-Kapazitätsumfang, indem sie **Kapazitätsumfang ändern** auswählen. Kapazitätsadministratoren, die keine Power BI- oder globale Office 365-Administratoren sind, verfügen nicht über diese Option.

![Ändern des Power BI Premium-Kapazitätsumfangs](media/service-admin-premium-manage/change-capacity-size.png)

Im Bildschirm **Kapazitätsumfang ändern** können Sie ein Upgrade oder Downgrade des Kapazitätsumfangs ausführen, wenn die entsprechenden Ressourcen verfügbar sind. Administratoren können Knoten erstellen, löschen und ihre Größe ändern, solange sie über die erforderliche Anzahl von V-Kernen verfügen. 

P-SKUs können nicht auf EM-SKUs herabgestuft werden. Sie können auf deaktivierte Optionen zeigen, um ihre Erläuterung anzuzeigen.

![Dropdownliste zum Ändern des Power BI Premium-Kapazitätsumfangs](media/service-admin-premium-manage/change-capacity-size2.png)

### <a name="capacity-assignment"></a>Kapazitätszuweisung
Sie können eine Kapazität verwalten, indem Sie deren Namen auswählen. Dadurch werden Sie zur Kapazitätsverwaltungsseite weitergeleitet.

![Auswählen des Kapazitätsnamens, um den Bildschirm für die Kapazitätszuweisung zu öffnen](media/service-admin-premium-manage/capacity-assignment.png)

Wenn der Kapazität keine Arbeitsbereiche zugewiesen wurden, wird die Meldung **Arbeitsbereiche zuweisen** angezeigt.

#### <a name="user-permissions"></a>Benutzerberechtigungen
Sie können zusätzliche **Kapazitätsadministratoren** für Power BI Premium-Kapazitäten zuweisen sowie Benutzer mit Berechtigung zur **Kapazitätszuweisung**. Benutzer mit Zuweisungsberechtigung können einer Kapazität einen App-Arbeitsbereich zuweisen, wenn sie ein Administrator dieses Arbeitsbereichs sind. Außerdem können sie der Kapazität ihren persönlichen Arbeitsbereich (*Mein Arbeitsbereich*) zuweisen. Benutzer mit Zuweisungsberechtigung haben keinen Zugang zum Verwaltungsportal.

> [!NOTE]
> Kapazitätsadministratoren für Power BI Embedded-Kapazität werden im Microsoft Azure-Portal zugewiesen.
> 
> 

![](media/service-admin-premium-manage/capacity-user-permissions.png)

![](media/service-admin-premium-manage/capacity-user-permissions2.png)

## <a name="usage-measurements-power-bi-premium"></a>Nutzungsmessungen (Power BI Premium)
Sie können für jede Kapazität Nutzungsmessungen der CPU, des Arbeitsspeichers und der direkten Abfragen vornehmen. Jeder KPI hat drei Anzeigemöglichkeiten, **Gut (grün)**, **Grenzwertig (gelb)** und **Kritisch (rot)**. Es wird empfohlen, dass Sie diese Metriken überwachen, um sicherzustellen, dass Ihre Benutzer beim Verwenden von Premiuminhalt mit der Leistung zufrieden sind.

**Die Power BI Embedded-Kapazitätsauslastung wird im Azure-Portal überwacht.**

![](media/service-admin-premium-manage/usage-metrics-critical.png "Metriken zur Kapazitätsauslastung – Kritisch")

| Metrik | Beschreibung |
| --- | --- |
| CPU |CPU-Auslastung Ihrer Kernspeicher |
| Arbeitsspeicher |Zeigt die Speicherauslastung Ihrer Back-End-Kernspeicher. Dies ist insbesondere eine Metrik darüber, wie oft Modelle aufgrund von hoher Speicherauslastung durch das Verwenden mehrerer Modelle aus dem Arbeitsspeicher entfernt werden. |
| DQ/s |* Die Gesamtzahl von Abfragen mit DirectQuery und Liveverbindungen pro Sekunde ist eingeschränkt.<br/>* Die Grenzwerte betragen 30/s für P1, 60/s für P2 und 120/s für P3.<br/>* Abfragen mit DirectQuery und Liveverbindungen zählen in die oben stehende Begrenzung gleichermaßen hinein. Wenn Sie z.B. 15 direkte Abfragen und 15 Liveverbindungen in einer Sekunde haben, ist die Begrenzung erreicht.<br/>* Dies gilt sowohl für lokale als auch Cloudverbindungen. |

Wenn diese Metriken grenzwertig/kritisch sind, bemerken Ihre Benutzer möglicherweise einen Verlust der Leistung beim Berichten und Aktualisieren, insbesondere bei Spitzen in den Ladezeiten.

Metriken spiegeln die Auslastung in der letzten Woche wieder. Sie wurden dazu entwickelt, Ihre Instanzen zu zählen, wenn die Kapazität überladen ist. Deshalb bieten sie Ihren Benutzern eine nicht optimale Leistung.

Jedes Vorkommen von *Auslastung über 80 %* sollte als möglicher Grund für einen Leistungsverlust behandelt werden. Wenn dies zu oft vorkommt, ist dies ein deutlicher Hinweis auf erhebliche Probleme in der Leistung für die Benutzer.

## <a name="assign-a-workspace-to-a-capacity"></a>Zuweisen eines Arbeitsbereichs zu einer Kapazität
Sie haben mehrere Möglichkeiten, einer Kapazität einen Arbeitsbereich zuzuweisen.

### <a name="capacity-management-in-admin-portal"></a>Verwaltung von Kapazitäten im Verwaltungsportal
Kapazitätsadministratoren können, genauso wie Administratoren von Power BI und globale Administratoren von Office 365, Massenzuweisungen von Arbeitsbereichen im Verwaltungsbereich für Premium-Kapazitäten im Verwaltungsportal durchführen. Beim Verwalten einer Kapazität wird Ihnen der Bereich **Workspaces** (Arbeitsbereiche) angezeigt, in dem Sie Arbeitsbereiche zuweisen können.

![Bereich für die Zuweisung von Arbeitsbereichen in der Kapazitätsverwaltung](media/service-admin-premium-manage/capacity-manage-workspaces.png)

1. Klicken Sie auf **Arbeitsbereiche zuweisen**. Dies wird an mehreren Stellen angezeigt und führt die gleiche Aufgabe durch.
2. Klicken Sie entweder auf **The entire organization's workspaces** (Arbeitsbereiche der gesamten Organisation) oder auf **Specific workspaces by user** (Bestimmte Arbeitsbereiche nach Benutzer).
   
   | Auswahl (Selection) | Beschreibung |
   | --- | --- |
   | **Arbeitsbereiche der gesamten Organisation** |Wenn Sie die Arbeitsbereiche der gesamten Organisation einer Premium-Kapazität zuweisen, werden alle App-Arbeitsbereiche und Meine Arbeitsbereiche, die sich in Ihrer Organisation befinden, dieser Premium-Kapazität zugewiesen. Des Weiteren erhalten alle aktuellen und zukünftigen Benutzer die Berechtigung, einzelne Arbeitsbereiche erneut dieser Kapazität zuzuweisen. |
   | **Bestimmte Arbeitsbereiche nach Benutzer** |Wenn Sie Ihre Arbeitsbereiche nach Benutzern oder Gruppen zuweisen, werden alle Arbeitsbereiche dieses Benutzers einer Premium-Kapazität zugewiesen, einschließlich seiner der persönlichen Arbeitsbereiche. Diese Benutzer erhalten automatisch Berechtigung zur Zuweisung von Arbeitsbereichen.<br>Dies gilt auch für Arbeitsbereiche, die bereits einer anderen Kapazität zugewiesen wurden. |
3. Klicken Sie auf **Übernehmen**.

Mit dieser Option können Sie einer Kapazität keine bestimmten Arbeitsbereiche zuweisen.

### <a name="app-workspace-settings"></a>Einstellungen von App-Arbeitsbereichen
Sie können einer Premium-Kapazität auch einen App-Arbeitsbereich über die Einstellungen dieses Arbeitsbereichs zuweisen. Um einer Premium-Kapazität einen App-Arbeitsbereich zuzuweisen, führen Sie folgende Schritte durch.

Um einen Arbeitsbereich in eine Kapazität zu verschieben, müssen Sie über Administratorberechtigungen für diesen Arbeitsbereich verfügen sowie über Berechtigungen zu Kapazitätszuweisung für diese Kapazität. Beachten Sie, dass Arbeitsbereichsadministratoren einen Arbeitsbereich jederzeit aus einer Premium-Kapazität entfernen können.

1. Sie können einen App-Arbeitsbereich bearbeiten, indem Sie auf die **Auslassungspunkte (...)** und dann auf **Edit workspace** (Arbeitsbereich bearbeiten) klicken.
   
    ![Bearbeiten des Arbeitsbereichs über das Kontextmenü mit den Auslassungspunkten](media/service-admin-premium-manage/edit-app-workspace.png)
2. Erweitern Sie unter **Edit workspace** (Arbeitsbereich bearbeiten) **Erweitert**.
3. Wenn Ihnen die Berechtigung zur Kapazitätszuweisung für eine Kapazität erteilt wurde, haben Sie die Option, **Premium** für diesen Arbeitsbereich zu aktivieren.
4. Wählen Sie die Kapazität aus, die Sie diesem App-Arbeitsbereich zuweisen möchten.
   
    ![Dropdownliste für die Kapazitätsauswahl](media/service-admin-premium-manage/app-workspace-advanced.png)
5. Wählen Sie **Speichern**.

Sobald Sie die Änderungen speichern, wird der Arbeitsbereich mitsamt seinen Inhalten in die Premium-Kapazität verschoben, ohne dass die Benutzererfahrung der Endbenutzer beeinträchtigt wird.

## <a name="what-premium-looks-like-for-users"></a>So sieht Premium für Benutzer aus
Meistens ist es nicht vonnöten, dass Benutzern überhaupt bewusst ist, dass sie sich in einer Premium-Kapazität befinden. Die Dashboards und Berichte der Benutzer funktionieren einfach wie gewohnt. Arbeitsbereiche, die sich in einer Premium-Kapazität befinden, sind durch ein Diamantsymbol optisch markiert. 

![Raute, die angibt, dass der Arbeitsbereich zu einer Premium-Kapazität gehört](media/service-admin-premium-manage/premium-workspace.png)

## <a name="power-bi-report-server-product-key"></a>Product Key für den Power BI-Berichtsserver
Auf der Registerkarte **Kapazitätseinstellungen** im Verwaltungsportal von Power BI haben Sie Zugang zum Product Key für den Power BI-Berichtsserver. Dieser steht nur globalen Administratoren oder Benutzern zur Verfügung, denen die Administratorrolle für den Power BI-Dienst zugewiesen wurde. Voraussetzung ist außerdem, dass Sie eine Power BI Premium-SKU erworben haben.

![Schlüssel für den Power BI-Berichtsserver in den Kapazitätseinstellungen](media/service-admin-premium-manage/pbirs-product-key.png)

Wenn Sie auf **Power BI Report Server key** (Schlüssel für den Power BI-Berichtsserver) klicken, wird ein Dialogfeld mit Ihrem Product Key angezeigt. Diesen können Sie kopieren und bei der Installation verwenden.

![Product Key für den Power BI-Berichtsserver](media/service-admin-premium-manage/pbirs-product-key-dialog.png)

Weitere Informationen finden Sie unter [Install Power BI Report Server (Installation vom Power BI-Berichtsserver)](report-server/install-report-server.md).

## <a name="next-steps"></a>Nächste Schritte
Geben Sie veröffentlichte Apps für Free-Benutzer frei, wenn Sie den Arbeitsbereich einer Premium-Kapazität zuweisen. Weitere Informationen finden Sie unter [Erstellen und Verteilen einer App in Power BI](service-create-distribute-apps.md).

Weitere Fragen? [Stellen Sie Ihre Frage in der Power BI-Community.](http://community.powerbi.com/)
