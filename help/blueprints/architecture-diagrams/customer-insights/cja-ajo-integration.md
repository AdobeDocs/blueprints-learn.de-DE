---
title: Integration von Adobe Customer Journey Analytics und Adobe Journey Optimizer
description: Architektur zur Analyse von Adobe Journey Optimizer Campaign- und Journey-Insights in Adobe Customer Journey Analytics und zur Veröffentlichung von Zielgruppen zurück für die Journey-Ausführung.
solution: Customer Journey Analytics, Journey Optimizer, Experience Platform
product_v2:
  - id: e98b7246-966c-4318-9e95-cad2f7a17dc7
    internal-label: Customer Journey Analytics
  - id: cb954087-f4fc-4456-afb9-e939cabcdc79
    internal-label: Journey Optimizer
  - id: edbd1a0e-46c8-49da-8c10-dba9ec80bba9
    internal-label: Experience Platform
source-git-commit: 1d6ba1444c119437eb8a86d5c4a1050d56d16023
workflow-type: tm+mt
source-wordcount: '264'
ht-degree: 0%
---
# Integration von Adobe Customer Journey Analytics und Adobe Journey Optimizer

Diese Architektur zeigt, wie Versand- und Interaktionsdaten von Adobe Journey Optimizer über Adobe Experience Platform in Customer Journey Analytics fließen, um Einblicke in Campaign und Journey zu erhalten. In Customer Journey Analytics erstellte Zielgruppen können über Real-Time CDP veröffentlicht werden, um sie in der Journey Optimizer-Ausführung zu verwenden.

## Architektur von Campaign und Journey Insights

Die Architektur verbindet Versand- und Interaktionsdaten aus Journey Optimizer mit Experience Platform und Customer Journey Analytics für die Erstellung von Berichten, Analysen und Zielgruppen.

![Architektur zur Integration von Adobe Customer Journey Analytics und Adobe Journey Optimizer](assets/cja_ajo_integration.png){width="1000" zoomable="yes"}

## Primäre Datenflüsse und Integrationspunkte

- Daten zu Bereitstellung, Interaktion und Effektivität von Journey Optimizer werden an Experience Platform-Datendienste weitergegeben.
- Experience Platform-Daten werden über eine CJA-Verbindung in Customer Journey Analytics aufgenommen.
- Datenansichten und Analysen in Customer Journey Analytics bieten Campaign- und Journey-insight.
- In Customer Journey Analytics erstellte Zielgruppen werden in Real-Time CDP veröffentlicht.
- Real-Time CDP-Zielgruppen stehen für die Ausführung und Personalisierung von Journey Optimizer Journey zur Verfügung.

## Unterstützte Anwendungsfallmuster

- [Generierung von Kundenanalysen und insight](/help/blueprints/use-case-patterns/analysis/customer-analytics-insight-generation.md) - Analysieren Sie das Kampagnen- und Journey-Verhalten kanalübergreifend.
- [Ereignisgesteuertes Messaging](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md) - Verwenden Sie Kunden- und Journey-Signale, um orchestriertes Messaging zu unterstützen.

## Weitere Informationen

- [Journey Optimizer-Berichte](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reporting/reports/sharing-overview)
- [Übersicht über Customer Journey Analytics](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-overview)
- [Veröffentlichen von Customer Journey Analytics-Zielgruppen](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/audiences/publish)
