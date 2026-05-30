---
title: Zielgruppen-Collaboration
description: Erfahren Sie, wie Sie Zielgruppensegmente mithilfe von Segment Match in Sandboxes oder Organisationen freigeben und abgleichen können.
solution: Real-Time Customer Data Platform, Experience Platform
exl-id: 7014849c-5e32-4ec3-a531-c0e8ce896f44
source-git-commit: 349d26f612d4002d1de3d27c7f893bd63ac467a3
workflow-type: tm+mt
source-wordcount: '1351'
ht-degree: 3%

---

# Zielgruppen-Collaboration

In diesem Handbuch wird das Anwendungsfallmuster für die Zusammenarbeit mit Zielgruppen beschrieben, bei dem [!DNL Segment Match] in [!DNL Real-Time CDP] und [!DNL Adobe Experience Platform] verwendet werden, um Zielgruppensegmente datenschutzsicher über Sandboxes oder Organisationen hinweg freizugeben und abzustimmen. Er wurde für Lösungsarchitekten, Marketing-Techniker und Implementierungstechniker entwickelt, die verstehen müssen, was dieses Muster bewirkt, welche Geschäftsziele es unterstützt, welche taktischen Anwendungsfälle es ermöglicht und welche Adobe-Anwendungen beteiligt sind.

[!DNL Segment Match] können zwei oder mehr [!DNL Experience Platform] (oder Sandboxes innerhalb einer Organisation) an Zielgruppendaten zusammenarbeiten, indem Informationen zur Segmentzugehörigkeit freigegeben werden, ohne die zugrunde liegenden personenbezogenen Daten offenzulegen. Die Teilnehmer können Überschneidungen schätzen, Audiences freigeben und übereinstimmende Profile für nachgelagerte Ziele aktivieren.

## Anwendungsfallmuster

Dieser Anwendungsfall folgt dem Audience Collaboration-Muster.

Freigeben und Abgleichen von Zielgruppensegmenten über Sandboxes oder Organisationen hinweg mithilfe von [!DNL Segment Match].

**Ausführungsplan:** Segmentauswahl > Übereinstimmungskonfiguration > Überschneidungsschätzung > Zielgruppenfreigabe > Aktivierung

## Anwendungsfall - Übersicht

Unternehmen müssen in zunehmendem Maße mit Partnern, Tochtergesellschaften oder über Geschäftsbereiche hinweg an Zielgruppendaten zusammenarbeiten, während gleichzeitig strenge Datenschutzkontrollen beibehalten werden. Die Zusammenarbeit mit Zielgruppen erfüllt diese Anforderung, indem sie die sichere Segmentfreigabe über [!DNL Segment Match] ermöglicht - eine Funktion in [!DNL Real-Time CDP], mit der zwei oder mehr [!DNL Experience Platform] Organisationen (oder Sandboxes) Informationen über die Zielgruppenzugehörigkeit mithilfe von gehashten, datenschutzsicheren Kennungen austauschen können.

Das Geschäftsszenario umfasst in der Regel eine Organisation (den Absender), die ein wertvolles Zielgruppensegment erstellt hat und dieses für eine Partnerorganisation (den Empfänger) freigeben möchte, um es gemeinsam anzusprechen, zu unterdrücken oder anzureichern. Vor der Freigabe können beide Parteien die Zielgruppenüberschneidung schätzen, um den Wert zu bewerten. Nach der Freigabe kann die empfangende Organisation die übereinstimmende Zielgruppe über ihre eigenen Ziele aktivieren.

Dieses Muster unterscheidet sich von der standardmäßigen Zielgruppenaktivierung, da es zwischen Organisationen oder Sandboxes und nicht zu externen Werbe- oder Marketing-Zielen funktioniert. Es unterscheidet sich auch von Data Clean Rooms oder Kollaborationsplattformen von Drittanbietern, da es nativ innerhalb des Adobe-Ökosystems unter Verwendung [!DNL Experience Platform] Identitätsinfrastruktur betrieben wird.

## Wichtige Geschäftsziele

Die folgenden Geschäftsziele werden durch dieses Anwendungsfallmuster unterstützt.

### Neue Kunden gewinnen

Erweitern Sie den Kundenstamm durch zielgerichtete Akquise-Kampagnen, Lookalike-Zielgruppen und Paid-Media-Optimierung. Die Zusammenarbeit mit Zielgruppen ermöglicht es Unternehmen, neue Interessentenpools zu entdecken, indem sie ihre Segmente mit den Partnerzielgruppen abgleichen, hochwertige Überschneidungen identifizieren und neue Kunden durch gemeinsame Aktivierung erreichen.

- **KPIs:** Neukunden, Kosten für Kundenakquise, Interessenten-/Lead-Konversion
- [Neue Kunden gewinnen](/help/blueprints/business-objectives/acquisition-growth/acquire-new-customers.md)

### Reduzierung der Kosten für die Kundenakquise

Verbessern Sie die Targeting-Effizienz, unterdrücken Sie Bestandskunden von Akquise-Kampagnen und optimieren Sie die Medienausgaben. Durch die gemeinsame Nutzung von Unterdrückungssegmenten in Unternehmen oder Geschäftsbereichen können Teams verschwendete Ausgaben für bereits konvertierte Kunden vermeiden und Budgets auf wirklich neue Interessenten konzentrieren.

- **KPIs:** Kosten für Kundenakquise, Kosten pro Lead, Effizienz
- [Reduzierung der Kosten für die Kundenakquise](/help/blueprints/business-objectives/cost-efficiency/reduce-customer-acquisition-cost.md)

### Marketing-Ausgaben und -ROI optimieren

Verbessern Sie den ROI Ihrer Marketing-Investitionen durch bessere Zielgruppenbestimmung, Attribution, Unterdrückung von Zielgruppen und Budgetzuweisung. [!DNL Segment Match] ermöglicht eine organisationsübergreifende Unterdrückung von Zielgruppen und ein gemeinsames Targeting, wodurch Duplikate reduziert und die Genauigkeit verbessert wird.

- **KPIs:** Kosteneinsparungen, Kosten für die Kundenakquise, inkrementelle Einnahmen
- [Marketing-Ausgaben und -ROI optimieren](/help/blueprints/business-objectives/cost-efficiency/optimize-marketing-spend-roi.md)

## Beispiele für taktische Anwendungsfälle

- **Zielgruppenvergleich zwischen Publisher und Advertiser** - Eine Marke teilt ihr hochwertiges Kundensegment mit einem Medienherausgeber, um Überschneidungen zu schätzen und abgestimmte Benutzende mit personalisierten Anzeigen anzusprechen, wodurch die Kampagnenrelevanz verbessert wird, ohne personenbezogene Daten offenzulegen.
- **Markenübergreifende Unterdrückung innerhalb einer Holdinggesellschaft** - Mehrere Marken unter einer übergeordneten Organisation teilen Kundensegmente, um bestehende Kunden von Schwestermarken aus Akquisitionskampagnen zu unterdrücken und so Werbeverschwendung zu reduzieren.
- **Zielgruppenerweiterung im Retail-**: Ein retailer teilt kaufbasierte Segmente mit CPG-Markenpartnern, sodass die Marken bewährte Käufer im retailer-Mediennetzwerk mit höheren Konversionsraten ansprechen können.
- **Co-Marketing-Partner-Zielgruppenfindung** - Zwei nicht konkurrierende Marken bewerten Zielgruppenüberschneidungen, um das Partnerschaftspotenzial zu bewerten, bevor eine gemeinsame Kampagne gestartet wird. Zur Validierung der Zielgruppenausrichtung wird eine Überschneidungsschätzung verwendet.
- **Datenkooperative Segmentfreigabe**: Organisationen in einer Datenkooperative teilen gehashte Zielgruppensegmente, um die Zielgruppenreichweite zu erweitern und gleichzeitig die Einhaltung von Datenschutzbestimmungen und Data Governance-Kontrollen zu gewährleisten.
- **Multi-Sandbox Audience Federation** - Ein globales Unternehmen teilt Zielgruppensegmente über regionale Sandboxes hinweg, um eine konsistente Zielgruppenbestimmung auf verschiedenen Märkten zu ermöglichen und gleichzeitig die regionalen Anforderungen an den Datenwohnsitz zu erfüllen.
- **Partnerübergreifende Aktivierung des Treueprogramms** - Eine Treuekonalition teilt Treuestufensegmente mit teilnehmenden Händlern, sodass jeder Partner dem gemeinsamen Kundenstamm geeignete Werbeaktionen anbieten kann.
- **Zusammenarbeit bei Messung und Attribution** - Ein Werbetreibender gibt ein Konversionssegment an einen Medienpartner weiter, damit der Partner die Kampagneneffektivität messen kann, indem er exponierte Benutzende mit Konvertern abgleicht.

## Wichtige Performance-Indikatoren

Die folgenden KPIs helfen, den Erfolg von Implementierungen der Audience-Zusammenarbeit zu messen.

| KPI | Beschreibung | Messansatz |
| --- | --- | --- |
| Rate der Zielgruppenüberschneidungen | Prozentsatz der Profile im freigegebenen Segment, die zwischen Absender und Empfänger übereinstimmen | Bericht [!DNL Segment Match] Überschneidungsschätzung |
| Übereinstimmende Zielgruppengröße | Anzahl der Profile, die erfolgreich abgeglichen wurden und für die Aktivierung verfügbar sind | [!DNL Segment Match] Freigabestatus und Anzahl der Zielgruppen |
| Neue Kundenakquise durch übereinstimmende Zielgruppen | Neue Kunden durch Kampagnen gewinnen, die auf übereinstimmende Segmente abzielen | Konversionsverfolgung bei Kampagnen mit übereinstimmenden Audiences |
| Reduzierung der Kundenakquisitionskosten | Kostensenkung pro Akquise bei Verwendung abgeglichener Zielgruppen im Vergleich zum breiten Targeting | Analyse der Kampagnenkosten beim Vergleich von übereinstimmenden und nicht übereinstimmenden Zielgruppen |
| Einsparungen durch Unterdrückung | Durch die Unterdrückung bekannter Kunden aus Akquise-Kampagnen eingesparte Medienausgaben | Vergleich der Medienausgaben vor/nach der Unterdrückung |
| Leistungssteigerung bei Kampagnen | Verbesserung der Konversionsrate, Klickrate oder Interaktion für Kampagnen, die übereinstimmende Audiences verwenden | A/B-Test zum Vergleich von übereinstimmenden Zielgruppenkampagnen mit Kontrolle |
| Zeit bis Collaboration | Verstrichene Zeit von der Initiierung der Segmentfreigabe bis zur Aktivierungsbereitschaft | [!DNL Segment Match] Workflow-Zeitstempel |

## Programme

Die folgenden Anwendungen werden in diesem Anwendungsfallmuster verwendet.

- **[!DNL Real-Time CDP]** - Bietet die [!DNL Segment Match] für die datenschutzfreundliche Freigabe von Zielgruppen, die Evaluierung von Zielgruppen für die Segmenterstellung und die Zielaktivierung für die nachgelagerte Verwendung übereinstimmender Zielgruppen.
- **[!DNL Adobe Experience Platform]** - Bietet die grundlegende Dateninfrastruktur, einschließlich Identitätsauflösung, Profilvereinheitlichung, Data Governance und Einverständnisdurchsetzung, von der [!DNL Segment Match] abhängt.

## Verwandte Dokumentation

Die folgenden Ressourcen bieten zusätzliche Details zu den in diesem Anwendungsfallmuster verwendeten Funktionen.

### [!DNL Segment Match]

- [Übersicht zu Segment Match](https://experienceleague.adobe.com/de/docs/experience-platform/segmentation/ui/segment-match/overview)
- [Fehlerbehebung bei Segment Match](https://experienceleague.adobe.com/de/docs/experience-platform/segmentation/ui/segment-match/troubleshooting)

### Segmentierung und Audiences

- [Übersicht über den Segmentierungs-Service](https://experienceleague.adobe.com/de/docs/experience-platform/segmentation/home)
- [Handbuch zur Benutzeroberfläche von Segment Builder](https://experienceleague.adobe.com/de/docs/experience-platform/segmentation/ui/segment-builder)
- [Zielgruppenkomposition - Übersicht](https://experienceleague.adobe.com/de/docs/experience-platform/segmentation/ui/audience-composition)
- [Profile Query Language-Referenz](https://experienceleague.adobe.com/de/docs/experience-platform/segmentation/pql/overview)
- [Streaming-Segmentierung](https://experienceleague.adobe.com/de/docs/experience-platform/segmentation/methods/streaming-segmentation)
- [Edge-Segmentierung](https://experienceleague.adobe.com/de/docs/experience-platform/segmentation/methods/edge-segmentation)

### Identität und Profil

- [Identity Service - Übersicht](https://experienceleague.adobe.com/de/docs/experience-platform/identity/home)
- [Übersicht über Identity-Namespaces](https://experienceleague.adobe.com/de/docs/experience-platform/identity/features/namespaces)
- [Übersicht über Zusammenführungsrichtlinien](https://experienceleague.adobe.com/de/docs/experience-platform/profile/merge-policies/overview)
- [Übersicht über das Echtzeit-Kundenprofil](https://experienceleague.adobe.com/de/docs/experience-platform/profile/home)

### Data Governance und Einverständnis

- [Übersicht zur Daten-Governance](https://experienceleague.adobe.com/de/docs/experience-platform/data-governance/home)
- [Datennutzungs-Labels – Überblick](https://experienceleague.adobe.com/de/docs/experience-platform/data-governance/labels/overview)
- [Durchsetzung von Richtlinien](https://experienceleague.adobe.com/de/docs/experience-platform/data-governance/enforcement/overview)
- [Einverständnis und Einstellungen](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/consent/adobe/overview)
- [Feldgruppe „Einverständnis und Voreinstellungen“](https://experienceleague.adobe.com/de/docs/experience-platform/xdm/field-groups/profile/consents)

### Ziele und Aktivierung

- [Übersicht über Ziele](https://experienceleague.adobe.com/de/docs/experience-platform/destinations/home)
- [Zielkatalog](https://experienceleague.adobe.com/de/docs/experience-platform/destinations/catalog/overview)
- [Überwachen von Datenflüssen für Ziele](https://experienceleague.adobe.com/de/docs/experience-platform/dataflows/ui/monitor-destinations)

### Datenmodellierung und Schema

- [XDM-Systemübersicht](https://experienceleague.adobe.com/de/docs/experience-platform/xdm/home)
- [Grundlagen der Schemakomposition](https://experienceleague.adobe.com/de/docs/experience-platform/xdm/schema/composition)

### Verwaltung und Zugriffskontrolle

- [Zugriffskontrolle - Übersicht](https://experienceleague.adobe.com/de/docs/experience-platform/access-control/home)
- [Sandbox-Übersicht](https://experienceleague.adobe.com/de/docs/experience-platform/sandbox/home)

### Überwachung und Beobachtbarkeit

- [Warnhinweise - Übersicht](https://experienceleague.adobe.com/de/docs/experience-platform/observability/alerts/overview)
- [Observability Insights - Übersicht](https://experienceleague.adobe.com/de/docs/experience-platform/observability/home)

### Leitlinien

- [Leitplanken für Echtzeit-Kundenprofile](https://experienceleague.adobe.com/de/docs/experience-platform/profile/guardrails)
- [Schutzmaßnahmen bei der Segmentierung](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/guardrails)
- [Aktivierungsleitplanken](https://experienceleague.adobe.com/de/docs/experience-platform/destinations/guardrails)

### Tutorials

- [Erstellen eines Schemas](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/tutorials/union-schema)
- [Aktivieren eines Datensatzes für Profil](https://experienceleague.adobe.com/de/docs/experience-platform/catalog/datasets/enable-for-profile)
