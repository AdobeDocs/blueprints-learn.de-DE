---
title: Echtzeit-Edge-Profilzugriff für Web- und Mobile-Personalization
description: '[!UICONTROL Echtzeit-Kundenprofil] Zugriff am Edge, um Kontext für die Echtzeit-Personalisierung im Web und auf Mobilgeräten bereitzustellen.'
solution: Real-Time Customer Data Platform, Data Collection
kt: 719
source-git-commit: 2fad3a8a9210d703130f251b0bd7cc4c0b7cbd32
workflow-type: tm+mt
source-wordcount: '1544'
ht-degree: 6%

---

# Echtzeit-Edge-Profilzugriff für Web- und Mobile-Personalization

Der Blueprint „Echtzeit-Edge-Profilzugriff für Web und Mobile Personalization&quot; zeigt, wie Web- und mobile Anwendungen [!UICONTROL &#x200B; Echtzeit-Kundenprofil von Adobe Experience Platform &#x200B;] können, um Personalisierung mit hohem Durchsatz und geringer Latenz zu ermöglichen.

Anwendungen können am Edge mit Millisekunden-Latenz auf Echtzeit-Profilattribute und Zielgruppen zugreifen. Attribute, Zielgruppenzugehörigkeiten und modellgesteuerte Funktionen, die im Profil als Attribute gespeichert sind, können in Echtzeit für die Personalisierung der gleichen Seite und der nächsten Seite über Web- und mobile Kanäle aufgerufen werden.

Mit dieser Funktion können Sie auf der Grundlage des Echtzeit-Kundenprofils hochgradig personalisierte Erlebnisse auf Ihren Websites und mobilen Anwendungen bereitstellen, einschließlich Zielgruppen aus Echtzeit-Verhaltensweisen, in das Echtzeit-Kundenprofil aufgenommene Attribute und berechnete Einblicke.

>[!NOTE]
>
>Der Zugriff auf Edge-Profile wurde speziell für Anwendungsfälle mit hohem Durchsatz und geringer Latenz entwickelt, wie z. B. Personalisierung über das Internet bzw. mobile eingehende Kontakte und Offer Decisioning in Echtzeit. Für Szenarien mit niedrigerem Durchsatz, wie z. B. Support durch Agenten oder Vertriebsinteraktionen, ist die Hub-Profil-Lookup-API geeigneter. Siehe [Blueprint „Echtzeit-Profilzugriff für Support- und Vertriebsszenarien](customer-activity.md) für den Hub-basierten Profilzugriff.

## Programme

* Real-time Customer Data Platform
* Datenerfassung in Adobe Experience Platform (Web SDK / Mobile SDK)
* Edge Network Server-API

## Anwendungsfälle

* Echtzeit-Personalisierung auf Web- und mobilen Kanälen für bekannte Kundenerlebnisse
* Personalisierung der gleichen und der nächsten Seite basierend auf Echtzeit-Profilattributen und Zielgruppen
* Personalisierung von Inhalten und Angeboten basierend auf Kundenprofilen, einschließlich Echtzeit-Verhaltensdaten, Attributen und berechneten Einblicken
* Integration mit Personalisierungs-Engines, Content-Management-Systemen und externen Anwendungen für Echtzeit-Entscheidungen
* Test- und Inhaltsoptimierung mit Echtzeit-Profilkontext

## Voraussetzungen

Dieser Blueprint erfordert die Verwendung einer der folgenden Datenerfassungsmethoden, wenn das Profil mit Streaming-Daten in Echtzeit aktualisiert werden soll. Es ist möglich, auf das Edge-Profil in Echtzeit zuzugreifen, ohne Daten direkt an das Edge-Profil erfassen zu müssen. Daten können auch auf dem Hub erfasst und auf das Edge-Profil projiziert werden. Beachten Sie, dass für Daten, die auf dem Hub erfasst und dann auf die Edge projiziert werden, eine zusätzliche Latenz entsteht.

* Verwenden Sie die [Adobe Experience Platform Web SDK](https://experienceleague.adobe.com/docs/experience-platform/web-sdk/home.html), wenn Sie Daten von Ihrer Website erfassen möchten.
* Verwenden Sie die [Adobe Experience Platform Mobile](https://developer.adobe.com/client-sdks/home/)SDK, wenn Sie Daten von Ihrer Mobile App erfassen möchten.
* Verwenden Sie die [Edge Network](https://experienceleague.adobe.com/docs/experience-platform/edge-network-server-api/overview.html?lang=de)Server-API, wenn Sie nicht die Web-SDK oder mobile SDK verwenden oder eine direktere Server-zu-Server-Verbindung implementieren.

>[!IMPORTANT]
>
>Bevor Sie die Edge-Personalisierung implementieren, lesen Sie das Handbuch zum Aktivieren [&#x200B; Zielgruppendaten für Edge-Personalisierungsziele &#x200B;](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/ui/activate/activate-edge-personalization-destinations). Dieses Handbuch führt Sie durch die erforderlichen Konfigurationsschritte für die Anwendungsfälle der Personalisierung der gleichen Seite und der nächsten Seite für mehrere Experience Platform-Komponenten.

## Architekturdiagramm

<img src="assets/real-time-edge-lookup.svg" alt="Referenzarchitektur für den Edge-Profilzugriff für Web- und Mobile-Personalization" style="width:90%; border:1px solid #4a4a4a"  class="modal-image" />

## Leitlinien

* [Leitlinien für [!UICONTROL Echtzeit-Kundenprofildaten]](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=de)
* [Edge Network-Leitplanken](https://experienceleague.adobe.com/docs/experience-platform/edge-network-server-api/guardrails.html)
* Edge-Profile haben eine TTL (Time-to-Live) von 14 Tagen. Wenn ein Benutzer seit 14 Tagen nicht am Edge aktiv ist, kann das Edge-Profil ablaufen und muss vom Hub abgerufen werden, was sich auf die Personalisierung der ersten Seite auswirken kann.
* Die Edge-Personalisierung unterstützt die Evaluierung der Zielgruppenzugehörigkeit in Echtzeit für Zielgruppen, die Edge-Segmentierungskriterien erfüllen. Batch- und Streaming-Zielgruppen vom Hub sind auch am Edge mit entsprechender Konfiguration verfügbar.

## Implementierungsmuster

Die Edge-Personalisierung kann mit dem Ziel [Benutzerdefinierte Personalization-Verbindung](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/personalization/custom-personalization) in Real-time Customer Data Platform implementiert werden. Dieses Ziel unterstützt je nach Anwendungsfall mehrere Datenerfassungsmethoden.

### Muster 1: Zielgruppenzugehörigkeits-basierte Personalisierung mit Web SDK / Mobile SDK

* Verwenden Sie die Adobe Experience Platform Web SDK oder Mobile SDK mit der Edge Network für eine zielgruppenmitgliedsbasierte Personalisierung.
* Dieser Ansatz bietet niedrige Latenz und beste Leistung für die Edge-Personalisierung basierend auf Zielgruppenmitgliedschaften.
* Für die Echtzeit-Edge-Segmentierung ist die Implementierung von Web/Mobile SDK erforderlich.
* Web SDK und Mobile SDK **unterstützen nur Personalisierung basierend auf der Zielgruppenzugehörigkeit**.
* [&#x200B; Informationen zur SDK-basierten Implementierung finden Sie &#x200B;](../experience-platform/deployment/websdk.md) Experience Platform Web and Mobile SDK Blueprint .
* Für die Implementierung von Mobile SDK muss die Erweiterung [Adobe Journey Optimizer - Decisioning](https://developer.adobe.com/client-sdks/edge/adobe-journey-optimizer-decisioning/) in der Mobile SDK installiert werden.

### Muster 2: Attributbasierte Personalisierung mit Edge Network Server-API (erforderlich für Profilattribute)

>[!IMPORTANT]
>
>**Attributbasierte Personalisierungsanforderungen:** Wenn Sie eine Personalisierung anhand von Profilattributen (nicht nur der Zielgruppenzugehörigkeit) vornehmen möchten, **&#x200B;**&#x200B;Sie die [Edge Network-Server-](https://experienceleague.adobe.com/docs/experience-platform/edge-network-server-api/overview.html?lang=de) mit authentifizierter serverseitiger Integration verwenden, unabhängig davon, ob Sie auch Web SDK oder Mobile SDK für die Datenerfassung verwenden.

* Ermöglicht die Integration mit Personalisierungs-Engines von Drittanbietern und CDN-basierter Personalisierung.
* Die Edge Network-Server **API ist erforderlich** um Profilattribute für die Personalisierung sicher abzurufen.
* Sie können Profilattribute über die Edge Network-Server-API abrufen, indem Sie eine serverseitige Integration hinzufügen, die denselben Datenstrom verwendet, den Sie bereits für Ihre Web- oder mobile SDK-Implementierung verwenden.
* Alle Edge Network Server-API-Aufrufe für Profilattribute müssen in einem authentifizierten Kontext erfolgen, um vertrauliche Daten zu schützen.
* Dieses Muster ermöglicht sowohl eine auf der Zielgruppenzugehörigkeit basierende Personalisierung als auch eine auf Attributen basierende Personalisierung.
* Geeignet für Anwendungsfälle der Server-seitigen Personalisierung, API-basierte Integrationen und Szenarien, die einen Zugriff auf Profilattribute erfordern.

## Implementierungsschritte

1. [Erstellen Sie Schemas](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2021.1.xdm&lang=de) für die zu erfassenden Daten.
1. [Erstellen Sie Datensätze](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-ingestion/create-datasets-and-ingest-data.html?lang=de) für die zu erfassenden Daten.
1. [Konfigurieren Sie die richtigen Identitäten und Identity](https://experienceleague.adobe.com/docs/platform-learn/tutorials/identities/label-ingest-and-verify-identity-data.html?lang=de)Namespaces im Schema, um sicherzustellen, dass aufgenommene Daten sich zu einem einheitlichen Profil zusammenfügen können.
1. [Aktivieren Sie die Schemas und Datensätze für Profile](https://experienceleague.adobe.com/docs/platform-learn/tutorials/profiles/bring-data-into-the-real-time-customer-profile.html?lang=de).
1. [Aufnehmen der Daten](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2020.1.dataingestion&lang=de) in Experience Platform.
1. [Einrichten von Zusammenführungsrichtlinien](https://experienceleague.adobe.com/docs/platform-learn/tutorials/profiles/create-merge-policies.html?lang=de) um eine korrekte Identitätszuordnung und Profilzusammenführung sicherzustellen.
1. [Konfigurieren eines Datenstroms](https://experienceleague.adobe.com/docs/experience-platform/datastreams/configure.html?lang=de) in der Experience Platform-Datenerfassung mit aktivierter Zielkonfiguration. Der Datenstrom bestimmt, in welchen Datenerfassungs-Datenstrom die Zielgruppen in der Antwort auf die Seite aufgenommen werden.
1. Implementieren Sie [Adobe Experience Platform Web SDK](https://experienceleague.adobe.com/docs/experience-platform/web-sdk/home.html) oder [Mobile SDK](https://developer.adobe.com/client-sdks/home/) für die Datenerfassung in Web- und Mobile-Eigenschaften.
1. Konfigurieren Sie die Edge-Segmentierung für Zielgruppen, für die eine Echtzeitbewertung erforderlich ist. [Dokumentation zur Edge-Segmentierung](https://experienceleague.adobe.com/docs/experience-platform/segmentation/ui/edge-segmentation.html?lang=de).
1. Richten Sie im Zielkatalog das Ziel [Benutzerdefinierte Personalization-Verbindung](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/personalization/custom-personalization) ein:
1. [Aktivieren von Zielgruppen für das Edge-Personalisierungsziel](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/ui/activate/activate-edge-personalization-destinations). Wählen Sie aus, welche Zielgruppen Sie für das Ziel aktivieren möchten.
1. (Optional für attributbasierte Personalisierung) Wenn Sie zusätzlich zur Zielgruppenzugehörigkeit eine Personalisierung anhand von Profilattributen durchführen müssen, implementieren Sie die [Edge Network Server-API](https://experienceleague.adobe.com/docs/experience-platform/edge-network-server-api/overview.html?lang=de) mit authentifizierter Server-seitiger Integration unter Verwendung desselben Datenstroms. Dies ist **erforderlich** für den Zugriff auf Profilattribute.
1. Implementieren Sie Personalisierungslogik in Ihre Web-/Mobile-App, um die exportierten Zielgruppendaten und Profilattribute zu verwenden:
   * Wenn Sie Tags in Adobe Experience Platform verwenden, verwenden Sie die Funktion [send event complete](https://experienceleague.adobe.com/docs/experience-platform/tags/event-forwarding/overview.html?lang=de), um auf `event.destinations` Variable mit den exportierten Daten zuzugreifen.
   * Wenn Sie keine Tags verwenden, verwenden Sie [Befehlsantworten](https://experienceleague.adobe.com/docs/experience-platform/web-sdk/commands/command-responses.html) um die JSON-Antwort von Adobe Experience Platform zu analysieren und Zielgruppen-IDs und Profilattribute abzurufen.

## Überlegungen bei der Implementierung

### Überlegungen zur Identität

* Bei Verwendung der Web-SDK oder mobilen SDK mit der Edge Network kann jede primäre Identität für die Edge-Personalisierung verwendet werden.
* Für die erste Personalisierung bei der Anmeldung mit bekannten Kundendaten muss die Personalisierungsanfrage eine primäre Identität verwenden, die mit der bekannten Kundenidentität in Real-time Customer Data Platform übereinstimmt. Wenn die primäre ID auf ECID oder eine anonyme Identität festgelegt ist, die noch nicht mit dem bekannten Kundenprofil verknüpft wurde, dauert es einige Zeit, bis die Identitätszuordnung realisiert wird, was sich auf die Verfügbarkeit historischer Profildaten für die Personalisierung auswirken kann.
* Edge-Profile müssen initialisiert werden, bevor sie für die Personalisierung verwendet werden können. Erstmalige Besuchende oder wiederkehrende Besuchende, deren Edge-Profil abgelaufen ist (14-tägige TTL), erleben möglicherweise eine erste Personalisierung auf der Grundlage begrenzter Profildaten, bis das Edge-Profil vollständig ausgefüllt ist.

### Attributbasierte Personalisierung

>[!IMPORTANT]
>
>Profilattribute können vertrauliche Daten enthalten. Um diese Daten zu schützen, **müssen** beim Konfigurieren des benutzerdefinierten Personalization-Ziels für [&#x200B; Attribut-basierte Personalisierung die &#x200B;](https://experienceleague.adobe.com/docs/experience-platform/edge-network-server-api/overview.html?lang=de)Edge Network-Server-API verwenden. Alle Aufrufe der Edge Network Server-API müssen in einem authentifizierten Kontext erfolgen.

* Für die attributbasierte Personalisierung mit Profilattributen müssen Sie eine serverseitige Integration mit der Edge Network-Server-API hinzufügen, die denselben Datenstrom verwendet, den Sie für Ihre Web- oder mobile SDK-Implementierung verwenden.
* Sie müssen konfigurieren, welche Profilattribute über die benutzerdefinierte Personalization-Verbindungszielkonfiguration in die Edge-Projektion einbezogen werden sollen.
* **Nur Web SDK und Mobile SDK unterstützen Personalisierung basierend auf der Zielgruppenzugehörigkeit**. Die Edge Network-Server **API ist erforderlich** um Profilattribute für die Personalisierung sicher abzurufen.
* Wenn Sie die Edge Network-Server-API nicht für den Attributzugriff implementieren, basiert die Personalisierung nur auf der Zielgruppenzugehörigkeit.
* Die API-Antwort für benutzerdefinierte Personalization mit Attributen enthält zusätzlich zu den Zielgruppensegmenten einen `attributes`.

### Überlegungen zur Zielgruppe

* Audiences, die über Streaming oder Batch-Segmentierung im Hub ausgewertet werden, werden an den Edge projiziert und können für die Personalisierung verwendet werden.
* Zielgruppen, die die Edge-Segmentierungskriterien erfüllen, werden am Edge in Echtzeit für die Personalisierung derselben Seite ausgewertet.
* Konfigurieren Sie geeignete Zielgruppen für die Edge-Evaluierung basierend auf ihrer Verwendung in Anwendungsfällen der Echtzeit-Personalisierung.

## Verwandte Dokumentation

### Zielkonfigurationen

* [Benutzerdefinierte Personalization-Verbindung](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/personalization/custom-personalization) - Handbuch zur Primären Implementierung
* [Personalization-Ziele - Übersicht](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/personalization/overview)
* [Aktivieren von Zielgruppen für Edge-Personalisierungsziele](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/ui/activate/activate-edge-personalization-destinations)
* [Profilattribute am Edge in Echtzeit nachschlagen](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/ui/activate/activate-edge-profile-lookup)

### SDK-Dokumentation

* [Dokumentation zu Experience Platform Web SDK](https://experienceleague.adobe.com/docs/experience-platform/web-sdk/home.html)
* [Dokumentation zu Experience Platform Mobile SDK](https://developer.adobe.com/client-sdks/home/)
* [Dokumentation zur Edge Network Server-API](https://experienceleague.adobe.com/docs/experience-platform/edge-network-server-api/overview.html?lang=de)
* [Dokumentation zu Experience Platform Tags &#x200B;](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=de)
* [Befehlsantworten in Web SDK](https://experienceleague.adobe.com/docs/experience-platform/web-sdk/commands/command-responses.html)

### Dokumentation zu Profilen und Segmentierung

* Dokumentation zum [[!UICONTROL Echtzeit-Kundenprofil]](https://experienceleague.adobe.com/docs/experience-platform/profile/home.html)
* [Leitlinien zum Profil](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=de)

### Tutorials

* [Personalisierung des nächsten Treffers mit Real-Time CDP und Adobe Target](https://experienceleague.adobe.com/docs/platform-learn/tutorials/experience-cloud/next-hit-personalization.html)
* [Datenstromkonfiguration](https://experienceleague.adobe.com/docs/experience-platform/datastreams/configure.html?lang=de)
