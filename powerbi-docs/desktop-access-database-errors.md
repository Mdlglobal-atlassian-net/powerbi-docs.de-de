---
title: Beheben von Problemen beim Importieren von Access- und XLS-Dateien in Power BI Desktop
description: Beheben von Problemen beim Importieren von Access-Datenbanken und XLS-Tabellen in Power BI Desktop und Power Query
author: davidiseminger
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 10/21/2019
ms.author: davidi
LocalizationGroup: Troubleshooting
ms.openlocfilehash: 1816fb7926ed378cdb70ce2e0ade08893828ce4c
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "75761954"
---
# <a name="troubleshoot-importing-access-and-excel-xls-files-in-power-bi-desktop"></a>Problembehandlung beim Import von XLS-Dateien aus Access und Excel in Power BI Desktop

In Power BI Desktop verwenden sowohl Access-Datenbanken als auch frühe Versionen von Excel-Arbeitsmappen (XLS-Dateien vom Typ Excel 2003 bis 97) die *Access-Datenbank-Engine*. Es gibt drei häufige Situationen, die dazu führen können, dass die Access-Datenbank-Engine nicht ordnungsgemäß funktioniert.

## <a name="situation-1-no-access-database-engine-is-installed"></a>Situation 1: Es ist keine Access-Datenbank-Engine installiert.

Wenn die Power BI Desktop-Fehlermeldung angibt, dass die Access-Datenbank-Engine nicht installiert ist, müssen Sie die Version der Access-Datenbank-Engine (entweder 32 Bit oder 64 Bit) installieren, die Ihrer Version von Power BI Desktop entspricht. Sie können das Access-Datenbankmodul von der [Downloadseite](https://www.microsoft.com/download/details.aspx?id=13255) aus installieren.

>[!NOTE]
>Wenn sich die Bitversion der installierten Access-Datenbank-Engine von der Bitversion Ihrer Microsoft Office-Installation unterscheidet, können Office-Anwendungen die Access-Datenbank-Engine nicht verwenden.

## <a name="situation-2-the-access-database-engine-bit-version-32-bit-or-64-bit-is-different-from-your-power-bi-desktop-bit-version"></a>Situation 2: Die Bitversion der Access-Datenbank-Engine (32 Bit oder 64 Bit) unterscheidet sich von Ihrer Power BI Desktop-Bitversion.

Diese Situation tritt häufig auf, wenn es sich bei der installierten Version von Microsoft Office um eine 32-Bit-Version und bei Power BI Desktop um eine 64-Bit-Version handelt. Auch im umgekehrten Fall kann das Problem nicht übereinstimmender Bitversionen auftreten. Wenn Sie ein Office 365-Abonnement verwenden, orientieren Sie sich für andere Probleme und Lösungen an [Situation 3](#situation-3-trouble-using-access-or-xls-files-with-an-office-365-subscription). Der Fehler durch nicht übereinstimmende Bit-Versionen kann mithilfe jeder dieser Lösungen behoben werden:

### <a name="solution-1"></a>Lösung 1

Ändern Sie die Power BI Desktop-Version, sodass diese mit der Bitversion Ihrer Microsoft Office-Installation übereinstimmt. 

1. Um die Bitversion von Power BI Desktop zu ändern, deinstallieren Sie Power BI Desktop, und installieren Sie anschließend die Version von Power BI Desktop, die Ihrer Office-Installation entspricht. 

1. Klicken Sie auf der Power BI Desktop-Downloadseite auf **Erweiterte Downloadoptionen**, um eine Version von Power BI Desktop auszuwählen.
   
   ![Erweiterte Downloadoptionen auf der Power BI Desktop-Downloadseite](media/desktop-access-database-errors/desktop-access-errors-1.png)
   
1. Wählen Sie auf der daraufhin angezeigten Downloadseite Ihre Sprache aus, und wählen Sie dann die Schaltfläche **Herunterladen** aus. 
 
1. Aktivieren Sie auf dem daraufhin angezeigten Bildschirm das Kontrollkästchen neben „PBIDesktop.msi“ für die 32-Bit-Version oder neben „PBIDesktop_x64.msi“ für die 64-Bit-Version. 

   Auf dem folgenden Screenshot ist die 64-Bit-Version ausgewählt.
   
   ![Auswählen des Power BI Desktop-Downloads](media/desktop-access-database-errors/desktop-access-errors-2.png)
   
   >[!NOTE]
   >Wenn Sie die 32-Bit-Version von Power BI Desktop beim Erstellen sehr großer Datenmodelle verwenden, können Probleme auftreten, weil nicht genügend Arbeitsspeicher vorhanden ist.

### <a name="solution-2"></a>Lösung 2

Ändern Sie die Microsoft Office-Bitversion, sodass diese mit der Bitversion Ihrer Power BI Desktop-Installation übereinstimmt.

1. Deinstallieren Sie Microsoft Office.

2. Installieren Sie die Office-Version, die Ihrer Power BI Desktop-Installation entspricht.

### <a name="solution-3"></a>Lösung 3

Wenn der Fehler beim Öffnen einer XLS-Datei (einer Excel 2003- bis 97-Arbeitsmappe) auftritt, können Sie die Verwendung der Access-Datenbank-Engine vermeiden, indem Sie die XLS-Datei in Excel öffnen und als XLSX-Datei speichern.

### <a name="solution-4"></a>Lösung 4

Wenn die vorherigen drei Lösungen nicht möglich sind, können Sie beide Versionen der Access-Datenbank-Engine installieren. Diese Problemumgehung wird jedoch nicht empfohlen. Das Installieren beider Versionen löst dieses Problem für Power Query für Excel und Power BI Desktop zwar, führt jedoch zu Fehlern und Problemen bei Anwendungen, die automatisch (standardmäßig) die zuerst installierte Bitversion der Access-Datenbank-Engine verwenden. 

Befolgen Sie diese Schritte, um beide Bitversionen der Access-Datenbank-Engine zu installieren:

1. Installieren Sie beide Bitversionen der Access-Datenbank-Engine über die [Downloadseite](https://www.microsoft.com/download/details.aspx?id=13255). 

1. Führen Sie jede Version der Access-Datenbank-Engine mit dem Befehl */passive* aus. Beispiel:
   
       c:\users\joe\downloads\AccessDatabaseEngine.exe /passive
   
       c:\users\joe\downloads\AccessDatabaseEngine_x64.exe /passive

## <a name="situation-3-trouble-using-access-or-xls-files-with-an-office-365-subscription"></a>Situation 3: Probleme mit Access- oder XLS-Dateien bei einem Office 365-Abonnement

Wenn Sie ein Office 365-Abonnement wie **Office 2013** oder **Office 2016** verwenden, wird der Anbieter der Access-Datenbank-Engine an einem virtuellen Registrierungsstandort registriert, auf den *ausschließlich* Microsoft Office-Prozesse zugreifen können. Die Mashup-Engine kann den Anbieter für die Access-Datenbank-Engine nicht verwenden, da diese kein Office-Prozess und nicht für die Ausführung von Versionen verantwortlich ist, die nicht zu Office 365 Excel und Power BI Desktop zählen.

Sie können das Problem beheben, indem Sie [die weitervertreibbare Komponente für die Access-Datenbank-Engine herunterladen und installieren](https://www.microsoft.com/download/details.aspx?id=13255), die der Version Ihrer Power BI Desktop-Installation entspricht. Weitere Informationen zu Bitversionen finden Sie in den vorherigen Abschnitten in diesem Artikel.

## <a name="other-situations-that-can-cause-import-issues"></a>Weitere für den Import problematische Situationen

Wir sind bemüht, im Zusammenhang mit Access- und XLS-Dateien auftretende Probleme möglichst umfassend darzustellen. Wenn ein Problem auftritt, das in diesem Artikel nicht behandelt wird, können Sie sich mit entsprechenden Fragen an den [Power BI-Support](https://powerbi.microsoft.com/support/) wenden. Wir erweitern unsere Artikel regelmäßig um Lösungen für Probleme, die viele Kunden betreffen.

