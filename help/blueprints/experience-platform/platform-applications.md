---
title: Architekturdiagramme für Experience Platform (AEP) und Anwendungen
description: Zeigen Sie Architekturdiagramme an, die zeigen, wie Adobe Experience Platform (AEP) mit anderen Experience Cloud-Anwendungen und Anwendungs-Services in Beziehung steht.
solution: Experience Platform, Campaign, Analytics, Target, Customer Journey Analytics, Journey Orchestration, Real-Time Customer Data Platform
kt: 7199
thumbnail: null
exl-id: 9b12cd7a-5e5f-443a-91a1-44273cdabc2d
source-git-commit: 495a2480828e2c6b4caa41226f4fe67437b081c1
workflow-type: tm+mt
source-wordcount: '551'
ht-degree: 10%

---

# Architekturdiagramme für Adobe Experience Platform und Programme

Diese Architekturdiagramme zeigen, wie Experience Platform (AEP) mit anderen Experience Cloud-Anwendungen und Anwendungs-Services in Beziehung steht.

>[!MORELIKETHIS]
>
>[Integrationskonfigurationen für Experience Cloud-Anwendungsintegrationen](https://experienceleague.adobe.com/docs/integrations-learn/experience-cloud/overview.html?lang=en).


## Architekturdiagramm

Dieses Architekturdiagramm zeigt, wie Adobe Experience Platform mit Programmen und Programm-Services von Adobe Experience Cloud zusammenarbeitet.

<img src="assets/aep+apps.svg" alt="Experience Platform und Programme" style="border:1px solid #4a4a4a; width:90%; margin-bottom: 15px;" class="modal-image" />

## Übersichtsdiagramm

<img src="assets/aep+apps_overview.svg" alt="Experience Platform und Programme" style="border:1px solid #4a4a4a; width:90%; margin-bottom: 15px;" class="modal-image" />

## Detailliertes Architekturdiagramm

<img src="assets/aep+apps_detailed.svg" alt="Experience Platform und Programme" style="border:1px solid #4a4a4a; width:90%; margin-bottom: 15px;" class="modal-image" />

>[!VIDEO](https://video.tv.adobe.com/v/32456/?quality=12&learn=on)

## Integration von AEP- und Experience Cloud-Anwendungen

| Programm | Von Experience Platform zum Programm | Vom Programm zu Experience Platform |
|------------------------------|-----------------------------------|-----------------------------------|
| **Ad Cloud** | - In Real-time Customer Data Platform definierte Zielgruppen können zur Zielgruppenbestimmung über Audience Manager für Ad Cloud freigegeben werden. | - Keine aktuelle Integration |
| **Analytics** | - Über das Web/Mobile SDK erfasste Daten können an Adobe Analytics weitergeleitet werden. | - Von Analytics erfasste Daten können an den Data Lake und den Profilspeicher von Experience Platform gesendet werden. [Analytics Data Connector](https://experienceleague.adobe.com/docs/experience-platform/sources/connectors/adobe-applications/analytics.html?lang=de) |
| **Audience Manager** | - In Real-time Customer Data Platform definierte Zielgruppen können zur Aktivierung für Drittanbieter-Cookie-Ziele an Audience Manager freigegeben werden. | - Daten, die zusammen mit der Zielgruppenzugehörigkeit von Audience Manager erfasst und ausgewertet werden, können an den Data Lake und den Profilspeicher von Experience Platform weitergegeben werden. [Audience Manager Source Connector](https://experienceleague.adobe.com/docs/experience-platform/sources/connectors/adobe-applications/audience-manager.html?lang=de) |
| **Adobe Campaign** | - In Real-time Customer Data Platform definierte Zielgruppen können für Campaign Classic freigegeben werden, um Kampagnen zu initiieren. | - Von Campaign erfasste Interaktions- und Kampagnendaten können in Experience Platform aufgenommen werden, um sie bei der Zielgruppenerstellung, in Customer Journey Analytics und im Abfrage-Service weiter zu verwenden. |
| **Campaign Standard** | - In Real-time Customer Data Platform definierte Zielgruppen können für Campaign Standard freigegeben werden, um Kampagnen zu initiieren. | - Von Campaign erfasste Interaktions- und Kampagnendaten können zur weiteren Verwendung in Experience Platform aufgenommen werden. |
| **Customer Journey Analytics** | - Erfasste und in den Data Lake von Experience Platform aufgenommene Daten stehen zur Verarbeitung in Customer Journey Analytics zur Verfügung. <br> - Profil- und Zielgruppendaten aus Real-time Customer Data Platform können in CJA aufgenommen werden. Integration von [RTCDP in CJA](https://experienceleague.adobe.com/docs/analytics-platform/using/cja-usecases/ingest-aep-segments.html?lang=de) | - Erstellen Sie Zielgruppen in CJA und geben Sie Zielgruppenergebnisse für die Real-time Customer Data Platform frei. [Veröffentlichung von CJA-Zielgruppen](https://experienceleague.adobe.com/docs/analytics-platform/using/cja-components/audiences/publish.html?lang=de) |
| **Experience Manager** | - Auf das Experience Platform-Profil kann Server-seitig zugegriffen werden, um personalisierte Erlebnisse in Experience Manager zu ermöglichen. | - Keine aktuelle Integration, Interaktionen, die auf Experience Manager-Sites durchgeführt werden, werden über das Experience Platform Web und Mobile SDK erfasst. |
| **Journey Optimizer** | - In Experience Platform aufgenommene Datenereignisse und Profile werden Journey Optimizer zur Verfügung gestellt. | - Von Journey Optimizer erzeugte Interaktions- und Kampagnendaten werden zur weiteren Verwendung in Experience Platform erfasst. |
| **Adobe Commerce** | - In Real-time Customer Data Platform erstellte Profile und Zielgruppen können für die Personalisierung in Adobe Commerce verwendet werden. | - Native Daten von Adobe Commerce können über einen Adobe Commerce-Quell-Connector an Experience Platform gesendet werden. |
| **Marketo** | - In Real-time Customer Data Platform definierte Zielgruppen können für Marketo freigegeben werden, um Kampagnen zu initiieren und Objekte zu aktualisieren. | - Marketo-Konten, -Kontakte und -Kampagnendaten werden zur weiteren Analyse in Experience Platform aufgenommen. [Marketo Engage-Connector](https://experienceleague.adobe.com/docs/experience-platform/sources/connectors/adobe-applications/marketo/marketo.html?lang=de) |
| **Real-Time CDP** | - In Experience Platform aufgenommene Daten sind die Quelle für Echtzeit-Kundenprofile, die die Echtzeit-Kundendatenplattform unterstützen. | - Zielgruppen- und Profilmetriken werden zur Einsichtnahme an den Data Lake von Experience Platform gesendet. |
| **Target** | - Zielgruppen und Profilattribute von Real-time Customer Data Platform können zur Personalisierung für Target freigegeben werden. | - Daten, die für Target-Erlebnisse erfasst wurden, können zur Zielgruppenerstellung und -analyse an Experience Platform gesendet werden. |
