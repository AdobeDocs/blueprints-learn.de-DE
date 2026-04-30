---
title: Echtzeit-Edge-Profilzugriff für Web- und Mobile-Personalization
description: '[!UICONTROL Echtzeit-Kundenprofil] Zugriff am Edge, um Kontext für die Echtzeit-Personalisierung im Web und auf Mobilgeräten bereitzustellen.'
solution: Real-Time Customer Data Platform, Data Collection
kt: 719
exl-id: 61b81d00-c4bd-41b2-8161-683814947b56
TQID: https://experienceleague.adobe.com/H59c3UBbNCQFs3H0VL5iVDKKZ5D3CFt4ri2RVwNlq7s
product_v2:
  - id: fdddec33-c9cb-4459-b8b6-2664395a6f10
feature_v2:
  - id: ba929a52-9339-4154-9487-317dc875a3c7
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
  - id: bce87dde-a4ab-44c9-8a18-ad66e4ddb377
  - id: c4147b6e-073b-4d3c-9ab1-d60f2f4434ef
  - id: cdd65e7e-8839-44a2-bc21-0e03623b5dd1
  - id: d3cdead0-685a-4489-9250-4bb709942f66
  - id: e0eb8757-182f-49f3-94a4-1587d16f5094
  - id: e1e0219c-f879-479f-8427-888ed2a6e9c2
  - id: fd2e3797-f2ea-4b36-a9af-52acf5e90513
source-git-commit: 95ba7aa681e67efb136adac15dc7894cb413a4f0
workflow-type: tm+mt
source-wordcount: 631
ht-degree: 8%

---

# Echtzeit-Edge-Profilzugriff für Web- und Mobile-Personalization

>[!TIP]
>Diese Blueprint ist auch als Anwendungsfallmuster [&#x200B; Personalization &#x200B;](/help/blueprints/use-case-patterns/personalization/edge-profile-access.md).

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

## Architekturdiagramm

<img src="assets/real-time-edge-lookup.svg" alt="Referenzarchitektur für den Edge-Profilzugriff für Web- und Mobile-Personalization" style="width:90%; border:1px solid #4a4a4a"  class="modal-image" />

## Leitlinien

* [Leitplanken für [!UICONTROL Echtzeit-])](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=de)
* [Edge Network-Leitplanken](https://experienceleague.adobe.com/docs/experience-platform/edge-network-server-api/guardrails.html)
* Edge-Profile haben eine TTL (Time-to-Live) von 14 Tagen. Wenn ein Benutzer seit 14 Tagen nicht am Edge aktiv ist, kann das Edge-Profil ablaufen und muss vom Hub abgerufen werden, was sich auf die Personalisierung der ersten Seite auswirken kann.
* Die Edge-Personalisierung unterstützt die Evaluierung der Zielgruppenzugehörigkeit in Echtzeit für Zielgruppen, die Edge-Segmentierungskriterien erfüllen. Batch- und Streaming-Zielgruppen vom Hub sind auch am Edge mit entsprechender Konfiguration verfügbar.

## Verwandte Dokumentation

### Zielkonfigurationen

* [Benutzerdefinierte Personalization-Verbindung](https://experienceleague.adobe.com/de/docs/experience-platform/destinations/catalog/personalization/custom-personalization) - Handbuch zur Primären Implementierung
* [Personalization-Ziele - Übersicht](https://experienceleague.adobe.com/de/docs/experience-platform/destinations/catalog/personalization/overview)
* [Aktivieren von Zielgruppen für Edge-Personalisierungsziele](https://experienceleague.adobe.com/de/docs/experience-platform/destinations/ui/activate/activate-edge-personalization-destinations)
* [Profilattribute am Edge in Echtzeit nachschlagen](https://experienceleague.adobe.com/de/docs/experience-platform/destinations/ui/activate/activate-edge-profile-lookup)

### SDK-Dokumentation

* [Dokumentation zu Experience Platform Web SDK](https://experienceleague.adobe.com/docs/experience-platform/web-sdk/home.html?lang=de)
* [Dokumentation zu Experience Platform Mobile SDK](https://developer.adobe.com/client-sdks/home/)
* [Dokumentation zur Edge Network Server-API](https://experienceleague.adobe.com/docs/experience-platform/edge-network-server-api/overview.html?lang=de)
* [Dokumentation zu Experience Platform Tags](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=de)
* [Befehlsantworten in Web SDK](https://experienceleague.adobe.com/docs/experience-platform/web-sdk/commands/command-responses.html?lang=de)

### Dokumentation zu Profilen und Segmentierung

* [[!UICONTROL Echtzeit-Kundenprofil] Dokumentation](https://experienceleague.adobe.com/docs/experience-platform/profile/home.html?lang=de)
* [Leitplanken für Profile](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=de)

### Tutorials

* [Next-Hit-Personalisierung mit Real-Time CDP und Adobe Target](https://experienceleague.adobe.com/docs/platform-learn/tutorials/experience-cloud/next-hit-personalization.html?lang=de)
* [Datenstromkonfiguration](https://experienceleague.adobe.com/docs/experience-platform/datastreams/configure.html?lang=de)
