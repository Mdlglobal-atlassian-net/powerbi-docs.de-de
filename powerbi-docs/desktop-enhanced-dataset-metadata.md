---
title: Verwenden der erweiterten Datasetmetadaten in Power BI Desktop (Vorschau)
description: In diesem Artikel wird beschrieben, wie Sie erweiterte Dataset-Metadaten in Power BI verwenden.
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 03/31/2020
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 301d6397e4a3ae4498234bae3ad8a49aa7552722
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "82584674"
---
# <a name="using-enhanced-dataset-metadata-preview"></a>Verwenden erweiterter Dataset-Metadaten (Vorschauversion)

Wenn Power BI Desktop Berichte erstellt, werden dabei auch Dataset-Metadaten in den entsprechenden PBIX- und PBIT-Dateien erstellt. Bisher wurden die Metadaten in einem für Power BI Desktop spezifischen Format gespeichert. Dabei wurden Base64-codierte M-Ausdrücke und Datenquellen verwendet, wobei für Benutzer nicht erkennbar war, wie die Metadaten gespeichert wurden.

Mit der Veröffentlichung des Features für **erweiterte Dataset-Metadaten** werden viele dieser Einschränkungen aufgehoben. Wenn das Feature für **erweiterte Dataset-Metadaten** aktiviert ist, wird für die von Power BI Desktop erstellten Metadaten ein ähnliches Format verwendet wie bei tabellarischen Modellen in Analysis Services, basierend auf dem [Tabellenobjektmodell](https://docs.microsoft.com/bi-reference/tom/introduction-to-the-tabular-object-model-tom-in-analysis-services-amo).


Das Feature für **erweiterte Dataset-Metadaten** ist ein strategisches und grundlegendes Feature, da zukünftige Power BI-Funktionen auf den Metadaten aufbauen werden. Weitere Funktionen, die von erweiterten Dataset-Metadaten profitieren, sind z. B. [XMLA read/write](https://docs.microsoft.com/power-platform-release-plan/2019wave2/business-intelligence/xmla-readwrite) (XMLA Lesen/Schreiben) für die Verwaltung von Power BI-Datasets und die Migration von Analysis Services-Workloads zu Power BI, um von Features der nächsten Generation zu profitieren.



## <a name="enable-enhanced-dataset-metadata"></a>Aktivieren erweiterter Dataset-Metadaten

Das Feature für **erweiterte Dataset-Metadaten** befindet sich derzeit in der Vorschauphase. Klicken Sie in Power BI Desktop auf **Datei > Optionen und Einstellungen > Optionen > Vorschaufeatures**, und aktivieren Sie dann das Kontrollkästchen für **Store datasets using enhanced metadata format** (Datasets im erweiterten Metadatenformat speichern), wie in der folgenden Abbildung gezeigt, um erweiterte Dataset-Metadaten in Power BI Desktop zu aktivieren. 

![Aktivieren der Previewfunktion](media/desktop-enhanced-dataset-metadata/enhanced-dataset-metadata-01.png)

Sie werden dazu aufgefordert, Power BI Desktop neu zu starten.

![Aufforderung zum Neustarten](media/desktop-enhanced-dataset-metadata/enhanced-dataset-metadata-02.png)

Sobald die Previewfunktion aktiviert ist, versucht Power BI Desktop, PBIX- und PBIT-Dateien, die das vorherige Metadatenformat verwenden, zu aktualisieren. 

> [!IMPORTANT]
> Wenn Sie die Funktion **Erweiterte Datasetmetadaten** aktivieren, kann das Upgrade der Berichte nicht mehr rückgängig gemacht werden. Alle Power BI-Berichte, die mit Power BI Desktop geladen oder erstellt wurden, werden nach Aktivierung der **erweiterten Datasetmetadaten** unumkehrbar in das erweiterte Metadatenformat konvertiert.

## <a name="considerations-and-limitations"></a>Überlegungen und Einschränkungen

In der Vorschauversion gelten die folgenden Einschränkungen, wenn die Previewfunktion aktiviert ist.

### <a name="unsupported-features-and-connectors"></a>Nicht unterstützte Features und Connectors
Beim Öffnen einer vorhandenen PBIX- oder PBIT-Datei, die nicht aktualisiert wurde, schlägt das Upgrade fehl, wenn das Dataset eines der folgenden Features oder einen der folgenden Connectors enthält. Wenn ein solcher Fehler auftritt, sollte dies keine unmittelbaren Auswirkungen auf das Benutzererlebnis haben, und Power BI Desktop verwendet weiterhin das vorherige Metadatenformat.

* Python-Skripts
* Benutzerdefinierte Connectors
* Azure DevOps Server
* BI-Connector
* Denodo
* Dremio
* Exasol
* Indexima
* Iris
* Jethro ODBC
* Kyligence Enterprise
* MarkLogic ODBC
* Qubole Presto
* TeamDesk
* M-Ausdrücke mit bestimmten Zeichenkombinationen wie „\\n“ in Spaltennamen
* Wenn Datasets verwendet werden, bei denen das Feature für **erweiterte Dataset-Metadaten** aktiviert ist, können im Power BI-Dienst keine Datenquellen für einmaliges Anmelden (SSO, Single Sign-On) eingerichtet werden.

Darüber hinaus können PBIX- und PBIT-Dateien, die bereits erfolgreich für die Verwendung von **erweiterten Dataset-Metadaten** aktualisiert wurden, die obigen Features und Connectors in der aktuellen Version *nicht* mehr verwenden.

### <a name="lineage-view"></a>Herkunftsansicht
Datasets, die das neue Metadatenformat verwenden, zeigen derzeit keine Links zu Dataflows in der Datenherkunftsansicht im Power BI-Dienst an.

## <a name="next-steps"></a>Nächste Schritte

Mit Power BI Desktop können Sie vielfältige Aufgaben ausführen. Weitere Informationen zu den Funktionen und Möglichkeiten finden Sie in den folgenden Ressourcen:

* [Was ist Power BI Desktop?](desktop-what-is-desktop.md)
* [Neuigkeiten in Power BI Desktop](desktop-latest-update.md)
* [Übersicht zu Abfragen mit Power BI Desktop](desktop-query-overview.md)
* [Datentypen in Power BI Desktop](desktop-data-types.md)
* [Strukturieren und Kombinieren von Daten mit Power BI Desktop](desktop-shape-and-combine-data.md)
* [Allgemeine Abfrageaufgaben in Power BI Desktop](desktop-common-query-tasks.md)

