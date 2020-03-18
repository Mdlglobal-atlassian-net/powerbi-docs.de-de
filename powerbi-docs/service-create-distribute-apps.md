---
title: Veröffentlichen von Apps in Power BI
description: Erfahren Sie, wie die neuen Apps veröffentlicht werden, die Sammlungen von Dashboards und Berichten mit integrierter Navigation sind.
author: maggiesMSFT
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 08/15/2019
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: 622d01632b9c9cbe6203090b3ac2149d4bc94474
ms.sourcegitcommit: 7e845812874b3347bcf87ca642c66bed298b244a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/13/2020
ms.locfileid: "79207871"
---
# <a name="publish-an-app-in-power-bi"></a>Veröffentlichen von Apps in Power BI

In Power BI können Sie offiziellen verpackten Inhalt erstellen und dann als *App* an eine breite Zielgruppe verteilen. Sie können Apps in *Arbeitsbereichen* erstellen, in denen Sie mit Ihren Kollegen zusammen an Power BI-Inhalten arbeiten können. Anschließend können Sie die fertigen Apps für große Personengruppen in Ihrer Organisation veröffentlichen. 

![Power BI-Apps](media/service-create-distribute-apps/power-bi-new-apps.png)

Ihre Geschäftskunden benötigen für den Betrieb ihres Unternehmens häufig mehrere Power BI-Dashboards und -Berichte. Mit Power BI-Apps können Sie Sammlungen von Dashboards und Berichten erstellen und diese Sammlungen als Apps in Ihrer gesamten Organisation oder für bestimmte Personen oder Gruppen veröffentlichen. Apps vereinfachen das Verwalten von Berechtigungen für derartige Sammlungen für Berichtersteller und Administratoren.

Geschäftskunden erhalten Ihre Apps mit unterschiedlichen Methoden:

- Sie können Ihre Apps in Microsoft AppSource suchen und installieren.
- Sie können Ihnen einen direkten Link senden.
- Sie können sie automatisch in den Power BI-Konten Ihrer Kollegen installieren, wenn Ihr Power BI-Administrator Ihnen die Berechtigung dazu erteilt.

Sie können die App mit einer eigenen integrierten Navigation erstellen, sodass Ihre Benutzer mühelos den Weg zu Ihren Inhalten finden. Den Inhalt der App können sie nicht ändern. Sie können mit ihr im Power BI-Dienst oder in einer der mobilen Apps interagieren, indem sie die Daten selbst filtern, hervorheben und sortieren. Sie erhalten Updates automatisch, und Sie können steuern, wie oft die Daten aktualisiert werden. Sie können ihnen auch die Berechtigung „Erstellen“ erteilen, damit sie eine Verbindung mit den zugrunde liegenden Datasets herstellen und Kopien der Berichte in der App erstellen können. Weitere Informationen zur [Erstellungsberechtigung](service-datasets-build-permissions.md).

## <a name="licenses-for-apps"></a>Lizenzen für Apps
Zum Erstellen oder Aktualisieren einer App benötigen Sie eine Power BI Pro-Lizenz. App-*Benutzern* stehen zwei Optionen zur Verfügung.

* **Option 1:** Der Arbeitsbereich für diese App befindet sich *nicht* in einer Power BI Premium-Kapazität: Alle Geschäftsbenutzer benötigen Power BI Pro-Lizenzen, um sich Ihre App anzeigen zu lassen. 
* **Option 2:** Der Arbeitsbereich für diese App *befindet sich* in einer Power BI Premium-Kapazität: Geschäftsbenutzer ohne Power BI Pro-Lizenzen in Ihrer Organisation können sich App-Inhalte anzeigen lassen. Diese Personen können die Berichte allerdings nicht kopieren oder Berichte mithilfe der zugrunde liegenden Datasets erstellen. Details finden Sie unter [Was ist Power BI Premium?](service-premium.md).

## <a name="publish-your-app"></a>Veröffentlichen der App
Wenn die Dashboards und Berichte in Ihrem Arbeitsbereich bereit sind, wählen Sie aus, welche Dashboards und Berichte Sie veröffentlichen möchten. Anschließend veröffentlichen Sie diese als App. 

1. Entscheiden Sie in der Listenansicht des Arbeitsbereichs, welche Dashboards und Berichte Sie **in die App einschließen** möchten.

     ![Das zu veröffentlichende Dashboard auswählen](media/service-create-distribute-apps/power-bi-apps-incude-dashboard.png)

     Wenn Sie einen Bericht mit einem zugehörige Dashboard nicht zu einem Bericht hinzufügen möchten, wird eine Warnung neben dem Bericht angezeigt. Sie können die App trotzdem veröffentlichen, jedoch fehlen im entsprechenden Dashboard die Kacheln aus diesem Bericht.

     ![Warnung zu zugehörigem Dashboard](media/service-create-distribute-apps/power-bi-apps-report-warning.png)

2. Wählen Sie rechts oben die Schaltfläche **App veröffentlichen** aus, um mit dem Erstellen und Veröffentlichen einer App aus dem Arbeitsbereich heraus zu beginnen.
   
     ![App veröffentlichen](media/service-create-distribute-apps/power-bi-apps-publish-button.png)

3. Geben Sie unter **Setup** den Namen und die Beschreibung ein, damit andere Personen die App leichter finden. Sie können eine Designfarbe festlegen, um die App zu personalisieren. Sie können auch einen Link zu einer Supportwebsite hinzufügen.
   
     ![Erstellen Sie Ihre App](media/service-create-distribute-apps/power-bi-apps-build-your-apps.png)

4. Wählen Sie in der **Navigation** den zu veröffentlichenden Inhalt als Teil der App aus. Dann fügen Sie die App-Navigation hinzu, um den Inhalt in Abschnitten zu organisieren. Weitere Informationen finden Sie in diesem Artikel unter [Entwerfen der Navigation für Ihre App](#design-the-navigation-experience).
   
     ![App-Navigation](media/service-create-distribute-apps/power-bi-apps-navigation.png)

5. Entscheiden Sie unter **Berechtigungen**, wer Zugriff auf die App erhält und wie diese Benutzer die App verwenden können. 
    - In [klassischen Arbeitsbereichen](service-create-workspaces.md): alle Benutzer in Ihrer Organisation, bestimmte Personen oder Azure Active Directory (AAD)-Sicherheitsgruppen.
    - In der [Arbeitsbereichen der neuen Oberfläche ](service-create-the-new-workspaces.md): bestimmte Personen, AAD-Sicherheitsgruppen und Verteilerlisten und Office 365-Gruppen. Alle Arbeitsbereichsbenutzer erhalten automatisch Zugriff auf die App für den Arbeitsbereich.
    - Sie können App-Benutzern eine Erstellungsberechtigung erteilen, damit sie eine Verbindung mit den zugrunde liegenden App-Datasets herstellen können. Die Datasets werden diesen Benutzern angezeigt, wenn sie nach freigegebenen Datasets suchen. Weitere Informationen finden Sie unter [Erteilen einer Benutzerberechtigung zum Herstellen einer Verbindung mit App-Datasets](#allow-users-to-connect-to-datasets).
    - Benutzer mit der Erstellungsberechtigung können auch über die Berechtigung verfügen, Berichte aus dieser App in einen anderen Arbeitsbereich zu kopieren. Weitere Informationen finden Sie unter [Erteilen einer Benutzerberechtigung zum Kopieren von Berichten in der App](#allow-users-to-copy-reports).
    
    >[!IMPORTANT]
    >Wenn Ihre App auf Datasets aus anderen Arbeitsbereichen basiert, müssen Sie sicherstellen, dass alle App-Benutzer Zugriff auf die zugrunde liegenden Datasets haben.
    >

6. Sie können die App automatisch für die Empfänger installieren, wenn Ihr Power BI-Administrator diese Einstellung für Sie im Power BI-Verwaltungsportal aktiviert hat. In diesem Artikel erfahren Sie mehr über das [automatische Installieren einer App](#automatically-install-apps-for-end-users).

     ![App-Berechtigungen](media/service-create-distribute-apps/power-bi-apps-permissions.png)

7. Wenn Sie **App veröffentlichen** auswählen, wird eine Meldung mit der Bestätigung angezeigt, dass die App jetzt veröffentlicht werden kann. Im Dialogfeld **Diese App freigeben**  können Sie die URL kopieren, die einen direkten Link zu dieser App darstellt.
   
     ![Fertigstellen der App](media/service-create-distribute-apps/power-bi-apps-success.png)

Diesen direkten Link können Sie an die Personen senden, für die Sie die App freigeben möchten. Alternativ können diese Personen zu **Mehr Apps aus AppSource herunterladen und kennenlernen** navigieren, um Ihre App auf der Registerkarte „Apps“ zu finden. Erfahren Sie mehr über die [Nutzung von Apps durch Geschäftskunden](consumer/end-user-apps.md).

## <a name="change-your-published-app"></a>Ändern der veröffentlichten App
Nachdem Sie Ihre App veröffentlicht haben, möchten Sie sie eventuell ändern oder aktualisieren. Sie lässt sich einfach aktualisieren, wenn Sie Administrator oder Mitglied des neuen Arbeitsbereichs sind. 

1. Öffnen Sie den Arbeitsbereich, der der App entspricht. 
   
     ![Öffnen des Arbeitsbereichs](media/service-create-distribute-apps/power-bi-apps-open-workspace.png)

2. Nehmen Sie alle gewünschten Änderungen an den Dashboards oder Berichten vor.
 
     Der Arbeitsbereich ist der Stagingbereich. Ihre Änderungen werden daher nicht in Echtzeit in der App angezeigt, bis Sie die App erneut veröffentlichen. So können Sie Änderungen vornehmen, ohne dass sich diese auf die veröffentlichten Apps auswirken.  
 
    > [!IMPORTANT]
    > Wenn Sie einen Bericht entfernen und die App aktualisieren, verlieren Ihre App-Benutzer alle Anpassungen wie Lesezeichen, Kommentare usw., selbst wenn Sie den Bericht anschließend wieder zur App hinzufügen.  
 
3. Kehren Sie zur Liste der Inhalte im Arbeitsbereich zurück, und klicken Sie oben rechts auf **App aktualisieren**.
   
1. Aktualisieren Sie bei Bedarf **Setup**, **Navigation** und **Berechtigungen**, und wählen Sie dann **App aktualisieren** aus.
   
Den Personen, für die Sie die App veröffentlicht haben, wird automatisch die aktualisierte Version der App angezeigt. 

## <a name="design-the-navigation-experience"></a>Entwerfen der Navigation
Mit der Option **Neuer Navigations-Generator** können Sie eine benutzerdefinierte Navigation für Ihre App erstellen. Die benutzerdefinierte Navigation erleichtert Ihren Benutzer das Suchen und Verwenden von Inhalten in der App. In vorhandenen Apps ist diese Option deaktiviert, in neuen Apps ist die Option standardmäßig aktiviert.

Ist die Option deaktiviert, können Sie für die **Landing Page der App** zwischen **Bestimmte Inhalte**, z.B. einem Dashboard oder Bericht, und **Keine** auswählen, wodurch dem Benutzer eine einfache Liste mit Inhalten angezeigt wird.

Wenn Sie **Neuer Navigations-Generator** aktivieren, können Sie eine benutzerdefinierte Navigation entwerfen. Standardmäßig werden alle Berichte, Dashboards und Excel-Arbeitsmappen, die Sie zu Ihrer App hinzugefügt haben, als flache Liste aufgeführt. 

![App-Navigation](media/service-create-distribute-apps/power-bi-apps-navigation.png)

Sie können die App-Navigation folgendermaßen weiter anpassen:
* Elemente mithilfe der Nach-Oben-/Nach-Unten-Tasten neu anordnen. 
* Elemente in den Bereichen **Berichtsdetails**, **Dashboarddetails** und **Arbeitsmappendetails** umbenennen.
* Bestimmte Elemente aus der Navigation ausblenden.
* Mithilfe der Option **Neu** **Abschnitte** hinzufügen, um verwandte Inhalte zu gruppieren.
* Mithilfe der Option **Neu** zum Navigationsbereich einen **Link** zu einer externen Ressource hinzufügen. 

Wenn Sie einen **Link** hinzufügen, können Sie unter **Linkdetails** auswählen, wo der Link geöffnet wird. Standardmäßig werden Links in der **aktuellen Registerkarte** geöffnet, Sie können jedoch auch **Neue Registerkarte** oder **Inhaltsbereich** auswählen. 

### <a name="considerations-for-using-the-new-navigation-builder-option"></a>Überlegungen zur Verwendung der Option „Neuer Navigations-Generator“
Hier finden Sie allgemeine Dinge, die Sie berücksichtigen sollten, wenn den neuen Navigations-Generator verwenden:
* Berichtsseiten werden im App-Navigationsbereich als erweiterbarer Abschnitt angezeigt.
* Wenn Sie den neuen Navigations-Generator deaktivieren, und für Ihre App auf „Veröffentlichen“ oder „Aktualisieren“ klicken, gehen die vorgenommenen Anpassungen verloren. Beispielsweise gehen Abschnitte, Sortierung, Links und benutzerdefinierte Namen für Navigationselemente verloren.

Wenn Sie Links zu Ihrer App-Navigation hinzufügen und die Option „Inhaltsbereich“ auswählen:
* Stellen Sie sicher, dass der Link eingebettet werden kann. Einige Dienste blockieren das Einbetten ihrer Inhalte in Drittanbieterwebsites wie Power BI.
* Das Einbetten von Inhalten wie Berichten oder Dashboards des Power BI-Diensts in andere Arbeitsbereiche wird nicht unterstützt. 
* Betten Sie Power BI-Berichtsserver-Inhalt unter Verwendung seines nativen eingebetteten URL-Inhalts aus einer lokalen Bereitstellung ein. Verwenden Sie die Schritte unter [Erstellen der Berichts-URL für den Power BI-Berichtsserver](https://docs.microsoft.com/power-bi/report-server/quickstart-embed#create-the-power-bi-report-url), um die URL abzurufen. Denken Sie daran, dass die regulären Authentifizierungsregeln gelten. Zum Anzeigen des Inhalts ist daher eine VPN-Verbindung mit dem lokalen Server erforderlich. 
* Am oberen Rand der eingebetteten Inhalte wird mit einer Sicherheitswarnung darauf hingewiesen, dass sich der Inhalt außerhalb von Power BI befindet.



## <a name="automatically-install-apps-for-end-users"></a>Automatisches Installieren von Apps für Endbenutzer
Wenn ein Administrator Ihnen Berechtigungen erteilt, können Sie Apps automatisch per *Push* an Endbenutzersenden und installieren. Diese Push-Funktionalität erleichtert es, die richtigen Apps an die richtigen Personen oder Gruppen zu verteilen. Ihre App wird automatisch in der Inhaltsliste der Apps Ihrer Endbenutzer angezeigt. Die Benutzer brauchen die App nicht in der Microsoft AppSource zu suchen oder einem Installationslink zu folgen. Im Artikel über das Power BI-Verwaltungsportal erfahren Sie, wie Administratoren das [Übertragen von Apps per Push an Endbenutzer](service-admin-portal.md#push-apps-to-end-users) aktivieren.

### <a name="how-to-push-an-app-automatically-to-end-users"></a>Automatisches Übertragen einer App per Push an Endbenutzer
Sobald der Administrator Ihnen die Berechtigungen zugewiesen hat, verfügen Sie über die neue Option **install the app automatically** (App automatisch installieren). Wenn Sie das Kontrollkästchen aktivieren und auf **App veröffentlichen** (oder **App aktualisieren**) klicken, wird die App mithilfe von Push an alle Benutzer oder Gruppen übertragen, die im Abschnitt **Berechtigungen** der App auf der Registerkarte **Zugriff** definiert sind.

![Aktivieren der Übertragung von Apps mithilfe von Push](media/service-create-distribute-apps//power-bi-apps-access.png)

### <a name="how-users-get-the-apps-that-you-push-to-them"></a>So erhalten Benutzer die Apps, die Sie mithilfe von Push an sie übertragen haben
Nachdem Sie eine App mithilfe von Push übertragen haben, wird sie automatisch in ihrer Liste der Apps angezeigt. Auf diese Weise können Sie die Apps zusammenstellen, die bestimmte Benutzer oder Aufgabengebiete in Ihrer Organisation benötigen.

![Aktivieren der Übertragung von Apps mithilfe von Push](media/service-create-distribute-apps/power-bi-apps-left-nav.png)

### <a name="considerations-for-automatically-installing-apps"></a>Überlegungen zum automatischen Installieren von Apps
Beachten Sie bei der Übertragung von Apps mithilfe von Push an Benutzer folgende Punkte:

* Die automatische Installation für Benutzer einer App kann zeitaufwendig sein. Die meisten Apps werden für Benutzer sofort installiert, die Übertragung von Apps mithilfe von Push kann allerdings einige Zeit in Anspruch nehmen.  Dies ist von der Anzahl der Elemente in der App und der Anzahl der Personen abhängig, denen der Zugriff gewährt wird. Es wird empfohlen, die Übertragung von Apps mithilfe von Push außerhalb der Stoßzeiten und mit ausreichend Vorlaufzeit durchzuführen, bevor die Benutzer diese benötigen. Überprüfen Sie die Funktionsfähigkeit des Vorgangs mit einigen wenigen Benutzern, bevor Sie die Verfügbarkeit der App im großen Rahmen ankündigen.

* Aktualisieren Sie den Browser. Bevor die mithilfe von Push übertragene App in der Liste der Apps angezeigt wird, muss der Benutzer seinen Browser gegebenenfalls aktualisieren, schließen und neu öffnen.

* Wenn Benutzer die App nicht sofort in der Liste der Apps sehen, sollte der Browser aktualisiert, geschlossen und neu geöffnet werden.

* Versuchen Sie die Benutzer nicht zu überfordern. Achten Sie darauf, dass nicht zu viele Apps mithilfe von Push übertragen werden, damit die Benutzer die vorinstallierten Apps als nützlich wahrnehmen. Um ein sinnvolles Timing zu gewährleisten, sollten Sie steuern können, wer Apps mithilfe von Push an Endbenutzer übertragen kann. Wählen Sie eine Kontaktperson aus, die für das Übertragen von Apps in Ihrer Organisation mithilfe von Push an Endbenutzer verantwortlich ist.

* Für Gastbenutzer, die keine Einladung angenommen haben, werden keine Apps automatisch installiert.  

## <a name="allow-users-to-connect-to-datasets"></a>Erteilen einer Benutzerberechtigung zum Herstellen einer Verbindung mit App-Datasets

Wenn Sie die Option **Allow users to connect to the app's underlying datasets** (Benutzern erlauben, eine Verbindung mit den zugrunde liegenden Datasets der App herzustellen) aktivieren, erteilen Sie App-Benutzern die *Erstellungsberechtigung* für diese Datasets. Mit dieser Berechtigung können sie mehrere wichtige Aktionen ausführen:

- Sie können die [App-Datasets als Grundlage für ihre Berichte verwenden](service-datasets-across-workspaces.md).
- Sie können in Power BI Desktop und mit dem Feature „Daten abrufen“ im Power BI-Dienst nach diesen Datasets suchen.
- Sie können Berichte und Dashboards auf Grundlage dieser Datasets erstellen.

Wenn Sie diese Option deaktivieren, erhalten neue Benutzer, die Sie der App hinzufügen, nicht die Berechtigung „Erstellen“. Die Berechtigungen der vorhandenen App-Benutzer für die zugrunde liegenden Datasets bleiben jedoch unverändert. Sie können App-Benutzern bei Bedarf die Berechtigung „Erstellen“ manuell entziehen. Weitere Informationen zur [Erstellungsberechtigung](service-datasets-build-permissions.md).

## <a name="allow-users-to-copy-reports"></a>Erteilen einer Benutzerberechtigung zum Kopieren von Berichten

Wenn Sie die Option **Allow users to make a copy of the reports in this app** (Benutzern erlauben, eine Kopie der Berichte in dieser App zu erstellen) aktivieren, können Benutzer alle Berichte in der App in „Mein Arbeitsbereich“ oder in einem anderen Arbeitsbereich speichern. Selbst wenn sich der ursprüngliche Bericht in einem Arbeitsbereich in einer Premium-Kapazität befindet, benötigen Benutzer eine Pro-Lizenz, um eine Kopie zu erstellen. Sie können die Berichte dann an ihre individuellen Anforderungen anpassen. Sie müssen zuerst die Option **Allen Benutzern das Herstellen einer Verbindung mit den der App zugrunde liegenden Datasets über die Berechtigung „Erstellen“ gestatten** aktivieren. Durch die Auswahl dieser Optionen aktivieren Sie das neue Feature zum [Kopieren von Berichten aus anderen Arbeitsbereichen](service-datasets-copy-reports.md).

## <a name="unpublish-an-app"></a>Aufheben der Veröffentlichung einer App
Jedes Mitglied eines Arbeitsbereichs kann die Veröffentlichung der App aufheben.

>[!IMPORTANT]
>Wenn Sie die Veröffentlichung einer App aufheben, gehen die Anpassungen der App-Benutzer verloren. Persönliche Lesezeichen, Kommentare oder Abonnements, die Inhalten der App zugeordnet sind, gehen verloren. Heben Sie die Veröffentlichung einer App nur dann auf, wenn Sie sie entfernen müssen.
> 

* Klicken Sie im Arbeitsbereich rechts oben auf die Auslassungspunkte ( **...** ) und anschließend auf **Veröffentlichung der App aufheben**.
  
     ![Veröffentlichung der App aufheben](media/service-create-distribute-apps/power-bi-app-unpublish.png)

Dadurch wird die App für alle Benutzer, für die sie veröffentlicht wurde, deinstalliert, sodass diese keinen Zugriff mehr darauf haben. Weder der Arbeitsbereich noch dessen Inhalt werden dadurch gelöscht.

## <a name="view-your-published-app"></a>Anzeigen der veröffentlichten App

Wenn Ihre App-Benutzer die App öffnen, wird anstelle des standardmäßigen Navigationsbereichs von Power BI die von Ihnen erstellte Navigation angezeigt. In der App-Navigation sind die Berichte und Dashboards in den von Ihnen definierten Abschnitten aufgelistet. Zudem sind die einzelnen Seiten in jedem Bericht aufgeführt, nicht nur der Berichtsname.

![App mit Navigation](media/service-create-distribute-apps/power-bi-new-apps-navigation.png)

## <a name="considerations-and-limitations"></a>Überlegungen und Einschränkungen
Aspekte, die beim Veröffentlichen von Apps zu beachten sind:

* Sie können maximal 100 Benutzer oder Gruppen in der Zugriffsliste der App haben. Allerdings können Sie mehr als 100 Benutzern Zugriff auf die App gewähren. Verwenden Sie dazu eine oder mehrere Benutzergruppen, die alle gewünschten Benutzer enthalten.
* Wenn bei der neuen Arbeitsbereichsfunktion der zur App-Zugriffsliste hinzugefügte Benutzer bereits über den Arbeitsbereich Zugriff auf die App hat, wird er nicht in der Zugriffsliste für die App angezeigt.  


## <a name="next-steps"></a>Nächste Schritte
* [Erstellen eines Arbeitsbereichs](service-create-workspaces.md)
* [Installieren und Verwenden von Apps in Power BI](consumer/end-user-apps.md)
* [Power BI-Apps für externe Dienste](service-connect-to-services.md)
* [Power BI-Verwaltungsportal](https://docs.microsoft.com/power-bi/service-admin-portal)
* Haben Sie Fragen? [Stellen Sie Ihre Frage in der Power BI-Community.](https://community.powerbi.com/)
