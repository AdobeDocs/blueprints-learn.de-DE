---
title: Campaign v8-Blueprint
description: Adobe Campaign v8 ist das Kampagnenwerkzeug der nächsten Generation, das für herkömmliche Marketingkanäle wie E-Mail und Briefpost entwickelt wurde. Es bietet zuverlässige ETL- und Data-Management-Funktionen, mit denen Sie die perfekte Kampagne erstellen und kuratieren können. Die Orchestrierungs-Engine bietet umfassende Multi-Touch-Marketingprogramme mit einem Schwerpunkt auf Batch-basierten Journey.  Er ist außerdem mit einem skalierbaren Echtzeit-Messaging-Server verbunden, der es Marketing-Teams ermöglicht, vordefinierte Nachrichten basierend auf einer allumfassenden Payload von jedem IT-System für Dinge wie Kennwortzurücksetzung, Bestellbestätigung, E-Receiver und vieles mehr zu senden.
solution: Campaign v8
source-git-commit: 1c46cbdfc395de4fc9139966cf869ba1feeceaaa
workflow-type: tm+mt
source-wordcount: '1084'
ht-degree: 3%

---

# Campaign v8-Blueprint

Adobe Campaign v8 ist das Kampagnenwerkzeug der nächsten Generation, das für herkömmliche Marketingkanäle wie E-Mail und Briefpost entwickelt wurde. Es bietet zuverlässige ETL- und Data-Management-Funktionen, mit denen Sie die perfekte Kampagne erstellen und kuratieren können. Die Orchestrierungs-Engine bietet umfassende Multi-Touch-Marketingprogramme mit einem Schwerpunkt auf Batch-basierten Journey.  Er ist außerdem mit einem skalierbaren Echtzeit-Messaging-Server verbunden, der es Marketing-Teams ermöglicht, vordefinierte Nachrichten basierend auf einer allumfassenden Payload von jedem IT-System für Dinge wie Kennwortzurücksetzung, Bestellbestätigung, E-Receiver und vieles mehr zu senden.

<br>

## Anwendungsfälle

* Hoch komplexe, Batch-basierte Messaging-Programme
* Onboarding- und Re-Marketing-Kampagnen
* Briefpost-Werbe-, Broschüren- und Zeitschriftenkampagnen
* Einfache Transaktionsnachrichten (d. h. Kennwortrücksetzung, E-Mail-Empfangsbestätigung, Bestellbestätigung usw.)

<br>

## Architektur

<img src="assets/campaign-v8-architecture.svg" alt="Referenzarchitektur für Campaign v8-Blueprint" style="width:100%; border:1px solid #4a4a4a" />

<br>

## Integrationsmuster

| Szenario | Beschreibung | Funktionen |
| :-- | :--- | :--- |
| [Journey Optimizer mit Adobe Campaign](ajo-and-campaign.md) | Zeigt, wie Sie Adobe Journey Optimizer verwenden können, um 1:1-Erlebnisse mithilfe des Echtzeit-Kundenprofils zu orchestrieren und das native Adobe Campaign-Transaktionsnachrichtensystem zu nutzen, um die Nachricht zu senden | Nutzen Sie das Echtzeit-Kundenprofil und die Leistungsfähigkeit von Journey Optimizer, um im Moment Erlebnisse zu orchestrieren und gleichzeitig die nativen Echtzeit-Messaging-Funktionen von Adobe Campaign für die Kommunikation in der letzten Meile zu nutzen.<br><br>Zu beachten:<br><ul><li>Kann bis zu 1 Mio. Nachrichten pro Stunde über den Echtzeit-Nachrichtenserver senden<li>Journey Optimizer führt keine Drosselung durch, um die technische Prüfung durch einen Unternehmensarchitekten vor dem Verkauf sicherzustellen</li><li>offer decisioning wird in Payloads zu Campaign v8 nicht unterstützt</li></ul> |

<br>

## Voraussetzungen


### Anwendungsserver und Echtzeit-Messaging-Server

* Die Adobe Campaign Client Console ist für die Interaktion und Verwendung der Campaign v8-Software erforderlich. Es handelt sich um einen Windows-basierten Client, der Standard-Internetprotokolle (SOAP, HTTP usw.) verwendet. Stellen Sie sicher, dass Sie in Ihrer Organisation die erforderlichen Berechtigungen zum Verteilen, Installieren und Ausführen von Software aktiviert haben.

* Zulassungsauflistung von IP-Adressen
   * Identifizieren Sie die IP-Bereiche, die alle Benutzer beim Zugriff auf die Client-Konsole nutzen
   * Identifizieren, welche Unternehmenssysteme mit dem Echtzeit-Messaging-Server kommunizieren dürfen, und stellen Sie sicher, dass ihnen eine statisch zugewiesene IP-Adresse oder ein statischer Bereich zugewiesen ist, den Sie zur Zulassungsliste nutzen können.
   * Dies kann über das Campaign Control Panel eingerichtet und gesteuert werden.
* sFTP-Schlüsselverwaltung
   * Sie können über öffentliche SSH-Schlüssel verfügen, die mit dem sFTP-Konto von Campaign verwendet werden können. Dies kann über das Campaign Control Panel eingerichtet und gesteuert werden.

### E-Mail

* Eine Subdomain für den Nachrichtenversand bereitstellen
* Subdomains können entweder vollständig an Adobe delegiert (empfohlen) oder CNAMEs verwendet werden, um auf Adobe-spezifische DNS-Server zu verweisen (benutzerdefiniert).
* Für jede Subdomain ist ein Google-TXT-Eintrag erforderlich, um eine korrekte Zustellbarkeit zu gewährleisten

### Mobilgeräte-Push

* Sie benötigen einen mobilen Entwickler, der für die Bereitstellung, Konfiguration und Erstellung der App verfügbar ist.
* Adobe stellt nur ein SDK bereit, um die erforderlichen Informationen von FCM (Android) und APNS (iOS) zu erfassen und Nachrichten-Payloads an ihre Server zu senden. Die Art und Weise, wie die mobile App codiert, bereitgestellt, verwaltet und debuggt werden muss, liegt in der Verantwortung des Kunden.

### Webapps (optional)

* Kann eine zusätzliche Subdomain für gehostete Kampagnen-Abmeldungen und Landingpages delegieren
* SSL-Zertifikat wird dringend empfohlen

<br>

## Leitlinien

### Größe des Anwendungsservers

* Der Speicher kann auf bis zu 200 Millionen Profile skaliert werden, mit der Möglichkeit, bis zu 1 B Profile zu skalieren
* Benutzerzugriff über Adobe Admin Console einrichten und steuern
* Das Laden von Daten in Campaign erfolgt voraussichtlich über Batch-Dateien
   * Die Unterstützung zum Laden von API-Daten dient hauptsächlich der Verwaltung von Profilen oder einfachen Objekten in der Datenbank (d. h. Erstellen und Aktualisieren). Sie ist nicht für das Laden großer Datenmengen oder Batch-ähnlicher Vorgänge vorgesehen.
   * Die Verwendung von APIs zum Lesen von Daten für benutzerdefinierte Anwendungszwecke wird nicht unterstützt
   * Die über die API geladenen Daten werden in der Anwendungsdatenbank gespeichert und dann stündlich in die Cloud-Datenbank repliziert
* API-Aufrufe sind auf 15 pro Sekunde oder 150.000 pro Tag im Maßstab beschränkt

### Größe des Batch Messaging-Servers

* Kann skaliert werden, um bis zu 20 M Nachrichten pro Stunde zu verarbeiten

### Skalierung von Echtzeit-Messaging-Servern

* Kann bis zu 1 Mio. Nachrichten pro Stunde senden
* Standardmäßig wird nur ein (1) Echtzeit-Messaging-Server bereitgestellt. Dadurch soll sichergestellt werden, dass jede Kommunikation mit dem Server über ein Sitzungstoken erfolgt, das in 24 Stunden abläuft.
* Optional können Sie bis zu acht (8) Echtzeit-Messaging-Server bereitstellen, aber die Authentifizierung unterstützt dann nur Benutzer/Pass
* Es wird empfohlen, immer einen Echtzeit-Messaging-Server zu verwenden, um nach Möglichkeit die Vorteile einer auf Sitzungstoken basierenden Methode zu nutzen

### SMS-Konfiguration

* Campaign ermöglicht die Integration mit einem SMS-Provider. Der Provider wird vom Kunden beschafft und in die Kampagne für den Versand von SMS-basierten Nachrichten integriert
* Die Unterstützung erfolgt über das SMPP-Protokoll.
* Es gibt drei (3) verschiedene Arten von SMS, die von Adobe unterstützt werden können:
   * SMS MT (Mobile Terminated): SMS, die von Adobe Campaign über den SMPP-Provider an Mobiltelefone gesendet werden.
   * SMS MO (Mobile Originated): eine SMS, die von einem Mobilgerät über den SMPP-Provider an Adobe Campaign gesendet wird.
   * SMS SR (Status Report) oder DR oder DLR (Delivery Receipt): eine vom Mobiltelefon an Adobe Campaign über den SMPP-Provider gesendete Rücksendungsquittung, die angibt, dass die SMS erfolgreich empfangen wurde. Adobe Campaign erhält möglicherweise auch einen SR, der angibt, dass die Nachricht nicht zugestellt werden konnte, oft mit einer Fehlerbeschreibung.

### Mobile Push-Konfiguration

* Nur das Campaign SDK wird für Campaign v8 unterstützt. Wenden Sie sich an die Kundenunterstützung der Adobe, um Zugriff zu erhalten.
* Bitte folgen Sie dem [Dokumentation zum Campaign SDK](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/sending-push-notifications/integrating-campaign-sdk-into-the-mobile-application.html?lang=en) Informationen zum Installieren und Konfigurieren des SDK

   >[!IMPORTANT]
   >Für andere Experience Cloud-Anwendungen ist die Verwendung des Experience Platform Mobile SDK für die Datenerfassung erforderlich. Dies ist ein anderes SDK und muss neben dem Campaign SDK installiert werden.

<br>

## Implementierungsschritte

Siehe Erste Schritte für [Implementieren von Adobe Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/implement/implement.html?lang=en)


## Verwandte Dokumentation

* [Dokumentation zu Campaign v8](https://experienceleague.adobe.com/docs/campaign-v8.html?lang=en)
* [Produktbeschreibung von Campaign v8](https://helpx.adobe.com/legal/product-descriptions/adobe-campaign-managed-cloud-services.html)
* [Dokumentation zu Experience Platform Tags ](https://experienceleague.adobe.com/docs/launch.html?lang=de)
* [Dokumentation zu Experience Platform Mobile SDK](https://experienceleague.adobe.com/docs/mobile.html?lang=de)
