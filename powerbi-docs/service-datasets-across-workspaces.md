---
title: Einführung in die Verwendung von Datasets in mehreren Arbeitsbereichen (Vorschau)
description: Erfahren Sie, wie Sie ein Dataset mit Benutzern in der gesamten Organisation teilen können. Dann können diese in ihren eigenen Arbeitsbereichen Berichte erstellen, die auf Ihrem Dataset basieren.
author: maggiesMSFT
ms.reviewer: chbraun
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 10/01/2019
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: 148e5283e1a2e2d5ef61027c24df1a4c3e574822
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "77179218"
---
# <a name="intro-to-datasets-across-workspaces-preview"></a>Einführung in die Verwendung von Datasets in mehreren Arbeitsbereichen (Vorschau)

Business Intelligence ist eine gemeinschaftliche Aktivität. Es ist wichtig, standardisierte Datasets einzurichten, die als „eindeutig wahre Quelle“ fungieren können. Dann sind das Entdecken und Wiederverwenden solcher standardisierten Datasets ist von entscheidender Bedeutung. Wenn Experten für Datenmodellierung in Ihrer Organisation optimierte Datasets erstellen und teilen, können Berichtersteller von diesen Datasets ausgehen, um präzise Berichte zu erstellen. Dann verfügt Ihre Organisation über konsistente Daten für die Entscheidungsfindung und ist auf dem Weg zu einer gesunden Datenkultur.

![Freigegebenes Dataset auswählen](media/service-datasets-across-workspaces/power-bi-select-shared-dataset.png)

In Power BI können Ersteller von Datasets mithilfe der [Erstellungsberechtigung](service-datasets-build-permissions.md) steuern, wer Zugriff auf ihre Daten hat. Datasetersteller können Datasets auch *zertifizieren* oder *höher stufen*, damit andere sie finden können. Auf diese Weise können Berichtsautoren erkennen, welche Datasets hohe Qualität aufweisen und offiziell sind, und können diese Datasets für das Erstellen in Power BI verwenden. Mandantenadministratoren verfügen über eine neue Mandanteneinstellung zum [Steuern der Arbeitsbereiche übergreifenden Verwendung von Datasets](service-datasets-admin-across-workspaces.md).

## <a name="dataset-sharing-and-the-new-workspace-experience"></a>Freigeben von Datasets und die neue Arbeitsbereichsoberfläche

Das Erstellen von Berichten auf der Grundlage von Datasets in verschiedenen Arbeitsbereichen und das Kopieren von Berichten in verschiedene Arbeitsbereiche sind eng mit der [neuen Arbeitsbereichsoberfläche](service-create-the-new-workspaces.md) verknüpft:

- Wenn Sie im Dienst den Datasetkatalog aus einer neuen Arbeitsbereichsoberfläche öffnen, zeigt der Datasetkatalog Datsets an, die sich in Ihren Arbeitsbereichen „Mein Arbeitsbereich“ und in anderen Arbeitsbereichen mit der neuen Arbeitsbereichsoberfläche befinden. 
- Wenn Sie den Datasetkatalog aus einem klassischen Arbeitsbereich öffnen, sehen Sie nur die Datasets aus dem betreffenden Arbeitsbereich, keine in anderen Arbeitsbereichen.
- In Power BI Desktop können Sie Live Connect-Berichte in verschiedenen Arbeitsbereichen veröffentlichen, sofern sich ihre Datasets in Arbeitsbereichen mit der neuen Benutzeroberfläche befinden.
- Beim übergreifenden Kopieren von Berichten über Arbeitsbereiche hinweg muss es sich bei dem Zielarbeitsbereich um einen Arbeitsbereich mit der neuen Benutzeroberfläche handeln.

## <a name="discover-datasets-preview"></a>Datasets entdecken (Vorschau)

Wenn Sie einen Bericht auf der Grundlage eines vorhandenen Datasets erstellen, besteht der erste Schritt darin, eine Verbindung mit dem Dataset herzustellen, entweder über den Power BI-Dienst oder Power BI Desktop. Weitere Informationen zum [Entdecken von Datasets aus verschiedenen Arbeitsbereichen (Vorschau)](service-datasets-discover-across-workspaces.md)

## <a name="copy-a-report"></a>Kopieren eines Berichts

Wenn Sie in einem Arbeitsbereich oder einer App einen Bericht gefunden haben, der Ihnen gefällt, können Sie eine Kopie davon erstellen und ihn anschließend nach Ihrem Bedarf anpassen. Sie brauchen sich nicht mit der Erstellung des Datenmodells abzugeben. Das wurde bereits für Sie erstellt. Und es ist viel einfacher, einen vorhandenen Bericht zu ändern, als einen von Grund auf neuen zu erstellen. Weitere Informationen zum [Kopieren von Berichten](service-datasets-copy-reports.md).

## <a name="build-permission-for-datasets"></a>Erstellungsberechtigung für Datasets

Als Ersteller eines Datasets können Sie mit dem Berechtigungstyp „Erstellen“ festlegen, wer in Ihrer Organisation neue Inhalte in Ihren Datasets erstellen kann. Benutzer mit der Berechtigung „Erstellen“ können darüber hinaus außerhalb von Power BI neue Inhalte anhand des Datasets erstellen, z. B. Excel-Datenblätter mithilfe von „In Excel analysieren“, von XMLA und durch Exportieren. Weitere Informationen zur [Erstellungsberechtigung](service-datasets-build-permissions.md).

## <a name="promotion-and-certification"></a>Bewerbung und Zertifizierung

Wenn Sie beim Erstellen von Datasets ein Dataset schaffen, von dem andere profitieren können, können Sie es ihnen leichter machen, Ihr Dataset zu finden, indem Sie [Ihr Dataset höher stufen](service-datasets-promote.md). Sie können darüber hinaus anfordern, dass die Experten in Ihrer Organisation [Ihr Dataset zertifizieren](service-datasets-certify.md).

## <a name="licensing"></a>Lizenzierung

Die spezifischen Features und Erfahrungen, die auf der Grundlage geteilter Datasets erstellt werden, werden gemäß ihren bestehenden Szenarien lizenziert. Beispiel:

- Im Allgemeinen stehen das Ermitteln freigegebener Datasets und das Herstellen von Verbindungen allen Benutzern offen. Eine Premium-Lizenz ist dafür nicht erforderlich.
- Benutzer ohne Pro-Lizenz können Datasets nur dann arbeitsbereichsübergreifend zum Erstellen von Berichten verwenden, wenn sich diese Datasets im persönlichen Arbeitsbereich der Benutzer („Mein Arbeitsbereich“) oder in einem Arbeitsbereich im Premium-Tarif befinden. Die gleiche Lizenzierungseinschränkung gilt unabhängig davon, ob sie Berichte in Power BI Desktop oder im Power BI-Dienst erstellen.
- Zum Kopieren von Berichten zwischen Arbeitsbereichen ist eine Pro-Lizenz erforderlich.
- Für das Kopieren von Berichten aus einer App ist ebenfalls eine Pro-Lizenz erforderlich, wie sie es bisher schon für organisationsbezogene Inhaltspakete erforderlich war.
- Zum Höherstufen und Zertifizieren von Datasets ist eine Pro-Lizenz erforderlich.

## <a name="considerations-and-limitations"></a>Überlegungen und Einschränkungen

- Als App-Herausgeber müssen Sie sicherstellen, dass Ihre Zielgruppe auf Datasets außerhalb des Arbeitsbereichs zugreifen kann. Andernfalls treten bei der Interaktion mit Ihrer App Probleme auf. Berichte werden ohne Zugriff auf das Dataset nicht geöffnet, und Dashboardkacheln werden gesperrt angezeigt. Außerdem können Benutzer die App nicht öffnen, wenn das erste Element in der Navigationsstruktur ein Bericht ohne Zugriff auf das Dataset ist.
- Das Erstellen eines Berichts auf der Grundlage eines Datasets in einem anderen Arbeitsbereich setzt die neue Arbeitsbereichsoberfläche an beiden Enden voraus: Der Bericht muss sich in einer neuen Arbeitsbereichsoberfläche befinden, und das Dataset muss sich in einer neuen Arbeitsbereichsoberfläche befinden. Sie können Berichte nur aus einer neuen Arbeitsbereichs-Benutzeroberfläche in eine andere neue Arbeitsbereichs-Benutzeroberfläche kopieren, nicht in klassische Arbeitsbereiche oder den Arbeitsbereich „Mein Arbeitsbereich“. 
- In einem klassischen Arbeitsbereich zeigt die Oberfläche zur Datasetermittlung nur die Datasets in dem betreffenden Arbeitsbereich an.
- Prinzipbedingt funktioniert „Im Web veröffentlichen“ nicht für Berichte, die auf einem freigegebenen Dataset basieren.
- Wenn zwei Personen Mitglieder eines Arbeitsbereichs sind, der auf ein freigegebenes Dataset zugreift, ist es möglich, dass nur eine von ihnen das zugehörige Dataset im Arbeitsbereich sieht. Nur Personen, die mindestens Lesezugriff auf das Dataset besitzen, können das freigegebene Dataset sehen. 

## <a name="next-steps"></a>Nächste Schritte

- [Höher Stufen von Datasets](service-datasets-promote.md)
- [Zertifizieren von Datasets](service-datasets-certify.md)
- [Steuern der Verwendung von Datasets in mehreren Arbeitsbereichen](service-datasets-admin-across-workspaces.md)
- Haben Sie Fragen? [Stellen Sie Ihre Frage in der Power BI-Community.](https://community.powerbi.com/)
