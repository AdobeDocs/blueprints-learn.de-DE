---
title: Edge Activation
description: Erfahren Sie, wie sich die Aktivierungsgeschwindigkeiten für Edge, Streaming und Batch unterscheiden, und sehen Sie sich eine Vorschau der Laborschritte zum Erstellen eines Edge-Segments und zum Konfigurieren der Ereignisweiterleitung an.
doc-type: overview-page
solution: Experience Platform
exl-id: 9ecadff9-3838-4cd4-93b1-7c23a232f84c
source-git-commit: 3039df0c022176e9dada9c5a300f2df14429033d
workflow-type: tm+mt
source-wordcount: '151'
ht-degree: 0%

---


# Edge Activation

## Aktivierungsgeschwindigkeits-Zusammenfassung

Adobe verfügt über drei Aktivierungsgeschwindigkeiten, die auf unterschiedliche Anforderungen zugeschnitten sind:

1. Edge
1. Streaming
1. Batch

Wir werden Ihnen zeigen, wie Sie Adobe Edge mit Ereignisweiterleitung, Edge-Zielgruppen und Edge Personalization aktivieren. Anschließend zeigen wir, wie Sie Streaming-Ziele vom Hub aus sowohl für die Edge als auch für ein externes Ziel verwenden.

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
