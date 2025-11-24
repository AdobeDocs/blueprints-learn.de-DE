---
title: '[!DNL Journey Optimizer] - Journey Blueprint'
description: Führen Sie ausgelöste Nachrichten und Erlebnisse mit Adobe Experience Platform als Zentrale für gestreamte Daten, Kundenprofile und Segmentierung aus.
solution: Journey Optimizer
exl-id: 97831309-f235-4418-bd52-28af815e1878
source-git-commit: 3a3988e93dd9e92f4f564bfedfa314e8e2b5d9ba
workflow-type: tm+mt
source-wordcount: '640'
ht-degree: 15%

---

# Blueprints [!DNL Journey Optimizer]

Adobe [!DNL Journey Optimizer] ist ein Cloud-natives Programm, das auf Adobe Experience Platform basiert und die Echtzeit- und geplante Orchestrierung von Kunden-Journey über mehrere Kanäle hinweg ermöglicht. Es unterstützt ereignisgesteuerte Trigger, Zielgruppensegmentierung und Entscheidungs-Services, um personalisierte Erlebnisse über E-Mail, SMS, Push, Web und In-App-Messaging bereitzustellen. Es lässt sich mit eingehenden und ausgehenden Systemen integrieren und ermöglicht so eine einheitliche Verwaltung des Zielgruppenstatus und kontextuelle Interaktion über den gesamten Kundenlebenszyklus hinweg.

Dieser Blueprint skizziert die technischen Möglichkeiten des Programms und bietet einen tiefen Einblick in die verschiedenen architektonischen Komponenten, aus denen [!DNL Journey Optimizer] besteht.

<br>

## Anwendungsfälle

>[!BEGINTABS]
>[!TAB Journey (ereignisgesteuert, in Echtzeit)]

- **Abbruch-Wiederherstellung:** Trigger personalisierte Nachrichten, wenn ein Benutzer einen Warenkorb, ein Formular oder eine Sitzung verlässt - per E-Mail, Push oder In-App.
- **Neue Benutzerregistrierung:** Sie neue Benutzer sofort nach der Registrierung mit neuen Kontovoreinstellungen, relevanten Aktionen oder Vorteilen ein.
- **Transaktionsnachrichten** Senden Sie Bestätigungen, Warnhinweise oder Aktualisierungen in Echtzeit (z. B. versendete Bestellung, Kennwortzurücksetzung) mithilfe von Ereignis-Triggern.
- **Kontextuelles Targeting:** Kommunizieren Sie mit Benutzern im Moment auf der Grundlage ihrer Signale und Standorte, um ihnen dabei zu helfen, ihr Erlebnis zu leiten und zu lenken
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

<img src="images/ajo-architecture.svg" alt="Referenzarchitektur Adobe Journey Optimizer Blueprint" style="width:100%; border:1px solid #4a4a4a" class="modal-image" />

<br>

## Blueprint-Szenarios

| Szenario | Beschreibung |
| :-- | :-- |
| [Journey](journey-optimizer-journeys.md) | AJO-Journey in Adobe Journey Optimizer sind automatisierte, personalisierte Kundenerlebnisse, die durch Echtzeit-Ereignisse oder Zielgruppensegmente ausgelöst werden. So können Marketing-Experten relevante Nachrichten über Kanäle wie E-Mail, SMS und Push-Benachrichtigungen versenden. |
| [Kampagnenorchestrierung](journey-optimizer-campaigns.md) | Mit AJO Campaign Orchestration können Marketing-Experten personalisierte, kanalübergreifende Kampagnen entwerfen und ausführen, indem sie Echtzeitdaten und Zielgruppeneinblicke nutzen. Es unterstützt Dynamic Targeting, Nachrichtenversand und Journey-Logik zur Optimierung der Kundeninteraktion über E-Mail-, SMS-, Push- und benutzerdefinierte Kanäle hinweg. |

<br>

## Integrationsmuster

| Integration | Beschreibung | Technische Überlegungen |
| :-- | :-- | :-- |
| [Drittanbieter-Messaging](3rd-party-messaging.md) | Veranschaulicht, wie Adobe [!DNL Journey Optimizer] in Messaging-Plattformen von Drittanbietern integrieren kann, um personalisierte Kundenkommunikation zu orchestrieren und bereitzustellen. | <ul><li>Das Drittanbietersystem muss die Authentifizierung mit **Bearer-Token“**</li><li>**Statische IPs werden aufgrund** Multi-Mandanten-Architektur nicht unterstützt.</li><li>Beachten Sie **API-Ratenbeschränkungen** auf Drittanbietersystemen. Kunden müssen möglicherweise zusätzliche Kapazität erwerben, um Traffic zu verarbeiten, der von **Adobe Journey Optimizer stammt**.</li><li>**Entscheidungs-Management** wird in Nachrichten-Payloads oder Versandlogik nicht unterstützt.</li></ul> |
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

[[!DNL Journey Optimizer] Leitplanken - Produktlink](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/get-started/guardrails.html)

[Leitplanken und Leitlinien für End-to-End-Latenzen](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/architecture-overview/deployment/guardrails.html?lang=de)

## Verwandte Dokumentation

- [[!DNL Experience Platform] Dokumentation](https://experienceleague.adobe.com/docs/experience-platform.html?lang=de)
- [[!DNL Experience Platform] Tags-Dokumentation](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=de)
- [[!DNL Experience Platform Mobile SDK] Dokumentation](https://experienceleague.adobe.com/docs/mobile.html?lang=de)
- [[!DNL Journey Optimizer] Dokumentation](https://experienceleague.adobe.com/docs/journey-optimizer/using/ajo-home.html?lang=de)
- [[!DNL Journey Optimizer] Produktbeschreibung](https://helpx.adobe.com/de/legal/product-descriptions/adobe-journey-optimizer.html)