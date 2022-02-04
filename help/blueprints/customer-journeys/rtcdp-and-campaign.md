---
title: Kampagne mit Real-Time CDP-Blueprint
description: zeigt, wie die Adobe Experience Platform und ihr Echtzeit-Kundenprofil sowie das zentralisierte Segmentierungs-Tool mit Adobe Campaign für personalisierte Konversationen genutzt werden können.
solution: Experience Platform, Campaign v8, Campaign Classic v7, Campaign Standard
hidefromtoc: true
source-git-commit: a86df4a1b2de38bcb244a6afe1cea87adc7e26fa
workflow-type: tm+mt
source-wordcount: '762'
ht-degree: 56%

---

# Kampagne mit Real-Time CDP-Blueprint

zeigt, wie die Adobe Experience Platform und ihr Echtzeit-Kundenprofil sowie das zentralisierte Segmentierungs-Tool mit Adobe Campaign für personalisierte Konversationen genutzt werden können.

<br>

## Programme

* Adobe Experience Platform Real-Time CDP
* Adobe Campaign v7 oder Campaign Standard

<br>

## Architektur

<img src="assets/rtcdp-campaign-architecture.svg" alt="Referenzarchitektur für die Blueprint „Batch-Messaging und Adobe Experience Platform“" style="width:100%; border:1px solid #4a4a4a" />

<br>

## Voraussetzungen

* Es wird empfohlen, Experience Platform und Campaign in derselben IMS-Organisation bereitzustellen und Adobe Admin Console für den Benutzerzugriff zu verwenden. Dadurch wird auch sichergestellt, dass Kunden den Lösungsschalter über die Marketing-Benutzeroberfläche verwenden können.

<br>

## Leitlinien

### Adobe Campaign

* Unterstützt nur Bereitstellungen einzelner Organisationseinheiten in Adobe Campaign
* Adobe Campaign ist die zentrale Datenquelle für alle aktiven Profile. Das heißt, die Profile müssen in Adobe Campaign vorhanden sein und neue Profile dürfen nicht basierend auf Experience Platform-Segmenten erstellt werden.
* Der Export von Workflows aus Campaign sollte höchstens alle vier Stunden erfolgen
* XDM-Schema und -Datensätze für Adobe Campaign broadLog, trackingLogs und nicht zustellbare Adressen sind nicht vorkonfiguriert und müssen entwickelt und erstellt werden

### Segmentfreigabe in der Experience Platform CDP

* Empfehlung von 20 Segmentgrenzwerten
* Die Aktivierung ist auf alle 24 Stunden beschränkt.
* Nur Vereinigungsschemaattribute, die zur Aktivierung verfügbar sind (keine Unterstützung für Array-/Maps-/Erlebnisereignisse)
* Empfehlung zu höchstens 20 Attributen pro Segment
* Eine Datei pro Segment von allen Profilen mit „realisierter“ Segmentzugehörigkeit ODER, wenn Segmentzugehörigkeit als Attribut in der Datei hinzugefügt wird, sowohl „realisierte“ als auch „verlassene“ Profile
* Inkrementelle und vollständige Segmentexporte werden unterstützt
* Datei-Verschlüsselung wird nicht unterstützt

<br>

## Implementierungsschritte

### Adobe Experience Platform

#### Schemas/Datensätze

1. [Konfigurieren Sie das individuelle Profil, das Erlebnisereignis und Schemas mit mehreren Einheiten](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2021.1.xdm) in Experience Platform basierend auf vom Kunden angegebenen Daten.
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


### Mobile Push-Konfiguration

* Zwei unterstützte Ansätze zur Integration mit Mobilgeräten für Push-Benachrichtigungen:
   * Experience Platform Mobile SDK
   * Campaign Mobile SDK
* Experience Platform Mobile SDK-Route:
   * Verwenden Sie Adobe Tags und die Campaign Classic-Erweiterung, um Ihre Integration mit dem Experience Platform Mobile SDK einzurichten.
   * Benötigen Sie Kenntnisse über Adobe Tags und Datenerfassung
   * Sie benötigen Erfahrung bei der Entwicklung von Mobilgeräten mit Push-Benachrichtigungen in Android und iOS, um das SDK bereitzustellen, die Integration mit FCM (Android) und APNS (iOS) durchzuführen, um Push-Token abzurufen, Ihre App für den Empfang von Push-Benachrichtigungen zu konfigurieren und Push-Interaktionen zu verarbeiten.
* Campaign Mobile SDK
   * Bitte folgen Sie dem [Dokumentation zum Campaign SDK](Campaign Mobile SDK Bitte folgen Sie der hier beschriebenen Implementierungsdokumentation)

   >[!IMPORTANT]
   >Wenn Sie das Campaign SDK bereitstellen und mit anderen Experience Cloud-Applikationen arbeiten, ist die Verwendung des Experience Platform Mobile SDK für die Datenerfassung erforderlich. Dadurch werden doppelte clientseitige Aufrufe auf dem Gerät erstellt.

## Verwandte Dokumentation

* [Dokumentation zu Adobe Experience Platform](https://experienceleague.adobe.com/docs/experience-platform.html?lang=de)
* [Dokumentation zu Campaign Classic](https://experienceleague.adobe.com/docs/campaign-classic.html?lang=de)
* [Dokumentation zu Campaign Standard](https://experienceleague.adobe.com/docs/campaign-standard.html?lang=de)
* [Dokumentation zu Experience Platform Launch](https://experienceleague.adobe.com/docs/launch.html?lang=de)
* [Dokumentation zu Experience Platform Mobile SDK](https://experienceleague.adobe.com/docs/mobile.html?lang=de)
