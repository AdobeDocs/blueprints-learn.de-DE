---
title: offer decisioning-Übersicht
description: Bereitstellung personalisierter Angebote für alle Journey.
solution: Experience Platform, Journey Optimizer
exl-id: f6271802-faab-4ffc-92d6-4c4d7d423ed4
source-git-commit: 7dcbf86b362350312a86445bbe7a020f5ccd1752
workflow-type: tm+mt
source-wordcount: '759'
ht-degree: 48%

---

# Journey Optimizer - Übersicht über Offer decisioning

Weitere Informationen zum Entscheidungs-Management finden Sie in der Produktdokumentation [HIER](https://experienceleague.adobe.com/docs/journey-optimizer/using/offer-decisioniong/get-started-decision/starting-offer-decisioning.html?lang=de)

Adobe Decisioning Management ist ein Service, der im Rahmen von Adobe Journey Optimizer bereitgestellt wird. In dieser Blueprint werden die Anwendungsfälle und technischen Funktionen des Programms vorgestellt und die verschiedenen Komponenten der Architektur von und Überlegungen zu Offer Decisioning eingehend erläutert.

Journey Optimizer wird verwendet, um Ihren Kunden zur richtigen Zeit über alle Touchpoints hinweg das beste Angebot und Erlebnis bereitzustellen. offer decisioning erleichtert die Personalisierung mit einer zentralen Bibliothek von Marketing-Angeboten und einer Entscheidungs-Engine, die Regeln und Einschränkungen auf von Adobe Experience Platform erstellte umfangreiche Echtzeitprofile anwendet, damit Sie Ihren Kunden zum richtigen Zeitpunkt das richtige Angebot unterbreiten können.

Die Entscheidungsverwaltungsfunktion besteht aus zwei Hauptkomponenten:

* Die zentrale Angebotsbibliothek , auf der Sie die verschiedenen Elemente erstellen und verwalten können, aus denen Ihre Angebote bestehen, und deren Regeln und Begrenzungen definieren.
* Die Offer Decisioning-Engine nutzt Adobe Experience Platform-Daten und Echtzeit-Kundenprofile zusammen mit der Angebotsbibliothek, um die richtigen Zeitpunkte, Kunden und Kanäle für die Bereitstellung von Angeboten auszuwählen.

<img src="../assets/offers_overview.png" alt="Offer Decisioning" style="width:100%; border:1px solid #4a4a4a" />

Die Entscheidungsverwaltung kann auf zwei Arten bereitgestellt werden: am Rand oder über den Hub. Jede dieser Methoden verfügt über einen spezifischen Satz von Schnittstellen und Protokollen zum Betrieb des Dienstes, wie in den entsprechenden unten referenzierten Blueprints beschrieben. Weitere Informationen finden Sie auch in der Dokumentation zur Entscheidungsverwaltung [HIER](https://experienceleague.adobe.com/docs/journey-optimizer/using/offer-decisioniong/api-reference/offer-delivery-api/decisioning-vs-edge-apis.html).

## Entscheidungsverwaltung am Hub

Einerseits über den Adobe Experience Platform-Hub, eine zentrale Rechenzentrums-Architektur. Im „Hub“-Ansatz werden Angebote mit >500 ms Latenz ausgeführt, personalisiert und bereitgestellt. Die Hub-Architektur eignet sich daher am besten für Kundenerlebnisse, die keine Latenz unterhalb einer Sekunde erfordern. Beispiele sind Angebotsentscheidungen, die für Terminals oder durch Agenten unterstützte Erlebnisse wie in Callcentern oder in persönlichen Interaktionen bereitgestellt werden. Angebote, die in E-Mails, SMS-Nachrichten, Push-Benachrichtigungen und andere ausgehende Kampagnen eingefügt werden, basieren ebenfalls auf dem Hub-Ansatz. Weitere Informationen zum Entscheidungs-Management auf dem Hub finden Sie in der Blueprint [Entscheidungs-Management auf dem Hub](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/customer-journeys/journey-optimizer/offer-decisioning/offers-hub.html?lang=de).

* Die Angebotseignung kann für das gesamte Echtzeit-Kundenprofil einschließlich aller Attribute und Erlebnisereignisse verwendet werden.

### Anwendungsfälle für die Entscheidungsverwaltung auf dem Hub

* Personalisierte Angebote für Terminals und Erlebnisse im Laden.
* Personalisierte Angebote über von Agenten unterstützte Erlebnisse wie Callcenter oder Vertriebsinteraktionen.
* In E-Mails, SMS oder anderen ausgehenden Interaktionen enthaltene Angebote.
* Kanalübergreifende Journey-Ausführung - Konsistenz in Web, Mobile, E-Mail und auf anderen Interaktionskanälen über Adobe Journey Optimizer.

### Entscheidungsmanagement aus technischen Erwägungen des Knotens

* Anforderungen pro Sekunde = 2000.
* Latenz der Reaktion &lt; 500 ms.
* Zugriff auf das gesamte Echtzeit-Kundenprofil, einschließlich Zielgruppenmitgliedschaften, Attributen und Erlebnisereignissen.

## Entscheidungsverwaltung am Rand

Der zweite Ansatz erfolgt über das Experience Edge Network, eine global verteilte, geografische Infrastruktur, die schnelle Erlebnisse in weniger als einer Sekunde bzw. Millisekunden bereitstellt. Das Endverbrauchererlebnis wird von der Edge-Infrastruktur ausgeführt, die dem geografischen Standort der Verbraucher am nächsten ist, um Latenzzeiten zu minimieren. Das Entscheidungs-Management im Edge ist für Echtzeit-Kundenerlebnisse konzipiert, wie über Web oder Mobile eingehende Personalisierungsanfragen. Weitere Informationen zum Entscheidungs-Management im Edge finden Sie in der Blueprint [Entscheidungs-Management im Edge](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/customer-journeys/journey-optimizer/offer-decisioning/offers-edge.html?lang=de).

### Anwendungsfälle für die Entscheidungsverwaltung am Rand

* Online-Personalisierung über eingehende Web- oder mobile Erlebnisse.
* Kanalübergreifende Journey-Ausführung - Konsistenz in Web, Mobile, E-Mail und auf anderen Interaktionskanälen über Adobe Journey Optimizer.

### Entscheidungsverwaltung zu technischen Aspekten der Edge

* Anforderungen pro Sekunde = 5000.
* Latenz der Reaktion &lt; 250 ms.
* Zugriff auf Edge-Echtzeitprofile. Im Profil sind nur Edge-prognostizierte Zielgruppen und Profilattribute verfügbar.
* Wenn in Erlebnissen zum ersten Mal eine Personalisierung erforderlich ist, ist der Hub ideal, da das vollständige Profil verfügbar ist. Das Edge-Profil muss zum ersten Mal vom Hub synchronisiert werden. Daher umfasst das allererste Erlebnis vom Edge keine zuvor hochgeladenen Profildaten zum Hub.

## Verwandte Dokumentation

* [Adobe Experience Platform](https://experienceleague.adobe.com/docs/experience-platform.html?lang=de)
* [Adobe Journey Optimizer](https://experienceleague.adobe.com/docs/journey-optimizer.html?lang=de)
* [Entscheidungs-Management in Adobe Journey Optimizer](https://experienceleague.adobe.com/docs/journey-optimizer/using/offer-decisioniong/get-started-decision/starting-offer-decisioning.html)
* [Produktbeschreibung zu Adobe Journey Optimizer](https://helpx.adobe.com/de/legal/product-descriptions/adobe-journey-optimizer.html)
* [Produktbeschreibung zu Adobe Offer Decisioning](https://helpx.adobe.com/de/legal/product-descriptions/offer-decisioning-app-service.html)
