---
title: Datenklassifizierung für Dashboards
description: Erfahren Sie mehr über die Datenklassifizierung für Dashboards. Hier erfahren Sie auch, wie diese von einem Administrator eingerichtet werden sollte und wie Eigentümer des Dashboards die Klassifizierung ändern können.
author: maggiesMSFT
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 08/10/2017
ms.author: maggies
LocalizationGroup: Dashboards
ms.openlocfilehash: b9aeb033586eaf5c0effd838626af6c877080f64
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/13/2020
ms.locfileid: "83322721"
---
# <a name="dashboard-data-classification"></a>Datenklassifizierung für Dashboards
Für jedes Dashboard bestehen andere Anforderungen. Je nach der Datenquelle, mit der Sie eine Verbindung herstellen, werden Sie wahrscheinlich feststellen, dass Sie und die Kollegen, für die Sie das Dashboard freigeben, abhängig von der Vertraulichkeit der Daten verschiedene Vorsichtsmaßnahmen treffen müssen. Einige Dashboards sollten niemals außerhalb Ihres Unternehmens freigegeben oder gedruckt werden, während andere ohne Bedenken freigegeben werden können. Mithilfe der Datenklassifizierung für Dashboards können Sie den Personen, von denen die Dashboards angezeigt werden, die Bestimmung der zu verwendenden Sicherheitsstufe erleichtern. Sie können die Dashboards mit Klassifizierungstags versehen, die von der IT-Abteilung Ihres Unternehmens definiert wurden, damit jede Person, die den Inhalt anzeigt, den gleichen Kenntnisstand hinsichtlich der Vertraulichkeit der Daten hat.

![](media/service-data-classification/dashboard_tagged_as_hbi.png)

## <a name="data-classification-tags"></a>Datenklassifizierungstags
Datenklassifizierungstags werden neben dem Namen des Dashboards angezeigt, sodass jede Person, die das Dashboard anzeigt, die auf das Dashboard anzuwendende Sicherheitsstufe kennt und weiß, welche Daten es enthält.

![](media/service-data-classification/tag_next_to_title.png)

Sie werden auch neben der Dashboardkachel in der Favoritenliste angezeigt.

![](media/service-data-classification/tag_on_dashboard_tile.png)

Wenn Sie auf das Tag zeigen, wird der vollständige Name der Klassifizierung angezeigt.

![](media/service-data-classification/tag_tooltip.png)

Administratoren können auch eine URL für ein Tag festlegen, um zusätzliche Informationen bereitzustellen.

> [!NOTE]
> Je nach den vom Administrator festgelegten Klassifizierungseinstellungen werden möglicherweise einige Klassifizierungstypen nicht als Tag auf dem Dashboard angezeigt. Wenn Sie Eigentümer eines Dashboards sind, können Sie immer unter den Dashboardeinstellungen den Dashboardklassifizierungstyp überprüfen.
> 
> 

## <a name="setting-a-dashboards-classification"></a>Festlegen der Klassifizierung eines Dashboards
Wenn Datenklassifizierung für Ihr Unternehmen aktiviert ist, verfügen alle Dashboards zunächst über einen Standardklassifizierungstyp. Als Eigentümer eines Dashboards können Sie jedoch die Klassifizierung ändern, damit sie mit der Sicherheitsstufe des Dashboards übereinstimmt.

Gehen Sie wie folgt vor, um den Klassifizierungstyp zu ändern:

1. Klicken Sie auf die **Auslassungspunkte** neben dem Dashboardnamen, und wählen Sie **Einstellungen** aus, um die Dashboardeinstellungen zu öffnen.
   
    ![](media/service-data-classification/dashboard_settings.png)
2. Unter den Dashboardeinstellungen wird die aktuelle Klassifizierung für das Dashboard angezeigt, und Sie können mithilfe der Dropdownliste den Klassifizierungstyp ändern.
   
    ![](media/service-data-classification/classification_setting_dropdown.png)
3. Wählen Sie **Anwenden** aus, wenn Sie den Vorgang abgeschlossen haben.

Nachdem Sie die Änderung angewendet haben, wird die Aktualisierung für jede Person, für die Sie das Dashboard freigegeben haben, beim nächsten Laden des Dashboards angezeigt.

## <a name="working-with-data-classification-tags-as-an-admin"></a>Arbeiten als Administrator mit Datenklassifizierungstags
Die Datenklassifizierung wird vom globalen Administrator für die Organisation eingerichtet. Gehen Sie wie folgt vor, um die Datenklassifizierung zu aktivieren:

1. Klicke Sie auf das Zahnradsymbol für die Einstellungen, und wählen Sie **Verwaltungsportal** aus.
   
    ![](media/service-data-classification/admin_portal_in_settings.png)
2. Legen Sie auf der Registerkarte **Mandanteneinstellungen** die Option *Datenklassifizierung für Dashboards und Berichte* auf **Ein** fest.
   
    ![](media/service-data-classification/data_classification_switch_location.png)

Wenn die Option aktiviert ist, wird ein Formular zum Erstellen der verschiedenen Klassifizierungen in der Organisation angezeigt.

![](media/service-data-classification/blank_classification_form.png)

Jede Klassifizierung verfügt über einen **Namen** und ein **Kompakttag**, das auf dem Dashboard angezeigt wird. Sie können für jede Klassifizierung durch Auswählen von **Tag anzeigen** festlegen, ob das Kompakttag auf dem Dashboard angezeigt wird. Wenn Sie festlegen, dass der Klassifizierungstyp nicht auf dem Dashboard angezeigt wird, kann der Eigentümer dennoch durch Überprüfen der Dashboardeinstellungen den Typ anzeigen. Optional können Sie zudem eine **URL** hinzufügen, die weitere Informationen über die Klassifizierungsrichtlinien und Verwendungsanforderungen der Organisation enthält.  

Als Letztes müssen Sie festlegen, welcher Klassifizierungstyp der Standardtyp ist.  

Nachdem Sie im Formular die Klassifizierungstypen festgelegt haben, wählen Sie **Anwenden** aus, um die Änderungen zu speichern.

![](media/service-data-classification/filled_in_classification_form.png)

An diesem Punkt wird allen Dashboards die Standardklassifizierung zugewiesen. Dashboardbesitzer können nun den Klassifizierungstyp auf den für ihren Inhalt geeigneten Klassifizierungstyp aktualisieren. Sie können in Zukunft an diese Stelle zurückkehren, um Klassifizierungstypen hinzuzufügen oder zu entfernen oder den Standardtyp zu ändern.  

> [!NOTE]
> Wenn Sie zurückkehren, um Änderungen vorzunehmen, sind einige wichtige Punkte zu beachten:
> 
> * Wenn Sie die Datenklassifizierung deaktivieren, wird keines der Tags gespeichert. Sie müssen von vorne beginnen, wenn Sie sie später wieder aktivieren möchten.  
> * Wenn Sie einen Klassifizierungstyp entfernen, werden alle Dashboards, die dem entfernten Klassifizierungstyp zugewiesen sind, wieder dem Standardklassifizierungstyp zugewiesen, bis der Klassifizierungstyp wieder vom Eigentümer festgelegt wird.  
> * Wenn Sie den Standardklassifizierungstyp ändern, wird allen Dashboards, denen vom Eigentümer noch kein Klassifizierungstyp zugewiesen wurde, der neue Standardklassifizierungstyp zugewiesen.
> 
> 

