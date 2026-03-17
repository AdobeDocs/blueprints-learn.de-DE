---
title: Anwendungsfallmuster
description: Erfahren Sie mehr über die Anwendungsfallmuster bei der Implementierung von Adobe Experience Platform und Programmen, um wichtige Geschäftsziele zu erreichen.
solution: Experience Platform, Real-Time Customer Data Platform, Journey Optimizer
doc-type: overview-page
source-git-commit: 61c2666b4546222423e85e52270b436c59d846a3
workflow-type: tm+mt
source-wordcount: '492'
ht-degree: 0%

---


# Anwendungsfallmuster

Anwendungsfallmuster definieren wiederholbare Implementierungsansätze für Adobe Experience Platform und Programme. Jedes Muster beschreibt eine bestimmte Funktion, die Funktionskette, die sie bereitstellt, die beteiligten Anwendungen und die [wichtigen Geschäftsziele](/help/blueprints/business-objectives/overview.md) die sie unterstützt.

Verwenden Sie die folgenden Tabellen, um das Muster zu finden, das Ihren Implementierungsanforderungen entspricht, und folgen Sie dann dem Link zur vollständigen Implementierungsreferenz, einschließlich Optionen, Phasen, Entscheidungshilfen und Experience League-Dokumentation.

## Zielgruppenerstellung und -aktivierung

Die folgenden Muster helfen Ihnen beim Erstellen, Auswerten und Aktivieren von Zielgruppensegmenten über Kanäle und Ziele hinweg.

| Muster | Primäre Funktion | Zentrale Lösungen |
| --- | --- | --- |
| [Audience Activation zu Zielen](audience-building-activation/audience-activation-to-destinations.md) | Auswerten und Veröffentlichen von Zielgruppensegmenten für externe Ziele zum Targeting oder zur Unterdrückung | [!DNL Real-Time CDP] |
| [Zielgruppen-Collaboration mit Segment Match](audience-building-activation/audience-collaboration-segment-match.md) | Freigeben und Abgleichen von Zielgruppensegmenten über Sandboxes oder Organisationen hinweg mithilfe von Segment Match | [!DNL Real-Time CDP], [!DNL Experience Platform] |
| [Ereignisweiterleitung](audience-building-activation/event-forwarding.md) | Weiterleiten von über Edge Network erfassten Echtzeit-Ereignisdaten an Ziele, die nicht mit Adobe verbunden sind | [!DNL Experience Platform] (Edge Network, Ereignisweiterleitung) |
| [B2B: Zielgruppenaktivierung](audience-building-activation/b2b-audience-activation.md) | Account-basierte B2B-Zielgruppen über Web-, E-Mail- und Werbekanäle aktivieren | [!DNL Real-Time CDP] B2B edition |

## Personalisierung

Die folgenden Muster bieten bekannten und unbekannten Besuchern über Web- und App-Oberflächen hinweg maßgeschneiderte Erlebnisse.

| Muster | Primäre Funktion | Zentrale Lösungen |
| --- | --- | --- |
| [Web-Personalization für anonyme Besucher](personalization/anonymous-visitor-web-personalization.md) | Bereitstellen von personalisierten Inhalten basierend auf sitzungsinternen Verhaltenssignalen für nicht identifizierte Besucher | [!DNL Journey Optimizer] (Web-Kanal), [!DNL Real-Time CDP] |
| [Web-/App-Personalization für bekannte Besucher](personalization/known-visitor-web-app-personalization.md) | Bereitstellung personalisierter Inhalte, Angebote oder Promotions für identifizierte Besucher auf der Grundlage von Echtzeit-Profil und Segmentzugehörigkeit | [!DNL Journey Optimizer], [!DNL Real-Time CDP] |
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
| [Customer Analytics und Insight Generation](analysis/customer-analytics-insight-generation.md) | Erstellen von kanalübergreifenden Analyse-Arbeitsbereichen, berechneten Metriken und Dashboards für die Verhaltens- und Leistungsanalyse | [!DNL Customer Journey Analytics], [!DNL Experience Platform] |
| [B2B Analytics](analysis/b2b-analytics.md) | Informationen auf B2B-Kontoebene in die kanalübergreifende Journey-Analyse für Kunden einschließen | [!DNL Customer Journey Analytics] B2B edition, [!DNL Real-Time CDP] B2B edition |

## Gesprächserfahrung

Die folgenden Muster ermöglichen KI-gestützte, markensichere Gesprächsinteraktionen über digitale Eigenschaften.

| Muster | Primäre Funktion | Zentrale Lösungen |
| --- | --- | --- |
| [Brand Concierge-Gesprächserlebnis](conversational-experience/brand-concierge-conversational-experience.md) | Transformieren Sie digitale Eigenschaften in KI-gestützte, markensichere Gesprächserlebnisse, die die Kundenfindung leiten | [!DNL Brand Concierge], [!DNL Experience Platform], [!DNL Real-Time CDP] |
