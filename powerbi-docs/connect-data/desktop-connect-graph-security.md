---
title: Herstellen einer Verbindung mit der Microsoft Graph-Sicherheits-API in Power BI Desktop
description: Einfaches Herstellen einer Verbindung mit der Microsoft Graph-Sicherheits-API in Power BI Desktop
author: preetikr
ms.reviewer: ''
ms.custom: seojan19
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 01/29/2019
ms.author: preetikr
LocalizationGroup: Connect to data
ms.openlocfilehash: c691446d7cc9a976e38cab5aefc385c988cb1552
ms.sourcegitcommit: bfc2baf862aade6873501566f13c744efdd146f3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/13/2020
ms.locfileid: "83347767"
---
# <a name="connect-to-the-microsoft-graph-security-api-in-power-bi-desktop"></a>Herstellen einer Verbindung mit der Microsoft Graph-Sicherheits-API in Power BI Desktop

Mit dem Microsoft Graph-Sicherheitsconnector von Power BI Desktop stellen Sie eine Verbindung mit der [Microsoft Graph-Sicherheits-API](https://aka.ms/graphsecuritydocs) her. Anschließend können Sie Dashboards und Berichte erstellen, um Erkenntnisse aus Ihren [Sicherheitswarnungen](https://docs.microsoft.com/graph/api/resources/alert?view=graph-rest-1.0) und [Sicherheitsbewertungen](https://docs.microsoft.com/graph/api/resources/securescores?view=graph-rest-beta) zu gewinnen.

Die Microsoft Graph-Sicherheits-API verbindet [mehrere Sicherheitslösungen](https://aka.ms/graphsecurityalerts) von Microsoft und dessen Ökosystempartnern, um die Korrelation von Warnungen zu vereinfachen. Diese Kombination ermöglicht den Zugriff auf umfangreiche Kontextinformationen und vereinfacht die Automatisierung. Organisationen können auf diese Weise in kurzer Zeit Erkenntnisse gewinnen und mit unterschiedlichen Sicherheitsprodukten entsprechend reagieren. Gleichzeitig verringern sich dabei für Organisationen die Kosten und die Komplexität.

## <a name="prerequisites-to-use-the-microsoft-graph-security-connector"></a>Voraussetzungen zur Verwendung des Microsoft Graph-Sicherheitsconnectors

Wenn Sie den Microsoft Graph-Sicherheitsconnector verwenden möchten, müssen Sie *explizit* die Einwilligung des Azure AD-Mandantenadministrators einholen. Weitere Informationen finden Sie unter [Authentifizierungsanforderungen der Microsoft Graph-Sicherheits-API](https://aka.ms/graphsecurityauth).
Für die Einwilligung sind die Anwendungs-ID und der Anwendungsname des Connectors erforderlich. Diese sind im Folgenden aufgeführt und auch im [Azure-Portal](https://portal.azure.com) verfügbar:

| Eigenschaft | Wert |
|----------|-------|
| **Anwendungsname** | `MicrosoftGraphSecurityPowerBIConnector` |
| **Anwendungs-ID** | `cab163b7-247d-4cb9-be32-39b6056d4189` |
|||

Der Administrator Ihres Azure AD-Mandanten kann eine der folgenden Methoden nutzen, um in die Verwendung des Connectors einzuwilligen:

* [Erteilen der Einwilligung für Azure AD-Anwendungen](https://docs.microsoft.com/azure/active-directory/develop/v2-permissions-and-consent)

* Reagieren auf Anforderungen, die Ihre Logik-App bei der ersten Ausführung über [Benutzeroberflächen zum Erteilen von Einwilligungen für Anwendungen](https://docs.microsoft.com/azure/active-directory/develop/application-consent-experience) übermittelt
   
Dem Benutzerkonto, das sich beim Microsoft Graph-Sicherheitsconnector anmeldet, muss die Azure AD-Rolle „Sicherheitsleseberechtigter“ zugewiesen sein, **falls** der Benutzer kein Mitglied der Rolle *Sicherheitsadministrator* ist. Weitere Informationen finden Sie unter [Assign Azure AD roles to users (Zuweisen von Azure AD-Rollen zu Benutzern)](https://docs.microsoft.com/graph/security-authorization#assign-azure-ad-roles-to-users).

## <a name="using-the-microsoft-graph-security-connector"></a>Verwenden des Microsoft Graph-Sicherheits-Connectors

Gehen Sie wie folgt vor, um den Connector zu verwenden:

1. Klicken Sie in Power BI Desktop im Menüband **Start** auf **Daten abrufen** > **Mehr**.
2. Wählen Sie links im Fenster aus der Liste der Kategorien **Onlinedienste** aus.
3. Wählen Sie **Microsoft Graph Security (Beta)** (Microsoft Graph-Sicherheit (Beta)) aus.

    ![Dialogfeld „Daten abrufen“](media/desktop-connect-graph-security/GetData.PNG)
    
4. Wählen Sie im Fenster **Microsoft Graph Security** (Microsoft Graph-Sicherheit) die Microsoft Graph-API-Version **v1.0** oder **beta** aus.

    ![Dialogfeld zum Auswählen der Version](media/desktop-connect-graph-security/selectVersion.PNG)
    
5. Melden Sie sich bei Ihrem Azure Active Directory-Konto an, wenn Sie dazu aufgefordert werden. Wie bereits im vorherigen Abschnitt erwähnt wurde, muss für dieses Konto die Rolle *Sicherheitsleseberechtigter* oder *Sicherheitsadministrator* festgelegt sein.

    ![Anmelden](media/desktop-connect-graph-security/SignIn.PNG) 
    
6. Wenn Sie Mandantenadministrator sind *und* noch nicht über die Einwilligung für die Microsoft Graph-Sicherheitsconnectoranwendung in Power BI verfügen, wird das folgende Dialogfeld angezeigt. Aktivieren Sie das Kontrollkästchen neben **Zustimmung im Namen Ihrer Organisation**.

    ![Dialogfeld für Einwilligung des Administrators](media/desktop-connect-graph-security/AdminConsent.PNG)
    
7. Nach Ihrer Anmeldung wird das folgende Dialogfeld angezeigt, in dem Sie darauf hingewiesen werden, dass Sie authentifiziert wurden. Wählen Sie **Verbinden** aus.

    ![Dialogfeld „Sie sind derzeit angemeldet.“](media/desktop-connect-graph-security/SignedIn.PNG)
    
8. Nachdem Sie eine Verbindung hergestellt haben, werden im Fenster **Navigator** Warnungen, Sicherheitsbewertungen und andere in der [Microsoft Graph-Sicherheits-API](https://aka.ms/graphsecuritydocs) verfügbare Entitäten für die Version angezeigt, die Sie in Schritt 4 ausgewählt haben. Wählen Sie mindestens eine Entität aus, die Sie importieren und in Power BI Desktop verwenden möchten. Klicken Sie anschließend auf **Laden**, um die Ergebnisansicht aufzurufen, die unter Schritt 9 zu sehen ist.

    ![Navigator-Dialogfeld](media/desktop-connect-graph-security/NavTable.PNG)
    
9. Wenn Sie eine erweiterte Abfrage der Microsoft Graph-Sicherheits-API ausführen möchten, wählen Sie die Funktion **Specify custom Microsoft Graph Security URL to filter results** (Angeben einer benutzerdefinierten Microsoft Graph-Sicherheits-URL zum Filtern von Ergebnissen) aus. Verwenden Sie diese Funktion, um eine [OData.Feed](https://docs.microsoft.com/power-bi/desktop-connect-odata)-Abfrage mit den erforderlichen Berechtigungen an die Microsoft Graph-Sicherheits-API zu senden.

   Im folgenden Beispiel wird der `https://graph.microsoft.com/v1.0/security/alerts?$filter=Severity eq 'High'` *serviceUri* verwendet. Unter [OData-Systemabfrageoptionen](https://docs.microsoft.com/graph/query-parameters) finden Sie Informationen dazu, wie Sie Abfragen zum Filtern, Sortieren oder Abrufen der aktuellen Ergebnisse erstellen.

   ![OData.Feed-Beispiel](media/desktop-connect-graph-security/ODataFeed.PNG)
    
   Wenn Sie auf **Aufrufen** klicken, ruft die **OData.Feed**-Funktion die API auf, wodurch der Abfrage-Editor geöffnet wird. Filtern Sie die zu verwendenden Daten, und schränken Sie sie weiter ein. Laden Sie diese anschließend in Power BI Desktop hoch.

Das Ergebnisfenster für die abgefragten Microsoft Graph-Sicherheitsentitäten sieht wie folgt aus:

   ![Beispiel für Ergebnisfenster](media/desktop-connect-graph-security/Result.PNG)
    

Nun können Sie die Daten, die Sie mit dem Microsoft Graph-Sicherheitsconnector importiert haben, in Power BI Desktop verwenden. Sie können Grafiken oder Berichte erstellen. Alternativ können Sie auch mit weiteren Daten arbeiten, die Sie aus Excel-Arbeitsmappen, Datenbanken oder anderen Datenquellen importieren.

## <a name="next-steps"></a>Nächste Schritte
* Testen Sie Power BI-Beispiele und -Vorlagen, in denen dieser Connector verwendet wird, mit den Ressourcen unter [Microsoft Graph Security GitHub Power BI sample repo (GitHub-Repository mit Power BI-Beispielen für die Microsoft Graph-Sicherheits-API)](https://aka.ms/graphsecuritypowerbiconnectorsamples).

* Benutzerszenarios und zusätzliche Informationen finden Sie im [Blogbeitrag zum Microsoft Graph-Sicherheitsconnector in Power BI](https://aka.ms/graphsecuritypowerbiconnectorblogpost).

* Es gibt viele verschiedene Arten von Datenquellen, mit denen Sie über Power BI Desktop eine Verbindung herstellen können. Weitere Informationen finden Sie in den folgenden Artikeln:

    * [Was ist Power BI Desktop?](../fundamentals/desktop-what-is-desktop.md)
    * [Datenquellen in Power BI Desktop](desktop-data-sources.md)
    * [Strukturieren und Kombinieren von Daten mit Power BI Desktop](desktop-shape-and-combine-data.md)
    * [Verbinden mit Excel in Power BI Desktop](desktop-connect-excel.md)
    * [Eingeben von Daten direkt in Power BI Desktop](desktop-enter-data-directly-into-desktop.md)
