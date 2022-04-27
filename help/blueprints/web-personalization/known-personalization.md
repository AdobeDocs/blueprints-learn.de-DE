---
title: Übersicht über die Web-/Mobile-Personalisierung
description: Synchronisieren Sie Web-Personalisierung mit E-Mail und anderen bekannten und anonymen Kanalpersonalisierungen.
landing-page-description: Synchronisieren Sie Web-Personalisierung mit E-Mail und anderen bekannten und anonymen Kanalpersonalisierungen.
solution: Real-time Customer Data Platform, Target, Audience Manager, Analytics, Experience Cloud Services, Data Collection, Experience Platform
kt: 7194thumb-web-personalization-scenario2.jpg
exl-id: 29667c0e-bb79-432e-af3a-45bd0b3b43bb
source-git-commit: b1da29f76b274334ca36d0c144adcb6aa797fc0e
workflow-type: tm+mt
source-wordcount: '1268'
ht-degree: 95%

---


# Web-/Mobile-Personalisierung mit bekannten Kundendaten

## Anwendungsfälle

* Online-Personalisierung mit bekannten Kundendaten
* Landingpage-Optimierung
* Personalisierung basierend auf vorherigen Produkt-/Content-Ansichten, Produkt-/Content-Affinität, Umgebungsattributen und Demografie neben Offline-Daten, wie Transaktionen, Treue- und CRM-Daten und Modellerkenntnissen
* Freigeben und Targeting von in Real-time Customer Data Platform definierten Zielgruppen auf Websites und in Mobile Apps mithilfe von Adobe Target.

## Programme

* [!UICONTROL Real-Time Customer Data Platform]
* Adobe Target
* Adobe Audience Manager (optional): Fügt Zielgruppendaten von Drittanbietern hinzu, kooperationsbasiertes Gerätediagramm
* Adobe Analytics (optional): Fügt die Möglichkeit hinzu, Segmente basierend auf historischen Verhaltensdaten und detaillierter Segmentierung aus Adobe Analytics-Daten aufzubauen

## Integrationsmuster

| Integrationsmuster | Fähigkeit | Voraussetzungen |
|---|---|---|
| Echtzeit-Segmentauswertung im Edge, von Real-time Customer Data Platform für Target freigegeben | <ul><li>Evaluieren von Zielgruppen in Echtzeit im Edge Network zur Personalisierung derselben oder der nächsten Seite.</li><li>Darüber hinaus werden alle im Streaming- oder Batch-Modus ausgewerteten Segmente auch in das Edge-Netzwerk projiziert, damit sie in die Auswertung und Personalisierung von Edge-Segmenten einbezogen werden.</li></ul> | <ul><li>Web/Mobile SDK muss implementiert sein oder die Edge Network Server-API</li><li>Datenstrom muss in Experience Edge bei aktivierter Target- und Experience Platform-Erweiterung konfiguriert werden</li><li>Target-Ziel muss in den Real-time Customer Data Platform-Zielen konfiguriert sein.</li><li>Zur Integration mit Target ist dieselbe IMS-Org wie für die Experience Platform-Instanz erforderlich.</li></ul> |
| Streaming- und Batch-Zielgruppenfreigabe von Real-time Customer Data Platform für Target über den Edge-Ansatz | <ul><li>Freigeben von Streaming- und Batch-Zielgruppen aus Real-time Customer Data Platform für Target über das Edge Network In Echtzeit evaluierte Zielgruppen erfordern die WebSDK- und Edge Network-Implementierung.</li></ul> | <ul><li>Web/Mobile SDK ist nicht erforderlich für die Freigabe von Streaming- und Batch-Zielgruppen für Target. Es ist aber erforderlich, um Edge-Segmente in Echtzeit auszuwerten.</li><li>Bei Verwendung von AT.js wird nur die Profilintegration mit dem ECID-Namespace unterstützt.</li><li>Für die Suche nach benutzerdefinierten Identity-Namespaces in Edge Network ist die WebSDK-Implementierung erforderlich. Außerdem muss jede Identität in der Identity Map als Identität festgelegt sein.</li><li>Target-Ziel muss in den Real-time Customer Data Platform-Zielen konfiguriert sein.</li><li>Zur Integration mit Target ist dieselbe IMS-Org wie für die Experience Platform-Instanz erforderlich.</li></ul> |
| Freigeben von Streaming- und Batch-Zielgruppen aus Real-time Customer Data Platform für Target und Audience Manager über den Zielgruppenfreigabe-Service-Ansatz | <ul><li>Dieses Integrationsmuster kann genutzt werden, wenn eine zusätzliche Anreicherung mit Third-Party-Daten und -Zielgruppen in Audience Manager gewünscht wird.</li></ul> | <ul><li>Web/Mobile SDK ist nicht erforderlich für die Freigabe von Streaming- und Batch-Zielgruppen für Target. Es ist aber erforderlich, um Edge-Segmente in Echtzeit auszuwerten.</li><li>Bei Verwendung von AT.js wird nur die Profilintegration mit dem ECID-Namespace unterstützt.</li><li>Für die Suche nach benutzerdefinierten Identity-Namespaces in Edge Network ist die WebSDK-Implementierung erforderlich. Außerdem muss jede Identität in der Identity Map als Identität festgelegt sein.</li><li>Die Zielgruppenprognose per Audience Sharing Service muss bereitgestellt werden.</li><li>Target-Ziel muss in den Real-time Customer Data Platform-Zielen konfiguriert sein.</li><li>Zur Integration mit Target ist dieselbe IMS-Org wie für die Experience Platform-Instanz erforderlich.</li></ul> |

## Echtzeit-, Streaming- und Batch-Zielgruppenfreigabe für Adobe Target

Architektur

<img src="assets/RTCDP+Target.png" alt="Referenzarchitektur für die Blueprint „Online-/Offline-Web-Personalisierung“" style="width:90%; border:1px solid #4a4a4a" />

Sequenzdetails

<img src="assets/RTCDP+Target_flow.png" alt="Referenzarchitektur für die Blueprint „Online-/Offline-Web-Personalisierung“" style="width:90%; border:1px solid #4a4a4a" />

Übersicht – Architektur

<img src="assets/personalization_with_apps.png" alt="Referenzarchitektur für die Blueprint „Online-/Offline-Web-Personalisierung“" style="width:90%; border:1px solid #4a4a4a"/>

## Implementierungsmuster

Die Personalisierung bekannter Kunden wird über verschiedene Implementierungsverfahren unterstützt.

### Implementierungsmuster 1 - Edge-Netzwerk mit Web/Mobile SDK oder Edge Network API (empfohlener Ansatz)

* Verwendung von Edge Network mit dem Web/Mobile SDK. Für die Edge-Echtzeit-Segmentierung ist das Implementierungsverfahren mit Web/Mobile SDKs oder der Edge-API erforderlich.
* [Weitere Informationen finden Sie in der Blueprint „Experience Platform Web and Mobile SDK“](../data-ingestion/websdk.md) für die SDK-basierte Implementierung.
* [Siehe Edge Network Server-API](https://experienceleague.adobe.com/docs/experience-platform/edge-network-server-api/overview.html) für eine API-basierte Implementierung von Adobe Target mit Edge Profile.

### Implementierungsmuster 2 – Anwendungsspezifische SDKs

Verwendung herkömmlicher anwendungsspezifischer SDKs (z. B. AT.js und AppMeasurement.js). Die Edge-Echtzeit-Segmentevaluierung wird bei diesem Implementierungsverfahren nicht unterstützt. Doch das Streaming und die Batch-Zielgruppenfreigabe über den Experience Platform-Hub werden durch dieses Implementierungsverfahren unterstützt.

[Weitere Informationen finden Sie im Blueprint für anwendungsspezifische SDKs.](../data-ingestion/appsdk.md)

### Implementierungsschritte

1. [Implementieren Sie Adobe Target](https://experienceleague.adobe.com/docs/target/using/implement-target/implementing-target.html?lang=de) für Ihre Web-Anwendungen oder Mobile Apps
1. [Implementieren Sie Experience Platform und [!UICONTROL Echtzet-Kundenprofil]](https://experienceleague.adobe.com/docs/platform-learn/getting-started-for-data-architects-and-data-engineers/overview.html?lang=de) Stellen Sie sicher, dass erstellte Zielgruppen für Edge aktiviert werden, indem Sie die entsprechenden [Zusammenführungsrichtlinie](https://experienceleague.adobe.com/docs/experience-platform/profile/merge-policies/ui-guide.html?lang=de#create-a-merge-policy) im Edge als aktiv konfigurieren.
1. Implementieren Sie das [Experience Platform Web SDK](https://experienceleague.adobe.com/docs/experience-platform/edge/home.html?lang=de). Experience Platform Web SDK ist für die Echtzeit-Edge-Segmentierung erforderlich, aber nicht für die Freigabe von Streaming- und Batch-Zielgruppen von Real-time Customer Data Platform an Target. Beachten Sie, dass die Unterstützung für die Echtzeit-Segmentierung über Mobile SDK und API derzeit noch nicht verfügbar ist.
1. [Konfigurieren Sie das Edge Network mit einem Edge-Datenstrom](https://experienceleague.adobe.com/docs/experience-platform/edge/fundamentals/datastreams.html?lang=de)
1. [Aktivieren Sie Adobe Target als Ziel in Real-time Customer Data Platform](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/personalization/adobe-target-connection.html?lang=de)
1. (Optional) [Implementieren von Adobe Audience Manager](https://experienceleague.adobe.com/docs/audience-manager/user-guide/implementation-integration-guides/implement-audience-manager.html?lang=de).
1. (Optional) [Fordern Sie die Bereitstellung der Zielgruppenfreigabe zwischen Experience Platform und Adobe Target an (freigegebene Zielgruppen)](https://www.adobe.com/go/audiences), um Zielgruppen in Experience Platform für Target freizugeben.

## Leitlinien

[Beachten Sie die Leitlinien auf der Übersichtsseite zu den Blueprints für die Web- und Mobile-Personalisierung.](overview.md)

## Überlegungen bei der Implementierung

Voraussetzungen für Identitäten

* Jede primäre Identität kann genutzt werden, wenn das oben erläuterte Implementierungsmuster 1 mit Edge Network und WebSDK verwendet wird. Personalisierung beim ersten Login erfordert, dass die in der Personalisierungsanfrage festgelegte primäre Identität mit der primären Identität des Profils in Real-time Customer Data Platform übereinstimmt. Identitäts-Stitching zwischen anonymen Geräten und bekannten Kunden wird im Hub verarbeitet und nachfolgend an das Edge projiziert.
* Die Freigabe von Zielgruppen aus Adobe Experience Platform für Adobe Target erfordert die Verwendung von ECID als Identität, wenn der Zielgruppenfreigabe-Service wie im Nutzungsszenario 3 oben verwendet wird.
* Alternative Identitäten können auch verwendet werden, um Experience Platform-Zielgruppen über Audience Manager für Adobe Target freizugeben. Experience Platform aktiviert Zielgruppen für Audience Manager über die folgenden unterstützten Namespaces: IDFA, GAID, AdCloud, Google, ECID, EMAIL_LC_SHA256. Beachten Sie, dass Audience Manager und Target Zielgruppenzugehörigkeiten über die ECID-Identität auflösen. Daher ist die ECID weiterhin für die endgültige Zielgruppenfreigabe für Adobe Target erforderlich.

## Verwandte Dokumentation

### SDK-Dokumentation

* [Dokumentation zu Experience Platform Web SDK](https://experienceleague.adobe.com/docs/experience-platform/edge/home.html)
* [Dokumentation zu Experience Platform Tags ](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=de)
* [Dokumentation zu Experience Cloud-ID-Service](https://experienceleague.adobe.com/docs/id-service/using/home.html?lang=de)

### Dokumentation zur Verbindung

* [Adobe Target-Verbindung für Real-time Customer Data Platform](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/personalization/adobe-target-connection.html?lang=en)
* [Edge-Datenstrom-Konfiguration](https://experienceleague.adobe.com/docs/experience-platform/edge/fundamentals/datastreams.html)
* [Segmentfreigabe für Experience Platform über Audience Manager und andere Experience Cloud-Lösungen](https://experienceleague.adobe.com/docs/audience-manager/user-guide/implementation-integration-guides/integration-experience-platform/aam-aep-audience-sharing.html?lang=de)

### Dokumentation zur Segmentierung

* [Überblick über Segmentierung in Experience Platform ](https://experienceleague.adobe.com/docs/experience-platform/segmentation/home.html?lang=de)
* [Echtzeit-Segmentierung](https://experienceleague.adobe.com/docs/experience-platform/segmentation/ui/edge-segmentation.html?lang=de)
* [Streaming-Segmentierung](https://experienceleague.adobe.com/docs/experience-platform/segmentation/api/streaming-segmentation.html?lang=de)
* [Segmentfreigabe in Adobe Analytics über Adobe Audience Manager](https://experienceleague.adobe.com/docs/analytics/components/segmentation/segmentation-workflow/seg-publish.html?lang=de)
* [Konfiguration der Zusammenführungsrichtlinie](https://experienceleague.adobe.com/docs/experience-platform/profile/merge-policies/ui-guide.html?lang=en#create-a-merge-policy)

### Tutorials

* [Personalisierung des nächsten Treffers mit Real-Time CDP und Adobe Target](https://experienceleague.adobe.com/docs/platform-learn/tutorials/experience-cloud/next-hit-personalization.html?lang=de)

### Verwandte Blog-Posts

* [Adobe kündigt verbesserte Personalisierung auf derselben Seite mit Adobe Target und Real-time Customer Data Platform an](https://blog.adobe.com/en/publish/2021/10/05/adobe-announces-same-page-enhanced-personalization-with-adobe-target-real-time-customer-data-platform)
* [[!DNL Blueprint for Web Personalization using Adobe Experience Platform Real-Time Customer Profile]](https://medium.com/adobetech/blueprint-for-web-personalization-using-adobe-experience-platform-real-time-customer-profile-fef2ce7a4b2f)
* [[!DNL Adobe Experience Platform’s Identity Service — How to Solve the Customer Identity Conundrum]](https://medium.com/adobetech/adobe-experience-platforms-identity-service-how-to-solve-the-customer-identity-conundrum-f95e22d16ea9)
* [[!DNL Adobe Experience Platform Web SDK for Audience Management]](https://medium.com/adobetech/adobe-experience-platform-web-sdk-for-audience-management-751fa6d063bc)
* [[!DNL Implementing Adobe Experience Platform Real-Time Customer Profile through our “Customer Zero” Program]](https://medium.com/adobetech/implementing-adobe-experience-platform-real-time-customer-profile-through-our-customer-zero-32e7cd952896)
* [[!DNL Segmentation in Seconds: How Adobe Experience Platform Made Real-time Customer Profiles a Reality]](https://medium.com/adobetech/segmentation-in-seconds-how-adobe-experience-platform-made-real-time-customer-profiles-a-reality-a7a8552b0847)
