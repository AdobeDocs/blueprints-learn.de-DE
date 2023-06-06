---
user-guide-title: 'Blueprints: Digitale Erlebnisse'
breadcrumb-title: Blueprints
user-guide-description: Blueprints sind wiederholbare Implementierungen, die bekannte Geschäftsprobleme adressieren und Architekturdiagramme, technische Überlegungen und Links zu relevanter Dokumentation enthalten.
product: adobe experience platform
mini-toc-levels: 3
role: Architect, Developer, User
source-git-commit: 85e3c9060ebbffcab73ee9621f610df1c8ff5bcb
workflow-type: tm+mt
source-wordcount: '255'
ht-degree: 97%

---


# Blueprints: Digitale Erlebnisse {#architecture}

+ [Überblick](/help/blueprints/overview.md)
+ Vertikale Branchen-Blueprints {#vertical-blueprints}
   + [Überblick](/help/blueprints/vertical-blueprints/overview.md)
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
   + [Überblick](/help/blueprints/audience-activation/overview.md)
   + [Anonyme Zielgruppenaktivierung            (AAM)](/help/blueprints/audience-activation/anonymous.md)
   + Aktivierung einer bekannten Kundin/eines bekannten Kunden (RTCDP) {#known-customer-audience-activation}
      + [Überblick](/help/blueprints/audience-activation/known.md)
      + [Aktivierung für Social-Media- und Advertising-Kanäle ](/help/blueprints/audience-activation/advertising-activation.md)
      + [Aktivierung für Datei- und Unternehmens-Streaming-Ziele](/help/blueprints/audience-activation/enterprise-destinations.md)
      + [Customer Activity Hub](/help/blueprints/audience-activation/customer-activity.md)
      + [Segment Match](/help/blueprints/audience-activation/segment-match.md)
   + [Aktivierung mit Experience Cloud-Programmen](/help/blueprints/audience-activation/platform-and-applications.md)
+ B2B: Aktivierung und Marketing {#b2b-activation}
   + [Überblick](/help/blueprints/b2b/overview.md)
   + [B2B: Aktivierung](/help/blueprints/b2b/b2bactivation.md)
   + Integrations-Blueprint für Marketo Engage und Workfront{#marketo-engage-and-workfront-integration-blueprint}
      + [Überblick](/help/blueprints/b2b/marketo-engage-and-workfront-integration-blueprint/overview.md)
      + [Annahme und Erstellung](/help/blueprints/b2b/marketo-engage-and-workfront-integration-blueprint/intake-and-create.md)
      + [Erfolgsgeschichten von Kunden](/help/blueprints/b2b/marketo-engage-and-workfront-integration-blueprint/customer-success-stories.md)
+ Customer Journey Analytics {#customer-journey-analytics}
   + [Überblick](/help/blueprints/customer-journey-analytics/overview.md)
   + [Freigabe von CJA-Zielgruppen für RTCDP](/help/blueprints/customer-journey-analytics/cja-rtcdp.md)
   + [CJA und Journey Optimizer](/help/blueprints/customer-journey-analytics/cja-ajo.md)
+ Customer Journeys {#customer-journeys}
   + [Überblick](/help/blueprints/customer-journeys/overview.md)
   + Journey Optimizer {#journey-optimizer}
      + [Journey Optimizer](/help/blueprints/customer-journeys/journey-optimizer.md)
      + Entscheidungs-Management {#decision-management}
         + [Überblick](/help/blueprints/customer-journeys/decision_management/decision-management-overview.md)
         + [Entscheidungs-Management im Edge](/help/blueprints/customer-journeys/decision_management/decision-management-edge.md)
         + [Entscheidungs-Management am Hub](/help/blueprints/customer-journeys/decision_management/decision-management-hub.md)
      + [Journey Optimizer mit Adobe Campaign](/help/blueprints/customer-journeys/ajo-and-campaign.md)
      + [Drittanbieter-Messaging](/help/blueprints/customer-journeys/3rd-party-messaging.md)
   + Campaign Standard {#campaign-standard}
      + [Campaign Standard](https://experienceleague.adobe.com/docs/campaign-standard.html?lang=de){target="_blank"}
      + [Real-Time CDP mit Adobe Campaign Standard](https://experienceleague.adobe.com/docs/campaign-standard/using/integrating-with-adobe-cloud/adobe-experience-platform/aep-sources-destinations/get-started-sources-destinations.html?lang=de){target="_blank"}
   + Campaign v8 {#campaign-v8}
      + [Campaign v8](/help/blueprints/customer-journeys/campaign-v8.md)
      + [Real-Time CDP mit Adobe Campaign v8](/help/blueprints/customer-journeys/rtcdp-and-campaign-v8.md)
      + [Journey Optimizer mit Adobe Campaign v8](/help/blueprints/customer-journeys/ajo-and-campaign-v8.md)
   + Campaign v7 {#campaign-v7}
      + [Campaign v7](/help/blueprints/customer-journeys/campaign-v7.md)
      + [Real-Time CDP mit Adobe Campaign          v7](/help/blueprints/customer-journeys/rtcdp-and-campaign.md)
      + [Journey Optimizer mit Adobe Campaign v7](/help/blueprints/customer-journeys/ajo-and-campaign-v7.md)
+ Datenerfassung, Datenzugriff und Datenexport {#data-ingestion}
   + [Überblick](/help/blueprints/data-ingestion/overview.md)
   + [: Datenerfassung bei Ereignisweiterleitung für mehrere Sandboxes](/help/blueprints/data-ingestion/multi-sandbox-event-forwarding.md)
   + [Datenvorbereitung und -aufnahme](/help/blueprints/data-ingestion/ingestion.md)
   + [Datenzugriff und Datenexport](/help/blueprints/data-ingestion/egress.md)
   + [Ereignisweiterleitung](/help/blueprints/data-ingestion/server-side-collection.md)
+ Datenanalyse, Datenintelligenz und KI/ML {#data-exploration}
   + [Überblick](/help/blueprints/data-insights/overview.md)
   + [Datenanalyse und Datenintelligenz](/help/blueprints/data-insights/analysis.md)
   + [Benutzerdefinierte Datenwissenschaft zur Profilanreicherung](/help/blueprints/data-insights/data-science.md)
+ Web- und Mobile-Personalisierung {#web-personalization}
   + [Überblick](/help/blueprints/web-personalization/overview.md)
   + [Verhaltensbasierte Personalisierung            - Target](/help/blueprints/web-personalization/behavioral.md)
   + [Personalisierung für bekannte Kunden – Target und RTCDP](/help/blueprints/web-personalization/known-personalization.md)
   + [Entscheidungs-Management](/help/blueprints/web-personalization/decision-management-edge.md)