---
title: Troubleshooting von Unterberichten in paginierten Power BI-Berichten
description: In diesem Artikel erfahren Sie mehr über unterstützte Datenquellen für paginierte Berichte im Power BI-Dienst und dazu, wie Sie eine Verbindung zu Datenquellen der Azure SQL-Datenbank herstellen.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.date: 04/29/2020
ms.openlocfilehash: 6de85f6dda69e902a98d6ee63d1fc4b86fb4180b
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "82615632"
---
# <a name="troubleshoot-subreports-in-power-bi-paginated-reports"></a>Troubleshooting von Unterberichten in paginierten Power BI-Berichten

Wenn Sie Unterberichte in paginierten Berichten verwenden, kann es gelegentlich vorkommen, dass Sie ein unerwartetes Ergebnis erhalten oder dass eine Funktion nicht wie erwartet funktioniert. Dieser Artikel enthält Lösungen für häufige Probleme bei der Verwendung von Unterberichten. Ein *Unterbericht* ist ein Berichtselement, das einen anderen Bericht innerhalb des Hauptteils eines paginierten Hauptberichts anzeigt. Weitere Informationen hierzu finden Sie unter [Troubleshooting von Unterberichten in paginierten Power BI-Berichten](subreports.md).

## <a name="subreport-couldnt-be-found"></a>Unterbericht wurde nicht gefunden

**Beschreibung:** Der Unterbericht wird nicht gerendert. Stattdessen wird eine Fehlermeldung angezeigt.

### <a name="message"></a>Nachricht

„Der Unterbericht "Unterbericht1" wurde am angegebenen Speicherort "Kundendetails" nicht gefunden. Stellen Sie sicher, dass der Unterbericht veröffentlicht wurde und dass der Name korrekt ist.“

### <a name="possible-reasons"></a>Mögliche Ursachen

- Es gibt in dem Arbeitsbereich oder in der App, in dem oder der sich der Hauptbericht befindet, keinen Unterbericht mit dem angegebenen Namen.
- Der Benutzer hat keinen Zugriff auf den Unterbericht.
- Die Anzahl der Unterberichte im Hauptbericht hat den Grenzwert für Unterberichte (50 Unterberichte) erreicht.

### <a name="troubleshooting-steps"></a>Schritte zur Problembehandlung

**In einem Arbeitsbereich**

- Überprüfen Sie, ob der Bericht mit dem in der Fehlermeldung aufgeführten Namen vorhanden ist. Für den Namen wird die Groß-/Kleinschreibung nicht beachtet.

**In einer App**

- Überprüfen Sie, ob der Bericht mit dem in der Fehlermeldung aufgeführten Namen in der App vorhanden ist. Wenden Sie sich an den Autor der App, um weitere Hilfe zu erhalten.

**Wenn der Bericht freigegeben ist**

1. Überprüfen Sie, ob der Bericht mit dem in der Fehlermeldung aufgeführten Namen für Sie freigegeben ist.
2. Wenn der Bericht vorhanden ist, überprüfen Sie, ob der Besitzername für den Hauptbericht und den Unterbericht identisch ist. Wenden Sie sich dann mit diesen Informationen an den Besitzer des Hauptberichts.

## <a name="subreport-renders-with-unexpected-content"></a>Unterbericht wird mit unerwartetem Inhalt gerendert

### <a name="possible-reason"></a>Mögliche Ursache

Power BI ermöglicht es Benutzern, mehrere Berichte mit demselben Namen im selben Arbeitsbereich zu haben.

### <a name="troubleshooting-steps-for-report-authors"></a>Troubleshootingschritte (für Berichtsautoren)

1. Öffnen Sie den Hauptbericht in Power BI Report Builder, und legen Sie den Namen des Unterberichts fest.
2. Suchen Sie im Arbeitsbereich nach Berichten mit demselben Namen.
3. Suchen Sie nach dem erwarteten Bericht, und benennen Sie die anderen Berichte um.

**Für Nicht-Autoren:** Wenden Sie sich an den Autor.

## <a name="data-retrieval-fails"></a>Fehler beim Datenabruf

**Beschreibung:** Beim Rendern des Unterberichts tritt beim Datenabruf ein Fehler auf. Der Unterbericht wird nicht gerendert. Stattdessen wird eine Fehlermeldung angezeigt.

### <a name="message"></a>Nachricht

„Fehler beim Datenabruf für den Unterbericht "Unterbericht1" in "Rechnungsdetails". Weitere Informationen finden Sie in den Protokolldateien.“

### <a name="troubleshooting-steps"></a>Schritte zur Problembehandlung

Identisch mit den allgemeinen Troubleshootingschritten für Berichte mit Datenzugriffsproblemen.

## <a name="rendering-fails-unspecified-parameters"></a>Fehler beim Rendern: nicht angegebene Parameter

**Beschreibung:** Der Unterbericht kann nicht gerendert werden, weil Parameter nicht angegeben sind. Der Unterbericht hat obligatorische Parameter, aber der Hauptbericht legt diese nicht alle fest.

### <a name="message"></a>Nachricht 
„Mindestens ein Parameter wurde für den Unterbericht "Unterbericht1" in "UnterberichtAMitDS" nicht angegeben.“

### <a name="troubleshooting-steps-for-the-report-author"></a>Troubleshootingschritte (für den Berichtsautor)

1. Öffnen Sie den Hauptbericht in Power BI Report Builder.
2. Öffnen Sie den Unterbericht in Power BI Report Builder.
3. Vergewissern Sie sich, dass der Parametersatz, der im Unterbericht-Berichtselement im Hauptbericht angezeigt wird, mit dem Satz von Parametern im Unterbericht übereinstimmt.

**Für Nicht-Autoren:** Wenden Sie sich an den Autor.

## <a name="rendering-fails-recursion-limit"></a>Fehler beim Rendern: Rekursionslimit

**Beschreibung:** Der Unterbericht kann nicht gerendert werden, weil das Rekursionslimit erreicht ist. Unterberichte können nicht tiefer als 20 Ebenen geschachtelt werden.

### <a name="message"></a>Nachricht

„Der Bericht oder Unterbericht hat einen rekursiven Unterbericht "Unterbericht1", der das maximal zulässige Rekursionslimit überschritten hat.“

### <a name="troubleshooting-steps-for-report-authors"></a>Troubleshootingschritte (für Berichtsautoren)

- Verringern Sie die Schachtelung.
- Gestalten Sie die Berichtsstruktur neu.

## <a name="other-errors"></a>Sonstige Fehler

**Beschreibung:** Der Fehler gehört zu keiner der vorherigen Kategorien.

### <a name="message"></a>Nachricht

„Fehler: Der Unterbericht konnte nicht angezeigt werden.“

### <a name="possible-reasons"></a>Mögliche Ursachen

- Beim Rendern des Unterberichts sind mehrere Fehler aufgetreten, z. B. Parameterabweichungs- und Datenabrufprobleme.
- Unerwartete Fehler.

### <a name="troubleshooting-steps-for-report-authors"></a>Troubleshootingschritte (für Berichtsautoren)

1. Überprüfen Sie, ob der Unterbericht direkt gerendert werden kann.
2. Wenn der Unterbericht gerendert werden kann, überprüfen Sie die Parameter sowohl im Unterbericht als auch im Hauptbericht.
3. Stellen Sie sicher, dass der Hauptbericht nicht mehr als 50 eindeutige Unterberichte hat, und dass der Unterbericht nicht tiefer als 20 Ebenen geschachtelt ist.
4. Wenn Sie das Problem nicht beheben können, wenden Sie sich an Power BI-Support.

**Für Nicht-Autoren:** Wenden Sie sich an den Autor.

## <a name="next-steps"></a>Nächste Schritte

[Unterberichte in paginierten Power BI-Berichten](subreports.md)

[Anzeigen eines paginierten Berichts im Power BI-Dienst](../consumer/paginated-reports-view-power-bi-service.md)

Weitere Fragen? [Wenden Sie sich an die Power BI-Community](https://community.powerbi.com/)
