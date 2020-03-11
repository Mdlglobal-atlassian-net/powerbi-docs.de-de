---
title: Veröffentlichen im Web aus Power BI
description: Mit der Power BI-Funktion „Im Web veröffentlichen“ können Sie auf einfache Weise interaktive Power BI-Visualisierungen auf beliebigen Geräten online einbetten, etwa in Blogbeiträgen, auf Websites, in E-Mails oder über soziale Medien.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 02/25/2020
LocalizationGroup: Share your work
ms.openlocfilehash: 99fd17e8491613affbfe78e7cd9a2f268f588975
ms.sourcegitcommit: d65da4738f011beec8f4423085cbd483511cdfb0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/03/2020
ms.locfileid: "78237981"
---
# <a name="publish-to-web-from-power-bi"></a>Veröffentlichen im Web aus Power BI

Mit der Power BI-Option **Im Web veröffentlichen** können Sie auf einfache Weise interaktive Power BI-Visualisierungen von beliebigen Geräten online einbetten, etwa in Blogbeiträgen, auf Websites, in E-Mails oder über soziale Medien. Ebenso einfach können Sie Ihre veröffentlichten Visuals bearbeiten, updaten, aktualisieren oder ihre Freigabe aufheben.

> [!WARNING]
> Wenn Sie **Im Web veröffentlichen** verwenden, kann jedermann Ihren veröffentlichten Bericht oder Ihr veröffentliches Visual im Internet ansehen. Dafür ist keine Authentifizierung erforderlich, und es umfasst das Anzeigen von Daten auf Detailebene, die in Ihren Berichten aggregiert sind. Vergewissern Sie sich vor dem Veröffentlichen eines Berichts, dass die öffentliche Weitergabe der Daten und Visuals in Ihrem Sinne ist. Veröffentlichen Sie keine vertraulichen oder proprietären Informationen. Überprüfen Sie vor der Veröffentlichung im Zweifelsfall die Richtlinien Ihrer Organisation.

>[!Note]
>Um Ihre Inhalte sicher in ein internes Portal oder eine interne Website einzubetten, verwenden Sie die Optionen [Einbetten](service-embed-secure.md) oder [In SharePoint Online einbetten](service-embed-report-spo.md). Dadurch wird sichergestellt, dass alle Berechtigungen und die Datensicherheit erzwungen werden, wenn die Benutzer Ihre internen Daten abrufen.

## <a name="how-to-use-publish-to-web"></a>Verwenden von „Im Web veröffentlichen“

**Im Web veröffentlichen** steht für Berichte zur Verfügung, die Sie in Ihren persönlichen Arbeitsbereichen oder Gruppenarbeitsbereichen bearbeiten können.  Sie besteht nicht für Berichte, die mit Ihnen geteilt wurden, oder für Berichte, für die Datenschutz mithilfe von Sicherheit auf Zeilenebene konfiguriert ist. Eine vollständige Liste der Fälle, in denen **Im Web veröffentlichen** nicht unterstützt wird, finden Sie weiter unten im Abschnitt [**Einschränkungen**](#limitations). Lesen Sie die **Warnung** weiter oben in diesem Artikel, bevor Sie **Im Web veröffentlichen** verwenden.

Das folgende kurze Video veranschaulicht die Funktionsweise dieses Features. Probieren Sie es anschließend in den unten angegebenen Schritten aus.

<iframe width="560" height="315" src="https://www.youtube.com/embed/UF9QtqE7s4Y" frameborder="0" allowfullscreen></iframe>

In den folgenden Schritten wird die Verwendung von **Im Web veröffentlichen**beschrieben.

1. Öffnen Sie in Ihrem Arbeitsbereich einen Bericht, den Sie bearbeiten können, und wählen Sie **Datei > Im Web veröffentlichen** aus.

   ![PtW1](media/service-publish-to-web/publish_to_web1.png)
   
2. Sollten Sie nicht berechtigt sein, Einbindungscodes zu erstellen, wenden Sie sich an Ihren [Power BI-Administrator](service-admin-role.md).

   ![PtW1](media/service-publish-to-web/publish_to_web_admin_prompt.png)
   
   Hilfe bei der Suche nach der Person, die die Veröffentlichung im Web in Ihrer Organisation aktivieren kann, finden Sie in [diesen Tipps](#how-to-find-your-power-bi-administrator).

3. Überprüfen Sie den Inhalt des Dialogfelds, und wählen Sie **Einbindungscode erstellen** aus.

   ![PtW2](media/service-publish-to-web/publish_to_web2_ga.png)

4. Lesen Sie die Warnung, wie hier dargestellt, und bestätigen Sie, dass die Daten auf einer öffentlichen Website eingebettet werden können. Wenn das der Fall ist, wählen Sie **Veröffentlichen** aus.

   ![PtW3](media/service-publish-to-web/publish_to_web3_ga.png)

5. Es wird ein Dialogfeld mit einem Link angezeigt. Sie können diesen Link per E-Mail senden, ihn in Code wie etwa einen iFrame einbetten oder ihn direkt in eine Webseite oder einen Blog einfügen.

   ![PtW4](media/service-publish-to-web/publish_to_web4.png)

6. Wenn Sie zuvor einen Einbindungscode für einen Bericht erstellt haben und Sie **Im Web veröffentlichen** auswählen, werden die Dialogfelder in den Schritten 2–4 nicht angezeigt. Stattdessen wird das Dialogfeld **Einbindungscode** angezeigt:

   ![PtW5](media/service-publish-to-web/publish_to_web5.png)

   Für jeden Bericht kann nur ein Einbindungscode erstellt werden.


## <a name="tips-and-tricks-for-view-modes"></a>Tipps und Tricks für Ansichtsmodi

Wenn Sie Inhalte in einen Blogbeitrag einbetten, müssen Sie sie in der Regel in eine bestimmte Bildschirmgröße einpassen.  Sie können die Höhe und Breite im iFrame-Tag nach Bedarf anpassen. Allerdings müssen Sie sicherstellen, dass Ihr Bericht in den bestehenden iFrame-Bereich passt, daher müssen Sie beim Bearbeiten des Berichts auch einen geeigneten Ansichtsmodus festlegen.

Die folgende Tabelle gibt Hilfestellung zum Ansichtsmodus und wie er sich auf die Darstellung bei der Einbettung auswirkt.

| Ansichtsmodus | Darstellung bei der Einbettung |
| --- | --- |
| ![PtW6b](media/service-publish-to-web/publish_to_web6b.png) |**An Seite anpassen** berücksichtigt die Seitenhöhe und -breite des Berichts. Wenn Sie für Ihre Seite ein *dynamisches* Seitenverhältnis – z. B. 16:9 oder 4:3 – festlegen, wird Ihr Inhalt so skaliert, dass er in den iFrame passt. Wenn Inhalt im iFrame eingebettet ist, kann die Verwendung von **An Seite anpassen** zu einem *Letterbox-Effekt* führen, wobei ein grauer Hintergrund in iFrame-Bereichen angezeigt wird, nachdem der Inhalt so skaliert wurde, dass er in den iFrame passt. Um den Letterbox-Effekt zu minimieren, legen Sie die Höhe und Breite Ihres iFrames entsprechend fest. |
| ![PtW6d](media/service-publish-to-web/publish_to_web6d.png) |**Originalgröße** stellt sicher, dass die Größe des Berichts so beibehalten wird, wie sie auf der Berichtsseite festgelegt ist. Dies kann zur Folge haben, dass im iFrame Scrollleisten angezeigt werden. Legen Sie die iFrame-Höhe und -Breite so fest, dass Scrollleisten vermieden werden. |
| ![PtW6c](media/service-publish-to-web/publish_to_web6c.png) |**An Breite anpassen** stellt sicher, dass die Inhalte den horizontalen Bereich des iFrames ausfüllen. Es wird trotzdem ein Rahmen angezeigt, die Inhalte werden aber so skaliert, dass der in der Horizontalen verfügbare Platz vollständig ausgenutzt wird. |

## <a name="tips-and-tricks-for-iframe-height-and-width"></a>Tipps und Tricks für die iFrame-Höhe und -Breite

Ein **Im Web veröffentlichen**-Einbindungscode sieht folgendermaßen aus:

![PtW7](media/service-publish-to-web/publish_to_web7.png)
 
Sie können Breite und Höhe manuell bearbeiten, um sicherzustellen, dass die Einpassung auf der Seite, auf der Sie den Code einbetten, genau Ihren Vorstellungen entspricht.

Um eine bessere Anpassung zu erreichen, können Sie versuchen, 56 Pixel zur Höhe des iFrames hinzuzufügen, um der aktuellen Größe der unteren Leiste Rechnung zu tragen. Wenn Ihre Berichtsseite die dynamische Größe verwendet, finden Sie in der nachstehenden Tabelle einige Größen, die Sie verwenden können, um eine Anpassung ohne Letterbox-Effekt zu erreichen.

| Seitenverhältnis | Größe | Dimension (Breite x Höhe) |
| --- | --- | --- |
| 16:9 |Small |640 x 416 px |
| 16:9 |Mittel |800 x 506 px |
| 16:9 |Large |960 x 596 px |
| 4:3 |Small |640 x 536 px |
| 4:3 |Mittel |800 x 656 px |
| 4:3 |Large |960 x 776 px |

## <a name="manage-embed-codes"></a>Einbindungscodes verwalten

Nachdem Sie einen **Im Web veröffentlichen**-Einbindungscode erstellt haben, können Sie Ihre Codes aus dem Menü **Einstellungen** in Power BI verwalten. Das Verwalten von Einbindungscodes schließt auch die Möglichkeit ein, das visuelle Zielelement oder den Zielbericht für einen Code zu entfernen (wodurch der Einbindungscode unbrauchbar wird) oder den Einbindungscode abzurufen.

1. Um Ihre Einbindungscodes für **Im Web veröffentlichen** zu verwalten, öffnen Sie über das Zahnrad das Menü **Einstellungen** , und wählen Sie **Einbindungscodes verwalten**aus.

   ![PtW8](media/service-publish-to-web/publish_to_web8.png)

2. Ihre Einbindungscodes werden angezeigt.

   ![PtW9](media/service-publish-to-web/publish_to_web9.png)

3. Sie können einen Einbindungscode entweder abrufen oder löschen. Durch das Löschen werden alle Verknüpfungen mit dem betreffenden Bericht oder dem betreffenden Visual deaktiviert.

   ![PtW10](media/service-publish-to-web/publish_to_web10.png)

4. Wenn Sie **Löschen** auswählen, werden Sie um eine Bestätigung gebeten.

   ![PtW11](media/service-publish-to-web/publish_to_web11.png)

## <a name="updates-to-reports-and-data-refresh"></a>Updates an Berichten und Datenaktualisierung

Nachdem Sie einen **Im Web veröffentlichen**-Einbindungscode erstellt und geteilt haben, werden alle Änderungen, die Sie vornehmen, im Bericht aktualisiert, und der Einbindungscodelink ist sofort aktiv. Jeder, der den Link öffnet, kann den Bericht sehen. Nach dieser anfänglichen Aktion kann es jedoch zwei bis drei Stunden dauern, bis Änderungen an Berichten oder visuellen Elementen für Ihre Benutzer sichtbar werden. Weitere Informationen finden Sie im Abschnitt [**Funktionsweise**](#howitworks) weiter unten in diesem Artikel. 

## <a name="data-refresh"></a>Datenaktualisierung

Datenaktualisierungen werden in Ihrem eingebetteten Bericht oder in Ihrer Virtualisierung automatisch wiedergegeben. Es kann ungefähr eine Stunde dauern, bis aktualisierte Daten über Einbindungscodes widergespiegelt werden. Um die automatische Aktualisierung zu deaktivieren, wählen Sie im Zeitplan für das vom Bericht verwendete Dataset **nicht aktualisieren** aus.  

## <a name="custom-visuals"></a>Benutzerdefinierte visuelle Elemente

Benutzerdefinierte visuelle Elemente werden von **Im Web veröffentlichen**unterstützt. Wenn Sie **Im Web veröffentlichen** verwenden, brauchen Benutzer, mit denen Sie Ihr veröffentlichtes Visual teilen, benutzerdefinierte Visuals nicht zu aktivieren, um den Bericht anzuzeigen.

## <a name="limitations"></a>Einschränkungen

**Im Web veröffentlichen** wird für die überwiegende Mehrheit der Datenquellen und Berichte im Power BI-Dienst unterstützt, die folgenden werden in **Im Web veröffentlichen** jedoch aktuell nicht unterstützt oder stehen nicht zur Verfügung:

- Berichte, die die Sicherheit auf Zeilenebene verwenden
- Berichte, die eine Datenquelle mit Liveverbindung verwenden, einschließlich dem lokal gehosteten tabellarischen Analysis Services-Dienst, dem mehrdimensionalen Analysis Services-Dienst und Azure Analysis Services.
- Berichte, die ein [freigegebenes Dataset](service-datasets-across-workspaces.md) verwenden, das in einem anderen Arbeitsbereich gespeichert ist als der Bericht.
- Berichte, die für Sie direkt oder über ein Organisationsinhaltspaket freigegeben werden
- Berichte in einer Gruppe, in der Sie kein Bearbeitungsmitglied sind
- „R“-Visualisierungen werden in **Im Web veröffentlichen**-Berichten derzeit nicht unterstützt.
- Exportieren von Daten aus visuellen Elementen in einen Bericht, der im Web veröffentlicht wurde.
- ArcGIS Maps for Power BI-Visuals
- Berichte, die DAX-Measures auf Berichtebene enthalten
- SSO-Datenabfragemodelle
- Geschützte vertrauliche oder proprietäre Informationen
- [Freigegebene und zertifizierte Datasets](service-datasets-share.md).
- Die Funktion zur automatischen Authentifizierung, die von der Option **Einbetten** unterstützt wird, kann nicht mit der Power BI-JavaScript-API verwendet werden. Verwenden Sie zum Einbetten mit der Power BI-JavaScript-API die Methode [Benutzer ist Besitzer der Daten](developer/embed-sample-for-your-organization.md).

## <a name="tenant-setting"></a>Mandanteneinstellung

Bei der Einstellung **Im Web veröffentlichen** gibt es mehrere Optionen dafür, welche Benutzer Einbindungscodes erstellen können.

![Einstellung „Im Web veröffentlichen“](media/service-admin-portal/powerbi-admin-publish-to-web-setting.png)

Sie werden dazu aufgefordert, sich zum Erstellen eines Einbindungscodes an einen Power BI-Administrator zu wenden, wenn bei der Option **Funktionsweise von Einbindungscodes auswählen** **Nur vorhandene Einbindungscodes zulassen** und für die Einstellung **Im Web veröffentlichen** **Aktiviert** ausgewählt ist.

![„Im Web veröffentlichen“-Aufforderung](media/service-publish-to-web/publish_to_web_admin_prompt.png)

Power BI-Administratoren können die Funktion **Im Web veröffentlichen** aktivieren oder deaktivieren. Sie können außerdem den Zugriff auf bestimmte Gruppen einschränken, was Ihre Möglichkeit zum Erstellen eines Einbindungscodes beeinträchtigen kann. Ihnen werden basierend auf der jeweiligen Einstellung **Im Web veröffentlichen** unterschiedliche Optionen in der Benutzeroberfläche angezeigt.

|Feature |Für die gesamte Organisation aktiviert |Für die gesamte Organisation deaktiviert |Sicherheitsgruppen angeben   |
|---------|---------|---------|---------|
|**Im Web veröffentlichen** im Menü **Datei** des Berichts|Für alle aktiviert|Nicht für alle sichtbar|Nur für autorisierte Benutzer oder Gruppen sichtbar|
|**Einbindungscodes verwalten** unter **Einstellungen**|Für alle aktiviert|Für alle aktiviert|Für alle aktiviert<br><br>Option * **Löschen** nur für autorisierte Benutzer oder Gruppen<br>* **Codes abrufen** für alle aktiviert|
|**Einbindungscodes** im Verwaltungsportal|Es wird einer der folgenden Status angezeigt:<br>* Aktiv<br>* Nicht unterstützt<br>* Blockiert|Als Status wird **Deaktiviert** angezeigt.|Es wird einer der folgenden Status angezeigt:<br>* Aktiv<br>* Nicht unterstützt<br>* Blockiert<br><br>Wenn ein Benutzer gemäß den Mandanteneinstellungen nicht autorisiert ist, wird als Status **Verletzt** angezeigt.|
|Vorhandene veröffentlichte Berichte|Alle aktiviert|Alle deaktiviert|Berichte werden weiterhin für alle gerendert.|

## <a name="understanding-the-embed-code-status-column"></a>Funktionsweise der Einbindungscode-Statusspalte

>[!Note]
>Sie sollten die von Ihnen veröffentlichten Einbindungscodes regelmäßig überprüfen und die Codes, die nicht mehr öffentlich verfügbar sein müssen, entfernen. 

Die Seite **Einbindungscodes verwalten** beinhaltet eine Statusspalte. Standardmäßig sind Einbindungscodes **aktiv**, sie können aber auch einen der unten aufgelisteten Status aufweisen.

| Status | Beschreibung |
| --- | --- |
| **Aktiv** |Der Bericht ist für Internetbenutzer zur Ansicht und Interaktion verfügbar. |
| **Blockiert** |Der Bericht verstößt gegen die [Power BI-Vertragsbedingungen](https://powerbi.microsoft.com/terms-of-service). Microsoft hat ihn blockiert. Kontaktieren Sie den Support, wenn Sie glauben, dass der Inhalt irrtümlich blockiert wurde. |
| **Nicht unterstützt** |Das Dataset des Berichts verwendet die Sicherheit auf Zeilenebene oder eine andere nicht unterstützte Konfiguration. Eine vollständige Liste finden Sie im Abschnitt [**Einschränkungen**](#limitations). |
| **Verletzt** |Der Einbindungscode befindet sich außerhalb der definierten Mandantenrichtlinie. Dies tritt normalerweise auf, wenn ein Einbindungscode erstellt und dann die Mandanteneinstellung **Im Web veröffentlichen** so geändert wurde, dass der Eigentümer des Einbindungscodes ausgeschlossen wird. Wenn die Mandanteneinstellung deaktiviert wird oder der Benutzer keine Einbindungscodes mehr erstellen darf, wird bei vorhandenen Einbindungscodes der Status **Verletzt** angezeigt. |

## <a name="how-to-report-a-concern-with-publish-to-web-content"></a>Melden eines Problems im Zusammenhang mit „Im Web veröffentlichen“-Inhalten

Um ein Problem im Zusammenhang mit den auf einer Website oder in einem Blog eingebetteten **Im Web veröffentlichen** -Inhalten zu melden, verwenden Sie das **Flaggensymbol** in der unteren Leiste, wie in der folgenden Abbildung dargestellt. Sie werden aufgefordert, eine E-Mail an Microsoft zu senden, in der Sie Ihr Anliegen erläutern. Microsoft beurteilt die Inhalte auf der Grundlage der Power BI-Vertragsbedingungen und leitet geeignete Maßnahmen ein.

Um ein Problem zu melden, wählen Sie das **Flaggensymbol** in der unteren Leiste des angezeigten **Im Web veröffentlichen**-Berichts aus.

![PtW12](media/service-publish-to-web/publish_to_web12_ga.png)

## <a name="licensing-and-pricing"></a>Lizenzierung und Preise

Sie müssen ein Microsoft Power BI-Benutzer sein, um **Im Web veröffentlichen**zu verwenden. Die Betrachter Ihres Berichts müssen keine Power BI-Benutzer sein.

<a name="howitworks"></a>
## <a name="how-it-works-technical-details"></a>Funktionsweise (technische Details)

Wenn Sie mithilfe von **Im Web veröffentlichen**einen Einbindungscode erstellen, wird der Bericht für Internetbenutzer sichtbar gemacht. Er ist öffentlich verfügbar, daher können Sie davon ausgehen, dass Leser den Bericht in Zukunft einfach über soziale Medien teilen. Wenn Benutzer den Bericht anzeigen, entweder indem sie die direkte öffentliche URL öffnen oder den Bericht auf einer Webseite oder in einem Blog eingebettet anzeigen, speichert Power BI die Berichtsdefinition und die Ergebnisse der zum Anzeigen des Berichts erforderlichen Abfragen zwischen. Dadurch wird sichergestellt, dass Tausende Benutzer den Bericht gleichzeitig anzeigen können, ohne dass die Leistung beeinträchtigt wird.

Der Cache hat einen langen Lebenszyklus. Wenn Sie die Berichtsdefinition aktualisieren (etwa, indem Sie den Ansichtsmodus ändern) oder die Berichtsdaten, kann es daher ungefähr eine Stunde dauern, ehe die Änderungen in der Ihren Benutzern angezeigten Version des Berichts angezeigt werden. Es wird daher empfohlen, dass Sie Ihre Arbeit rechtzeitig vorab bereitstellen und den Einbindungscode für **Im Web veröffentlichen** erst erstellen, wenn Sie mit den Einstellungen zufrieden sind.

## <a name="how-to-find-your-power-bi-administrator"></a>So finden Sie den Power BI-Administrator

Wenn Sie die [Einstellungen für die Veröffentlichung im Webmandanten](#tenant-setting) ändern möchten, müssen Sie sich an den [Power BI-Administrator](service-admin-role.md) Ihrer Organisation wenden.

Kleinere Organisationen oder Einzelpersonen, die sich für Power BI registriert haben, verfügen möglicherweise noch nicht über einen Power BI-Administrator. Sie müssen unseren [Prozess für die Übernahme des Mandantenadministrators](https://docs.microsoft.com/azure/active-directory/users-groups-roles/domains-admin-takeover) ausführen. Sobald Sie einen Power BI-Administrator haben, kann er die Erstellung von Einbindungscode für Sie aktivieren.

Etablierte Organisationen verfügen in der Regel bereits über einen Power BI-Administrator. Personen mit einer der folgenden Rollen können als Power BI-Administrator fungieren:

- Office 365-Administratoren
- Azure Active Directory-Administratoren
- Benutzer mit der Rolle eines Power BI-Dienstadministrators in Azure Active Directory

Suchen Sie eine [dieser Personen](https://docs.microsoft.com/office365/admin/admin-overview/admin-overview#who-has-admin-permissions-in-my-business) in Ihrer Organisation, damit diese die Einstellung aktualisieren kann.


## <a name="next-steps"></a>Nächste Schritte

- [SharePoint Online-Berichts-Webpart](service-embed-report-spo.md) 

- [Einbetten eines Berichts in ein sicheres Portal oder eine sichere Website](service-embed-secure.md)

Weitere Fragen? [Wenden Sie sich an die Power BI-Community](https://community.powerbi.com/)
