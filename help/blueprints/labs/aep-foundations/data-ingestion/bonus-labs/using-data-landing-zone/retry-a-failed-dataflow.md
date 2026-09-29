---
title: Wiederholen eines fehlgeschlagenen Datenflusses
description: Wiederholen Sie eine fehlgeschlagene Datenflussausführung, damit die Quelldaten in einem neuen Datenfluss anhand aktualisierter Zuordnungsregeln erneut verarbeitet werden.
doc-type: article
solution: Experience Platform
exl-id: 83ecf037-e524-4887-b833-5ed96af40419
product_v2:
  - id: edbd1a0e-46c8-49da-8c10-dba9ec80bba9
    internal-label: Experience Platform
source-git-commit: 1d6ba1444c119437eb8a86d5c4a1050d56d16023
workflow-type: tm+mt
source-wordcount: '117'
ht-degree: 0%
---

# Wiederholen eines fehlgeschlagenen Datenflusses

Gehen Sie wie folgt vor, um einen Workflow erneut auszuführen:

1. Navigieren Sie zu **Quellen -> Datenflüsse -> \[Name des Datenflusses] -> \[Fehler beim Ausführen]**
1. Markieren Sie die Datenflussausführung, bei der die rechte Leiste nicht angezeigt werden konnte.
1. Klicken Sie auf **Wiederholen**. Bei einem erneuten Versuch wird die Kopie der Daten, die mit der fehlgeschlagenen Ausführung verknüpft sind, erstellt und dann werden die neuen Zuordnungsregeln auf sie angewendet

![Wiederholen eines fehlgeschlagenen Datenflusses über die rechte Leiste](assets/retry-a-failed-dataflow.png)

>[!NOTE]
>
>Beachten Sie, dass beim erneuten Versuch eines fehlgeschlagenen Datenflusses ein neuer Datenfluss erstellt und ausgeführt wird. Er wird oben in der Liste der Datenflüsse angezeigt
