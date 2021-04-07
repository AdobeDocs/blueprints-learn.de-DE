---
title: Data Analyse and Intelligence Blueprint
description: Dieser Plan zeigt, wie in Adobe Experience Platform erforscht werden kann, wie Abfrage und Analyse der Daten, die im Datensee vorhanden sind, durchgeführt werden können.
solution: Experience Platform
kt: 7207
thumbnail: null
exl-id: 3b22dfdd-3fbe-40b3-b798-1ee983723039
translation-type: tm+mt
source-git-commit: 844fff1cefe367575beb5c03aa0f0d026eb9f39b
workflow-type: tm+mt
source-wordcount: '361'
ht-degree: 0%

---

# Data Analyse and Intelligence Blueprint

Data Analyse and Intelligence umfasst die Fähigkeit innerhalb von Adobe Experience Platform, die Abfrage und Analyse der Daten, die im Datensee vorhanden sind, zu untersuchen.

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