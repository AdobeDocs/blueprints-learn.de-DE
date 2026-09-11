---
user-guide-title: Customer Experience Orchestration - Geschäftsziele, Anwendungsfälle, Architekturdiagramme und Blueprints
breadcrumb-title: Anwendungsfälle und Blueprints
user-guide-description: Informieren Sie sich über wichtige Geschäftsziele, Anwendungsfallmuster und branchenspezifische Anwendungsfälle für Adobe Experience Platform und Programme. Visuelle Architekturdiagramme und Blueprints bieten technische Referenzen für Systemintegration, Datenflüsse und Lösungsdesign und verbinden den geschäftlichen Nutzen mit der Implementierung.
product: adobe experience platform
mini-toc-levels: 3
role: Developer, User
nudge: orange
source-git-commit: 2b2b9b9c359c4cc6757ac62ad502ece9a4923095
workflow-type: tm+mt
source-wordcount: '1172'
ht-degree: 15%

---


# Blueprints zur Orchestrierung des Kundenerlebnisses {#architecture}

+ [Blueprints zur Orchestrierung des Kundenerlebnisses](/help/blueprints/overview.md)
+ Wichtige Geschäftsziele für AEP und Apps{#business-objectives}
  + [Übersicht](/help/blueprints/business-objectives/overview.md)
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
  + [Übersicht](/help/blueprints/use-case-patterns/overview.md)
  + Zielgruppenbildung und -aktivierung{#audience-building-activation}
    + [Audience Activation zu Zielen](/help/blueprints/use-case-patterns/audience-building-activation/audience-activation-to-destinations.md)
    + [Zielgruppen-Collaboration mit Segment Match](/help/blueprints/use-case-patterns/audience-building-activation/audience-collaboration-segment-match.md)
    + [Ereignisweiterleitung](/help/blueprints/use-case-patterns/audience-building-activation/event-forwarding.md)
    + [Echtzeit-Profilsuche für Support und Vertrieb](/help/blueprints/use-case-patterns/audience-building-activation/real-time-profile-lookup.md)
    + [Benutzerdefinierte Datenwissenschaft für die Profilanreicherung](/help/blueprints/use-case-patterns/audience-building-activation/data-science-profile-enrichment.md)
  + Personalisierung{#personalization-patterns}
    + [Web-Personalization für anonyme Besucher](/help/blueprints/use-case-patterns/personalization/anonymous-visitor-web-personalization.md)
    + [Web-/App-Personalization für bekannte Besucher](/help/blueprints/use-case-patterns/personalization/known-visitor-web-app-personalization.md)
    + [Offer Decisioning](/help/blueprints/use-case-patterns/personalization/offer-decisioning.md)
    + [Verhaltensempfehlung](/help/blueprints/use-case-patterns/personalization/behavioral-recommendation.md)
    + [Edge-Profilzugriff für Web/Mobile Personalization](/help/blueprints/use-case-patterns/personalization/edge-profile-access.md)
    + [Audience-Freigabe mit Adobe Target](/help/blueprints/use-case-patterns/personalization/audience-sharing-with-target.md)
  + Kampagnenverwaltung und -orchestrierung{#campaign-orchestration-patterns}
    + [Batch-Aktivierung ausgehender Nachrichten](/help/blueprints/use-case-patterns/campaign-management-orchestration/batch-outbound-message-activation.md)
    + [Ereignisausgelöstes Messaging](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md)
    + [Mehrstufige orchestrierte Journey](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md)
    + [Cross-Channel-Journey mit Decisioning](/help/blueprints/use-case-patterns/campaign-management-orchestration/cross-channel-journey-with-decisioning.md)
    + [Batch-Orchestrierung und Transaktionsnachrichten in Campaign v8](/help/blueprints/use-case-patterns/campaign-management-orchestration/campaign-v8-orchestration.md)
    + [Integration von Drittanbieter-Messaging mit Journey Optimizer](/help/blueprints/use-case-patterns/campaign-management-orchestration/third-party-messaging.md)
  + Analyse{#analysis-patterns}
    + [Generierung von Customer Analytics und Insight](/help/blueprints/use-case-patterns/analysis/customer-analytics-insight-generation.md)
  + B2B: Aktivierung und Marketing{#b2b-patterns}
    + [B2B-Audience Activation](/help/blueprints/use-case-patterns/b2b/account-audience-activation.md)
    + [Einkauf von gruppenbasiertem Marketing und Journey-Management](/help/blueprints/use-case-patterns/b2b/buying-group-marketing.md)
    + [B2B-Analyse](/help/blueprints/use-case-patterns/b2b/account-analytics.md)
    + [B2B-Journey, die Marketo-Daten verwenden](/help/blueprints/use-case-patterns/b2b/marketo-data-journeys.md)
    + [Bezahlter AJO B2B-Medien-Controller](/help/blueprints/use-case-patterns/b2b/paid-media-orchestration.md)
    + [Aufnahme und Erstellung von Marketo und Workfront](/help/blueprints/use-case-patterns/b2b/campaign-intake-and-creation.md)
    + [Überprüfen und Genehmigen von Marketo und Workfront](/help/blueprints/use-case-patterns/b2b/campaign-review-and-approval.md)
  + Dialogerfahrung{#conversational-experience-patterns}
    + [Brand Concierge - Gesprächserlebnis](/help/blueprints/use-case-patterns/conversational-experience/brand-concierge-conversational-experience.md)
+ Anwendungsfälle der Branche - Beispiele{#industry-use-cases}
  + [Anwendungsfallkatalog](/help/blueprints/industry-use-cases/use-case-catalog.md)
  + [Automobil](/help/blueprints/industry-use-cases/automotive/automotive-overview.md)
  + [B2B](/help/blueprints/industry-use-cases/b2b/b2b-overview.md)
  + [Finanzdienstleistungen](/help/blueprints/industry-use-cases/financial-services/financial-services-overview.md)
  + [Gesundheitswesen](/help/blueprints/industry-use-cases/healthcare/healthcare-overview.md)
  + [Versicherung](/help/blueprints/industry-use-cases/insurance/insurance-overview.md)
  + [Medien und Unterhaltung](/help/blueprints/industry-use-cases/media-entertainment/media-entertainment-overview.md)
  + [Einzelhandel](/help/blueprints/industry-use-cases/retail/retail-overview.md)
  + [Telekommunikation](/help/blueprints/industry-use-cases/telecommunications/telecommunications-overview.md)
  + [Technologie](/help/blueprints/industry-use-cases/technology/technology-overview.md)
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
        + [[!DNL Campaign Standard]](https://experienceleague.adobe.com/en/docs/campaign-standard){target="_blank"}
        + [Real-Time CDP mit Adobe [!DNL Campaign Standard]](https://experienceleague.adobe.com/en/docs/campaign-standard/using/integrating-with-adobe-cloud/adobe-experience-platform/get-started-sources-destinations)
      + Campaign v7{#campaign-v7}
        + [Campaign v7](/help/blueprints/customer-journeys/campaign-v7/campaign-v7-overview.md)

+ {hide-from-toc}Hands-On Labs{#labs}
  + [Übersicht über Hands-On Labs](/help/blueprints/labs/overview.md)
  + Praktische Workshops{#workshops}
    + AEP Foundations{#aep-foundations}
      + [Übersicht](/help/blueprints/labs/aep-foundations/overview.md)
      + [Einrichtung](/help/blueprints/labs/aep-foundations/setup.md)
      + Sandbox-Setup{#aep-sandbox}
        + [Developer Console-Setup](/help/blueprints/labs/aep-foundations/sandbox-setup/developer-console-setup.md)
        + [Bereitstellungsanweisungen](/help/blueprints/labs/aep-foundations/sandbox-setup/deployment-instructions.md)
      + Postman-Setup{#aep-postman}
        + [Postman-Installation](/help/blueprints/labs/aep-foundations/postman-setup/postman-installation.md)
        + [Umgebungsdatei](/help/blueprints/labs/aep-foundations/postman-setup/environment-file.md)
        + [API-Sammlung](/help/blueprints/labs/aep-foundations/postman-setup/api-collection.md)
        + [Sandbox-Zugriff](/help/blueprints/labs/aep-foundations/postman-setup/sandbox-access.md)
        + [Zugriffstoken](/help/blueprints/labs/aep-foundations/postman-setup/access-token.md)
      + Echtzeit-Kundenprofil{#aep-rtcp}
        + [Vorlesungen](/help/blueprints/labs/aep-foundations/real-time-customer-profile/lectures.md)
        + Überprüfen des Profils{#aep-rtcp-inspect}
          + [Übersicht](/help/blueprints/labs/aep-foundations/real-time-customer-profile/inspecting-the-profile/overview.md)
          + [Profilgrundlagen](/help/blueprints/labs/aep-foundations/real-time-customer-profile/inspecting-the-profile/profile-basics.md)
          + [Zusammenführungsrichtlinien.](/help/blueprints/labs/aep-foundations/real-time-customer-profile/inspecting-the-profile/merge-policies.md)
          + [Profil- und Identity-APIs](/help/blueprints/labs/aep-foundations/real-time-customer-profile/inspecting-the-profile/profile-and-identity-apis.md)
      + LID-Methode{#aep-lid}
        + [Voraussetzungen](/help/blueprints/labs/aep-foundations/lid-methodology/prerequisites.md)
        + [Label](/help/blueprints/labs/aep-foundations/lid-methodology/label.md)
        + Identifizieren{#aep-lid-identify}
          + [Übersicht](/help/blueprints/labs/aep-foundations/lid-methodology/identify/overview.md)
          + [Teil 1: Verbleibende Tabellentypen](/help/blueprints/labs/aep-foundations/lid-methodology/identify/part-1-remaining-table-types.md)
          + [Teil 2: Schlüsselfelder](/help/blueprints/labs/aep-foundations/lid-methodology/identify/part-2-key-fields.md)
        + [denormalisieren](/help/blueprints/labs/aep-foundations/lid-methodology/denormalize.md)
      + XDM-Modellierung{#aep-xdm}
        + [Vorlesungen](/help/blueprints/labs/aep-foundations/xdm-modeling/lectures.md)
        + Benutzeroberflächenmodellierung{#aep-xdm-ui}
          + [Übersicht](/help/blueprints/labs/aep-foundations/xdm-modeling/ui-modeling/overview.md)
          + [Anmelden und Durchsuchen](/help/blueprints/labs/aep-foundations/xdm-modeling/ui-modeling/login-and-browse.md)
          + [Standardobjekte modellieren](/help/blueprints/labs/aep-foundations/xdm-modeling/ui-modeling/model-standard-objects.md)
          + [Benutzerdefinierte Objekte modellieren](/help/blueprints/labs/aep-foundations/xdm-modeling/ui-modeling/model-custom-objects.md)
          + [Für Profil konfigurieren](/help/blueprints/labs/aep-foundations/xdm-modeling/ui-modeling/configure-for-profile.md)
        + API-Modellierung{#aep-xdm-api}
          + [Übersicht](/help/blueprints/labs/aep-foundations/xdm-modeling/api-modeling/overview.md)
          + Schema erstellen{#aep-xdm-api-build}
            + [Übersicht](/help/blueprints/labs/aep-foundations/xdm-modeling/api-modeling/build-schema/overview.md)
            + [Abrufen von Standardfeldgruppen](/help/blueprints/labs/aep-foundations/xdm-modeling/api-modeling/build-schema/get-standard-field-groups.md)
            + [Erstellen benutzerdefinierter Feldergruppen](/help/blueprints/labs/aep-foundations/xdm-modeling/api-modeling/build-schema/create-custom-field-groups.md)
            + [Profilklasse abrufen](/help/blueprints/labs/aep-foundations/xdm-modeling/api-modeling/build-schema/get-profile-class.md)
            + [Schema erstellen](/help/blueprints/labs/aep-foundations/xdm-modeling/api-modeling/build-schema/create-schema.md)
            + [Schema anzeigen](/help/blueprints/labs/aep-foundations/xdm-modeling/api-modeling/build-schema/view-schema.md)
            + [Schema ändern - JSON-Patch](/help/blueprints/labs/aep-foundations/xdm-modeling/api-modeling/build-schema/modify-schema-json-patch.md)
          + Identitätsfelder markieren{#aep-xdm-api-identity}
            + [Übersicht](/help/blueprints/labs/aep-foundations/xdm-modeling/api-modeling/mark-identity-fields/overview.md)
            + [Primäre Identität erstellen](/help/blueprints/labs/aep-foundations/xdm-modeling/api-modeling/mark-identity-fields/create-primary-identity.md)
            + [Erstellen anderer Identitäten](/help/blueprints/labs/aep-foundations/xdm-modeling/api-modeling/mark-identity-fields/create-other-identities.md)
            + [Schema anzeigen](/help/blueprints/labs/aep-foundations/xdm-modeling/api-modeling/mark-identity-fields/view-schema.md)
          + Definieren von Beziehungen{#aep-xdm-api-relationships}
            + [Übersicht](/help/blueprints/labs/aep-foundations/xdm-modeling/api-modeling/define-relationships/overview.md)
            + [Plan-Schema-ID abrufen](/help/blueprints/labs/aep-foundations/xdm-modeling/api-modeling/define-relationships/get-plan-schema-id.md)
            + [Erstellen einer Schemabeziehung](/help/blueprints/labs/aep-foundations/xdm-modeling/api-modeling/define-relationships/create-schema-relationship.md)
            + [Planreferenz-Identität erstellen](/help/blueprints/labs/aep-foundations/xdm-modeling/api-modeling/define-relationships/create-plan-reference-identity.md)
            + [Schema anzeigen](/help/blueprints/labs/aep-foundations/xdm-modeling/api-modeling/define-relationships/view-schema.md)
          + [Zusammenfassung](/help/blueprints/labs/aep-foundations/xdm-modeling/api-modeling/recap.md)
        + Bonus-Labs{#aep-xdm-bonus}
          + [Übersicht](/help/blueprints/labs/aep-foundations/xdm-modeling/bonus-labs/overview.md)
          + [Automatisieren mit APIs](/help/blueprints/labs/aep-foundations/xdm-modeling/bonus-labs/automate-with-apis.md)
      + Datenaufnahme{#aep-ingestion}
        + [Vorlesungen](/help/blueprints/labs/aep-foundations/data-ingestion/lectures.md)
        + [Labor-Übersicht](/help/blueprints/labs/aep-foundations/data-ingestion/lab-overview.md)
        + [Beispieldateien](/help/blueprints/labs/aep-foundations/data-ingestion/sample-files.md)
        + Batch-Erfassung{#aep-ingestion-batch}
          + [Übersicht](/help/blueprints/labs/aep-foundations/data-ingestion/batch-ingestion/overview.md)
          + [Datenfluss erstellen](/help/blueprints/labs/aep-foundations/data-ingestion/batch-ingestion/create-dataflow.md)
          + Zuordnen von Daten{#aep-ingestion-batch-mapping}
            + [Übersicht](/help/blueprints/labs/aep-foundations/data-ingestion/batch-ingestion/mapping-data/overview.md)
            + [Passthrough-Zuordnungen korrigieren](/help/blueprints/labs/aep-foundations/data-ingestion/batch-ingestion/mapping-data/fix-passthrough-mappings.md)
            + [Berechnete Felder](/help/blueprints/labs/aep-foundations/data-ingestion/batch-ingestion/mapping-data/calculated-fields.md)
            + [Endgültigen Zuordnungssatz überprüfen](/help/blueprints/labs/aep-foundations/data-ingestion/batch-ingestion/mapping-data/check-final-mapping-set.md)
          + [Datenfluss ausführen](/help/blueprints/labs/aep-foundations/data-ingestion/batch-ingestion/run-dataflow.md)
          + [Debuggen von Fehlern](/help/blueprints/labs/aep-foundations/data-ingestion/batch-ingestion/debugging-errors.md)
          + [Erstellen eines neuen Datenflusses](/help/blueprints/labs/aep-foundations/data-ingestion/batch-ingestion/create-a-new-dataflow.md)
          + [Beheben von Fehlern](/help/blueprints/labs/aep-foundations/data-ingestion/batch-ingestion/fixing-errors.md)
          + [Überprüfung und Validierung](/help/blueprints/labs/aep-foundations/data-ingestion/batch-ingestion/verification-and-validation.md)
        + Stream-Aufnahme{#aep-ingestion-stream}
          + [Übersicht](/help/blueprints/labs/aep-foundations/data-ingestion/stream-ingestion/overview.md)
          + [Einrichten von Source](/help/blueprints/labs/aep-foundations/data-ingestion/stream-ingestion/setup-source.md)
          + [Konfigurieren der Zuordnung](/help/blueprints/labs/aep-foundations/data-ingestion/stream-ingestion/configure-mapping.md)
          + [Endgültigen Zuordnungssatz überprüfen](/help/blueprints/labs/aep-foundations/data-ingestion/stream-ingestion/check-final-mapping-set.md)
          + [Streamen eines Profils](/help/blueprints/labs/aep-foundations/data-ingestion/stream-ingestion/stream-a-profile.md)
          + [Überprüfen des aufgenommenen Profils](/help/blueprints/labs/aep-foundations/data-ingestion/stream-ingestion/verify-ingested-profile.md)
          + [Überwachen und Debuggen von Fehlern](/help/blueprints/labs/aep-foundations/data-ingestion/stream-ingestion/monitoring-and-debugging-errors.md)
          + [Überprüfung und Validierung](/help/blueprints/labs/aep-foundations/data-ingestion/stream-ingestion/verification-and-validation.md)
        + Bonus-Labs{#aep-ingestion-bonus}
          + [Übersicht](/help/blueprints/labs/aep-foundations/data-ingestion/bonus-labs/overview.md)
          + [Beheben von MAPPER-Fehlern für CreateDate](/help/blueprints/labs/aep-foundations/data-ingestion/bonus-labs/fix-mapper-errors-for-createdate.md)
          + [Streamen eines Bestellereignisses](/help/blueprints/labs/aep-foundations/data-ingestion/bonus-labs/stream-an-order-event.md)
          + Verwenden der Data Landing Zone{#aep-ingestion-dlz}
            + [Übersicht](/help/blueprints/labs/aep-foundations/data-ingestion/bonus-labs/using-data-landing-zone/overview.md)
            + [Einrichten von Source](/help/blueprints/labs/aep-foundations/data-ingestion/bonus-labs/using-data-landing-zone/setup-source.md)
            + [Erstellen von Zuordnungen](/help/blueprints/labs/aep-foundations/data-ingestion/bonus-labs/using-data-landing-zone/create-mappings.md)
            + [Datenfluss planen](/help/blueprints/labs/aep-foundations/data-ingestion/bonus-labs/using-data-landing-zone/schedule-dataflow.md)
            + [Wiederholen eines fehlgeschlagenen Datenflusses](/help/blueprints/labs/aep-foundations/data-ingestion/bonus-labs/using-data-landing-zone/retry-a-failed-dataflow.md)
            + Bestellungen laden{#aep-ingestion-dlz-orders}
              + [Übersicht](/help/blueprints/labs/aep-foundations/data-ingestion/bonus-labs/using-data-landing-zone/load-orders/overview.md)
              + [Einrichten von Source](/help/blueprints/labs/aep-foundations/data-ingestion/bonus-labs/using-data-landing-zone/load-orders/setup-source.md)
              + [Erste Zuordnungen](/help/blueprints/labs/aep-foundations/data-ingestion/bonus-labs/using-data-landing-zone/load-orders/initial-mappings.md)
              + [Objektkopie-Zuordnungen](/help/blueprints/labs/aep-foundations/data-ingestion/bonus-labs/using-data-landing-zone/load-orders/object-copy-mappings.md)
              + [Datenfluss überprüfen und planen](/help/blueprints/labs/aep-foundations/data-ingestion/bonus-labs/using-data-landing-zone/load-orders/verify-and-schedule-dataflow.md)
      + Segmentierung und Aktivierung{#aep-segmentation}
        + [Vortrag](/help/blueprints/labs/aep-foundations/segmentation-and-activation/lecture.md)
        + Edge Activation{#aep-segmentation-edge}
          + [Übersicht](/help/blueprints/labs/aep-foundations/segmentation-and-activation/edge-activation/overview.md)
          + [Edge-Zielgruppe erstellen](/help/blueprints/labs/aep-foundations/segmentation-and-activation/edge-activation/create-edge-audience.md)
          + [Edge-Ereignis senden](/help/blueprints/labs/aep-foundations/segmentation-and-activation/edge-activation/send-an-edge-event.md)
          + Einrichten der Ereignisweiterleitung{#aep-segmentation-edge-ef}
            + [Übersicht](/help/blueprints/labs/aep-foundations/segmentation-and-activation/edge-activation/setup-event-forwarding/overview.md)
            + [Eigenschaft erstellen](/help/blueprints/labs/aep-foundations/segmentation-and-activation/edge-activation/setup-event-forwarding/create-property.md)
            + [Erstellen eines Datenstroms](/help/blueprints/labs/aep-foundations/segmentation-and-activation/edge-activation/setup-event-forwarding/create-datastream.md)
      + Zielgruppenbildung{#aep-audiences}
        + Nutzungsszenario 1 - Akquise{#aep-uc1}
          + [Übersicht](/help/blueprints/labs/aep-foundations/audience-building/use-case-1-acquisition/overview.md)
          + Konfigurieren von Zielen{#aep-uc1-destinations}
            + [Einrichten eines benutzerdefinierten Personalization-Ziels](/help/blueprints/labs/aep-foundations/audience-building/use-case-1-acquisition/configure-destinations/setup-custom-personalization-destination.md)
            + [Streaming-Ziel einrichten](/help/blueprints/labs/aep-foundations/audience-building/use-case-1-acquisition/configure-destinations/setup-streaming-destination.md)
          + [Zielgruppe 1 erstellen](/help/blueprints/labs/aep-foundations/audience-building/use-case-1-acquisition/build-audience-1.md)
          + [Zielgruppe 2 erstellen](/help/blueprints/labs/aep-foundations/audience-building/use-case-1-acquisition/build-audience-2.md)
          + [Zielgruppe 3 erstellen](/help/blueprints/labs/aep-foundations/audience-building/use-case-1-acquisition/build-audience-3.md)
          + [Edge-Ereignis senden](/help/blueprints/labs/aep-foundations/audience-building/use-case-1-acquisition/send-an-edge-event.md)
          + [Kritische Denkprüfung](/help/blueprints/labs/aep-foundations/audience-building/use-case-1-acquisition/critical-thinking-review.md)
        + Anwendungsfall 2: Upsell{#aep-uc2}
          + [Übersicht](/help/blueprints/labs/aep-foundations/audience-building/use-case-2-upsell/overview.md)
          + [Vorbereitung](/help/blueprints/labs/aep-foundations/audience-building/use-case-2-upsell/pre-work.md)
          + [Option 1: Aggregieren von Zielgruppen](/help/blueprints/labs/aep-foundations/audience-building/use-case-2-upsell/option-1-using-audiences-to-aggregate.md)
          + [Option 2: Verwenden von Pre-Aggregaten](/help/blueprints/labs/aep-foundations/audience-building/use-case-2-upsell/option-2-use-pre-aggregates.md)
          + [Kritische Denkprüfung](/help/blueprints/labs/aep-foundations/audience-building/use-case-2-upsell/critical-thinking-review.md)
        + Anwendungsfall 3: Kontaktaufnahme{#aep-uc3}
          + [Übersicht](/help/blueprints/labs/aep-foundations/audience-building/use-case-3-outreach/overview.md)
          + [Build-Anwendungsfall 3](/help/blueprints/labs/aep-foundations/audience-building/use-case-3-outreach/build-use-case-3.md)
          + [Kritische Denkprüfung](/help/blueprints/labs/aep-foundations/audience-building/use-case-3-outreach/critical-thinking-review.md)
        + Bonus-Labs{#aep-audiences-bonus}
          + [Übersicht](/help/blueprints/labs/aep-foundations/audience-building/bonus-labs/overview.md)
          + [Auftragsereignis an Hub senden](/help/blueprints/labs/aep-foundations/audience-building/bonus-labs/send-order-event-to-hub.md)
          + [Web-Ereignis an Hub senden](/help/blueprints/labs/aep-foundations/audience-building/bonus-labs/send-web-event-to-hub.md)
          + [Überwachen des Ereignisses](/help/blueprints/labs/aep-foundations/audience-building/bonus-labs/monitor-your-event.md)
    + AJO Foundations{#ajo-foundations}
      + [Übersicht](/help/blueprints/labs/ajo-foundations/overview.md)
      + [Einrichtung](/help/blueprints/labs/ajo-foundations/setup.md)
      + Sandbox-Setup{#ajo-sandbox}
        + [Developer Console-Setup](/help/blueprints/labs/ajo-foundations/sandbox-setup/developer-console-setup.md)
        + [Bereitstellungsanweisungen](/help/blueprints/labs/ajo-foundations/sandbox-setup/deployment-instructions.md)
      + Postman-Setup{#ajo-postman}
        + [Postman-Installation](/help/blueprints/labs/ajo-foundations/postman-setup/postman-installation.md)
        + [Umgebungsdatei importieren](/help/blueprints/labs/ajo-foundations/postman-setup/import-environment-file.md)
        + [API-Sammlung importieren](/help/blueprints/labs/ajo-foundations/postman-setup/import-api-collection.md)
      + Bausteine für Architekturen{#ajo-architecture}
        + [Vortrag](/help/blueprints/labs/ajo-foundations/architecture-building-blocks/lecture.md)
        + Zuordnen von Anwendungsfällen zur Architektur{#ajo-architecture-mapping}
          + [Übersicht](/help/blueprints/labs/ajo-foundations/architecture-building-blocks/mapping-use-cases-to-architecture/overview.md)
          + [Einführung in das Labor](/help/blueprints/labs/ajo-foundations/architecture-building-blocks/mapping-use-cases-to-architecture/lab-introduction.md)
          + [Laborübung](/help/blueprints/labs/ajo-foundations/architecture-building-blocks/mapping-use-cases-to-architecture/lab-exercise.md)
          + [Laborprüfung](/help/blueprints/labs/ajo-foundations/architecture-building-blocks/mapping-use-cases-to-architecture/lab-review.md)
      + Datenspeicher{#ajo-data-stores}
        + [Vorlesung zu Echtzeit-Kundenprofilen](/help/blueprints/labs/ajo-foundations/data-stores/real-time-customer-profile-lecture.md)
        + Profil in Aktion{#ajo-profile}
          + [Übersicht](/help/blueprints/labs/ajo-foundations/data-stores/profile-in-action/overview.md)
          + [Anmelden und Durchsuchen](/help/blueprints/labs/ajo-foundations/data-stores/profile-in-action/login-and-browse.md)
          + [Erstellen eines Datenstroms](/help/blueprints/labs/ajo-foundations/data-stores/profile-in-action/create-datastream.md)
          + [Senden eines Edge-Web-Ereignisses](/help/blueprints/labs/ajo-foundations/data-stores/profile-in-action/send-an-edge-web-event.md)
          + [Profil im Hub validieren](/help/blueprints/labs/ajo-foundations/data-stores/profile-in-action/validate-profile-on-hub.md)
          + [Profil auf Edge validieren](/help/blueprints/labs/ajo-foundations/data-stores/profile-in-action/validate-profile-on-edge.md)
          + [Validieren des Ereignisses im Data Lake](/help/blueprints/labs/ajo-foundations/data-stores/profile-in-action/validate-event-on-data-lake.md)
          + [Momentaufnahme des Profils validieren](/help/blueprints/labs/ajo-foundations/data-stores/profile-in-action/validate-profile-snapshot.md)
          + [Zusammenfassung](/help/blueprints/labs/ajo-foundations/data-stores/profile-in-action/summary.md)
        + [relationale Speichervorlesung](/help/blueprints/labs/ajo-foundations/data-stores/relational-store-lecture.md)
        + Relationaler Speicher in Aktion{#ajo-relational}
          + [Übersicht](/help/blueprints/labs/ajo-foundations/data-stores/relational-store-in-action/overview.md)
          + [Durchsuchen von Schemata](/help/blueprints/labs/ajo-foundations/data-stores/relational-store-in-action/browse-schemas.md)
          + [Profil - Target Dimension](/help/blueprints/labs/ajo-foundations/data-stores/relational-store-in-action/profile-target-dimension.md)
          + [Eine Zielgruppe lesen](/help/blueprints/labs/ajo-foundations/data-stores/relational-store-in-action/read-an-audience.md)
          + [Zusammenfassung](/help/blueprints/labs/ajo-foundations/data-stores/relational-store-in-action/summary.md)
        + E-Mail-Kanäle konfigurieren{#ajo-email}
          + [Übersicht](/help/blueprints/labs/ajo-foundations/data-stores/configure-email-channels/overview.md)
          + [Für Profil konfigurieren](/help/blueprints/labs/ajo-foundations/data-stores/configure-email-channels/configure-for-profile.md)
          + [Konfigurieren von für relationale](/help/blueprints/labs/ajo-foundations/data-stores/configure-email-channels/configure-for-relational.md)
          + [Warten auf aktiven Status](/help/blueprints/labs/ajo-foundations/data-stores/configure-email-channels/waiting-for-active-status.md)
      + Orchestrierte Kampagnen{#ajo-campaigns}
        + [Nachrichtenversand-Lektion](/help/blueprints/labs/ajo-foundations/orchestrated-campaigns/message-delivery-lecture.md)
        + Nachrichtenversand in Aktion{#ajo-campaigns-delivery}
          + [Übersicht](/help/blueprints/labs/ajo-foundations/orchestrated-campaigns/message-delivery-in-action/overview.md)
          + [Erstellen einer Kampagne](/help/blueprints/labs/ajo-foundations/orchestrated-campaigns/message-delivery-in-action/create-a-campaign.md)
          + [Erstellen einer Zielgruppe](/help/blueprints/labs/ajo-foundations/orchestrated-campaigns/message-delivery-in-action/build-an-audience.md)
          + [Aktivität „Verzweigung hinzufügen“](/help/blueprints/labs/ajo-foundations/orchestrated-campaigns/message-delivery-in-action/add-fork-activity.md)
          + [E-Mail-Aktivitäten hinzufügen](/help/blueprints/labs/ajo-foundations/orchestrated-campaigns/message-delivery-in-action/add-email-activities.md)
          + [Testen der Kampagne](/help/blueprints/labs/ajo-foundations/orchestrated-campaigns/message-delivery-in-action/test-the-campaign.md)
          + [Zusammenfassung](/help/blueprints/labs/ajo-foundations/orchestrated-campaigns/message-delivery-in-action/summary.md)
        + [Workflow-Bausteine - Lektion](/help/blueprints/labs/ajo-foundations/orchestrated-campaigns/workflow-building-blocks-lecture.md)
        + Flaggschiff-Telefonstart{#ajo-campaigns-flagship}
          + [Übersicht](/help/blueprints/labs/ajo-foundations/orchestrated-campaigns/flagship-phone-launch/overview.md)
          + [SMS-Kanal konfigurieren](/help/blueprints/labs/ajo-foundations/orchestrated-campaigns/flagship-phone-launch/configure-sms-channel.md)
          + [Erstellen einer orchestrierten Kampagne](/help/blueprints/labs/ajo-foundations/orchestrated-campaigns/flagship-phone-launch/create-an-orchestrated-campaign.md)
          + [Erstellen einer Zielgruppe](/help/blueprints/labs/ajo-foundations/orchestrated-campaigns/flagship-phone-launch/build-an-audience.md)
          + [Ergebnis verzweigen](/help/blueprints/labs/ajo-foundations/orchestrated-campaigns/flagship-phone-launch/fork-the-result.md)
          + [Zielgruppe speichern](/help/blueprints/labs/ajo-foundations/orchestrated-campaigns/flagship-phone-launch/save-the-audience.md)
          + [Zeilen filtern](/help/blueprints/labs/ajo-foundations/orchestrated-campaigns/flagship-phone-launch/filter-the-lines.md)
          + [SMS erstellen](/help/blueprints/labs/ajo-foundations/orchestrated-campaigns/flagship-phone-launch/compose-the-sms.md)
          + [Workflow ausführen](/help/blueprints/labs/ajo-foundations/orchestrated-campaigns/flagship-phone-launch/run-the-workflow.md)
          + [Zusammenfassung](/help/blueprints/labs/ajo-foundations/orchestrated-campaigns/flagship-phone-launch/summary.md)
      + Journeys{#ajo-journeys}
        + [Vortrag](/help/blueprints/labs/ajo-foundations/journeys/lecture.md)
        + Aufregung nach Kauf{#ajo-journeys-post-purchase}
          + [Übersicht](/help/blueprints/labs/ajo-foundations/journeys/post-purchase-excitement/overview.md)
          + [Ereignis konfigurieren](/help/blueprints/labs/ajo-foundations/journeys/post-purchase-excitement/configure-event.md)
          + [Konfigurieren einer benutzerdefinierten Aktion](/help/blueprints/labs/ajo-foundations/journeys/post-purchase-excitement/configure-custom-action.md)
          + [Build-Journey](/help/blueprints/labs/ajo-foundations/journeys/post-purchase-excitement/build-journey.md)
          + [Test-Journey](/help/blueprints/labs/ajo-foundations/journeys/post-purchase-excitement/test-journey.md)
          + [Senden eines Ereignisses](/help/blueprints/labs/ajo-foundations/journeys/post-purchase-excitement/send-an-event.md)
          + [Validieren des erfassten Ereignisses](/help/blueprints/labs/ajo-foundations/journeys/post-purchase-excitement/validate-event-ingested.md)
          + [Journey validieren](/help/blueprints/labs/ajo-foundations/journeys/post-purchase-excitement/validate-journey.md)
          + [Zusammenfassung](/help/blueprints/labs/ajo-foundations/journeys/post-purchase-excitement/summary.md)
      + Entscheidungsfindung{#ajo-decisioning}
        + [Experience Edge](/help/blueprints/labs/ajo-foundations/decisioning/experience-edge.md)
        + Entscheidungsfindung - Erklärung{#ajo-decisioning-explained}
          + [Übersicht](/help/blueprints/labs/ajo-foundations/decisioning/decisioning-explained/overview.md)
          + [Einführung](/help/blueprints/labs/ajo-foundations/decisioning/decisioning-explained/introduction.md)
          + [Entscheidungselement-XDM](/help/blueprints/labs/ajo-foundations/decisioning/decisioning-explained/decision-item-xdm.md)
          + [Erstellung von Entscheidungselementen](/help/blueprints/labs/ajo-foundations/decisioning/decisioning-explained/decision-item-creation.md)
          + [Sammlungen](/help/blueprints/labs/ajo-foundations/decisioning/decisioning-explained/collections.md)
          + [Rangfolgeformeln](/help/blueprints/labs/ajo-foundations/decisioning/decisioning-explained/ranking-formulas.md)
          + [Auswahlstrategien](/help/blueprints/labs/ajo-foundations/decisioning/decisioning-explained/selection-strategies.md)
          + [Entscheidungsrichtlinien](/help/blueprints/labs/ajo-foundations/decisioning/decisioning-explained/decision-policies.md)
          + [Leitplanken, KI-Modelle für zukünftige Entscheidungen](/help/blueprints/labs/ajo-foundations/decisioning/decisioning-explained/guardrails-ai-models-decisioning-future.md)
        + Abgebrochenes Durchsuchen{#ajo-decisioning-abandoned}
          + [Übersicht](/help/blueprints/labs/ajo-foundations/decisioning/abandoned-browse/overview.md)
          + [Entscheidungsregel erstellen](/help/blueprints/labs/ajo-foundations/decisioning/abandoned-browse/create-decision-rule.md)
          + [Angebotsattribute erstellen](/help/blueprints/labs/ajo-foundations/decisioning/abandoned-browse/create-offer-attributes.md)
          + [Erstellen von Angebotselementen](/help/blueprints/labs/ajo-foundations/decisioning/abandoned-browse/create-offer-items.md)
          + [Angebotssammlung erstellen](/help/blueprints/labs/ajo-foundations/decisioning/abandoned-browse/create-offer-collection.md)
          + [Rangfolgenformel erstellen](/help/blueprints/labs/ajo-foundations/decisioning/abandoned-browse/create-ranking-formula.md)
          + [Auswahlstrategie erstellen](/help/blueprints/labs/ajo-foundations/decisioning/abandoned-browse/create-selection-strategy.md)
          + [Erstellen eines Code-basierten Erlebniskanals](/help/blueprints/labs/ajo-foundations/decisioning/abandoned-browse/create-code-based-experience-channel.md)
          + [Erstellen der Journey](/help/blueprints/labs/ajo-foundations/decisioning/abandoned-browse/create-the-journey.md)
          + [Decisioning und CBEs in Aktion](/help/blueprints/labs/ajo-foundations/decisioning/abandoned-browse/decisioning-and-cbes-in-action.md)
          + [Zusammenfassung](/help/blueprints/labs/ajo-foundations/decisioning/abandoned-browse/summary.md)
      + Inhaltserstellung mit KI{#ajo-content-ai}
        + [Vortrag](/help/blueprints/labs/ajo-foundations/content-authoring-with-ai/lecture.md)
        + [Übersicht](/help/blueprints/labs/ajo-foundations/content-authoring-with-ai/overview.md)
        + [Markenverwaltung](/help/blueprints/labs/ajo-foundations/content-authoring-with-ai/brand-management.md)
        + [Erstellen von Inhaltsfragmenten](/help/blueprints/labs/ajo-foundations/content-authoring-with-ai/building-content-fragments.md)
        + [Erstellen einer Inhaltsvorlage](/help/blueprints/labs/ajo-foundations/content-authoring-with-ai/building-content-template.md)
        + [E-Mail erstellen](/help/blueprints/labs/ajo-foundations/content-authoring-with-ai/creating-the-email.md)
        + [KI-Assistent und Content Personalization](/help/blueprints/labs/ajo-foundations/content-authoring-with-ai/ai-assistant-and-content-personalization.md)
        + [Personalization und Inhaltsexperiment](/help/blueprints/labs/ajo-foundations/content-authoring-with-ai/personalization-and-content-experimentation.md)
        + [Content-Simulation](/help/blueprints/labs/ajo-foundations/content-authoring-with-ai/content-simulation.md)
        + [Markenausrichtung](/help/blueprints/labs/ajo-foundations/content-authoring-with-ai/brand-alignment.md)
        + [E-Mail testen](/help/blueprints/labs/ajo-foundations/content-authoring-with-ai/test-the-email.md)
        + [Zusammenfassung](/help/blueprints/labs/ajo-foundations/content-authoring-with-ai/summary.md)
