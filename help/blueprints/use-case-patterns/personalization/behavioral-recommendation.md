---
title: Verhaltensempfehlung
description: Erfahren Sie, wie Sie Element- und Inhaltsempfehlungen mithilfe von Auswahlstrategien und Rangfolgemodellen generieren.
solution: Journey Optimizer, Real-Time Customer Data Platform
exl-id: db16e773-e0da-46c4-9fa5-d16f04feb46b
source-git-commit: 9ea30e48ec0fade2f9a97b185e35fbfa93f49c43
workflow-type: tm+mt
source-wordcount: '1652'
ht-degree: 5%

---

# Verhaltensempfehlung

In diesem Handbuch wird das Anwendungsfallmuster für Verhaltensempfehlungen beschrieben, bei dem [!DNL Adobe Journey Optimizer] (AJO) Decisioning, [!DNL Real-Time Customer Data Platform] (RT-CDP) und [!DNL Adobe Experience Platform] (AEP) verwendet werden, um personalisierte Empfehlungserlebnisse über Web-, Mobile App- und E-Mail-Kanäle bereitzustellen. Er wurde für Lösungsarchitekten, Marketing-Techniker und Implementierungstechniker entwickelt, die verstehen müssen, was dieses Muster bewirkt, welche Geschäftsziele es unterstützt, welche taktischen Anwendungsfälle es ermöglicht und welche Adobe-Anwendungen beteiligt sind.

Verhaltensempfehlungen generieren Empfehlungen auf Element- oder Inhaltsebene mithilfe von Verhaltenssignalen - Produktansichten, Käufe, Inhaltsinteraktionen, Suchabfragen - in Kombination mit AJO-Entscheidungsauswahlstrategien und Ranking-Modellen. Im Gegensatz zu Offer Decisioning - das eine begrenzte Anzahl von Angeboten, Promotions oder Incentives mithilfe von Eignungsregeln und Geschäftsbeschränkungen steuert - funktioniert dieses Muster bei großen, sich kontinuierlich ändernden Elementkatalogen (Produkten, Artikeln, Videos), bei denen die Auswahl durch verhaltensbezogene Affinitätssignale gesteuert wird und nicht durch die Eignungsregeln.

## Anwendungsfallmuster

**Verhaltensempfehlung**

Generieren Sie Empfehlungen auf Element- oder Inhaltsebene basierend auf Verhaltenssignalen, indem Sie AJO-Entscheidungsauswahlstrategien und Rangfolgemodelle verwenden, um kontextuelle Inhalte bereitzustellen.

**Ausführungsplan:** Aufnahme von Verhaltenssignalen > Bewertung der Entscheidungsstrategie > Recommendations-Versand > Reporting

## Anwendungsfall - Übersicht

Organisationen mit Produktkatalogen, Inhaltsbibliotheken oder Medienbibliotheken müssen für jeden Besucher die relevantesten Elemente basierend auf seinem Verhaltensverlauf und seiner Aktivität während der Sitzung aufdecken. Unabhängig davon, ob es sich um ein „empfohlenes“ Karussell auf einer Homepage, ein Crosssell-Widget auf einer Produktdetailseite oder Produktempfehlungen handelt, die in eine E-Mail-Kampagne eingebettet sind, ist die zugrunde liegende Herausforderung dieselbe: Ordnen Sie das Verhaltensprofil jedes Besuchers den relevantesten Elementen aus einem Katalog zu und stellen Sie diese Empfehlungen dann im richtigen Moment im richtigen Kanal bereit.

Dieses Muster löst diese Herausforderung, indem es Verhaltenssignale in Echtzeit über [!DNL Web SDK] oder [!DNL Mobile SDK] aufnimmt, sie über AJO Decisioning-Auswahlstrategien verarbeitet, die Elementattribute mit Verhaltenskontext kombinieren, und die empfohlenen Elemente über Web-, In-App- oder E-Mail-Kanäle bereitstellt. Rangfolgemodelle können formularbasiert (z. B. nach Kategorieaffinitätswert sortiert) oder KI-geordnet (z. B. personalisiertes Empfehlungsmodell) sein. Das Muster behandelt auch Kaltstart-Szenarien für neue Besucher ohne Verhaltensverlauf, indem es Fallback-Empfehlungen konfiguriert.

Die Zielgruppe für dieses Muster umfasst E-Commerce-Merchandising-Teams, Personalisierungs-Teams für Inhalte und Teams für digitale Erlebnisse, die durch personalisierte Empfehlungen, die auf echtem Benutzerverhalten basieren, die Interaktion, Konversion und den durchschnittlichen Bestellwert verbessern möchten.

## Wichtige Geschäftsziele

Die folgenden Geschäftsziele werden durch dieses Anwendungsfallmuster unterstützt.

### Umsätze durch Crosssell und Upsell steigern

[Umsätze durch Crosssell und Upsell steigern](../../business-objectives/revenue-monetization/drive-cross-sell-upsell-revenue.md)

Werben Sie für ergänzende und Premium-Produkte oder -Services für bestehende Kunden auf der Grundlage des Verhaltens und der Kaufhistorie.

**KPIs:** Upsell/Crosssell %, Inkrementeller Umsatz, Kundenlebenszeitwert

### Erhöhung der Konversionsraten

[Erhöhung der Konversionsraten](../../business-objectives/revenue-monetization/increase-conversion-rates.md)

Verbessern Sie den Prozentsatz der Besucher und Interessenten, die die gewünschten Aktionen wie Käufe, Anmeldungen oder Formularübermittlungen durchführen.

**KPIs:** Konversionsraten, Lead-Konversion, Kosten pro Lead

### Bereitstellen personalisierter Kundenerlebnisse

[Bereitstellen personalisierter Kundenerlebnisse](../../business-objectives/customer-experience/deliver-personalized-customer-experiences.md)

Passen Sie Inhalte, Angebote und Nachrichten an individuelle Voreinstellungen, Verhaltensweisen und Lebenszyklusphasen an.

**KPIs:** Interaktion, Konversionsraten, Kundenzufriedenheit (CSAT)

## Beispiele für taktische Anwendungsfälle

Im Folgenden finden Sie häufige taktische Implementierungen dieses Musters:

- Produkt-Crosssell-Widget auf der Produktdetailseite („Kunden haben auch gekauft„)
- Karussell „Empfohlen für Sie“ auf der Startseite basierend auf dem Durchsuchen-Verlauf
- Inhaltsempfehlungen auf der Media-Site basierend auf dem Leseverhalten
- Widget „Kürzlich angesehen“ mit ähnlichen Elementen kombiniert
- Ergänzende Produktempfehlungen nach dem Kauf
- E-Mail-Produktempfehlungen basierend auf der Affinität zum Verhalten
- Kategoriespezifische Empfehlungen, die auf dem Verhalten beim Durchsuchen während der Sitzung basieren
- Neureihung von Suchergebnissen basierend auf Verhaltenssignalen

## Wichtige Performance-Indikatoren

Die folgenden KPIs helfen dabei, die Effektivität der Implementierungen von Verhaltensempfehlungen zu messen.

| KPI | Messansatz |
| --- | --- |
| Klickrate für Empfehlungen (CTR) | Klicks auf empfohlene Elemente dividiert durch Empfehlungsimpressionen |
| Konversionsrate der Empfehlung | Käufe oder gewünschte Aktionen aus Empfehlungsklicks dividiert durch die Gesamtzahl der Empfehlungsklicks |
| Durch Recommendations beeinflusster Umsatz | Gesamtumsatz aus Bestellungen, die mindestens ein empfehlungsgesteuertes Produkt enthalten |
| Steigerung des durchschnittlichen Bestellwerts (AOV) | Erhöhung der AOV für Sitzungen, die mit Recommendations interagiert haben, im Vergleich zu Sitzungen ohne |
| Artikel pro Bestellung | Anzahl der Artikel pro Bestellung für Sitzungen, die mit Empfehlungen interagieren |
| Umfang der Empfehlung | Prozentsatz der zulässigen Seitenansichten oder Sitzungen, die personalisierte (Nicht-Fallback-)Empfehlungen erhalten haben |
| Kaltstart-Ausweichrate | Prozentsatz der Empfehlungsanfragen, die von der Fallback-Logik aufgrund eines unzureichenden Verhaltensverlaufs bereitgestellt wurden |

## Programme

Die folgenden Anwendungen werden in diesem Anwendungsfallmuster verwendet.

- **[!DNL Adobe Journey Optimizer](AJO) Decisioning** - Auswahlstrategien, Rangfolgemodelle, Elementkataloge und Entscheidungsrichtlinien, die Verhaltenssignale auswerten und für jeden Besucher die relevantesten Elemente zurückgeben
- **[!DNL Adobe Real-Time Customer Data Platform](RT-CDP)** — Akkumulation von Verhaltensprofildaten, Zielgruppenbewertung für das Recommendations-Scoping und berechnete Attribute für die Bewertung der Affinität im Verhalten
- **[!DNL Adobe Experience Platform](AEP)** - Aufnahme von Verhaltensereignissen über [!DNL Web SDK] und [!DNL Mobile SDK], [!DNL Edge Network] Verarbeitung, XDM-Schemaverwaltung für Ereignis- und Katalogdaten

## Verwandte Dokumentation

Die folgenden Ressourcen bieten zusätzliche Details zu den in diesem Muster verwendeten Technologien und Funktionen.

### Entscheidungs-Management

- [Überblick über das Entscheidungs-Management](https://experienceleague.adobe.com/de/docs/journey-optimizer/using/decisioning/offer-decisioning/get-started-decision/starting-offer-decisioning)
- [Erstellen von Platzierungen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-placements)
- [Erstellen von Entscheidungsregeln](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-decision-rules)
- [Personalisierte Angebote erstellen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-personalized-offers)
- [Erstellen von Fallback-Angeboten](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-fallback-offers)
- [Erstellen von Sammlungen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-collections)
- [Erstellen von Sammlungsqualifizierern](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-tags)
- [Entscheidungen erstellen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-activities)
- [Rangfolgestrategien](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/ranking/ranking-strategies)
- [Versand von Angeboten in Nachrichten](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/deliver-offers/deliver-offers-in-messages)
- [Unterbreiten von Angeboten mithilfe der Edge Decisioning-API](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/api/offer-delivery-api/edge-decisioning-api)

### Datenerfassung und Web/Mobile SDK

- [Übersicht über Web SDK](https://experienceleague.adobe.com/en/docs/experience-platform/web-sdk/home)
- [Installieren von Web SDK](https://experienceleague.adobe.com/en/docs/experience-platform/web-sdk/install/overview)
- [Übersicht über Mobile SDK](https://experienceleague.adobe.com/en/docs/experience-platform/edge-network/mobile-sdk/overview)
- [Konfigurieren von Datenströmen](https://experienceleague.adobe.com/en/docs/experience-platform/datastreams/configure)
- [Übersicht über die Edge Network Server-API](https://experienceleague.adobe.com/en/docs/experience-platform/edge-network-server-api/overview)

### XDM und Datenmodellierung

- [XDM-Systemübersicht](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/home)
- [Grundlagen der Schemakomposition](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/schema/composition)
- [Erstellen eines Datensatzes](https://experienceleague.adobe.com/en/docs/experience-platform/catalog/datasets/create)
- [Definieren einer Beziehung zwischen zwei Schemata](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/tutorials/relationship-api)

### Identität und Profil

- [Identity Service - Übersicht](https://experienceleague.adobe.com/en/docs/experience-platform/identity/home)
- [Übersicht über Identity-Namespaces](https://experienceleague.adobe.com/de/docs/experience-platform/identity/features/namespaces)
- [Übersicht über Zusammenführungsrichtlinien](https://experienceleague.adobe.com/en/docs/experience-platform/profile/merge-policies/overview)
- [Übersicht über das Echtzeit-Kundenprofil](https://experienceleague.adobe.com/en/docs/experience-platform/profile/home)

### Zielgruppen und Segmentierung

- [Übersicht über den Segmentierungs-Service](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/home)
- [Handbuch zur Benutzeroberfläche von Segment Builder](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-builder)
- [Streaming-Segmentierung](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/streaming-segmentation)
- [Edge-Segmentierung](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/edge-segmentation)

### Berechnete Attribute und Profilanreicherung

- [Berechnete Attribute - Übersicht](https://experienceleague.adobe.com/en/docs/experience-platform/profile/computed-attributes/overview)
- [Handbuch zur Benutzeroberfläche für berechnete Attribute](https://experienceleague.adobe.com/en/docs/experience-platform/profile/computed-attributes/ui)
- [Kunden-KI - Übersicht](https://experienceleague.adobe.com/en/docs/experience-platform/intelligent-services/customer-ai/overview)

### Kanalkonfiguration

- [Erste Schritte mit der E-Mail-Konfiguration](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/get-started-email-config)
- [Einrichten von Kanaloberflächen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/email-settings)
- [Delegieren von Subdomains](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/delegate-subdomain)

### Verfassen und Personalisieren von Nachrichten

- [Entwerfen von E-Mail-Inhalten](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/design-email/design-emails)
- [Hinzufügen von Personalisierung](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalize)
- [Personalization-Syntax](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalization-syntax)
- [Dynamische Inhalte](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/dynamic-content)
- [Arbeiten mit Inhaltsvorlagen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-templates/content-templates)

### Reporting und Analysen

- [Globaler Kampagnenbericht](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/campaign-global-report-cja)
- [Globaler Journey-Bericht](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/journey-global-report-cja)
- [Arbeiten mit Customer Journey Analytics](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/report-cja-manage)
- [Übersicht über CJA](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-overview)
- [Übersicht über Analysis Workspace](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/home)
- [Übersicht über berechnete Metriken](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/cja-calcmetrics/calc-metr-overview)

### Data Governance und Lebenszyklus

- [Übersicht zur Daten-Governance](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/home)
- [Datennutzungs-Labels – Überblick](https://experienceleague.adobe.com/de/docs/experience-platform/data-governance/labels/overview)
- [Erweiterte Übersicht über die Verwaltung des Datenlebenszyklus](https://experienceleague.adobe.com/en/docs/experience-platform/data-lifecycle/home)
- [Datensatzgültigkeiten](https://experienceleague.adobe.com/en/docs/experience-platform/data-lifecycle/ui/dataset-expiration)

### Überwachung und Beobachtbarkeit

- [Observability Insights - Übersicht](https://experienceleague.adobe.com/en/docs/experience-platform/observability/home)
- [Warnhinweise - Übersicht](https://experienceleague.adobe.com/en/docs/experience-platform/observability/alerts/overview)

### Leitlinien

- [Journey Optimizer-Leitplanken](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/get-started/guardrails)
- [Leitplanken für Echtzeit-Kundenprofile](https://experienceleague.adobe.com/en/docs/experience-platform/profile/guardrails)
- [Schutzmaßnahmen bei der Aufnahme](https://experienceleague.adobe.com/en/docs/experience-platform/ingestion/guardrails)
- [Leitplanken für Identity Service](https://experienceleague.adobe.com/en/docs/experience-platform/identity/guardrails)

### Tutorials und Handbücher

- [Überblick über Quellen](https://experienceleague.adobe.com/en/docs/experience-platform/sources/home)
- [Übersicht über Tags](https://experienceleague.adobe.com/en/docs/experience-platform/tags/home)
- [Feldgruppe „Einverständnis und Voreinstellungen“](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/field-groups/profile/consents)
