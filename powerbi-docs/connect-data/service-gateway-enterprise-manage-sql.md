---
title: Verwalten Ihrer Datenquelle – SQL
description: So verwalten Sie On-premises data gateway und die zu diesem Gateway gehörigen Datenquellen.
author: arthiriyer
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: conceptual
ms.date: 07/15/2019
ms.author: arthii
LocalizationGroup: Gateways
ms.openlocfilehash: 575c4007b85d6aebaa1b0fae993ea9457f45d680
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/13/2020
ms.locfileid: "83307656"
---
# <a name="manage-your-data-source---sql-server"></a>Verwalten Ihrer Datenquelle – SQL Server

[!INCLUDE [gateway-rewrite](../includes/gateway-rewrite.md)]

Nachdem Sie das [lokale Datengateway installiert haben](/data-integration/gateway/service-gateway-install), können Sie [Datenquellen hinzufügen](service-gateway-data-sources.md#add-a-data-source), die mit dem Gateway verwendet werden können. In diesem Artikel wird beschrieben, wie Sie für die geplante Aktualisierung oder für DirectQuery mit Gateways und SQL Server-Datenquellen arbeiten.

## <a name="add-a-data-source"></a>Hinzufügen einer Datenquelle

Weitere Informationen zum Hinzufügen einer Datenquelle finden Sie unter [Hinzufügen einer Datenquelle](service-gateway-data-sources.md#add-a-data-source). Wählen Sie unter **Datenquellentyp** die Option **SQL Server** aus.

![Auswählen der SQL Server-Datenquelle](media/service-gateway-enterprise-manage-sql/datasourcesettings2.png)

> [!NOTE]
> Bei Verwendung von DirectQuery unterstützt das Gateway nur **SQL Server 2012 SP1** und nachfolgende Versionen.

Füllen Sie die Informationen für die Datenquelle aus, dazu gehören **Server** und **Datenbank**. 

Wählen Sie unter **Authentifizierungsmethode** entweder **Windows** oder **Standard** aus. Wählen Sie **Standard** aus, wenn die SQL-Authentifizierung statt der Windows-Authentifizierung verwendet werden soll. Geben Sie dann die Anmeldeinformationen ein, die für diese Datenquelle verwendet werden sollen.

> [!NOTE]
> Alle Abfragen der Datenquelle werden mit diesen Anmeldeinformationen ausgeführt, es sei denn, für die Datenquelle ist einmaliges Anmelden (Single Sign-On, SSO) mit Kerberos-Authentifizierung konfiguriert und aktiviert. Bei Verwendung von SSO werden für Importdatasets die gespeicherten Anmeldeinformationen verwendet. Für DirectQuery-Datasets wird jedoch der aktuelle Power BI-Benutzer zum Ausführen der Abfragen mit SSO verwendet. Weitere Informationen zum Speichern von Anmeldeinformationen finden Sie unter [Speichern verschlüsselter Anmeldeinformationen in der Cloud](service-gateway-data-sources.md#store-encrypted-credentials-in-the-cloud). Alternativ finden Sie weitere Informationen im Artikel zum [Verwenden von Kerberos für SSO (Single Sign-On, Einmaliges Anmelden) von Power BI bei lokalen Datenquellen](service-gateway-sso-kerberos.md).

![Ausfüllen der Einstellungen zur Datenquelle](media/service-gateway-enterprise-manage-sql/datasourcesettings3.png)

Nachdem Sie alles ausgefüllt haben, klicken Sie auf **Hinzufügen**. Sie können diese Datenquelle nun für eine geplante Aktualisierung oder DirectQuery mit einer lokalen SQL Server-Instanz verwenden. Bei erfolgreicher Ausführung wird *Verbindung erfolgreich* angezeigt.

![Anzeigen des Verbindungsstatus](media/service-gateway-enterprise-manage-sql/datasourcesettings4.png)

### <a name="advanced-settings"></a>Erweiterte Einstellungen

Optional können Sie die Datenschutzebene für die Datenquelle konfigurieren. Diese Einstellung steuert, wie Daten kombiniert werden können. Sie wird nur für die geplante Aktualisierung verwendet. Die Einstellung für die Datenschutzebene gilt nicht für DirectQuery. Weitere Informationen zu Datenschutzebenen für Ihre Datenquelle finden Sie unter [Privacy levels (Power Query) (Datenschutzebenen (Power Query))](https://support.office.com/article/Privacy-levels-Power-Query-CC3EDE4D-359E-4B28-BC72-9BEE7900B540).

![Festlegen der Datenschutzebene](media/service-gateway-enterprise-manage-sql/datasourcesettings9.png)

## <a name="use-the-data-source"></a>Verwenden der Datenquelle

Nachdem Sie die Datenquelle erstellt haben, kann diese mit DirectQuery-Verbindungen oder durch eine geplante Aktualisierung verwendet werden.

> [!NOTE]
> Server- und Datenbanknamen müssen in Power BI Desktop und der Datenquelle innerhalb des lokalen Datengateways übereinstimmen.

Der Link zwischen Ihrem Dataset und der Datenquelle innerhalb des Gateways basiert auf dem Namen Ihres Servers und Ihrer Datenbank. Diese Namen müssen übereinstimmen. Wenn Sie z.B. eine IP-Adresse für den Servernamen in Power BI Desktop angeben, müssen Sie die IP-Adresse für die Datenquelle innerhalb der Gatewaykonfiguration verwenden. Wenn Sie *SERVER\INSTANCE* in Power BI Desktop verwenden, müssen Sie dies in der für das Gateway konfigurierten Datenquelle verwenden.

Diese Voraussetzung gilt für DirectQuery ebenso wie für geplante Aktualisierungen.

### <a name="use-the-data-source-with-directquery-connections"></a>Verwenden der Datenquelle mit DirectQuery-Verbindungen

Achten Sie darauf, dass die Namen des Servers und der Datenbank in Power BI Desktop mit der für das Gateway konfigurierten Datenquelle übereinstimmen. Stellen Sie außerdem sicher, dass der Benutzer auf der Registerkarte **Benutzer** der Datenquelle aufgeführt ist, um DirectQuery-Datasets veröffentlichen zu können. Die Auswahl für DirectQuery in Power BI Desktop erfolgt beim erstmaligen Importieren der Daten. Weitere Informationen zur Verwendung von DirectQuery finden Sie unter [Verwenden von DirectQuery in Power BI Desktop](desktop-use-directquery.md).

Nach der Veröffentlichung, entweder aus Power BI Desktop oder mithilfe von **Daten abrufen**, sollten Ihre Berichte funktionieren. Es kann nach dem Erstellen der Datenquelle im Gateway mehrere Minuten dauern, bis die Verbindung genutzt werden kann.

### <a name="use-the-data-source-with-scheduled-refresh"></a>Verwenden der Datenquelle mit geplanten Aktualisierungen

Wenn Sie auf der Registerkarte **Benutzer** der im Gateway konfigurierten Datenquelle aufgeführt sind und die Namen des Servers und der Datenbank übereinstimmen, wird das Gateway als Option für geplante Aktualisierungen angezeigt.

![Anzeigen der Benutzer](media/service-gateway-enterprise-manage-sql/powerbi-gateway-enterprise-schedule-refresh.png)

## <a name="next-steps"></a>Weitere Schritte

* [Herstellen einer Verbindung mit lokalen Daten in SQL Server](service-gateway-sql-tutorial.md)
* [Problembehandlung beim lokalen Datengateway](/data-integration/gateway/service-gateway-tshoot)
* [Lokales Datengateway – Power BI](service-gateway-onprem-tshoot.md)
* [Verwenden von Kerberos für SSO (Single Sign-On, Einmaliges Anmelden) von Power BI bei lokalen Datenquellen](service-gateway-sso-kerberos.md)

Weitere Fragen? Stellen Sie Ihre Frage in der [Power BI-Community](https://community.powerbi.com/).
