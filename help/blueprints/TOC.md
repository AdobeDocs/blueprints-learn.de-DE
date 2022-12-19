---
user-guide-title: 'Blueprints: Digitale Erlebnisse'
breadcrumb-title: Blueprints
user-guide-description: Blueprints sind wiederholbare Implementierungen, die bekannte Geschäftsprobleme adressieren und Architekturdiagramme, technische Überlegungen und Links zu relevanter Dokumentation enthalten.
product: adobe experience platform
mini-toc-levels: 3
role: Architect, Developer, User
source-git-commit: e07ff74f901932c42ddaf6cb36b557535b9a2c43
workflow-type: tm+mt
source-wordcount: '262'
ht-degree: 94%

---


# Blueprints: Digitale Erlebnisse {#architecture}

+ [Übersicht](/help/blueprints/overview.md)
+ Vertikale Branchen-Blueprints {#vertical-blueprints}
   + [Übersicht](/help/blueprints/vertical-blueprints/overview.md)
   + [Bekleidung](/help/blueprints/vertical-blueprints/apparel.md)
   + [Einzelhandel](/help/blueprints/vertical-blueprints/retail.md)
   + [Telekommunikation](/help/blueprints/vertical-blueprints/telecommunications.md)
   + [Tourismus und Gastgewerbe](/help/blueprints/vertical-blueprints/travel-hospitality.md)
+ Architekturübersicht {#architecture-overview}
   + [Experience Cloud](/help/blueprints/experience-platform/experience-cloud.md)
   + [Experience Platform und Programme](/help/blueprints/experience-platform/platform-applications.md)
   + [Datenfluss in Experience Platform](/help/blueprints/experience-platform/platform-data-flow.md)
   + Implementierung {#deployment}
      + [Experience Platform Web SDK und Edge Network](/help/blueprints/experience-platform/deployment/websdk.md)
      + [Anwendungs-SDKs](/help/blueprints/experience-platform/deployment/appsdk.md)
      + [Leitlinien](/help/blueprints/experience-platform/deployment/guardrails.md)
+ Aktivierung von Zielgruppen und Profilen {#audience-activation}
   + [Übersicht](/help/blueprints/audience-activation/overview.md)
   + [Anonyme Zielgruppenaktivierung       (AAM)](/help/blueprints/audience-activation/anonymous.md)
   + Aktivierung eines bekannten Kunden (RTCDP) {#known-customer-audience-activation}
      + [Übersicht](/help/blueprints/audience-activation/known.md)
      + Aktivierung für Social-Media- und Advertising-Kanäle {#audience-activation}
         + [Aktivierung für Facebook Custom Audiences](/help/blueprints/audience-activation/destinations/facebook.md)
         + [Aktivierung für Google Customer Match](/help/blueprints/audience-activation/destinations/gcm.md)
      + [Aktivierung für Datei- und Unternehmens-Streaming-Ziele](/help/blueprints/audience-activation/enterprise-destinations.md)
      + [Customer Activity Hub](/help/blueprints/audience-activation/customer-activity.md)
      + [Segment Match](/help/blueprints/audience-activation/segment-match.md)
   + [Aktivierung mit Experience Cloud-Programmen](/help/blueprints/audience-activation/platform-and-applications.md)
+ B2B: Aktivierung und Marketing {#b2b-activation}
   + [Übersicht](/help/blueprints/b2b/overview.md)
   + [B2B: Aktivierung](/help/blueprints/b2b/b2bactivation.md)
+ Customer Journey Analytics {#customer-journey-analytics}
   + [Übersicht](/help/blueprints/customer-journey-analytics/overview.md)
   + [Freigabe von CJA-Zielgruppen für RTCDP](/help/blueprints/customer-journey-analytics/cja-rtcdp.md)
   + [CJA und Journey Optimizer](/help/blueprints/customer-journey-analytics/cja-ajo.md)
+ Customer Journeys {#customer-journeys}
   + [Übersicht](/help/blueprints/customer-journeys/overview.md)
   + Journey Optimizer {#journey-optimizer}
      + [Journey Optimizer](/help/blueprints/customer-journeys/journey-optimizer.md)
      + Entscheidungs-Management {#decision-management}
         + [Übersicht](/help/blueprints/customer-journeys/decision_management/decision-management-overview.md)
         + [Entscheidungs-Management im Edge](/help/blueprints/customer-journeys/decision_management/decision-management-edge.md)
         + [Entscheidungs-Management am Hub](/help/blueprints/customer-journeys/decision_management/decision-management-hub.md)
      + [Journey Optimizer mit Adobe Campaign](/help/blueprints/customer-journeys/ajo-and-campaign.md)
      + [Drittanbieter-Messaging](/help/blueprints/customer-journeys/3rd-party-messaging.md)
   + Campaign Standard {#campaign-standard}
      + [Campaign Standard](https://experienceleague.adobe.com/docs/campaign-standard.html?lang=de)
      + [Real-Time CDP mit Adobe Campaign Standard](https://experienceleague.adobe.com/docs/campaign-standard/using/integrating-with-adobe-cloud/adobe-experience-platform/aep-sources-destinations/get-started-sources-destinations.html?lang=de)
   + Campaign v8 {#campaign-v8}
      + [Campaign v8](/help/blueprints/customer-journeys/campaign-v8.md)
      + [Real-Time CDP mit Adobe Campaign v8](/help/blueprints/customer-journeys/rtcdp-and-campaign-v8.md)
      + [Journey Optimizer mit Adobe Campaign v8](/help/blueprints/customer-journeys/ajo-and-campaign-v8.md)
   + Campaign v7 {#campaign-v7}
      + [Campaign v7](/help/blueprints/customer-journeys/campaign-v7.md)
      + [Real-Time CDP mit Adobe Campaign     v7](/help/blueprints/customer-journeys/rtcdp-and-campaign.md)
      + [Journey Optimizer mit Adobe Campaign v7](/help/blueprints/customer-journeys/ajo-and-campaign-v7.md)
+ Datenerfassung, Datenzugriff und Datenexport {#data-ingestion}
   + [Übersicht](/help/blueprints/data-ingestion/overview.md)
   + [Datenvorbereitung und -aufnahme](/help/blueprints/data-ingestion/ingestion.md)
   + [Datenzugriff und Datenexport](/help/blueprints/data-ingestion/egress.md)
   + [Ereignisweiterleitung](/help/blueprints/data-ingestion/server-side-collection.md)
+ Datenanalyse, Datenintelligenz und KI/ML {#data-exploration}
   + [Übersicht](/help/blueprints/data-insights/overview.md)
   + [Datenanalyse und Datenintelligenz](/help/blueprints/data-insights/analysis.md)
   + [Benutzerdefinierte Datenwissenschaft zur Profilanreicherung](/help/blueprints/data-insights/data-science.md)
+ Optimieren der Kampagnenlieferkette mit Marketo und Workfront{#optimize-campaign-supply-chain-with-marketo-and-workfront}
   + [Übersicht](/help/blueprints/optimize-campaign-supply-chain-with-marketo-and-workfront/overview.md)
   + [Kundenerfolgsgeschichten](/help/blueprints/optimize-campaign-supply-chain-with-marketo-and-workfront/customer-success-stories.md)
   + [Aufnahme und Erstellung](/help/blueprints/optimize-campaign-supply-chain-with-marketo-and-workfront/intake-and-create.md)
+ Web- und Mobile-Personalisierung {#web-personalization}
   + [Übersicht](/help/blueprints/web-personalization/overview.md)
   + [Verhaltensbasierte Personalisierung       - Target](/help/blueprints/web-personalization/behavioral.md)
   + [Personalisierung für bekannte Kunden – Target und RTCDP](/help/blueprints/web-personalization/known-personalization.md)
   + [Entscheidungs-Management](/help/blueprints/web-personalization/decision-management-edge.md)