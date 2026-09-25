---
title: Customer Journey Analytics mit Real-time Customer Data Platform
description: Vereinheitlichen und analysieren Sie in Customer Journey Analytics Daten und Kundenverhalten von der gesamten Customer Journey und veröffentlichen Sie in CJA identifizierte Zielgruppe in RTCDP.
solution: Customer Journey Analytics
kt: null
thumbnail: null
exl-id: 9e1ba723-63f2-4622-ba67-f2a315c3ba0c
TQID: https://experienceleague.adobe.com/gbNXsco0cQIcn5O83ofB-rb0PF65v7kaTZ7mTngqHks
product_v2:
  - id: e98b7246-966c-4318-9e95-cad2f7a17dc7
    internal-label: Customer Journey Analytics
feature_v2:
  - id: ce577701-5b9e-4fe4-8fa3-4eedea976da4
    internal-label: Components
source-git-commit: ce7331f279a6e59db95ca3b763148440598cde84
workflow-type: tm+mt
source-wordcount: '302'
ht-degree: 8%
---

# Adobe Customer Journey Analytics

Adobe Customer Journey Analytics fasst Kundeninteraktionsdaten aus Adobe Experience Platform und anderen Quellen in einem Journey-basierten Analyse-Service zusammen. Diese Architektur stellt die Hauptreferenz für kanalübergreifende Analysen, B2B-CJA-Ableitungen und die Veröffentlichung von CJA-Zielgruppen in Real-Time CDP bereit.

## Customer Journey Analytics-Architektur

Dieses Diagramm zeigt den Hauptfluss von Kundeninteraktionsdaten in Customer Journey Analytics für Verbindungen, Datenansichten, Analysen und die Erstellung von Zielgruppen.

![Adobe Customer Journey Analytics-Kernarchitektur](assets/cja.png){width="1000" zoomable="yes"}

## Architekturableitungen

- B2B Customer Journey Analytics erweitert die Kernarchitektur um die Dimensionen Konto, Opportunity, Einkaufsgruppe und Person für die Account-basierte Analyse.
- Bei der CJA-Zielgruppenfreigabe werden von Customer Journey Analytics erstellte Zielgruppen in Real-Time CDP zur Aktivierung und nachgelagerten Journey-Ausführung veröffentlicht.

## Primäre Datenflüsse und Integrationspunkte

- Kundeninteraktionsdaten werden aus Web-, Mobile-, Commerce-, CRM- und anderen Quellen in Adobe Experience Platform erfasst.
- Experience Platform-Datensätze werden in einer Customer Journey Analytics-Verbindung ausgewählt.
- Datenansichten stellen Metriken, Dimensionen und berechnete Felder für die kanalübergreifende Analyse bereit.
- Customer Journey Analytics-Zielgruppen können zur Aktivierung in Real-Time CDP veröffentlicht werden.
- Customer Journey Analytics Insights kann über die dedizierte Integrationsarchitektur mit Journey Optimizer verwendet werden.

## Unterstützte Anwendungsfallmuster

- [B2B-](/help/blueprints/use-case-patterns/b2b/account-analytics.md): Analysieren Sie Journey auf Konto-, Opportunity- und Personenebene mit B2B-Dimensionen.
- [Generierung von Kundenanalysen und insight](/help/blueprints/use-case-patterns/analysis/customer-analytics-insight-generation.md) - Analysieren Sie das kanalübergreifende Verhalten und generieren Sie Journey-Erkenntnisse.

## Weitere Informationen

- [Übersicht über Customer Journey Analytics](https://experienceleague.adobe.com/de/docs/analytics-platform/using/cja-overview/cja-overview)
- [Customer Journey Analytics-Verbindungen](https://experienceleague.adobe.com/de/docs/analytics-platform/using/cja-connections/create-connection)
- [Veröffentlichen von Customer Journey Analytics-Zielgruppen](https://experienceleague.adobe.com/de/docs/analytics-platform/using/cja-components/audiences/publish)
