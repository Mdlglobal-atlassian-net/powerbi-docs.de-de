---
title: Dynamische Sicherheit auf Zeilenebene mit dem tabellarischen Modell von Analysis Services
description: Dynamische Sicherheit auf Zeilenebene mit dem tabellarischen Modell von Analysis Services
author: davidiseminger
ms.reviewer: davidi
editor: davidi
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: tutorial
ms.date: 01/17/2020
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 83cf7517fac569f8439f1debcdf621a786835d2c
ms.sourcegitcommit: d6a48e6f6e3449820b5ca03638b11c55f4e9319c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/18/2020
ms.locfileid: "77427367"
---
# <a name="implement-row-level-security-in-an-analysis-services-tabular-model"></a>Implementieren der Sicherheit auf Zeilenebene in einem tabellarischen Analysis Services-Modell

In diesem Tutorial arbeiten Sie die unten aufgeführten Schritte anhand eines Beispieldatasets durch. Dabei lernen Sie mehr über die [**Sicherheit auf Zeilenebene**](service-admin-rls.md) in einem *Analysis Services-Tabellenmodell* und verwenden dieses in einem Power BI-Bericht.

* Erstellen einer neuen Sicherheitstabelle in der [AdventureworksDW2012-Datenbank](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks)
* Erstellen des tabellarischen Modells mit erforderlichen Fakten- und Dimensionstabellen
* Definieren von Benutzerrollen und -berechtigungen
* Bereitstellen des Modells auf einer *Analysis Services-Tabelleninstanz*
* Erstellen eines Power BI Desktop-Berichts, der Daten anzeigt, die genau auf den Benutzer zugeschnitten sind, der auf den Bericht zugreift
* Bereitstellen des Berichts im *Power BI-Dienst*
* Erstellen eines neuen Dashboards basierend auf dem Bericht
* Freigeben des Dashboards an Ihre Kollegen

Für dieses Tutorial ist die [AdventureworksDW2012-Datenbank](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) erforderlich.

## <a name="task-1-create-the-user-security-table-and-define-data-relationship"></a>Aufgabe 1: Erstellen einer Benutzersicherheitstabelle und Definieren der Datenbeziehung

Es gibt viele Artikel darüber, wie die dynamische Sicherheit auf Zeilenebene mit dem *SQL Server Analysis Services-Tabellenmodell* definiert wird. In unserem Beispiel folgen wir dem Artikel [Implement Dynamic Security by Using Row Filters (Implementieren dynamischer Sicherheit mithilfe von Zeilenfiltern)](/analysis-services/tutorial-tabular-1200/supplemental-lesson-implement-dynamic-security-by-using-row-filters).

Für die hier aufgeführten Schritte ist die relationale Datenbank AdventureworksDW2012 erforderlich.

1. Erstellen Sie in AdventureworksDW2012 wie unten gezeigt die Tabelle `DimUserSecurity`. Sie können [SQL Server Management Studio (SSMS)](/sql/ssms/download-sql-server-management-studio-ssms) zum Erstellen der Tabelle verwenden.

   ![Erstellen der Tabelle „DimUserSecurity“](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/createusersecuritytable.png)

1. Nachdem Sie die Tabelle erstellt und gespeichert haben, müssen Sie die Beziehung zwischen der Spalte `SalesTerritoryID` der Tabelle `DimUserSecurity` und der Spalte `SalesTerritoryKey` der Tabelle `DimSalesTerritory` wie unten gezeigt erstellen.

   Klicken Sie in SSMS mit der rechten Maustaste auf die Tabelle **DimUserSecurity** und dann auf **Entwurf**. Klicken Sie dann auf **Tabellen-Designer** > **Beziehungen...** . Speichern Sie anschließend die Tabelle.

   ![Fremdschlüsselbeziehungen](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/createusersecuritytable_keys.png)

1. Fügen Sie Benutzer zur Tabelle hinzu. Klicken Sie mit der rechten Maustaste auf die Tabelle **DimUserSecurity** und dann auf **Edit Top 200 Rows** (Obere 200 Zeilen bearbeiten). Wenn Sie Benutzer hinzugefügt haben, sollte die Tabelle `DimUserSecurity` ähnlich wie im folgenden Beispiel aussehen:

   ![Tabelle „DimUserSecurity“ mit Beispielbenutzern](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/createusersecuritytable_users.png)

   Sie werden in den nächsten Aufgaben zu diesen Benutzern zurückkehren.

1. Als Nächstes führen Sie einen *inneren Join* mit der Tabelle `DimSalesTerritory` durch, die Details zur Region anzeigt, die dem Benutzer zugeordnet ist. Der folgende SQL-Code führt den inneren Join durch, und die folgende Abbildung zeigt, wie die Tabelle danach aussieht.

    ```sql
    select b.SalesTerritoryCountry, b.SalesTerritoryRegion, a.EmployeeID, a.FirstName, a.LastName, a.UserName from [dbo].[DimUserSecurity] as a join [dbo].[DimSalesTerritory] as b on a.[SalesTerritoryID] = b.[SalesTerritoryKey]
    ```

   Die verknüpfte Tabelle zeigt, wer für welche Vertriebsregion zuständig ist. Dies ist aufgrund der in Schritt 2 erstellten Beziehung möglich. Sie sehen z. B., dass *Rita Santos* für *Australien* zuständig ist.

## <a name="task-2-create-the-tabular-model-with-facts-and-dimension-tables"></a>Aufgabe 2: Erstellen des tabellarischen Modells mit Fakten- und Dimensionstabellen

Sobald Ihr relationales Data Warehouse vorhanden ist, müssen Sie das Tabellenmodell definieren. Das Modell kann mit [SQL Server Data Tools](/sql/ssdt/sql-server-data-tools) (SSDT) erstellt werden. Weitere Informationen finden Sie unter [Create a New Tabular Model Project (Erstellen eines neuen Tabellenmodells)](/sql/analysis-services/lesson-1-create-a-new-tabular-model-project).

1. Importieren Sie alle erforderlichen Tabellen so wie unten dargestellt in das Modell.

    ![Importierte SQL Server für die Verwendung mit Data Tools](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/ssdt_model.png)

1. Nachdem Sie die erforderlichen Tabellen importiert haben, müssen Sie eine Rolle namens *SalesTerritoryUsers* definieren und ihr die Leseberechtigung erteilen. Klicken Sie in SSDT auf das Menü **Model** (Modell) und anschließend auf **Roles** (Rollen). Klicken Sie im **Rollen-Manager** auf **Neu**.

1. Fügen Sie im **Rollen-Manager** unter **Mitglieder** die Benutzer hinzu, die Sie in der Tabelle `DimUserSecurity` in [Aufgabe 1](#task-1-create-the-user-security-table-and-define-data-relationship) definiert haben.

    ![Hinzufügen von Benutzern im Rollen-Manager](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/rolemanager.png)

1. Fügen Sie anschließend die korrekten Funktionen für die Tabellen `DimSalesTerritory` und `DimUserSecurity` so wie unten in der Registerkarte **Zeilenfilter** gezeigt hinzu.

    ![Hinzufügen von Funktionen zu „Zeilenfilter“](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/rolemanager_complete.png)

1. Die Funktion `LOOKUPVALUE` gibt Werte für eine Spalte zurück, bei denen der Windows-Benutzername dem von der Funktion `USERNAME` zurückgegebenen Benutzernamen entspricht. Dann können Sie die Abfragen einschränken, sodass die von `LOOKUPVALUE` zurückgegebenen Werte den Werten in derselben oder einer ähnlichen Tabelle entsprechen. Geben Sie in der Spalte **DAX Filter** die folgende Formel ein:

    ```dax
        =DimSalesTerritory[SalesTerritoryKey]=LOOKUPVALUE(DimUserSecurity[SalesTerritoryID], DimUserSecurity[UserName], USERNAME(), DimUserSecurity[SalesTerritoryID], DimSalesTerritory[SalesTerritoryKey])
    ```

    In dieser Formel gibt die Funktion `LOOKUPVALUE` alle Werte für die Spalte `DimUserSecurity[SalesTerritoryID]` zurück, in der `DimUserSecurity[UserName]` dem aktuell angemeldeten Windows-Benutzernamen entspricht und `DimUserSecurity[SalesTerritoryID]` gleich `DimSalesTerritory[SalesTerritoryKey]` ist.

    > [!IMPORTANT]
    > Beachten Sie, dass die DAX-Funktion [USERELATIONSHIP](/dax/userelationship-function-dax) nicht unterstützt wird, wenn Sie Sicherheit auf Zeilenebene verwenden.

   Mithilfe der `SalesTerritoryKey`-Werte, die `LOOKUPVALUE` zurückgibt, werden dann die in `DimSalesTerritory` angezeigten Zeilen eingeschränkt. Es werden nur Zeilen angezeigt, in denen sich der `SalesTerritoryKey`-Wert in den IDs befindet, die von der Funktion `LOOKUPVALUE` zurückgegeben werden.

1. Fügen Sie für die Tabelle `DimUserSecurity` in der Spalte **DAX-Filter** die folgende Formel ein:

    ```dax
        =FALSE()
    ```

    Diese Formel gibt an, dass alle Spalten nach `false` aufgelöst werden sollen. Das bedeutet, dass Spalten in der Tabelle `DimUserSecurity` nicht abgefragt werden können.

Nun müssen Sie das Modell verarbeiten und bereitstellen. Weitere Informationen finden Sie unter [Lektion 14: Bereitstellen](/sql/analysis-services/lesson-13-deploy).

## <a name="task-3-add-data-sources-within-your-on-premises-data-gateway"></a>Aufgabe 3: Hinzufügen von Datenquellen im lokalen Datengateway

Sobald das tabellarische Modell bereitgestellt und für die Verwendung bereit ist, müssen Sie eine Datenquellenverbindung mit Ihrem lokalen tabellarischen Analysis Services-Server hinzufügen.

1. Sie müssen ein [lokales Datengateway](service-gateway-onprem.md) in Ihrer Umgebung installiert und konfiguriert haben, damit der Power BI-Dienst auf Ihren lokalen Analysedienst zugreifen kann.

1. Wenn das Gateway ordnungsgemäß konfiguriert wurde, müssen Sie eine Datenquellenverbindung für die *Analysis Services*-Tabelleninstanz erstellen. Weitere Informationen finden Sie unter [Verwalten Ihrer Datenquelle – Analysis Services](service-gateway-enterprise-manage-ssas.md).

   ![Erstellen einer Datenquellenverbindung](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/pbi_gateway.png)

Wenn dieser Vorgang abgeschlossen ist, ist das Gateway konfiguriert und kann mit der lokalen Analysis Services-Datenquelle interagieren.

## <a name="task-4-create-report-based-on-analysis-services-tabular-model-using-power-bi-desktop"></a>Aufgabe 4: Erstellen eines Berichts basierend auf einem Analysis Services-Tabellenmodell mit Power BI Desktop

1. Starten Sie Power BI Desktop, und wählen Sie **Daten abrufen** > **Datenbank** aus.

1. Wählen Sie aus der Liste der Datenquellen die **SQL Server Analysis Services-Datenbank**, und klicken Sie auf **Verbinden**.

   ![Verbinden mit der SQL Server Analysis Services-Datenbank](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/getdata.png)

1. Geben Sie die Details zu Ihrer Analysis Services-Tabelleninstanz ein, und wählen Sie **Live verbinden** aus. Wählen Sie dann **OK** aus.
  
   ![Analysis Services-Details](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/getdata_connectlive.png)

   Mit Power BI funktioniert die dynamische Sicherheit nur mit einer Liveverbindung.

1. Sie sehen, dass sich das bereitgestellte Modell in der Analysis Services-Instanz befindet. Wählen Sie das jeweilige Modell, und klicken Sie auf **OK**.

   Power BI Desktop zeigt nun alle verfügbaren Felder rechts neben dem Canvas im Bereich **Felder** an.

1. Wählen Sie rechts im Bereich **Felder** das Measure **SalesAmount** aus der Tabelle **FactInternetSales** sowie die Dimension **SalesTerritoryRegion** aus der Tabelle **SalesTerritory** aus.

1. Fügen Sie zunächst keine weiteren Spalten hinzu, um diesen Bericht einfach zu halten. Ändern Sie die Visualisierung in ein **Ringdiagramm**, um die Datendarstellung aussagekräftiger zu gestalten.

   ![Visualisierung eines Ringdiagramms](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/donut_chart.png)

1. Wenn Ihr Bericht fertig ist, können Sie ihn direkt im Power BI-Portal veröffentlichen. Wählen Sie im Menüband **Start** in Power BI Desktop **Veröffentlichen** aus.

## <a name="task-5-create-and-share-a-dashboard"></a>Aufgabe 5: Erstellen und Freigeben eines Dashboards

Sie haben bis jetzt einen Bericht erstellt und ihn im **Power BI-Dienst** veröffentlicht. Jetzt können Sie das vorherig erstellte Beispiel verwenden, um ein Szenario zum Sichern von Modellen zu veranschaulichen.

In Ihrer Rolle als *Vertriebsleiterin* (Sales Manager) kann sich die Benutzerin Grace die Daten von allen verschiedenen Vertriebsregionen anzeigen lassen. Grace erstellt den Bericht und veröffentlicht ihn im Power BI-Dienst. Dieser Bericht wurde in den vorherigen Aufgaben erstellt.

Nachdem Grace den Bericht veröffentlicht hat, erstellt sie nun anhand dieses Berichts im Power BI-Dienst ein Dashboard namens *TabularDynamicSec*. Beachten Sie in der folgenden Abbildung, dass Grace sich die Daten aus allen Vertriebsregionen anzeigen lassen kann.

   ![Dashboard des Power BI-Diensts](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/donut_chart_1.png)

Grace gibt das Dashboard jetzt für ihre Kollegin Rita frei, die für den Vertrieb in der Region Australien zuständig ist.

   ![Freigeben eines Power BI-Dashboards](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/pbi_dashboard.png)

Wenn Rita sich im Power BI-Dienst anmeldet und das freigegebene Dashboard aufruft, das Grace erstellt hat, sollten nur Umsätze aus der Region Australien zu sehen sein.

Herzlichen Glückwunsch! Der Power BI-Dienst zeigt die dynamische Sicherheit auf Zeilenebene an, die im lokalen Analysis Services-Tabellenmodell definiert wurde. Power BI verwendet die Eigenschaft `EffectiveUserName`, um die aktuellen Power BI-Benutzeranmeldeinformationen zum Ausführen der Abfragen an die lokale Datenquelle zu senden.

## <a name="task-6-understand-what-happens-behind-the-scenes"></a>Aufgabe 6: Verstehen der Hintergrundvorgänge

Bei dieser Aufgabe wird vorausgesetzt, dass Sie sich mit dem [SQL Server Profiler](/sql/tools/sql-server-profiler/sql-server-profiler) auskennen, denn Sie müssen eine SQL Server Profiler-Ablaufverfolgung auf Ihrer lokalen SSAS-Tabelleninstanz erfassen.

Sobald der Benutzer (Rita) auf das Dashboard im Power BI-Dienst zugreift, wird die Sitzung initialisiert. Wie Sie sehen, nimmt die **SalesTerritoryUsers**-Rolle unmittelbar den effektiven Benutzernamen **<EffectiveUserName>rita@contoso.com</EffectiveUserName>** an.

       <PropertyList><Catalog>DefinedSalesTabular</Catalog><Timeout>600</Timeout><Content>SchemaData</Content><Format>Tabular</Format><AxisFormat>TupleFormat</AxisFormat><BeginRange>-1</BeginRange><EndRange>-1</EndRange><ShowHiddenCubes>false</ShowHiddenCubes><VisualMode>0</VisualMode><DbpropMsmdFlattened2>true</DbpropMsmdFlattened2><SspropInitAppName>PowerBI</SspropInitAppName><SecuredCellValue>0</SecuredCellValue><ImpactAnalysis>false</ImpactAnalysis><SQLQueryMode>Calculated</SQLQueryMode><ClientProcessID>6408</ClientProcessID><Cube>Model</Cube><ReturnCellProperties>true</ReturnCellProperties><CommitTimeout>0</CommitTimeout><ForceCommitTimeout>0</ForceCommitTimeout><ExecutionMode>Execute</ExecutionMode><RealTimeOlap>false</RealTimeOlap><MdxMissingMemberMode>Default</MdxMissingMemberMode><DisablePrefetchFacts>false</DisablePrefetchFacts><UpdateIsolationLevel>2</UpdateIsolationLevel><DbpropMsmdOptimizeResponse>0</DbpropMsmdOptimizeResponse><ResponseEncoding>Default</ResponseEncoding><DirectQueryMode>Default</DirectQueryMode><DbpropMsmdActivityID>4ea2a372-dd2f-4edd-a8ca-1b909b4165b5</DbpropMsmdActivityID><DbpropMsmdRequestID>2313cf77-b881-015d-e6da-eda9846d42db</DbpropMsmdRequestID><LocaleIdentifier>1033</LocaleIdentifier><EffectiveUserName>rita@contoso.com</EffectiveUserName></PropertyList>

Basierend auf den effektiven Anforderungen des Benutzernamens konvertiert Analysis Services die Anforderung in die tatsächliche Anmeldeinformation `contoso\rita`, nachdem die lokale Active Directory-Instanz abgefragt wurde. Sobald Analysis Services die Anmeldeinformationen abgerufen hat, gibt der Dienst die Daten zurück, die der Benutzer anzeigen und auf die er zugreifen darf.

Wenn im Dashboard weitere Aktivitäten auftreten, wird im SQL Profiler eine spezifische Abfrage angezeigt, die als DAX-Abfrage wieder an das Analysis Services-Tabellenmodell zurückgegeben wird. Wenn Rita beispielsweise vom Dashboard zum zugrunde liegenden Bericht wechselt, erfolgt die folgende Abfrage.

   ![DAX-Abfrage wird an das Analysis Services-Modell zurückgegeben](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/profiler1.png)

Sie können unten auch die DAX-Abfrage sehen, die ausgeführt wird, um die Berichtsdaten aufzufüllen.
   
   ```dax
   EVALUATE
     ROW(
       "SumEmployeeKey", CALCULATE(SUM(Employee[EmployeeKey]))
     )
   
   <PropertyList xmlns="urn:schemas-microsoft-com:xml-analysis">``
             <Catalog>DefinedSalesTabular</Catalog>
             <Cube>Model</Cube>
             <SspropInitAppName>PowerBI</SspropInitAppName>
             <EffectiveUserName>rita@contoso.com</EffectiveUserName>
             <LocaleIdentifier>1033</LocaleIdentifier>
             <ClientProcessID>6408</ClientProcessID>
             <Format>Tabular</Format>
             <Content>SchemaData</Content>
             <Timeout>600</Timeout>
             <DbpropMsmdRequestID>8510d758-f07b-a025-8fb3-a0540189ff79</DbpropMsmdRequestID>
             <DbPropMsmdActivityID>f2dbe8a3-ef51-4d70-a879-5f02a502b2c3</DbPropMsmdActivityID>
             <ReturnCellProperties>true</ReturnCellProperties>
             <DbpropMsmdFlattened2>true</DbpropMsmdFlattened2>
             <DbpropMsmdActivityID>f2dbe8a3-ef51-4d70-a879-5f02a502b2c3</DbpropMsmdActivityID>
           </PropertyList>
   ```

## <a name="considerations"></a>Überlegungen

* Die lokale Sicherheit auf Zeilenebene von Power BI ist nur bei einer Liveverbindung verfügbar.

* Alle Änderungen an Daten, die nach der Modellverarbeitung vorgenommen werden, stehen unmittelbar allen Benutzern zur Verfügung, die über eine Liveverbindung aus dem Power BI-Dienst auf den Bericht zugreifen.

