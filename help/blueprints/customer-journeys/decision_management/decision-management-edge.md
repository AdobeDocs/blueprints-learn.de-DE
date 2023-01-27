---
title: Entscheidungsverwaltung im Edge-Blueprint
description: Stellen Sie personalisierte Angebote für Verbraucher über verschiedene Kanäle, einschließlich Echtzeit-Erlebnissen für Web und Mobile, bereit.
solution: Experience Platform, Journey Optimizer
exl-id: 31e5f624-5578-49e1-ab92-5cabd596a632
source-git-commit: b18d491fdefc57762932d1570401b5437bf97c76
workflow-type: tm+mt
source-wordcount: '856'
ht-degree: 95%

---

# Journey Optimizer - Entscheidungsverwaltung im Edge-Blueprint

Weitere Informationen zum Entscheidungs-Management finden Sie [HIER](https://experienceleague.adobe.com/docs/journey-optimizer/using/offer-decisioniong/get-started-decision/starting-offer-decisioning.html?lang=de) in der Produktdokumentation und [HIER](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/customer-journeys/journey-optimizer/decision-management/decision-management-overview.html?lang=de) in der Übersicht über Entscheidungs-Management

Das Entscheidungs-Management von Adobe ist ein Service, der im Rahmen von Adobe Journey Optimizer bereitgestellt wird. In dieser Blueprint werden die Anwendungsfälle und technischen Funktionen des Programms vorgestellt und die verschiedenen Komponenten der Architektur von und Überlegungen zu Entscheidungs-Management eingehend erläutert.

Entscheidungs-Management kann auf zwei Arten bereitgestellt werden. Einerseits über den Adobe Experience Platform-Hub, eine zentrale Rechenzentrums-Architektur. Im „Hub“-Ansatz werden Angebote in zweiter Latenz ausgeführt, personalisiert und bereitgestellt. Die Hub-Architektur eignet sich daher am besten für Kundenerlebnisse, die keine Latenz unterhalb einer Sekunde erfordern. Beispiele sind Angebotsentscheidungen, die für Terminals oder durch Agenten unterstützte Erlebnisse wie in Callcentern oder in persönlichen Interaktionen bereitgestellt werden.

Der zweite Ansatz erfolgt über das Experience Edge Network, eine global verteilte, geografische Infrastruktur, die schnelle Erlebnisse in weniger als einer Sekunde bzw. Millisekunden bereitstellt. Das Endverbrauchererlebnis wird von der Edge-Infrastruktur ausgeführt, die dem geografischen Standort der Verbraucher am nächsten ist, um Latenzzeiten zu minimieren. Das Entscheidungs-Management im Edge ist für Echtzeit-Kundenerlebnisse konzipiert. Dazu gehören Erlebnisse wie über Web oder Mobile eingehende Personalisierungsanfragen.

In dieser Blueprint werden die Besonderheiten des Entscheidungs-Managements im Edge behandelt.

Weitere Informationen zum Entscheidungs-Management auf dem Hub finden Sie in der Blueprint [Entscheidungs-Management auf dem Hub](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/customer-journeys/journey-optimizer/decision-management/decision-management-hub.html?lang=de).

## Anwendungsbeispiele für die Entscheidungsverwaltung am Rand

* Online-Personalisierung über eingehende Web- oder mobile Erlebnisse.
* Kanalübergreifende Journey-Ausführung - Konsistenz in Web, Mobile, E-Mail und auf anderen Interaktionskanälen über Adobe Journey Optimizer.

<br>

## Architektur

<img src="../assets/offers_edge.svg" alt="Referenzarchitektur zur Blueprint „Entscheidungs-Management im Edge“" style="width:100%; border:1px solid #4a4a4a" />

<br>

## Integrationsmuster

| Integration | Beschreibung |
| :-- | :--- |
| [Entscheidungs-Management mit Adobe Target](https://experienceleague.adobe.com/docs/target/using/integrate/ajo/offer-decision.html?lang=de) | Entscheidungs-Management kann mit Adobe Target integriert werden, sodass Angebote getestet und als Target-Erlebnisse bereitgestellt werden können. |

## Voraussetzungen

Adobe Experience Platform

* Schemas und Datensätze müssen im System konfiguriert werden, bevor Sie Journey Optimizer-Datenquellen konfigurieren können.
* Fügen Sie für Schemas, die auf der Klasse „Erlebnisereignis“ basieren, die Feldgruppe „Orchestrierungsereignis-ID“ hinzu, wenn ein Ereignis ausgelöst werden soll, das kein regelbasiertes Ereignis ist.
* Fügen Sie für Schemas, die auf der Klasse „Individuelles Profil“ basieren, die Feldgruppe „Profil-Testdetails“ hinzu, um die Testprofile für die Verwendung mit Journey Optimizer laden zu können.

<br>

## Leitlinien

* Weitere Informationen zu Journey Optimizer finden Sie in den [Leitlinien zu Journey Optimizer](https://experienceleague.adobe.com/docs/journey-optimizer/using/get-started/limitations.html?lang=de).
* Die Leitlinien für Entscheidungs-Management beziehen sich auf die folgende [Produktbeschreibung für Entscheidungs-Management](https://helpx.adobe.com/de/legal/product-descriptions/offer-decisioning-app-service.html).
* Anfragen pro Sekunde = 5.000.
* Latenz der Reaktion &lt; 250 ms.
* Zugriff auf das Edge-Echtzeitprofil. Im Profil sind nur von Edge projizierte Zielgruppen und Profilattribute verfügbar.
* Wenn in erstmaligen Erlebnissen eine Personalisierung erforderlich ist, ist der Hub ideal, da das vollständige Profil verfügbar ist. Das Edge-Profil muss für das erste Edge-Erlebnis vom Hub synchronisiert werden. Daher umfasst das allererste Erlebnis vom Edge keine zuvor in den Hub hochgeladenen Profildaten.

### Limits bei der Datenerfassung

<img src="../../experience-platform/assets/aep_data_flow_guardrails.svg" alt="Datenfluss in Experience Platform" style="border:1px solid #4a4a4a" width="85%" />

<br>

### Limits bei der Aktivierung

<img src="../../experience-platform/assets/AJO_guardrails.svg" alt="Referenzarchitektur für die Blueprint „Journey Optimizer“" style="width:85%; border:1px solid #4a4a4a" />

<br>

## Implementierungsmuster

* Verwenden Sie das Web- oder Mobile-SDK für die Implementierung auf Websites und in Mobile Apps, um Entscheidungs-Management dort zu implementieren, wo das SDK bereitgestellt wurde.
   * [Blueprint: Web/Mobile SDK](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/architecture-overview/deployment/websdk.html?lang=de)
   * [Web SDK](https://experienceleague.adobe.com/docs/experience-platform/edge/personalization/offer-decisioning/offer-decisioning-overview.html?lang=de)
   * [MobileSDK](https://aep-sdks.gitbook.io/docs/)

Oder

* Verwenden Sie die Edge Network Service-API für die direkte API-basierte Server-zu-Server-Implementierung von Entscheidungs-Management.
   * [Edge Network Server-API](https://experienceleague.adobe.com/docs/journey-optimizer/using/offer-decisioniong/api-reference/offer-delivery/deliver-offers.html?lang=de)

<br>

## Implementierungsschritte

### Adobe Experience Platform

#### Schema/Datensätze

1. [Konfigurieren Sie das individuelle Profil, das Erlebnisereignis und Schemas mit mehreren Einheiten](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2021.1.xdm&amp;lang=de) in Experience Platform basierend auf den vom Kunden angegebenen Daten.
1. [Erstellen Sie Datensätze](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-ingestion/create-datasets-and-ingest-data.html?lang=de) in Experience Platform für die aufzunehmenden Daten.
1. [Fügen Sie dem Datensatz in Experience Platform Datennutzungskennzeichnungen hinzu](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-governance/classify-data-using-governance-labels.html?lang=de), um ordnungsgemäße Governance zu gewährleisten.
1. [Erstellen Sie Richtlinien](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-governance/create-data-usage-policies.html?lang=de), um die Governance an den Zielen umzusetzen.

#### Profil/Identität

1. [Erstellen Sie sämtliche kundenspezifischen Namespaces](https://experienceleague.adobe.com/docs/platform-learn/tutorials/identities/label-ingest-and-verify-identity-data.html?lang=de).
1. [Fügen Sie Identitäten zu Schemas hinzu](https://experienceleague.adobe.com/docs/platform-learn/tutorials/identities/label-ingest-and-verify-identity-data.html?lang=de).
1. [Aktivieren Sie die Schemas und Datensätze für Profile](https://experienceleague.adobe.com/docs/platform-learn/tutorials/profiles/bring-data-into-the-real-time-customer-profile.html?lang=de).
1. [Richten Sie Zusammenführungsrichtlinien](https://experienceleague.adobe.com/docs/platform-learn/tutorials/profiles/create-merge-policies.html?lang=de) für unterschiedliche Ansichten des [!UICONTROL Echtzeit-Kundenprofils] ein (optional).
1. Erstellen Sie Segmente für die Journey-Nutzung.

#### Quellen/Ziele

1. [Nehmen Sie Daten mit Streaming-APIs und Quellen-Connectoren in Experience Platform auf.](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2020.1.dataingestion&amp;lang=de)

## Verwandte Dokumentation

* [Adobe Experience Platform](https://experienceleague.adobe.com/docs/experience-platform.html?lang=de)
* [Adobe Journey Optimizer](https://experienceleague.adobe.com/docs/journey-optimizer.html?lang=de)
* [Entscheidungs-Management in Adobe Journey Optimizer](https://experienceleague.adobe.com/docs/journey-optimizer/using/offer-decisioniong/get-started-decision/starting-offer-decisioning.html?lang=de)
* [Produktbeschreibung zu Adobe Journey Optimizer](https://helpx.adobe.com/de/legal/product-descriptions/adobe-journey-optimizer.html)
* [Produktbeschreibung für das Entscheidungs-Management von Adobe](https://helpx.adobe.com/de/legal/product-descriptions/offer-decisioning-app-service.html)
