---
title: Visuals für Organisationen in Power BI
description: Verwenden, Verwalten und Erstellen von Visuals für Organisationen in Power BI
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 12/11/2018
LocalizationGroup: Visualizations
ms.openlocfilehash: 8c28c5ee89ffee37c09db8dc6ffcd6fb90274786
ms.sourcegitcommit: 08b73af260ded51daaa6749338cb85db2eab587f
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/15/2019
ms.locfileid: "74102086"
---
# <a name="organizational-visuals-in-power-bi"></a>Visuals für Organisationen in Power BI

Sie können Power BI-Visuals in Power BI verwenden, um einen einzigartigen Typ von Visual zu erstellen, der auf Ihre Zwecke zugeschnitten ist. Power BI-Visuals werden von Entwicklern erstellt. Der Grund dafür ist oft, dass die Visuals, die in Power BI enthalten sind, deren Anforderungen nicht ganz erfüllen.

In einigen Organisationen sind Power BI-Visuals sogar noch wichtiger, da sie notwendig sein können, um bestimmte Daten oder Einsichten zu übermitteln, die für die Organisation einzigartig sind. Sie können ebenfalls spezielle Anforderungen für Daten enthalten oder private Geschäftsmethoden hervorheben. Solche Organisationen müssen Power BI-Visuals entwickeln, diese innerhalb der Organisation freigeben und sicherstellen, dass sie ordnungsgemäß verwaltet werden. Durch benutzerdefinierte Power BI-Visuals in Power BI können Organisationen dies erreichen.

Die folgende Abbildung stellt den Prozess dar, den Power BI-Visuals für Organisationen in Power BI durchlaufen. Dieser beginnt beim Administrator, wird in der Entwicklung und Verwaltung fortgesetzt und endet beim Datenanalysten.

![Bild benutzerdefiniertes Visual](media/power-bi-custom-visuals-organizational/custom-visual-org-01.jpg)

Visuals für Organisationen werden vom Power BI-Administrator über das Verwaltungsportal bereitgestellt und verwaltet. Nach der Bereitstellung im Repository der Organisation können die Benutzer in der Organisation diese Power BI-Visuals für Organisationen einfach ermitteln und direkt über Power BI Desktop in ihre Berichte importieren.

Weitere Informationen zur Verwendung von Power BI-Visuals für Organisationen in den von Ihnen erstellten Berichten finden Sie im folgenden Artikel: [Weitere Informationen zum Importieren von Visuals für Organisationen in Berichten](power-bi-custom-visuals.md).

## <a name="administer-organizational-power-bi-visuals"></a>Verwalten von Power BI-Visuals für Organisationen

Weitere Informationen über die Verwaltung und Bereitstellung von Power BI-Visuals für Organisationen finden Sie im folgenden Artikel: [Weitere Informationen zu Bereitstellung und Verwaltung von Power BI-Visuals für Organisationen](https://go.microsoft.com/fwlink/?linkid=866790).

> [!WARNING]
> Ein benutzerdefiniertes Visual kann Code mit Sicherheits- oder Datenschutzrisiken enthalten. Stellen Sie sicher, dass Sie dem Autor und der Quelle eines benutzerdefinierten Visuals vertrauen können, bevor Sie dieses für das Repository der Organisation bereitstellen.

## <a name="considerations-and-limitations"></a>Überlegungen und Einschränkungen

Es gibt einige Überlegungen und Einschränkungen, die Sie berücksichtigen müssen.

Administrator:

* Veraltete Power BI-Visuals (z. B. Power BI-Visuals, die nicht mit den neuen API-Versionen erstellt wurden) werden nicht unterstützt.

* Wenn ein benutzerdefiniertes Visual aus dem Repository gelöscht wird, wird das Rendern aller vorhandenen Berichte beendet, die das gelöschte Visual verwenden. Das Löschen des Visuals aus dem Repository kann nicht rückgängig gemacht werden. Um ein benutzerdefiniertes Visual vorübergehend zu deaktivieren, verwenden Sie die Funktion „Deaktivieren“.

Benutzer:

* Power BI-Visuals für Organisationen sind private Visuals, die aus dem Repository der Organisation importiert wurden. Wie jedes andere private Visual können Sie [nicht zu PowerPoint exportiert](https://docs.microsoft.com/power-bi/consumer/end-user-powerpoint) oder in empfangenen E-Mails angezeigt werden, wenn ein Benutzer [Berichtsseiten abonniert](https://docs.microsoft.com/power-bi/consumer/end-user-subscribe). Nur direkt aus dem Marketplace importierte [zertifizierte Power BI-Visuals](https://docs.microsoft.com/power-bi/power-bi-custom-visuals-certified) unterstützen diese Features.

* Visio-Visuals, PowerApps-Visuals, Map Box-Visuals und GlobeMap-Visuals aus dem AppSource-Marketplace werden nicht gerendert, wenn diese über das Repository der Organisation bereitgestellt wurden.

## <a name="troubleshoot"></a>Problembehandlung

Informationen zur Problembehandlung finden Sie auf der Seite [Problembehandlung für Power BI-Visuals in Power BI](power-bi-custom-visuals-troubleshoot.md).

## <a name="faq"></a>HÄUFIG GESTELLTE FRAGEN

Weitere Informationen und Antworten auf Fragen finden Sie in den [häufig gestellten Fragen zu Power BI-Visuals in Power BI](power-bi-custom-visuals-faq.md#organizational-visuals).

Weitere Fragen? [Wenden Sie sich an die Power BI-Community](https://community.powerbi.com/).