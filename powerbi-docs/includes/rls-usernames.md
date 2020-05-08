---
ms.openlocfilehash: 3e89344ef1298864b485f465b28c56397a7e1511
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "61193816"
---
## <a name="using-the-username-or-userprincipalname-dax-function"></a>Verwenden der DAX-Funktion „username()“ oder „userprincipalname()“
Sie können die DAX-Funktion *username()* oder *userprincipalname()* in Ihrem Dataset verwenden. Sie können beide Funktionen in Ausdrücken in Power BI Desktop verwenden. Wenn Sie Ihr Modell veröffentlichen, wird es im Power BI-Dienst verwendet.

In Power BI Desktop gibt *username()* einen Benutzer im Format *DOMÄNE\Benutzer* und *userprincipalname()* einen Benutzer im Format <em>user@contoso.com</em> zurück.

Im Power BI-Dienst geben sowohl *username()* als auch *userprincipalname()* den Benutzerprinzipalnamen (User Principal Name, UPN) des Benutzers zurück. Dieser ähnelt einer E-Mail-Adresse.

