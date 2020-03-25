---
title: Anhalten und Starten einer Power BI Embedded-Kapazität im Azure-Portal | Microsoft-Dokumentation
description: In diesem Artikel erfahren Sie, wie Sie eine Power BI Embedded-Kapazität in Microsoft Azure anhalten und starten.
services: power-bi-embedded
author: KesemSharabi
ms.author: kesharab
editor: ''
tags: ''
ms.service: power-bi-embedded
ms.topic: conceptual
ms.date: 09/28/2017
ms.openlocfilehash: 07c9c12366b100936e03fe07358ee180e026dfc5
ms.sourcegitcommit: 2c798b97fdb02b4bf4e74cf05442a4b01dc5cbab
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/21/2020
ms.locfileid: "80114748"
---
# <a name="pause-and-start-your-power-bi-embedded-capacity-in-the-azure-portal"></a>Anhalten und Starten einer Power BI Embedded-Kapazität im Azure-Portal

In diesem Artikel erfahren Sie, wie Sie eine Power BI Embedded-Kapazität in Microsoft Azure anhalten und starten. Dies setzt voraus, dass Sie eine Power BI Embedded-Kapazität erstellt haben. Wenn das nicht der Fall ist, erfahren Sie mehr darüber unter [Erstellen einer Power BI Embedded-Kapazität im Azure-Portal](azure-pbie-create-capacity.md).

Wenn Sie kein Azure-Abonnement haben, erstellen Sie ein [kostenloses Konto](https://azure.microsoft.com/free/), bevor Sie beginnen.

## <a name="pause-your-capacity"></a>Anhalten einer Kapazität

Das Anhalten Ihrer Kapazität verhindert, dass sie berechnet wird. Diese Option ist sehr praktisch, wenn Sie eine Kapazität für eine bestimmte Zeitdauer nicht benötigen. Gehen Sie wie folgt vor, um Ihre Kapazität anzuhalten.

> [!NOTE]
> Wenn Sie eine Kapazität anhalten, sind Inhalte möglicherweise nicht in Power BI verfügbar. Heben Sie unbedingt die Zuweisung von Arbeitsbereichen vor dem Anhalten auf, um Unterbrechungen zu vermeiden.

1. Melden Sie sich beim [Azure-Portal](https://portal.azure.com/) an.

2. Wählen Sie **Alle Dienste** > **Power BI Embedded** aus, um Ihre Kapazitäten anzuzeigen.

    ![Alle Dienste im Azure-Portal](media/azure-pbie-pause-start/azure-portal-more-services.png)

3. Wählen Sie die Kapazität aus, die Sie anhalten möchten.

    ![Power BI Embedded-Kapazitätenliste im Azure-Portal](media/azure-pbie-pause-start/azure-portal-capacity-list.png)

4. Wählen Sie in den Kapazitätsdetails **Anhalten** aus.

    ![Anhalten einer Kapazität](media/azure-pbie-pause-start/azure-portal-pause-capacity.png)

5. Wählen Sie **Ja** aus, um zu bestätigen, dass Sie die Kapazität anhalten möchten.

    ![Bestätigen von „Anhalten“](media/azure-pbie-pause-start/azure-portal-confirm-pause.png)

## <a name="start-your-capacity"></a>Starten einer Kapazität

Setzen Sie die Nutzung fort, indem Sie Ihre Kapazität starten. Wenn Sie Ihre Kapazität starten, wird diese auch wieder berechnet.

1. Melden Sie sich beim [Azure-Portal](https://portal.azure.com/) an.

2. Wählen Sie **Alle Dienste** > **Power BI Embedded** aus, um Ihre Kapazitäten anzuzeigen.

    ![Alle Dienste im Azure-Portal](media/azure-pbie-pause-start/azure-portal-more-services.png)

3. Wählen Sie die Kapazität aus, die Sie starten möchten.

    ![Power BI Embedded-Kapazitätenliste im Azure-Portal](media/azure-pbie-pause-start/azure-portal-capacity-list.png)

4. Wählen Sie in den Kapazitätsdetails **Starten** aus.

    ![Starten einer Kapazität](media/azure-pbie-pause-start/azure-portal-start-capacity.png)

5. Wählen Sie **Ja** aus, um zu bestätigen, dass Sie die Kapazität starten möchten.

    ![Bestätigen von „Starten“](media/azure-pbie-pause-start/azure-portal-confirm-start.png)

Ist dieser Kapazität Inhalte zugeordnet sind, stehen diese nach dem Start zur Verfügung.

## <a name="next-steps"></a>Nächste Schritte

Wie Sie eine Kapazität hoch- oder herunterskalieren, erfahren Sie in Artikel [Skalieren einer Power BI Embedded-Kapazität](azure-pbie-scale-capacity.md).

Weitere Informationen zum Einbetten von Power BI-Inhalten in Ihre Anwendung finden Sie unter [Einbetten von Power BI-Berichten, -Dashboards, oder -Kacheln](https://powerbi.microsoft.com/documentation/powerbi-developer-embedding-content/).

Weitere Fragen? [Stellen Sie Ihre Frage in der Power BI-Community.](https://community.powerbi.com/)