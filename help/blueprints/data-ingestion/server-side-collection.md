---
title: 'Blueprint: Ereignisweiterleitung'
description: Erfasste Daten streamen von [!DNL Experience Platform] SDKs an Ziele
solution: Data Collection
kt: 7202
exl-id: 8d6f0705-628b-44e4-a3fc-da6c5e308a5b
source-git-commit: 72eb4e2ff276279a2fc88ead0b17d77cc8e99b97
workflow-type: tm+mt
source-wordcount: '217'
ht-degree: 55%

---

# Entwurf für die Ereignisweiterleitung

Der Entwurf für die Ereignisweiterleitung zeigt, wie Daten mit Adobe erfasst werden [!DNL Experience Platform] Web- und Mobile-SDKs können von weitergeleitet werden [!DNL Experience Platform] [!DNL Edge Network] zu einem gewünschten Ziel hinzu. Sie können alle mit den SDKs erfassten Rohdaten oder bestimmte Daten basierend auf Ereignissen und Regeln entsprechend der Konfiguration in Tag-Eigenschaften (ehemals Launch) weiterleiten.

## Anwendungsfälle

* Erfassen von Web- oder Mobile-Daten mit einem zentralen Sammlungs-Tag, wodurch weniger Code für Client-Browser und -Mobile-Apps nötig ist. Propagieren der erfassten Daten an verschiedene Endpunkte aus einer zentralen Datenerfassungsquelle.
* Weiterleiten von erfassten Daten an Partnerprogramme oder Datenspeicher-Standorte für den Gewinn von Erkenntnissen und die Erstellung von Programmen anhand der erfassten Daten.

## Programme

* Adobe [!DNL Experience Platform] Datenerfassung

## Architektur

<img src="assets/enterprise_collection.svg" alt="Referenzarchitektur für die Erfassung von Unternehmensdaten" style="width:90%; border:1px solid #4a4a4a" class="modal-image" />

## Verwandte Dokumentation

* [Dokumentation zur Ereignisweiterleitung](https://experienceleague.adobe.com/docs/experience-platform/tags/event-forwarding/overview.html?lang=de)
* [Videos zur Ereignisweiterleitung](https://experienceleague.adobe.com/docs/launch-learn/tutorials/server-side/overview.html?lang=de)
* [Lektion zur Ereignisweiterleitung](https://experienceleague.adobe.com/docs/platform-learn/implement-web-sdk/event-forwarding/setup-event-forwarding.html?lang=de) des Web SDK-Tutorials

## Verwandte Blog-Posts

* [Steigern der Website-Leistung mit Adobe [!DNL Experience Platform] Web SDK und [!DNL Edge Network]](https://medium.com/adobetech/boosting-website-performance-with-adobe-experience-platform-web-sdk-and-edge-network-329fcf70fdf9)
* [Lösen von Implementierungs-Paintpunkten mit Adobe [!DNL Experience Platform] Web SDK und [!DNL Edge Network]](https://medium.com/adobetech/solving-implementation-pain-points-with-adobe-experience-platform-web-sdk-and-edge-network-880b635e6819)
* [Adobe [!DNL Experience Platform] Web SDK für Zielgruppen-Management](https://medium.com/adobetech/adobe-experience-platform-web-sdk-for-audience-management-751fa6d063bc)
* [Adobe [!DNL Experience Platform] Web SDK - Adobe Target](https://medium.com/adobetech/adobe-experience-platform-web-sdk-adobe-target-9b9f621d271)
* [Adobe [!DNL Experience Platform] Web SDK-Migrationsszenarios für Adobe Analytics](https://medium.com/adobetech/adobe-experience-platform-web-sdk-migration-scenarios-for-adobe-analytics-91c255ec82b0)
* [Adobe vereinheitlichen [!DNL Experience Platform] Dienste mit Adobe [!DNL Experience Platform] Web SDK](https://medium.com/adobetech/unify-your-adobe-experience-platform-services-with-adobe-experience-platform-web-sdk-75cf6851a9fc)
* [Beschleunigen der Entwicklung von Mobile Apps mit Adobe [!DNL Experience Platform] Mobile SDK und Launch](https://medium.com/adobetech/accelerate-your-mobile-application-development-with-adobe-experience-platform-mobile-sdk-and-launch-ed023536d611)
* [Vereinfachung von Kunden-Workflows mit Adobe [!DNL Experience Platform] Web SDK](https://medium.com/adobetech/simplifying-customer-workflows-with-adobe-experience-platform-web-sdk-4e54fe134f4a)
