---
title: B2B-Zielgruppe und Profilaktivierung
description: Stellen Sie mit Real-Time Customer Data Platform B2B edition Account-basierte und personenbasierte Zielgruppen zur Aktivierung über verschiedene Kanäle und Ziele hinweg bereit.
solution: Real-Time Customer Data Platform
source-git-commit: ce7331f279a6e59db95ca3b763148440598cde84
workflow-type: tm+mt
source-wordcount: '1264'
ht-degree: 5%
---

# B2B-Zielgruppe und Profilaktivierung

Verwenden Sie **Real-Time Customer Data Platform B2B edition**, um Account-, Opportunity- und Personendaten in einheitlichen B2B-Profilen zusammenzuführen und dann sowohl Personen- als auch Account-Zielgruppen in Zielen wie LinkedIn, Marketo Engage und Cloud-Speicher zu aktivieren. In diesem Blueprint wird beschrieben, wie Sie B2B-Schemata entwerfen, Zielgruppen mit mehreren Entitäten erstellen und für die Aktivierung über mehrere Kanäle und Ziele sowie für die Orchestrierung und Analyse in Programmen wie **Journey Optimizer B2B Edition** und **Customer Journey Analytics B2B edition** exportieren.

## Anwendungsfälle

- Erstellen Sie Zielgruppen von Personen für das kanalübergreifende Targeting und die Personalisierung basierend auf B2B-Daten, einschließlich Konten, Chancen und Leads.
- Erstellen Sie Audiences mit mehreren Entitäten, die Attribute auf Konto- und Opportunity-Ebene mit dem Verhalten auf Personenebene kombinieren, indem Sie einen **Segment-of-Segments**-Ansatz verwenden (z. B. „Personen, die die Preisfindungsseite in den letzten 3 Tagen besucht haben und Entscheidungsträger bei Opportunitys in Phase X für Accounts in Branche Y sind„).
- Aktivieren Sie Personen- und Account-Zielgruppen für Experience Platform- und Cloud-Speicher-Ziele - wie Marketo Engage, LinkedIn Matched Audiences, Google Customer Match, DV360, The Trade Desk, Amazon Ads, Bombora und Demandbase - für Targeting, Personalisierung, Verkaufskontakte und Analysen.

## Programme

- Real-Time Customer Data Platform B2B edition
- (Optional) **Customer Journey Analytics B2B edition**
- (Optional) **Journey Optimizer B2B Edition**

## Integrationsmuster

Typische B2B-Integrationsmuster für diesen Blueprint sind:

- **B2B-Interaktion und CRM-Quellen → RTCDP B2B-→-Ziele**

  B2B-Interaktion und CRM-Systeme wie Marketo Engage, Salesforce und Microsoft Dynamics senden Leads/Kontakte, Konten und Opportunities mithilfe der standardmäßigen B2B-**in** Real-Time CDP B2B edition. Von dort aus werden Zielgruppen von Personen und Konten für Ziele aktiviert, darunter:

  - Marketo Engage
  - Abgestimmte LinkedIn-/LinkedIn-Zielgruppen
  - Google Customer Match und DV360
  - The Trade Desk
  - Amazon Ads
  - Trade Desk CRM, Criteo, Bing und andere Werbeplattformen
  - Cloud-Speicher-Ziele wie Amazon S3, ADLS und Snowflake für die nachgelagerte Verwendung

- **B2B-Absicht und Ereignisquellen → RTCDP B2B-→-Zielgruppen → -Ziele**

  B2B-Absicht und Ereignisquellen wie Bombora Intent, Demandbase Intent, PathFactory und RainFocus streamen Absichts- und Interaktionsereignisse in RTCDP B2B. Diese Ereignisse werden standardmäßigen B2B-Schemata zugeordnet und verwendet, um Personen- und Account-Zielgruppen zu erstellen, die für Werbe- und Marketing-Ziele aktiviert werden können.

Verschiedene B2B-Datenquellen können verwendet werden, um Account-, Lead-, Opportunity- und Personendaten mithilfe der standardmäßigen B2B **Schemata und -Beziehungen der B2B edition von Real-Time Customer Data Platform**.

## Architektur

![Referenzarchitektur für den Blueprint „B2B-Zielgruppe“ und „Profilaktivierung“](assets/b2b-audience-profile-activation.png){width="1000" zoomable="yes"}

## Leitlinien

Beachten Sie beim Entwerfen von B2B-Zielgruppen und Profilen die folgenden Leitplanken und die Dokumentation zur Eignung:

- [Leitplanken für Real-Time Customer Data Platform B2B edition](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/intro/rtcdpb2b-intro/b2b-guardrails?lang=en)
- [Anwendungsfälle für die Segmentierung für Real-Time CDP B2B edition](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/segmentation/b2b)
- [Leitplanken für Profile und Segmentierung](https://experienceleague.adobe.com/en/docs/experience-platform/profile/guardrails)
- [Aktualisierung der Eignungskriterien für Streaming-Segmentierung](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/eligibility-criteria-update)

### Unterstützung mehrerer Instanzen und IMS-Organisation

Im Folgenden werden die unterstützten Muster für die Zuordnung von Experience Platform- und Marketo Engage-Instanzen beschrieben.

#### Marketo als Datenquelle für Experience Platform

- Es werden mehrere Marketo Engage-Instanzen zu einer Experience Platform-Instanz unterstützt.
- Eine Marketo Engage-Instanz für mehrere Experience Platform-Instanzen wird nicht unterstützt.
- Eine Marketo Engage-Instanz für eine Experience Platform-Instanz und mehrere Sandboxes werden unterstützt.

#### Marketo als Ziel für Experience Platform

- Experience Platform wird für viele Marketo Engage-Instanzen unterstützt.
- Es werden viele Experience Platform-Instanzen auf einer Marketo Engage-Instanz unterstützt.

#### Experience Platform-Profil und Segmentierungsleitplanken

Die Experience Platform-Profil- und Segmentierungsleitplanken finden Sie hier: [Profil- und Segmentierungsleitplanken](https://experienceleague.adobe.com/en/docs/experience-platform/profile/guardrails).

Segmente, die B2B-Entitäten wie Konten, Leads oder Opportunities enthalten, beruhen auf Beziehungen mit mehreren Entitäten und werden in &quot;**&quot;**. Im Gegensatz dazu wird **Streaming-Segmentierung** für Zielgruppen unterstützt, die auf Personen und Ereignisse beschränkt sind, die keine B2B-Entitäten enthalten. Bei B2B-Aktivierungsszenarien in nahezu Echtzeit sollten Sie Batch-bewertete B2B-Zielgruppen als Eingaben für Streaming- oder Edge-Zielgruppen verwenden, sofern unterstützt.

#### Experience Platform - Marketo Engage Source Connector

- Siehe die Dokumentation [hier](https://experienceleague.adobe.com/en/docs/experience-platform/sources/connectors/adobe-applications/marketo/marketo).

#### Experience Platform - Marketo-Ziel-Connector

- Siehe die Dokumentation [hier](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/adobe/marketo-engage-connection).

#### Ziel-Leitlinien

- Spezifische Anleitungen zu den einzelnen Zielen finden Sie in der Zieldokumentation: [Ziel-Leitplanken](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/guardrails).
- Stellen Sie bei Werbezielen wie Facebook, Google Customer Match &amp; DV360, Microsoft Bing, The Trade Desk, Amazon Ads, Bombora, Demandbase und anderen sicher, dass die Kennungen, die Sie in Ihrem Schema und Ihrer Identitätsstrategie auswählen (E-Mail, mobile Werbe-IDs, Adressfelder, Konto-IDs), mit den Zuordnungsfunktionen und unterstützten Identitäten für diese Ziele übereinstimmen.

## Implementierungsschritte

Anleitungen zur Implementierung und Konfiguration der B2B edition von Real-Time Customer Data Platform finden Sie in der Dokumentation zu Real-Time CDP B2B edition: [B2B edition von Real-Time Customer Data Platform](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/intro/rtcdpb2b-intro/b2b-overview).

Zwei Implementierungsmuster sind häufig:

- Nehmen Sie B2B-Daten und -Profile aus Marketo Engage (und dem zugehörigen CRM-System) in RTCDP B2B edition auf.
- Nehmen Sie B2B-Daten direkt aus CRM- oder anderen B2B-Systemen über die entsprechenden Quell-Connectoren in RTCDP B2B edition auf.

Im Rahmen der Upgrades der RTCDP B2B-Architektur werden einige zuvor verwendete Muster für B2B-Entitäten jetzt nicht mehr unterstützt. Weitere Informationen zu Datensätzen finden Sie in der detaillierten Dokumentation [hier](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/intro/rtcdpb2b-intro/b2b-architecture-upgrade).

## Überlegungen bei der Implementierung

Anleitung zu wichtigen Erwägungen und Konfigurationen der Blueprint.

- **CRM-Integration mit und ohne Marketo**

  - Wenn die Implementierung Marketo Engage als Quelle verwendet und Marketo Engage mit dem CRM verbunden ist, fließen CRM-Daten, die mit Marketo synchronisiert werden (z. B. Leads/Kontakte, Konten, Opportunities), über den Marketo-Quell-Connector in RTCDP B2B edition ein.
  - Wenn es zusätzliche CRM-Tabellen oder -Attribute gibt, die nicht über Marketo übergeben werden (z. B. benutzerdefinierte Objekte oder zusätzliche Felder), verbinden Sie die CRM-Quelle mithilfe der CRM-Quell-Connectoren direkt mit Experience Platform und ordnen Sie diese Tabellen den standardmäßigen B2B-Schemata und -Beziehungen zu.
  - Entwerfen Sie die Aufnahme in CRM und Marketo gemeinsam, um doppelte oder widersprüchliche Darstellungen von B2B-Entitäten in RTCDP B2B zu vermeiden und sicherzustellen, dass alle B2B-Entitäten den Standardschemata entsprechen.

## Verwandte Dokumentation

- [B2B edition von Real-Time Customer Data Platform](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/intro/rtcdpb2b-intro/b2b-overview)
- [Erste Schritte mit Real-Time Customer Data Platform B2B edition](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/intro/rtcdpb2b-intro/b2b-tutorial?lang=en)
- [Leitplanken für Real-Time Customer Data Platform B2B edition](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/intro/rtcdpb2b-intro/b2b-guardrails?lang=en)
- [Schemata in Real-Time Customer Data Platform B2B edition](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/schemas/b2b)
- [Architekturupgrades auf Real-Time CDP B2B edition](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/intro/rtcdpb2b-intro/b2b-architecture-upgrade)
- [Adobe Experience Platform](https://experienceleague.adobe.com/en/docs/experience-platform)
- [Marketo Engage](https://experienceleague.adobe.com/en/docs/marketo/using/home)
- [Adobe Experience Platform - Marketo Source Connector](https://experienceleague.adobe.com/en/docs/experience-platform/sources/connectors/adobe-applications/marketo/marketo)
- [Adobe Experience Platform - Marketo-Ziel-Connector](https://experienceleague.adobe.com/en/docs/marketo/using/product-docs/core-marketo-concepts/smart-lists-and-static-lists/static-lists/push-an-adobe-experience-platform-segment-to-a-marketo-static-list)
- [Ziel-Leitlinien](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/guardrails)
