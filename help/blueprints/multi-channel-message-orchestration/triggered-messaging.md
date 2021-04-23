---
title: Ausgelöste Nachrichten und Adobe Experience Platform-Blueprint
description: Führen Sie ausgelöste Botschaften und Erlebnisse mit Adobe Experience Platform als zentraler Drehscheibe für gestreamte Daten, Kundenprofile und Segmentierung aus.
solution: Experience Platform, Campaign, Journey Orchestration
kt: 7197
exl-id: 97831309-f235-4418-bd52-28af815e1878
translation-type: tm+mt
source-git-commit: 37416aafc997838888edec2658d2621d20839f94
workflow-type: tm+mt
source-wordcount: '621'
ht-degree: 81%

---

# Ausgelöste Nachrichten und Adobe Experience Platform-Blueprint

Führen Sie ausgelöste Botschaften und Erlebnisse mit Adobe Experience Platform als zentraler Drehscheibe für gestreamte Daten, Kundenprofile und Segmentierung aus.

## Anwendungsfälle

* Trigger-basierte Nachrichten
* Registrierungsbestätigungen
* Abgebrochene Warenkörbe und Anmeldeformulare
* Standortbasierte Nachrichten

## Architektur

<img src="assets/triggered.svg" alt="Referenzarchitektur für die Auslösung von Messaging und Adobe Experience Platform-Blaupausen" style="border:1px solid #4a4a4a" />

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

1. Konfigurieren Sie das individuelle Profil, das Erlebnisereignis und Schemas mit mehreren Einheiten in Experience Platform basierend auf vom Kunden angegebenen Daten.
1. Erstellen Sie Adobe Campaign-Schema für Folgendes: wideLog, trackingLog, nicht bereitstellbare Adressen und Voreinstellungen für Profile (optional).
1. Fügen Sie Datennutzungs-Labels für die Governance zum Datensatz hinzu.
1. Erstellen Sie Richtlinien, um die Governance an den Zielen umzusetzen.

#### Profil/Identität

1. Erstellen Sie sämtliche kundenspezifischen Namespaces.
1. Fügen Sie Identitäten zu Schemas hinzu.
1. Aktivieren Sie Schemas und Datensätze für Profile.
1. Richten Sie Zusammenführungsregeln für verschiedene Ansichten von [!UICONTROL Echtzeit-Kundenkonto] ein (optional).
1. Erstellen Sie Segmente für die Verwendung von Adobe Campaignen.

#### Quellen/Ziele

1. Nehmen Sie Daten mit Streaming-APIs und Quellen-Connectoren in Experience Platform auf.
1. Konfigurieren Sie das Ziel für die Blob-Datenspeicherung für die Verwendung mit Adobe Campaign.[!DNL Azure]

#### Bereitstellung für Mobile App

1. Implementieren Sie Adobe Campaign SDK für Adobe Campaign Classic oder Experience Platform SDK für Adobe Campaign Standard. Wenn Experience Platform Launch vorhanden ist, wird empfohlen, die Adobe Campaign Classic- oder Adobe Campaign Standard-Erweiterung mit Experience Platform SDK zu verwenden.


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
* [Adobe Campaign Classic-Dokumentation](https://experienceleague.adobe.com/docs/campaign-classic.html?lang=de)
* [Adobe Campaign Standard-Dokumentation](https://experienceleague.adobe.com/docs/campaign-standard.html?lang=de)
* [Dokumentation zu Experience Platform Launch](https://experienceleague.adobe.com/docs/launch.html?lang=de)
* [Dokumentation zu Experience Platform Mobile SDK](https://experienceleague.adobe.com/docs/mobile.html?lang=de)
