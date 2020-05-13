---
title: Einschränken des Datenzugriffs mit Sicherheit auf Zeilenebene (RLS) für Power BI Desktop
description: Erfahren Sie, wie Sie die Sicherheit auf Zeilenebene für importierte Datasets und DirectQuery in Power BI Desktop konfigurieren.
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.custom: ''
ms.date: 01/31/2020
LocalizationGroup: Create reports
ms.openlocfilehash: 89c33de2ef7319c6dcbeace0df79786128e16cd9
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/13/2020
ms.locfileid: "83334313"
---
# <a name="restrict-data-access-with-row-level-security-rls-for-power-bi-desktop"></a>Einschränken des Datenzugriffs mit Sicherheit auf Zeilenebene (RLS) für Power BI Desktop

Sie können die RLS zusammen mit Power BI Desktop verwenden, um den Datenzugriff bestimmter Benutzer einzuschränken. Filter beschränken die Daten auf Zeilenebene. Sie können Filter für Rollen definieren.

Sie können RLS jetzt für Datenmodelle konfigurieren, die mithilfe von Power BI Desktop in Power BI importiert wurden. Außerdem können Sie die RLS für Datasets konfigurieren, die [DirectQuery](../connect-data/desktop-use-directquery.md) verwenden. Dies ist beispielsweise für SQL Server möglich. Bisher konnte die RLS nur in lokalen Analysis Services-Modellen außerhalb von Power BI implementiert werden. Für Liveverbindungen von Analysis Services konfigurieren Sie RLS auf dem lokalen Modell. Die Sicherheitsoption wird nicht für Liveverbindungsdatasets angezeigt.

> [!IMPORTANT]
> Wenn Sie im Power BI-Dienst Rollen und Regeln definiert haben, müssen Sie diese Rollen in Power BI Desktop neu erstellen und den Bericht im Dienst veröffentlichen. Informieren Sie sich über die Optionen für [RLS innerhalb des Power BI-Diensts](../admin/service-admin-rls.md).

[!INCLUDE [include-short-name](../includes/rls-desktop-define-roles.md)]

[!INCLUDE [include-short-name](../includes/rls-desktop-view-as-roles.md)]

[!INCLUDE [include-short-name](../includes/rls-limitations.md)]

[!INCLUDE [include-short-name](../includes/rls-faq.md)]

## <a name="next-steps"></a>Weitere Schritte

[Sicherheit auf Zeilenebene (row-level security; RLS) mit Power BI](../admin/service-admin-rls.md)  

Weitere Fragen? [Stellen Sie Ihre Frage in der Power BI-Community.](https://community.powerbi.com/)