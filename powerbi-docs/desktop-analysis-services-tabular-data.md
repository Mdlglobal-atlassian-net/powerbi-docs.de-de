---
title: Verbinden mit tabellarischen Analysis Services-Daten in Power BI Desktop
description: Mit Power BI Desktop können Sie eine Verbindung mit tabellarischen Modellen von SQL Server Analysis Services herstellen und Daten aus diesen Modellen abrufen, indem Sie eine Liveverbindung verwenden oder Elemente für den Import in Power BI Desktop auswählen.
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 01/28/2020
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: ac15a732f3d388fd5dafa61d33eec1d82022da54
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "77464247"
---
# <a name="connect-to-analysis-services-tabular-data-in-power-bi-desktop"></a>Verbinden mit tabellarischen Analysis Services-Daten in Power BI Desktop
Mit Power BI Desktop verfügen Sie über zwei Möglichkeiten, eine Verbindung mit tabellarischen Modellen von SQL Server Analysis Services herzustellen und Daten aus diesen Modellen abzurufen: Durchsuchen mit Liveverbindung oder Auswählen und Importieren von Elementen in Power BI Desktop.

Sehen wir uns das einmal näher an.

**Erkunden mithilfe einer Liveverbindung:** Bei Verwendung einer Liveverbindung werden Elemente wie Tabellen, Spalten und Measures im tabellarischen Modell oder einer Perspektive in der Power BI Desktop-Bereichsliste **Felder** angezeigt. Die erweiterte Visualisierung und Bericht-Tools von Power BI Desktop bieten Ihnen neue und hoch interaktive Möglichkeiten zum Untersuchen Ihres tabellarischen Modells.

Bei einer Liveverbindung werden keine Daten aus dem tabellarischen Modell in Power BI Desktop importiert. Bei jeder Interaktion mit einer Visualisierung fragt Power BI Desktop das tabellarische Modell ab und berechnet die angezeigten Ergebnisse. Ihnen werden immer die aktuellsten Daten angezeigt, die entweder über den letzten Verarbeitungszeitpunkt oder über DirectQuery-Tabellen im tabellarischen Modell verfügbar sind. 

Beachten Sie, dass tabellarische Modelle eine hohe Sicherheit bieten. Die in Power BI Desktop angezeigten Elemente hängen von Ihren Berechtigungen für das tabellarische Modell ab, mit dem Sie verbunden sind.

Dynamische Berichte, die Sie in Power BI Desktop erstellt haben, können Sie durch die Veröffentlichung auf Ihrer Power BI-Website freigeben. Wenn Sie eine Power BI Desktop-Datei mit einer Liveverbindung mit einem tabellarischen Modell auf Ihrer Power BI-Website veröffentlichen möchten, muss ein lokales Datengateway installiert sein und von einem Administrator konfiguriert werden. Lesen Sie zu diesem Thema den Artikel [Lokales Datengateway](service-gateway-onprem.md).

**Auswählen und Importieren von Elementen in Power BI Desktop:** Wenn Sie eine Verbindung mit dieser Option herstellen, können Sie Elemente wie Tabellen, Spalten und Measures in Ihrem tabellarischen Modell bzw. einer Perspektive auswählen und in ein Power BI Desktop-Modell laden. Verwenden Sie den Power Query-Editor von Power BI Desktop, um die gewünschten Funktionen und die entsprechenden Modellierungsfunktionen weiter zu strukturieren und die Daten weiter zu modellieren. Da keine Liveverbindung zwischen Power BI Desktop und dem tabellarischen Modell verwaltet wird, können Sie das Power BI Desktop-Modell offline untersuchen oder auf Ihrer Power BI-Website veröffentlichen.

## <a name="to-connect-to-a-tabular-model"></a>So stellen Sie eine Verbindung mit einem tabellarischen Modell her
1. Klicken Sie in Power BI Desktop auf der Registerkarte **Home** auf **Daten abrufen** > **Mehr** > **Datenbank**.
   
1. Klicken Sie zunächst auf **SQL Server Analysis Services-Datenbank** und dann auf **Verbinden**.
   
   ![Klicken auf die Option „SQL Server Analysis Services-Datenbank“](media/desktop-analysis-services-tabular-data/pbid_sqlas_getdata_as.png)
3. Geben Sie im Fenster **SQL Server Analysis Services-Datenbank** den Namen des **Servers** ein, wählen Sie einen Verbindungsmodus aus, und klicken Sie dann auf **OK**.
   
   ![Fenster „SQL Server Analysis Services-Datenbank“](media/desktop-analysis-services-tabular-data/pbid_sqlas_getdata_as_server.png)
4. Dieser Schritt im Fenster **Navigator** hängt von dem von Ihnen ausgewählten Verbindungsmodus ab:

   - Wählen Sie ein tabellarisches Modell oder eine Perspektive aus, wenn Sie eine Liveverbindung herstellen.
  
      ![Auswählen eines tabellarischen Modells oder einer Perspektive im Navigator](media/desktop-analysis-services-tabular-data/pbid_sqlas_getdata_as_live.png)
   - Wählen Sie zum Auswählen von Elementen und Abrufen von Daten ein tabellarisches Modell oder eine Perspektive aus, und wählen Sie dann eine bestimmte Tabelle oder Spalte aus, die geladen werden soll. Klicken Sie auf **Abfragen bearbeiten**, um den Power Query-Editor zu öffnen und die Daten vor dem Laden zu strukturieren. Wenn Sie dies abgeschlossen haben, klicken Sie auf **Laden**, um die Daten in Power BI Desktop zu importieren.

      ![Auswählen einer zu ladenden Tabelle oder Spalte im Navigator](media/desktop-analysis-services-tabular-data/pbid_sqlas_getdata_as_select.png)

## <a name="frequently-asked-questions"></a>Häufig gestellte Fragen
**Frage:** Benötige ich ein lokales Datengateway?

**Antwort:** Das kommt darauf an. Wenn Sie Power BI Desktop verwenden, um eine Liveverbindung mit einem tabellarischen Modell herzustellen, jedoch keine Veröffentlichung auf Ihrer Power BI-Website beabsichtigen, benötigen Sie kein Gateway. Wenn Sie jedoch eine Veröffentlichung auf Ihrer Power BI-Website beabsichtigen, benötigen Sie ein Datengateway, um eine sichere Kommunikation zwischen dem Power BI-Dienst und dem lokalen Analysis Services-Server sicherzustellen. Wenden Sie sich unbedingt an Ihren Analysis Services Server-Administrator, bevor Sie ein Datengateway installieren.

Wenn Sie Elemente auswählen und Daten abrufen, importieren Sie tabellarische Modelldaten direkt in Ihre Power BI Desktop-Datei. Daher ist kein Gateway erforderlich.

**Frage:** Was ist der Unterschied zwischen einer Live-Verbindung mit einem tabellarischen Modell im Power BI-Dienst gegenüber einer Live-Verbindung in Power BI Desktop?

**Antwort:** Beim Herstellen einer Liveverbindung mit einem tabellarischen Modell Ihrer Website im Power BI-Dienst mit einer lokal in Ihrem Unternehmen vorhandenen Analysis Services-Datenbank ist ein lokales Datengateway erforderlich, um eine sichere Kommunikation zwischen diesen sicherzustellen. Beim Herstellen einer Liveverbindung mit einem tabellarischen Modell in Power BI Desktop benötigen Sie kein Gateway, da sowohl Power BI Desktop als auch der Analysis Services-Server, mit denen Sie die Verbindung herstellen, in Ihrer Organisation lokal ausgeführt werden. Wenn Sie jedoch Ihre Power BI Desktop-Datei auf Ihrer Power BI-Website veröffentlichen, ist ein Gateway erforderlich.

**Frage:** Kann ich, wenn ich eine Live-Verbindung hergestellt habe, auch eine Verbindung zu einer anderen Datenquelle in derselben Power BI Desktop-Datei herstellen?

**Antwort:** Nein. Sie können keine Livedaten untersuchen und auch keine Verbindung mit einem anderen Datenquellentyp in derselben Datei herstellen. Wenn Sie bereits Daten importiert oder eine Verbindung mit einer anderen Datenquelle in einer Power BI Desktop-Datei hergestellt haben, müssen Sie für eine Liveuntersuchung eine neue Datei erstellen.

**Frage:** Kann ich, wenn ich eine Live-Verbindung erstellt habe, das Modell oder die Abfrage in Power BI Desktop bearbeiten?

**Antwort:** Sie können in Power BI Desktop Measures auf Berichtsebene erstellen, aber alle anderen Abfrage- und Modellierungsfeatures sind beim Untersuchen von Livedaten deaktiviert.

**Frage:** Ist eine von mir erstellte Live-Verbindung sicher?

**Antwort:** Ja. Ihre aktuellen Windows-Anmeldeinformationen werden für die Verbindung mit dem Analysis Services-Server verwendet. Sie können Standard- oder gespeicherte Anmeldeinformationen bei der Liveuntersuchung weder im Power BI-Dienst noch in Power BI Desktop verwenden.

**Frage:** Im Navigator werden ein Modell und eine Perspektive angezeigt. Was ist der Unterschied?

**Antwort:** Eine Perspektive ist eine bestimmte Ansicht eines tabellarischen Modells. Sie enthält ggf. nur bestimmte Tabellen, Spalten oder Maße in Abhängigkeit von einem speziellen Datenanalysebedarf. Ein tabellarisches Modell enthält immer mindestens eine-Perspektive, die alles, was im Modell enthalten ist, umfassen kann. Wenden Sie sich an Ihren Administrator, wenn Sie nicht sicher sind, welche Perspektive Sie auswählen sollen.

**Frage:** Gibt es Funktionen von Analysis Services, die das Verhalten von Power BI verändern?

**Antwort:** Ja. Abhängig von den Funktionen, die Ihr tabellarisches Modell verwendet, kann sich die Benutzeroberfläche in Power BI Desktop ändern. Beispiele hierfür sind:
* Möglicherweise werden die Measures im Modell oben in der Bereichsliste **Felder** gruppiert und nicht in Tabellen neben den Spalten angezeigt. Sie können diese trotzdem wie gewohnt verwenden. Es ist nur einfacher, sie auf diese Weise zu finden.

* Wenn im tabellarischen Modell Berechnungsgruppen definiert sind, können Sie diese nur in Verbindung mit Modellmeasures und nicht mit impliziten Measures verwenden, die Sie durch Hinzufügen von numerischen Feldern zu einem Visual erstellen. Das Modell könnte auch das Flag **DiscourageImplicitMeasures** manuell festgelegt haben, was den gleichen Effekt hat. Weitere Informationen finden Sie unter [Berechnungsgruppen in Analysis Services](https://docs.microsoft.com/analysis-services/tabular-models/calculation-groups#benefits).

## <a name="to-change-the-server-name-after-initial-connection"></a>So ändern Sie den Namen des Servers nach der ersten Verbindung
Nachdem Sie eine Power BI Desktop-Datei mit einer Liveverbindung erstellt haben, kann es in einigen Fällen erforderlich sein, die Verbindung auf einen anderen Server umzuschalten. Wenn Sie beispielsweise Ihre Power BI-Desktop-Datei bei der Verbindung mit einem Entwicklungsserver und vor der Veröffentlichung im Power BI-Dienst erstellt haben, möchten Sie die Verbindung zum Produktionsserver umschalten.

So ändern Sie den Servernamen:

1. Klicken Sie auf der Registerkarte **Home** auf **Abfragen bearbeiten**.

2. Geben Sie im Fenster **SQL Server Analysis Services-Datenbank** den neuen Namen des **Servers** ein, und klicken Sie dann auf **OK**.

   
## <a name="troubleshooting"></a>Problembehandlung 
In der folgenden Liste sind alle bekannten Probleme beim Herstellen einer Verbindung mit SQL Server Analysis Services (SSAS) und Azure Analysis Services aufgeführt: 

* **Fehler: Das Modellschema konnte nicht geladen werden**: Dieser Fehler tritt normalerweise nur dann auf, wenn der Benutzer, der eine Verbindung mit Analysis Services herstellt, keine Zugriffsberechtigungen für die Datenbank bzw. das Modell besitzt.

