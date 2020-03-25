---
title: Zertifizierte Power BI-Visuals
description: Anforderungen und Vorgehensweise für das Einreichen eines benutzerdefinierten Visuals zur Zertifizierung sowie eine Liste der zertifizierten Power BI-Visuals.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
featuredvideoid: ''
ms.service: powerbi
ms.topic: conceptual
ms.subservice: powerbi-custom-visuals
ms.date: 03/08/2020
ms.openlocfilehash: 2dee596648c9921cefab6903167e780bfacb122e
ms.sourcegitcommit: 2c798b97fdb02b4bf4e74cf05442a4b01dc5cbab
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/21/2020
ms.locfileid: "80113898"
---
# <a name="get-a-power-bi-visual-certified"></a>So lassen Sie sich ein Power BI-Visual zertifizieren

Zertifizierte Power BI-Visuals sind Power BI-Visuals in [AppSource](https://appsource.microsoft.com/en-us/marketplace/apps?page=1&product=power-bi-visuals), die den [Codeanforderungen](#certification-requirements) des Microsoft Power BI-Teams entsprechen. Diese Visuals wurden getestet, um sicherzustellen, dass sie nicht auf externe Dienste oder Ressourcen zugreifen und dass sie sicheren Codierungsmustern und -richtlinien folgen.

Wenn ein Power BI-Visual zertifiziert wurde, bietet es mehr Features. Beispielsweise können Sie ein Visual [nach PowerPoint exportieren](../../consumer/end-user-powerpoint.md) oder in empfangenen E-Mails anzeigen, wenn ein Benutzer [Berichtsseiten abonniert](../../consumer/end-user-subscribe.md).

Der Zertifizierungsprozess ist optional. Power BI-Visuals ohne Zertifizierung sind nicht notwendigerweise unsicher. Einige Power BI-Visuals sind nicht zertifiziert, weil sie mindestens eine [Zertifizierungsanforderung](power-bi-custom-visuals-certified.md#certification-requirements) nicht erfüllen. Beispiele: Ein Power BI-Kartenvisual, das eine Verbindung mit einem externen Dienst herstellt, oder ein Power BI-Visual, das kommerzielle Bibliotheken verwendet.

> [!NOTE]
> Microsoft ist nicht der Autor von Power BI-Visuals von Drittanbietern. Um die Funktionalität eines Drittanbietervisuals zu verifizieren, wenden Sie sich direkt an den Autor.

## <a name="certification-requirements"></a>Zertifizierungsanforderungen

Damit Ihr Power BI-Visual [zertifiziert](#get-a-power-bi-visual-certified) werden kann, muss es die in diesem Abschnitt aufgeführten Anforderungen erfüllen. 

### <a name="general-requirements"></a>Allgemeine Anforderungen

Ihr Power BI-Visual muss von Partner Center genehmigt werden. Es empfiehlt sich, das Power BI-Visual bereits vorher in [AppSource](https://appsource.microsoft.com/marketplace/apps?page=1&product=power-bi-visuals) bereitzustellen. Informationen zum Veröffentlichen eines Power BI-Visuals in AppSource finden Sie unter [Veröffentlichen von Power BI-Visuals in Partner Center](office-store.md).

Bevor Sie Ihre Power BI-Visual zur Zertifizierung einreichen, überprüfen Sie, ob es den [Richtlinien für Power BI-Visuals](guidelines-powerbi-visuals.md) entspricht.

Stellen Sie beim Einreichen des Power BI-Visuals sicher, dass das kompilierte Paket exakt mit dem eingereichten Paket übereinstimmt.

### <a name="code-repository-requirements"></a>Anforderungen in Bezug auf das Coderepository

Sie müssen Ihren Code zwar nicht öffentlich auf GitHub freigeben, aber das Coderepository muss dem Power BI-Team zur Überprüfung zur Verfügung stehen. Die beste Möglichkeit hierfür besteht darin, den Quellcode (JavaScript oder TypeScript) auf GitHub bereitzustellen.

Das Repository muss Folgendes enthalten:
* Code für eine einzelne Power BI-Visualisierung. Es darf weder Code für mehrere Power BI-Visuals noch Code enthalten, der in keinem Zusammenhang mit dem Visual steht.
* Einen Branch namens **certification** („Zertifizierung“, Kleinschreibung erforderlich). Der Quellcode in diesem Branch muss mit dem eingereichten Paket übereinstimmen. Dieser Code kann erst während des nächsten Einreichungsprozesses aktualisiert werden, wenn Sie das Power BI-Visual erneut einreichen.

Wenn Ihr Power BI-Visual private npm-Pakete oder git-Untermodule verwendet, müssen Sie Zugriff auf die zusätzlichen Repositorys bereitstellen, die diesen Code enthalten.

Der Aufbau eines visuellen Power BI-Repositorys ist im GitHub-Repository im [Beispielbalkendiagramm für Power BI-Visualisierungen](https://github.com/microsoft/PowerBI-visuals-sampleBarChart) gezeigt.

### <a name="file-requirements"></a>Anforderungen in Bezug auf Dateien

Verwenden Sie die neueste Version der API, um Ihr Power BI-Visual zu schreiben.

Das Repository muss die folgenden Dateien enthalten:
* **.gitignore**: Fügen Sie dieser Datei `node_modules`, `.tmp` und `dist` hinzu. Der Code darf die Ordner *node_modules*, *.tmp* oder *dist* nicht enthalten.
* **capabilities.json**: Wenn Sie eine neuere Version Ihres Power BI-Visuals mit Änderungen an den Eigenschaften in dieser Datei einreichen, stellen Sie sicher, dass diese nicht zu Fehlern bei Berichten für vorhandene Benutzer führen.
* **pbiviz.json** 
* **package.json**: Für das Visual müssen die folgenden Pakete installiert sein:
   * [tslint](https://www.npmjs.com/package/tslint)-Version 5.18.0 oder höher
   * [typescript](https://www.npmjs.com/package/typescript)-Version 3.0.0 oder höher
   * [tslint-microsoftcontrib](https://www.npmjs.com/package/tslint-microsoft-contrib)-Version 6.2.0 oder höher
   * Die Datei muss einen Befehl zum Ausführen von Linter enthalten: `"lint": "tslint -c tslint.json -p tsconfig.json"`
* **package-lock.json**
* **tsconfig.json**

### <a name="command-requirements"></a>Anforderungen in Bezug auf Befehle

Stellen Sie sicher, dass die folgenden Befehle keine Fehler zurückgeben.

* `npm install`
* `pbiviz package`
* `npm audit` darf keine Warnungen mit hohem oder mittlerem Schweregrad zurückgeben.
* [TSLint von Microsoft](https://www.npmjs.com/package/tslint-microsoft-contrib) mit der [erforderlichen Konfiguration](https://github.com/microsoft/PowerBI-visuals-sampleBarChart/blob/master/tslint.json). Dieser Befehl darf keine lint-Fehler zurückgeben.

### <a name="compiling-requirements"></a>Anforderungen in Bezug auf die Kompilierung

Verwenden Sie die neueste Version von [powerbi-visuals-tools](https://www.npmjs.com/package/powerbi-visuals-tools), um Ihr Power BI-Visual zu schreiben.

Sie müssen das Power BI-Visual mit `pbiviz package` kompilieren. Wenn Sie eigene Buildskripts verwenden, geben Sie einen benutzerdefinierten `npm run package`-Buildbefehl an.



### <a name="source-code-requirements"></a>Anforderungen in Bezug auf den Quellcode

Stellen Sie sicher, dass alle Richtlinien in der Liste der [zusätzlichen Zertifizierungsanforderungen für Power BI-Visuals](https://docs.microsoft.com/legal/marketplace/certification-policies#1200-power-bi-visuals-additional-certification) eingehalten werden. Wenn Ihre Einreichung nicht mit diesen Richtlinien übereinstimmt, werden Ihnen in der Ablehnungs-E-Mail von Partner Center die unter diesem Link aufgeführten Richtliniennummern mitgeteilt.

Berücksichtigen Sie die im Folgenden aufgeführten Codeanforderungen, um sicherzustellen, dass Ihr Code den Power BI-Zertifizierungsrichtlinien entspricht.  

**Erforderlich**
* Verwenden Sie nur öffentlich überprüfbare OSS-Komponenten wie öffentliche JavaScript- oder TypeScript-Bibliotheken.
* Der Code muss die [API zum Rendern von Ereignissen](event-service.md) unterstützen.
* Stellen Sie sicher, dass DOM auf sichere Weise geändert wird. Bereinigen Sie Benutzereingaben oder Benutzerdaten, bevor Sie den Code zu DOM hinzufügen.
* Verwenden Sie den [Beispielbericht](https://github.com/Microsoft/PowerBI-visuals/raw/gh-pages/assets/reports/large_data.pbix) als Testdataset.

**Nicht zulässig**
* Zugriff auf externe Dienste oder Ressourcen. Beispielsweise dürfen aus Power BI keine HTTP/S- oder WebSocket-Anforderungen an Dienste gesendet werden.
* Verwenden von `innerHTML` oder `D3.html(user data or user input)`.
* JavaScript-Fehler oder -Ausnahmen in der Browserkonsole für Eingabedaten.
* Zufälliger oder dynamischer Code wie `eval()`, unsichere Verwendung von `settimeout()`, `requestAnimationFrame()`, `setinterval(user input function)` sowie Benutzereingaben oder Benutzerdaten.
* Minimierte JavaScript-Dateien oder -Projekte.

## <a name="submitting-a-power-bi-visual-for-certification"></a>Übermitteln eines Power BI-Visual zur Zertifizierung

Sie können über Partner Center eine Zertifizierung Ihres Power BI-Visuals durch das Power BI-Team anfordern.

>[!TIP]
>Der Zertifizierungsprozess für ein Power BI-Visual kann einige Zeit in Anspruch nehmen. Wenn Sie ein neues Power BI-Visual erstellen, empfiehlt es sich, dieses über Partner Center zu veröffentlichen, bevor Sie eine Power BI-Zertifizierung anfordern. Damit wird sichergestellt, dass sich die Veröffentlichung Ihres Visuals nicht verzögert.

So fordern Sie eine Power BI-Zertifizierung an:

1. Melden Sie sich bei Partner Center an.
2. Wählen Sie auf der **Übersichtsseite** Ihre Power BI-Visual aus, und wechseln Sie zur Seite **Produkteinrichtung**.
3. Aktivieren Sie das Kontrollkästchen **Power BI-Zertifizierung anfordern**.
4. Geben Sie auf der Seite **Überprüfen und veröffentlichen** im Textfeld **Hinweise für Zertifizierung** einen Link zum Quellcode sowie die Anmeldeinformationen für den Zugriff darauf an.

### <a name="private-repository-submission-process"></a>Einreichungsprozess bei privaten Repositorys

Befolgen Sie die Anweisungen in diesem Abschnitt, wenn Sie ein privates Repository wie GitHub verwenden, um Ihre Power BI-Visualisierung zur Zertifizierung einzureichen.
1. Erstellen Sie ein neues Konto für das Überprüfungsteam.
2. Konfigurieren Sie für Ihr Konto die [zweistufige Authentifizierung](https://help.github.com/github/authenticating-to-github/securing-your-account-with-two-factor-authentication-2fa).
3. [Generieren Sie einen neuen Satz an Wiederherstellungscodes](https://help.github.com/github/authenticating-to-github/configuring-two-factor-authentication-recovery-methods#generating-a-new-set-of-recovery-codes).
4. Geben Sie folgende Informationen an, wenn Sie Ihre Power BI-Visualisierung einreichen:
    * Einen Link zum Repository
    * Anmeldeinformationen (einschließlich Kennwort)
    * Wiederherstellungscodes
    * Leseberechtigungen für unser Konto ([pbicvsupport](https://github.com/pbicvsupport))

## <a name="certified-power-bi-visual-badges"></a>Badges für zertifizierte Power BI-Visuals

Sobald ein Power BI-Visual zertifiziert ist, erhält es einen entsprechenden Badge.

### <a name="certified-power-bi-visuals-in-appsource"></a>Zertifizierte Power BI-Visuals in AppSource

* Bei der Onlinesuche nach [Power BI-Visuals in AppSource](https://appsource.microsoft.com/marketplace/apps?product=power-bi-visuals) zeigt ein kleiner gelber Badge auf der Karte des Visuals an, dass es sich um ein zertifiziertes Power BI-Visual handelt.

    ![AppSource-zertifizierte Power BI-Visuals](media/power-bi-custom-visuals-certified/certified-visual-yellow-small.png)

* Nach dem Klicken auf die Karte des Power BI-Visuals in AppSource zeigt ein gelber Badge mit der Bezeichnung *PBI Certified* an, dass dieses Power BI-Visual zertifiziert ist.

    ![App-Seite mit zertifiziertem Power BI-Visual](media/power-bi-custom-visuals-certified/certified-visual-yellow-big.png)

### <a name="certified-power-bi-visuals-in-the-power-bi-interface"></a>Zertifizierte Power BI-Visuals auf der Power BI-Oberfläche

* Beim Importieren eines Power BI-Visuals aus Power BI (Desktop oder Dienst) zeigt ein blaues Badge an, dass das Power BI-Visual zertifiziert ist.

    ![Power BI-Oberfläche mit zertifiziertem Power BI-Visual](media/power-bi-custom-visuals-certified/certified-visual-blue.png)

* Sie können ausschließlich zertifizierte Power BI-Visuals anzeigen, indem Sie die Filteroption *Power BI-zertifiziert* auswählen.

## <a name="next-steps"></a>Nächste Schritte

* Wenn Sie Webentwickler sind und selbst Power BI-Visuals erstellen und zu [Microsoft AppSource](https://appsource.microsoft.com) hinzufügen möchten, beginnen Sie mit dem Tutorial  [Entwickeln eines Power BI-Visuals](custom-visual-develop-tutorial.md).

* Weitere Informationen zu Visuals finden Sie in den [häufig gestellten Fragen zu zertifizierten Visuals](power-bi-custom-visuals-faq.md#certified-power-bi-visuals).

* [Entwickeln eines Power BI-Visuals](custom-visual-develop-tutorial.md)

* [Wiedergabeliste von Microsoft für Power BI-Visuals auf YouTube](https://www.youtube.com/playlist?list=PL1N57mwBHtN1vIjfvuBIzZllrmKo-Vz6x)

* [Visuals in Power BI](power-bi-custom-visuals.md)

* [Veröffentlichen von Power BI-Visuals in Microsoft AppSource](office-store.md)

* Weitere Fragen? [Wenden Sie sich an die Power BI-Community](https://community.powerbi.com/)