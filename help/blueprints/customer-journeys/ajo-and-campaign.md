---
title: 'Blueprint: Journey Optimizer mit Adobe Campaign'
description: Zeigt, wie Adobe Journey Optimizer mit Adobe Campaign verwendet werden kann, um nativ mithilfe des Echtzeit-Messaging-Servers in Campaign Nachrichten zu versenden
solution: Journey Optimizer, Campaign, Campaign v8, Campaign Classic v7, Campaign Standard
exl-id: 076446a9-dfb9-464c-a04f-6864b8cb7b48
source-git-commit: d19555201107b6aa827e63eb8ecff8642d9f967c
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Journey Optimizer mit Adobe Campaign

Zeigt, wie Adobe Journey Optimizer mit Adobe Campaign verwendet werden kann, um nativ mithilfe des Echtzeit-Messaging-Servers in Campaign Nachrichten zu versenden.

<br>

## Architektur

<img src="assets/ajo-campaign-architecture.svg" alt="Referenzarchitektur für die Blueprint „Journey Optimizer“" style="width:100%; border:1px solid #4a4a4a" />

>[!IMPORTANT]
>Die Verwendung sowohl von Journey Optimizer als auch von Campaign zum unabhängigen Versand von Nachrichten ist möglich, allerdings müssen dabei einige technische Überlegungen angestellt werden. Wenn Sie diesen Ansatz verfolgen möchten, besprechen Sie ihn mit Ihrem Pre-Sales Enterprise Architect, um sicherzustellen, dass Sie die Voraussetzungen für die Implementierung verstehen.

<br>

## Voraussetzungen

### Adobe Experience Platform

* Schemas und Datensätze müssen im System konfiguriert werden, bevor Sie Journey Optimizer-Datenquellen konfigurieren können.
* Fügen Sie für Schemas, die auf der Klasse „Erlebnisereignis“ basieren, die Feldgruppe „Orchestrierungsereignis-ID“ hinzu, wenn ein Ereignis ausgelöst werden soll, das kein regelbasiertes Ereignis ist.
* Fügen Sie für Schemas, die auf der Klasse „Individuelles Profil“ basieren, die Feldgruppe „Profil-Testdetails“ hinzu, um die Testprofile für die Verwendung mit Journey Optimizer laden zu können
* Journey Optimizer und Campaign werden in derselben IMS-Organisation bereitgestellt

### Campaign v7/v8 oder Campaign Standard

* Ausführungsinstanz des Echtzeit-Messaging-Service (d. h. Message Center) muss von Adobe Managed Cloud Services gehostet werden
* Sämtliches Nachrichten-Authoring erfolgt direkt in der Campaign-Instanz

<br>

## Leitlinien

[Produkt-Link zu Journey Optimizer-Leitlinien](https://experienceleague.adobe.com/docs/journeys/using/starting-with-journeys/limitations.html?lang=de)

### Weitere Leitlinien für Journey Optimizer

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
* Unternehmens-Events werden nicht unterstützt
* Ausgehende Integrationen mit Drittanbietersystemen
   * Keine Unterstützung für einzelne statische IPs, da wir eine Mehrmandanten-Infrastruktur verwenden (alle Daten-Center-IPs müssen aufgelistet sein)
   * Nur die POST- und die PUT-Methode werden für benutzerdefinierte Aktionen unterstützt
   * Authentifizierungsunterstützung: Token | Passwort | OAuth2
* Keine Möglichkeit, einzelne Komponenten von Adobe Experience Platform oder Journey Optimizer zu packen und zwischen verschiedenen Sandboxes zu verschieben. Muss in neuen Umgebungen erneut implementiert werden

<br>

### Campaign (v7/v8)

* Ausführungsinstanz von Message Center muss von Adobe Managed Cloud Services gehostet werden
* Muss entweder v7, Build >21.1 oder v8 sein
* Messaging-Durchsatz
   * AC (v7) 50.000 pro Stunde
   * AC (v8) bis zu 1 Mio. pro Stunde basierend auf Paket
* AC (v7) unterstützt nur durch Events ausgelöste Journeys
   * Keine durch Segment oder Segmentzugehörigkeit ausgelösten Journeys
   * Zielgruppen- und Unternehmens-Event-basierte Journeys werden aufgrund des Volumens, das an Ausführungsinstanzen gesendet werden kann, nicht unterstützt
* Weder AC (v7) noch AC (v8) unterstützt Offer Decisioning in Nachrichten
* Keine Drosselung ausgehender API-Aufrufe an Campaign
* Protokolle von Transaktionsnachrichten werden nicht nativ mit AEP synchronisiert. Beratung erforderlich. Es wird empfohlen, Protokolle höchstens alle vier Stunden zu exportieren.

<br>

### Campaign Standard

* Unterstützt einen Durchsatz von 14 tps (50.000 pro Stunde)
* Unterstützt nur durch Events ausgelöste Journeys
   * Keine durch Segment oder Segmentzugehörigkeit ausgelösten Journeys
   * Zielgruppen- und Unternehmens-Event-basierte Journeys werden aufgrund des Volumens, das an Ausführungsinstanzen gesendet werden kann, nicht unterstützt
* Öffnungs- und Klickaktivitäten aus an Campaign Standard gesendeten Transaktionsnachrichten werden auf der Journey-Arbeitsfläche von Journey Optimizer nativ als „Reaktions-Events“ angezeigt
* Protokolle von Transaktionsnachrichten werden nicht nativ mit Experience Platform synchronisiert. Beratung erforderlich. Es wird empfohlen, Protokolle höchstens alle vier Stunden zu exportieren.

<br>

## Implementierungsschritte

### Adobe Experience Platform

#### Schema/Datensätze

1. [Konfigurieren Sie das individuelle Profil, das Erlebnisereignis und Schemas mit mehreren Einheiten](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2021.1.xdm) in Experience Platform basierend auf den vom Kunden angegebenen Daten.
1. Erstellen Sie Schemas auf Basis der Klasse „Erlebnisereignis“ für Adobe Campaign-Tabellen broadLog, trackingLog und nicht zustellbare Adressen (optional).
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

### Journey Optimizer

1. Konfigurieren Sie die Experience Platform-Datenquelle und bestimmen Sie, welche Felder als Teil des Profils zwischengespeichert werden sollen. Streaming-Daten, die zum Auslösen einer Customer Journey verwendet werden, müssen zunächst in Journey Optimizer konfiguriert werden, damit eine Orchestrierungs-ID erstellt wird. Die Orchestrierungs-ID wird dann an den Entwickler weitergegeben, der sie bei der Aufnahme nutzen kann
1. Konfigurieren Sie externe Datenquellen
1. Konfigurieren Sie benutzerdefinierte Aktionen für die Campaign-Instanz

### Campaign v7/v8 oder Campaign Standard

* Messaging-Vorlagen müssen mit geeignetem Personalisierungskontext konfiguriert werden
* Export-Workflows müssen zum Export der Protokolle für Transaktionsnachrichten zurück in Experience Platform konfiguriert werden. Es wird empfohlen, sie höchstens alle vier Stunden auszuführen

### Mobilgeräte-Push-Konfiguration (optional)

1. Implementieren Sie das Experience Platform Mobile SDK zum Sammeln von Push-Tokens und Login-Informationen zum Abgleich mit Kundenprofilen
1. Nutzen Sie Adobe Tags und erstellen Sie eine Mobile-Präsenz mit der folgenden Erweiterung:
   * Adobe Journey Optimizer | Adobe Campaign Classic | Adobe Campaign Standard
   * Adobe Experience Platform Edge Network
   * Identität  für Edge Network
   * Mobile Core
1. Stellen Sie sicher, dass Sie über einen dedizierten Daten-Stream für Mobile-App-Implementierungen verfügen, der sich von dem für Web-Implementierungen unterscheidet
1. Weitere Informationen finden Sie im [Mobile-Handbuch für Adobe Journey Optimizer](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-journey-optimizer)

   >[!IMPORTANT]
   >Mobile-Token müssen sowohl in Journey Optimizer als auch in Campaign erfasst werden, wenn Echtzeit-Kommunikation über Journey Optimizer gesendet werden soll und Push-Benachrichtigungen im Batch über Campaign übermittelt werden sollen. Campaign v8 erfordert die exklusive Verwendung des Campaign SDK für das Erfassen von Push-Tokens.

<br>

## Verwandte Dokumentation

* [Dokumentation zu Experience Platform ](https://experienceleague.adobe.com/docs/experience-platform.html?lang=de)
* [Dokumentation zu Experience Platform Tags ](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=de)
* [Dokumentation zu Experience Platform Mobile SDK](https://experienceleague.adobe.com/docs/mobile.html?lang=de)
* [Dokumentation zu Journey Optimizer](https://experienceleague.adobe.com/docs/journey-optimizer/using/ajo-home.html?lang=de)
* [Produktbeschreibung zu Journey Optimizer](https://helpx.adobe.com/de/legal/product-descriptions/adobe-journey-optimizer.html)
* [Dokumentation zu Campaign v8](https://experienceleague.adobe.com/docs/campaign-v8.html?lang=de)
* [Dokumentation zu Campaign v7](https://experienceleague.adobe.com/docs/campaign-classic.html?lang=de)
* [Dokumentation zu Campaign Standard](https://experienceleague.adobe.com/docs/campaign-standard.html?lang=de)
