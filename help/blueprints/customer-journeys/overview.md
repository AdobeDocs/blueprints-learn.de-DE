---
title: Customer-Journey-Blueprints
description: Liefern Sie individuelle, zeitgenaue und abgestimmte Kundenerlebnisse über Bildschirme hinweg.
solution: Journey Optimizer, Campaign, Experience Platform
exl-id: 273d024f-a220-4336-89f2-e3bffafcdc37
source-git-commit: 8ee7fe8d38343a669f5ad57e69367fbe6a3e1024
workflow-type: tm+mt
source-wordcount: '221'
ht-degree: 13%

---

# Kunden-Journey - Blueprints

Moderne Marketing-Teams benötigen Plattformen, die sowohl die reaktive Interaktion - die Reaktion auf individuelle Kundenverhaltensweisen - als auch die proaktive Öffentlichkeitsarbeit unterstützen. Dies führt zu Kampagnen, die Zielgruppen in Konversionstrichter führen. Diese Anwendungsfälle umfassen Kanäle wie E-Mail, SMS, Push-Benachrichtigungen und zunehmend auch Web- und In-App-Erlebnisse.

Adobe Journey Optimizer und Adobe Campaign v8 unterstützen jeweils zwei grundlegende Modelle für die Kundeninteraktion:

- Kundengesteuerte Journey: Ereignisgesteuerte Echtzeit-Orchestrierung basierend auf individuellen Verhaltensweisen und Signalen.
- Markeninitiierte Kampagnen: Strategisch zeitlich abgestimmte Push-Vorgänge, die Zielgruppen basierend auf der Segmentierung oder Geschäftslogik in Interaktionstrichter einführen.

Beide Lösungen ermöglichen ausgehende Kommunikation über herkömmliche und digitale Kanäle. AJO unterstützt außerdem die Integration mit eingehenden Kanälen (z. B. Web- und Mobile Apps) durch Audience State Sharing- und Decisioning-Services, was eine einheitliche kanalübergreifende Personalisierung ermöglicht.

Die Auswahl zwischen diesen Tools hängt von architektonischen Überlegungen wie Latenztoleranz, Kanalanforderungen, Datenintegrationsstrategie und Skalierbarkeit ab.

<br>

| Blueprint | Beschreibung | Architektur |
|---|---|:---:|
| **[Adobe Journey Optimizer](journey-optimizer/journey-optimizer-overview.md)** | Kombiniert ereignisgesteuerte Orchestrierung mit :1 Profilen mit zielgruppenbasierter Markenkommunikation über mehrere Kanäle wie E-Mail, SMS, Web, Push, In-App-Messaging, Desktop usw. | <img src="journey-optimizer/images/ajo-architecture.svg" alt="Referenzarchitektur für die Blueprint „Journey Optimizer“" style="width:75%; border:1px solid #4a4a4a" class="modal-image" /> |
| **[Adobe [!DNL Campaign] v8](campaign-v8/campaign-v8-overview.md)** | Konzentriert auf Batch-basiertes Multi-Channel-Kampagnen-Management, ideal für herkömmliche Marketing-Kanäle wie E-Mail, SMS und Briefpost. | <img src="campaign-v8/images/campaign-v8-architecture.svg" alt="Referenzarchitektur für die Blueprint „Campaign v8“" style="width:75%; border:1px solid #4a4a4a" class="modal-image" /> |

<br>

## Veraltete Blueprints

| Blueprint | Architektur |
|---|:---:|
| **[Adobe [!DNL Campaign] v7](campaign-v7/campaign-v7-overview.md)** | <img src="campaign-v7/images/campaign-v7-architecture.svg" alt="Referenzarchitektur für die Blueprint „Campaign v7“" style="width:50%; border:1px solid #4a4a4a" class="modal-image" /> |