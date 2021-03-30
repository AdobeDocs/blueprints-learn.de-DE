---
title: Datenaufbereitung und Ingestion - Blueprint
description: Dieser Entwurf zeigt alle Methoden, mit denen Daten in Adobe Experience Platform erfasst und vorbereitet werden können.
solution: Experience Platform, Data Collection
kt: 7204
thumbnail: null
translation-type: tm+mt
source-git-commit: e1a9881996a181310bdc32cb083e4c5654139bf0
workflow-type: tm+mt
source-wordcount: '666'
ht-degree: 0%

---


# Datenaufbereitung und Ingestion - Blueprint

Datenaufbereitung und Ingestion Blueprint umfassen alle Methoden, mit denen Daten in Adobe Experience Platform vorbereitet und aufgenommen werden können.

Die Datenvorbereitung umfasst die Zuordnung von Quelldaten zum Experience Data Model (XDM)-Schema. Dazu gehören auch die Durchführung von Datentransformationen, einschließlich Datumsformatierung, Feldteilungs-/Verkettungs-/Konvertierungen und das Verbinden/Zusammenführen/erneute Keying von Datensätzen. Die Datenvorbereitung hilft bei der Vereinheitlichung von Kundendaten, um eine aggregierte/gefilterte Analyse bereitzustellen, einschließlich Berichte oder der Vorbereitung von Daten für die Zusammenstellung/Datenwissenschaft/Aktivierung von Profilen.

## Architektur

<img src="assets/dataingest.svg" alt="Referenzarchitektur für das Datenaufbereitungs- und -aufbereitungs-Blueprint" style="border:1px solid #4a4a4a" />

## Datenaufnahmemethoden

| Ingestion | Beschreibung |
|------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Web/Mobile SDK | Latenz:<ul><li>Echtzeit - gleiche Seitenerfassung mit Edge Network</li><li>Streaming-Erfassung auf Profil ca. 1 Minute</li><li>Streaming der Erfassung zum Datensee (Mikrostapel ca. 15 Minuten)</ul>Dokumentation: <ul><li>[Web SDK](https://experienceleague.corp.adobe.com/docs/web-sdk.html)</li><li>[Mobile SDK](https://experienceleague.adobe.com/docs/mobile.html?lang=en)</li></ul> |
| Streaming-Quellen | Latenz:<ul><li>Echtzeit - gleiche Seitenerfassung mit Edge Network</li><li>Streaming-Erfassung auf Profil ca. 1 Minute</li><li>Streaming der Erfassung zum Datensee (Mikrostapel ca. 15 Minuten)</li></ul>[Dokumentation](https://experienceleague.adobe.com/docs/experience-platform/sources/home.html?lang=en#connectors) |
| Streaming-API | Latenz:<ul><li>Echtzeit - gleiche Seitenerfassung mit Edge Network</li><li>Streaming-Erfassung auf Profil ca. 1 Minute</li><li>Streaming der Erfassung zum Datensee (Mikrostapel ca. 15 Minuten)</li><li>7 GB/Stunde</li></ul>[Dokumentation](https://experienceleague.adobe.com/docs/experience-platform/ingestion/streaming/overview.html?lang=en#what-can-you-do-with-streaming-ingestion%3F) |
| ETL-Tooling | Verwenden Sie ETL-Tools, um Unternehmensdaten zu ändern und zu transformieren, bevor sie in Experience Platformen aufgenommen werden.<br><br>Latenz:<ul><li>Die Zeitdauer hängt von der externen ETL-Tool-Planung ab, dann gelten die standardmäßigen Erfassungsgarantien basierend auf der für die Erfassung verwendeten Methode.</li></ul> |
| Stapelquellen | Geplanter Abruf aus Quellen<br>Latenz: ~ 200 GB/h<br><br>[Dokumentation](https://experienceleague.adobe.com/docs/experience-platform/sources/home.html?lang=en#connectors)<br>[Tutorials](https://experienceleague.adobe.com/docs/platform-learn/tutorials/sources/overview.html) |
| Stapel-API | Latenz:<ul><li>Die Stapelverarbeitung zum Profil je nach Größe und Traffic lädt ca. 45 Minuten</li><li>Stapelverarbeitung zum Datensee abhängig von Größe und Traffic-Lasten</li></ul>[Dokumentation](https://experienceleague.adobe.com/docs/experience-platform/ingestion/batch/overview.html?lang=en#batch) |
| Adobe Application Connectors | Daten aus Adobe Experience Cloud-Anwendungen automatisch erfassen<ul><li>Adobe Analytics: [Dokumentation](https://experienceleague.adobe.com/docs/experience-platform/sources/connectors/adobe-applications/analytics.html?lang=en#connectors) und [Videolehrgang](https://experienceleague.adobe.com/docs/platform-learn/tutorials/sources/ingest-data-from-adobe-analytics.html)</li><li>Audience Manager: [Dokumentation](https://experienceleague.adobe.com/docs/experience-platform/sources/connectors/adobe-applications/audience-manager.html?lang=en#connectors) und [Videolehrgang](https://experienceleague.adobe.com/docs/platform-learn/tutorials/sources/ingest-data-from-aam.html)</li></ul> |


## Datenaufbereitungsmethoden

| Methoden der Datenaufbereitung | Beschreibung |
|------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Data Science Workspace - Datenvorbereitung | Modellgesteuerte Transformation, skriptgesteuerte Transformation.<br>[Dokumentation](https://experienceleague.adobe.com/docs/experience-platform/data-science-workspace/home.html?lang=en) |
>[!NOTE]
>
>| Externes ETL-Tool ([!DNL Snaplogic], [!DNL Mulesoft], [!DNL Informatica] usw.) | Durchführen komplexer Transformationen in der ETL-Tooling und Verwenden von Standard-Experience Platform-Source-APIs oder Connectors zum Erfassen der resultierenden Daten.                                                                                                                                                               |

| Abfrage Service - Data Prep                                  | Verbinden, Teilen, Zusammenführen, Transformieren, Abfrage und Filtern von Daten in einem neuen Datensatz. Tabelle als Auswahl erstellen (CTAS) <br>[Dokumentation](https://experienceleague.adobe.com/docs/experience-platform/query/home.html?lang=en#sql)                                                                       |
| XDM Mapper- und Data Prep-Funktionen (Streaming und Batch)     | Ordnen Sie Quellattribute im CSV- oder JSON-Format während der Experience Platform XDM-Attributen zu.<br>Funktionen auf Daten während der Erfassung berechnen; d. h. Datenformatierung, Aufteilung, Verkettung usw.<br>[Dokumentation](https://experienceleague.adobe.com/docs/experience-platform/data-prep/home.html?lang=en) |

## Verwandte Blog-Beiträge

* [Nutzung externer Datenplattformen in der Adobe Experience Platform-Journey Orchestration](https://medium.com/adobetech/leveraging-external-data-platforms-in-adobe-experience-platform-journey-orchestration-54fc6134fe17?source=your_stories_page-------------------------------------)
* [Hochdurchsatz-Ingestion mit Iceberg](https://medium.com/adobetech/high-throughput-ingestion-with-iceberg-ccf7877a413f?source=your_stories_page-------------------------------------)
* [Abfrage Service Tricks in Adobe Experience Platform (Schreiben von Abfragen und Speichern von abgeleiteten Datensätzen)](https://medium.com/adobetech/query-service-tricks-in-adobe-experience-platform-writing-queries-and-storing-derived-datasets-eaee0d6d683e?source=your_stories_page-------------------------------------)
* [Einblick in das Experience Data Model von Adobe Experience Platform, um die Leistung des Echtzeit-Kundendiensts besser zu verstehen](https://medium.com/adobetech/digging-into-adobe-experience-platforms-experience-data-model-to-more-fully-understand-the-power-3e109271e04f?source=your_stories_page-------------------------------------)
* [Einführung zur Analyse von Sondierungsdaten über Adobe Experience Platform](https://medium.com/adobetech/an-introductory-look-at-exploratory-data-analysis-on-adobe-experience-platform-1bfce7501d9a?source=your_stories_page-------------------------------------)
* [Modellieren von XDM-Daten für Datenwissenschaften im Maßstab unter Adobe Experience Platform](https://medium.com/adobetech/modeling-xdm-data-for-data-science-at-scale-on-adobe-experience-platform-222bb2a6dbf7?source=your_stories_page-------------------------------------)

