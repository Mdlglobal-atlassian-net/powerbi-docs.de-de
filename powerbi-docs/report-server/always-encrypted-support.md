---
title: Always Encrypted im Power BI-Berichtsserver
description: In diesem Artikel wird die Unterstützung von Always Encrypted im Power BI-Berichtsserver bei Verwendung der Datenquellentypen Microsoft SQL Server und Microsoft Azure SQL-Datenbank erläutert.
author: maggiesMSFT
ms.reviewer: cfinlan
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.topic: conceptual
ms.date: 01/22/2020
ms.author: maggies
ms.openlocfilehash: f8d711bba8dc7570f2d470554fd1d971639bbb7b
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "76710204"
---
# <a name="always-encrypted-in-power-bi-report-server"></a>Always Encrypted im Power BI-Berichtsserver

In diesem Artikel wird die Unterstützung von Always Encrypted im Power BI-Berichtsserver bei Verwendung der Datenquellentypen Microsoft SQL Server und Microsoft Azure SQL-Datenbank erläutert. Weitere Informationen zu den Always Encrypted-Funktionen in SQL Server finden Sie im [Artikel zu Always Encrypted](https://docs.microsoft.com/sql/relational-databases/security/encryption/always-encrypted-database-engine).

## <a name="always-encrypted-user-isolation"></a>Always Encrypted-Benutzerisolation

Zur Zeit schränkt der Power BI-Berichtsserver den Zugriff auf die Always Encrypted-Spalten in Berichten nicht ein, wenn ein Benutzer Zugriff auf den Bericht hat.  Wenn der Server also über den Spaltenhauptschlüssel Zugriff auf die Spaltenverschlüsselungsschlüssel erhalten hat, dann haben die Benutzer Zugriff auf alle Spalten für die Berichte, auf die sie zugreifen können.

## <a name="always-encrypted-column-usage"></a>Verwendung der Always Encrypted-Spalte

### <a name="key-storage-strategies"></a>Strategien für Schlüsselspeicher

|Storage  |Unterstützt  |
|---------|---------|
|Windows-Zertifikatspeicher | Ja |
|Azure Key Vault | Nein |
| Cryptography Next Generation (CNG) | Nein |

### <a name="certificate-storage-and-access"></a>Speicher für das Zertifikat und Zugriff auf das Zertifikat

Das Konto, das den Zugriff auf das Zertifikat erfordert, ist das Dienstkonto. Das Zertifikat sollte im Zertifikatsspeicher des lokalen Computers gespeichert werden. Weitere Informationen finden Sie unter:

- [Konfigurieren des Berichtsserver-Dienstkontos (SSRS-Konfigurations-Manager)](https://docs.microsoft.com/sql/reporting-services/install-windows/configure-the-report-server-service-account-ssrs-configuration-manager)
- Im Abschnitt [Verfügbarmachen von Zertifikaten für Anwendungen und Benutzer](https://docs.microsoft.com/sql/relational-databases/security/encryption/create-and-store-column-master-keys-always-encrypted#making-certificates-available-to-applications-and-users) im Artikel „Erstellen und Speichern von Spaltenhauptschlüsseln für Always Encrypted“ von SQL Server.

### <a name="column-encryption-strategy"></a>Spaltenverschlüsselungsstrategie

Im Power BI-Berichtsserver kann die Spaltenverschlüsselungsstrategie *deterministisch* oder *zufällig* sein. In der folgenden Tabelle werden die Unterschiede je nach verwendeter Strategie erläutert.

|Zweck  |Deterministisch  |Zufällig  |
|---------|---------|---------|
|kann in den Ergebnissen einer Abfrage, z. B. SELECT-Anweisungen, in der vorliegenden Form gelesen werden | Ja  | Ja  |
|kann als eine GROUP BY-Entität innerhalb der Abfrage verwendet werden | Ja | Nein |
|kann mit Ausnahme von COUNT und DISTINCT als aggregiertes Feld verwendet werden | nein, außer für COUNT und DISTINCT | Nein |
|kann als Berichtsparameter verwendet werden | Ja | Nein |

Lesen Sie hier mehr über die [deterministische oder zufällige Verschlüsselung](https://docs.microsoft.com/sql/relational-databases/security/encryption/always-encrypted-database-engine#selecting--deterministic-or-randomized-encryption).

### <a name="parameter-usage"></a>Parameterverwendung

Die Parameterverwendung gilt nur für die deterministische Verschlüsselung.

**Parameter mit nur einem Wert:**  Sie können einen Parameter mit nur einem Wert für eine Always Encrypted-Spalte verwenden.

**Ein Parameter, der mehrere Werte enthält:** Sie können einen Parameter, der mehr als einen Wert enthält, nicht für eine Always Encrypted-Spalte verwenden.

**Kaskadierende Parameter:** Sie können kaskadierende Parameter mit Always Encrypted verwenden, wenn *alle* folgenden Bedingungen zutreffen:

- Alle Always Encrypted-Spalten müssen mit einer deterministischen Strategie Always Encrypted sein.
- Alle für Always Encrypted-Spalten verwendeten Parameter sind Parameter mit nur einem Wert.
- Alle SQL-Vergleiche verwenden Gleichheitsoperatoren (=).

## <a name="datatype-support"></a>Datentypunterstützung

| SQL-Datentyp | Unterstützt das Lesen eines Felds | Unterstützt die Verwendung als GROUP BY-Element | Unterstützte Aggregationen (COUNT, DISTINCT, MAX, MIN, SUM, etc.) | Unterstützt das Filtern mithilfe von Gleichheitsparametern | Notizen |
| --- | --- | --- | --- | --- | --- |
| int | Ja | Ja | COUNT, DISTINCT | ja, als ganze Zahl |   |
| float | Ja | Ja | COUNT, DISTINCT | ja, als Float |   |
| NVARCHAR | Ja | Ja | COUNT, DISTINCT | ja, als Text | Die deterministische Verschlüsselung muss eine Spaltensortierung mit einer binary2-Sortierreihenfolge für Zeichenspalten verwenden. Weitere Informationen finden Sie im [Artikel zu Always Encrypted](https://docs.microsoft.com/sql/relational-databases/security/encryption/always-encrypted-database-engine#selecting--deterministic-or-randomized-encryption) von SQL Server.  |
| varchar | Ja | Ja | COUNT, DISTINCT | Nein |   |
| Decimal | Ja | Ja | COUNT, DISTINCT | Nein |   |
| numeric | Ja | Ja | COUNT, DISTINCT | Nein |   |
| datetime | Ja | Ja | COUNT, DISTINCT | Nein |   |
| datetime2 | Ja | Ja | COUNT, DISTINCT | ja, als Datum/Uhrzeit | Dies wird unterstützt, wenn eine Spalte keine Genauigkeit im Millisekundenbereich aufweist, d. h., wenn datetime2(0) nicht vorliegt. |

## <a name="aggregation-alternatives"></a>Aggregationsalternativen

Derzeit werden nur solche Aggregationen für deterministische Always Encrypted-Spalten unterstützt, die direkt den Gleichheitsoperator (=) verwenden. Diese Einschränkung von SQL Server ist auf die Natur der Always Encrypted-Spalten zurückzuführen. Benutzer müssen innerhalb des Berichts statt in der Datenbank aggregieren.

## <a name="always-encrypted-in-connection-strings"></a>Always Encrypted in Verbindungszeichenfolgen

Sie müssen Always Encrypted in der Verbindungszeichenfolge für eine SQL Server-Datenquelle aktivieren. Lesen Sie hierzu mehr unter [Aktivieren von Always Encrypted für Anwendungsabfragen](https://docs.microsoft.com/sql/relational-databases/security/encryption/develop-using-always-encrypted-with-net-framework-data-provider#enabling-always-encrypted-for-application-queries).

## <a name="next-steps"></a>Weitere Schritte

[Always Encrypted](https://docs.microsoft.com/sql/relational-databases/security/encryption/always-encrypted-database-engine) für SQL Server und Azure SQL-Datenbank

Weitere Fragen? [Stellen Sie Ihre Frage in der Power BI-Community.](https://community.powerbi.com/)

