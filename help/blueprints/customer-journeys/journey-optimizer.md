---
title: Journey Optimizer - Triggers Messaging und Adobe Experience Platform-Blueprint
description: Führen Sie ausgelöste Nachrichten und Erlebnisse mit Adobe Experience Platform als Zentrale für gestreamte Daten, Kundenprofile und Segmentierung aus.
solution: Experience Platform, Campaign, Journey Orchestration
kt: 7197
exl-id: 97831309-f235-4418-bd52-28af815e1878
source-git-commit: dc13a1fe9a32f70497c5c73485618e6989b7a644
workflow-type: tm+mt
source-wordcount: '700'
ht-degree: 49%

---

# Journey Optimizer

Adobe Journey Optimizer ist ein speziell entwickeltes System, mit dem Marketing-Teams in Echtzeit auf Kundenverhalten reagieren und diese dort treffen können, wo sie sich befinden. Data-Management-Funktionen wurden in die Adobe Experience Platform verschoben, sodass sich Marketing-Teams auf das konzentrieren können, was sie am besten tun: die erstklassige Journey und personalisierte Gespräche schafft.  In diesem Blueprint werden die technischen Funktionen des Programms vorgestellt und die verschiedenen architektonischen Komponenten, aus denen Adobe Journey Optimizer besteht, eingehend erläutert.

## Anwendungsfälle

* Trigger-basierte Nachrichten
* Registrierungsbestätigungen
* Abgebrochene Warenkörbe und Anmeldeformulare
* Standortbasierte Nachrichten

## Architektur

<img src="assets/journey-optimizer.png" alt="Referenzarchitektur für Blueprint „Trigger-basiertes Messaging und Adobe Experience Platform“" style="border:1px solid #4a4a4a" />

## Integrationsmuster

* Adobe Experience Platform -> Journey Optimizer

## Voraussetzungen

1. Der Kunde muss für Experience Cloud mit einer gültigen IMS-Organisation bereitgestellt werden
1. Mobile Push

* Der Kunde muss über einen Entwickler für Mobilgeräte verfügen, um die App erstellen zu können
* Adobe Experience Platform Mobile SDK
* Adobe Launch
   * Mobileigenschaft
      * Erweiterungen:
         * Adobe Journey Optimizer-Erweiterung
         * Adobe Experience Platform Edge Network
         * Identität
         * Mobile Core
         * Profil
   * App-Konfigurationen
   * Datenspeicher
      * Aktiviert für Experience Platform
      * Ereignis-Datensatz - wird zur Erfassung des allgemeinen Verhaltens von Mobilgeräten verwendet
      * Profildatensatz - AJO Push Profile DataSet (kann nicht anders sein)

## Leitlinien

* Im Link erhalten Sie weitere Details zu Einschränkungen
* Batch-Segmente - Sie müssen sicherstellen, dass Sie das tägliche Volumen qualifizierter Benutzer verstehen und sicherstellen, dass das Zielsystem den Burst-Durchsatz pro Journey und über alle Journey hinweg handhaben kann.
* Streaming-Segmente - müssen sicherstellen, dass der anfängliche Berst von Profilqualifikationen zusammen mit dem täglichen Streaming-qualifizierenden Volumen pro Journey und über alle Journey hinweg verarbeitet werden kann
* Aktivität Profilaktualisierung : Das Echtzeit-Kundenprofil kann nativ über eine Journey aktualisiert werden.  Bei der Verarbeitung der Aktualisierung in den Profilspeicher dauert es bis zu 1 Min.
* Geschäftsereignisse - Eine auf einem Lesesegment basierende Journey kann ausgelöst werden, um basierend auf einem externen Aufruf an das JO-System zu starten.
* Nativ unterstützt nur Offer decisioning in Nachrichten. Zukünftige Unterstützung durch native Aktionen
* Unterstützte Kanäle:
   * Email
   * Push (FCM/APNS)
   * REST API-Endpunkte
* Verarbeitet 5.000 Ereignisse pro Sekunde mit horizontaler Skalierung (Portemonnaie ist begrenzt)
* A/B-Tests werden durchgeführt, indem zwei Sendungen verwendet und Ergebnisse mithilfe von QS oder CJA ermittelt werden.
* Litmus-Integration - muss über ein Konto mit Litmus verfügen, um die Integration nutzen zu können

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
1. Erstellen Sie Segmente für die Kampagnennutzung.

#### Quellen/Ziele

1. [Nehmen Sie Daten in Experience Platform mithilfe von Streaming-APIs und Quell-Connectoren](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2020.1.dataingestion&amp;lang=de) auf.1. Konfigurieren Sie das [!DNL Azure]-Blob-Speicherziel für die Verwendung mit Adobe Campaign.

#### Bereitstellung für Mobile App

1. Implementieren Sie das Adobe Campaign-SDK für Adobe Campaign Classic oder das Experience Platform-SDK für Adobe Campaign Standard. Wenn Experience Platform Launch vorhanden ist, wird empfohlen, die Erweiterung für Adobe Campaign Classic oder Adobe Campaign Standard mit dem Experience Platform-SDK zu verwenden.


### Journey Orchestration

1. Streaming-Daten, die zum Initiieren einer Journey verwendet werden, müssen in Journey Optimizer konfiguriert werden, bevor eine Orchestrierungs-ID abgerufen werden kann. Die Orchestrierungs-ID wird dann an den Entwickler weitergegeben, der sie bei der Aufnahme nutzen kann.
1. Konfigurieren Sie externe Datenquellen.
1. Konfigurieren Sie benutzerdefinierte Aktionen.

## Verwandte Dokumentation

* [Dokumentation zu Adobe Experience Platform](https://experienceleague.adobe.com/docs/experience-platform.html?lang=de)
* [Journey Optimizer-Dokumentation](https://experienceleague.adobe.com/docs/journey-orchestration.html?lang=de)
* [Dokumentation zu Experience Platform Launch](https://experienceleague.adobe.com/docs/launch.html?lang=de)
* [Dokumentation zu Experience Platform Mobile SDK](https://experienceleague.adobe.com/docs/mobile.html?lang=de)
