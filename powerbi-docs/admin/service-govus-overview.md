---
title: Power BI für US-Behördenkunden – Übersicht
description: US-Behördenkunden können ihrem Microsoft 365 Government-Plan ein Power BI Pro-Abonnement hinzufügen. Erfahren Sie in dieser Dienstbeschreibung, wie Sie sich registrieren und die Verfügbarkeit von Funktionen überprüfen können.
author: kfollis
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 04/07/2020
ms.author: kfollis
LocalizationGroup: Get started
ms.openlocfilehash: aeaaf0e1e8baa70b5159d908ce1e27bb937de372
ms.sourcegitcommit: bfc2baf862aade6873501566f13c744efdd146f3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/13/2020
ms.locfileid: "83344708"
---
# <a name="power-bi-for-us-government-customers"></a>Power BI für US-Behördenkunden
Dieser Artikel richtet sich an US-Behörden, die Power BI als Bestandteil eines Office 365 Government-Plans bereitstellen. Die Government-Pläne sind auf die besonderen Bedürfnisse von Organisationen zugeschnitten, die in den USA geltende Compliance- und Sicherheitsstandards erfüllen müssen. Der für US-Behördenkunden entwickelte Power BI-Dienst unterscheidet sich von der kommerziellen Version des Power BI-Diensts. Diese Funktionsunterschiede werden in den folgenden Abschnitten beschrieben.

## <a name="add-power-bi-to-your-office-365-government-plan"></a>Hinzufügen von Power BI zu Ihrem Office 365 Government-Plan

Bevor Sie ein Power BI-Abonnement für US-Behörden erwerben und Benutzern Lizenzen zuweisen können, müssen Sie sich für einen Office 365 Government-Plan registrieren. Wenn Ihre Organisation bereits über einen Office 365 Government-Plan verfügt, fahren Sie mit [Erwerben eines Power BI Pro-Abonnements für Behördenkunden](#buy-a-power-bi-pro-subscription-for-government-customers) fort.

### <a name="enroll-in-an-office-365-government-plan"></a>Registrierung für einen Office 365 Government-Plan

Als Neukunde müssen Sie einen Berechtigungsnachweis für Ihre Organisation erbringen, bevor Sie sich für einen Office 365 Government-Plan registrieren können.  Füllen Sie zunächst das [Formular zum Berechtigungsnachweis für Office 365 für Behörden](https://www.microsoft.com/microsoft-365/government/eligibility-validation) aus. Um sicherzustellen, dass Sie den richtigen Plan für Ihre Organisation auswählen, konsultieren Sie die [Dienstbeschreibungen für Office 365 für US-Behörden](https://docs.microsoft.com/office365/servicedescriptions/office-365-platform-service-description/office-365-us-government/office-365-us-government).

> [!NOTE]
> Wenn Sie Power BI bereits in einer kommerziellen Umgebung implementiert haben und zur Microsoft Cloud for US Government migrieren möchten, müssen Sie Ihrem Office 365 Government-Plan ein neues Power BI Pro-Abonnement hinzufügen. Als Nächstes replizieren Sie die kommerziellen Daten in den Power BI-Dienst für US-Behörden, entfernen die Zuordnungen kommerzieller Lizenzen aus den Benutzerkonten und weisen den Benutzerkonten anschließend eine Power BI Pro Government-Lizenz zu.
>
>
## <a name="government-cloud-instances"></a>Instanzen der Government-Cloud
Office 365 bietet verschiedene Umgebungen für Regierungsbehörden, um unterschiedliche Anforderungen an die Einhaltung von Vorschriften zu erfüllen. Weitere Informationen zu jeder Umgebung finden Sie unter:

* [Office 365 Government Community Cloud (GCC)](https://docs.microsoft.com/office365/servicedescriptions/office-365-platform-service-description/office-365-us-government/gcc) ist für US-Behörden auf landesweiter, bundesstaatlicher und kommunaler Ebene konzipiert.

* [Office 365 Government Community Cloud High (GCC High)](https://docs.microsoft.com/office365/servicedescriptions/office-365-platform-service-description/office-365-us-government/gcc-high-and-dod) ist für US-amerikanische Bundesbehörden, Organisationen aus den Bereichen Verteidigung, Luft- und Raumfahrt sowie für weitere Organisationen konzipiert, die mit Daten der Kategorie „Controlled Unclassified Information (CUI)“ arbeiten. Diese Umgebung eignet sich für Organisationen und Unternehmen, die mit Aufgaben der nationalen Sicherheit betraut sind und deren Daten den Anforderungen der International Traffic in Arms Regulations (ITAR) oder der Defense Federal Acquisition Regulations Supplement (DFARS) unterliegen.

* Die [Office 365 DoD-Umgebung](https://docs.microsoft.com/office365/servicedescriptions/office-365-platform-service-description/office-365-us-government/gcc-high-and-dod) wurde exklusiv für das US-Verteidigungsministerium entworfen. 

## <a name="connect-to-power-bi-for-us-government"></a>Verbindungsherstellung mit Power BI für US-Behörden

Die URL zum Herstellen einer Verbindung mit Power BI unterscheidet sich für behördliche und kommerzielle Benutzer. Verwenden Sie zur Anmeldung bei Power BI die folgenden URLs:

| Kommerzielle Version  | GCC  | GCC High | DoD |
| --- | --- | --- | --- |
| [https://app.powerbi.com/](https://app.powerbi.com) |[https://app.powerbigov.us](https://app.powerbigov.us) | [https://app.high.powerbigov.us](https://app.high.powerbigov.us) | [https://app.mil.powerbigov.us](https://app.mil.powerbigov.us) |

Ihr Konto kann in mehr als einer Cloud eingerichtet sein. Wenn Ihr Konto auf diese Weise eingerichtet ist, können Sie bei der Anmeldung bei Power BI Desktop wählen, mit welcher Cloud Sie sich verbinden möchten.

## <a name="buy-a-power-bi-pro-subscription-for-government-customers"></a>Erwerben eines Power BI Pro-Abonnements für Behördenkunden

Nachdem Sie Office 365 bereitgestellt haben, können Sie ein Power BI Pro-Abonnement hinzufügen. Befolgen Sie die ausführliche Anleitung unter [Registrieren einer US-Behörde](service-govus-signup.md), um den Power BI Pro Government-Dienst zu erwerben. Erwerben Sie eine ausreichende Anzahl von Lizenzen für alle Benutzer, die Power BI benötigen, und weisen Sie die Lizenzen anschließend einzelnen Benutzerkonten zu.

> [!IMPORTANT]
> Power BI US Government ist nicht als *Free*-Lizenz verfügbar. Um auf die Communitycloud für Behörden zugreifen zu können, muss jedem Benutzer eine *Pro*-Lizenz zugewiesen werden. Wenn einem Benutzerkonto eine Free-Lizenz zugewiesen wurde, ist der Benutzer nur für den Zugriff auf die kommerzielle Cloud berechtigt, weshalb es zu Authentifizierungs- und Zugriffsproblemen kommt. Wenn Sie Power BI Premium gekauft haben, müssen Sie keine Pro-Lizenzen zuweisen, um den Benutzerzugriff zu ermöglichen.  Benutzer in der Organisation können auf Berichte zugreifen, die mit ihnen gemeinsam genutzt werden, solange die Berichte in einer Premium-Kapazität veröffentlicht werden. Informationen zu den Unterschieden der Lizenztypen finden Sie unter [Features des Power BI-Diensts nach Lizenztyp](../fundamentals/service-features-license-type.md).
>

## <a name="connect-government-and-global-azure-cloud-services"></a>Verbinden von behördlichen und globalen Azure-Clouddiensten

Azure ist auf mehrere Clouds verteilt. Standardmäßig können Sie Firewallregeln aktivieren, um eine Verbindung mit einer cloudspezifischen Instanz zu öffnen, aber bei einem cloudübergreifenden Netzwerk ist dies anders.  Für die Kommunikation zwischen Diensten in der öffentlichen Cloud und Diensten in der Government Community Cloud ist es erforderlich, spezifische Firewallregeln zu konfigurieren. Wenn Sie beispielsweise in Ihrer behördlichen Cloudbereitstellung von Power BI auf SQL-Datenbank-Instanzen in der öffentlichen Cloud zugreifen möchten, benötigen Sie eine Firewallregel in der SQL-Datenbank-Instanz. Konfigurieren Sie spezifische Firewallregeln für SQL-Datenbank-Instanzen, um Verbindungen mit der Azure Government Cloud für folgende Rechenzentren zuzulassen:

* USGov Iowa
* USGov Virginia
* USGov Texas
* USGov Arizona

In der öffentlichen Cloud sind die IP-Adressbereiche frei verfügbar. Die IP-Adressbereiche für die US Government-Cloud finden Sie in der herunterladbaren Datei [Azure IP Ranges and Service Tags – US Government Cloud](https://www.microsoft.com/download/details.aspx?id=57063). 

Informationen zum Einrichten von Firewalls für SQL-Datenbank-Instanzen finden Sie unter [Erstellen und Verwalten von IP-Firewallregeln](https://docs.microsoft.com/azure/sql-database/sql-database-firewall-configure#create-and-manage-ip-firewall-rules).

## <a name="power-bi-feature-availability"></a>Power BI-Featureverfügbarkeit

Um den Anforderungen der Government Cloud-Kunden gerecht zu werden, gibt es einige Unterschiede zwischen den Plänen für US-Behörden und den kommerziellen Plänen. In der folgenden Tabelle sehen Sie, welche Features in den einzelnen behördlichen Umgebungen verfügbar sind:

|Feature |   |GCC |GCC High |DoD|
|------|------|------|------|------|
|Verwaltung|Free-Lizenzen|Nicht verfügbar|Nicht verfügbar|Nicht verfügbar|
|  |Festlegen von Datenspeicherlimits|Verfügbar|Verfügbar|Verfügbar|
|  |Verwendung von Active Directory-Gruppen für Freigabe und Zugriffssteuerung|Verfügbar|Verfügbar|Verfügbar|
|  |Überwachung über das Office 365 Security and Compliance Admin Center|Verfügbar|Verfügbar|Verfügbar|
|  |Freigabe für externe Benutzer|Verfügbar|Verfügbar|Verfügbar|
|  |Nutzungsmetriken für Dashboards und Berichte|Nicht verfügbar|Nicht verfügbar|Nicht verfügbar|
|  |Azure B2B zwischen GCC und kommerzieller Cloud|Nicht verfügbar|Nicht verfügbar|Nicht verfügbar|
|Berichterstellung|Erstellen und Anzeigen von Dashboards und Berichten|Verfügbar|Verfügbar|Verfügbar|
|  |Geplante Datenaktualisierung|Verfügbar|Verfügbar|Verfügbar|
|  |Aktualisierbare Teamdashboards|Verfügbar|Verfügbar|Verfügbar|
|  |Paginierte Berichte|Verfügbar|In der Roadmap|In der Roadmap|
|  |Vorlagen-Apps|Nicht verfügbar|Nicht verfügbar|Nicht verfügbar|
|Verbinden mit Daten|Importieren von Daten und Berichten aus Excel|Verfügbar|Verfügbar|Verfügbar|
|  |Importieren von Daten aus CSV-Dateien|Verfügbar|Verfügbar|Verfügbar|
|  |Importieren von Daten aus Power BI Desktop-Dateien|Verfügbar|Verfügbar|Verfügbar|
|  |Konnektivität mit CDS|Verfügbar|Nicht verfügbar|Nicht verfügbar|
|  |Azure Data Lake Storage Gen2-Connector|Verfügbar|Nicht verfügbar|Nicht verfügbar|
|Datenverwaltung|Datenverwaltungsgateway|Verfügbar|Verfügbar|Verfügbar|
|  |Datenverschlüsselung in Azure SQL-Datenbank|Verfügbar|Verfügbar|Verfügbar|
|  |Datenverschlüsselung in Blob Storage für Power BI|Verfügbar|Verfügbar|Verfügbar|
|Produktübergreifende Integration|Einbettung in SharePoint Online über das Power BI-Webpart|Nicht verfügbar|Nicht verfügbar|Nicht verfügbar|
|  |Einbettung in SharePoint Online über das Webpart zur Einbettung|Verfügbar|Verfügbar|Verfügbar|
|  |Datenflows und KI-Funktionen|Nicht verfügbar|Nicht verfügbar|Nicht verfügbar|
|  |Power Automate-Konnektivität für datengesteuerte Warnungen|Nicht verfügbar|Nicht verfügbar|Nicht verfügbar|
|  |Power BI-Registerkarte in Teams|Verfügbar|Nicht verfügbar|Nicht verfügbar|
|  |Automatisiertes maschinelles Lernen|Nicht verfügbar|Nicht verfügbar|Nicht verfügbar|
|  |Azure Cognitive Services|Nicht verfügbar|Nicht verfügbar|Nicht verfügbar|
|  |Azure Machine Learning|Nicht verfügbar|Nicht verfügbar|Nicht verfügbar|

## <a name="next-steps"></a>Nächste Schritte

* [Registrierung bei Power BI für US-Behörden](service-govus-signup.md)
* [Microsoft Power Apps für US-Regierungsbehörden](https://docs.microsoft.com/power-platform/admin/powerapps-us-government)
* [Power Automate für US-Regierungsbehörden](https://docs.microsoft.com/power-automate/us-govt)
* <a href="https://channel9.msdn.com/Blogs/Azure/Cognitive-Services-HDInsight-and-Power-BI-on-Azure-Government">Demo zu Power BI US Government</a>
