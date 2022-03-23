---
title: 'Blueprint: Anonyme Zielgruppenaktivierung'
description: Erfahren Sie, wie Sie Zielgruppen basierend auf anonymen und verhaltensbasierten Kundendaten über Web- und Werbekanäle hinweg identifizieren. So erstellen Sie personalisierte und konsistente Echtzeit-Kundenerlebnisse auf allen Geräten.
landing-page-description: Erfahren Sie, wie Sie Zielgruppen basierend auf anonymen und verhaltensbasierten Kundendaten über Web- und Werbekanäle hinweg identifizieren.
solution: Experience Platform, Audience Manager
kt: 7211
thumbnail: null
exl-id: f17599f1-2e75-4cbe-841a-9fd1dae71ada
source-git-commit: 64e7b61c1b4b1d600641fd3299a2b84154873cfb
workflow-type: tm+mt
source-wordcount: '397'
ht-degree: 41%

---

# Blueprint: Anonyme Zielgruppenaktivierung

Die Aktivierung einer anonymen Zielgruppe ist die Möglichkeit, Zielgruppen über Web-, Mobile- und Werbekanäle hinweg auf der Grundlage anonymer Geräte- und Verhaltensdaten anzusprechen und zu personalisieren.

## Anwendungsfälle

* Führen Sie anonyme Targeting- und Personalisierungen für digitale Zielgruppen auf der Website, in der mobilen App oder in unterstützten Werbekanälen durch.
* Optimieren Sie Landingpage- und Vorauthentifizierungserlebnisse basierend auf bekannten Geräte- und Verhaltenseigenschaften.
* Nutzen Sie das Datennetzwerk von Audience Manager-Drittanbietern, um Ihre Zielgruppen für das Targeting weiter zu verfeinern und zu erweitern.


## Programme

* Audience Manager
* Real-time Customer Data Platform

Sowohl Audience Manager als auch Real-time Customer Data Platform können genutzt werden, um anonyme Audience Activationen für Onsite- und Werbeziele zu unterstützen. Beachten Sie, dass Real-time Customer Data Platform nur eine Untergruppe von Werbezielen mit anonymen Geräte-IDs unterstützt, die im [Dokumentation zu Zielen](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/advertising/overview.html?lang=en).

Microsoft Bing, Google DV360 und TradeDesk sind die am häufigsten unterstützten Real-time Customer Data Platform-Werbeziele für anonymes gerätebasiertes Targeting. Darüber hinaus unterstützt Real-time Customer Data Platform zahlreiche bekannte kundenbasierte Ziele, die im [Dokumentation zu Zielen](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/advertising/overview.html?lang=en) und wie in [bekanntes Blueprint zur Kundenaktivierung](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/audience-activation/known-customer-audience-activation/known.html).

## Architektur

<img src="assets/anonymous_activation.svg" alt="Referenzarchitektur für die Blueprint „Anonyme Zielgruppenaktivierung“" style="width:80%; border:1px solid #4a4a4a" />

<br>

## Implementierungsschritte

1. [Implementieren Sie Audience Manager](https://experienceleague.adobe.com/docs/audience-manager/user-guide/implementation-integration-guides/implement-audience-manager.html?lang=de#implementation-integration-guides).
1. Erfassen Sie Daten in Audience Manager.
1. Konfigurieren Sie Signale und Eigenschaften für die Verwendung in Segmentdefinitionen.
1. Erstellen Sie Segmente in Audience Manager.
1. Konfigurieren Sie Ziele in Audience Manager, um Zielgruppen freizugeben.

Informationen zu den Implementierungsschritten von Real-time Customer Data Platform finden Sie im Abschnitt [bekanntes Blueprint zur Kundenaktivierung](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/audience-activation/known-customer-audience-activation/known.html).

## Verwandte Dokumentation

* [Audience Manager](https://experienceleague.adobe.com/docs/audience-manager.html?lang=de)
* [Experience Cloud-[!UICONTROL Zielgruppen]](https://experienceleague.adobe.com/docs/core-services/interface/audiences/audience-library.html?lang=de)
* [Integration von Audience Manager mit Target](https://experienceleague.adobe.com/docs/audience-manager/user-guide/implementation-integration-guides/integration-other-solutions/aam-target-integration.html?lang=de)
* [Segmentfreigabe in Adobe Analytics über Audience Manager](https://experienceleague.adobe.com/docs/analytics/components/segmentation/segmentation-workflow/seg-publish.html?lang=de)
* [Bekanntes Blueprint zur Kundenaktivierung](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/audience-activation/known-customer-audience-activation/known.html).
* [Real-Time Customer Data Platform](https://experienceleague.adobe.com/docs/experience-platform/rtcdp/overview.html)
