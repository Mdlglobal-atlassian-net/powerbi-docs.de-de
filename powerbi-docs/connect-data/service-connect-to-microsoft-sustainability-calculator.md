---
title: Herstellen einer Verbindung mit dem Microsoft Sustainability Calculator (Nachhaltigkeitsrechner)
description: Microsoft Sustainability Calculator für Power BI
author: joshthor3222
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: conceptual
ms.date: 01/06/2020
ms.author: v-tikid
LocalizationGroup: Connect to services
ms.openlocfilehash: 8ab3dbb500faf072b87ba398b16b820c164cdefa
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/13/2020
ms.locfileid: "83337602"
---
# <a name="connect-the-microsoft-sustainability-calculator"></a>Herstellen einer Verbindung mit dem Microsoft Sustainability Calculator (Nachhaltigkeitsrechner)
Verschaffen Sie sich Erkenntnisse über den CO2-Ausstoß Ihrer IT-Infrastruktur, um nachhaltigere IT-Entscheidungen treffen zu können.

Microsoft Sustainability Calculator bietet neue Einblicke in die mit Azure-Diensten verbundenen Daten zum CO2-Ausstoß. Die Verantwortlichen für die Berichterstattung zur Nachhaltigkeit und deren Förderung innerhalb ihrer Organisationen haben jetzt die Möglichkeit, den CO2-Ausstoß jedes Azure-Abonnements zu quantifizieren und die geschätzten CO2-Einsparungen zu ermitteln, die sich aus der Ausführung dieser Workloads in Azure im Vergleich zu lokalen Rechenzentren ergeben. Diese Daten können für die Berichterstattung zu Treibhausgasen in Bezug auf Scope 3-Emissionen verwendet werden. Für den Zugriff auf den Microsoft Sustainability Calculator benötigen Sie Ihre Mandanten-ID und Ihren Zugriffsschlüssel, die Sie in der Regel vom Azure-Administrator Ihrer Organisation erhalten.

Um diese App nutzen zu können, benötigen Sie Informationen aus dem Azure Enterprise Portal. Die Systemadministratoren Ihres Unternehmens können Ihnen möglicherweise beim Beschaffen dieser Informationen behilflich sein. Lesen Sie diese Anleitung durch, und verschaffen Sie sich vor der Installation der App die erforderlichen Informationen. 

Diese Version des Connectors unterstützt nur Enterprise-Registrierungen über [https://ea.azure.com](https://ea.azure.com/). Registrierungen in China werden derzeit nicht unterstützt.

## <a name="how-to-connect"></a>Herstellen der Verbindung
[!INCLUDE [powerbi-service-apps-get-more-apps](../includes/powerbi-service-apps-get-more-apps.md)]

1. Wählen Sie **Microsoft Sustainability Calculator** \> **Jetzt anfordern** aus.
1. Wählen Sie unter **Diese Power BI-App installieren?** die Option **Installieren** aus.
1. Wählen Sie im Bereich **Apps** die Kachel **Microsoft Sustainability Calculator** aus.
1. Klicken Sie im Fenster **Erste Schritte mit Ihrer neuen App** auf **Verbinden**.

    ![Erste Schritte mit Ihrer neuen App](media/service-connect-to-zendesk/power-bi-new-app-connect-get-started.png)

1. Geben Sie **Unternehmensname, Benutzerregistrierungsnummer** und **Anzahl der Monate\> ein, und melden Sie sich an.** Nachstehend finden Sie weitere Informationen zum [Suchen dieser Parameter](#finding-parameters).

    ![Unternehmensregistrierung](media/service-connect-to-microsoft-sustainability-calculator/company-enrollment.png)

1. Wählen Sie als **Authentifizierungsmethode** die Option **Schlüssel** und für **Datenschutzebene** die Option **Organisation** aus.
1. Geben Sie für **Schlüssel** Ihren **Zugriffsschlüssel ein. \>Melden Sie sich an**.

    ![Zugriffsschlüsseleintrag](media/service-connect-to-microsoft-sustainability-calculator/access-key-entry.png)

1. Der Importvorgang startet automatisch. Nach Abschluss des Vorgangs werden im **Navigationsbereich** ein neues Dashboard, ein Bericht und ein Modell angezeigt. Wählen Sie den Bericht aus, um die importierten Daten anzuzeigen.

## <a name="finding-parameters"></a>Suchen von Parametern

Um die **Registrierungs-ID** und den **Zugriffsschlüssel** Ihres Unternehmens zu finden, arbeiten Sie mit Ihrem Azure-Administrator zusammen, um die erforderlichen Informationen zu erhalten. Als Administrator führen Sie diese Aufgaben aus:

1. Melden Sie sich im [Azure Enterprise Portal](https://ea.azure.com) an. Klicken Sie auf dem linken Menüband auf **Verwalten**, und beziehen Sie die **Registrierungsnummer** wie unten gezeigt.
2. Klicken Sie im [Azure Enterprise Portal](https://ea.azure.com) auf **Berichte** und dann auf „API-Zugriffsschlüssel“, wie unten gezeigt, um den primären Registrierungskontoschlüssel zu erhalten.

## <a name="using-the-app"></a>Verwenden der App

Um die Parameter zu einem beliebigen Zeitpunkt zu aktualisieren, navigieren Sie zu den Einstellungen für **Dataset**. Greifen Sie auf den verknüpften App-Arbeitsbereich zu. Aktualisieren Sie die Mandanten-ID, den Unternehmensnamen oder die Monate mit den Daten. Nachdem Sie die Parameter übernommen haben, klicken Sie auf **Aktualisieren**, um die Daten mit den neuen Parametern erneut zu laden.