---
title: Edge Activation
description: Erfahren Sie, wie sich die Aktivierungsgeschwindigkeiten für Edge, Streaming und Batch unterscheiden, und sehen Sie sich eine Vorschau der Laborschritte zum Erstellen eines Edge-Segments und zum Konfigurieren der Ereignisweiterleitung an.
doc-type: overview-page
solution: Experience Platform
exl-id: 9ecadff9-3838-4cd4-93b1-7c23a232f84c
product_v2:
  - id: edbd1a0e-46c8-49da-8c10-dba9ec80bba9
    internal-label: Experience Platform
source-git-commit: 1d6ba1444c119437eb8a86d5c4a1050d56d16023
workflow-type: tm+mt
source-wordcount: '175'
ht-degree: 0%
---

# Edge Activation

## Aktivierungsgeschwindigkeits-Zusammenfassung

Adobe verfügt über drei Aktivierungsgeschwindigkeiten, die auf unterschiedliche Anforderungen zugeschnitten sind:

1. Edge
1. Streaming
1. Batch

Wir werden Ihnen zeigen, wie Sie Adobe Edge mit Ereignisweiterleitung, Edge-Zielgruppen und Edge Personalization aktivieren. Anschließend zeigen wir, wie Sie Streaming-Ziele vom Hub aus sowohl für die Edge als auch für ein externes Ziel verwenden.

>[!IMPORTANT]
>
>Schließen Sie [die Postman-Einrichtung ab](../../setup.md) bevor Sie dieses Labor starten. Sie benötigen auch Zugriff auf [webhook.site](https://webhook.site/), um das an das externe Ziel gesendete Ereignis zu erfassen.

>[!NOTE]
>
>Die Batch-Aktivierung wird in diesem Labor nicht behandelt. Die Batch-Aktivierung kann in verschiedenen Intervallen geplant werden. Aufgrund des zeitlichen Verlaufs ist es schwierig, eine Batch-Aktivierung in einer Laborumgebung darzustellen, ohne mindestens 3 bis 24 Stunden Zeit zu haben.



## Was das Labor abdecken wird

- Edge-Segment erstellen
- Konfigurieren der Ereignisweiterleitung
- Senden eines Edge-Ereignisses
- Dieser Trigger
  - Zu qualifizierendes Edge-Segment
  - Ereignisweiterleitung auf Edge zum Senden an Webhook
