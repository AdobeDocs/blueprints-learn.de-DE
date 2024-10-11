---
title: 'Blueprint: Entscheidungs-Management auf dem Hub'
description: Stellen Sie personalisierte Angebote für Verbraucher über Kanäle bereit, einschließlich Terminals, durch Agenten unterstützte Erlebnisse sowie in E-Mails und anderen ausgehenden Sendungen.
solution: Experience Platform, Journey Optimizer
exl-id: 5a386e18-bbac-4216-a35f-0a5016785e4a
source-git-commit: f6c4a0f39acdc177ac23c4314d2f50f793cbf270
workflow-type: tm+mt
source-wordcount: '656'
ht-degree: 80%

---

# Blueprint: Entscheidungs-Management auf dem Hub

Weitere Informationen zum Entscheidungs-Management finden Sie [HIER](https://experienceleague.adobe.com/docs/journey-optimizer/using/offer-decisioniong/get-started-decision/starting-offer-decisioning.html?lang=de) in der Produktdokumentation und [HIER](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/customer-journeys/journey-optimizer/decision-management/decision-management-overview.html?lang=de) in der Übersicht über Entscheidungs-Management

Das Entscheidungs-Management von Adobe ist ein Service, der im Rahmen von Adobe Journey Optimizer bereitgestellt wird. In dieser Blueprint werden die Anwendungsfälle und technischen Funktionen des Programms vorgestellt und die verschiedenen Komponenten der Architektur von und Überlegungen zu Entscheidungs-Management eingehend erläutert.

Journey Optimizer wird verwendet, um Ihren Kunden zur richtigen Zeit auf allen Touchpoints das beste Angebot und Erlebnis bereitzustellen. Entscheidungs-Management ermöglicht die Personalisierung durch eine zentrale Bibliothek von Marketing-Angeboten und eine Entscheidungs-Engine, die Regeln und Einschränkungen auf umfangreiche Echtzeitprofile anwendet, die auf Adobe Experience Platform erstellt wurden. Dadurch können Sie Ihren Kunden zum richtigen Zeitpunkt das richtige Angebot unterbreiten.

Entscheidungs-Management kann auf zwei Arten bereitgestellt werden. Einerseits über den Adobe Experience Platform-Hub, eine zentrale Rechenzentrums-Architektur. Im „Hub“-Ansatz werden Angebote mit >500 ms Latenz ausgeführt, personalisiert und bereitgestellt. Die Hub-Architektur eignet sich daher am besten für Kundenerlebnisse, die keine Latenz unterhalb einer Sekunde erfordern. Beispiele sind Angebotsentscheidungen, die für Terminals oder durch Agenten unterstützte Erlebnisse wie in Callcentern oder in persönlichen Interaktionen bereitgestellt werden. In E-Mails und ausgehende Kampagnen eingefügt Angebote werden ebenfalls vom Hub-Ansatz unterstützt.

Der zweite Ansatz erfolgt über das Erlebnis [!DNL [!DNL Edge Network]], eine global verteilte, geografisch verteilte Infrastruktur, die schnelle Erlebnisse auf einer Sekunde und einer Millisekunde bietet. Das Endverbrauchererlebnis wird von der Edge-Infrastruktur ausgeführt, die dem geografischen Standort der Verbraucher am nächsten ist, um Latenzzeiten zu minimieren. Das Entscheidungs-Management im Edge ist für Echtzeit-Kundenerlebnisse konzipiert, wie über Web oder Mobile eingehende Personalisierungsanfragen.

In dieser Blueprint werden die Besonderheiten des Entscheidungs-Managements auf dem Hub behandelt.

Weitere Informationen zum Entscheidungs-Management im Edge finden Sie in der Blueprint [Entscheidungs-Management im Edge](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/customer-journeys/journey-optimizer/decision-management/decision-management-edge.html?lang=de).

## Anwendungsfälle für das Entscheidungs-Management auf dem Hub

* Streaming-Anwendungsfälle, in denen die Latenz des Profilkontexts nicht streng ist - Latenz 15 Minuten oder höher.
* Personalisierte Angebote für Terminals und Erlebnisse im Laden.
* Personalisierte Angebote über von Agenten unterstützte Erlebnisse wie Callcenter oder Vertriebsinteraktionen.
* Angebote in E-Mails, SMS, Mobilgeräte-Push-Benachrichtigungen oder anderen ausgehenden Interaktionen.
* Bereitstellung von Angeboten für externe ESP- und Messaging-Systeme, um sie unterbreiten zu können.
* Kanalübergreifende Journey-Ausführung - Konsistenz in Web, Mobile, E-Mail und auf anderen Interaktionskanälen über Adobe Journey Optimizer.

>[!IMPORTANT]
>
>Bei Angebots- und Journey-Anwendungsfällen, bei denen für zusätzliche Informationen und Kontext auf das Profil zugegriffen werden muss. Es ist wichtig, die damit verbundene Latenz der Aufnahme von Daten in das Profil auf dem Hub zu berücksichtigen, um sicherzustellen, dass sie zum Zeitpunkt der Entscheidung verfügbar ist. In Szenarien, in denen der Kontext Streaming oder Erfassen in das Profil ist und der Kontext bzw. die Journey diesen Kontext innerhalb von Sekunden oder Minuten nach der Angebotsentscheidung verfügbar machen muss, sollten diese Szenarien am besten mit der Entscheidungsverwaltung in der Edge bedient werden.

## Architektur

<img src="../assets/offers_hub.svg" alt="Referenzarchitektur zur Blueprint „Entscheidungs-Management im Edge“" style="width:100%; border:1px solid #4a4a4a" class="modal-image" />

## Leitlinien

* Weitere Informationen zu Journey Optimizer finden Sie in den [Leitlinien zu Journey Optimizer](https://experienceleague.adobe.com/docs/journey-optimizer/using/get-started/limitations.html?lang=de).
* Die Leitlinien für Entscheidungs-Management beziehen sich auf die folgende [Produktbeschreibung für Entscheidungs-Management](https://helpx.adobe.com/de/legal/product-descriptions/offer-decisioning-app-service.html).

[Limits und Ende-zu-Ende-Latenzrichtlinien](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/architecture-overview/deployment/guardrails.html)

## Implementierungsmuster

* Implementiert in E-Mails, SMS und ausgehenden Kanälen über eine direkte Integration mit [Adobe Journey Optimizer](https://experienceleague.adobe.com/docs/journey-optimizer/using/offer-decisioniong/get-started-decision/offers-e2e.html?lang=de).
* Nutzen Sie für eine Server-API-basierte Implementierung von Entscheidungs-Management die [Decisioning-API](https://experienceleague.adobe.com/docs/journey-optimizer/using/offer-decisioniong/api-reference/offer-delivery/decisioning-vs-edge-apis.html?lang=de).
* Verwenden Sie für die Implementierung Batch-basierter Entscheidung, um Angebote stapelweise für ein Nachrichtenversand-Programm bereitzustellen, die [Batch Decisioning-API](https://experienceleague.adobe.com/docs/journey-optimizer/using/offer-decisioniong/api-reference/offer-delivery/batch-decisioning-api.html?lang=de).
* Verwenden Sie für Edge-basierte Echtzeit-Erlebnisse das Web/Mobile SDK oder die Edge Decisioning-API, wie in der Blueprint [Entscheidungs-Management im Edge](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/customer-journeys/journey-optimizer/decision-management/decision-management-edge.html?lang=de) erläutert.

## Verwandte Dokumentation

* [Adobe Experience Platform](https://experienceleague.adobe.com/docs/experience-platform.html?lang=de)
* [Adobe Journey Optimizer](https://experienceleague.adobe.com/docs/journey-optimizer.html?lang=de)
* [Entscheidungs-Management in Adobe Journey Optimizer](https://experienceleague.adobe.com/docs/journey-optimizer/using/offer-decisioniong/get-started-decision/starting-offer-decisioning.html?lang=de)
* [Produktbeschreibung zu Adobe Journey Optimizer](https://helpx.adobe.com/de/legal/product-descriptions/adobe-journey-optimizer.html)
* [Produktbeschreibung für das Entscheidungs-Management von Adobe](https://helpx.adobe.com/de/legal/product-descriptions/offer-decisioning-app-service.html)
