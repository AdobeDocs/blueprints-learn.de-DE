---
title: Data Analyse and Intelligence Blueprint
description: Dieser Plan zeigt, wie in Adobe Experience Platform erforscht werden kann, wie Abfrage und Analyse der Daten, die im Datensee vorhanden sind, durchgeführt werden können.
solution: Experience Platform
kt: 7207
thumbnail: null
exl-id: 3b22dfdd-3fbe-40b3-b798-1ee983723039,a972ea56-d1c8-45da-9044-ed31222a2441
translation-type: tm+mt
source-git-commit: 9a5137c5e71946c258cb94188ee53d742396d361
workflow-type: tm+mt
source-wordcount: '283'
ht-degree: 0%

---

# Data Analyse and Intelligence Blueprint

Data Analyse and Intelligence umfasst die Fähigkeit innerhalb von Adobe Experience Platform, die Abfrage und Analyse der Daten, die im Datensee vorhanden sind, zu untersuchen.

Der [!UICONTROL Abfrage-Dienst] der Experience Platform ermöglicht die Ausführung von SQL-Abfragen an den Daten. [!UICONTROL Data Science ] Workspace ermöglicht die Datenerforschung, Datenwissenschaft und maschinelle Lernarbeit.

Darüber hinaus ermöglicht die Experience Platform Verbindungen mit SQL-Clients, Schnittstellen und Business Intelligence-Tools von Drittanbietern, eine direkte Verbindung zu den Daten innerhalb der Experience Platform herzustellen, auf diese zuzugreifen und sie mit dem Protokoll [!DNL PostgreSQL] Abfrage.

Bestimmte Garantien gelten für die Zeitüberschreitung der Abfrage und für die Datenmenge, die im Ergebnis der Abfrage enthalten ist, wie in den Szenariodetails angegeben.

## Anwendungsfälle

* Interaktive Abfrage und Aggregation von Daten
* Zeilen- und Spaltenzugriff auf erfasste Daten für die Exploration und Validierung
* Dashboards und Visualisierungen von Daten mithilfe von Business Intelligencen

## Anwendungen

* Adobe Experience Platform

## Architektur

<img src="assets/dataexplore.svg" alt="Referenzarchitektur für Enterprise Data Exploration and Berichte Blueprint" style="border:1px solid #4a4a4a" />

## Guardraht

* 10-minütige Zeitbeschränkung für interaktive Abfragen
* In der Benutzeroberfläche zurückgegebene Beschränkung auf 100 Datensätze
* 50.000 Datensatzbegrenzung, die über den SQL-Connector zurückgegeben wird

## Implementierungsschritte

1. Konfigurieren Sie Datasets und Schema für die Datenerfassung in den Datensee.
1. Daten erfassen.
1. Vergewissern Sie sich, dass die Daten für [!UICONTROL Abfrage Service] und [!UICONTROL Data Science Workspace] für den Rohzugriff und die Abfrage verfügbar sind.
1. Verbinden Sie Business Intelligencen- und SQL-Clients mit dem [!UICONTROL Abfrage-Dienst], um Visualisierungen, Daten-Abfragen und Exploration durchzuführen.

## Verwandte Dokumentation

* [Produktbeschreibung für Adobe Experience Platform Intelligence](https://helpx.adobe.com/legal/product-descriptions/adobe-experience-platform-intelligence---product-description.html)
* [[!UICONTROL Abfrage ] Servicedocumentation](https://experienceleague.adobe.com/docs/experience-platform/query/home.html?lang=en)
