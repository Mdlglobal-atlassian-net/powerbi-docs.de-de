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
ms.date: 02/17/2020
ms.openlocfilehash: 52a99380f8e1afc39ddfc59a401418e61fe6ad58
ms.sourcegitcommit: ec4d2d0f52d737e8e0583f6a7b16e6fd87382510
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/28/2020
ms.locfileid: "77782414"
---
# <a name="get-a-power-bi-visual-certified"></a>So lassen Sie sich ein Power BI-Visual zertifizieren

Zertifizierte Power BI-Visuals sind Power BI-Visuals in [AppSource](https://appsource.microsoft.com/en-us/marketplace/apps?page=1&product=power-bi-visuals), die den [Codeanforderungen](#certification-requirements) des Microsoft Power BI-Teams entsprechen. Diese Visuals wurden getestet, um sicherzustellen, dass sie nicht auf externe Dienste oder Ressourcen zugreifen und dass sie sicheren Codierungsmustern und -richtlinien folgen.

Wenn ein Power BI-Visual zertifiziert wurde, bietet es mehr Features. Beispielsweise können Sie ein Visual [nach PowerPoint exportieren](../consumer/end-user-powerpoint.md) oder in empfangenen E-Mails anzeigen, wenn ein Benutzer [Berichtsseiten abonniert](../consumer/end-user-subscribe.md).

Der Zertifizierungsprozess ist optional. Power BI-Visuals ohne Zertifizierung sind nicht notwendigerweise unsicher. Einige Power BI-Visuals sind nicht zertifiziert, weil sie mindestens eine [Zertifizierungsanforderung](https://docs.microsoft.com/power-bi/power-bi-custom-visuals-certified?#certification-requirements) nicht erfüllen. Beispiele: Ein Power BI-Kartenvisual, das eine Verbindung mit einem externen Dienst herstellt, oder ein Power BI-Visual, das kommerzielle Bibliotheken verwendet.

> [!NOTE]
> Microsoft ist nicht der Autor von Power BI-Visuals von Drittanbietern. Um die Funktionalität eines Drittanbietervisuals zu verifizieren, wenden Sie sich direkt an den Autor.

## <a name="certification-requirements"></a>Zertifizierungsanforderungen

Damit Ihr Power BI-Visual [zertifiziert](#get-a-power-bi-visual-certified) werden kann, muss es die in diesem Abschnitt aufgeführten Anforderungen erfüllen. 

### <a name="general-requirements"></a>Allgemeine Anforderungen

Ihre Power BI-Visual muss im Verkäuferdashboard oder in Partner Center genehmigt werden. Es empfiehlt sich, das Power BI-Visual bereits vorher in [AppSource](https://appsource.microsoft.com/marketplace/apps?page=1&product=power-bi-visuals) bereitzustellen. Informationen zum Veröffentlichen eines Power BI-Visuals in AppSource finden Sie unter [Veröffentlichen von Power BI-Visuals in Partner Center](office-store.md).

Bevor Sie Ihre Power BI-Visual zur Zertifizierung einreichen, überprüfen Sie, ob es den [Richtlinien für Power BI-Visuals](./guidelines-powerbi-visuals.md) entspricht.

Stellen Sie beim Einreichen des Power BI-Visuals sicher, dass das kompilierte Paket exakt mit dem eingereichten Paket übereinstimmt.

### <a name="code-repository-requirements"></a>Anforderungen in Bezug auf das Coderepository

Sie müssen Ihren Code zwar nicht öffentlich auf GitHub freigeben, aber das Coderepository muss dem Power BI-Team zur Überprüfung zur Verfügung stehen. Die beste Möglichkeit hierfür besteht darin, den Quellcode (JavaScript oder TypeScript) auf GitHub bereitzustellen.

Das Repository muss Folgendes enthalten:
* Code für eine einzelne Power BI-Visualisierung. Es darf weder Code für mehrere Power BI-Visuals noch Code enthalten, der in keinem Zusammenhang mit dem Visual steht.
* Einen Branch namens **certification** („Zertifizierung“, Kleinschreibung erforderlich). Der Quellcode in diesem Branch muss mit dem eingereichten Paket übereinstimmen. Dieser Code kann erst während des nächsten Einreichungsprozesses aktualisiert werden, wenn Sie das Power BI-Visual erneut einreichen.

Wenn Ihr Power BI-Visual private npm-Pakete oder git-Untermodule verwendet, müssen Sie Zugriff auf die zusätzlichen Repositorys bereitstellen, die diesen Code enthalten.

Der Aufbau eines visuellen Power BI-Repositorys ist im GitHub-Repository im [Beispielbalkendiagramm für Power BI-Visualisierungen](https://github.com/microsoft/PowerBI-visuals-sampleBarChartgi) gezeigt.

### <a name="file-requirements"></a>Anforderungen in Bezug auf Dateien

Verwenden Sie die neueste Version der API, um Ihr Power BI-Visual zu schreiben.

Das Repository muss die folgenden Dateien enthalten:
* **.gitignore**: Fügen Sie `node_modules` zu dieser Datei hinzu. Der Code darf den Ordner *node_modules* nicht enthalten.
* **capabilities.json**: Wenn Sie eine neuere Version Ihres Power BI-Visuals mit Änderungen an den Eigenschaften in dieser Datei einreichen, stellen Sie sicher, dass diese nicht zu Fehlern bei Berichten für vorhandene Benutzer führen.
* **pbiviz.json**
* **package.json**
* **package-lock.json**
* **tsconfig.json**

### <a name="command-requirements"></a>Anforderungen in Bezug auf Befehle

Stellen Sie sicher, dass die folgenden Befehle keine Fehler zurückgeben.

* `npm install`
* `pbiviz package`
* `npm audit` darf keine Warnungen mit hohem oder mittlerem Schweregrad zurückgeben.
* [TSLint von Microsoft](https://www.npmjs.com/package/tslint-microsoft-contrib) darf keine überschriebene Konfigurationen enthalten. Dieser Befehl darf keine lint-Fehler zurückgeben.

### <a name="compiling-requirements"></a>Anforderungen in Bezug auf die Kompilierung

Verwenden Sie die neueste Version von [powerbi-visuals-tools](https://www.npmjs.com/package/powerbi-visuals-tools), um Ihr Power BI-Visual zu schreiben.

Sie müssen das Power BI-Visual mit `pbiviz package` kompilieren. Wenn Sie eigene Buildskripts verwenden, geben Sie einen benutzerdefinierten `npm run package`-Buildbefehl an.



### <a name="source-code-requirements"></a>Anforderungen in Bezug auf den Quellcode

Stellen Sie sicher, dass alle Richtlinien in der Liste der [zusätzlichen Zertifizierungsanforderungen für Power BI-Visuals](https://docs.microsoft.com/legal/marketplace/certification-policies#1200-power-bi-visuals-additional-certification) eingehalten werden. Wenn Ihre Einreichung nicht mit diesen Richtlinien übereinstimmt, werden Ihnen in der Ablehnungs-E-Mail von Partner Center die unter diesem Link aufgeführten Richtliniennummern mitgeteilt.

Berücksichtigen Sie die im Folgenden aufgeführten Codeanforderungen, um sicherzustellen, dass Ihr Code den Power BI-Zertifizierungsrichtlinien entspricht.  

**Erforderlich**
* Verwenden Sie nur öffentlich überprüfbare OSS-Komponenten wie öffentliche JavaScript- oder TypeScript-Bibliotheken.
* Der Code muss die [API zum Rendern von Ereignissen](./visuals/event-service.md) unterstützen.
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

>[!NOTE]
> Wenn Sie sich gerade mitten im Übermittlungsprozess für ein Power BI-Visual befinden und das [Verkäuferdashboard](https://docs.microsoft.com/office/dev/store/use-the-seller-dashboard-to-submit-to-the-office-store) (das alte Verwaltungstool) verwenden müssen, lesen Sie die Anweisungen für den [Übermittlungsprozess für die Zertifizierung auf dem Verkäuferdashboard](seller-dashboard.md#seller-dashboard-certification-submission-process).

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

## <a name="certified-power-bi-visuals"></a>Zertifizierte Power BI-Visuals

Die zertifizierten Power BI-Visuals werden nachfolgend aufgeführt. Klicken Sie auf den Link, um das Power BI-Visual in AppSource zu öffnen. Wenn ein Video verfügbar ist, können Sie auf den jeweiligen Link klicken, um dieses anzusehen.

* [3AG Systems - Bar Chart With Absolute Variance](https://appsource.microsoft.com/product/power-bi-visuals/WA104381802)
*  [3AG Systems – Bar Chart With Relative Variance (3AG Systems: Balkendiagramm mit relativer Varianz)](https://appsource.microsoft.com/product/power-bi-visuals/WA104381912)
*  [3AG Systems – Column Chart With Relative Variance (3AG Systems: Säulendiagramm mit relativer Varianz)](https://appsource.microsoft.com/product/power-bi-visuals/WA104381803)
*  [3AG Systems - Column Chart with Variance](https://appsource.microsoft.com/product/power-bi-visuals/WA104381724)
* [Advanced Donut Visual (Vollversion)](https://appsource.microsoft.com/product/power-bi-visuals/WA104381941)
*  [Advanced Donut Visual (Eingeschränkte Version)](https://appsource.microsoft.com/product/power-bi-visuals/WA104380858)
*  [Advanced Graph Visual](https://appsource.microsoft.com/product/power-bi-visuals/WA104382086)
*  [Advanced Network Visualization (Erweiterte Netzwerkvisualisierung)](https://appsource.microsoft.com/product/power-bi-visuals/WA104381942)
*  [Advanced TimeSeries Visual (Vollversion)](https://appsource.microsoft.com/product/power-bi-visuals/WA104381943)
*  [Aster-Plot](https://appsource.microsoft.com/product/power-bi-visuals/WA104380759)
*  [Beyondsoft-Kalender](https://appsource.microsoft.com/product/power-bi-visuals/WA104381096)
*  [Schleifendiagramm von MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380838)
*  [Kastengrafikdiagramm](https://appsource.microsoft.com/product/power-bi-visuals/WA104380831)
* [Kastengrafikdiagramm von MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104381351)
*  [Ziegeldiagramm von MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380836)
*  [Blasendiagramm von Akvelon](https://appsource.microsoft.com/product/power-bi-visuals/WA104381340)
*  [Bullet Chart](https://appsource.microsoft.com/product/power-bi-visuals/WA104380755), **[Link zum Video](https://youtu.be/AOlsFYkfkcw)**
* [Bullet-Diagramm](https://appsource.microsoft.com/product/power-bi-visuals/WA104380755)
*  [Bullet Chart by OKViz](https://appsource.microsoft.com/product/power-bi-visuals/WA104380953), **[Link zum Video](https://youtu.be/mtvUNl9bMjA)**
* [Calendar by MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104381844)
*  [Kalender von Tallan](https://appsource.microsoft.com/product/power-bi-visuals/WA104381146)
*  [Candlestick by OKViz](https://appsource.microsoft.com/product/power-bi-visuals/WA104380952), **[Link zum Video](https://youtu.be/nT_18gyRxPo)**
*  [Karte mit Zuständen von OKViz](https://appsource.microsoft.com/product/power-bi-visuals/WA104380967)
*  [Chiclet-Slicer](https://appsource.microsoft.com/product/power-bi-visuals/WA104380756)
*  [Chord](https://appsource.microsoft.com/product/power-bi-visuals/WA104380761), **[Link zum Video](https://youtu.be/AQvd2FhRyCI)**
*  [Kreisförmiges Messgerät von MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380837)
*  [Clusterzuordnung](https://appsource.microsoft.com/product/power-bi-visuals/WA104380806)
* [Custom Calendar by Akvelon](https://appsource.microsoft.com/product/power-bi-visuals/WA104381179)
* [Zylindrisches Messgerät von MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380874)
*  [Dial Gauge](https://appsource.microsoft.com/product/power-bi-visuals/WA104381184)
[Dot Plot](https://appsource.microsoft.com/product/power-bi-visuals/WA104380760)
*  [Dot Plot by OKViz](https://appsource.microsoft.com/product/power-bi-visuals/WA104380949), **[Link zum Video](https://youtu.be/By16pX9KT40)**
*  [Drilldown-Kartogramm](https://appsource.microsoft.com/product/power-bi-visuals/WA104381045)
*  [Drilldown-Choroplethenkarte](https://appsource.microsoft.com/product/power-bi-visuals/WA104381044)
*  [Drilldown-Säulendiagramm](https://appsource.microsoft.com/product/power-bi-visuals/WA104380857), **[Link zum Video](https://youtu.be/lBy2gQQ5YsQ)**
*  [Drilldown-Säulendiagramm für zeitbasierte Daten](https://appsource.microsoft.com/product/power-bi-visuals/WA104380881), **[Link zum Video](https://youtu.be/T_mRou18vx0)**
*  [Drilldown-Ringdiagramm](https://appsource.microsoft.com/product/power-bi-visuals/WA104380858), **[Link zum Video](https://youtu.be/AUVFrSHmPeo)**
*  [Dual KPI](https://appsource.microsoft.com/product/power-bi-visuals/WA104380774)
*  [Dynamic Tooltip von MAQ](https://appsource.microsoft.com/product/power-bi-visuals/WA104380983)
*  [Erweitertes Punktdiagramm](https://appsource.microsoft.com/product/power-bi-visuals/WA104380762), **[Link zum Video](https://youtu.be/xCfM0cjM4do)**
*  [Enlighten Aquarium](https://appsource.microsoft.com/product/power-bi-visuals/WA104381112)
*  [Enlighten Slicer](https://appsource.microsoft.com/product/power-bi-visuals/WA104380960)
*  [Enlighten Stack Shuffle](https://appsource.microsoft.com/product/power-bi-visuals/WA104380849)
*  [Enlighten-Waffeldiagramm](https://appsource.microsoft.com/product/power-bi-visuals/WA104380850)
*  [Filern nach Liste von Devscope](https://appsource.microsoft.com/product/power-bi-visuals/WA104381413), **[Link zum Video](https://youtu.be/RetEWGwBu0I)**
*  [Force-Directed Graph](https://appsource.microsoft.com/product/power-bi-visuals/WA104380764), **[Link zum Video](https://youtu.be/YsTa7uyJ4sg)**
*  [Trichterdiagramm mit Quelle von MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104381334)
*  [Gantt](https://appsource.microsoft.com/product/power-bi-visuals/WA104380765), **[Link zum Video](https://youtu.be/qJ7s_KrGiUU)**
* [Gantt-Diagramm von MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104381364)
*  [Globe Data Bars](https://appsource.microsoft.com/product/power-bi-visuals/WA104381344)
*  [Grid by MAQ Software (Raster von MAQ Software)](https://appsource.microsoft.com/product/power-bi-visuals/WA104380825)
*  [Hierarchy Chart by Akvelon](https://appsource.microsoft.com/product/power-bi-visuals/WA104381333), **[Link zum Video](https://youtu.be/0ZGzJaq_KT4)**
*  [Histogramm](https://appsource.microsoft.com/product/power-bi-visuals/WA104380776)
*  [Histogramm mit Punkten von MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104381032)
* [Horizontal bar chart](https://appsource.microsoft.com/product/power-bi-visuals/WA104381230)
*  [Horizontales Trichterdiagramm von MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380846)
*  [Bild von CloudScope](https://appsource.microsoft.com/product/power-bi-visuals/WA104381297)
*  [Bildraster](https://appsource.microsoft.com/product/power-bi-visuals/WA104381355)
*  [Designer für Infografiken](https://appsource.microsoft.com/product/power-bi-visuals/WA104380898)
*  [KPI-Diagramm von Akvelon](https://appsource.microsoft.com/product/power-bi-visuals/WA104381432)
*  [KPI Column von MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380996)
*  [KPI-Raster von MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380947)
*  [KPI-Indikator](https://appsource.microsoft.com/product/power-bi-visuals/WA104380832)
*  [KPI-Ticker von MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380946)
* [Linearmessgerät von MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380821)
*  [LineDot-Diagramm](https://appsource.microsoft.com/product/power-bi-visuals/WA104380766)
*  [Mekko Chart](https://appsource.microsoft.com/product/power-bi-visuals/WA104380785), **[Link zum Video](https://youtu.be/90FLCKpgicA)**
*  [Multi-KPI](https://appsource.microsoft.com/product/power-bi-visuals/WA104381763)
*  [Overview von CloudScope](https://appsource.microsoft.com/product/power-bi-visuals/WA104381477)
*  [Wiedergabeachse (dynamischer Slicer)](https://appsource.microsoft.com/product/power-bi-visuals/WA104380981)
*  [Power KPI](https://appsource.microsoft.com/product/power-bi-visuals/WA104381083), [Link zum Video](https://youtu.be/IvfIP3E6-1Q)
*  [Power KPI Matrix](https://appsource.microsoft.com/product/power-bi-visuals/WA104381299), **[Link zum Video](https://youtu.be/1enze8pcGzY)**
*  [Pulse Chart](https://appsource.microsoft.com/product/power-bi-visuals/WA104381006), **[Link zum Video](https://youtu.be/DQWdcQtjDVw)**
*  [Quadrant Chart by MAQ Software (Quadrant-Diagramm von MAQ Software)](https://appsource.microsoft.com/product/power-bi-visuals/WA104381011)
*  [Netzdiagramm](https://appsource.microsoft.com/product/power-bi-visuals/WA104380771)
*  [Ringdiagramm von MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380824)
*  [Drehbares Diagramm von MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104381007)
*  [Sankey Chart](https://appsource.microsoft.com/product/power-bi-visuals/WA104380777), **[Link zum Video](https://youtu.be/WWP9wVUHGaA)**
*  [Punktdiagramm von Akvelon](https://appsource.microsoft.com/product/power-bi-visuals/WA104381703)
*  [Scroller](https://appsource.microsoft.com/product/power-bi-visuals/WA104381018)
*  [Smart Filter by OKViz](https://appsource.microsoft.com/product/power-bi-visuals/WA104380859), **[Link zum Video](https://youtu.be/gcJsDDRQq28)**
*  [Sparkline by OKViz](https://appsource.microsoft.com/product/power-bi-visuals/WA104380910), **[Link zum Video](https://youtu.be/0m3Vnvso9tY)**
*  [Stream-Diagramm](https://appsource.microsoft.com/product/power-bi-visuals/WA104380772)
*  [Sunburst](https://appsource.microsoft.com/product/power-bi-visuals/WA104380767)
*  [Synoptic Panel von OKViz](https://appsource.microsoft.com/product/power-bi-visuals/WA104380873)
*  [Tabellenheatmap](https://appsource.microsoft.com/product/power-bi-visuals/WA104380818)
*  [Tachometer](https://appsource.microsoft.com/product/power-bi-visuals/WA104380937), **[Link zum Video](https://youtu.be/C3OXdETbS9o)**
*  [Textfilter](https://appsource.microsoft.com/product/power-bi-visuals/WA104381309)
*  [Text-Wrapper von MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380826)
*  [Thermometer von MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380847)
*  [Time Brush-Slicer](https://appsource.microsoft.com/product/power-bi-visuals/WA104380798)
*  [Timeline Slicer](https://appsource.microsoft.com/product/power-bi-visuals/WA104380786), **[Link zum Video](https://youtu.be/ozMtZ4_NZ10)**
*  [Timeline by CloudScope](https://appsource.microsoft.com/product/power-bi-visuals/WA104381427), [Link zum Video](https://youtu.be/szNi9YgXFJc)
*  [Tornado chart](https://appsource.microsoft.com/product/power-bi-visuals/WA104380768), **[Link zum Video](https://www.youtube.com/watch?v=AQvd2FhRyCI)**
*  [Handelsdiagramm von MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380823)
* [Ultimate KPI Card](https://appsource.microsoft.com/product/power-bi-visuals/WA104381977)
*  [Ultimate Variance](https://appsource.microsoft.com/product/power-bi-visuals/WA104381140), **[Link zum Video](https://youtu.be/pDYF8iZxERs)**
*  [Ultimate Waterfall](https://appsource.microsoft.com/product/power-bi-visuals/WA104380956), **[Link zum Video](https://youtu.be/0BZsVCQdEkc)**
*  [Benutzerliste von CloudScope](https://appsource.microsoft.com/product/power-bi-visuals/WA104381426)
*  [Venn-Diagramm von MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104381231)
*  [Violin Plot](https://appsource.microsoft.com/product/power-bi-visuals/WA104381947)
*  [Visio Visual](https://appsource.microsoft.com/product/power-bi-visuals/WA104381132)
*  [Waffle Chart](https://appsource.microsoft.com/product/power-bi-visuals/WA104381049), **[Link zum Video](https://youtu.be/1vRqYUsm3Vk)**
*  [Word Cloud](https://appsource.microsoft.com/product/power-bi-visuals/WA104380752), **[Link zum Video](https://youtu.be/AblTenl9fqo)**

## <a name="faq"></a>Häufig gestellte Fragen

Weitere Informationen zu Visuals finden Sie in den [häufig gestellten Fragen zu zertifizierten Visuals](power-bi-custom-visuals-faq.md#certified-power-bi-visuals).

## <a name="next-steps"></a>Nächste Schritte

* [Entwickeln eines benutzerdefinierten Visuals für Power BI](../developer/custom-visual-develop-tutorial.md)
* [Wiedergabeliste benutzerdefinierter visueller Elemente von Microsoft auf YouTube](https://www.youtube.com/playlist?list=PL1N57mwBHtN1vIjfvuBIzZllrmKo-Vz6x)  
* [Visualisierungen in Power BI](../visuals/power-bi-report-visualizations.md)  
* [Benutzerdefinierte Visualisierungen in Power BI](power-bi-custom-visuals.md)  
* [Veröffentlichen von Power BI-Visuals in Microsoft AppSource](../developer/office-store.md) 
* Wenn Sie Webentwickler sind und selbst Power BI-Visuals erstellen und zu [Microsoft AppSource](https://appsource.microsoft.com) hinzufügen möchten, beginnen Sie mit dem Tutorial  [Entwickeln eines Power BI-Visuals](visuals/custom-visual-develop-tutorial.md). 

Weitere Fragen? [Wenden Sie sich an die Power BI-Community](https://community.powerbi.com/)
