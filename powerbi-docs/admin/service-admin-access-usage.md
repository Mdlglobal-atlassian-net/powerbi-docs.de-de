---
title: Suchen nach angemeldeten Power BI-Benutzern
description: Wenn Sie Mandantenadministrator sind und sehen möchten, wer sich bei Power BI angemeldet hat, können Sie dazu die Azure Active Directory-Zugriffs- und -Verwendungsberichte verwenden.
author: kfollis
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 09/09/2019
ms.author: kfollis
LocalizationGroup: Administration
ms.openlocfilehash: 32ca01d06f4fc8c3f90f73bf8137349eed0220a6
ms.sourcegitcommit: bfc2baf862aade6873501566f13c744efdd146f3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/13/2020
ms.locfileid: "83129806"
---
# <a name="find-power-bi-users-that-have-signed-in"></a>Suchen nach angemeldeten Power BI-Benutzern

Wenn Sie Mandantenadministrator sind können Sie mithilfe der [Zugriffs- und Verwendungsberichte von Azure Active Directory](/azure/active-directory/reports-monitoring/concept-sign-ins) sehen, wer sich bei Power BI angemeldet hat.

> [!NOTE]
> Der Bericht **Anmeldungen** enthält zwar nützliche Informationen, identifiziert jedoch nicht den Lizenztyp von Benutzern. Verwenden Sie das Microsoft 365 Admin Center, um Lizenzen anzuzeigen.

## <a name="requirements"></a>Anforderungen

Alle Benutzer – auch Nichtadministratoren – können einen Bericht mit den eigenen Anmeldeaktivitäten sehen. Allerdings müssen die folgenden Anforderungen erfüllt sein, um einen Bericht für alle Benutzer anzuzeigen:

* Ihr Mandant verfügt über eine Azure Active Directory Premium-Lizenz.

* Sie verfügen über eine der folgenden Rollen: „Globaler Administrator“, „Sicherheitsadministrator“ oder „Sicherheitsleseberechtigter“.

## <a name="use-the-azure-portal-to-view-sign-ins"></a>Anzeigen von Anmeldungen mit dem Azure-Portal

So können Sie Anmeldeaktivitäten anzeigen

1. Wählen Sie im **Azure-Portal** **Azure Active Directory** aus.

1. Wählen Sie unter **Überwachung** **Anmeldungen** aus.
   
    ![Screenshot der Azure-Benutzeroberfläche mit hervorgehobenen Optionen „Azure Active Directory“ und „Anmeldungen“.](media/service-admin-access-usage/azure-portal-sign-ins.png)

1. Filtern Sie die Anwendung entweder nach **Microsoft Power BI** oder nach **Power BI Gateway**, und wählen Sie **Übernehmen** aus.

    **Microsoft Power BI** filtert nach Anmeldeaktivitäten in Bezug auf den Dienst, wohingegen **Power BI Gateway** nach Anmeldeaktivitäten für das spezifische lokale Datengateway filtert.
   
    ![Screenshot des Anmeldefilters mit hervorgehobenem Feld „Anwendungen“.](media/service-admin-access-usage/sign-in-filter.png)

## <a name="export-the-data"></a>Exportieren der Daten

Sie können [einen Anmeldebericht](/azure/active-directory/reports-monitoring/quickstart-download-sign-in-report) in einem von zwei Formaten herunterladen: als CSV-Datei oder als JSON-Datei.

![Screenshot der Schaltfläche „Herunterladen“.](media/service-admin-access-usage/download-sign-in-data-csv.png)

Wählen Sie oben im Bericht **Anmeldungen** **Herunterladen** und dann eine der folgenden Optionen aus:

* **CSV** zum Herunterladen einer CSV-Datei für die aktuell gefilterten Daten.

* **JSON** zum Herunterladen einer JSON-Datei für die aktuell gefilterten Daten.

## <a name="data-retention"></a>Datenaufbewahrung

Daten zu Anmeldungen sind bis zu 30 Tage verfügbar. Weitere Informationen finden Sie unter [Aufbewahrungsrichtlinien für Azure Active Directory-Berichte](/azure/active-directory/reports-monitoring/reference-reports-data-retention).

## <a name="next-steps"></a>Weitere Schritte

[Verwenden von Überwachung in der Organisation](service-admin-auditing.md)

Weitere Fragen? [Stellen Sie Ihre Frage in der Power BI-Community.](https://community.powerbi.com/)