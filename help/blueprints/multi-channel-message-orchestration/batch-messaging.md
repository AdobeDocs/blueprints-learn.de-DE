---
title: Batch Messaging und Adobe Experience Platform Blueprint
description: Ausführen von geplanten und Batch-Messaging-Kampagnen mit Adobe Experience Platform als Zentrale für Kundenprofile und Segmentierung.
solution: Experience Platform, Campaign
kt: 7196
exl-id: 4e55218c-c158-4f78-9f0b-c03528d992fa
translation-type: tm+mt
source-git-commit: 37416aafc997838888edec2658d2621d20839f94
workflow-type: tm+mt
source-wordcount: '564'
ht-degree: 59%

---

# Batch Messaging und Adobe Experience Platform Blueprint

Ausführen von geplanten und Batch-Messaging-Kampagnen mit Adobe Experience Platform als Zentrale für Kundenprofile und Segmentierung.

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

<img src="assets/aepbatch.svg" alt="Referenzarchitektur für Batch Messaging und Adobe Experience Platform Blueprint" style="border:1px solid #4a4a4a" />

## Leitlinien

* Unterstützt nur organisatorische Einsätze von Adobe Campaignen
* Adobe Campaign ist eine Wahrheitsquelle für alle aktiven Profil, d.h. Profil müssen in Adobe Campaign vorhanden sein, und neue Profil sollten nicht auf der Grundlage von Experience Platformen erstellt werden.
* Die Umsetzung von Segmentzugehörigkeit aus Experience Platform ist sowohl für Batch (1 pro Tag) als auch für Streaming (~5 Minuten) latent

**[!UICONTROL Freigabe von ] Segmenten für Kundendaten in Echtzeit für Adobe Campaign:**

* Begrenzung auf 20 Segmente empfohlen
* Die Aktivierung ist auf einmal pro 24 Stunden begrenzt
* Nur Vereinigungsschema-Attribute sind für die Aktivierung verfügbar (keine Unterstützung von Array/Karten/Erlebnisereignisse)
* Begrenzung auf 20 Attribute pro Segment empfohlen
* Eine Datei pro Segment von allen Profilen mit „realisierter“ Segmentzugehörigkeit ODER, wenn Segmentzugehörigkeit als Attribut in der Datei hinzugefügt wird, sowohl „realisierte“ als auch „verlassene“ Profile
* Schrittweise oder vollständige Segment-Exporte werden unterstützt
* Datei-Verschlüsselung wird nicht unterstützt
* Workflows des Adobe Campaign-Exports wird maximal alle 4 Stunden ausgeführt
* Siehe [Leitlinien für Profil- und Datenaufnahme für Experience Platform](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=de)

## Implementierungsschritte

### Adobe Experience Platform

#### Schemas/Datensätze

1. Konfigurieren Sie das individuelle Profil, das Erlebnisereignis und Schemas mit mehreren Einheiten in Experience Platform basierend auf vom Kunden angegebenen Daten.
1. Erstellen Sie Adobe Campaign-Schema für &quot;wideLog&quot;, &quot;trackingLog&quot;, &quot;non-delivery&quot;-Adressen und Profil-Voreinstellungen (optional).
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

#### Adobe Campaign

1. Konfigurieren Sie Schemas für das Profil, Suchdaten und relevante Personalisierungsdaten für die Bereitstellung.

>[!IMPORTANT]
>
>Es ist äußerst wichtig, an dieser Stelle zu verstehen, welches Datenmodell in der Experience Platform für Profil- und Ereignis-Daten liegt, damit Sie wissen, welche Daten in Adobe Campaign benötigt werden.

#### Workflows für den Import

1. Vereinfachte Profil-Daten werden auf Adobe Campaign sFTP geladen und erfasst.
1. Laden und erfassen Sie Orchester- und Messaging-Personalisierungsdaten auf Adobe Campaign sFTP.
1. Nehmen Sie Experience Platform-Segmenten aus dem [!DNL Azure]-Blob über Workflows auf.

#### Workflows für den Export

1. Senden Sie Adobe Campaign-Logs alle vier Stunden über Workflows an die Experience Platform zurück (wideLog, trackingLog, nicht lieferbare Adressen).
1. Senden Sie Profileinstellungen über Consulting-Workflows alle vier Stunden an Experience Platform (optional).


## Verwandte Dokumentation

* [Dokumentation zu Adobe Experience Platform](https://experienceleague.adobe.com/docs/experience-platform.html?lang=de)
* [Dokumentation zu Campaign Classic](https://experienceleague.adobe.com/docs/campaign-classic.html?lang=de)
* [Dokumentation zu Campaign Standard](https://experienceleague.adobe.com/docs/campaign-standard.html?lang=de)
* [Dokumentation zu Experience Platform Launch](https://experienceleague.adobe.com/docs/launch.html?lang=de)
* [Dokumentation zu Experience Platform Mobile SDK](https://experienceleague.adobe.com/docs/mobile.html?lang=de)
