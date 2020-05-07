---
title: Entwickeln mithilfe der REST-APIs für Power BI-Berichtsserver
description: Die REST-API bietet programmgesteuerten Zugriff auf die Objekte in einem Katalog für Power BI-Berichtsserver.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.topic: conceptual
ms.date: 05/25/2018
ms.openlocfilehash: 9b8e795c4a55f9efd6fd534d92d95b36c93cf2c0
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "73874078"
---
# <a name="develop-with-the-rest-apis-for-power-bi-report-server"></a>Entwickeln mithilfe der REST-APIs für Power BI-Berichtsserver

Power BI Report Server unterstützt REST-APIs (Representational State Transfer). Die REST-APIs sind Dienstendpunkte, die eine Reihe von HTTP-Vorgängen (Methoden) unterstützen, die Erstellungs-, Abruf-, Aktualisierungs- oder Löschzugriff auf Ressourcen in einem Berichtsserver bieten.

Die REST-API bietet programmgesteuerten Zugriff auf die Objekte in einem Katalog für Power BI-Berichtsserver. Beispiele für Objekte sind Ordner, Berichte, KPIs, Datenquellen, Datasets, Aktualisierungspläne, Abonnements und vieles mehr. Mit der REST-API können Sie beispielsweise durch die Ordnerhierarchie navigieren, den Inhalt eines Ordners durchsuchen oder eine Berichtsdefinition herunterladen. Außerdem können Sie Objekte erstellen, aktualisieren und löschen. Beispiele für das Arbeiten mit Objekten sind das Hochladen eines Berichts, das Ausführen eines Aktualisierungsplans, das Löschen eines Ordners usw.

[!INCLUDE [GDPR-related guidance](../includes/gdpr-hybrid-note.md)]

## <a name="components-of-a-rest-api-requestresponse"></a>Komponenten einer REST-API-Anforderung/-Antwort

Ein REST API-Anforderungs-/Antwortpaar kann in fünf Komponenten unterteilt werden:

* Den **Anforderungs-URI**, der aus Folgendem besteht: `{URI-scheme} :// {URI-host} / {resource-path} ? {query-string}`. Der Anforderungs-URI ist zwar im Nachrichtenheader der Anforderung enthalten, er wird jedoch hier separat aufgerufen, da die meisten Sprachen und Frameworks erfordern, dass er separat von der Anforderungsnachricht übergeben wird.
  
  * URI-Schema: Gibt das Protokoll an, mit dem die Anforderung übertragen wird. Beispiele sind `http` und `https`.
  * URI-Host: Gibt den Domänennamen oder die IP-Adresse des Servers an, auf dem der REST-Dienstendpunkt gehostet wird, beispielsweise `myserver.contoso.com`.
  * Ressourcenpfad: Gibt die Ressource oder die Ressourcensammlung an, die mehrere Segmente enthalten, anhand derer der Dienst die Auswahl der betreffenden Ressourcen bestimmt. Beispiel: `CatalogItems(01234567-89ab-cdef-0123-456789abcdef)/Properties` kann verwendet werden, um die angegebenen Eigenschaften für das CatalogItem abzurufen.
  * Abfragezeichenfolge (optional): Gibt zusätzliche einfache Parameter an, z.B. die API-Version oder die Ressourcenauswahlkriterien.
* Headerfelder der HTTP-Anforderungsnachricht:
  
  * Eine erforderliche [HTTP-Methode](https://www.w3.org/Protocols/rfc2616/rfc2616-sec9.html) (die auch als Vorgang oder Verb bezeichnet wird), die dem Dienst den Typ des angeforderten Vorgangs mitteilt. Reporting Services-REST-APIs unterstützen DELETE-, GET-, HEAD-, PUT-, POST- und PATCH-Methoden.
  * Optionale zusätzliche Headerfelder, die jeweils durch die angegebene URI- und HTTP-Methode gefordert werden.
* Optionale Felder für den HTTP-**Anforderungsnachrichtentext**, um den URI- und HTTP-Vorgang zu unterstützen. POST-Vorgänge enthalten beispielsweise MIME-codierte Objekte, die als komplexe Parameter übergeben werden. Für POST- oder PUT-Vorgänge muss auch der MIME-Codierungstyp für den Text im `Content-type`-Anforderungsheader angegeben werden. Für einige Dienste muss ein bestimmter MIME-Typ verwendet werden, z.B. `application/json`.
* **Nachrichtenheaderfelder mit HTTP-Anworten**:
  
  * Ein [HTTP-Statuscode](https://www.w3.org/Protocols/HTTP/HTRESP.html), der 2xx Erfolgscodes bis zu 4xx oder 5xx Fehlercodes enthalten kann. Alternativ kann ein vom Dienst definierter Statuscode zurückgegeben werden, entsprechend der Angabe in der API-Dokumentation.
  * Optionale zusätzliche Headerfelder, die jeweils zum Unterstützen der Antwort auf die Anforderung erforderlich sein können, z.B. ein `Content-type`-Antwortheader.
* Optionale Felder für den HTTP-**Antwortnachrichtentext**:
  
  * MIME-codierte Antwortobjekte werden im HTTP-Antworttext zurückgegeben, z.B. eine Antwort einer GET-Methode, die Daten zurückgibt. Normalerweise werden diese Objekte in einem strukturierten Format wie JSON oder XML zurückgegeben, entsprechend der Angabe im `Content-type`-Antwortheader.

## <a name="api-documentation"></a>API-Dokumentation

Eine moderne REST-API benötigt eine moderne API-Dokumentation. Die REST-API baut auf der OpenAPI-Spezifikation (auch bezeichnet als Swagger-Spezifikation) auf, und die Dokumentation ist verfügbar auf [SwaggerHub](https://app.swaggerhub.com/apis/microsoft-rs/PBIRS/2.0). Über das Dokumentieren der API hinaus trägt SwaggerHub zum Generieren einer Clientbibliothek in der Sprache Ihrer Wahl bei – JavaScript, TypeScript, C#, Java, Python, Ruby usw.

## <a name="testing-api-calls"></a>Testen von API-Aufrufen

[Fiddler](https://www.telerik.com/fiddler) ist ein Tool zum Testen von HTTP-Anforderungs- bzw. Antwortnachrichten. Fiddler ist ein kostenloser Webdebugproxy, der Ihre REST-Anforderungen abfangen kann, wodurch die HTTP-Anforderungs-/Antwortnachrichten auf einfache Weise diagnostiziert werden können.

## <a name="next-steps"></a>Weitere Schritte

Prüfen Sie die verfügbaren APIs im [SwaggerHub](https://app.swaggerhub.com/apis/microsoft-rs/PBIRS/2.0).

Beispiele sind auf [GitHub](https://github.com/Microsoft/Reporting-Services) verfügbar. Das Beispiel enthält eine HTML5-App, die auf TypeScript, React und webpack aufbaut, sowie ein PowerShell-Beispiel.

Weitere Fragen? [Stellen Sie Ihre Frage in der Power BI-Community.](https://community.powerbi.com/)