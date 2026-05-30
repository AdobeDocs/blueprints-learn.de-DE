---
title: Zielgruppenaktivierung für Ziele
description: Erfahren Sie, wie Sie Zielgruppensegmente mithilfe von Adobe Real-Time CDP für das Targeting oder die Unterdrückung auswerten und für externe Ziele veröffentlichen können.
solution: Real-Time Customer Data Platform, Experience Platform
exl-id: b0b9d937-45d2-48f9-ac4c-3611c6e35f58
source-git-commit: 349d26f612d4002d1de3d27c7f893bd63ac467a3
workflow-type: tm+mt
source-wordcount: '1365'
ht-degree: 4%

---

# Zielgruppenaktivierung für Ziele

In diesem Handbuch wird das Anwendungsfallmuster für die Zielgruppenaktivierung für Ziele beschrieben, das Zielgruppensegmente in Adobe [!DNL Real-Time Customer Data Platform] (RT-CDP) auswertet und auf Anzeigenplattformen, Cloud-Speichern, CRM-Systemen oder Datenpartnern veröffentlicht, um sie für Targeting, Unterdrückung, Lookalike-Modellierung oder Analytics-Anreicherung zu verwenden. Er wurde für Lösungsarchitekten, Marketing-Techniker und Implementierungstechniker entwickelt, die verstehen müssen, was dieses Muster bewirkt, welche Geschäftsziele es unterstützt, welche taktischen Anwendungsfälle es ermöglicht und welche Adobe-Anwendungen beteiligt sind.

Dieses Muster deckt den gesamten Lebenszyklus der Zielgruppenaktivierung ab - von der Definition und Bewertung von Zielgruppensegmenten über die Konfiguration von Zielverbindungen und die Veröffentlichung von Zielgruppen bis hin zur Überwachung des Aktivierungszustands und zur Durchsetzung der Governance-Compliance.

## Anwendungsfallmuster

**Audience Activation für Ziele** — Auswerten und Veröffentlichen eines Zielgruppensegments für externe Ziele zum Targeting oder zur Unterdrückung.

**Ausführungsplan:** Zielgruppenevaluierung > Zielkonfiguration > Audience Activation > Überwachung

## Anwendungsfall - Übersicht

Unternehmen müssen Zielgruppendaten an externe Systeme senden, um Kampagnen mit bezahlten Medien zu unterstützen, CRM-Datensätze anzureichern, Daten mit Partnern auszutauschen oder nachgelagerte Analysen zu nutzen. Audience Activation to Destinations ist das grundlegende Aktivierungsmuster in RT-CDP: Es bewertet, welche Profile für eine Zielgruppe qualifiziert sind, stellt eine Verbindung zu einem oder mehreren externen Zielen her, ordnet Profilattribute zielspezifischen Feldern zu und veröffentlicht die Zielgruppe für die nachgelagerte Nutzung.

Dieses Muster gilt immer dann, wenn das Ziel darin besteht, Zielgruppendaten zum richtigen Zeitpunkt in einem externen System im richtigen Format abzurufen. Sie umfasst keinen Nachrichtenversand, keine Personalisierung vor Ort und keine Analysen. Es ist der häufigste Ausgangspunkt für RT-CDP-Implementierungen und dient als Baustein, den andere Muster aufbauen.

Zu den typischen Stakeholdern gehören Teams für digitales Marketing, die bezahlte Medien verwalten, Daten-Teams, die Warehouses anreichern, CRM-Teams, die Kontaktlisten für Kampagnen vorbereiten, und Datenschutz-Teams, die die Einhaltung von Governance-Richtlinien bei ausgehenden Datenflüssen sicherstellen.

>[!NOTE]
>Wenn Ihr Unternehmen [!DNL Real-Time CDP] B2B edition verwendet und für kontobasierte Ziele aktiviert, finden Sie weitere Informationen unter [B2B-Zielgruppenaktivierung](../b2b/account-audience-activation.md). Dieses Muster verwendet dieselbe Aktivierungsmechanik, verwendet jedoch ein B2B-Konto-und-Person-Datenmodell und erfordert eine B2B edition-Lizenz.

## Wichtige Geschäftsziele

Die folgenden Geschäftsziele werden durch dieses Anwendungsfallmuster unterstützt.

### Neue Kunden gewinnen

Erweitern Sie den Kundenstamm durch zielgerichtete Akquise-Kampagnen, Lookalike-Zielgruppen und Paid-Media-Optimierung.

**KPIs:** Neukunden, Kosten für Kundenakquise, Interessenten-/Lead-Konversion

[Weitere Informationen über die Akquise von Neukunden](/help/blueprints/business-objectives/acquisition-growth/acquire-new-customers.md)

### Reduzierung der Kosten für die Kundenakquise

Verbessern Sie die Targeting-Effizienz, unterdrücken Sie Bestandskunden von Akquise-Kampagnen und optimieren Sie die Medienausgaben.

**KPIs:** Kosten für Kundenakquise, Kosten pro Lead, Effizienz

[Erfahren Sie mehr über die Reduzierung der Kundenakquisitionskosten](/help/blueprints/business-objectives/cost-efficiency/reduce-customer-acquisition-cost.md)

### Marketing-Ausgaben und -ROI optimieren

Verbessern Sie den ROI Ihrer Marketing-Investitionen durch bessere Zielgruppenbestimmung, Attribution, Unterdrückung von Zielgruppen und Budgetzuweisung.

**KPIs:** Kosteneinsparungen, Kosten für die Kundenakquise, inkrementelle Einnahmen

[Erfahren Sie mehr über die Optimierung von Marketing-Ausgaben und ROI](/help/blueprints/business-objectives/cost-efficiency/optimize-marketing-spend-roi.md)

## Beispiele für taktische Anwendungsfälle

- **Zielgruppen-Targeting der Anzeigenplattform** — Pushen Sie qualifizierte Segmente auf Paid-Media-Plattformen für das Kampagnen-Targeting
- **Bezahlte Medienunterdrückung bestehender Kunden** - Schließen Sie bekannte Kunden von Akquise-Kampagnen auf Werbeplattformen aus, um verschwendete Ausgaben zu vermeiden.
- **Lookalike-Seed-Zielgruppen** - Übertragen Sie hochwertige Kundensegmente als Seed-Zielgruppen für die Lookalike-Erweiterung an Facebook, Google Ads oder The Trade Desk
- **CRM-Synchronisation für die Sales-Aktivierung** — Aktivieren Sie Zielgruppen mit hohen Absichten oder hohem Wert, damit Vertriebsteams die Kontaktaufnahme priorisieren können
- **Audience-Freigabe durch Datenpartner** — Teilen Sie qualifizierte Audience-Segmente mit Datenpartnern für das Co-op-Targeting oder die Messung
- **Cloud-Speicherexport zur Data Warehouse-Anreicherung** - Exportieren Sie Zielgruppenzugehörigkeit und Profilattribute für nachgelagerte Analysen in Amazon S3, Azure Blob, Google Cloud Storage oder SFTP
- **Aktivierung der Retargeting-Zielgruppe** — Aktivieren Sie Website-Besucher, die nicht zu Retargeting-Plattformen konvertiert wurden
- **Synchronisierung der Kontaktliste mit E-Mail-**: Pushen der Zielgruppenzugehörigkeit auf E-Mail-Plattformen von Drittanbietern, um eine koordinierte Kontaktaufnahme zu ermöglichen

## Wichtige Performance-Indikatoren

| KPI | Beschreibung | Messansatz |
| --- | --- | --- |
| Kosten für Kundenakquise (CAC) | Kosten für die Akquise eines neuen Kunden über aktivierte Zielgruppen | Gesamtausgaben für Medien/neue Kunden, die aktivierten Zielgruppen zugeordnet wurden |
| Übereinstimmungsrate der Zielgruppe | Prozentsatz der aktivierten Profile, die am Ziel erfolgreich abgeglichen wurden | Am Ziel übereinstimmende Profile/aus RT-CDP exportierte Profile |
| Einsparungen durch Unterdrückung | Medienausgaben werden vermieden, indem Bestandskunden von Akquise-Kampagnen unterdrückt werden | Geschätzte Größe von CPM x unterdrückter Zielgruppe |
| Aktivierungsrate | Prozentsatz der erfolgreich an das Ziel zugestellten Profile | Bereitgestellte Profile/Profile in der Quell-Audience |
| Zeit bis zur Aktivierung | Verstrichene Zeit von der Zielgruppendefinition bis zum ersten Versand am Ziel | Messung von der Segmenterstellung bis zur ersten bestätigten Datenflussausführung |
| Genauigkeit der Zielgruppenpopulation | Abstimmung zwischen erwarteten und tatsächlichen Zielgruppengrößen am Ziel | Ziel-Zielgruppengröße/RT-CDP-Zielgruppengröße |

## Programme

- **Adobe [!DNL Real-Time Customer Data Platform] (RT-CDP)** - Zielgruppenbewertung, Zielverwaltung, Zielgruppenaktivierung, Einverständnis und Durchsetzung der Governance
- **Adobe [!DNL Experience Platform] (AEP)** - Profilspeicher, Identity Service, Segmentierungs-Engine, Data Governance

## Architektur

Die folgende Referenzarchitektur veranschaulicht, wie Zielgruppen- und Profildaten von Real-Time CDP zu Unternehmenszielen fließen, einschließlich Cloud-Speicher, Streaming-Endpunkten und SaaS-Programmen.

![Referenzarchitektur für Zielgruppen- und Profilaktivierung für Unternehmensziele](/help/blueprints/audience-activation/assets/known_activation.png)

## Verwandte Dokumentation

**Ziele**

- [Übersicht über Ziele](https://experienceleague.adobe.com/de/docs/experience-platform/destinations/home)
- [Zielkatalog](https://experienceleague.adobe.com/de/docs/experience-platform/destinations/catalog/overview)
- [Aktivieren von Zielgruppen für Streaming-Ziele](https://experienceleague.adobe.com/de/docs/experience-platform/destinations/ui/activate/activate-segment-streaming-destinations)
- [Aktivieren von Zielgruppen für Batch-Profil-Exportziele](https://experienceleague.adobe.com/de/docs/experience-platform/destinations/ui/activate/activate-batch-profile-destinations)
- [Zielgruppen bei Bedarf für Batch-Ziele aktivieren](https://experienceleague.adobe.com/de/docs/experience-platform/destinations/api/ad-hoc-activation-api)
- [Leitplanken für Ziele](https://experienceleague.adobe.com/de/docs/experience-platform/destinations/guardrails)
- [Übersicht über Destination SDK](https://experienceleague.adobe.com/de/docs/experience-platform/destinations/destination-sdk/overview)

**Zielgruppen und Segmentierung**

- [Übersicht über den Segmentierungs-Service](https://experienceleague.adobe.com/de/docs/experience-platform/segmentation/home)
- [Handbuch zur Benutzeroberfläche von Segment Builder](https://experienceleague.adobe.com/de/docs/experience-platform/segmentation/ui/segment-builder)
- [Profile Query Language-Referenz](https://experienceleague.adobe.com/de/docs/experience-platform/segmentation/pql/overview)
- [Streaming-Segmentierung](https://experienceleague.adobe.com/de/docs/experience-platform/segmentation/methods/streaming-segmentation)
- [Edge-Segmentierung](https://experienceleague.adobe.com/de/docs/experience-platform/segmentation/methods/edge-segmentation)
- [Zielgruppenkomposition - Übersicht](https://experienceleague.adobe.com/de/docs/experience-platform/segmentation/ui/audience-composition)
- [Schutzmaßnahmen bei der Segmentierung](https://experienceleague.adobe.com/de/docs/experience-platform/profile/guardrails)

**Identität und Profil**

- [Identity Service - Übersicht](https://experienceleague.adobe.com/de/docs/experience-platform/identity/home)
- [Übersicht über Identity-Namespaces](https://experienceleague.adobe.com/de/docs/experience-platform/identity/features/namespaces)
- [Verknüpfungsregeln für Identitätsdiagramme](https://experienceleague.adobe.com/de/docs/experience-platform/identity/features/identity-linking-logic)
- [Profilübersicht](https://experienceleague.adobe.com/de/docs/experience-platform/profile/home)
- [Übersicht über Zusammenführungsrichtlinien](https://experienceleague.adobe.com/de/docs/experience-platform/profile/merge-policies/overview)

**Datenmodellierung und Schemata**

- [XDM-Systemübersicht](https://experienceleague.adobe.com/de/docs/experience-platform/xdm/home)
- [Grundlagen der Schemakomposition](https://experienceleague.adobe.com/de/docs/experience-platform/xdm/schema/composition)

**Data Governance**

- [Übersicht zur Daten-Governance](https://experienceleague.adobe.com/de/docs/experience-platform/data-governance/home)
- [Datennutzungs-Labels – Überblick](https://experienceleague.adobe.com/de/docs/experience-platform/data-governance/labels/overview)
- [Data Governance-Richtlinien](https://experienceleague.adobe.com/de/docs/experience-platform/data-governance/policies/overview)
- [Durchsetzung von Richtlinien](https://experienceleague.adobe.com/de/docs/experience-platform/data-governance/enforcement/overview)
- [Einverständnis und Einstellungen](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/consent/adobe/overview)

**Überwachung und Beobachtbarkeit**

- [Überwachen von Datenflüssen für Ziele](https://experienceleague.adobe.com/de/docs/experience-platform/dataflows/ui/monitor-destinations)
- [Warnhinweise - Übersicht](https://experienceleague.adobe.com/de/docs/experience-platform/observability/alerts/overview)
- [Observability Insights - Übersicht](https://experienceleague.adobe.com/de/docs/experience-platform/observability/home)
- [Lizenznutzungs-Dashboard](https://experienceleague.adobe.com/en/docs/experience-platform/landing/license-usage-and-guardrails/license-usage-dashboard)

**Berechnete Attribute**

- [Berechnete Attribute - Übersicht](https://experienceleague.adobe.com/de/docs/experience-platform/profile/computed-attributes/overview)
- [Handbuch zur Benutzeroberfläche für berechnete Attribute](https://experienceleague.adobe.com/de/docs/experience-platform/profile/computed-attributes/ui)

**Datenerfassung und Quellen**

- [Überblick über Quellen](https://experienceleague.adobe.com/de/docs/experience-platform/sources/home)
- [Übersicht über Web SDK](https://experienceleague.adobe.com/de/docs/experience-platform/web-sdk/home)
- [Konfigurieren von Datenströmen](https://experienceleague.adobe.com/de/docs/experience-platform/datastreams/configure)

**Administration**

- [Sandbox-Übersicht](https://experienceleague.adobe.com/de/docs/experience-platform/sandbox/home)
- [Zugriffskontrolle - Übersicht](https://experienceleague.adobe.com/de/docs/experience-platform/access-control/home)
- [Attributbasierte Zugriffssteuerung](https://experienceleague.adobe.com/de/docs/experience-platform/access-control/abac/overview)

**Leitplanken**

- [Leitplanken für Echtzeit-Kundenprofile](https://experienceleague.adobe.com/de/docs/experience-platform/profile/guardrails)
- [Leitplanken für Identity Service](https://experienceleague.adobe.com/de/docs/experience-platform/identity/guardrails)
- [Aktivierungsleitplanken](https://experienceleague.adobe.com/de/docs/experience-platform/destinations/guardrails)
- [Schutzmaßnahmen bei der Aufnahme](https://experienceleague.adobe.com/de/docs/experience-platform/ingestion/guardrails)
