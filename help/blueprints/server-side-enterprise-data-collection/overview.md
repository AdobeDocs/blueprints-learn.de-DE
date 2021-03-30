---
title: Blueprint zur serverseitigen Datenerfassung
description: Datenerfassung durch Experience Platform-SDKs an Ziele streamen
solution: Experience Platform, Data Collection
kt: 7202
translation-type: tm+mt
source-git-commit: e1a9881996a181310bdc32cb083e4c5654139bf0
workflow-type: tm+mt
source-wordcount: '299'
ht-degree: 0%

---


# Blueprint zur serverseitigen Datenerfassung

Das serverseitige Enterprise Data Collection-Konzept zeigt, wie mit Adobe Experience Platform Web- und Mobile-SDKs erfasste Daten vom Experience Platform Edge Network an ein gewünschtes Ziel weitergeleitet werden können. Sie können alle Rohdaten weiterleiten, die aus den SDKs oder spezifischen Daten auf der Grundlage der in Experience Platform Launch konfigurierten Ereignis und Regeln erfasst wurden.

## Anwendungsfälle

* Datenerfassung über Web oder Mobilgeräte mit einem einzigen Datenerfassungs-Tag, wodurch die Gewichtung von Code in Client-Browsern und -Apps verringert wird. Propagieren Sie die erfassten Daten an verschiedene Endpunkte für eine einzige Datenquelle der Datenerfassung.
* Weiterleiten erfasster Daten an Partneranwendungen oder Datenerfassungsorte, um Erkenntnisse und Datenspeicherung anhand der erfassten Daten zu erstellen.

## Anwendungen

* Adobe Experience Platform Collection

## Architektur

<img src="assets/entcollect.svg" alt="Referenzarchitektur für die Sammlung von Unternehmensdaten" style="border:1px solid #4a4a4a" />

## Verwandte Dokumentation

[Dokumentation zum Experience Platform Launch-Server](https://experienceleague.adobe.com/docs/launch/using/server-side-info/server-side-overview.html?lang=en#server-side-info)

## Verwandte Blog-Beiträge

* [Verbessern der Website-Performance mit Adobe Experience Platform Web SDK und Edge Network](https://medium.com/adobetech/boosting-website-performance-with-adobe-experience-platform-web-sdk-and-edge-network-329fcf70fdf9)
* [Lösen von Implementierungsproblemen mit Adobe Experience Platform Web SDK und Edge Network](https://medium.com/adobetech/solving-implementation-pain-points-with-adobe-experience-platform-web-sdk-and-edge-network-880b635e6819)
* [Adobe Experience Platform Web SDK for Audience Management](https://medium.com/adobetech/adobe-experience-platform-web-sdk-for-audience-management-751fa6d063bc)
* [Adobe Experience Platform Web SDK - Adobe Target](https://medium.com/adobetech/adobe-experience-platform-web-sdk-adobe-target-9b9f621d271)
* [Adobe Experience Platform Web SDK-Migrationsszenarien für Adobe Analytics](https://medium.com/adobetech/adobe-experience-platform-web-sdk-migration-scenarios-for-adobe-analytics-91c255ec82b0)
* [Einheitliche Adobe Experience Platform-Dienste mit Adobe Experience Platform Web SDK](https://medium.com/adobetech/unify-your-adobe-experience-platform-services-with-adobe-experience-platform-web-sdk-75cf6851a9fc)
* [Beschleunigen Sie die Entwicklung von Mobilanwendungen mit dem Adobe Experience Platform Mobile SDK und dem Start](https://medium.com/adobetech/accelerate-your-mobile-application-development-with-adobe-experience-platform-mobile-sdk-and-launch-ed023536d611)
* [Vereinfachung der Workflows mit dem Adobe Experience Platform Web SDK](https://medium.com/adobetech/simplifying-customer-workflows-with-adobe-experience-platform-web-sdk-4e54fe134f4a)
