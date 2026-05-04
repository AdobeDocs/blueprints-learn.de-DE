---
title: Leitlinien für Experience Platform und Anwendungen
description: Die Leitlinien definieren die Leistungserwartungen und -auswirkung auf die Komponenten und Services in Adobe Experience Platform und den entsprechenden Anwendungen
solution: Experience Platform
thumbnail: null
exl-id: b64cf3e4-cc5d-4984-8a0f-4736d432b8e1
TQID: https://experienceleague.adobe.com/ZSHbFR3sEy4C-876IU3yN8U5vOUVvDWIP-O3l-wKm78
product_v2:
  - id: edbd1a0e-46c8-49da-8c10-dba9ec80bba9
feature_v2:
  - id: a37e4ecd-c740-426a-addf-cb1b483c5c5a
  - id: c132d929-fa62-4271-803e-b823be07b914
  - id: daec7ead-f475-492a-a3b3-02ae08565d6f
subfeature_v2:
  - id: d1823595-9241-4128-8a33-e4ac3bf08773
  - id: e5ae22e3-a3b0-46ed-804f-9abf1bbe3e74
  - id: ee602049-8a18-43df-9299-a689a025a371
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
source-git-commit: a99add31cc9f485db119ca00426798545e6a7316
workflow-type: tm+mt
source-wordcount: 486
ht-degree: 14%

---

# Leitlinien

Leitplanken spiegeln Systemeinschränkungen, erwartete Latenzen und Leistungserwartungen wider, um die Architektur und die Leistung von Anwendungsfällen für Kunden zu optimieren und Stabilität zu gewährleisten, Fehler oder unerwartete Ergebnisse zu vermeiden.

## Typen von Leitplanken

| Art der Leitplanke | Beschreibung |
|---|---|
| Leistungs-Schutzmaßnahme (weiches Limit) | Die Leistung betreffende Leitplanken sind Nutzungsbeschränkungen, die sich auf den Umfang Ihrer Anwendungsfälle beziehen und die erwartete Leistung unter normalen Bedingungen umreißen. Bei Überschreitung kann es zu Leistungseinbußen und Latenzen kommen. Die Leistung betreffende Leitplanken werden in den Experience League-Dokumenten in den Abschnitten zu den Leitplanken für jede Lösung beschrieben. |
| Statische Grenze (feste Grenze) | Dies sind vom System erzwungene Grenzwerte, die nicht überschritten werden dürfen. Statische Beschränkungen sind in der Regel vertraglich gebunden und im Kundenvertrag und in den [Produktbeschreibungen](https://helpx.adobe.com/de/legal/product-descriptions.html) beschrieben. |

>[!NOTE]
>
> Leitplanken sind nicht als Service Level Agreements gedacht, sondern als Anleitungen für optimale Konfigurationen und das erwartete Systemverhalten. Alle Leitplanken, bei denen es sich um System- oder vertragliche Beschränkungen oder Service Level Agreements handelt, werden speziell in den Kundenverträgen und Produktbeschreibungen dokumentiert. Wenn Sie mehr über benutzerdefinierte Limits erfahren möchten, wenden Sie sich an Ihren Kundenbetreuer.

>[!NOTE]
>
> Für Anwendungsfälle mit strikter Latenz oder Leistungsanforderungen empfiehlt Adobe, die Details mit Ihrem Adobe-Account-Team und dem Implementierungspartner zu besprechen. Jede Kundeneinrichtung kann je nach Datenaufnahmemuster, Profilanzahl und -reichhaltigkeit, Segmentregeln und Aktivierungskanälen variieren. Daher ist es wichtig, Ihren Anwendungsfall zu entwickeln und zu testen, um seine Leistung zu optimieren und die erwarteten Leistungsmerkmale vollständig zu verstehen.

## Referenzdokumentation zu den Leitlinien für Adobe Experience Platform und Programmen

Die folgenden Seiten enthalten Informationen zu Leitplanken für Funktionen, Services und Programme von Adobe Experience Platform:

**Experience Platform-Programme**

* [Übersicht über Real-Time CDP-Schutzmechanismen](https://experienceleague.adobe.com/docs/experience-platform/rtcdp/guardrails/overview.html?lang=de)
* [Leitplanken für die Freigabe von Customer Journey Analytics-Zielgruppen](https://experienceleague.adobe.com/docs/analytics-platform/using/cja-components/audiences/publish.html?lang=de#latency)
* [Leitplanken für die Datenaufnahme in Customer Journey Analytics](https://experienceleague.adobe.com/docs/experience-platform/sources/connectors/adobe-applications/analytics.html?lang=de#what-is-the-expected-latency-for-analytics-data-on-platform%3F)
* [Journey Optimizer-Leitplanken](https://experienceleague.adobe.com/docs/journey-optimizer/using/get-started/guardrails.html?lang=de)

**Experience Platform-Services**

* [Leitplanken für die Datenaufnahme](https://experienceleague.adobe.com/docs/experience-platform/ingestion/guardrails.html?lang=de)
* [[!DNL Edge Network] API-Leitplanken](https://experienceleague.adobe.com/docs/experience-platform/edge-network-server-api/guardrails.html)
* [Leitplanken für Echtzeit-Kundenprofil und Segmentierung](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=de)
* [Identitäts-Leitplanken](https://experienceleague.adobe.com/docs/experience-platform/identity/guardrails.html?lang=de)
* [Leitplanken für den Abfrage-Service](https://experienceleague.adobe.com/docs/experience-platform/query/guardrails.html?lang=de)
* [Leitplanken für die Zielaktivierung](https://experienceleague.adobe.com/docs/experience-platform/destinations/guardrails.html?lang=de)

## End-to-End-Latenzdiagramme {#end-to-end-latency}

### Primäre Latenzen bei Experience Platform Edge Network und Hub {#edge-hub-latencies}

Das folgende Diagramm zeigt die Latenzen an den primären Edge- und Hub-Standorten, die bei der Entwicklung von Anwendungsfällen für Experience Platform und Anwendungen zu beachten sind.

![In Experience Platform [!DNL Edge Network] und Hub wurden primäre Latenzen beobachtet.](/help/blueprints/experience-platform/assets/aep_edge_hub_latency_v1.svg "Von Experience Platform Edge Network und Hub wurden primäre Latenzen beobachtet"){width="1000" zoomable="yes"}