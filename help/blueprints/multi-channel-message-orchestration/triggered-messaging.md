---
title: Ausgelöste Nachrichten und Adobe Experience Platform-Blueprint
description: Ausgelöste Nachrichten und Erlebnisse mit Adobe Experience Platform als zentraler Hub-Streaming-Daten, Profilen und Segmentierung ausführen.
solution: Experience Platform, Campaign, Journey Orchestration
kt: 7197
exl-id: 97831309-f235-4418-bd52-28af815e1878
translation-type: tm+mt
source-git-commit: 2404d871a852df8fed3adb97a79cc15e994db762
workflow-type: tm+mt
source-wordcount: '605'
ht-degree: 1%

---

# Ausgelöste Nachrichten und Adobe Experience Platform-Blueprint

Ausgelöste Nachrichten und Erlebnisse mit Adobe Experience Platform als zentraler Hub-Streaming-Daten, Profilen und Segmentierung ausführen.

## Anwendungsfälle

* Ausgelöste Meldungen
* Registrierungsbestätigungen
* Warenkorb- und Antragsformularabbrüche
* Ortsbedingte Meldungen

## Architektur

<img src="assets/triggered.svg" alt="Referenzarchitektur für das Szenario "Ausgelöste Nachrichten"und "Adobe Experience Platform"" style="border:1px solid #4a4a4a" />

## Integrationsmuster

* Adobe Experience Platform -> Journey Orchestration

## Voraussetzungen

* Adobe Experience Platform
* Journey Orchestration

## Guardraht

### Journey Orchestration

* Siehe Link für [weitere Details zu Einschränkungen](https://experienceleague.adobe.com/docs/journeys/using/starting-with-journeys/limitations.html?lang=en#starting-with-journeys)
* Durch die API-Einrichtung ist eine Deckelung verfügbar, um sicherzustellen, dass das Zielsystem nicht bis zum Fehlerzeitpunkt gesättigt ist. Durch Tippen werden Nachrichten, die die Obergrenze überschreiten, vollständig abgelegt und nie gesendet. Einschränkungen werden weiterhin nicht unterstützt.
   * max. Verbindungen: Maximale Anzahl HTTP/s Verbindungen, die ein Ziel verarbeiten kann
   * maximale Anzahl von Anrufen: Maximale Anzahl der Aufrufe im Parameter &quot;periodInMs&quot;
   * periodInMs: Zeit in Millisekunden
* Die Segmentmitgliedschaft, die initiiert wurde, kann in zwei Modi ausgeführt werden:
   * Stapelsegmente (alle 24 Stunden aktualisiert)
   * Streaming-Segmente (&lt;5-Minuten-Qualifikation)
* Stapelsegmente: Vergewissern Sie sich, dass Sie das tägliche Volumen qualifizierter Benutzer verstehen und sicherstellen, dass das Zielsystem den Burst-Durchsatz pro Journey und über alle Journey hinweg verarbeiten kann
* Streaming-Segmente: Sicherstellen, dass der anfängliche Ausbruch von Profil-Qualifikationen zusammen mit dem täglichen Streaming-qualifizierenden Volumen pro Journey und über alle Journey verarbeitet werden kann
* Endziel muss REST API und JSON Payload unterstützen
* Offer decisioning wird derzeit nicht unterstützt
* Siehe [Profil- und Datenerfassungsgarantien für Experience Platform](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=en)

### Campaign Standard

* Kann nur 14 tps (50 k/h) als Durchsatz unterstützen
* Von der Segmentmitgliedschaft initiierte Journey werden nicht unterstützt
* Ereignis zur Reaktion auf Transaktionsnachrichten, die geöffnet/angeklickt werden, werden in der Journey Orchestration unterstützt.
* Transaktionsprotokolle werden derzeit nicht nativ mit der Experience Platform synchronisiert, was eine manuelle Konfiguration erfordert. Es wird empfohlen, Protokolle maximal alle vier Stunden zu exportieren.


## Implementierungsschritte

### Adobe Experience Platform

#### Schema/Datensätze

1. Konfigurieren Sie individuelle Profil-, Erlebnis-Ereignis- und Multi-Entität-Schema in Experience Platform auf der Grundlage von vom Kunden bereitgestellten Daten.
1. Erstellen Sie Kampagne-Schema für Folgendes: wideLog, trackingLog, nicht bereitstellbare Adressen und Voreinstellungen für Profile (optional).
1. hinzufügen die Datenverwendungsbeschriftungen zum Dataset für Governance.
1. Erstellen Sie Richtlinien, um die Verwaltung von Zielen durchzusetzen.

#### Profil/Identität

1. Erstellen Sie kundenspezifische Namensraum.
1. hinzufügen Identitäten mit Schemas.
1. Aktivieren Sie Schema und Datensätze zum Profil.
1. Richten Sie Zusammenführungsregeln für verschiedene Ansichten von [!UICONTROL Echtzeit-Kundenkonto] ein (optional).
1. Erstellen Sie Segmente zur Kampagne.

#### Quellen/Ziele

1. Daten mithilfe von Streaming-APIs und Quell-Connectors in die Experience Platform aufnehmen
1. Konfigurieren Sie das Ziel für die Blob-Datenspeicherung für die Verwendung mit der Kampagne.[!DNL Azure]

#### Bereitstellung mobiler Apps

1. Implementieren Sie Kampagne SDK für Campaign Classic oder Experience Platform SDK für Campaign Standard. Wenn Experience Platform Launch vorhanden ist, wird empfohlen, die Campaign Classic/Standard-Erweiterung mit Experience Platform SDK zu verwenden.


### Journey Orchestration

1. Streaming-Daten, die zum Initiieren einer Journey verwendet werden, müssen innerhalb der Journey Orchestration konfiguriert werden, bevor eine Orchester-ID abgerufen werden kann. Diese Orchester-ID wird dann an den Entwickler zur Verwendung mit der Erfassung bereitgestellt.
1. Konfigurieren Sie externe Datenquellen.
1. Konfigurieren Sie benutzerdefinierte Aktionen.

### Campaign Standard

1. Konfigurieren Sie Messaging-Vorlagen mit entsprechenden Personalisierungseinstellungen.
1. Konfigurieren Sie Export Workflows Export-Transaktionsnachrichtenprotokolle. Die Empfehlung soll höchstens alle vier Stunden ausgeführt werden.


## Verwandte Dokumentation

* [Adobe Experience Platform-Dokumentation](https://experienceleague.adobe.com/docs/experience-platform.html?lang=en)
* [Dokumentation zur Journey Orchestration](https://experienceleague.adobe.com/docs/journey-orchestration.html?lang=en)
* [Dokumentation zum Campaign Classic](https://experienceleague.adobe.com/docs/campaign-classic.html?lang=en)
* [Dokumentation zum Campaign Standard](https://experienceleague.adobe.com/docs/campaign-standard.html?lang=en)
* [Dokumentation zum Experience Platform Launch](https://experienceleague.adobe.com/docs/launch.html?lang=en)
* [Dokumentation zum Experience Platform Mobile SDK](https://experienceleague.adobe.com/docs/mobile.html?lang=en)
