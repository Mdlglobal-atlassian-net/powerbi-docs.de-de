---
title: Grundlegende Konzepte für Designer im Power BI-Dienst
description: Kapazitäten für Power BI-Dienst, Arbeitsbereiche, Dashboards, Berichte, Arbeitsmappen, Datasets und Dataflows.
author: maggiesMSFT
manager: kfollis
ms.reviewer: ''
featuredvideoid: B2vd4MQrz4M
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 11/14/2019
ms.author: maggies
LocalizationGroup: Get started
ms.openlocfilehash: b85ae8fa082de887b02cee19c9adb22a2250df05
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/13/2020
ms.locfileid: "83277270"
---
# <a name="basic-concepts-for-designers-in-the-power-bi-service"></a>Grundlegende Konzepte für Designer im Power BI-Dienst

Dieser Artikel soll Ihnen die Orientierung im Power BI-Dienst erleichtern: Was sind die verschiedenen Elemente, wie arbeiten sie zusammen und wie können Sie mit ihnen arbeiten. Sie profitieren mehr davon, wenn Sie sich bereits [für den Power BI-Dienst registriert](service-self-service-signup-for-power-bi.md) und [Daten hinzugefügt](connect-data/service-get-data.md) haben. Als Entwerfer beginnt Ihr normaler Workflow üblicherweise mit dem Erstellen von Berichten in Power BI Desktop. Anschließend veröffentlichen Sie sie im Power BI-Dienst, wo Sie sie weiter bearbeiten können. Auf der Grundlage Ihrer Berichte erstellen Sie außerdem die Dashboards im Power BI-Dienst. 

Wenn Sie noch nicht über eigene Berichte verfügen, installieren Sie für die Zwecke dieses Artikels eines der [Power BI-Beispiele](create-reports/sample-datasets.md).

![Startbildschirm des Power BI-Diensts in einem Browser](media/service-basic-concepts/power-bi-home-screen.png)

Wenn Sie den Power BI-Dienst in einem Browser öffnen, sehen Sie zunächst den Startbildschirm. Vermutlich sind dies die Elemente, die angezeigt werden:

1. Navigationsbereich
2. Office 365-App-Startfeld
3. Power BI-Schaltfläche „Start“
4. Symbolschaltflächen, einschließlich Einstellungen, Hilfe und Feedback
5. Suchfeld
6. Favoriten und häufig verwendete Dashboards, Berichte und Arbeitsbereiche
7. Zuletzt verwendete Dashboards, Berichte und Arbeitsbereiche
8. Ihre Arbeitsbereiche

Sie und die Endbenutzer Ihrer Berichte und Dashboards haben im Power BI-Dienst das gleiche Starterlebnis in einem Browser.

Diese Features werden später näher erläutert. Zunächst werden einige Grundkonzepte von Power BI besprochen. Alternativ können Sie sich zuerst dieses Video ansehen.  In diesem Video gibt Will einen Überblick über den Power BI-Dienst und erklärt die grundlegenden Konzepte.

<iframe width="560" height="315" src="https://www.youtube.com/embed/B2vd4MQrz4M" frameborder="0" allowfullscreen></iframe>


## <a name="power-bi-concepts"></a>Power BI-Konzepte
Die fünf wichtigsten Grundkomponenten von Power BI sind: *Dashboards*, *Berichte*, *Arbeitsmappen*, *Datasets* und *Dataflows*. Alle Komponenten sind in *Arbeitsbereichen* angeordnet und werden basierend auf *Kapazitäten* erstellt.  Zunächst werden in diesem Artikel die Konzepte von Kapazitäten und Arbeitsbereichen beschrieben. Anschließend erhalten Sie weitere Informationen zu den fünf Grundkomponenten.

## <a name="capacities"></a>Funktionen
Kapazitäten sind ein zentrales Konzept von Power BI, das eine Reihe von Ressourcen (Speicher, Prozessor und Arbeitsspeicher) darstellt, die zum Hosten und Bereitstellen Ihrer Power BI-Inhalte verwendet werden. Kapazitäten werden entweder _gemeinsam_ genutzt oder sind _dediziert_. Eine gemeinsam genutzte Kapazität wird für andere Microsoft-Kunden freigegeben, während eine dedizierte Kapazität vollständig einem einzelnen Kunden zugewiesen wird. Für dedizierte Kapazitäten wird ein [Abonnement](admin/service-premium-what-is.md) benötigt. Weitere Informationen zu dieser Art von Kapazitäten finden Sie im Artikel [Verwalten von Premium-Kapazitäten](admin/service-premium-capacity-manage.md).

Standardmäßig werden Arbeitsbereiche auf einer freigegebenen Kapazität erstellt. Bei gemeinsam genutzten Kapazitäten werden Workloads auf Computeressourcen ausgeführt, die gemeinsam mit anderen Kunden genutzt werden. Da die Kapazität Ressourcen teilen muss, werden Einschränkungen auferlegt, um „Fair Play“ zu gewährleisten, z. B. eine maximale Modellgröße (1 GB) und eine maximale tägliche Aktualisierungshäufigkeit (acht Mal pro Tag).

## <a name="workspaces"></a>Arbeitsbereiche
Arbeitsbereiche werden basierend auf Kapazitäten erstellt. Im Wesentlichen handelt es dabei sich um Container für Dashboards, Berichte, Arbeitsmappen, Datasets und Dataflows in Power BI.

Es gibt zwei Typen von Arbeitsbereichen: *Mein Arbeitsbereich* und *Arbeitsbereiche*.

- *Mein Arbeitsbereich* ist der persönliche Arbeitsbereich jedes Power BI-Kunden, in dem Sie Ihre eigenen Inhalte bearbeiten. Nur Sie haben Zugriff auf Ihren „Mein Arbeitsbereich“. Sie können Dashboards und Berichte von Ihrem Arbeitsbereich aus freigeben. Wenn Sie in Dashboards und Berichte mit anderen Personen zusammenarbeiten oder eine App erstellen möchten, sollten Sie einen Arbeitsbereich verwenden.      
-  *Arbeitsbereiche* werden für die Zusammenarbeit und die Freigabe von Inhalten für Kollegen verwendet. Sie können Ihren Arbeitsbereichen Kollegen hinzufügen und gemeinsam an Dashboards, Berichten, Arbeitsmappen und Datasets arbeiten. Alle Mitglieder von Arbeitsbereichen benötigen Power BI Pro-Lizenzen. Es gibt dabei nur eine Ausnahme. Weitere Informationen zu den [neuen Arbeitsbereichen](collaborate-share/service-create-the-new-workspaces.md). 

    Darüber hinaus werden in *Arbeitsbereichen* Apps für Ihre Organisation erstellt, veröffentlicht und verwaltet. Betrachten Sie Arbeitsbereiche als eine Art Bereitstellungsraum und Container für Ihre Inhalte, die eine Power BI-App bilden. Was genau ist eine *App*? Es handelt sich dabei um eine Sammlung von Dashboards und Berichten, die erstellt wurden, um Schlüsselmetriken für die Power BI-Endbenutzer Ihrer Organisation bereitzustellen. Apps sind interaktiv, können von Kunden aber nicht bearbeitet werden. Für App-Anwender, also die Kollegen, die Zugriff auf die Apps haben, sind Pro-Lizenzen jedoch nicht zwingend erforderlich.  

Um mehr über Teilen im Allgemeinen zu erfahren, beginnen Sie mit [Wege zum Teilen Ihrer Arbeit mit Dashboards](collaborate-share/service-how-to-collaborate-distribute-dashboards-reports.md).

Nun zu den fünf Grundkomponenten von Power BI.

## <a name="dataflows"></a>Dataflows
Mit einem *Dataflow* können Organisationen Daten aus unterschiedlichen Quellen vereinheitlichen. Sie sind optional und werden häufig in komplexen oder größeren Projekten eingesetzt. Sie stellen Daten dar, die für die Verwendung durch Datasets vorbereitet und bereitgestellt werden. Sie können jedoch nicht direkt als Quelle für die Berichterstellung verwendet werden. Sie nutzen die umfangreiche Sammlung von Microsoft-Datenconnectors und ermöglichen so die Erfassung von Daten aus lokalen und cloudbasierten Datenquellen.

Dataflows werden nur in Arbeitsbereichen erstellt und verwaltet (aber nicht unter *Mein Arbeitsbereich*). Außerdem werden sie als Entitäten im Common Data Model (CDM) in Azure Data Lake Storage Gen2 gespeichert. In der Regel werden regelmäßig Aktualisierungen durchgeführt, um die Daten aktuell zu halten. Dataflows eignen sich hervorragend für die Vorbereitung von Daten für die Verwendung – und potenzielle Wiederverwendung – durch ihre Datasets. Weitere Informationen finden Sie im Artikel [Self-Service-Datenaufbereitung in Power BI](transform-model/service-dataflows-overview.md).

Sie können keine Dashboards oder Berichte ohne Daten erstellen. Zwar können leere Dashboards und Berichte verwendet werden, diese wären jedoch nicht nützlich. Deswegen finden Sie im Folgenden Informationen zu **Datasets**.

## <a name="datasets"></a>Datasets
Ein *Dataset* ist eine Sammlung von Daten, die Sie *importieren* oder mit denen Sie eine *Verbindung herstellen*. In Power BI können Sie Verbindungen mit allen Arten von Datasets herstellen, sie importieren und zentral anordnen. Datasets können auch Daten aus Dataflows entnehmen.

Datasets sind *Arbeitsbereichen* zugeordnet, und ein einzelnes Dataset kann Teil mehrerer Arbeitsbereiche sein. Wenn Sie einen Arbeitsbereich öffnen, werden die zugeordneten Datasets auf der Registerkarte **Datasets** aufgeführt. Jedes aufgelistete Dataset stellt eine einzelne Datenquelle dar, z. B. eine Excel-Arbeitsmappe auf OneDrive oder ein lokales tabellarisches SSAS-Dataset oder ein Salesforce-Dataset. Es werden viele verschiedene Datenquellen unterstützt, zu denen ständig neue hinzukommen. Mehr dazu finden Sie in der Liste der [Datasettypen, die mit Power BI verwendet werden können](connect-data/service-get-data.md).

Im folgenden Beispiel ist der Arbeitsbereich „Vertrieb und Marketing“ ausgewählt, und es wurde auf die Registerkarte **Datasets** geklickt.

![Ausgewählte Datasets](media/service-basic-concepts/power-bi-datasets.png)

**EIN** Dataset...

* kann beliebig oft in einem oder mehreren verschiedenen Arbeitsbereichen verwendet werden.
* kann in vielen verschiedenen Berichten verwendet werden.
* Visualisierungen dieses einen Datasets können auf vielen verschiedenen Dashboards angezeigt werden.

  ![Diagramm der Datasets](media/service-basic-concepts/drawing2.png)

Wählen Sie am unteren Rand des Navigationsbereichs **Daten abrufen** aus, um die [Verbindung mit einem Dataset herzustellen oder es zu importieren](connect-data/service-get-data.md). Befolgen Sie die Anweisungen zum Herstellen einer Verbindung mit der jeweiligen Quelle bzw. zum Importieren, und fügen Sie das Dataset dem aktiven Arbeitsbereich hinzu. Neue Datasets werden mit einem gelben Sternchen markiert. Das zugrunde liegende Dataset wird durch Ihre Arbeit in Power BI nicht verändert.

Datasets, die von einem Arbeitsbereichsmitglied hinzugefügt wurden, sind für die anderen Arbeitsbereichsmitglieder mit den Rollen *Administrator*, *Mitglied* oder *Mitwirkender* verfügbar.

Datasets können aktualisiert, umbenannt, untersucht und entfernt werden. Verwenden Sie ein Dataset, um einen völlig neuen Bericht zu erstellen, oder führen Sie [Schnelleinblicke](create-reports/service-insights.md) aus.  Wählen Sie **Verwandte Inhalte anzeigen**, um zu erfahren, welche Berichte und Dashboards ein Dataset bereits verwenden. Wählen Sie ein Dataset aus, um es zu untersuchen. Tatsächlich öffnen Sie das Dataset im Berichts-Editor, wo Sie beginnen können, die Daten zu untersuchen und Visualisierungen zu erstellen.

Damit zum nächsten Thema: Berichte.

### <a name="dig-deeper"></a>Weiterführende Themen
* [Datasets im Power BI-Dienst](connect-data/service-datasets-understand.md)
* [Datasetmodi im Power BI-Dienst](connect-data/service-dataset-modes-understand.md)
* [Was ist Power BI Premium?](admin/service-premium-what-is.md)
* [Abrufen von Daten in Power BI](connect-data/service-get-data.md)
* [Beispieldatasets für Power BI](create-reports/sample-datasets.md)

## <a name="reports"></a>Berichte
Ein Power BI-Bericht besteht aus mindestens einer Seite mit Visualisierungen, wie z. B. Liniendiagrammen, Maps und Treemaps. Visualisierungen werden auch als **_visuelle Elemente oder Visuals_** bezeichnet. Alle Visualisierungen in einem Bericht stammen aus einem einzelnen Dataset. Sie können Berichte in Power BI von Grund auf neu erstellen oder sie mithilfe von Dashboards importieren, die Kollegen mit Ihnen teilen. Außerdem kann Power BI sie erstellen, wenn Sie Verbindungen mit Datasets aus Excel, Power BI Desktop, Datenbanken und SaaS-Anwendungen herstellen.  Wenn Sie z. B. eine Verbindung mit einer Excel-Arbeitsmappe herstellen, die Power View-Tabellen enthält, dann erstellt Power BI einen Bericht auf Basis dieser Tabellen. Und wenn Sie eine Verbindung mit einer SaaS-Anwendung herstellen, wird ein vorgefertigter Bericht von Power BI importiert.

Es gibt zwei Modi, um Berichte anzuzeigen und mit ihnen zu interagieren: *Leseansicht* und *Bearbeitungsansicht*. Wenn Sie einen Bericht öffnen, wird er in der Leseansicht geöffnet. Wenn Sie über Bearbeitungsberechtigungen verfügen, wird in der oberen linken Ecke **Bericht bearbeiten** angezeigt, und Sie können den Bericht in der Bearbeitungsansicht anzeigen.  Wenn sich ein Bericht in einem Arbeitsbereich befindet, kann ihn jeder Inhaber der Rollen *Administrator*, *Mitglied* oder *Mitwirkender* bearbeiten. Sie haben Zugriff auf alle Funktionen zum Untersuchen, Entwerfen, Erstellen und Teilen der Bearbeitungsansicht für den betreffenden Bericht. Die Personen, mit denen sie den Bericht teilen, können den Bericht in der Leseansicht untersuchen und mit ihm interagieren.   

Wenn Sie einen Arbeitsbereich öffnen, werden die zugeordneten Berichte auf der Registerkarte **Berichte** aufgeführt. Jeder aufgeführte Bericht stellt mindestens eine Seite mit Visualisierungen dar, die auf nur einem der zugrunde liegenden Datasets basieren. Wählen Sie einen Bericht aus, um ihn zu öffnen.

Wenn Sie eine App öffnen, wird ein Dashboard angezeigt.  Wählen Sie eine Dashboardkachel (siehe weiter unten) aus, die aus einem Bericht angeheftet wurde, um auf den zugrunde liegenden Bericht zuzugreifen. Beachten Sie, dass nicht alle Kacheln aus Berichten angeheftet werden, möglicherweise müssen Sie also einige Kacheln durchprobieren, bis Sie den gesuchten Bericht finden.

Der Bericht wird standardmäßig in der Leseansicht geöffnet.  Wählen Sie einfach **Bericht bearbeiten** aus, um den Bericht in der Bearbeitungsansicht zu öffnen (falls Sie über die erforderlichen Berechtigungen verfügen).

Im folgenden Beispiel ist der Arbeitsbereich „Vertrieb und Marketing“ ausgewählt, und es wurde auf die Registerkarte **Berichte** geklickt.

![Ausgewählte Berichte](media/service-basic-concepts/power-bi-reports.png)

**EIN** Bericht...

* ist in einem einzelnen Arbeitsbereich enthalten.
* kann mehreren Dashboards innerhalb des gleichen Arbeitsbereichs zugeordnet werden. Angeheftete Kacheln aus diesem einen Bericht können auf mehreren Dashboards vorkommen.
* kann mithilfe der Daten aus einem Dataset erstellt werden. Power BI Desktop kann mehrere Datasets zu einem einzelnen Bericht zusammenfassen, der seinerseits in Power BI importiert werden kann.

  ![Diagramm der Berichte](media/service-basic-concepts/drawing3new.png)

### <a name="dig-deeper"></a>Weiterführende Themen
- [Erstellen eines Berichts im Power BI-Dienst durch Importieren eines Datasets](create-reports/service-report-create-new.md)
- [Optimieren von Berichten für die mobilen Power BI-Apps](create-reports/desktop-create-phone-report.md)

## <a name="dashboards"></a>Dashboards
Ein *Dashboard* ist ein von Ihnen **im Power BI-Dienst** oder von einem Kollegen **im Power BI-Dienst** erstelltes Objekt, das für Sie freigegeben wurde. Es handelt sich um einen einzelnen Zeichenbereich, der keine, eine oder mehrere Kacheln und Widgets enthält. Jede aus einem Bericht oder aus [Q&A](power-bi-q-and-a.md) angeheftete Kachel zeigt eine einzelne [Visualisierung](power-bi-report-visualizations.md) an, die aus einem Dataset erstellt wurde und an das Dashboard angeheftet ist. Gesamte Berichtsseiten können ebenfalls als einzelne Kachel an ein Dashboard angeheftet werden. Es gibt viele Möglichkeiten, dem Dashboard Kacheln hinzuzufügen – zu viele, um sie in diesem Übersichtsthema zu behandeln. Weitere Informationen finden Sie unter [Dashboardkacheln in Power BI](create-reports/service-dashboard-tiles.md).

Warum werden Dashboards erstellt?  Hier sind nur einige der Gründe:

* Sie können auf einen Blick alle Informationen erkennen, die zum Treffen von Entscheidungen erforderlich sind.
* Sie können die wichtigsten unternehmensbezogenen Informationen überwachen.
* Sie können sicherstellen, dass sich alle Kollegen auf derselben Seite befinden und dabei dieselben Informationen anzeigen und verwenden.
* Sie können die Integrität eines Geschäfts, Produkts, Unternehmensbereichs oder einer Marketingkampagne usw. überwachen.
* Sie können eine personalisierte Ansicht eines umfangreicheren Dashboards erstellen, das alle für Sie erforderlichen Metriken enthält.

Wenn Sie einen Arbeitsbereich öffnen, werden die zugeordneten Dashboards auf der Registerkarte **Dashboards** aufgeführt. Wählen Sie ein Dashboard aus, um es zu öffnen. Wenn Sie eine App öffnen, sehen Sie ein Dashboard.  Jedes Dashboard stellt eine angepasste Ansicht einer Teilmenge der zugrunde liegenden Datasets dar.  Wenn Sie der Besitzer des Dashboards sind, haben Sie auch Bearbeitungszugriff auf das oder die zugrunde liegenden Datasets und Berichte.  Wenn das Dashboard für Sie freigegeben wurde, können Sie mit dem Dashboard und allen zugrunde liegenden Berichten interagieren, Sie können jedoch keine Änderungen speichern.

Es gibt viele verschiedene Möglichkeiten, wie Sie oder ein Kollege [ein Dashboard freigeben](collaborate-share/service-share-dashboards.md) können. Power BI Pro ist für das Freigeben eines Dashboards und möglicherweise auch zum Anzeigen eines freigegebenen Dashboards erforderlich.

**EIN** Dashboard...

* ist einem einzelnen Arbeitsbereich zugeordnet.
* kann Visualisierungen von verschiedenen Datasets anzeigen.
* kann Visualisierungen von verschiedenen Berichten anzeigen.
* kann Visualisierungen anzeigen, die aus anderen Tools (z.B. Excel) angeheftet wurden.

  ![Ausgewähltes Dashboard](media/service-basic-concepts/drawing1.png)

### <a name="dig-deeper"></a>Weiterführende Themen
* [Erstellen eines leeren Dashboards und Abrufen von Daten](create-reports/service-dashboard-create.md)
* [Duplizieren eines Dashboards](create-reports/service-dashboard-copy.md)
* [Erstellen einer Telefonansicht eines Dashboards](create-reports/service-create-dashboard-mobile-phone-view.md)


## <a name="workbooks"></a>Arbeitsmappen
Arbeitsmappen sind eine besondere Art von Dataset. Wenn Sie den Abschnitt **Datasets** weiter oben gelesen haben, wissen Sie bereits das Wichtigste über Arbeitsmappen. Vielleicht fragen Sie sich jedoch, warum Excel-Arbeitsmappen in Power BI manchmal ein **Dataset** und manchmal eine **Arbeitsmappe** sind.

Wenn Sie **Daten abrufen** für Excel-Dateien verwenden, können Sie zwischen den Optionen *Importieren* und *Verknüpfen* für die Datei wählen. Wenn Sie „Verknüpfen“ wählen, wird die Arbeitsmappe in Power BI genauso angezeigt wie in Excel Online. Allerdings stehen Ihnen im Gegensatz zu Excel Online einige hervorragende Funktionen zur Verfügung, mit denen Sie Elemente aus den Arbeitsblättern direkt an Ihre Dashboards anheften können.

Sie können Ihre Arbeitsmappe in Power BI nicht bearbeiten. Wenn Sie aber Änderungen vornehmen müssen, können Sie auf „Bearbeiten“ klicken und die Arbeitsmappe in Excel online oder lokal bearbeiten. Alle vorgenommenen Änderungen werden in der Arbeitsmappe in OneDrive gespeichert.

### <a name="dig-deeper"></a>Weiterführende Themen
* [Abrufen von Daten aus Excel-Arbeitsmappendateien](connect-data/service-excel-workbook-files.md)
* [Veröffentlichen in Power BI aus Excel](connect-data/service-publish-from-excel.md)


## <a name="a-dashboard-in-my-workspace"></a>Dashboard in „Mein Arbeitsbereich“
Bis hierher wurden Arbeitsbereiche und die Grundkomponenten erläutert. Nun bringen wir diese zusammen und sehen uns die einzelnen Komponenten der Dashboardumgebung im Power BI-Dienst an.

![Der Power BI-Dienst in einem Browser](media/service-basic-concepts/completenewest.png)

### <a name="1-navigation-pane"></a>1. **Navigationsbereich**
Verwenden Sie den Navigationsbereich, um zwischen den Arbeitsbereichen und den Grundkomponenten von Power BI zu wechseln: Dashboards, Berichte, Arbeitsmappen und Datasets.  

  ![Navigationsbereich](media/service-basic-concepts/power-bi-navigation.png)

* Wählen Sie **Daten abrufen** aus, um [Datasets, Berichte und Dashboards zu Power BI hinzuzufügen](connect-data/service-get-data.md).
* Erweitern und reduzieren Sie den Navigationsbereich mit diesem Symbol ![Symbol „Navigationsbereich“](media/service-basic-concepts/expand-icon.png).
* Öffnen oder verwalten Sie Ihre wichtigsten Inhalte, indem Sie **Favoriten** auswählen.
* Zum Anzeigen und Öffnen der zuletzt abgerufenen Inhalte wählen Sie **Zuletzt verwendet** aus.
* Zum Anzeigen, Öffnen oder Löschen von Apps wählen Sie **Apps** aus.
* Hat ein Kollege Inhalte für Sie freigegeben? Wählen Sie **Für mich freigegeben** aus, um nach den gewünschten Inhalten zu suchen und diese zu sortieren.
* Klicken Sie auf **Arbeitsbereiche**, um Ihre Arbeitsbereiche anzuzeigen und zu öffnen.

Einfachklick auf diese Elemente:

* auf ein Symbol oder eine Überschrift öffnet die Inhaltsansicht.
* auf einen Rechtspfeil (>) öffnet ein Flyoutmenü für Arbeitsbereiche, Favoriten und zuletzt verwendete Elemente.
* ein Doppelpfeilsymbol zeigt die scrollfähige Liste der Dashboards, Berichte, Arbeitsmappen und Datasets für **Mein Arbeitsbereich** an.

### <a name="2-canvas"></a>2. **Zeichenbereich**
Da wir ein Dashboard geöffnet haben, werden im Zeichenbereich Visualisierungskacheln angezeigt. Wenn z.B. der Berichts-Editor geöffnet wäre, würde im Zeichnungsbereich eine Berichtsseite angezeigt werden.

Dashboards bestehen aus [Kacheln](create-reports/service-dashboard-tiles.md).  Kacheln werden in der Bearbeitungsansicht, Q&A und anderen Dashboards für Berichte erstellt und können aus Excel, SSRS usw. angeheftet werden. Ein besonderer Kacheltyp namens [Widget](create-reports/service-dashboard-add-widget.md) wird dem Dashboard direkt hinzugefügt. Die auf einem Dashboard angezeigten Kacheln wurden vom Ersteller/Besitzer eines Berichts eigens dort abgelegt.  Das Hinzufügen einer Kachel zu einem Dashboard wird als *anheften* bezeichnet.

![Power BI-Dashboardzeichenbereich](media/service-basic-concepts/canvas.png)

Weitere Informationen finden Sie unter [Dashboards](#dashboards) (oben).

### <a name="3-qa-question-box"></a>3. **Fragenfeld für Fragen und Antworten (F&A)**
Eine Möglichkeit zum Untersuchen der Daten besteht darin, eine Frage zu stellen, um über den Bereich für Fragen und Antworten von Power BI eine Antwort in Form einer Visualisierung zu erhalten. Mit Q&A können Inhalte einem Dashboard oder einem Bericht hinzugefügt werden.

Der Bereich für Fragen und Antworten sucht im Dataset bzw. in Datasets, die mit dem Dashboard verbunden sind, nach Antworten.  Bei einem verbundenen Dataset handelt es sich um ein Dataset, für das mindestens eine Kachel an dieses Dashboard angeheftet ist.

![Fragenfeld für Fragen und Antworten (F&A)](media/service-basic-concepts/power-bi-qna.png)

Sobald Sie mit der Eingabe einer Frage beginnen, gelangen Sie zur Seite für Fragen und Antworten (F&A). Während der Eingabe unterstützt Sie der Bereich für Fragen und Antworten mithilfe von Umformulierungen, AutoAusfüllen, Vorschlägen usw. dabei, die richtige Frage zu stellen und die beste Antwort zu finden. Wenn Sie eine Visualisierung (Antwort) gefunden haben, die Ihnen gefällt, fügen Sie diese einfach zum Dashboard hinzu. Weitere Informationen finden Sie unter [Fragen und Antworten in Power BI](power-bi-q-and-a.md).

### <a name="4-icons-in-the-black-header-bar"></a>4. **Symbole in der schwarzen Kopfzeile**
Die Symbole in der rechten oberen Ecke sind Ihre Ressourcen für Einstellungen, Benachrichtigungen, Downloads, zum Öffnen der Hilfe, zum Aktivieren oder Deaktivieren von **Neues Design** und zum Senden von Feedback an das Power BI-Team.  

![Symbolschaltflächen](media/service-basic-concepts/power-bi-icons.png)

### <a name="5-dashboard-title-navigation-path-or-breadcrumbs"></a>5. **Dashboardtitel** (Navigationspfad oder Breadcrumbs)
Damit Sie leichter erkennen können, welcher Arbeitsbereich und welches Dashboard gerade aktiv ist, wird in Power BI automatisch ein Navigationspfad erstellt.  In diesem Beispiel sehen Sie den Arbeitsbereich („Mein Arbeitsbereich“) und den Dashboardtitel („Retail Analysis Sample“).  Wenn ein Bericht geöffnet wäre, wurde der Name des Berichts am Ende des Navigationspfads angehängt werden.  Jeder Abschnitt des Pfads ist ein aktiver Link.  

Beachten Sie das Symbol „C“ nach dem Dashboardtitel. Dieses Dashboard besitzt das [Datenklassifizierungstag](create-reports/service-data-classification.md) für „Vertraulich“. Das Tag gibt die Vertraulichkeits- und Sicherheitsstufe der Daten an. Wenn Ihr Administrator die Datenklassifizierung aktiviert hat, wird für jedes Dashboard ein Standardtag festgelegt. Dashboardbesitzer sollten das Tag entsprechend der richtigen Sicherheitsstufe des Dashboards ändern.

![Symbol für die Datenklassifizierung](media/service-basic-concepts/power-bi-title.png)

### <a name="6-office-365-app-launcher"></a>6. **Office 365-App-Startfeld**
Über das App-Startfeld können Sie mit einem Mausklick einfach auf alle Ihre Office 365-Apps zugreifen. Hier können Sie schnell Ihre E-Mails, Dokumente, Kalender und vieles mehr starten.

![Office App-Startfeld](media/service-basic-concepts/power-bi-waffle.png)

### <a name="7-power-bi-home"></a>7. **Power BI-Startseite**
Wenn Sie auf **Power BI** klicken, gelangen Sie zur Power BI-Startseite zurück.

   ![„Power BI“ im Dienst](media/service-basic-concepts/version-new.png)

### <a name="8-labeled-icons-in-the-gray-menu-bar"></a>8. **Gekennzeichnete Symbole in der grauen Menüleiste**
In diesem Bereich des Bildschirms finden Sie zusätzliche Optionen für die Interaktion mit Inhalten (in diesem Fall dem Dashboard).  Neben den beschrifteten Symbolen können Sie **Weitere Optionen (...)** auswählen, um Optionen zum Duplizieren, Drucken und Aktualisieren des Dashboards und mehr anzuzeigen.

   ![Beschriftete Symbolschaltflächen](media/service-basic-concepts/power-bi-labeled-icons.png)

## <a name="next-steps"></a>Nächste Schritte
- [Was ist Power BI?](fundamentals/power-bi-overview.md)  
- [Power BI-Videos](videos.md)  
- [Berichts-Editor – Verschaffen Sie sich einen Überblick](create-reports/service-the-report-editor-take-a-tour.md)
- Weitere Fragen? [Stellen Sie Ihre Frage in der Power BI-Community.](https://community.powerbi.com/)
