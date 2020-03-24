---
title: Häufig gestellte Fragen zu Power BI-Visuals
description: In diesem Artikel finden Sie eine Liste häufig gestellter Fragen und Antworten zu Power BI-Visuals.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.topic: conceptual
ms.subservice: powerbi-custom-visuals
ms.custom: ''
ms.date: 12/17/2018
ms.openlocfilehash: d70d1357af3309ddd9584b11ccf79115cde095c8
ms.sourcegitcommit: 6bbc3d0073ca605c50911c162dc9f58926db7b66
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/14/2020
ms.locfileid: "79383296"
---
# <a name="power-bi-visuals-faq"></a>Häufig gestellte Fragen zu Power BI-Visuals

## <a name="organizational-power-bi-visuals"></a>Power BI-Organisationsvisuals

Das Verwaltungsportal ermöglicht die Verwaltung von Power BI-Visuals für Ihre Organisation.

### <a name="how-can-the-admin-manage-organizational-power-bi-visuals"></a>Wie können Administratoren Power BI-Organisationsvisuals verwalten?

Im Verwaltungsportal können Administratoren auf der Registerkarte *Organisationsvisuals*[alle Power BI-Organisationsvisuals im Unternehmen anzeigen und verwalten](../../service-admin-portal.md#organizational-visuals). Dies umfasst das Hinzufügen, Deaktivieren, Aktivieren und Löschen von Power BI-Visuals.

Benutzer in der Organisation können Power BI-Visuals problemlos finden und direkt aus Power BI Desktop oder dem Power BI-Dienst in ihre Berichte importieren.

Sobald ein Administrator eine neue Version eines Power BI-Organisationsvisuals hochlädt, erhalten alle Benutzer in der Organisation die gleiche aktualisierte Version. Alle Berichte, die aktualisierte Power BI-Visuals verwenden, werden automatisch aktualisiert.

Benutzer können die Power BI-Organisationsvisuals im integrierten Organisationsstore für Power BI Desktop und den Power BI-Dienst auf der Registerkarte *MEINE ORGANISATION* finden. 

### <a name="if-an-admin-uploads-a-power-bi-visual-from-the-public-marketplace-to-the-organization-store-is-it-automatically-updated-once-a-vendor-updates-the-visual-in-the-public-marketplace"></a>Wenn ein Administrator ein Power BI-Visual aus dem öffentlichen Marketplace in den Organisationsstore hochlädt, wird es dann automatisch aktualisiert, sobald ein Anbieter das Visual im öffentlichen Marketplace aktualisiert?

Nein, es gibt keine automatische Aktualisierungen vom öffentlichen Marketplace. Es liegt in der Verantwortung des Administrators, die Versionen der Power BI-Organisationsvisuals zu aktualisieren.

### <a name="is-there-a-way-to-disable-the-organization-store"></a>Gibt es eine Möglichkeit, den Store der Organisation zu deaktivieren?

Nein, die Registerkarte *MEINE ORGANISATION* wird in Power BI Desktop und dem Power BI-Dienst immer für die Benutzer angezeigt. Wenn ein Administrator alle Power BI-Organisationsvisuals im Verwaltungsportal deaktiviert oder löscht, ist der Organisationsstore leer.
  
### <a name="if-the-admin-disables-power-bi-visuals-from-the-admin-portal-tenant-settings-do-users-still-have-access-to-the-organizational-power-bi-visuals"></a>Wenn der Administrator Power BI-Organisationsvisuals über das Verwaltungsportal deaktiviert (Mandanteneinstellungen), haben Benutzer dann noch Zugriff auf diese Visuals?

Ja, wenn der Administrator die Power BI-Visuals über das Verwaltungsportal deaktiviert, hat dies keine Auswirkungen auf den Organisationsspeicher.

Einige Organisationen deaktivieren Power BI-Visuals und aktivieren nur handverlesene Visuals, die vom Power BI-Administrator importiert und in den Organisationsstore hochgeladen wurden.

Das Deaktivieren der Power BI-Visuals über das Verwaltungsportal wird in Power BI Desktop nicht erzwungen. Desktop-Benutzer können weiterhin Power BI-Visuals vom öffentlichen Marketplace in ihren Berichten hinzufügen und verwenden. Diese öffentlichen Power BI-Visuals werden nach der Veröffentlichung im Power BI-Dienst jedoch nicht mehr gerendert und geben einen entsprechenden Fehler aus. 

Wenn die Einstellung für Power BI-Visuals im Verwaltungsportal aktiviert wurde, können Benutzer im Power BI-Dienst keine Power BI-Visuals aus dem öffentlichen Marketplace importieren. Es können nur Visual aus dem Organisationsstore importiert werden.

### <a name="what-are-the-advantages-of-power-bi-visuals-in-the-organizational-store"></a>Welche Vorteile bieten Power BI-Visuals im Organisationsstore?

* Alle Benutzer erhalten die gleiche Visualversion, die vom Power BI-Administrator gesteuert wird. Sobald der Administrator die Version des Visuals im Administratorportal aktualisiert, erhalten alle Benutzer in der Organisation automatisch die aktualisierte Version.

* Eine Weitergabe von Visualdateien per E-Mail oder über freigegebene Ordner ist nicht mehr erforderlich. Der Angebote im Organisationsstore sind für alle angemeldeten Mitglieder sichtbar.

* Aus Gründen der Sicherheit und Unterstützbarkeit werden neue Versionen von Power BI-Organisationsvisuals automatisch in allen Berichten aktualisiert.

* Administratoren können steuern, welche Power BI-Visuals in der gesamten Organisation verfügbar sein sollen.

* Administratoren können Visuals zu Testzwecken im Administratorportal aktivieren/deaktivieren.

## <a name="certified-power-bi-visuals"></a>Zertifizierte Power BI-Visuals

### <a name="what-are-certified-power-bi-visuals"></a>Was sind zertifizierte Power BI-Visuals?

Zertifizierte Power BI-Visuals sind Power BI-Visuals, die bestimmte [Anforderungen](power-bi-custom-visuals-certified.md) erfüllen und von Microsoft zertifiziert sind.

Im [Marketplace](https://appsource.microsoft.com/marketplace/apps?page=1&product=power-bi-visuals) sind zertifizierte Power BI-Visuals mit einem gelben Badge gekennzeichnet.

Microsoft ist nicht der Autor von Power BI-Visuals von Drittanbietern. Wir raten Kunden, direkt mit dem Autor Kontakt aufzunehmen, um die Funktionalität solcher Visuals zu verifizieren.

### <a name="what-tests-are-done-during-the-certification-process"></a>Welche Tests werden während des Zertifizierungsprozesses durchgeführt?

Die Zertifizierungsprozesstests beinhalten u. a. Folgendes: 
* Codebewertungen
* Analyse des statischen Codes
* Datenlecks
* Datenfuzzing
* Penetrationstests
* Testen des Zugriffs per XSS
* Einschleusen schädlicher Daten
* Eingabeüberprüfung
* Funktionstests
 
### <a name="are-certified-power-bi-visual-checked-again-with-every-new-submission-upgrade"></a>Werden zertifizierte Power BI-Visuals bei jeder neuen Übermittlung (Upgrade) erneut überprüft?

Ja. Jedes Mal, wenn eine neue Version eines zertifizierten Visuals im Marketplace eingereicht wird, wird das Update der Visualversion denselben Zertifizierungsüberprüfungen unterzogen.

Die Zertifizierung des Versionsupdates erfolgt automatisch. Sollte ein Verstoß vorliegen, der eine Ablehnung des Updates zur Folge hat, wird eine E-Mail an den Entwickler gesendet, in der erläutert wird, was korrigiert werden muss.

### <a name="can-a-certified-power-bi-visual-stop-lose-its-certification-after-a-new-update"></a>Kann ein zertifiziertes Power BI-Visual nach einem Update die Zertifizierung verlieren?

Nein, das ist nicht möglich. Ein zertifiziertes Visual kann die Zertifizierung durch ein Update nicht verlieren. Das Update wird zurückgewiesen.
 
### <a name="do-i-need-to-share-my-code-in-a-public-repository-if-im-certifying-my-power-bi-visual"></a>Muss ich meinen Code in einem öffentlichen Repository freigeben, wenn ich mein Power BI-Visual zertifiziere?

Nein, Sie müssen Ihren Code nicht veröffentlichen.

Geben Sie Leseberechtigungen an, damit der Code des Power BI-Visuals überprüft werden kann. Verwenden Sie dafür beispielsweise ein privates Repository in GitHub.
 
### <a name="does-a-certified-power-bi-visual-have-to-be-in-the-marketplace"></a>Muss sich ein zertifiziertes Power BI-Visual im Marketplace befinden?

Ja. Private Visuals werden nicht zertifiziert.
 
### <a name="how-long-does-it-take-to-certify-my-visual"></a>Wie lange benötigt die Zertifizierung eines Visuals?

Die Zertifizierung eines neuen Power BI-Visuals (erstmalige Zertifizierung) kann bis zu vier Wochen dauern. 

Die Zertifizierung einer aktualisierten Version eines Power BI-Visuals kann bis zu drei Wochen dauern. 

### <a name="does-the-certification-process-ensure-that-there-is-no-data-leakage"></a>Stellt der Zertifizierungsprozess sicher, dass keine Datenlecks vorhanden sind?

Die durchgeführten Tests wurden entworfen, um zu überprüfen, ob das Visual nicht auf externe Dienste oder Ressourcen zugreift. 

Microsoft ist nicht der Autor von Power BI-Visuals von Drittanbietern. Wir raten Kunden, direkt mit dem Autor Kontakt aufzunehmen, um die Funktionalität solcher Visuals zu verifizieren.
 
### <a name="are-uncertified-power-bi-visuals-safe-to-use"></a>Ist die Verwendung nicht zertifizierter Power BI-Visuals sicher?

Nicht zertifizierte Power BI-Visuals sind nicht zwangsläufig unsicher.

Einige Visuals sind nicht zertifiziert, weil sie in mindestens einem Punkt die [Zertifizierungsanforderungen](power-bi-custom-visuals-certified.md#certification-requirements) nicht erfüllen. Beispiele hierfür sind die Herstellung einer Verbindung zu einem externen Dienst wie Kartenvisuals oder Visuals, die kommerzielle Bibliotheken verwenden.
 
## <a name="visuals-with-additional-purchases"></a>Visuals mit zusätzlichen Käufen

### <a name="what-is-a-visual-with-additional-purchases"></a>Was ist ein Visual mit zusätzlichen Käufen?

Ein Visual mit zusätzlichen Käufen ähnelt einem Add-In mit In-App-Kauf (In-App Purchase, IAP). Diese Add-Ins weisen die Preisauszeichnung **Möglicherweise sind zusätzliche Käufe erforderlich** auf.

Power BI-IAP-Visuals sind kostenlose herunterladbare Power BI-Visuals. Benutzer zahlen für das Herunterladen dieser Power BI-Visuals aus dem Marketplace nichts.

In IAP-Visuals stehen optionale In-App-Käufe für erweiterte Features zur Verfügung.  

### <a name="what-is-changing-in-the-submission-process"></a>Was ändert sich am Übermittlungsvorgang?

Der Vorgang zum Übermitteln von Power BI-IAP-Visuals an den Marketplace ist der gleiche wie bei kostenlosen Power BI-Visuals. Sie können ein Power BI-Visual über [Partner Center](https://docs.microsoft.com/partner-center/) zur Zertifizierung übermitteln.


Wenn Sie Ihr Power BI-Visual registrieren, navigieren Sie zur Registerkarte *Produkteinrichtung*, und aktivieren Sie das Kontrollkästchen *Mein Produkt erfordert den Erwerb eines Diensts*.

### <a name="what-should-i-do-beforesubmittingmy-iap-power-bi-visual"></a>Was sollte ich vor dem Übermitteln meines Power BI-IAP-Visuals unternehmen?

Wenn Sie an einem Power BI-IAP-Visual arbeiten, achten Sie darauf, dass es den [Richtlinien](guidelines-powerbi-visuals.md) entspricht.  

> [!NOTE]
> Kostenlose Power BI-Visuals mit einem hinzugefügten IAP-Feature müssen die gleichen kostenlosen Features enthalten, die zuvor angeboten worden waren. Sie können zusätzlich zu den bisherigen kostenlosen Features optionale erweiterte Features hinzufügen, die kostenpflichtig sind. Es empfiehlt sich, ein Power BI-IAP-Visual mit erweiterten Features als neues Power BI-Visual zu übermitteln, anstatt das bisherige kostenlose Visual zu aktualisieren.

### <a name="do-iap-power-bi-visuals-need-to-be-certified"></a>Müssen Power BI-IAP-Visuals zertifiziert werden?

Der Prozess der [Zertifizierung](power-bi-custom-visuals-certified.md) ist optional. Es liegt im Ermessen des Entwicklers, ob seine Power BI-IAP-Visuals zertifiziert werden sollen oder nicht.

### <a name="can-i-get-my-iap-power-bi-visual-certified"></a>Kann ich mein Power BI-IAP-Visual zertifizieren lassen?

Ja, sobald Ihr Power BI-IAP-Visual vom AppSource-Team genehmigt wurde, können Sie es zur [Zertifizierung](power-bi-custom-visuals-certified.md) übermitteln.

Die Zertifizierung ist ein optionaler Vorgang, daher liegt es ganz bei Ihnen, ob Sie Ihr IAP-Visual zertifizieren lassen möchten.

## <a name="additional-questions"></a>Weitere Fragen

### <a name="how-to-get-support"></a>Wie erhalte ich Support?

Sie können sich mit Fragen, Kommentaren oder Problemen jederzeit gerne unter pbicvsupport@microsoft.com an das Power BI-Visuals-Supportteam wenden.  

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen finden Sie auf der Seite [Problembehandlung bei Power BI-Visuals](power-bi-custom-visuals-troubleshoot.md).
