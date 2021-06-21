---
title: 'Blueprint: Batch-Messaging und Adobe Experience Platform'
description: Führen Sie terminierte und Batch-Nachrichtenkampagnen mit Adobe Experience Platform als zentrale Drehscheibe für Kundenprofile und Segmentierung durch.
solution: Experience Platform, Campaign
kt: 7196
exl-id: 4e55218c-c158-4f78-9f0b-c03528d992fa
source-git-commit: 584007cc71e00729732c67a97546e2c21aed3f87
workflow-type: tm+mt
source-wordcount: '639'
ht-degree: 100%

---

# Blueprint: Batch-Messaging und Adobe Experience Platform

Führen Sie terminierte und Batch-Nachrichtenkampagnen mit Adobe Experience Platform als zentrale Drehscheibe für Kundenprofile und Segmentierung durch.

## Anwendungsfälle

* Geplante E-Mail-Kampagnen
* Onboarding- und Re-Marketing-Kampagnen

## Programme

* Adobe Experience Platform
* Adobe Campaign Classic oder Standard

## Integrationsmuster

* Adobe Experience Platform → Adobe Campaign Classic
* Adobe Experience Platform → Adobe Campaign Standard

## Architektur

<img src="assets/aepbatch.svg" alt="Referenzarchitektur für die Blueprint „Batch-Messaging und Adobe Experience Platform“" style="border:1px solid #4a4a4a" />

## Leitlinien

* Unterstützt nur die Bereitstellung einzelner Organisationseinheiten in Adobe Campaign
* Adobe Campaign ist die zentrale Datenquelle für alle aktiven Profile. Das heißt, die Profile müssen in Adobe Campaign vorhanden sein und neue Profile dürfen nicht basierend auf Experience Platform-Segmenten erstellt werden.
* Die Realisierung von Segmentzugehörigkeit aus Experience Platform ist sowohl für Batch (1 pro Tag) als auch für Streaming (~5 Minuten) latent.

Segmentfreigabe in **[!UICONTROL Real-Time Customer Data Platform] für Adobe Campaign:**

* Begrenzung auf 20 Segmente empfohlen
* Die Aktivierung ist auf einmal pro 24 Stunden begrenzt
* Nur Vereinigungsschema-Attribute sind für die Aktivierung verfügbar (keine Unterstützung von Array/Karten/Erlebnisereignisse)
* Begrenzung auf 20 Attribute pro Segment empfohlen
* Eine Datei pro Segment von allen Profilen mit „realisierter“ Segmentzugehörigkeit ODER, wenn Segmentzugehörigkeit als Attribut in der Datei hinzugefügt wird, sowohl „realisierte“ als auch „verlassene“ Profile
* Schrittweise oder vollständige Segment-Exporte werden unterstützt
* Datei-Verschlüsselung wird nicht unterstützt
* Der Export von Workflows aus Adobe Campaign sollte höchstens alle vier Stunden erfolgen
* Siehe [Leitlinien für Profil- und Datenaufnahme für Experience Platform](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=de)

## Implementierungsschritte

### Adobe Experience Platform

#### Schemas/Datensätze

1. [Konfigurieren Sie das individuelle Profil, das Erlebnisereignis und Schemas mit mehreren Einheiten](https://experienceleague.adobe.com/docs/platform-learn/tutorials/schemas/create-a-schema.html?lang=de) in Experience Platform basierend auf vom Kunden angegebenen Daten.
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

1. [Nehmen Sie Daten mit Streaming-APIs und Quellen-Connectoren in Experience Platform auf.](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2020.1.dataingestion&amp;lang=de)
1. Konfigurieren Sie das [!DNL Azure]-Blob-Speicherziel für die Verwendung mit Adobe Campaign.

#### Bereitstellung für Mobile App

1. Implementieren Sie das Adobe Campaign-SDK für Adobe Campaign Classic oder das Experience Platform-SDK für Adobe Campaign Standard. Wenn Experience Platform Launch vorhanden ist, wird empfohlen, die Erweiterung für Adobe Campaign Classic oder Adobe Campaign Standard mit dem Experience Platform-SDK zu verwenden.

#### Adobe Campaign

1. Konfigurieren Sie Schemas für das Profil, Suchdaten und relevante Personalisierungsdaten für die Bereitstellung.

>[!IMPORTANT]
>
>Hierfür müssen Sie mit dem Datenmodell in Experience Platform für Profil- und Ereignisdaten vertraut sein, damit Sie wissen, welche Daten in Adobe Campaign erforderlich sind.

#### Workflows für den Import

1. Laden und erfassen Sie vereinfachte Profildaten auf dem Adobe Campaign-sFTP.
1. Laden und erfassen Sie Personalisierungsdaten für Orchestrierung und Messaging auf dem Adobe Campaign-sFTP.
1. Nehmen Sie Experience Platform-Segmenten aus dem [!DNL Azure]-Blob über Workflows auf.

#### Workflows für den Export

1. Senden Sie Adobe Campaign-Protokolle alle vier Stunden über Workflows an Experience Platform (broadLog, trackingLog, nicht zustellbare Adressen).
1. Senden Sie Profileinstellungen über Consulting-Workflows alle vier Stunden an Experience Platform (optional).


## Verwandte Dokumentation

* [Dokumentation zu Adobe Experience Platform](https://experienceleague.adobe.com/docs/experience-platform.html?lang=de)
* [Dokumentation zu Campaign Classic](https://experienceleague.adobe.com/docs/campaign-classic.html?lang=de)
* [Dokumentation zu Campaign Standard](https://experienceleague.adobe.com/docs/campaign-standard.html?lang=de)
* [Dokumentation zu Experience Platform Launch](https://experienceleague.adobe.com/docs/launch.html?lang=de)
* [Dokumentation zu Experience Platform Mobile SDK](https://experienceleague.adobe.com/docs/mobile.html?lang=de)
