---
title: '[!DNL Journey Optimizer] - Ausgelöstes Messaging und Adobe Experience Platform Blueprint'
description: Führen Sie ausgelöste Nachrichten und Erlebnisse mit Adobe Experience Platform als Zentrale für gestreamte Daten, Kundenprofile und Segmentierung aus.
solution: Journey Optimizer
exl-id: 70573eb9-cd69-4fe6-b2ae-dae81665a308
TQID: https://experienceleague.adobe.com/MuodOvJ52G9lmUAmsuj06q1aTXkRg7W0Bj6nxLp96N8
product_v2:
  - id: cb954087-f4fc-4456-afb9-e939cabcdc79
feature_v2:
  - id: a653cc2e-bc85-4353-a306-399e5b247978
  - id: d998adac-2f81-400b-a669-d07bb196e4eb
  - id: fe338112-e2ce-4876-8989-fc4d497613f1
  - id: fe96aceb-8194-4a8a-a6b0-75302d02804d
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
  - id: e0eb8757-182f-49f3-94a4-1587d16f5094
  - id: fd2e3797-f2ea-4b36-a9af-52acf5e90513
source-git-commit: 95ba7aa681e67efb136adac15dc7894cb413a4f0
workflow-type: tm+mt
source-wordcount: 357
ht-degree: 12%

---

# [!DNL Journey Optimizer] - Journey Blueprint

>[!TIP]
>Diese Blueprint ist auch als Anwendungsfallmuster [&#x200B; Kampagnenverwaltung &#x200B;](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md) Orchestrierung verfügbar.

Adobe Journey Optimizer-Journey sind ereignisgesteuerte Echtzeit-Workflows, die auf der Grundlage individueller Kundenverhaltensweisen personalisierte, mehrstufige Erlebnisse bereitstellen. Sie unterstützen eine breite Palette von Kanälen - einschließlich E-Mail, SMS, Push-Benachrichtigungen, In-App-Messaging, Code-basierte Erlebnisse und benutzerdefinierte API-basierte Integrationen, die es Marken ermöglichen, Kunden über ihre bevorzugten Touchpoints hinweg kontextuell anzusprechen.

<br>

## Architektur

<img src="images/ajo-journeys-architecture.svg" alt="Referenzarchitektur Adobe Journey Optimizer - Journey-Blueprint" style="width:100%; border:1px solid #4a4a4a" class="modal-image" />

<br>

## Überlegungen zur Architektur für Journeys

- **Profilfrische**: AJO-Journey verwenden Echtzeit-Updates für das Kundenprofil. Stellen Sie sicher, dass Datenquellen, die in Adobe Experience Platform (AEP) eingespeist werden, für die Aufnahme mit geringer Latenz konfiguriert sind, um die Profilgenauigkeit aufrechtzuerhalten.
- **Skalierbare Ereignisverarbeitung:** Stellen Sie sicher, dass die Infrastruktur große Mengen an Journey-Triggern und den Nachrichtenversand verarbeiten kann.
- **Modulare Integration:** Design-APIs und benutzerdefinierte Aktionen zur Verbindung von AJO mit externen Systemen für die dynamische Personalisierung.
- **Identitätsauflösung**: Eine genaue Zuordnung von Kundenidentitäten über Geräte und Kanäle hinweg ist wichtig. Falsch ausgerichtete Identitäten können zu fehlerhaften oder fehlgeleiteten Journey führen.
- **Zeitpunkt der Segmentqualifizierung**: Zielgruppenbasierte Journey sind von der Segmentzugehörigkeit abhängig. Erfahren Sie, wie oft Segmente ausgewertet werden und wie sich dieses Timing auf den Journey-Einstieg und die Personalisierung auswirkt.
- **Journey-Einstiegsbedingungen**: Profile müssen bestimmte Bedingungen erfüllen, um eine Journey aufzurufen. Diese Bedingungen sollten sorgfältig gestaltet werden, um unbeabsichtigte Ausschlüsse oder Überschneidungen zu vermeiden.
- **Zielgruppenauswertung und Latenz**: Die Schritte „Zielgruppe lesen“ hängen von Segmentauswertungen in Adobe Experience Platform ab, die möglicherweise nicht in Echtzeit erfolgen. Architekten-Journey mit Kenntnis der Auswertungshäufigkeit und -latenz, um Verzögerungen bei der Zielgruppen-Qualifizierung zu vermeiden und eine zeitnahe Personalisierung sicherzustellen.

<br>

## Leitlinien

[Produkt-Link zu [!DNL Journey Optimizer]-Schutzmechanismen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/get-started/guardrails.html)

[Leitplanken und Leitlinien für End-to-End-Latenzen](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/architecture-overview/deployment/guardrails.html)

<br>

## Verwandte Dokumentation

- [[!DNL Experience Platform] Dokumentation](https://experienceleague.adobe.com/docs/experience-platform.html?lang=de)
- [Dokumentation zu [!DNL Experience Platform] Tags](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=de)
- [[!DNL Experience Platform Mobile SDK] Dokumentation](https://experienceleague.adobe.com/docs/mobile.html)
- [[!DNL Journey Optimizer] Dokumentation](https://experienceleague.adobe.com/docs/journey-optimizer/using/ajo-home.html)
- [[!DNL Journey Optimizer] Produktbeschreibung](https://helpx.adobe.com/de/legal/product-descriptions/adobe-journey-optimizer.html)
