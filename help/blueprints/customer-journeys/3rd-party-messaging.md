---
title: 'Blueprint: Journey Optimizer - Drittanbieter-Messaging'
description: Zeigt, wie Adobe Journey Optimizer mit Drittanbieter-Messaging-Systemen genutzt werden kann, um personalisierte Kommunikation zu orchestrieren und zu senden.
solution: Journey Optimizer
exl-id: 3a14fc06-6d9c-4cd8-bc5c-f38e253d53ce
source-git-commit: d19555201107b6aa827e63eb8ecff8642d9f967c
workflow-type: ht
source-wordcount: '829'
ht-degree: 100%

---

# Drittanbieter-Messaging

Zeigt, wie Adobe Journey Optimizer mit Drittanbieter-Messaging-Systemen genutzt werden kann, um personalisierte Kommunikation zu orchestrieren und zu senden.

<br>

## Architektur

<img src="assets/3rd-party-messaging-architecture.svg" alt="Referenzarchitektur für die Blueprint „Journey Optimizer“" style="width:100%; border:1px solid #4a4a4a" />

<br>

## Voraussetzungen

Adobe Experience Platform

* Schemas und Datensätze müssen im System konfiguriert werden, bevor Sie Journey Optimizer-Datenquellen konfigurieren können.
* Fügen Sie für Schemas, die auf der Klasse „Erlebnisereignis“ basieren, die Feldgruppe „Orchestrierungsereignis-ID“ hinzu, wenn ein Ereignis ausgelöst werden soll, das kein regelbasiertes Ereignis ist.
* Fügen Sie für Schemas, die auf der Klasse „Individuelles Profil“ basieren, die Feldgruppe „Profil-Testdetails“ hinzu, um die Testprofile für die Verwendung mit Journey Optimizer laden zu können

Drittanbieter-Messaging-Programm

* Muss REST-API-Aufrufe zum Senden von Transaktions-Payloads unterstützen

<br>

## Leitlinien

[Produkt-Link zu Journey Optimizer-Leitlinien](https://experienceleague.adobe.com/docs/journeys/using/starting-with-journeys/limitations.html?lang=de)

Weitere Leitlinien für Journey Optimizer:

* Die Begrenzung ist jetzt über eine API möglich. So wird sichergestellt, dass das Zielsystem nicht so überlastet wird, dass ein Fehler auftritt. Dies bedeutet, dass Nachrichten, die die Begrenzung überschreiten, vollständig ignoriert und niemals gesendet werden. Drosselung wird nicht unterstützt.
   * Max. Verbindungen: Maximale Zahl der http/s-Verbindungen, die ein Ziel bewältigen kann
   * Max. Aufrufanzahl: Maximale Aufrufzahl, die im Parameter periodInMs erfolgen kann
   * periodInMs: Zeit in Millisekunden
* Von der Segmentzugehörigkeit initiierte Journeys können in zwei Modi operieren:
   * Batch-Segmente (alle 24 Stunden aktualisiert)
   * Streaming-Segmente (Qualifikation &lt;5 Minuten)
* Batch-Segmente: Stellen Sie sicher, dass Sie das tägliche Volumen an qualifizierten Nutzern verstehen und dass das Zielsystem den maximalen Durchsatz pro Journey und für sämtliche Journeys bewältigen kann
* Streaming-Segmente: Stellen Sie sicher, dass der erste Strom von Profilqualifikationen neben täglichen Streaming-Volumen pro Journey und für sämtliche Journeys bewältigt werden kann
* Offer Decisioning wird nicht unterstützt
* Ausgehende Integrationen mit Drittanbietersystemen
   * Keine Unterstützung für einzelne statische IPs, da wir eine Mehrmandanten-Infrastruktur verwenden (alle Daten-Center-IPs müssen aufgelistet sein)
   * Nur die POST- und die PUT-Methode werden für benutzerdefinierte Aktionen unterstützt
   * Authentifizierungsunterstützung: Token | Passwort | OAuth2
* Keine Möglichkeit, einzelne Komponenten von Adobe Experience Platform oder Journey Optimizer zu packen und zwischen verschiedenen Sandboxes zu verschieben. Muss in neuen Umgebungen erneut implementiert werden

<br>

Drittanbieter-Messaging-System

* Es muss bekannt sein, welche Last das System für Transaktions-API-Aufrufe unterstützen kann
   * Anzahl der zulässigen Aufrufe pro Sekunde
   * Anzahl der Verbindungen
* Es muss bekannt sein, welche Authentifizierung für API-Aufrufe erforderlich ist
   * Authentifizierungstyp:  Token | Passwort | OAuth2 über Journey Optimizer unterstützt
   * Authentifizierungs-Aufbewahrungsfrist im Cache:  Wie lang ist das Token gültig? 
* Wenn nur Batch-Aufnahme unterstützt wird, muss in eine Cloud-Speicher-Engine wie Amazon Kinesis oder Azure Event Grid 1st gestreamt werden
   * Daten können per Batch über einen Trichter aus diesen Cloud-Speicher-Engines in die Drittanbieterlösung geleitet werden
   * Die Bereitstellung sämtlicher erforderlicher Middleware liegt in der Verantwortung des Kunden oder des Drittanbieters

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
1. [Fügen Sie Identitäten zu Schemas hinzu](https://experienceleague.adobe.com/docs/platform-learn/tutorials/identities/label-ingest-and-verify-identity-data.html?lang=de).
1. [Aktivieren Sie die Schemas und Datensätze für Profile](https://experienceleague.adobe.com/docs/platform-learn/tutorials/profiles/bring-data-into-the-real-time-customer-profile.html?lang=de).
1. [Richten Sie Zusammenführungsrichtlinien](https://experienceleague.adobe.com/docs/platform-learn/tutorials/profiles/create-merge-policies.html?lang=de) für unterschiedliche Ansichten des [!UICONTROL Echtzeit-Kundenprofils] ein (optional).
1. Erstellen Sie Segmente für die Journey-Nutzung.

#### Quellen/Ziele

1. [Nehmen Sie Daten mit Streaming-APIs und Quellen-Connectoren in Experience Platform auf.](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2020.1.dataingestion&amp;lang=de)

### Journey Optimizer

1. Konfigurieren Sie die Experience Platform-Datenquelle und bestimmen Sie, welche Felder als Teil des Profils zwischengespeichert werden sollen. Streaming-Daten, die zum Auslösen einer Customer Journey verwendet werden, müssen zunächst in Journey Optimizer konfiguriert werden, damit eine Orchestrierungs-ID erstellt wird. Die Orchestrierungs-ID wird dann an den Entwickler weitergegeben, der sie bei der Aufnahme nutzen kann
1. Konfigurieren Sie externe Datenquellen
1. Konfigurieren Sie benutzerdefinierte Aktionen für ein Drittanbieterprogramme

### Mobile-Push-Konfiguration (optional, da Drittanbieter möglicherweise Token sammelt)

1. Implementieren Sie das Experience Platform Mobile SDK zum Sammeln von Push-Tokens und Login-Informationen zum Abgleich mit Kundenprofilen
1. Nutzen Sie Adobe Tags und erstellen Sie eine Mobile-Präsenz mit der folgenden Erweiterung:
   * Adobe Journey Optimizer
   * Adobe Experience Platform Edge Network
   * Identität  für Edge Network
   * Mobile Core
1. Stellen Sie sicher, dass Sie über einen dedizierten Daten-Stream für Mobile-App-Implementierungen verfügen, der sich von dem für Web-Implementierungen unterscheidet
1. Weitere Informationen finden Sie im [Mobile-Handbuch für Adobe Journey Optimizer](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-journey-optimizer)

<br>

## Verwandte Dokumentation

* [Dokumentation zu Experience Platform ](https://experienceleague.adobe.com/docs/experience-platform.html?lang=de)
* [Dokumentation zu Experience Platform Tags ](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=de)
* [Dokumentation zu Experience Platform Mobile SDK](https://experienceleague.adobe.com/docs/mobile.html?lang=de)
* [Dokumentation zu Journey Optimizer](https://experienceleague.adobe.com/docs/journey-optimizer/using/ajo-home.html?lang=de)
* [Produktbeschreibung zu Journey Optimizer](https://helpx.adobe.com/de/legal/product-descriptions/adobe-journey-optimizer.html)
