---
title: Web-/Mobile-Personalisierung mit Online- und Offline-Daten
description: Synchronisieren Sie Web-Personalisierung mit E-Mail und anderen bekannten und anonymen Kanalpersonalisierungen.
landing-page-description: Synchronisieren Sie Web-Personalisierung mit E-Mail und anderen bekannten und anonymen Kanalpersonalisierungen.
solution: Experience Platform, Real-time Customer Data Platform, Target, Audience Manager, Analytics, Experience Cloud Services, Data Collection
kt: 7194thumb-web-personalization-scenario2.jpg
exl-id: 29667c0e-bb79-432e-af3a-45bd0b3b43bb
source-git-commit: 91db73c9fb14d461ee62444199c3d053bd094639
workflow-type: tm+mt
source-wordcount: '1146'
ht-degree: 68%

---

# Web-/Mobile-Personalisierung mit Online- und Offline-Daten

Synchronisieren Sie Web-Personalisierung mit E-Mail und anderen bekannten und anonymen Kanalpersonalisierungen.

## Anwendungsfälle

* Landingpage-Optimierung
* Verhaltens- und Offline-Profil-Targeting
* Personalisierung basierend auf vorherigen Produkt-/Content-Ansichten, Produkt-/Content-Affinität, Umgebungsattributen, Third-Party-Zielgruppendaten und Offline-Erkenntnissen, wie Transaktionen, Treue- und CRM-Daten und Modellerkenntnissen.
* Freigeben und Targeting von in Real-time Customer Data Platform definierten Zielgruppen auf Websites und in Mobile Apps mithilfe von Adobe Target.

## Programme

* [!UICONTROL Real-Time Customer Data Platform]
* Adobe Target
* Adobe Audience Manager (optional): Fügt Zielgruppendaten von Drittanbietern, Co-op-basiertes Gerätediagramm, die Möglichkeit zur Oberflächenbearbeitung von Real-time Customer Data Platform-Zielgruppen in Adobe Analytics und die Möglichkeit hinzu, Adobe Analytics-Zielgruppen in Real-time Customer Data Platform zu überlagern
* Adobe Analytics (optional): Fügt die Möglichkeit hinzu, Segmente basierend auf historischen Verhaltensdaten und detaillierte Segmentierung aus Adobe Analytics-Daten aufzubauen

## Integrationsmuster

<table class="tg" style="undefined;table-layout: fixed; width: 790px">
<colgroup>
<col style="width: 20px">
<col style="width: 276px">
<col style="width: 229px">
<col style="width: 265px">
</colgroup>
<thead>
  <tr>
    <th class="tg-y6fn">Nr.</th>
    <th class="tg-f7v4">Integrationsmuster</th>
    <th class="tg-y6fn">Fähigkeit</th>
    <th class="tg-f7v4">Voraussetzungen</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td class="tg-0lax">1</td>
<td class="tg-73oq">Echtzeit-Segmentbewertung von Real-time Customer Data Platform an Edge, die für Target freigegeben wurde</td>
    <td class="tg-0lax">- Evaluieren von Zielgruppen in Echtzeit im Edge Network zur Personalisierung derselben oder der nächsten Seite.</td>
    <td class="tg-73oq">- Das Target-Ziel muss in Real-time Customer Data Platform Destinations konfiguriert werden.<br>- Zur Integration mit Target ist dieselbe IMS-Org wie für die Experience Platform-Instanz erforderlich.<br>- WebSDK muss implementiert sein.<br>- Mobile SDK- und API-basierte Implementierung ist derzeit nicht verfügbar</td> 
  </tr>
  <tr>
    <td class="tg-0lax">2</td>
    <td class="tg-73oq">Real-time Customer Data Platform-Streaming und Freigabe von Batch-Zielgruppen für Target über den Edge-Ansatz</td>
    <td class="tg-0lax">- Freigeben von Streaming- und Batch-Zielgruppen von Real-time Customer Data Platform an Target über das Edge Network. Die Auswertung von Zielgruppen in Echtzeit erfordert das WebSDK und die Echtzeitauswertung der Zielgruppe, wie im Integrationsmuster 1 beschrieben.</td>
    <td class="tg-73oq">- Das Target-Ziel muss in Real-time Customer Data Platform Destinations konfiguriert werden.<br>- Zur Integration mit Target ist dieselbe IMS-Org wie für die Experience Platform-Instanz erforderlich.<br>WebSDK ist nicht erforderlich. <br>- Bei Verwendung von AT.js wird nur die Profilsuche mit der ECID unterstützt. <br>- Für die Suche nach benutzerdefinierten Identitäts-Namespaces in Edge ist die WebSDK-Bereitstellung erforderlich und jede Identität muss in der Identitätszuordnung als Identität festgelegt werden.</td>
  </tr>
  <tr>
    <td class="tg-0lax">3</td>
    <td class="tg-73oq"><span style="font-weight:400;font-style:normal">Real-time Customer Data Platform-Streaming- und Batch-Zielgruppenfreigabe an Target und Audience Manager über den Ansatz des Zielgruppenfreigabe-Dienstes</span></td>
    <td class="tg-0lax"><span style="font-weight:400;font-style:normal">- Freigeben von Streaming- und Batch-Zielgruppen von Real-time Customer Data Platform für Target und Audience Manager über den Zielgruppenfreigabe-Dienst. Die Auswertung von Zielgruppen in Echtzeit erfordert das WebSDK und die Echtzeitauswertung der Zielgruppe, wie im Integrationsmuster 1 beschrieben.</span></td>
    <td class="tg-73oq">- Die Zielgruppenprognose per Audience Sharing Service muss bereitgestellt werden.<br>- Zur Integration mit Target ist dieselbe IMS-Org wie für die Experience Platform-Instanz erforderlich.<br>- Die Identität muss in ECID aufgelöst werden, damit sie im Edge Network zur Nutzung für Target freigegeben werden kann.<br>- Für diese Integration ist keine WebSDK-Bereitstellung erforderlich.</td>
  </tr>
</tbody>
</table>


## Architektur

Detaillierte Architektur

<img src="assets/RTCDP+Target.png" alt="Referenzarchitektur für die Blueprint „Online-/Offline-Web-Personalisierung“" style="width:80%; border:1px solid #4a4a4a" />

Sequenzdiagramm

<img src="assets/RTCDP+Target_flow.png" alt="Referenzarchitektur für die Blueprint „Online-/Offline-Web-Personalisierung“" style="width:80%; border:1px solid #4a4a4a" />

<br>

<img src="assets/RTCDP+Target_sequence.png" alt="Referenzarchitektur für die Blueprint „Online-/Offline-Web-Personalisierung“" style="width:80%; border:1px solid #4a4a4a" />


Übersicht – Architektur

<img src="assets/personalization_with_apps.png" alt="Referenzarchitektur für die Blueprint „Online-/Offline-Web-Personalisierung“" style="width:80%; border:1px solid #4a4a4a"/>

## Leitlinien

[Beachten Sie die Leitlinien auf der Übersichtsseite zu den Blueprints für die Web- und Mobile-Personalisierung.](overview.md)

## Implementierungsmuster

Die Blueprint „Web-/Mobile-Personalisierung“ lässt sich wie folgt implementieren:

1. Verwendung des [!UICONTROL Platform Web SDK] oder [!UICONTROL Platform Mobile SDK] und [!UICONTROL Edge Network]. [Weitere Informationen finden Sie in der Blueprint „Experience Platform Web and Mobile SDK“](../data-ingestion/websdk.md)
1. Verwendung herkömmlicher programmspezifischer SDKs (z. B. AppMeasurement.js)
<img src="assets/app_sdk_flow.png" alt="Referenzarchitektur für die Herangehensweise für programmspezifische SDKs" style="width:80%; border:1px solid #4a4a4a" />

## Überlegungen bei der Implementierung

Voraussetzungen für Identitäten

* Bei Verwendung des oben beschriebenen Integrationsmusters 1 mit dem Edge-Netzwerk und dem WebSDK kann jede primäre Identität genutzt werden. Für die Personalisierung der ersten Anmeldung ist es erforderlich, dass die primäre Identität des Personalisierungsanfragesatzes mit der primären Identität des Profils aus Real-time Customer Data Platform übereinstimmt. Die Identitätszuordnung zwischen anonymen Geräten und bekannten Kunden wird auf dem Hub verarbeitet und anschließend an die Kante projiziert. Wenn also die primäre Identität als Gerätekennung festgelegt ist, gelten bekannte Kundendaten erst dann, wenn nachfolgende Sitzungen, in denen die anonymen und bekannten Profile vereinheitlicht wurden, angewendet werden.
* Die Freigabe von Zielgruppen von Adobe Experience Platform für Adobe Target erfordert die Verwendung von ECID als Identität bei der Verwendung des Zielgruppenfreigabe-Service, wie im Integrationsmuster 3 oben beschrieben.
* Alternative Identitäten können auch verwendet werden, um Experience Platform-Zielgruppen über Audience Manager für Adobe Target freizugeben. Experience Platform aktiviert Zielgruppen für Audience Manager über die folgenden unterstützten Namespaces: IDFA, GAID, AdCloud, Google, ECID, EMAIL_LC_SHA256. Beachten Sie, dass Audience Manager und Target Zielgruppenzugehörigkeiten über die ECID-Identität auflösen. Daher ist die ECID weiterhin für die endgültige Zielgruppenfreigabe für Adobe Target erforderlich.

## Implementierungsschritte

1. [Implementieren Sie Adobe Target](https://experienceleague.adobe.com/docs/target/using/implement-target/implementing-target.html?lang=de) für Ihre Web-Anwendungen oder Mobile Apps
1. [Implementieren Sie Adobe Audience Manager](https://experienceleague.adobe.com/docs/audience-manager/user-guide/implementation-integration-guides/implement-audience-manager.html?lang=de) (optional)
1. [Implementieren Sie Adobe Analytics](https://experienceleague.adobe.com/docs/analytics/implementation/home.html?lang=de) (optional)
1. [Implementieren Sie Experience Platform und das [!UICONTROL Echtzeit-Kundenprofil]](https://experienceleague.adobe.com/docs/platform-learn/getting-started-for-data-architects-and-data-engineers/overview.html?lang=de)
1. Implementieren Sie [Experience Cloud Identity Service](https://experienceleague.adobe.com/docs/id-service/using/implementation/implementation-guides.html?lang=de) oder [Experience Platform Web SDK](https://experienceleague.adobe.com/docs/experience-platform/edge/home.html?lang=de). Experience Platform Web SDK ist für die Echtzeit-Edge-Segmentierung erforderlich, aber nicht für die Freigabe von Streaming- und Batch-Zielgruppen von Real-time Customer Data Platform nach Target. Beachten Sie, dass die Echtzeitsegmentierung über das Mobile SDK und die API derzeit nicht unterstützt wird.
1. [Aktivieren von Adobe Target als Ziel in Real-time Customer Data Platform](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/personalization/adobe-target-connection.html?lang=de) oder für den Ansatz der Zielgruppenfreigabe [Anfordern der Bereitstellung der Zielgruppenfreigabe zwischen Experience Platform und Adobe Target (freigegebene Zielgruppen)](https://www.adobe.com/go/audiences) zur Freigabe von Zielgruppen von Experience Platform für Target.

## Verwandte Dokumentation

### Dokumentation

* [Adobe Target-Verbindung für Real-time Customer Data Platform](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/personalization/adobe-target-connection.html?lang=en)
* [Segmentfreigabe für Experience Platform über Audience Manager und andere Experience Cloud-Lösungen](https://experienceleague.adobe.com/docs/audience-manager/user-guide/implementation-integration-guides/integration-experience-platform/aam-aep-audience-sharing.html?lang=de)
* [Dokumentation zu Experience Platform Web SDK](https://experienceleague.adobe.com/docs/experience-platform/edge/home.html)
* [Dokumentation zu Experience Cloud-ID-Service](https://experienceleague.adobe.com/docs/id-service/using/home.html?lang=de)
* [Überblick über Segmentierung in Experience Platform ](https://experienceleague.adobe.com/docs/experience-platform/segmentation/home.html?lang=de)
* [Streaming-Segmentierung](https://experienceleague.adobe.com/docs/experience-platform/segmentation/api/streaming-segmentation.html?lang=de)
* [Überblick über Experience Platform Segment Builder](https://experienceleague.adobe.com/docs/experience-platform/segmentation/ui/overview.html?lang=de)
* [Audience Manager Source Connector](https://experienceleague.adobe.com/docs/experience-platform/sources/connectors/adobe-applications/audience-manager.html?lang=de)
* [Segmentfreigabe in Adobe Analytics über Adobe Audience Manager](https://experienceleague.adobe.com/docs/analytics/components/segmentation/segmentation-workflow/seg-publish.html?lang=de)
* [Dokumentation zu Experience Platform Tags ](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=de)

### Tutorials

* [Nächste Hit-Personalisierung mit Echtzeit-Kundendatenplattform und Adobe Target](https://experienceleague.adobe.com/docs/platform-learn/tutorials/experience-cloud/next-hit-personalization.html?lang=en)

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
