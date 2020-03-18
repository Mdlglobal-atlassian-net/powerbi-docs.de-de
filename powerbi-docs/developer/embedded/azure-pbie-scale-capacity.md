---
title: Skalieren einer Power BI Embedded-Kapazität | Microsoft-Dokumentation
description: In diesem Artikel erfahren Sie, wie Sie eine Power BI Embedded-Kapazität in Microsoft Azure skalieren.
services: power-bi-embedded
author: KesemSharabi
ms.author: kesharab
editor: ''
tags: ''
ms.service: power-bi-embedded
ms.topic: how-to
ms.date: 01/31/2019
ms.openlocfilehash: 18ce2f9b89e78fee3856bf1ceb93805ebc4d27b9
ms.sourcegitcommit: a175faed9378a7d040a08ced3e46e54503334c07
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/18/2020
ms.locfileid: "79495617"
---
# <a name="scale-your-power-bi-embedded-capacity-in-the-azure-portal"></a>Skalieren einer Power BI Embedded-Kapazität im Azure-Portal

In diesem Artikel erfahren Sie, wie Sie eine Power BI Embedded-Kapazität in Microsoft Azure skalieren. Durch Skalierung können Sie Ihre Kapazität erweitern oder reduzieren.

Dies setzt voraus, dass Sie eine Power BI Embedded-Kapazität erstellt haben. Wenn das nicht der Fall ist, erfahren Sie mehr darüber unter [Erstellen einer Power BI Embedded-Kapazität im Azure-Portal](azure-pbie-create-capacity.md).

> [!NOTE]
> Ein Skalierungsvorgang dauert ca. eine Minute. Währenddessen ist die Kapazität nicht verfügbar. Eingebettete Inhalte können dann möglicherweise nicht geladen werden.

## <a name="scale-a-capacity"></a>Skalieren einer Kapazität

1. Melden Sie sich beim [Azure-Portal](https://portal.azure.com/) an.

2. Wählen Sie **Alle Dienste** > **Power BI Embedded** aus, um Ihre Kapazitäten anzuzeigen.

    ![Alle Dienste im Azure-Portal](media/azure-pbie-scale-capacity/azure-portal-more-services.png)

3. Wählen Sie die Kapazität aus, die Sie skalieren möchten.

    ![Power BI Embedded-Kapazitätenliste im Azure-Portal](media/azure-pbie-scale-capacity/azure-portal-capacity-list.png)

4. Wählen Sie in Ihrer Kapazität unter **Skalieren** **Tarif** aus.

    ![Option „Tarif“ unter „Skalieren“](media/azure-pbie-scale-capacity/azure-portal-scale-pricing-tier.png)

    Ihr aktueller Tarif wird blau hervorgehoben.

    ![Blaue Hervorhebung des aktuellen Tarifs](media/azure-pbie-scale-capacity/azure-portal-current-tier.png)

5. Wählen Sie den neuen Tarif aus, zu dem Sie wechseln möchten, um hoch- oder herunterzuskalieren. Wenn Sie einen neuen Tarif auswählen, wird er durch eine gestrichelte blaue Umrandung hervorgehoben. Wählen Sie **Auswählen** aus, um den neuen Tarif zu skalieren.

    ![Auswählen eines neuen Tarifs](media/azure-pbie-scale-capacity/azure-portal-select-new-tier.png)

    Das Skalieren Ihrer Kapazität dauert ein bis zwei Minuten.

6. Bestätigen Sie Ihren Tarif in der Registerkarte „Übersicht“. Der aktuelle Tarif wird angezeigt.

    ![Bestätigen des aktuellen Tarifs](media/azure-pbie-scale-capacity/azure-portal-confirm-tier.png)

## <a name="next-steps"></a>Nächste Schritte

Wie Sie Ihre Kapazität anhalten oder starten, erfahren Sie unter [Anhalten und Starten einer Power BI Embedded-Kapazität im Azure-Portal](azure-pbie-pause-start.md).

Weitere Informationen zum Einbetten von Power BI-Inhalten in Ihre Anwendung finden Sie unter [Einbetten von Power BI-Berichten, -Dashboards, oder -Kacheln](https://powerbi.microsoft.com/documentation/powerbi-developer-embedding-content/).

Weitere Fragen? [Stellen Sie Ihre Frage in der Power BI-Community.](https://community.powerbi.com/)
