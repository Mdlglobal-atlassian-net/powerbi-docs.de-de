---
title: Leitfaden zum Bereitstellen eines Datengateways für Power BI
description: Informationen zu bewährten Methoden und Überlegungen für das Bereitstellen eines Gateways für Power BI.
author: arthiriyer
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: conceptual
ms.date: 07/15/2019
ms.author: arthii
LocalizationGroup: Gateways
ms.openlocfilehash: 3cb11f3faf9b9da5872cf2dba67222760c720f23
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/13/2020
ms.locfileid: "83329966"
---
# <a name="guidance-for-deploying-a-data-gateway-for-power-bi"></a>Leitfaden zum Bereitstellen eines Datengateways für Power BI

[!INCLUDE [gateway-rewrite](../includes/gateway-rewrite.md)]

Dieser Artikel bietet eine Anleitung sowie Überlegungen zur Bereitstellung eines Datengateways für Power BI in Ihrer Netzwerkumgebung.

Informationen zum Herunterladen, Installieren, Konfigurieren und Verwalten des lokalen Datengateways finden Sie unter [Was ist ein lokales Datengateway?](/data-integration/gateway/service-gateway-onprem). Weitere Informationen zum lokalen Datengateway und Power BI finden Sie zudem im [Microsoft Power BI-Blog](https://powerbi.microsoft.com/blog/) und in der [Microsoft Power BI-Community](https://community.powerbi.com/).

## <a name="installation-considerations-for-the-on-premises-data-gateway"></a>Hinweise zur Installation für das lokale Datengateway

Bevor Sie das lokale Datengateway für Ihren Power BI-Clouddienst installieren, müssen Sie verschiedene Punkte beachten. Dies wird in den folgenden Abschnitten beschrieben.

### <a name="number-of-users"></a>Anzahl von Benutzern

Die Anzahl der Benutzer, die einen Bericht nutzen, der das Gateway verwendet, ist eine wichtige Metrik bei der Entscheidung, wo das Gateway installiert werden soll. Hier sind einige Fragen, die es zu berücksichtigen gilt:

* Verwenden Benutzer diese Berichte zu unterschiedlichen Tageszeiten?
* Welche Arten von Verbindungen werden von ihnen verwendet (DirectQuery oder Import)?
* Verwenden alle Benutzer denselben Bericht?

Wenn alle Benutzer gleichzeitig auf einen bestimmten Bericht zugreifen, stellen Sie sicher, dass Sie das Gateway auf einem Computer installieren, der alle diese Anforderungen verarbeiten kann. In den folgenden Abschnitten finden Sie Leistungsindikatoren und Mindestanforderungen, mit deren Hilfe Sie bestimmen können, ob ein Computer in Frage kommt.

Eine Einschränkung in Power BI ist, dass nur *ein* Gateway pro *Bericht* zulässig ist. Auch wenn ein Bericht auf mehreren Datenquellen basiert, müssen alle Datenquellen über ein einzelnes Gateway geleitet werden. Wenn ein Dashboard auf *mehreren* Berichten basiert, können Sie für jeden beitragenden Bericht ein dediziertes Gateway verwenden. Auf diese Weise verteilen Sie die Gatewaylast auf mehrere Berichte, die Daten zum einzigen Dashboard beitragen.

### <a name="connection-type"></a>Verbindungstyp

Power BI bietet zwei Arten von Verbindungen: DirectQuery und Import. Nicht alle Datenquellen unterstützen beide Verbindungstypen. Viele Faktoren können zu Ihrer Wahl beitragen, z. B. Sicherheitsanforderungen, Leistung, Datengrenzwerte und Datenmodellgrößen. Weitere Informationen zu Verbindungstypen und unterstützten Datenquellen finden Sie in der [Liste der verfügbaren Datenquellentypen](service-gateway-data-sources.md#list-of-available-data-source-types).

Je nachdem, welcher Verbindungstyp verwendet wird, kann die Gatewaynutzung variieren. Versuchen Sie z.B. DirectQuery-Datenquellen nach Möglichkeit von Datenquellen mit geplanter Aktualisierung zu trennen. Dabei wird angenommen, dass Sie sich in verschiedenen Berichten befinden und getrennt werden können.
 Durch das Trennen von Quellen wird verhindert, dass sich im Gateway tausende DirectQuery-Anforderungen in der Warteschlange befinden, wenn gleichzeitig die morgendlich geplante Aktualisierung eines großen Datenmodells stattfindet, das für das Hauptdashboard des Unternehmens verwendet wird.
 

Berücksichtigen Sie deshalb für jede Option Folgendes:

* **Geplante Aktualisierung**: Je nach Abfragegröße und Anzahl der Aktualisierungen pro Tag können Sie sich zwischen den empfohlenen Mindestanforderungen für die Hardware und dem Upgrade auf einen Computer mit höherer Leistung entscheiden. Wenn eine bestimmte Abfrage nicht gefaltet ist, erfolgen auf dem Gatewaycomputer Transformationen. Dadurch profitiert der Gatewaycomputer von mehr verfügbarem RAM.

* **DirectQuery**: Jedes Mal, wenn ein Benutzer den Bericht öffnet oder Daten ansieht, wird eine Abfrage gesendet. Wenn Sie erwarten, dass mehr als 1.000 Benutzer gleichzeitig auf die Daten zugreifen, müssen Sie sicherstellen, dass Ihr Computer über zuverlässige und leistungsfähige Hardwarekomponenten verfügt. Für eine DirectQuery-Verbindung führen mehr CPU-Kerne zu einem besseren Durchsatz.

Informationen zu den Anforderungen an die Computerinstallation finden Sie in den [Installationsanforderungen](/data-integration/gateway/service-gateway-install#requirements) für das lokale Datengateway.

### <a name="location"></a>Standort

Der Speicherort der Gatewayinstallation kann erhebliche Auswirkungen auf die Abfrageleistung haben. Stellen Sie sicher, dass der physische Abstand zwischen Ihrem Gateway, den Speicherorten der Datenquellen und dem Power BI-Mandanten so gering wie möglich ist, um die Netzwerklatenz zu minimieren.
 Um den Speicherort Ihres Power BI-Mandaten im Power BI-Dienst zu bestimmen, wählen Sie das Fragezeichen **?** Symbol rechts oben. Wählen Sie dann **Info** aus.

![Ermitteln des Speicherorts des Power BI-Mandanten](media/service-gateway-deployment-guidance/powerbi-gateway-deployment-guidance_02.png)

Wenn Sie das Power BI-Gateway mit Azure Analysis Services verwenden möchten, stellen Sie sicher, dass die Datenbereiche übereinstimmen. Weitere Informationen zum Festlegen von Datenbereichen für mehrere Dienste finden Sie in [diesem Video](https://guyinacube.com/2018/01/power-bi-azure-analysis-services-gateway-data-region/).

## <a name="next-steps"></a>Nächste Schritte

* [Konfigurierung von Proxyeinstellungen](/data-integration/gateway/service-gateway-proxy)  
* [Lokales Datengateway – Power BI](service-gateway-onprem-tshoot.md)  
* [On-premises data gateway FAQ - Power BI (Häufig gestellte Fragen zum lokalen Datengateway – Power BI)](service-gateway-power-bi-faq.md)  

Weitere Fragen? Wenden Sie sich an die [Power BI-Community](https://community.powerbi.com/).
