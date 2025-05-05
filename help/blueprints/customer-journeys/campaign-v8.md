---
title: Campaign v8-Blueprint, Campaign und Platform
description: Erfahren Sie mehr über den Blueprint für Campaign v8.
solution: Campaign,Campaign v8
version: Campaign v8
exl-id: 89b3a761-9cb3-4e01-8da0-043e634fa61f
source-git-commit: 1d10727899aaae6b8cd339ce10d2a520c73bdaa2
workflow-type: tm+mt
source-wordcount: '966'
ht-degree: 41%

---

# Blueprint: Campaign v8

Adobe Campaign v8 ist ein Kampagnen-Tool der nächsten Generation, das für traditionelle Marketing-Kanäle wie E-Mail und Direkt-Mail entwickelt wurde. Es bietet robuste ETL- und Daten-Management-Funktionen, die Sie beim Entwurf und bei der Kuratierung der perfekten Kampagne unterstützen. Die Orchestrierungs-Engine bietet umfassende Multitouch-Marketing-Programme mit einem Schwerpunkt auf Batch-basierten Journey.

Außerdem bietet es einen skalierbaren Echtzeit-Messaging-Server, mit dem Marketing-Teams vordefinierte Mitteilungen auf Basis einer vollumfänglichen Payload aus beliebigen IT-Systemen senden können, wenn z. B. Passwörter zurückgesetzt, Bestellungen bestätigt oder Empfangsbelege versendet werden müssen.

## Anwendungsfälle

* Hochkomplexe Batch-basierte Messaging-Programme.
* Onboarding- und Re-Marketing-Kampagnen.
* Kampagnen über Direkt-Mail-Werbung, Broschüren und Magazine
* Einfache Transaktionsnachrichten (z. B. Zurücksetzen des Kennworts, E-Mail-Quittungen, Bestellbestätigungen usw.).
* Integration von Campaign-Daten in Adobe Experience Platform zur Analyse und Profilerstellung.
* Freigabe von Real-time Customer Data Platform-Audiences für Campaign.

## Architekturdiagramme

Weitere Informationen zu [Bereitstellungsmodellen für Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/config/architecture/architecture.html?lang=de#ac-deployment){target="_blank"}.

### Bereitstellung von Campaign Enterprise (FFDA)

<img src="assets/P4-architecture.png" alt="Referenzarchitektur für den Campaign v8-Blueprint (P4)" style="width:100%; border:1px solid #4a4a4a" class="modal-image" />

### Campaign v8 FDA-Bereitstellung

<img src="assets/P1-P3-architecture.png" alt="Referenzarchitektur für den Campaign v8-Blueprint (P1-P3)" style="width:100%; border:1px solid #4a4a4a" class="modal-image" />

## Integrationsmuster

| Szenario | Beschreibung | Funktionen |
| :-- | :--- | :--- |
| [[!DNL Real-time Customer Data Platform] mit Adobe [!DNL Campaign]](rtcdp-and-campaign-v8.md) | Zeigt, wie Adobe Experience Platform und sein Echtzeit-Kundenprofil sowie das zentralisierte Segmentierungs-Tool mit Adobe [!DNL Campaign] verwendet werden können, um personalisierte Konversationen bereitzustellen | <ul><li>Freigabe von Profilen und Audiences aus der [!DNL Real-Time CDP] in die Adobe-[!DNL Campaign] mithilfe von Cloud-Speicher-Dateiaustausch- und Adobe-[!DNL Campaign]-Aufnahme-Workflows </li><li>Geben Sie Versand- und Interaktionsdaten aus Kundengesprächen einfach von Adobe [!DNL Campaign] wieder in die [!DNL Real-Time CDP] frei, um sowohl das Echtzeit-Kundenprofil zu verbessern als auch kanalübergreifende Berichte zu Messaging-Kampagnen bereitzustellen</li></ul> |
| [[!DNL Journey Optimizer] mit Adobe [!DNL Campaign]](ajo-and-campaign.md) | Zeigt, wie Sie mit Adobe Journey Optimizer 1:1-Erlebnisse mithilfe des Echtzeit-Kundenprofils orchestrieren und das native Transaktionsnachrichtensystem von Adobe [!DNL Campaign] nutzen können, um die Nachricht zu senden | Nutzen Sie das Echtzeit-Kundenprofil und die Leistungsfähigkeit von [!DNL Journey Optimizer], um Erlebnisse in Echtzeit zu orchestrieren, während Sie die nativen Echtzeit-Messaging-Funktionen von Adobe [!DNL Campaign] nutzen, um die letzte Meile der <br><br> zu bewältigen<br><ul><li>Kann bis zu 1 Mio. Nachrichten pro Stunde über den Echtzeit-Messaging-Server senden<li>Von [!DNL Journey Optimizer] wird keine Drosselung durchgeführt, um eine technische Überprüfung durch einen Pre-Sales Enterprise Architect sicherzustellen.</li><li>Entscheidungs-Management wird in Payloads an Campaign v8 nicht unterstützt</li></ul> |

## Voraussetzungen

Die folgenden Voraussetzungen sind für diesen Blueprint vorhanden.

### Anwendungs-Server und Echtzeit-Messaging-Server

* Die Adobe [!DNL Campaign] Client-Konsole ist für die Interaktion und Verwendung der Software [!DNL Campaign] v8 erforderlich. Dies ist ein Windows-basierter Client, der Standard-Internet-Protokolle verwendet (SOAP, HTTP usw.). Stellen Sie sicher, dass in Ihrem Unternehmen die erforderlichen Berechtigungen für das Verteilen, Installieren und Ausführen von Software aktiviert sind

* Zulassungsauflistung von IP-Adressen:
   * Identifizieren Sie die IP-Bereiche, die alle Benutzer beim Zugriff auf die Client-Konsole nutzen.
   * Identifizieren Sie, welche Unternehmenssysteme mit dem Echtzeit-Messaging-Server kommunizieren dürfen, und stellen Sie sicher, dass ihnen eine statisch zugewiesene IP-Adresse oder ein Bereich zugewiesen wurde, den Sie auf die Zulassungsliste setzen können.
   * Dies kann über das Control Panel von Campaign eingerichtet werden.
* SFTP-Schlüsselverwaltung:
   * Halten Sie öffentliche SSH-Schlüssel bereit, die Sie mit dem Campaign-sFTP verwenden können. Dies kann über das Control Panel von Campaign eingerichtet werden.

### E-Mail

* Eine Subdomain haben, die für den Nachrichtenversand verwendet werden kann.
* Subdomain kann entweder vollständig an Adobe delegiert werden (empfohlen) oder CNAMEs können verwendet werden, um auf Adobe-spezifische DNS-Server zu verweisen (benutzerdefiniert).
* Für jede Subdomain ist ein Google-TXT-Eintrag erforderlich, um eine gute Zustellbarkeit sicherzustellen.

### Mobilgeräte-Push

* Ein Entwickler für Mobilgeräte muss verfügbar sein, um die Mobile App bereitzustellen, zu konfigurieren und zu erstellen.
* Adobe bietet lediglich ein SDK zum Erfassen der nötigen Informationen von FCM (Android) und APNS (iOS), um Message-Payloads an die Server zu senden. Wie die Mobile App codiert, bereitgestellt, verwaltet und debuggt werden muss, liegt in der Verantwortung des Kunden.

### Web-Apps (optional)

* Kann eine zusätzliche Subdomain für von Campaign gehostete Abmelde- und Landingpages delegieren.
* Das SSL-Zertifikat wird dringend empfohlen.

## Leitlinien

Die Leitplanken werden unten beschrieben.

### Größe des Anwendungs-Servers

* Der Speicher kann auf bis zu 200 Millionen Profile skaliert werden, mit dem Potenzial, bis zu 1 Milliarde Profile zu skalieren.
* Einrichten und Steuern des Benutzerzugriffs über Adobe [!DNL Admin Console].
* Das Laden von Daten in [!DNL Campaign] erfolgt normalerweise über Batch-Dateien:
   * Unterstützung beim Laden von API-Daten ist vor allem für das Verwalten von Profilen oder simplen Objekten innerhalb der Datenbank erforderlich (d. h. Erstellen und Aktualisieren). Sie soll nicht für das Laden großer Datenvolumen oder Batch-artige Vorgänge verwendet werden.
   * Die Verwendung von APIs zum Lesen von Daten für benutzerdefinierte Anwendungszwecke wird nicht unterstützt
   * Über API geladene Daten werden in der Anwendungsdatenbank bereitgestellt und dann jede Stunde in der Cloud-Datenbank repliziert
* Es gelten Beschränkungen für API-Aufrufe. Weitere Informationen finden Sie in der [Adobe Campaign-](https://helpx.adobe.com/de/legal/product-descriptions/adobe-campaign-managed-cloud-services.html){target="_blank"}.

### Größe des Batch-Messaging-Servers

* Kann für die Verarbeitung von bis zu 20 Mio. Nachrichten pro Stunde skaliert werden

### Größe des Echtzeit-Messaging-Servers

* Kann bis zu 1 Mio. Nachrichten pro Stunde senden
* Standardmäßig werden zwei Echtzeit-Messaging-Server bereitgestellt. Möglichkeit, auf bis zu acht Echtzeit-Messaging-Server zu skalieren.

### SMS-Konfiguration

* Campaign bietet die Möglichkeit zur Integration mit einem SMS-Anbieter. Der Anbieter wird vom Kunden beschafft und in Campaign integriert, um SMS-basierte Nachrichten zu versenden.
* Unterstützung erfolgt über das SMPP-Protokoll.
* Es gibt drei (3) verschiedene Arten von SMS, die Adobe alle unterstützen kann:
   * SMS-MT (Mobile Terminated): Eine SMS, die von Adobe [!DNL Campaign] über den SMPP-Provider an Mobiltelefone gesendet wird.
   * SMS-MO (Mobile Originated): eine SMS, die von einem Mobilgerät über den SMPP-Provider an Adobe [!DNL Campaign] gesendet wird.
   * SMS SR (Statusbericht) oder DR oder DLR (Versandbestätigung): Eine Rücksendung, die vom Mobilgerät über den SMPP-Provider an Adobe [!DNL Campaign] gesendet wurde und die angibt, dass die SMS erfolgreich empfangen wurde. Adobe [!DNL Campaign] erhält möglicherweise auch eine Statusmeldung, dass die Nachricht nicht zugestellt werden konnte, häufig mit einer Beschreibung des Fehlers.

## Implementierungsschritte

Weitere Informationen für die ersten Schritte finden Sie im Handbuch [Implementierung von Adobe Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/implement/implement.html?lang=de)

## Verwandte Dokumentation

* [Dokumentation zu Campaign v8](https://experienceleague.adobe.com/docs/campaign-v8.html?lang=de)
* [Produktbeschreibung zu Campaign v8](https://helpx.adobe.com/de/legal/product-descriptions/adobe-campaign-managed-cloud-services.html)
* [Dokumentation zu Experience Platform Tags ](https://experienceleague.adobe.com/docs/launch.html?lang=de)
* [Dokumentation zu Experience Platform Mobile SDK](https://experienceleague.adobe.com/docs/mobile.html?lang=de)
