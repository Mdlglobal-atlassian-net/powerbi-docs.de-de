---
title: Übermittlungstests für ein Power BI-Visual
description: In diesem Artikel werden Testfälle beschrieben, die Ihr Visual bestehen muss, bevor es in AppSource veröffentlicht werden kann. Es werden auch optionale Testfälle vorgestellt.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: how-to
ms.date: 04/15/2020
ms.openlocfilehash: 65e00fa5311ea12c9fe0011c6aa7c3e779f33dc5
ms.sourcegitcommit: bfc2baf862aade6873501566f13c744efdd146f3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/13/2020
ms.locfileid: "83131114"
---
# <a name="submission-testing-of-a-power-bi-visual"></a>Übermittlungstests für ein Power BI-Visual

Bevor Sie Ihr Visual in [AppSource](https://appsource.microsoft.com/marketplace/apps?product=power-bi-visuals) veröffentlichen können, muss es diese Testfälle erfolgreich durchlaufen. Testen Sie Ihr Visual, bevor Sie es übermitteln. Wenn Ihr Visual die erforderlichen Testfälle nicht besteht, wird es abgelehnt.

Weitere Informationen zum Veröffentlichungsprozess finden Sie unter [Veröffentlichen von Power BI-Visuals in Partner Center](./office-store.md).

## <a name="general-test-cases"></a>Allgemeine Testfälle

| Testfall | Erwartete Ergebnisse
| --------- | ----------------
| Erstellen Sie ein **gestapeltes Säulendiagramm** mit **Kategorie** und **Wert**. Konvertieren Sie es in Ihr Visual und dann zurück in ein Säulendiagramm. | Nach diesen Konvertierungen wird kein Fehler gemeldet. |
| Erstellen Sie ein **Messgerät** mit drei Messwerten. Konvertieren Sie es in Ihr Visual und dann zurück in ein **Messgerät**. | Nach diesen Konvertierungen wird kein Fehler gemeldet. |
| Wählen Sie Elemente in Ihrem Visual aus. | Die Auswahl wird in anderen Visuals widergespiegelt. |
| Wählen Sie Elemente in anderen Visuals aus. | Ihr Visual zeigt gemäß Auswahl in anderen Visuals gefilterte Daten an. |
| Überprüfen Sie Mindest-/Höchstwerte für **dataViewMapping**-Bedingungen. | Feldbuckets können mehrere Felder oder ein einzelnes Feld akzeptieren oder werden durch andere Buckets bestimmt. Die Mindest-/Höchstwerte für **dataViewMapping**-Bedingungen müssen in den Funktionen Ihres Visuals korrekt festgelegt sein. |
| Entfernen Sie alle Felder in unterschiedlicher Reihenfolge. | Das Visual führt nach dem Entfernen von Feldern in willkürlicher Reihenfolge eine ordnungsgemäße Bereinigung durch. In der Konsole oder im Browser werden keine Fehler angezeigt. |
| Öffnen Sie den Bereich **Format** mit jeder möglichen Bucketkonfiguration. | Dieser Test löst keine NULL-Verweisausnahmen aus. |
| Filtern Sie Daten mit dem Bereich **Filter** auf Visual-, Seiten- und Berichtsebene. | Nach dem Anwenden von Filtern werden QuickInfos korrekt angezeigt. Die QuickInfos zeigen den gefilterten Wert. |
| Filtern Sie Daten einem **Slicer**. | Nach dem Anwenden von Filtern werden QuickInfos korrekt angezeigt. Die QuickInfos zeigen den gefilterten Wert. |
| Filtern Sie Daten mit einem veröffentlichten Visual. Wählen Sie beispielsweise ein Kreissegment oder eine Spalte aus. | Nach dem Anwenden von Filtern werden QuickInfos korrekt angezeigt. Die QuickInfos zeigen den gefilterten Wert. |
| Wenn eine Kreuzfilterung unterstützt wird, überprüfen Sie die ordnungsgemäße Funktion der Filter. | Eine angewendete Auswahl filtert andere Visuals auf dieser Seite des Berichts heraus. |
| Wählen Sie mit den Tasten STRG, ALT und UMSCHALT Elemente aus. | Es kommt nicht zu einem unerwarteten Verhalten. |
| Ändern Sie den **Ansichtsmodus** in **Originalgröße**, **An Seite anpassen** und **An Breite anpassen**. | Die Mauskoordinaten sind korrekt. |
| Ändern Sie die Größe Ihres Visuals. | Das Visual reagiert richtig auf die Größenänderung. |
| Legen Sie die Berichtsgröße auf den Mindestwert fest. | Es kommt nicht zu Anzeigefehlern. |
| Stellen Sie sicher, dass die Scrollleisten ordnungsgemäß funktionieren. | Scrollleisten sollten vorhanden sein, sofern erforderlich. Überprüfen Sie die Größe der Scrollleisten. Die Scrollleisten dürfen weder zu breit noch zu lang sein. Position und Größe der Scrollleisten müssen den weiteren Elementen Ihres Visuals entsprechen. Überprüfen Sie, ob Scrollleisten für unterschiedliche Größen des Visuals benötigt werden. |
| Heften Sie Ihr Visual an ein **Dashboard** an. | Das Visual sollte ordnungsgemäß angezeigt werden. |
| Fügen Sie einer einzelnen Berichtsseite mehrere Versionen Ihres Visuals hinzu. | Alle Versionen des Visuals werden korrekt angezeigt und funktionieren ordnungsgemäß. |
| Fügen Sie mehreren Berichtsseiten mehrere Versionen Ihres Visuals hinzu. | Alle Versionen des Visuals werden korrekt angezeigt und funktionieren ordnungsgemäß. |
| Wechseln Sie zwischen Berichtsseiten. | Das Visual wird ordnungsgemäß angezeigt. |
| Testen Sie die Leseansicht und die Bearbeitungsansicht für Ihr Visual. | Alle Funktionen arbeiten ordnungsgemäß. |
| Falls Ihr Visual Animationen verwendet, fügen Sie Ihrem Visual Elemente hinzu, ändern und löschen Sie Elemente. | Die Animation von Visualelementen funktioniert ordnungsgemäß. |
| Öffnen Sie den Bereich **Eigenschaften**. Aktivieren und deaktivieren Sie Eigenschaften, geben Sie benutzerdefinierten Text ein, testen Sie die verfügbaren Optionen, und geben Sie ungültige Daten ein. | Das Visual reagiert ordnungsgemäß. |
| Speichern Sie den Bericht, und öffnen Sie ihn erneut. | Alle Eigenschafteneinstellungen bleiben erhalten. |
| Tauschen Sie Seiten im Bericht aus, und machen Sie den Vorgang rückgängig. | Alle Eigenschafteneinstellungen bleiben erhalten. |
| Testen Sie die sämtliche Funktionen Ihres Visuals, einschließlich der verschiedenen Optionen, die das Visual bereitstellt. | Alle Anzeigen und Features arbeiten ordnungsgemäß. |
| Testen Sie alle numerischen, Datums- und Zeichendatentypen, wie in den folgenden Tests veranschaulicht. | Sämtliche Daten werden ordnungsgemäß formatiert. |
| Überprüfen Sie die Formatierung von QuickInfo-Werten, Achsenbeschriftungen, Datenbeschriftungen und weiteren Visualelementen mit Formatierung. | Alle Elemente werden ordnungsgemäß formatiert. |
| Überprüfen Sie, ob Datenbeschriftungen die Formatzeichenfolge verwenden. | Alle Datenbeschriftungen werden ordnungsgemäß formatiert. |
| Aktivieren und deaktivieren Sie die automatische Formatierung für numerische Werte in QuickInfos. | Die QuickInfos zeigen Werte korrekt an. |
| Testen Sie Dateneinträge mit unterschiedlichen Datentypen, darunter numerische Daten, Text, Datum/Uhrzeit und unterschiedliche Formatzeichenfolgen aus dem Modell. Testen Sie unterschiedliche Datenmengen, z. B. Tausende von Zeilen, eine Zeile und zwei Zeilen. | Alle Anzeigen und Features arbeiten ordnungsgemäß. |
| Geben Sie ungültige Daten in Ihr Visual ein, z. B. NULL, unendliche Werte, negative Werte und falsche Werttypen. | Alle Anzeigen und Features arbeiten ordnungsgemäß. |

## <a name="optional-browser-testing"></a>Optionale Browsertests

Das AppSource-Team prüft ein Visual in den aktuellen Windows-Versionen der Browser Google Chrome, Microsoft Edge und Mozilla Firefox.
Testen Sie Ihr Visual optional in den nachstehend genannten Browsern.

| Testfall | Erwartete Ergebnisse
| --------- | ----------------
| **Windows** |
| Google Chrome (vorherige Version) | Alle Anzeigen und Features arbeiten ordnungsgemäß. |
| Mozilla Firefox (vorherige Version) | Alle Anzeigen und Features arbeiten ordnungsgemäß. |
| Microsoft Edge (vorherige Version) | Alle Anzeigen und Features arbeiten ordnungsgemäß. |
| Microsoft Internet Explorer 11 (optional) | Alle Anzeigen und Features arbeiten ordnungsgemäß. |
| **macOS** |
| Chrome (vorherige Version) | Alle Anzeigen und Features arbeiten ordnungsgemäß. |
| Firefox Chrome (vorherige Version) | Alle Anzeigen und Features arbeiten ordnungsgemäß. |
| Safari (vorherige Version) | Alle Anzeigen und Features arbeiten ordnungsgemäß. |
| **Linux** |
| Firefox (aktuelle und vorherige Version) | Alle Anzeigen und Features arbeiten ordnungsgemäß. |
| **Mobil (iOS)** |
| Apple Safari iPad (vorherige Safari-Version) | Alle Anzeigen und Features arbeiten ordnungsgemäß. |
| Chrome iPad (aktuelle Safari-Version) | Alle Anzeigen und Features arbeiten ordnungsgemäß. |
| **Mobil (Android)** |
| Chrome (aktuelle und vorherige Version) | Alle Anzeigen und Features arbeiten ordnungsgemäß. |

## <a name="desktop-testing"></a>Desktoptests

Testen Sie Ihr Visual in der aktuellen Version von [Power BI Desktop](https://powerbi.microsoft.com/en-us/desktop/).

| Testfall | Erwartete Ergebnisse
| --------- | ----------------
| Testen Sie alle Features Ihres Visuals. | Alle Anzeigen und Features arbeiten ordnungsgemäß. |
| Importieren, speichern und öffnen Sie eine Datei, und veröffentlichen Sie sie mithilfe der Schaltfläche **Veröffentlichen** in Power BI Desktop im Power BI-Webdienst. | Alle Anzeigen und Features arbeiten ordnungsgemäß. |
| Ändern Sie die numerische Formatzeichenfolge, um 0 Dezimalstellen oder 3 Dezimalstellen zu verwenden, indem Sie die Genauigkeit erhöhen oder verringern. | Das Visual wird ordnungsgemäß angezeigt. |

## <a name="performance-testing"></a>Leistungstests

Ihr Visual sollte eine akzeptable Leistung zeigen. Überprüfen Sie mithilfe von Entwicklertools die Leistung Ihres Visuals. Verlassen Sie sich nicht auf visuelle Hinweise und die Zeitprotokolle der Konsole.

| Testfall | Erwartete Ergebnisse
| --------- | ----------------
| Erstellen Sie ein Visual mit vielen visuellen Elementen. | Das Visual sollte eine angemessene Leistung zeigen und darf nicht dazu führen, dass die Anwendung nicht mehr reagiert. Es sollten keine Leistungsprobleme mit Features wie Animationsgeschwindigkeit, Größenänderung, Filterung und Auswahl auftreten.

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zum Veröffentlichungsprozess finden Sie unter [Veröffentlichen von Power BI-Visuals in Partner Center](./office-store.md).

Weitere Fragen? [Fragen an die Power BI-Community](https://community.powerbi.com/)
