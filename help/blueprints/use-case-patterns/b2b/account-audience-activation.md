---
title: B2B-Audience Activation
description: Erfahren Sie, wie Sie Account-basierte B2B-Zielgruppen über Web-, E-Mail- und Werbekanäle aktivieren.
solution: Real-Time Customer Data Platform
exl-id: 2b979159-37aa-41d4-a6b4-1105538f6546
source-git-commit: 349d26f612d4002d1de3d27c7f893bd63ac467a3
workflow-type: tm+mt
source-wordcount: '1540'
ht-degree: 2%

---

# B2B-Zielgruppenaktivierung

In diesem Handbuch wird das Anwendungsfallmuster für die B2B-Zielgruppenaktivierung beschrieben, bei dem [!DNL Adobe Real-Time Customer Data Platform] ([!DNL RT-CDP]) B2B edition verwendet wird, um Zielgruppen auf Kontoebene über Web-, E-Mail-, Werbe- und CRM-Kanäle zu erstellen, zu bewerten und zu aktivieren. Er wurde für Lösungsarchitekten, Marketing-Techniker und Implementierungstechniker entwickelt, die verstehen müssen, was dieses Muster bewirkt, welche Geschäftsziele es unterstützt, welche taktischen Anwendungsfälle es ermöglicht und welche Adobe-Anwendungen beteiligt sind.

Dieses Muster deckt den gesamten Lebenszyklus ab - von der Vereinheitlichung von Account-Profilen über die Bewertung und Aktivierung von Audiences bis hin zu B2B-spezifischen Zielen wie [!DNL Marketo Engage]-, [!DNL LinkedIn]- und CRM-Systemen.

## Anwendungsfallmuster

**B2B-Zielgruppenaktivierung**

Account-basierte B2B-Zielgruppen über Web-, E-Mail- und Werbekanäle aktivieren.

**Ausführungsplan:** Kontoprofilanreicherung > Kontozielgruppenbewertung > Zielkonfiguration > Audience Activation > Überwachung

## Anwendungsfall - Übersicht

B2B-Marketing-Teams müssen Zielgruppen auf Kontoebene und nicht auf der Ebene einzelner Personen ansprechen und aktivieren. Im Gegensatz zur B2C-Zielgruppenaktivierung, bei der die Zielgruppenbestimmungseinheit ein einzelnes Kundenprofil ist, erfordert die B2B-Zielgruppenaktivierung, dass Sie die Beziehung zwischen Personen und den Konten, zu denen sie gehören, verstehen, die Zielgruppenzugehörigkeit auf der Grundlage von Attributen auf Kontoebene in Kombination mit Interaktionssignalen auf Personenebene bewerten und diese Zielgruppen an Ziele bereitstellen, die Account-basiertes Targeting unterstützen.

[!DNL RT-CDP] B2B edition erweitert die [!DNL Real-Time Customer Data Platform] um spezielle XDM-Klassen für Konten, Opportunitys und Kampagnen sowie eine B2B-Identitätsauflösung, die Person-zu-Account-Beziehungen zuordnet. Dadurch können Marketing-Experten Account-Zielgruppen erstellen, die firmografische Daten (Branche, Umsatz, Mitarbeiteranzahl), technische Daten (Technologie-Stack, Produktnutzung) und Verhaltensdaten (Web-Besuche, E-Mail-Interaktion, Ereignisteilnahme) der mit diesen Accounts verknüpften Personen kombinieren.

Die aktivierten Account-Zielgruppen ermöglichen Anwendungsfälle für die Nachfragegenerierung in funnel: Top-of-funnel-Awareness-Kampagnen zu [!DNL LinkedIn] und Display-Werbung, Mid-funnel-Nurture-Programme in [!DNL Marketo Engage] und funnel-Verkaufsförderung auf unterster Ebene durch CRM-Integration. Zielgruppen zur Kontounterdrückung verhindern verschwendete Ausgaben, indem bestehende Kunden, abgeschlossene Konten oder Konten, die sich bereits in aktiven Verkaufszyklen befinden, ausgeschlossen werden.

>[!NOTE]
>Wenn Ihr Anwendungsfall die Aktivierung von Zielgruppen auf Personenebene (B2C) statt auf Kontoebene beinhaltet, finden Sie weitere Informationen unter [Zielgruppenaktivierung für Ziele](../audience-building-activation/audience-activation-to-destinations.md). Dieses Muster verwendet das standardmäßige RT-CDP-Datenmodell und erfordert keine B2B edition.

## Wichtige Geschäftsziele

Die folgenden Geschäftsziele werden durch dieses Anwendungsfallmuster unterstützt.

### Lead-Generierung erhöhen

Generieren Sie durch Formulare, Ereignisse, Inhalte und kanalübergreifende Interaktionen besser qualifizierte Leads für die Vertriebs-Pipeline.

**KPIs:** Interessenten, Kosten pro Lead, Lead-Konversion

[Weitere Informationen zur Steigerung der Lead-Generierung](/help/blueprints/business-objectives/acquisition-growth/increase-lead-generation.md)

### Verbessern der Lead-Qualifizierung und -Konversion

Erhöhen Sie die Lead-Qualität und beschleunigen Sie den Pipeline-Fortschritt durch Bewertung, Pflege und personalisierte Nachverfolgung.

**KPIs:** Lead-Konversion, Interessenten-/Lead-Konversion, Effizienz

[Erfahren Sie mehr über die Verbesserung der Lead-Qualifizierung und -Konversion](/help/blueprints/business-objectives/qualification-sales-b2b/improve-lead-qualification-conversion.md)

### Neue Kunden gewinnen

Erweitern Sie den Kundenstamm durch zielgerichtete Akquise-Kampagnen, Lookalike-Zielgruppen und Paid-Media-Optimierung.

**KPIs:** Neukunden, Kosten für Kundenakquise, Interessenten-/Lead-Konversion

[Weitere Informationen über die Akquise von Neukunden](/help/blueprints/business-objectives/acquisition-growth/acquire-new-customers.md)

### Marketing-Ausgaben und -ROI optimieren

Verbessern Sie den ROI Ihrer Marketing-Investitionen durch bessere Zielgruppenbestimmung, Attribution, Unterdrückung von Zielgruppen und Budgetzuweisung.

**KPIs:** Kosteneinsparungen, Kosten für die Kundenakquise, inkrementelle Einnahmen

[Erfahren Sie mehr über die Optimierung von Marketing-Ausgaben und ROI](/help/blueprints/business-objectives/cost-efficiency/optimize-marketing-spend-roi.md)

## Beispiele für taktische Anwendungsfälle

Die folgenden Szenarien veranschaulichen, wie dieses Muster in der Praxis angewendet werden kann.

- **Account-based Advertising on[!DNL LinkedIn]** - Targeting von Accounts, die Ihrem Idealkundenprofil (ICP) entsprechen, mit gesponserten Inhalten und InMail-Kampagnen auf [!DNL LinkedIn], unter Verwendung von Account-Listen, die von [!DNL RT-CDP] B2B edition aktiviert werden
- Zielgruppenbestimmung **[!DNL Marketo Engage]Nurture-**: Aktivieren Sie Account-Zielgruppen, um [!DNL Marketo Engage] verknüpfte Leads und Kontakte basierend auf Qualifizierungskriterien auf Account-Ebene für die gezielte Pflege zu registrieren
- **Synchronisation der CRM-**: Übertragen von Listen qualifizierter Konten an [!DNL Salesforce] oder [!DNL Microsoft Dynamics], um die Sichtbarkeit des Vertriebsteams, die Gebietszuweisung und die Workflows für ausgehende Kundenakquise zu gewährleisten
- **Kontounterdrückung für bezahlte Medien** - Unterdrückt bestehende Kunden, abgeschlossene Konten oder Konten in aktiven Verkaufszyklen von Paid-Akquise-Kampagnen, um verschwendete Ausgaben zu reduzieren
- **Absichtsbasiertes Konto-Targeting** - Kombinieren Sie Absichtssignale von Drittanbietern mit Interaktionsdaten von Erstanbietern auf Kontoebene, um Zielgruppen von marktinternen Konten zu identifizieren und zu aktivieren
- **Produkt-Crosssell an vorhandene Konten** - Erstellen Sie Zielgruppen von Konten mit einer Produktlinie, aber nicht mit einer anderen, und aktivieren Sie dann E-Mail- und Werbekanäle für Crosssell-Kampagnen
- **Ereignis- und Webinar-Targeting** - Aktivieren Sie Konto-Zielgruppen für Werbe- und E-Mail-Kanäle, um die Ereignisregistrierung von Zielkonten aus zu fördern
- **Wettbewerbsverdrängungskampagnen** - Targeting von Accounts unter Verwendung von Produkten von Mitbewerbern mit maßgeschneidertem Messaging, das über Werbe- und E-Mail-Kanäle aktiviert wird
- **Mehrstufige Kontointeraktion** - Segmentieren Sie Konten in Interaktionsstufen (hoch, mittel, niedrig) basierend auf aggregierter Aktivität auf Personenebene und aktivieren Sie für jede Stufe differenzierte Kampagnen
- **Partner-Co-Marketing-Zielgruppen** - Teilen Sie Account-Zielgruppensegmente mit Channel-Partnern oder Co-Marketing-Programmen über Cloud-Speicher-Ziele

## Wichtige Performance-Indikatoren

Die folgenden KPIs helfen, den Erfolg dieses Anwendungsfallmusters zu messen.

| KPI | Beschreibung | Messansatz |
| --- | --- | --- |
| Kontoreichweite | Anzahl der über Aktivierungskanäle hinweg erreichten Zielkonten | Tracking der pro Ziel aktivierten eindeutigen Konten |
| Kundeninteraktionsrate | Prozentsatz der aktivierten Konten mit Interaktionssignalen | Interaktion auf Personenebene aggregiert mit Konto messen |
| Pipeline-Einfluss | Umsatz-Pipeline, die Account-basierten Aktivierungskampagnen zugeordnet wurde | Verfolgen von mit aktivierten Account-Zielgruppen erstellten Opportunitys |
| Kosten pro engagiertem Konto | Marketingausgaben geteilt durch die Anzahl der Konten, die Interaktion anzeigen | Berechnung der Kosten für Werbung und E-Mail-Kanal |
| Lead-Konversionsrate | Prozentsatz der Leads von aktivierten Konten, die in Opportunities konvertiert wurden | Konversion von Lead zu Opportunity für aktivierte Zielgruppen verfolgen |
| Einsparungen bei der Zielgruppenunterdrückung | Durch Unterdrückung nicht förderfähiger Konten aus bezahlten Kampagnen vermiedene Kosten | Ausgabenreduzierung aus Unterdrückungszielgruppen messen |
| Account Coverage | Prozentsatz des gesamten adressierbaren Marktes (TAM), der von aktivierten Zielgruppen abgedeckt wird | Vergleichen aktivierter Konten mit dem gesamten ICP-Universum |

## Programme

Die folgenden Anwendungen werden verwendet, um dieses Anwendungsfallmuster zu implementieren.

- **[!DNL Real-Time CDP]B2B edition** - Kernplattform für die Vereinheitlichung von Account-Profilen, B2B-Identitätsauflösung, Evaluierung der Account-Zielgruppe, B2B-spezifische Zielkonfiguration und Aktivierung der Account-Zielgruppe
- **[!DNL Adobe Experience Platform](AEP)** - Grundlegende Infrastruktur für B2B-XDM-Datenmodellierung, Datenaufnahme aus CRM- und Marketing-Automatisierungsquellen, Identity Service und Governance
- **[!DNL Marketo Engage]** - Primäres B2B-Marketing-Automatisierungsziel für Lead-Nurture-Programme, Scoring und Kampagnenausführung, die von aktivierten Account-Zielgruppen gespeist werden

## Verwandte Dokumentation

Die folgenden Ressourcen bieten zusätzlichen Kontext und detaillierte Anleitungen für die in diesem Anwendungsfallmuster verwendeten Funktionen.

**[!DNL RT-CDP]B2B edition**

- [Übersicht über Real-Time CDP B2B edition](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/overview#rtcdp-b2b)
- [B2B-Schemata in Real-Time CDP](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/schemas/b2b)
- [Konto-Zielgruppen](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/types/account-audiences)
- [RT-CDP B2B edition - Produktbeschreibung](https://helpx.adobe.com/legal/product-descriptions/real-time-customer-data-platform-b2b-edition-prime-and-ultimate-packages.html)

**Zielgruppenauswertung und Segmentierung**

- [Übersicht über den Segmentierungs-Service](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/home)
- [Handbuch zur Benutzeroberfläche von Segment Builder](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-builder)
- [Audience-Komposition](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/audience-composition)
- [Streaming-Segmentierung](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/streaming-segmentation)
- [Schutzmaßnahmen bei der Segmentierung](https://experienceleague.adobe.com/en/docs/experience-platform/profile/guardrails)

**Ziele und Aktivierung**

- [Übersicht über Ziele](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/home)
- [Zielkatalog](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/overview)
- [Marketo Engage-Ziel](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/adobe/marketo-engage)
- [Ziel für abgeglichene LinkedIn-Zielgruppen](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/social/linkedin)
- [Salesforce CRM-Ziel](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/crm/salesforce)
- [Microsoft Dynamics 365-Ziel](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/crm/microsoft-dynamics-365)
- [Amazon S3-Ziel](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/cloud-storage/amazon-s3)
- [Aktivieren von Zielgruppen für Streaming-Ziele](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/ui/activate/activate-segment-streaming-destinations)
- [Aktivieren von Zielgruppen für Batch-Ziele](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/ui/activate/activate-batch-profile-destinations)
- [Aktivierungsleitplanken](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/guardrails)

**Datenquellen und Connectoren**

- [Überblick über Quellen](https://experienceleague.adobe.com/en/docs/experience-platform/sources/home)
- [Marketo Engage-Connector](https://experienceleague.adobe.com/en/docs/experience-platform/sources/connectors/adobe-applications/marketo/marketo)
- [Salesforce-Connector](https://experienceleague.adobe.com/en/docs/experience-platform/sources/connectors/crm/salesforce)

**Datenmodellierung und Identität**

- [XDM-Systemübersicht](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/home)
- [Identity Service - Übersicht](https://experienceleague.adobe.com/en/docs/experience-platform/identity/home)
- [Profilübersicht](https://experienceleague.adobe.com/en/docs/experience-platform/profile/home)
- [Übersicht über Zusammenführungsrichtlinien](https://experienceleague.adobe.com/en/docs/experience-platform/profile/merge-policies/overview)

**Data Governance und Datenschutz**

- [Übersicht zur Daten-Governance](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/home)
- [Datennutzungs-Labels – Überblick](https://experienceleague.adobe.com/de/docs/experience-platform/data-governance/labels/overview)
- [Einverständnis und Einstellungen](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/consent/adobe/overview)

**Überwachung und Beobachtbarkeit**

- [Warnhinweise - Übersicht](https://experienceleague.adobe.com/en/docs/experience-platform/observability/alerts/overview)
- [Überwachen von Zieldatenflüssen](https://experienceleague.adobe.com/en/docs/experience-platform/dataflows/ui/monitor-destinations)
- [Überwachen von Quelldatenflüssen](https://experienceleague.adobe.com/en/docs/experience-platform/sources/api-tutorials/monitor)
- [Lizenznutzungs-Dashboard](https://experienceleague.adobe.com/en/docs/experience-platform/landing/license-usage-and-guardrails/license-usage-dashboard)

**Reporting und Analysen**

- [Übersicht über CJA](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-overview)
- [Verbindungen - Übersicht](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-connections/overview)
- [Übersicht über Datenansichten](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dataviews/data-views)

**Tutorials und Handbücher**

- [Erste Schritte mit Real-Time CDP B2B edition](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/intro/rtcdpb2b-intro)
- [Erstellen eines Schemas für B2B-Quellen](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/schemas/b2b)
- [Sandbox-Tools](https://experienceleague.adobe.com/en/docs/experience-platform/sandbox/sandbox-tooling-api/overview)
