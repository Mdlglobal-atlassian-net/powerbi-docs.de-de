---
title: Power BI-Lizenzierung in Ihrem Unternehmen
description: Übersicht über die verschiedenen in Power BI verfügbaren Lizenztypen und die Möglichkeiten für Administratoren, die Lizenzierung für Ihre Organisation zu erwerben und zu verwalten
author: kfollis
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 04/08/2020
ms.author: kfollis
LocalizationGroup: Administration
ms.openlocfilehash: a41e9453158c38a208fe7f4ac937b4e86a515f4b
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "81436320"
---
# <a name="power-bi-licensing-in-your-organization"></a>Power BI-Lizenzierung in Ihrem Unternehmen

Welche Möglichkeiten Benutzer im Power BI-Dienst haben, hängt von der Art der benutzerspezifischen Lizenz sowie davon ab, ob der Inhalt, mit dem diese agieren, sich in einem Arbeitsbereich befindet, der einer Power BI Premium-Kapazität zugewiesen ist. Alle Benutzer des Power BI-Diensts müssen eine Lizenz besitzen.

Es gibt zwei Möglichkeiten für Benutzer, eine Lizenz zu erhalten. Mithilfe der Self-Service-Registrierungsfunktion und ihres Geschäfts-, Schul- oder Unikontos können Benutzer sich eigenständig Free- oder Pro-Lizenz beschaffen. Alternativ können Administratoren ein Power BI-Abonnement erwerben und Benutzern Lizenzen zuweisen.

Der Schwerpunkt dieses Artikels liegt auf dem Erwerb von Diensten und der Lizenzierung pro Benutzer aus Administratorsicht. Weitere Informationen dazu, wie Benutzer sich selbstständig eine Lizenz beschaffen können, finden Sie unter [Registrieren für Power BI als Einzelperson](service-self-service-signup-for-power-bi.md).

## <a name="who-can-purchase-and-assign-licenses"></a>Wer kann Lizenzen erwerben und zuweisen?

Sie müssen der Administratorrolle zugewiesen sein, um Lizenzen für Ihre Organisation erwerben oder zuweisen zu können. Administratorrollen werden über das Azure Active Directory Admin Center oder das Microsoft 365 Admin Center zugewiesen. In der folgenden Tabelle wird aufgeführt, welche Rolle für Aufgaben im Zusammenhang mit Erwerb und Lizenzierung erforderlich ist. Weitere Informationen zu Administratorrollen in Azure Active Directory finden Sie unter [Anzeigen und Zuweisen von Administratorrollen in Azure Active Directory](https://docs.microsoft.com/azure/active-directory/users-groups-roles/directory-manage-roles-portal). Weitere Informationen zu Administratorrollen in Microsoft 365, einschließlich bewährter Methoden, finden Sie unter [Informationen zu Administratorrollen](https://docs.microsoft.com/microsoft-365/admin/add-users/about-admin-roles?view=o365-worldwide).

| Wer kann Dienste und Lizenzen erwerben? | Wer kann Benutzerlizenzen verwalten? |
| --------------- | --------------- |
| Rechnungsadministrator | Lizenzadministrator |
| Globaler Administrator | Benutzeradministrator |
|  | Globaler Administrator |

Diese Rollen sind für die Verwaltung der Organisation vorgesehen. Weitere Informationen zur Power BI-Dienstadministratorrolle finden Sie unter [Grundlegendes zur Dienstadministratorrolle in Power BI](service-admin-role.md).

## <a name="get-power-bi-for-your-organization"></a>Abrufen von Power BI für Ihre Organisation

Ein globaler Administrator oder ein Abrechnungsadministrator kann sich für den Power BI-Dienst registrieren und Lizenzen für die Benutzer in Ihrer Organisation erwerben. Wenn Sie noch nicht kaufbereit sind, können Sie auch mit der Power BI Pro-Testversion beginnen. Durch diese erhalten Sie einen Monat lang 25 Lizenzen. Ausführliche Anleitungen zur Registrierung finden Sie unter [Erwerb eines Power BI-Abonnements für Ihre Organisation](admin/service-admin-org-subscription.md).

## <a name="about-self-service-sign-up"></a>Grundlegendes zur Self-Service-Registrierung

Einzelbenutzer können sich eine eigene Power BI-Lizenz zulegen, indem sie sich mit ihrem Geschäfts-, Schul- oder Unikonto anmelden. Mit einer kostenlosen Lizenz können Benutzer Power BI für die Analyse und Visualisierung persönlicher Daten über „Mein Arbeitsbereich“ nutzen, aber Sie können keine Zusammenarbeit mit anderen Benutzern initiieren. Zum Freigeben von Inhalten ist eine Power BI Pro-Lizenz erforderlich. Benutzer können ihren Lizenztyp auf Pro upgraden oder sich direkt für Pro registrieren, wenn die Organisation die kommerzielle Cloud verwendet. Der direkte Erwerb von oder ein Upgrade auf Pro ist für Bildungseinrichtungen oder Organisationen nicht verfügbar, die Government-Cloud- oder Sovereign-Cloud Instanzen nutzen.

Wenn Sie nicht möchten, dass Benutzern in Ihrer Organisation die Self-Service-Registrierung nutzen können, finden Sie unter [Aktivieren oder Deaktivieren der Self-Service-Registrierung](admin/service-admin-disable-self-service.md) weitere Informationen zu deren Deaktivierung.

Wenn Sie wissen möchten, welche Benutzer in Ihrer Organisation bereits Lizenzen besitzen, finden Sie unter [Anzeigen und Verwalten von Benutzerlizenzen](admin/service-admin-manage-licenses.md) weitere Informationen.

## <a name="license-types-and-capabilities"></a>Lizenztypen und Funktionen

Es gibt zwei Arten von Power BI-Lizenzen für Benutzer: Free und Pro. Welche Art von Lizenz ein Benutzer benötigt, hängt davon ab, wo der Inhalt gespeichert wird und wie dieser mit dem Inhalt interagieren muss. Wo der Inhalt gespeichert werden kann, hängt vom [Abonnementtyp Ihrer Organisation](#subscription-types) ab.

Mit dem Abonnementtyp [Power BI Premium](service-admin-premium-purchase.md) können Benutzer mit einer Free-Lizenz mit Inhalten in Arbeitsbereichen interagieren, die einer Premium-Kapazität zugewiesen sind. Außerhalb der Premium-Kapazität kann ein Benutzer mit einer Free-Lizenz den Power BI-Dienst nur zum Herstellen einer Verbindung mit Daten und zum Erstellen von Berichten und Dashboards in einem persönlichen Arbeitsbereich verwenden. Sie können Inhalte nicht für andere Benutzer freigeben oder in App-Arbeitsbereichen veröffentlichen.

Bei einem Power BI-Standardabonnement wird eine gemeinsam genutzte Kapazität verwendet. Wenn Inhalt in der gemeinsam genutzten Kapazität gespeichert wird, können Benutzer, denen eine Power BI Pro-Lizenz zugewiesen ist, nur mit anderen Power BI Pro-Benutzern zusammenarbeiten. Sie können von anderen Benutzern freigegebene Inhalte nutzen, Inhalte in App-Arbeitsbereichen veröffentlichen, Dashboards freigeben sowie Dashboards und Berichte abonnieren.  Wenn sich Arbeitsbereiche in der Premium-Kapazität befinden, können Pro-Benutzer Inhalte an Benutzer verteilen, die keine Power BI Pro-Lizenz besitzen.

In der folgenden Tabelle wird der Funktionsumfang der einzelnen Lizenztypen zusammengefasst. Eine ausführliche Übersicht über die verfügbaren Features pro Lizenztyp finden Sie unter [Features nach Lizenztyp](service-features-license-type.md).

| Lizenztyp | Funktionen, wenn der Arbeitsbereich sich in einer gemeinsam genutzten Kapazität befindet | Zusätzliche Funktionen, wenn der Arbeitsbereich sich in einer Premium-Kapazität befindet |
| --------- | ----------- | ----------- |
| Power BI Free | Zugriff auf Inhalte in „Mein Arbeitsbereich“ | Nutzung freigegebener Inhalte |
| Power BI Pro | Veröffentlichen von Inhalten in App-Arbeitsbereichen, Freigeben von Dashboards, Abonnieren von Dashboards und Berichten, Freigeben von Inhalten für Benutzer mit einer Pro-Lizenz | Verteilen von Inhalten an Benutzer mit Free-Lizenzen |

## <a name="subscription-types"></a>Abonnementtypen

Alle benutzerbasierten, kommerziellen Lizenzabonnements von Microsoft basieren auf Azure Active Directory-Identitäten. Das bedeutet, dass Sie sich mit einer Identität anmelden müssen, für die Azure Active Directory kommerzielle Lizenzen unterstützt. Sie können einem Microsoft-Abonnement, das Azure Active Directory für Identitätsdienste verwendet, ein Power BI-Abonnement hinzufügen. Manche Abonnements, z. B. Office 365 E5, enthalten eine Power BI Pro-Lizenz, sodass keine separate Registrierung für Power BI erforderlich ist.

Es gibt zwei Arten von Power BI-Abonnements für Organisationen: Self-Service-BI mit Power BI Pro und Advanced Analytics mit Power BI Premium.

Mit einem Self-Service-Standardabonnement für Power BI Pro weisen Administratoren Lizenzen pro Benutzer zu. Für Power BI Pro-Lizenzen fällt eine monatliche Gebühr pro Benutzer an, die die Zusammenarbeit, Veröffentlichung, Freigabe und Ad-hoc-Analyse ermöglicht. Der Inhalt wird in einer gemeinsam genutzten Speicherkapazität gespeichert, die vollständig von Microsoft verwaltet wird.

Ein Power BI Premium-Abonnement ordnet einer Organisation eine dedizierte Kapazität zu. Premium eignet sich für Unternehmens-BI, Big-Data-Analysen, die lokale Berichterstellung und die Berichterstellung in der Cloud, während Premium erweiterte Steueroptionen für die Verwaltung und Bereitstellung bietet. Dedizierte Compute- und Speicherressourcen werden von den Kapazitätsadministratoren in Ihrer Organisation verwaltet. Für diese dedizierte Umgebung fallen monatliche Kosten an. Zusätzlich zu anderen Premium-Vorteilen können Inhalte, die in einer Premium-Kapazität gespeichert sind, von Benutzern aufgerufen und an Benutzer verteilt werden, die keine Power BI Pro-Lizenz besitzen. Mindestens ein Benutzer muss eine Power BI Pro-Lizenz besitzen, die für die Verwendung von Premium zugewiesen ist, und Inhaltsersteller und Entwickler benötigen weiterhin eine Power BI Pro-Lizenz.

Die beiden Abonnementtypen schließen sich nicht gegenseitig aus. Sie können sowohl Power BI Premium als auch Power BI Pro besitzen. In dieser Konfiguration können Inhalte, die in einer Premium-Kapazität gespeichert sind, für alle Benutzer freigegeben werden, und auch die gemeinsam genutzte Kapazität steht zur Verfügung. Informationen zu Kapazitätslimits finden Sie unter [Verwalten des Datenspeichers in Power BI-Arbeitsbereichen](service-admin-manage-your-data-storage-in-power-bi.md).

Auf der [Power BI-Preisseite](https://powerbi.microsoft.com/pricing) werden Produktfeatures und -preise gegenübergestellt.

## <a name="guest-user-access"></a>Gastbenutzerzugriff

In manchen Fällen müssen Inhalte an externe Benutzer verteilt werden. Sie können Inhalte für externe Benutzer freigeben, indem Sie diesen eine Einladung senden, Inhalte als Gast anzuzeigen. Azure AD B2B ermöglicht die Freigabe von Inhalten für externe Gastbenutzer. Die folgenden Voraussetzungen müssen erfüllt sein, damit Sie Inhalte für externe Benutzer freigeben können:

- Die Option zum Freigeben von Inhalten für externe Benutzer muss aktiviert sein.

- Der Gastbenutzer benötigt eine entsprechende Lizenz, um die freigegebenen Inhalte anzuzeigen.

Weitere Informationen zum Gastbenutzerzugriff finden Sie unter [Verteilen von Power BI-Inhalten an externe Gastbenutzer mit Azure AD B2B](service-admin-azure-ad-b2b.md).

## <a name="purchase-power-bi-pro-licenses"></a>Erwerben von Power BI Pro-Lizenzen

Als Administrator können Sie Power BI Pro-Lizenzen über Microsoft 365 oder einen Microsoft-Partner erwerben. Nach dem Erwerb weisen Sie die Lizenzen einzelnen Benutzern zu. Weitere Informationen finden Sie unter [Purchase and assign Power BI Pro licenses](service-admin-purchasing-power-bi-pro.md) (Erwerben und Zuweisen von Power BI Pro-Lizenzen).

### <a name="power-bi-pro-license-expiration"></a>Ablauf der Power BI Pro-Lizenz

Nach Ablauf einer Power BI Pro-Lizenz gibt es eine Karenzzeit. Bei Lizenzen, die Teil einer Volumenlizenz sind, beträgt die Karenzzeit 90 Tage. Bei direkt erworbenen Lizenzen beträgt die Karenzzeit 30 Tage.

Für Power BI Pro gilt der gleiche Abonnementslebenszyklus wie für Office 365. Weitere Informationen finden Sie unter [Was geschieht mit meinen Daten und dem Zugriff darauf, wenn mein Office 365 Business-Abonnement endet?](https://support.office.com/article/What-happens-to-my-data-and-access-when-my-Office-365-for-business-subscription-ends-4436582f-211a-45ec-b72e-33647f97d8a3).


## <a name="next-steps"></a>Nächste Schritte

- [Erwerben und Zuweisen von Power BI Pro-Lizenzen](service-admin-purchasing-power-bi-pro.md)
- [Dokumentation zu Business-Abonnements und Abrechnung in Microsoft 365](https://docs.microsoft.com/microsoft-365/commerce/?view=o365-worldwide)
- [Suchen von Power BI-Benutzer, die sich angemeldet haben](service-admin-access-usage.md)
- Weitere Fragen? [Stellen Sie Ihre Frage in der Power BI-Community.](https://community.powerbi.com/)
