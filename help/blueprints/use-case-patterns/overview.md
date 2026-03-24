---
title: Anwendungsfallmuster
description: Erfahren Sie mehr über die Anwendungsfallmuster bei der Implementierung von Adobe Experience Platform und Programmen, um wichtige Geschäftsziele zu erreichen.
solution: Experience Platform, Real-Time Customer Data Platform, Journey Optimizer
doc-type: overview-page
exl-id: 58caa6ad-0d1c-4290-9614-c68c9c9028bb
source-git-commit: 27f7e230982807ec70ca96af7f737944a6588f27
workflow-type: tm+mt
source-wordcount: '760'
ht-degree: 0%

---

# Anwendungsfallmuster

Anwendungsfallmuster definieren wiederholbare Implementierungsansätze für Adobe Experience Platform und Programme. Jedes Muster beschreibt eine bestimmte Funktion, die Funktionskette, die sie bereitstellt, die beteiligten Anwendungen und die [wichtigen Geschäftsziele](/help/blueprints/business-objectives/overview.md) die sie unterstützt.

Verwenden Sie die folgenden Tabellen, um das Muster zu finden, das Ihren Implementierungsanforderungen entspricht, und folgen Sie dann dem Link zur vollständigen Implementierungsreferenz, einschließlich Optionen, Phasen, Entscheidungshilfen und Experience League-Dokumentation.

## Zielgruppenerstellung und -aktivierung

Die folgenden Muster helfen Ihnen beim Erstellen, Auswerten und Aktivieren von Zielgruppensegmenten über Kanäle und Ziele hinweg.

| Muster | Primäre Funktion | Zentrale Lösungen |
| --- | --- | --- |
| [Zielgruppenaktivierung für Ziele](audience-building-activation/audience-activation-to-destinations.md) | Auswerten und Veröffentlichen von Zielgruppensegmenten für externe Ziele zum Targeting oder zur Unterdrückung | [!DNL Real-Time CDP] |
| [Zielgruppen-Collaboration](audience-building-activation/audience-collaboration-segment-match.md) | Freigeben und Abgleichen von Zielgruppensegmenten über Sandboxes oder Organisationen hinweg mithilfe von Segment Match | [!DNL Real-Time CDP], [!DNL Experience Platform] |
| [Ereignisweiterleitung](audience-building-activation/event-forwarding.md) | Weiterleiten von über Edge Network erfassten Echtzeit-Ereignisdaten an Ziele, die nicht mit Adobe verbunden sind | [!DNL Experience Platform] (Edge Network, Ereignisweiterleitung) |
| [B2B-Zielgruppenaktivierung](audience-building-activation/b2b-audience-activation.md) | Account-basierte B2B-Zielgruppen über Web-, E-Mail- und Werbekanäle aktivieren | [!DNL Real-Time CDP] B2B edition |

## Personalisierung

Die folgenden Muster bieten bekannten und unbekannten Besuchern über Web- und App-Oberflächen hinweg maßgeschneiderte Erlebnisse.

| Muster | Primäre Funktion | Zentrale Lösungen |
| --- | --- | --- |
| [Anonyme Web-Personalisierung für Besucher](personalization/anonymous-visitor-web-personalization.md) | Bereitstellen von personalisierten Inhalten basierend auf sitzungsinternen Verhaltenssignalen für nicht identifizierte Besucher | [!DNL Journey Optimizer] (Web-Kanal), [!DNL Real-Time CDP] |
| [Web-/App-Personalisierung für bekannte Besucher](personalization/known-visitor-web-app-personalization.md) | Bereitstellung personalisierter Inhalte, Angebote oder Promotions für identifizierte Besucher auf der Grundlage von Echtzeit-Profil und Segmentzugehörigkeit | [!DNL Journey Optimizer], [!DNL Real-Time CDP] |
| [Offer Decisioning](personalization/offer-decisioning.md) | Verwenden Sie eine zentralisierte Entscheidungslogik, um kanalübergreifend das nächstbeste Angebot oder den nächstbesten Inhalt für ein Profil auszuwählen. | [!DNL Journey Optimizer] (decisioning), [!DNL Real-Time CDP] |
| [Verhaltensempfehlung](personalization/behavioral-recommendation.md) | Generieren von Element- und Inhaltsempfehlungen mithilfe von Auswahlstrategien und Rangfolgemodellen | [!DNL Journey Optimizer] (decisioning), [!DNL Real-Time CDP] |

## Kampagnenverwaltung und -orchestrierung

Die folgenden Muster decken den geplanten, ausgelösten und mehrstufigen Nachrichtenversand über verschiedene Kanäle hinweg ab.

| Muster | Primäre Funktion | Zentrale Lösungen |
| --- | --- | --- |
| [Batch-Aktivierung ausgehender Nachrichten](campaign-management-orchestration/batch-outbound-message-activation.md) | Auswertung einer Audience und Versand einer geplanten ausgehenden Nachricht in einer einzigen Batch-Ausführung | [!DNL Journey Optimizer], [!DNL Real-Time CDP] |
| [Ereignisausgelöstes Messaging](campaign-management-orchestration/event-triggered-messaging.md) | Auf ein Echtzeit-Verhaltens- oder Systemereignis achten und dann eine kontextuelle Nachricht an das auslösende Profil senden | [!DNL Journey Optimizer], [!DNL Real-Time CDP] |
| [Mehrstufige orchestrierte Journey](campaign-management-orchestration/multi-step-orchestrated-journey.md) | Führen Sie ein Profil durch einen verzweigenden Multi-Touch-Journey mit Wartezeiten, Bedingungen und mehreren Nachrichtenaktionen | [!DNL Journey Optimizer], [!DNL Real-Time CDP] |
| [Cross-Channel-Journey mit Decisioning](campaign-management-orchestration/cross-channel-journey-with-decisioning.md) | Orchestrieren Sie eine mehrstufige Journey mit Echtzeit-Entscheidungsfindung, um optimale Kanäle, Inhalte oder Angebote auszuwählen | [!DNL Journey Optimizer], [!DNL Real-Time CDP] |
| [Kaufen von gruppenbasiertem Marketing und Journey-Management](campaign-management-orchestration/buying-group-based-marketing.md) | Entwickeln von Journey auf Kontoebene, die Leads zu Einkaufsgruppen qualifizieren, um die B2B-Marketing-Effektivität zu verbessern | [!DNL Journey Optimizer] B2B edition, [!DNL Real-Time CDP] B2B edition |

## Analyse

Die folgenden Muster unterstützen Cross-Channel-Verhaltens- und Leistungsanalysen.

| Muster | Primäre Funktion | Zentrale Lösungen |
| --- | --- | --- |
| [Generierung von Kundenanalysen und insight](analysis/customer-analytics-insight-generation.md) | Erstellen von kanalübergreifenden Analyse-Arbeitsbereichen, berechneten Metriken und Dashboards für die Verhaltens- und Leistungsanalyse | [!DNL Customer Journey Analytics], [!DNL Experience Platform] |
| [B2B-Analyse](analysis/b2b-analytics.md) | Informationen auf B2B-Kontoebene in die kanalübergreifende Journey-Analyse für Kunden einschließen | [!DNL Customer Journey Analytics] B2B edition, [!DNL Real-Time CDP] B2B edition |

## Gesprächserfahrung

Die folgenden Muster ermöglichen KI-gestützte, markensichere Gesprächsinteraktionen über digitale Eigenschaften.

| Muster | Primäre Funktion | Zentrale Lösungen |
| --- | --- | --- |
| [Brand Concierge-Gesprächserlebnis](conversational-experience/brand-concierge-conversational-experience.md) | Transformieren Sie digitale Eigenschaften in KI-gestützte, markensichere Gesprächserlebnisse, die die Kundenfindung leiten | [!DNL Brand Concierge], [!DNL Experience Platform], [!DNL Real-Time CDP] |

## Szenario-Auswahl

Verwenden Sie diese Anleitung, wenn ein Szenario mehr als ein Muster aufweisen könnte. Beantworten Sie die Fragen zur Verzweigung, um das primäre Muster zu finden, und erweitern Sie es dann optional mit den aufgelisteten Mustern.

### Win-back mit Incentive-Angebot

*Ein abgelaufener Kunde hat innerhalb von 90 Tagen keinen Kauf getätigt. Sie möchten sie erneut mit einem zielgerichteten Angebot interagieren.*

- **Ist die Angebotsauswahl dynamisch (verschiedene Kunden erhalten unterschiedliche Angebote basierend auf ihrer Eignung oder ihrem Ranking)?**
   - Ja → [Offer Decisioning](personalization/offer-decisioning.md) als Angebotsebene, umschlossen in [Mehrstufiger orchestrierter Journey](campaign-management-orchestration/multi-step-orchestrated-journey.md) für die Rückgewinnungssequenz
   - Nein (gleiches Angebot für alle qualifizierten abgelaufenen Kunden) → [Mehrstufige orchestrierte Journey](campaign-management-orchestration/multi-step-orchestrated-journey.md)

### Follow-up nach dem Kauf

*Ein Kunde hat gerade einen Kauf abgeschlossen. Sie möchten eine Bestätigung, eine Crosssell-Empfehlung und eine Treueprämien-Benachrichtigung senden.*

- **Erfordert die Sequenz eine adaptive Verzweigung auf der Grundlage von Echtzeit-Ereignissen (z. B. beanspruchte Belohnung, überprüftes Produkt)?**
   - Ja → [Mehrstufige orchestrierte Journey](campaign-management-orchestration/multi-step-orchestrated-journey.md)
   - Nein (feste Reihenfolge, keine Verzweigung) → [Aktivierung ausgehender Nachrichten im Batch](campaign-management-orchestration/batch-outbound-message-activation.md)
- **Enthält es personalisierte Produktempfehlungen?**
   - Ja → Erweitern mit [Verhaltensempfehlung](personalization/behavioral-recommendation.md) auf Inhaltsebene

### Personalisierung für Treue-Meilenstein

*Ein Kunde erreicht eine neue Treuestufe. Sie möchten personalisierte Webinhalte anzeigen und eine Glückwunschnachricht senden.*

- **Ist der Web-Inhalt personalisiert (unterschiedliche Inhalte pro Ebene oder Segment)?**
   - Ja → [Web-/App-Personalisierung bekannter Besucher](personalization/known-visitor-web-app-personalization.md) für die Web-Oberfläche
- **Handelt es sich bei der ausgehenden Nachricht um einen einzelnen Versand oder eine Nurture-Sequenz?**
   - Einmaliger Versand → [ereignisgesteuertes Messaging](campaign-management-orchestration/event-triggered-messaging.md)
   - Sequenz → [Mehrstufige orchestrierte Journey](campaign-management-orchestration/multi-step-orchestrated-journey.md)

### Rückgewinnungskampagne

*Ein Segment von inaktiven Benutzern benötigt eine Multitouch-Reaktivierungssequenz.*

- **Müssen einzelne Nachrichten in Echtzeit aus mehreren Angebotsvarianten auswählen?**
   - Ja → [Cross-Channel-Journey mit Entscheidungsfindung](campaign-management-orchestration/cross-channel-journey-with-decisioning.md)
   - Keine → [Mehrstufige orchestrierte Journey](campaign-management-orchestration/multi-step-orchestrated-journey.md)
