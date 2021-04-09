---
title: Batch Messaging und Adobe Experience Platform Blueprint
description: Führen Sie terminierte und Batch-Nachrichten-Kampagnen mit Adobe Experience Platform als zentraler Hub für Profil und Segmentierung aus.
solution: Experience Platform, Campaign
kt: 7196
exl-id: 4e55218c-c158-4f78-9f0b-c03528d992fa
translation-type: tm+mt
source-git-commit: ee1d97af9bf58076fbce24fbc8a3f0d50a4b52a0
workflow-type: tm+mt
source-wordcount: '544'
ht-degree: 0%

---

# Batch Messaging und Adobe Experience Platform Blueprint

Führen Sie terminierte und Batch-Nachrichten-Kampagnen mit Adobe Experience Platform als zentraler Hub für Profil und Segmentierung aus.

## Anwendungsfälle

* Geplante E-Mail-Kampagnen
* Kampagnen des An- und Weiterverkaufs

## Anwendungen

* Adobe Experience Platform
* Adobe Campaign Classic oder Standard

## Integrationsmuster

* Adobe Experience Platform → Adobe Campaign Classic
* Adobe Experience Platform → Adobe Campaign Standard

## Architektur

<img src="assets/aepbatch.svg" alt="Referenzarchitektur für Batch Messaging und Adobe Experience Platform" style="border:1px solid #4a4a4a" />

## Guardraht

* Unterstützt nur die Bereitstellung einzelner organisatorischer Kampagnen
* Kampagne ist eine Wahrheitsquelle für alle aktiven Profil, d.h. Profil müssen in der Kampagne vorhanden sein, und neue Profil sollten nicht auf der Grundlage von Experience Platformen erstellt werden.
* Die Realisierung der Segmentmitgliedschaft aus der Experience Platform ist für Batch (1 pro Tag) und Streaming (~5 Minuten) latent.

**[!UICONTROL Freigabe von ] Segmenten für Kundendaten in Echtzeit für Kampagne:**

* Empfehlung einer Beschränkung auf 20 Segmente
* Die Aktivierung ist auf alle 24 Stunden beschränkt
* Nur für die Aktivierung verfügbare Vereinigung-Schema-Attribute (keine Unterstützung für Array-/Maps-/Erlebnis-Ereignis).
* Empfehlung von höchstens 20 Attributen pro Segment
* Eine Datei pro Segment aller Profil mit &quot;realisierter&quot;Segmentmitgliedschaft ODER wenn die Segmentmitgliedschaft als Attribut in der Datei sowohl &quot;realisiert&quot;als auch &quot;Ausstiegsdatei&quot;hinzugefügt wird
* Inkrementelle oder vollständige Segmentexporte werden unterstützt
* Dateiverschlüsselung wird nicht unterstützt
* Workflows der Kampagne wird maximal alle 4 Stunden ausgeführt
* Siehe [Profil- und Datenerfassungsgarantien für Experience Platform](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html)

## Implementierungsschritte

### Adobe Experience Platform

#### Schema/Datensätze

1. Konfigurieren Sie individuelle Profil-, Erlebnis-Ereignis- und Multi-Entität-Schema in der Experience Platform, basierend auf vom Kunden bereitgestellten Daten.
1. Erstellen Sie Kampagne-Schema für &quot;wideLog&quot;, &quot;trackingLog&quot;, &quot;non-delivery&quot;-Adressen und Profil-Voreinstellungen (optional).
1. hinzufügen die Datenverwendungsbeschriftungen zum Dataset für Governance.
1. Erstellen Sie Richtlinien, die die Verwaltung von Zielen erzwingen.

#### Profil/Identität

1. Erstellen Sie kundenspezifische Namensraum.
1. hinzufügen Identitäten mit Schemas.
1. Aktivieren Sie Schema und Datensätze zum Profil.
1. Richten Sie Zusammenführungsregeln für verschiedene Ansichten des Echtzeit-Kundendiensts ein (optional).
1. Erstellen Sie Segmente zur Kampagne.

#### Quellen/Ziele

1. Daten mithilfe von Streaming-APIs und Quell-Connectors in die Experience Platform aufnehmen
1. Konfigurieren Sie das Ziel für die Blob-Datenspeicherung für die Verwendung mit der Kampagne.[!DNL Azure]

#### Bereitstellung mobiler Apps

1. Implementieren Sie Kampagne SDK für Campaign Classic oder Experience Platform SDK für Campaign Standard. Wenn Experience Platform Launch vorhanden ist, wird empfohlen, die Campaign Classic/Standard-Erweiterung mit Experience Platform SDK zu verwenden.

#### Campaign

1. Konfigurieren von Schemas für Profil, Nachschlagedaten und relevante Personalisierungsdaten für Versand.

>[!IMPORTANT]
>
>Es ist äußerst wichtig, an dieser Stelle zu verstehen, welches Datenmodell in der Experience Platform für Profil- und Ereignis-Daten liegt, damit Sie wissen, welche Daten in der Kampagne benötigt werden.

#### Workflows importieren

1. Vereinfachte Profil-Daten können auf sFTP der Kampagne geladen und erfasst werden.
1. Laden und erfassen Sie Orchester- und Messaging-Personalisierungsdaten auf sFTP der Kampagne.
1. Erfassen Sie Experience Platformen von [!DNL Azure] blob über Workflows.

#### Workflows

1. Senden Sie die Kampagne-Logs alle vier Stunden über Workflows an die Experience Platform zurück (wideLog, trackingLog, nicht lieferbare Adressen).
1. Schicken Sie Profil-Präferenzen alle vier Stunden per Consulting-Workflows zurück in die Experience Platform (optional).


## Verwandte Dokumentation

* [Adobe Experience Platform-Dokumentation](https://experienceleague.adobe.com/docs/experience-platform.html?lang=en)
* [Dokumentation zum Campaign Classic](https://experienceleague.adobe.com/docs/campaign-classic.html?lang=en)
* [Dokumentation zum Campaign Standard](https://experienceleague.adobe.com/docs/campaign-standard.html?lang=en)
* [Dokumentation zum Experience Platform Launch](https://experienceleague.adobe.com/docs/launch.html?lang=en)
* [Dokumentation zum Experience Platform Mobile SDK](https://experienceleague.adobe.com/docs/mobile.html?lang=en)
