---
ms.openlocfilehash: cd0696b44e285119193059304c89cfa04c755771
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "71409363"
---
## <a name="faq"></a>Häufig gestellte Fragen
**Frage:** Was passiert, wenn ich im Power BI-Dienst bereits Rollen und Regeln für ein Dataset erstellt habe? Werden sie weiterhin funktionieren, wenn ich sie so belasse?  
**Antwort:** Nein. Visuals werden nicht richtig gerendert. Sie müssen die Rollen und Regeln in Power BI Desktop neu erstellen und anschließend im Power BI-Dienst veröffentlichen.

**Frage:** Kann ich solche Rollen für Analysis Services-Datenquellen erstellen?  
**Antwort:** Das ist möglich, wenn Sie die Daten in Power BI Desktop importiert haben. Wenn Sie eine Liveverbindung verwenden, werden Sie RLS nicht im Power BI-Dienst konfigurieren können. Dies wird im lokalen Analysis Services-Modell definiert.

**Frage:** Kann ich mit der RLS die Spalten oder Measures einschränken, auf die Benutzer Zugriff haben?  
**Antwort:** Nein. Wenn ein Benutzer Zugriff auf eine bestimmte Datenzeile hat, sind alle Datenspalten dieser Zeile für ihn sichtbar.

**Frage:** Kann ich mit der RLS Detaildaten in Visuals ausblenden und Zugriff auf in Visuals zusammengefasste Daten erteilen?  
**Antwort:** Nein. Sie sichern einzelne Datenzeilen, für die Benutzer werden jedoch immer entweder die Details oder die zusammengefassten Daten angezeigt.

**Frage:** Für meine Datenquelle sind bereits Sicherheitsrollen definiert (z. B. SQL Server-Rollen oder SAP BW-Rollen). Worin besteht die Beziehung zwischen diesen und RLS?  
**Antwort:** Die Antwort hängt davon ab, ob Sie Daten importieren oder DirectQuery verwenden. Wenn Sie Daten in das Power BI-Dataset importieren, werden die Sicherheitsrollen in der Datenquelle nicht verwendet. In diesem Fall sollten Sie RLS definieren, um Sicherheitsregeln für Benutzer zu erzwingen, die in Power BI eine Verbindung herstellen. Wenn Sie DirectQuery verwenden, werden die Sicherheitsrollen in Ihrer Datenquelle verwendet. Wenn ein Benutzer einen Bericht öffnet, sendet Power BI eine Abfrage an die zugrunde liegende Datenquelle, die Sicherheitsregeln für die Daten basierend auf den Anmeldeinformationen des Benutzers anwendet.
