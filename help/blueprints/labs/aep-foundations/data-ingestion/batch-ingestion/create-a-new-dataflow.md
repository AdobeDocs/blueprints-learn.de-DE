---
hold: true
title: Erstellen eines neuen Datenflusses
description: Erstellen Sie einen Batch-Quelldatenfluss für einen vorhandenen Datensatz und importieren Sie Zuordnungen aus einem vorherigen Datenfluss, um die Einrichtung zu beschleunigen.
doc-type: article
solution: Experience Platform
exl-id: 6f26f742-27e8-445a-8005-21d4e59dc3d0
source-git-commit: 2b2b9b9c359c4cc6757ac62ad502ece9a4923095
workflow-type: tm+mt
source-wordcount: '357'
ht-degree: 0%

---


# Erstellen eines neuen Datenflusses

## Zu Quellen navigieren

1. Navigieren Sie in der Adobe Experience Platform-Benutzeroberfläche zum folgenden Speicherort:\
   **Quellen** -> **Katalog** -> **Lokales System**
1. Klicken Sie als Nächstes auf **Daten hinzufügen** für die Karte **Lokaler Datei-Upload** .

![Schaltfläche „Daten hinzufügen“ für die Karte „Lokaler Datei-Upload“ im Quellkatalog](assets/create-a-new-dataflow-local-file-upload-add-data.png "Zugriff auf die Data Landing Zone")



## Datenfluss einrichten

1. Wählen Sie im Bildschirm „Datenflussdetails“ die Option **Vorhandener Datensatz**.
1. Verwenden Sie den zuvor erstellten Datensatz mit dem Namen **Kundenkonto - &lt;Ihre Initialen>**
1. Stellen Sie sicher, dass der Umschalter **Profildatensatz** aktiviert ist.
(Wenn Sie dies nicht aktivieren, kann der Profilspeicher nicht überwachen, ob neue Daten in diesen Datensatz eingehen, und nimmt diese Daten daher nicht in Profile auf.)
1. Stellen Sie sicher, dass **Umschalter „Partielle Aufnahme aktivieren** eingeschaltet ist
(Wenn Sie dies nicht aktivieren, kann die gesamte Aufnahme fehlschlagen, wenn nur einer der Datensätze einen Fehler aufweist)
1. Legen Sie den Datenflussnamen als **Kundenkonto-Batch v2 - \&lt;Ihre Initialen>** fest
1. Aktivieren Sie alle Warnhinweise **Quellen: Datenflussstart/-erfolg/-fehler**
1. Wenn alles gut aussieht, klicken Sie auf **Weiter** in der oberen rechten Ecke des Bildschirms, um mit dem nächsten Schritt fortzufahren.

![Datenflussdetailbildschirm, der mit dem vorhandenen Datensatz für den zweiten Datenfluss/Datenflussdetails &#x200B;](assets/create-a-new-dataflow-existing-dataset-flow-details.png " wurde")



## Beispieldatei hochladen

1. Ziehen Sie die Datei „Lab\_&#x200B;**\_Account.csv“ per Drag-and-Drop**/oder laden Sie sie in die Benutzeroberfläche hoch.  Danach sollte der Bildschirm wie folgt aussehen.

![Vorschau der hochgeladenen CSV-Datei des Kundenkontos für den zweiten Datenfluss](assets/create-a-new-dataflow-uploaded-csv-preview.png "Zugriff auf die Azure Storage Explorer-Dateien in Adobe Experience Platform")



## Zuordnungen importieren

Auf dem Zuordnungsbildschirm können Sie die zuvor erstellten Zuordnungen importieren, anstatt alle Zuordnungen erneut einzurichten.

1. Klicken Sie auf die Schaltfläche **Zuordnung importieren**.
1. Wählen Sie den Datenfluss aus, der die zuvor erstellte Zuordnung enthält



![Schaltfläche „Zuordnung importieren“ auf dem Zuordnungsbildschirm](assets/create-a-new-dataflow-import-mapping-button.png "Schaltfläche „Zuordnung importieren“")



![Dialogfeld zur Auswahl des Datenflusses, aus dem die Zuordnung importiert werden soll](assets/create-a-new-dataflow-select-dataflow-to-import-mapping-from.png "Wählen Sie den Datenfluss aus, aus dem die Zuordnung importiert werden soll")

>[!NOTE]
>
>Der Import von Zuordnungen ist eine praktische Möglichkeit, Zuordnungen aus anderen Datenflüssen wiederzuverwenden und den Zuordnungsaufwand zu reduzieren
