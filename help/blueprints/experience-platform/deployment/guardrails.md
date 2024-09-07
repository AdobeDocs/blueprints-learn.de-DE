---
title: Leitlinien für Experience Platform und Anwendungen
description: Die Leitlinien definieren die Leistungserwartungen und -auswirkung auf die Komponenten und Services in Adobe Experience Platform und den entsprechenden Anwendungen
solution: Customer Journey Analytics, Journey Orchestration, Real-Time Customer Data Platform
thumbnail: null
exl-id: b64cf3e4-cc5d-4984-8a0f-4736d432b8e1
source-git-commit: 8ab82995ad7762f8ed6f706aa4c4fe59d47abb20
workflow-type: tm+mt
source-wordcount: '612'
ht-degree: 10%

---


# Leitlinien

Limits spiegeln Systembeschränkungen, erwartete Latenzen und Leistungserwartungen wider, um die Kundenarchitektur und die Anwendungsfallleistung zu optimieren und Stabilität zu gewährleisten, Fehler oder unerwartete Ergebnisse zu vermeiden.

## Arten von Limits

| Schutztyp | Beschreibung |
|---|---|
| Leistungsgarantie (weiche Begrenzung) | Leistungsgarantien sind Nutzungsbeschränkungen, die sich auf das Scoping Ihrer Anwendungsfälle beziehen und die erwartete Leistung unter normalen Bedingungen beschreiben. Bei einer Überschreitung können Leistungseinbußen und Latenzzeiten auftreten. Performance-Limits werden in den Experience League-Dokumenten unter den Limits für die einzelnen Lösungen dokumentiert, wie nachfolgend beschrieben. |
| Statische Beschränkung (Hardbounce) | Hierbei handelt es sich um systemerzwungene Beschränkungen, die nicht überschritten werden können. Statische Beschränkungen sind in der Regel vertraglich gebunden und im Kundenvertrag und in den [Produktbeschreibungen](https://helpx.adobe.com/legal/product-descriptions.html) beschrieben. |

>[!NOTE]
>
> Limits sind nicht als Service Level Agreements gedacht, sondern als Orientierung für optimale Konfigurationen und erwartetes Systemverhalten. Sämtliche Garantien, die System- oder vertragliche Beschränkungen oder Service Level Agreements sind, werden speziell in den Kundenverträgen und Produktbeschreibungen dokumentiert. Wenden Sie sich an Ihren Kundenbetreuer, wenn Sie mehr über benutzerdefinierte Beschränkungen erfahren möchten.

>[!NOTE]
>
> Für Anwendungsfälle mit strikter Latenz oder Leistungsanforderungen empfiehlt Adobe, die Details mit Ihrem Adobe-Account-Team und Implementierungspartner zu besprechen. Jedes Kundensetup kann je nach Datenerfassungsmuster, Profilzählungen und Reichweite, Segmentregeln und Aktivierungskanälen variieren. Daher ist es wichtig, Ihren Anwendungsfall zu konstruieren und zu testen, um die Leistung zu optimieren und die erwarteten Leistungsmerkmale vollständig zu verstehen.

## Referenzdokumentation zu den Leitlinien für Adobe Experience Platform und Programmen

Auf den folgenden Seiten finden Sie Informationen zu Limits für Adobe Experience Platform-Funktionen, -Dienste und -Anwendungen:

**Experience Platform Applications**

* [Übersicht über die Limits in Real-Time CDP](https://experienceleague.adobe.com/docs/experience-platform/rtcdp/guardrails/overview.html)
* [Customer Journey Analytics Zielgruppenfreigabe-Limits](https://experienceleague.adobe.com/docs/analytics-platform/using/cja-components/audiences/publish.html#latency)
* [Limits bei der Datenerfassung durch Customer Journey Analytics](https://experienceleague.adobe.com/docs/experience-platform/sources/connectors/adobe-applications/analytics.html#what-is-the-expected-latency-for-analytics-data-on-platform%3F)
* [Journey Optimizer-Limits](https://experienceleague.adobe.com/docs/journey-optimizer/using/get-started/guardrails.html)

**Experience Platform services**

* [Leitlinien für die Datenaufnahme](https://experienceleague.adobe.com/docs/experience-platform/ingestion/guardrails.html)
* [[!DNL Edge Network] API-Limits](https://experienceleague.adobe.com/docs/experience-platform/edge-network-server-api/guardrails.html)
* [Limits für das Echtzeit-Kundenprofil und die Segmentierung](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=de)
* [Leitlinien zu Identitäten](https://experienceleague.adobe.com/docs/experience-platform/identity/guardrails.html?lang=de)
* [Leitlinien zu Query Service](https://experienceleague.adobe.com/docs/experience-platform/query/guardrails.html?lang=de)
* [Leiltlinien zur Zielaktivierung](https://experienceleague.adobe.com/docs/experience-platform/destinations/guardrails.html?lang=de)

## End-to-End-Latenzdiagramme {#end-to-end-latency}

### Primäre Latenzen bei Experience Platform-Edge Network und Hub-Überwachung {#edge-hub-latencies}

Das folgende Diagramm zeigt die beobachteten primären Edge- und Hub-Latenzen, die bei der Architektur von Anwendungsfällen auf Experience Platform und Anwendungen berücksichtigt werden sollten.

![Experience Platform [!DNL Edge Network] und primäre beobachtete Latenzen der Nabe.](/help/blueprints/experience-platform/deployment/assets/aep_edge_hub_latency_v1.svg "Experience Platform Edge Network- und Hub-primäre beobachtete Latenzen"){width="1000" zoomable="yes"}

### Datenaufnahme {#data-ingestion}

Das folgende Diagramm zeigt die erwarteten Datenerfassungslatenzwerte über die [Streaming-Erfassung](https://experienceleague.adobe.com/docs/experience-platform/ingestion/streaming/overview.html) und die [Batch-Erfassung](https://experienceleague.adobe.com/docs/experience-platform/ingestion/batch/getting-started.html?lang=de) beim Einbringen von Daten in Real-Time CDP. Klicken Sie auf das Bild, um eine hochauflösende Version anzuzeigen.

![Allgemeine visuelle Übersicht über die Datenerfassung.](/help/blueprints/experience-platform/deployment/assets/aep_data_flow_guardrails.svg "Allgemeine visuelle Übersicht über die Datenerfassung und Latenzwerte"){width="1000" zoomable="yes"}

### Segmentierung {#segmentation}

Das folgende Diagramm zeigt erwartete Latenzwerte beim Arbeiten mit Zielgruppen im [Real-Time CDP-Segmentierungsdienst](https://experienceleague.adobe.com/docs/experience-platform/segmentation/home.html?lang=de). Klicken Sie auf das Bild, um eine hochauflösende Version anzuzeigen.

![Allgemeine visuelle Übersicht über die Segmentierung.](/help/blueprints/experience-platform/deployment/assets/segmentation_guardrails.svg "Visuelle Übersicht über die Segmentierung auf hoher Ebene und Latenzwerte"){width="1000" zoomable="yes"}

### Real-time Customer Data Platform &amp; [!DNL Edge Network] {#adobe-edge-latency}

Das folgende Diagramm zeigt erwartete Latenzwerte bei der Nutzung von [!DNL Edge Network] - z. B. zur Nutzung von RTCDP-Zielgruppen in [Adobe Target](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/personalization/adobe-target-connection.html?lang=de). Klicken Sie auf das Bild, um eine hochauflösende Version anzuzeigen.

![Adobe Edge-Netzwerk und Experience Platform - Überblick auf hoher Ebene.](/help/blueprints/experience-platform/deployment/assets/RTCDP_Edge_guardrails.svg "Exportieren von Zielgruppen in Adobe Target - Überblick und Latenz auf hoher Ebene"){width="1000" zoomable="yes"}

### Customer Journey Analytics     {#customer-journey-analytics}

Das folgende Diagramm zeigt die erwarteten Latenzwerte bei der Arbeit mit [Customer Journey Analytics](https://experienceleague.adobe.com/docs/analytics-platform/using/cja-overview/cja-overview.html?lang=en). Klicken Sie auf das Bild, um eine hochauflösende Version anzuzeigen.

![Arbeiten mit einer visuellen Übersicht auf hoher Ebene mit Customer Journey Analytics.](/help/blueprints/experience-platform/deployment/assets/CJA_guardrails.svg "Arbeiten mit Customer Journey Analytics einer allgemeinen visuellen Übersicht und Latenzwerten"){width="1000" zoomable="yes"}

### Journey Optimizer   {#journey-optimizer}

Das folgende Diagramm zeigt die erwarteten Latenzwerte bei der Arbeit mit [Adobe Journey Optimizer](https://experienceleague.adobe.com/docs/journey-optimizer/using/get-started/get-started.html?lang=en). Klicken Sie auf das Bild, um eine hochauflösende Version anzuzeigen.

![Arbeiten mit einer allgemeinen visuellen Übersicht über Adobe Journey Optimizer.](/help/blueprints/experience-platform/deployment/assets/AJO_guardrails.svg "Arbeiten mit Adobe Journey Optimizer - Überblick und Latenzwerten auf hoher Ebene"){width="1000" zoomable="yes"}