---
title: Journey Optimizer mit Adobe Campaign-Blueprint
description: Veranschaulicht die Verwendung von Adobe Journey Optimizer mit Adobe Campaign zum nativen Senden von Nachrichten mithilfe des Echtzeit-Messaging-Servers in Campaign
solution: Experience Platform, Journey Optimizer, Campaign v8, Campaign Classic v7, Campaign Standard
hidefromtoc: true
exl-id: 214126d1-d106-4d1a-9fa3-92c40dc5f187
source-git-commit: 13f750c0ff820ab01ed4fc615aba864bc2dc7b75
workflow-type: tm+mt
source-wordcount: '1150'
ht-degree: 26%

---

# Journey Optimizer mit Adobe Campaign

Veranschaulicht die Verwendung von Adobe Journey Optimizer mit Adobe Campaign zum nativen Senden von Nachrichten mithilfe des Echtzeit-Messaging-Servers in Campaign.

<br>

## Architektur

<img src="assets/ajo-campaign-architecture.svg" alt="Journey Optimizer-Blueprint zur Referenzarchitektur" style="width:100%; border:1px solid #4a4a4a" />

>[!IMPORTANT]
>Die Verwendung von Journey Optimizer und Campaign zum unabhängig voneinander durchgeführten Versand von Nachrichten ist zwar möglich, bietet jedoch einige technische Aspekte, die bedacht werden müssen. Wenn Sie diesen Weg weiterverfolgen möchten, wenden Sie sich an Ihren Unternehmensarchitekten für Pre-Sales, um sicherzustellen, dass Sie über Kenntnisse darüber verfügen, was zur Unterstützung der Implementierung erforderlich ist.

<br>

## Voraussetzungen

### Adobe Experience Platform

* Schemas und Datensätze müssen im System konfiguriert werden, bevor Sie Journey Optimizer-Datenquellen konfigurieren können
* Fügen Sie für klassenbasierte Experience Event-Schemata die Feldergruppe &quot;Orchestration eventID&quot;hinzu, wenn Sie ein Ereignis auslösen möchten, das kein regelbasiertes Ereignis ist
* Fügen Sie für klassenbasierte Einzelprofile die Feldergruppe &quot;Profiltestdetails&quot;hinzu, um Testprofile zur Verwendung mit Journey Optimizer laden zu können.
* Journey Optimizer und Campaign werden in derselben IMS-Organisation bereitgestellt

### Campaign v7/v8 oder Campaign Standard

* Die Ausführungsinstanz des Echtzeit-Messaging-Dienstes (d. h. Message Center) muss von Adobe Managed Cloud Services gehostet werden
* Die Bearbeitung aller Nachrichten erfolgt in der Campaign-Instanz selbst

<br>

## Leitlinien

[Journey Optimizer Guardrads-Produktlink](https://experienceleague.adobe.com/docs/journeys/using/starting-with-journeys/limitations.html?lang=de)

### Zusätzliche Journey Optimizer-Limits

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
* Geschäftsereignisse werden nicht unterstützt
* Ausgehende Integrationen in Drittanbietersysteme
   * Keine Unterstützung für einzelne statische IPs, da unsere Infrastruktur mehrere Mandanten umfasst (alle Data Center IPs müssen Zulassungsliste werden)
   * Für benutzerdefinierte Aktionen werden nur POST- und PUT-Methoden unterstützt
   * Authentifizierungsunterstützung: token | password | OAuth2
* Es ist nicht möglich, einzelne Komponenten von Adobe Experience Platform oder Journey Optimizer zwischen verschiedenen Sandboxes zu verpacken und zu verschieben. Muss in neuen Umgebungen neu implementiert werden

<br>

### Campaign (v7/v8)

* Die Ausführungsinstanz von Message Center muss von Adobe Managed Cloud Services gehostet werden
* Muss entweder auf v7 Build >21.1 oder v8 sein
* Messaging-Durchsatz
   * AC (v7) 50 k/h
   * AC (v8) bis zu 1 M pro Stunde basierend auf dem Paket
* AC (v7) unterstützt nur Journey initiiert
   * Keine Segment- oder Segmentmitgliedschaft initiiert Journey
   * Audience lesen und Business Event-basierte Journey werden aufgrund des Umfangs, der an die Ausführungsinstanzen gesendet werden kann, nicht unterstützt
* Weder AC (v7) noch AC (v8) unterstützen Offer decisioning in Nachrichten
* Keine Einschränkung von ausgehenden API-Aufrufen an Campaign
* Transaktionsnachrichten-Protokolle werden nicht nativ mit AEP synchronisiert. Erfordert Beratungsanstrengungen. Es wird empfohlen, Logs maximal alle 4 Stunden zu exportieren

<br>

### Campaign Standard

* Unterstützt den Durchsatz von 14 tps (50.000 pro Stunde)
* Unterstützt nur Journey, die durch Ereignisse initiiert wurden
   * Keine Segment- oder Segmentmitgliedschaft initiiert Journey
   * Audience lesen und Business Event-basierte Journey werden aufgrund des Umfangs, der an die Ausführungsinstanzen gesendet werden kann, nicht unterstützt
* An Campaign Standard gesendete Transaktionsnachrichten, die Aktivitäten mit Öffnungen und Klicks enthalten, werden nativ als &quot;Wiederaktionsereignisse&quot;auf der Journey Optimizer-Journey-Arbeitsfläche angezeigt
* Transaktionsnachrichten-Protokolle werden nicht nativ mit der Experience Platform synchronisiert. Erfordert Beratungsanstrengungen. Es wird empfohlen, Logs maximal alle 4 Stunden zu exportieren

<br>

## Implementierungsschritte

### Adobe Experience Platform

#### Schema/Datensätze

1. [Konfigurieren Sie das individuelle Profil, das Erlebnisereignis und Schemas mit mehreren Einheiten](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2021.1.xdm) in Experience Platform basierend auf den vom Kunden angegebenen Daten.
1. Erstellen Sie auf Experience Event-Klassen basierende Schemata für Adobe Campaign broadLog, trackingLog und Tabellen mit nicht zustellbaren Adressen (optional).
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
1. Benutzerdefinierte Aktionen für die Campaign-Instanz konfigurieren

### Campaign v7/v8 oder Campaign Standard

* Nachrichtenvorlagen müssen mit einem geeigneten Personalisierungskontext konfiguriert werden
* Export-Workflows müssen konfiguriert werden, um die Transaktionsnachrichten-Logs zurück in die Experience Platform zu exportieren. Es wird empfohlen, maximal alle vier Stunden zu starten.

### Mobile Push-Konfiguration (optional)

1. Implementieren von Experience Platform Mobile SDK zur Erfassung von Push-Token und Anmeldedaten, um eine Verbindung zu bekannten Kundenprofilen herzustellen
1. Nutzen Sie Adobe Tags und erstellen Sie eine mobile Eigenschaft mit der folgenden Erweiterung:
   * Adobe Journey Optimizer | Adobe Campaign Classic | Adobe Campaign Standard
   * Adobe Experience Platform Edge Network
   * Identität für Edge Network
   * Mobile Core
1. Stellen Sie sicher, dass Sie über einen dedizierten Datastrom für Mobile-App-Bereitstellungen im Vergleich zu Web-Bereitstellungen verfügen.
1. Weitere Informationen finden Sie unter [Adobe Journey Optimizer Mobile-Handbuch](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-journey-optimizer)

   >[!IMPORTANT]
   >Mobile Token müssen möglicherweise sowohl in Journey Optimizer als auch in Campaign erfasst werden, wenn Echtzeit-Nachrichten über Journey Optimizer und Batch-Push-Benachrichtigungen über Campaign gesendet werden sollen. Für Campaign v8 ist die exklusive Verwendung des Campaign SDK zur Erfassung von Push-Token erforderlich.

<br>

## Verwandte Dokumentation

* [Dokumentation zur Experience Platform](https://experienceleague.adobe.com/docs/experience-platform.html?lang=de)
* [Dokumentation zu Experience Platform Tags ](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=en)
* [Dokumentation zu Experience Platform Mobile SDK](https://experienceleague.adobe.com/docs/mobile.html?lang=de)
* [Dokumentation zu Journey Optimizer](https://experienceleague.adobe.com/docs/journey-optimizer/using/ajo-home.html?lang=de)
* [Journey Optimizer-Produktbeschreibung](https://helpx.adobe.com/legal/product-descriptions/adobe-journey-optimizer.html)
* [Dokumentation zu Campaign v8](https://experienceleague.adobe.com/docs/campaign-v8.html?lang=en)
* [Dokumentation zu Campaign v7](https://experienceleague.adobe.com/docs/campaign-classic.html?lang=de)
* [Dokumentation zu Campaign Standard](https://experienceleague.adobe.com/docs/campaign-standard.html?lang=de)
