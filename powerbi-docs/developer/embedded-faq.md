---
title: Häufig gestellte Fragen zu Power BI Embedded
description: Durchsuchen Sie die Liste der häufig gestellten Fragen und Antworten zu Power BI Embedded.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 02/11/2020
ms.openlocfilehash: 3561d122dde324f1d383d40a152bccc193a2afbe
ms.sourcegitcommit: 17aad73762579d6822383b27b96b1b63f87f2d6f
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/14/2020
ms.locfileid: "77259699"
---
# <a name="frequently-asked-questions-about-power-bi-embedded"></a>Häufig gestellte Fragen zu Power BI Embedded

* Wenn Sie weitere Fragen haben, [stellen Sie sie in der Power BI-Community](https://community.powerbi.com/).
* Treten weiterhin Probleme auf? Besuchen Sie die [Supportseite für Power BI](https://powerbi.microsoft.com/support/).

## <a name="general"></a>Allgemein

### <a name="what-is-power-bi-embedded"></a>Was ist Power BI Embedded?

Mit [Microsoft Power BI Embedded (PBIE)](azure-pbie-what-is-power-bi-embedded.md) können Anwendungsentwickler ansprechende, vollständig interaktive Berichte in ihre Anwendungen einbetten, ohne selbst Datenvisualisierungen und Steuerelemente von Grund auf neu erstellen zu müssen.

### <a name="who-is-the-target-audience-for-power-bi-embedded"></a>Für wen ist Power BI Embedded gedacht?

Power BI Embedded ist für Entwickler und Softwarehersteller gedacht, die als unabhängige Softwarehersteller (ISVs) eigene Anwendungen entwickeln.

### <a name="how-is-power-bi-embedded-different-from-power-bi-the-service"></a>Worin unterscheidet sich Power BI Embedded vom Power BI-Dienst?

Power BI ist eine Software-as-a-Service-Analyselösung, die Organisationen eine zentrale Ansicht ihrer wichtigsten Geschäftsdaten bietet.

Microsoft hat Power BI Embedded für unabhängige Softwarehersteller entwickelt, die Visuals in ihre Anwendungen einbetten möchten, damit ihre Kunden auf Analysen basierte Entscheidungen treffen können. Dadurch müssen sie keine eigenen Analyselösungen entwickeln. [Embedded Analytics](embedding.md) ermöglicht Geschäftskunden den Zugriff auf Unternehmensdaten und die Ausführung von Abfragen, um anhand dieser Daten in der Anwendung Erkenntnisse zu gewinnen.


### <a name="what-is-the-difference-between-power-bi-premium-and-power-bi-embedded"></a>Worin unterscheidet sich Power BI Premium von Power BI Embedded?

Power BI Premium unterstützt Kapazitäten, die auf Unternehmen zugeschnitten sind, die eine umfassende BI-Lösung mit einer zentralen Ansicht ihrer Organisation, ihrer Partner, Kunden und Zulieferer benötigen. Power BI Premium unterstützt Ihr Unternehmen bei der Entscheidungsfindung. Power BI Premium ist ein SaaS-Produkt, das es Benutzern ermöglicht, Inhalte über das Power BI-Portal, die mobile App und intern entwickelte Apps zu verarbeiten.

Power BI Embedded wurde für unabhängige Softwarehersteller entwickelt, die Visuals in ihre Anwendungen einbetten möchten. Power BI Embedded unterstützt Ihre Kunden bei der Entscheidungsfindung, und da Power BI Embedded auf Anwendungsentwickler ausgerichtet ist, können diese Kunden der Anwendung und beliebige Benutzer innerhalb und außerhalb der Organisation Inhalte verarbeiten, die in der Power BI Embedded-Kapazität gespeichert sind. Sie können die Inhalte einer Power BI Embedded-Kapazität nicht per Mausklick im Web oder auf SharePoint veröffentlichen.

### <a name="what-is-the-microsoft-recommendation-for-when-a-customer-should-buy-power-bi-premium-vs-power-bi-embedded"></a>Welche Empfehlungen gibt Microsoft Kunden für die Entscheidung zwischen Power BI Premium und Power BI Embedded?

Microsoft empfiehlt Unternehmen, Power BI Premium zu erwerben. Dabei handelt es sich um eine auf Unternehmen zugeschnittene Self-Service-BI-Cloudlösung. Es wird empfohlen, unabhängige Softwareherstellern, Power BI Embedded für ihre cloudgestützten Embedded Analytics-Komponenten zu erwerben. Es gibt jedoch keine Einschränkungen dafür, welches Produkt ein Kunde kauft.

In bestimmten Fällen empfiehlt sich zusätzlich zur App-Einbettung eine P-SKU für (in der Regel große) unabhängige Softwarehersteller, um von den Vorteilen des vorkonfigurierten Power BI-Diensts in einer Organisation profitieren zu können. Einige Unternehmen entscheiden sich möglicherweise nur für A-SKUs in Azure, weil sie Branchenanwendungen erstellen und Analysefunktionen in diese einbetten möchten und nicht daran interessiert sind, den vorkonfigurierten Power BI-Dienst zu nutzen.

### <a name="how-many-embed-tokens-can-i-create"></a>Wie viele Einbettungstokens kann ich erstellen?

Da Einbettungstoken mit einer Pro-Lizenz nur für Entwicklungstests vorgesehen sind, ist die Anzahl von Token limitiert, die ein Power BI-Hauptkonto oder ein [Dienstprinzipal](embed-service-principal.md) generieren kann. [Erwerben Sie eine Kapazität](#technical), um Einbettungen in einer Produktionsumgebung vornehmen zu können. Wenn Sie eine Kapazität erwerben, gibt es keine Einschränkungen hinsichtlich der Anzahl von Einbettungstoken, die generiert werden können. Verwenden Sie die Vorgänge zum Abrufen [verfügbarer Features](https://docs.microsoft.com/rest/api/power-bi/availablefeatures), um den Auslastungswert zu überprüfen, der die derzeit eingebettete Auslastung in Prozent angibt.

## <a name="technical"></a>Technische Fragen

### <a name="where-can-i-learn-more-about-capacity-and-skus-in-power-bi-embedded-analytics"></a>Wo kann ich mehr über Kapazitäten und SKUs in Power BI Embedded Analytics erfahren?

Weitere Informationen finden Sie unter [Kapazität und SKUs in Power BI Embedded Analytics](embedded-capacity.md).

### <a name="what-are-the-prerequisites-for-creating-a-pbie-capacity-in-azure"></a>Was sind die Voraussetzungen für das Erstellen einer PBIE-Kapazität in Azure?

* Sie müssen sich bei Ihrem Organisationsverzeichnis anmelden (Microsoft-Konten werden nicht unterstützt).
* Sie müssen über einen Power BI-Mandanten verfügen, d. h. mindestens ein Benutzer in Ihrem Verzeichnis muss bei Power BI registriert sein. 
* Sie müssen über ein Azure-Abonnement in Ihrem Organisationsverzeichnis verfügen.

### <a name="how-can-i-monitor-power-bi-embedded-capacity-consumption"></a>Überwachen der Kapazitätsnutzung von Power BI Embedded

* Verwenden Sie dazu das [Power BI Admin-Portal](../service-admin-portal.md#power-bi-embedded).

* Herunterladen der [Metrik-App](https://docs.microsoft.com/power-bi/service-admin-premium-monitor-capacity) in Power BI.

* Mithilfe von [Azure-Diagnoseprotokollierung](azure-pbie-diag-logs.md).

### <a name="can-my-capacity-scale-automatically-to-adjust-to-my-app-consumption"></a>Kann meine Kapazität automatisch an die Nutzung meiner App angepasst werden?

Derzeit wird zwar keine automatische Skalierung unterstützt. Sämtliche APIs können jedoch jederzeit skaliert werden.

### <a name="why-creatingscalingresuming-a-capacity-results-in-putting-the-capacity-into-a-suspended-state"></a>Weshalb führt das Erstellen/Skalieren/Fortsetzen einer Kapazität dazu, dass die Kapazität suspendiert wird?

Die Bereitstellung einer Kapazität (Skalieren/Fortsetzen/Erstellen) kann fehlschlagen. Sie können die API zum Abrufen von Details verwenden, um den ProvisioningState-Wert einer Kapazität zu überprüfen: [Kapazitäten: Abrufen von Details](https://docs.microsoft.com/rest/api/power-bi-embedded/capacities/getdetails).

### <a name="can-i-only-create-power-bi-embedded-capacities-in-a-specific-region"></a>Kann ich Power BI Embedded-Kapazitäten nur in einer bestimmten Region erstellen?

Mit dem Feature [Multi-Geo (Vorschau)](embedded-multi-geo.md) können Sie eine [Power BI Embedded-Kapazität](azure-pbie-create-capacity.md) in einer anderen Region als dem Standort Ihres Power BI-Basismandanten erwerben.

### <a name="why-cant-i-see-a-workspace-although-i-have-permissions"></a>Warum wird mir kein Arbeitsbereich angezeigt, obwohl ich die Berechtigungen dafür habe?

Wenn einem Benutzer die Berechtigung für einen Arbeitsbereich, eine App oder ein Artefakt erteilt wird, ist diese/r/s über API-Aufrufe möglicherweise nicht sofort verfügbar.
Dies kann zu einem fehlenden Artefakt in einer GET-API-Antwort oder einem Fehler bei der Verwendung des Artefakts führen.
Der Benutzer kann dieses Problem beheben, indem er die [refreshUserPermissions-API](https://docs.microsoft.com/rest/api/power-bi/users/refreshuserpermissions) aufruft, die die Benutzerberechtigungen aktualisiert.


### <a name="how-can-i-find-my-pbi-tenant-region"></a>Wie finde ich die Region meines Power BI-Mandanten heraus?

Über das Power BI-Portal können Sie die Region Ihres Power BI-Mandanten ermitteln.

Navigieren Sie zu https://app.powerbi.com/ > ? > Info

![Info](media/embedded-faq/about-01.png)
![Mandanten-Region](media/embedded-faq/tenant-location-01.png)

### <a name="what-does-the-cloud-solution-provider-csp-channel-support"></a>Wofür kann ich den Cloud Solution Provider-Kanal (CSP) nutzen?

* Sie können die Power BI Embedded-Kapazität für Ihren Mandanten mit einem CSP-Abonnement erstellen.
* Partnerkonten können sich beim Kundenmandanten anmelden, Power BI Embedded für diesen erwerben und einen Kundenmandanten als Administrator der Power BI-Kapazität festlegen.

### <a name="why-do-i-get-an-unsupported-account-message"></a>Weshalb erhalte ich eine Meldung, die besagt, dass mein Konto nicht unterstützt wird?

Sie müssen sich in Power BI mit einem Unternehmenskonto anmelden. Eine Anmeldung bei Power BI mit einem Microsoft-Konto wird nicht unterstützt.

### <a name="can-i-use-apis-to-create-and-manage-azure-capacities"></a>Kann ich Azure-Kapazitäten mit APIs erstellen und verwalten?

Ja, es gibt PowerShell-Cmdlets und Azure Resource Manager-APIs, mit denen Sie Power BI Embedded-Ressourcen erstellen und verwalten können.

* [REST-APIs](https://docs.microsoft.com/rest/api/power-bi-embedded/) 
* [PowerShell-Cmdlets](https://docs.microsoft.com/powershell/module/azurerm.powerbiembedded/)

### <a name="what-is-the-pbi-embedded-dedicated-capacity-role-in-a-pbi-embedded-solution"></a>Was ist die Power BI Embedded-Rolle „Dedizierte Kapazität“ in einer Power BI Embedded-Lösung?

Zur [Höherstufung Ihrer Lösung in die Produktion](embed-sample-for-customers.md#move-to-production) müssen Sie den Power BI-Inhalt (Arbeitsbereich), den Ihre Anwendung verwendet, einer Power BI Embedded-Kapazität (A-SKU) zuweisen.

### <a name="in-what-azure-regions-is-pbi-embedded-available"></a>In welchen Azure-Regionen ist Power BI Embedded verfügbar?

[PAM](https://ecosystemmanager.azurewebsites.net/home) (EcoManager): Weitere Informationen im Manager zur Produktverfügbarkeit

Verfügbare Regionen (16, die gleichen Regionen wie Power BI)

* USA (6): USA, Osten; USA, Osten 2; USA, Norden-Mitte; USA, Süden-Mitte; USA, Westen; USA, Westen 2
* Europa (2): Europa, Norden; Europa, Westen
* Asien-Pazifik (2): Asien, Südosten; Asien, Osten
* Brasilien (1): Brasilien, Süden
* Japan (1): Japan, Osten
* Australien (1): Australien, Südosten
* Indien (1): Indien, Westen
* Kanada (1): Kanada, Mitte
* Vereinigtes Königreich (1): Vereinigtes Königreich, Süden

### <a name="what-is-power-bi-embeddeds-authentication-model"></a>Welches Authentifizierungsmodell wird für Power BI Embedded verwendet?

Für Power BI Embedded wird weiterhin Azure AD für die Authentifizierung des Hauptbenutzers (ein festgelegter Benutzer mit Power BI Pro-Lizenz) verwendet, oder alternativ ein [Dienstprinzipal](embed-service-principal.md), der die Anwendung in Power BI authentifiziert.  

 Unabhängige Softwarehersteller können eigene Authentifizierungs- und Autorisierungsmethoden für ihre Anwendungen implementieren.

Sie können ein vorhandenes Verzeichnis verwenden, wenn Sie bereits einen Azure AD-Mandanten besitzen. Sie können zudem einen neuen Azure AD-Mandanten erstellen, um die Sicherheit der Inhalte Ihrer eingebetteten Anwendungen zu gewährleisten.

Sie eine der [Azure Active Directory-Authentifizierungsbibliotheken](https://docs.microsoft.com/azure/active-directory/develop/active-directory-authentication-libraries) verwenden, um ein AAD-Token abzurufen. Es sind Clientbibliotheken für mehrere Plattformen verfügbar.

### <a name="my-application-already-uses-aad-for-user-authentication-how-can-we-use-this-identity-when-authenticating-to-power-bi-in-a-user-owns-data-scenario"></a>Meine Anwendung verwendet bereits AAD für die Benutzerauthentifizierung Wie können wir diese Identität bei der Authentifizierung in Power BI in einem Szenario einsetzen, in dem der Benutzer die Daten besitzt?

Es ist standardmäßig ein OAuth-On-Behalf-Of-Fluss (<https://docs.microsoft.com/azure/active-directory/develop/web-api>). Sie müssen die Anwendung so konfigurieren, dass Berechtigungen für den Power BI-Dienst (mit den erforderlichen Bereichen) erforderlich sind. Sobald Sie über ein Benutzertoken für Ihre App verfügen, rufen Sie einfach die AcquireTokenAsync-Methode der ADAL-API mit dem Benutzerzugriffstoken auf, und geben Sie die Power BI-Ressourcen-URL als Ressourcen-ID an:

```csharp
var context = new AD.AuthenticationContext(authorityUrl);
var userAssertion = new AD.UserAssertion(userAccessToken);
var clientAssertion = new AD.ClientAssertionCertificate(MyAppId, MyAppCertificate)
var authenticationResult = await context.AcquireTokenAsync(resourceId, clientAssertion, userAssertion);
```

### <a name="what-object-id-is-the-service-principal-object-id"></a>Welche Objekt-ID ist die des Dienstprinzipals?

Die *Objekt-ID* auf dem Hauptbildschirm einer registrierten App ist die Objekt-ID für die App.

Die Objekt-ID im Abschnitt *Verwaltete Anwendung in lokalem Verzeichnis > Eigenschaften* ist die des Dienstprinzipals, die Sie verwenden müssen. Diese Objekt-ID verweist auf einen Dienstprinzipal für Vorgänge oder wird verwendet, um Änderungen an der Objekt-ID des Dienstprinzipals vorzunehmen. Dazu zählt beispielsweise, einen Dienstprinzipal als Administrator für einen Arbeitsbereich einzurichten.

### <a name="how-is-power-bi-embedded-different-from-other-azure-services"></a>Worin unterscheidet sich Power BI Embedded von anderen Azure-Diensten?

Sie müssen ein Power BI-Konto besitzen, bevor Sie Power BI Embedded in Azure erwerben können. Die Region, in der Power BI Embedded bereitgestellt wird, richtet sich nach Ihrem Power BI-Konto. Verwalten Sie Ihre Power BI Embedded-Ressource in Azure:

* Vertikale Skalierung
* Hinzufügen von Kapazitätsadministratoren
* Anhalten/Fortsetzen des Diensts

Verwenden Sie powerbi.com, um Ihrer Power BI Embedded-Kapazität Arbeitsbereiche zuzuweisen bzw. die Zuweisung aufzuheben.

### <a name="what-content-pack-data-types-can-you-embed"></a>Welche Datentypen für Inhaltspakete können eingebettet werden?

Sie können *keine* **Dashboards** und **Kacheln** einbetten, die über Inhaltspaketdatasets erstellt wurden. Sie *können* jedoch **Berichte** einbetten, die über Inhaltspaketdatasets erstellt wurden.

### <a name="what-is-the-difference-between-using-row-level-security-rls-vs-javascript-filters"></a>Worin besteht der Unterschied zwischen der Verwendung der Sicherheit auf Zeilenebene (RLS) und JavaScript-Filtern?

Häufig stellt sich die Frage, ob die Sicherheit auf Zeilenebene oder JavaScript-Filter verwendet werden sollten. Bei der einen Methode wird gesteuert, was ein bestimmter Benutzer sehen darf, bei der anderen wird die Ansicht des Benutzers optimiert.

Bei RLS steuert der ISV-Entwickler die Datenfilterung im Rahmen der Modellerstellung und Generierung des Einbettungstokens. Der Endbenutzer sieht nur die Daten, deren Anzeige der ISV dem Benutzer gestattet. In diesem Fall kann der Benutzer zwar weniger Daten anzeigen als durch den Filter zulässig, aber er kann die RLS-Konfiguration nicht umgehen und mehr Daten anzeigen als erlaubt.

Bei der clientseitigen Filterung (JavaScript) kann der unabhängige Softwarehersteller entscheiden, welche Daten dem Benutzer zunächst in der Ansicht angezeigt werden. Die Änderungen, die der Endbenutzer selbst auf die Ansicht anwendet, können jedoch nicht beeinflusst werden. Da JavaScript-Clientcode von Benutzern dazu führen kann, dass eine Datenfilterung im Back-End ausgelöst wird, wird diese Methode nicht als sicher angesehen.

Weitere Details finden Sie unter [Verwenden von RLS im Vergleich zu JavaScript-Filtern](embedded-row-level-security.md#using-rls-vs-javascript-filters).

### <a name="how-do-i-manage-permissions-for-service-principals-with-power-bi"></a>Wie verwalte ich Berechtigungen für Dienstprinzipale mit Power BI?

Sobald Sie festlegen, dass ein [Dienstprinzipal](embed-service-principal.md) mit Power BI verwendet werden soll, sind die AD-Berechtigungen der Anwendung nicht mehr wirksam. Die Anwendungsberechtigungen werden dann über das Power BI-Verwaltungsportal verwaltet.

Dienstprinzipale erben die Berechtigungen für alle Power BI-Mandanteneinstellungen von ihrer Sicherheitsgruppe. Wenn Berechtigungen eingeschränkt werden sollen, erstellen Sie eine dedizierte Sicherheitsgruppe für Dienstprinzipale und fügen diese der Liste **Ausgenommen spezifische Sicherheitsgruppen** für die relevanten, aktivierten Power BI-Einstellungen hinzu.

Dieser Schritt ist wichtig, wenn Sie den Dienstprinzipal als **Administrator** dem neuen Arbeitsbereich hinzufügen. Sie können diese Aufgabe über die [APIs](https://docs.microsoft.com/rest/api/power-bi/groups/addgroupuser) oder den Power BI-Dienst verwalten.

### <a name="when-to-use-an-application-id-vs-a-service-principal-object-id"></a>Wann wird eine Anwendungs-ID verwendet und wann eine Objekt-ID des DIenstprinzipals?

Die **[Anwendungs-ID](embed-sample-for-customers.md#application-id)** wird zum Erstellen des Zugriffstokens verwendet, wenn sie für die Authentifizierung übergeben wird.

Wenn Sie für Vorgänge auf einen Dienstprinzipal verweisen oder Änderungen vornehmen möchten, z.B. einen Dienstprinzipal als Administrator auf einen Arbeitsbereich anwenden, verwenden Sie die **[Objekt-ID des Dienstprinzipals](embed-service-principal.md#how-to-get-the-service-principal-object-id)** .

### <a name="can-you-manage-an-on-premises-data-gateway-with-service-principal"></a>Kann ich ein lokales Datengateway mit dem Dienstprinzipal verwalten?

Sie können ein lokales Datengateway (Datengateway) mit einem [Dienstprinzipal](embed-service-principal.md) nicht so wie mit einem Hauptkonto verwalten.

Mit einem Hauptkonto können Sie ein Datengateway installieren, Benutzer dem Gateway hinzufügen, eine Verbindung zu Datenquellen herstellen und weitere Verwaltungsaufgaben durchführen.

Mit einem Dienstprinzipal können Sie die [Sicherheit auf Zeilenebene (RLS)](embedded-row-level-security.md#on-premises-data-gateway-with-service-principal) über eine lokale SSAS-Datenquelle (SQL Server Analysis Services) mit Liveverbindung konfigurieren. So können Sie bei der Integration in **Power BI Embedded** über einen Dienstprinzipal Benutzer und deren Zugriff auf Daten in SSAS verwalten.

### <a name="can-you-sign-into-the-power-bi-service-with-service-principal"></a>Kann ich mich über den Dienstprinzipal beim Power BI-Dienst anmelden?

Nein, Sie können sich über den Dienstprinzipal nicht in Power BI anmelden.

Sie können ebenso als Benutzer in externen Anwendungen (SaaS-Einbettung) keine Inhalte nutzen, es sei denn, Sie erstellen ein Einbettungstoken.

### <a name="what-are-the-best-practices-to-improve-performance"></a>Welche bewährten Methoden zur Verbesserung der Leistung gibt es?

[Leistung von Power BI Embedded](embedded-performance-best-practices.md)

## <a name="licensing"></a>Lizenzierung

### <a name="how-do-i-purchase-power-bi-embedded"></a>Wie erwerbe ich Power BI Embedded?

Power BI Embedded ist über Azure erhältlich.

### <a name="what-happens-if-i-already-purchased-power-bi-premium-and-now-i-want-some-power-bi-embedded-in-azure-benefits"></a>Was geschieht, wenn ich Power BI Premium bereits erworben habe und jetzt einige der Vorteile von Power BI Embedded in Azure nutzen möchte?

Kunden zahlen bis zum Ende der Laufzeit ihrer aktuellen Vereinbarung weiterhin für vorhandene Power BI Premium-Lizenzen und können anschließend ihre Power BI Premium-Lizenzen nach Bedarf umstellen.

### <a name="do-i-still-have-to-buy-power-bi-premium-to-get-access-to-power-bi-embedded"></a>Muss ich Power BI Premium trotzdem erwerben, um auf Power BI Embedded zugreifen zu können?

Nein, Power BI Embedded umfasst die auf Azure basierende Kapazität, die Sie zum Bereitstellen und Verteilen Ihrer Lösung für Kunden benötigen.

### <a name="whats-the-purchase-commitment-for-power-bi-embedded"></a>Welche Verpflichtung ist mit dem Kauf von Power BI Embedded verbunden?

Kunden können ihre Nutzung auf Stundenbasis anpassen. Es gibt keine monatliche oder jährliche Verpflichtung für den Power BI Embedded-Dienst.

### <a name="how-does-the-usage-of-power-bi-embedded-show-up-on-my-bill"></a>Wie wird die Nutzung von Power BI Embedded auf meiner Rechnung aufgeführt?

Power BI Embedded wird nach einem feststehenden Stundensatz abgerechnet, der vom Typ der bereitgestellten Knoten abhängt. Solange eine Ressource aktiv ist, fallen Kosten an, auch wenn Sie die Ressource nicht nutzen. Sie müssen Ihre Ressource pausieren, um die Abrechnung zu unterbrechen.

### <a name="who-needs-a-power-bi-pro-license-for-power-bi-embedded-and-why"></a>Wer benötigt aus welchen Gründen eine Power BI Pro-Lizenz für Power BI Embedded?

Sie benötigen eine Power BI Pro-Lizenz oder einen [Dienstprinzipal](embed-service-principal.md), um REST-APIs nutzen zu können. Analysten benötigen entweder eine Power BI Pro-Lizenz oder einen Dienstprinzipal, um Berichte zu einem Power BI-Arbeitsbereich hinzufügen zu können. Administratoren benötigen eine Power BI Pro-Lizenz, um den Power BI-Mandanten und die Power BI-Kapazität zu verwalten.

Da Power BI Embedded die Verwendung des Power BI-Portals zum Verwalten und Überprüfen eingebetteter Inhalte zulässt, ist eine Power BI Pro-Lizenz erforderlich, um die App auf powerbi.com zu authentifizieren und Zugriff auf die Berichte in den richtigen Repositorys zu erhalten.

Allerdings benötigt der Endbenutzer keine Pro-Lizenz, um in seiner eigenen Anwendung [eingebettete Berichte erstellen oder bearbeiten](https://github.com/Microsoft/PowerBI-JavaScript/wiki/Create-Report-in-Embed-View) zu können, da er kein Power BI-Benutzer sein muss.

### <a name="can-i-get-started-for-free"></a>Ist ein kostenloser Einstieg möglich?

Ja, Sie können eine [Azure-Gutschrift](https://azure.microsoft.com/free/) für Power BI Embedded verwenden.

### <a name="can-i-get-a-trial-experience-for-power-bi-embedded-in-azure"></a>Ist eine Testversion von Power BI Embedded in Azure erhältlich?

Da Power BI Embedded Teil von Azure ist, können Sie den Dienst mit der [bei der Registrierung bei Azure erhaltenen Gutschrift über 200 USD](https://azure.microsoft.com/free/) verwenden.

### <a name="is-power-bi-embedded-available-for-national-clouds-us-government-germany-china"></a>Ist Power BI Embedded für nationale Clouds (US-Behörden, Deutschland, China) verfügbar?

Power BI Embedded ist auch für [nationale Clouds](embed-sample-for-customers-national-clouds.md) verfügbar.

### <a name="is-power-bi-embedded-available-for-non-profits-and-educational"></a>Ist Power BI Embedded für Non-Profit-Organisationen und Bildungseinrichtungen erhältlich?

Es gibt keine speziellen Azure-Preise für gemeinnützige Organisationen und Bildungseinrichtungen.

## <a name="power-bi-workspace-collection"></a>Power BI-Arbeitsbereichssammlung

### <a name="what-is-power-bi-workspace-collection"></a>Was ist eine Power BI-Arbeitsbereichssammlung?

Die **Power BI-Arbeitsbereichssammlung** (**Power BI Embedded** Version 1) ist eine Lösung, die auf der Azure-Ressource **Power BI-Arbeitsbereichssammlung** basiert. Mit dieser Lösung können Sie **Power BI Embedded**-Anwendungen für Ihre Kunden erstellen. Dabei verwenden Sie Power BI-Inhalte in der Lösung **Power BI-Arbeitsbereichssammlung**, dedizierte APIs und Schlüssel für die Arbeitsbereichssammlung, um die Anwendung bei Power BI zu authentifizieren.

### <a name="can-i-migrate-from-power-bi-workspace-collection-to-power-bi-embedded"></a>Kann ich eine Power BI-Arbeitsbereichssammlung zu Power BI Embedded migrieren?

1. Sie können das Migrationstool verwenden, um Inhalte einer **Power BI-Arbeitsbereichssammlung** in Power BI zu klonen: https://docs.microsoft.com/power-bi/developer/migrate-from-powerbi-embedded#content-migration.

2. Beginnen Sie mit dem Anwendungs-PoC für **Power BI Embedded**, der Power BI-Inhalte verwendet.

3. Wenn Sie bereits sind für den Produktionsbetrieb, erwerben Sie eine dedizierte **Power BI Embedded**-Kapazität und weisen Sie dieser Ihre Power BI-Inhalte (Arbeitsbereich) zu.

    > [!Note]
    > Sie können die **Power BI-Arbeitsbereichssammlung** weiter nutzen, während Sie parallel eine **Power BI Embedded**-Lösung für die Entwicklung verwenden. Sobald Sie bereit sind, können Sie Ihren Kunden zur neuen **Power BI Embedded**-Lösung verlagern und die **Power BI-Arbeitsbereichssammlung** außer Betrieb nehmen.

Weitere Informationen dazu finden Sie unter [Migrieren von Inhalten aus der Power BI-Arbeitsbereichssammlung zu Power BI Embedded](https://docs.microsoft.com/power-bi/developer/migrate-from-powerbi-embedded).

### <a name="is-power-bi-workspace-collection-on-a-deprecation-path"></a>Werden Power BI-Arbeitsbereichssammlungen demnächst eingestellt?

Ja, aber Kunden, die bereits eine **Power BI-Arbeitsbereichssammlung** verwenden, können diese weiter nutzen, bis sie eingestellt wird. Kunden können auch neue Arbeitsbereichssammlungen sowie **Power BI Embedded**-Anwendungen erstellen, die weiterhin die Lösung **Power BI-Arbeitsbereichssammlung** verwenden.

Das bedeutet jedoch auch, dass keine neuen Features mehr zu **Power BI-Arbeitsbereichssammlungen** hinzugefügt werden. Wir empfehlen unseren Kunden, ihre Migration zur neuen **Power BI Embedded**-Lösung zu planen.

### <a name="when-is-power-bi-workspace-collection-support-discontinued"></a>Wann wird der Support für die Power BI-Arbeitsbereichssammlung eingestellt?

Kunden, die die Lösung **Power BI-Arbeitsbereichssammlungen** bereits nutzen, können diese bis Ende Juni 2018 oder bis zum Ende ihrer Supportvereinbarung weiterhin verwenden.

### <a name="in-what-regions-can-i-create-a-pbi-workspace-collection"></a>In welchen Regionen kann ich Power BI-Arbeitsbereichssammlungen erstellen?

Folgende Regionen sind verfügbar: Australien, Südosten; Brasilien, Süden; Kanada, Mitte; USA, Osten 2; Japan, Osten; USA, Norden-Mitte; Europa, Norden; USA, Süden-Mitte; Asien, Südosten; Vereinigtes Königreich, Süden; Europa, Westen; Indien, Westen und USA, Westen.

### <a name="why-should-i-migrate-from-pbi-workspace-collection-to-power-bi-embedded"></a>Warum sollte ich eine Power BI-Arbeitsbereichssammlung zu Power BI Embedded migrieren?

**Power BI Embedded** enthält einige neue Features und Funktionen, die in der **Power BI-Arbeitsbereichssammlung** nicht genutzt werden können.

Dies sind einige dieser Features:
* Alle Power BI-Datenquellen werden unterstützt. Nur zwei Datenquellen der **Power BI-Arbeitsbereichssammlung** werden unterstützt. 
* Neue Features wie Q&A, Aktualisieren, Lesezeichen, Einbetten von Dashboards und Kacheln, benutzerdefinierte Menüs usw. werden nur in der Lösung **Power BI Embedded** unterstützt.
* Kapazitätsbasiertes Abrechnungsmodell.

## <a name="embedding-setup-tool"></a>Einbettungssetuptool

### <a name="what-is-the-embedding-setup-tool"></a>Was ist das Einbettungssetuptool?

Mit dem [Einbettungssetuptool](https://aka.ms/embedsetup) können Sie schnell einsteigen und eine Beispielanwendung herunterladen, um mit dem Einbetten mit Power BI zu beginnen.

### <a name="which-solution-should-i-choose"></a>Welche Lösung soll ich verwenden?

* Das [Einbetten für Ihre Kunden](embedding.md#embedding-for-your-customers) bietet die Möglichkeit, Dashboards und Berichte für Benutzer einzubetten, die nicht über ein Konto für Power BI verfügen. Führen Sie die Lösung [Einbetten für Ihre Kunden](https://aka.ms/embedsetup/AppOwnsData) aus.
* Das [Einbetten für Ihre Organisation](embedding.md#embedding-for-your-organization) ermöglicht Ihnen das Erweitern des Power BI-Diensts. Führen Sie die Lösung [Einbetten für Ihre Organisation](https://aka.ms/embedsetup/UserOwnsData) aus.

### <a name="ive-downloaded-the-sample-app-which-solution-do-i-choose"></a>Ich habe die Beispiel-App heruntergeladen. Welche Lösung soll ich verwenden?

Wenn Sie mit dem Szenario **Einbetten für Ihre Kunden arbeiten**, speichern und entzippen Sie die Datei *PowerBI-Developer-Samples.zip*. Öffnen Sie anschließend den Ordner *PowerBI-Developer-Samples-master\App Owns Data*, und führen Sie die Datei *PowerBIEmbedded_AppOwnsData.sln* aus.

Wenn Sie mit dem Szenario **Einbetten für Ihre Organisation arbeiten**, speichern und entzippen Sie die Datei *PowerBI-Developer-Samples.zip*. Öffnen Sie dann den Ordner *PowerBI-Developer-Samples-master\User Owns Data\integrate-report-web-app*, und führen Sie die Datei *pbi-saas-embed-report.sln* aus.

### <a name="how-can-i-edit-my-registered-application"></a>Wie kann ich meine registrierte Anwendung bearbeiten?

Wie Sie mit Azure AD-registrierte Anwendungen bearbeiten können, erfahren Sie unter [Schnellstart: Aktualisieren einer Anwendung in Azure Active Directory](https://docs.microsoft.com/azure/active-directory/develop/quickstart-v1-update-azure-ad-app).

### <a name="how-can-i-edit-my-power-bi-user-profile-or-data"></a>Wie kann ich mein Power BI-Benutzerprofil bzw. meine Power BI-Benutzerdaten bearbeiten?

[Hier](https://docs.microsoft.com/power-bi/service-basic-concepts) erfahren Sie, wie Sie Ihre Power BI-Daten bearbeiten.

Weitere Informationen finden Sie unter [Problembehandlung bei Embedded-Anwendungen](embedded-troubleshoot.md).

Weitere Fragen? [Wenden Sie sich an die Power BI-Community](https://community.powerbi.com/)
