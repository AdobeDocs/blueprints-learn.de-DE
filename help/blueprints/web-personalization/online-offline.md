---
title: Online-/Offline-Web-Personalisierung
description: Synchronisieren Sie die Web-Personalisierung mit E-Mail und anderen bekannten und anonymen Kanälen.
solution: Experience Platform, Real-time Customer Data Platform, Target, Audience Manager, Analytics, Experience Cloud Services, Data Collection
kt: 7194thumb-web-personalization-scenario2.jpg
translation-type: tm+mt
source-git-commit: 9b6c220a515c5abae22b58fe33558d7d2fed375d
workflow-type: tm+mt
source-wordcount: '958'
ht-degree: 0%

---



# Online-/Offline-Web-Personalisierung

Synchronisieren Sie die Web-Personalisierung mit E-Mail und anderen bekannten und anonymen Kanälen.

## Anwendungsfälle

* Optimierung der Landingpage
* Behavioral- und Offline-Profil-Targeting
* Personalisierung basierend auf vorherigen Produkt-/Content-Ansichten, Produkt-/Content-Affinität, Umweltattributen, Daten zur Audience von Drittanbieterdaten und demografischen Daten sowie Offline-Einblicke wie Transaktionen, Treue- und CRM-Daten und modellierte Einblicke

## Anwendungen

* Echtzeit-Kundendatenplattform
* Adobe Target
* Adobe Audience Manager (optional): Fügt Daten zur Audience von Drittanbietern, Co-op-basiertes Gerätediagramm, die Möglichkeit, Plattformsegmente in Adobe Analytics zu überlagern, und die Möglichkeit hinzu, Adobe Analytics-Segmente in Plattform zu überlagern
* Adobe Analytics (optional): Erweitert die Möglichkeit, Segmente basierend auf historischen Verhaltensdaten und einer feinkörnigen Segmentierung aus Adobe Analytics-Daten zu erstellen

## Architektur

<img src="assets/onoff.svg" alt="Referenzarchitektur für das Szenario Online-/Offline-Web-Personalisierung" style="border:1px solid #4a4a4a" />

## Guardraht

* Segmente, die von Experience Platform zu Audience Manager freigegeben werden, werden innerhalb von Minuten nach der Segmentrealisierung freigegeben - sei es über die Streaming- oder Batch-Evaluierungsmethode. Es gibt eine anfängliche Segmentkonfigurationssynchronisierung zwischen AEP und AAM von etwa 4 Stunden, damit die AEP-Segmentmitgliedschaften in AAM Profilen realisiert werden können. In den AAM Profilen sind die AEP-Segmentmitgliedschaften für dieselbe Seitenpersonalisierung über Adobe Target verfügbar.
* Beachten Sie, dass bei Segmentrealisierungen, die innerhalb der 4-Stunden-Segmentkonfigurationssynchronisierung zwischen AEP und AAM auftreten, diese Segmentrealisierungen beim nachfolgenden Stapelsegmentauftrag als &quot;vorhandene&quot;Segmente in AAM umgesetzt werden.
* Freigabe von Stapelsegmenten über AEP - einmal pro Tag oder manuell über API initiiert. Sobald diese Segmentmitgliedschaften realisiert sind, werden sie innerhalb von Minuten AAM freigegeben und stehen für die Personalisierung der gleichen/nächsten Seite in der Zielgruppe zur Verfügung.
* Die Streaming-Segmentierung erfolgt innerhalb von ca. 95 Minuten. Sobald diese Segmentrealisierungen auftreten, werden sie innerhalb von Minuten für AAM freigegeben und für die Personalisierung der gleichen/nächsten Seite in der Zielgruppe verfügbar gemacht.
* Standardmäßig ermöglicht der Segmentfreigabedienst die Freigabe von maximal 75 Audiencen für jede Adobe Analytics Report Suite. Wenn der Kunde über eine Audience Manager-Lizenz verfügt, ist die Anzahl der Audiencen, die zwischen Adobe Analytics und Adobe Target oder Audience Manager und Adobe Target freigegeben werden können, unbegrenzt.

## Voraussetzungen für die Implementierung

| Anwendung/Dienst | Erforderliche Bibliothek | Hinweise |
|---|---|---|
| Adobe Target | Platform Web SDK*, at.js 0.9.1+ oder mbox.js 61+ | &quot;at.js&quot;wird bevorzugt, da &quot;mbox.js&quot;nicht mehr entwickelt wird. |
| Adobe Audience Manager (optional) | Platform Web SDK* oder dil.js 5.0+ |  |
| Adobe Analytics (optional) | Platform Web SDK* oder AppMeasurement.js 1.6.4+ | Die Adobe Analytics-Verfolgung muss die regionale Datenerfassung (Regional Data Collection, RDC) verwenden. |
| Experience Cloud-ID-Dienst | Platform Web SDK* oder VisitorAPI.js 2.0+ | (Empfohlen) Verwenden Sie Experience Platform Launch zur Bereitstellung des ID-Diensts, um sicherzustellen, dass die ID vor Anwendungsaufrufen festgelegt ist |
| Experience Platform Mobile SDK (optional) | 4.11 oder höher für iOS und Android™ |  |
| Experience Platform Web SDK | 1.0, aktuelle Experience Platform SDK-Version hat [verschiedene Anwendungsfälle, die noch nicht für Experience Cloud-Anwendungen](https://github.com/adobe/alloy/projects/5) unterstützt werden |  |


## Implementierungsschritte

1. [Implementieren von Adobe ](https://experienceleague.adobe.com/docs/target/using/implement-target/implementing-target.html) Target für Ihre Web- oder Mobilanwendungen
1. [Implementierung von Adobe Audience Manager](https://experienceleague.adobe.com/docs/audience-manager/user-guide/implementation-integration-guides/implement-audience-manager.html)  (optional)
1. [Implementierung von Adobe Analytics](https://experienceleague.adobe.com/docs/analytics/implementation/home.html)   (optional)
1. [Implementierung von Experience Platform- und Echtzeit-Profil für Kunden](https://experienceleague.adobe.com/docs/platform-learn/getting-started-for-data-architects-and-data-engineers/overview.html)
1. Implementieren Sie [Experience Cloud Identity Service](https://experienceleague.adobe.com/docs/id-service/using/implementation/implementation-guides.html) oder [Experience Platform Web SDK](https://experienceleague.adobe.com/docs/experience-platform/edge/home.html)
   >[!NOTE]
   >
   >Jede Anwendung muss die Experience Cloud-ID verwenden und zum selben Experience Cloud-Org gehören, damit die Audience zwischen den Anwendungen freigegeben werden kann.
1. [Anfordern der Bereitstellung für die Freigabe von Audiencen zwischen Experience Platform und Adobe Target (Freigegebene Audiencen)](https://www.adobe.com/go/audiences)

## Diagramme zu Implementierungsdatenströmen

Der Web/Mobile-Personalisierungsentwurf kann entweder mit herkömmlichen anwendungsspezifischen SDKs (z. B. AppMeasurement.js) oder mit dem Platform Web SDK/Mobile SDK und Edge Network implementiert werden.

### Plattform-Web/Mobile-SDK und Edge-Ansatz

<img src="assets/websdkflow.svg" alt="Referenzarchitektur für das Platform Web SDK/Mobile SDK und den Edge Network Approach" style="border:1px solid #4a4a4a" />

### Anwendungsspezifischer SDK-Ansatz

<img src="assets/appsdkflow.png" alt="Referenzarchitektur für den anwendungsspezifischen SDK-Ansatz" style="border:1px solid #4a4a4a" />

## Verwandte Dokumentation

* [Segmentfreigabe für Experience Platformen mit Audience Manager und anderen Experience Cloud-Lösungen](https://experienceleague.adobe.com/docs/audience-manager/user-guide/implementation-integration-guides/integration-experience-platform/aam-aep-audience-sharing.html)
* [Übersicht über die Segmentierung von Experience Platformen](https://experienceleague.adobe.com/docs/experience-platform/segmentation/home.html)
* [Streaming-Segmentierung](https://experienceleague.adobe.com/docs/experience-platform/segmentation/api/streaming-segmentation.html)
* [Übersicht über den Segmentaufbau in Experience Platformen](https://experienceleague.adobe.com/docs/experience-platform/segmentation/ui/overview.html)
* [Audience Manager Source Connector](https://experienceleague.adobe.com/docs/experience-platform/sources/connectors/adobe-applications/audience-manager.html)
* [Adobe Analytics-Segmentfreigabe durch AAM](https://experienceleague.adobe.com/docs/analytics/components/segmentation/segmentation-workflow/seg-publish.html)
* [Dokumentation zum Experience Platform Web SDK](https://experienceleague.adobe.com/docs/experience-platform/edge/home.html)
* [Dokumentation zum Experience Cloud-ID-Dienst](https://experienceleague.adobe.com/docs/id-service/using/home.html)
* [Dokumentation zum Experience Platform Launch](https://experienceleague.adobe.com/docs/launch/using/home.html)

## Verwandte Blog-Beiträge

* [Blueprint für die Web-Personalisierung mit Adobe Experience Platform Real-Time Customer Profil](https://medium.com/adobetech/blueprint-for-web-personalization-using-adobe-experience-platform-real-time-customer-profile-fef2ce7a4b2f)
* [Erstellen Sie ein optimales Online-Erlebnis: Verbesserung des einheitlichen Profils mit dem Abfrage-Dienst](https://medium.com/adobetech/build-an-optimal-online-experience-enrich-unified-profile-with-query-service-8027c196ab33)
* [Integrieren der Adobe Experience Platform-Entscheidungsmodul in AEM Websites](https://jaeness.medium.com/integrating-adobe-experience-platform-decisioning-engine-with-aem-websites-9c222acd12e2)
* [Adobe Experience Platforms Identitätsdienst - Lösung des Problems der Kundenidentität](https://medium.com/adobetech/adobe-experience-platforms-identity-service-how-to-solve-the-customer-identity-conundrum-f95e22d16ea9)
* [Verbessern der personalisierten Erlebnisse durch Adobe Experience Platform Predictive-Audiencen](https://medium.com/adobetech/how-adobe-experience-platform-predictive-audiences-improves-personalized-experiences-1f75a60cb7a3)
* [Adobe Experience Platform Web SDK for Audience Management](https://medium.com/adobetech/adobe-experience-platform-web-sdk-for-audience-management-751fa6d063bc)
* [Implementierung von Adobe Experience Platform Echtzeit-Kundendaten-Profil durch unser Programm &quot;Customer Zero&quot;](https://medium.com/adobetech/implementing-adobe-experience-platform-real-time-customer-profile-through-our-customer-zero-32e7cd952896)
* [Wie Adobe Experience Platform Kunden dabei unterstützen kann, ihre Mobile Messaging in Echtzeit mit Journey Orchestration Service und einem Anbieter von Mobile Messaging zu personalisieren](https://medium.com/adobetech/how-adobe-experience-platform-helped-a-client-personalize-their-mobile-messaging-in-real-time-with-7d634aefa098)
* [Segmentierung in Sekunden: Wie Adobe Experience Platform Kundendaten in Echtzeit zur Realität gemacht hat](https://medium.com/adobetech/segmentation-in-seconds-how-adobe-experience-platform-made-real-time-customer-profiles-a-reality-a7a8552b0847)
* [Erstellen Sie ein optimales Online-Erlebnis: Verbesserung des einheitlichen Profils mit dem Abfrage-Dienst](https://medium.com/adobetech/build-an-optimal-online-experience-enrich-unified-profile-with-query-service-8027c196ab33)


