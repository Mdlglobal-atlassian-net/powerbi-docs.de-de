---
title: Konformität der PDF-Renderingerweiterung mit ISO 14289-1 – Power BI-Berichtsserver & SSRS
description: Dieses Dokument beschreibt die Konformität der PDF-Renderingerweiterung von Power BI-Berichtsserver und SQL Server Reporting Services mit den ISO 14289-1-Spezifikationen (PDF/UA).
author: maggiesMSFT
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.topic: conceptual
ms.date: 11/04/2019
ms.author: maggies
ms.openlocfilehash: bfefcef18b8cd92a5c3b15c2dcbd4653a6c7c9cd
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "76819512"
---
# <a name="pdf-rendering-extension-conformance-to-iso-14289-1---power-bi-report-server--ssrs"></a>Konformität der PDF-Renderingerweiterung mit ISO 14289-1 – Power BI-Berichtsserver & SSRS

Gilt für: Power BI-Berichtsserver und SQL Server Reporting Services (SSRS)

Dieses Dokument beschreibt die Konformität der PDF-Renderingerweiterung von Power BI-Berichtsserver und SQL Server Reporting Services mit den [ISO 14289-1-Spezifikationen (PDF/UA)](https://www.pdfa.org/publication/pdfua-in-a-nutshell/).

> [!NOTE]
> Sie können dieses Whitepaper speichern oder ausdrucken, indem Sie in Ihrem Browser erst auf **Drucken** und dann auf **Als PDF speichern** klicken.

## <a name="1--scope"></a>1.  Bereich

Nicht zutreffend

## <a name="2--normative-references"></a>2.  Normative Verweise

Nicht zutreffend

## <a name="3--terms-and-definitions"></a>3.  Bedingungen und Definitionen

Nicht zutreffend

## <a name="4--notation"></a>4.  Notation

Nicht zutreffend

## <a name="5-version-identification"></a>5. Versionsidentifikation

Die PDF-Renderingerweiterung bietet Unterstützung für PDF/UA, wie in diesem Dokument beschrieben. In einigen der unten genannten Fälle ist es Aufgabe des Benutzers, Schritte zu unternehmen, um vollständige PDF-Konformität mit PDF/UA sicherzustellen.  Es wird vom Benutzer erwartet, dass er im letzten Schritt in diesem Prozess die entsprechende PDF/UA-Version und Konformitätskennzeichen hinzufügt. So wird nachgewiesen, dass die erforderlichen Maßnahmen getroffen wurden, um vollständige PDF-Konformität mit PDF/UA sicherzustellen.

Sämtliche Informationen in diesem Dokument basierend auf dem Rendering eines PDF-Dokuments, bei dem die AccessiblePdf-Geräteinfoeinstellung auf `true` festgelegt ist. In einigen Fällen sind Konformitätsbeschränkungen auf Einschränkungen in der Berichtsdefinitionssprache (Report Definition Language, RDL) zurückzuführen.

## <a name="6--conformance-requirements"></a>6.  Konformitätsanforderungen

|     Kriterien     |     Unterstützendes Feature     |     Bemerkungen      |
|----|--------|--------|
|    6.1 Allgemein    |                 Unterstützt    |    Die PDF-Renderingerweiterung erstellt PDF-Dokumente der Version 1.7.    |
|    6.2 Konforme Dateien    |                 Unterstützt mit Ausnahmen    |    Siehe Bemerkungen in Abschnitt 7: Anforderungen an das Dateiformat.    |
|    6.3 Konformer Reader    |     Nicht zutreffend     |         |
|    6.4 Konforme Hilfstechnologie    |     Nicht zutreffend     |         |

## <a name="7--file-format-requirements"></a>7.  Anforderungen an das Dateiformat

|     Kriterien     |     Unterstützendes Feature     |     Bemerkungen      |
|-----|-------|------------------------|
|    7.1 Allgemein    |                 Unterstützt mit Ausnahmen    |    Alle bedeutungstragenden Inhalte müssen gemäß Definition in ISO 32000-1:2008, 14.8 mit Tags versehen werden. Artefakte (ISO 32000-1:2008, 14.8.2.2.2) dürfen in der Baumstruktur nicht mit Tags versehen werden. <li> Die PDF-Renderingerweiterung bietet keine Flexibilität zur expliziten Markierung einzelner Elemente als Artefakte. Stattdessen werden alle Elemente als Artefakte markiert, die den Kriterien in ISO 32000-1:2008, 14.8.2.2.2. entsprechen.<br>Inhalte müssen in der Baumstruktur mithilfe semantisch geeigneter Tags in logischer Lesereihenfolge markiert werden. <br> **Hinweis** WCAG 2.0, Richtlinie 1.4 erläutert Probleme in Bezug auf Kontrast, Farbe und andere Formatierungen für Barrierefreiheit. <br><li> Der Benutzer muss sicherstellen, dass keines dieser Probleme im Dokument vorliegt. <br>Die in ISO 32000-1:2008, 14.8.4 definierten Standardtags dürfen nicht neu zugeordnet werden. <li> Über die PDF-Renderingerweiterung findet keine Neuzuordnung der Standardtags statt. Dokumente beginnen mit dem Stammelement „Document“. <br>Dateien, die Anspruch auf Konformität mit dieser internationalen Norm erheben, müssen den Suspects-Wert „false“ aufweisen (ISO 32000-1:2008, Tabelle 321). <li> Die PDF-Renderingerweiterung weist keinen Suspects-Eintrag auf. Diese Eigenschaft ist optional.    |
|    7.2 Text    |                 Unterstützt mit Ausnahmen    |    Inhalte müssen in der logischen Lesereihenfolge markiert werden. Für jedes logische Element im Dokumentinhalt ist das semantisch am besten geeignete Tag zu verwenden. <br><li> Die PDF-Renderingerweiterung markiert Inhalte in logischer Lesereihenfolge, soweit dies möglich ist.<br>Zeichencodes müssen Unicode zugeordnet sein, wie in ISO 32000-1:2008, 14.8.2.4.2 beschrieben. Zeichen, die nicht in der Unicode-Spezifikation enthalten sind, können den privaten Unicode-Nutzungsbereich verwenden oder eine andere Zeichencodierung deklarieren. <br>Die natürliche Sprache muss wie in ISO 32000-1:2008, 14.9.2 und/oder wie in ISO 32000-1:2008, 7.9.2 beschrieben deklariert werden. Änderungen in der natürlichen Sprache sind zu deklarieren. Änderungen in der natürlichen Sprache innerhalb von Textzeichenfolgen (z. B. in alternativen Beschreibungen) müssen mit einem Sprachbezeichner gemäß ISO 32000-1:2008, 14.9.2.2 deklariert werden. <br><li> Die PDF-Renderingerweiterung deklariert natürliche Sprache nur auf Dokumentebene.    |
|    7.3 Grafiken    |                 Unterstützt mit Ausnahmen    |    Grafikobjekte müssen, anders als Textobjekte, mit einem Figure-Tag versehen werden, wie beschrieben in ISO 32000-1:2008, 14.8.4.5, Tabelle 340. Wenn eine der folgenden Ausnahmen zutrifft, muss die Grafik als Artefakt gekennzeichnet werden: <br><li> Die Grafik repräsentiert keinen bedeutungstragenden Inhalt. <li>  Die Grafik erscheint als Hintergrund für eine Anmerkung zu einem Link. In diesem Fall muss der alternative Text für den Link sowohl die Grafik als auch den Link beschreiben. <li> Die PDF-Renderingerweiterung versieht Grafikobjekte mit dem Figure-Tag. <br>Eine Beschriftung für eine Abbildung muss mit einem Caption-Tag versehen werden. <li> Die PDF-Renderingerweiterung versieht Beschriftungen für Abbildungen aktuell nicht mit einem Caption-Tag. <br>Figure-Tags müssen eine alternative Darstellung oder Ersetzungstext enthalten, der die mit dem Figure-Tag markierten Inhalte repräsentiert, wie beschrieben in ISO 32000-1:2008, 14.7.2, Tabelle 323. <br>**Hinweis** 1 Siehe auch WCAG 2.0, Richtlinie 1.1. <br>Wenn der in einer Grafik dargestellte Text nicht in einer natürlichen Sprache vorliegt und nicht darauf ausgelegt ist, von Personen gelesen zu werden, muss ein alternativer Text bereitgestellt werden, der die Art oder den Zweck der Grafik beschreibt. <br>**Hinweis** 2 Ein Typenbeispiel oder ein Beispiel für das in einer Sprache verwendete Schriftsystem sind Beispiele für Text, der nicht in einer natürlichen Sprache vorliegt.   Die PDF-Renderingerweiterung unterstützt alternativen Text für Abbildungen, dieser muss jedoch durch den Benutzer hinzugefügt werden. <br>Zusätzlicher Hinweis zum BBox-Attribut: <br><li> Die PDF-Renderingerweiterung bietet aktuell keine Unterstützung für das BBox-Attribut. <li> Eine Umgehung besteht darin, Abbildungen manuell als neue Abbildungen oder Artefakte zu markieren.    |
|    7.4 Überschriften    |                 Nicht zutreffend    |    RDL unterstützt keine Form von Markup für Überschriften. Es liegt in der Verantwortung des Benutzers, diese nach Bedarf zu markieren.    |
|    7.5 Tabellen    |                 Unterstützt mit Ausnahmen    |    Tabellen müssen Überschriften aufweisen. Tabellen sind gemäß  ISO 32000-1:2008, Tabelle 337 und Tabelle 349 mit Tags zu versehen. <br>**Hinweis** 1 Tabellen können Spaltenüberschriften, Zeilenüberschriften oder beides enthalten. <br>**Hinweis** 2 Bei Verwendung einer Hilfstechnologie müssen so viele Informationen wie möglich über die Struktur von Tabellen zur Verfügung stehen. Überschriften spielen bei der Bereitstellung von Strukturinformationen eine entscheidende Rolle. <br><li> Es liegt in der Verantwortung des Benutzers, Überschriften in Tabellen einzufügen. RDL und PDF-Renderingerweiterung bieten Unterstützung für Zeilenüberschriften. <br>  Strukturelemente vom Typ „TH“ müssen ein Scope-Attribut aufweisen.   <li> Die PDF-Renderingerweiterung umfasst für Column- und Row-Member ein Scope-Attribut für TH-Elemente, nicht jedoch für Corner-Zellen.<br>Strukturen für die Tabellenmarkierung dürfen nur für die Kennzeichnung von Inhalten verwendet werden, die in logischen Zeilen- und/oder Spaltenbeziehungen dargestellt werden.   <li> Dies hängt davon ab, wie der Benutzer sich für die Verwendung von Tabellen in RDL entschieden hat.    |
|    7.6 Listen    |                 Nicht zutreffend    |    RDL bietet keine Unterstützung für das Markup von Listen. In RDL handelt es sich bei einer Liste strukturell um eine Tabelle mit einer einzigen Tabellenzelle. <br>Es liegt in der Verantwortung des Benutzers, sie nach Bedarf neu zu markieren.    |
|    7.7 Mathematische Ausdrücke    |                 Unterstützt mit Ausnahmen    |    Alle mathematischen Ausdrücke müssen in einem Formula-Tag gemäß ISO 32000-1:2008, 14.8.4.5 eingeschlossen sein und ein Alt-Attribut aufweisen. <br><li> Die PDF-Renderingerweiterung schließt mathematische Ausdrücke aktuell nicht in ein Formula-Tag ein. <br>Die Anforderungen bezüglich der Unicode-Zuordnung von Zeichen gelten für mathematische Ausdrücke, wie in ISO 32000-1:2008, 9.10.2 und 14.8.2.4 beschrieben. <br><li> Diese Anforderung wird von der PDF-Renderingerweiterung erfüllt.    |
|    7.8 Kopf- und Fußzeilen für Seiten    |                 Unterstützt    |    Fortlaufende Kopf- und Fußzeilen müssen gemäß ISO 32000-1:2008, 14.8.2.2.2, Tabelle 330 als Pagination-Artefakte gekennzeichnet und entweder als Header- oder Footer-Untertypen klassifiziert werden. <br><li> Kopf- und Fußzeilen werden wie Artefakte behandelt und markiert.    |
|    7.9 Hinweise und Referenzen    |                 Nicht zutreffend    |    Die PDF-Renderingerweiterung bietet keine Unterstützung für das Markup von Hinweisen und Referenzen. <br>Es liegt in der Verantwortung des Benutzers, diese nach Bedarf zu markieren.    |
|    7.10 Optionale Inhalte    |                 Nicht zutreffend    |         |
|    7.11 Eingebettete Dateien    |                 Nicht zutreffend    |         |
|    7.12 Artikelthreads    |                 Nicht zutreffend    |         |
|    7.13 Digitale Signaturen    |                 Nicht zutreffend    |         |
|    7.14 Nicht interaktive Formulare    |                 Nicht zutreffend    |         |
|    7.15 XFA    |                 Nicht zutreffend    |         |
|    7.16 Sicherheit    |                 Nicht zutreffend    |         |
|    7.17 Navigation    |                 Unterstützt    |    Ein Dokument muss eine Dokumentenbeschreibung enthalten, die der Lesereihenfolge und der Ebene der Navigationsziele entspricht (ISO 32000-1:2008, 12.3.3). <br><li> RDL unterstützt Lesezeichen für ein Berichtselement, aber der Benutzer muss diese Option auswählen. Diese Lesezeichen werden dann von der PDF-Renderingerweiterung als Dokumentgliederung gerendert. <br>Sofern vorhanden, müssen die Einträge in der PageLabels-Nummernstruktur (ISO 32000-1:2008, 7.7.2, Tabelle 28) semantisch angemessen sein. <br><li> Die PDF-Renderingerweiterung umfasst keine PageLabels-Zahlenstruktur.    |
|    7.18 Anmerkungen    |                 Nicht zutreffend    |    RDL unterstützt keine Anmerkungen.    |
|    7.21 Schriftarten    |                 Unterstützt    |         |
|    7.21.1 Allgemein    |                 Unterstützt    |         |
|    7.21.2 Schriftarttypen    |                 Unterstützt    |         |
|    7.21.3 Zusammengesetzte Schriftarten    |                 Unterstützt    |         |
|    7.21.3.1 Allgemein    |                 Unterstützt    |         |
|    7.21 3.2 CIDFonts    |                 Unterstützt    |         |
|    7.21.3.3 CMaps    |                 Unterstützt    |         |
|    7.21.4 Einbettung    |                 Unterstützt    |         |
|    7.21.4.1 Allgemein    |                 Unterstützt    |         |
|    7.21.4.2 Einbetten von Teilmengen    |                 Unterstützt    |         |
|    7.21.5 Fontmetriken    |                 Unterstützt    |         |
|    7.21.6 Zeichencodierungen    |                 Unterstützt    |         |
|    7.21.7 Unicode-Zeichenzuordnungen    |                 Unterstützt    |         |
|    7.21.8 Verwendung der .notdef-Glyphe    |                 Unterstützt    |         |

## <a name="8--conforming-reader-requirements"></a>8.  Anforderungen an einen konformen Reader

Nicht zutreffend

## <a name="9--at-requirements"></a>9.  AT-Anforderungen

Nicht zutreffend

## <a name="disclaimer"></a>Disclaimer

© 2017 Microsoft Corporation. All rights reserved. The names of actual companies and products mentioned herein may be the trademarks of their respective owners. The information contained in this document represents the current view of Microsoft Corporation on the issues discussed as of the date of publication. Microsoft cannot guarantee the accuracy of any information presented after the date of publication. Microsoft regularly updates its websites with new information about the accessibility of products as that information becomes available.

Customization of the product voids this conformance statement from Microsoft. Please consult with Assistive Technology (AT) vendors for compatibility specifications of specific AT products.

This document is for informational purposes only. MICROSOFT MAKES NO WARRANTIES, EXPRESS OR IMPLIED, IN THIS DOCUMENT.


## <a name="next-steps"></a>Nächste Schritte
[Administratorübersicht](admin-handbook-overview.md)  

Weitere Fragen? [Stellen Sie Ihre Frage in der Power BI-Community.](https://community.powerbi.com/)

