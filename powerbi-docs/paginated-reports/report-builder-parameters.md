---
title: Berichtsparameter im Berichts-Generator von Power BI
description: In diesem Thema werden allgemeine Verwendungsmöglichkeiten für Berichtsparameter im Power BI Report Builder, die Eigenschaften, die Sie festlegen können, und vieles mehr beschrieben.
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.custom: ''
ms.date: 06/06/2019
ms.openlocfilehash: 823f2ea621d16eb911284cadeced2fb676fa5c75
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "78923055"
---
# <a name="report-parameters-in-power-bi-report-builder"></a>Berichtsparameter im Berichts-Generator von Power BI

In diesem Thema werden allgemeine Verwendungsmöglichkeiten für Berichtsparameter im Power BI Report Builder, die Eigenschaften, die Sie festlegen können, und vieles mehr beschrieben. Mithilfe von Berichtsparametern können Sie Berichtsdaten steuern, verwandte Berichte miteinander verbinden und die Berichtspräsentation anpassen. Sie können Berichtsparameter in paginierten Berichten verwenden, die Sie im Berichts-Generator erstellen.

## <a name="common-uses-for-parameters"></a><a name="bkmk_Common_Uses_for_Parameters"></a> Allgemeine Verwendungsmöglichkeiten für Parameter

 Im Folgenden sind einige der häufigsten Verwendungsmöglichkeiten für Parameter aufgeführt.  
  
**Steuern von Daten in paginierten Berichten**
  
- Filtern Sie Daten in paginierten Berichten an der Datenquelle, indem Sie Datasetabfragen schreiben, die Variablen enthalten.  
  
- Ermöglichen Sie Benutzern, Werte anzugeben, um die Daten in einem paginierten Bericht anzupassen. Stellen Sie beispielsweise zwei Parameter für das Startdatum und Enddatum für Vertriebsdaten bereit.  
  
**Variieren der Berichtspräsentation**
  
- Ermöglichen Sie Benutzern, Werte anzugeben, um die Darstellung eines Berichts anzupassen. Beispiel: Angabe eines booleschen Parameters, um anzugeben, ob alle geschachtelten Zeilengruppen in einer Tabelle erweitert oder reduziert werden sollen.  
  
- Ermöglichen Sie Benutzern das Anpassen von Berichtsdaten und der Darstellung von Berichten, indem Sie Parameter in einen Ausdruck einschließen.  
  
## <a name="viewing-a-report-with-parameters"></a><a name="UserInterface"></a> Anzeigen von paginierten Berichten mit Parametern

Wenn Sie einen Bericht mit Parametern anzeigen, zeigt die Symbolleiste der Berichtanzeige jeden Parameter an, sodass Sie interaktiv Werte angeben können. Die folgende Abbildung zeigt den Bereich „Parameter“ für einen Bericht mit Parametern für @ReportMonth, @ReportYear, @EmployeeID, @ShowAll, @ExpandTableRows, @CategoryQuota und @SalesDate.  

![Anzeigen eines Berichts mit Parametern](media/report-builder-parameters/report-builder-parameters-power-bi-service.png "Anzeigen von Berichten mit Parametern")
  
1. **Bereich „Parameter“** : In der Symbolleiste der Berichtanzeige wird eine Eingabeaufforderung und der Standardwert jedes Parameters angezeigt. Im Bereich „Parameter“ können Sie das Layout von Parametern anpassen.  
  
2. **@SalesDate Parameter** Parameters @SalesDate Datentyp **"DateTime"** . Neben dem Textfeld wird die Eingabeaufforderung „Select the Date“ (Wählen Sie das Datum aus) angezeigt. Wenn Sie das Datum ändern möchten, geben Sie ein neues Datum in das Textfeld ein, oder verwenden Sie das Kalendersteuerelement.  
  
3. **@ShowAll Parameter** Parameters @ShowAll Datentyp **booleschen**. Verwenden Sie die Optionsfelder, um **True** oder **False** anzugeben.  
  
4. **Ein- oder Ausblenden des Handles für Parameterbereich**: Klicken Sie in der Symbolleiste der Berichtanzeige auf diesen Pfeil, um den Parameterbereich ein- oder auszublenden.  
  
5. **@CategoryQuota Parameter** Parameters @CategoryQuota Datentyp **"float"** , sodass sie einen numerischen Wert akzeptiert.  @CategoryQuota wird so festgelegt, dass mehrere Werte zulässig sind.  
  
6. **Bericht anzeigen**: Nachdem Sie die Parameterwerte eingegeben haben, klicken Sie auf **Bericht anzeigen**, um den Bericht auszuführen. Wenn alle Parameter Standardwerte aufweisen, wird der Bericht beim ersten Anzeigen automatisch ausgeführt.  
  
## <a name="creating-parameters"></a><a name="bkmk_Create_Parameters"></a> Erstellen von Parametern

Sie können Berichtsparameter auf verschiedene Arten erstellen.
  
> [!NOTE]
>  Nicht alle Datenquellen unterstützen Parameter.
  
**Datasetabfrage oder gespeicherte Prozedur mit Parametern**
  
 Fügen Sie eine Datasetabfrage hinzu, die Variablen enthält, oder eine gespeicherte Datasetprozedur, die Eingabeparameter enthält. Für alle Variablen oder Eingabeparameter wird jeweils ein Datasetparameter erstellt und für alle Datasetparameter jeweils ein Berichtsparameter.  
  
![Berichts-Generator Dataset-Parametereigenschaften](media/report-builder-parameters/report-builder-parameter-dataset.png "Dataseteigenschaften für Berichts-Generator-Parameter")

  
 Dieses Bild vom Berichts-Generator zeigt Folgendes:  
  
1.  Die Berichtsparameter im Bereich „Berichtsdaten“.  
  
2.  Das Dataset mit den Parametern.  
  
3.  Der Bereich „Parameter“.  
  
4.  Die im Dialogfeld „Dataseteigenschaften“ aufgeführten Parameter.  
  
**Manuelles Erstellen von Parametern**
  
Über den Berichtsdatenbereich können Sie Parameter manuell erstellen. Sie können Berichtsparameter so konfigurieren, dass ein Benutzer Werte interaktiv eingeben kann, um den Inhalt oder die Darstellung eines Berichts anzupassen. Sie können Berichtsparameter auch so konfigurieren, dass ein Benutzer vorkonfigurierte Werte nicht ändern kann.  
  
> [!NOTE]  
>  Da Parameter auf dem Server unabhängig verwaltet werden, werden die vorhandenen Parametereinstellungen im Bericht beim erneuten Veröffentlichen eines Hauptberichts mit neuen Parametereinstellungen nicht überschrieben.  

### <a name="parameter-values"></a>Parameterwerte

 Folgende Optionen können zum Auswählen von Parameterwerten im Bericht verwendet werden.  
  
- Wählen Sie einen einzelnen Parameterwert in einer Dropdownliste aus.  
  
- Wählen Sie mehrere Parameterwerte in einer Dropdownliste aus.  
  
- Wählen Sie in einer Dropdownliste einen Wert für einen Parameter aus, der die Werte bestimmt, die in der Dropdownliste für einen anderen Parameter verfügbar sind. Hierbei handelt es sich um kaskadierende Parameter. Mithilfe von kaskadierenden Parametern können Sie Parameterwerte nach und nach aus Tausenden von Werten herausfiltern, sodass eine überschaubare Anzahl übrig bleibt. Weitere Informationen finden Sie unter [Verwenden von kaskadierenden Parametern in paginierten Berichten](../guidance/paginated-report-cascading-parameter.md).
  
- Führen Sie den Bericht aus, ohne zuvor einen Parameterwert auswählen zu müssen, da ein Standardwert für den Parameter erstellt wurde.  
  
## <a name="report-parameter-properties"></a><a name="bkmk_Report_Parameters"></a> Berichtsparametereigenschaften

 Sie können die Berichtsparametereigenschaften mithilfe des Dialogfelds „Berichtseigenschaften“ ändern. Die folgende Tabelle enthält die Eigenschaften, die Sie für die einzelnen Parameter festlegen können:  
  
|Eigenschaft|Beschreibung|  
|--------------|-----------------|  
|Name|Geben Sie für den Parameter einen Namen ein, bei dem die Groß-/Kleinschreibung beachtet werden muss. Der Name muss mit einem Buchstaben beginnen und kann Buchstaben, Zahlen und einen Unterstrich (_) enthalten. Der Name darf keine Leerzeichen enthalten. Bei automatisch erstellten Parametern entspricht der Name dem Parameter in der Datasetabfrage. Manuell erstellte Parameter sehen standardmäßig ähnlich aus wie „BerichtsParameter1“.|  
|Eingabeaufforderung|Der Text wird neben dem Parameter in der Symbolleiste der Berichtanzeige angezeigt.|  
|Datentyp|Ein Berichtsparameter muss einen der folgenden Datentypen aufweisen:<br /><br /> **Boolean**. Der Benutzer wählt über ein Optionsfeld „True“ oder „False“ aus.<br /><br /> **DateTime**. Der Benutzer wählt in einem Kalendersteuerelement ein Datum aus.<br /><br /> **Integer**. Der Benutzer gibt Werte in ein Textfeld ein.<br /><br /> **Float**. Der Benutzer gibt Werte in ein Textfeld ein.<br /><br /> **Text**. Der Benutzer gibt Werte in ein Textfeld ein.<br /><br /> Wenn für einen Parameter verfügbare Werte definiert wurden, wählt der Benutzer Werte in einer Dropdownliste aus, auch wenn der Datentyp **DateTime** verwendet wird.|  
|Leeren Wert zulassen|Wählen Sie diese Option aus, wenn der Wert des Parameters eine leere Zeichenfolge oder ein Leerzeichen sein darf.<br /><br /> Wenn Sie für einen Parameter gültige Werte angeben und möchten, dass ein leerer Wert zu den gültigen Werten zählt, muss der Wert zusammen mit den anderen Werten angegeben werden. Durch die Auswahl dieser Option ist in den verfügbaren Werten nicht automatisch ein Leerzeichen enthalten.|  
|NULL-Wert zulassen|Wählen Sie diese Option aus, wenn der Wert des Parameters ein NULL-Wert sein darf.<br /><br /> Wenn Sie für einen Parameter gültige Werte angeben und möchten, dass NULL zu den gültigen Werten zählt, muss der Wert zusammen mit den anderen Werten angegeben werden. Durch die Auswahl dieser Option ist in den verfügbaren Werten nicht automatisch ein NULL-Wert enthalten.|  
|Mehrere Werte zulassen|Geben Sie verfügbare Werte an, um eine Dropdownliste zu erstellen, in der Benutzer Werte auswählen können. Auf diese Weise können Sie sicherstellen, dass in der Datasetabfrage nur gültige Werte übermittelt werden.<br /><br /> Wählen Sie diese Option aus, wenn es sich bei dem Wert für den Parameter um mehrere Werte handeln kann, die in einer Dropdownliste angezeigt werden. NULL-Werte sind nicht zulässig. Wenn Sie diese Option ausgewählt haben, werden der Liste mit verfügbaren Werten Kontrollkästchen in einer Dropdownliste mit Parametern hinzugefügt. Oben in der Liste befindet sich das Kontrollkästchen für **Alle auswählen**. Benutzer können die gewünschten Werte aktivieren.<br /><br /> Wenn sich die Daten, die die Werte bereitstellen, schnell ändern, ist die dem Benutzer angezeigte Liste möglicherweise nicht aktuell.|  
|Sichtbar|Wählen Sie diese Option aus, um den Berichtsparameter oben im Bericht anzuzeigen, wenn der Bericht ausgeführt wird. Mit dieser Option können Benutzer Parameterwerte zur Laufzeit auswählen.|  
|Ausgeblendet|Wählen Sie diese Option aus, um den Berichtsparameter im veröffentlichten Bericht auszublenden. Die Berichtsparameterwerte können weiterhin auf eine Berichts-URL, in einer Abonnementdefinition oder auf dem Berichtsserver festgelegt werden.|  
|Intern|Wählen Sie diese Option aus, um den Berichtsparameter auszublenden. Der Berichtsparameter lässt sich im veröffentlichten Bericht nur in der Berichtsdefinition anzeigen.|  
|Verfügbare Werte|Wenn Sie für einen Parameter verfügbare Werte angegeben haben, werden die gültigen Werte immer in Form einer Dropdownliste angezeigt. Wenn Sie also beispielsweise verfügbare Werte für einen **DateTime** -Parameter angeben, wird im Parameterbereich anstelle eines Kalendersteuerelements eine Dropdownliste mit Datumsangaben angezeigt.<br /><br /> Sie können für die Datenquelle eine Option festlegen, dass für alle Abfragen in den Datasets, die mit einer Datenquelle verknüpft sind, eine einzige Transaktion verwendet wird, um sicherzustellen, dass in einem Bericht und den entsprechenden Unterberichten eine einheitliche eine Werteliste verwendet wird.<br /><br /> **Sicherheitshinweis** Verwenden Sie bei einem Bericht, der einen Parameter vom Datentyp **Text** enthält, eine Liste mit verfügbaren Werten (auch als Liste mit gültigen Werten bezeichnet), und sorgen Sie dafür, dass Benutzer, die den Bericht ausführen, nur über die Berechtigungen zum Anzeigen der Daten im Bericht verfügen.|  
|Standardwerte|Legen Sie Standardwerte über eine Abfrage oder eine statische Liste fest.<br /><br /> Wenn alle Parameter Standardwerte aufweisen, wird der Bericht beim ersten Anzeigen automatisch ausgeführt.|  
|Erweiterte|Legen Sie das Berichtsdefinitionsattribut **UsedInQuery** fest. Hierbei handelt es sich um einen Wert, der angibt, ob sich dieser Parameter direkt oder indirekt auf die Daten in einem Bericht auswirkt.<br /><br /> **Aktualisierungszeitpunkt automatisch bestimmen**<br /> Wählen Sie diese Option aus, wenn Sie möchten, dass der Berichtsprozessor eine Einstellung für diesen Wert bestimmt. Der Wert lautet **True**, wenn der Berichtsprozessor eine Datasetabfrage mit einem direkten oder indirekten Verweis auf diesen Parameter erkennt oder wenn der Bericht Unterberichte enthält.<br /><br /> **Immer aktualisieren**<br /> Wählen Sie diese Option aus, wenn der Berichtsparameter in einer Datasetabfrage oder in einem Parameterausdruck direkt oder indirekt verwendet wird. Diese Option legt **UsedInQuery** auf „True“ fest.<br /><br /> **Nie aktualisieren**<br /> Wählen Sie diese Option aus, wenn der Berichtsparameter nicht direkt oder indirekt in einer Datasetabfrage oder einem Parameterausdruck verwendet wird. Diese Option legt **UsedInQuery** auf „False“ fest.<br /><br /> **Vorsicht** Verwenden Sie **Nie aktualisieren** mit Vorsicht. Auf dem Berichtsserver wird **UsedInQuery** zur Steuerung von Cacheoptionen für Berichtsdaten und gerenderte Berichte sowie von Parameteroptionen für Berichtsmomentaufnahmen verwendet. Wenn **Nie aktualisieren** falsch festgelegt wird, werden möglicherweise falsche Berichtsdaten oder Berichte zwischengespeichert, oder die Daten in einer Berichtsmomentaufnahme sind inkonsistent. |  
  
##  <a name="dataset-query"></a><a name="bkmk_Dataset_Parameters"></a> Datasetabfrage  
 Zum Filtern von Daten in der Datasetabfrage können Sie eine Einschränkungsklausel einbinden, mit der die abgerufenen Daten durch Angeben von Werten, die im Resultset eingeschlossen oder ausgeschlossen werden sollen, begrenzt werden.  
  
 Verwenden Sie zum Erstellen einer parametrisierten Abfrage den Abfrage-Designer für die Datenquelle.  
  
-   Bei Transact-SQL-Abfragen werden für Parameter je nach Datenquelle unterschiedliche Syntaxen unterstützt. Unterstützt werden Parameterbereiche, die in der Abfrage nach Position oder Name identifiziert werden. Im relationalen Abfrage-Designer müssen Sie die Parameteroption für einen Filter auswählen, um eine parametrisierte Abfrage zu erstellen.   
  
-   Für Abfragen, die auf einer mehrdimensionalen Datenquelle wie Microsoft SQL Server Analysis Services basieren, können Sie angeben, ob ein Parameter basierend auf einem Filter erstellt werden soll, den Sie im Abfrage-Designer angeben. 
  
##  <a name="parameter-management-for-a-published-report"></a><a name="bkmk_Manage_Parameters"></a> Parameterverwaltung für einen veröffentlichten Bericht  
 Wenn Sie einen Bericht entwerfen, werden Berichtsparameter in der Berichtsdefinition gespeichert. Wenn Sie einen Bericht veröffentlichen, werden Berichtsparameter getrennt von der Berichtsdefinition gespeichert und verwaltet.  
  
 Für einen veröffentlichten Bericht können Sie Folgendes verwenden:  
  
-   **Berichtsparametereigenschaften.** Ändern Sie Berichtsparameterwerte direkt auf dem Berichtsserver, unabhängig von der Berichtsdefinition.  
  
-   **Berichtsabonnements.** Sie können Parameterwerte angeben, um Daten zu filtern und Berichte über Abonnements bereitzustellen. 
  
 Parametereigenschaften für einen veröffentlichten Bericht werden beim erneuten Veröffentlichen der Berichtsdefinition beibehalten. Wenn die Berichtsdefinition als derselbe Bericht noch mal veröffentlicht wird und Parameternamen und Datentypen dieselben bleiben, werden Ihre Eigenschafteneinstellungen beibehalten. Wenn Sie in der Berichtsdefinition Parameter hinzufügen oder löschen oder den Datentyp oder Namen eines vorhandenen Parameters ändern, müssen Sie möglicherweise die Parametereigenschaften im veröffentlichten Bericht ändern.  
  
 Nicht alle Parameter können in allen Fällen geändert werden. Wenn ein Berichtsparameter einen Standardwert über eine Datasetabfrage abfragt, kann dieser Wert weder für einen veröffentlichten Bericht noch auf dem Berichtsserver geändert werden. Der zur Laufzeit verwendete Wert wird bestimmt, wenn die Abfrage ausgeführt wird oder bei ausdruckbasierten Parametern, wenn der Ausdruck ausgewertet wird.  
  
 Berichtsausführungsoptionen können sich auf die Verarbeitung von Parametern auswirken. In einem Bericht, der als Momentaufnahme ausgeführt wird, können keine Parameter verwendet werden, die von einer Abfrage abgeleitet werden, außer die Abfrage enthält Standardwerte für die Parameter.  
  
##  <a name="parameters-for-a-subscription"></a><a name="bkmk_Parameters_Subscription"></a> Parameter für ein Abonnement  
 Sie können ein Abonnement für einen bedarfsgesteuerten Bericht oder für eine Berichtsmomentaufnahme definieren und Parameterwerte zur Verarbeitung während der Abonnementverarbeitung angeben.  
  
-   **Bedarfsgesteuerter Bericht.**  Für einen bedarfsgesteuerten Bericht können Sie einen anderen Parameterwert angeben als den veröffentlichten Wert für die einzelnen für den Bericht aufgeführten Parameter. Ein Beispiel hierfür ist ein Dienstanforderungsbericht, der einen *Zeitraum*-Parameter verwendet, um Kundenserviceanforderungen für den aktuellen Tag, die aktuelle Woche oder den aktuellen Monat zurückzugeben. Hier kann der Standardparameterwert für den Bericht auf **heute** festgelegt werden, während gleichzeitig vom Abonnement ein anderer Parameterwert verwendet werden kann (z. B. **Woche** oder **Monat**), um einen Bericht zu erstellen, der wöchentliche oder monatliche Zahlen enthält.  
  
## <a name="next-steps"></a>Weitere Schritte

- [Was sind paginierte Berichte in Power BI Premium? (Vorschau)](paginated-reports-report-builder-power-bi.md)  
- [Verwenden von kaskadierenden Parametern in paginierten Berichten](../guidance/paginated-report-cascading-parameter.md)
