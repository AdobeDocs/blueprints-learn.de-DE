---
title: Überprüfung und Validierung
description: Zeigen Sie eine Vorschau eines gestreamten Datensatzes in der Benutzeroberfläche an und führen Sie SQL-Abfragen aus, um aufgenommene Datensätze und verschachtelte Schemafelder zu überprüfen.
doc-type: article
solution: Experience Platform
exl-id: fbdb0b6b-08b6-49b8-b6ab-d59d5941c678
product_v2:
  - id: edbd1a0e-46c8-49da-8c10-dba9ec80bba9
    internal-label: Experience Platform
source-git-commit: 1d6ba1444c119437eb8a86d5c4a1050d56d16023
workflow-type: tm+mt
source-wordcount: '278'
ht-degree: 0%
---

# Überprüfung und Validierung

## Vorschau des Datensatzes

1. Klicken Sie auf **Datensätze**
1. **Suchen** und **Klicken** den von Ihnen erstellten Datensatznamen.

   ![Zugriff auf den erstellten Datensatz im Bereich Datensätze](assets/verification-and-validation-access-the-dataset-in-the-datasets-pane.png "Zugriff auf den Datensatz im Bereich Datensätze")



1. Klicken Sie oben **auf** Datensatz in der Vorschau anzeigen“

   ![Die Schaltfläche Datensatz in der Vorschau anzeigen in der oberen rechten Ecke des Datensatzbildschirms](assets/verification-and-validation-preview-dataset-button.png "Datensatz in der Vorschau anzeigen befindet sich in der oberen rechten Ecke ")



1. **Überprüfen** und **validieren** Sie dieselben Datensätze, die Sie aufgenommen haben, indem Sie auf den linken Bereich klicken, der die Schemahierarchie anzeigt.

![Überprüfen und Validieren erfasster Datensätze mithilfe des Schemahierarchiebereichs](assets/verification-and-validation-verify-and-validate-the-dataset.png " Überprüfen und Validieren des Datensatzes")

>[!NOTE]
>
>**Vorschau des**) zeigt nur die ersten Zeilen des Datensatzes an. Array-Objekte können nicht angezeigt werden.



## Abfragedatensatz

1. **Vorschau** schließen)
1. Klicken Sie im Datensatzbildschirm auf das Kopiersymbol unter **Tabellenname**. Im folgenden Beispielbildschirm ist der Tabellenname `customer_account_sm`

   ![Kopieren des Tabellennamen vom Datensatzbildschirm zur Verwendung in einer Abfrage](assets/verification-and-validation-copy-the-table-name.png "Kopieren des Tabellennamen")



1. Navigieren Sie zum Abschnitt **Abfragen**

1. Klicken Sie auf **Abfrage erstellen**

   ![Zugriff auf den Abfrage-Editor über den Abschnitt „Abfragen](assets/verification-and-validation-access-the-query-editor.png "Zugriff auf den Abfrage-Editor")



1. Aktivieren Sie den **Erweiterter Abfrage-Editor** Umschalter

   ![Benutzeroberfläche des Abfrage-Editors mit aktiviertem Umschalter für den erweiterten Abfrage](assets/verification-and-validation-enhanced-query-editor-toggle.png "Editor")



1. Kopieren Sie die folgende SQL-Abfrage in den **Editor**. Denken Sie daran, `<table_name>` durch den Wert zu ersetzen, den Sie in Schritt 2 erhalten haben.

   ```sql
   SELECT * FROM <table_name>
   ```



1. Drücken Sie die **Play**-Taste.

1. **Vorschau** der Ergebnisse.

1. Führen Sie außerdem die folgende SQL-Abfrage aus, um das XDM-Schema zusammen mit den Daten abzurufen:

   ```sql
   SELECT to_json(shippingAddress) FROM <table_name>
   ```



1. Geben Sie Folgendes ein, um auf die Daten im `postalCode`Knoten **zuzugreifen**:

```sql
SELECT shippingAddress.postalCode FROM <table_name>
```

>[!SUCCESS]
>
>Herzlichen Glückwunsch!  Sie haben erfolgreich einen Beispielsatz von Echtzeit-Kundenprofilen aufgenommen und erstellt
