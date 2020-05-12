---
title: Dienstprinzipal – Übersicht
description: Dienstprinzipal – Übersicht
services: powerbi
author: KesemSharabi
ms.author: kesharab
ms.topic: include
ms.date: 04/05/2020
ms.custom: include file
ms.openlocfilehash: 7fc4412a66602fe3a6548c3e1afb06de788da90d
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "82616025"
---
Der Dienstprinzipal ist eine Authentifizierungsmethode, die verwendet kann, um einer Azure AD-Anwendung den Zugriff auf die Inhalte und die APIs im Power BI-Dienst zu ermöglichen.

Beim Erstellen einer Azure Active Directory-App (Azure AD) wird ein [Dienstprinzipalobjekt](https://docs.microsoft.com/azure/active-directory/develop/app-objects-and-service-principals#service-principal-object) angelegt. Das Dienstprinzipalobjekt, das manchmal auch einfach als *Dienstprinzipal* bezeichnet wird, ermöglicht Azure AD die Authentifizierung Ihrer App. Nach der Authentifizierung kann die App auf Azure AD-Mandantenressourcen zugreifen.

Zum Authentifizieren verwendet der Dienstprinzipal die *Anwendungs-ID* der Azure AD-App und eines der folgenden Elemente:
* Anwendungsgeheimnis
* Zertifikat