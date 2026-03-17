---
user-guide-title: Customer Experience Orchestration - Geschäftsziele, Anwendungsfälle, Architekturdiagramme und Blueprints
breadcrumb-title: Anwendungsfälle und Blueprints
user-guide-description: Informieren Sie sich über wichtige Geschäftsziele, Anwendungsfallmuster und branchenspezifische Anwendungsfälle für Adobe Experience Platform und Programme. Visuelle Architekturdiagramme und Blueprints bieten technische Referenzen für Systemintegration, Datenflüsse und Lösungsdesign und verbinden den geschäftlichen Nutzen mit der Implementierung.
product: adobe experience platform
mini-toc-levels: 3
role: Developer, User
source-git-commit: 6bf36e8e5d797eef5b2dfe86e4e75d36b0c026d4
workflow-type: tm+mt
source-wordcount: '474'
ht-degree: 12%

---


# Blueprints zur Orchestrierung des Kundenerlebnisses {#architecture}

+ [Blueprints zur Orchestrierung des Kundenerlebnisses](/help/blueprints/overview.md)
+ Wichtige Geschäftsziele für AEP und Apps{#business-objectives}
   + [Überblick](/help/blueprints/business-objectives/overview.md)
   + Akquise und Wachstum{#acquisition-growth}
      + [Neue Kunden gewinnen](/help/blueprints/business-objectives/acquisition-growth/acquire-new-customers.md)
      + [Lead-Generierung erhöhen](/help/blueprints/business-objectives/acquisition-growth/increase-lead-generation.md)
      + [Website-Interaktion steigern](/help/blueprints/business-objectives/acquisition-growth/increase-website-engagement.md)
   + Umsatz und Monetarisierung{#revenue-monetization}
      + [Erhöhung der Konversionsraten](/help/blueprints/business-objectives/revenue-monetization/increase-conversion-rates.md)
      + [Umsatz und Umsatz steigern](/help/blueprints/business-objectives/revenue-monetization/increase-revenue-sales.md)
      + [Umsätze durch Crosssell und Upsell steigern](/help/blueprints/business-objectives/revenue-monetization/drive-cross-sell-upsell-revenue.md)
      + [Steigerung der Kundentreue und des Werts während der gesamten Lebensdauer](/help/blueprints/business-objectives/revenue-monetization/increase-customer-loyalty-lifetime-value.md)
   + Kosten und Effizienz{#cost-efficiency}
      + [Reduzierung der Kosten für die Kundenakquise](/help/blueprints/business-objectives/cost-efficiency/reduce-customer-acquisition-cost.md)
      + [Marketing-Ausgaben und -ROI optimieren](/help/blueprints/business-objectives/cost-efficiency/optimize-marketing-spend-roi.md)
      + [Verbesserung der Datenqualität und Governance](/help/blueprints/business-objectives/cost-efficiency/improve-data-quality-governance.md)
      + [Konsolidierung und Modernisierung der Marketing-Technologie](/help/blueprints/business-objectives/cost-efficiency/consolidate-modernize-marketing-technology.md)
   + Kundenerlebnis{#customer-experience-objectives}
      + [Bereitstellen personalisierter Kundenerlebnisse](/help/blueprints/business-objectives/customer-experience/deliver-personalized-customer-experiences.md)
      + [Verbesserung der Kundenbindung](/help/blueprints/business-objectives/customer-experience/improve-customer-retention.md)
      + [Verbessern des Kunden-Onboarding](/help/blueprints/business-objectives/customer-experience/improve-customer-onboarding.md)
      + [Wiederherstellen von Transaktionsabbrüchen und Journey](/help/blueprints/business-objectives/customer-experience/recover-abandoned-carts-journeys.md)
   + Analytics und Insights{#analytics-insights}
      + [Analyse und Reporting verbessern](/help/blueprints/business-objectives/analytics-insights/improve-analytics-reporting.md)
      + [Datengestützte Entscheidungsfindung ermöglichen](/help/blueprints/business-objectives/analytics-insights/enable-data-driven-decision-making.md)
      + [Marketing-Attribution verbessern](/help/blueprints/business-objectives/analytics-insights/improve-marketing-attribution.md)
   + Qualifizierung und Vertrieb (B2B){#qualification-sales-b2b}
      + [Verbessern der Lead-Qualifizierung und -Konversion](/help/blueprints/business-objectives/qualification-sales-b2b/improve-lead-qualification-conversion.md)
      + [Verbessern der Kundeninteraktion](/help/blueprints/business-objectives/qualification-sales-b2b/improve-customer-engagement.md)
+ Anwendungsfallmuster{#use-case-patterns}
   + [Überblick](/help/blueprints/use-case-patterns/overview.md)
   + Zielgruppenbildung und -aktivierung{#audience-building-activation}
      + [Audience Activation zu Zielen](/help/blueprints/use-case-patterns/audience-building-activation/audience-activation-to-destinations.md)
      + [Zielgruppen-Collaboration mit Segment Match](/help/blueprints/use-case-patterns/audience-building-activation/audience-collaboration-segment-match.md)
      + [Ereignisweiterleitung](/help/blueprints/use-case-patterns/audience-building-activation/event-forwarding.md)
      + [B2B-Audience Activation](/help/blueprints/use-case-patterns/audience-building-activation/b2b-audience-activation.md)
   + Personalisierung{#personalization-patterns}
      + [Web-Personalization für anonyme Besucher](/help/blueprints/use-case-patterns/personalization/anonymous-visitor-web-personalization.md)
      + [Web-/App-Personalization für bekannte Besucher](/help/blueprints/use-case-patterns/personalization/known-visitor-web-app-personalization.md)
      + [Offer Decisioning](/help/blueprints/use-case-patterns/personalization/offer-decisioning.md)
      + [Verhaltensempfehlung](/help/blueprints/use-case-patterns/personalization/behavioral-recommendation.md)
   + Kampagnenverwaltung und -orchestrierung{#campaign-orchestration-patterns}
      + [Batch-Aktivierung ausgehender Nachrichten](/help/blueprints/use-case-patterns/campaign-management-orchestration/batch-outbound-message-activation.md)
      + [Ereignisausgelöstes Messaging](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md)
      + [Mehrstufige orchestrierte Journey](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md)
      + [Cross-Channel-Journey mit Decisioning](/help/blueprints/use-case-patterns/campaign-management-orchestration/cross-channel-journey-with-decisioning.md)
      + [Einkauf von gruppenbasiertem Marketing und Journey-Management](/help/blueprints/use-case-patterns/campaign-management-orchestration/buying-group-based-marketing.md)
   + Analyse{#analysis-patterns}
      + [Generierung von Customer Analytics und Insight](/help/blueprints/use-case-patterns/analysis/customer-analytics-insight-generation.md)
      + [B2B-Analyse](/help/blueprints/use-case-patterns/analysis/b2b-analytics.md)
   + Dialogerfahrung{#conversational-experience-patterns}
      + [Brand Concierge - Gesprächserlebnis](/help/blueprints/use-case-patterns/conversational-experience/brand-concierge-conversational-experience.md)
+ Anwendungsfälle der Branche - Beispiele{#industry-use-cases}
   + [Überblick](/help/blueprints/industry-use-cases/overview.md)
   + [Automobil](/help/blueprints/industry-use-cases/automotive/automotive-overview.md)
   + [B2B](/help/blueprints/industry-use-cases/b2b/b2b-overview.md)
   + [Finanzdienstleistungen](/help/blueprints/industry-use-cases/financial-services/financial-services-overview.md)
   + [Gesundheitswesen](/help/blueprints/industry-use-cases/healthcare/healthcare-overview.md)
   + [Versicherung](/help/blueprints/industry-use-cases/insurance/insurance-overview.md)
   + [Medien und Unterhaltung](/help/blueprints/industry-use-cases/media-entertainment/media-entertainment-overview.md)
   + [Einzelhandel](/help/blueprints/industry-use-cases/retail/retail-overview.md)
   + [Telekommunikation](/help/blueprints/industry-use-cases/telecommunications/telecommunications-overview.md)
   + [Reisen und Gastgewerbe](/help/blueprints/industry-use-cases/travel-hospitality/travel-hospitality-overview.md)
+ Architekturdiagramme und Blueprints{#architecture-diagrams}
   + Architekturübersichten{#architecture-overview}
      + [Experience Cloud](/help/blueprints/experience-platform/experience-cloud.md)
      + [Experience Platform und Anwendungen](/help/blueprints/experience-platform/platform-applications.md)
      + [Experience Platform-Datenfluss](/help/blueprints/experience-platform/platform-data-flow.md)
      + [Experience Platform-Leitplanken](/help/blueprints/experience-platform/guardrails.md)
      + Implementierung{#deployment}
         + [Experience Platform Web SDK und  [!DNL Edge Network]](/help/blueprints/experience-platform/deployment/websdk.md)
         + [Anwendungs-SDKs](/help/blueprints/experience-platform/deployment/appsdk.md)
   + Aktivierung von Zielgruppen und Profilen{#audience-activation}
      + [Gerätebasiert - Anonyme Zielgruppen-Zielgruppenbestimmung mit Audience Manager](/help/blueprints/audience-activation/audience-manager.md)
      + Real-Time Customer Data Platform (RTCDP) {#known-customer-audience-activation}
         + [Zielgruppenaktivierung für Social-Media- und Werbeziele](/help/blueprints/audience-activation/advertising-activation.md)
         + [Blueprint zur Aktivierung von Zielgruppen und Profilen für Unternehmensziele](/help/blueprints/audience-activation/enterprise-destinations.md)
         + [Echtzeit-Profilzugriff für Support- und Vertriebsszenarien](/help/blueprints/audience-activation/customer-activity.md)
         + [Echtzeit-Edge-Profilzugriff für Web- und Mobile-Personalisierung](/help/blueprints/audience-activation/real-time-lookup.md)
         + [Audience-Zusammenarbeit mit Segment Match](/help/blueprints/audience-activation/segment-match.md)
         + [Bekannte Kundenpersonalisierung mit Target](/help/blueprints/audience-activation/rtcdp-target.md)
         + [Benutzerdefinierte Datenwissenschaft zur Profilanreicherung](/help/blueprints/audience-activation/data-science.md)
   + B2B-Aktivierung und Marketing{#b2b-activation}
      + [Überblick](/help/blueprints/b2b/overview.md)
      + [B2B-Aktivierung](/help/blueprints/b2b/b2bactivation.md)
      + [B2B-Kontoaktivierung](/help/blueprints/b2b/b2b-account-activation.md)
      + [Einkauf von gruppenbasiertem Marketing und Journey-Management](/help/blueprints/b2b/b2b-buying-group-journeys.md)
      + [B2B-Journey, die Marketo-Daten verwenden](/help/blueprints/b2b/b2b-journeys-with-marketo.md)
      + [Bezahlter B2B-Medien-Controller](/help/blueprints/b2b/ajo-b2b-paid-media-controller.md)
      + Blueprint zur Integration von Marketo Engage und Workfront{#marketo-engage-and-workfront-integration-blueprint}
         + [Überblick](/help/blueprints/b2b/marketo-engage-and-workfront-integration-blueprint/overview.md)
         + [Aufnehmen und erstellen](/help/blueprints/b2b/marketo-engage-and-workfront-integration-blueprint/intake-and-create.md)
         + [Überprüfen und genehmigen](/help/blueprints/b2b/marketo-engage-and-workfront-integration-blueprint/review-and-approve-blueprint.md)
         + [Erfolgsgeschichten von Kunden](/help/blueprints/b2b/marketo-engage-and-workfront-integration-blueprint/customer-success-stories.md)
   + Customer Journey Analytics{#customer-journey-analytics}
      + [Überblick](/help/blueprints/customer-journey-analytics/overview.md)
      + [B2B-Customer Journey Analytics](/help/blueprints/customer-journey-analytics/b2b-cja.md)
      + [Freigeben von CJA-Zielgruppen für RTCDP](/help/blueprints/customer-journey-analytics/cja-rtcdp.md)
      + [CJA und Journey Optimizer](/help/blueprints/customer-journey-analytics/cja-ajo.md)
      + [Datenanalyse und Intelligenz](/help/blueprints/customer-journey-analytics/analysis.md)
   + Kunden-Journey{#customer-journeys}
      + [Überblick](/help/blueprints/customer-journeys/overview.md)
      + Journey Optimizer{#journey-optimizer}
         + [Journey Optimizer](/help/blueprints/customer-journeys/journey-optimizer/journey-optimizer-overview.md)
         + [Journey von AJO](/help/blueprints/customer-journeys/journey-optimizer/journey-optimizer-journeys.md)
         + [AJO-Kampagnen](/help/blueprints/customer-journeys/journey-optimizer/journey-optimizer-campaigns.md)
         + [Messaging von Drittanbietern](/help/blueprints/customer-journeys/journey-optimizer/3rd-party-messaging.md)
      + Entscheidungs-Management{#decision-management}
         + [Überblick](/help/blueprints/customer-journeys/decision-management/decision-management-overview.md)
         + [Entscheidungs-Management in Edge](/help/blueprints/customer-journeys/decision-management/decision-management-edge.md)
         + [Entscheidungs-Management im Hub](/help/blueprints/customer-journeys/decision-management/decision-management-hub.md)
      + Campaign v8{#campaign-v8}
         + [Campaign v8](/help/blueprints/customer-journeys/campaign-v8/campaign-v8-overview.md)
         + [Real-Time CDP mit Adobe [!DNL Campaign] v8](/help/blueprints/customer-journeys/campaign-v8/rtcdp-and-campaign-v8.md)
         + [Journey Optimizer mit Adobe Campaign v8](/help/blueprints/customer-journeys/campaign-v8/ajo-and-campaign-v8.md)
      + Veraltete Blueprints{#deprecated-blueprints}
         + Campaign Standard{#campaign-standard}
            + [[!DNL Campaign Standard]](https://experienceleague.adobe.com/de/docs/campaign-standard){target="_blank"}
            + [Real-Time CDP mit Adobe [!DNL Campaign Standard]](https://experienceleague.adobe.com/de/docs/campaign-standard/using/integrating-with-adobe-cloud/adobe-experience-platform/get-started-sources-destinations)
         + Campaign v7{#campaign-v7}
            + [Campaign v7](/help/blueprints/customer-journeys/campaign-v7/campaign-v7-overview.md)
