---
title: Campaign v8-Blueprint, Campaign und Platform
description: Adobe Campaign v8 ist ein Kampagnen-Tool der nächsten Generation, das für traditionelle Marketing-Kanäle wie E-Mail und Direkt-Mail entwickelt wurde. Es bietet robuste ETL- und Daten-Management-Funktionen, die Sie beim Entwurf und bei der Kuratierung der perfekten Kampagne unterstützen. Die Orchestrierungs-Engine ermöglicht umfangreiche Multi-Touch-Marketing-Programme mit zentralem Fokus auf Batch-basierten Journeys. Außerdem bietet es einen skalierbaren Echtzeit-Messaging-Server, mit dem Marketing-Teams vordefinierte Mitteilungen auf Basis einer vollumfänglichen Payload aus beliebigen IT-Systemen senden können, wenn z. B. Passwörter zurückgesetzt, Bestellungen bestätigt oder Empfangsbelege versendet werden müssen.
solution: Campaign,Campaign v8
exl-id: 89b3a761-9cb3-4e01-8da0-043e634fa61f
source-git-commit: ac6e27e88854f5a05a7ff7428cd4375b3532f632
workflow-type: tm+mt
source-wordcount: '1074'
ht-degree: 95%

---

# Blueprint: Campaign v8

Adobe Campaign v8 ist ein Kampagnen-Tool der nächsten Generation, das für traditionelle Marketing-Kanäle wie E-Mail und Direkt-Mail entwickelt wurde. Es bietet robuste ETL- und Daten-Management-Funktionen, die Sie beim Entwurf und bei der Kuratierung der perfekten Kampagne unterstützen. Die Orchestrierungs-Engine ermöglicht umfangreiche Multi-Touch-Marketing-Programme mit zentralem Fokus auf Batch-basierten Journeys. Außerdem bietet es einen skalierbaren Echtzeit-Messaging-Server, mit dem Marketing-Teams vordefinierte Mitteilungen auf Basis einer vollumfänglichen Payload aus beliebigen IT-Systemen senden können, wenn z. B. Passwörter zurückgesetzt, Bestellungen bestätigt oder Empfangsbelege versendet werden müssen.

<br>

## Anwendungsfälle

* Hochkomplexe Batch-basierte Messaging-Programme
* Onboarding- und Re-Marketing-Kampagnen
* Kampagnen über Direkt-Mail-Werbung, Broschüren und Magazine
* Einfaches Transaktions-Messaging (Passwort zurücksetzen, Empfang bestätigen, Bestellung bestätigen usw.)
* Integration von Campaign-Daten in Adobe Experience Platform zur Analyse und Profilerstellung
* Freigabe von Real-time Customer Data Platform-Audiences für Campaign.

<br>

## Architekturdiagramme

Erfahren Sie mehr über die Campaign v8-Implementierungsmodelle in [diese Seite](https://experienceleague.adobe.com/docs/campaign/campaign-v8/config/architecture/architecture.html#ac-deployment){target="_blank"}.

### Bereitstellung für Campaign Enterprise (FFDA)

<img src="assets/P4-architecture.png" alt="Referenzarchitektur für Campaign v8-Blueprint (P4)" style="width:100%; border:1px solid #4a4a4a" class="modal-image" />


### Campaign v8-FDA-Implementierung

<img src="assets/P1-P3-architecture.png" alt="Referenzarchitektur für Campaign v8-Blueprint (P1-P3)" style="width:100%; border:1px solid #4a4a4a" class="modal-image" />

<br>

## Integrationsmuster

| Szenario | Beschreibung | Funktionen |
| :-- | :--- | :--- |
| [Real-Time Customer Data Platform mit Adobe Campaign](rtcdp-and-campaign-v8.md) | Zeigt, wie Adobe Experience Platform und ihr Echtzeit-Kundenprofil sowie das zentralisierte Segmentierungs-Tool mit Adobe Campaign zur Bereitstellung personalisierter Konversationen genutzt werden können | <ul><li>Freigabe von Profilen und Zielgruppen von Real-Time CDP für Adobe Campaign per Cloud-Speicher-Dateiaustausch und Aufnahme-Workflows von Adobe Campaign </li><li>Einfaches Teilen von Bereitstellungs- und Interaktionsdaten aus Kundenkonversationen zurück in Real-Time CDP aus Adobe Campaign, um einerseits das Echtzeit-Kundenprofil zu optimieren und gleichzeitig Cross-Channel-Reporting für Messaging-Kampagnen zu ermöglichen</li></ul> |
| [Journey Optimizer mit Adobe Campaign](ajo-and-campaign.md) | Zeigt, wie Sie Adobe Journey Optimizer verwenden können, um 1:1-Erlebnisse mit dem Echtzeit-Kundenprofil zu orchestrieren, und dabei das native Transaktionsnachrichtensystem von Adobe Campaign verwenden, um die Nachrichten zu versenden. | Nutzen Sie das Echtzeit-Kundenprofil und die Möglichkeiten von Journey Optimizer, um Erlebnisse im richtigen Moment zu orchestrieren, und nutzen Sie gleichzeitig die nativen Echtzeit-Messaging-Funktionen von Adobe Campaign, um die Kommunikation auf der letzten Meile durchzuführen.<br><br>Überlegungen:<br><ul><li>Kann bis zu 1 Mio. Nachrichten pro Stunde über den Echtzeit-Messaging-Server senden<li>Keine Drosselung durch Journey Optimizer, um technische Prüfung durch einen Pre-Sales Enterprise Architect sicherzustellen</li><li>Entscheidungs-Management wird in Payloads an Campaign v8 nicht unterstützt</li></ul> |

<br>

## Voraussetzungen


### Anwendungs-Server und Echtzeit-Messaging-Server

* Die Client-Konsole von Adobe Campaign ist für die Interaktion mit und Nutzung von Campaign v8 erforderlich. Dies ist ein Windows-basierter Client, der Standard-Internet-Protokolle verwendet (SOAP, HTTP usw.). Stellen Sie sicher, dass in Ihrem Unternehmen die erforderlichen Berechtigungen für das Verteilen, Installieren und Ausführen von Software aktiviert sind

* IP-Adressen-Zulassungsliste
   * Ermitteln Sie die IP-Bereiche, die alle Anwender während des Zugriffs auf die Client-Konsole nutzen werden
   * Ermitteln Sie, welche Unternehmenssysteme mit dem Echtzeit-Messaging-Server kommunizieren dürfen, und stellen Sie sicher, dass diesen eine statische IP (bzw. ein Bereich) zugewiesen ist, die sich auf Ihrer Zulassungsliste befindet
   * Dies kann über das Control Panel von Campaign eingerichtet werden
* sFTP-Schlüssel-Management
   * Halten Sie öffentliche SSH-Schlüssel bereit, die Sie mit dem Campaign-sFTP verwenden können. Dies kann über das Control Panel von Campaign eingerichtet werden.

### E-Mail

* Halten Sie eine Subdomain bereit, die für den Versand von Nachrichten verwendet werden kann
* Die Subdomain kann entweder komplett an Adobe delegiert werden (empfohlen) oder CNAMEs können zum Verweis an Adobe-spezifische DNS-Server (benutzerdefiniert) verwendet werden
* Für jede Subdomain ist ein Google-TXT-Datensatz erforderlich, um gute Zustellbarkeit sicherzustellen

### Mobilgeräte-Push

* Halten Sie einen Mobile-Entwickler bereit, der die Mobile App bereitstellen, konfigurieren und aufbauen kann
* Adobe bietet lediglich ein SDK zum Erfassen der nötigen Informationen von FCM (Android) und APNS (iOS), um Message-Payloads an die Server zu senden. Das Programmieren, Bereitstellen, Verwalten und Debuggen der Mobil App fällt jedoch in den Verantwortungsbereich des Kunden

### Web-Apps (optional)

* Kann eine weitere Subdomain für Campaign-gehostete Abmeldungen und Landingpages delegieren
* SSL-Zertifikat wird empfohlen

<br>

## Leitlinien

### Größe des Anwendungs-Servers

* Der Speicher kann auf bis zu 200 Mio. Profile skaliert werden, potenzielle Weiterskalierung auf 1 Mrd. Profile
* Benutzerzugriff wird über die Adobe Admin Console eingerichtet und gesteuert
* Das Laden von Daten in Campaign sollte über Batch-Dateien erfolgen
   * Unterstützung beim Laden von API-Daten ist vor allem für das Verwalten von Profilen oder simplen Objekten innerhalb der Datenbank erforderlich (d. h. Erstellen und Aktualisieren). Sie soll nicht für das Laden großer Datenvolumen oder Batch-artige Vorgänge verwendet werden.
   * Die Verwendung von APIs zum Lesen von Daten für benutzerdefinierte Anwendungszwecke wird nicht unterstützt
   * Über API geladene Daten werden in der Anwendungsdatenbank bereitgestellt und dann jede Stunde in der Cloud-Datenbank repliziert
* Es gelten Beschränkungen für API-Aufrufe. Weitere Informationen finden Sie unter [Adobe Campaign-Produktbeschreibung](https://helpx.adobe.com/de/legal/product-descriptions/adobe-campaign-managed-cloud-services.html){target="_blank"}.

### Größe des Batch-Messaging-Servers

* Kann für die Verarbeitung von bis zu 20 Mio. Nachrichten pro Stunde skaliert werden

### Größe des Echtzeit-Messaging-Servers

* Kann bis zu 1 Mio. Nachrichten pro Stunde senden
* Standardmäßig werden zwei Echtzeit-Messaging-Server bereitgestellt. Möglichkeit, auf bis zu acht Echtzeit-Messaging-Server zu skalieren.

### SMS-Konfiguration

* Campaign bietet die Möglichkeit zur Integration mit einem SMS-Anbieter. Dieser Anbieter wird vom Kunden erworben und mit Campaign integriert, um SMS-basiert Nachrichten zu senden
* Die Unterstützung erfolgt über das SMPP-Protokoll
* Es gibt drei (3) verschiedene Arten von SMS, die Adobe alle unterstützen kann:
   * SMS MT (endet auf Mobilgerät): Eine SMS, die von Adobe Campaign über den SMPP-Anbieter an Mobiltelefone gesendet wird.
   * SMS MO (geht von Mobilgerät aus): Eine SMS, die von einem Mobiltelefon über den SMPP-Anbieter an Adobe Campaign gesendet wird.
   * SMS SR (Statusbericht) oder DR oder DLR (Versandbestätigung): Eine Empfangsbestätigung, die vom Mobiltelefon über den SMPP-Anbieter an Adobe Campaign gesendet wird und angibt, dass die SMS erfolgreich übermittelt wurde. Adobe Campaign kann auch SR mit einer Meldung empfangen, dass die Nachricht nicht zugestellt wird. Häufig ist auch eine Beschreibung des Fehlers enthalten.

## Implementierungsschritte

Weitere Informationen für die ersten Schritte finden Sie im Handbuch [Implementierung von Adobe Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/implement/implement.html?lang=de)


## Verwandte Dokumentation

* [Dokumentation zu Campaign v8](https://experienceleague.adobe.com/docs/campaign-v8.html)
* [Produktbeschreibung zu Campaign v8](https://helpx.adobe.com/de/legal/product-descriptions/adobe-campaign-managed-cloud-services.html)
* [Dokumentation zu Experience Platform Tags ](https://experienceleague.adobe.com/docs/launch.html)
* [Dokumentation zu Experience Platform Mobile SDK](https://experienceleague.adobe.com/docs/mobile.html)
