---
title: Ergebnis verzweigen
description: Erfahren Sie, wie Sie einer orchestrierten Kampagne eine Aktivität Verzweigung hinzufügen, um ein Ergebnis zum Speichern einer Audience und zum Senden von SMS-Nachrichten zu verzweigen.
doc-type: article
solution: Experience Platform
exl-id: 8f1d0839-e4ca-4b7c-bc97-4e271a457296
source-git-commit: 3076f01e06023cebd30ead73d61f4540da9ce791
workflow-type: tm+mt
source-wordcount: '259'
ht-degree: 0%

---


# Ergebnis verzweigen

## Ziel

Dieser Schritt ist einfach, da Sie nur eine Aktivität Verzweigung hinzufügen möchten, sodass Sie das Ergebnis duplizieren können, um in zukünftigen Schritten zwei verschiedene Dinge damit zu tun:

1. Die Zielgruppe für andere zur Verwendung für Werbe- oder Cross-Channel-Zwecke speichern
1. SMS-Nachrichten an die einzelnen Zeilen senden.



## Verzweigung erstellen

1. Klicken Sie auf der Workflow-Arbeitsfläche auf das Symbol **+** **&#x200B;**&#x200B;nach der Aktivität Zielgruppe aufbauen und wählen Sie die Aktivität **Verzweigung**

   ![Fügen Sie nach der Aktivität „Zielgruppe aufbauen“ die Aktivität „Verzweigung“ hinzu](assets/fork-the-result-add-fork-activity.png)



2. Aktualisieren Sie die Namen der einzelnen Transitionen im Formular, indem Sie auf die Transition klicken und dann die Namen wie unten beschrieben zuweisen:
   - **Oben** —> `Save Audience`
   - **Bottom** —> `SMS`

   ![Verzweigungen wurden in „Zielgruppe und SMS speichern“ umbenannt](assets/fork-the-result-rename-transitions.png)



   Wenn Sie fertig sind, sollte Ihre Arbeitsfläche nun wie folgt aussehen…

   ![Workflow-Arbeitsfläche nach dem Hinzufügen der Aktivität Verzweigung](assets/fork-the-result-final-canvas.png)

   >[!NOTE]
   >
   >Eine Verzweigung dupliziert im Wesentlichen das Ergebnis der vorherigen Aktivität in zwei unabhängige Verzweigungen



3. Klicken **oben** der Workflow-Arbeitsfläche auf „Speichern“.

![Schaltfläche „Speichern“ in der Symbolleiste der Workflow-Arbeitsfläche](assets/fork-the-result-click-save.png)

>[!TIP]
>
>Das war ziemlich schwierig, nicht 😁



## Zusammenfassung

Nun, Sie haben eine Verzweigung des Ergebnisses erstellt (d. h. das Duplizieren des Ergebnisses), mit der Sie eine Verzweigung klar angeben können, um eine Zielgruppe speichern zu verarbeiten, während die andere für den SMS-Versand verwendet werden kann.

>[!NOTE]
>
>Sie müssen Formulare verwenden, insbesondere wenn Sie die Zielgruppe speichern möchten, da die Aktivität „Zielgruppe speichern“ nicht zulässt, dass Aktivitäten ihr folgen.
