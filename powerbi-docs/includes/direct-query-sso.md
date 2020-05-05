---
title: Includedatei
description: Includedatei
services: powerbi
author: davidiseminger
ms.service: powerbi
ms.topic: include
ms.date: 04/28/2020
ms.author: davidi
ms.openlocfilehash: d56988986cfd994bb21c9bc25d024903719472cf
ms.sourcegitcommit: c772c544ce2e1e2a147b9b62e5579ac3cb59d54c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/29/2020
ms.locfileid: "82255820"
---
## <a name="single-sign-on"></a>Einmaliges Anmelden

Nachdem Sie ein Azure SQL DirectQuery-Dataset im Dienst veröffentlichen, können Sie einmaliges Anmelden (Single Sign-On, SSO) über Azure AD-OAuth2 (Azure Active Directory) für Endbenutzer aktivieren.

Um SSO zu aktivieren, rufen Sie die Einstellungen für das Dataset auf, öffnen die Registerkarte **Datenquellen**, und aktivieren Sie das Kontrollkästchen „SSO“.

![Dialogfeld zum Konfigurieren von Azure SQL-Datenquellen](media/direct-query-sso/sso-dialog.png)

Wenn die Option „SSO“ aktiviert ist und Benutzer auf Berichte zugreifen, die auf der Datenquelle beruhen, werden deren authentifizierte Azure AD-Anmeldeinformationen von Power BI in den Abfragen an die Azure SQL-Datenbank oder das Data Warehouse gesendet. Mit dieser Option wird sichergestellt, dass die auf Datenquellenebene konfigurierten Sicherheitseinstellungen in Power BI berücksichtigt werden.

Die SSO-Option gilt für alle Datasets, die diese Datenquelle verwenden. Sie hat keine Auswirkungen auf das Authentifizierungsverfahren, das bei Importszenarien verwendet wird.

