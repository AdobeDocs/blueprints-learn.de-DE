---
title: Szenario zur verhaltensbasierten Web-Personalisierung
description: Personalisieren Sie diese auf Grundlage von Online-Verhaltensdaten und Daten zur Audience.
solution: Experience Platform, Target, Audience Manager, Analytics, Experience Cloud Services, Data Collection
kt: 7085thumb-web-personalization-scenario1.jpg
translation-type: tm+mt
source-git-commit: e1a9881996a181310bdc32cb083e4c5654139bf0
workflow-type: tm+mt
source-wordcount: '607'
ht-degree: 0%

---


# Szenario zur verhaltensbasierten Web-Personalisierung

Personalisieren Sie diese auf Grundlage von Online-Verhaltensdaten und Daten zur Audience.

## Anwendungsfälle

* Optimierung der Landingpage
* Verhaltensbasiertes Targeting
* Personalisierung basierend auf früheren Ansichten von Produkten/Inhalten, Affinität von Produkten/Inhalten, Umweltattributen, Daten zur Audience von Drittanbieterdaten und demografischen 

## Anwendungen

* Adobe Target
* Adobe Analytics (optional)
* Adobe Audience Manager (optional)

## Architektur

<img src="assets/personalization.svg" alt="Referenzarchitektur für das Szenario "Verhaltensbasierte Web-Personalisierung"" style="border:1px solid #4a4a4a" />


## Guardraht

Der Segmentfreigabedienst ermöglicht standardmäßig die Freigabe von maximal 75 Audiencen für jede Adobe Analytics Report Suite. Wenn Audience Manager für die Freigabe von Audiencen verwendet wird, gibt es keine Beschränkung für die Anzahl der Audiencen, die freigegeben werden können. 

## Voraussetzungen für die Implementierung

| Anwendung/Dienst | Erforderliche Bibliothek | Hinweise |
|---|---|---|
| Adobe Target | Platform Web SDK*, at.js 0.9.1+ oder mbox.js 61+ | &quot;at.js&quot;wird bevorzugt, da &quot;mbox.js&quot;nicht mehr entwickelt wird. |
| Adobe Audience Manager (optional) | Platform Web SDK* oder dil.js 5.0+ |  |
| Adobe Analytics (optional) | Platform Web SDK* oder AppMeasurement.js 1.6.4+ |  |
| Experience Cloud-Identitätsdienst | Platform Web SDK* oder VisitorAPI.js 2.0+ |  |
| Experience Platform Mobile SDK (optional) | 4.11 oder höher für iOS und Android™ |  |
| Experience Platform Web SDK | 1.0, aktuelle Experience Platform SDK-Version hat [verschiedene Anwendungsfälle, die noch nicht für Experience Cloud-Anwendungen](https://github.com/adobe/alloy/projects/5) unterstützt werden |  |

## Implementierungsschritte

1. [Implementieren Sie Adobe ](https://experienceleague.adobe.com/docs/target/using/implement-target/implementing-target.html) Target für Ihre Web- oder Mobilanwendungen.

   Bei Verwendung von Audience Manager oder Analytics:

1. [Implementierung von Adobe Audience Manager](https://experienceleague.adobe.com/docs/audience-manager/user-guide/implementation-integration-guides/implement-audience-manager.html)
1. [Implementierung von Adobe Analytics](https://experienceleague.adobe.com/docs/analytics/implementation/home.html)
1. [Experience Cloud-Identitätsdienst implementieren](https://experienceleague.adobe.com/docs/id-service/using/implementation/implementation-guides.html)

   >[!NOTE]
   >
   >Jede Anwendung muss die Experience Cloud-ID verwenden und zum selben Experience Cloud-Org gehören, damit die Audience zwischen den Anwendungen freigegeben werden kann.

1. [Anfordern der Bereitstellung für die Freigabe von Personen und Audiencen (Freigegebene Audiencen)](https://www.adobe.com/go/audiences)
1. Erstellen Sie Segmente in [Adobe Analytics](https://experienceleague.adobe.com/docs/analytics/components/segmentation/segmentation-workflow/seg-build.html) oder [Adobe Audience Manager](https://experienceleague.adobe.com/docs/audience-manager/user-guide/features/segments/segment-builder.html) und [konfigurieren Sie diese Audiencen für die Freigabe für das Experience Cloud](https://experienceleague.adobe.com/docs/analytics/components/segmentation/segmentation-workflow/seg-publish.html) (bei Audience Manager oder Adobe Analytics).
1. Sobald die Audiencen in Adobe Target verfügbar sind, können sie für [Targeting-Erlebnisse mit Adobe Target](https://experienceleague.adobe.com/docs/target/using/audiences/target.html) verwendet werden


## Diagramme zu Implementierungsdatenströmen

Das Web/Mobile Personalization Blueprint kann entweder mit dem Platform Web SDK oder dem Mobile SDK und dem Edge-Netzwerk oder mit herkömmlichen anwendungsspezifischen SDKs (z. B. AppMeasurement.js) implementiert werden.

### Plattform-Web/Mobile-SDK und Edge-Netzwerkansatz

<img src="assets/websdkflow.svg" alt="Referenzarchitektur für das Platform Web SDK/Mobile SDK und den Edge Network Approach" style="border:1px solid #4a4a4a" />


### Anwendungsspezifischer SDK-Ansatz

<img src="assets/appsdkflow.png" alt="Referenzarchitektur für den anwendungsspezifischen SDK-Ansatz" style="border:1px solid #4a4a4a" />


## Verwandte Dokumentation

* [Experience Cloud-Audiencen](https://experienceleague.adobe.com/docs/core-services/interface/audiences/audience-library.html)
* [Audience Manager mit Adobe Target integrieren](https://experienceleague.adobe.com/docs/audience-manager/user-guide/implementation-integration-guides/integration-other-solutions/aam-target-integration.html)
* [Adobe Analytics-Segmentfreigabe durch AAM](https://experienceleague.adobe.com/docs/analytics/components/segmentation/segmentation-workflow/seg-publish.html)


## Verwandte Blog-Beiträge

* [Blueprint für die Web-Personalisierung mit Adobe Experience Platform Real-Time Customer Profil](https://medium.com/adobetech/blueprint-for-web-personalization-using-adobe-experience-platform-real-time-customer-profile-fef2ce7a4b2f)
* [Integrieren der Adobe Experience Platform-Entscheidungsmodul in AEM Websites](https://jaeness.medium.com/integrating-adobe-experience-platform-decisioning-engine-with-aem-websites-9c222acd12e2)
* [Verbessern der personalisierten Erlebnisse durch Adobe Experience Platform Predictive-Audiencen](https://medium.com/adobetech/how-adobe-experience-platform-predictive-audiences-improves-personalized-experiences-1f75a60cb7a3)
* [Adobe Experience Platform Web SDK for Audience Management](https://medium.com/adobetech/adobe-experience-platform-web-sdk-for-audience-management-751fa6d063bc)
* [Implementierung von Adobe Experience Platform Echtzeit-Kundendaten-Profil durch unser Programm &quot;Customer Zero&quot;](https://medium.com/adobetech/implementing-adobe-experience-platform-real-time-customer-profile-through-our-customer-zero-32e7cd952896)
* [Wie Adobe Experience Platform Kunden dabei unterstützen kann, ihre Mobile Messaging in Echtzeit mit Journey Orchestration Service und einem Anbieter von Mobile Messaging zu personalisieren](https://medium.com/adobetech/how-adobe-experience-platform-helped-a-client-personalize-their-mobile-messaging-in-real-time-with-7d634aefa098)
* [Segmentierung in Sekunden: Wie Adobe Experience Platform Kundendaten in Echtzeit zur Realität gemacht hat](https://medium.com/adobetech/segmentation-in-seconds-how-adobe-experience-platform-made-real-time-customer-profiles-a-reality-a7a8552b0847)