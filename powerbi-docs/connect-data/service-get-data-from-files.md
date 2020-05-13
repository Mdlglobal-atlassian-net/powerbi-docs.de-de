---
title: Abrufen von Daten aus Dateien für Power BI
description: Erfahren Sie, wie Sie Daten aus Excel-, Power BI Desktop- sowie CSV-Dateien in Power BI abrufen
author: davidiseminger
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 05/08/2019
ms.author: davidi
LocalizationGroup: Data from files
ms.openlocfilehash: bc68fda914450345f5854375e3ef0964438eef30
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/13/2020
ms.locfileid: "83285737"
---
# <a name="get-data-from-files-for-power-bi"></a>Abrufen von Daten aus Dateien für Power BI
![](media/service-get-data-from-files/file_icons.png)

In Power BI können Sie Daten und Berichte aus drei Dateitypen verknüpfen oder importieren.

* Microsoft Excel (XLSX- oder XLSM-Dateien)
* Power BI Desktop (PBIX-Dateien)
* Kommagetrennte Dateien (CSV-Dateien)

## <a name="what-does-get-data-from-a-file-really-mean"></a>Was bedeutet es wirklich, Daten aus einer Datei abzurufen?
In Power BI stammen die Daten, die Sie auswerten, aus einem Dataset. Für ein Dataset benötigen Sie jedoch zuerst Daten. In diesem Artikel legen wir den Fokus auf das Abrufen von Daten aus Dateien.

Um uns der Bedeutung von Datasets bewusst zu werden und zu erfahren, wie wir Daten daraus abrufen, nehmen wir das Beispiel eines Autos zur Hand. Setzen Sie sich in Ihr Auto, und betrachten Sie das Armaturenbrett. Das hat viel mit dem Blick auf ein Dashboard in Power BI gemein. Das Dashboard zeigt Ihnen alle Vorgänge in Ihrem Auto an: wie schnell der Motor beschleunigt, die Temperatur, welcher Gang eingelegt ist, Ihre Geschwindigkeit usw.

Ein Dataset in Power BI ist wie der Motor Ihres Autos. Das Dataset stellt die Daten, Metriken und Informationen bereit, die in Ihrem Power BI-Dashboard angezeigt werden. Natürlich benötigt Ihr Motor oder Dataset Treibstoff, und in Power BI stellen Daten diesen Treibstoff dar. Ihr Auto hat einen Tank, aus dem Treibstoff in den Motor gepumpt wird. Ebenso benötigen Sie in Power BI einen Treibstofftank mit Daten, die Sie in Ihr Dataset einspeisen können. In unserem Fall ist der Treibstofftank eine Power BI Desktop-Datei, eine Excel-Arbeitsmappendatei oder eine CSV-Datei.

Wir können sogar noch einen Schritt weitergehen. Der Treibstofftank eines Auto muss mit Benzin gefüllt werden. Das Benzin für unsere Power BI Desktop-, Excel-, oder CSV-Datei sind Daten aus einer anderen Datenquelle. Wir rufen die Daten aus einer anderen Datenquelle ab und speichern diese in einer Excel-, Power BI Desktop- oder CSV-Datei. Wenn es sich um eine Excel-Arbeitsmappen- oder CSV-Datei handelt, können wir die Datenzeilen auch manuell eingeben. Alternativ können wir eine Verknüpfung mit einer externen Datenquelle erstellen, um Daten abzufragen und in unsere Datei zu laden. Sobald wir eine Datei mit Daten erstellt haben, können wir diese in Power BI als Dataset verwenden.

> [!NOTE]
> Daten in Excel-Arbeitsmappen müssen in einer Tabelle vorliegen oder im Datenmodell, um von Power BI importiert werden zu können.
> 
> 

## <a name="where-your-file-is-saved-makes-a-difference"></a>Der Speicherort Ihrer Datei ist entscheidend
**Lokal** – Wenn Sie Ihre Datei auf einem lokalen Laufwerk Ihres Computers oder an einem anderen Speicherort in Ihrer Organisation speichern, können Sie Ihre Datei über Power BI in Power BI *importieren*. In Wahrheit verbleibt Ihre Datei aber auf Ihrem lokalen Laufwerk. Die Datei wird also eigentlich gar nicht in Power BI importiert. Tatsächlich wird ein neues Dataset auf Ihrer Power BI-Website erstellt. Daraufhin werden Daten und ggf. das Datenmodell in das Dataset geladen. Wenn Ihre Datei Berichte enthält, werden diese auf Ihrer Power BI-Website unter „Berichte“ angezeigt.

**OneDrive – Geschäftlich** – Wenn Sie OneDrive for Business verwenden, können Sie sich mit demselben Konto auch bei Power BI anmelden. So synchronisieren Sie Ihre Arbeit in Excel, Power BI Desktop oder einer CSV-Datei mit den Datasets, Berichten und Dashboards in Power BI auf mit Abstand effektivste Art und Weise. Da sich sowohl Power BI als auch OneDrive in der Cloud befinden, verbindet sich Power BI etwa einmal in der Stunde mit Ihrer Datei in OneDrive. Wenn Änderungen gefunden werden, werden Ihre Dataset, Berichte und Dashboards in Power BI automatisch aktualisiert.

**OneDrive – Persönlich** – Wenn Sie Ihre Dateien in Ihrem eigenen OneDrive-Konto speichern, erhalten Sie dennoch viele der Vorteile, die Ihnen OneDrive for Business bieten würde. Der Hauptunterschied besteht darin, dass Sie sich beim ersten Verknüpfen mit Ihrer Datei, mit Ihrem Microsoft-Konto bei OneDrive anmelden müssen (mit „Daten abrufen“ > „Dateien“ > „OneDrive – Persönlich“). Normalerweise sind Ihr Microsoft- und Ihr Power BI-Konto nicht identisch. Stellen Sie bei der OneDrive-Anmeldung mithilfe Ihres Microsoft Kontos sicher, dass Sie die Option „Angemeldet bleiben“ aktiviert haben. Auf diese Weise ist Power BI in der Lage, sich etwa einmal die Stunde mit Ihrer Datei zu verbinden und sicherzustellen, dass Ihr Dataset in Power BI synchronisiert ist.

**SharePoint-Teamwebsites** – Ihre Power BI Desktop-Dateien in SharePoint-Teamwebsites zu speichern funktioniert ähnlich wie das Speichern in OneDrive for Business. Der größte Unterschied besteht im Herstellen der Verknüpfung zur Datei aus Power BI. Sie können eine URL angeben oder eine Verknüpfung mit einem Stammordner erstellen.

## <a name="ready-to-get-started"></a>Sind Sie bereit für den Einstieg?
Weitere Informationen zum Abrufen Ihrer Datei in Power BI finden Sie in den folgenden Artikeln.

* [Abrufen von Daten aus Excel-Arbeitsmappendateien](service-excel-workbook-files.md)
* [Abrufen von Daten aus Power BI Desktop-Dateien](service-desktop-files.md)
* [Abrufen von Daten aus einer kommagetrennten Datei (CSV)](service-comma-separated-value-files.md)

