---
title: Richtlinien für Power BI-Visuals
description: Erfahren Sie, wie Sie ein benutzerdefiniertes Visual in Microsoft AppSource veröffentlichen, damit es von anderen gefunden und erworben werden kann.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.topic: conceptual
ms.subservice: powerbi-custom-visuals
ms.date: 07/16/2019
ms.openlocfilehash: 1602743230f1a369fe3da48fa37a313b9d9bbea4
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "79435879"
---
# <a name="guidelines-for-power-bi-visuals"></a>Richtlinien für Power BI-Visuals
Bevor Sie Ihr Power BI-Visual in Microsoft AppSource [veröffentlichen](office-store.md), damit andere es verwenden können, stellen Sie sicher, dass Sie die Richtlinien befolgen, um Ihren Benutzern eine hohe Benutzerfreundlichkeit zu bieten.

## <a name="power-bi-visuals-with-additional-purchases"></a>Power BI-Visuals mit zusätzlichen Käufen

Sie können kostenlose Power BI-Visuals beim Marketplace (Microsoft AppSource) einreichen. Darüber hinaus können Sie bei Microsoft AppSource Power BI-Visuals anbieten, die mit einer Preisauszeichnung „Möglicherweise sind zusätzliche Käufe erforderlich“ versehen sind. Power BI-Visuals mit der Auszeichnung „Möglicherweise sind zusätzliche Käufe erforderlich“ sind ähnlich wie IAP-Add-Ins (In-App Purchase, Kauf in der App) im Office Store. 

Analog zu einem kostenlosen Power BI-Visual kann auch ein IAP Power BI-Visual zertifiziert werden. Bevor Sie ein IAP Power BI-Visual zur Zertifizierung einreichen, stellen Sie sicher, dass den [Zertifizierungsanforderungen](power-bi-custom-visuals-certified.md) entspricht.

### <a name="what-is-a-power-bi-visual-with-iap-features"></a>Was ist ein Power BI-Visual mit In-App-Käufen?

Ein IAP Power BI-Visual ist ein *kostenloses* Visual, das *kostenlose Features* bietet. Ein solches Visual verfügt auch über einige erweiterte Features, für die zusätzliche Gebühren anfallen können. Entwickler müssen die Benutzer in der Beschreibung des Power BI-Visuals über die Features informieren, für deren Funktionsweise möglicherweise zusätzliche Komponenten erworben werden müssen. Derzeit bietet Microsoft keine nativen APIs an, den Erwerb von Apps und Add-Ins unterstützen.

Entwickler müssen ein Zahlungssystem von einem Drittanbieter für diese Käufe verwenden. Weitere Informationen finden Sie in [den Richtlinien für unseren Store](https://docs.microsoft.com/legal/marketplace/certification-policies#11002-displaying-ads).


>[!IMPORTANT]  
> Wenn Sie Ihr Power BI-Visual von „Kostenlos“ zu „Möglicherweise sind zusätzliche Käufe erforderlich“ aktualisieren, müssen den Benutzern im gleichen Umfang kostenlose Funktionen zur Verfügung stehen wie vor der Aktualisierung. Sie können zusätzlich zu den vorhandenen kostenlosen Features optionale erweiterte Features hinzufügen, die kostenpflichtig sind.

### <a name="watermarks"></a>Wasserzeichen

Sie können Wasserzeichen verwenden, damit Kunden die erweiterten IAP-Features weiterhin verwenden können, ohne zu bezahlen. 

Wasserzeichen können verwendet werden, um die gesamte Funktionalität des Power BI-Visuals vorzustellen, bevor ein Kauf erfolgt. 

* Wasserzeichen können nur in kostenpflichtigen Features verwendet werden, die ohne gültige Lizenz verwendet werden.
* Wasserzeichen sind in Power BI-Visuals mit der Preisauszeichnung *kostenlos* nicht zulässig.
* Wasserzeichen sind in IAP-Visuals nicht zulässig, wenn der Benutzer kostenlose Funktionen verwendet. 

### <a name="pop-up-window"></a>Popupfenster

Sie können ein Popupfenster verwenden, um den Lizenzerwerb zu erläutern, wenn eine ungültige (oder abgelaufene) Lizenz mit Ihrem Power BI IAP-Visual verwendet wird.

### <a name="submission-process"></a>Einreichungsprozess

Führen Sie den [Übermittlungsprozess](office-store.md#submitting-to-appsource) aus. Navigieren Sie dann zur Registerkarte *Produkteinrichtung*, und aktivieren Sie das Kontrollkästchen *Mein Produkt erfordert den Erwerb eines Diensts*.

Sobald das Power BI-Visual überprüft und genehmigt wurde, zeigt das Microsoft AppSource-Listing für das IAP Power BI-Visual den Hinweis „Möglicherweise müssen weitere Komponenten erworben werden“ in den Preisoptionen an.

## <a name="context-menu"></a>Kontextmenü
Das Kontextmenü ist das Rechtsklickmenü, das angezeigt wird, wenn der Benutzer mit der Maus über ein Visual fährt.
Alle Power BI-Visuals sollten das Kontextmenü für eine einheitliche Darstellung aktivieren.
Lesen Sie [diesen Artikel](https://github.com/Microsoft/PowerBI-visuals/blob/gh-pages/tutorials/building-bar-chart/adding-context-menu-to-the-bar.md), um zu erfahren, wie Sie ein Kontextmenü hinzufügen.

## <a name="commercial-logo"></a>Kommerzielles Logo
In diesem Abschnitt werden die Spezifikationen zum Hinzufügen von kommerziellen Logos in Power BI-Visuals erläutert. Kommerzielle Logos sind nicht obligatorisch. Wenn sie hinzugefügt werden, müssen Sie diesen Richtlinien entsprechen.

> [!NOTE]
> * Im Rahmen dieses Artikels bezeichnet der Ausdruck „kommerzielles Logo“ beliebige kommerzielle Firmenlogos, wie in den Abbildungen unten beschrieben.
> * Das kommerzielle Logo von Microsoft wird in diesem Artikel nur als Beispiel verwendet. Verwenden Sie für Ihr Power BI-Visual Ihr eigenes kommerzielles Logo.

> [!IMPORTANT]
> Kommerzielle Logos sind *nur im Bearbeitungsmodus* zulässig. Kommerzielle Logos können im Anzeigemodus *nicht* dargestellt werden.

### <a name="commercial-logo-type"></a>Typ des kommerziellen Logos

Es gibt drei Arten von kommerziellen Logos:
* **Logo**: Ein Logo besteht aus zwei Elementen, die fest aneinander gebunden sind, einem Symbol und einem Namen.

    ![Microsoft-Logo](media/guidelines-powerbi-visuals/microsoft-logo.png)

* **Symbol**:-eine Grafik ohne Text.

    ![Microsoft-Symbol](media/guidelines-powerbi-visuals/microsoft-symbol.png)

* **Logoschrift**-ein Logo ohne -Symbol, das nur aus Text besteht.

    ![Microsoft-Symbol](media/guidelines-powerbi-visuals/microsoft-logotype.png)

### <a name="commercial-logo-color"></a>Farbe des kommerziellen Logos

Wenn ein kommerzielles Logo verwendet wird, muss die Farbe des Logos grau sein (Hexadezimal-Farbcode #C8C8C8). Fügen Sie dem kommerziellen Logo keine Effekte wie Farbverläufe hinzu.

* **Logo**

    ![Microsoft-Symbol](media/guidelines-powerbi-visuals/grey-microsoft-logo.png)

* **Symbol**:-eine Grafik ohne Text.

    ![Microsoft-Symbol](media/guidelines-powerbi-visuals/grey-microsoft-symbol.png)

* **Logoschrift**-ein Logo ohne -Symbol, das nur aus Text besteht.

    ![Microsoft-Symbol](media/guidelines-powerbi-visuals/grey-microsoft-logotype.png)

> [!TIP]
> * Wenn Ihr Power BI-Visual eine Grafik enthält, fügen Sie Ihrem Logo ggf. einen weißen Hintergrund hinzu (mit Rändern in der Größe von 10 px).
> * Fügen Sie für Ihr Logo ggf. einen Schlagschatten hinzu (Durchlässigkeit in schwarz von 30 %).{1}

### <a name="commercial-logo-size"></a>Größe des kommerziellen Logos

Für ein Power BI-Visual sind zwei kommerzielle Logos erforderlich, eins für große und eins für kleine Kacheln. Platzieren Sie das Logo in einem Begrenzungsrahmen, der sich in der oberen oder unteren rechten Ecke befindet und Ränder von 4 px Breite aufweist.

In der folgenden Tabelle werden die Größenaspekte von Power BI-Visuals beschrieben.

|  |Kleines Power BI-Visual  |Großes Power BI-Visual  |
|---------|---------|---------|
|*Logobreite*    |Bis zu 240 px         |Größer als 240 px         |
|*Logohöhe*     |Bis zu 160 px         |Größer als 160 px         |
|*Größe des Begrenzungsrahmens*     |40 x 15 px         |101 x 30 px         |
|*Beispiel für ein kommerzielles Logo*     |![Microsoft-Symbol](media/guidelines-powerbi-visuals/grey-microsoft-symbol.png)         |![Microsoft-Logo](media/guidelines-powerbi-visuals/grey-microsoft-logo.png)         |
|*Beispiel für Begrenzungsrahmen*    |![Beispiel für kleines Logo](media/guidelines-powerbi-visuals/small-logo-box.png)         |![Beispiel für großes Logo](media/guidelines-powerbi-visuals/big-logo-box.png)         |
|    |         |         |

### <a name="commercial-logo-behavior"></a>Verhalten von kommerziellen Logos

Kommerzielle Logos sind nur im Bearbeitungsmodus zulässig. Wenn Sie darauf klicken, darf ein kommerzielles Logo nur die folgende Funktionalität aufweisen:

* Durch Klicken auf das Logo erfolgt eine Umleitung auf Ihre Website.

* Durch Klicken auf das kommerzielle Logo wird ein Popupfenster mit zusätzlichen Informationen geöffnet. Das Popupfenster sollte in zwei Abschnitte unterteilt sein:
    * Einen Marketingbereich, der das kommerzielle Logo, ein Visual und Marktbewertungen enthalten kann.
    * Einen Informationsbereich, der Informationen und Links enthalten kann.    


### <a name="things-to-avoid"></a>Dinge, die Sie vermeiden sollten

* Kommerzielle Logos können im Anzeigemodus nicht dargestellt werden.

* Ein animiertes kommerzielles Logo kann eine Animation bis zu fünf Sekunden lang anzeigen.

* Wenn Ihr Power BI-Visual im Lesemodus informative Symbole (i) beinhaltet, sollten diese in Farbe, Größe und Positionierung dem kommerziellen Logo entsprechen, wie oben beschrieben.

* Vermeiden Sie ein buntes oder schwarzes kommerzielles Logo. Das kommerzielle Logo muss grau sein (hexadezimaler Farbcode #C8C8C8).

    ![Unzulässiges buntes Logo](media/guidelines-powerbi-visuals/no-color-logo.png) ![Unzulässiges schwarzes Logo](media/guidelines-powerbi-visuals/black-logo.png)

* Ein kommerzielles Logo mit Effekten wie Farbverläufen oder starken Schatten.

    ![Unzulässiger Logostil](media/guidelines-powerbi-visuals/no-style-logo.png)

## <a name="best-practices"></a>Bewährte Methoden

Wenn Sie ein Power BI-Visual veröffentlichen, sollten Sie die folgenden Empfehlungen beachten, um Ihren Benutzern ein gutes Erlebnis zu bieten.

### <a name="visual-landing-page"></a>Startseite für Visuals

Verwenden Sie die Startseite, um den Benutzern zu verdeutlichen, wie sie Power BI-Visuals verwenden und wo Lizenzen erworben werden können. Fügen Sie keine Videos ein, die automatisch abgespielt werden. Fügen Sie nur Inhalte hinzu, die das Benutzererlebnis verbessern, z.B. Informationen oder Links zu den Details für den Erwerb von Lizenzen und zum Einsatz von In-App-Features.

### <a name="license-key-and-token"></a>Lizenzschlüssel und Token

Fügen Sie Felder für Lizenzschlüssel oder Token im oberen Teil des Formatierungsbereichs hinzu, sodass Benutzer diese leicht finden können.

## <a name="faq"></a>HÄUFIG GESTELLTE FRAGEN

Weitere Informationen zu Power BI-Visuals finden Sie in den [häufig gestellten Fragen zu Power BI-Visuals mit zusätzlichen Käufen](power-bi-custom-visuals-faq.md#visuals-with-additional-purchases).

## <a name="next-steps"></a>Weitere Schritte

Erfahren Sie, wie Sie ein Power BI-Visual in [Microsoft AppSource](office-store.md) veröffentlichen, damit es von anderen gefunden und verwendet werden kann.