---
ms.openlocfilehash: 8dc488a47ac2b5b4e7980b7404b2722b1120b6ab
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "77464386"
---
## <a name="validate-the-roles-within-power-bi-desktop"></a>Überprüfen der Rollen in Power BI Desktop
Nachdem Sie Ihre Rollen erstellt haben, können Sie die Ergebnisse der Rollen in Power BI Desktop testen.

1. Klicken Sie auf der Registerkarte **Modellierung** auf die Option **Als Rollen anzeigen**. 

    ![Klicken auf „Als Rollen anzeigen“](./media/rls-desktop-view-as-roles/powerbi-desktop-rls-view-as-roles.png)

    Das Fenster **Als Rollen anzeigen** wird angezeigt, in dem Sie sich die erstellten Rollen ansehen können.

    ![Fenster „Als Rollen anzeigen“](./media/rls-desktop-view-as-roles/powerbi-desktop-rls-view-as-roles-dialog.png)

3. Wählen Sie eine von Ihnen erstellte Rolle aus, und klicken Sie anschließend auf **OK**, um diese Rolle anzuwenden. 

   Die Berichte rendert dann die Daten, die für diese Rolle relevant sind.

4. Sie können auch **Anderer Benutzer** auswählen und einen bestimmten Benutzer angeben. 

    ![Klicken auf „Anderer Benutzer“](./media/rls-desktop-view-as-roles/powerbi-desktop-rls-other-user.png)

   Es wird empfohlen, den Benutzerprinzipalnamen (User Principal Name; UPN) anzugeben, da der Power BI-Dienst und der Power BI-Berichtsserver diesen verwenden.

   In Power BI Desktop zeigt die Option **Anderer Benutzer** nur dann unterschiedliche Ergebnisse an, wenn Sie die dynamische Sicherheit auf Ihren DAX-Ausdrücken basierend verwenden. 

5. Klicken Sie auf **OK**. 

   Die Berichte werden auf Grundlage dessen gerendert, was dem Benutzer angezeigt wird.



