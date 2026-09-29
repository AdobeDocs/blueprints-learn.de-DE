---
title: Überprüfung und Validierung
description: Zeigen Sie eine Vorschau eines aufgenommenen Datensatzes in der Benutzeroberfläche an und führen Sie SQL-Abfragen aus, um im Batch aufgenommene Datensätze und verschachtelte Schemafelder zu überprüfen.
doc-type: article
solution: Experience Platform
exl-id: 7e7cd43d-cc24-4a40-a175-2c651436ab79
product_v2:
  - id: edbd1a0e-46c8-49da-8c10-dba9ec80bba9
    internal-label: Experience Platform
source-git-commit: 1d6ba1444c119437eb8a86d5c4a1050d56d16023
workflow-type: tm+mt
source-wordcount: '302'
ht-degree: 0%
---

# Überprüfung und Validierung

## Vorschau des Datensatzes

1. Klicken Sie auf **Datensätze**
1. **Suchen** und **Klicken** den von Ihnen erstellten Datensatznamen.

   ![Suchen und Klicken auf den Datensatznamen im Datensatzbereich](assets/verification-and-validation-access-dataset-in-datasets-pane.png "Greifen Sie auf den Datensatz im Datensatzbereich zu")



1. Klicken Sie oben **auf** Datensatz in der Vorschau anzeigen“

   ![Position der Schaltfläche Datensatz in der Vorschau anzeigen in der oberen rechten Ecke des Datensatzbildschirms](assets/verification-and-validation-preview-dataset-button-location.png "Datensatz in der Vorschau anzeigen befindet sich in der oberen rechten Ecke")



1. **Überprüfen** und **validieren** Sie dieselben Datensätze, die Sie aufgenommen haben, indem Sie auf den linken Bereich klicken, der die Schemahierarchie anzeigt.

![Datensatzvorschau mit Schemahierarchie-Bereich mit aufgenommenen Datensätzen](assets/verification-and-validation-verify-and-validate-the-dataset.png)

>[!NOTE]
>
>**Vorschau des Datensatzes** zeigt den letzten erfolgreichen Batch in diesem Datensatz an. Die vorherigen Batches werden nicht angezeigt. Komplexe Daten wie Arrays und Zuordnungen sind heute nicht mehr sichtbar und erscheinen als leere Spalten. Um eine umfassendere Ansicht zu erhalten, müssen Sie SQL verwenden, um den Datensatz wie unten beschrieben zu untersuchen.



## Abfragedatensatz

1. **Vorschau** schließen)
1. Klicken Sie im Datensatzbildschirm auf das Kopiersymbol unter **Tabellenname**. Im folgenden Beispielbildschirm ist der Tabellenname `customer_account_sm`

   ![Kopieren-Symbol neben dem Tabellennamen im Datensatzbildschirm](assets/verification-and-validation-copy-table-name.png "Kopieren Sie den Tabellennamen")



1. Navigieren Sie zum Abschnitt **Abfragen**

1. Klicken Sie auf **Abfrage erstellen**

   ![Schaltfläche „Abfrage erstellen“ im Abschnitt „Abfragen“](assets/verification-and-validation-access-the-query-editor.png)



1. Kopieren Sie die folgende SQL-Abfrage in den **Editor**. Denken Sie daran, `<table_name>` durch den Wert zu ersetzen, den Sie in Schritt 6 erhalten haben.

   ```sql
   SELECT * FROM <table_name>
   ```



1. Drücken Sie die **Play**-Taste.

   ![Benutzeroberfläche des Abfrage-Editors mit SQL-Abfrage- und Wiedergabe](assets/verification-and-validation-query-editor-interface.png "Schaltfläche „Abfrage-Editor“")



1. **Vorschau** der Ergebnisse

1. Um das XDM-Schema zusammen mit den Daten abzurufen, führen Sie auch die folgende SQL-Abfrage aus:

```sql
SELECT to_json(shippingAddress) FROM <table_name>
```

Um auf die Daten im Knoten `postalCode`**zuzugreifen** können Sie Folgendes eingeben:

```sql
SELECT shippingAddress.postalCode FROM <table_name>
```

>[!SUCCESS]
>
>Herzlichen Glückwunsch!  Sie haben erfolgreich einen Beispielsatz von Echtzeit-Kundenprofilen aufgenommen und erstellt
