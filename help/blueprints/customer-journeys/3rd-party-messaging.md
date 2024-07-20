---
title: 'Blueprint: Journey Optimizer - Drittanbieter-Messaging'
description: Zeigt, wie Adobe Journey Optimizer mit Drittanbieter-Messaging-Systemen genutzt werden kann, um personalisierte Kommunikation zu orchestrieren und zu senden.
solution: Journey Optimizer
exl-id: 3a14fc06-6d9c-4cd8-bc5c-f38e253d53ce
source-git-commit: 60a7785ea0ec4ee83fd9a1e843f0b84fc4cb1150
workflow-type: tm+mt
source-wordcount: '419'
ht-degree: 97%

---

# Blueprint: Drittanbieter-Messaging

Zeigt, wie Adobe Journey Optimizer mit Drittanbieter-Messaging-Systemen genutzt werden kann, um personalisierte Kommunikation zu orchestrieren und zu senden.

<br>

## Architektur

<img src="assets/3rd-party-messaging-architecture.svg" alt="Referenzarchitektur für die Blueprint „Journey Optimizer“" style="width:100%; border:1px solid #4a4a4a" class="modal-image" />

<br>

## Voraussetzungen

Adobe Experience Platform

* Schemas und Datensätze müssen im System konfiguriert werden, bevor Sie Journey Optimizer-Datenquellen konfigurieren können.
* Fügen Sie für Schemas, die auf der Klasse „Erlebnisereignis“ basieren, die Feldgruppe „Orchestrierungsereignis-ID“ hinzu, wenn ein Ereignis ausgelöst werden soll, das kein regelbasiertes Ereignis ist.
* Fügen Sie für Schemas, die auf der Klasse „Individuelles Profil“ basieren, die Feldgruppe „Profil-Testdetails“ hinzu, um die Testprofile für die Verwendung mit Journey Optimizer laden zu können.

Drittanbieter-Messaging-Programm

* Muss REST-API-Aufrufe zum Senden von Transaktions-Payloads unterstützen

<br>

## Leitlinien

[Produkt-Link zu Journey Optimizer-Leitlinien](https://experienceleague.adobe.com/docs/journeys/using/starting-with-journeys/limitations.html?lang=de)

[Limits und Ende-zu-Ende-Latenzrichtlinien](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/architecture-overview/deployment/guardrails.html)


## Implementierungsschritte

### Adobe Experience Platform

#### Schema/Datensätze

1. [Konfigurieren Sie das individuelle Profil, das Erlebnisereignis und Schemas mit mehreren Einheiten](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2021.1.xdm&amp;lang=de) in Experience Platform basierend auf den von der Kundin oder dem Kunden angegebenen Daten.
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

1. [Nehmen Sie Daten mit Streaming-APIs und Quell-Connectoren in Experience Platform auf.](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2020.1.dataingestion&amp;lang=de)

### Journey Optimizer

1. Konfigurieren Sie die Experience Platform-Datenquelle und bestimmen Sie, welche Felder als Teil des Profils zwischengespeichert werden sollen. Streaming-Daten, die zum Auslösen einer Customer Journey verwendet werden, müssen zunächst in Journey Optimizer konfiguriert werden, damit eine Orchestrierungs-ID erstellt wird. Die Orchestrierungs-ID wird dann an den Entwickler weitergegeben, der sie bei der Aufnahme nutzen kann
1. Konfigurieren Sie externe Datenquellen
1. Konfigurieren Sie benutzerdefinierte Aktionen für ein Drittanbieterprogramme

### Mobilgeräte-Push-Konfiguration (optional, da Drittanbieter möglicherweise Token sammelt)

1. Implementieren Sie das Experience Platform Mobile SDK zum Sammeln von Push-Tokens und Login-Informationen zum Abgleich mit Kundenprofilen
1. Nutzen Sie Adobe Tags und erstellen Sie eine Mobile-Präsenz mit der folgenden Erweiterung:
   * Adobe Journey Optimizer
   * Adobe Experience Platform Edge Network
   * Identität für [!DNL Edge Network]
   * Mobile Core
1. Stellen Sie sicher, dass Sie über einen dedizierten Daten-Stream für Mobile-App-Implementierungen verfügen, der sich von dem für Web-Implementierungen unterscheidet
1. Weitere Informationen finden Sie im [Mobile-Handbuch für Adobe Journey Optimizer](https://developer.adobe.com/client-sdks/documentation/adobe-journey-optimizer/)

<br>

## Verwandte Dokumentation

* [Dokumentation zu Experience Platform ](https://experienceleague.adobe.com/docs/experience-platform.html?lang=de)
* [Dokumentation zu Experience Platform Tags ](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=de)
* [Dokumentation zu Experience Platform Mobile SDK](https://experienceleague.adobe.com/docs/mobile.html?lang=de)
* [Dokumentation zu Journey Optimizer](https://experienceleague.adobe.com/docs/journey-optimizer/using/ajo-home.html?lang=de)
* [Produktbeschreibung zu Journey Optimizer](https://helpx.adobe.com/de/legal/product-descriptions/adobe-journey-optimizer.html)
