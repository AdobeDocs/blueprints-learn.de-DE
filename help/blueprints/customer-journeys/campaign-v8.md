---
title: Campaign v8-Blueprint, Campaign und Platform
description: Erfahren Sie mehr über den Entwurf für Campaign v8.
solution: Campaign,Campaign v8
exl-id: 89b3a761-9cb3-4e01-8da0-043e634fa61f
source-git-commit: 16b233c7ea9077566ebf12238f0a87beec1c61ce
workflow-type: tm+mt
source-wordcount: '966'
ht-degree: 41%

---

# Blueprint: Campaign v8

Adobe Campaign v8 ist ein Kampagnen-Tool der nächsten Generation, das für traditionelle Marketing-Kanäle wie E-Mail und Direkt-Mail entwickelt wurde. Es bietet robuste ETL- und Daten-Management-Funktionen, die Sie beim Entwurf und bei der Kuratierung der perfekten Kampagne unterstützen. Die Orchestrierungs-Engine bietet umfassende Multi-Touch-Marketingprogramme mit einem Schwerpunkt auf Batch-basierten Journey.

Außerdem bietet es einen skalierbaren Echtzeit-Messaging-Server, mit dem Marketing-Teams vordefinierte Mitteilungen auf Basis einer vollumfänglichen Payload aus beliebigen IT-Systemen senden können, wenn z. B. Passwörter zurückgesetzt, Bestellungen bestätigt oder Empfangsbelege versendet werden müssen.

## Anwendungsfälle

* Hoch komplexe, Batch-basierte Messaging-Programme.
* Onboarding- und Re-Marketing-Kampagnen.
* Kampagnen über Direkt-Mail-Werbung, Broschüren und Magazine
* Einfache Transaktionsnachrichten (wie Kennwortzurücksetzung, E-Mail-Empfangsbestätigung, Bestellbestätigung usw.).
* Integration von Campaign-Daten in Adobe Experience Platform zur Analyse und Profilerstellung.
* Freigabe von Real-time Customer Data Platform-Audiences für Campaign.

## Architekturdiagramme

Erfahren Sie mehr über die [Campaign v8-Bereitstellungsmodelle](https://experienceleague.adobe.com/docs/campaign/campaign-v8/config/architecture/architecture.html#ac-deployment){target="_blank"}.

### Bereitstellung für Campaign Enterprise (FFDA)

<img src="assets/P4-architecture.png" alt="Referenzarchitektur für Campaign v8-Blueprint (P4)" style="width:100%; border:1px solid #4a4a4a" class="modal-image" />

### Campaign v8 FDA-Bereitstellung

<img src="assets/P1-P3-architecture.png" alt="Referenzarchitektur für Campaign v8-Blueprint (P1-P3)" style="width:100%; border:1px solid #4a4a4a" class="modal-image" />

## Integrationsmuster

| Szenario | Beschreibung | Funktionen |
| :-- | :--- | :--- |
| [[!DNL Real-time Customer Data Platform] mit Adobe [!DNL Campaign]](rtcdp-and-campaign-v8.md) | Veranschaulicht, wie die Adobe Experience Platform und ihr Echtzeit-Kundenprofil sowie das zentralisierte Segmentierungstool mit Adobe [!DNL Campaign] für personalisierte Konversationen verwendet werden können. | <ul><li>Freigeben von Profilen und Audiences von [!DNL Real-Time CDP] an Adobe [!DNL Campaign] durch Nutzung des Cloud-Speicher-Dateiaustauschs und Adobe [!DNL Campaign]-Aufnahme-Workflows </li><li>Einfaches Freigeben von Versand- und Interaktionsdaten aus Kundengesprächen zurück in die [!DNL Real-Time CDP] von Adobe [!DNL Campaign], um sowohl das Echtzeit-Kundenprofil zu verbessern als auch kanalübergreifende Berichte zu Nachrichtenkampagnen bereitzustellen</li></ul> |
| [[!DNL Journey Optimizer] mit Adobe [!DNL Campaign]](ajo-and-campaign.md) | Zeigt, wie Sie Adobe Journey Optimizer verwenden können, um 1:1-Erlebnisse mithilfe des Echtzeit-Kundenprofils zu orchestrieren und das native Adobe [!DNL Campaign] -Transaktionsnachrichtensystem zum Senden der Nachricht zu nutzen | Nutzen Sie das Echtzeit-Kundenprofil und die Leistungsfähigkeit von [!DNL Journey Optimizer], um im Moment Erlebnisse zu orchestrieren und gleichzeitig die nativen Echtzeit-Messaging-Funktionen von Adobe [!DNL Campaign] zu nutzen, um die letzte Meilenkommunikation durchzuführen.<br><br>Zu beachten:<br><ul><li>Kann bis zu 1 Mio. Nachrichten pro Stunde über den Echtzeit-Messaging-Server senden<li>Von [!DNL Journey Optimizer] werden keine Einschränkungen vorgenommen, sodass eine technische Überprüfung durch einen Unternehmensarchitekten vor dem Verkauf gewährleistet ist</li><li>Entscheidungs-Management wird in Payloads an Campaign v8 nicht unterstützt</li></ul> |

## Voraussetzungen

Für diesen Blueprint sind folgende Voraussetzungen erforderlich:

### Anwendungs-Server und Echtzeit-Messaging-Server

* Die Adobe [!DNL Campaign] Client Console ist erforderlich, um die [!DNL Campaign] v8-Software zu verwenden und zu interagieren. Dies ist ein Windows-basierter Client, der Standard-Internet-Protokolle verwendet (SOAP, HTTP usw.). Stellen Sie sicher, dass in Ihrem Unternehmen die erforderlichen Berechtigungen für das Verteilen, Installieren und Ausführen von Software aktiviert sind

* Zulassungsauflistung von IP-Adressen:
   * Identifizieren Sie die IP-Bereiche, die alle Benutzer beim Zugriff auf die Client-Konsole nutzen.
   * Identifizieren Sie, welche Unternehmenssysteme mit dem Echtzeit-Messaging-Server kommunizieren dürfen, und stellen Sie sicher, dass ihnen eine statisch zugewiesene IP-Adresse oder ein Bereich zugewiesen ist, die Sie auf die Zulassungsliste setzen können.
   * Dies kann über das Control Panel von Campaign eingerichtet werden.
* sFTP-Schlüsselverwaltung:
   * Halten Sie öffentliche SSH-Schlüssel bereit, die Sie mit dem Campaign-sFTP verwenden können. Dies kann über das Control Panel von Campaign eingerichtet werden.

### E-Mail

* Sie können eine Subdomain für den Nachrichtenversand verwenden.
* Subdomain kann entweder vollständig an Adobe (empfohlen) delegiert werden oder CNAMEs können verwendet werden, um auf Adobe-spezifische DNS-Server zu verweisen (benutzerdefiniert).
* Für jede Subdomain ist ein Google-TXT-Eintrag erforderlich, um eine gute Zustellbarkeit zu gewährleisten.

### Mobilgeräte-Push

* Sie benötigen einen mobilen Entwickler, um die mobile App bereitzustellen, zu konfigurieren und zu erstellen.
* Adobe bietet lediglich ein SDK zum Erfassen der nötigen Informationen von FCM (Android) und APNS (iOS), um Message-Payloads an die Server zu senden. Die Art und Weise, wie die mobile App codiert, bereitgestellt, verwaltet und debuggt werden muss, liegt in der Verantwortung des Kunden.

### Web-Apps (optional)

* Kann eine zusätzliche Subdomain für gehostete Kampagnen-Abmeldungen und Landingpages delegieren.
* SSL-Zertifikat wird dringend empfohlen.

## Leitlinien

Die Limits werden nachfolgend beschrieben.

### Größe des Anwendungs-Servers

* Der Speicher kann auf bis zu 200 Millionen Profile skaliert werden, mit der Möglichkeit, bis zu 1B-Profile zu skalieren.
* Einrichten und Steuern des Benutzerzugriffs über Adobe [!DNL Admin Console].
* Das Laden von Daten in [!DNL Campaign] wird voraussichtlich über Batch-Dateien durchgeführt:
   * Unterstützung beim Laden von API-Daten ist vor allem für das Verwalten von Profilen oder simplen Objekten innerhalb der Datenbank erforderlich (d. h. Erstellen und Aktualisieren). Sie soll nicht für das Laden großer Datenvolumen oder Batch-artige Vorgänge verwendet werden.
   * Die Verwendung von APIs zum Lesen von Daten für benutzerdefinierte Anwendungszwecke wird nicht unterstützt
   * Über API geladene Daten werden in der Anwendungsdatenbank bereitgestellt und dann jede Stunde in der Cloud-Datenbank repliziert
* Es gelten Beschränkungen für API-Aufrufe. Weitere Informationen finden Sie in der [Adobe Campaign-Produktbeschreibung](https://helpx.adobe.com/de/legal/product-descriptions/adobe-campaign-managed-cloud-services.html){target="_blank"}.

### Größe des Batch-Messaging-Servers

* Kann für die Verarbeitung von bis zu 20 Mio. Nachrichten pro Stunde skaliert werden

### Größe des Echtzeit-Messaging-Servers

* Kann bis zu 1 Mio. Nachrichten pro Stunde senden
* Standardmäßig werden zwei Echtzeit-Messaging-Server bereitgestellt. Möglichkeit, auf bis zu acht Echtzeit-Messaging-Server zu skalieren.

### SMS-Konfiguration

* Campaign bietet die Möglichkeit zur Integration mit einem SMS-Anbieter. Der Provider wird vom Kunden beschafft und in die Kampagne zum Senden von SMS-basierten Nachrichten integriert.
* Die Unterstützung erfolgt über das SMPP-Protokoll.
* Es gibt drei (3) verschiedene Arten von SMS, die Adobe alle unterstützen kann:
   * SMS MT (Mobile Terminated): eine SMS, die von Adobe [!DNL Campaign] über den SMPP-Provider an Mobiltelefone ausgegeben wird.
   * SMS MO (Mobile Originated): eine SMS, die von einem Mobiltelefon über den SMPP-Provider an Adobe [!DNL Campaign] gesendet wird.
   * SMS SR (Status Report) oder DR oder DLR (Delivery Receipt): eine vom Mobiltelefon an Adobe [!DNL Campaign] über den SMPP-Provider gesendete Rücksendungsquittung, die angibt, dass die SMS erfolgreich empfangen wurde. Adobe [!DNL Campaign] kann auch einen SR erhalten, der angibt, dass die Nachricht nicht zugestellt werden konnte, oft mit einer Fehlerbeschreibung.

## Implementierungsschritte

Weitere Informationen für die ersten Schritte finden Sie im Handbuch [Implementierung von Adobe Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/implement/implement.html?lang=de)

## Verwandte Dokumentation

* [Dokumentation zu Campaign v8](https://experienceleague.adobe.com/docs/campaign-v8.html)
* [Produktbeschreibung zu Campaign v8](https://helpx.adobe.com/de/legal/product-descriptions/adobe-campaign-managed-cloud-services.html)
* [Dokumentation zu Experience Platform Tags ](https://experienceleague.adobe.com/docs/launch.html)
* [Dokumentation zu Experience Platform Mobile SDK](https://experienceleague.adobe.com/docs/mobile.html)
