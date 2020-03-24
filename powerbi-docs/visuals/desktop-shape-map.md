---
title: Verwenden von Flächenkartogrammen in Power BI Desktop (Vorschauversion)
description: Erstellen von relativen Vergleichen von Regionen mithilfe von Flächenkartogrammen in Power BI Desktop
author: mihart
ms.reviewer: justyna, sujata
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 03/18/2020
ms.author: mihart
LocalizationGroup: Transform and shape data
ms.openlocfilehash: 67c2acad74827c515c92ed0d16dd642170b8dc61
ms.sourcegitcommit: 646d2de454a2897dc52cbc02b7743aaa021bac04
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/18/2020
ms.locfileid: "79525658"
---
# <a name="create-shape-map-visualizations-in-power-bi-desktop-preview"></a>Erstellen von Visualisierungen für Flächenkartogramme in Power BI Desktop (Vorschau)

[!INCLUDE [power-bi-visuals-desktop-banner](../includes/power-bi-visuals-desktop-banner.md)]

Erstellen Sie ein Visual für die **Formenzuordnung**, um Regionen auf einer Karte voneinander abzutrennen. Im Gegensatz zum Visual **Karte** kann das Visual **Formenzuordnung** keine genauen geografischen Standorte von Datenpunkten auf einer Karte anzeigen. Stattdessen soll es vor allem Regionen auf einer Karte in Beziehung zueinander setzen, indem diese unterschiedliche Farben erhalten.

Visuals für die **Formenzuordnung** basieren auf TopoJSON-Karten. Diese Karten können von Ihnen erstellte benutzerdefinierte Karten verwenden. Benutzerdefinierte Karten sind beispielswiese die Folgenden: geografische Pläne, Sitz- oder Raumpläne. In diesem Vorschaurelease von **Flächenkartogramm** ist es nicht möglich, benutzerdefinierte Karten zu verwenden.

## <a name="creating-shape-maps"></a>Erstellen von Flächenkartogrammen
Sie können das Steuerelement **Flächenkartogramm** mit den Karten testen, die mit dieser Vorschauversion geliefert werden. Alternativ können Sie eine eigene benutzerdefinierte Karte verwenden, sofern sie die im folgenden Abschnitt **Verwenden benutzerdefinierter Karten** genannten Anforderungen erfüllt.

Die Visualisierung **Flächenkartogramm** befindet sich in der Vorschauversion und muss in Power BI Desktop aktiviert werden. Wählen Sie **Datei > Optionen und Einstellungen > Optionen > Vorschaufeatures** aus, und aktivieren Sie anschließend das Kontrollkästchen bei **Visuelles Formzuordnungselement**, um **Formzuordnung** zu aktivieren. Sie müssen Power BI Desktop neu starten, nachdem Sie die Auswahl vorgenommen haben.

![Aktivieren der Previewfunktion für das Flächenkartogramm](media/desktop-shape-map/power-bi-preview-features.png)

Sobald das **Flächenkartogramm** aktiviert ist, wählen Sie das Steuerelement **Flächenkartogramm** im Bereich **Visualisierungen** aus.

![Auswählen der Vorlage für das Flächenkartogramm](media/desktop-shape-map/power-bi-shape-map-template2.png)

Power BI Desktop erstellt einen leeren Entwurfszeichenbereich für die Visualisierung **Flächenkartogramm**.

![Leeres Flächenkartogramm, das im Zeichenbereich angezeigt wird](media/desktop-shape-map/shape-map-3.png)

Führen Sie die folgenden Schritte aus, um ein **Flächenkartogramm** zu erstellen:

1. Ziehen Sie im Bereich **Felder** ein Datenfeld mit den Regionsnamen (oder Abkürzungen) auf den Bucket **Speicherort** und ein Datenmeasurefeld in den Bucket **Farbsättigung** (eine Zuordnung wird noch nicht angezeigt).

   > [!NOTE]
   > Informationen dazu, wie Sie schnell Kartendaten zum Testen eines **Flächenkartogramms** erhalten, finden Sie weiter unten im Abschnitt **Abrufen von Kartendaten**.
   > 
   > 

   ![Erstellen des Flächenkartogramms](media/desktop-shape-map/shape-map-3a.png)
2. Erweitern Sie im Bereich **Formateinstellungen** **Form**, und wählen Sie aus der Dropdownliste **Standardkarten** aus, um Ihre Daten anzuzeigen. Zu diesem Zeitpunkt erfolgt das Rendering wie in folgender Abbildung dargestellt.

   ![Öffnen des Bereichs „Formatierung“ und Auswählen der Form](media/desktop-shape-map/shape-map-3b-new.png)

   > [!NOTE]
   > Im Abschnitt **Regionsschlüssel** am Ende dieses Artikels finden Sie eine Sammlung von Tabellen, die Regionsschlüssel für Karten enthalten, die Sie zum Testen des Visuals **Flächenkartogramm** verwenden können.
   > 
   > 
3. Mithilfe von Formatierungsoptionen wie **Standardfarbe**, **Zoom** etc. können Sie die Karte ändern. Außerdem können Sie dem Bucket **Legende** auch eine Spalte „Datenkategorie“ hinzufügen und die Kartenregionen basierend auf Kategorien klassifizieren.

## <a name="use-custom-maps"></a>Verwenden benutzerdefinierter Karten
Sie können benutzerdefinierte Karten für das **Flächenkartogramm** verwenden, sofern sie das **TopoJSON**-Format aufweisen. Wenn die Karte in einem anderen Format vorliegt, können Sie mit Onlinetools, z.B. [**Map Shaper**](https://mapshaper.org/), die *Shape-Dateien* oder *GeoJSON*-Karten in das **TopoJSON**-Format konvertieren.

Um die **TopoJSON**-Kartendatei zu verwenden, fügen Sie dem Bericht ein visuelles ShapeMap-Element hinzu, und fügen Sie den Buckets *Standort* und *Farbsättigung* Daten hinzu. Erweitern Sie dann im Bereich **Visualisierungen**, in dem der Abschnitt **Format** (in der folgenden Abbildung als (1) dargestellt) ausgewählt ist, den Abschnitt **Form**, und wählen Sie **+ Karte hinzufügen** aus.

![Öffnen des Bereichs „Formatierung“ und Auswählen der Option „Karte hinzufügen“](media/desktop-shape-map/shape-map-6-new.png)

## <a name="sample-custom-map"></a>Benutzerdefinierte Beispielkarte
Die *Büros der United States Attorneys* (Anwälte der Vereinigten Staaten) veröffentlichen einen jährlichen Finanzbericht über ihre Daten von Gerichtsverfahren und der Anzahl von Fällen.  Alle Berichte finden Sie unter folgendem Link:

https://www.justice.gov/usao/resources/annual-statistical-reports

Da Staaten in mehrere Bezirke unterteilt werden können, müssen wir ein benutzerdefiniertes Flächenkartogramm verwenden.  Durch Importieren der **TopoJSON**-Karte der US-Gerichtsbezirke in **Power BI Desktop** können wir die jährlichen Finanzdaten der Bezirksanwälte anzeigen.  Das nachfolgende Bild stellt ein Beispiel dieser Karte dar.

![Benutzerdefiniertes Flächenkartogramm](media/desktop-shape-map/shape-map-7a.png)

Sie können mit den einzelnen Karten der US-Staaten auch interessante Vorgänge durchführen und weitere Details auf Grundlage der auf der Karte enthaltenen Bezirke anzeigen. 

![Flächenkartogramm von Texas](media/desktop-shape-map/shape-map-7b.png)

Wenn Sie gerne mit diesem Dataset und der Visualisierung experimentieren möchten, können Sie die ursprüngliche PBIX-Datei herunterladen, die zum Generieren dieses Berichts verwendet wurde. Sie finden sie unter folgendem Link:

* [PBIX-Demodatei des benutzerdefinierten Flächenkartogramms](https://download.microsoft.com/download/1/2/8/128943FB-9231-42BD-8A5D-5E2362C9D589/DistrictAttorneyFiscalReport.pbix)

## <a name="getting-map-data"></a>Abrufen von Kartendaten
Um schnell Daten in ein Modell abzurufen, um **Flächenkartogramm** zu testen, können Sie eine der Tabellen am Ende dieses Artikels kopieren und anschließend auf dem Menüband **Start** **Daten eingeben** auswählen.

![Auswählen von „Daten eingeben“ in Power BI Desktop](media/desktop-shape-map/shape-map-4-new.png)

Wenn Ihre Daten mehrere Spalten haben, müssen Sie zum Einfügen der Daten einen Editor wie Excel verwenden und dann jede Datenspalte einzeln kopieren. Sie können die Daten anschließend in Power BI Desktop einfügen. Die oberste Zeile wird automatisch als Überschrift identifiziert.

![Bereich „Tabelle erstellen“](media/desktop-shape-map/shape-map-5.png)

Sie können eine neue Spalte einfach hinzufügen, indem Sie einen neuen Spaltennamen (in die leere Spalte auf der rechten Seite) eingeben und anschließend wie in Excel jeder Zelle Werte hinzufügen. Wenn Sie damit fertig sind, wählen Sie **Laden** aus, und die Tabelle wird dem Datenmodell von Power BI Desktop hinzugefügt.

> [!NOTE]
> Verwenden Sie bei der Arbeit mit Ländern oder Regionen das dreistellige Buchstabenkürzel, um sicherzustellen, dass die Geocodierung in Kartenvisualisierungen ordnungsgemäß funktioniert. Verwenden Sie *nicht* die zweistelligen Kürzel, da einige Länder oder Regionen sonst unter Umständen nicht ordnungsgemäß erkannt werden.
> 
> Falls Sie nur über zweistellige Kürzel verfügen, informieren Sie sich in [diesem externen Blogbeitrag](https://blog.ailon.org/how-to-display-2-letter-country-data-on-a-power-bi-map-85fc738497d6#.yudauacxp) darüber, wie Sie Ihren zweistelligen Länder-/Regionskürzeln die dreistelligen Länder-/Regionskürzel zuordnen.
> 
> 

## <a name="preview-behavior-and-requirements"></a>Vorschauverhalten und -anforderungen
Für dieses Vorschaurelease von **Flächenkartogramm** gibt es einige Bedingungen und Anforderungen:

* Die Visualisierung **Flächenkartogramm** befindet sich in der Vorschauversion und muss in Power BI Desktop aktiviert werden. Wählen Sie **Datei > Optionen und Einstellungen > Optionen > Vorschaufeatures** aus, und aktivieren Sie anschließend das Kontrollkästchen bei **Visuelles Formzuordnungselement**, um **Formzuordnung** zu aktivieren.
* Derzeit muss auch der Bucket **Farbsättigung** festgelegt sein, damit die Klassifizierung **Legende** ordnungsgemäß funktioniert.
* Die endgültige Version **Formenzuordnung** wird über eine Benutzeroberfläche verfügen, die die Zuordnungsschlüssel der aktuell ausgewählten Zuordnung anzeigt (es ist kein Datum festgelegt, für die endgültige Version, und **Formenzuordnung** ist weiterhin als Vorschau verfügbar). In dieser Vorschauversion können Sie auf die Zuordnungsregionsschlüssel in den Tabellen verweisen, die in folgendem Abschnitt **Regionsschlüssel** dieses Artikels zu finden sind.
* Das visuelle Element **Flächenkartogramm** kann maximal 1.500 Datenpunkte zeichnen.

## <a name="region-keys"></a>Regionsschlüssel

Verwenden Sie in dieser Vorschauversion die folgenden **Regionsschlüssel**, um **Flächenkartogramm** zu testen.

### <a name="australia-states"></a>Australien: Staaten

| ID | abbr | iso | name | postal |
| --- | --- | --- | --- | --- |
| au-wa |WA |AU-WA |Western Australia |WA |
| au-vic |Vic |AU-VIC |Victoria |VIC |
| au-tas |Tas |AU-TAS |Tasmania |TAS |
| au-sa |SA |AU-SA |South Australia |SA |
| au-qld |Qld |AU-QLD |Queensland |QLD |
| au-nt |NT |AU-NT |Northern Territory |NT |
| au-nsw |NSW |AU-NSW |New South Wales |NSW |
| au-act |ACT |AU-ACT |Australian Capital Territory |ACT |

### <a name="austria-states"></a>Österreich: Staaten

| ID | iso | name | name-en | postal |
| --- | --- | --- | --- | --- |
| at-wi |AT-9 |Wien |Vienna |WI |
| at-vo |AT-8 |Vorarlberg |Vorarlberg |VO |
| at-tr |AT-7 |Tirol |Tyrol |TR |
| at-st |AT-6 |Steiermark |Styria |ST |
| at-sz |AT-5 |Salzburg |Salzburg |SZ |
| at-oo |AT-4 |Oberösterreich |Upper Austria |OO |
| at-no |AT-3 |Niederösterreich |Lower Austria |NO |
| at-ka |AT-2 |Kärnten |Carinthia |KA |
| at-bu |AT-1 |Burgenland |Burgenland |BU |

### <a name="brazil-states"></a>Brasilien: Staaten

| ID |
| --- |
| Tocantins |
| Pernambuco |
| Goias |
| Sergipe |
| Sao Paulo |
| Santa Catarina |
| Roraima |
| Rondonia |
| Rio Grande do Sul |
| Rio Grande do Norte |
| Rio de Janeiro |
| Piaui |
| Parana |
| Paraiba |
| Para |
| Minas Gerais |
| Mato Grosso |
| Maranhao |
| Mato Grosso do Sul |
| Distrito Federal |
| Ceara |
| Espirito Santo |
| Bahia |
| Amazonas |
| Amapa |
| Alagoas |
| Acre |
| Litigated Zone 1 |
| Litigated Zone 2 |
| Litigated Zone 3 |
| Litigated Zone 4 |

### <a name="canada-provinces"></a>Kanada: Provinzen

| ID | iso | name | postal |
| --- | --- | --- | --- |
| ca-nu |CA-NU |Nunavut |NU |
| ca-nt |CA-NT |Northwest Territories |NT |
| ca-yt |CA-YT |Yukon |YT |
| ca-sk |CA-SK |Saskatchewan |SK |
| ca-qc |CA-QC |Quebec |QC |
| ca-pe |CA-PE |Prince Edward Island |PE |
| ca-on |CA-ON |Ontario |ON |
| ca-ns |CA-NS |Nova Scotia |NS |
| ca-nl |CA-NL |Newfoundland and Labrador |NL |
| ca-nb |CA-NB |New Brunswick |NB |
| ca-mb |CA-MB |Manitoba |MB |
| ca-bc |CA-BC |British Columbia |BC |
| ca-ab |CA-AB |Alberta |AB |

### <a name="france-regions"></a>Frankreich: Regionen

| ID | name | name-en |
| --- | --- | --- |
| Auvergne-Rhone-Alpes |  |  |
| Bourgogne-Franche-Comte |  |  |
| Bretagne |Bretagne |Brittany |
| Centre-Val de Loire |Centre-Val de Loire |Centre-Val de Loire |
| Corse |Corse |Corsica |
| Grand Est |  |  |
| Guadeloupe | |   |
| Hauts-de-France |  |  |
| Ile-de-France |Île-de-France |Ile-de-France |
| La Réunion |  |  |
| Mayotte  |  |  |
| Normandie |Normandie |  |
| Nouvelle-Aquitaine |  |  |
| Occitanie  |  |  |
| Pays de la Loire |Pays de la Loire |Pays de la Loire |
| Provence-Alpes-Cote d'Azur |Provence-Alpes-Côte d'Azur |Provence-Alpes-Cote d'Azur |
|  |  |  |

### <a name="germany-states"></a>Deutschland: Staaten

| ID | iso | name | name-en | postal |
| --- | --- | --- | --- | --- |
| de-be |DE-BE |Berlin |Berlin |BE |
| de-th |DE-TH |Thüringen |Thuringia |TH |
| de-st |DE-ST |Sachsen-Anhalt |Saxony-Anhalt |ST |
| de-sn |DE-SN |Sachsen |Saxony |SN |
| de-mv |DE-MV |Mecklenburg-Vorpommern |Mecklenburg-Vorpommern |MV |
| de-bb |DE-BB |Brandenburg |Brandenburg |BB |
| de-sh |DE-SH |Schleswig-Holstein |Schleswig-Holstein |SH |
| de-sl |DE-SL |Saarland |Saarland |SL |
| de-rp |DE-RP |Rheinland-Pfalz |Rhineland-Palatinate |RP |
| de-nw |DE-NW |Nordrhein-Westfalen |North Rhine-Westphalia |NW |
| de-ni |DE-NI |Niedersachsen |Lower Saxony |NI |
| de-he |DE-HE |Hessen |Hesse |HE |
| de-hh |DE-HH |Hamburg |Hamburg |HH |
| de-hb |DE-HB |Bremen |Bremen |HB |
| de-by |DE-BY |Bayern |Bavaria |BY |
| de-bw |DE-BW |Baden-Württemberg |Baden-Wurttemberg |BW |

### <a name="ireland-counties"></a>Irland: Grafschaften

| ID |
| --- |
| Wicklow |
| Wexford |
| Westmeath |
| Waterford |
| Sligo |
| Tipperary |
| Roscommon |
| Offaly |
| Monaghan |
| Meath |
| Mayo |
| Louth |
| Longford |
| Limerick |
| Leitrim |
| Laoighis |
| Kilkenny |
| Kildare |
| Kerry |
| Galway |
| Dublin |
| Donegal |
| Cork |
| Clare |
| Cavan |
| Carlow |

### <a name="italy-regions"></a>Italien: Regionen

| ID | iso | name | name-en | postal |
| --- | --- | --- | --- | --- |
| it-vn |IT-34 |Veneto |Veneto |VN |
| it-vd |IT-23 |Valle d'Aosta |Aosta Valley |VD |
| it-um |IT-55 |Umbria |Umbria |UM |
| it-tt |IT-32 |Trentino-Alto Adige |Trentino-South Tyrol |TT |
| it-tc |IT-52 |Toscana |Tuscany |TC |
| it-sc |IT-82 |Sicilia |Sicily |SC |
| it-sd |IT-88 |Sardegna |Sardinia |SD |
| it-pm |IT-21 |Piemonte |Piedmont |Uhr |
| it-ml |IT-67 |Molise |Molise |ML |
| it-mh |IT-57 |Marche |Marche |MH |
| it-lm |IT-25 |Lombardia |Lombardy |LM |
| it-lg |IT-42 |Liguria |Liguria |LG |
| it-lz |IT-62 |Lazio |Lazio |LZ |
| it-fv |IT-36 |Friuli-Venezia Giulia |Friuli-Venezia Giulia |FV |
| it-er |IT-45 |Emilia-Romagna |Emilia-Romagna |ER |
| it-cm |IT-72 |Campania |Campania |CM |
| it-lb |IT-78 |Calabria |Calabria |LB |
| it-bc |IT-77 |Basilicata |Basilicata |BC |
| it-pu |IT-75 |Apulia |Puglia |PU |
| it-ab |IT-65 |Abruzzo |Abruzzo |AB |

### <a name="mexico-states"></a>Mexiko: Staaten

| ID | abreviatura | iso | name | name-en | postal |
| --- | --- | --- | --- | --- | --- |
| mx-zac |Zac. |MX-ZAC |Zacatecas |Zacatecas |ZA |
| mx-yuc |Yuc. |MX-YUC |Yucatán |Yucatan |YU |
| mx-ver |Ver. |MX-VER |Veracruz |Veracruz |VE |
| mx-tla |Tlax. |MX-TLA |Tlaxcala |Tlaxcala |TL |
| mx-tam |Tamps. |MX-TAM |Tamaulipas |Tamaulipas |TM |
| mx-tab |Tab. |MX-TAB |Tabasco |Tabasco |TB |
| mx-son |Son. |MX-SON |Sonora |Sonora |SO |
| mx-sin |Sin. |MX-SIN |Sinaloa |Sinaloa |SI |
| mx-slp |S.L.P. |MX-SLP |San Luis Potosí |San Luis Potosi |SL |
| mx-roo |Q.R. |MX-ROO |Quintana Roo |Quintana Roo |QR |
| mx-que |Qro. |MX-QUE |Querétaro |Queretaro |QE |
| mx-pue |Pue. |MX-PUE |Puebla |Puebla |PU |
| mx-oax |Oax. |MX-OAX |Oaxaca |Oaxaca |OA |
| mx-nle |N.L. |MX-NLE |Nuevo León |Nuevo Leon |NL |
| mx-nay |Nay. |MX-NAY |Nayarit |Nayarit |NA |
| mx-mor |Mor. |MX-MOR |Morelos |Morelos |MR |
| mx-mic |Mich. |MX-MIC |Michoacán |Michoacan |MC |
| mx-mex |Méx. |MX-MEX |Estado de México |Mexico State |MX |
| mx-jal |Jal. |MX-JAL |Jalisco |Jalisco |JA |
| mx-hid |Hgo. |MX-HID |Hidalgo |Hidalgo |HI |
| mx-gro |Gro. |MX-GRO |Guerrero |Guerrero |GR |
| mx-gua |Gto. |MX-GUA |Guanajuato |Guanajuato |GT |
| mx-dur |Dgo. |MX-DUR |Durango |Durango |DU |
| mx-dif |CDMX. |MX-DIF |Ciudad de México |Mexico City |DF |
| mx-col |Col. |MX-COL |Colima |Colima |CL |
| mx-coa |Coah. |MX-COA |Coahuila |Coahuila |CA |
| mx-chh |Chih. |MX-CHH |Chihuahua |Chihuahua |CH |
| mx-chp |Chis. |MX-CHP |Chiapas |Chiapas |CP |
| mx-cam |Camp. |MX-CAM |Campeche |Campeche |CM |
| mx-bcs |B.C.S. |MX-BCS |Baja California Sur |Baja California Sur |BS |
| mx-bcn |B.C. |MX-BCN |Baja California |Baja California |BN |
| mx-agu |Ags. |MX-AGU |Aguascalientes |Aguascalientes |AG |

### <a name="netherlands-provinces"></a>Niederlande: Provinzen

| ID | iso | name | name-en |
| --- | --- | --- | --- |
| nl-zh |NL-ZH |Zuid-Holland |South Holland |
| nl-ze |NL-ZE |Zeeland |Zeeland |
| nl-ut |NL-UT |Utrecht |Utrecht |
| nl-ov |NL-OV |Overijssel |Overijssel |
| nl-nh |NL-NH |Noord-Holland |North Holland |
| nl-nb |NL-NB |Noord-Brabant |North Brabant |
| nl-li |NL-LI |Limburg |Limburg |
| nl-gr |NL-GR |Groningen |Groningen |
| nl-ge |NL-GE |Gelderland |Gelderland |
| nl-fr |NL-FR |Fryslân |Friesland |
| nl-fl |NL-FL |Flevoland |Flevoland |
| nl-dr |NL-DR |Drenthe |Drenthe |

### <a name="uk-countries"></a>Vereinigtes Königreich: Länder

| ID | iso | name |
| --- | --- | --- |
| gb-wls |GB-WLS |Wales |
| gb-sct |GB-SCT |Scotland |
| gb-nir |GB-NIR |Northern Ireland |
| gb-eng |GB-ENG |England |

### <a name="usa-states"></a>USA: Staaten

| ID | name | postal |
| --- | --- | --- |
| us-mi |Michigan |MI |
| us-ak |Alaska |AK |
| us-hi |Hawaii |HI |
| us-fl |Florida |FL |
| us-la |Louisiana |LA |
| us-ar |Arkansas |AR |
| us-sc |South Carolina |SC |
| us-ga |Georgia |GA |
| us-ms |Mississippi |MS |
| us-al |Alabama |AL |
| us-nm |New Mexico |NM |
| us-tx |Texas |TX |
| us-tn |Tennessee |TN |
| us-nc |North Carolina |NC |
| us-ok |Oklahoma |OK |
| us-az |Arizona |AZ |
| us-mo |Missouri |MO |
| us-va |Virginia |VA |
| us-ks |Kansas |KS |
| us-ky |Kentucky |KY |
| us-co |Colorado |CO |
| us-md |Maryland |MD |
| us-wv |West Virginia |WV |
| us-de |Delaware |DE |
| us-dc |District of Columbia |DC |
| us-il |Illinois |IL |
| us-oh |Ohio |OH |
| us-ca |California |CA |
| us-ut |Utah |UT |
| us-nv |Nevada |NV |
| us-in |Indiana |IN |
| us-nj |New Jersey |NJ |
| us-ri |Rhode Island |RI |
| us-ct |Connecticut |CT |
| us-pa |Pennsylvania |PA |
| us-ny |New York |NY |
| us-ne |Nebraska |NE |
| us-ma |Massachusetts |MA |
| us-ia |Iowa |IA |
| us-nh |New Hampshire |NH |
| us-or |Oregon |OR |
| us-mn |Minnesota |MN |
| us-vt |Vermont |VT |
| us-id |Idaho |ID |
| us-wi |Wisconsin |WI |
| us-wy |Wyoming |WY |
| us-sd |South Dakota |SD |
| us-nd |North Dakota |ND |
| us-me |Maine |ME |
| us-mt |Montana |MT |
| us-wa |Washington |WA |

## <a name="next-steps"></a>Nächste Schritte

* [Matrixvisuals in Power BI](desktop-matrix-visual.md)

* [Visualisierungstypen in Power BI](power-bi-visualization-types-for-reports-and-q-and-a.md)
