---
title: 'Blueprint: Web-Personalisierung basierend auf Verhaltensdaten'
description: Hier erfahren Sie, wie Sie Inhalte basierend auf dem Online-Verhalten und den Zielgruppendaten personalisieren können.
landing-page-description: Erfahren Sie, wie Sie basierend auf Daten zu Online-Verhalten und Zielgruppen personalisieren.
short-description: Erfahren Sie, wie Sie basierend auf Daten zu Online-Verhalten und Zielgruppen personalisieren.
solution: Target, Audience Manager, Analytics, Experience Cloud Services, Data Collection, Experience Platform
kt: 7085
thumbnail: thumb-web-personalization-scenario1.jpg
exl-id: b9882c2c-cb45-4efa-a85c-8fe48f641a12
source-git-commit: 1ee81e6e2e9847f53f51bc96e55ea434a0a1cbda
workflow-type: tm+mt
source-wordcount: '442'
ht-degree: 98%

---

# Blueprint: Web-/Mobile-Personalisierung basierend auf Verhaltensdaten

Personalisieren Sie basierend auf Daten zu Online-Verhalten und Zielgruppen.

## Anwendungsfälle

* Landingpage-Optimierung
* Behavioral Targeting
* Personalisierung basierend auf früheren Produkt-/Content-Ansichten, Produkt-/Content-Affinität, Umgebungsattributen, Third-Party-Zielgruppendaten und demografischen Daten

## Programme

* Adobe Target
* Adobe Analytics (optional)
* Adobe Audience Manager (optional)
* Adobe Real-time Customer Data Platform (optional)

## Architektur

<img src="assets/behavioral_personalization.svg" alt="Referenzarchitektur für die Blueprint „Web-Personalisierung basierend auf Verhaltensdaten“" style="width:90%; border:1px solid #4a4a4a; margin-bottom: 15px;" class="modal-image" />


## Implementierungsmuster

Die Blueprint „Web-/Mobile-Personalisierung“ lässt sich wie folgt implementieren:

1. Verwendung des [!UICONTROL Platform Web SDK] oder [!UICONTROL Platform Mobile SDK] und [!UICONTROL Edge Network]. [Weitere Informationen finden Sie in der Blueprint „Experience Platform Web and Mobile SDK“](//experience-platform/deployment/websdk.md)
1. Verwenden herkömmlicher anwendungsspezifischer SDKs (z. B. AppMeasurement.js). [Weitere Informationen finden Sie im Blueprint für anwendungsspezifische SDKs.](//experience-platform/deployment/appsdk.md)

## Implementierungsschritte

1. [Implementieren Sie Adobe Target](https://experienceleague.adobe.com/docs/target/using/implement-target/implementing-target.html?lang=de) für Ihre Web-Anwendungen oder Mobile Apps.

### Implementierungsschritte – Audience Manager oder Adobe Analytics

1. [Implementieren Sie Adobe Audience Manager ](https://experienceleague.adobe.com/docs/audience-manager/user-guide/implementation-integration-guides/implement-audience-manager.html?lang=de)
1. [Implementieren Sie Adobe Analytics](https://experienceleague.adobe.com/docs/analytics/implementation/home.html?lang=de)
1. [Implementieren Sie Experience Cloud Identity Service ](https://experienceleague.adobe.com/docs/id-service/using/implementation/implementation-guides.html?lang=de)

   >[!NOTE]
   >
   >Jedes Programm muss die Experience Cloud-ID nutzen und Teil derselben Experience Cloud-Organisation sein, damit die Zielgruppenfreigabe zwischen Programmen möglich ist.

1. [Fordern Sie die Bereitstellung für die Services „People“ und „Audience Sharing“ an (Freigegebene Zielgruppen)](https://www.adobe.com/go/audiences)
1. Erstellen Sie Segmente in [Adobe Analytics](https://experienceleague.adobe.com/docs/analytics/components/segmentation/segmentation-workflow/seg-build.html?lang=de) oder [Adobe Audience Manager](https://experienceleague.adobe.com/docs/audience-manager/user-guide/features/segments/segment-builder.html?lang=de) und [konfigurieren Sie diese Zielgruppen für die Freigabe in Experience Cloud](https://experienceleague.adobe.com/docs/analytics/components/segmentation/segmentation-workflow/seg-publish.html?lang=de) (bei Verwendung von Audience Manager oder Adobe Analytics)
1. Sobald die Zielgruppen in Adobe Target verfügbar sind, können sie für das [Erlebnis-Targeting mit Adobe Target](https://experienceleague.adobe.com/docs/target/using/audiences/target.html?lang=de) verwendet werden

### Implementierungsschritte – Real-time Customer Data Platform

1. [Erstellen Sie Schemas](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2021.1.xdm&amp;lang=de) für die zu erfassenden Daten.
1. [Erstellen Sie Datensätze](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-ingestion/create-datasets-and-ingest-data.html?lang=de) für die zu erfassenden Daten.
1. [Konfigurieren Sie die korrekten Identitäten und Identitäts-Namespaces](https://experienceleague.adobe.com/docs/platform-learn/tutorials/identities/label-ingest-and-verify-identity-data.html?lang=de) im Schema, um sicherzustellen, dass aufgenommene Daten zu einem einheitlichen Profil zusammengefügt werden können.
1. [Aktivieren Sie die Schemas und Datensätze für Profile](https://experienceleague.adobe.com/docs/platform-learn/tutorials/profiles/bring-data-into-the-real-time-customer-profile.html?lang=de).
1. [Aufnehmen der Daten](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2020.1.dataingestion&amp;lang=de) in Experience Platform.
1. [Stellen Sie in [!UICONTROL Real-Time Customer Data Platform] die Segmentfreigabe](https://www.adobe.com/go/audiences) zwischen Experience Platform und Audience Manager für Zielgruppen bereit, die in Experience Platform für die Freigabe an Audience Manager definiert sind.
1. [Erstellen Sie Segmente](https://experienceleague.adobe.com/docs/platform-learn/tutorials/segments/create-segments.html?lang=de) in Experience Platform. Das System stellt automatisch fest, ob das Segment per Batch oder Streaming evaluiert wird.
1. [Konfigurieren Sie Ziele](https://experienceleague.adobe.com/docs/platform-learn/tutorials/destinations/create-destinations-and-activate-data.html?lang=de) für die Freigabe von Profilattributen und Zielgruppenzugehörigkeiten zu gewünschten Zielen.


## Verwandte Dokumentation

* [Experience Cloud-Zielgruppen](https://experienceleague.adobe.com/docs/core-services/interface/audiences/audience-library.html?lang=de)
* [Integration von Audience Manager mit Adobe Target](https://experienceleague.adobe.com/docs/audience-manager/user-guide/implementation-integration-guides/integration-other-solutions/aam-target-integration.html?lang=de)
* [Segmentfreigabe in Adobe Analytics über Adobe Audience Manager](https://experienceleague.adobe.com/docs/analytics/components/segmentation/segmentation-workflow/seg-publish.html?lang=de)
* Überblick über [[!UICONTROL Real-time Customer Data Platform] ](https://experienceleague.adobe.com/docs/platform-learn/tutorials/application-services/rtcdp/understanding-the-real-time-customer-data-platform.html?lang=de)
* Produktbeschreibung zu [[!UICONTROL Real-time Customer Data Platform] ](https://helpx.adobe.com/de/legal/product-descriptions/real-time-customer-data-platform.html)
* [Richtlinien für Profile und Segmentierung](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=de)
* [Dokumentation zur Segmentierung](https://experienceleague.adobe.com/docs/experience-platform/segmentation/api/streaming-segmentation.html?lang=de)
* [Dokumentation zu Zielen](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/overview.html?lang=de)

## Verwandte Blog-Posts

* [[!DNL Blueprint for Web Personalization using Adobe Experience Platform Real-Time Customer Profile]](https://medium.com/adobetech/blueprint-for-web-personalization-using-adobe-experience-platform-real-time-customer-profile-fef2ce7a4b2f)
* [[!DNL Integrating Adobe Experience Platform Decisioning Engine with AEM Websites]](https://jaeness.medium.com/integrating-adobe-experience-platform-decisioning-engine-with-aem-websites-9c222acd12e2)
* [[!DNL Adobe Experience Platform Web SDK for Audience Management]](https://medium.com/adobetech/adobe-experience-platform-web-sdk-for-audience-management-751fa6d063bc)
* [[!DNL Implementing Adobe Experience Platform Real-Time Customer Profile through our "Customer Zero" Program]](https://medium.com/adobetech/implementing-adobe-experience-platform-real-time-customer-profile-through-our-customer-zero-32e7cd952896)
* [[!DNL How Adobe Experience Platform Can Help Customers Personalize Their Mobile Messaging in Real-Time with Journey Orchestration Service and a Mobile Messaging Vendor]](https://medium.com/adobetech/how-adobe-experience-platform-helped-a-client-personalize-their-mobile-messaging-in-real-time-with-7d634aefa098)
* [[!DNL Segmentation in Seconds: How Adobe Experience Platform Made Real-time Customer Profiles a Reality]](https://medium.com/adobetech/segmentation-in-seconds-how-adobe-experience-platform-made-real-time-customer-profiles-a-reality-a7a8552b0847)
