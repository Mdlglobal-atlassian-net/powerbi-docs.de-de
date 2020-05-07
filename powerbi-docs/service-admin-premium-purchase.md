---
title: Erwerben von Power BI Premium
description: Erfahren Sie, wie Sie Power BI Premium erwerben und den Zugriff auf Inhalte für Ihre gesamte Organisation ermöglichen können.
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 02/13/2020
LocalizationGroup: Premium
ms.openlocfilehash: aed0d1e4dec6f6efe49dd39cd5b6fc60f8977e44
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "79488612"
---
# <a name="how-to-purchase-power-bi-premium"></a>Erwerben von Power BI Premium

In diesem Artikel wird beschrieben, wie Sie eine Power BI Premium-Kapazität für Ihre Organisation erwerben. In diesem Artikel werden zwei Szenarios beschrieben:

- Verwenden von P-SKUs für übliche Produktionsszenarios. Für P-SKUs gilt ein monatlicher oder jährlicher Prepaidtarif, und sie werden monatlich abgerechnet.

- Verwenden von A-SKUs für Testszenarios und für Fälle, in denen Sie nicht die Berechtigungen haben, um P-SKUs erwerben zu können (Microsoft 365-Rollen „Globaler Administrator“ oder „Rechnungsadministrator“). Tarife für A-SKUs sind nicht zeitlich gebunden und werden stündlich abgerechnet. A-SKUs können Sie über das [Azure-Portal](https://portal.azure.com) erwerben.

Weitere Informationen über Power BI Premium finden Sie unter [Was ist Power BI Premium?](service-premium-what-is.md). Aktuelle Informationen zu Preisen und zur Planung finden Sie auf der [Seite zu den Power BI-Preisen](https://powerbi.microsoft.com/pricing/) und über den [Power BI Premium-Rechner](https://powerbi.microsoft.com/calculator/). Auch wenn Ihre Organisation Power BI Premium verwendet, benötigen Inhaltsautoren weiterhin eine [Power BI Pro-Lizenz](service-admin-purchasing-power-bi-pro.md). Stellen Sie sicher, dass Sie mindestens eine Power BI Pro-Lizenz für Ihre Organisation erwerben. Bei A-SKUs benötigen _alle Benutzer_, die Inhalte nutzen möchten, Power BI Pro-Lizenzen.

> [!NOTE]
> Wenn ein Power BI Premium-Abonnement abläuft, bleibt der vollständige Zugriff auf die Kapazität 30 Tage lang erhalten. Danach wird der Inhalt auf eine gemeinsam genutzte Kapazität zurückgesetzt. Modelle mit mehr als 1 GB werden in gemeinsam genutzten Kapazitäten nicht unterstützt.

## <a name="purchase-p-skus-for-typical-production-scenarios"></a>Erwerben von P-SKUs für übliche Produktionsszenarios

Sie können entweder einen neuen Mandanten mit einer konfigurierten P1-SKU für Power BI Premium erstellen, oder Sie kaufen eine Power BI Premium-Kapazität für eine bereits bestehende Organisation. In beiden Fällen können Sie bei Bedarf Kapazität hinzufügen.

### <a name="create-a-new-tenant-with-power-bi-premium-p1"></a>Erstellen eines neuen Mandanten mit Power BI Premium P1

Wenn Sie noch nicht über einen Mandanten verfügen und einen erstellen möchten, können Sie gleichzeitig Power BI Premium erwerben. Der folgende Link führt Sie durch die Schritte zum Erstellen eines neuen Mandanten und ermöglicht Ihnen den Erwerb von Power BI Premium: [Power BI Premium-P1-Angebot](https://signup.microsoft.com/Signup?OfferId=b3ec5615-cc11-48de-967d-8d79f7cb0af1). Wenn Sie den Mandanten erstellen, wird Ihnen automatisch die globale Microsoft 365-Administratorrolle für diesen Mandanten zugewiesen.

Nachdem Sie Kapazität erworben haben, sollten Sie lernen, wie Sie [Kapazitäten verwalten](service-admin-premium-manage.md#manage-capacity) und einer Kapazität [Arbeitsbereiche zuweisen](service-admin-premium-manage.md#assign-a-workspace-to-a-capacity).

### <a name="purchase-a-power-bi-premium-capacity-for-an-existing-organization"></a>Erwerben einer Power BI Premium-Kapazität für eine vorhandene Organisation

Wenn Sie über eine vorhandene Organisation (einen Mandanten) verfügen, müssen Sie über die globale Microsoft 365-Administratorrolle oder die Rechnungsadministratorrolle verfügen, um Abonnements und Lizenzen zu erwerben. Weitere Informationen finden Sie unter [Informationen zu Microsoft 365-Administratorrollen](https://support.office.com/article/About-Office-365-admin-roles-da585eea-f576-4f55-a1e0-87090b6aaa9d).

Führen Sie die folgenden Schritte aus, um eine Premium-Kapazität zu erwerben.

1. Klicken Sie im Power BI-Dienst auf die Microsoft 365-App-Auswahl, und wählen Sie dann **Administrator** aus.

    ![Microsoft 365-App-Auswahl](media/service-admin-premium-purchase/o365-app-picker.png)

    Alternativ können Sie zum Microsoft 365 Admin Center wechseln.

1. Wählen Sie **Abrechnung** > **Dienste erwerben** aus.

1. Suchen Sie unter **Andere Pläne** nach Angeboten für Power BI Premium. Diese werden als P1 bis P3, EM3 und P1 (monatlich) aufgeführt.

1. Zeigen Sie mit dem Mauszeiger auf die Auslassungspunkte ( **...** ), und klicken Sie dann auf **Jetzt kaufen**.

    ![Jetzt kaufen](media/service-admin-premium-purchase/premium-purchase.png)

1. Führen Sie die Schritte zum Abschließen des Kaufs aus.

Nachdem Sie den Kauf abgeschlossen haben, zeigt die Seite **Dienste kaufen** an, dass das Angebot erworben wurde und aktiv ist.

![Power BI Premium](media/service-admin-premium-purchase/premium-purchased.png)

Nachdem Sie Kapazität erworben haben, sollten Sie lernen, wie Sie [Kapazitäten verwalten](service-admin-premium-manage.md#manage-capacity) und einer Kapazität [Arbeitsbereiche zuweisen](service-admin-premium-manage.md#assign-a-workspace-to-a-capacity).

### <a name="purchase-additional-capacities"></a>Erwerben zusätzlicher Kapazitäten

Da Sie nun über eine Kapazität verfügen, können Sie weitere hinzufügen, wenn Ihre Anforderungen steigen. Darüber hinaus können Sie innerhalb Ihrer Organisation beliebige Kombinationen von Premium-Kapazitäts-SKUs (P1 bis P3) verwenden. Die unterschiedlichen SKUs bieten unterschiedliche Ressourcenfunktionen an.

1. Klicken Sie im Microsoft 365 Admin Center auf **Abrechnung** > **Dienste kaufen**.

1. Suchen Sie unter **Andere Pläne** den Power BI Premium-Artikel aus, von dem Sie mehr erwerben möchten.

1. Zeigen Sie mit dem Mauszeiger auf **Weitere Optionen** (...), und wählen Sie dann **Lizenzanzahl ändern** aus.

    ![Lizenzanzahl ändern](media/service-admin-premium-purchase/premium-purchase-more.png)

1. Ändern Sie die Anzahl der Instanzen, über die Sie von diesem Artikel verfügen möchten. Wählen Sie dann **Senden** aus, wenn Sie fertig sind.

   > [!IMPORTANT]
   > Wenn Sie auf **Senden** klicken, wird die hinterlegte Kreditkarte belastet.

Die Seite **Kaufdienste** weist dann die Anzahl der Instanzen aus, über die Sie verfügen. Im Power BI-Verwaltungsportal geben die unter **Kapazitätseinstellungen** als verfügbar angegebenen V-Kerne die neue erworbene Kapazität wieder.

![Verfügbare V-Kerne für Power BI Premium-Kapazität](media/service-admin-premium-purchase/premium-capacities.png)

### <a name="cancel-your-subscription"></a>Kündigen Ihres Abonnements

Sie können Ihr Abonnement über das Microsoft 365 Admin Center kündigen. Gehen Sie wie folgt vor, um Ihr Premium-Abonnement zu kündigen.

1. Navigieren Sie zum Microsoft 365 Admin Center.

1. Wählen Sie **Abrechnung** > **Abonnements** aus.

1. Wählen Sie Ihr Power BI Premium-Abonnement aus der Liste aus.

1. Klicken Sie auf **Weitere Aktionen** > **Abonnement kündigen**.

1. Auf der Seite **Abonnement kündigen** wird angegeben, ob für Sie [Gebühren wegen vorzeitiger Beendigung](https://support.office.com/article/early-termination-fees-6487d4de-401a-466f-8bc3-c0beb5cc40d3) anfallen. Auf dieser Seite wird Ihnen außerdem mitgeteilt, wann die Daten für das Abonnement gelöscht werden.

1. Lesen Sie die Informationen. Wenn Sie fortfahren möchten, wählen Sie **Abonnement kündigen** aus.

#### <a name="when-canceling-or-your-license-expires"></a>Kündigung oder Ablauf Ihrer Lizenz

Wenn Sie Ihr Premium-Abonnement kündigen oder Ihre Kapazitätslizenz abläuft, können Sie weiterhin für einen Zeitraum von 30 Tagen ab dem Datum der Kündigung oder des Ablaufs der Lizenz auf Ihre Premium-Kapazitäten zugreifen. Nach 30 Tagen können Sie nicht mehr auf Ihre Premium-Kapazitäten oder die darin enthaltenen Arbeitsbereiche zugreifen.

## <a name="purchase-a-skus-for-testing-and-other-scenarios"></a>Erwerben von A-SKUs für Test- und andere Szenarios

A-SKUs werden über Azure Power BI Embedded zur Verfügung gestellt. Sie können A-SKUs folgendermaßen nutzen:

- Aktivieren der Einbettung von Power BI in Anwendungen von Drittanbietern. Weitere Informationen finden Sie im Artikel [Was ist Power BI Embedded in Azure?](developer/embedded/azure-pbie-what-is-power-bi-embedded.md)

- Testen von Premium-Funktionen vor dem Kauf einer P-SKU.

- Erstellen von Entwicklungs- und Testumgebungen parallel zu einer Produktionsumgebung, die P-SKUs verwendet.

- Erwerben von Power BI Premium, obwohl Sie keine der Microsoft 365-Rollen „Globaler Administrator“ oder „Rechnungsadministrator“ innehaben.

> [!NOTE]
> Wenn Sie eine A4- oder eine höhere SKU erwerben, können Sie alle Premium-Funktionen nutzen, mit Ausnahme der unbegrenzten Freigabe von Inhalten. Bei A-SKUs benötigen _alle Benutzer_, die Inhalte nutzen möchten, Power BI Pro-Lizenzen.

Gehen Sie folgendermaßen vor, um A-SKUs im Azure-Portal zu erwerben:

1. Melden Sie sich im [Azure-Portal](https://portal.azure.com) mit einem Konto an, das mindestens über Administratorberechtigungen für Kapazitäten in Power BI verfügt.

1. Suchen Sie nach _Power BI Embedded_, und wählen Sie den Dienst in den Suchergebnissen aus.

    ![Suchergebnisse im Azure-Portal](media/service-admin-premium-purchase/azure-portal-search.png)

1. Wählen Sie **Create Power BI Embedded** (Power BI Embedded erstellen) aus.

    ![Power BI Embedded erstellen](media/service-admin-premium-purchase/create-power-bi-embedded.png)

1. Geben Sie auf dem **Power BI Embedded**-Bildschirm für die Erstellung folgende Informationen an:

    - Das **Abonnement**, in dem Power BI Embedded erstellt werden soll

    - Der physische **Speicherort**, an dem die Ressourcengruppe erstellt werden soll, die den Dienst enthält. Dieser Speicherort sollte sich in der Nähe des Speicherorts Ihres Azure Active Directory-Mandanten für Power BI befinden, um die Leistung zu verbessern.

    - Die bereits vorhandene **Ressourcengruppe**, die verwendet werden soll. Gibt es noch keine, können Sie wie im Beispiel gezeigt eine neue erstellen.

    - Der **Power BI-Kapazitätsadministrator** Der Kapazitätsadministrator muss selbst Mitglied oder ein Dienstprinzipal in Ihrem Azure Active Directory-Mandaten sein.

    ![Abonnement und Ressourcengruppe](media/service-admin-premium-purchase/subscription-resource-group.png)

1. Wenn Sie Zugriff auf alle Funktionen von Power BI Premium haben möchten (mit Ausnahme unbegrenzter Freigabe), benötigen Sie eine A4-SKU oder höher. Wählen Sie **Größe ändern** aus.

    ![Kapazitätsumfang ändern](media/service-admin-premium-purchase/change-capacity-size.png)

1. Wählen Sie eine der Kapazitätsgrößen A4, A5 oder A6 aus, die P1, P2 und P3 entspricht.

    ![Auswählen einer A3-Kapazität](media/service-admin-premium-purchase/select-a3-capacity.png)

1. Wählen Sie **Überprüfen und erstellen** aus, überprüfen Sie die ausgewählten Optionen, und wählen Sie dann die Option **Erstellen** aus.

    ![Erstellen von Ressourcen](media/service-admin-premium-purchase/create-resource.png)

1. Die Bereitstellung kann einige Minuten dauern. Wenn sie abgeschlossen ist, wählen Sie **Zu Ressource wechseln** aus.

    ![Bereitstellung abgeschlossen](media/service-admin-premium-purchase/deployment-complete.png)

1. Sehen Sie sich auf dem Verwaltungsbildschirm die Optionen an, die Ihnen für die Verwaltung des Diensts zur Verfügung stehen, z. B. das Pausieren des Diensts, wenn Sie ihn nicht verwenden.

    ![Verwalten der Kapazität](media/service-admin-premium-purchase/manage-capacity.png)

Nachdem Sie Kapazität erworben haben, sollten Sie lernen, wie Sie [Kapazitäten verwalten](service-admin-premium-manage.md#manage-capacity) und einer Kapazität [Arbeitsbereiche zuweisen](service-admin-premium-manage.md#assign-a-workspace-to-a-capacity).

## <a name="next-steps"></a>Weitere Schritte

[Konfigurieren und Verwalten von Kapazitäten in Power BI Premium](service-admin-premium-manage.md)\
[Power BI – Preise](https://powerbi.microsoft.com/pricing/)\
[Power BI Premium-Rechner](https://powerbi.microsoft.com/calculator/)\
[Power BI Premium – Häufig gestellte Fragen](service-premium-faq.md)\
[Planning a Power BI Enterprise Deployment whitepaper (Whitepaper zum Planen der Unternehmensbereitstellung von Power BI)](https://aka.ms/pbienterprisedeploy)

Weitere Fragen? [Stellen Sie Ihre Frage in der Power BI-Community.](https://community.powerbi.com/)
