---
title: Hinzufügen einer benutzerdefinierten Spalte in Power BI Desktop
description: Schnelles Erstellen einer neuen benutzerdefinierten Spalte in Power BI Desktop
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 10/18/2019
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: 443053bc973005d3e2a655b1222d049a4251e7d7
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/13/2020
ms.locfileid: "83329069"
---
# <a name="add-a-custom-column-in-power-bi-desktop"></a>Hinzufügen einer benutzerdefinierten Spalte in Power BI Desktop

Mit dem Abfrage-Editor in Power BI Desktop können Sie Ihrem Modell einfach eine neue benutzerdefinierte Datenspalte hinzufügen. Mit dem Abfrage-Editor können Sie Ihre benutzerdefinierte Spalte erstellen und umbenennen, um [PowerQuery M-Formelabfragen](https://docs.microsoft.com/powerquery-m/quick-tour-of-the-power-query-m-formula-language) zum Definieren Ihrer benutzerdefinierten Spalte zu erstellen. PowerQuery M-Formelabfragen weisen einen [umfassenden Funktionsreferenz-Inhaltssatz](https://docs.microsoft.com/powerquery-m/power-query-m-function-reference) auf. 

Wenn Sie im Abfrage-Editor eine benutzerdefinierte Spalte erstellen, fügt Power BI Desktop sie den **Abfrageeinstellungen** der Abfrage als **Angewendeten Schritt** hinzu. Er kann jederzeit geändert oder verschoben werden.

![Seite „Benutzerdefinierte Spalte hinzufügen“](media/desktop-add-custom-column/add-custom-column_01.png)

## <a name="use-query-editor-to-add-a-custom-column"></a>Hinzufügen einer benutzerdefinierten Spalte mithilfe des Abfrage-Editors

Führen Sie die folgenden Schritte aus, um mit der Erstellung einer benutzerdefinierten Spalte zu beginnen:

1. Starten Sie Power BI Desktop, und laden Sie einige Daten.

2. Wählen Sie auf der Registerkarte **Start** im Menüband **Abfragen bearbeiten** und dann **Abfragen bearbeiten** im Menü aus.

   ![Auswählen von „Abfragen bearbeiten“](media/desktop-add-custom-column/add-column-from-example_02.png)

   Das **Abfrage-Editor**-Fenster wird geöffnet. 

2. Wählen Sie auf der Registerkarte **Spalte hinzufügen** im Menüband **Benutzerdefinierte Spalte** aus.

   ![Auswahl von „Benutzerdefinierte Spalte“](media/desktop-add-custom-column/add-custom-column_02.png)

   Das Fenster **Benutzerdefinierte Spalte hinzufügen** wird angezeigt.

## <a name="the-add-custom-column-window"></a>Das Fenster „Benutzerdefinierte Spalte hinzufügen“

Das Fenster **Benutzerdefinierte Spalte hinzufügen** weist die folgenden Features auf: 
- Eine Liste der verfügbaren Spalten in der Liste **Verfügbare Spalten** auf der rechten Seite.

- Den ursprünglichen Namen Ihrer benutzerdefinierten Spalte im Feld **Neuer Spaltenname**. Sie können diese Spalte umbenennen.

- [PowerQuery M-Formelabfragen](https://docs.microsoft.com/powerquery-m/power-query-m-function-reference) im Feld **Benutzerdefinierte Spaltenformel**. Sie erstellen diese Abfragen durch Erstellen der Formel, in der Ihre neue benutzerdefinierte Spalte definiert ist. 

   ![Seite „Benutzerdefinierte Spalte hinzufügen“](media/desktop-add-custom-column/add-custom-column_03.png)

## <a name="create-formulas-for-your-custom-column"></a>Erstellen von Formeln für die benutzerdefinierte Spalte

1. Wählen Sie in der Liste **Verfügbare Spalten** auf der rechten Seite eine Spalte aus, und wählen Sie dann unterhalb der Liste **Einfügen** aus, um sie der Formel für die benutzerdefinierte Spalte hinzuzufügen. Außerdem können Sie eine Spalte hinzufügen, indem Sie in der Liste darauf doppelklicken.

2. Achten Sie beim Eingeben der Formel und dem Erstellen Ihrer Spalte auf den Indikator unten im Fenster **Benutzerdefinierte Spalte hinzufügen**. 

   Wenn keine Fehler vorhanden sind, sehen Sie ein grünes Markierungshäkchen und die Meldung *Es wurden keine Syntaxfehler gefunden*.

   ![Erfolgreiche Syntaxprüfung auf der Seite „Benutzerdefinierte Spalte hinzufügen“](media/desktop-add-custom-column/add-custom-column_04.png)

   Wenn ein Syntaxfehler vorliegt, wird ein gelbes Warnsymbol zusammen mit einem Link zu der fehlerhaften Stelle in Ihrer Formel angezeigt.

   ![Fehler auf der Seite „Benutzerdefinierte Spalte hinzufügen“](media/desktop-add-custom-column/add-custom-column_05.png)

3. Klicken Sie auf **OK**. 

   Power BI Desktop fügt dem Modell Ihre benutzerdefinierte Spalte und der Liste **Angewendete Schritte** in den **Abfrageeinstellungen** den Schritt **Spalte hinzugefügt** hinzu.

   ![„Benutzerdefinierte Spalte“ zu Abfrageeinstellungen hinzugefügt](media/desktop-add-custom-column/add-custom-column_06.png)

4. Um Ihre benutzerdefinierte Spalte zu ändern, doppelklicken Sie in der Liste **Angewendete Schritte** auf den Schritt **Spalte hinzugefügt**. 

   Das Fenster **Benutzerdefinierte Spalte hinzufügen** wird mit der benutzerdefinierten Spaltenformel angezeigt, die Sie erstellt haben.

## <a name="use-the-advanced-editor-for-custom-columns"></a>Verwenden des erweiterten Editors für benutzerdefinierte Spalten

Nachdem Sie Ihre Abfrage erstellt haben, können Sie auch den **Erweiterten Editor** verwenden, um die Schritte Ihrer Abfrage zu ändern. Gehen Sie hierzu folgendermaßen vor:

1. Wählen Sie im Fenster **Abfrage-Editor** die Registerkarte **Ansicht** im Menüband aus. 

2. Wählen Sie **Erweiterter Editor** aus.

   Die Seite **Erweiterter Editor** wird angezeigt, die Ihnen vollständige Kontrolle über Ihre Abfrage bietet. 

   ![Seite „Erweiterter Editor“](media/desktop-add-custom-column/add-custom-column_07.png)

   
## <a name="next-steps"></a>Weitere Schritte

- Sie können eine benutzerdefinierte Spalte auch auf andere Weise erstellen, beispielsweise indem Sie eine Spalte anhand von Beispielen erstellen, die Sie im Abfrage-Editor angeben. Weitere Informationen finden Sie unter [Hinzufügen einer Spalte aus einem Beispiel in Power BI Desktop](desktop-add-column-from-example.md).

- Referenzinformationen zu Power Query M finden Sie in der [Power Query M-Funktionsreferenz](/powerquery-m/power-query-m-function-reference).

