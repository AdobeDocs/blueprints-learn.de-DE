---
title: Echtzeit-Profilzugriff für Support- und Vertriebsszenarien
description: Suchvorgänge im [!UICONTROL Echtzeit-Kundenprofil] bieten Kontext für mitarbeitergestützten Support und Vertrieb.
solution: Data Collection
kt: 7195
exl-id: 3616cbf1-2e59-4e68-a1ff-1d2e3b344a1c
TQID: https://experienceleague.adobe.com/Ci9pUbGCLQ9uhlQ9l1na7A2NiI9CpCRMLrUSN6lSOnU
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
  - id: edbd1a0e-46c8-49da-8c10-dba9ec80bba9
  - id: fdddec33-c9cb-4459-b8b6-2664395a6f10
feature_v2:
  - id: a075b2c1-7748-4328-b7f6-343aa314616a
  - id: b12f6872-9271-4369-85e5-86969a0b99a2
  - id: b82389f8-9b5e-4083-8e3b-3cef299fb8b9
  - id: ba929a52-9339-4154-9487-317dc875a3c7
  - id: c132d929-fa62-4271-803e-b823be07b914
  - id: daec7ead-f475-492a-a3b3-02ae08565d6f
  - id: e08599ea-8888-4294-ba74-3ba0a7762a46
subfeature_v2:
  - id: cfc95e9b-b035-4403-a6a9-b27a8a053a37
  - id: e5ae22e3-a3b0-46ed-804f-9abf1bbe3e74
  - id: ee602049-8a18-43df-9299-a689a025a371
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
  - id: d3cdead0-685a-4489-9250-4bb709942f66
  - id: e0eb8757-182f-49f3-94a4-1587d16f5094
  - id: e1e0219c-f879-479f-8427-888ed2a6e9c2
source-git-commit: 95ba7aa681e67efb136adac15dc7894cb413a4f0
workflow-type: tm+mt
source-wordcount: 368
ht-degree: 54%

---

# Echtzeit-Profilzugriff für Support- und Vertriebsszenarien

>[!TIP]
>Diese Blueprint ist auch als Anwendungsfallmuster [&#x200B; Audience Building &#x200B;](/help/blueprints/use-case-patterns/audience-building-activation/real-time-profile-lookup.md) Activation verfügbar.

Der Blueprint „Echtzeit-Profilzugriff für Support- und Vertriebsszenarien“ zeigt, wie externe Anwendungen auf das Echtzeit[!UICONTROL Kundenprofil von Adobe Experience Platform zugreifen &#x200B;].

Externe Programme können über API-GET-Anfragen auf Profile zugreifen. Attribute, Ereignisse, Segmentzugehörigkeiten und modellgestützte Funktionen, die im Profil gespeichert sind, können dann in diesen externen Drittanbieterprogrammen verwendet werden.

Mit dieser Funktion können Sie auf umfangreichen Kontext zugreifen, wenn ein Kunde im Callcenter anruft. Der Support-Mitarbeiter hat beispielsweise Einblick in den Lebenszeitwert des Kunden, seine Abwanderungsneigung und die ihm bekannten Marketing-Kampagnen. Vertriebsmitarbeiter können ebenfalls von mehr Kontext und Erkenntnissen über Kunden profitieren.

>[!NOTE]
>
>Die Profilsuche im Hub ist nicht für Anwendungsfälle mit hohem Durchsatz und geringer Latenz vorgesehen, wie z. B. Personalisierung eingehender Web-/Mobilgeräte. Die Profilsuche im Hub ist für Szenarien mit niedrigerer Latenz vorgesehen, wie z. B. Support durch Agenten oder Vertriebsinteraktionen. Für Szenarien mit geringer Latenz, hohem Durchsatz, wie Web-/Mobile-Personalisierung oder Echtzeit-Offer Decisioning, sollte das Edge-Profil genutzt werden. Das Edge-Profil ermöglicht den Echtzeitzugriff über die [benutzerdefinierte Personalization-Verbindung](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/personalization/custom-personalization) von Real-time Customer Data Platform.

## Anwendungsfälle

* Besserer Verbraucherkontext für mitarbeitergestützte Interaktionen wie Support- und Vertriebserlebnisse. Dank der Profilsuche in Experience Platform erhalten Mitarbeiter Kontext zum Verbraucher wie kürzlich durchgeführte Käufe, Kampagneninteraktionen, Neigungen, Zielgruppenzugehörigkeiten und andere Attribute sowie Erkenntnisse, die im Echtzeit-Kundenprofil gespeichert sind.

## Architektur

<img src="assets/customer_activity_hub.svg" alt="Referenzarchitektur für die Blueprint „Customer Activity Hub“" style="width:90%; border:1px solid #4a4a4a"  class="modal-image" />

## Leitlinien

* [Leitplanken für [!UICONTROL Echtzeit-])](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=de)

## Verwandte Dokumentation

* [Adobe Experience Platform Activation - Produktbeschreibung](https://helpx.adobe.com/de/legal/product-descriptions/adobe-experience-platform0.html)
* [[!UICONTROL Echtzeit-Kundenprofil] Dokumentation](https://experienceleague.adobe.com/docs/experience-platform/profile/home.html?lang=de)
* [Leitplanken für Profile](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=de)
* [API für die Profilsuche](https://www.adobe.io/apis/experienceplatform/home/api-reference.html)
