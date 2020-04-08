---
ms.openlocfilehash: 26f4b82301915524b65d9d2d6b39d61b54ed0321
ms.sourcegitcommit: 8eeb784fd46321680367ac913ef976aeedaa7766
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/03/2020
ms.locfileid: "80621610"
---
Der Dienstprinzipal ist eine Authentifizierungsmethode, die verwendet kann, um einer Azure AD-Anwendung den Zugriff auf die Inhalte und die APIs im Power BI-Dienst zu ermöglichen.

Beim Erstellen einer Azure Active Directory-App (Azure AD) wird ein [Dienstprinzipalobjekt](https://docs.microsoft.com/azure/active-directory/develop/app-objects-and-service-principals#service-principal-object) angelegt. Das Dienstprinzipalobjekt, das manchmal auch einfach als *Dienstprinzipal* bezeichnet wird, ermöglicht Azure AD die Authentifizierung Ihrer App. Nach der Authentifizierung kann die App auf Azure AD-Mandantenressourcen zugreifen.

Zum Authentifizieren verwendet der Dienstprinzipal die *Anwendungs-ID* der Azure AD-App und eines der folgenden Elemente:
* Anwendungsgeheimnis
* Zertifikat