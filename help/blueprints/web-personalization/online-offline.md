---
title: Online-/Offline-Webpersonalisierungskonzept
description: Synchronisieren von Web-Personalisierung mit E-Mail und anderen bekannten und anonymen Kanalpersonalisierungen.
solution: Experience Platform, Real-time Customer Data Platform, Target, Audience Manager, Analytics, Experience Cloud Services, Data Collection
kt: 7194thumb-web-personalization-scenario2.jpg
exl-id: 29667c0e-bb79-432e-af3a-45bd0b3b43bb
translation-type: tm+mt
source-git-commit: 37416aafc997838888edec2658d2621d20839f94
workflow-type: tm+mt
source-wordcount: '865'
ht-degree: 69%

---

# Online-/Offline-Web-/Mobile-Personalisierungskonzept

Synchronisieren von Web-Personalisierung mit E-Mail und anderen bekannten und anonymen Kanalpersonalisierungen.

## Anwendungsfälle

* Landingpage-Optimierung
* Verhaltens- und Offline-Profil-Targeting
* Personalisierung basierend auf vorherigen Produkt-/Content-Ansichten, Produkt-/Content-Affinität, Umgebungsattributen, Third-Party-Zielgruppendaten und Offline-Erkenntnissen, wie Transaktionen, Treue- und CRM-Daten und Modellerkenntnissen.

## Programme

* [!UICONTROL Real-Time Customer Data Platform]
* Adobe Target
* Adobe Audience Manager (optional): Fügt Third-Party-Zielgruppendaten, Co-op-basierte Gerätediagramme und die Möglichkeit hinzu, Platform-Segmente in Adobe Analytics und Adobe Analytics-Segmente in Platform zu ermitteln
* Adobe Analytics (optional): Fügt die Möglichkeit hinzu, Segmente basierend auf historischen Verhaltensdaten und detaillierte Segmentierung aus Adobe Analytics-Daten aufzubauen

## Architektur

<img src="assets/onoff.svg" alt="Referenzarchitektur für das Web-Personalisierungskonzept für Online-/Offline" style="border:1px solid #4a4a4a" />

## Leitlinien

* Segmente, die von Experience Platform an Audience Manager freigegeben werden, werden innerhalb von Minuten nach der Segmentrealisierung freigegeben - entweder über Streaming- oder Batch-Evaluierung. Es gibt eine anfängliche Segmentkonfigurationssynchronisierung zwischen Experience Platform und Audience Manager von etwa 4 Stunden, damit die Segmentmitgliedschaften der Experience Platform in Audience Manager-Profilen realisiert werden. Sobald die Audience Manager-Profil vorhanden sind, können die Experience Platformen-Segmentmitgliedschaften über Adobe Target für dieselbe Seitenpersonalisierung genutzt werden.
* Beachten Sie, dass bei Segmentrealisierungen, die innerhalb der 4-Stunden-Segmentkonfigurationssynchronisierung zwischen Experience Platform und Audience Manager stattfinden, diese Segmentrealisierungen beim nachfolgenden Stapelsegmentauftrag als &quot;vorhandene&quot;Segmente in Audience Manager implementiert werden.
* Segmentfreigabe per Batch von der Experience Platform - einmal pro Tag oder manuell über die API initiiert. Sobald diese Segmentmitgliedschaften realisiert sind, werden sie innerhalb von Minuten für den Audience Manager freigegeben und stehen für die Personalisierung der gleichen/nächsten Seite in der Zielgruppe zur Verfügung.
* Die Streaming-Segmentierung wird innerhalb von etwa 5 Minuten durchgeführt. Sobald diese Segmentrealisierungen auftreten, werden sie innerhalb von Minuten für den Audience Manager freigegeben und für die Personalisierung der gleichen/nächsten Seite in der Zielgruppe verfügbar gemacht.
* Standardmäßig ermöglicht der Segmentfreigabe-Service die Freigabe von maximal 75 Zielgruppen pro Adobe Analytics-Report-Suite. Wenn der Kunde über eine Audience Manager-Lizenz verfügt, ist die Anzahl der Zielgruppen, die zwischen Adobe Analytics und Adobe Target oder Audience Manager und Adobe Target freigegeben werden können, nicht begrenzt.

## Implementierungsmuster

Der Personalisierungsentwurf für Web/Mobile lässt sich wie folgt implementieren:

1. Verwenden des [!UICONTROL Platform Web SDK] oder [!UICONTROL Platform Mobile SDK] und [!UICONTROL Edge Network].
1. Verwenden herkömmlicher anwendungsspezifischer SDKs (z. B. AppMeasurement.js)

### 1. Plattform-Web/Mobile-SDK und Edge-Ansatz

<img src="assets/websdkflow.svg" alt="Referenzarchitektur für das [!UICONTROL Platform Web SDK] oder [!UICONTROL Platform Mobile SDK] und [!UICONTROL Edge Network] Ansatz" style="border:1px solid #4a4a4a" />

### 2. Anwendungsspezifischer SDK-Ansatz

<img src="assets/appsdkflow.png" alt="Referenzarchitektur für die Herangehensweise für anwendungsspezifische SDKs" style="border:1px solid #4a4a4a" />

## Voraussetzungen für die Implementierung

| Anwendung/Service | Erforderliche Bibliothek | Hinweise |
|---|---|---|
| Adobe Target | [!UICONTROL Platform Web SDK]*, at.js 0.9.1+ oder mbox.js 61+ | at.js wird bevorzugt, da mbox.js nicht mehr entwickelt wird. |
| Adobe Audience Manager (optional) | [!UICONTROL Platform Web SDK]* oder dil.js 5.0+ |  |
| Adobe Analytics (optional) | [!UICONTROL Platform Web SDK]* oder AppMeasurement.js 1.6.4+ | Adobe Analytics-Tracking muss Regional Data Collection (RDC) verwenden. |
| Experience Cloud-ID-Service | [!UICONTROL Platform Web SDK]* oder VisitorAPI.js 2.0+ | (Empfohlen) Verwenden Sie Adobe Experience Platform Launch zur Bereitstellung des ID-Service, um sicherzustellen, dass die ID eingestellt ist, bevor Programmaufrufe erfolgen |
| Experience Platform Mobile SDK (optional) | 4.11 oder höher für iOS und Android™ |  |
| Experience Platform Web SDK | 1.0, die aktuelle Experience Platform SDK-Version verfügt über [diverse Anwendungsfälle, die noch nicht für die Experience Cloud-Programme unterstützt werden](https://github.com/adobe/alloy/projects/5) |  |


## Implementierungsschritte

1. [Implementieren Sie Adobe Target](https://experienceleague.adobe.com/docs/target/using/implement-target/implementing-target.html?lang=de) für Ihre Web-Anwendungen oder Mobile Apps
1. [Implementieren Sie Adobe Audience Manager](https://experienceleague.adobe.com/docs/audience-manager/user-guide/implementation-integration-guides/implement-audience-manager.html?lang=de) (optional)
1. [Implementieren Sie Adobe Analytics](https://experienceleague.adobe.com/docs/analytics/implementation/home.html?lang=de) (optional)
1. [[!UICONTROL Implementieren Sie Experience Platform und das Echtzeit-Kundenprofil]](https://experienceleague.adobe.com/docs/platform-learn/getting-started-for-data-architects-and-data-engineers/overview.html?lang=de)
1. Implementieren Sie [Experience Cloud Identity Service](https://experienceleague.adobe.com/docs/id-service/using/implementation/implementation-guides.html?lang=de) oder [Experience Platform Web SDK](https://experienceleague.adobe.com/docs/experience-platform/edge/home.html?lang=de)
   >[!NOTE]
   >
   >Jedes Programm muss die Experience Cloud-ID nutzen und Teil derselben Experience Cloud-Organisation sein, damit die Zielgruppenfreigabe zwischen Programmen möglich ist.
1. [Fordern Sie die Bereitstellung der Zielgruppenfreigabe zwischen Experience Platform und Adobe Target an (Freigegebene Zielgruppen)](https://www.adobe.com/go/audiences)

## Verwandte Dokumentation

* [Segmentfreigabe für Experience Platform über Audience Manager und andere Experience Cloud-Lösungen](https://experienceleague.adobe.com/docs/audience-manager/user-guide/implementation-integration-guides/integration-experience-platform/aam-aep-audience-sharing.html?lang=de)
* [Überblick über Segmentierung in Experience Platform ](https://experienceleague.adobe.com/docs/experience-platform/segmentation/home.html?lang=de)
* [Streaming-Segmentierung](https://experienceleague.adobe.com/docs/experience-platform/segmentation/api/streaming-segmentation.html?lang=de)
* [Überblick über Experience Platform Segment Builder](https://experienceleague.adobe.com/docs/experience-platform/segmentation/ui/overview.html?lang=de)
* [Audience Manager Source Connector](https://experienceleague.adobe.com/docs/experience-platform/sources/connectors/adobe-applications/audience-manager.html?lang=de)
* [Adobe Analytics-Segmentfreigabe über Adobe Audience Manager](https://experienceleague.adobe.com/docs/analytics/components/segmentation/segmentation-workflow/seg-publish.html?lang=de)
* [Dokumentation zu Experience Platform Web SDK](https://experienceleague.adobe.com/docs/experience-platform/edge/home.html)
* [Dokumentation zu Experience Cloud-ID-Service](https://experienceleague.adobe.com/docs/id-service/using/home.html?lang=de)
* [Dokumentation zu Experience Platform Launch](https://experienceleague.adobe.com/docs/launch/using/home.html?lang=de)

## Verwandte Blog-Posts

* [[!DNL Blueprint for Web Personalization using Adobe Experience Platform Real-Time Customer Profile]](https://medium.com/adobetech/blueprint-for-web-personalization-using-adobe-experience-platform-real-time-customer-profile-fef2ce7a4b2f)
* [[!DNL Build an Optimal Online Experience: Enrich Unified Profile with Query Service]](https://medium.com/adobetech/build-an-optimal-online-experience-enrich-unified-profile-with-query-service-8027c196ab33)
* [[!DNL Integrating Adobe Experience Platform Decisioning Engine with AEM Websites]](https://jaeness.medium.com/integrating-adobe-experience-platform-decisioning-engine-with-aem-websites-9c222acd12e2)
* [[!DNL Adobe Experience Platform’s Identity Service — How to Solve the Customer Identity Conundrum]](https://medium.com/adobetech/adobe-experience-platforms-identity-service-how-to-solve-the-customer-identity-conundrum-f95e22d16ea9)
* [[!DNL How Adobe Experience Platform Predictive Audiences improves Personalized Experiences]](https://medium.com/adobetech/how-adobe-experience-platform-predictive-audiences-improves-personalized-experiences-1f75a60cb7a3)
* [[!DNL Adobe Experience Platform Web SDK for Audience Management]](https://medium.com/adobetech/adobe-experience-platform-web-sdk-for-audience-management-751fa6d063bc)
* [[!DNL Implementing Adobe Experience Platform Real-Time Customer Profile through our “Customer Zero” Program]](https://medium.com/adobetech/implementing-adobe-experience-platform-real-time-customer-profile-through-our-customer-zero-32e7cd952896)
* [[!DNL How Adobe Experience Platform Can Help Customers Personalize Their Mobile Messaging in Real-Time with Journey Orchestration Service and a Mobile Messaging Vendor]](https://medium.com/adobetech/how-adobe-experience-platform-helped-a-client-personalize-their-mobile-messaging-in-real-time-with-7d634aefa098)
* [[!DNL Segmentation in Seconds: How Adobe Experience Platform Made Real-time Customer Profiles a Reality]](https://medium.com/adobetech/segmentation-in-seconds-how-adobe-experience-platform-made-real-time-customer-profiles-a-reality-a7a8552b0847)
* [[!DNL Build an Optimal Online Experience: Enrich Unified Profile with Query Service]](https://medium.com/adobetech/build-an-optimal-online-experience-enrich-unified-profile-with-query-service-8027c196ab33)
