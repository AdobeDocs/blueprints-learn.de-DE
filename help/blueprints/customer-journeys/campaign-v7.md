---
title: 'Blueprint: Campaign v7'
description: Erfahren Sie mehr über die Campaign v7-Blueprint für Batch-basierte Messaging-Programme, Onboarding- und Remarketing-Kampagnen, Briefpost-Werbung und einfache Transaktionsnachrichten.
solution: Campaign,Campaign Classic v7
exl-id: 71c808f5-59e6-4f49-a6ba-581ed508bc04
source-git-commit: 60a7785ea0ec4ee83fd9a1e843f0b84fc4cb1150
workflow-type: tm+mt
source-wordcount: '1103'
ht-degree: 94%

---

# Blueprint: Campaign v7

Adobe Campaign v7 ist ein Kampagnen-Tool, das für traditionelle Marketing-Kanäle wie E-Mail und Direkt-Mail entwickelt wurde. Es bietet robuste ETL- und Daten-Management-Funktionen, die Sie beim Entwurf und bei der Kuratierung der perfekten Kampagne unterstützen. Die Orchestrierungs-Engine bietet umfassende Multitouch-Marketing-Programme mit einem Schwerpunkt auf Batch-basierten Journey.

Außerdem bietet es einen Echtzeit-Messaging-Server, mit dem Marketing-Teams vordefinierte Mitteilungen auf Basis einer vollumfänglichen Payload aus beliebigen IT-Systemen senden können, wenn z. B. Passwörter zurückgesetzt, Bestellungen bestätigt oder Empfangsbelege versendet werden müssen.

## Anwendungsfälle

* Batch-basierte Messaging-Programme
* Onboarding- und Re-Marketing-Kampagnen
* Kampagnen über Direkt-Mail-Werbung, Broschüren und Magazine
* Einfaches Transaktions-Messaging für geringes Volumen (Passwort zurücksetzen, Empfang bestätigen, Bestellung bestätigen usw.)

## Architektur

<img src="assets/campaign-v7-architecture.svg" alt="Referenzarchitektur für die Blueprint „Campaign v7“" style="width:100%; border:1px solid #4a4a4a" class="modal-image" />

## Integrationsmuster

| Szenario | Beschreibung | Funktionen |
| :-- | :--- | :--- |
| [Real-Time CDP mit Adobe Campaign](rtcdp-and-campaign.md) | Zeigt, wie Real-Time CDP und das zentralisierte Segmentierungs-Tool von Adobe Experience Platform mit Adobe Campaign genutzt werden können, um personalisierte Konversationen bereitzustellen | <ul><li>Freigabe von Profilen und Zielgruppen von Real-Time CDP für Adobe Campaign per Cloud-Speicher-Dateiaustausch und Aufnahme-Workflows von Adobe Campaign </li><li>Einfaches Teilen von Bereitstellungs- und Interaktionsdaten aus Kundenkonversationen zurück in Real-Time CDP aus Adobe Campaign, um einerseits das Echtzeit-Kundenprofil zu optimieren und gleichzeitig Cross-Channel-Reporting für Messaging-Kampagnen zu ermöglichen</li></ul> |
| [Journey Optimizer mit Adobe Campaign](ajo-and-campaign.md) | Zeigt, wie Sie Adobe Journey Optimizer verwenden können, um 1:1-Erlebnisse mit dem Echtzeit-Kundenprofil zu orchestrieren, und dabei das native Transaktionsnachrichtensystem von Adobe Campaign verwenden, um die Nachrichten zu versenden. | Nutzen Sie das Echtzeit-Kundenprofil und die Möglichkeiten von Journey Optimizer, um Erlebnisse im richtigen Moment zu orchestrieren, und nutzen Sie gleichzeitig die nativen Echtzeit-Messaging-Funktionen von Adobe Campaign, um die Kommunikation auf der letzten Meile durchzuführen.<br><br>Überlegungen:<br><ul><li>Kann bis zu 50.000 Nachrichten pro Stunde über den Echtzeit-Messaging-Server senden<li>Keine Drosselung durch Journey Optimizer, um technische Prüfung durch einen Pre-Sales Enterprise Architect sicherzustellen</li><li>Entscheidungs-Management wird in Payloads an den Echtzeit-Messaging-Server von Campaign v7 nicht unterstützt</li></ul> |

## Voraussetzungen

Überprüfen Sie die folgenden Voraussetzungen unten.

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

Überprüfen Sie die folgenden Leitplanken.

### Größe des Anwendungs-Servers

* Speicher kann auf bis zu 100 Mio. Profile skaliert werden
* Benutzerzugriff wird über die Adobe Admin Console eingerichtet und gesteuert (empfohlen) oder lokal im Programm selbst
* Das Laden von Daten in Campaign sollte über Batch-Dateien erfolgen
   * Unterstützung beim Laden von API-Daten ist vor allem für das Verwalten von Profilen oder simplen Objekten innerhalb der Datenbank erforderlich (d. h. Erstellen und Aktualisieren). Sie soll nicht für das Laden großer Datenvolumen oder Batch-artige Vorgänge verwendet werden.
   * Die Verwendung von APIs zum Lesen von Daten für benutzerdefinierte Anwendungszwecke wird nicht unterstützt
* API-Aufrufe sind auf 15 pro Sekunde oder 150.000 pro Tag begrenzt

### Größe des Batch-Messaging-Servers

* Kann für die Verarbeitung von bis zu 2,5 Mio. Nachrichten pro Stunde skaliert werden

### Größe des Echtzeit-Messaging-Servers

* Kann bis zu 50.000 Nachrichten pro Stunde senden
* Standardmäßig werden zwei Echtzeit-Messaging-Server bereitgestellt. Möglichkeit, auf bis zu acht Echtzeit-Messaging-Server zu skalieren.

### SMS-Konfiguration

* Campaign bietet die Möglichkeit zur Integration mit einem SMS-Anbieter. Dieser Anbieter wird vom Kunden erworben und mit Campaign integriert, um SMS-basiert Nachrichten zu senden
* Die Unterstützung erfolgt über das SMPP-Protokoll
* Es gibt drei (3) verschiedene Arten von SMS, die Adobe alle unterstützen kann:
   * SMS MT (endet auf Mobilgerät): Eine SMS, die von Adobe Campaign über den SMPP-Anbieter an Mobiltelefone gesendet wird.
   * SMS MO (geht von Mobilgerät aus): Eine SMS, die von einem Mobiltelefon über den SMPP-Anbieter an Adobe Campaign gesendet wird.
   * SMS SR (Statusbericht) oder DR oder DLR (Versandbestätigung): Eine Empfangsbestätigung, die vom Mobiltelefon über den SMPP-Anbieter an Adobe Campaign gesendet wird und angibt, dass die SMS erfolgreich übermittelt wurde. Adobe Campaign kann auch SR mit einer Meldung empfangen, dass die Nachricht nicht zugestellt wird. Häufig ist auch eine Beschreibung des Fehlers enthalten.

### Mobilgeräte-Push-Konfiguration

* Zwei unterstützte Ansätze für die Integration mit Mobilgeräten für Push-Benachrichtigungen:
   * Experience Platform Mobile SDK (empfohlen)
   * Campaign Mobile SDK
* Vorgehensweise für Experience Platform Mobile SDK:
   * Nutzung von Adobe Tags und der Campaign Classic-Erweiterung zum Einrichten der Integration mit dem Experience Platform Mobile SDK
   * Erfahrung im Umgang mit Adobe Tags und Datenerfassung nötig
   * Erfahrung bei der Mobile-Entwicklung mit Push-Benachrichtigungen sowohl für Android als auch iOS erforderlich zur Implementierung des SDK, Integration mit FCM (Android) und APNS (iOS), um Push-Token zu erhalten, Konfiguration der Mobile App zum Erhalt von und Umgang mit Push-Benachrichtigungen
* Campaign Mobile SDK
   * Kontaktieren Sie die Adobe-Kundenunterstützung, um Zugriff zu erhalten
   * Folgen Sie der [Dokumentation zum Campaign SDK](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/sending-push-notifications/integrating-campaign-sdk-into-the-mobile-application.html?lang=de), um mehr über die Installation und Konfiguration des SDK zu erfahren

  >[!IMPORTANT]
  >Wenn Sie das Campaign SDK implementieren und mit anderen Experience Cloud-Programmen arbeiten, muss zur Datenerfassung das Experience Platform Mobile SDK verwendet werden. Dies ist ein anderes SDK, das zusätzlich zum Campaign SDK installiert werden muss

## Implementierungsschritte

Siehe [ Erste Schritte für ](https://experienceleague.adobe.com/docs/campaign-classic/using/getting-started/starting-with-adobe-campaign/about-adobe-campaign-classic.html?lang=de) Implementierung von Adobe Campaign v7.


## Verwandte Dokumentation

* [Dokumentation zu Campaign v7](https://experienceleague.adobe.com/docs/campaign-classic.html?lang=de)
* [Produktbeschreibung zu Campaign v7](https://helpx.adobe.com/de/legal/product-descriptions/adobe-campaign-managed-cloud-services.html)
* [Dokumentation zu Experience Platform Tags ](https://experienceleague.adobe.com/docs/launch.html?lang=de)
* [Dokumentation zu Experience Platform Mobile SDK](https://experienceleague.adobe.com/docs/mobile.html?lang=de)
