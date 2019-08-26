---
title: Erstellen von klassischen Arbeitsbereichen in Power BI
description: Informationen zum Erstellen von Arbeitsbereichen, Sammlungen von Dashboards, Berichten und paginierten Berichten, die zum Bereitstellen von Schlüsselmetriken für Ihre Organisation konzipiert wurden.
author: maggiesMSFT
manager: kfile
ms.reviewer: lukaszp
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 08/12/2019
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: 0bb8d796af5139cd89f4bdfa0a8da10603acb2ed
ms.sourcegitcommit: 4d5166944fcc6fe4666cab055ae75e7a0a77866d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/16/2019
ms.locfileid: "69530560"
---
# <a name="create-classic-workspaces-in-power-bi"></a>Erstellen von klassischen Arbeitsbereichen in Power BI

In Power BI können Sie *Arbeitsbereiche* erstellen, um in Zusammenarbeit mit Kollegen Sammlungen von Dashboards, Berichten und paginierten Berichten zu erstellen und zu verfeinern. Anschließend können Sie die Sammlung in *Apps* bündeln, die Sie an Ihre gesamte Organisation oder an bestimmte Personen oder Gruppen verteilen können. 

**Wussten Sie schon?** Power BI bietet einen neuen Arbeitsbereich, der nun standardmäßig eingestellt ist. Weitere Informationen zu den neuen Arbeitsbereichen finden Sie unter [Organisieren Ihrer Arbeit in den neuen Arbeitsbereichen](service-new-workspaces.md). 

Wenn Sie einen klassischen Arbeitsbereich erstellen, erstellen Sie eine zugrunde liegende, zugehörige Office 365-Gruppe. Die gesamte Arbeitsbereichsverwaltung findet in Office 365 statt. Sie können diesen Arbeitsbereichen Kollegen als Mitglieder oder Administratoren hinzufügen. Im Arbeitsbereich können Sie alle beim Erstellen von Dashboards, Berichten und anderen Artikeln zusammenarbeiten, die Sie für eine größere Zielgruppe veröffentlichen möchten. Alle Benutzer, die Sie einem App-Arbeitsbereich hinzufügen, benötigen eine Power BI Pro-Lizenz. 

## <a name="video-apps-and-app-workspaces"></a>Video: Apps und App-Arbeitsbereiche
<iframe width="640" height="360" src="https://www.youtube.com/embed/Ey5pyrr7Lk8?showinfo=0" frameborder="0" allowfullscreen></iframe>

## <a name="create-a-classic-app-workspace-based-on-an-office-365-group"></a>Erstellen eines klassischen App-Arbeitsbereichs auf Grundlage einer Office 365-Gruppe

Wenn Sie einen App-Arbeitsbereich erstellen, basiert dieser auf einer Office 365-Gruppe.

[!INCLUDE [powerbi-service-create-app-workspace](./includes/powerbi-service-create-app-workspace.md)]

Wenn Sie diesen erstellen, müssen Sie möglicherweise etwa eine Stunde warten, bis der Arbeitsbereich an Office 365 weitergeleitet wurde. 

### <a name="add-an-image-to-your-office-365-app-workspace-optional"></a>Hinzufügen eines Bilds im Office 365-App-Arbeitsbereich (optional)
Standardmäßig wird für die App in Power BI ein kleiner farbiger Kreis mit den Initialen der App erstellt. Sie können dies jedoch mit einem Bild anpassen. Sie benötigen eine Exchange Online-Lizenz, um ein Bild hinzuzufügen.

1. Wählen Sie **Arbeitsbereiche**, wählen Sie die Auslassungspunkte (...) neben dem Namen des Arbeitsbereichs, und wählen Sie dann **Mitglieder** aus. 
   
     ![Auswählen von Mitgliedern des Arbeitsbereichs](media/service-create-distribute-apps/power-bi-apps-workspace-members.png)
   
    Das Office 365 Outlook-Konto für den Arbeitsbereich wird in einem neuen Browserfenster geöffnet.
2. Wenn Sie auf den farbigen Kreis in der oberen linken Ecke zeigen, ändert er sich in ein Stiftsymbol. Wählen Sie sie aus.
   
     ![Office 365-Stiftsymbol](media/service-create-distribute-apps/power-bi-apps-workspace-edit-image.png)
3. Wählen Sie das Stiftsymbol erneut aus, und suchen Sie das Bild, das Sie verwenden möchten.
   
     ![Erneutes Auswählen des Stifts](media/service-create-distribute-apps/power-bi-apps-workspace-edit-group.png)

     Die Bilder können PNG-, JPG- oder BMP-Dateien sein. Die Dateien können groß sein (bis zu 3 MB). 

4. Wählen Sie **Speichern**.
   
     ![Auswählen von „Speichern“](media/service-create-distribute-apps/power-bi-apps-workspace-save-image.png)
   
    Das Bild ersetzt den farbigen Kreis im Office 365 Outlook-Fenster. 
   
     ![Benutzerdefiniertes Bild](media/service-create-distribute-apps/power-bi-apps-workspace-image-in-office-365.png)
   
    In einigen Minuten wird es auch in der App in Power BI angezeigt.
   
     ![Benutzerdefiniertes Bild](media/service-create-distribute-apps/power-bi-apps-image.png)

## <a name="add-content-to-your-app-workspace"></a>Hinzufügen von Inhalt zum App-Arbeitsbereich

Nachdem Sie einen App-Arbeitsbereich erstellt haben, ist es Zeit, diesem Inhalte hinzuzufügen. Sie fügen Inhalte auf die gleiche Weise hinzu, wie Sie in „Mein Arbeitsbereich“ Inhalt hinzufügen, mit dem Unterschied, dass andere Personen im Arbeitsbereich ebenfalls den Inhalt anzeigen und bearbeiten können. Ein großer Unterschied ist, dass Sie nach Abschluss der Bearbeitung den Inhalt als App veröffentlichen können. Wenn Sie Inhalte in der Inhaltsliste eines App-Arbeitsbereichs anzeigen, wird der Name des Arbeitsbereichs als Besitzer aufgeführt.

### <a name="connect-to-third-party-services-in-app-workspaces"></a>Herstellen einer Verbindung mit Drittanbieterdiensten in App-Arbeitsbereichen

Apps werden für alle Drittanbieterdienste bereitgestellt, die Power BI unterstützt, was Ihnen erleichtert, Daten von den Diensten abzurufen, die Sie verwenden, z.B. Microsoft Dynamics CRM, Salesforce oder Google Analytics. Sie können organisationsbezogene Apps veröffentlichen, um Ihren Benutzern die Daten bereitzustellen, die sie benötigen.

In den aktuellen Arbeitsbereichen können Sie auch mithilfe organisationsbezogener Inhaltspakete und mithilfe von Inhaltspaketen von Drittanbietern Verbindungen herstellen, z. B. Microsoft Dynamics CRM, Salesforce oder Google Analytics. Erwägen Sie, Ihre organisationsbezogenen Inhaltspakete in Apps zu migrieren.

## <a name="distribute-an-app"></a>Verteilen einer App

Wenn Sie offizielle Inhalte an eine große Zielgruppe innerhalb Ihrer Organisation verteilen möchten, können Sie eine App aus Ihrem Arbeitsbereich veröffentlichen.  Wenn der Inhalt bereit ist, wählen Sie aus, welche Dashboards und Berichte Sie veröffentlichen möchten, und veröffentlichen Sie diese dann als *App*. Sie können über jeden Arbeitsbereich eine App erstellen.

In der Liste der Apps im linken Navigationsbereich werden alle Apps angezeigt, die Sie installiert haben. Ihre Kollegen können Ihre App auf verschiedene Weise abrufen. 
- Sie können Ihre Apps in Microsoft AppSource suchen und installieren.
- Sie können Ihnen einen direkten Link senden. 
- Sie können sie automatisch in den Power BI-Konten Ihrer Kollegen installieren, wenn Ihr Power BI-Administrator Ihnen die Berechtigung dazu erteilt. 

Benutzern wird der aktualisierte App-Inhalt automatisch angezeigt, nachdem Sie ein Update aus Ihrem Arbeitsbereich veröffentlicht haben. Sie können steuern, wie häufig die Daten aktualisiert werden, indem Sie den Aktualisierungszeitplan in den Datasets festlegen, die vom App-Inhalt in Ihrem Arbeitsbereich verwendet werden. Weitere Informationen finden Sie unter [Veröffentlichen einer App aus den neuen Arbeitsbereichen in Power BI](service-create-distribute-apps.md).

## <a name="power-bi-classic-apps-faq"></a>FAQ zu klassischen Apps in Power BI

### <a name="how-are-apps-different-from-organizational-content-packs"></a>Wie unterscheiden sich Apps von organisationsbezogenen Inhaltspaketen?
Apps sind die Weiterentwicklung von organisationsbezogenen Inhaltspaketen. Wenn Sie bereits über organisationsbezogene Inhaltspakete verfügen, können sie weiterhin neben Apps verwendet werden. Apps und Inhaltspakete unterscheiden sich deutlich. 

* Nachdem Geschäftskunden ein Inhaltspaket installiert haben, verliert es seine Gruppenidentität. Es ist dann lediglich eine Liste von Dashboards und Berichten zwischen anderen Dashboards und Berichten. Hingegen bleibt die Gruppierung und Identität von Apps auch nach der Installation erhalten. Durch diese Gruppierung können Geschäftskunden nun zu späteren Zeitpunkten immer wieder unkompliziert dorthin navigieren.
* Sie können in jedem Arbeitsbereich mehrere Inhaltspakete erstellen, eine App weist jedoch eine 1:1-Beziehung zu ihrem Arbeitsbereich auf. 
* Wir planen, im Verlauf der Zeit die Unterstützung organisationsbezogener Inhaltspakete einzustellen, daher wird empfohlen, von nun an Apps zu erstellen.  
* Die Veröffentlichung der Vorschauversion stellt den Beginn des Endes der Unterstützung organisationsbezogener Inhaltspakete dar. Sie können diese nicht in der Vorschauversion für Arbeitsbereiche nutzen oder erstellen.

Einen Vergleich der beiden Arbeitsbereiche finden Sie unter [Unterschiede zwischen den neuen und den alten App-Arbeitsbereichen](service-new-workspaces.md#how-the-new-workspaces-are-different). 

## <a name="next-steps"></a>Nächste Schritte
* [Installieren und Verwenden von Apps in Power BI](service-create-distribute-apps.md)
- [Erstellen der neuen Arbeitsbereiche (Vorschau)](service-create-the-new-workspaces.md)
* Haben Sie Fragen? [Stellen Sie Ihre Frage in der Power BI-Community.](http://community.powerbi.com/)
