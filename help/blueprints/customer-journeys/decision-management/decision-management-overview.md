---
title: 'Blueprints: Entscheidungs-Management'
description: Bereitstellung personalisierter Angebote für alle Customer Journeys.
solution: Experience Platform, Journey Optimizer
exl-id: 1bc9335c-5321-4d0c-939e-4f402e2e8f51
TQID: https://experienceleague.adobe.com/FWKq0QzEzCXp8TrfECmhY4E3ocA4zZkTGyHrrKQCOBw
product_v2:
  - id: cb954087-f4fc-4456-afb9-e939cabcdc79
  - id: edbd1a0e-46c8-49da-8c10-dba9ec80bba9
feature_v2:
  - id: c132d929-fa62-4271-803e-b823be07b914
  - id: d998adac-2f81-400b-a669-d07bb196e4eb
  - id: daec7ead-f475-492a-a3b3-02ae08565d6f
  - id: df64005d-8f9a-422e-ba4d-c6f6dc3454b4
  - id: fe338112-e2ce-4876-8989-fc4d497613f1
subfeature_v2:
  - id: e5ae22e3-a3b0-46ed-804f-9abf1bbe3e74
  - id: fa683eda-48de-4558-af32-2673edcd44fe
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
  - id: bce87dde-a4ab-44c9-8a18-ad66e4ddb377
  - id: d00e9f03-e50b-4162-b143-0c0817c937c2
  - id: e0eb8757-182f-49f3-94a4-1587d16f5094
  - id: fd2e3797-f2ea-4b36-a9af-52acf5e90513
source-git-commit: a99add31cc9f485db119ca00426798545e6a7316
workflow-type: tm+mt
source-wordcount: 731
ht-degree: 76%

---

# Journey Optimizer - Blueprints für das Entscheidungs-Management

Weitere Informationen finden Sie in der folgenden Dokumentation zu [Entscheidungs-Management](https://experienceleague.adobe.com/docs/journey-optimizer/using/offer-decisioniong/get-started-decision/starting-offer-decisioning.html?lang=de)

In der folgenden Dokumentation finden Sie Leitplanken im Zusammenhang mit dem Entscheidungs-Management. [Leitplanken für das Entscheidungs-Management](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/get-started/guardrails#decision-management.html)

Das Entscheidungs-Management von Adobe ist ein Service, der im Rahmen von Adobe Journey Optimizer bereitgestellt wird. In dieser Blueprint werden die Anwendungsfälle und technischen Funktionen des Programms vorgestellt und die verschiedenen Komponenten der Architektur von und Überlegungen zu Entscheidungs-Management eingehend erläutert.

Journey Optimizer wird verwendet, um Ihren Kunden zur richtigen Zeit auf allen Touchpoints das beste Angebot und Erlebnis bereitzustellen. Entscheidungs-Management erleichtert die Personalisierung durch eine zentrale Bibliothek mit Marketing-Angeboten und eine Entscheidungs-Engine, die Regeln und Einschränkungen auf die von Adobe Experience Platform erstellten Echtzeit-Profile anwendet. Auf diese Weise können Sie Ihren Kunden einfach das richtige Angebot zur richtigen Zeit senden.

Die Entscheidungs-Management-Funktion besteht aus zwei Hauptkomponenten:

* Die zentrale Angebotsbibliothek ist die Schnittstelle, über die Sie die verschiedenen Elemente, aus denen sich Ihre Angebote zusammensetzen, erstellen und verwalten sowie deren Regeln und Einschränkungen definieren.
* Die Offer Decisioning-Engine nutzt Adobe Experience Platform-Daten und Echtzeit-Kundenprofile zusammen mit der Angebotsbibliothek, um die richtigen Momente, Kunden und Kanäle für die Bereitstellung von Angeboten auszuwählen.

<img src="images/offers_overview.png" alt="Entscheidungs-Management" style="width:100%; border:1px solid #4a4a4a" />

Das Entscheidungs-Management kann auf zwei Arten bereitgestellt werden: im Edge oder über den Hub. Jede dieser Methoden verfügt über einen spezifischen Satz von Schnittstellen und Protokollen zum Betrieb des Service, die in den entsprechenden unten genannten Blueprints beschrieben werden. Weitere Informationen finden Sie auch in der [Dokumentation zum Entscheidungs-Management](https://experienceleague.adobe.com/docs/journey-optimizer/using/offer-decisioniong/api-reference/offer-delivery-api/decisioning-vs-edge-apis.html?lang=de).

## Entscheidungs-Management am Hub

Einerseits über den Adobe Experience Platform-Hub, eine zentrale Rechenzentrums-Architektur. Die Hub-Architektur eignet sich am besten für Kundenerlebnisse, die keine niedrige Latenz und einen hohen Durchsatz erfordern, aber eine umfassendere Ansicht des Kundenprofils erfordern. Beispiele sind Angebotsentscheidungen, die für Kiosks oder agentenunterstützte Erlebnisse wie in Callcentern oder in persönlichen Interaktionen bereitgestellt werden. Angebote, die in E-Mails, SMS-Nachrichten, Push-Benachrichtigungen und andere ausgehende Kampagnen eingefügt werden, werden ebenfalls vom Hub-Ansatz unterstützt. Weitere Informationen zum Entscheidungs-Management auf dem Hub finden Sie in der Blueprint [Entscheidungs-Management auf dem Hub](decision-management-hub.md).

* Die Angebotseignung kann auf das gesamte Echtzeit-Kundenprofil einschließlich aller Attribute und Erlebnisereignisse angewendet werden.

### Anwendungsfälle für das Entscheidungs-Management auf dem Hub

* Personalisierte Angebote für Terminals und Erlebnisse im Laden.
* Personalisierte Angebote über von Agenten unterstützte Erlebnisse wie Callcenter oder Vertriebsinteraktionen.
* In E-Mails, SMS oder anderen ausgehenden Interaktionen enthaltene Angebote.
* Kanalübergreifende Journey-Ausführung - Konsistenz in Web, Mobile, E-Mail und auf anderen Interaktionskanälen über Adobe Journey Optimizer.

### Technische Überlegungen zu Entscheidungs-Management auf dem Hub

* Zugriff auf das gesamte Echtzeit-Kundenprofil, einschließlich Zielgruppenzugehörigkeit, Attributen und Erlebnisereignissen.

## Entscheidungs-Management im Edge

Der zweite Ansatz erfolgt über Experience [!DNL Edge Network], eine global verteilte, geografisch verteilte Infrastruktur, die schnelle Erlebnisse in Unter- und Millisekunden ermöglicht. Das Endverbrauchererlebnis wird von der Edge-Infrastruktur ausgeführt, die dem geografischen Standort der Verbraucher am nächsten ist, um Latenzzeiten zu minimieren. Das Entscheidungs-Management im Edge ist für Echtzeit-Kundenerlebnisse konzipiert, wie über Web oder Mobile eingehende Personalisierungsanfragen. Weitere Informationen zum Entscheidungs-Management im Edge finden Sie in der Blueprint [Entscheidungs-Management im Edge](decision-management-edge.md).

### Anwendungsfälle für das Entscheidungs-Management im Edge

* Online-Personalisierung über eingehende Web- oder mobile Erlebnisse.
* Kanalübergreifende Journey-Ausführung - Konsistenz in Web, Mobile, E-Mail und auf anderen Interaktionskanälen über Adobe Journey Optimizer.

### Technische Überlegungen zu Entscheidungs-Management im Edge Network

* Zugriff auf das Edge-Echtzeitprofil. Im Profil sind nur von Edge projizierte Zielgruppen und Profilattribute verfügbar.

## Verwandte Dokumentation

* [Adobe Experience Platform](https://experienceleague.adobe.com/docs/experience-platform.html?lang=de)
* [Adobe Journey Optimizer](https://experienceleague.adobe.com/docs/journey-optimizer.html?lang=de)
* [Entscheidungs-Management in Adobe Journey Optimizer](https://experienceleague.adobe.com/docs/journey-optimizer/using/offer-decisioniong/get-started-decision/starting-offer-decisioning.html?lang=de)
* [Adobe Journey Optimizer-Produktbeschreibung](https://helpx.adobe.com/de/legal/product-descriptions/adobe-journey-optimizer.html)
* [Adobe-Produktbeschreibung für das Entscheidungs-Management](https://helpx.adobe.com/de/legal/product-descriptions/offer-decisioning-app-service.html)
