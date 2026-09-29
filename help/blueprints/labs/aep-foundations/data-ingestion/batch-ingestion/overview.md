---
title: Batch-Erfassung
description: Laden Sie Kundenkontendaten durch Batch-Aufnahme in den Data Lake und das Profil, während Sie Zuordnungs- und Datenqualitätsfehler beheben.
doc-type: overview-page
solution: Experience Platform
exl-id: 76830e79-8fc0-4fda-98b1-2c1de19e8158
product_v2:
  - id: edbd1a0e-46c8-49da-8c10-dba9ec80bba9
    internal-label: Experience Platform
source-git-commit: 1d6ba1444c119437eb8a86d5c4a1050d56d16023
workflow-type: tm+mt
source-wordcount: '143'
ht-degree: 0%
---

# Batch-Erfassung

## Lernziele

In dieser Übung laden Sie die Kundenkontodaten aus einem dateibasierten Quell-Connector in den Data Lake von AEP und dann in das Profil. Sie erfahren Folgendes:

1. Grundlegendes zu Passthrough-Zuordnungen
1. Korrigieren von ML-generierten Passthrough-Zuordnungen
1. Verwenden der Datenquellenvorschau zur Überprüfung von Datenqualitätsproblemen
1. Planen der Ausführung eines Datenflusses
1. Umgang mit Fehlern aufgrund fehlender Werte in Pflichtfeldern
1. Umgang mit Fehlern, die durch Fehler wegen nicht übereinstimmender Datentypen verursacht werden
1. Umgang mit Fehlern bei der Datenaufnahme und Wiederherstellung nach einem solchen Fehler
1. Iterative Verwendung von Testdaten zum Generieren eines umfassenden Zuordnungssatzes.

>[!NOTE]
>
>Wenn Sie die Erstellung des Kundenkonto-Schemas in den vorherigen Labs nicht abgeschlossen haben, können Sie den Schemakatalog durchsuchen und stattdessen **dep: Kundenkonto** verwenden
