---
title: Ausgehender Datenverkehr in Power BI und Azure
description: Informationen zu den Preisen für ausgehenden Datenverkehr in Azure und Power BI basierend auf dem Standort des Mandanten und Power BI Premium
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 05/08/2019
ms.author: davidi
LocalizationGroup: Data from databases
ms.openlocfilehash: b39812eb155d1d1c32ddba984986e5260f4b1ad1
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/13/2020
ms.locfileid: "83302228"
---
# <a name="power-bi-and-azure-egress"></a>Ausgehender Datenverkehr in Power BI und Azure

Wenn Sie Power BI mit Azure-Datenquellen verwenden, können Sie Kosten für ausgehenden Azure-Datenverkehr vermeiden, indem Sie darauf achten, dass sich Ihr Power BI-Mandant in derselben Region wie Ihre Azure-Datenquelle befindet.

Wenn Ihr Power BI-Mandant in der gleichen Azure-Region wie Ihre Datenquellen bereitgestellt wird, entstehen keine Kosten für ausgehenden Datenverkehr für geplante Aktualisierungen und DirectQuery-Interaktionen. 

## <a name="determining-where-your-power-bi-tenant-is-located"></a>Bestimmen der Region des Power BI-Mandanten

Im Artikel [Where is my Power BI tenant located?](../admin/service-admin-where-is-my-tenant-located.md) erfahren Sie, wie Sie herauszufinden, in welcher Region sich Ihr Power BI-Mandant befindet.

Wenn Sie Multi-Geo von Power BI Premium verwenden und sich ihr Power BI-Mandant nicht in der optimalen Region für einige Azure-basierte Datenquellen befindet, können Sie Multi-Geo von Power BI Premium in der gewünschten Azure-Region bereitstellen und so Ihren Power BI-Mandaten und die Azure-Datenquellen in derselben Azure-Region nutzen.

## <a name="next-steps"></a>Weitere Schritte

Weitere Informationen zu Power BI Premium oder Multi-Geo finden Sie in den folgenden Artikeln:

* [Was ist Microsoft Power BI Premium?](../admin/service-premium-what-is.md)
* [Erwerben von Power BI Premium](../admin/service-admin-premium-purchase.md)
* [Multi-Geo-Unterstützung für Power BI Premium (Vorschau)](../admin/service-admin-premium-multi-geo.md)
* [Wo befindet sich mein Power BI-Mandant?](../admin/service-admin-where-is-my-tenant-located.md)
* [Power BI Premium FAQ (Häufig gestellte Fragen zu Power BI Premium)](../admin/service-premium-faq.md)
