---
title: Anzeigen von Bildern in einer Tabelle oder Matrix in einem Bericht
description: In Power BI Desktop erstellen Sie eine Spalte mit Hyperlinks zu Bildern. Fügen Sie diese Hyperlinks dann entweder in Power BI Desktop oder im Power BI-Dienst einer Berichtstabelle, Matrix, einem Slicer oder einer Karte mit mehreren Zeilen hinzu, um das Bild anzuzeigen.
author: maggiesMSFT
ms.reviewer: ''
ms.custom: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 09/11/2019
ms.author: maggies
LocalizationGroup: Visualizations
ms.openlocfilehash: 4aa10a08757b9d62d4d8c987aedbede47f936a00
ms.sourcegitcommit: bfc2baf862aade6873501566f13c744efdd146f3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/13/2020
ms.locfileid: "83344616"
---
# <a name="display-images-in-a-table-matrix-or-slicer-in-a-report"></a>Anzeigen von Bildern in einem Bericht in einer Tabelle, Matrix oder einem Slicer

Ihren Berichten Bilder hinzuzufügen ist eine gute Möglichkeit, sie zu verbessern. Statische Bilder auf der Seite sind für einige Zwecke geeignet. Doch manchmal sind Ihnen Bilder lieber, die sich auf die Daten in Ihrem Bericht beziehen. In diesem Thema erfahren Sie, wie Sie Bilder in einer Tabelle, Matrix, einem Slicer oder einer mehrzeiligen Karte anzeigen. 

![URL-Bilder in einer Tabelle](media/power-bi-images-tables/power-bi-url-images-table.png)

## <a name="add-images-to-your-report"></a>Hinzufügen von Bildern zum Bericht

1. Erstellen Sie eine Spalte mit den URLs der Bilder. Weitere Informationen zu den Anforderungen finden Sie weiter unten in diesem Artikel unter [Überlegungen](#considerations).

1. Wählen Sie diese Spalte aus. Wählen Sie im Menüband **Modellierung** für **Datenkategorie** die Option **Bild-URL** aus.

    ![Festlegen von „Datenkategorie“ auf „Bild-URL“](media/power-bi-images-tables/power-bi-set-url-image.png)

1. Fügen Sie die Spalte einer Tabelle, Matrix, einem Slicer oder einer mehrzeiligen Karte hinzu.

    ![Slicer mit Bildern](media/power-bi-images-tables/power-bi-url-images-slicer.png)

## <a name="considerations"></a>Überlegungen

- Das Bild muss in einem der folgenden Dateiformate vorliegen: BMP, JPG, JPEG, GIF, PNG oder SVG.
- Anonymer Zugriff auf die URL muss möglich sein, nicht auf einer Site, für die eine Anmeldung erforderlich ist, z. B. SharePoint. Wenn Bilder jedoch auf SharePoint oder OneDrive gehostet werden, können Sie möglicherweise einen Einbindungscode erhalten, der direkt auf sie verweist. 


## <a name="next-steps"></a>Weitere Schritte

[Seitenlayout und Formatierung](/learn/modules/visuals-in-power-bi/12-formatting)

[Grundlegende Konzepte für Designer im Power BI-Dienst](../fundamentals/service-basic-concepts.md)

Weitere Fragen? [Wenden Sie sich an die Power BI-Community](https://community.powerbi.com/)
