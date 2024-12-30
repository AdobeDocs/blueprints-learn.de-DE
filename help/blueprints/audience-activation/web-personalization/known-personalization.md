---
title: Übersicht über Web/Mobile Personalization - Adobe Target und RTCDP
description: Synchronisieren Sie Web-Personalisierung mit E-Mail und anderen bekannten und anonymen Kanalpersonalisierungen.
landing-page-description: Synchronisieren Sie Web-Personalisierung mit E-Mail und anderen bekannten und anonymen Kanalpersonalisierungen.
short-description: Synchronisieren Sie Web-Personalisierung mit E-Mail und anderen bekannten und anonymen Kanalpersonalisierungen.
solution: Real-Time Customer Data Platform, Target, Audience Manager, Analytics, Experience Cloud Services, Data Collection, Experience Platform
kt: 7194
thumbnail: thumb-web-personalization-scenario2.jpg
exl-id: 29667c0e-bb79-432e-af3a-45bd0b3b43bb
source-git-commit: 845655a275cdb6d4a9cd397ec7c3515cbf02d321
workflow-type: tm+mt
source-wordcount: '891'
ht-degree: 79%

---


# Web/Mobile Personalization mit Blueprint für bekannte Kundendaten

## Anwendungsfälle

* Online-Personalisierung mit bekannten Kundendaten
* Landingpage-Optimierung
* Personalisierung basierend auf vorherigen Produkt-/Content-Ansichten, Produkt-/Content-Affinität, Umgebungsattributen und Demografie neben Offline-Daten, wie Transaktionen, Treue- und CRM-Daten und Modellerkenntnissen
* Freigeben und Targeting von in Real-time Customer Data Platform definierten Zielgruppen auf Websites und in Mobile Apps mithilfe von Adobe Target.

## Programme

* [!UICONTROL Real-Time Customer Data Platform]
* Adobe Target
* Adobe Audience Manager (optional): Fügt Third-Party-Zielgruppendaten hinzu
* Adobe Analytics oder Customer Journey Analytics (optional): ermöglicht die Erstellung von granularen Segmenten anhand von historischen Kunden- und Verhaltensdaten

### Referenzdokumentation

* [Adobe Target-Verbindung für Real-time Customer Data Platform](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/personalization/adobe-target-connection.html)
* [Edge-Datenstrom-Konfiguration](https://experienceleague.adobe.com/docs/experience-platform/edge/fundamentals/datastreams.html?lang=de)
* [Segmentfreigabe für Experience Platform über Audience Manager und andere Experience Cloud-Lösungen](https://experienceleague.adobe.com/docs/audience-manager/user-guide/implementation-integration-guides/integration-experience-platform/aam-aep-audience-sharing.html?lang=de)


## Integrationsmuster

| Integrationsmuster | Fähigkeit | Voraussetzungen |
|---|---|---|
| Echtzeit-Segmentauswertung im Edge, von Real-time Customer Data Platform für Target freigegeben | <ul><li>Evaluieren von Zielgruppen in Echtzeit im Edge Network zur Personalisierung derselben oder der nächsten Seite.</li><li>Darüber hinaus werden alle Segmente, die im Streaming- oder Batch-Modus ausgewertet werden, auch an die [!DNL Edge Network] projiziert, um sie in die Evaluierung und Personalisierung der Edge-Segmente einzubeziehen.</li></ul> | <ul><li>Web-/Mobile-SDK muss für die [!DNL Edge Network]-Server-API implementiert werden</li><li>Datenstrom muss in Experience Edge bei aktivierter Target- und Experience Platform-Erweiterung konfiguriert werden.</li><li>Target-Ziel muss in den Real-time Customer Data Platform-Zielen konfiguriert sein.</li><li>Zur Integration mit Target ist dieselbe IMS-Org wie für die Experience Platform-Instanz erforderlich.</li></ul> |
| Streaming- und Batch-Zielgruppenfreigabe von Real-time Customer Data Platform für Target über den Edge-Ansatz | <ul><li>Geben Sie Streaming- und Batch-Zielgruppen von Real-time Customer Data Platform über die [!DNL Edge Network] für Target frei. Zielgruppen, die in Echtzeit ausgewertet werden, erfordern die Implementierung von Web SDK und [!DNL Edge Network].</li></ul> | <ul><li>Web/Mobile SDK oder die Edge API-Implementierung von Target ist nicht erforderlich für die Freigabe von Streaming- und Batch-RTCDP-Zielgruppen für Target. Es ist aber erforderlich, um Edge-Segmente wie oben beschrieben in Echtzeit auszuwerten.</li><li>Bei Verwendung von AT.js wird nur die Profilintegration mit dem ECID-Identity-Namespace unterstützt.</li><li>Für die Suche nach benutzerdefinierten Identity-Namespaces im Edge Network ist die Web SDK/Edge API-Implementierung erforderlich. Außerdem muss jede Identität in der Identity Map als Identität festgelegt sein.</li><li>Das Target-Ziel muss in den Zielen von Real-time Customer Data Platform konfiguriert werden. In Real-time Customer Data Platform wird nur die standardmäßige Produktions-Sandbox unterstützt.</li><li>Zur Integration mit Target ist dieselbe IMS-Org wie für die Experience Platform-Instanz erforderlich.</li></ul> |
| Freigeben von Streaming- und Batch-Zielgruppen aus Real-time Customer Data Platform für Target und Audience Manager über den Zielgruppenfreigabe-Service-Ansatz | <ul><li>Dieses Integrationsmuster kann genutzt werden, wenn eine zusätzliche Anreicherung mit Third-Party-Daten und -Zielgruppen in Audience Manager gewünscht wird.</li></ul> | <ul><li>Web/Mobile SDK ist nicht erforderlich für die Freigabe von Streaming- und Batch-Zielgruppen für Target. Es ist aber erforderlich, um Edge-Segmente in Echtzeit auszuwerten.</li><li>Bei Verwendung von AT.js wird nur die Profilintegration mit dem ECID-Identity-Namespace unterstützt.</li><li>Für die Suche nach benutzerdefinierten Identity-Namespaces im Edge Network ist die Web SDK/Edge API-Implementierung erforderlich. Außerdem muss jede Identität in der Identity Map als Identität festgelegt sein.</li><li>Die Zielgruppenprognose per Zielgruppenfreigabe-Service muss bereitgestellt werden.</li><li>Zur Integration mit Target ist dieselbe IMS-Org wie für die Experience Platform-Instanz erforderlich.</li><li>Nur Zielgruppen aus der standardmäßigen Produktions-Sandbox unterstützen den zentralen Service zur Zielgruppenfreigabe.</li></ul> |

## Echtzeit-, Streaming- und Batch-Zielgruppenfreigabe für Adobe Target

Architektur

<img src="assets/RTCDP+Target.svg" alt="Referenzarchitektur für die Blueprint „Online-/Offline-Web-Personalisierung“" style="width:90%; border:1px solid #4a4a4a" class="modal-image" />

Sequenzdetails

<img src="assets/RTCDP+Target_flow.svg" alt="Referenzarchitektur für die Blueprint „Online-/Offline-Web-Personalisierung“" style="width:90%; border:1px solid #4a4a4a" class="modal-image" />

Übersicht – Architektur

<img src="assets/personalization_with_apps.svg" alt="Referenzarchitektur für die Blueprint „Online-/Offline-Web-Personalisierung“" style="width:90%; border:1px solid #4a4a4a" class="modal-image" />

## Implementierungsmuster

Die Personalisierung bekannter Kundinnen und Kunden wird über verschiedene Implementierungsverfahren unterstützt.

### Implementierungsmuster 1: [!DNL Edge Network] mit Web/Mobile SDK oder [!DNL Edge Network] API (empfohlener Ansatz)

* Verwenden der [!DNL Edge Network] mit der Web-/Mobile-SDK. Für die Edge-Echtzeit-Segmentierung ist das Implementierungsverfahren mit Web/Mobile SDKs oder der Edge-API erforderlich.
* [ Informationen zur SDK-basierten Implementierung finden Sie ](../../experience-platform/deployment/websdk.md) der Experience Platform-Blueprint für Web und Mobile SDK .
* Zur Verwendung im Mobile SDK muss die [Decisioning-Erweiterung von Adobe Journey Optimizer](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-journey-optimizer-decisioning) im Mobile SDK installiert sein.
* [Siehe die  [!DNL Edge Network] -Server-](https://experienceleague.adobe.com/docs/experience-platform/edge-network-server-api/overview.html?lang=de)) für eine API-basierte Implementierung von Adobe Target mit Edge-Profil.

### Implementierungsmuster 2 – Anwendungsspezifische SDKs

Verwendung herkömmlicher anwendungsspezifischer SDKs (z. B. AT.js und AppMeasurement.js). Die Edge-Echtzeit-Segmentevaluierung wird bei diesem Implementierungsverfahren nicht unterstützt. Doch das Streaming und die Batch-Zielgruppenfreigabe über den Experience Platform-Hub werden durch dieses Implementierungsverfahren unterstützt.

[Weitere Informationen finden Sie in der Dokumentation zum Adobe Target-Connector](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/personalization/adobe-target-connection)
[Siehe programmspezifische SDK-Blueprint](../../experience-platform/deployment/appsdk.md)

## Überlegungen bei der Implementierung

Voraussetzungen für Identitäten

* Jede primäre Identität kann bei der Verwendung des oben beschriebenen Implementierungsmusters 1 mit dem [!DNL Edge Network] und Web SDK genutzt werden. Für die Personalisierung der ersten Anmeldung muss die primäre Identität der Personalisierungsanfrage mit der primären Identität des Profils aus Real-time Customer Data Platform übereinstimmen.

## Verwandte Dokumentation

### SDK-Dokumentation

* [Dokumentation zu Experience Platform Web SDK](https://experienceleague.adobe.com/docs/experience-platform/edge/home.html?lang=de)
* [Dokumentation zu Experience Platform Tags ](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=de)
* [Dokumentation zu Experience Cloud-ID-Service](https://experienceleague.adobe.com/docs/id-service/using/home.html?lang=de)

### Dokumentation zur Segmentierung

* [Überblick über Segmentierung in Experience Platform ](https://experienceleague.adobe.com/docs/experience-platform/segmentation/home.html?lang=de)
* [Echtzeit-Segmentierung](https://experienceleague.adobe.com/docs/experience-platform/segmentation/ui/edge-segmentation.html?lang=de)
* [Streaming-Segmentierung](https://experienceleague.adobe.com/docs/experience-platform/segmentation/api/streaming-segmentation.html?lang=de)
* [Segmentfreigabe in Adobe Analytics über Adobe Audience Manager](https://experienceleague.adobe.com/docs/analytics/components/segmentation/segmentation-workflow/seg-publish.html?lang=de)
* [Konfiguration der Zusammenführungsrichtlinie](https://experienceleague.adobe.com/docs/experience-platform/profile/merge-policies/ui-guide.html?lang=de#create-a-merge-policy)

### Tutorials

* [Personalisierung des nächsten Treffers mit Real-Time CDP und Adobe Target](https://experienceleague.adobe.com/docs/platform-learn/tutorials/experience-cloud/next-hit-personalization.html?lang=de)

### Verwandte Blog-Posts

* [Adobe kündigt verbesserte Personalisierung auf derselben Seite mit Adobe Target und Real-time Customer Data Platform an](https://blog.adobe.com/en/publish/2021/10/05/adobe-announces-same-page-enhanced-personalization-with-adobe-target-real-time-customer-data-platform)
* [[!DNL Blueprint for Web Personalization using Adobe Experience Platform Real-Time Customer Profile]](https://medium.com/adobetech/blueprint-for-web-personalization-using-adobe-experience-platform-real-time-customer-profile-fef2ce7a4b2f)
* [[!DNL Adobe Experience Platform's Identity Service — How to Solve the Customer Identity Conundrum]](https://medium.com/adobetech/adobe-experience-platforms-identity-service-how-to-solve-the-customer-identity-conundrum-f95e22d16ea9)
* [[!DNL Adobe Experience Platform Web SDK for Audience Management]](https://medium.com/adobetech/adobe-experience-platform-web-sdk-for-audience-management-751fa6d063bc)
* [[!DNL Implementing Adobe Experience Platform Real-Time Customer Profile through our "Customer Zero" Program]](https://medium.com/adobetech/implementing-adobe-experience-platform-real-time-customer-profile-through-our-customer-zero-32e7cd952896)
* [[!DNL Segmentation in Seconds: How Adobe Experience Platform Made Real-time Customer Profiles a Reality]](https://medium.com/adobetech/segmentation-in-seconds-how-adobe-experience-platform-made-real-time-customer-profiles-a-reality-a7a8552b0847)
