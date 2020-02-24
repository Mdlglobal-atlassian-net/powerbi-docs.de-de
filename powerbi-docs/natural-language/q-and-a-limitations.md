---
title: Einschränkungen von Power BI Q&A
description: Aktuelle Einschränkungen von Power BI Q&A
author: mohaali
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 10/18/2019
ms.author: mohaali
ms.openlocfilehash: 9f1beed3408d53a58a0fb725f9d98a4a95bb1b7c
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/09/2019
ms.locfileid: "73874903"
---
# <a name="limitations-of-power-bi-qa"></a>Einschränkungen von Power BI Q&A

Power BI Q&A weist zurzeit einige Einschränkungen auf.

## <a name="data-sources"></a>Datenquellen

### <a name="supported-data-sources"></a>Unterstützte Datenquellen

Power BI Q&A unterstützt die folgenden Konfigurationen von Datenquellen im Power BI-Dienst:

- Import-Modus
- Liveverbindungen mit Analysis Services
- Liveverbindungen mit SQL Server-Analysis Services (mit einem Gateway)
- Power BI-Datasets. Power BI Desktop meldet einen Fehler bei Q&A, wenn ein Power BI DataSet verwendet wird. Wenn der Bericht im Power BI-Dienst veröffentlicht wird, verschwindet der Fehler jedoch.

In jeder dieser Konfigurationen wird außerdem Sicherheit auf Zeilenebene unterstützt.

### <a name="data-sources-not-supported"></a>Nicht unterstützte Datenquellen

Power BI Q&A unterstützt derzeit die folgenden Konfigurationen nicht:

- Sicherheit auf Objektebene mit beliebigen Datenquellentypen
- DirectQuery für beliebige Quellen. Eine Problemumgehung, um Unterstützung zu realisieren, besteht im Verwenden von Liveverbindungen mit Azure Analysis Services, die DirectQuery verwenden.
- Zusammengesetzte Modelle
- Reporting Services 

## <a name="tooling-limitations"></a>Tooleinschränkungen

Das neue Tooldialogfeld ermöglicht es Benutzern, die natürliche Sprache in Q&A anzupassen und zu verbessern. Weitere Informationen zu Tools finden Sie in der [Einführung in Q&A-Tools](q-and-a-tooling-intro.md).

## <a name="review-question-limitations"></a>Einschränkungen bei den Fragen zur Überprüfung

Die Fragen zur Überprüfung speichern Fragen, die an Ihr Datenmodell gestellt wurden, nur 28 Tage lang. Beim Verwenden der neuen Funktion für Fragen zur Überprüfung stellen Sie möglicherweise fest, dass einige Fragen nicht aufgezeichnet werden. Dies ist beabsichtigt, da die Engine für die Verarbeitung von natürlicher Sprache eine Reihe von Bereinigungsschritten der Daten ausführt, um sicherzustellen, dass nicht jeder Tastendruck eines Benutzers aufgezeichnet oder angezeigt wird.

Mandantenadministratoren können die Administratoreinstellungen des Mandanten verwenden, um die Fähigkeit zum Speichern von Fragen zu verwalten. Berechtigungen basieren auf Sicherheitsgruppen. 

Außerdem können Benutzer die Aufzeichnung ihrer Fragen verhindern, indem sie **Einstellungen** > **Allgemein** auswählen und **Allow Q&A to record my utterance** (Q&A das Aufzeichnen meiner Äußerung erlauben) deaktivieren. 

## <a name="teach-qa-limitations"></a>Einschränkungen für Q&A-Training

Q&A-Training ermöglicht Ihnen die Behebung zweier Typen von Fehlern:

- Zuweisen eines Worts zu einem Feld
- Zuweisen eines Worts zu einer Filterbedingung

Aktuell unterstützen wir die Neudefinition eines erkannten Ausdrucks oder das Definieren anderer Typen von Bedingungen oder Formulierungen nicht. Darüber hinaus kann beim Definieren von Filterbedingungen nur eine eingeschränkte Teilmenge der Sprache verwendet werden, darunter:

- „Land/Region“ mit dem Wert „USA“
- „Land/Region“ mit einem anderen Wert als „USA“
- „Gewicht“ > 2000
- „Gewicht“ = 2000
- „Gewicht“ < 2000

> [!NOTE]
> Q&A-Tools unterstützen nur den Importmodus. Q&A bietet bisher noch keine Unterstützung für die Verbindung mit einer lokalen oder Azure Analysis Services-Datenquelle. Diese aktuelle Einschränkung wird in zukünftigen Versionen von Power BI entfallen.

### <a name="statements-not-supported"></a>Nicht unterstütze Anweisungen

- Die Verwendung von Measures in Bedingungen wird aktuell nicht unterstützt. Konvertieren Sie Measures stattdessen in berechnete Spalten um, damit sie funktionieren.
- Mehrere Bedingungen werden nicht unterstützt. Erstellen Sie als Problemumgehung eine berechnete DAX-Spalte, die eine Anweisung mit mehreren Bedingungen zu einem Booleschen Wert auswertet, und verwenden Sie stattdessen dieses Feld.
- Wenn Sie keine Filterbedingung angeben, wenn Q&A zur Angabe einer Teilmenge der Daten auffordert, können Sie die Definition nicht speichern, auch dann nicht, wenn die gesamte Anweisung keine roten Unterstreichungen aufweist.
