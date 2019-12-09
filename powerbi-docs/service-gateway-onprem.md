---
title: Lokales Datengateway
description: Dieser Artikel bietet einen Überblick über das lokale Datengateway für Power BI. Mithilfe dieses Gateways können Sie mit DirectQuery-Datenquellen arbeiten. Sie können damit außerdem die Clouddatasets mit lokalen Daten aktualisieren.
author: arthiriyer
ms.author: arthii
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
LocalizationGroup: Gateways
ms.date: 07/15/2019
ms.openlocfilehash: 96a006f60e08d35ef6bbe13a2033d866814ec5b2
ms.sourcegitcommit: f77b24a8a588605f005c9bb1fdad864955885718
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/02/2019
ms.locfileid: "74697541"
---
# <a name="what-is-an-on-premises-data-gateway"></a>Was ist ein lokales Datengateway?

[!INCLUDE [gateway-rewrite](includes/gateway-rewrite.md)]

Das lokale Datengateway fungiert als Brücke, die die schnelle und sichere Übertragung von Daten zwischen lokalen Daten (Daten, die nicht in der Cloud gespeichert sind) und mehreren Microsoft Cloud Services ermöglicht. Diese Clouddienste umfassen Power BI, PowerApps, Power Automate, Azure Analysis Services und Azure Logic Apps. Mithilfe eines Gateways können Organisationen Datenbanken und andere Datenquellen in ihren eigenen Netzwerken behalten, diese lokalen Daten aber sicher in Clouddiensten verwenden.

## <a name="how-the-gateway-works"></a>So funktioniert das Gateway

![Übersicht über Gateways](media/service-gateway-onprem/on-premises-data-gateway.png)

Weitere Informationen zur Funktionsweise des Gateways finden Sie unter [Architektur eines lokalen Datengateways](/data-integration/gateway/service-gateway-onprem-indepth).

## <a name="types-of-gateways"></a>Arten von Gateways

Es gibt zwei verschiedene Arten von Gateways für zwei verschiedene Szenarios:

* **Lokales Datengateway** ermöglicht mehreren Benutzern, eine Verbindung mit mehreren lokalen Datenquellen herzustellen. Sie können ein lokales Datengateway mit allen unterstützten Diensten mit einer einzigen Gatewayinstallation verwenden. Dieses Gateway eignet sich für komplexe Szenarios, in denen mehrere Benutzer auf mehrere Datenquellen zugreifen.

* **Lokales Datengateway (persönlicher Modus)** ermöglicht einem Benutzer die Verbindung mit Datenquellen und kann nicht für andere Benutzer freigegeben werden. Ein lokales Datengateway (persönlicher Modus) kann nur mit Power BI verwendet werden. Dieses Gateway eignet sich für Szenarios, in denen Sie die einzige Person sind, die Berichte erstellt, und Sie Datenquellen nicht für andere Personen freigeben müssen.

## <a name="use-a-gateway"></a>Verwenden eines Gateways

Die Verwendung eines Gateways besteht aus vier Hauptschritten.

1. [Laden Sie das Gateway herunter, und installieren Sie es](/data-integration/gateway/service-gateway-install) auf einem lokalen Computer.
1. [Konfigurieren](/data-integration/gateway/service-gateway-app) Sie das Gateway basierend auf Ihrer Firewall und anderen Netzwerkanforderungen.
1. [Fügen Sie Gatewayadministratoren](/data-integration/gateway/service-gateway-manage) hinzu, die auch andere Netzwerkanforderungen verwalten können.
1. [Verwenden Sie das Gateway](service-gateway-sql-tutorial.md), um eine lokale Datenquelle zu aktualisieren.
1. [Beheben Sie Probleme](service-gateway-onprem-tshoot.md) mit dem Gateway, falls Fehler auftreten.

## <a name="next-steps"></a>Nächste Schritte

* [Installieren des lokalen Datengateways](/data-integration/gateway/service-gateway-install)

Weitere Fragen? [Wenden Sie sich an die Power BI-Community](https://community.powerbi.com/)
