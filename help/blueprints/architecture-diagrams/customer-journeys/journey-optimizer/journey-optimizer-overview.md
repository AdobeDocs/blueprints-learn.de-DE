---
title: '[!DNL Journey Optimizer]'
description: Führen Sie ausgelöste Nachrichten und Erlebnisse mit Adobe Experience Platform als Zentrale für gestreamte Daten, Kundenprofile und Segmentierung aus.
solution: Journey Optimizer
exl-id: 97831309-f235-4418-bd52-28af815e1878
TQID: https://experienceleague.adobe.com/Rfi-0QD8bQpD-Zp2CDpzqxrge0yVs2CFt5mDKibNogI
product_v2:
  - id: cb954087-f4fc-4456-afb9-e939cabcdc79
    internal-label: Journey Optimizer
feature_v2:
  - id: a653cc2e-bc85-4353-a306-399e5b247978
    internal-label: Journey Optimizer campaigns
  - id: d998adac-2f81-400b-a669-d07bb196e4eb
    internal-label: Journeys
  - id: df64005d-8f9a-422e-ba4d-c6f6dc3454b4
    internal-label: Use cases
  - id: fe338112-e2ce-4876-8989-fc4d497613f1
    internal-label: Email
subfeature_v2:
  - id: fa683eda-48de-4558-af32-2673edcd44fe
    internal-label: Events
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
topic_v2:
  - id: addf009e-030a-4310-8534-776a3e62ed48
    internal-label: Customer lifecycle
  - id: b5520579-b31f-4df7-9281-f0d9f91e2edc
    internal-label: Customer engagement
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
    internal-label: Implementation
  - id: bce87dde-a4ab-44c9-8a18-ad66e4ddb377
    internal-label: Customer experience
  - id: d00e9f03-e50b-4162-b143-0c0817c937c2
    internal-label: Customer journeys
  - id: e1e0219c-f879-479f-8427-888ed2a6e9c2
    internal-label: Insights
  - id: fd2e3797-f2ea-4b36-a9af-52acf5e90513
    internal-label: Customer profiles
  - id: ff2b9b37-92e0-45fc-b853-379d44c08c89
    internal-label: Audience segmentation
source-git-commit: 79738031788419872e32b8f754febacbfd18cc06
workflow-type: tm+mt
source-wordcount: '717'
ht-degree: 15%
---
# [!DNL Journey Optimizer]

Adobe [!DNL Journey Optimizer] ist ein Cloud-natives Programm, das auf Adobe Experience Platform basiert und die Echtzeit- und geplante Orchestrierung von Kunden-Journey über mehrere Kanäle hinweg ermöglicht. Es unterstützt ereignisgesteuerte Trigger, Zielgruppensegmentierung und Entscheidungs-Services, um personalisierte Erlebnisse über E-Mail, SMS, Push, Web und In-App-Messaging bereitzustellen. Es lässt sich mit eingehenden und ausgehenden Systemen integrieren und ermöglicht so eine einheitliche Verwaltung des Zielgruppenstatus und kontextuelle Interaktion über den gesamten Kundenlebenszyklus hinweg.

In diesem Überblick werden die technischen Funktionen der Anwendung erläutert und die verschiedenen Architekturkomponenten erläutert, aus denen [!DNL Journey Optimizer] besteht.

<br>

## Anwendungsfälle

>[!BEGINTABS]
>[!TAB Journey (ereignisgesteuert, in Echtzeit)]

- **Abbruch-Wiederherstellung:** Trigger personalisierte Nachrichten, wenn ein Benutzer einen Warenkorb, ein Formular oder eine Sitzung abbricht â€ per E-Mail, Push oder In-App.
- **Neue Benutzeranmeldung:** Sie neue Benutzer sofort nach der Registrierung mit neuen Kontovoreinstellungen, relevanten Aktionen oder Vorteilen ein.
- **Transaktionsnachrichten** Senden Sie Bestätigungen, Warnhinweise oder Aktualisierungen in Echtzeit (z. B. versendete Bestellung, Kennwortzurücksetzung) mithilfe von Ereignis-Triggern.
- **Kontextuelles Targeting:** Kommunizieren Sie mit Benutzenden im Moment auf der Grundlage ihrer Signale und Standorte, um ihnen dabei zu helfen, ihr Erlebnis zu leiten und zu lenken
- **Kontextueller Upsell/Crosssell** Stellen Sie personalisierte Angebote auf der Grundlage von Echtzeit-Profilattributen und aktuellen Interaktionen bereit.

>[!TAB Kampagnenorchestrierung (geplant, markeninitiiert)]

- **Werbekampagnen**: Starten Sie mehrstufige Multi-Channel-Kampagnen für Produkteinführungen, saisonale Angebote oder Verkaufsereignisse.
- **Lebenszyklus-Marketing**: Automatisieren Sie wiederkehrende Kampagnen wie Geburtstagsnachrichten, Verlängerungserinnerungen oder Treue-Meilensteine.
- **Zielgruppenbasierte Funnel-Push**: Segmentieren und Pushen von Zielgruppen in strukturierte Kampagnen, die auf Geschäftslogik oder CRM-Attributen basieren.
- **Newsletter- und Inhaltsverteilung**: Planen und Bereitstellen personalisierter Inhalte für ausgewählte Zielgruppen über E-Mail und Mobilgeräte hinweg.
- **Rückgewinnungskampagnen**: Identifizieren Sie inaktive Benutzende und führen Sie sie basierend auf Inaktivitätsschwellen erneut in Interaktionsflüsse ein.

>[!ENDTABS]

<br>

## Architektur

![Referenzarchitektur für Adobe Journey Optimizer](images/ajo-architecture.png){width="1000" zoomable="yes"}

<br>

## Beispielszenarien

| Szenario | Beschreibung |
| :-- | :-- |
| [Journey](journey-optimizer-journeys.md) | AJO-Journey in Adobe Journey Optimizer sind automatisierte, personalisierte Kundenerlebnisse, die durch Echtzeit-Ereignisse oder Zielgruppensegmente ausgelöst werden. So können Marketing-Experten relevante Nachrichten über Kanäle wie E-Mail, SMS und Push-Benachrichtigungen versenden. |
| [Kampagnenorchestrierung](journey-optimizer-campaigns.md) | Mit AJO Campaign Orchestration können Marketing-Experten personalisierte, kanalübergreifende Kampagnen entwerfen und ausführen, indem sie Echtzeitdaten und Zielgruppeneinblicke nutzen. Es unterstützt Dynamic Targeting, Nachrichtenversand und Journey-Logik zur Optimierung der Kundeninteraktion über E-Mail-, SMS-, Push- und benutzerdefinierte Kanäle hinweg. |

<br>

## Integrationsmuster

| Integration | Beschreibung | Technische Überlegungen |
| :-- | :-- | :-- |
| [Nachrichten von Drittanbietern](3rd-party-messaging.md) | Veranschaulicht, wie Adobe [!DNL Journey Optimizer] in Messaging-Plattformen von Drittanbietern integrieren kann, um personalisierte Kundenkommunikation zu orchestrieren und bereitzustellen. | <ul><li>Das Drittanbietersystem muss die Authentifizierung mit **Bearer-Token“**</li><li>**Statische IPs werden aufgrund** Multi-Mandanten-Architektur nicht unterstützt.</li><li>Beachten Sie **API-Ratenbeschränkungen** auf Drittanbietersystemen. Kunden müssen möglicherweise zusätzliche Kapazität erwerben, um Traffic zu verarbeiten, der von **Adobe Journey Optimizer stammt**.</li><li>**Entscheidungs-Management** wird in Nachrichten-Payloads oder Versandlogik nicht unterstützt.</li></ul> |
| [[!DNL Journey Optimizer] mit Adobe Campaign v8](../campaign-v8/ajo-and-campaign-v8.md) | Veranschaulicht, wie Adobe [!DNL Journey Optimizer] in die Transaktionsnachrichten-Funktionen von Adobe Campaign v8 integriert werden kann, um den endgültigen Nachrichtenversand auszuführen. | <ul><li>Es gibt keine Einschränkung bei Nachrichten. Begrenzung auf 4.000 Nachrichten pro 5 Minuten.</li><li>Unterstützt nur ereignisinitiierte Journey-Dateien</li><li>Entscheidungs-Management wird in von Campaign gesendeten Nachrichten nicht unterstützt</li></ul> |

<br>

## Voraussetzungen

Adobe [!DNL Experience Platform]:

- Schemata und Datensätze müssen im System konfiguriert werden, bevor Sie [!DNL Journey Optimizer] Datenquellen konfigurieren können
- Fügen Sie für klassenbasierte XDM-Erlebnisereignis-Schemata die Feldergruppe „Orchestration eventID“ hinzu, wenn Sie ein Ereignis auslösen möchten, das kein regelbasiertes Ereignis ist
- Fügen Sie für klassenbasierte XDM Individual Profile-Schemata die Feldergruppe „Profil-Testdetails“ hinzu, um Testprofile für die Verwendung mit [!DNL Journey Optimizer] laden zu können

<br>

E-Mail:

- Eine Subdomain muss verfügbar sein, die für den Versand von Nachrichten verwendet werden kann
- Die Subdomain kann entweder komplett an Adobe delegiert werden (empfohlen) oder CNAMEs können zum Verweis an Adobe-spezifische DNS-Server (benutzerdefiniert) verwendet werden
- Für jede Subdomain ist ein Google-TXT-Datensatz erforderlich, um gute Zustellbarkeit sicherzustellen

<br>

Mobile Push:

- Der Kunde muss über einen Mobile-Entwickler verfügen, der die Mobile App erstellen kann
- Adobe Experience Platform Mobile SDK

<br>

## Leitlinien

[Produkt-Link zu [!DNL Journey Optimizer]-Schutzmechanismen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/get-started/guardrails.html)

[Leitplanken und Leitlinien für End-to-End-Latenzen](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/architecture-overview/deployment/guardrails.html?lang=de)

## Verwandte Dokumentation

- [[!DNL Experience Platform] Dokumentation](https://experienceleague.adobe.com/docs/experience-platform.html?lang=de)
- [Dokumentation zu [!DNL Experience Platform] Tags](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=de)
- [[!DNL Experience Platform Mobile SDK] Dokumentation](https://experienceleague.adobe.com/docs/mobile.html?lang=de)
- [[!DNL Journey Optimizer] Dokumentation](https://experienceleague.adobe.com/docs/journey-optimizer/using/ajo-home.html?lang=de)
- [[!DNL Journey Optimizer] Produktbeschreibung](https://helpx.adobe.com/de/legal/product-descriptions/adobe-journey-optimizer.html)
