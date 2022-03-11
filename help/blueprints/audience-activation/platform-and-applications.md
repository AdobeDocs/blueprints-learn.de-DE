---
title: 'Blueprint: Zielgruppen- und Profilaktivierung mit Experience Cloud-Programmen'
description: Verwalten Sie Profile und Zielgruppen in Experience Platform und geben Sie sie für Experience Cloud-Programme frei.
solution: Experience Platform, Real-time Customer Data Platform, Target, Audience Manager, Analytics, Experience Cloud Services
kt: 7722
exl-id: f36014e8-170d-47e1-b4ec-10c0ea70612d
source-git-commit: 20dd657a85ffeb8ae2f160855369643c2f2743bb
workflow-type: tm+mt
source-wordcount: '710'
ht-degree: 86%

---

# Blueprint: Zielgruppen- und Profilaktivierung mit Experience Cloud-Programmen

Verwalten Sie Profile und Zielgruppen in Experience Platform und geben Sie sie für Experience Cloud-Programme frei. Erstellen Sie umfassende Kundensegmente und Einblicke in Experience Platform und geben Sie sie für Experience Cloud-Programme frei.

Die Aktivierung mit Experience Cloud-Anwendungen passt sich eng an die [Bekanntes Blueprint zur Kundenaktivierung](known.md).

## Anwendungsfälle

* Personalisierung und Targeting auf allen Kundeninteraktionskanälen, die auf Experience Cloud basieren
* Gemeinsame Nutzung von Zielgruppen- und Profildaten von Experience Platform und Experience Cloud-Programmen

## Programme

* Adobe Experience Platform
* [!UICONTROL Real-Time Customer Data Platform]
* Experience Platform Activation
* Experience Cloud-Programme
   * Adobe Audience Manager
   * Adobe Target
   * Adobe Campaign
   * Journey Optimizer

## Architektur

[Weitere Architekturdiagramme für Experience Platform-Integrationen mit Experience Cloud-Programmen finden Sie im Abschnitt „Architekturdiagramm zu Experience Platform und Programmen“.](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/architecture-overview/platform-applications.html?lang=de)

### Zielgruppen- und Profilaktivierung mit Experience Cloud-Programmen

<img src="../experience-platform/assets/aep+apps_horizontal.svg" alt="Referenzarchitektur für die Zielgruppen- und Profilaktivierung mit Experience Cloud-Programmen" style="width:80%; border:1px solid #4a4a4a" />
<br>

## Leitlinien

Beachten Sie die [Leitlinien auf der Übersichtsseite zur Zielgruppen- und Profilaktivierung](overview.md).

## Überlegungen bei der Implementierung

* Die Freigabe von Profildaten an Ziele erfordert, dass der spezifische Identitätswert, der vom Ziel in der Ziel-Payload verwendet wird, mit eingeschlossen wird. Jede Identität, die für ein Ziel notwendig ist, muss in Platform aufgenommen und als eine Identität für das [!UICONTROL Echtzeit-Kundenprofil] konfiguriert werden.

### Zielgruppenfreigabe von Real-time Customer Data Platform an Audience Manager

* Die Zielgruppenzugehörigkeit aus RT-CDP wird für Audience Manager per Streaming freigegeben, sobald die Segmentauswertung abgeschlossen ist. Sie wird unabhängig davon, ob die Segmentauswertung im Batch- oder Streaming-Modus erfolgte, in das Echtzeit-Kundenprofil geschrieben. Wenn das qualifizierte Profil die regionalen Routing-Informationen für zugehörige Profilgeräte enthält, wird die Zielgruppenzugehörigkeit von RTCDP auf dem zugehörigen Audience Manager Edge im Streaming-Modus qualifiziert. Wenn die regionalen Routing-Informationen auf ein Profil mit einem Zeitstempel aus den vergangen 14 Tagen angewendet wurden, wird es beim Streaming im Audience Manager-Edge ausgewertet. Wenn die Profile aus RTCDP keine regionalen Routing-Informationen enthalten oder diese älter als 14 Tage sind, werden die Profilzugehörigkeiten zur Batch-basierten Auswertung und Aktivierung an den Audience Manager-Hub gesendet. Profile, die für die Edge-Aktivierung infrage kommen, werden innerhalb von Minuten nach der Segmentqualifizierung durch RTCDP aktiviert. Profile, die nicht für die Edge-Aktivierung qualifiziert sind, qualifizieren sich für den Audience Manager-Hub, dabei dauert die Verarbeitung 12 bis 24 Stunden.

* Regionale Routing-Informationen, für die das Audience Manager-Profil auf Edge gespeichert ist, können aus Audience Manager, dem Besucher-ID-Service, Analytics, Launch oder direkt aus dem Web SDK als separater Profildatensatz mit der XDM-Feldgruppe „Datenerfassung Regionsinformationen“ in Experience Platform gesammelt werden.

* In Aktivierungsszenarios, in denen Zielgruppen aus Experience Platform für Audience Manager freigegeben werden, werden die folgenden Identitäten automatisch freigegeben: IDFA, GAID, AdCloud, Google, ECID, EMAIL_LC_SHA256. Benutzerdefinierte Namespaces werden derzeit nicht freigegeben.

* Die Zielgruppen aus Experience Platform können über Audience Manager-Ziele freigegeben werden, wenn die erforderlichen Zielidentitäten im [!UICONTROL Echtzeit-Kundenprofil] enthalten sind oder wenn Identitäten im [!UICONTROL Echtzeit-Kundenprofil] mit den erforderlichen Zielidentitäten verbunden werden können, die in Audience Manager verknüpft sind.

### Zielgruppenfreigabe von Real-time Customer Data Platform an Target

* Siehe [Web-/Mobile-Personalisierung mit Online- und Offline-Daten-Blueprint](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/web-personalization/online-offline.html) für zusätzliche Informationen zur Freigabe von Profilen und Zielgruppen von Real-time Customer Data Platform für Target.

### Zielgruppenfreigabe von Real-time Customer Data Platform für Campaign und Journey Optimizer

* Siehe [Journey-Blueprints für Kunden](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/customer-journeys/overview.html) für weitere Informationen zur Freigabe von Profilen und Audiences von Real-time Customer Data Platform für Campaign und Journey Optimizer.

## Verwandte Dokumentation

* Produktbeschreibung zu [[!UICONTROL Real-Time Customer Data Platform] ](https://helpx.adobe.com/de/legal/product-descriptions/real-time-customer-data-platform.html)
* [Richtlinien für Profile und Segmentierung](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=de)
* [Dokumentation zur Segmentierung](https://experienceleague.adobe.com/docs/experience-platform/segmentation/api/streaming-segmentation.html?lang=de)
* [Dokumentation zu Zielen](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/overview.html?lang=de)

## Verwandte Videos und Tutorials

* Überblick über [[!UICONTROL Real-Time Customer Data Platform] ](https://experienceleague.adobe.com/docs/platform-learn/tutorials/application-services/rtcdp/understanding-the-real-time-customer-data-platform.html?lang=de)
* [Demo zu [!UICONTROL Real-Time Customer Data Platform]](https://experienceleague.adobe.com/docs/platform-learn/tutorials/application-services/rtcdp/demo.html?lang=de)
* [Erstellen von Segmenten](https://experienceleague.adobe.com/docs/platform-learn/tutorials/segments/create-segments.html?lang=de)
