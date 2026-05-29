---
title: Bekannte Kunden-Personalization mit Target
description: Integrieren Sie RTCDP-Profile und -Zielgruppen mit Adobe Target.
landing-page-description: Integrieren Sie RTCDP-Profile und -Zielgruppen mit Adobe Target.
short-description: Integrieren Sie RTCDP-Profile und -Zielgruppen mit Adobe Target.
solution: Real-Time Customer Data Platform, Target, Experience Platform
kt: 7194
thumbnail: thumb-web-personalization-scenario2.jpg
exl-id: 29667c0e-bb79-432e-af3a-45bd0b3b43bb
TQID: https://experienceleague.adobe.com/1ti2SqfAFOgnKbaJ70xwGI-xHDE1WXJ7-oTStcJJy1E
product_v2: id: e43347a8-f2c5-4aa4-8623-6f13875d7e3aid: edbd1a0e-46c8-49da-8c10-dba9ec80bba9id: fdddec33-c9cb-4459-b8b6-2664395a6f10
feature_v2: id: a37e4ecd-c740-426a-addf-cb1b483c5c5aid: adee20bd-51f4-461d-b9db-d215f8756eebid: ba929a52-9339-4154-9487-317dc875a3c7id: c132d929-fa62-4271-803e-b823be07b914id: c93393a4-e558-47e1-992e-c91ed4d480ceid: daec7ead-f475-492a-a3b3-02ae08565d6f
subfeature_v2: id: cbd4a8d8-97a6-4ac9-b8d6-b6c1f28d3342id: cdd3e38b-fec2-4f39-8b10-83ddaab1ac16id: d1823595-9241-4128-8a33-e4ac3bf08773id: ee602049-8a18-43df-9299-a689a025a371id: fd0ff162-b6d3-4a11-8aeb-e165a01c0f0a
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2: id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87cid: c2be0313-b3ae-45e0-b454-d20bf54b23f2id: cdd65e7e-8839-44a2-bc21-0e03623b5dd1id: e0eb8757-182f-49f3-94a4-1587d16f5094id: e1e0219c-f879-479f-8427-888ed2a6e9c2
source-git-commit: 213e2d7d73d91fa7b487289dfe62685bc32d5029
workflow-type: tm+mt
source-wordcount: 735
ht-degree: 37%

---

# Bekannte Kunden-Personalization mit Target

>[!TIP]
>Diese Blueprint ist auch als Anwendungsfallmuster [ Personalization ](/help/blueprints/use-case-patterns/personalization/audience-sharing-with-target.md).

## Anwendungsfälle

* Online-Personalisierung mit bekannten Kundendaten
* Landingpage-Optimierung
* Personalisierung basierend auf vorherigen Produkt-/Content-Ansichten, Produkt-/Content-Affinität, Umgebungsattributen und Demografie neben Offline-Daten, wie Transaktionen, Treue- und CRM-Daten und Modellerkenntnissen
* Freigeben und Targeting von in Real-time Customer Data Platform definierten Zielgruppen auf Websites und mobilen Apps mit Adobe Target

## Programme

* [!UICONTROL Real-Time Customer Data Platform]
* Adobe Target

### Referenzdokumentation

* [Adobe Target-Verbindung für Real-time Customer Data Platform](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/personalization/adobe-target-connection.html)
* [Edge-Datenstromkonfiguration](https://experienceleague.adobe.com/docs/experience-platform/edge/fundamentals/datastreams.html?lang=de)

## Integrationsmuster

| Integrationsmuster | Fähigkeit | Voraussetzungen |
|--------------------|------------|---------------|
| **Echtzeit-Segmentauswertung auf der Edge, die von Real-time Customer Data Platform an Target freigegeben wurde** | - Auswerten von Zielgruppen in Echtzeit für die Personalisierung derselben oder der nächsten Seite auf der Edge. <br>- Alle Segmente, die im Streaming- oder Batch-Modus ausgewertet werden, werden auch auf die Edge Network projiziert, um sie in die Evaluierung und Personalisierung der Edge-Segmente einzubeziehen. | - Web-/Mobile-SDK muss für die Edge Network-Server-API implementiert werden. <br> - Der Datenstrom muss in Experience Edge mit aktivierter Erweiterung „Target“ und &quot;Experience Platform&quot; konfiguriert werden. <br> - Das Target-Ziel muss in Real-time Customer Data Platform-Zielen konfiguriert werden. <br>- Zur Integration mit Target ist dieselbe IMS-Org wie für die Experience Platform-Instanz erforderlich. |
| **Streaming- und Batch-Zielgruppenfreigabe von Real-time Customer Data Platform zu Target über den Edge-Ansatz** | - Teilen von Streaming- und Batch-Zielgruppen aus Real-time Customer Data Platform an Target über das Edge Network <br>- In Echtzeit ausgewertete Zielgruppen erfordern die Implementierung von Web SDK und Edge Network. | - Die Implementierung von Target über Web/Mobile SDK oder die Edge-API ist nicht erforderlich, um Streaming- und Batch-Zielgruppen von RTCDP für Target freizugeben, sondern ist erforderlich, um die Evaluierung von Edge-Segmenten in Echtzeit zu ermöglichen. <br>- Bei Verwendung von AT.js wird nur die Profilintegration mit dem ECID-Namespace unterstützt. <br>- Für die Suche nach benutzerdefinierten Identity-Namespaces auf der Edge ist die Bereitstellung der Web-SDK/Edge-API erforderlich und jede Identität muss in der Identitätszuordnung als Identität festgelegt werden. <br> - Das Target-Ziel muss in Real-time Customer Data Platform-Zielen konfiguriert werden, nur die standardmäßige Produktions-Sandbox in RTCDP wird unterstützt. <br>- Zur Integration mit Target ist dieselbe IMS-Org wie für die Experience Platform-Instanz erforderlich. |
| **Streaming- und Batch-Zielgruppenfreigabe von der Real-time Customer Data Platform zu Target und Audience Manager über den Audience Sharing Service-Ansatz** | - Dieses Integrationsmuster kann genutzt werden, wenn in Audience Manager eine zusätzliche Anreicherung aus Daten und Zielgruppen von Drittanbietern gewünscht wird. | - Web/Mobile SDK ist nicht erforderlich, um Streaming- und Batch-Zielgruppen für Target freizugeben, sondern ist erforderlich, um die Evaluierung von Edge-Segmenten in Echtzeit zu ermöglichen. <br>- Bei Verwendung von AT.js wird nur die Profilintegration mit dem ECID-Namespace unterstützt. <br>- Für die Suche nach benutzerdefinierten Identity-Namespaces auf der Edge ist die Bereitstellung der Web-SDK/Edge-API erforderlich und jede Identität muss in der Identitätszuordnung als Identität festgelegt werden. <br>- Zielgruppenprojektion über den Audience Sharing-Service muss bereitgestellt werden. <br>- Zur Integration mit Target ist dieselbe IMS-Org wie für die Experience Platform-Instanz erforderlich. <br>- Nur Zielgruppen aus der standardmäßigen Produktions-Sandbox unterstützen den Service „Audience Sharing Core“. |

## Echtzeit-, Streaming- und Batch-Zielgruppenfreigabe für Adobe Target

Architektur

![Referenzarchitektur für den Online-/Offline-Web-Personalization-Blueprint](assets/RTCDP+Target.png)

Sequenzdetails

![Referenzarchitektur für den Online-/Offline-Web-Personalization-Blueprint](assets/RTCDP+Target_flow.png)

Übersicht – Architektur

![Referenzarchitektur für den Online-/Offline-Web-Personalization-Blueprint](assets/personalization_with_apps.png)

## Verwandte Dokumentation

### SDK-Dokumentation

* [Dokumentation zu Experience Platform Web SDK](https://experienceleague.adobe.com/docs/experience-platform/edge/home.html?lang=de)
* [Dokumentation zu Experience Platform Tags](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=de)
* [Dokumentation zum Experience Cloud ID-Service](https://experienceleague.adobe.com/docs/id-service/using/home.html?lang=de)

### Dokumentation zur Segmentierung

* [Übersicht über die Experience Platform-Segmentierung](https://experienceleague.adobe.com/docs/experience-platform/segmentation/home.html?lang=de)
* [Echtzeitsegmentierung](https://experienceleague.adobe.com/docs/experience-platform/segmentation/ui/edge-segmentation.html?lang=de)
* [Streaming-Segmentierung](https://experienceleague.adobe.com/docs/experience-platform/segmentation/api/streaming-segmentation.html?lang=de)
* [Segmentfreigabe in Adobe Analytics über Adobe Audience Manager](https://experienceleague.adobe.com/docs/analytics/components/segmentation/segmentation-workflow/seg-publish.html?lang=de)
* [Konfiguration der Zusammenführungsrichtlinie](https://experienceleague.adobe.com/docs/experience-platform/profile/merge-policies/ui-guide.html?lang=de#create-a-merge-policy)

### Tutorials

* [Next-Hit-Personalisierung mit Real-Time CDP und Adobe Target](https://experienceleague.adobe.com/docs/platform-learn/tutorials/experience-cloud/next-hit-personalization.html?lang=de)
