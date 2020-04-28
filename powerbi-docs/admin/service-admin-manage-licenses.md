---
title: Anzeigen und Verwalten von Power BI-Benutzerlizenzen
description: Hier finden Sie Informationen dazu, wie Administratoren die Power BI-Benutzerlizenzen in Ihrer Organisation anzeigen und verwalten können.
author: kfollis
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 04/08/2020
ms.author: kfollis
LocalizationGroup: Administration
ms.openlocfilehash: c3f0b536695f5ed126ddc82c9e1891d317ef953f
ms.sourcegitcommit: b2cb0b02bdc451bf11a92a68f2c4d560a811f563
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2020
ms.locfileid: "81447439"
---
# <a name="view-and-manage-power-bi-user-licenses"></a>Anzeigen und Verwalten von Power BI-Benutzerlizenzen

In diesem Artikel wird erläutert, wie Administratoren das Microsoft 365 Admin Center oder das Azure-Portal verwenden können, um Benutzerlizenzen anzuzeigen und zu verwalten.

> [!NOTE]
>
>Es ist möglich, dass einem Benutzer sowohl eine Power BI Free- als auch eine Power BI Pro-Lizenz zugewiesen ist. Das kann vorkommen, wenn sich ein Benutzer für eine kostenlose Lizenz registriert und ihm später eine Power BI Pro-Lizenz zugewiesen wird. In diesem Fall wird die höchste Lizenzierungsstufe wirksam.
>

## <a name="view-your-subscriptions"></a>Anzeigen Ihrer Abonnements

Führen Sie die folgenden Schritte aus, um zu sehen, welche Power BI-Abonnements Ihre Organisation besitzt.

1. Melden Sie sich beim [Microsoft 365 Admin Center](https://admin.microsoft.com) an.
2. Klicken Sie im Navigationsmenü auf **Abrechnung** > **Produkte und Dienste**.

Ihre aktiven Power BI-Abonnements werden zusammen mit allen anderen Abonnements aufgelistet, die Sie besitzen. Möglicherweise wird wie in diesem Beispiel ein unerwartetes Abonnement für Power BI Free angezeigt.

  ![Durch Benutzer aktiviertes Power BI Free-Abonnement](media/service-admin-manage-licenses/power-bi-free-user-activated.png)

Dieser Abonnementtyp wird für Sie erstellt, wenn Benutzer die Self-Service-Registrierung nutzen. Weitere Informationen finden Sie unter [Power BI in Ihrer Organisation](https://docs.microsoft.com/microsoft-365/admin/misc/power-bi-in-your-organization?view=o365-worldwide).

## <a name="manage-user-licenses-in-microsoft-365"></a>Verwalten von Benutzerlizenzen in Microsoft 365

Informationen zur Verwendung des Microsoft 365 Admin Center zum Verwalten von Benutzerlizenzen finden Sie in der Dokumentation zu [Business-Abonnements und Abrechnung](https://docs.microsoft.com/microsoft-365/commerce/?view=o365-worldwide).

## <a name="manage-user-licenses-in-azure-portal"></a>Verwalten von Benutzerlizenzen im Azure-Portal

Führen Sie die folgenden Schritte aus, um Power BI-Lizenzen mithilfe des Azure-Portals anzuzeigen und zuzuweisen.

1. Melden Sie sich beim [Azure-Portal](https://portal.azure.com) an.

2. Suchen Sie nach **Azure Active Directory**, und wählen Sie diese Option aus.

3. Klicken Sie im Ressourcenmenü in Azure Active Directory unter **Verwalten** auf **Lizenzen**.

4. Wählen Sie in im Ressourcenmenü die Option **Alle Produkte** und dann den Power BI-Lizenztyp aus, um die Liste der lizenzierten Benutzer anzuzeigen.

5. Klicken Sie in der Befehlsleiste auf **+ Zuweisen**, um eine Lizenz zuzuweisen. Wählen Sie auf der Seite **Lizenz zuweisen** einen Benutzer aus, und klicken Sie dann auf **Zuweisungsoptionen**, um eine Power BI-Lizenz für das ausgewählte Benutzerkonto zu aktivieren.

6. Aktivieren Sie das Kontrollkästchen neben dem Namen des Benutzers, und wählen Sie **Lizenz entfernen** aus, um eine Lizenz zu entfernen.

## <a name="next-steps"></a>Nächste Schritte

- [Power BI Pro kaufen](../service-admin-purchasing-power-bi-pro.md)
- [Lizenzierung für Ihre Organisation](../service-admin-licensing-organization.md)
