---
title: Zusammenführen oder Anfügen von lokalen und Clouddatenquellen
description: Verwenden Sie das lokale Datengateway, um lokale und Clouddatenquellen in derselben Abfrage zusammenzuführen oder daran anzufügen.
author: arthiriyer
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: conceptual
ms.date: 07/15/2019
ms.author: arthii
LocalizationGroup: Gateways
ms.openlocfilehash: 10aec8659fcb643c5b0511360ba798c7b4873c77
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "74697886"
---
# <a name="merge-or-append-on-premises-and-cloud-data-sources"></a>Zusammenführen oder Anfügen von lokalen und Clouddatenquellen

[!INCLUDE [gateway-rewrite](includes/gateway-rewrite.md)]

Sie können das lokale Datengateway verwenden, um lokale und Clouddatenquellen in derselben Abfrage zusammenzuführen oder daran anzufügen. Diese Lösung ist hilfreich, wenn Sie Daten aus mehreren Quellen in derselben Abfrage kombinieren möchten.

>[!NOTE]
>Dieser Artikel gilt nur für Datensätze, bei denen Cloud- und lokale Datenquellen in einer einzigen Abfrage zusammengefasst oder hinzugefügt wurden. Bei Datasets, die getrennte Abfragen beinhalten – eine mit einer Verbindung zu einer lokalen Datenquelle und eine mit einer Verbindung zu einer Clouddatenquelle –, führt das Gateway die Abfrage für die Clouddatenquelle nicht aus.

## <a name="prerequisites"></a>Voraussetzungen

- Ein [auf einem lokalen Computer installiertes Gateway](/data-integration/gateway/service-gateway-install)
- Eine Power BI Desktop-Datei mit Abfragen, die lokale und Clouddatenquellen enthält.

>[!NOTE]
>Um auf Clouddatenquellen zugreifen zu können, müssen Sie sicherstellen, dass das Gateway Zugriff auf diese Datenquellen hat.

1. Klicken Sie in der oberen rechten Ecke des Power BI-Diensts auf das Zahnradsymbol ![Zahnradsymbol für Einstellungen](media/service-gateway-mashup-on-premises-cloud/icon-gear.png) >  und dann auf **Gateways verwalten**.

    ![Verwalten von Gateways](media/service-gateway-mashup-on-premises-cloud/manage-gateways.png)

2. Wählen Sie das Gateway aus, das Sie konfigurieren möchten.

3. Klicken Sie unter **Gatewayclustereinstellungen** auf die Optionen **Ermöglichen Sie die Aktualisierung der Clouddatenquellen des Benutzers über diesen Gatewaycluster** > **Übernehmen**.

    ![Über dieses Gatewaycluster aktualisieren](media/service-gateway-mashup-on-premises-cloud/refresh-gateway-cluster.png)

4. Fügen Sie unter diesem Gatewaycluster alle [lokalen Datenquellen](service-gateway-enterprise-manage-scheduled-refresh.md#add-a-data-source) hinzu, die in Ihren Abfragen verwendet werden. Die Clouddatenquellen müssen hier nicht hinzugefügt werden.

5. Laden Sie die Power BI Desktop-Datei mit den Abfragen, die lokale und Clouddatenquellen enthalten, zu Power BI hoch.

6. Gehen Sie auf der Seite **Dataseteinstellungen** für das neue Dataset folgendermaßen vor:

   - Wählen Sie für die lokale Quelle das Gateway aus, das dieser Datenquelle zugeordnet ist.
   - Bearbeiten Sie unter **Datenquellen-Anmeldeinformationen** die Clouddatenquellen-Anmeldeinformationen nach Bedarf.

    Stellen Sie sicher, dass die Datenschutzebenen sowohl für Cloud- als auch für lokale Datenquellen entsprechend eingestellt sind, um sicherzustellen, dass die Joins sicher verarbeitet werden.

     ![Dataseteinstellungen](media/service-gateway-mashup-on-premises-cloud/dataset-settings.png)

7. Wenn Sie die Cloudanmeldeinformationen festgelegt haben, können Sie eine Aktualisierung des Datasets mithilfe der Option **Jetzt aktualisieren** vornehmen. Sie können aber auch eine Aktualisierung in regelmäßigen Abständen planen.

## <a name="next-steps"></a>Weitere Schritte

Weitere Informationen zur Datenaktualisierung für Gateways finden Sie unter [Verwenden der Datenquelle für geplanten Aktualisierungen](service-gateway-enterprise-manage-scheduled-refresh.md#use-the-data-source-for-scheduled-refresh).
