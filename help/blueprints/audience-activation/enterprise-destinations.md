---
title: 'Blueprint: Zielgruppen- und Profilaktivierung für Datei- und Unternehmens-Streaming-Ziele'
description: Zielgruppen- und Profilaktivierung für Unternehmensziele
solution: Real-time Customer Data Platform
kt: 7475
exl-id: 32133174-eb28-44ce-ab2a-63fcb5b51cb5
source-git-commit: 3425495df36ff8da0f2fd737b35d294ccafe31bd
workflow-type: tm+mt
source-wordcount: '415'
ht-degree: 100%

---

# Blueprint: Zielgruppen- und Profilaktivierung für Datei- und Unternehmens-Streaming-Ziele

Geben Sie Profil- und Zielgruppenänderungen und -ereignisse per Streaming oder Batch aus [!UICONTROL Real-Time Customer Data Platform] in Unternehmensdatenspeichern und -programmen frei. Diese Profil- und Zielgruppenereignisse können verwendet werden, um eine Verkaufs- oder Support-Aktion für den Kunden einzuleiten, z. B. im Anschluss an einen abgebrochenen Anmeldevorgang oder eine Webinar-Registrierung, oder um Unternehmensprogramme mit den neuesten Kundenattributen und Daten aus [!UICONTROL Real-Time Customer Data Platform] zu aktualisieren.

## Anwendungsfälle

* Zielgruppen- und Profilaktivierung für Cloud-Datenspeicherziele oder Streaming-Ziele für das Tracking, die Speicherung, die Analyse und die Aktivierung von Kundendaten und Erkenntnissen.

## Programme

* Adobe Experience Platform  Activation

## Architektur

<img src="assets/enterprise_destination_activation.svg" alt="Referenzarchitektur für das Unternehmensaktivierungs-Szenario" style="width:90%; border:1px solid #4a4a4a" />


## Leitlinien

[Beachten Sie die Leitlinien auf der Übersichtsseite zur Zielgruppen- und Profilaktivierung.](overview.md)

## Implementierungsschritte

1. [Erstellen Sie Schemas](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2021.1.xdm) für die zu erfassenden Daten.
1. [Erstellen Sie Datensätze](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-ingestion/create-datasets-and-ingest-data.html?lang=de) für die zu erfassenden Daten.
1. [Konfigurieren Sie die korrekten Identitäten und Identitäts-Namespaces](https://experienceleague.adobe.com/docs/platform-learn/tutorials/identities/label-ingest-and-verify-identity-data.html?lang=de) im Schema, um sicherzustellen, dass aufgenommene Daten zu einem einheitlichen Profil zusammengefügt werden können.
1. [Aktivieren Sie die Schemas und Datensätze für Profile](https://experienceleague.adobe.com/docs/platform-learn/tutorials/profiles/bring-data-into-the-real-time-customer-profile.html?lang=de).
1. [Aufnehmen der Daten](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2020.1.dataingestion&amp;lang=de) in Experience Platform.
1. [Stellen Sie in [!UICONTROL Real-Time Customer Data Platform] die Segmentfreigabe](https://www.adobe.com/go/audiences) zwischen Experience Platform und Audience Manager für Zielgruppen bereit, die in Experience Platform für die Freigabe an Audience Manager definiert sind.
1. [Erstellen Sie Segmente](https://experienceleague.adobe.com/docs/platform-learn/tutorials/segments/create-segments.html?lang=de) in Experience Platform. Das System stellt automatisch fest, ob das Segment per Batch oder Streaming evaluiert wird.
1. [Konfigurieren Sie Ziele](https://experienceleague.adobe.com/docs/platform-learn/tutorials/destinations/create-destinations-and-activate-data.html?lang=de) für die Freigabe von Profilattributen und Zielgruppenzugehörigkeiten zu gewünschten Zielen.

## Verwandte Dokumentation

* [Dokumentation zu Zielen](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/overview.html?lang=de)
* [Übersicht über Cloud-Speicherplatz-Ziele](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/cloud-storage/overview.html?lang=de#catalog)
* [HTTP-Ziel](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/http-destination.html?lang=de#overview)
* Produktbeschreibung zu [[!UICONTROL Real-Time Customer Data Platform] ](https://helpx.adobe.com/de/legal/product-descriptions/real-time-customer-data-platform.html)
* [Richtlinien für Profile und Segmentierung](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=de)
* [Dokumentation zur Segmentierung](https://experienceleague.adobe.com/docs/experience-platform/segmentation/api/streaming-segmentation.html?lang=de)

## Verwandte Videos und Tutorials

* Überblick über [[!UICONTROL Real-Time Customer Data Platform] ](https://experienceleague.adobe.com/docs/platform-learn/tutorials/application-services/rtcdp/understanding-the-real-time-customer-data-platform.html?lang=de)
* [Demo zu [!UICONTROL Real-Time Customer Data Platform]](https://experienceleague.adobe.com/docs/platform-learn/tutorials/application-services/rtcdp/demo.html?lang=de)
* [Erstellen von Segmenten](https://experienceleague.adobe.com/docs/platform-learn/tutorials/segments/create-segments.html)
