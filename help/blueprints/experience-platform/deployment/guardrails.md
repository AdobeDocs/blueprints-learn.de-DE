---
title: Leitlinien für Experience Platform und Anwendungen
description: Die Leitlinien definieren die Leistungserwartungen und -auswirkung auf die Komponenten und Services in Adobe Experience Platform und den entsprechenden Anwendungen
solution: Customer Journey Analytics, Journey Orchestration, Real-Time Customer Data Platform
thumbnail: null
exl-id: b64cf3e4-cc5d-4984-8a0f-4736d432b8e1
source-git-commit: 60a7785ea0ec4ee83fd9a1e843f0b84fc4cb1150
workflow-type: tm+mt
source-wordcount: '680'
ht-degree: 15%

---

# Leitlinien

Limits sind empfohlene Schwellenwerte für Daten, beobachtete Latenzen und die Systemnutzung in Adobe Experience Platform und Anwendungen. Limits spiegeln Systemeinschränkungen und Leistungserwartungen wider, um die Kundenarchitektur und die Leistung von Anwendungsfällen zu optimieren und Fehler oder unerwartete Ergebnisse zu vermeiden. Limits sind nicht als Service Level Agreement vorgesehen, Service Level Agreements sind in den unten stehenden Produktbeschreibungen sowie in den Lizenzvereinbarungen für Kunden dokumentiert. Limits sollen bei der Architektur von Lösungen für spezifische Anwendungsfälle des Kunden Hinweise geben, um Stabilität und Ausführung zu gewährleisten.

Informationen zu spezifischen Service-Level-Vereinbarungen für Anwendungen und Funktionen finden Sie im Abschnitt [Beschreibung der Anwendungen und Funktionen](#application-feature-descriptions) unten auf dieser Seite.

Beachten Sie, dass Adobe bei allen Kundenanwendungsfällen mit strengen Latenz- oder Volumenanforderungen empfiehlt, Ihr Anwendungsbeispiel gemeinsam mit Ihrem Adobe-Account-Team und Implementierungspartner sorgfältig zu überprüfen. In bestimmten Fällen ist es ratsam, die Implementierung eines bestimmten Anwendungsfalls vor dem Start des Anwendungsfalls zu testen und zu beobachten, um das erwartete Verhalten zu beobachten und zu verstehen - da jede Kundenimplementierung unterschiedliche Faktoren spielt, einschließlich der Art und Häufigkeit der Datenerfassung, der Details der zu erstellenden Segmentregeln und der verschiedenen Aktivierungskanäle und Nutzlasten - wird jede Implementierung eines Anwendungsfalls eine unterschiedliche Performance aufweisen. Daher ist es am besten, die erwartete Leistung vorab festzulegen und zu testen, um eine ordnungsgemäße Architektur und Implementierung entsprechend den Latenz- und Leistungsanforderungen des Anwendungsfalls sicherzustellen.


## Referenzdokumentation zu den Leitlinien für Adobe Experience Platform und Programmen

Auf den folgenden Seiten finden Sie Informationen zu Limits für Adobe Experience Platform-Funktionen, -Dienste und -Anwendungen:

**Experience Platform-Anwendungen**

* [Übersicht über Real-Time CDP-Limits](https://experienceleague.adobe.com/docs/experience-platform/rtcdp/guardrails/overview.html)
* [Limits bei der Freigabe von Customer Journey Analytics-Zielgruppen](https://experienceleague.adobe.com/docs/analytics-platform/using/cja-components/audiences/publish.html#latency)
* [Limits bei der Customer Journey Analytics-Datenerfassung](https://experienceleague.adobe.com/docs/experience-platform/sources/connectors/adobe-applications/analytics.html#what-is-the-expected-latency-for-analytics-data-on-platform%3F)
* [Limits in Journey Optimizer](https://experienceleague.adobe.com/docs/journey-optimizer/using/get-started/guardrails.html)

**Experience Platform-Dienste**

* [Leitlinien für die Datenaufnahme](https://experienceleague.adobe.com/docs/experience-platform/ingestion/guardrails.html)
* [[!DNL Edge Network] API-Limits](https://experienceleague.adobe.com/docs/experience-platform/edge-network-server-api/guardrails.html)
* [Limits für das Echtzeit-Kundenprofil und die Segmentierung](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=de)
* [Leitlinien zu Identitäten](https://experienceleague.adobe.com/docs/experience-platform/identity/guardrails.html?lang=de)
* [Leitlinien zu Query Service](https://experienceleague.adobe.com/docs/experience-platform/query/guardrails.html?lang=de)
* [Leiltlinien zur Zielaktivierung](https://experienceleague.adobe.com/docs/experience-platform/destinations/guardrails.html?lang=de)

## End-to-End-Latenzdiagramme {#end-to-end-latency}

### Primäre Latenzen für Experience Platform Edge Network und Hub {#edge-hub-latencies}

Das folgende Diagramm zeigt die beobachteten primären Edge- und Hub-Latenzen, die bei der Architektur von Anwendungsfällen auf Experience Platform und Anwendungen berücksichtigt werden sollten.

![Experience Platform [!DNL Edge Network] primär beobachtete Latenzen in Hub.](/help/blueprints/experience-platform/deployment/assets/aep_edge_hub_latency.svg "Experience Platform Edge Network- und Hub-primäre beobachtete Latenzen"){width="1000" zoomable="yes"}

### Datenaufnahme {#data-ingestion}

Das folgende Diagramm zeigt erwartete Datenaufnahme-Latenzwerte durch [Streaming-Erfassung](https://experienceleague.adobe.com/docs/experience-platform/ingestion/streaming/overview.html) und [Batch-Erfassung](https://experienceleague.adobe.com/docs/experience-platform/ingestion/batch/getting-started.html?lang=de) beim Einbringen von Daten in Real-Time CDP. Klicken Sie auf das Bild, um eine hochauflösende Version anzuzeigen.

![Allgemeine visuelle Übersicht über die Datenerfassung.](/help/blueprints/experience-platform/deployment/assets/aep_data_flow_guardrails.svg "Allgemeine visuelle Übersicht über die Datenerfassung und Latenzwerte"){width="1000" zoomable="yes"}

### Segmentierung {#segmentation}

Das folgende Diagramm zeigt erwartete Latenzwerte beim Arbeiten mit Zielgruppen in der [Real-Time CDP-Segmentierungsdienst](https://experienceleague.adobe.com/docs/experience-platform/segmentation/home.html?lang=de). Klicken Sie auf das Bild, um eine hochauflösende Version anzuzeigen.

![Visuelle Übersicht über die Segmentierung auf hoher Ebene.](/help/blueprints/experience-platform/deployment/assets/segmentation_guardrails.svg "Visuelle Segmentierung auf oberster Ebene - Überblick und Latenzwerte"){width="1000" zoomable="yes"}

### REAL-TIME CUSTOMER DATA PLATFORM &amp; [!DNL Edge Network] {#adobe-edge-latency}

Das folgende Diagramm zeigt erwartete Latenzwerte bei der Nutzung der Variablen [!DNL Edge Network] - zum Beispiel zur Nutzung von RTCDP-Zielgruppen in [Adobe Target](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/personalization/adobe-target-connection.html?lang=de). Klicken Sie auf das Bild, um eine hochauflösende Version anzuzeigen.

![Adobe Edge Network und Experience Platform - Überblick über die allgemeine Benutzeroberfläche.](/help/blueprints/experience-platform/deployment/assets/RTCDP_Edge_guardrails.svg "Exportieren von Zielgruppen in Adobe Target - Allgemeine visuelle Übersicht und Latenz"){width="1000" zoomable="yes"}

### Customer Journey Analytics     {#customer-journey-analytics}

Das folgende Diagramm zeigt erwartete Latenzwerte bei der Arbeit mit [Customer Journey Analytics](https://experienceleague.adobe.com/docs/analytics-platform/using/cja-overview/cja-overview.html?lang=en). Klicken Sie auf das Bild, um eine hochauflösende Version anzuzeigen.

![Arbeiten mit einer allgemeinen visuellen Customer Journey Analytics-Übersicht.](/help/blueprints/experience-platform/deployment/assets/CJA_guardrails.svg "Arbeiten mit einer allgemeinen visuellen Customer Journey Analytics-Übersicht und Latenzwerten"){width="1000" zoomable="yes"}

### Journey Optimizer   {#journey-optimizer}

Das folgende Diagramm zeigt erwartete Latenzwerte bei der Arbeit mit [Adobe Journey Optimizer](https://experienceleague.adobe.com/docs/journey-optimizer/using/get-started/get-started.html?lang=en). Klicken Sie auf das Bild, um eine hochauflösende Version anzuzeigen.

![Arbeiten mit einer allgemeinen visuellen Übersicht über Adobe Journey Optimizer.](/help/blueprints/experience-platform/deployment/assets/AJO_guardrails.svg "Arbeiten mit Adobe Journey Optimizer - Allgemeine visuelle Übersicht und Latenzwerte"){width="1000" zoomable="yes"}

## Beschreibung der Anwendungen und Funktionen {#application-feature-descriptions}

Informationen zu funktionsspezifischen Service-Level-Vereinbarungen finden Sie in den folgenden Produktbeschreibungen:

* [Experience Platform Collection Enterprise](https://helpx.adobe.com/de/legal/product-descriptions/adobe-experience-platform-collection-enterprise.html)
* [Real-time Customer Data Platform](https://helpx.adobe.com/de/legal/product-descriptions/real-time-customer-data-platform.html)
* [B2B-Kundendatenplattform](https://helpx.adobe.com/de/legal/product-descriptions/adobe-experience-platform-b2b.html)
* [Experience Platform Activation](https://helpx.adobe.com/de/legal/product-descriptions/adobe-experience-platform0.html)
* [Experience Platform Intelligence](https://helpx.adobe.com/de/legal/product-descriptions/adobe-experience-platform-intelligence---product-description.html)
* [Intelligent Services](https://helpx.adobe.com/de/legal/product-descriptions/intelligent-services.html)
* [Data Distiller](https://helpx.adobe.com/de/legal/product-descriptions/data-distiller.html)
* [Customer Journey Analytics](https://helpx.adobe.com/de/legal/product-descriptions/customer-journey-analytics.html)
* [Journey Optimizer](https://helpx.adobe.com/de/legal/product-descriptions/adobe-journey-optimizer.html)
* [Journey Orchestration](https://helpx.adobe.com/de/legal/product-descriptions/journey-orchestration.html)
* [Offer Decisioning](https://helpx.adobe.com/de/legal/product-descriptions/offer-decisioning-app-service.html)
