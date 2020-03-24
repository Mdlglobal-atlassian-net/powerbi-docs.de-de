---
title: Erwerben und Zuweisen von Power BI Pro-Lizenzen
description: Erfahren Sie, wie Sie Power BI Pro-Benutzerlizenzen erwerben und Benutzern zuweisen, damit diese auf Inhalte zugreifen und mit Kollegen im Power BI-Dienst zusammenarbeiten können.
author: kfollis
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 01/16/2020
ms.author: kfollis
LocalizationGroup: Administration
ms.openlocfilehash: eefae2b230bf087635b79ed4645a9297b7194edd
ms.sourcegitcommit: 646d2de454a2897dc52cbc02b7743aaa021bac04
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/18/2020
ms.locfileid: "79525635"
---
# <a name="purchase-and-assign-power-bi-pro-user-licenses"></a>Erwerben und Zuweisen von Power BI Pro-Benutzerlizenzen

>[!IMPORTANT]
>Sind Sie ein Benutzer, der zum Upgrade auf eine Power BI Pro Lizenz bereit ist? Navigieren Sie direkt zu [Erste Schritte mit Power BI Pro](https://go.microsoft.com/fwlink/?LinkId=2106428&clcid=0x409&cmpid=pbidocs-purchasing-power-bi-pro), um Ihr Konto einzurichten.

Power BI Pro wird als Einzelbenutzerlizenz bereitgestellt, die Benutzern das Lesen von und Interagieren mit Berichten und Dashboards ermöglicht, die andere im Power BI-Dienst veröffentlicht haben. Benutzer mit diesem Lizenztyp können Inhalte freigeben und mit anderen Power BI Pro-Benutzern zusammenarbeiten. Nur Power BI Pro-Benutzer können Inhalte veröffentlichen oder für andere Benutzer freigeben und Inhalte nutzen, die von anderen Benutzern erstellt wurden – es sei denn, diese Inhalte werden in einer Power BI Premium-Kapazität gehostet. Weitere Informationen finden Sie auf der Website [Power BI – Preise](https://powerbi.microsoft.com/pricing/) im Abschnitt _Vergleich der Power BI-Funktionen_.

## <a name="purchase-power-bi-pro-user-licenses"></a>Erwerben von Power BI Pro-Benutzerlizenzen

In diesem Artikel wird erläutert, wie Sie Power BI Pro-Benutzerlizenzen im Microsoft 365 Admin Center erwerben. Nach dem Erwerb von Lizenzen können Sie diese Benutzern entweder im Microsoft 365 Admin Center oder im Azure-Portal zuweisen.

> [!NOTE]
> Ab dem 14. Januar 2020 stehen für kommerzielle Cloudkunden Self-Service-Einkaufs-, Abonnement- und Lizenzverwaltungsfunktionen für Power Platform-Produkte (Power BI, Power Apps und Power Automate) zur Verfügung. Weitere Informationen – einschließlich der Schritte zum Aktivieren oder Deaktivieren des Self-Service-Erwerbs in Ihrer Organisation – finden Sie unter [FAQ zum Self-Service-Kauf](https://docs.microsoft.com/microsoft-365/commerce/subscriptions/self-service-purchase-faq).

### <a name="prerequisites"></a>Voraussetzungen

Um Lizenzen im Microsoft 365 Admin Center zu erwerben und zuzuweisen, müssen Sie Mitglied der Rolle **[Globaler Administrator oder Abrechnungsadministrator](https://support.office.com/article/about-office-365-admin-roles-da585eea-f576-4f55-a1e0-87090b6aaa9d)** in Microsoft 365 sein.

Für die Lizenzzuweisung im Azure-Portal müssen Sie ein Besitzer des Azure-Abonnements sein, das Power BI für Suchvorgänge in Active Directory verwendet.

### <a name="purchase-licenses-in-microsoft-365"></a>Erwerben von Lizenzen in Microsoft 365

Führen Sie diese Schritte aus, um Power BI Pro-Lizenzen im Microsoft 365 Admin Center zu erwerben:

1. Melden Sie sich beim [Microsoft 365 Admin Center](https://admin.microsoft.com) an.

2. Klicken Sie im Navigationsmenü auf **Abrechnung** > **Dienste erwerben**.

3. Suchen Sie das Abonnement, oder scrollen Sie zu dem Abonnement, das Sie erwerben möchten. Sie finden **Power BI** unter **Weitere Kategorien, die Sie interessieren könnten** im unteren Bereich der Seite. Klicken Sie auf den Link, um die für Ihre Organisation verfügbaren Power BI-Abonnements anzuzeigen.

4. Wählen Sie **Power BI Pro**aus.

5. Klicken Sie auf der Seite **Dienste erwerben** auf **Kaufen**.

6. Wählen Sie je nach bevorzugter Zahlungsart **Monatlich bezahlen** oder **Für ein volles Jahr bezahlen** aus.

7. Geben Sie unter **Wie viele Benutzerlizenzen möchten Sie erwerben?** die gewünschte Anzahl von Lizenzen ein, und klicken Sie dann auf **Jetzt auschecken**, um die Transaktion abzuschließen.

8. Um Ihren Kauf zu bestätigen, wechseln Sie zu **Abrechnung** > **Produkte und Dienste**, und suchen Sie nach **Power BI Pro**.

9. Um weitere Lizenzen hinzuzufügen, suchen Sie auf der Seite **Produkte und Dienste** nach **Power BI Pro**, und klicken Sie dann auf **Lizenzen hinzufügen/entfernen**.

## <a name="assign-licenses-in-the-microsoft-365-admin-center"></a>Zuweisen von Lizenzen im Microsoft 365 Admin Center

Informationen zum Zuweisen von Lizenzen im Microsoft 365 Admin Center finden Sie im Artikel [Zuweisen von Lizenzen für Benutzer](/office365/admin/manage/assign-licenses-to-users).

Informationen zum Zuweisen von Lizenzen für Gastbenutzer finden Sie im Artikel [Zuweisen von Lizenzen für Benutzer auf der Seite „Lizenzen“](/office365/admin/manage/assign-licenses-to-users#assign-licenses-to-users-on-the-licenses-page). Bevor Sie Gastbenutzern Pro-Lizenzen zuweisen, wenden Sie sich an Ihren Microsoft-Kundenbetreuer, um sicherzustellen, dass Sie die Bedingungen Ihrer Vereinbarung mit Microsoft einhalten.

## <a name="assign-licenses-in-the-azure-portal"></a>Zuweisen von Lizenzen im Azure-Portal

Führen Sie folgende Schritte aus, um einzelnen Benutzerkonten Power BI Pro-Lizenzen zuzuweisen:

1. Melden Sie sich beim [Azure-Portal](https://portal.azure.com/) an.

2. Suchen Sie nach **Azure Active Directory**, und wählen Sie diese Option aus.

3. Klicken Sie im Ressourcenmenü **Azure Active Directory** unter **Verwalten** auf **Lizenzen**.

4. Wählen Sie in **Lizenzen – Übersicht** die Option **Alle Produkte** und dann **Power BI Pro** aus, um die Liste der lizenzierten Benutzer anzuzeigen.

5. Wählen Sie in der Befehlsleiste **+ Zuweisen** aus. Wählen Sie auf der Seite **Lizenz zuweisen** zunächst einen Benutzer und dann **Zuweisungsoptionen** aus, um eine Power BI Pro-Lizenz für das ausgewählte Benutzerkonto zu aktivieren.

## <a name="next-steps"></a>Nächste Schritte

Nachdem Sie die Lizenzen zugewiesen haben, informieren Sie sich eingehend über Power BI Pro.

[Power BI licensing in your organization (Power BI-Lizenzierung in Ihrem Unternehmen)](service-admin-licensing-organization.md)

[Suchen nach angemeldeten Power BI-Benutzern](service-admin-access-usage.md)

Weitere Fragen? [Stellen Sie Ihre Frage in der Power BI-Community.](https://community.powerbi.com/)
