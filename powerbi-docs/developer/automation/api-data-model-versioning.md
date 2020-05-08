---
title: Versionsverwaltung für Power BI-Datenmodelle
description: Von einem OData-Dienst verfügbar gemachtes Datenmodell
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 06/08/2018
ms.openlocfilehash: 76947b1e311bbd1a21e09ce39461a70bed61d926
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "79079598"
---
# <a name="data-model-versioning"></a>Versionsverwaltung für Datenmodelle

Das Datenmodell, das von einem OData-Dienst wie dem Power BI-Datenmodell verfügbar gemacht wird, definiert einen Vertrag zwischen dem OData-Dienst und seinen Clients. Dienste können ihr Modell nur in dem Umfang erweitern, in dem vorhandene Clients nicht beeinträchtigt werden. Beeinträchtigende Änderungen, z. B. das Entfernen von Eigenschaften oder das Ändern des Typs von vorhandenen Eigenschaften erfordern, dass eine neue Dienstversion unter einem anderen Dienststamm-URL für das neue Modell bereitgestellt wird.  
  
Die folgenden Hinzufügungen zu Datenmodellen werden als sicher eingestuft und machen es nicht erforderlich, dass Dienste eine Versionsverwaltung ihres Einstiegspunkts vornehmen.  
  
* Hinzufügen einer Eigenschaft, die Nullwerte zulässt oder einen Standardwert aufweist. Wenn sie den gleichen Namen wie eine vorhandene dynamische Eigenschaft hat, muss sie den gleichen Typ (oder Basistyp) wie die vorhandene dynamische Eigenschaft aufweisen  
* Hinzufügen einer Navigationseigenschaft, die Nullwerte zulässt oder einen Sammlungswert aufweist. Wenn sie den gleichen Namen wie eine vorhandene dynamische Navigationseigenschaft hat, muss sie den gleichen Typ (oder Basistyp) wie die vorhandene dynamische Navigationseigenschaft aufweisen  
* Hinzufügen eines neuen Entitätstyps zum Modell  
* Hinzufügen eines neuen komplexen Typs zum Modell  
* Hinzufügen einer neuen Entitätenmenge  
* Hinzufügen eines neuen Singleton  
* Hinzufügen einer Aktion, einer Funktion, eines Aktionsimports oder eines Funktionsimports
* Hinzufügen eines Aktionsparameters, der Nullwerte zulässt  
* Hinzufügen einer Typdefinition oder -enumeration  
* Hinzufügen einer beliebigen Anmerkung zu einem Modellelement, die nicht vom Client verstanden werden muss, um ordnungsgemäß mit dem Dienst zu interagieren  
  
Clients ***SOLLTEN*** darauf vorbereitet sein, dass Dienste solche inkrementellen Änderungen an ihrem Modell vornehmen. Insbesondere sollten Clients darauf vorbereitet sein, Eigenschaften und abgeleitete Typen zu empfangen, die zuvor nicht vom Dienst definiert wurden.  
  
Dienste sollten ihr Datenmodell ***NICHT*** in Abhängigkeit vom authentifizierten Benutzer ändern. Ist das Datenmodell vom Benutzer oder einer Benutzergruppe abhängig, MUSS es sich bei allen Änderungen um sichere Änderungen handeln, wie sie in diesem Abschnitt definiert sind, wenn das vollständige Modell mit dem für Benutzer mit eingeschränkten Autorisierungen sichtbaren Modell verglichen wird.  
  
Weitere Informationen zu OData-Datenmodellstandards finden Sie unter [OData Version 4.0 Part 1: Protocol Plus Errata 02](https://docs.oasis-open.org/odata/odata/v4.0/odata-v4.0-part1-protocol.html).  
  
## <a name="see-also"></a>Siehe auch
[Übersicht über Power BI-REST-API](https://docs.microsoft.com/rest/api/power-bi/)