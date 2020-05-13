---
title: Häufig gestellte Fragen zum lokalen Datengateway – Power BI
description: Dieser Artikel enthält häufig gestellte Fragen zum lokalen Datengateway für Power BI. Hier werden häufig gestellte Fragen für das in Power BI verwendete Gateway zentral gesammelt.
author: arthiriyer
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: conceptual
ms.date: 07/15/2019
ms.author: arthii
LocalizationGroup: Gateways
ms.openlocfilehash: f64fcd86d54c20e1318d38c2a73e9bca2174558a
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/13/2020
ms.locfileid: "83302665"
---
# <a name="on-premises-data-gateway-faq---power-bi"></a>Häufig gestellte Fragen zum lokalen Datengateway – Power BI

[!INCLUDE [gateway-rewrite](../includes/gateway-rewrite.md)]

## <a name="power-bi"></a>Power BI

**Frage:** Muss ich ein Upgrade für das lokales Datengateway (persönlicher Modus) durchführen?

**Antwort:** Nein, Sie können weiterhin das Datengateway im persönlichen Modus für Power BI verwenden.

**Frage:** Sind besondere Berechtigungen erforderlich, um das Gateway zu installieren und im Power BI-Dienst zu verwalten?

**Antwort:** Es sind keine besonderen Berechtigungen erforderlich.

**Frage:** Kann ich Excel-Arbeitsmappen mit Power Pivot-Datenmodellen hochladen, die Verbindungen mit lokalen Datenquellen herstellen? Benötige ich bei diesem Szenario ein Gateway? 

**Antwort:** Ja, Sie können die Arbeitsmappe hochladen. Sie benötigen aber kein Gateway. Da die Daten sich im Excel-Datenmodell befinden, sind Berichte in Power BI, die auf der Excel-Arbeitsmappe beruhen, jedoch nicht live. Um Berichte in Power BI zu aktualisieren, müssen Sie jedes Mal wieder eine aktualisierte Arbeitsmappe hochladen. Verwenden Sie alternativ das Gateway mit geplanter Aktualisierung.

**Frage:** Wenn Benutzer Dashboards freigeben, die eine DirectQuery-Verbindung verwenden, können die anderen Benutzer die Daten auch dann sehen, wenn sie nicht über die gleichen Berechtigungen verfügen? 

**Antwort:** Wenn ein Dashboard mit Azure Analysis Services verbunden ist, können Benutzer nur die Daten sehen, auf die sie Zugriff haben. Wenn die Benutzer nicht über die gleichen Berechtigungen verfügen, werden ihnen keine Daten angezeigt. Bei anderen Datenquellen verwenden alle Benutzer die gleichen Anmeldeinformationen, die vom Administrator für diese Datenquelle eingegeben wurden.

**Frage:** Warum kann ich keine Verbindung mit meinem Oracle-Server aufbauen? 

**Antwort:** Möglicherweise müssen Sie den Oracle-Client installieren und in der Datei „tnsnames.ora“ die benötigten Serverdaten eintragen, um die Verbindung mit dem Oracle-Server herzustellen. Diese Installation erfolgt separat außerhalb des Gateways. Weitere Informationen finden Sie unter [Installieren des Oracle-Clients](service-gateway-onprem-manage-oracle.md#install-the-oracle-client).

**Frage:** Ich verwende R-Skripts. Wird dies unterstützt?

**Antwort**: R-Skripts werden nur für den persönlichen Modus unterstützt.

## <a name="analysis-services-in-power-bi"></a>Analysis Services in Power BI

**Frage:** Kann „msdmpump.dll“ zum Erstellen eigener Zuordnungen zu effektiven Benutzernamen für Analysis Services verwendet werden? 

**Antwort:** Nein. Dies wird zurzeit nicht unterstützt.

**Frage:** Kann das Gateway für Verbindungen mit einer mehrdimensionalen (OLAP-) Instanz verwendet werden? 

**Antwort:** Ja. Das lokale Datengateway unterstützt Liveverbindungen mit Tabellen- und mehrdimensionalen Modellen von Analysis Services.

**Frage:** Was geschieht, wenn ich das Gateway auf einem Computer in einer anderen Domäne als dem lokalen Server installiere, der die Windows-Authentifizierung verwendet? 

**Antwort:** Dafür geben wir keine Garantien. Es hängt alles von der Vertrauensstellung zwischen den beiden Domänen ab. Wenn sich die zwei verschiedenen Domänen in einem vertrauenswürdigen Domänenmodell befinden, ist das Gateway möglicherweise in der Lage, eine Verbindung mit dem Analysis Services-Server herzustellen, und der effektive Benutzername kann aufgelöst werden. Falls nicht, treten bei der Anmeldung möglicherweise Fehler auf.

**Frage:** Wie kann ich herausfinden, welcher effektive Benutzername an meine lokalen Analysis Services-Server übergeben wird? 

**Antwort:** Wir beantworten diese Frage im [Artikel zur Problembehandlung](service-gateway-onprem-tshoot.md).

## <a name="next-steps"></a>Nächste Schritte

* [Problembehandlung beim lokalen Datengateway](/data-integration/gateway/service-gateway-tshoot)

Weitere Fragen? Wenden Sie sich an die [Power BI-Community](https://community.powerbi.com/).
