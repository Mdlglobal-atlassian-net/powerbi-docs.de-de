---
title: Power BI-Berechtigungen
description: Power BI-Berechtigungen
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 10/01/2018
ms.openlocfilehash: 51c43a19613381d39e0397864e55baed2022663c
ms.sourcegitcommit: abc8419155dd869096368ba744883b865c5329fa
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/18/2020
ms.locfileid: "79487192"
---
# <a name="power-bi-permissions"></a>Power BI-Berechtigungen

## <a name="permission-scopes"></a>Berechtigungsbereiche

Mit Power BI-Berechtigungen kann eine Anwendung bestimmte Aktionen im Namen des Benutzers ausführen. Berechtigungen sind erst gültig, wenn sie von einem Benutzer genehmigt wurden.

| Anzeigename | Beschreibung | Bereichswert |
| --- | --- | --- |
| Alle Datasets anzeigen |Die App kann alle Datasets für den angemeldeten Benutzer und Datasets, auf die der Benutzer Zugriff hat, anzeigen. |Dataset.Read.All |
| Alle Datasets lesen und schreiben |Die App kann alle Datasets für den angemeldeten Benutzer und Datasets, auf die der Benutzer Zugriff hat, anzeigen und darin schreiben. |Dataset.ReadWrite.All |
| Daten einem Dataset eines Benutzers hinzufügen |Erteilt einer App Zugriff zum Hinzufügen oder Löschen der Dataset-Zeilen eines Benutzers. Diese Berechtigung gewährt der App keinen Zugriff auf die Daten des Benutzers. |Data.Alter_Any |
| Inhalt erstellen |Die App kann automatisch Inhalt und Datasets für einen Benutzer erstellen. |Content.Create |
| Benutzergruppen anzeigen |Die App kann alle Gruppen anzeigen, denen der angemeldete Benutzer angehört. |Group.Read |
| Alle Gruppen anzeigen |Die App kann alle Gruppen anzeigen, denen der angemeldete Benutzer angehört. |Group.Read.All |
| Alle Gruppen lesen und schreiben |Die App kann alle Gruppen für den angemeldeten Benutzer und alle Gruppen, auf die der Benutzer Zugriff hat, anzeigen und in ihnen schreiben. |Group.ReadWrite.All |
| Alle Dashboards anzeigen |Die App kann alle Dashboards für den angemeldeten Benutzer und Dashboards, auf die der Benutzer Zugriff hat, anzeigen. |Dashboard.Read.All |
| Alle Berichte anzeigen |Die App kann alle Berichte für den angemeldeten Benutzer anzeigen sowie Berichte, auf die der Benutzer Zugriff hat. Die App kann ebenso die Daten in den Berichten sowie den Aufbau der Berichte anzeigen. |Report.Read.All |
| Alle Berichte lesen und schreiben |Die App kann alle Berichte für den angemeldeten Benutzer und alle Berichte, auf die der Benutzer Zugriff hat, anzeigen und darin schreiben. Hiermit wird nicht das Recht erteilt, neue Berichte zu erstellen. |Report.ReadWrite.All |
| Alle Kapazitäten lesen und schreiben |Die App kann alle Kapazitäten für den angemeldeten Benutzer und alle Kapazitäten, auf die der Benutzer Zugriff hat, anzeigen und in ihnen schreiben. Hiermit wird nicht das Recht zum Erstellen neuer Kapazitäten erteilt. |Capacities.ReadWrite.All |
| Alle Kapazitäten lesen |Die App kann alle Kapazitäten für den angemeldeten Benutzer und alle Kapazitäten, auf die der Benutzer Zugriff hat, anzeigen und in ihnen schreiben. Hiermit wird nicht das Recht zum Erstellen neuer Kapazitäten erteilt. |Capacities.Read.All |
| Alle Inhalte im Mandanten lesen und schreiben |Die App kann alle Artefakte, z.B. Gruppen, Berichte, Dashboards und Datasets, in Power BI anzeigen und in ihnen schreiben. Vorausgesetzt, der angemeldete Benutzer ist ein Power BI-Dienstadministrator. |Tenant.ReadWrite.All |
| Alle Inhalte im Mandanten anzeigen |Die App kann alle Artefakte, z.B. Gruppen, Berichte, Dashboards und Datasets, in Power BI anzeigen. Vorausgesetzt, der angemeldete Benutzer ist ein Power BI-Dienstadministrator. |Tenant.Read.All |

Eine Anwendung kann bei der ersten Anmeldung auf der Seite eines Benutzers Berechtigungen anfordern. Die angeforderten Berechtigungen werden im Bereichsparameter des Aufrufs übergeben. Wenn die Berechtigungen gewährt werden, wird ein Zugriffstoken an die App zurückgegeben, das für zukünftige API-Aufrufe verwendet werden kann. Der Zugriff ist nur für eine bestimmte Anwendung möglich.

> [!NOTE]
> In Power BI-APIs werden Arbeitsbereiche weiterhin als Gruppen bezeichnet. Alle Verweise auf Gruppen bedeuten, dass Sie mit Arbeitsbereichen arbeiten.

## <a name="requesting-permissions"></a>Anfordern von Berechtigungen

Sie können die API aufrufen, um sich mit einem Benutzernamen und einem Kennwort zu authentifizieren und im Namen eines anderen Benutzers Aktionen ausführen. Zu diesem Zweck müssen jedoch Berechtigungen angefordert und vom Benutzer genehmigt werden. Daraufhin wird bei allen zukünftigen Aufrufen das zurückgegebene Zugriffstoken gesendet. Bei diesem Vorgang befolgen wir das Standardprotokoll [OAuth 2.0](https://oauth.net/2/). Während die tatsächliche Implementierung variieren kann, beinhaltet der OAuth-Flow für Power BI die folgenden Elemente:

* **Anmeldebenutzeroberfläche**: Über diese Benutzeroberfläche kann der Entwickler Berechtigungen anfordern. Der Benutzer muss sich hierfür anmelden, sofern er dies nicht bereits getan hat. Zudem muss der Benutzer die von der Anwendung angeforderten Berechtigungen genehmigen. Das Anmeldefenster sendet einen Zugriffscode oder eine Fehlermeldung an eine festgelegte Umleitungs-URL zurück.
  * In Power BI sollte für native Anwendungen eine Standard-Umleitungs-URL angegeben werden.
* **Autorisierungscode**: Autorisierungscodes werden nach der Anmeldung über URL-Parameter in der Umleitungs-URL für Webanwendungen zurückgegeben. Da sie in Parametern enthalten sind, besteht ein gewisses Sicherheitsrisiko. Webanwendungen müssen den Autorisierungscode gegen ein Autorisierungstoken austauschen.
* **Autorisierungstoken**: Werden verwendet, um API-Aufrufe im Namen eines anderen Benutzers zu authentifizieren. Sie sind auf eine bestimmte Anwendung begrenzt. Token haben eine feste Lebensdauer und müssen nach Ablauf aktualisiert werden.
* **Aktualisierungstoken** : Token werden nach ihrem Ablauf aktualisiert.

Weitere Fragen? [Stellen Sie Ihre Frage in der Power BI-Community.](https://community.powerbi.com/)