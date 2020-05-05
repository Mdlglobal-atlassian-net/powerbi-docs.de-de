---
title: Mobile-Entwicklung
description: Erstellen von für mobile Geräte optimierten Power BI-Visuals
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: how-to
ms.date: 03/12/2019
ms.openlocfilehash: 38e6ac3be143381304f1fdfc8e1427b91f398a9a
ms.sourcegitcommit: 1059c6222458f189fb5301dcb689dad2b2c00bc1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/28/2020
ms.locfileid: "82196627"
---
# <a name="how-to-create-mobile-friendly-power-bi-visuals"></a>Erstellen von für mobile Geräte optimierten Power BI-Visuals
Die Nutzung auf mobilen Geräten spielt bei Power BI eine entscheidende Rolle. Einer der Vorteile des Diensts ist es, mit seinen Daten immer und überall in Verbindung bleiben zu können.

Als Entwickler müssen Sie beim Erstellen von Power BI-Visuals die speziellen Einschränkungen jedes mobilen Geräts berücksichtigen, um so viele Benutzer wie möglich erreichen zu können und die bestmögliche Servicequalität bieten zu können.

Verwenden Sie die [Power BI-Apps für Windows, iOS und Android](/power-bi/consumer/mobile/mobile-apps-for-mobile-devices), damit Ihre Unternehmenskunden auch unterwegs mit nur einem Fingertipp einen umfassenden Überblick über ihre Daten erhalten können.

## <a name="requirements"></a>Anforderungen

Die folgenden Anforderungen sind wichtig für die Entwicklung von für mobile Geräte optimierten Visuals:

- Rendern

  Ihre Power BI-Visuals müssen auf allen unterstützten mobilen Geräten gerendert werden können, einschließlich unterstützter Browser und Anwendungen. Dabei dürfen keine Fehler in Berichten, Dashboards oder bei der Ausführung im **Fokusmodus** auftreten. 

- Interactive

  Interaktive Funktionen müssen auf dieselbe Weise verfügbar sein, wie sie auch für Desktopgeräte zur Verfügung stehen. Alle Ereignisse, die in Desktopbrowsern verarbeitet werden können, müssen unterstützt werden, oder es muss vergleichbare Ereignishandler für mobile Geräte geben.
  
  Die grundlegende Navigation und die Auswahl von Datenpunkten sollten beispielsweise die gleichen Funktionen wie bei Desktopbrowsern aufweisen. Wenn ein Visual die Mehrfachauswahl mithilfe von **STRG** unterstützt, muss der Entwickler dies berücksichtigen, indem er einen ähnlichen Ereignishandler für mobile Geräte hinzufügt.

  In der folgenden Tabelle finden Sie eine Liste der entsprechenden Ereignisse auf mobilen Geräten.

  | Name des Mauseingabeereignisses | Name des Fingereingabeereignisses |
  |:----------------:|:----------------:|
  | `click` | `click` |
  | `mousemove` | `touchmove` |
  | `mousedown` | `touchstart` |
  | `mouseup` | `touchend` |
  | `dblclick` | Verwenden externer Bibliotheken |
  | `contextmenu` | Verwenden externer Bibliotheken |
  | `mouseover` | `touchmove` |
  | `mouseout` | `touchmove` (oder Verwenden externer Bibliotheken) |
  | `wheel` | `NaN` |

  > [!NOTE]
  > Nicht alle mobilen Geräte oder Geräte mit Touchscreen unterstützen Mauseingabeereignisse oder Ereignisse mit dem Präfix *mouse*. In solchen Fällen sollten sowohl *Mauseingabeereignisse* als auch *Fingereingabeereignisse* gleichzeitig verarbeitet werden.

## <a name="optional"></a>Optional
Die folgenden Punkte sind als optional zu verstehen und werden verwendet, um eine bessere Servicequalität für Endbenutzer zu ermöglichen.

- Rendern

  Wenn Sie kleinere Visualgrößen unterstützen möchten, können Sie Formatoptionen hinzufügen, die der Benutzer ändern kann, um die Größe der einzelnen Elemente anzupassen. Fügen Sie beispielsweise Labels Formatoptionen zur Verwendung in Berichten und Dashboards hinzu. So können Benutzer ein Visual genau auf ihr mobiles Gerät anpassen.
  
  Dieselben Einstellungen können auch auf Visuals in Desktopbrowsern angewendet werden und bei Bedarf überschrieben werden, um das Visual an kleinere Bildschirme anzupassen.

  > [!NOTE]
  > Wenn Sie ein Visual für den **Fokusmodus** optimieren möchten, muss sowohl die Ausrichtung der Bildschirmgröße im Hochformat als auch im Querformat bedacht werden. Unter [Anzeigen von Inhalten im Detail: Fokusmodus und Vollbildmodus](/power-bi/consumer/end-user-focus) finden Sie weitere Informationen dazu.

- Interactive

  Gegebenenfalls können Sie für bestimmte mobile Geräte spezifische Ereignishandler hinzufügen, z. B. für das Ziehen und Scrollen.

- Failover

  Ein Visual sollte eine beschreibende Fehlermeldung anzeigen, wenn es auf einem mobilen Gerät nicht gerendert werden kann.

## <a name="supported-browsers-and-devices"></a>Unterstützte Browser und Geräte
Das Power BI-Visual muss auf allen Geräten gerendert werden können, die Power BI-Apps unterstützen. Weitere Informationen finden Sie unter [Unterstützte Browser für Power BI](/power-bi/power-bi-browsers) und [Was sind die mobilen Power BI-Apps?](/power-bi/consumer/mobile/mobile-apps-for-mobile-devices).

Beim Testen des Visuals für die aktuellen Modelle von Windows-, iOS- und Android-Geräten muss der Entwickler die meisten dieser Qualitätsaspekte berücksichtigen.

## <a name="next-steps"></a>Nächste Schritte
Informationen zu den ersten Schritten finden Sie unter [Tutorial: Entwickeln eines Power BI-Visuals](/power-bi/developer/visuals/custom-visual-develop-tutorial).
