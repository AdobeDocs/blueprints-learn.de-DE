---
title: '[!DNL Journey Optimizer] - Kampagnenorchestrierung'
description: Ermöglicht es Marketing-Experten, geplante, zielgruppenbasierte, mehrstufige Marketing-Nachrichten über ausgehende Messaging-Kanäle hinweg zu koordinieren.
solution: Journey Optimizer
exl-id: a8ff16f8-146d-4e1f-9bd0-9eda6af0c69b
TQID: https://experienceleague.adobe.com/aPDagEC1zZdi-Bz29fFf6g5Uy8v4qMPhDA47Cdwl-Sw
product_v2:
  - id: cb954087-f4fc-4456-afb9-e939cabcdc79
feature_v2:
  - id: a653cc2e-bc85-4353-a306-399e5b247978
  - id: d998adac-2f81-400b-a669-d07bb196e4eb
  - id: df64005d-8f9a-422e-ba4d-c6f6dc3454b4
  - id: fe338112-e2ce-4876-8989-fc4d497613f1
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
  - id: e0eb8757-182f-49f3-94a4-1587d16f5094
source-git-commit: 95ba7aa681e67efb136adac15dc7894cb413a4f0
workflow-type: tm+mt
source-wordcount: 358
ht-degree: 6%

---

# [!DNL Journey Optimizer] - Blueprint zur Kampagnenorchestrierung

>[!TIP]
>Diese Blueprint ist auch als Anwendungsfallmuster [&#x200B; Kampagnenverwaltung &#x200B;](/help/blueprints/use-case-patterns/campaign-management-orchestration/batch-outbound-message-activation.md) Orchestrierung verfügbar.

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

[Produkt-Link für orchestrierte Kampagnen](https://experienceleague.adobe.com/de/docs/journey-optimizer/using/campaigns/orchestrated-campaigns/guardrails)

[Leitplanken und Leitlinien für End-to-End-Latenzen](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/architecture-overview/deployment/guardrails)

<br>

## Verwandte Dokumentation

- [Orchestrierte Kampagnen [!DNL Journey Optimizer]](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/orchestrated-campaigns/orchestrated-campaigns-landing-page.html)
- [[!DNL Experience Platform] Dokumentation](https://experienceleague.adobe.com/docs/experience-platform.html?lang=de)
- [Dokumentation zu [!DNL Experience Platform] Tags](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=de)
- [[!DNL Experience Platform Mobile SDK] Dokumentation](https://experienceleague.adobe.com/docs/mobile.html?lang=de)
- [[!DNL Journey Optimizer] Dokumentation](https://experienceleague.adobe.com/docs/journey-optimizer/using/ajo-home.html?lang=de)
- [[!DNL Journey Optimizer] Produktbeschreibung](https://helpx.adobe.com/de/legal/product-descriptions/adobe-journey-optimizer.html)
