---
title: 'Blueprint: Datenanalyse und Datenintelligenz'
description: Diese Blueprint zeigt, wie in Adobe Experience Platform sondierende Abfragen sowie Analysen der Daten im Data Lake ausgeführt werden.
solution: Experience Platform
kt: 7207
thumbnail: null
exl-id: a972ea56-d1c8-45da-9044-ed31222a2441
source-git-commit: 4eb6100fa29eac9426fd03ccceadc0a64f1d4b8f
workflow-type: tm+mt
source-wordcount: '337'
ht-degree: 100%

---

# Blueprint: Datenanalyse und Datenintelligenz

„Datenanalyse und Datenintelligenz“ zeigt, wie in Adobe Experience Platform sondierende Abfragen sowie Analysen der Daten im Data Lake ausgeführt werden.

Der [!UICONTROL Abfrage-Service] von Experience Platform ermöglicht die Ausführung von SQL-Abfragen auf Daten. [!UICONTROL Data Science Workspace] ermöglicht die Anwendung von Datensondierung, Datenanalysen und ML-Abläufen auf Daten.

Zusätzlich ermöglicht Experience Platform Verbindungen mit SQL-Clients von Drittanbietern, Schnittstellen und Business-Intelligence-Tools (BI), über die mit dem [!DNL PostgreSQL]-Protokoll direkt eine Verbindung mit den Daten hergestellt sowie auf diese zugegriffen werden kann.

Es gibt einige Leitlinien für die maximale Wartezeit bei Abfragen und die Datenmenge, die im Abfrageresultat enthalten ist, wie in den Blueprint-Details bereits erläutert wurde.

## Anwendungsfälle

* Interaktive Abfrage und Sammlung von Daten
* Zeilen- und Spaltenzugriff auf aufgenommene Daten zur Erkundung und Validierung
* Dashboarding und Visualisierung von Daten über Business-Intelligence-Tools

## Programme

* Adobe Experience Platform 

## Architektur

<img src="assets/data_exploration.svg" alt="Referenzarchitektur für Blueprint „Datenuntersuchung und Reporting in Unternehmen“" style="width:90%; border:1px solid #4a4a4a" />

## Leitlinien

Beachten Sie die Produktdokumentation zum Abfrage-Service für Details zu Best Practices und Leitlinien.
[Anleitung für den Abfrage-Service](https://experienceleague.adobe.com/docs/experience-platform/query/best-practices/writing-queries.html?lang=de#best-practices)

## Implementierungsschritte

1. [Erstellen Sie Schemas](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2021.1.xdm) für die zu erfassenden Daten.
1. [Erstellen Sie Datensätze](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-ingestion/create-datasets-and-ingest-data.html?lang=de) für die zu erfassenden Daten.
1. [Aufnehmen der Daten](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2020.1.dataingestion&amp;lang=de) in Experience Platform.
1. Bestätigen Sie, dass die Daten für den [[!UICONTROL Abfrage-Service]](https://experienceleague.adobe.com/docs/platform-learn/tutorials/queries/explore-data.html?lang=de) und [[!UICONTROL Data Science Workspace]](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-science-workspace/load-data-in-jupyterlab-notebooks.html?lang=de) für Rohzugriff und -abfrage verfügbar sind.
1. [Verbinden Sie Business-Intelligence-Tools und SQL-Clients für Visualisierung, Datenabfrage und Erkundung mit dem [!UICONTROL Abfrage-Service]](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2021.1.qsvc.dash).

## Verwandte Dokumentation

* [Produktbeschreibung zu Adobe Experience Platform Intelligence](https://helpx.adobe.com/de/legal/product-descriptions/adobe-experience-platform-intelligence---product-description.html)
* Dokumentation zum [[!UICONTROL Abfrage-Service]](https://experienceleague.adobe.com/docs/experience-platform/query/home.html?lang=de)
