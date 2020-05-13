---
title: Verwalten des Power BI Desktop-Anmeldeformulars durch Administratoren
description: Hier erfahren Sie, wie Sie das Anmeldeformular beim Öffnen von Power BI Desktop verwalten können.
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 04/15/2019
ms.author: davidi
ms.openlocfilehash: 934827311e089e34e56fbcffe4d4c58a056df4ad
ms.sourcegitcommit: bfc2baf862aade6873501566f13c744efdd146f3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/13/2020
ms.locfileid: "83130246"
---
# <a name="administrators-manage-the-power-bi-desktop-sign-in-form"></a>Administratoren: Verwalten des Power BI Desktop-Anmeldeformulars
Wenn Power BI Desktop erstmalig gestartet wird, wird ein Anmeldeformular geöffnet. Dort können Informationen eingegeben werden, oder es kann die Anmeldung bei Power BI ausgeführt werden, um fortzufahren. Administratoren verwalten dieses Formular mithilfe eines Registrierungsschlüssels. 

![Anmeldeformular für Power BI Desktop](media/desktop-admin-sign-in-form/sign-in-form.png)

Administratoren verwenden den folgenden Registrierungsschlüssel, um das Anmeldeformular zu deaktivieren. Dies kann auch über globale Richtlinien mithilfe von Push an eine gesamte Organisation übertragen werden.

```
Key: HKEY_CURRENT_USER\SOFTWARE\Policies\Microsoft\Microsoft Power BI Desktop
valueName: ShowLeadGenDialog
```
Sie können auch den folgenden Schlüssel ausprobieren, der bei einigen Kunden auf der Grundlage ihrer Konfiguration erfolgreich war:

```
Key: HKEY_CURRENT_USER\SOFTWARE\Microsoft\Microsoft Power BI Desktop
valueName: ShowLeadGenDialog
```

Durch den Wert „0“ wird das Dialogfeld deaktiviert.




Weitere Fragen? [Stellen Sie Ihre Frage in der Power BI-Community.](https://community.powerbi.com/)

