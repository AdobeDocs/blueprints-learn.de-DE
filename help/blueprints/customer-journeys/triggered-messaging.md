---
title: 'Blueprint: Trigger-basiertes Messaging und Adobe Experience Platform'
description: Führen Sie ausgelöste Nachrichten und Erlebnisse mit Adobe Experience Platform als Zentrale für gestreamte Daten, Kundenprofile und Segmentierung aus.
solution: Experience Platform, Campaign, Journey Orchestration
kt: 7197
exl-id: 97831309-f235-4418-bd52-28af815e1878
source-git-commit: 584007cc71e00729732c67a97546e2c21aed3f87
workflow-type: tm+mt
source-wordcount: '694'
ht-degree: 100%

---

# Blueprint: Trigger-basiertes Messaging und Adobe Experience Platform

Führen Sie ausgelöste Nachrichten und Erlebnisse mit Adobe Experience Platform als Zentrale für gestreamte Daten, Kundenprofile und Segmentierung aus.

## Anwendungsfälle

* Trigger-basierte Nachrichten
* Registrierungsbestätigungen
* Abgebrochene Warenkörbe und Anmeldeformulare
* Standortbasierte Nachrichten

## Architektur

<img src="assets/triggered.svg" alt="Referenzarchitektur für Blueprint „Trigger-basiertes Messaging und Adobe Experience Platform“" style="border:1px solid #4a4a4a" />

## Integrationsmuster

* Adobe Experience Platform -> Journey Orchestration

## Voraussetzungen

* Adobe Experience Platform
* Journey Orchestration

## Leitlinien

### Journey Orchestration

* Im Link erhalten Sie [weitere Details zu Einschränkungen](https://experienceleague.adobe.com/docs/journeys/using/starting-with-journeys/limitations.html?lang=de#starting-with-journeys)
* Die Begrenzung ist über die Einrichtung einer API möglich. So wird sichergestellt, dass das Zielsystem nicht so überlastet wird, dass ein Fehler auftritt. Eine Begrenzung bedeutet, dass Nachrichten, die die Grenze überschreiten, vollständig ignoriert und niemals gesendet werden. Drosselung wird weiterhin nicht unterstützt.
   * Max. Verbindungen: Maximale Zahl der http/s-Verbindungen, die ein Ziel bewältigen kann
   * Max. Aufrufanzahl: Maximale Aufrufzahl, die im Parameter periodInMs erfolgen kann
   * periodInMs: Zeit in Millisekunden
* Von der Segmentzugehörigkeit initiierte Journeys können in zwei Modi operieren:
   * Batch-Segmente (alle 24 Stunden aktualisiert)
   * Streaming-Segmente (Qualifikation &lt;5 Minuten)
* Batch-Segmente: Stellen Sie sicher, dass Sie das tägliche Volumen an qualifizierten Nutzern verstehen und dass das Zielsystem den maximalen Durchsatz pro Journey und für sämtliche Journeys bewältigen kann
* Streaming-Segmente: Stellen Sie sicher, dass der erste Strom von Profilqualifikationen neben täglichen Streaming-Volumen pro Journey und für sämtliche Journeys bewältigt werden kann
* Das Endziel muss die REST-API- und JSON-Payload unterstützen
* Offer Decisioning wird derzeit nicht unterstützt
* Siehe [Leitlinien für Profil- und Datenaufnahme für Experience Platform](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=de)

### Adobe Campaign Standard

* Kann nur einen Durchsatz von 14 tps (50.000 pro Stunde) unterstützen
* Von der Segmentzugehörigkeit initiierte Journeys werden nicht unterstützt
* Reaktionsereignisse auf geöffnete/angeklickte Transaktionsnachrichten werden in Journey Orchestration unterstützt.
* Protokolle zu Transaktionsnachrichten werden derzeit nicht nativ mit Experience Platform synchronisiert, eine manuelle Konfiguration ist hierfür erforderlich. Es wird empfohlen, Protokolle höchstens alle vier Stunden zu exportieren.


## Implementierungsschritte

### Adobe Experience Platform

#### Schema/Datensätze

1. [Konfigurieren Sie das individuelle Profil, das Erlebnisereignis und Schemas mit mehreren Einheiten](https://experienceleague.adobe.com/docs/platform-learn/tutorials/schemas/create-a-schema.html?lang=de) in Experience Platform basierend auf den vom Kunden angegebenen Daten.
1. Erstellen Sie Adobe Campaign-Schemas für broadLog, trackingLog, nicht zustellbare Adressen und Profileinstellungen (optional).
1. [Erstellen Sie Datensätze](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-ingestion/create-datasets-and-ingest-data.html?lang=de) in Experience Platform für die aufzunehmenden Daten.
1. [Fügen Sie dem Datensatz in Experience Platform Datennutzungskennzeichnungen hinzu](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-governance/classify-data-using-governance-labels.html?lang=de), um ordnungsgemäße Governance zu gewährleisten.
1. [Erstellen Sie Richtlinien](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-governance/create-data-usage-policies.html?lang=de), um die Governance an den Zielen umzusetzen.

#### Profil/Identität

1. [Erstellen Sie sämtliche kundenspezifischen Namespaces](https://experienceleague.adobe.com/docs/platform-learn/tutorials/identities/label-ingest-and-verify-identity-data.html?lang=de).
1. [Fügen Sie Identitäten zu Schemas hinzu](https://experienceleague.adobe.com/docs/platform-learn/tutorials/identities/label-ingest-and-verify-identity-data.html).
1. [Aktivieren Sie die Schemas und Datensätze für Profile](https://experienceleague.adobe.com/docs/platform-learn/tutorials/profiles/bring-data-into-the-real-time-customer-profile.html?lang=de).
1. [Richten Sie Zusammenführungsrichtlinien](https://experienceleague.adobe.com/docs/platform-learn/tutorials/profiles/create-merge-policies.html?lang=de) für unterschiedliche Ansichten des [!UICONTROL Echtzeit-Kundenprofils] ein (optional).
1. Erstellen Sie Segmente für die Verwendung mit Adobe Campaign.

#### Quellen/Ziele

1. [Nehmen Sie Daten in Experience Platform mithilfe von Streaming-APIs und Quell-Connectoren](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2020.1.dataingestion&amp;lang=de) auf.1. Konfigurieren Sie das [!DNL Azure]-Blob-Speicherziel für die Verwendung mit Adobe Campaign.

#### Bereitstellung für Mobile App

1. Implementieren Sie das Adobe Campaign-SDK für Adobe Campaign Classic oder das Experience Platform-SDK für Adobe Campaign Standard. Wenn Experience Platform Launch vorhanden ist, wird empfohlen, die Erweiterung für Adobe Campaign Classic oder Adobe Campaign Standard mit dem Experience Platform-SDK zu verwenden.


### Journey Orchestration

1. Streaming-Daten, die zur Initiierung einer Customer Journey genutzt werden, müssen zunächst in Journey Orchestration konfiguriert werden, um eine Orchestrierungs-ID zu erhalten. Die Orchestrierungs-ID wird dann an den Entwickler weitergegeben, der sie bei der Aufnahme nutzen kann.
1. Konfigurieren Sie externe Datenquellen.
1. Konfigurieren Sie benutzerdefinierte Aktionen.

### Adobe Campaign Standard

1. Konfigurieren Sie Messaging-Vorlagen mit entsprechenden Personalisierungseinstellungen.
1. Konfigurieren Sie Export-Workflows für den Export von Protokollen für Transaktionsnachrichten. Es wird empfohlen, sie höchstens alle vier Stunden auszuführen.


## Verwandte Dokumentation

* [Dokumentation zu Adobe Experience Platform](https://experienceleague.adobe.com/docs/experience-platform.html?lang=de)
* [Dokumentation zu Journey Orchestration](https://experienceleague.adobe.com/docs/journey-orchestration.html?lang=de)
* [Dokumentation zu Adobe Campaign Classic](https://experienceleague.adobe.com/docs/campaign-classic.html?lang=de)
* [Dokumentation zu Adobe Campaign Standard](https://experienceleague.adobe.com/docs/campaign-standard.html?lang=de)
* [Dokumentation zu Experience Platform Launch](https://experienceleague.adobe.com/docs/launch.html?lang=de)
* [Dokumentation zu Experience Platform Mobile SDK](https://experienceleague.adobe.com/docs/mobile.html?lang=de)
