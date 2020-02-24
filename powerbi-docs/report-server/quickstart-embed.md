---
title: Einbetten eines Power BI-Berichtsserver-Berichts in einen iFrame in SharePoint Server
description: In diesem Artikel wird beschrieben, wie Sie einen Bericht des Power BI-Berichtsservers in einen iFrame in SharePoint Server einbetten.
author: maggiesMSFT
ms.author: maggies
ms.date: 08/12/2019
ms.topic: conceptual
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.custom: mvc
ms.openlocfilehash: 4e7616ec3ce6552130848bc0508bf8b9ac8ac965
ms.sourcegitcommit: 97597ff7d9ac2c08c364ecf0c729eab5d59850ce
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/09/2020
ms.locfileid: "75762598"
---
# <a name="embed-a-power-bi-report-server-report-using-an-iframe-in-sharepoint-server"></a>Einbetten eines Power BI-Berichtsserver-Berichts in einen iFrame in SharePoint Server

In diesem Artikel erfahren Sie, wie Sie einen Bericht des Power BI-Berichtsservers mithilfe eines iFrames in eine SharePoint-Seite einbetten. Wenn Sie mit SharePoint Online arbeiten, muss der öffentliche Zugriff auf den Power BI-Berichtsserver möglich sein. In SharePoint Online kann der Power BI-Webpart, der mit dem Power BI-Dienst eingesetzt wird, nicht mit dem Power BI-Berichtsserver verwendet werden.  

![iFrame-Beispiel](media/quickstart-embed/quickstart_embed_01.png)

## <a name="prerequisites"></a>Voraussetzungen
* Der [Power BI-Berichtsserver](https://powerbi.microsoft.com/report-server/) ist installiert und konfiguriert.
* Die [für den Power BI-Berichtsserver optimierte Version von Power BI Desktop](install-powerbi-desktop.md) ist installiert.
* Eine [SharePoint-Umgebung](https://docs.microsoft.com/sharepoint/install/install) ist installiert und konfiguriert.
* Internet Explorer 11 wird nur unterstützt, wenn der Dokumentmodus auf den Modus „IE11 (Microsoft Edge)“ festgelegt ist oder wenn SharePoint Online verwendet wird. Sie können mit lokalem SharePoint und SharePoint Online auch andere unterstützte Browser verwenden.

## <a name="create-the-power-bi-report-url"></a>Erstellen der Power BI-Berichts-URL

1. Laden Sie das Beispiel [Blogdemo](https://github.com/Microsoft/powerbi-desktop-samples) von GitHub herunter. Klicken Sie auf **Clone or download** (Klonen oder herunterladen) und anschließend auf **Download ZIP** (ZIP herunterladen).

    ![Herunterladen der PBIX-Beispieldatei](media/quickstart-embed/quickstart_embed_14.png)

2. Entzippen Sie die Datei, und öffnen Sie die PBIX-Beispieldatei in der für den Power BI-Berichtsserver optimierten Version von Power BI Desktop.

    ![Power BI-Berichtsserver-Desktop-Tool](media/quickstart-embed/quickstart_embed_02.png)

3. Speichern Sie den Bericht auf dem **Power BI-Berichtsserver**. 

    ![Speichern auf dem Power BI-Berichtsserver](media/quickstart-embed/quickstart_embed_03.png)

4. Lassen Sie sich den Bericht im Webportal des Power BI-Berichtsservers anzeigen.

    ![Webportal](media/quickstart-embed/quickstart_embed_04.png)

### <a name="capture-the-url-parameter"></a>Erfassen des URL-Parameters

Sobald die URL verfügbar ist, können Sie auf einer SharePoint-Seite einen iFrame erstellen, in dem der Bericht gehostet wird. Fügen Sie einer beliebigen URL eines Berichts des Power BI-Berichtsservers den Abfragezeichenfolgenparameter `?rs:embed=true` hinzu, um den Bericht in einen SharePoint-iFrame einzubetten.

   Beispiel:
    ``` 
    https://myserver/reports/powerbi/Sales?rs:embed=true
    ```
## <a name="embed-the-report-in-a-sharepoint-iframe"></a>Einbetten des Berichts in einen SharePoint-iFrame

1. Navigieren Sie zu einer **Websiteinhalte**-Seite in SharePoint.

    ![Seite mit Websiteinhalten](media/quickstart-embed/quickstart_embed_05.png)

2. Wählen Sie die Seite aus, auf der Sie Ihren Bericht hinzufügen möchten.

    ![App für Seite mit Websiteinhalten](media/quickstart-embed/quickstart_embed_06.png)

3. Klicken Sie auf das Zahnradsymbol oben rechts und dann auf **Seite bearbeiten**.

    ![Option „Seite bearbeiten“](media/quickstart-embed/quickstart_embed_07.png)

4. Klicken Sie auf **Webpart hinzufügen**.

5. Klicken Sie unter **Kategorien** auf **Medien und Inhalt**. Klicken Sie unter **Webparts** auf **Inhalts-Editor** und anschließend auf **Hinzufügen**.

    ![Klicken auf „Webparts“ und „Inhalts-Editor“](media/quickstart-embed/quickstart_embed_09.png)

6. Wählen Sie **Hier klicken, um neue Inhalte hinzuzufügen** aus.

7. Klicken Sie im oberen Menü auf **Text formatieren** und anschließend auf **Quelle bearbeiten**.

     ![Quelle bearbeiten](media/quickstart-embed/quickstart_embed_11.png)

8. Fügen Sie im Fenster **Quelle bearbeiten** den iFrame-Code in **HTML-Quelle** ein, und klicken Sie auf **OK**.

    ![iFrame-Code](media/quickstart-embed/quickstart_embed_12.png)

     Beispiel:
     ```html
     <iframe width="800" height="600" src="https://myserver/reports/powerbi/Sales?rs:embed=true" frameborder="0" allowFullScreen="true"></iframe>
     ```

9. Klicken Sie im oberen Menü auf **Seite** und anschließend auf **Bearbeitung beenden**.

    ![Bearbeitung beenden](media/quickstart-embed/quickstart_embed_13.png)

    Der Bericht wird auf der Seite angezeigt.

    ![iFrame-Beispiel](media/quickstart-embed/quickstart_embed_01.png)

## <a name="next-steps"></a>Nächste Schritte

- [Erstellen eines Power BI-Berichts für den Power BI-Berichtsserver](quickstart-create-powerbi-report.md)  
- [Erstellen eines paginierten Berichts für den Power BI-Berichtsserver](quickstart-create-paginated-report.md)  

Weitere Fragen? [Wenden Sie sich an die Power BI-Community](https://community.powerbi.com/). 
