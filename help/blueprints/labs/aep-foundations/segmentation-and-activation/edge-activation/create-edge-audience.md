---
title: Edge-Zielgruppe erstellen
description: Erstellen und veröffentlichen Sie eine von Edge ausgewertete Zielgruppe zusammen mit einer Batch-Entsprechung, um zu vergleichen, wie jede auf eingehende Echtzeit-Ereignisse reagiert.
doc-type: article
solution: Experience Platform
exl-id: 79265a8f-81dd-41a3-89c5-c6646e435328
source-git-commit: 3039df0c022176e9dada9c5a300f2df14429033d
workflow-type: tm+mt
source-wordcount: '362'
ht-degree: 0%

---


# Edge-Zielgruppe erstellen

Diese Zielgruppe wird verwendet, um jemanden zu qualifizieren, wenn eine Payload (z. B. eine Seitenansicht) vom Client (z. B. Web SDK) zur Edge kommt.

>[!NOTE]
>
>Wir werten eine Zielgruppe auf der Edge in der Regel aus, damit wir sie umdrehen und in Personalization verwenden können. Wenn wir Personalization nicht auf dem Edge durchführen, können wir einfach die Zielgruppe als Streaming auf dem Hub bewerten lassen.

## Zielgruppe erstellen

1. Klicken Sie in der linken Leiste auf Zielgruppen .
1. Klicken Sie dann auf Zielgruppe erstellen in der oberen rechten Ecke Ihres Bildschirms
1. Klicken Sie dann auf Regel erstellen .



![Seite „Zielgruppen“ mit hervorgehobener Schaltfläche „Zielgruppe erstellen“ und hervorgehobener Option „Regel erstellen“](assets/create-edge-audience-create-audience-step-1.png)



![Die Arbeitsfläche „Regel erstellen“ wurde zum Erstellen einer neuen Zielgruppe geöffnet](assets/create-edge-audience-create-audience-step-2.png)



## Zielgruppe in Regeln konvertieren

1. Wechseln Sie zu **Zielgruppen** und klicken Sie in den Ordner **Experience Platform**
1. Ziehen Sie die Zielgruppe mit dem Namen **dep: Beliebiges Ereignis-Streaming (innerhalb einer Stunde)** auf die Arbeitsfläche

![Ziehen Sie die Zielgruppe Dep: Any Event Streaming (innerhalb einer Stunde) auf die Arbeitsfläche des Regel-Builders](assets/create-edge-audience-drag-audience-to-canvas.png)



1. Konvertieren Sie die Zielgruppe in einen Regelsatz auf der Arbeitsfläche, indem Sie auf das **Symbol** unten klicken und dann auf **Konvertieren**

![Konvertieren-Symbol auf der Arbeitsfläche, das zum Konvertieren der Zielgruppe in einen Regelsatz verwendet wird](assets/create-edge-audience-convert-to-rules-icon.png)

## Ereignisregeln aktualisieren

Nehmen Sie die folgenden Änderungen an den Ereignisregeln vor (möglicherweise müssen Sie das Ereignis erweitern, um es anzuzeigen)

1. Letzte
1. 15
1. Minuten

![Ereignisregel zum Trigger in den letzten 15 Minuten konfiguriert](assets/create-edge-audience-update-event-rules.png)

## Segment veröffentlichen

1. Aktualisieren Sie den Segmentnamen auf &quot;**Edge&quot; (innerhalb von 15 Minuten)**
1. Aktualisieren der Auswertungsmethode auf Edge
1. Segment veröffentlichen

![Segmentdetails, die die Edge-Auswertungsmethode vor der Veröffentlichung zeigen](assets/create-edge-audience-publish-segment.png)

## Batch-evaluiertes Segment erstellen

Wiederholen Sie die gleichen Schritte, die Sie gerade für das von Ihnen erstellte Edge-Segment ausgeführt haben, verwenden Sie jedoch stattdessen die folgenden Informationen:

>[!NOTE]
>
>Wir erstellen eine Batch-Zielgruppe, damit Sie sehen können, dass, obwohl ein Ereignis an die Edge übergeben wird, alle Zielgruppen, die als Batch-Auswertung gespeichert wurden, nicht gestreamt werden.

Ereignisregeln:

- Letzte
- 1
- Tag



Segmentdetails:

- Name -> **Beliebiger Ereignis-Batch (innerhalb von 1 Tag)**
- Auswertungsmethode -> Batch
