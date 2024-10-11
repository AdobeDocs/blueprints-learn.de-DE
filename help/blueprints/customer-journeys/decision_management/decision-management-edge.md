---
title: 'Blueprint: Entscheidungs-Management im Edge'
description: Stellen Sie personalisierte Angebote für Verbraucher über verschiedene Kanäle, einschließlich Echtzeit-Erlebnissen für Web und Mobile, bereit.
solution: Experience Platform, Journey Optimizer
exl-id: 31e5f624-5578-49e1-ab92-5cabd596a632
source-git-commit: f6c4a0f39acdc177ac23c4314d2f50f793cbf270
workflow-type: tm+mt
source-wordcount: '395'
ht-degree: 68%

---

# Journey Optimizer - [!DNL Decision Management] auf dem Edge-Blueprint

[!DNL Decision Management] ist ein Dienst, der als Teil von [!DNL Journey Optimizer] bereitgestellt wird. In dieser Blueprint werden die Anwendungsfälle und technischen Funktionen des Programms vorgestellt und die verschiedenen Komponenten der Architektur von und Überlegungen zu Entscheidungs-Management eingehend erläutert.

>[!MORELIKETHIS]
>
>Weitere Informationen zu [!DNL Decision Management] finden Sie in der [Blueprint-Übersicht](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/customer-journeys/journey-optimizer/decision-management/decision-management-overview.html?lang=de) oder in der [Produktdokumentation](https://experienceleague.adobe.com/docs/journey-optimizer/using/offer-decisioniong/get-started-decision/starting-offer-decisioning.html?lang=de).

[!DNL Decision Management] kann auf zwei Arten bereitgestellt werden. Der erste erfolgt über den [!DNL Experience Platform] Hub, einer zentralen Rechenzentrumsarchitektur. Im „Hub“-Ansatz werden Angebote in zweiter Latenz ausgeführt, personalisiert und bereitgestellt. Die Hub-Architektur eignet sich daher am besten für Kundenerlebnisse, die keine Latenz unterhalb einer Sekunde erfordern. Beispiele sind Angebotsentscheidungen, die für Terminals oder durch Agenten unterstützte Erlebnisse wie in Callcentern oder in persönlichen Interaktionen bereitgestellt werden.

Der zweite Ansatz erfolgt über die Experience Platform [!DNL Edge Network], die eine global verteilte geografisch verteilte Infrastruktur ist, die schnelle Erlebnisse auf einer Sub- und Millisekunde ermöglicht. Das Endverbrauchererlebnis, das von der Edge-Infrastruktur ausgeführt wird, die dem geografischen Standort der Verbraucher am nächsten ist, um Latenzzeiten zu minimieren. [!DNL Decision Management] in der Edge ist für Echtzeit-Kundenerlebnisse konzipiert. Dazu gehören Erlebnisse wie über Web oder Mobile eingehende Personalisierungsanfragen.

In dieser Blueprint werden die Besonderheiten des Entscheidungs-Managements im Edge behandelt.

Weitere Informationen zum Entscheidungs-Management auf dem Hub finden Sie in der Blueprint [Entscheidungs-Management auf dem Hub](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/customer-journeys/journey-optimizer/decision-management/decision-management-hub.html?lang=de).

## Anwendungsfälle für das Entscheidungs-Management im Edge

* Streaming-Anwendungsfälle, in denen die Latenz des Profilkontexts strikt unter 15 Minuten Latenz liegt und die Ausführung der Entscheidungsverwaltung unter einer Sekunde erfolgt.
* Online-Personalisierung über eingehende Web- oder mobile Erlebnisse.
* Kanalübergreifende Journey-Ausführung - Konsistenz in Web, Mobile, E-Mail und auf anderen Interaktionskanälen über Adobe Journey Optimizer.

## Architektur

<img src="../assets/offers_edge.svg" alt="Referenzarchitektur zur Blueprint „Entscheidungs-Management im Edge“" style="width:100%; border:1px solid #4a4a4a" class="modal-image" />

## Integrationsmuster

| Integration | Beschreibung |
| :-- | :--- |
| [Entscheidungs-Management mit Adobe Target](https://experienceleague.adobe.com/docs/target/using/integrate/ajo/offer-decision.html?lang=de) | Entscheidungs-Management kann mit Adobe Target integriert werden, sodass Angebote getestet und als Target-Erlebnisse bereitgestellt werden können. |

## Leitlinien

* Weitere Informationen zu Journey Optimizer finden Sie in den [Leitlinien zu Journey Optimizer](https://experienceleague.adobe.com/docs/journey-optimizer/using/get-started/limitations.html?lang=de).

* Die Leitlinien für Entscheidungs-Management beziehen sich auf die folgende [Produktbeschreibung für Entscheidungs-Management](https://helpx.adobe.com/de/legal/product-descriptions/offer-decisioning-app-service.html).

[Limits und Ende-zu-Ende-Latenzrichtlinien](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/architecture-overview/deployment/guardrails.html)

## Verwandte Dokumentation

* [Adobe Experience Platform](https://experienceleague.adobe.com/docs/experience-platform.html?lang=de)
* [Adobe Journey Optimizer](https://experienceleague.adobe.com/docs/journey-optimizer.html?lang=de)
* [Entscheidungs-Management in Adobe Journey Optimizer](https://experienceleague.adobe.com/docs/journey-optimizer/using/offer-decisioniong/get-started-decision/starting-offer-decisioning.html?lang=de)
* [Produktbeschreibung zu Adobe Journey Optimizer](https://helpx.adobe.com/de/legal/product-descriptions/adobe-journey-optimizer.html)
* [Produktbeschreibung für das Entscheidungs-Management von Adobe](https://helpx.adobe.com/de/legal/product-descriptions/offer-decisioning-app-service.html)
