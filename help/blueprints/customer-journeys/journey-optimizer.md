---
title: 'Blueprint: Journey Optimizer – Trigger-basiertes Messaging und Adobe Experience Platform'
description: Führen Sie ausgelöste Nachrichten und Erlebnisse mit Adobe Experience Platform als Zentrale für gestreamte Daten, Kundenprofile und Segmentierung aus.
solution: Experience Platform, Journey Optimizer
exl-id: 97831309-f235-4418-bd52-28af815e1878
source-git-commit: 2ead62f94e761cd9453be284a9fde3c5803879eb
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Journey Optimizer

Adobe Journey Optimizer ist ein speziell entwickeltes System, mit dem Marketing-Teams in Echtzeit auf Kundenverhalten reagieren und diese dort ansprechen können, wo sie sich gerade befinden. Daten-Management-Funktionen wurden nach Adobe Experience Platform verschoben, sodass sich Marketing-Teams auf ihre Kernkompetenz konzentrieren können: die Erstellung herausragender Customer Journeys und personalisierter Kommunikation.  In dieser Blueprint werden die technischen Funktionen des Programms vorgestellt und die verschiedenen Komponenten der Architektur von Adobe Journey Optimizer eingehend erläutert.

<br>

## Anwendungsfälle

* Trigger-basierte Nachrichten
* Willkommens- und Registrierungsbestätigungen
* Abgebrochene Warenkörbe und Anmeldeformulare
* Standortbasierte Nachrichten
* In-Stadium-Erlebnisse
* Reise- und Gastfreundschaft vor der Ankunft und Aufenthalt Erlebnisse

<br>

## Architektur

<img src="assets/ajo-architecture.svg" alt="Journey Optimizer-Blueprint zur Referenzarchitektur" style="width:100%; border:1px solid #4a4a4a" />

<br>

## Blueprint-Szenarien

| Szenario | Beschreibung | Funktionen |
| :-- | :--- | :--- |
| [Drittanbieter-Nachrichten](3rd-party-messaging.md) | Veranschaulicht, wie Adobe Journey Optimizer mit Drittanbieter-Messaging-Systemen verwendet werden kann, um personalisierte Nachrichten zu orchestrieren und zu senden | Bereitstellung von 1:1-Nachrichten, sobald Kunden personalisierte Nachrichten erhalten, während sie mit Ihrer Marke oder Ihrem Unternehmen interagieren<br><br>Zu beachten:<br><ul><li>Drittanbietersystem muss Träger-Token für die Authentifizierung unterstützen</li><li>Keine Unterstützung für statische IPs aufgrund der Architektur mit mehreren Mandanten</li><li>Beachten Sie bei API-Aufrufen pro Sekunde die architektonischen Einschränkungen des Drittanbietersystems.  Möglicherweise ist es erforderlich, dass der Kunde zusätzliche Mengen von einem Drittanbieter kauft, um das von Journey Optimizer kommende Supportvolumen zu unterstützen.</li><li>Offer decisioning wird in Nachrichten oder Payloads nicht unterstützt</li></ul> |

<br>

## Integrationsmuster

| Integration | Beschreibung | Funktionen |
| :-- | :--- | :--- |
| [Journey Optimizer mit Adobe Campaign](ajo-and-campaign.md) | Zeigt, wie Sie Adobe Journey Optimizer verwenden können, um 1:1-Erlebnisse mithilfe des Echtzeit-Kundenprofils zu orchestrieren und das native Adobe Campaign-Transaktionsnachrichtensystem zu nutzen, um die Nachricht zu senden | Nutzen Sie das Echtzeit-Kundenprofil und die Leistungsfähigkeit von Journey Optimizer, um im Moment Erlebnisse zu orchestrieren und gleichzeitig die nativen Echtzeit-Messaging-Funktionen von Adobe Campaign für die Kommunikation in der letzten Meile zu nutzen.<br><br>Zu beachten:<br><ul><li>Die Campaign-Anwendung muss sich entweder auf v7 Build >21.1 oder v8 befinden</li><li>Messaging-Durchsatz</li><ul><li>Campaign v7 - bis zu 50 k/h</li><li>Campaign v8 - bis zu 1 MB pro Stunde</li><li>Campaign Standard - bis zu 50 k/h</li></ul><li>Da keine Einschränkungen vorgenommen werden, müssen Anwendungsfälle von einem Unternehmensarchitekten einer technischen Prüfung unterzogen werden</li><li>Keine Unterstützung für die Verwendung von Offer decisioning in von Campaign gesendeten Nachrichten</li></ul> |

<br>

## Voraussetzungen

Adobe Experience Platform

* Schemas und Datensätze müssen im System konfiguriert werden, bevor Sie Journey Optimizer-Datenquellen konfigurieren können
* Fügen Sie für klassenbasierte Experience Event-Schemata die Feldergruppe &quot;Orchestration eventID&quot;hinzu, wenn Sie ein Ereignis auslösen möchten, das kein regelbasiertes Ereignis ist
* Fügen Sie für klassenbasierte Einzelprofile die Feldergruppe &quot;Profiltestdetails&quot;hinzu, um Testprofile zur Verwendung mit Journey Optimizer laden zu können.

E-Mail

* Muss über eine Subdomain verfügen, die für den Nachrichtenversand verwendet werden kann
* Subdomains können entweder vollständig an Adobe delegiert (empfohlen) oder CNAMEs verwendet werden, um auf Adobe-spezifische DNS-Server zu verweisen (benutzerdefiniert).
* Für jede Subdomain ist ein Google-TXT-Eintrag erforderlich, um eine korrekte Zustellbarkeit zu gewährleisten

Mobilgeräte-Push

* Der Kunde muss über einen Mobile-Entwickler verfügen, der die Mobile App erstellen kann
* Adobe Experience Platform Mobile SDK

<br>

## Leitlinien

[Journey Optimizer Guardrads-Produktlink](https://experienceleague.adobe.com/docs/journeys/using/starting-with-journeys/limitations.html?lang=de)

Beachten Sie diese, die nicht im obigen Link aufgeführt sind:

* Batch-Segmente: Stellen Sie sicher, dass Sie das tägliche Volumen an qualifizierten Nutzern verstehen und dass das Zielsystem den maximalen Durchsatz pro Journey und für sämtliche Journeys bewältigen kann
* Streaming-Segmente: Stellen Sie sicher, dass der erste Strom von Profilqualifikationen neben täglichen Streaming-Volumen pro Journey und für sämtliche Journeys bewältigt werden kann
* Nativ unterstützt nur Offer decisioning in Nachrichten (keine benutzerdefinierten Aktionen)
* Unterstützte Nachrichtentypen:
   * E-Mail
   * Push (FCM/APNS)
   * Benutzerdefinierte Aktionen (über die REST-API)
* Ausgehende Integrationen in Drittanbietersysteme
   * Keine Unterstützung für einzelne statische IPs, da unsere Infrastruktur mehrere Mandanten umfasst (alle Data Center IPs müssen Zulassungsliste werden)
   * Für benutzerdefinierte Aktionen werden nur POST- und PUT-Methoden unterstützt
   * Authentifizierung über Benutzer/Pass oder Autorisierungstoken
* Es ist nicht möglich, einzelne Komponenten von Adobe Experience Platform oder Journey Optimizer zwischen verschiedenen Sandboxes zu verpacken und zu verschieben. Muss in neuen Umgebungen neu implementiert werden

### Leitlinien für die Datenaufnahme

<img src="assets/aep-data-ingestion-details-latency.svg" alt="Journey Optimizer-Blueprint zur Referenzarchitektur" style="width:80%; border:1px solid #4a4a4a" />

<br>

### AktivierungsLimits

<img src="assets/ajo-activation-details-latency.svg" alt="Journey Optimizer-Blueprint zur Referenzarchitektur" style="width:80%; border:1px solid #4a4a4a" />

<br>

## Implementierungsschritte

### Adobe Experience Platform

#### Schema/Datensätze

1. [Konfigurieren Sie das individuelle Profil, das Erlebnisereignis und Schemas mit mehreren Einheiten](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2021.1.xdm) in Experience Platform basierend auf den vom Kunden angegebenen Daten.
1. [Erstellen Sie Datensätze](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-ingestion/create-datasets-and-ingest-data.html?lang=de) in Experience Platform für die aufzunehmenden Daten.
1. [Fügen Sie dem Datensatz in Experience Platform Datennutzungskennzeichnungen hinzu](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-governance/classify-data-using-governance-labels.html?lang=de), um ordnungsgemäße Governance zu gewährleisten.
1. [Erstellen Sie Richtlinien](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-governance/create-data-usage-policies.html?lang=de), um die Governance an den Zielen umzusetzen.

#### Profil/Identität

1. [Erstellen Sie sämtliche kundenspezifischen Namespaces](https://experienceleague.adobe.com/docs/platform-learn/tutorials/identities/label-ingest-and-verify-identity-data.html?lang=de).
1. [Fügen Sie Identitäten zu Schemas hinzu](https://experienceleague.adobe.com/docs/platform-learn/tutorials/identities/label-ingest-and-verify-identity-data.html).
1. [Aktivieren Sie die Schemas und Datensätze für Profile](https://experienceleague.adobe.com/docs/platform-learn/tutorials/profiles/bring-data-into-the-real-time-customer-profile.html?lang=de).
1. [Richten Sie Zusammenführungsrichtlinien](https://experienceleague.adobe.com/docs/platform-learn/tutorials/profiles/create-merge-policies.html?lang=de) für unterschiedliche Ansichten des [!UICONTROL Echtzeit-Kundenprofils] ein (optional).
1. Erstellen Sie Segmente zur Journey-Nutzung.

#### Quellen/Ziele

1. [Nehmen Sie Daten mit Streaming-APIs und Quellen-Connectoren in Experience Platform auf.](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2020.1.dataingestion&amp;lang=de)

### Journey Optimizer

1. Konfigurieren Sie Ihre Experience Platform-Datenquelle und legen Sie fest, welche  als Teil der profileStreaming-Daten, die zum Initiieren einer Kunden-Journey verwendet werden, zwischengespeichert werden sollen. Diese Daten müssen zunächst in Journey Optimizer konfiguriert werden, um eine Orchestrierungs-ID zu erhalten. Die Orchestrierungs-ID wird dann an den Entwickler weitergegeben, der sie bei der Aufnahme nutzen kann
1. Konfigurieren Sie externe Datenquellen.
1. Konfigurieren Sie benutzerdefinierte Aktionen.

### Mobile Push-Konfiguration

1. Implementieren von Experience Platform Mobile SDK zur Erfassung von Push-Token und Anmeldedaten, um eine Verbindung zu bekannten Kundenprofilen herzustellen
1. Nutzen Sie Adobe Tags und erstellen Sie eine mobile Eigenschaft mit der folgenden Erweiterung:
1. Adobe Journey Optimizer
1. Adobe Experience Platform Edge Network
1. Identität für Edge Network
1. Mobile Core
1. Stellen Sie sicher, dass Sie über einen dedizierten Datastrom für Mobile-App-Bereitstellungen im Vergleich zu Web-Bereitstellungen verfügen.
1. Weitere Informationen finden Sie unter [Adobe Journey Optimizer Mobile-Handbuch](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-journey-optimizer)


## Verwandte Dokumentation

* [Dokumentation zur Experience Platform](https://experienceleague.adobe.com/docs/experience-platform.html?lang=de)
* [Dokumentation zu Experience Platform Tags ](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=en)
* [Dokumentation zu Experience Platform Mobile SDK](https://experienceleague.adobe.com/docs/mobile.html?lang=de)
* [Dokumentation zu Journey Optimizer](https://experienceleague.adobe.com/docs/journey-optimizer/using/ajo-home.html?lang=de)
* [Journey Optimizer-Produktbeschreibung](https://helpx.adobe.com/legal/product-descriptions/adobe-journey-optimizer.html)
