---
title: Modellieren von Beziehungen in Power BI Desktop
description: Einführung in die Theorie zum Modellieren von Beziehungen in Power BI Desktop
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 10/15/2019
ms.author: v-pemyer
ms.openlocfilehash: 991f8b47337ba563ecfd223d69d687269a44ed78
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "79041606"
---
# <a name="model-relationships-in-power-bi-desktop"></a>Modellieren von Beziehungen in Power BI Desktop

Dieser Artikel ist an Modellierer von Import-Daten gerichtet, die mit Power BI Desktop arbeiten. Es geht um ein wichtiges Thema beim Entwurf von Modellen, das von essenzieller Bedeutung für die Bereitstellung intuitiver, präziser und optimaler Modelle ist.

Eine ausführlichere Erläuterung zum optimalen Modellentwurf, einschließlich Tabellenrollen und Beziehungen, finden Sie im Artikel [Informationen zum Sternschema und der Wichtigkeit für Power BI](guidance/star-schema.md).

## <a name="relationship-purpose"></a>Zweck von Beziehungen

Einfach gesagt: Power BI-Beziehungen geben Filter, die auf die Spalten von Modelltabellen angewendet wurden, an andere Modelltabellen weiter. Filter werden so lange weitergegeben, wie ein Beziehungspfad verfolgt werden kann, woraus die Weitergabe an mehrere Tabellen resultieren kann.

Beziehungspfade sind deterministisch, d. h., Filter werden immer auf die gleiche Weise und ohne zufällige Variation weitergegeben. Beziehungen können jedoch deaktiviert werden, oder ihr Filterkontext wird durch Modellberechnungen geändert, die bestimmte DAX-Funktionen verwenden. Weitere Informationen finden Sie weiter unten in diesem Artikel im Thema [Relevante DAX-Funktionen](#relevant-dax-functions).

> [!IMPORTANT]
> Es ist wichtig zu verstehen, dass Modellbeziehungen keine Datenintegrität erzwingen. Weitere Informationen finden Sie weiter unten in diesem Artikel im Thema [Beziehungsauswertung](#relationship-evaluation). In diesem Thema wird erläutert, wie sich Modellbeziehungen verhalten, wenn Integritätsprobleme bei Ihren Daten auftreten.

Betrachten wir anhand eines animierten Beispiels, wie Beziehungen Filter weitergeben.

![Animiertes Beispiel der Weitergabe von Filtern durch Beziehungen](media/desktop-relationships-understand/animation-filter-propagation.gif)

In diesem Beispiel besteht das Modell aus vier Tabellen: **Category**, **Product**, **Year** und **Sales**. Die Tabelle **Category** bezieht sich auf die Tabelle **Product** und die Tabelle **Product** auf die **Tabelle** Sales. Die Tabelle **Year** bezieht sich auch auf die Tabelle **Sales**. Alle Beziehungen sind 1:n-Beziehungen (Näheres hierzu erfahren Sie später in diesem Artikel).

Eine – möglicherweise von einem Power BI-Kartenvisual generierte – Abfrage ruft die Gesamtverkaufsmenge für Verkaufsaufträge ab, die für die einzelne Kategorie **Cat-A** und für das einzelne Jahr **CY2018** eingegangen sind. Aus diesem Grund sehen Sie, dass Filter auf die Tabellen **Category** und **Year** angewendet werden. Der Filter für die Tabelle **Category** wird an die Tabelle **Product** weitergegeben, um zwei Produkte der Kategorie **Cat-A** zu isolieren. Anschließend werden die Filter der Tabelle **Product** an die Tabelle **Sales** weitergegeben, um zwei Verkaufszeilen für diese Produkte zu isolieren. Diese zwei Verkaufszeilen stellen die Verkäufe von Produkten der Kategorie **Cat-A** dar. Die kombinierte Menge beträgt 14 Einheiten. Gleichzeitig wird der Filter der Tabelle **Year** weitergegeben, um die Tabelle **Sales** weiter zu filtern. Daraus resultiert nur eine Verkaufszeile für Produkte, die der Kategorie **Cat-A** zugewiesen sind und im Jahr **CY2018** bestellt wurden. Der von der Abfrage zurückgegebene Mengenwert beträgt 11 Einheiten. Beachten Sie Folgendes: Wenn mehrere Filter auf eine Tabelle angewendet werden (wie z. B. auf die Tabelle **Sales** in diesem Beispiel), ist es immer eine AND-Operation, die erfordert, dass alle Bedingungen erfüllt sind.

### <a name="disconnected-tables"></a>Getrennte Tabellen

Es ist ungewöhnlich, dass eine Modelltabelle nicht mit einer anderen Modelltabelle verknüpft ist. Eine solche Tabelle in einem gültigen Modellentwurf kann als _getrennte Tabelle_ bezeichnet werden. Eine getrennte Tabelle ist nicht für die Weitergabe von Filtern an andere Modelltabellen vorgesehen. Stattdessen wird sie verwendet, um „Benutzereingaben“ (möglicherweise mit einem Slicervisual) zu akzeptieren, sodass der Eingabewert auf sinnvolle Weise für Modellberechnungen verwendet werden kann. Stellen Sie sich beispielsweise eine getrennte Tabelle vor, in die ein Bereich von Währungskurswerten geladen wird. Solange ein Filter angewendet wird, um nach einem einzelnen Kurswert zu filtern, kann der Wert von einem Measureausdruck verwendet werden, um Verkaufswerte zu konvertieren.

Der What-if-Parameter von Power BI Desktop ist ein Feature, das eine getrennte Tabelle erstellt. Weitere Informationen finden Sie im Artikel [Erstellen und Verwenden eines Was-wäre-wenn-Parameters zum Visualisieren von Variablen in Power BI Desktop](desktop-what-if.md).

## <a name="relationship-properties"></a>Beziehungseigenschaften

In einer Modellbeziehung ist eine Spalte in einer Tabelle mit einer Spalte in einer anderen Tabelle verknüpft. (Auf einen speziellen Fall trifft diese Anforderung nicht zu, und zwar nur auf mehrspaltige Beziehungen in DirectQuery-Modellen. Weitere Informationen finden Sie im Artikel zur DAX-Funktion [COMBINEVALUES](/dax/combinevalues-function-dax).)

> [!NOTE]
> Es ist nicht möglich, eine Spalte mit einer anderen Spalte _in derselben Tabelle_ zu verknüpfen. Dies wird manchmal mit der Möglichkeit verwechselt, eine Fremdschlüsseleinschränkung für relationale Datenbanken zu definieren, bei der die Tabelle auf sich selbst verweist. Mit diesem Konzept der relationalen Datenbank können Beziehungen zwischen übergeordneten und untergeordneten Elementen gespeichert werden (Beispiel: Jeder Mitarbeiterdatensatz ist mit einem „berichtet an mich“-Mitarbeiter verknüpft). Das auf diesem Beziehungstyp basierende Generieren einer Modellhierarchie kann nicht durch Erstellen von Modellbeziehungen gelöst werden. Informationen hierzu finden Sie im Artikel [Über- und untergeordnete Funktionen](/dax/parent-and-child-functions-dax).

### <a name="cardinality"></a>Kardinalität

Jede Modellbeziehung muss mit einem Kardinalitätstyp definiert werden. Es gibt vier Kardinalitätstypoptionen, die die Dateneigenschaften der „von“- und „zu“-verknüpften Spalten darstellen. Die „Eins“-Seite bedeutet, dass die Spalte eindeutige Werte enthält; die „Zwei“-Seite bedeutet, dass die Spalte doppelte Werte enthalten kann.

> [!NOTE]
> Wenn bei einer Datenaktualisierung versucht wird, doppelte Werte in eine „Eins“-Seiten-Spalte zu laden, wird die gesamte Datenaktualisierung nicht durchgeführt.

Die vier Optionen – und ihre Kurzschreibweisen – werden in der folgenden Aufzählung beschrieben:

- Eins-zu-viele (1:\*)
- Viele-zu-eins (\*:1)
- Eins-zu-eins (1:1)
- Viele-zu-viele (\*:\*)

Wenn Sie in Power BI Desktop eine Beziehung erstellen, erkennt der Designer den Kardinalitätstyp automatisch und legt ihn fest. Der Designer fragt das Modell ab, um zu ermitteln, welche Spalten eindeutige Werte enthalten. Bei Importmodelle verwendet der Designer interne Speicherstatistiken; bei DirectQuery-Modellen sendet er Abfragen zur Profilerstellung an die Datenquelle. Manchmal kann er jedoch daneben liegen. Das kann passieren, wenn Tabellen noch mit Daten geladen werden müssen oder wenn Spalten, von denen Sie erwarten, dass sie doppelte Werte enthalten, derzeit eindeutige Werte enthalten. In beiden Fällen können Sie den Kardinalitätstyp aktualisieren, sofern alle Spalten der 1-Seite eindeutige Werte enthalten (oder noch Datenzeilen in die Tabelle geladen werden müssen).

Die **1:n**- und **n:1**-Kardinalitätsoptionen sind im Wesentlichen identisch und auch die gängigsten Kardinalitätstypen.

Beim Konfigurieren einer 1:n- oder n:1-Beziehung wählen Sie den Wert aus, der der Reihenfolge entspricht, in der Sie die Spalten verknüpft haben. Überlegen Sie, wie Sie die Beziehung zwischen der Tabelle **Product** und der Tabelle **Sales** mithilfe der in beiden Tabellen vorhandenen Spalte **ProductID** konfigurieren würden. Der Kardinalitätstyp wäre _1:n_, da die Spalte **ProductID** in der Tabelle **Product** eindeutige Werte enthält. Wenn Sie die Tabellen in umgekehrter Richtung verknüpfen würden – **Sales** zu **Product** – wäre die Kardinalität _n:1_.

Eine **1:1**-Beziehung bedeutet, dass beide Spalten eindeutige Werte enthalten. Dieser Kardinalitätstyp ist nicht gängig und weist aufgrund der Speicherung redundanter Daten eher auf einen suboptimalen Modellentwurf hin. Weitere Informationen zur Verwendung dieses Kardinalitätstyps finden Sie im [Leitfaden zu 1:1-Beziehungen](guidance/relationships-one-to-one.md).

Eine **m:n**-Beziehung bedeutet, dass beide Spalten doppelte Werte enthalten können. Dieser Kardinalitätstyp wird selten verwendet. Er ist in der Regel nützlich, wenn komplexe Modellanforderungen entworfen werden. Hinweise zur Verwendung dieses Kardinalitätstyps finden Sie unter [Leitfaden zu m:n-Beziehungen](guidance/relationships-many-to-many.md).

> [!NOTE]
> Der m:n-Kardinalitätstyp wird für Modelle, die für den Power BI-Berichtsserver entwickelt werden, derzeit nicht unterstützt.

> [!TIP]
> In der Power BI Desktop-Modellansicht können Sie den Kardinalitätstyp einer Beziehung interpretieren, indem Sie sich die Indikatoren (1 oder \*) auf beiden Seiten der Beziehungslinie ansehen. Um zu ermitteln, welche Spalten verknüpft sind, müssen Sie die Beziehungslinie auswählen (oder den Cursor darüber bewegen), um die Spalten hervorzuheben.

### <a name="cross-filter-direction"></a>Kreuzfilterrichtung

Jede Modellbeziehung muss mit einer Kreuzfilterrichtung definiert werden. Ihre Auswahl bestimmt die Richtung(en), in der/die Filter weitergegeben werden. Die möglichen Kreuzfilteroptionen sind vom Kardinalitätstyp abhängig.

| Kardinalitätstyp | Kreuzfilteroptionen |
| --- | --- |
| 1:n (oder n:1) | Einfach<br>Beide |
| 1:1 | Beide |
| M:n | Einzeln (Tabelle1 zu Tabelle2)<br>Einzeln (Tabelle2 zu Tabelle1)<br>Beide |

_Einzelne_ Kreuzfilterrichtung bedeutet „einzelne Richtung“ und _Beide_ bedeutet „beide Richtungen“. Eine Beziehung, die in beide Richtungen filtert, wird häufig als _bidirektional_ beschrieben.

Bei 1:n-Beziehungen verläuft die Kreuzfilterrichtung immer von der „Eins“-Seite und optional von der „Viele“-Seite (bidirektional). Bei 1:1-Beziehungen verläuft die Kreuzfilterrichtung immer von beiden Tabellen. Schließlich kann bei m:n-Beziehungen die Kreuzfilterrichtung von einer der Tabellen oder von beiden verlaufen. Beachten Sie: Wenn der Kardinalitätstyp eine „Eins“-Seite enthält, werden Filter immer von dieser Seite weitergegeben.

Wenn die Kreuzfilterrichtung auf **Beide** festgelegt ist, steht eine weitere Eigenschaft zur Verfügung. Diese kann eine bidirektionale Filterung anwenden, wenn Sicherheitsregeln auf Zeilenebene erzwungen werden. Weitere Informationen zur Sicherheit auf Zeilenebene finden Sie im Artikel [Einschränken des Datenzugriffs mit Sicherheit auf Zeilenebene (RLS) für Power BI Desktop](desktop-rls.md).

Die Kreuzfilterrichtung der Beziehung – einschließlich Deaktivierung der Filterweitergabe – kann auch durch eine Modellberechnung geändert werden. Hierzu wird die DAX-Funktion [CROSSFILTER](/dax/crossfilter-function) verwendet.

Bidirektionale Beziehungen können sich negativ auf die Leistung auswirken. Außerdem kann der Versuch, eine bidirektionale Beziehung zu konfigurieren, zu mehrdeutigen Filterweitergabe-Pfaden führen. In diesem Fall kann Power BI Desktop die Beziehungsänderung möglicherweise nicht committen, sodass Sie eine Fehlermeldung erhalten. Manchmal kann Power BI Desktop Ihnen jedoch ermöglichen, mehrdeutige Beziehungspfade zwischen Tabellen zu definieren. Rangfolgeregeln, die sich auf die Erkennung von Mehrdeutigkeiten und Pfadauflösung auswirken, werden weiter unten in diesem Artikel im Thema [Rangfolgeregeln](#precedence-rules) beschrieben.

Sie sollten die bidirektionale Filterung nur bei Bedarf verwenden. Weitere Informationen finden Sie im [Leitfaden zu bidirektionalen Beziehungen](guidance/relationships-bidirectional-filtering.md).

> [!TIP]
> In der Power BI Desktop-Modellansicht können Sie die Kreuzfilterrichtung einer Beziehung anhand der entlang der Beziehungslinie verlaufenden Pfeilspitze(n) interpretieren. Eine einzelne Pfeilspitze stellt einen in Richtung der Pfeilspitze verlaufenden Einzelrichtungsfilter dar; eine doppelte Pfeilspitze stellt eine bidirektionale Beziehung dar.

### <a name="make-this-relationship-active"></a>Diese Beziehung aktivieren

Zwischen zwei Modelltabellen kann nur ein einziger aktiver Filterweitergabe-Pfad vorhanden sein. Es ist jedoch möglich, zusätzliche Beziehungspfade einzuführen, obwohl alle diese Beziehungen als _inaktiv_ konfiguriert werden müssen. Inaktive Beziehungen können nur während der Auswertung einer Modellberechnung aktiviert werden. Hierzu wird die DAX-Funktion [USERELATIONSHIP](/dax/userelationship-function-dax) verwendet.

Weitere Informationen finden Sie unter [Aktive und inaktive Beziehungen im Vergleich – Leitfaden](guidance/relationships-active-inactive.md).

> [!TIP]
> In der Power BI Desktop-Modellansicht können Sie den aktiven oder inaktiven Status einer Beziehung interpretieren. Eine aktive Beziehung wird als durchgezogene Linie dargestellt, eine inaktive Beziehung als gestrichelte Linie.

### <a name="assume-referential-integrity"></a>Referenzielle Integrität voraussetzen

Die Eigenschaft _Referenzielle Integrität voraussetzen_ ist nur für 1:n- und 1:1-Beziehungen zwischen zwei DirectQuery-Speichermodustabellen verfügbar, die auf derselben Datenquelle basieren. Wenn sie aktiviert ist, werden die beiden Tabellen von nativen Abfragen, die an die Datenquelle gesendet werden, mit einem INNER JOIN statt eines OUTER JOIN verknüpft. Die Abfrageleistung wird mit Aktivierung dieser Eigenschaft somit generell verbessert, obwohl dies von den Besonderheiten der Datenquelle abhängt.

Aktivieren Sie diese Eigenschaft immer, wenn zwischen den beiden Tabellen eine Fremdschlüsseleinschränkung für Datenbanken vorhanden ist. Wenn keine Fremdschlüsseleinschränkung vorhanden ist, können Sie die Eigenschaft dennoch aktivieren, sofern Sie sicher sind, dass die Datenintegrität gegeben ist.

> [!IMPORTANT]
> Sollte die Datenintegrität kompromittiert werden, eliminiert der INNER JOIN nicht übereinstimmende Zeilen zwischen den Tabellen. Stellen Sie sich beispielsweise eine Modell-**Sales**-Tabelle mit einem **ProductID**-Spaltenwert vor, der in der verknüpften **Product**-Tabelle nicht vorhanden ist. Die Filterweitergabe von der **Product**-Tabelle zur **Sales**-Tabelle eliminiert die Verkaufszeilen für unbekannte Produkte. Dies würde dazu führen, dass die Verkaufsergebnisse zu niedrig angegeben werden.
>
> Weitere Informationen finden Sie im Artikel [Anwenden der Einstellung „Referenzielle Integrität voraussetzen“ in Power BI Desktop](desktop-assume-referential-integrity.md).

## <a name="relevant-dax-functions"></a>Relevante DAX-Funktionen

Es gibt mehrere DAX-Funktionen, die für Modellbeziehungen relevant sind. Jede Funktion wird in der folgenden Aufzählung kurz beschrieben:

- [RELATED](/dax/related-function-dax): Ruft den Wert von der „Eins“-Seite ab.
- [RELATEDTABLE](/dax/relatedtable-function-dax): Ruft eine Tabelle mit Zeilen von der „Viele“-Seite ab.
- [USERELATIONSHIP](/dax/userelationship-function-dax): Erzwingt die Verwendung einer bestimmten inaktiven Modellbeziehung.
- [CROSSFILTER](/dax/crossfilter-function): Ändert die Kreuzfilterrichtung der Beziehung (in „einzeln“ oder „beide“) oder deaktiviert die Filterweitergabe (keine).
- [COMBINEVALUES](/dax/combinevalues-function-dax): Verbindet zwei oder mehr Textzeichenfolgen zu einer einzigen Textzeichenfolge. Zweck dieser Funktion ist die Unterstützung mehrspaltiger Beziehungen in DirectQuery-Modellen.
- [TREATAS](/dax/treatas-function): Wendet das Ergebnis eines Tabellenausdrucks als Filter auf Spalten aus einer nicht verknüpften Tabelle an
- [Übergeordnete und untergeordnete Funktionen](/dax/parent-and-child-functions-dax): Eine Familie verwandter Funktionen, mit denen berechnete Spalten generiert werden können, um eine Über-/Unterordnungshierarchie zu etablieren. Diese Spalten können dann zum Erstellen einer Hierarchie auf fester Ebene verwendet werden.

## <a name="relationship-evaluation"></a>Beziehungsauswertung

Modellbeziehungen werden aus der Perspektive der Auswertung entweder als _stark_ oder _schwach_ klassifiziert. Es handelt sich nicht um eine konfigurierbare Beziehungseigenschaft. Sie wird tatsächlich vom Kardinalitätstyp und der Datenquelle der beiden verknüpften Tabellen abgeleitet. Es ist wichtig, den Auswertungstyp zu verstehen, da eine Kompromittierung der Datenintegrität Auswirkungen auf die Leistung oder sonstige Konsequenzen haben könnte. Diese Auswirkungen und die Konsequenzen für die Integrität werden in diesem Thema beschrieben.

Zuerst ist eine Modellierungstheorie erforderlich, um Beziehungsauswertungen vollständig verstehen zu können.

Ein Import- oder DirectQuery-Modell bezieht sämtliche Daten entweder aus dem Vertipaq-Cache oder der Quelldatenbank. In beiden Fällen kann Power BI bestimmen, ob die „Eins“-Seite einer Beziehung vorhanden ist.

Ein zusammengesetztes Modell kann jedoch Tabellen enthalten, die unterschiedliche Speichermodi (Import, DirectQuery oder Dual) bzw. mehrere DirectQuery-Quellen verwenden. Jede Quelle, einschließlich des Vertipaq-Caches der Import-Daten, wird als _Dateninsel_ betrachtet. Modellbeziehungen können dann als _inselintern_ oder _inselübergreifend_ klassifiziert werden. Eine inselinterne Beziehung ist eine Beziehung zwischen zwei Tabellen innerhalb einer Dateninsel, während in einer inselübergreifenden Beziehung Tabellen aus verschiedenen Dateninseln miteinander verknüpft sind. Beachten Sie, dass Beziehungen in Import- oder DirectQuery-Modell immer inselintern sind.

Wir betrachten nun ein Beispiel für ein zusammengesetztes Modell.

![Beispiel für ein zusammengesetztes Modell, das aus zwei Inseln besteht](media/desktop-relationships-understand/data-island-example.png)

In diesem Beispiel besteht das zusammengesetzte Modell aus zwei Inseln: einer Vertipaq-Dateninsel und einer DirectQuery-Quelldateninsel. Die Vertipaq-Dateninsel enthält drei Tabellen, und die DirectQuery-Quelldateninsel enthält zwei Tabellen. Eine inselübergreifende Beziehung hat den Zweck, eine Tabelle in der Vertipaq-Dateninsel mit einer Tabelle in der DirectQuery-Quelldateninsel zu verknüpfen.

### <a name="strong-relationships"></a>Starke Beziehungen

Eine Modellbeziehung ist _stark_, wenn die Abfrage-Engine die „Eins“-Seite der Beziehung bestimmen kann. Sie hat die Bestätigung, dass die Spalte der „Eins“-Seite eindeutige Werte enthält. Alle inselinternen 1:n-Beziehungen sind starke Beziehungen.

Im folgenden Beispiel gibt es zwei starke Beziehungen, die beide mit **S** gekennzeichnet sind. Zu den Beziehungen gehören die 1:n-Beziehung, die sich auf der Vertipaq-Insel befindet, und die 1:n-Beziehung, die in der DirectQuery-Quelle enthalten ist.

![Beispiel für ein zusammengesetztes Modell, das aus zwei Inseln besteht, mit gekennzeichneten starken Beziehungen](media/desktop-relationships-understand/data-island-example-strong.png)

Für Import-Modelle, bei denen alle Daten im Vertipaq-Cache gespeichert werden, wird für jede starke Beziehung zum Zeitpunkt der Datenaktualisierung eine Datenstruktur erstellt. Die Datenstrukturen bestehen aus indizierten Zuordnungen aller „Spalte-zu-Spalte“-Werte, und sie sollen das Verknüpfen von Tabellen zur Abfragezeit beschleunigen.

Zur Abfragezeit ermöglichen starke Beziehungen eine _Tabellenerweiterung_. Die Tabellenerweiterung führt zum Erstellen einer virtuellen Tabelle, indem die nativen Spalten der Basistabelle einbezogen und dann in verknüpfte Tabellen erweitert werden. Für Import-Tabellen erfolgt dies in der Abfrage-Engine, für DirectQuery-Tabellen in der nativen Abfrage, die an die Quelldatenbank gesendet wird (sofern die Eigenschaft **Referenzielle Integrität voraussetzen** nicht aktiviert ist). Die Abfrage-Engine bearbeitet dann die erweiterte Tabelle, wendet Filter an und führt eine Gruppierung nach den Werten in den Spalten der erweiterten Tabelle durch.

> [!NOTE]
> Inaktive Beziehungen werden ebenfalls erweitert, auch wenn die Beziehung nicht von einer Berechnung verwendet wird. Bidirektionale Beziehungen haben keine Auswirkung auf die Tabellenerweiterung.

Bei 1:n-Beziehungen erfolgt die Tabellenerweiterung von der n- zur 1-Seite mithilfe der LEFT OUTER JOIN-Semantik. Wenn kein übereinstimmender Wert in der „Viele“- und „Eins“-Seite vorhanden ist, wird der „Eins“-Seiten-Tabelle eine leere virtuelle Zeile hinzugefügt.

Die Tabellenerweiterung wird auch für inselinterne 1:1-Beziehungen durchgeführt, jedoch mithilfe der FULL OUTER JOIN-Semantik. Dadurch wird ggf. sichergestellt, dass jeder Seite leere virtuelle Zeilen hinzugefügt werden.

Die leeren virtuellen Zeilen sind eigentlich _unbekannte Elemente_. Unbekannte Elemente stellen Verstöße gegen die referenzielle Integrität dar, wobei für den Wert der „Viele“-Seite kein entsprechender „Eins“-Seiten-Wert vorhanden ist. Im Idealfall sollten diese leeren Zeilen nicht vorhanden sein, und sie können durch Bereinigung oder Reparatur der Quelldaten entfernt werden.

Wir betrachten nun anhand eines animierten Beispiels, wie die Tabellenerweiterung funktioniert.

![Animiertes Beispiel der Tabellenerweiterung](media/desktop-relationships-understand/animation-expanded-table.gif)

In diesem Beispiel besteht das Modell aus drei Tabellen: **Category**, **Product** und **Year**. Die Tabelle **Category** ist mit einer 1:n-Beziehung mit der Tabelle **Product** verknüpft, und die Tabelle **Product** ist mit einer 1:n-Beziehung mit der Tabelle **Sales** verknüpft. Die Tabelle **Category** enthält zwei Zeilen, die Tabelle **Product** drei Zeilen und die Tabelle **Sales** fünf Zeilen. Es gibt auf beiden Seiten aller Beziehungen übereinstimmende Werte, was bedeutet, dass keine Verletzungen der referenziellen Integrität vorliegen. Eine erweiterte Tabelle zur Abfragezeit wird angezeigt. Die Tabelle besteht aus den Spalten aller drei Tabellen. Es handelt sich tatsächlich um eine denormalisierte Perspektive der in den drei Tabellen enthaltenen Daten. Der **Sales**-Tabelle wird eine neue Zeile hinzugefügt, und sie verfügt über einen Produktionsbezeichnerwert (9), für den es keine Übereinstimmung in der **Product**-Tabelle gibt. Dies ist ein Verstoß gegen die referenzielle Integrität. In der erweiterten Tabelle enthält die neue Zeile (leere) Werte für die Tabellenspalten **Category** und **Product**.

### <a name="weak-relationships"></a>Schwache Beziehungen

Eine Modellbeziehung ist _schwach_, wenn keine garantierte „Eins“-Seite vorhanden ist. Dies kann aus zwei Gründen der Fall sein:

- In der Beziehung wird ein m:n-Kardinalitätstyp verwendet (auch wenn eine oder beide Spalten eindeutige Werte enthalten)
- Die Beziehung ist inselübergreifend (was nur bei zusammengesetzten Modellen der Fall sein kann)

Im folgenden Beispiel gibt es zwei schwache Beziehungen, die beide mit **W** gekennzeichnet sind. Die beiden Beziehungen sind die m:n-Beziehung, die sich auf der Vertipaq-Insel befindet, und die inselübergreifende 1:n-Beziehung.

![Beispiel für ein zusammengesetztes Modell, das aus zwei Inseln besteht, mit gekennzeichneten schwachen Beziehungen](media/desktop-relationships-understand/data-island-example-weak.png)

Bei Import-Modellen werden nie Datenstrukturen für schwache Beziehungen erstellt. Dies bedeutet, dass Tabellenverknüpfungen zur Abfragezeit aufgelöst werden müssen.

Tabellenerweiterungen werden nie für schwache Beziehungen durchgeführt. Tabellenverknüpfungen werden mithilfe der INNER JOIN-Semantik erzielt. Aus diesem Grund werden keine leeren virtuellen Zeilen hinzugefügt, um Verletzungen der referenziellen Integrität zu kompensieren.

Es gibt zusätzliche Einschränkungen in Bezug auf schwache Beziehungen:

- Die Spaltenwerte der „Eins“-Seite können nicht mit der DAX-Funktion RELATED abgerufen werden.
- Topologieeinschränkungen beim Erzwingen von RLS

> [!NOTE]
> In der Modellansicht von Power BI Desktop kann nicht immer bestimmt werden, ob eine Modellbeziehung stark oder schwach ist. Eine m:n-Beziehung ist immer schwach, genauso wie eine 1:n-Beziehung, wenn sie eine inselübergreifende Beziehung ist. Um zu ermitteln, ob eine inselübergreifende Beziehung vorliegt, müssen Sie die Tabellenspeichermodi und Datenquellen überprüfen.

### <a name="precedence-rules"></a>Rangfolgeregeln

Bidirektionale Beziehungen können mehrere – und somit mehrdeutige – Filterweitergabepfade zwischen Modelltabellen mit sich bringen. In der folgenden Liste sind Rangfolgeregeln aufgeführt, die Power BI für Mehrdeutigkeitserkennung und Pfadauflösung verwendet:

1. N:1- und 1:1-Beziehungen, einschließlich schwacher Beziehungen
2. M:n-Beziehungen
3. Bidirektionale Beziehungen in umgekehrter Richtung (d. h. von der „Viele“-Seite)

### <a name="performance-preference"></a>Leistungspräferenz

In der folgenden Liste sind die Beziehungen nach ihrer Filterweitergabe-Leistung von der höchsten bis zur niedrigsten sortiert:

1. Inselinterne 1:n-Beziehungen
2. M:n-Kardinalitätsbeziehungen
3. M:n-Modellbeziehungen, die mit einer Zwischentabelle erzielt werden und mindestens eine bidirektionale Beziehung beinhalten
4. Inselübergreifende Beziehungen

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zu diesem Artikel finden Sie in den folgenden Ressourcen:

- [Informationen zum Sternschema und dessen Wichtigkeit für Power BI](guidance/star-schema.md)
- [Leitfaden zu 1:1-Beziehungen](guidance/relationships-one-to-one.md)
- [Leitfaden zu m:n-Beziehungen](guidance/relationships-many-to-many.md)
- [Aktive und inaktive Beziehungen im Vergleich – Leitfaden](guidance/relationships-active-inactive.md)
- [Leitfaden zu bidirektionalen Beziehungen](guidance/relationships-bidirectional-filtering.md)
- [Leitfaden zur Problembehandlung bei Beziehungen](guidance/relationships-troubleshoot.md)
- Video: [Worauf Sie bei Power BI-Beziehungen achten sollten](https://www.youtube.com/watch?v=78d6mwR8GtA)
- Haben Sie Fragen? [Stellen Sie Ihre Frage in der Power BI-Community.](https://community.powerbi.com/)
- Vorschläge? [Einbringen von Ideen zur Verbesserung von Power BI](https://ideas.powerbi.com/)
