---
title: offer decisioning auf dem Hub
description: Bereitstellung personalisierter Angebote für Verbraucher über Kanäle, einschließlich Kiosks, durch Agenten unterstützte Erlebnisse sowie in E-Mail- und anderen ausgehenden Sendungen.
solution: Experience Platform, Journey Optimizer
exl-id: 5a386e18-bbac-4216-a35f-0a5016785e4a
source-git-commit: 7f566536c4ff5a6af321d60058ad67c13c28bf64
workflow-type: tm+mt
source-wordcount: '904'
ht-degree: 28%

---

# Journey Optimizer - Offer decisioning am Hub

Weitere Informationen zur Entscheidungsverwaltung finden Sie in der Produktdokumentation [HIER](https://experienceleague.adobe.com/docs/journey-optimizer/using/offer-decisioniong/get-started-decision/starting-offer-decisioning.html) und die Offer decisioning-Übersicht [HIER](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/customer-journeys/journey-optimizer/offer-decisioning/offers-overview.html)

Adobe Decisioning Management ist ein Dienst, der im Rahmen von Adobe Journey Optimizer bereitgestellt wird. In diesem Blueprint werden die Anwendungsfälle und technischen Funktionen der Anwendung erläutert und ein tiefer Einblick in die verschiedenen architektonischen Komponenten und Überlegungen, aus denen Offer decisioning besteht, geboten.

Journey Optimizer wird verwendet, um Ihren Kunden zur richtigen Zeit über alle Touchpoints hinweg das beste Angebot und Erlebnis bereitzustellen. offer decisioning erleichtert die Personalisierung mit einer zentralen Bibliothek von Marketing-Angeboten und einer Entscheidungs-Engine, die Regeln und Einschränkungen auf von Adobe Experience Platform erstellte umfangreiche Echtzeitprofile anwendet, damit Sie Ihren Kunden zum richtigen Zeitpunkt das richtige Angebot unterbreiten können.

Die Entscheidungsverwaltung kann auf zwei Arten bereitgestellt werden. Die erste erfolgt über den Adobe Experience Platform-Hub, eine zentrale Rechenzentrumsarchitektur. Im &quot;Hub&quot;-Ansatz werden Angebote in einer Latenz von mehr als 500 ms ausgeführt, personalisiert und bereitgestellt. Die Hub-Architektur eignet sich daher am besten für Kundenerlebnisse, die keine Latenz unterhalb der Sekunde erfordern. Beispiele sind Angebotsentscheidungen, die für Kiosks oder durch Agenten unterstützte Erlebnisse wie in Callcentern oder in persönlichen Interaktionen bereitgestellt werden. Angebote, die in E-Mails und ausgehende Kampagnen eingefügt werden, basieren ebenfalls auf dem Hub-Ansatz.

Der zweite Ansatz erfolgt über das Experience Edge Network, eine global verteilte, geografisch verteilte Infrastruktur, die schnelle Erlebnisse auf einer Untersekunde und einer Millisekunde bereitstellt. Das Endverbrauchererlebnis, das von der Edge-Infrastruktur ausgeführt wird, die dem geografischen Standort der Verbraucher am nächsten ist, um Latenzzeiten zu minimieren. Die Entscheidungsverwaltung in Edge dient der Bereitstellung von Echtzeit-Kundenerlebnissen wie Web- oder mobilen eingehenden Personalisierungsanfragen.

In diesem Entwurf werden die Besonderheiten des Entscheidungsmanagements in der Drehscheibe behandelt.

Weitere Informationen zur Entscheidungsverwaltung an Edge finden Sie im Abschnitt [Entscheidungsverwaltung am Rand](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/customer-journeys/journey-optimizer/offer-decisioning/offers-edge.html) Blueprint.

## Anwendungsfälle für die Entscheidungsverwaltung auf dem Hub

* Personalisierte Angebote auf Kiosks und in Store-Erlebnissen
* Personalisierte Angebote über agentengestützte Erlebnisse wie Callcenter oder Verkaufsinteraktionen.
* Angebote in E-Mail, SMS oder anderen ausgehenden Interaktionen.
* Kanalübergreifende Journey-Ausführung - Bietet über Adobe Journey Optimizer Konsistenz über Web-, Mobile-, E-Mail- und andere Interaktionskanäle hinweg.

<br>

## Architektur

<img src="../assets/offers_hub.svg" alt="Offer decisioning der Referenzarchitektur auf dem Edge-Blueprint" style="width:100%; border:1px solid #4a4a4a" />

<br>

## Integrationsmuster

| Integration | Beschreibung |
| :-- | :--- |
| [offer decisioning mit Adobe Target](https://experienceleague.adobe.com/docs/target/using/integrate/ajo/offer-decision.html) | offer decisioning kann in Adobe Target integriert werden, sodass Angebote getestet und als Target-Erlebnisse bereitgestellt werden können. |

## Voraussetzungen

Adobe Experience Platform

* Schemas und Datensätze müssen im System konfiguriert werden, bevor Sie Journey Optimizer-Datenquellen konfigurieren können.
* Fügen Sie für Schemas, die auf der Klasse „Erlebnisereignis“ basieren, die Feldgruppe „Orchestrierungsereignis-ID“ hinzu, wenn ein Ereignis ausgelöst werden soll, das kein regelbasiertes Ereignis ist.
* Fügen Sie für Schemas, die auf der Klasse „Individuelles Profil“ basieren, die Feldgruppe „Profil-Testdetails“ hinzu, um die Testprofile für die Verwendung mit Journey Optimizer laden zu können

<br>

## Leitlinien

* Informationen zu den Limits in Journey Optimizer finden Sie unter: [Journey Optimizer-Schutzmechanismen](https://experienceleague.adobe.com/docs/journey-optimizer/using/get-started/limitations.html).
* Offer decisioning-Limits: [offer decisioning Produktbeschreibung](https://helpx.adobe.com/legal/product-descriptions/offer-decisioning-app-service.html).


### Leitlinien für die Datenaufnahme

<img src="../assets/aep-data-ingestion-details-latency.svg" alt="Referenzarchitektur für die Blueprint „Journey Optimizer“" style="width:80%; border:1px solid #4a4a4a" />

<br>

### Leitlinien für die Aktivierung

<img src="../assets/ajo-activation-details-latency.svg" alt="Referenzarchitektur für die Blueprint „Journey Optimizer“" style="width:80%; border:1px solid #4a4a4a" />

<br>

## Implementierungsmuster

* Implementiert in E-Mail-, SMS- und ausgehenden Kanälen über eine direkte Integration mit [Adobe Journey Optimizer](https://experienceleague.adobe.com/docs/journey-optimizer/using/offer-decisioniong/get-started-decision/offers-e2e.html).
* Für eine Server-API-basierte Implementierung von Offer decisioning nutzen Sie die [Decisioning API](https://experienceleague.adobe.com/docs/journey-optimizer/using/offer-decisioniong/api-reference/offer-delivery/decisioning-vs-edge-apis.html).
* Verwenden Sie für die Implementierung der Batch-basierten Entscheidung, Angebote stapelweise an eine Nachrichtenversand-Anwendung zu senden, den [Batch Decisioning-API](https://experienceleague.adobe.com/docs/journey-optimizer/using/offer-decisioniong/api-reference/offer-delivery/batch-decisioning-api.html).
* Verwenden Sie für Edge-basierte Echtzeit-Erlebnisse das Web/Mobile SDK oder die Edge Decisioning-API, wie im Abschnitt [offer decisioning auf dem Edge-Blueprint](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/customer-journeys/journey-optimizer/offer-decisioning/offers-edge.html).
<br>

## Implementierungsschritte

### Adobe Experience Platform

#### Schema/Datensätze

1. [Konfigurieren Sie das individuelle Profil, das Erlebnisereignis und Schemas mit mehreren Einheiten](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2021.1.xdm) in Experience Platform basierend auf den vom Kunden angegebenen Daten.
1. [Erstellen Sie Datensätze](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-ingestion/create-datasets-and-ingest-data.html?lang=de) in Experience Platform für die aufzunehmenden Daten.
1. [Fügen Sie dem Datensatz in Experience Platform Datennutzungskennzeichnungen hinzu](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-governance/classify-data-using-governance-labels.html?lang=de), um ordnungsgemäße Governance zu gewährleisten.
1. [Erstellen Sie Richtlinien](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-governance/create-data-usage-policies.html?lang=de), um die Governance an den Zielen umzusetzen.

#### Profil/Identität

1. [Erstellen Sie sämtliche kundenspezifischen Namespaces](https://experienceleague.adobe.com/docs/platform-learn/tutorials/identities/label-ingest-and-verify-identity-data.html?lang=de).
1. [Fügen Sie Identitäten zu Schemas hinzu](https://experienceleague.adobe.com/docs/platform-learn/tutorials/identities/label-ingest-and-verify-identity-data.html).
1. [Aktivieren Sie die Schemas und Datensätze für Profile](https://experienceleague.adobe.com/docs/platform-learn/tutorials/profiles/bring-data-into-the-real-time-customer-profile.html?lang=de).
1. [Richten Sie Zusammenführungsrichtlinien](https://experienceleague.adobe.com/docs/platform-learn/tutorials/profiles/create-merge-policies.html?lang=de) für unterschiedliche Ansichten des [!UICONTROL Echtzeit-Kundenprofils] ein (optional).
1. Erstellen Sie Segmente für die Journey-Nutzung.

#### Quellen/Ziele

1. [Nehmen Sie Daten mit Streaming-APIs und Quellen-Connectoren in Experience Platform auf.](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2020.1.dataingestion&amp;lang=de)

## Verwandte Dokumentation

* [Adobe Experience Platform](https://experienceleague.adobe.com/docs/experience-platform.html)
* [Adobe Journey Optimizer](https://experienceleague.adobe.com/docs/journey-optimizer.html)
* [Entscheidungsverwaltung in Adobe Journey Optimizer](https://experienceleague.adobe.com/docs/journey-optimizer/using/offer-decisioniong/get-started-decision/starting-offer-decisioning.html)
* [Adobe Journey Optimizer-Produktbeschreibung](https://helpx.adobe.com/legal/product-descriptions/adobe-journey-optimizer.html)
* [Adobe Offer decisioning Produktbeschreibung](https://helpx.adobe.com/legal/product-descriptions/offer-decisioning-app-service.html)
