---
ms.openlocfilehash: 27d6db6cf8ad8ebd7b2c957954ceec34b83681d0
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "77464389"
---
## <a name="define-roles-and-rules-in-power-bi-desktop"></a>Definieren von Rollen und Regeln in Power BI Desktop
Sie können Rollen und Regeln in Power BI Desktop definieren. Wenn Sie etwas in Power BI veröffentlichen, werden auch die Rollendefinitionen veröffentlicht.

Gehen Sie folgendermaßen vor, wenn Sie Sicherheitsrollen definieren möchten.

1. Importieren Sie Daten in Ihren Power BI Desktop-Bericht, oder konfigurieren Sie eine DirectQuery-Verbindung.
   
   > [!NOTE]
   > Sie können in Power BI Desktop keine Rollen für Analysis Services-Liveverbindungen definieren. Sie müssen sie im Analysis Services-Modell definieren.
   > 
   > 
2. Klicken Sie auf der Registerkarte **Modellierung** auf die Option **Rollen verwalten**.
   
   ![Klicken auf „Rollen verwalten“](./media/rls-desktop-define-roles/powerbi-desktop-security.png)
3. Klicken Sie im Fenster **Rollen verwalten** auf **Erstellen**.
   
   ![Wählen Sie „Erstellen“ aus.](./media/rls-desktop-define-roles/powerbi-desktop-security-create-role.png)
4. Geben Sie unter **Rollen** der Rolle einen Namen. 
5. Wählen Sie unter **Tabellen** die Tabelle aus, auf die eine DAX-Regel angewendet werden soll.
6. Geben Sie im Feld **Tabellenfilter-DAX-Ausdruck** DAX-Ausdrücke ein. Dieser Ausdruck gibt TRUE oder FALSE als Wert zurück. Beispiel: ```[Entity ID] = “Value”```
      
   ![Fenster „Rollen verwalten“](./media/rls-desktop-define-roles/powerbi-desktop-security-create-rule.png)

   > [!NOTE]
   > Sie können *username()* innerhalb dieses Ausdrucks verwenden. Beachten Sie, dass *username()* in Power BI Desktop das Format *DOMÄNE\Benutzername* aufweist. Im Power BI-Dienst und im Power BI-Berichtsserver entspricht das Format dem Benutzerprinzipalnamen des Benutzers. Alternativ können Sie *userprincipalname()* verwenden, wodurch der Benutzer immer im Format seines Benutzerprinzipalnamens (*Benutzername\@contoso.com*) zurückgegeben wird.
   > 
   > 

7. Klicken Sie nach der Erstellung des DAX-Ausdrucks auf das Häkchen über dem Ausdrucksfeld, um den Ausdruck zu überprüfen.
      
   ![Ein gültiger DAX-Ausdruck](./media/rls-desktop-define-roles/powerbi-desktop-security-validate-dax.png)
   
   > [!NOTE]
   > In diesem Ausdrucksfeld verwenden Sie Kommas, um Argumente der DAX-Funktion zu trennen, auch wenn Sie ein Gebietsschema verwenden, das normalerweise Semikolontrennzeichen verwendet (z. B. Französisch oder Deutsch). 
   >
   >
   
8. Wählen Sie **Speichern**.

In Power BI Desktop ist es nicht möglich, Benutzer einer Rolle zuzuweisen. Sie können diese Zuweisung im Power BI-Dienst vornehmen. Sie können die dynamische Sicherheit in Power BI Desktop aktivieren, indem Sie *username()* - oder *userprincipalname()* -DAX-Funktionen verwenden und die richtigen Beziehungen konfigurieren. 

