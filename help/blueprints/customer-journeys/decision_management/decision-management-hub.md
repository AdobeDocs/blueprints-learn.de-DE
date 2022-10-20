---
title: Entscheidungs-Management am Hub
description: Stellen Sie personalisierte Angebote für Verbraucher über Kanäle bereit, einschließlich Terminals, durch Agenten unterstützte Erlebnisse sowie in E-Mails und anderen ausgehenden Sendungen.
solution: Experience Platform, Journey Optimizer
exl-id: 5a386e18-bbac-4216-a35f-0a5016785e4a
source-git-commit: 1c05a017e7729d2be676203c2bc06bddd5f9141a
workflow-type: tm+mt
source-wordcount: '906'
ht-degree: 96%

---

# Journey Optimizer - Entscheidungs-Management auf dem Hub

Weitere Informationen zum Entscheidungs-Management finden Sie [HIER](https://experienceleague.adobe.com/docs/journey-optimizer/using/offer-decisioniong/get-started-decision/starting-offer-decisioning.html?lang=de) in der Produktdokumentation und [HIER](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/customer-journeys/journey-optimizer/decision-management/decision-management-overview.html?lang=en) in der Übersicht über Entscheidungs-Management

Das Entscheidungs-Management von Adobe ist ein Service, der im Rahmen von Adobe Journey Optimizer bereitgestellt wird. In dieser Blueprint werden die Anwendungsfälle und technischen Funktionen des Programms vorgestellt und die verschiedenen Komponenten der Architektur von und Überlegungen zu Entscheidungs-Management eingehend erläutert.

Journey Optimizer wird verwendet, um Ihren Kunden zur richtigen Zeit auf allen Touchpoints das beste Angebot und Erlebnis bereitzustellen. Entscheidungs-Management ermöglicht die Personalisierung durch eine zentrale Bibliothek von Marketing-Angeboten und eine Entscheidungs-Engine, die Regeln und Einschränkungen auf umfangreiche Echtzeitprofile anwendet, die auf Adobe Experience Platform erstellt wurden. Dadurch können Sie Ihren Kunden zum richtigen Zeitpunkt das richtige Angebot unterbreiten.

Entscheidungs-Management kann auf zwei Arten bereitgestellt werden. Einerseits über den Adobe Experience Platform-Hub, eine zentrale Rechenzentrums-Architektur. Im „Hub“-Ansatz werden Angebote mit >500 ms Latenz ausgeführt, personalisiert und bereitgestellt. Die Hub-Architektur eignet sich daher am besten für Kundenerlebnisse, die keine Latenz unterhalb einer Sekunde erfordern. Beispiele sind Angebotsentscheidungen, die für Terminals oder durch Agenten unterstützte Erlebnisse wie in Callcentern oder in persönlichen Interaktionen bereitgestellt werden. In E-Mails und ausgehende Kampagnen eingefügt Angebote werden ebenfalls vom Hub-Ansatz unterstützt.

Der zweite Ansatz erfolgt über das Experience Edge Network, eine global verteilte, geografische Infrastruktur, die schnelle Erlebnisse in weniger als einer Sekunde bzw. Millisekunden bereitstellt. Das Endverbrauchererlebnis wird von der Edge-Infrastruktur ausgeführt, die dem geografischen Standort der Verbraucher am nächsten ist, um Latenzzeiten zu minimieren. Das Entscheidungs-Management im Edge ist für Echtzeit-Kundenerlebnisse konzipiert, wie über Web oder Mobile eingehende Personalisierungsanfragen.

In dieser Blueprint werden die Besonderheiten des Entscheidungs-Managements auf dem Hub behandelt.

Weitere Informationen zum Entscheidungs-Management im Edge finden Sie in der Blueprint [Entscheidungs-Management im Edge](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/customer-journeys/journey-optimizer/decision-management/decision-management-edge.html?lang=en).

## Anwendungsfälle für das Entscheidungs-Management auf dem Hub

* Personalisierte Angebote für Terminals und Erlebnisse im Laden.
* Personalisierte Angebote über von Agenten unterstützte Erlebnisse wie Callcenter oder Vertriebsinteraktionen.
* Angebote in E-Mails, SMS, Mobile-Push-Benachrichtigungen oder anderen ausgehenden Interaktionen.
* Bereitstellung von Angeboten für externe ESP- und Messaging-Systeme, um sie unterbreiten zu können.
* Kanalübergreifende Journey-Ausführung - Konsistenz in Web, Mobile, E-Mail und auf anderen Interaktionskanälen über Adobe Journey Optimizer.

<br>

## Architektur

<img src="../assets/offers_hub.svg" alt="Referenzarchitektur zur Blueprint „Entscheidungs-Management im Edge“" style="width:100%; border:1px solid #4a4a4a" />

<br>

## Voraussetzungen

Adobe Experience Platform

* Schemas und Datensätze müssen im System konfiguriert werden, bevor Sie Journey Optimizer-Datenquellen konfigurieren können.
* Fügen Sie für Schemas, die auf der Klasse „Erlebnisereignis“ basieren, die Feldgruppe „Orchestrierungsereignis-ID“ hinzu, wenn ein Ereignis ausgelöst werden soll, das kein regelbasiertes Ereignis ist.
* Fügen Sie für Schemas, die auf der Klasse „Individuelles Profil“ basieren, die Feldgruppe „Profil-Testdetails“ hinzu, um die Testprofile für die Verwendung mit Journey Optimizer laden zu können.

<br>

## Leitlinien

* Weitere Informationen zu Journey Optimizer finden Sie in den [Leitlinien zu Journey Optimizer](https://experienceleague.adobe.com/docs/journey-optimizer/using/get-started/limitations.html?lang=de).
* Die Leitlinien für Entscheidungs-Management beziehen sich auf die folgende [Produktbeschreibung für Entscheidungs-Management](https://helpx.adobe.com/de/legal/product-descriptions/offer-decisioning-app-service.html).
* Anfragen pro Sekunde = 2.000.
* Latenz der Reaktion &lt; 500 ms.
* Zugriff auf das gesamte Echtzeit-Kundenprofil, einschließlich Zielgruppenzugehörigkeit, Attributen und Erlebnisereignissen.


### Leitlinien für die Datenaufnahme

<img src="../../experience-platform/assets/aep_data_flow_guardrails.svg" alt="Datenfluss in Experience Platform" style="border:1px solid #4a4a4a" width="85%" />

<br>

### Leitlinien für die Aktivierung

<img src="../../experience-platform/assets/activation-latency.svg" alt="Referenzarchitektur für die Blueprint „Journey Optimizer“" style="width:85%; border:1px solid #4a4a4a" />

<br>

## Implementierungsmuster

* Implementiert in E-Mails, SMS und ausgehenden Kanälen über eine direkte Integration mit [Adobe Journey Optimizer](https://experienceleague.adobe.com/docs/journey-optimizer/using/offer-decisioniong/get-started-decision/offers-e2e.html?lang=de).
* Nutzen Sie für eine Server-API-basierte Implementierung von Entscheidungs-Management die [Decisioning-API](https://experienceleague.adobe.com/docs/journey-optimizer/using/offer-decisioniong/api-reference/offer-delivery/decisioning-vs-edge-apis.html?lang=de).
* Verwenden Sie für die Implementierung Batch-basierter Entscheidung, um Angebote stapelweise für ein Nachrichtenversand-Programm bereitzustellen, die [Batch Decisioning-API](https://experienceleague.adobe.com/docs/journey-optimizer/using/offer-decisioniong/api-reference/offer-delivery/batch-decisioning-api.html?lang=de).
* Verwenden Sie für Edge-basierte Echtzeit-Erlebnisse das Web/Mobile SDK oder die Edge Decisioning-API, wie in der Blueprint [Entscheidungs-Management im Edge](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/customer-journeys/journey-optimizer/decision-management/decision-management-edge.html?lang=en) erläutert.
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

* [Adobe Experience Platform](https://experienceleague.adobe.com/docs/experience-platform.html?lang=de)
* [Adobe Journey Optimizer](https://experienceleague.adobe.com/docs/journey-optimizer.html?lang=de)
* [Entscheidungs-Management in Adobe Journey Optimizer](https://experienceleague.adobe.com/docs/journey-optimizer/using/offer-decisioniong/get-started-decision/starting-offer-decisioning.html)
* [Produktbeschreibung zu Adobe Journey Optimizer](https://helpx.adobe.com/de/legal/product-descriptions/adobe-journey-optimizer.html)
* [Produktbeschreibung für das Entscheidungs-Management von Adobe](https://helpx.adobe.com/legal/product-descriptions/offer-decisioning-app-service.html)
