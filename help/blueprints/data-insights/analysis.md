---
title: 'Blueprint: Datenanalyse und Datenintelligenz'
description: Diese Blueprint zeigt, wie in Adobe Experience Platform sondierende Abfragen sowie Analysen der Daten im Data Lake ausgeführt werden.
solution: Experience Platform
kt: 7207
thumbnail: null
exl-id: a972ea56-d1c8-45da-9044-ed31222a2441
source-git-commit: b18d491fdefc57762932d1570401b5437bf97c76
workflow-type: ht
source-wordcount: '293'
ht-degree: 100%

---

# Blueprint: Datenanalyse und Datenintelligenz

„Datenanalyse und Datenintelligenz“ zeigt, wie in Adobe Experience Platform sondierende Abfragen sowie Analysen der Daten im Data Lake ausgeführt werden.

Der [!UICONTROL Abfrage-Service] von Experience Platform ermöglicht die Ausführung von SQL-Abfragen auf Daten.

Experience Platform ermöglicht Verbindungen mit SQL-Clients von Drittanbietern, Schnittstellen und Business-Intelligence-Tools (BI), über die mit dem [!DNL PostgreSQL]-Protokoll direkt eine Verbindung mit den Daten in Experience Platform hergestellt sowie auf diese zugegriffen werden kann.

## Anwendungsfälle

* Interaktive Abfrage und Sammlung von Daten
* Zeilen- und Spaltenzugriff auf aufgenommene Daten zur Erkundung und Validierung
* Dashboarding und Visualisierung von Daten über Business-Intelligence-Tools

Weitere häufige Anwendungsfälle für den Abfrage-Service werden hier beschrieben: [Anwendungsfälle für den Abfrage-Service](https://experienceleague.adobe.com/docs/experience-platform/query/use-cases/abandoned-browse.html?lang=de).

## Programme

* Adobe Experience Platform

## Architektur

<img src="assets/data_exploration.svg" alt="Referenzarchitektur für die Blueprint „Datenuntersuchung und Reporting in Unternehmen“" style="width:90%; border:1px solid #4a4a4a" />

## Leitlinien

Beachten Sie die Produktdokumentation zum Abfrage-Service für Details zu Best Practices und Leitlinien.
[Anleitung für den Abfrage-Service](https://experienceleague.adobe.com/docs/experience-platform/query/guardrails.html?lang=de)

## Implementierungsschritte

1. [Erstellen Sie Schemas](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2021.1.xdm&amp;lang=de) für die zu erfassenden Daten.
1. [Erstellen Sie Datensätze](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-ingestion/create-datasets-and-ingest-data.html?lang=de) für die zu erfassenden Daten.
1. [Aufnehmen der Daten](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2020.1.dataingestion&amp;lang=de) in Experience Platform.
1. Vergewissern Sie sich, dass die Daten für den [[!UICONTROL Abfrage-Service]](https://experienceleague.adobe.com/docs/platform-learn/tutorials/queries/explore-data.html?lang=de) verfügbar sind.
1. [Verbinden Sie Business-Intelligence-Tools und SQL-Clients für Visualisierung, Datenabfrage und Erkundung mit dem [!UICONTROL Abfrage-Service]](https://experienceleague.adobe.com/docs/experience-platform/query/clients/overview.html?lang=de).

## Verwandte Dokumentation

* [Produktbeschreibung zu Adobe Experience Platform Intelligence](https://helpx.adobe.com/de/legal/product-descriptions/adobe-experience-platform-intelligence---product-description.html)
* Dokumentation zum [[!UICONTROL Abfrage-Service]](https://experienceleague.adobe.com/docs/experience-platform/query/home.html?lang=de)
