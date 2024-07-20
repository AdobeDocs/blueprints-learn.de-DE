---
title: 'Blueprint: Datenanalyse und Datenintelligenz'
description: Verwenden Sie Adobe [!DNL Experience Platform] (AEM), um eine forschende Abfrage und Analyse der Daten durchzuführen, die im Data Lake vorhanden sind.
solution: Experience Platform
kt: 7207
thumbnail: null
exl-id: a972ea56-d1c8-45da-9044-ed31222a2441
source-git-commit: 7f3bc307f74aa88a7a73f3e50cc48bd16f58b37f
workflow-type: tm+mt
source-wordcount: '223'
ht-degree: 59%

---

# Datenanalyse und intelligente Konzepte

Datenanalyse und Intelligenz beinhalten die Fähigkeit innerhalb von [!DNL Experience Platform], eine forschende Abfrage und Analyse der Daten durchzuführen, die im Data Lake vorhanden sind.

Der [!UICONTROL Abfragedienst ] von [!DNL Experience Platform] ermöglicht die Durchführung von SQL-Abfragen für die Daten.

[!DNL Experience Platform] ermöglicht Verbindungen mit SQL-Clients, Schnittstellen und Business Intelligence-Tools von Drittanbietern, über das [!DNL PostgreSQL] -Protokoll direkt eine Verbindung zu den Daten herzustellen, darauf zuzugreifen und sie abzufragen.[!DNL Experience Platform]

## Anwendungsfälle

* Interaktive Abfrage und Sammlung von Daten
* Zeilen- und Spaltenzugriff auf aufgenommene Daten zur Erkundung und Validierung
* Dashboarding und Visualisierung von Daten über Business-Intelligence-Tools

Weitere häufige Anwendungsfälle für den Abfrage-Service werden hier beschrieben: [Anwendungsfälle für den Abfrage-Service](https://experienceleague.adobe.com/docs/experience-platform/query/use-cases/abandoned-browse.html?lang=de).

## Programme

* Adobe [!DNL Experience Platform]

## Architektur

<img src="assets/data_exploration.svg" alt="Referenzarchitektur für die Blueprint „Datenuntersuchung und Reporting in Unternehmen“" style="width:90%; border:1px solid #4a4a4a" />

## Leitlinien

Beachten Sie die Produktdokumentation zum Abfrage-Service für Details zu Best Practices und Leitlinien.
[Anleitung für den Abfrage-Service](https://experienceleague.adobe.com/docs/experience-platform/query/guardrails.html?lang=de)

## Implementierungsschritte

1. [Erstellen Sie Schemas](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2021.1.xdm&amp;lang=de) für die zu erfassenden Daten.
1. [Erstellen Sie Datensätze](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-ingestion/create-datasets-and-ingest-data.html?lang=de) für die zu erfassenden Daten.
1. [Aufnehmen von Daten](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2020.1.dataingestion&amp;lang=de) in [!DNL Experience Platform].
1. Vergewissern Sie sich, dass die Daten für den [[!UICONTROL Abfrage-Service]](https://experienceleague.adobe.com/docs/platform-learn/tutorials/queries/explore-data.html?lang=de) verfügbar sind.
1. [Verbinden Sie Business-Intelligence-Tools und SQL-Clients für Visualisierung, Datenabfrage und Erkundung mit dem [!UICONTROL Abfrage-Service]](https://experienceleague.adobe.com/docs/experience-platform/query/clients/overview.html?lang=de).

## Verwandte Dokumentation

* [Adobe [!DNL Experience Platform] Intelligence product description](https://helpx.adobe.com/de/legal/product-descriptions/adobe-experience-platform-intelligence---product-description.html)
* Dokumentation zum [[!UICONTROL Abfrage-Service]](https://experienceleague.adobe.com/docs/experience-platform/query/home.html?lang=de)
