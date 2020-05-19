---
title: Behandeln von Problemen mit Bereitstellungspipelines
description: Behandeln von Problemen mit Bereitstellungspipelines in Power BI
author: KesemSharabi
ms.author: kesharab
ms.topic: overview
ms.service: powerbi
ms.subservice: powerbi-service
ms.date: 05/06/2020
ms.openlocfilehash: fda846a19b5c6081c59f08f2bf9f94eddbc9852c
ms.sourcegitcommit: bfc2baf862aade6873501566f13c744efdd146f3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/13/2020
ms.locfileid: "83148553"
---
# <a name="deployment-pipelines-troubleshooting-preview"></a>Behandeln von Problemen mit Bereitstellungspipelines (Vorschau)

In diesem Artikel finden Sie Informationen zum Behandeln von Problemen mit Bereitstellungspipelines.

## <a name="general"></a>Allgemein

### <a name="whats-deployment-pipelines-in-power-bi"></a>Was sind Bereitstellungspipelines in Power BI?

Informationen zu Bereitstellungspipelines in Power BI finden Sie in der [Übersicht über Bereitstellungspipelines](deployment-pipelines-overview.md).

### <a name="how-do-i-get-started-with-deployment-pipelines"></a>Was sind die ersten Schritte mit Bereitstellungspipelines?

Anweisungen zu den ersten Schritten mit Bereitstellungspipelines finden Sie [hier](deployment-pipelines-get-started.md).

### <a name="why-cant-i-see-the-deployment-pipelines-button"></a>Warum wird mir die Schaltfläche „Bereitstellungspipelines“ nicht angezeigt?

Wenn die folgenden Bedingungen nicht erfüllt sind, wird die Schaltfläche „Bereitstellungspipelines“ nicht angezeigt.

* Sie sind ein [Power BI Pro](../admin/service-admin-purchasing-power-bi-pro.md)-Benutzer.

* Sie gehören zu einer Organisation mit Premium-Kapazität.

* Ein Arbeitsbereich kann nur einer einzelnen Pipeline zugewiesen werden.

* Sie sind Administrator eines neuen Arbeitsbereichs.

## <a name="licensing"></a>Lizenzierung

### <a name="what-licenses-are-needed-to-work-with-deployment-pipelines"></a>Welche Lizenzen sind für Bereitstellungspipelines erforderlich?

Um Bereitstellungspipelines verwenden zu können, müssen Sie ein [Pro-Benutzer](../admin/service-admin-purchasing-power-bi-pro.md) mit [Premium-Kapazität](../admin/service-premium-what-is.md) sein. Weitere Informationen finden Sie unter [Zugreifen auf Bereitstellungspipelines](deployment-pipelines-get-started.md#accessing-deployment-pipelines).

### <a name="what-type-of-capacity-can-i-assign-to-a-workspace-in-a-pipeline"></a>Welche Art von Kapazität kann ich einem Arbeitsbereich in einer Pipeline zuweisen?

Alle Arbeitsbereiche in einer Bereitstellungspipeline müssen sich innerhalb einer dedizierten Kapazität befinden, damit die Pipeline funktionsfähig ist. Sie können jedoch für verschiedene Arbeitsbereiche in einer Pipeline unterschiedliche Kapazitäten verwenden. Sie können in derselben Pipeline auch unterschiedliche Kapazitätstypen für verschiedene Arbeitsbereiche verwenden.

Für Entwicklungs- und Testzwecke können Sie A- oder EM-Kapazität neben einem Power BI Pro-Konto für jeden Benutzer nutzen.

Für Produktionsarbeitsbereiche benötigen Sie eine P-Kapazität. Wenn Sie ein ISV sind, der Inhalte über eingebettete Anwendungen vertreibt, können Sie A- oder EM-Kapazität auch für die Produktion nutzen.

## <a name="technical"></a>Technische Fragen

### <a name="why-cant-i-see-all-my-workspaces-when-i-try-to-assign-a-workspace-to-a-pipeline"></a>Warum kann ich nicht alle meine Arbeitsbereiche sehen, wenn ich versuche, einer Pipeline einen Arbeitsbereich zuzuweisen?

Um einer Pipeline einen Arbeitsbereich zuweisen zu können, müssen die folgenden Bedingungen erfüllt sein:

* Der Arbeitsbereich hat eine [neue Arbeitsbereichsoberfläche](../collaborate-share/service-create-the-new-workspaces.md).

* Sie sind ein Administrator des Arbeitsbereichs.

* Der Arbeitsbereich ist keiner anderen Pipeline zugewiesen.

* Der Arbeitsbereich befindet sich in einer [Premium-Kapazität](../admin/service-premium-what-is.md).

Arbeitsbereiche, die diese Bedingungen nicht erfüllen, werden nicht in der Liste der Arbeitsbereiche angezeigt, aus denen Sie wählen können.

### <a name="how-can-i-assign-workspaces-to-all-the-stages-in-a-pipeline"></a>Wie kann ich Arbeitsbereiche allen Phasen einer Pipeline zuweisen?

Sie können pro Pipeline nur einen Arbeitsbereich zuweisen. Nachdem ein Arbeitsbereich einer Pipeline zugewiesen wurde, können Sie ihn den nächsten Pipelinephasen bereitstellen. Bei der erstmaligen Bereitstellung wird ein neuer Arbeitsbereich mit Kopien der Elemente in der Quellphase erstellt. Die Beziehungen der kopierten Elemente werden beibehalten. Weitere Informationen finden Sie unter [Zuweisen eines Arbeitsbereichs zu einer Bereitstellungspipeline](deployment-pipelines-get-started.md#step-2---assign-a-workspace-to-a-deployment-pipeline).

### <a name="why-did-my-first-deployment-fail"></a>Warum ist meine erste Bereitstellung fehlgeschlagen?

Ihre erste Bereitstellung kann aus verschiedenen Gründen fehlschlagen. Einige davon sind in der folgenden Tabelle aufgeführt.

|Fehler  |Aktion  |
|---------|---------|
|Sie verfügen nicht über [Premium-Kapazitätsberechtigungen](deployment-pipelines-process.md#creating-a-premium-capacity-workspace).     |Um Premium-Kapazitätsberechtigungen zu erhalten, bitten Sie einen Administrator, Ihren Arbeitsbereich einer Kapazität hinzuzufügen, oder um Zuweisungsberechtigungen für die Kapazität. Sobald sich der Arbeitsbereich in einer Kapazität befindet, wiederholen Sie die Bereitstellung.        |
|Sie haben keine Berechtigungen für den Arbeitsbereich.     |Für eine Bereitstellung müssen Sie Mitglied des Arbeitsbereichs sein. Bitten Sie Ihren Arbeitsbereichsadministrator, Ihnen die erforderlichen Berechtigungen zu erteilen.         |
|Der Power BI-Administrator hat das Erstellen von Arbeitsbereichen deaktiviert.     |Bitten Sie Ihren Power BI-Administrator um Unterstützung.         |
|Ihr Arbeitsbereich hat keine [neue Arbeitsbereichsoberfläche](../collaborate-share/service-create-the-new-workspaces.md).     |Erstellen Sie Ihre Inhalte auf der neuen Arbeitsbereichsoberfläche. Wenn Sie über Inhalte in einem klassischen Arbeitsbereich verfügen, können Sie diesen [in eine neue Arbeitsbereichsoberfläche umwandeln](../collaborate-share/service-upgrade-workspaces.md).         |
|Sie arbeiten mit der [selektiven Bereitstellung](deployment-pipelines-get-started.md#selective-deployment) und wählen nicht das Dataset Ihres Inhalts aus.     |Führen Sie einen der folgenden Schritte aus: </br></br>Heben Sie die Auswahl des Inhalts auf, der mit Ihrem Dataset verknüpft ist. Ihre nicht mehr ausgewählten Inhalte (z. B. Berichte oder Dashboards) werden nicht in die nächste Phase kopiert. </br></br>Wählen Sie das Dataset aus, das mit dem ausgewählten Inhalt verknüpft ist. Ihr Dataset wird in die nächste Phase kopiert.         |

### <a name="im-getting-a-warning-that-i-have-unsupported-artifacts-in-my-workspace-when-im-trying-to-deploy-how-can-i-know-which-artifacts-are-not-supported"></a>Ich erhalte die Warnung, dass mein Arbeitsbereich „nicht unterstützte Artefakte“ enthält, wenn ich versuche, eine Bereitstellung vorzunehmen. Woher weiß ich, welche Artefakte nicht unterstützt werden?

Eine umfassende Liste von Elementen und Artefakten, die in Bereitstellungspipelines nicht unterstützt werden, finden Sie in den folgenden Abschnitten:

* [Nicht unterstützte Elemente](deployment-pipelines-process.md#unsupported-items)

* [Nicht kopierte Elementeigenschaften](deployment-pipelines-process.md#item-properties-that-are-not-copied)

### <a name="why-did-my-deployment-fail-due-to-broken-rules"></a>Warum ist meine Bereitstellung aufgrund nicht eingehaltener Regeln fehlgeschlagen?

Wenn Sie Probleme bei der Konfiguration von Datasetregeln haben, lesen Sie den Artikel zu [Datasetregeln](deployment-pipelines-get-started.md#step-4---create-dataset-rules), und stellen Sie sicher, dass Sie die [Einschränkungen für Datasetregeln](deployment-pipelines-get-started.md#dataset-rule-limitations) beachten.

Wenn Ihre Bereitstellung zuvor erfolgreich war und plötzlich aufgrund nicht eingehaltener Regeln misslingt, kann dies auf die Neuveröffentlichung eines Datasets zurückzuführen sein. Die folgenden Änderungen am Quelldataset führen zum Fehlschlagen der Bereitstellung:

**Parameterregeln**

* Ein entfernter Parameter

* Ein geänderter Parametername

**Datenquellenregeln**

In Ihren Datasetregeln fehlen Werte. Dies ist möglicherweise die Folge einer Änderung des Datasets.

![Nicht eingehaltene Regel](media/deployment-pipelines-troubleshooting/broken-rule.png)

Wenn eine zuvor erfolgreiche Bereitstellung aufgrund fehlerhafter Verknüpfungen fehlschlägt, wird eine Warnung angezeigt. Sie können auf **Regeln konfigurieren** klicken, um zum Einstellungsbereich für die Bereitstellung zu navigieren, in dem das fehlerhafte Dataset markiert ist. Wenn Sie auf das Dataset klicken, werden die nicht eingehaltenen Regeln markiert.

Für eine erfolgreiche Bereitstellung müssen die nicht eingehaltenen Regeln repariert oder entfernt und anschließend erneut bereitgestellt werden.

### <a name="how-can-i-change-the-data-source-in-the-pipeline-stages"></a>Wie kann ich die Datenquelle in den Pipelinephasen ändern?

Die Datenquellenverbindung kann nicht im Power BI-Dienst geändert werden.

Wenn Sie die Datenquelle in der Test- oder Produktionsphase ändern möchten, können Sie [Datasetregeln](deployment-pipelines-get-started.md#step-4---create-dataset-rules) oder [APIs](https://docs.microsoft.com/rest/api/power-bi/datasets/updateparametersingroup) verwenden. Datasetregeln gelten erst nach der nächsten Bereitstellung.

### <a name="i-fixed-a-bug-in-production-but-now-i-cant-click-the-deploy-to-previous-stage-button-why-is-it-greyed-out"></a>Ich habe einen Fehler in der Produktion behoben, aber jetzt kann ich nicht mehr auf die Schaltfläche „In vorheriger Phase bereitstellen“ klicken. Warum ist sie abgeblendet?

Rückwärts kann die Bereitstellung nur in einer leeren Phase erfolgen. Wenn Sie Inhalte in der Testphase haben, können Sie diese nicht rückwärts aus der Produktion bereitstellen.

Nach Erstellung der Pipeline können Sie Ihre Inhalte in der Entwicklungsphase entwickeln und in den Testphasen überprüfen und testen. Sie können Fehler in diesen Phasen beheben und dann die korrigierte Umgebung in der Produktionsphase bereitstellen.

>[!NOTE]
>Bei einer Rückwärtsbereitstellung wird nur eine [vollständige Bereitstellung](deployment-pipelines-get-started.md#deploying-all-content) unterstützt. Die [selektive Bereitstellung](deployment-pipelines-get-started.md#selective-deployment) wird nicht unterstützt.

### <a name="does-deployment-pipelines-support-multi-geo"></a>Unterstützen Bereitstellungspipelines Multi-Geo?

Multi-Geo wird unterstützt. Die Bereitstellung von Inhalten zwischen Phasen in verschiedenen geografischen Räumen kann allerdings länger dauern.

## <a name="permissions"></a>Berechtigungen

### <a name="what-is-the-deployment-pipelines-permissions-model"></a>Wie sieht das Berechtigungsmodell für Bereitstellungspipelines aus?

Das Berechtigungsmodell für Bereitstellungspipelines wird im Abschnitt [Berechtigungen](deployment-pipelines-process.md#permissions) beschrieben.

### <a name="who-can-deploy-content-between-stages"></a>Wer kann Inhalte zwischen Phasen bereitstellen?

Inhalte können in einer Phase ohne oder mit Inhalten bereitgestellt werden. Der Inhalt muss sich in einer [Premium-Kapazität](../admin/service-premium-what-is.md) befinden.

* **Bereitstellung in einer leeren Phase**: beliebiger [Pro-Benutzer](../admin/service-admin-purchasing-power-bi-pro.md), der Mitglied oder Administrator des Quellarbeitsbereichs ist.

* **Bereitstellung in einer Phase mit Inhalt**: beliebiger [Pro-Benutzer](../admin/service-admin-purchasing-power-bi-pro.md), der Mitglied oder Administrator beider Arbeitsbereiche in der Quell- und Zielbereitstellungsphase ist.

* **Überschreiben eines Datasets**: Die Bereitstellung hat Vorrang vor jedem Dataset, das in der Zielphase enthalten ist, auch wenn das Dataset nicht geändert wurde. Der Benutzer muss Besitzer aller Datasets in der Zielphase sein, die in der Bereitstellung angegeben sind.

### <a name="which-permissions-do-i-need-to-configure-dataset-rules"></a>Welche Berechtigungen benötige ich zum Konfigurieren von Datasetregeln?

Zum Konfigurieren von Datasetregeln in Bereitstellungspipelines müssen Sie Besitzer des Datasets sein.

### <a name="why-cant-i-see-workspaces-in-the-pipeline"></a>Warum sehe ich keine Arbeitsbereiche in der Pipeline?

Berechtigungen für Pipelines und Arbeitsbereiche werden getrennt verwaltet. Sie verfügen möglicherweise über Pipeline-, jedoch nicht über Arbeitsbereichsberechtigungen. Weitere Informationen finden Sie im Abschnitt [Berechtigungen](deployment-pipelines-process.md#permissions).

## <a name="next-steps"></a>Nächste Schritte

>[!div class="nextstepaction"]
>[Einführung in Bereitstellungspipelines](deployment-pipelines-overview.md)

>[!div class="nextstepaction"]
>[Erste Schritte mit Bereitstellungspipelines](deployment-pipelines-get-started.md)

>[!div class="nextstepaction"]
>[Grundlegendes zum Prozess für Bereitstellungspipelines](deployment-pipelines-process.md)

>[!div class="nextstepaction"]
>[Bewährte Methoden für Bereitstellungspipelines](deployment-pipelines-best-practices.md)