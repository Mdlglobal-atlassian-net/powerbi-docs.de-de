---
title: Multi-Geo-Unterstützung für Power BI Premium
description: In diesem Artikel erfahren Sie, wie Sie Inhalte für Rechenzentren in anderen Regionen als der ursprünglichen Region des Power BI-Mandanten bereitstellen können.
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 02/05/2019
LocalizationGroup: Premium
ms.openlocfilehash: 4b30e2fbf4ec3607b3ee155749a1ddeeb9f76cad
ms.sourcegitcommit: 075a0ade4134d28f578fda78996595e8cd9f3555
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80147352"
---
# <a name="configure-multi-geo-support-for-power-bi-premium"></a>Konfigurieren von Multi-Geo-Unterstützung für Power BI Premium

Multi-Geo ist ein Power BI Premium-Feature, das multinationale Kunden bei der Erfüllung von regionalen, branchenspezifischen oder organisationsbezogenen Data Residency-Anforderungen unterstützt. Als Power BI Premium-Kunde können Sie Inhalte für Rechenzentren in anderen Regionen als der ursprünglichen Region des Power BI-Mandanten bereitstellen. Eine geografische Region (Geografie) kann mehr als eine Region umfassen. Die USA sind z.B. eine geografische Region und „USA, Westen-Mitte“ und „USA, Süden-Mitte“ Regionen innerhalb der USA. Außerdem können Sie Inhalte für eine der folgenden geografischen Regionen bereitstellen:

- USA
- Kanada
- Vereinigtes Königreich
- Brasilien
- Europa
- Japan
- Indien
- Asien-Pazifik
- Australien
- Afrika

Multi-Geo ist nicht für Power BI Deutschland, Power BI China (betrieben von 21Vianet) oder Power BI für die US-Regierung verfügbar.

Multi-Geo steht ab sofort auch in Power BI Embedded zur Verfügung. Weitere Informationen finden Sie unter [Multi-Geo-Unterstützung in Power BI Embedded](developer/embedded/embedded-multi-geo.md).

## <a name="enable-and-configure"></a>Aktivieren und konfigurieren

Aktivieren Sie für die Verwendung der neuen Funktionen Multi-Geo, indem Sie eine andere Region als die Standardregion aus der Dropdownliste auswählen.  Jede verfügbare Kapazität zeigt die Region an, in der sie sich zurzeit befindet, z.B. **USA, Westen-Mitte**.

![Auswählen einer Region auf der Seite „Kapazitätsumfang“ Power BI Multi-Geo](media/service-admin-premium-multi-geo/power-bi-multi-geo-capacity-size.png)

Nachdem Sie die Kapazität erstellt haben, verbleibt sie in dieser Region und die Inhalte aller erstellten Arbeitsbereiche werden in dieser Region gespeichert. Auf der Seite mit den Arbeitsbereichseinstellungen können Sie über die Dropdownliste Arbeitsbereiche von einer Region zu einer anderen migrieren.

![Arbeitsbereich bearbeiten: Wählen Sie eine verfügbare Kapazität aus. Power BI Multi-Geo](media/service-admin-premium-multi-geo/power-bi-multi-geo-edit-workspace.png)

Diese Meldung wird angezeigt, um die Änderung zu bestätigen.

![Bestätigung „Zugewiesene Arbeitsbereichskapazität ändern“](media/service-admin-premium-multi-geo/power-bi-multi-geo-change-assigned-workspace-capacity.png)

Die Gatewayanmeldeinformationen müssen bei der Migration gegenwärtig nicht zurückgesetzt werden.  Nachdem sie in der Region der Premium-Kapazität gespeichert wurden, müssen Sie sie bei der Migration zurückzusetzen.

Bei der Migration tritt bei bestimmten Vorgängen möglicherweise ein Fehler auf, wie etwa beim Veröffentlichen neuer Datasets oder bei geplanten Datenaktualisierungen.  

Die folgenden Elemente werden in der Premium-Region gespeichert, sofern Multi-Geo aktiviert ist:

- Modelle (ABF-Dateien) für Import- und DirectQuery-Datasets
- Abfragecache
- R-Grafiken

Diese Elemente bleiben in der ursprünglichen Region des Mandanten:

- Pushdatasets
- Excel-Arbeitsmappen
- Dashboard-/Berichtsmetadaten, z.B. Kachelnamen, Kachelabfragen
- Service Busse für Gatewayabfragen oder geplante Aktualisierungsaufträge
- Berechtigungen
- Datasetanmeldeinformationen

## <a name="view-capacity-regions"></a>Anzeigen von Kapazitätsregionen

Im Verwaltungsportal können Sie alle Kapazitäten für Ihren Power BI-Mandanten und die Regionen anzeigen, in denen sie sich aktuell befinden.

![Anzeigen von Premium-Kapazitäten](media/service-admin-premium-multi-geo/power-bi-multi-geo-premium-capacities.png) 

## <a name="change-the-region-for-existing-content"></a>Ändern der Region für vorhandene Inhalte

Wenn Sie die Region für vorhandene Inhalte ändern müssen, stehen Ihnen zwei Optionen zur Verfügung.

- Erstellen Sie eine zweite Kapazität, und verschieben Sie Arbeitsbereiche. Bei freigegebenen Benutzern treten keine Ausfallzeiten auf, solange der Mandant über zusätzliche virtuelle Kerne verfügt.
- Wenn die Erstellung einer zweiten Kapazität nicht infrage kommt, können Sie den Inhalt vorübergehend in eine gemeinsam genutzte Kapazität der Premium-Kapazität verschieben. Zusätzliche virtuelle Kerne sind nicht erforderlich, aber bei freigegebenen Benutzern treten Ausfallzeiten auf.

## <a name="move-content-out-of-multi-geo"></a>Verschieben von Inhalten aus Multi-Geo  

Sie haben zwei Möglichkeiten, Arbeitsbereiche aus der Multi-Geo-Kapazität zu entfernen:

- Löschen Sie die aktuelle Kapazität, in der sich der Arbeitsbereich befindet.  Dadurch wird der Arbeitsbereich wieder in die gemeinsam genutzte Kapazität in der ursprünglichen Region verschoben.
- Migrieren Sie einzelne Arbeitsbereiche wieder zur Premium-Kapazität, die sich in dem Mandanten in der ursprünglichen Region befindet.

## <a name="limitations-and-considerations"></a>Einschränkungen und Überlegungen

- Vergewissern Sie sich, dass Sie bei Verschiebungen zwischen Regionen alle unternehmensspezifischen und gesetzlichen Complianceanforderungen erfüllen, bevor Sie eine Datenübertragung initiieren.
- Eine zwischengespeicherte Abfrage, die sich in einer weit entfernten Region befindet, verbleibt in dieser Region im Ruhezustand. Allerdings werden andere in Übertragung begriffene Daten möglicherweise zwischen mehreren geografischen Regionen hin und her verschoben.
- Beim Verschieben von Daten aus einer Region in eine andere in einer Multi-Geo-Umgebung können die Quelldaten bis zu 30 Tage lang in der Region verbleiben, von der aus die Daten verschoben wurden. In diesem Zeitraum haben Benutzer keinen Zugriff auf diese. Nach Ablauf der 30 Tage werden sie aus dieser Region entfernt und gelöscht.

- Das [Dataflows](service-dataflows-overview.md)-Feature wird aktuell für Multi-Geo nicht unterstützt.

## <a name="next-steps"></a>Nächste Schritte

- [Was ist Power BI Premium?](service-premium-what-is.md)
- [Multi-Geo für Power BI Embedded-Kapazitäten](developer/embedded/embedded-multi-geo.md)

Weitere Fragen? [Stellen Sie Ihre Frage in der Power BI-Community.](https://community.powerbi.com/)
