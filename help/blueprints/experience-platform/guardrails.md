---
title: Leitlinien für Experience Platform und Anwendungen
description: Die Leitlinien definieren die Leistungserwartungen und -auswirkung auf die Komponenten und Services in Adobe Experience Platform und den entsprechenden Anwendungen
solution: Experience Platform
thumbnail: null
exl-id: b64cf3e4-cc5d-4984-8a0f-4736d432b8e1
source-git-commit: 75a0f2a77f39a4320dc4c4b0db918879be099dd3
workflow-type: tm+mt
source-wordcount: '390'
ht-degree: 13%

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

**Experience Platform-Programme**

* Übersicht über die [Real-Time CDP-Leitplanken](https://experienceleague.adobe.com/docs/experience-platform/rtcdp/guardrails/overview.html)
* Leitplanken für die Freigabe von [Customer Journey Analytics-Zielgruppen](https://experienceleague.adobe.com/docs/analytics-platform/using/cja-components/audiences/publish.html#latency)
* [Leitplanken für die Datenaufnahme in Customer Journey Analytics](https://experienceleague.adobe.com/docs/experience-platform/sources/connectors/adobe-applications/analytics.html#what-is-the-expected-latency-for-analytics-data-on-platform%3F)
* [Journey Optimizer-Leitplanken](https://experienceleague.adobe.com/docs/journey-optimizer/using/get-started/guardrails.html)

**Experience Platform-Services**

* [Leitlinien für die Datenaufnahme](https://experienceleague.adobe.com/docs/experience-platform/ingestion/guardrails.html)
* [[!DNL Edge Network] API-Leitplanken](https://experienceleague.adobe.com/docs/experience-platform/edge-network-server-api/guardrails.html)
* [Leitplanken für Echtzeit-Kundenprofil und Segmentierung](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=de)
* [Leitlinien zu Identitäten](https://experienceleague.adobe.com/docs/experience-platform/identity/guardrails.html?lang=de)
* [Leitlinien zu Query Service](https://experienceleague.adobe.com/docs/experience-platform/query/guardrails.html?lang=de)
* [Leiltlinien zur Zielaktivierung](https://experienceleague.adobe.com/docs/experience-platform/destinations/guardrails.html?lang=de)

## End-to-End-Latenzdiagramme {#end-to-end-latency}

### Primäre Latenzen bei Experience Platform Edge Network und Hub {#edge-hub-latencies}

Das folgende Diagramm zeigt die Latenzen an den primären Edge- und Hub-Standorten, die bei der Entwicklung von Anwendungsfällen für Experience Platform und Anwendungen zu beachten sind.

![In Experience Platform [!DNL Edge Network] und Hub wurden primäre Latenzen beobachtet.](/help/blueprints/experience-platform/assets/aep_edge_hub_latency_v1.svg "Von Experience Platform Edge Network und Hub wurden primäre Latenzen beobachtet"){width="1000" zoomable="yes"}