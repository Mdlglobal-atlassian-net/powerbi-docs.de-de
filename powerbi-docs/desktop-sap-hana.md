---
title: Verwenden von SAP HANA in Power BI Desktop
description: Verwenden von SAP HANA in Power BI Desktop
author: davidiseminger
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 01/15/2020
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 9b205a0ae9b58acf054a9afe43196e77ee404c84
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "76753105"
---
# <a name="connect-to-sap-hana-databases-in-power-bi-desktop"></a>Herstellen einer Verbindung mit SAP HANA-Datenbanken in Power BI Desktop

Sie haben nun die Möglichkeit, mit Power BI Desktop auf *SAP HANA* -Datenbanken zuzugreifen. Für die Verwendung von SAP HANA muss der SAP HANA-ODBC-Treiber auf dem lokalen Clientcomputer installiert sein, damit die Datenverbindung für SAP HANA von Power BI Desktop ordnungsgemäß funktioniert. Sie können die SAP HANA-Clienttools, die den erforderlichen ODBC-Treiber enthalten, von [SAP-Entwicklungstools](https://tools.hana.ondemand.com/#hanatools) herunterladen. Alternativ können Sie ihn aus dem [SAP Software-Downloadcenter](https://support.sap.com/en/my-support/software-downloads.html) beziehen. Suchen Sie auf dem Softwareportal nach dem *SAP HANA CLIENT* für Windows-Computer. Da die Struktur des SAP Software Downloadcenter regelmäßig überarbeitet wird, können wir keine genaueren Angaben zu dieser Website machen.

Zum Herstellen einer Verbindung mit einer SAP HANA-Datenbank klicken Sie auf **Daten abrufen**, wählen Sie **Datenbank** > **SAP HANA-Datenbank** aus, und klicken Sie anschließend auf **Verbinden**:

![SAP HANA-Datenbank, Dialogfeld „Daten abrufen“, Power BI Desktop](media/desktop-sap-hana/sap-hana-1.png)

Geben Sie beim Herstellen einer Verbindung mit einer SAP HANA-Datenbank den Servernamen an. Geben Sie dann im Dropdown- und Eingabefeld den Port an.

In diesem Release wird SAP HANA im Modus [DirectQuery](desktop-directquery-sap-hana.md) in Power BI Desktop und im Power BI-Dienst unterstützt. Sie können Berichte, die SAP HANA im DirectQuery-Modus verwenden, im Power BI-Dienst veröffentlichen und hochladen. Darüber hinaus können Sie Berichte im Power BI-Dienst veröffentlichen und hochladen, wenn SAP HANA nicht im DirectQuery-Modus verwendet wird.

## <a name="supported-features-for-sap-hana"></a>Unterstützte Funktionen für SAP HANA

Diese Version enthält viele Funktionen für SAP HANA. Diese sind in der folgenden Liste aufgeführt:

* Der Power BI-Connector für SAP HANA verwendet für eine benutzerfreundliche Anwendung den SAP-ODBC-Treiber.

* SAP HANA unterstützt sowohl DirectQuery als auch Importoptionen

* Power BI unterstützt HANA-Informationsmodelle (z. B. Analyse- und Berechnungsansichten) und bietet optimierte Navigation.

* Mit SAP HANA lässt sich auch die direkte SQL-Funktion zur Verbindung mit Zeilen- und Spaltentabellen nutzen.

* Power BI enthält eine optimierte Navigation für HANA-Modelle.

* Power BI unterstützt SAP HANA-Variablen und -Eingangsparameter.

* Power BI unterstützt die auf HDI-Containern basierten Berechnungsansichten.

  * Die Unterstützung für auf HDI-Containern basierende Berechnungsansichten ist ab dem Power BI Desktop-Release von August 2019 in der öffentlichen Vorschau. Stellen Sie sicher, dass die HANA-Datenbankbenutzer für Power BI über Berechtigungen für den Zugriff auf den HDI-Laufzeitcontainer verfügen, der die Ansichten enthält, auf die Sie zugreifen möchten, um auf Ihre auf HDI-Container basierten Berechnungsansichten in Power BI zuzugreifen. Erstellen Sie eine Rolle, um den Zugriff auf Ihren HDI-Container zu ermöglichen. Weisen Sie anschließend dem HANA-Datenbankbenutzer, den Sie bei Power BI verwenden, die Rolle zu. (Dieser Benutzer muss wie üblich auch über die Berechtigung zum Lesen aus den Systemtabellen im \_SYS\_BI-Schema verfügen.) Ausführliche Anweisungen zum Erstellen und Zuweisen von Datenbankrollen finden Sie in der offiziellen SAP-Dokumentation. [Dieser SAP-Blogbeitrag](https://blogs.sap.com/2018/01/24/the-easy-way-to-make-your-hdi-container-accessible-to-a-classic-database-user/) bietet einen guten Ausgangspunkt.

  * Derzeit liegen einige Einschränkungen für HANA-Variablen vor, die an HDI-basierte Berechnungsansichten angefügt sind. Der Grund dieser Einschränkungen sind Fehler bei HANA.
  
    Erstens ist es nicht möglich, eine HANA-Variable auf eine freigegebene Spalte einer HDI-Container-basierten Berechnungsansicht anzuwenden. Diese Einschränkung kann mithilfe eines Upgrades auf HANA 2 Version 37.02 oder höher bzw. HANA 2 Version 42 oder höher behoben werden. Zweitens werden Standardwerte mit mehreren Einträgen für Variablen und Parameter derzeit nicht in der Power BI-Benutzeroberfläche angezeigt. Ein Fehler in SAP HANA verursacht diese Einschränkung. SAP hat bisher noch keine Lösung angekündigt.

## <a name="limitations-of-sap-hana"></a>Einschränkungen für SAP HANA

Es gibt auch wie nachfolgend dargestellt einige Einschränkungen bei der Verwendung von SAP HANA:

* NVARCHAR-Zeichenfolgen werden auf maximal 4000 Unicode-Zeichen gekürzt.
* SMALLDECIMAL wird nicht unterstützt.
* VARBINARY wird nicht unterstützt.
* Gültige Datumsangaben liegen zwischen 1899/12/30 und 9999/12/31.

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen über DirectQuery und SAP HANA finden Sie in den folgenden Ressourcen:

* [DirectQuery und SAP HANA](desktop-directquery-sap-hana.md)
* [Verwenden von DirectQuery in Power BI](desktop-directquery-about.md)
* [Power BI-Datenquellen](power-bi-data-sources.md)
* [Aktivieren der Verschlüsselung für SAP HANA](desktop-sap-hana-encryption.md)
