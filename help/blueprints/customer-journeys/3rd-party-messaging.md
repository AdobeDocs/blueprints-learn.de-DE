---
title: Journey Optimizer - Nachrichten-Blueprint von Drittanbietern
description: Veranschaulicht, wie Adobe Journey Optimizer mit Drittanbieter-Messaging-Systemen verwendet werden kann, um personalisierte Nachrichten zu orchestrieren und zu senden.
solution: Experience Platform, Journey Optimizer
hidefromtoc: true
source-git-commit: a86df4a1b2de38bcb244a6afe1cea87adc7e26fa
workflow-type: tm+mt
source-wordcount: '829'
ht-degree: 35%

---

# Drittanbieter-Nachrichten

Veranschaulicht, wie Adobe Journey Optimizer mit Drittanbieter-Messaging-Systemen verwendet werden kann, um personalisierte Nachrichten zu orchestrieren und zu senden.

<br>

## Architektur

<img src="assets/3rd-party-messaging-architecture.svg" alt="Journey Optimizer-Blueprint zur Referenzarchitektur" style="width:100%; border:1px solid #4a4a4a" />

<br>

## Voraussetzungen

Adobe Experience Platform

* Schemas und Datensätze müssen im System konfiguriert werden, bevor Sie Journey Optimizer-Datenquellen konfigurieren können
* Fügen Sie für klassenbasierte Experience Event-Schemata die Feldergruppe &quot;Orchestration eventID&quot;hinzu, wenn Sie ein Ereignis auslösen möchten, das kein regelbasiertes Ereignis ist
* Fügen Sie für klassenbasierte Einzelprofile die Feldergruppe &quot;Profiltestdetails&quot;hinzu, um Testprofile zur Verwendung mit Journey Optimizer laden zu können.

Messaging-Anwendung von Drittanbietern

* Muss REST-API-Aufrufe zum Senden von Transaktions-Payloads unterstützen

<br>

## Leitlinien

[Journey Optimizer Guardrads-Produktlink](https://experienceleague.adobe.com/docs/journeys/using/starting-with-journeys/limitations.html?lang=de)

Zusätzliche Journey Optimizer-Limits:

* Die Begrenzung ist heute über die API verfügbar, um sicherzustellen, dass das Zielsystem nicht bis zum Zeitpunkt des Fehlschlagens gesättigt ist. Nachrichten, die die Obergrenze überschreiten, werden also vollständig abgelegt und nie gesendet. Einschränkungen werden nicht unterstützt.
   * Maximale Verbindungen - maximale Anzahl von HTTP/s-Verbindungen, die ein Ziel verarbeiten kann
   * Maximale Anzahl der Aufrufe - maximale Anzahl der Aufrufe, die im Parameter periodInFrau durchgeführt werden sollen
   * periodInMS - Zeit in Millisekunden
* Von der Segmentzugehörigkeit initiierte Journeys können in zwei Modi operieren:
   * Batch-Segmente (alle 24 Stunden aktualisiert)
   * Streaming-Segmente (&lt;5 Minuten Qualifikation)
* Batch-Segmente: Stellen Sie sicher, dass Sie das tägliche Volumen an qualifizierten Nutzern verstehen und dass das Zielsystem den maximalen Durchsatz pro Journey und für sämtliche Journeys bewältigen kann
* Streaming-Segmente: Stellen Sie sicher, dass der erste Strom von Profilqualifikationen neben täglichen Streaming-Volumen pro Journey und für sämtliche Journeys bewältigt werden kann
* offer decisioning wird nicht unterstützt
* Ausgehende Integrationen in Drittanbietersysteme
   * Keine Unterstützung für einzelne statische IPs, da unsere Infrastruktur mehrere Mandanten umfasst (alle Data Center IPs müssen Zulassungsliste werden)
   * Für benutzerdefinierte Aktionen werden nur POST- und PUT-Methoden unterstützt
   * Authentifizierungsunterstützung: token | password | OAuth2
* Es ist nicht möglich, einzelne Komponenten von Adobe Experience Platform oder Journey Optimizer zwischen verschiedenen Sandboxes zu verpacken und zu verschieben. Muss in neuen Umgebungen neu implementiert werden

<br>

Drittanbieter-Messaging-System

* Sie müssen wissen, welche Last das System für Transaktions-API-Aufrufe unterstützen kann.
   * Anzahl der zulässigen Aufrufe pro Sekunde
   * Anzahl der Verbindungen
* Sie müssen wissen, welche Authentifizierung für API-Aufrufe erforderlich ist
   * Authentifizierungstyp:  token | password | OAuth2 wird über Journey Optimizer unterstützt.
   * Auth-Cache-Dauer:  Wie lange ist das Token gültig? 
* Wenn die Batch-Erfassung nur unterstützt wird, muss an eine Cloud-Speicher-Engine wie Amazon Kinesis oder Azure Event Grid 1. gestreamt werden
   * Daten können aus diesen Cloud-Speicher-Engines in Batches zusammengefasst und in die Drittanbieter übertragen werden.
   * Jegliche erforderliche Middleware ist vom Kunden oder Dritten zu erbringen

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
1. Erstellen Sie Segmente zur Journey-Nutzung.

#### Quellen/Ziele

1. [Nehmen Sie Daten mit Streaming-APIs und Quellen-Connectoren in Experience Platform auf.](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2020.1.dataingestion&amp;lang=de)

### Journey Optimizer

1. Konfigurieren Sie Ihre Experience Platform-Datenquelle und legen Sie fest, welche Felder im Rahmen der profileStreaming-Daten, die zum Initiieren einer Kunden-Journey verwendet werden, zwischengespeichert werden sollen. Diese Daten müssen zunächst in Journey Optimizer konfiguriert werden, um eine Orchestrierungs-ID zu erhalten. Die Orchestrierungs-ID wird dann an den Entwickler weitergegeben, der sie bei der Aufnahme nutzen kann
1. Konfigurieren Sie externe Datenquellen
1. Benutzerdefinierte Aktionen für Drittanbieteranwendungen konfigurieren

### Mobile Push-Konfiguration (optional, da Drittanbieter-Token erfassen können)

1. Implementieren von Experience Platform Mobile SDK zur Erfassung von Push-Token und Anmeldedaten, um eine Verbindung zu bekannten Kundenprofilen herzustellen
1. Nutzen Sie Adobe Tags und erstellen Sie eine mobile Eigenschaft mit der folgenden Erweiterung:
   * Adobe Journey Optimizer
   * Adobe Experience Platform Edge Network
   * Identität für Edge Network
   * Mobile Core
1. Stellen Sie sicher, dass Sie über einen dedizierten Datastrom für Mobile-App-Bereitstellungen im Vergleich zu Web-Bereitstellungen verfügen.
1. Weitere Informationen finden Sie unter [Adobe Journey Optimizer Mobile-Handbuch](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-journey-optimizer)

<br>

## Verwandte Dokumentation

* [Dokumentation zur Experience Platform](https://experienceleague.adobe.com/docs/experience-platform.html?lang=de)
* [Dokumentation zu Experience Platform Tags ](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=en)
* [Dokumentation zu Experience Platform Mobile SDK](https://experienceleague.adobe.com/docs/mobile.html?lang=de)
* [Dokumentation zu Journey Optimizer](https://experienceleague.adobe.com/docs/journey-optimizer/using/ajo-home.html?lang=de)
* [Journey Optimizer-Produktbeschreibung](https://helpx.adobe.com/legal/product-descriptions/adobe-journey-optimizer.html)
