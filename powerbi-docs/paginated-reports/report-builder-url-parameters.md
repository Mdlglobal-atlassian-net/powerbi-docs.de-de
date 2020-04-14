---
title: 'URL-Parameter in paginierten Berichten: Power BI-Berichts-Generator'
description: In diesem Thema werden allgemeine Verwendungsmöglichkeiten für Berichtsparameter im Power BI Report Builder, die Eigenschaften, die Sie festlegen können, und vieles mehr beschrieben.
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
author: maggiesMSFT
ms.author: maggies
ms.reviewer: cfinlan
ms.custom: ''
ms.date: 04/02/2020
ms.openlocfilehash: df59d09a1e8557842904b46eded0a83c86448224
ms.sourcegitcommit: e0833ec22b263f919025acae88551570b4def0cd
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/03/2020
ms.locfileid: "80647718"
---
# <a name="url-parameters-in-paginated-reports-in-power-bi"></a>URL-Parameter in paginierten Berichten in Power BI

Sie können Befehle an paginierte Berichte in Power BI senden, indem Sie einen Parameter zu einer URL hinzufügen. Beispielsweise haben Sie den Bericht möglicherweise mithilfe bestimmter Berichtsparameterwerte angezeigt. Sie kapseln diese Informationen in der URL, indem Sie vordefinierte URL-Zugriffsparameter verwenden. Ferner passen Sie an, wie Power BI den Bericht verarbeitet, indem Sie Parameter zum Rendern von Formaten oder für die Benutzeroberfläche der Berichtssymbolleiste einbetten. Sie fügen diese URL anschließend in eine E-Mail oder Webseite ein, damit sich Andere Ihren Bericht auf dieselbe Weise im Browser anzeigen lassen können. 

Folgende Aktionen können Sie mithilfe von URL-Zugriffsparametern durchführen: 

- Senden von Berichtsparametern an einen Bericht 
- Initiieren des Berichtsinhaltsexports in einem unterstützten Dateiformat 
- Ausblenden oder Anzeigen des Parameterbereichs 
- Festlegen der DeviceInfo-Einstellung 

Eine umfassende Liste der Befehle und Einstellungen, die über den URL-Zugriff verfügbar sind, finden Sie unter  [Referenz zu URL-Zugriffsparametern](#url-access-parameter-reference) weiter unten in diesem Artikel. 

## <a name="url-access-concepts"></a>URL-Zugriffskonzepte 

URL-Anforderungen an Power BI enthalten Parameter, die vom Dienst verarbeitet werden. Die Art und Weise, in der der Dienst URL-Anforderungen verarbeitet, hängt von den Parametern, Parameterpräfixen und Elementtypen ab, die in der URL enthalten sind. Die URL-Funktionalität für paginierte Berichte ist mit den meisten Browsern und Anwendungen kompatibel, die die Standard-URL-Adressierung unterstützen. 

## <a name="url-access-syntax"></a>URL-Zugriffssyntax 

URL-Anforderungen können mehrere Parameter enthalten, die in beliebiger Reihenfolge aufgelistet sind. Parameter sind durch ein kaufmännisches Und-Zeichen (&) getrennt. Name-Wert-Paare sind durch ein Gleichheitszeichen (=) getrennt. Beispiel:

```
powerbiserviceurl?rp:parametervalueh&rdl:parameter=value  
```

## <a name="syntax-description"></a>Syntaxbeschreibung 

### <a name="powerbiserviceurl"></a>powerbiserviceurl 

Die Webdienst-URL Ihres Power BI-Mandanten. Beispiel: 

**&** Wird verwendet, um Name-Wert-Paare von URL-Zugriffsparametern zu trennen

**Präfix** Ein Präfix für den URL-Parameter (z. B. „rp:“ oder „rdl:“), das eine Aktion im Power BI-Dienst angibt 

> [!NOTE]
> Berichtsparameter erfordern ein Parameterpräfix, und die Groß-/Kleinschreibung wird beachtet 

**Parameter** Der Parametername 

### <a name="value"></a>Wert 

Der URL-Text, der dem Wert des verwendeten Parameters entspricht. 

Beispiele für das Übergeben von Berichtsparametern in der URL finden Sie unter  [Übergeben eines Berichtsparameters in einer URL](report-builder-url-pass-parameters.md).

## <a name="url-access-parameter-reference"></a>Referenz zu URL-Zugriffsparametern

Sie können die folgenden Parameter als Teil einer URL verwenden, um die Benutzeroberfläche der paginierten Berichte in Power BI zu konfigurieren. Die häufigsten Parameter sind in diesem Abschnitt aufgeführt. Bei Parametern wird die Groß-/Kleinschreibung nicht beachtet, und sie verfügen über das Parameterpräfix `rdl:` , falls sie mit dem Ausgabeformat verknüpft sind.  

### <a name="report-commands-rdl"></a>Berichtsbefehle (`rdl:`) 

**Exportformat** gibt das Format an, in dem ein Bericht gerendert und exportiert werden soll. Folgende Werte sind verfügbar:
 
- PPTX (PowerPoint)
- MHTML 
- BILD 
- EXCELOPENXML (EXCEL) 
- WORDOPENXML (WORD) 
- CSV 
- PDF 
- XML 

**Zustand des Parameterbereichs** gibt an, ob der Parameterbereich beim Laden des Berichts geschlossen oder geöffnet oder vollständig ausgeblendet ist.

-   rdl:parameterPanelState

    - 'collapsed': Der Bericht wird mit geschlossenem Parameterbereich geladen. Die Schaltfläche „Parameter“ ist aktiviert, sodass Benutzer darauf klicken können, um den Bereich aufzuklappen.
    - 'hidden': Der Bericht wird mit geschlossenem Parameterbereich geladen, und die Schaltfläche „Parameter“ ist deaktiviert.
    - 'expanded' (Standardwert): Der Bericht wird mit geöffnetem Parameterbereich geladen, und die Schaltfläche „Parameter“ ist aktiviert.

**Geräteinformationen** Sie können zusätzliche Ausgabeparameter für die folgenden Exportformate angeben. 

PDF:

- rdl:AccessiblePDF=true/false
- rdl:Columns=integer
- rdl:ColumnSpacing=decimal(in)
- rdl:DpiX=integer
- rdl:DpiY=integer
- rdl:EndPage=integer
- rdl:HumanReadablePDF=true/false
- rdl:MarginBottom=decimal(in)
- rdl:MarginLeft=decimal(in)
- rdl:MarginRight=decimal(in)
- rdl:MarginTop=decimal(in)
- rdl:MarginRight=decimal(in)
- rdl:PageWidth=decimal(in)
    - rdl:StartPage=integer
    
CSV:

- rdl:Encoding=string
- rdl:ExcelMode=true/false
- rdl:FieldDelimiter=string
- rdl:FileExtension=string
- rdl:NoHeader=true/false
- rdl:Qualifier=string
- rdl:RecordDelimiter=string
- rdl:SuppressLineBreaks=true/false
    - rdl:UseFormattedValues=true/false
    
WORDOPENXML (WORD):

- rdl:AutoFit=string -> True/False/Never/Default
- rdl:ExpandToggles=true/false
- rdl:FixedPageWidth=true/false
- rdl:OmitHyperlinks=true/false
- rdl:OmitDrillthroughs=true/false

EXCELOPENXML (EXCEL):

- rdl:OmitDocumentMap=true/false
- rdl:OmitFormulas=true/false
    - rdl:SimplePageHeaders=true/false
    
PPTX (PowerPoint):
 
- rdl:Columns=integer
- rdl:ColumnSpacing=decimal(in)
- rdl:DpiX=integer
- rdl:DpiY=integer
- rdl:EndPage=integer
- rdl:MarginBottom=decimal(in)
- rdl:MarginLeft=decimal(in)
- rdl:MarginRight=decimal(in)
- rdl:MarginTop=decimal(in)
- rdl:MarginRight=decimal(in)
- rdl:PageWidth=decimal(in)
- rdl:StartPage=integer
    - rdl:UseReportPageSize=true/false

XML:

- rdl:XSLT=string
- rdl:MIMEType=string
- rdl:UseFormattedValues=true/false
- rdl:Indented=true/false
- rdl:OmitNamespace=true/false
- rdl:OmitSchema=true/false
- rdl:Encoding=string
- rdl:FileExtension=string
- rdl:Schema=true/false

## <a name="next-steps"></a>Nächste Schritte

- [Übergeben eines Berichtsparameters in einer URL für einen paginierten Bericht in Power BI](report-builder-url-pass-parameters.md)
- [Was sind paginierte Berichte in Power BI Premium? (Vorschau)](paginated-reports-report-builder-power-bi.md)
