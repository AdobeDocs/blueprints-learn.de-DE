---
title: Web-/Mobile-Personalisierung mit Online- und Offline-Daten
description: Synchronisieren Sie Web-Personalisierung mit E-Mail und anderen bekannten und anonymen Kanalpersonalisierungen.
landing-page-description: Synchronisieren Sie Web-Personalisierung mit E-Mail und anderen bekannten und anonymen Kanalpersonalisierungen.
solution: Experience Platform, Real-time Customer Data Platform, Target, Audience Manager, Analytics, Experience Cloud Services, Data Collection
kt: 7194thumb-web-personalization-scenario2.jpg
exl-id: 29667c0e-bb79-432e-af3a-45bd0b3b43bb
source-git-commit: 0746a479d4e651244995a8c355ed4c58b968f0c1
workflow-type: tm+mt
source-wordcount: '1143'
ht-degree: 63%

---

# Web-/Mobile-Personalisierung mit Online- und Offline-Daten

Synchronisieren Sie Web-Personalisierung mit E-Mail und anderen bekannten und anonymen Kanalpersonalisierungen.

## Anwendungsfälle

* Landingpage-Optimierung
* Verhaltens- und Offline-Profil-Targeting
* Personalisierung basierend auf vorherigen Produkt-/Content-Ansichten, Produkt-/Content-Affinität, Umgebungsattributen, Third-Party-Zielgruppendaten und Offline-Erkenntnissen, wie Transaktionen, Treue- und CRM-Daten und Modellerkenntnissen.
* Freigeben und Targeting von in Real-time Customer Data Platform definierten Zielgruppen für Websites und mobile Apps mithilfe von Adobe Target.

## Programme

* [!UICONTROL Real-Time Customer Data Platform]
* Adobe Target
* Adobe Audience Manager (optional): Fügt Third-Party-Zielgruppendaten, Co-op-basierte Gerätediagramme und die Möglichkeit hinzu, Platform-Segmente in Adobe Analytics und Adobe Analytics-Segmente in Platform zu ermitteln
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
    <th class="tg-y6fn">#</th>
    <th class="tg-f7v4">Integrationsmuster</th>
    <th class="tg-y6fn">Funktion</th>
    <th class="tg-f7v4">Voraussetzungen</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td class="tg-0lax">1</td>
    <td class="tg-73oq"><span style="font-weight:400;font-style:normal">RTCDP-Streaming und Freigabe von Batch-Zielgruppen für Target und Audience Manager über den Audience Sharing Service-Ansatz</span></td>
    <td class="tg-0lax"><span style="font-weight:400;font-style:normal">- Freigeben von Streaming- und Batch-Zielgruppen aus RTCDP für Target und Audience Manager über den Audience Sharing-Dienst. Zielgruppen, die in Echtzeit ausgewertet werden, erfordern die WebSDK- und Echtzeitauswertung der Zielgruppe, wie im Integrationsmuster 3 beschrieben.</span></td>
    <td class="tg-73oq">- Die Zielgruppenprojektion über den Zielgruppen-Sharing-Dienst muss bereitgestellt werden.<br>- Die Integration mit Target erfordert dieselbe IMS-Org wie die Experience Platform-Instanz.<br>- Identität muss in ECID aufgelöst werden, damit sie für Target freigegeben werden kann, damit Maßnahmen ergriffen werden können. AAM verfügt über eine eigene Liste genehmigter Identitäten, die abgeglichen werden sollen<br>- Für diese Integration ist keine WebSDK-Bereitstellung erforderlich.</td>
  </tr>
  <tr>
    <td class="tg-0lax">2</td>
    <td class="tg-73oq">RTCDP-Streaming und Freigabe von Batch-Zielgruppen für Target über den Edge-Ansatz</td>
    <td class="tg-0lax">- Freigeben von Streaming- und Batch-Zielgruppen von RTCDP an Target über das Edge Network. Zielgruppen, die in Echtzeit ausgewertet werden, erfordern die WebSDK- und Echtzeitauswertung der Zielgruppe, wie im Integrationsmuster 3 beschrieben.</td>
    <td class="tg-73oq"><span style="text-decoration:none">- Derzeit in der Beta-Phase</span><br>- Das Target-Ziel muss in den RTCDP-Zielen konfiguriert werden.<br>- Die Integration mit Target erfordert dieselbe IMS-Org wie die Experience Platform-Instanz.<br>WebSDK ist nicht erforderlich. WebSDk und AT.js werden unterstützt. <br>- Bei Verwendung von AT.js wird nur die Profilsuche mit der ECID unterstützt. <br>- Für die Suche nach benutzerdefinierten ID-Namespaces in Edge ist die WebSDK-Bereitstellung erforderlich und jede Identität muss in der Identitätszuordnung als Identität festgelegt werden.</td>
  </tr>
  <tr>
    <td class="tg-0lax">3</td>
    <td class="tg-73oq">Echtzeit-Segmentbewertung der RTCDP-Echtzeit an Edge, die über das Edge-Netzwerk mithilfe des WebSDK für Target freigegeben wurde.</td>
    <td class="tg-0lax">- Bewerten Sie Zielgruppen in Echtzeit für die gleiche oder die nächste Seitenpersonalisierung an Edge.</td>
    <td class="tg-73oq"><span style="text-decoration:none">- Derzeit in der Beta-Phase</span><br>- Das Target-Ziel muss in den RTCDP-Zielen konfiguriert werden.<br>- Die Integration mit Target erfordert dieselbe IMS-Org wie die Experience Platform-Instanz.<br>- WebSDK muss implementiert sein.<br>- Auch über API unterstützt.</td>
  </tr>
</tbody>
</table>


## Architektur

Übersichtsarchitektur

<img src="assets/RTCDP+Target.png" alt="Referenzarchitektur für die Blueprint „Online-/Offline-Web-Personalisierung“" style="width:80%; border:1px solid #4a4a4a" />

Prozessflussarchitektur

<img src="assets/RTCDP+Target_flow.png" alt="Referenzarchitektur für die Blueprint „Online-/Offline-Web-Personalisierung“" style="width:80%; border:1px solid #4a4a4a" />

Detaillierte Architektur

<img src="assets/personalization_with_apps.png" alt="Referenzarchitektur für die Blueprint „Online-/Offline-Web-Personalisierung“" style="width:80%; border:1px solid #4a4a4a"/>

## Leitlinien

[Beachten Sie die Leitlinien auf der Übersichtsseite zu den Blueprints für die Web- und Mobile-Personalisierung.](overview.md)

## Implementierungsmuster

Die Blueprint „Web-/Mobile-Personalisierung“ lässt sich wie folgt implementieren:

1. Verwendung des [!UICONTROL Platform Web SDK] oder [!UICONTROL Platform Mobile SDK] und [!UICONTROL Edge Network].
1. Verwendung herkömmlicher programmspezifischer SDKs (z. B. AppMeasurement.js)

### 1. Herangehensweise für Platform Web/Mobile SDK und Edge

[Weitere Informationen finden Sie in der Blueprint „Experience Platform Web and Mobile SDK“](../data-ingestion/websdk.md)

### 2. Herangehensweise für programmspezifische SDKs

<img src="assets/app_sdk_flow.png" alt="Referenzarchitektur für die Herangehensweise für programmspezifische SDKs" style="width:80%; border:1px solid #4a4a4a" />

## Voraussetzungen für die Implementierung

Voraussetzungen für Identitäten

* Die Freigabe von Zielgruppen aus Adobe Experience Platform für Adobe Target erfordert die Verwendung von ECID als Identität.
* Alternative Identitäten können auch verwendet werden, um Experience Platform-Zielgruppen über Audience Manager für Adobe Target freizugeben. Experience Platform aktiviert Zielgruppen für Audience Manager über die folgenden unterstützten Namespaces: IDFA, GAID, AdCloud, Google, ECID, EMAIL_LC_SHA256. Beachten Sie, dass Audience Manager und Target Zielgruppenzugehörigkeiten über die ECID-Identität auflösen. Daher ist die ECID weiterhin für die endgültige Zielgruppenfreigabe für Adobe Target erforderlich.

| Programm/Service | Erforderliche Bibliothek | Hinweise |
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
1. [Implementieren Sie Experience Platform und das [!UICONTROL Echtzeit-Kundenprofil]](https://experienceleague.adobe.com/docs/platform-learn/getting-started-for-data-architects-and-data-engineers/overview.html?lang=de)
1. Implementieren Sie [Experience Cloud Identity Service](https://experienceleague.adobe.com/docs/id-service/using/implementation/implementation-guides.html?lang=de) oder [Experience Platform Web SDK](https://experienceleague.adobe.com/docs/experience-platform/edge/home.html?lang=de)
1. [Aktivieren von Adobe Target as a destination in Real-time Customer Data Platform](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/personalization/adobe-target-connection.html?lang=en) oder für den Ansatz der Zielgruppenfreigabe [Anfordern der Bereitstellung für Zielgruppenfreigabe zwischen Experience Platform und Adobe Target (freigegebene Zielgruppen)](https://www.adobe.com/go/audiences) , um Zielgruppen von Experience Platform für Target freizugeben.
   >[!NOTE]
   >
   >Bei Verwendung des Zielgruppenfreigabe-Dienstes zwischen RTCDP und Adobe Target müssen Zielgruppen mit der Experience Cloud-ID freigegeben werden und zur gleichen Experience Cloud-Org gehören. Die Unterstützung anderer Identitäten als ECID erfordert die Verwendung von WebSDK und Experience Edge Network.


## Verwandte Dokumentation

* [Segmentfreigabe für Experience Platform über Audience Manager und andere Experience Cloud-Lösungen](https://experienceleague.adobe.com/docs/audience-manager/user-guide/implementation-integration-guides/integration-experience-platform/aam-aep-audience-sharing.html?lang=de)
* [Überblick über Segmentierung in Experience Platform ](https://experienceleague.adobe.com/docs/experience-platform/segmentation/home.html?lang=de)
* [Streaming-Segmentierung](https://experienceleague.adobe.com/docs/experience-platform/segmentation/api/streaming-segmentation.html?lang=de)
* [Adobe Target-Verbindung für Real-time Customer Data Platform](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/personalization/adobe-target-connection.html?lang=en)
* [Überblick über Experience Platform Segment Builder](https://experienceleague.adobe.com/docs/experience-platform/segmentation/ui/overview.html?lang=de)
* [Audience Manager Source Connector](https://experienceleague.adobe.com/docs/experience-platform/sources/connectors/adobe-applications/audience-manager.html?lang=de)
* [Segmentfreigabe in Adobe Analytics über Adobe Audience Manager](https://experienceleague.adobe.com/docs/analytics/components/segmentation/segmentation-workflow/seg-publish.html?lang=de)
* [Dokumentation zu Experience Platform Web SDK](https://experienceleague.adobe.com/docs/experience-platform/edge/home.html)
* [Dokumentation zu Experience Cloud-ID-Service](https://experienceleague.adobe.com/docs/id-service/using/home.html?lang=de)
* [Dokumentation zu Experience Platform Tags ](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=de)

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
