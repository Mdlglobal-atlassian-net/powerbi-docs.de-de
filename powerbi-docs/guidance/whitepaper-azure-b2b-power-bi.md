---
title: Verteilen von Power BI-Inhalten an externe Gastbenutzer mit Azure Active Directory B2B
description: Whitepaper, in dem beschrieben wird, wie Azure Active Directory B2B verwendet wird, um Power BI an externe Gastbenutzer zu verteilen
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 03/07/2019
ms.author: davidi
LocalizationGroup: Conceptual
ms.openlocfilehash: 955a14b37d59f554fb12b302c16472387c896e54
ms.sourcegitcommit: 220910f0b68cb1e265ccd5ac0cee4ee9c6080b26
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "82843639"
---
# <a name="distribute-power-bi-content-to-external-guest-users-using-azure-active-directory-b2b"></a>Verteilen von Power BI-Inhalten an externe Gastbenutzer mit Azure Active Directory B2B

**Zusammenfassung:** Dieses Whitepaper erläutert das Verteilen von Inhalten an Benutzer außerhalb der Organisation mithilfe der Integration von Azure Active Directory Business-to-Business (Azure AD B2B).

**Writer:** Lukasz Pawlowski, Kasper de Jonge

**Technische Reviewer:** Adam Wilson, Sheng Liu, Qian Liang, Sergei gundorov, Jacob Grimm, Adam Saxton, Maya shenhav, Nimrod Shalit, Elisabeth Olson

> [!NOTE]
> Sie können dieses Whitepaper speichern oder drucken, indem Sie in Ihrem Browser **Drucken** auswählen und dann **als PDF speichern**auswählen.

## <a name="introduction"></a>Einführung

Power BI bietet Organisationen einen 360-Fach Einblick in Ihr Unternehmen und ermöglicht allen Personen in diesen Organisationen das Treffen intelligenter Entscheidungen mithilfe von Daten. Viele dieser Organisationen verfügen über starke und vertrauenswürdige Beziehungen mit externen Partnern, Clients und Auftragnehmern. Diese Organisationen müssen den Benutzern dieser externen Partner einen sicheren Zugriff auf Power BI Dashboards und Berichte ermöglichen.

Power BI in [Azure Active Directory Business-to-Business (Azure AD B2B)](https://docs.microsoft.com/azure/active-directory/b2b/what-is-b2b) integriert, um die sichere Verteilung von Power BI Inhalten an Gastbenutzer außerhalb der Organisation zu ermöglichen – und gleichzeitig die Kontrolle zu behalten und den Zugriff auf interne Daten zu steuern.

Dieses Whitepaper behandelt alle Details, die Sie benötigen, um die Integration von Power BI in Azure Active Directory B2B zu verstehen. Wir behandeln den gängigsten Anwendungsfall, Setup, Lizenzierung und Sicherheit auf Zeilenebene.

> [!NOTE]
> In diesem Whitepaper bezeichnen wir Azure Active Directory als Azure AD und Azure Active Directory Business to Business as Azure AD B2B.

## <a name="scenarios"></a>Szenarien

"Configuration Manager" ist ein Automobilhersteller, der mit vielen unterschiedlichen Lieferanten zusammenarbeitet, die ihm alle Komponenten, Materialien und Dienste zur Verfügung stellen, die für die Ausführung der Fertigungs Vorgänge erforderlich sind. Die Lieferkette der Lieferkette muss von "fitoso" optimiert werden, und es ist geplant, Power BI zur Überwachung wichtiger Leistungsmetriken der Lieferkette zu verwenden. Mit der Analyse der externen Lieferkettenpartner möchte man eine sichere und verwaltbare Methode nutzen.

Mit dem Power BI und Azure AD B2B können externe Benutzer mit der folgenden Oberfläche arbeiten.

### <a name="ad-hoc-per-item-sharing"></a>Ad-hoc-Freigabe pro Element

Mit einem Lieferanten, der die Heizkörper für die Fahrzeuge von der Stadt von "The Cars" erstellt, funktioniert " Häufig müssen Sie die Zuverlässigkeit der Heizkörper mithilfe von Daten aus allen "" von "" von "" von "" von "". Ein Analyst bei "Configuration Manager" verwendet Power BI, um einen Bericht über die Heizkörper Zuverlässigkeit mit einem Techniker beim Lieferanten gemeinsam zu nutzen. Der Techniker erhält eine e-Mail mit einem Link, um den Bericht anzuzeigen.

Wie oben beschrieben, wird diese Ad-hoc-Freigabe von Geschäfts Benutzern bei Bedarf ausgeführt. Der von Power BI an den externen Benutzer gesendete Link ist ein Azure AD B2B-Einladungslink. Wenn der externe Benutzer den Link öffnet, wird er aufgefordert, der Azure AD Organisation von "Configuration Manager" als Gastbenutzer beizutreten. Nachdem die Einladung angenommen wurde, wird der jeweilige Bericht bzw. das betreffende Dashboard geöffnet. Der Azure Active Directory Administrator delegiert die Berechtigung zum einladen externer Benutzer zur Organisation und wählt, was diese Benutzer tun können, sobald Sie die Einladung akzeptieren, wie im Abschnitt Governance dieses Dokuments beschrieben. Der IT-Analyst kann den Gastbenutzer nur einladen, weil der Azure AD Administrator diese Aktion zugelassen hat und der Power BI Administrator Benutzern gestattet hat, Gäste aufzufordern, Inhalte in den Mandanten Einstellungen Power BI anzuzeigen.

![Einladen von Gästen zum Power BI mit Aad](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_01.png)

1. Der Prozess beginnt mit einem internen Benutzer von "Configuration Manager", der ein Dashboard oder einen Bericht mit einem externen Benutzer freigibt. Wenn der externe Benutzer noch kein Gast in der Azure AD von "Configuration Manager" ist, werden Sie eingeladen. Eine e-Mail wird an Ihre e-Mail-Adresse gesendet, die eine Einladung zu den Azure AD von "Configuration Manager" enthält.
2. Der Empfänger akzeptiert die Einladung zum Azure AD von "Azure AD" und wird als Gastbenutzer in der von "" hinzugefügt.
3. Der Empfänger wird dann an das Power BI Dashboard, den Bericht oder die APP umgeleitet, die für den Benutzer schreibgeschützt sind.

Der Prozess wird als Ad-hoc angesehen, da Geschäfts Benutzer in "Azure" die Einladungs Aktion nach Bedarf für Ihre geschäftlichen Zwecke ausführen. Jedes freigegebene Element ist ein einzelner Link, auf den der externe Benutzer zugreifen kann, um den Inhalt anzuzeigen.

Nachdem der externe Benutzer eingeladen wurde, auf die Ressourcen von "fitoso" zuzugreifen, kann ein Schatten Konto für Sie in der Azure AD von "Configuration Manager" erstellt werden, und Sie müssen nicht erneut eingeladen werden.  Wenn Sie zum ersten Mal versuchen, auf eine Ressource von "Configuration Manager" (z. b. ein Power BI Dashboard) zuzugreifen, durchlaufen Sie einen Zustimmungsprozess, der die Einladung einlöst.  Wenn Sie die Zustimmung nicht erfüllen, können Sie nicht auf den Inhalt von "fium" zugreifen.  Wenn Sie Probleme haben, Ihre Einladung über den ursprünglich bereitgestellten Link einlösen zu müssen, kann ein Azure AD Administrator einen bestimmten Einladungslink erneut senden, um ihn einlösen zu können.

### <a name="planned-per-item-sharing"></a>Geplante Freigabe pro Element

Mit einem Subauftragnehmer kann von "Configuration Manager" eine Zuverlässigkeitsanalyse durchgeführt werden. Der Subauftragnehmer verfügt über ein Team von 10 Personen, die Zugriff auf Daten in der Power BI Umgebung von "Configuration Manager" benötigen. Der Azure AD Administrator von "Configuration Manager" ist daran beteiligt, alle Benutzer einzuladen und Ergänzungen und Änderungen zu behandeln, wenn sich die Mitarbeiter des subauftragnehmers ändern. Der Azure AD-Administrator erstellt eine Sicherheitsgruppe für alle Mitarbeiter des subauftragnehmers. Mithilfe der Sicherheitsgruppe können die Mitarbeiter von Configuration Manager den Zugriff auf Berichte problemlos verwalten und sicherstellen, dass alle erforderlichen Subauftragnehmer-Mitarbeiter Zugriff auf alle erforderlichen Berichte, Dashboards und Power BI-apps haben. Der Azure AD-Administrator kann auch vermeiden, dass er am Einladungsprozess beteiligt ist, indem er die Einladung von Einladungs Rechten an einen vertrauenswürdigen Mitarbeiter bei der Gruppe von "Configuration Manager" delegiert.

Einige Organisationen benötigen mehr Kontrolle darüber, wann externe Benutzer hinzugefügt werden, und laden viele Benutzer in einer externen Organisation oder in vielen externen Organisationen ein. In diesen Fällen kann die geplante Freigabe verwendet werden, um den Umfang der Freigabe zu verwalten, Organisations Richtlinien zu erzwingen und sogar Rechte an vertrauenswürdige Personen zu delegieren, um externe Benutzer einzuladen und zu verwalten. Azure AD B2B unterstützt geplante Einladungen, [die von einem IT-Administrator direkt von der Azure-Portal](https://docs.microsoft.com/azure/active-directory/b2b/add-users-administrator)gesendet werden können, oder über [PowerShell mithilfe der Einladungs-Manager-API](https://docs.microsoft.com/azure/active-directory/b2b/customize-invitation-api) , bei der eine Gruppe von Benutzern in eine Aktion eingeladen werden kann. Mithilfe des Ansatzes für geplante Einladungen kann die Organisation steuern, wer Benutzer einladen und Genehmigungsprozesse implementieren kann. Erweiterte Azure AD Funktionen wie dynamische Gruppen erleichtern das automatische Verwalten der Mitgliedschaft in Sicherheitsgruppen.


![Steuern, welche Gäste Inhalte sehen können](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_02.png)



1. Der Prozess Sterne mit einem IT-Administrator lädt den Gastbenutzer entweder manuell oder über die Azure Active Directory von bereitgestellte API ein.
2. Der Benutzer akzeptiert die Einladung für die Organisation.
3. Nachdem der Benutzer die Einladung akzeptiert hat, kann ein Benutzer in Power BI einen Bericht oder ein Dashboard für den externen Benutzer oder eine Sicherheitsgruppe freigeben, in der er sich befindet. Genau wie bei der regulären Freigabe in Power BI der externe Benutzer eine e-Mail mit dem Link zum Element erhalten.
4. Wenn der externe Benutzer auf den Link zugreift, wird die Authentifizierung in Ihrem Verzeichnis an die Azure AD von "fitoso" übermittelt und für den Zugriff auf den Power BI Inhalt verwendet.

### <a name="ad-hoc-or-planned-sharing-of-power-bi-apps"></a>Ad-hoc-oder geplante Freigabe von Power BI-apps

Für "Configuration Manager" gibt es eine Reihe von Berichten und Dashboards, die Sie für einen oder mehrere Lieferanten freigeben müssen. Um sicherzustellen, dass alle erforderlichen externen Benutzer auf diese Inhalte zugreifen können, wird Sie als Power BI-App verpackt. Die externen Benutzer werden entweder direkt der APP-Zugriffsliste oder Sicherheitsgruppen hinzugefügt. Eine Person bei der Verbindung mit der APP sendet die App-URL an alle externen Benutzer, z. b. in einer e-Mail. Wenn die externen Benutzer den Link öffnen, sehen Sie den gesamten Inhalt in einer einzigen leicht zu navigierbaren Benutzeroberflächen.

Die Verwendung einer Power BI-App vereinfacht das Erstellen eines BI-Portals für die Lieferanten durch "Configuration Manager". Eine einzige Zugriffsliste steuert den Zugriff auf alle erforderlichen Inhalte, wodurch das Überprüfen der Wartezeit und das Festlegen von Berechtigungen auf Element Ebene reduziert wird. Azure AD B2B verwaltet den Sicherheits Zugriff mithilfe der nativen Identität des Lieferanten, sodass Benutzer keine zusätzlichen Anmelde Informationen benötigen. Wenn Sie geplante Einladungen mit Sicherheitsgruppen verwenden, wird die Zugriffs Verwaltung auf die APP vereinfacht, wenn Personal in das oder aus dem Projekt gedreht wird. Mitgliedschaft in Sicherheitsgruppen manuell oder mithilfe [dynamischer Gruppen](https://docs.microsoft.com/azure/active-directory/b2b/use-dynamic-groups), sodass alle externen Benutzer von einem Lieferanten automatisch der entsprechenden Sicherheitsgruppe hinzugefügt werden.


![Steuern von Inhalten mit Aad](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_03.png)

1. Der Prozess beginnt damit, dass der Benutzer über die Azure-Portal oder PowerShell zur Azure AD Organisation von "" eingeladen wird.
2. Der Benutzer kann in Azure AD einer Benutzergruppe hinzugefügt werden. Eine statische oder dynamische Benutzergruppe kann verwendet werden, aber dynamische Gruppen helfen bei der Reduzierung der manuellen Arbeit.
3. Die externen Benutzer erhalten Zugriff auf die Power BI-App über die Benutzergruppe. Die App-URL sollte direkt an den externen Benutzer gesendet oder auf einer Website platziert werden, auf die Sie Zugriff haben. Power BI versucht, eine e-Mail mit dem App-Link an externe Benutzer zu senden, aber wenn Benutzergruppen verwendet werden, deren Mitgliedschaft geändert werden kann, kann Power BI nicht an alle externen Benutzer senden, die durch Benutzergruppen verwaltet werden.
4. Wenn der externe Benutzer auf die URL der Power BI-App zugreift, wird er von der Azure AD von "" authentifiziert, die APP wird für den Benutzer installiert, und der Benutzer kann alle enthaltenen Berichte und Dashboards innerhalb der App anzeigen.

Apps verfügen auch über ein eindeutiges Feature, mit dem App-Autoren die Anwendung automatisch für den Benutzer installieren können, sodass Sie verfügbar ist, wenn sich der Benutzer anmeldet. Diese Funktion wird nur automatisch für externe Benutzer installiert, die zu dem Zeitpunkt, zu dem die Anwendung veröffentlicht oder aktualisiert wird, bereits Teil der Organisation von "Configuration" ist. Daher wird es am besten mit dem Plan für geplante Einladungen verwendet und hängt von der App ab, die veröffentlicht oder aktualisiert wird, nachdem die Benutzer zu den Azure AD von "Configuration Manager" hinzugefügt wurden. Externe Benutzer können die APP immer über den App-Link installieren.

### <a name="commenting-and-subscribing-to-content-across-organizations"></a>Kommentieren und Abonnieren von Inhalten zwischen Organisationen

Da die Mitarbeiter von "Configuration Manager" weiterhin mit den unter Unternehmen oder Lieferanten zusammenarbeiten können, müssen die externen Techniker eng mit den Analysten von "zusammenarbeiten". Power BI bietet mehrere Features für die Zusammenarbeit, mit denen Benutzer über Inhalte kommunizieren können, die Sie nutzen können. Durch das Abonnieren von Dashboards (und das kurze kommentieren von Berichten) können Benutzerdaten Punkte erörtern, die Ihnen angezeigt werden, und mit den Berichts Autoren kommunizieren, um Fragen

Derzeit können externe Gastbenutzer an Kommentaren teilnehmen, indem Sie Kommentare hinterlassen und die Antworten lesen. Im Unterschied zu internen Benutzern können Gastbenutzer jedoch nicht sein, @mentioned und Sie erhalten keine Benachrichtigungen, dass Sie einen Kommentar erhalten haben. Gastbenutzer können die Funktion "Abonnements" nicht innerhalb Power BI zum Zeitpunkt der Erstellung verwenden. In einer zukünftigen Version werden diese Einschränkungen aufgehoben, und der Gastbenutzer erhält eine e-Mail, wenn er einen Kommentar erhält @mentions , oder wenn ein Abonnement an die e-Mail-Adresse gesendet wird, die einen Link zum Inhalt in Power BI enthält.

### <a name="access-content-in-the-power-bi-mobile-apps"></a>Zugreifen auf Inhalte in den mobilen Power BI-apps

Wenn in einer zukünftigen Version Berichte oder Dashboards von den Benutzern von "Kunden" gemeinsam mit Ihren externen Gast-Kollegen gemeinsam genutzt werden, sendet Power BI eine e-Mail, in der der Gast benachrichtigt wird. Wenn der Gastbenutzer den Link zum Bericht oder Dashboard auf dem mobilen Gerät öffnet, wird der Inhalt in den systemeigenen Power BI mobilen apps auf dem Gerät geöffnet, sofern diese installiert sind. Der Gastbenutzer ist dann in der Lage, zwischen den für Sie freigegebenen Inhalten im externen Mandanten und zurück zu seinem eigenen Inhalt von seinem privat Mandanten zu navigieren.

> [!NOTE]
> Der Gastbenutzer kann die Power BI Mobile App nicht öffnen und sofort zum externen Mandanten navigieren. er muss mit einem Link zu einem Element im externen Mandanten beginnen. Allgemeine Problem Umgehungen werden im Abschnitt [Verteilen von Links zu Inhalten im Power BI der übergeordneten Organisation weiter](#distributing-links-to-content-in-the-parent-organizations-power-bi) unten in diesem Dokument beschrieben.

### <a name="cross-organization-editing-and-management-of-power-bi-content"></a>Organisations übergreifende Bearbeitung und Verwaltung von Power BI Inhalt

Die Zusammenarbeit zwischen dem und seinen Lieferanten und Unterauftragnehmern ist immer enger. Häufig benötigt ein Analyst des subauftragnehmers zusätzliche Metriken oder Datenvisualisierungen, die zu einem Bericht hinzugefügt werden, der von "Configuration Manager" für Sie freigegeben wurde. Die Daten sollten sich im Power BI Mandanten von "Configuration Manager" befinden, aber externe Benutzer sollten Sie bearbeiten, neue Inhalte erstellen und sogar an die entsprechenden Personen verteilen können.

Power BI bietet eine Option, mit der **externe Gastbenutzer Inhalte in der Organisation bearbeiten und verwalten können** . Standardmäßig verfügen externe Benutzer über einen schreibgeschützten Verwendungs orientierten Gebrauch. Mit dieser neuen Einstellung kann der Power BI Administrator jedoch auswählen, welche externen Benutzerinhalte innerhalb ihrer eigenen Organisation bearbeiten und verwalten können. Nach der Zulassung kann der externe Benutzer Berichte, Dashboards, Apps veröffentlichen oder aktualisieren, in Arbeitsbereichen arbeiten und eine Verbindung mit Daten herstellen, deren Verwendung Sie verwenden möchten.

Dieses Szenario wird im Abschnitt "Aktivieren externer Benutzer zum Bearbeiten und Verwalten von Inhalten in Power BI weiter unten in diesem Dokument ausführlich beschrieben.

## <a name="organizational-relationships-using-power-bi-and-azure-ad-b2b"></a>Organisations Beziehungen mithilfe von Power BI und Azure AD B2B

Wenn alle Benutzer von Power BI für die Organisation intern sind, besteht keine Notwendigkeit, Azure AD B2B zu verwenden. Wenn jedoch zwei oder mehr Organisationen an Daten und Einsichten zusammenarbeiten möchten, ist die Unterstützung von Azure AD B2B durch Power BI die einfache und kostengünstige Lösung.

Im folgenden finden Sie in der Regel Organisationsstrukturen, die sich gut für Azure AD B2B-Stil übergreifende Zusammenarbeit in Power BI eignen. Azure AD B2B funktioniert in den meisten Fällen gut, aber in einigen Situationen sind die allgemeinen alternativen Ansätze, die am Ende dieses Dokuments abgedeckt werden, in Erwägung gezogen.

### <a name="case-1-direct-collaboration-between-organizations"></a>Fall 1: direkte Zusammenarbeit zwischen Organisationen

Die Beziehung zwischen der Beziehung zwischen und Ihrem Heizkörper Lieferanten ist ein Beispiel für die direkte Zusammenarbeit zwischen Organisationen. Da es relativ wenig Benutzer bei "Configuration Manager" gibt, und der Lieferant, der Zugriff auf die Informationen zur Heiz Zuverlässigkeit benötigt, ist die Verwendung Azure AD B2B-basierten externen Freigabe ideal. Es ist einfach zu verwenden und einfach zu verwalten. Dies ist auch ein gängiges Muster in Beratungsdiensten, in dem ein Berater möglicherweise Inhalte für eine Organisation erstellen muss.

![Freigabe zwischen Organisationen](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_04.png)


Diese Freigabe erfolgt in der Regel zunächst mithilfe der Ad-hoc-Freigabe pro Element. Wenn sich die Teams jedoch vergrößern oder Beziehungen vertiefen, wird der geplante Freigabe Ansatz pro Element zur bevorzugten Methode, um den Verwaltungsaufwand zu reduzieren. Darüber hinaus kann die Ad-hoc-oder geplante Freigabe von Power BI-apps, das kommentieren und Abonnieren von Inhalten in Unternehmen, der Zugriff auf Inhalte in Mobile Apps und die Organisations übergreifende Bearbeitung und Verwaltung von Power BI Inhalten ebenfalls durch die Organisation erfolgen. Wichtig: Wenn die Benutzer beider Organisationen über Power BI pro Lizenzen in den jeweiligen Organisationen verfügen, können Sie diese pro-Lizenzen in den Power BI Umgebungen der anderen verwenden. Dies bietet eine vorteilhafte Lizenzierung, da die einladende Organisation möglicherweise nicht für eine Power BI pro Lizenz für externe Benutzer bezahlen muss. Dies wird im Abschnitt zur Lizenzierung weiter unten in diesem Dokument ausführlicher erläutert.

### <a name="case-2-parent-and-its-subsidiaries-or-affiliates"></a>Fall 2: übergeordnetes Element und seine Tochtergesellschaften oder Tochtergesellschaften

Einige Organisationsstrukturen sind komplexer, einschließlich teilweiser oder vollständig eigener Niederlassungen, verbundener Unternehmen oder verwalteter Dienstanbieter Beziehungen. Diese Organisationen verfügen über eine übergeordnete Organisation, z. b. ein firmeneigenes Unternehmen, aber die zugrunde liegenden Organisationen arbeiten teilweise unabhängig voneinander unterschiedlichen regionalen Anforderungen. Dies führt dazu, dass jede Organisation über eine eigene Azure AD Umgebung verfügt und Power BI Mandanten trennt.

![Arbeiten mit Niederlassungen](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_05.png)


In dieser Struktur muss die übergeordnete Organisation in der Regel standardisierte Einblicke an seine Niederlassungen verteilen. Diese Freigabe erfolgt in der Regel mithilfe der Ad-hoc-oder der geplanten Freigabe von Power BI apps-Ansatz, wie in der folgenden Abbildung dargestellt, da Sie die Verteilung standardisierter autorisierter Inhalte an große Zielgruppen ermöglicht. In der Praxis wird eine Kombination aus allen zuvor in diesem Dokument erwähnten Szenarien verwendet.

![Kombinieren von Szenarien](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_06.png)


Dies folgt dem folgenden Prozess:

1. Benutzer der einzelnen Niederlassungen werden zu den Azure AD von "Configuration Manager" eingeladen.
2. Anschließend wird die Power BI-App veröffentlicht, um diesen Benutzern den Zugriff auf die erforderlichen Daten zu erhalten.
3. Schließlich öffnen die Benutzer die APP über einen Link, den Sie erhalten haben, um die Berichte anzuzeigen.

Unternehmen in dieser Struktur haben einige wichtige Herausforderungen:

- Verteilen von Links zu Inhalten in den Power BI der übergeordneten Organisation
- Gewähren von Zugriff auf die Datenquelle, die von der übergeordneten Organisation gehostet wird

#### <a name="distributing-links-to-content-in-the-parent-organizations-power-bi"></a>Verteilen von Links zu Inhalten im Power BI der übergeordneten Organisation

Zum Verteilen von Links an den Inhalt werden üblicherweise drei Ansätze verwendet. Die erste und einfachste Möglichkeit besteht darin, den Link an die APP an die erforderlichen Benutzer zu senden oder Sie auf einer SharePoint Online-Website zu platzieren, von der Sie geöffnet werden kann. Benutzer können dann den Link in ihren Browsern markieren, um schnelleren Zugriff auf die benötigten Daten zu erhalten.

Der zweite Ansatz basiert auf der Organisations übergreifenden Bearbeitung und Verwaltung Power BI Inhalts Funktionen. Die übergeordnete Organisation ermöglicht es Benutzern aus den Niederlassungen, auf Ihre Power BI zuzugreifen und zu steuern, auf welche Berechtigungen Sie über die Berechtigung zugreifen können. Dies ermöglicht den Zugriff auf Power BI Startseite, wo der Benutzer aus der Niederlassung eine umfassende Liste von Inhalten erhält, die für ihn im Mandanten der übergeordneten Organisation freigegeben wurden. Dann wird die URL zur Power BI Umgebung der übergeordneten Organisationen den Benutzern in den Niederlassungen erteilt.

Beim letzten Ansatz wird eine Power BI-App verwendet, die innerhalb des Power BI-Mandanten für jede Niederlassung erstellt wurde. Die Power BI-app enthält ein Dashboard mit [Kacheln, die mit der Option externer Link konfiguriert](https://docs.microsoft.com/power-bi/service-dashboard-edit-tile#hyperlink)sind. Wenn der Benutzer die Kachel drückt, werden Sie im Power BI der übergeordneten Organisation an den entsprechenden Bericht, das gewünschte Dashboard oder die entsprechende App geleitet. Dieser Ansatz bietet den zusätzlichen Vorteil, dass die APP automatisch für alle Benutzer in der Niederlassung installiert werden kann und Ihnen zur Verfügung steht, wenn Sie sich bei ihrer eigenen Power BI Umgebung anmelden. Ein zusätzlicher Vorteil dieses Ansatzes besteht darin, dass er gut für die Power BI mobilen apps funktioniert, die den Link System intern öffnen können. Dies kann auch mit dem zweiten Ansatz kombiniert werden, um einen einfacheren Wechsel zwischen Power BI-Umgebungen zu ermöglichen.

#### <a name="allowing-subsidiary-users-to-access-data-sources-hosted-by-the-parent-organization"></a>Gestatten von Tochter Benutzern den Zugriff auf Datenquellen, die von der übergeordneten Organisation gehostet werden

Häufig müssen Analysten an einer Tochtergesellschaft mithilfe von Daten, die von der übergeordneten Organisation bereitgestellt werden, eigene Analysen erstellen. In diesem Fall werden häufig clouddatenquellen verwendet, um die Herausforderung zu beheben.

Der erste Ansatz nutzt [Azure Analysis Services](https://docs.microsoft.com/azure/analysis-services/analysis-services-overview) , um eine unternehmensweite Data Warehouse zu erstellen, die die Anforderungen von Analysten über das übergeordnete Element und seine Niederlassungen erfüllt, wie in der folgenden Abbildung dargestellt. Von "Configuration Manager" können die Daten gehostet und Funktionen wie Sicherheit auf Zeilenebene verwendet werden, um sicherzustellen, dass Benutzer in jeder Tochter nur auf Ihre Daten zugreifen können. Analysten in den einzelnen Organisationen können über Power BI Desktop auf die Data Warehouse zugreifen und resultierende Analysen auf ihren jeweiligen Power BI Mandanten veröffentlichen.

![So erfolgt die Freigabe mit Power BI Mandanten](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_07.png)


Der zweite Ansatz nutzt [Azure SQL-Datenbank](https://azure.microsoft.com/services/sql-database/) , um eine relationale Data Warehouse zu erstellen, um den Zugriff auf Daten zu ermöglichen. Dies funktioniert ähnlich wie bei der Azure Analysis Services Herangehensweise, obwohl einige Funktionen wie die Sicherheit auf Zeilenebene für die Bereitstellung und Verwaltung von Niederlassungen hinweg möglicherweise schwieriger sind.

Es sind auch anspruchsvollere Ansätze möglich, die oben genannten sind jedoch die gängigste Vorgehensweise.

### <a name="case-3-shared-environment-across-partners"></a>Fall 3: gemeinsam genutzte Umgebung zwischen Partnern

Bei der Zusammenarbeit mit einem Mitbewerber ist es möglich, ein Auto in einer gemeinsam genutzten assemblyleitung zu erstellen, das Fahrzeug jedoch unter verschiedenen Marken oder in verschiedenen Regionen zu verteilen. Dies erfordert umfassende Zusammenarbeit und gemeinsamen Besitz von Daten, Intelligenz und Analysen in Organisationen. Diese Struktur ist auch in der Consulting Services-Branche üblich, in der ein Team von Beratern eine Projekt basierte Analyse für einen Client durchführen kann.

![Gemeinsam genutzte Umgebung zwischen Partnern](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_08.png)



In der Praxis sind diese Strukturen Komplex, wie in der folgenden Abbildung dargestellt, und erfordern die Pflege von Mitarbeitern. Um effektiv zu sein, basiert diese Struktur auf der Organisations übergreifenden Bearbeitung und Verwaltung von Power BI Inhalts Funktionen, da Sie es Organisationen ermöglichen, Power BI pro Lizenzen wiederzuverwenden, die für ihre jeweiligen Power BI Mandanten erworben wurden.

![Lizenzen und freigegebene Organisations Inhalte](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_09.png)



Zum Einrichten eines freigegebenen Power BI Mandanten muss ein Azure Active Directory erstellt werden, und mindestens ein Power BI pro Benutzerkonto muss für einen Benutzer in diesem Active Directory erworben werden. Dieser Benutzer fordert die erforderlichen Benutzer der gemeinsam genutzten Organisation an. Wichtig: in diesem Szenario werden die Benutzer von "Configuration Manager" als externe Benutzer behandelt, wenn Sie innerhalb der Power BI der gemeinsam genutzten Organisation arbeiten.

Der Prozess sieht folgendermaßen aus:

1. Die freigegebene Organisation wird als neue Azure Active Directory erstellt, und mindestens ein Benutzerkonto wird in der neuen Organisation erstellt. Diesem Benutzer sollte eine Power BI pro Lizenz zugewiesen sein.
2. Dieser Benutzer richtet dann einen Power BI-Mandanten ein und fordert die erforderlichen Benutzer von "Configuration Manager" und der Partner Organisation an. Der Benutzer legt auch alle freigegebenen datenassets wie Azure Analysis Services fest. Die Benutzer von "Configuration Manager" und "Partner" können als Gastbenutzer auf die Power BI der gemeinsam genutzten Organisation zugreifen. Wenn das Bearbeiten und Verwalten von Inhalten in gestattet ist Power BI können externe Benutzer Power BI Startseite verwenden, Arbeitsbereiche verwenden, Inhalte hochladen oder bearbeiten und Berichte freigeben. In der Regel werden alle freigegebenen Assets gespeichert, und der Zugriff erfolgt über die freigegebene Organisation.
3. Je nachdem, wie die Parteien mit der Zusammenarbeit einverstanden sind, ist es für jede Organisation möglich, eigene proprietäre Daten und Analysen mithilfe von freigegebenen Data Warehouse Ressourcen zu entwickeln. Sie können diese mithilfe ihrer internen Power BI Mandanten an die entsprechenden internen Benutzer verteilen.

### <a name="case-4-distribution-to-hundreds-or-thousands-of-external-partners"></a>Fall 4: Verteilung auf Hunderte oder Tausende externer Partner

Während von "Configuration Manager" ein Bericht zur Zuverlässigkeit der Zuverlässigkeit für einen Lieferanten erstellt wurde, möchte ich, dass "Configuration Manager" nun einen Satz standardisierter Berichte für Hunderte von Zulieferern erstellen möchte. Auf diese Weise kann von "Configuration Manager" sichergestellt werden, dass alle Lieferanten über die Analyse verfügen, die Sie benötigen, um Verbesserungen vorzunehmen

![Verteilung an viele Partner](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_10.png)


Wenn eine Organisation standardisierte Daten und Einblicke an viele externe Benutzer/Organisationen verteilen muss, können Sie die Ad-hoc-oder geplante Freigabe von Power BI apps-Szenario verwenden, um schnell und ohne umfassende Entwicklungskosten ein BI-Portal zu erstellen. Der Prozess zum Erstellen eines solchen Portals mithilfe einer Power BI-APP wird in der Fallstudie: Erstellen eines BI-Portals mit Power BI + Azure AD B2B – Schritt-für-Schritt-Anweisungen weiter unten in diesem Dokument behandelt.

Eine gängige Variante dieses Szenarios ist, wenn eine Organisation versucht, Erkenntnisse mit Consumern auszutauschen, insbesondere wenn Sie Azure B2C mit Power BI verwenden möchten. Power BI bietet keine native Unterstützung für Azure B2C. Wenn Sie die Optionen für diesen Fall auswerten, empfiehlt es sich, die alternative Option 2 in der allgemeinen Alternative zu verwenden, die im Abschnitt weiter unten in diesem Dokument erläutert wird.

## <a name="case-study-building-a-bi-portal-using-power-bi--azure-ad-b2b--step-by-step-instructions"></a>Fallstudie: Aufbau eines BI-Portals mit Power BI + Azure AD B2B – Schritt-für-Schritt-Anweisungen

Die Integration von Power BI in Azure AD B2B sorgt für eine nahtlose und unkomplizierte Möglichkeit, Gastbenutzern einen sicheren Zugriff auf das BI-Portal zu ermöglichen. Dies kann von "Configuration Manager" in drei Schritten festgelegt werden:

![Aufbauen eines Portals](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_11.png)


1. Erstellen eines BI-Portals in Power BI

    Die erste Aufgabe von "Configuration Manager" besteht darin, das BI-Portal in Power BI zu erstellen. Das BI-Portal von Configuration Manager besteht aus einer Sammlung von speziell erstellten Dashboards und Berichten, die vielen internen und Gastbenutzern zur Verfügung gestellt werden. Die empfohlene Vorgehensweise in Power BI besteht darin, eine Power BI-APP zu erstellen. Erfahren Sie mehr über [apps in Power BI](https://powerbi.microsoft.com/blog/distribute-to-large-audiences-with-power-bi-apps/).

- Das BI-Team von Configuration Manager erstellt einen Arbeitsbereich in Power BI

    ![Arbeitsbereich](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_12.png)
    

- Weitere Autoren werden dem Arbeitsbereich hinzugefügt.

    ![Hinzufügen von Autoren](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_13.png)


- Der Inhalt wird innerhalb des Arbeitsbereichs erstellt.

    ![Inhalt innerhalb des Arbeitsbereichs erstellen](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_14.png)


    Nachdem der Inhalt nun in einem Arbeitsbereich erstellt wurde, kann er von der Gastbenutzer in Partnerorganisationen eingeladen werden, diesen Inhalt zu nutzen.

2. Einladen von Gastbenutzern

    Es gibt zwei Möglichkeiten für die Einladung von "Gastbenutzer" in das BI-Portal in Power BI:

    * Geplante Einladungen
    * Ad-hoc-Einladungen

    **Geplante Einladungen**

    Bei dieser Vorgehensweise werden die Gastbenutzer von "Configuration Manager" im Voraus zum Azure AD aufgefordert und dann Power BI Inhalt an diese verteilt. Mithilfe von "Configuration Manager" können Gastbenutzer aus dem Azure-Portal oder mithilfe von PowerShell eingeladen werden. Hier finden Sie die Schritte zum Einladen von Gastbenutzern aus der Azure-Portal:

    - Der Azure AD Administrator von "Configuration Manager" navigiert zu **Azure-Portal > Azure Active Directory > Benutzer und Gruppen > alle Benutzer > neuen Gastbenutzer** .

    ![Gastbenutzer](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_15.png)


    - Fügen Sie eine Einladungs Nachricht für Gastbenutzer hinzu, und klicken Sie auf einladen.

    ![Einladung hinzufügen](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_16.png)


    > [!NOTE]
    > Um Gastbenutzer aus dem Azure-Portal einzuladen, müssen Sie ein Administrator für die Azure Active Directory Ihres Mandanten sein.

    Wenn von "mso" viele Gastbenutzer eingeladen werden sollen, können Sie dies mithilfe von PowerShell tun. Der Azure AD Administrator von "Configuration Manager" speichert die e-Mail-Adressen aller Gastbenutzer in einer CSV-Datei. Hier finden Sie [Azure Active Directory B2B-Kollaborations Code und PowerShell-Beispiele](https://docs.microsoft.com/azure/active-directory/b2b/code-samples) und-Anweisungen.

    Nach der Einladung erhalten Gastbenutzer eine e-Mail mit dem Einladungslink.

    ![Einladungs Verknüpfung](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_17.png)


    Nachdem die Gastbenutzer auf den Link klicken, können Sie auf den Inhalt im Azure AD Mandanten von "" zugreifen.

    > [!NOTE]
    > Es ist möglich, das Layout der Einladungs-e-Mail mithilfe des Azure AD brandingfeatures zu ändern, wie [hier](https://docs.microsoft.com/azure/active-directory/active-directory-b2b-invitation-email)beschrieben.


    **Ad-hoc-Einladungen**

    Was geschieht, wenn "Configuration Manager" nicht alle Gastbenutzer kennt, die Sie im Voraus einladen möchten? Oder was ist, wenn der Analyst in der Rolle von "Configuration Manager", der das BI-Portal erstellt hat, Inhalte an Gastbenutzer selbst verteilen möchte? Wir unterstützen dieses Szenario auch in Power BI mit Ad-hoc-Einladungen.

    Der Analyst kann die externen Benutzer einfach der Zugriffsliste der APP hinzufügen, wenn Sie Sie veröffentlichen. Die Gastbenutzer erhalten eine Einladung, und sobald Sie Sie akzeptieren, werden Sie automatisch an den Power BI Inhalt umgeleitet.

    ![Externen Benutzer hinzufügen](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_18.png)


    > [!NOTE]
    > Einladungen werden nur benötigt, wenn ein externer Benutzer zum ersten Mal in Ihre Organisation eingeladen wird.


3. Treiberpakete

    Nachdem das BI-Team von Configuration Manager das BI-Portal erstellt und Gastbenutzer eingeladen hat, kann es das Portal an seine Endbenutzer verteilen, indem er Gastbenutzern den Zugriff auf die APP gewährt und diese veröffentlicht. Power BI Namen der Gastbenutzer, die zuvor dem Mandanten von "Configuration Manager" hinzugefügt wurden, automatisch vervollständigen. An dieser Stelle können auch Ad-hoc-Einladungen zu anderen Gastbenutzern hinzugefügt werden.

    > [!NOTE]
    > Wenn Sie Sicherheitsgruppen verwenden, um den Zugriff auf die APP für externe Benutzer zu verwalten, verwenden Sie den Ansatz für geplante Einladungen, und geben Sie den App-Link direkt für jeden externen Benutzer frei, der darauf zugreifen muss. Andernfalls ist der externe Benutzer möglicherweise nicht in der Lage, Inhalte innerhalb der APP zu installieren oder anzuzeigen.

    Gastbenutzer erhalten eine e-Mail mit einem Link zur APP.

    ![Link für e-Mail-Einladung](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_19.png)


    Wenn Sie auf diesen Link klicken, werden Gastbenutzer aufgefordert, sich mit der Identität ihrer eigenen Organisation zu authentifizieren.

    ![Anmeldeseite](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_20.png)


    Sobald Sie erfolgreich authentifiziert wurden, werden Sie an die BI-APP von "apptoso" umgeleitet.

    ![Anzeigen von freigegebenen Inhalten](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_21.png)

    Gastbenutzer können dann die APP von "" von "" von "" von "" von "" der App "" von "" auf den Link klicken. Dies kann auch für Gastbenutzer durch das Hinzufügen dieses Links zu einem vorhandenen Extranetportal, das die Gastbenutzer bereits verwenden, vereinfacht werden.

4. Nächste Schritte

    Mit einer Power BI-APP und Azure AD B2B konnte von "Configuration Manager" schnell ein BI-Portal für seine Lieferanten ohne Code erstellt werden. Dadurch wurde die Verteilung standardisierter Analysen an alle Lieferanten, die Sie benötigten, erheblich vereinfacht.

    Obwohl das Beispiel gezeigt hat, wie ein einzelner allgemeiner Bericht auf die Lieferanten verteilt werden kann, können Power BI viel weiter gehen. Um sicherzustellen, dass jedem Partner nur relevante Daten angezeigt werden, können Sicherheit auf Zeilenebene problemlos dem Bericht und dem Datenmodell hinzugefügt werden. Im Abschnitt Datensicherheit für externe Partner in diesem Dokument wird dieser Prozess ausführlich beschrieben.

    Häufig müssen einzelne Berichte und Dashboards in ein vorhandenes Portal eingebettet werden. Dies kann auch durch die Wiederverwendung zahlreicher der im Beispiel gezeigten Techniken erreicht werden. In diesen Situationen kann es jedoch einfacher sein, Berichte oder Dashboards direkt aus einem Arbeitsbereich einzubetten. Der Prozess zum einladen und Zuweisen der Sicherheits Berechtigung für die erfordern, dass Benutzer unverändert bleiben.

## <a name="under-the-hood-how-is-lucy-from-supplier1-able-to-access-power-bi-content-from-contosos-tenant"></a>Im Hintergrund: Wie kann Lucy von der Supplier1 auf Power BI Inhalt aus dem Mandanten von "Configuration Manager" zugreifen?

Nachdem wir nun erfahren haben, wie wir Power BI Inhalte nahtlos an Gastbenutzer in Partnerorganisationen verteilen können, sehen wir uns an, wie dies im Hintergrund funktioniert.

Wenn "Configuration Manager" in das zugehörige [lucy@supplier1.com](mailto:lucy@supplier1.com) Verzeichnis geladen wurde, erstellt Azure AD eine Verknüpfung zwischen [Lucy@supplier1.com](mailto:Lucy@supplier1.com) und dem Azure AD Mandanten von "". Über diesen Link können Sie Azure AD wissen, dass auf Inhalte im Mandanten von "Configuration Manager" Lucy@supplier1.com zugreifen kann.

Wenn Lucy versucht, auf die Power BI-APP von Azure AD von Configuration Manager zuzugreifen, überprüft, ob Lucy auf den Mandanten von "Configuration Manager" zugreifen kann, und stellt Power BI ein Token bereit, das angibt, dass Lucy für den Zugriff auf Inhalte im Mandanten von "Configuration Manager" authentifiziert ist. Power BI verwendet dieses Token, um zu autorisieren und sicherzustellen, dass Lucy Zugriff auf die Power BI-APP von.

![Überprüfung und Autorisierung](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_22.png)

Die Integration von Power BI in Azure AD B2B funktioniert mit allen geschäftlichen e-Mail-Adressen. Wenn der Benutzer nicht über eine Azure AD Identität verfügt, wird er möglicherweise aufgefordert, eine zu erstellen. Die folgende Abbildung zeigt den detaillierten Ablauf:

![Integrations Flussdiagramm](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_23.png)


Es ist wichtig zu erkennen, dass das Azure AD Konto im Azure Ad der externen Partei verwendet oder erstellt wird. Dadurch kann Lucy seinen eigenen Benutzernamen und Ihr Kennwort verwenden, und ihre Anmelde Informationen werden automatisch in anderen Mandanten arbeiten, wenn Lucy das Unternehmen verlässt, wenn die Organisation auch Azure AD verwendet.

## <a name="licensing"></a>Lizenzierung

Mit einem von drei Ansätzen können Gastbenutzer von seinen Lieferanten und Partnerorganisationen auf Power BI Inhalte zugreifen.

> [!NOTE]
> _Der Free-Tarif Azure AD B2B's reicht für die Verwendung von Power BI mit Azure AD B2B aus. Für einige erweiterte Azure AD B2B-Features wie dynamische Gruppen ist eine zusätzliche Lizenzierung erforderlich. Weitere Informationen finden Sie in der Azure AD B2B-Dokumentation:_[_https://docs.microsoft.com/azure/active-directory/b2b/licensing-guidance_](https://docs.microsoft.com/azure/active-directory/b2b/licensing-guidance)

### <a name="approach-1-contoso-uses-power-bi-premium"></a>Ansatz 1: von "Configuration Manager" verwendet Power BI Premium

Bei diesem Ansatz erwirbt "Configuration Manager" Power BI Premium Kapazität und weist dieser Kapazität den Inhalt des BI-Portals zu. Dadurch können Gastbenutzer von Partnerorganisationen ohne Power BI Lizenz auf die Power BI-APP von zugreifen.

Externe Benutzer unterliegen auch der Nutzung von Benutzeroberflächen, die für "kostenlose" Benutzer in Power BI angeboten werden, wenn Inhalte innerhalb Power BI Premium genutzt werden.

Außerdem kann es von den anderen Power BI Premium-Funktionen für die apps profitieren, wie z. b. eine Erhöhung der Aktualisierungs Raten, dedizierte Kapazität und große Modellgrößen.

![Weitere Funktionen](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_24.png)


### <a name="approach-2-contoso-assigns-power-bi-pro-licenses-to-guest-users"></a>Ansatz 2: von "Configuration Manager" werden Gastbenutzern Power BI pro Lizenzen zugewiesen.

Bei dieser Vorgehensweise weist "Ada" von "Configuration Manager" pro-Lizenzen von Partnerorganisationen zu – Dies kann über das Microsoft 365 Admin Center von "" erfolgen. Dadurch können Gastbenutzer von Partnerorganisationen auf die Power BI-APP von "App" zugreifen, ohne selbst eine Lizenz erwerben zu müssen. Dies kann für die Freigabe mit externen Benutzern geeignet sein, deren Organisation Power BI noch nicht übernommen hat.

> [!NOTE]
> Die pro-Lizenz von "Configuration Manager" gilt nur für Gastbenutzer, wenn Sie auf Inhalte im Mandanten von "Configuration Manager" zugreifen. Pro-Lizenzen ermöglichen den Zugriff auf Inhalte, die sich nicht in einer Power BI Premium Kapazität befinden. Externe Benutzer mit einer pro-Lizenz werden jedoch standardmäßig auf eine reine Nutzung beschränkt. Dies kann mithilfe des Ansatzes geändert werden, der im Abschnitt _Aktivieren externer Benutzer zum Bearbeiten und Verwalten von Inhalten in Power BI weiter_ unten in diesem Dokument beschrieben wird.

![Lizenzinformationen](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_25.png)


### <a name="approach-3-guest-users-bring-their-own-power-bi-pro-license"></a>Ansatz 3: Gastbenutzer haben ihre eigene Power BI pro Lizenz

Bei dieser Vorgehensweise weist Lieferant 1 Lucy eine Power BI pro-Lizenz zu. Sie können dann mit dieser Lizenz auf die Power BI-APP von "Configuration Manager" zugreifen. Da Lucy beim Zugriff auf eine externe Power BI Umgebung seine pro-Lizenz aus seiner eigenen Organisation verwenden kann, wird diese Vorgehensweise auch als _Bring-your-own-License_ (byol) bezeichnet. Wenn beide Organisationen Power BI verwenden, bietet dies eine vorteilhafte Lizenzierung für die allgemeine Analyselösung und minimiert den Aufwand für das Zuweisen von Lizenzen für externe Benutzer.

> [!NOTE]
> Die pro-Lizenz, die Lucy von Supplier 1 erhält, gilt für jeden Power BI Mandanten, bei dem Lucy ein Gastbenutzer ist. Pro-Lizenzen ermöglichen den Zugriff auf Inhalte, die sich nicht in einer Power BI Premium Kapazität befinden. Externe Benutzer mit einer pro-Lizenz werden jedoch standardmäßig auf eine reine Nutzung beschränkt. Dies kann geändert werden, indem Sie den im Abschnitt _Aktivieren externer Benutzer zum Bearbeiten und Verwalten von Inhalten in Power BI weiter_ unten in diesem Dokument beschriebenen Ansatz verwenden.

![Pro-Lizenzanforderungen](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_26.png)

## <a name="data-security-for-external-partners"></a>Datensicherheit für externe Partner

Häufig muss bei der Arbeit mit mehreren externen Lieferanten sichergestellt werden, dass jeder Lieferant nur Daten über seine eigenen Produkte sieht. Durch die benutzerbasierte Sicherheit und dynamische Sicherheit auf Zeilenebene wird dies mit Power BI problemlos erreicht.

### <a name="user-based-security"></a>Benutzerbasierte Sicherheit

Eines der leistungsstärksten Features von Power BI ist Sicherheit auf Zeilenebene. Diese Funktion ermöglicht es, dass von "Configuration Manager" ein einzelner Bericht und ein DataSet erstellt werden, aber dennoch für jeden Benutzer unterschiedliche Sicherheitsregeln angewendet werden. Eine ausführliche Erläuterung finden Sie unter Sicherheit auf [Zeilenebene (Row-Level Security, RLS)](https://powerbi.microsoft.com/documentation/powerbi-admin-rls/).

Die Integration von Power BI in Azure AD B2B ermöglicht es, dass der Gastbenutzer Sicherheit auf Zeilenebene Regeln zuweist, sobald diese zum Mandanten von "Configuration Manager" eingeladen werden. Wie wir bereits gesehen haben, kann "Azure" Gastbenutzer über geplante oder Ad-hoc-Einladungen hinzufügen. Wenn die Sicherheit auf Zeilenebene erzwungen werden soll, wird dringend empfohlen, geplante Einladungen zu verwenden, um die Gastbenutzer vorab hinzuzufügen und diese den Sicherheitsrollen vor der Freigabe der Inhalte zuzuweisen. Wenn von "Azure" stattdessen Ad-hoc-Einladungen verwendet werden, kann es eine kurze Zeitspanne geben, in der die Gastbenutzer keine Daten sehen können.

> [!NOTE]
> Diese Verzögerung beim Zugriff auf Daten, die von RLS bei der Verwendung von Ad-hoc-Einladungen geschützt werden, kann zu Supportanfragen für Ihr IT-Team führen, da Benutzern entweder leere oder unterbrochene Berichte/Dashboards angezeigt werden, wenn ein Freigabe Link in der empfangenen e-Mail geöffnet wird. Daher wird dringend empfohlen, geplante Einladungen in diesem Szenario zu verwenden. * *

Sehen wir uns dies mit einem Beispiel an.

Wie bereits erwähnt, gibt es von "Configuration Manager" weltweit Lieferanten auf der ganzen Welt, und Sie möchten sicherstellen, dass die Benutzer Ihrer lieferantenorganisationen Einblicke aus den Daten aus Ihrem Gebiet erhalten.  Benutzer von "Configuration Manager" können allerdings auf alle Daten zugreifen. Anstatt mehrere verschiedene Berichte zu erstellen, erstellt "Configuration Manager" einen einzelnen Bericht und filtert die Daten basierend auf dem Benutzer.

![Freigegebener Inhalt](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_27.png)

Um sicherzustellen, dass von Configuration Manager Daten basierend auf der Verbindung gefiltert werden können, werden in Power BI Desktop zwei Rollen erstellt. Eine zum Filtern aller Daten aus der SalesTerritory "Europa" und eine andere für "Nordamerika".

![Verwalten von Rollen](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_28.png)

Wenn Rollen im Bericht definiert sind, muss ein Benutzer einer bestimmten Rolle zugewiesen werden, um Zugriff auf alle Daten zu erhalten. Die Zuweisung von Rollen erfolgt innerhalb des Power BI-Dienst ( **DataSets > Sicherheit** ).

![Festlegen der Sicherheit](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_29.png)

Dadurch wird eine Seite geöffnet, auf der das BI-Team von Team die beiden erstellten Rollen anzeigen kann.  Jetzt kann das BI-Team von Team der Rollen Benutzer zuweisen.

![Sicherheit auf Zeilenebene](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_30.png)

In dem Beispiel fügt "Configuration Manager" einen Benutzer in einer Partnerorganisation mit der e-Mail-Adresse " [adam@themeasuredproduct.com](mailto:adam@themeasuredproduct.com) " der Rolle "Europa" hinzu:

![Sicherheitseinstellungen auf Zeilenebene](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_31.png)

Wenn dies durch Azure AD gelöst wird, kann von "Configuration Manager" angezeigt werden, dass der Name im Fenster angezeigt wird, das hinzugefügt werden kann:

![Rollen anzeigen](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_32.png)

Wenn dieser Benutzer nun die APP öffnet, die für ihn freigegeben wurde, wird nur ein Bericht mit Daten aus Europa angezeigt:

![Inhalt der Sicht](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_33.png)

### <a name="dynamic-row-level-security"></a>Dynamische Sicherheit auf Zeilenebene

Ein weiteres interessantes Thema besteht darin, zu erfahren, wie die dynamische Sicherheit auf Zeilenebene (RLS) mit Azure AD B2B funktioniert.

Kurz gesagt funktioniert die dynamische Sicherheit auf Zeilenebene, indem Daten im Modell basierend auf dem Benutzernamen der Person gefiltert werden, die eine Verbindung mit Power BI herstellt. Anstatt mehrere Rollen für Gruppen von Benutzern hinzuzufügen, definieren Sie die Benutzer im Modell. Das Muster wird hier nicht ausführlich beschrieben. Kasper de Jong bietet einen detaillierten Schreibvorgang für alle Varianten der Sicherheit auf Zeilenebene in [Power BI Desktop Dynamic Security Cheat Sheet](https://www.kasperonbi.com/power-bi-desktop-dynamic-security-cheat-sheet/)und in [diesem Whitepaper](https://msdn.microsoft.com/library/jj127437.aspx) .

Sehen wir uns ein kleines Beispiel an: "". "" ist ein einfacher Bericht zu "Sales by Groups":

![Beispiel Inhalt](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_34.png)

Nun muss dieser Bericht für zwei Gastbenutzer und einen internen Benutzer freigegeben werden. der interne Benutzer kann alles sehen, aber die Gastbenutzer können nur die Gruppen sehen, auf die Sie Zugriff haben. Dies bedeutet, dass die Daten nur für die Gastbenutzer gefiltert werden müssen. Um die Daten entsprechend zu filtern, verwendet "Configuration Manager" das dynamische RLS-Muster, wie im Whitepaper und im Blogbeitrag beschrieben. Dies bedeutet, dass die Benutzernamen von "Configuration Manager" den Daten selbst hinzugefügt werden:

![Anzeigen von RLS-Benutzern für die Daten selbst](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_35.png)

Dann erstellt "Configuration Manager" das richtige Datenmodell, das die Daten entsprechend den richtigen Beziehungen filtert:

![Es werden entsprechende Daten angezeigt.](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_36.png)

Zum automatischen Filtern der Daten basierend auf der Anmeldung muss von "Configuration Manager" eine Rolle erstellt werden, die den Benutzer übergibt, der eine Verbindung herstellt. In diesem Fall werden von "Configuration Manager" zwei Rollen erstellt – bei der ersten handelt es sich um die "SecurityRole", die die Tabelle "Users" mit dem aktuellen Benutzernamen des Power BI angemeldeten Benutzers filtert (dies funktioniert auch für Azure AD B2B-Gastbenutzer).

![Verwalten von Rollen](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_37.png)

Außerdem erstellt der Dienst "allrole" für die internen Benutzer, die alles sehen können – diese Rolle verfügt nicht über ein Sicherheits Prädikat.

Nachdem die Power BI Desktop-Datei in den Dienst hochgeladen wurde, kann der Benutzer "SecurityRole" und den internen Benutzern von "allrole" Gastbenutzer zuweisen.

Wenn nun der Gastbenutzer den Bericht öffnet, sehen Sie nur Umsätze aus Gruppe A:

![Nur aus Gruppe A](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_38.png)

In der Matrix auf der rechten Seite sehen Sie das Ergebnis der username ()-und der userPrincipalName ()-Funktion, die beide die e-Mail-Adresse des Gast Benutzers zurückgeben.

Nun erhält der interne Benutzer alle Daten:

![Alle angezeigten Daten](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_39.png)

Wie Sie sehen, können dynamische RLS sowohl mit internen als auch mit Gastbenutzern verwendet werden.

> [!NOTE]
> Dieses Szenario funktioniert auch, wenn Sie ein Modell in Azure Analysis Services verwenden. In der Regel ist Ihr Azure Analysis Service mit dem gleichen Azure AD verbunden wie Ihre Power BI. in diesem Fall kennt Azure Analysis Services auch die durch Azure AD B2B geladenen Gastbenutzer.

## <a name="connecting-to-on-premises-data-sources"></a>Herstellen einer Verbindung mit lokalen Datenquellen

Power BI bietet die Möglichkeit, dass mit dem lokalen [Daten Gateway](https://powerbi.microsoft.com/documentation/powerbi-gateway-onprem/)lokale Datenquellen wie [SQL Server Analysis Services](https://powerbi.microsoft.com/documentation/powerbi-gateway-enterprise-manage-ssas/) oder [SQL Server](https://powerbi.microsoft.com/documentation/powerbi-gateway-kerberos-for-sso-pbi-to-on-premises-data/) direkt genutzt werden können. Es ist sogar möglich, sich bei diesen Datenquellen mit denselben Anmelde Informationen anzumelden, die mit Power BI verwendet werden.

> [!NOTE]
> Wenn Sie ein Gateway installieren, um eine Verbindung mit Ihrem Power BI-Mandanten herzustellen, müssen Sie einen Benutzer verwenden, der in Ihrem Mandanten erstellt wurde. Externe Benutzer können kein Gateway installieren und eine Verbindung mit Ihrem Mandanten herstellen.

Für externe Benutzer ist dies möglicherweise komplizierter, da die externen Benutzer in der Regel nicht dem lokalen AD bekannt sind. Power BI bietet hierfür eine Problem Umgehung, indem es den Administratoren von Configuration Manager gestattet wird, die externen Benutzernamen den internen Benutzernamen zuzuordnen, wie unter [Verwalten Ihrer Datenquelle-Analysis Services](https://powerbi.microsoft.com/documentation/powerbi-gateway-enterprise-manage-ssas/)beschrieben. Beispielsweise [lucy@supplier1.com](mailto:lucy@supplier1.com) kann [Lucy \_ supplier1 \_ com # EXT@contoso.com ](mailto:lucy_supplier1_com)zugeordnet werden.

![Zuordnen von Benutzernamen](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_40.png)

Diese Methode ist in Ordnung, wenn "Configuration Manager" nur eine Handvoll Benutzer hat oder wenn "Configuration Manager" alle externen Benutzer einem einzigen internen Konto zuordnen kann. Für komplexere Szenarios, in denen jeder Benutzer seine eigenen Anmelde Informationen benötigt, gibt es einen erweiterten Ansatz, bei dem Benutzer [definierte AD-Attribute](https://technet.microsoft.com/library/cc961737.aspx) verwendet werden, um die Zuordnung durchzuführen, wie unter [Verwalten der Datenquelle Analysis Services](https://powerbi.microsoft.com/documentation/powerbi-gateway-enterprise-manage-ssas/)beschrieben. Dadurch kann der Administrator von "Configuration Manager" eine Zuordnung für jeden Benutzer in ihrer Azure AD definieren (auch externe B2B-Benutzer).  Diese Attribute können über das AD-Objektmodell mithilfe von Skripts oder Code festgelegt werden, damit die Zuordnung bei Einladungen oder bei einem geplanten Rhythmus vollständig automatisiert werden kann.

## <a name="enabling-external-users-to-edit-and-manage-content-within-power-bi"></a>Aktivieren externer Benutzer zum Bearbeiten und Verwalten von Inhalten in Power BI

Mit Configuration Manager können externe Benutzerinhalte innerhalb der Organisation wie zuvor im Abschnitt Organisations übergreifende Bearbeitung und Verwaltung von Power BI Inhalt beschrieben mitwirken.

> [!NOTE]
> Um Inhalte innerhalb der Power BI Ihrer Organisation zu bearbeiten und zu verwalten, muss der Benutzer über eine Power BI pro Lizenz in einem anderen Arbeitsbereich als meinem Arbeitsbereich verfügen. Benutzer können pro-Lizenzen abrufen, wie im Abschnitt zur _Lizenzierung_ dieses Dokuments beschrieben.

Das Power BI Admin-Portal enthält die Einstellung **externen Gastbenutzern das Bearbeiten und Verwalten von Inhalten in den** Einstellungen der Organisation in den Mandanten Einstellungen. Standardmäßig ist die Einstellung auf deaktiviert festgelegt, was bedeutet, dass externe Benutzer standardmäßig eine eingeschränkte schreibgeschützte Benutzerumgebung erhalten. Die Einstellung gilt für Benutzer, deren usertype in Azure AD auf Guest festgelegt ist. In der folgenden Tabelle wird das Verhalten der Benutzerfreundlichkeit in Abhängigkeit von Ihrem usertype und der Konfiguration der Einstellungen beschrieben.

| **Benutzertyp in Azure AD** | **Bearbeiten und Verwalten von Inhaltseinstellungen durch externe Gastbenutzer zulassen** | **Behavior class (Behavior-Klasse)** |
| --- | --- | --- |
| Gast | Für den Benutzer deaktiviert (Standard) | Pro Element Verbrauchs Ansicht. Ermöglicht den schreibgeschützten Zugriff auf Berichte, Dashboards und apps, wenn Sie über eine URL angezeigt werden, die an den Gastbenutzer gesendet wird. Power BI Mobile-Apps bieten dem Gastbenutzer eine schreibgeschützte Ansicht. |
| Gast | Für den Benutzer aktiviert | Der externe Benutzer erhält Zugriff auf die vollständige Power BI, obwohl einige Features Ihnen nicht zur Verfügung stehen. Der externe Benutzer muss sich bei Power BI mithilfe der URL des Power BI Dienstanbieter mit den darin enthaltenen Mandanten Informationen anmelden. Der Benutzer erhält das Zuhause, einen eigenen Arbeitsbereich und auf der Grundlage der Berechtigungen zum Durchsuchen, anzeigen und Erstellen von Inhalt. </br></br> Power BI Mobile-Apps bieten dem Gastbenutzer eine schreibgeschützte Ansicht. |

> [!NOTE]
> Externe Benutzer in Azure AD können auch auf usertype-Member festgelegt werden. Dies wird derzeit in Power BI nicht unterstützt.

Im Power BI Admin-Portal ist die Einstellung in der folgenden Abbildung dargestellt.

![Administratoreinstellungen](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_41.png)

Gastbenutzer erhalten die schreibgeschützte Standardbenutzer Einstellung und können Inhalte bearbeiten und verwalten. Der Standardwert ist deaktiviert. Dies bedeutet, dass alle Gastbenutzer die schreibgeschützte Benutzerfunktion haben. Der Power BI Administrator kann entweder die Einstellung für alle Gastbenutzer in der Organisation oder für bestimmte Sicherheitsgruppen aktivieren, die in Azure AD definiert sind. In der folgenden Abbildung hat der Administrator von "Configuration Manager" Power BI eine Sicherheitsgruppe in Azure AD erstellt, um zu verwalten, welche externen Benutzerinhalte im Mandanten von "Configuration Manager" Bearbeiten und verwalten können.

Um diese Benutzer bei der Anmeldung bei Power BI zu unterstützen, geben Sie Ihnen die Mandanten-URL. Gehen Sie wie folgt vor, um die Mandanten-URL zu finden:

1. Wählen Sie im Power BI-Dienst im oberen Menü Hilfe ( **?** ), **über Power BI**.
2. Suchen Sie nach dem Wert neben Mandanten- **URL**. Dies ist die Mandanten-URL, die Sie für Ihre Gastbenutzer freigeben können.

    ![Mandanten-URL](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_42.png)

Bei Verwendung der Option "externe Gastbenutzer dürfen Inhalte in der Organisation bearbeiten und verwalten" erhalten die angegebenen Gastbenutzer Zugriff auf die Power BI Ihrer Organisation, und es werden alle Inhalte angezeigt, für die Sie über die Berechtigung verfügen. Sie können auf "Home" zugreifen, Inhalte durchsuchen und an Arbeitsbereichen mitwirken, Apps installieren, in denen Sie sich in der Zugriffsliste befinden, und einen eigenen Arbeitsbereich haben. Sie können einen Administrator für Arbeitsbereiche erstellen, der die neue Arbeitsbereichsoberfläche verwendet, oder sie können selbst ein Administrator für diese Bereiche sein.

> [!NOTE]
> Wenn Sie diese Option verwenden, sollten Sie sicherstellen, dass der governanceabschnitt dieses Dokuments überprüft wird, da die Standard Azure AD Einstellungen verhindern, dass Gastbenutzer bestimmte Features wie z. b. Personen adressierer verwenden, was zu einer geringeren Benutzerumgebung führen kann

Für Gastbenutzer, die über die Einstellung erlauben Sie externen Gastbenutzern das Bearbeiten und Verwalten von Inhalten in der Mandanten Einstellung der Organisation ermöglicht, stehen Ihnen einige Umgebungen nicht zur Verfügung. Um Berichte zu aktualisieren oder zu veröffentlichen, müssen Gastbenutzer die Power BI-Dienst-Webbenutzer Oberfläche verwenden, einschließlich Daten zum Hochladen Power BI Desktop Dateien. Die folgenden Funktionen werden nicht unterstützt:

- Direktes Veröffentlichen aus Power BI Desktop im Power BI-Dienst
- Gastbenutzer können Power BI Desktop nicht dazu verwenden, eine Verbindung mit Dienstdatasets im Power BI-Dienst herzustellen.
- Klassische Arbeitsbereiche, die an Office 365-Gruppen gebunden sind: Gastbenutzer können diese Arbeitsbereiche nicht erstellen oder Administratoren erstellen. Sie können Mitglieder sein.
- Das Senden von Ad-hoc-Einladungen wird für Arbeitsbereichszugriffslisten nicht unterstützt.
- Power BI Publisher für Excel wird für Gastbenutzer nicht unterstützt.
- Gastbenutzer können nicht Power BI Gateway installieren und eine Verbindung von Power BI Gateway mit Ihrer Organisation herstellen.
- Gastbenutzer können keine Apps installieren und diese für die gesamte Organisation freigeben.
- Gastbenutzer können keine Organisationsinhaltspakete verwenden, erstellen, aktualisieren oder installieren.
- Gastbenutzer können nicht „In Excel analysieren“ verwenden.
- Gastbenutzer können nicht @mentioned kommentiert werden (diese Funktion wird in einer zukünftigen Version hinzugefügt)
- Gastbenutzer können keine Abonnements verwenden (diese Funktion wird in einer zukünftigen Version hinzugefügt)
- Gastbenutzer, die diese Funktion verwenden, sollten ein Geschäfts-, Schul- oder Unikonto besitzen. Gastbenutzer, die persönliche Konten verwenden, haben aufgrund von Anmelde Beschränkungen weitere Einschränkungen.



## <a name="governance"></a>Governance

### <a name="additional-azure-ad-settings-that-affect-experiences-in-power-bi-related-to-azure-ad-b2b"></a>Zusätzliche Azure AD Einstellungen, die sich auf die Benutzererfahrung Power BI im Zusammenhang mit Azure AD B2B auswirken

Wenn Sie Azure AD B2B-Freigabe verwenden, steuert der Azure Active Directory Administrator Aspekte der Benutzeroberflächen des externen Benutzers. Diese werden auf der Seite mit den Einstellungen für die externe Zusammenarbeit in den Azure Active Directory Einstellungen für Ihren Mandanten gesteuert.

Details zu den Einstellungen finden Sie hier:

[https://docs.microsoft.com/azure/active-directory/b2b/delegate-invitations](https://docs.microsoft.com/azure/active-directory/b2b/delegate-invitations)

> [!NOTE]
> Standardmäßig ist die Option Berechtigungen für Gastbenutzer eingeschränkt auf Ja festgelegt, sodass Gastbenutzer innerhalb Power BI nur begrenzte Möglichkeiten haben, die Freigabe zu übernehmen, bei der die Benutzer Auswahl nicht für diese Benutzer funktioniert. Es ist wichtig, dass Sie mit Ihrem Azure AD-Administrator zusammenarbeiten, um ihn auf Nein festzulegen, wie unten gezeigt, um eine gute Leistung zu gewährleisten. * *

![Einstellungen für externe Zusammenarbeit](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_43.png)


### <a name="control-guest-invites"></a>Gast Einladungen Steuern

Power BI Administratoren können die externe Freigabe nur für Power BI steuern, indem Sie das Power BI Admin-Portal besuchen. Mandanten Administratoren können jedoch auch die externe Freigabe mit verschiedenen Azure AD Richtlinien steuern.  Mit diesen Richtlinien können Mandanten Administratoren

- Einladungen von Endbenutzern deaktivieren
- Nur Administratoren und Benutzer in der Rolle „Gasteinladender“ dürfen einladen.
- Administratoren, Benutzer in der Rolle „Gasteinladender“ und Mitglieder dürfen einladen.
- Alle Benutzer, einschließlich Gästen, dürfen einladen.

Weitere Informationen zu diesen Richtlinien finden Sie unter [Delegieren von Einladungen für Azure Active Directory B2B-Zusammenarbeit](https://docs.microsoft.com/azure/active-directory/active-directory-b2b-delegate-invitations).

Alle Power BI Aktionen durch externe Benutzer werden auch [in unserem Überwachungs Portal](https://powerbi.microsoft.com/documentation/powerbi-admin-auditing/)überwacht.

### <a name="conditional-access-policies-for-guest-users"></a>Bedingte Zugriffsrichtlinien für Gastbenutzer

Die Richtlinien für den bedingten Zugriff können von Configuration Manager für Gastbenutzer erzwungen werden Ausführliche Anweisungen finden Sie unter [bedingter Zugriff für Benutzer der B2B-Zusammenarbeit](https://docs.microsoft.com/azure/active-directory/active-directory-b2b-mfa-instructions).

## <a name="common-alternative-approaches"></a>Allgemeine alternative Ansätze

Obwohl Azure AD B2B das Freigeben von Daten und Berichten in Unternehmen vereinfacht, gibt es mehrere andere Ansätze, die häufig verwendet werden und in bestimmten Fällen überlegen sein können.

### <a name="alternative-option-1-create-duplicate-identities-for-partner-users"></a>Alternative Option 1: Erstellen von doppelten Identitäten für Partner Benutzer

Bei dieser Option musste von "Configuration Manager" für jeden Partner Benutzer im Mandanten von "Configuration Manager" manuell doppelte Identitäten erstellt werden, wie in der folgenden Abbildung dargestellt. In Power BI kann von "Configuration Manager" in den zugewiesenen Identitäten die entsprechenden Berichte, Dashboards oder apps gemeinsam genutzt werden.

![Festlegen geeigneter Zuordnungen und Namen](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_44.png)

Gründe für die Auswahl dieser Alternative:

- Da die Identität des Benutzers von Ihrer Organisation gesteuert wird, sind alle zugehörigen Dienste wie e-Mail, SharePoint usw. auch innerhalb der Kontrolle Ihrer Organisation. Ihre IT-Administratoren können Kenn Wörter zurücksetzen, den Zugriff auf Konten deaktivieren oder Aktivitäten in diesen Diensten überwachen.
- Benutzer, die persönliche Konten für Ihr Unternehmen verwenden, sind häufig auf bestimmte Dienste beschränkt, sodass Sie möglicherweise ein Organisations Konto benötigen.
- Einige Dienste können nur über die Benutzer Ihrer Organisation verwendet werden. Beispielsweise ist die Verwendung von InTune zum Verwalten von Inhalten auf persönlichen/mobilen Geräten externer Benutzer mithilfe von Azure B2B möglicherweise nicht möglich.

Gründe für die Auswahl dieser Alternativen:

- Benutzer von Partnerorganisationen müssen zwei Sätze von Anmelde Informationen speichern – eines für den Zugriff auf Inhalte aus ihrer eigenen Organisation und das andere für den Zugriff auf Inhalte von "Configuration Manager". Dies ist ein Problem für diese Gastbenutzer, und viele Gastbenutzer sind durch diese Benutzer Verwirrung verwirrt.
- Von "Configuration Manager" müssen diese Benutzerlizenzen pro Benutzer erwerben und zuweisen. Wenn ein Benutzer e-Mails erhalten oder Office-Anwendungen verwenden muss, benötigt er die entsprechenden Lizenzen, einschließlich Power BI pro, Inhalte in Power BI zu bearbeiten und freizugeben.
- Möglicherweise möchten Sie von "Configuration Manager" strengere Autorisierungs-und governancerichtlinien für externe Benutzer im Vergleich zu internen Benutzern erzwingen. Um dies zu erreichen, muss von "Configuration Manager" eine interne Nomenklatur für externe Benutzer erstellt werden, und alle Benutzer von "Configuration Manager" müssen über diese Nomenklatur informiert werden.
- Wenn der Benutzer seine Organisation verlässt, haben Sie weiterhin Zugriff auf die Ressourcen von "fitoso", bis der Administrator von "Configuration Manager" Ihr Konto manuell löscht.
- Die Administratoren von "Configuration Manager" müssen die Identität für den Gast verwalten, einschließlich Erstellung, Zurücksetzen von Kenn Wörtern usw.

### <a name="alternative-option-2-create-a-custom-power-bi-embedded-application-using-custom-authentication"></a>Alternative Option 2: Erstellen einer benutzerdefinierten Power BI Embedded Anwendung mithilfe der benutzerdefinierten Authentifizierung

Eine weitere Option für "Configuration Manager" besteht darin, eine eigene benutzerdefinierte eingebettete Power BI Anwendung mit benutzerdefinierter Authentifizierung (["App besitzt Daten"](https://docs.microsoft.com/power-bi/developer/embedded/embed-sample-for-customers)) zu erstellen. Obwohl viele Organisationen nicht über die Zeit oder Ressourcen zum Erstellen einer benutzerdefinierten Anwendung verfügen, um Power BI Inhalte an externe Partner zu verteilen, ist dies für einige Organisationen der beste Ansatz und verdient ernsthafte Überlegungen.

Häufig verfügen Organisationen über vorhandene Partnerportale, die den Zugriff auf alle Organisations Ressourcen für Partner zentralisieren, die Isolation interner Organisations Ressourcen bereitstellen und den Partnern optimierte Möglichkeiten zur Unterstützung vieler Partner und der einzelnen Benutzer bieten.

![Viele Partnerportale](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_45.png)

Im obigen Beispiel melden sich Benutzer von jedem Lieferanten beim Partner Portal von Azure AD an, das Aad als Identitäts Anbieter verwendet. Sie können Aad B2B, Azure B2C, Native Identitäten oder einen Verbund mit einer beliebigen Anzahl anderer Identitäts Anbieter verwenden. Der Benutzer meldet sich mit der Azure-Web-App oder einer ähnlichen Infrastruktur an und greift auf einen Partnerportal-Build zu.

In der Web-App werden Power BI Berichte aus einer Power BI Embedded Bereitstellung eingebettet. Die Web-App vereinfacht den Zugriff auf die Berichte und alle zugehörigen Dienste in einer zusammenhängenden Darstellung, die es den Lieferanten erleichtern soll, mit der Verwendung von "Configuration Manager" zu interagieren. Diese Portal Umgebung wird von der internen Azure AD-und der internen Power BI Umgebung von Azure Active Directory isoliert, um sicherzustellen, dass die Lieferanten nicht auf diese Ressourcen zugreifen können. Normalerweise werden Daten in einem separaten Partner Data Warehouse gespeichert, um auch die Isolation von Daten sicherzustellen. Diese Isolation hat Vorteile, da Sie die Anzahl externer Benutzer mit direktem Zugriff auf die Daten Ihrer Organisation beschränkt, die Daten einschränkt, die dem externen Benutzer möglicherweise zur Verfügung stehen, und die versehentliche Freigabe für externe Benutzer beschränken.

Mithilfe von Power BI Embedded kann das Portal eine vorteilhafte Lizenzierung nutzen, indem Sie das App-Token oder den Master Benutzer zuzüglich der im Azure-Modell erworbenen Premium-Kapazität verwendet. Dies vereinfacht die Zuweisung von Lizenzen zu Endbenutzern und kann basierend auf der erwarteten Nutzung zentral hoch-oder herunterskaliert werden. Das Portal kann eine qualitativ hochwertige und konsistente Gesamtleistung bieten, da Partner auf ein einziges Portal zugreifen, das mit allen Anforderungen eines Partners entworfen wurde. Da Power BI Embedded basierte Lösungen in der Regel als mehrinstanzfähige Lösungen entworfen werden, ist es einfacher, die Isolation zwischen Partnerorganisationen sicherzustellen.

Gründe für die Auswahl dieser Alternative:

- Einfacher zu verwalten, wenn die Anzahl von Partnerorganisationen wächst. Da Partner zu einem separaten Verzeichnis hinzugefügt werden, das vom internen Aad-Verzeichnis von "Azure" isoliert ist, werden die IT-Governance-Aufgaben vereinfacht und die versehentliche Freigabe interner Daten für externe Benutzer verhindert.
- Typische Partnerportale sind eine hoch Branding-Umgebung mit konsistenten Erfahrungen zwischen Partnern, die optimiert wird, um die Anforderungen typischer Partner zu erfüllen. Mit der Integration aller erforderlichen Dienste in ein einziges Portal bietet die Lösung von "Configuration Manager" daher eine bessere Gesamtleistung für Partner.
- Die Lizenzierungs Kosten für erweiterte Szenarien wie das Bearbeiten von Inhalten innerhalb der Power BI Embedded werden durch den von Azure erworbenen Power BI Premium abgedeckt und erfordern keine Zuweisung von Power BI pro Lizenzen zu diesen Benutzern.
- Bietet eine bessere Isolation zwischen Partnern, wenn Sie als mehrinstanzfähige Lösung entworfen wurde.
- Das Partner Portal enthält häufig andere Tools für Partner, die über Power BI Berichte, Dashboards und apps hinausgehen.

Gründe für die Auswahl dieser Alternativen:

- Ein erheblicher Aufwand ist erforderlich, um ein solches Portal zu erstellen, zu betreiben und zu verwalten, sodass es eine beträchtliche Investition in die Ressourcen und die Zeit hat.
- Die Zeit bis zur Lösung ist deutlich länger als die Verwendung der B2B-Freigabe, da eine sorgfältige Planung und Ausführung über mehrere Arbeitsströme erforderlich ist.
- Bei einer geringeren Anzahl von Partnern ist der erforderliche Aufwand für diese Alternative wahrscheinlich zu hoch, um zu rechtfertigen.
- Die Zusammenarbeit mit Ad-hoc-Freigabe ist das primäre Szenario Ihrer Organisation.
- Die Berichte und Dashboards unterscheiden sich für jeden Partner. Diese Alternative führt zu einem Verwaltungsaufwand, der über die direkte Freigabe mit Partnern hinausgeht.



## <a name="faq"></a>Häufig gestellte Fragen

**Kann von "Configuration Manager" eine Einladung gesendet werden, die automatisch eingelöst wird, sodass der Benutzer nur "bereit für den Start" ist? Oder muss der Benutzer immer zur einlösungs-URL durch Klicken?**

Der Endbenutzer muss immer durch die Zustimmung klicken, bevor er auf den Inhalt zugreifen kann.

Wenn Sie viele Gastbenutzer einladen werden, empfiehlt es sich, dies von ihrem Kern Azure AD Administratoren zu delegieren, indem Sie [der Rolle "Gast einladender" in der Ressourcen Organisation einen Benutzer hinzufügen](https://docs.microsoft.com/azure/active-directory/active-directory-b2b-add-guest-to-role). Dieser Benutzer kann über die Anmeldeoberfläche, PowerShell-Skripts oder APIs andere Benutzer in der Partnerorganisation einladen. Dadurch wird der administrative Aufwand für Ihre Azure AD Administratoren reduziert, Einladungen für Benutzer bei der Partnerorganisation einzuladen oder erneut zu senden.

**Kann die mehrstufige Authentifizierung für Gastbenutzer von "Multi-Factor Authentication" erzwungen werden, wenn die Partner nicht über Multi-Factor Authentication verfügen?**

Ja. Weitere Informationen finden Sie unter [bedingter Zugriff für Benutzer der B2B-Zusammenarbeit](https://docs.microsoft.com/azure/active-directory/active-directory-b2b-mfa-instructions).

**Wie erfolgt die B2B-Zusammenarbeit, wenn der eingeladene Partner den Partnerverbund verwendet, um die eigene lokale Authentifizierung hinzuzufügen?**

Wenn der Partner über einen Azure AD-Mandanten verfügt, der über einen Verbund in die lokale Authentifizierungsinfrastruktur eingebunden ist, wird automatisch lokales einmaliges Anmelden (Single Sign-On, SSO) ausgeführt. Wenn der Partner über keinen Azure AD Mandanten verfügt, kann ein Azure AD Konto für neue Benutzer erstellt werden.

**Kann ich Gastbenutzer mit e-Mail-Konten für Kunden einladen?**

Das Einladen von Gastbenutzern mit e-Mail-Konten für Consumer wird in Power BI unterstützt Dies schließt Domänen ein, z. b. hotmail.com, Outlook.com und gmail.com. Allerdings können diese Benutzer Einschränkungen aufweisen, die über die Benutzer mit Geschäfts-, Schul-oder unikonten hinausgehen.
