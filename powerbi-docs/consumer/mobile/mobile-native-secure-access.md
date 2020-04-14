---
title: Schützen von Power BI-Daten mit nativer Geräteidentifikation
description: Erfahren Sie, wie Sie Ihre iOS- und Android-Apps so konfigurieren, dass diese eine zusätzliche Identifizierung erfordern, bevor Sie auf Ihre Power BI-Daten zugreifen können.
author: paulinbar
ms.service: powerbi
ms.subservice: powerbi-mobile
ms.topic: conceptual
ms.date: 04/07/2020
ms.author: painbar
ms.openlocfilehash: ce7b3c3bc667023ef36650d8c551caaceab04c02
ms.sourcegitcommit: 9b806dfe62c2dee82d971bb4f89d983b97931b43
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/07/2020
ms.locfileid: "80802799"
---
# <a name="protect-power-bi-app-with-face-id-touch-id-passcode-or-biometric-data"></a>Schützen einer Power BI-App mit Face ID, Touch ID, einem Passcode oder biometrischen Daten 

In vielen Fällen sind die in Power BI verwalteten Daten vertraulich und müssen so geschützt werden, dass nur autorisierte Benutzer darauf zugreifen können. 

In den Power BI-Apps für iOS und Android können Sie Ihre Daten schützen, indem Sie eine zusätzliche Identifizierung konfigurieren. Jedes Mal, wenn die App dann gestartet oder in den Vordergrund gebracht wird, ist eine Identifizierung erforderlich. Unter iOS bedeutet dies, dass Face ID, Touch ID oder ein Passcode angegeben werden muss. Unter Android bedeutet dies, biometrische Daten (Fingerabdruck-ID) bereitzustellen.

Gilt für:

| ![iPhone](./media/mobile-native-secure-access/ios-logo-40-px.png) | ![iPads](./media/mobile-native-secure-access/ios-logo-40-px.png) | ![Android-Smartphone](././media/mobile-native-secure-access/android-logo-40-px.png) | ![Android-Tablet](././media/mobile-native-secure-access/android-logo-40-px.png) |
|:--- |:--- |:--- |:--- |
|iPhones |iPads |Android-Telefone |Android-Tablets |

## <a name="turn-on-face-id-touch-id-or-passcode-on-ios"></a>Aktivieren von Face ID, Touch ID oder des Passcodes unter iOS

Navigieren Sie zur App-Einstellung unter **Privacy and Security** (Datenschutz und Sicherheit), um eine zusätzliche Identifizierung in der mobilen Power BI-App für iOS zu verwenden. Die Option zum Aktivieren von Face ID, Touch ID oder des Passcodes wird angezeigt. Welche Optionen Ihnen angezeigt werden, hängt von den Funktionen Ihres Geräts ab.

![Einstellungsseite der Power BI-App für iOS](./media/mobile-native-secure-access/mobile-ios-native-secured-setting.png)

Wenn diese Einstellung aktiviert ist, werden Sie jedes Mal, wenn Sie die App starten oder in den Vordergrund bringen, dazu aufgefordert, Ihre ID bereitzustellen, um auf die App zugreifen zu können.

Welchen ID-Typ Sie bereitstellen müssen, hängt von den Funktionen Ihres Geräts ab. Wenn Ihr Gerät Face ID unterstützt, müssen Sie Face ID verwenden. Wenn es Touch ID unterstützt, müssen Sie Touch ID verwenden. Wenn keine der beiden Optionen unterstützt wird, müssen Sie einen Passcode angeben. Die Abbildung unten zeigt den Bildschirm der Face ID-Authentifizierung.

![Face ID für Power BI iOS](./media/mobile-native-secure-access/mobile-ios-native-secured-faceid.png)

## <a name="turn-on-biometric-data-fingerprint-id-on-android"></a>Aktivieren der biometrischen Daten (Fingerabdruck-ID) unter Android

Navigieren Sie zur App-Einstellung unter **Privacy and Security** (Datenschutz und Sicherheit), um eine zusätzliche Identifizierung in der mobilen Power BI-App für Android zu verwenden. Die Option zum Aktivieren der biometrischen Daten wird angezeigt.

![Einstellungsseite der Power BI-App für Android](./media/mobile-native-secure-access/mobile-android-native-secured-setting.png)

Wenn diese Einstellung aktiviert ist, werden Sie jedes Mal, wenn Sie die App starten oder in den Vordergrund bringen, dazu aufgefordert, Ihre biometrischen Daten (Fingerabdruck-ID) bereitzustellen, um auf die App zugreifen zu können.

Die Abbildung unten zeigt den Bildschirm der Authentifizierung über den Fingerabdruck.

![Face ID für Power BI iOS](./media/mobile-native-secure-access/mobile-android-native-secured-fingerprint-id.png)

>[!NOTE]
>Sie müssen zunächst biometrische Daten in Ihrem Android-Gerät einrichten, um die Einstellung der mobilen App zum Anfordern einer biometrischen Authentifizierung verwenden zu können. Wenn Ihr Gerät keine biometrischen Daten unterstützt, können Sie den Zugriff auf Ihre Power BI-Daten mit dieser Einstellung für die mobile App nicht sichern.
>
>Wenn Ihr Administrator für die mobile App den [sicheren Zugriff remote aktiviert](#mdm-enforcement-of-secure-access-to-your-power-bi-mobile-app) hat, müssen Sie, falls nicht bereits getan, biometrische Daten auf Ihrem Gerät einrichten, um auf die App zugreifen zu können. Wenn Ihr Gerät keine biometrischen Daten unterstützt, betrifft Sie diese Remoteeinstellung nicht. Der Zugriff auf Ihre mobile App bleibt ungesichert.

## <a name="mdm-enforcement-of-secure-access-to-your-power-bi-mobile-app"></a>MDM-Erzwingung des sicheren Zugriffs auf Ihre mobile Power BI-App

Einige Organisationen verfügen über Sicherheitsrichtlinien und Konformitätsanforderungen, die eine zusätzliche Identifizierung erzwingen, bevor auf vertrauliche Geschäftsdaten zugegriffen werden kann.

Zur Unterstützung dessen ermöglicht die mobile Power BI-App Administratoren, die Einstellung für den sicheren Zugriff auf die mobile App zu steuern, indem sie die Konfigurationseinstellungen der App aus Microsoft Intune und anderen Lösungen für die mobile Geräteverwaltung (MDM) mithilfe von Push übertragen. Administratoren können die App-Schutzrichtlinie verwenden, um diese Einstellung für alle Benutzer oder für eine Benutzergruppe zu aktivieren. Genauere Informationen finden Sie unter [Remotekonfiguration der Power BI-App mithilfe des Tools für die mobile Geräteverwaltung](mobile-app-configuration.md#data-protection-settings-ios-and-android).

## <a name="next-steps"></a>Nächste Schritte
* [Remotekonfiguration der Power BI-App mithilfe des Tools für die mobile Geräteverwaltung](mobile-app-configuration.md)
