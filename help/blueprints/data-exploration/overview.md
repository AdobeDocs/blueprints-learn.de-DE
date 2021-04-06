---
title: Enterprise Data Exploration and Berichte Blueprint
description: Dieser Plan zeigt, wie in Adobe Experience Platform erforscht werden kann, wie Abfrage und Analyse der Daten, die im Datensee vorhanden sind, durchgeführt werden können.
solution: Experience Platform
kt: 7207
thumbnail: null
translation-type: tm+mt
source-git-commit: e1a9881996a181310bdc32cb083e4c5654139bf0
workflow-type: tm+mt
source-wordcount: '364'
ht-degree: 0%

---


# Enterprise Data Exploration and Berichte Blueprint

Enterprise Data Exploration and Berichte umfasst die Fähigkeit innerhalb von Adobe Experience Platform, erforsche Abfrage und Analyse der Daten durchzuführen, die im Datensee vorhanden sind.

Der Abfrage Service der Experience Platform ermöglicht die Ausführung von SQL-Abfragen an den Daten. Der Data Science Workspace ermöglicht die Durchführung von Datenforschungs-, Datenwissenschaft- und maschinellem Lernaufwand für die Daten.

Darüber hinaus ermöglicht die Experience Platform Verbindungen mit SQL-Clients, Schnittstellen und Business Intelligence-Tools von Drittanbietern, direkt eine Verbindung zu den Daten innerhalb der Experience Platform herzustellen, auf diese zuzugreifen und sie mit dem PostgreSQL-Protokoll Abfrage.

Bestimmte Garantien gelten für die Zeitüberschreitung der Abfrage und für die Datenmenge, die im Ergebnis der Abfrage enthalten ist, wie in den Szenariodetails angegeben.

## Anwendungsfälle

* Interaktive Abfrage und Aggregation von Daten
* Zeilen- und Spaltenzugriff auf erfasste Daten für die Exploration und Validierung
* Dashboards und Visualisierungen von Daten mithilfe von Business Intelligencen

## Anwendungen

* Adobe Experience Platform

## Szenarien

| Szenario | Beschreibung | Experience Cloud Applications/Services |
|---|---|---|
| **Datenforschung - Rohdaten-Abfrage** | <ul><li>Schreiben und führen Sie SQL-Abfragen im Datensee mithilfe der interaktiven Abfrage-Benutzeroberfläche oder eines angeschlossenen SQL-Clients durch. Data Science Workspace kann auch zur Abfrage und zum Einblick in die Rohdaten in die Experience Platform verwendet werden.</li></ul> | <ul><li>Adobe Experience Platform</li></ul> |
| **Enterprise Dashboard** | <ul><li>Verbinden Sie Business Intelligencen-Tools mit Experience Platformen, um Daten für Dashboards und Berichte-Anwendungsfälle zu visualisieren.</li></ul> | <ul><li>Adobe Experience Platform</li></ul> |

## Architektur

<img src="assets/dataexplore.svg" alt="Referenzarchitektur für Enterprise Data Exploration and Berichte Blueprint" style="border:1px solid #4a4a4a" />

## Guardraht

* 10-minütige Zeitbeschränkung für interaktive Abfragen
* In der Benutzeroberfläche zurückgegebene Beschränkung auf 100 Datensätze
* 50.000 Datensatzbegrenzung, die über den SQL-Connector zurückgegeben wird

## Implementierungsschritte

1. Konfigurieren Sie Datasets und Schema für die Datenerfassung in den Datensee.
1. Daten erfassen.
1. Vergewissern Sie sich, dass die Daten für den Zugriff auf Rohdaten und die Abfrage in Abfrage Service und Data Science Workspace verfügbar sind.
1. Business Intelligence-Tools und SQL-Clients mit dem Abfrage Service für Visualisierung, Abfrage und Exploration von Daten verbinden.

## Verwandte Dokumentation

* [Produktbeschreibung für Adobe Experience Platform Intelligence](https://helpx.adobe.com/legal/product-descriptions/adobe-experience-platform-intelligence---product-description.html)
* [Dokumentation zum Abfrage Service](https://experienceleague.adobe.com/docs/experience-platform/query/home.html?lang=en)