---
title: '[!DNL Journey Optimizer] - Kampagnenorchestrierung'
description: Ermöglicht es Marketing-Experten, geplante, zielgruppenbasierte, mehrstufige Marketing-Nachrichten über ausgehende Messaging-Kanäle hinweg zu koordinieren.
solution: Journey Optimizer
source-git-commit: 0a3ebcbc6029df46bd988cb8f15ecf838f80c3c9
workflow-type: tm+mt
source-wordcount: '273'
ht-degree: 2%

---

# [!DNL Journey Optimizer] - Blueprint zur Kampagnenorchestrierung

Mit AJO Campaign Orchestration können Marketing-Experten geplante, zielgruppenbasierte, mehrstufige Kommunikationen über ausgehende Kanäle wie E-Mail, SMS, Push und Briefpost entwerfen und ausführen. Im Gegensatz zu AJO Journey, die auf individuelles Kundenverhalten mit Echtzeitdaten aus dem Echtzeit-Kundenprofil reagieren, sind Kampagnen koordinierte Marketing-Maßnahmen, die Zielgruppen in geplanten Intervallen ansprechen. Gemeinsam bieten Kampagnen und Journey einander ergänzende Ansätze. Kampagnen fördern die Strategien der Markeninteraktion, während Journey personalisierte, responsive Erlebnisse bereitstellen.

<br>

## Architektur

<img src="images/ajo-campaigns-architecture.svg" alt="Referenzarchitektur Adobe Journey Optimizer Campaign Orchestration Blueprint" style="width:100%; border:1px solid #4a4a4a" class="modal-image" />

<br>

### Architektur der Nachrichtenausführung

<img src="images/ajo-campaigns-message-sending-architecture.png" alt="Referenzarchitektur Adobe Journey Optimizer Campaign Orchestration Blueprint" style="width:100%; border:1px solid #4a4a4a" class="modal-image" />

<br>

### Relationaler Speicher - Latenz bei der Datenaufnahme

<img src="images/ajo-campaigns-data-ingestion-architecture.png" alt="Referenzarchitektur Adobe Journey Optimizer Campaign Orchestration Blueprint" style="width:100%; border:1px solid #4a4a4a" class="modal-image" />

<br>

## Überlegungen zur Architektur für Journeys

- **Datenarchitektur**: AJO Campaign Orchestration verwendet eine darunter liegende relationale Datenbank zur Zielgruppenerstellung und -orchestrierung
- **Audience Portal-Integration**: Native Integration mit dem Audience Portal im Echtzeit-Kundenprofil, um sowohl aus vorhandenen Zielgruppen zu lesen als auch neue Zielgruppen beim Erstellen von Kampagnen in zu speichern
- **On-Demand-Zielgruppenerstellung**: Erstellen, Auswerten und Ausführen einer Zielgruppe sofort für dringende Marketing-Anwendungsfälle
- **Echtzeit-Kundenprofil-Integration:** Quelle der Wahrheit für den Einverständnis- und Kommunikationsverlauf; unterstützt „schmales Profil“-Design für die Personalisierung
- **Versand von Nachrichten mehrerer Entitäten:** Möglichkeit, mehrere Nachrichten pro Profil in einem Versand zu senden (z. B. eine Nachricht pro Reservierung an die E-Mail-Adresse des Kunden zu senden)
- **Segmentierung mehrerer Entitäten** Beginnen Sie mit der Erstellung einer Zielgruppe aus einer beliebigen Entität im relationalen Speicher (d. h. Produkt, Inventar, Plan usw.)

<br>

## Leitlinien

[Orchestrierte Kampagnen - Produktlink](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/orchestrated-campaigns/guardrails)

[Leitplanken und Leitlinien für End-to-End-Latenzen](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/architecture-overview/deployment/guardrails)

<br>

## Verwandte Dokumentation

- [[!DNL Journey Optimizer] Orchestrierte Kampagnen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/orchestrated-campaigns/orchestrated-campaigns-landing-page.html)
- [[!DNL Experience Platform] Dokumentation](https://experienceleague.adobe.com/docs/experience-platform.html?lang=de)
- [[!DNL Experience Platform] Tags-Dokumentation](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=de)
- [[!DNL Experience Platform Mobile SDK] Dokumentation](https://experienceleague.adobe.com/docs/mobile.html)
- [[!DNL Journey Optimizer] Dokumentation](https://experienceleague.adobe.com/docs/journey-optimizer/using/ajo-home.html)
- [[!DNL Journey Optimizer] Produktbeschreibung](https://helpx.adobe.com/de/legal/product-descriptions/adobe-journey-optimizer.html)