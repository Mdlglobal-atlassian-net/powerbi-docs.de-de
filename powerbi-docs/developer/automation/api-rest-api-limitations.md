---
title: Einschränkungen für Power BI-REST-API
description: 'Für die Power BI-REST-API gelten die folgenden Einschränkungen:'
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 06/08/2018
ms.openlocfilehash: 5f4067e77631f22951844c0d4d64b06e5e2e30cc
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "79079575"
---
# <a name="power-bi-rest-api-limitations"></a>Einschränkungen für Power BI-REST-API  
  
**Bereitstellen von Zeilen mit POST**
  
* Max. 75 Spalten
* Max. 75 Tabellen
* Max. 10.000 Zeilen pro einzelner POST-Zeilenanforderung  
* 1\.000.000 Zeilen pro Stunde und Dataset hinzugefügt  
* Max. 5 ausstehende POST-Zeilenanforderungen pro Dataset  
* 120 POST-Zeilenanforderungen pro Minute und Dataset
* 120 POST-Zeilenanforderungen pro Stunde und Dataset, wenn die Tabelle aus mindestens 250.000 Zeilen besteht
* Max. 200.000 Zeilen pro Tabelle im FIFO-Dataset gespeichert
* Max. 5.000.000 Zeilen pro Tabelle in einem Dataset ohne Aufbewahrungsrichtlinie gespeichert  
* 4\.000 Zeichen pro Wert für Zeichenfolgenspalten in POST-Zeilenvorgängen
  
## <a name="see-also"></a>Siehe auch

* [Dienst- und andere Einschränkungen für Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-service-limits-restrictions)   
* [Übersicht über Power BI-REST-API](https://docs.microsoft.com/rest/api/power-bi/)