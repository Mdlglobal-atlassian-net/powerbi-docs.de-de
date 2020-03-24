---
title: Grundlegendes zur Zuordnung von Datenansichten in Power BI-Visuals
description: In diesem Artikel wird beschrieben, wie Power BI Daten transformiert, bevor diese an Visuals übergeben werden.
author: KesemSharabi
ms.author: kesharab
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: reference
ms.date: 06/18/2019
ms.openlocfilehash: bb323737934ade08ed4998bdcf8d441e8951732c
ms.sourcegitcommit: 6bbc3d0073ca605c50911c162dc9f58926db7b66
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/14/2020
ms.locfileid: "79379855"
---
# <a name="add-the-locale-in-power-bi-for-power-bi-visuals"></a>Hinzufügen des Gebietsschemas in Power BI für benutzerdefinierte Power BI-Visuals

Mit Visuals lässt sich das Power BI-Gebietsschema abrufen, um den Inhalt in der relevanten Sprache zu lokalisieren.

Weitere Informationen zu [Unterstützte Sprachen und Länder/Regionen für Power BI](./../../supported-languages-countries-regions.md)

Ein Beispiel ist das Abrufen des Gebietsschemas im Visual mit dem Beispielbalkendiagramm.

![Lokalisierung im Visual des Beispielbalkendiagramms](media/localization/locale-in-samplebarchart.png)

Jedes dieser Balkendiagramme wurde unter einem anderen Gebietsschema (Englisch, Baskisch und Hindi) erstellt, wie in der QuickInfo angezeigt wird.

> [!NOTE]
> Der Lokalisierungs-Manager im Code des Visuals wird von der API 1.10.0 und höher unterstützt.

## <a name="get-the-locale"></a>Abrufen des Gebietsschemas

Das `locale`-Element wird während der Initialisierung des Visuals an eine Zeichenfolge übergeben. Wird ein Gebietsschema in Power BI geändert, wird das Visual nochmal mit dem neuen Gebietsschema generiert. Den vollständigen Beispielcode finden Sie in SampleBarChart mit dem Gebietsschema.

Der BarChart-Konstruktor verfügt jetzt über ein locale-Element das im Konstruktor mit der locale-Hostinstanz instanziiert wird.

```typescript
private locale: string;
...
this.locale = options.host.locale;
```

Unterstützte Gebietsschemas:

Zeichenfolge des Gebietsschemas | Sprache
--------------|----------------------
ar-SA | العربية (Arabisch)
bg-BG | Български (Bulgarisch)
ca-ES | Katala (Katalanisch)
cs-CZ | Čeština (Tschechisch)
da-DK | Dansk (Dänisch)
de-de | Deutsch (Deutsch)
el-GR | ελληνικά (Griechisch)
en-US | Englisch (Englisch)
es-ES | Español-Dienst (Spanisch)
et-EE | Eesti (Estonian)
eU-ES | Euskal (Baskisch)
fi-FI | Suomi (Finnisch)
fr-FR | Französisch (Frankreich)
gl-ES | Galego (Galicisch)
he-IL | עברית (Hebräisch)
hi-IN | हिन्दी (Hindi)
hr-HR | Hrvatski (Kroatisch)
hu-HU | Magyar (Ungarisch)
id-ID | Bahasa Indonesien (Indonesisch)
it-IT | Italiano (Italienisch)
ja-JP | 日本の (Japanisch)
kk-KZ | Қазақ (Kazakh)
ko-KR | 한국의 (Koreanisch)
lt-LT | Lietuvos (Litauisch)
lv-LV | Latvijas (Lettisch)
ms-MY | Bahasa Melayu (Malaiisch)
nb-NO | Norsk (Norwegisch)
nl-NL | Nederlands (Niederländisch)
pl-PL | Polski (Polnisch)
pt-BR | Português (Portugiesisch)
pt-PT | Português (Portugiesisch)
ro-RO | Românesc (Rumänisch)
ru-RU | русский (Russisch)
sk-SK | Slovenský (Slowakisch)
sl-SI | Slovenski (Slowenisch)
sr-Cyrl-RS | српски (Serbisch)
sr-Latn-RS | srpski (Serbisch)
sv-SE | Svenska (schwedisch)
th-TH | ไทย (Thai)
tr-TR | Türk (Türkisch)
uk-UA | український (Ukrainisch)
vi-VN | Tiếng Việt (Vietnamesisch)
zh-CN | 中国 (vereinfachtes Chinesisch)
zh-TW | 中國 (traditionelles Chinesisch)

> [!NOTE]
> In Power BI Desktop enthält die Gebietsschemaeigenschaft die Sprache der installierten Power BI Desktop-Instanz.

## <a name="localizing-the-property-pane-for-power-bi-visuals"></a>Lokalisierung des Eigenschaftenbereichs für Power BI-Visuals

Felder im Eigenschaftenbereich können lokalisiert werden, um eine stärker integrierte und kohärente Darstellung bereitzustellen. Dadurch verhält sich Ihr benutzerdefiniertes Visual wie jedes andere visuelle Power BI-Element.

Ein nicht lokalisiertes benutzerdefiniertes Visual, das mit dem Befehl `pbiviz new` erstellt wurde, zeigt beispielsweise die folgenden Felder im Eigenschaftenbereich an:

![Lokalisierung im Eigenschaftenbereich](media/localization/property-pane.png)

Sowohl die „Category Data“ (Kategoriedaten) als auch die „Measure Data“ (Messdaten) werden in der Datei „capabilities.json“ als `displayName` definiert.

## <a name="how-to-localize-capabilities"></a>Lokalisieren von Funktionen

Fügen Sie zunächst jedem Anzeigenamen, den Sie in Ihren Funktionen lokalisieren möchten, einen Anzeigenamenschlüssel hinzu. In diesem Beispiel:

```json
{
    "dataRoles": [
        {
            "displayName": "Category Data",
            "displayNameKey": "VisualCategoryDataNameKey1",
            "name": "category",
            "kind": "Grouping"
        },
        {
            "displayName": "Measure Data",
            "displayNameKey": "VisualMeasureDataNameKey2",
            "name": "measure",
            "kind": "Measure"
        }
    ]
}
```

Fügen Sie dann ein Verzeichnis namens „stringResources“ hinzu. Das Verzeichnis enthält alle unterschiedlichen Zeichenfolgen-Ressourcendateien auf der Grundlage der Gebietsschemas, die von Ihrem Visual unterstützt werden sollen. In diesem Verzeichnis müssen Sie für jedes Gebietsschema, das Sie unterstützen möchten, eine JSON-Datei hinzufügen. Diese Dateien enthalten die Gebietsschema-Informationen und die lokalisierten Zeichenfolgenwerte für jeden displayNameKey, den Sie ersetzen möchten.

Im Beispiel soll Arabisch und Hebräisch unterstützt werden. Sie müssen zwei JSON-Dateien auf folgende Weise hinzufügen:

![Lokalisierungszeichenfolgen im Ordner für Zeichenfolgenressourcen](media/localization/stringresources-files.png)

Jede JSON-Datei definiert ein einzelnes Gebietsschema (diese Datei muss eines der Gebietsschemas aus der obigen Liste sein) mit den Zeichenfolgenwerten für die gewünschten Anzeigenamensschlüssel. In diesem Beispiel sieht die Ressourcendatei für die hebräische Zeichenfolge wie folgt aus:

```json
{
    "locale": "he-IL",
    "values": {
        "VisualCategoryDataNameKey1": "קטגוריה",
        "VisualMeasureDataNameKey2": "יחידות מידה"
    }
}
```

Alle erforderlichen Schritte zur Verwendung des Lokalisierungs-Managers sind unten beschrieben.

> [!NOTE]
> Derzeit wird die Lokalisierung für das Debuggen des Entwicklungsvisuals nicht unterstützt.

## <a name="setup-environment"></a>Setupumgebung

### <a name="desktop"></a>Desktop

Laden Sie für die Verwendung auf dem Desktop die lokalisierte Version von Power BI Desktop von https://powerbi.microsoft.com herunter.

### <a name="web-service"></a>Webdienst

Wenn Sie den Webclient (Browser) im Dienst verwenden, ändern Sie die Sprache in den Einstellungen:

![Lokalisierung im Webdienst](media/localization/webservice-settings.png)

## <a name="resource-file"></a>Ressourcendatei

Fügen Sie eine Datei „resources.resjson“ zu einem Ordner mit dem Namen des Gebietsschemas hinzu, das Sie im Ordner „stringResources“ verwenden möchten. Dies ist in diesem Beispiel „en-US“ und „ru-ru“.

![Die neue RESJSON-Datei](media/localization/new-resjson.png)

Fügen Sie anschließend alle zu verwendenden Lokalisierungszeichenfolgen in die Datei „resources.resjson“ ein, die Sie im vorherigen Schritt hinzugefügt haben.

```json
{
    ...
    "Role_Legend": "Обозначения",
    "Role_task": "Задача",
    "Role_StartDate": "Дата начала",
    "Role_Duration": "Длительность"
    ...
}
```

Dieses Beispiel zeigt die en-US-Version der Datei „resources.resjson“:

```json
{
    ...
    "Role_Legend": "Legend",
    "Role_task": "Task",
    "Role_StartDate": "Start date",
    "Role_Duration": "Duration"
    ...
}
```

Neue localizationManager-Instanz Erstellen Sie wie folgt eine Instanz von localizationManager im Code Ihres Visuals:

```typescript
private localizationManager: ILocalizationManager;

constructor(options: VisualConstructorOptions) {
    this.localizationManager = options.host.createLocalizationManager();
}
```

## <a name="localizationmanager-usage-sample"></a>Anwendungsbeispiel für localizationManager

Nun können Sie die getDisplayName-Funktion des Lokalisierungs-Managers mit dem Zeichenfolgen-Schlüsselargument aufrufen, das Sie in „resources.resjson“ definiert haben, um die gewünschte Zeichenfolge irgendwo in Ihrem Code zu erhalten:

```typescript
let legend: string = this.localization.getDisplayName("Role_Legend");
```

Für en-US wird „Legend“ und für ru-RU wird „Обозначения“ zurückgegeben.

## <a name="next-steps"></a>Nächste Schritte

* [Lesen Sie, wie Sie mit Formatierungshilfsprogrammen lokalisierte Formate bereitstellen](utils-formatting.md)
