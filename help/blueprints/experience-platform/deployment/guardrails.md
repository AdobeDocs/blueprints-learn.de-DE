---
title: Leitlinien für Experience Platform und Anwendungen
description: Die Leitlinien definieren die Leistungserwartungen und -auswirkung auf die Komponenten und Services in Adobe Experience Platform und den entsprechenden Anwendungen
solution: Experience Platform
thumbnail: null
exl-id: b64cf3e4-cc5d-4984-8a0f-4736d432b8e1
source-git-commit: a5d127c2a9e18ebbf25012475b9f474c07575362
workflow-type: tm+mt
source-wordcount: '612'
ht-degree: 10%

---


# Leitlinien

Leitplanken spiegeln Systemeinschränkungen, erwartete Latenzen und Leistungserwartungen wider, um die Architektur und die Leistung von Anwendungsfällen für Kunden zu optimieren und Stabilität zu gewährleisten, Fehler oder unerwartete Ergebnisse zu vermeiden.

## Typen von Leitplanken

| Art der Leitplanke | Beschreibung |
|---|---|
| Leistungs-Schutzmaßnahme (weiches Limit) | Die Leistung betreffende Leitplanken sind Nutzungsbeschränkungen, die sich auf den Umfang Ihrer Anwendungsfälle beziehen und die erwartete Leistung unter normalen Bedingungen umreißen. Bei Überschreitung kann es zu Leistungseinbußen und Latenzen kommen. Die Leistung betreffende Leitplanken werden in den Experience League-Dokumenten in den Abschnitten zu den Leitplanken für jede Lösung beschrieben. |
| Statische Grenze (feste Grenze) | Dies sind vom System erzwungene Grenzwerte, die nicht überschritten werden dürfen. Statische Beschränkungen sind in der Regel vertraglich gebunden und im Kundenvertrag und in den [Produktbeschreibungen](https://helpx.adobe.com/legal/product-descriptions.html) beschrieben. |

>[!NOTE]
>
> Leitplanken sind nicht als Service Level Agreements gedacht, sondern als Anleitungen für optimale Konfigurationen und das erwartete Systemverhalten. Alle Leitplanken, bei denen es sich um System- oder vertragliche Beschränkungen oder Service Level Agreements handelt, werden speziell in den Kundenverträgen und Produktbeschreibungen dokumentiert. Wenn Sie mehr über benutzerdefinierte Limits erfahren möchten, wenden Sie sich an Ihren Kundenbetreuer.

>[!NOTE]
>
> Für Anwendungsfälle mit strikter Latenz oder Leistungsanforderungen empfiehlt Adobe, die Details mit Ihrem Adobe-Account-Team und dem Implementierungspartner zu besprechen. Jede Kundeneinrichtung kann je nach Datenaufnahmemuster, Profilanzahl und -reichhaltigkeit, Segmentregeln und Aktivierungskanälen variieren. Daher ist es wichtig, Ihren Anwendungsfall zu entwickeln und zu testen, um seine Leistung zu optimieren und die erwarteten Leistungsmerkmale vollständig zu verstehen.

## Referenzdokumentation zu den Leitlinien für Adobe Experience Platform und Programmen

Die folgenden Seiten enthalten Informationen zu Leitplanken für Funktionen, Services und Programme von Adobe Experience Platform:

**Experience Platform-Anwendungen**

* Übersicht über die [Real-Time CDP-Leitplanken](https://experienceleague.adobe.com/docs/experience-platform/rtcdp/guardrails/overview.html)
* Leitplanken für die Freigabe von [Customer Journey Analytics-Zielgruppen](https://experienceleague.adobe.com/docs/analytics-platform/using/cja-components/audiences/publish.html#latency)
* [Schutzmaßnahmen bei der Datenaufnahme beim Customer Journey Analytics](https://experienceleague.adobe.com/docs/experience-platform/sources/connectors/adobe-applications/analytics.html#what-is-the-expected-latency-for-analytics-data-on-platform%3F)
* [Journey Optimizer-Leitplanken](https://experienceleague.adobe.com/docs/journey-optimizer/using/get-started/guardrails.html)

**Experience Platform-Services**

* [Leitlinien für die Datenaufnahme](https://experienceleague.adobe.com/docs/experience-platform/ingestion/guardrails.html)
* [[!DNL Edge Network] API-Leitplanken](https://experienceleague.adobe.com/docs/experience-platform/edge-network-server-api/guardrails.html)
* [Leitplanken für Echtzeit-Kundenprofil und Segmentierung](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=de)
* [Leitlinien zu Identitäten](https://experienceleague.adobe.com/docs/experience-platform/identity/guardrails.html?lang=de)
* [Leitlinien zu Query Service](https://experienceleague.adobe.com/docs/experience-platform/query/guardrails.html?lang=de)
* [Leiltlinien zur Zielaktivierung](https://experienceleague.adobe.com/docs/experience-platform/destinations/guardrails.html?lang=de)

## End-to-End-Latenzdiagramme {#end-to-end-latency}

### Experience Platform-Edge Network und Hub Primäre beobachtete Latenzen {#edge-hub-latencies}

Das folgende Diagramm zeigt die Latenzen an den primären Edge- und Hub-Standorten, die bei der Architektur von Anwendungsfällen auf der Experience Platform und in Anwendungen zu beachten sind.

Bei ![Experience Platform [!DNL Edge Network] und Hub wurden primäre Latenzen beobachtet.](/help/blueprints/experience-platform/deployment/assets/aep_edge_hub_latency_v1.svg "Primär beobachtete Latenzen von Experience Platform-Edge Network und -Hub"){width="1000" zoomable="yes"}

### Datenaufnahme {#data-ingestion}

Das folgende Diagramm zeigt die erwarteten Werte für die Datenaufnahmelatenz durch [Streaming-Aufnahme](https://experienceleague.adobe.com/docs/experience-platform/ingestion/streaming/overview.html) und [Batch-Aufnahme](https://experienceleague.adobe.com/docs/experience-platform/ingestion/batch/getting-started.html?lang=de) beim Übertragen von Daten in Real-Time CDP. Klicken Sie auf das Bild, um eine Version mit hoher Auflösung anzuzeigen.

![Allgemeine visuelle Übersicht über die Datenaufnahme.](/help/blueprints/experience-platform/deployment/assets/aep_data_flow_guardrails.svg "Datenaufnahme Allgemeine visuelle Übersicht und Latenzwerte"){width="1000" zoomable="yes"}

### Segmentierung {#segmentation}

Das folgende Diagramm zeigt die erwarteten Latenzwerte bei der Arbeit mit Zielgruppen im Segmentierungs-Service [Real-Time CDP](https://experienceleague.adobe.com/docs/experience-platform/segmentation/home.html?lang=de). Klicken Sie auf das Bild, um eine Version mit hoher Auflösung anzuzeigen.

![Segmentierung - Allgemeine visuelle Übersicht.](/help/blueprints/experience-platform/deployment/assets/segmentation_guardrails.svg "Segmentierung: Allgemeine visuelle Übersicht und Latenzwerte"){width="1000" zoomable="yes"}

### Real-time Customer Data Platform und [!DNL Edge Network] {#adobe-edge-latency}

Das folgende Diagramm zeigt die erwarteten Latenzwerte bei der Nutzung der [!DNL Edge Network] - zum Beispiel zur Nutzung von RTCDP-Zielgruppen in [Adobe Target](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/personalization/adobe-target-connection.html?lang=de). Klicken Sie auf das Bild, um eine Version mit hoher Auflösung anzuzeigen.

![Allgemeine visuelle Übersicht über Adobe Edge Network and Experience Platform.](/help/blueprints/experience-platform/deployment/assets/RTCDP_Edge_guardrails.svg "Exportieren von Zielgruppen in Adobe Target - Allgemeine visuelle Übersicht und Latenz"){width="1000" zoomable="yes"}

### Customer Journey Analytics     {#customer-journey-analytics}

Das folgende Diagramm zeigt die erwarteten Latenzwerte bei der Arbeit mit [Customer Journey Analytics](https://experienceleague.adobe.com/docs/analytics-platform/using/cja-overview/cja-overview.html?lang=en). Klicken Sie auf das Bild, um eine Version mit hoher Auflösung anzuzeigen.

![Allgemeine visuelle Übersicht über das Arbeiten mit Customer Journey Analytics.](/help/blueprints/experience-platform/deployment/assets/CJA_guardrails.svg "Arbeiten mit allgemeinen visuellen Customer Journey Analytics-Übersichts- und Latenzwerten"){width="1000" zoomable="yes"}

### Journey Optimizer   {#journey-optimizer}

Das folgende Diagramm zeigt die erwarteten Latenzwerte bei der Arbeit mit [Adobe Journey Optimizer](https://experienceleague.adobe.com/docs/journey-optimizer/using/get-started/get-started.html?lang=en). Klicken Sie auf das Bild, um eine Version mit hoher Auflösung anzuzeigen.

![Allgemeine visuelle Übersicht über die Arbeit mit Adobe Journey Optimizer.](/help/blueprints/experience-platform/deployment/assets/AJO_guardrails.svg "Arbeiten mit Adobe Journey Optimizer - Allgemeine visuelle Übersicht und Latenzwerte"){width="1000" zoomable="yes"}