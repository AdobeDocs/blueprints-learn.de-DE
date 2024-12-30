---
title: 'Blueprint: Zielgruppen- und Profilaktivierung mit Experience Cloud-Programmen'
description: Verwalten Sie Profile und Zielgruppen in Experience Platform und geben Sie sie für Experience Cloud-Programme frei.
solution: Real-Time Customer Data Platform, Target, Audience Manager, Analytics, Experience Cloud Services
kt: 7722
exl-id: f36014e8-170d-47e1-b4ec-10c0ea70612d
source-git-commit: 2dab717d638bdbc0a903861ec743a81f2aed986d
workflow-type: tm+mt
source-wordcount: '799'
ht-degree: 97%

---

# Blueprint: Zielgruppen- und Profilaktivierung mit Experience Cloud-Programmen

Verwalten Sie Profile und Zielgruppen in Experience Platform und geben Sie sie für Experience Cloud-Programme frei. Erstellen Sie umfassende Kundensegmente und Erkenntnisse in Experience Platform und geben Sie sie für Experience Cloud-Programme frei.

Die Aktivierung mithilfe von Experience Cloud-Programmen entspricht in etwa der Blueprint [Aktivierung einer bekannten Kundin/eines bekannten Kunden](known.md).

## Anwendungsfälle

* Personalisierung und Targeting auf allen Kundeninteraktionskanälen, die auf Experience Cloud basieren
* Gemeinsame Nutzung von Zielgruppen- und Profildaten von Experience Platform und Experience Cloud-Programmen
* Erzielen umfassender Erkenntnisse aus kanalübergreifenden Daten, einschließlich Online-Verhaltensdaten und Datenwissenschaftsmodellen, um das Echtzeit-Kundenprofil in Experience Platform anzureichern, das danach für Experience Cloud-Anwendungen freigegeben werden kann.

## Programme

* Adobe Experience Platform
* [!UICONTROL Real-Time Customer Data Platform]
* Experience Platform Activation
* Experience Cloud-Programme
   * Adobe Audience Manager
   * Adobe Target
   * Adobe Campaign
   * Journey Optimizer
   * Marketo Engage
   * Adobe Commerce
   * Customer Journey Analytics

## Architektur

Weitere Architekturdiagramme für Experience Platform-Integrationen mit Experience Cloud-Programmen finden Sie im Abschnitt [Architekturdiagramm zu Experience Platform und Programmen](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/architecture-overview/platform-applications.html?lang=de).

### Zielgruppen- und Profilaktivierung mit Experience Cloud-Programmen

<img src="../experience-platform/assets/aep+apps.svg" alt="Referenzarchitektur für die Zielgruppen- und Profilaktivierung mit Experience Cloud-Programmen" style="width:90%; border:1px solid #4a4a4a"  class="modal-image" />
<br>

## Leitlinien

Weitere Informationen finden Sie [ den Leitplanken auf der Seite Übersicht über Zielgruppe und Profilaktivierung ](overview.md) auf der Seite [Leitplanken für die Bereitstellung](../experience-platform/deployment/guardrails.md).

## Überlegungen bei der Implementierung

* Die Freigabe von Profildaten an Ziele erfordert, dass der spezifische Identitätswert, der vom Ziel in der Ziel-Payload verwendet wird, mit eingeschlossen wird. Jede Identität, die für ein Ziel notwendig ist, muss in Platform aufgenommen und als eine Identität für das [!UICONTROL Echtzeit-Kundenprofil] konfiguriert werden.

### Zielgruppenfreigabe von Real-time Customer Data Platform an Audience Manager

* Weitere Informationen finden Sie in der folgenden Dokumentation. [Segmentfreigabe für Experience Platform über Audience Manager und andere Experience Cloud-Lösungen](https://experienceleague.adobe.com/docs/audience-manager/user-guide/implementation-integration-guides/integration-experience-platform/aam-aep-audience-sharing.html?lang=de).

* Die Zielgruppenzugehörigkeit in RT-CDP wird für Audience Manager per Streaming freigegeben, sobald die Segmentauswertung abgeschlossen ist. Sie wird unabhängig davon, ob die Segmentauswertung im Batch- oder Streaming-Modus erfolgte, in das Echtzeit-Kundenprofil geschrieben.
* Wenn ein qualifiziertes Profil die regionalen Routing-Informationen für zugehörige Profilgeräte enthält, wird die Zielgruppenzugehörigkeit in RTCDP im zugehörigen Audience Manager Edge im Streaming-Modus qualifiziert. Wenn die regionalen Routing-Informationen auf ein Profil mit einem Zeitstempel aus den vergangen 14 Tagen angewendet wurden, wird es beim Streaming im Audience Manager-Edge ausgewertet. Wenn die Profile aus RTCDP keine regionalen Routing-Informationen enthalten oder diese älter als 14 Tage sind, werden die RTCDP-Zielgruppenzugehörigkeiten zur Batch-basierten Auswertung und Aktivierung an den Audience Manager-Hub gesendet.
* Sind regionale Routing-Informationen enthalten, kommen diese Profile für die Edge-Aktivierung infrage und werden innerhalb von Minuten nach der Segmentqualifizierung durch RTCDP aktiviert. Profile, die nicht für die Edge-Aktivierung qualifiziert sind, werden im Audience Manager-Hub qualifiziert. Die Verarbeitung dauert dabei 12 bis 24 Stunden.
* Regionale Routing-Informationen darüber, auf welchem Edge das Audience Manager-Profil gespeichert ist, können in Audience Manager, im Besucher-ID-Service, in Analytics, in Launch oder direkt im Web SDK als separater Profildatensatz mithilfe der XDM-Feldgruppe „Datenerfassung Regionsinformationen“ erfasst und in Experience Platform gesammelt werden. Weitere Informationen finden Sie im [Dokument zu regionalen Informationen](https://experienceleague.adobe.com/docs/id-service/using/reference/regions.html?lang=de).
* In Aktivierungsszenarios, in denen Zielgruppen aus Experience Platform für Audience Manager freigegeben werden, werden die folgenden Identitäten automatisch freigegeben: ECID, IDFA, GAID, gehashte E-Mail-Adressen (EMAIL_LC_SHA256), AdCloud ID. Benutzerdefinierte Namespaces werden derzeit nicht freigegeben.
* Die Zielgruppen aus Experience Platform können über Audience Manager-Ziele freigegeben werden, wenn die erforderlichen Zielidentitäten im [!UICONTROL Echtzeit-Kundenprofil] enthalten sind oder wenn Identitäten im [!UICONTROL Echtzeit-Kundenprofil] mit den erforderlichen Zielidentitäten verbunden werden können, die in Audience Manager verknüpft sind.

### Zielgruppenfreigabe aus Real-time Customer Data Platform für Target

* In der Blueprint [Personalisierung für bekannte Kunden – Target und RTCDP](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/audience-activation/web-personalization/known-personalization.html) finden Sie weitere Informationen zur Freigabe von Profilen und Zielgruppen aus Real-time Customer Data Platform für Target.

### Zielgruppenfreigabe aus Real-time Customer Data Platform für Campaign und Journey Optimizer

* In den [Blueprints zu Customer Journeys](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/b2b-activation/b2bactivation.html?lang=de) finden Sie weitere Informationen zur Freigabe von Profilen und Zielgruppen aus Real-time Customer Data Platform für Campaign und Journey Optimizer.

### Zielgruppenfreigabe von Real-time Customer Data Platform an Marketo Engage

* In den [Blueprints zur B2B-Aktivierung](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/b2b-activation/b2bactivation.html?lang=de) finden Sie weitere Informationen zur Freigabe von Profilen und Zielgruppen in Real-time Customer Data Platform für Marketo Engage.

### Zielgruppenfreigabe in Real-time Customer Data Platform für Customer Journey Analytics

* Weitere Informationen zur Freigabe von Real-time Customer Data Platform-Zielgruppen für Customer Journey Analytics finden Sie [in diesem Abschnitt](https://experienceleague.adobe.com/docs/analytics-platform/using/cja-usecases/ingest-aep-segments.html?lang=de).

## Verwandte Dokumentation

* Produktbeschreibung zu [[!UICONTROL Real-time Customer Data Platform] ](https://helpx.adobe.com/de/legal/product-descriptions/real-time-customer-data-platform.html)
* [Richtlinien für Profile und Segmentierung](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=de)
* [Dokumentation zur Segmentierung](https://experienceleague.adobe.com/docs/experience-platform/segmentation/api/streaming-segmentation.html?lang=de)
* [Dokumentation zu Zielen](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/overview.html?lang=de)

## Verwandte Videos und Tutorials

* Überblick über [[!UICONTROL Real-Time Customer Data Platform] ](https://experienceleague.adobe.com/docs/platform-learn/tutorials/application-services/rtcdp/understanding-the-real-time-customer-data-platform.html?lang=de)
* [Demo zu [!UICONTROL Real-Time Customer Data Platform]](https://experienceleague.adobe.com/docs/platform-learn/tutorials/application-services/rtcdp/demo.html?lang=de)
* [Erstellen von Segmenten](https://experienceleague.adobe.com/docs/platform-learn/tutorials/segments/create-segments.html?lang=de)
