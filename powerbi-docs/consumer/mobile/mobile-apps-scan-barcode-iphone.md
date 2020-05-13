---
title: Scannen eines Barcodes aus der mobilen Power BI-App
description: Scannen Sie reale Barcodes, um direkt zu gefilterten BI-Informationen in der mobilen Power BI-App zu gelangen.
author: paulinbar
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-mobile
ms.topic: conceptual
ms.date: 12/02/2019
ms.author: painbar
ms.openlocfilehash: dfe5e6350d0209f836900a921aadc5347b181766
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/13/2020
ms.locfileid: "83276166"
---
# <a name="scan-a-barcode-with-your-device-from-the-power-bi-mobile-app"></a>Scannen eines Barcodes aus der mobilen Power BI-App mit Ihrem Gerät
Scannen Sie reale Barcodes, um direkt zu gefilterten BI-Informationen in der mobilen Power BI-App zu gelangen.


Gilt für:

| ![iPhone](./media/mobile-apps-qr-code/ios-logo-40-px.png) | ![iPads](./media/mobile-apps-qr-code/ios-logo-40-px.png) | ![Android-Smartphone](././media/mobile-apps-qr-code/android-logo-40-px.png) | ![Android-Tablet](././media/mobile-apps-qr-code/android-logo-40-px.png) |
|:--- |:--- |:--- |:--- |
|iPhones |iPads |Android-Telefone |Android-Tablets |

Angenommen, ein Kollege hat [ein Barcodefeld in einem Bericht in Power BI Desktop markiert](../../transform-model/desktop-mobile-barcodes.md) und den Bericht für Sie freigegeben. 

![](media/mobile-apps-scan-barcode-iphone/power-bi-barcode-scanner.png)

Wenn Sie den Barcode eines Produkts mit dem Scanner in der Power BI-App auf Ihrem Gerät scannen, wird Ihnen der Bericht (oder eine Liste der Berichte) mit diesem Barcode angezeigt. Sie können den Bericht öffnen, der mit diesem Barcode herausgefiltert wurde.

## <a name="scan-a-barcode-with-the-power-bi-scanner"></a>Scannen eines Barcodes mit dem Power BI-Scanner
1. Tippen Sie auf der Navigationsleiste auf **Weitere Optionen** (...) und dann auf **Scanner**.

    ![](media/mobile-apps-scan-barcode-iphone/power-bi-scanner.png)

2. Wenn die Kamera nicht aktiviert ist, müssen Sie der Power BI-App die Verwendung der Kamera gestatten. Eine einmalige Genehmigung ist erforderlich. 
4. Richten Sie den Scanner auf einen Barcode auf einem Produkt. Sie sehen eine Liste der Berichte, die diesem Barcode zugeordnet sind.
5. Tippen Sie auf den Namen des Berichts, der automatisch zu diesem Barcode herausgefiltert wurde, um ihn auf Ihrem Gerät zu öffnen.

## <a name="filter-by-other-barcodes-while-in-a-report"></a>Nach anderen Barcodes in einem Bericht filtern
Während ein Bericht angezeigt wird, der von einem Barcode auf Ihrem Gerät herausgefiltert wurde, sollten Sie denselben Bericht mit einem anderen Barcode herausfiltern.

* Wenn das Symbol „Barcode“ über einen Filter verfügt ![](media/mobile-apps-scan-barcode-iphone/power-bi-barcode-filtered-icon-black.png), ist der Filter aktiv, und der Bericht wird bereits von einem Barcode herausgefiltert. 
* Wenn das Symbol über keinen Filter verfügt ![](media/mobile-apps-scan-barcode-iphone/power-bi-barcode-unfiltered-icon.png), ist der Filter nicht aktiv, und der Bericht wird von keinem Barcode herausgefiltert. 

Tippen Sie in beiden Fällen auf das Symbol, um ein kleines Menü mit einem schwebenden Scanbereich zu öffnen.

* Fokussieren Sie den Scanner auf das neue Element, um den Filter des Berichts auf einen anderen Barcodewert zu ändern. 
* Wählen Sie **Clear barcode filter** (Barcodefilter löschen), um zurück zum ungefilterten Bericht zu gelangen.
* Wählen Sie **Filter by recent barcodes** (Filtern nach aktuellen Barcodes) aus, um den Berichtsfilter für eines Produkt-Barcodes zu ändern, den Sie während der aktuellen Sitzung gescannt haben.

## <a name="issues-with-scanning-a-barcode"></a>Probleme beim Scannen eines Barcodes
Nachstehend finden Sie einige Nachrichten, die beim Scannen eines Barcodes für ein Produkt angezeigt werden.

### <a name="couldnt-filter-report"></a>„Der Bericht...konnte nicht gefiltert werden.“
Der Bericht, den Sie filtern möchten, basiert auf einem Datenmodell, in dem dieser Barcodewert nicht enthalten ist. Beispielsweise ist das Produkt „Mineralwasser“ nicht im Bericht enthalten.  

### <a name="allsome-of-the-visuals-in-the-report-dont-contain-any-value"></a>Alle/Einige der Visuals im Bericht enthalten keinen Wert
Der Barcodewert, den Sie gescannt haben, existiert in Ihrem Modell, jedoch enthalten alle/einige Visuals in Ihrem Bericht diesen Wert nicht. So gibt der Filtervorgang einen leeren Zustand zurück. Versuchen Sie, in anderen Berichtsseiten zu suchen, oder bearbeiten Sie Ihre Berichte in Power BI Desktop, um diesen Wert hinzuzufügen. 

### <a name="looks-like-you-dont-have-any-reports-that-can-be-filtered-by-barcodes"></a>„Offenbar verfügen Sie über keine Berichte, die nach Barcodes gefiltert werden können.“
Dies bedeutet, dass Sie keine barcodefähigen Berichte besitzen. Der Barcodescanner kann nur Berichte filtern, die über eine Spalte verfügen, die als **Barcode** markiert ist.  

Stellen Sie sicher, eine Spalte von Ihnen oder dem Besitzer des Berichts als **Barcode** in Power BI Desktop markiert wurde. Erfahren Sie mehr über [das Markieren eines Barcodefelds in Power BI Desktop](../../transform-model/desktop-mobile-barcodes.md)

### <a name="couldnt-filter-report---looks-like-this-barcode-doesnt-exist-in-the-report-data"></a>„Der Bericht konnte nicht gefiltert werden. Dieser Barcode ist offenbar nicht in den Berichtsdaten enthalten.“
Der Bericht, den Sie filtern möchten, basiert auf einem Datenmodell, in dem dieser Barcodewert nicht enthalten ist. Beispielsweise ist das Produkt „Mineralwasser“ nicht im Bericht enthalten. Sie können ein anderes Produkt scannen, einen anderen Bericht auswählen (falls mehr als ein Bericht verfügbar ist) oder den ungefilterten Bericht anzeigen. 

## <a name="next-steps"></a>Nächste Schritte
* [Markieren eines Barcodefelds in Power BI Desktop](../../transform-model/desktop-mobile-barcodes.md)
* [Dashboardkacheln in Power BI](../end-user-tiles.md)
* [Dashboards in Power BI](../end-user-dashboards.md)
