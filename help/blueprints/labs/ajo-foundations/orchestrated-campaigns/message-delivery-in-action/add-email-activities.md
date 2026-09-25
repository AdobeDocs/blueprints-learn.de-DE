---
title: E-Mail-Aktivitäten hinzufügen
description: Erfahren Sie, wie Sie in einer orchestrierten Kampagne zwei E-Mail-Aktivitäten in separaten Verzweigungen mit unterschiedlichen E-Mail-Kanal-Konfigurationen hinzufügen und konfigurieren.
doc-type: article
solution: Experience Platform
exl-id: e911a251-9f9f-484c-a2de-101b0fc2c417
source-git-commit: 96308d5726def849ef22540a5d13618017c40cc3
workflow-type: tm+mt
source-wordcount: '479'
ht-degree: 0%
---

# E-Mail-Aktivitäten hinzufügen

## Ziel

In den nächsten Schritten fügen Sie den beiden Verzweigungen der Aktivität Verzweigung über die Kampagne zwei E-Mail-Aktivitäten hinzu. Sie konfigurieren die beiden E-Mail-Aktivitäten für die Verwendung der zuvor erstellten E-Mail-Kanäle. Schließlich fügen Sie jeder dieser E-Mail-Aktivitäten auch eine grundlegende E-Mail-Einrichtung (Betreff und Text) hinzu.

>[!CAUTION]
>
>Bevor Sie fortfahren, müssen Sie sicherstellen, dass Ihre beiden E-Mail-Kanal-Konfigurationen in ihrem Status Aktiv angezeigt werden.
>
>![Beide E-Mail-Kanal-Konfigurationen mit aktivem Status](assets/add-email-activities-email-channel-configs-active.png "E-Mail-Kanal-Konfigurationen")



## E-Mail-Aktivität der obersten Verzweigung hinzufügen

1. Klicken Sie auf das **+** des oberen Flusses und wählen Sie **E-Mail** aus den **Kanalaktivitäten**

   ![E-Mail-Aktivität hinzufügen](assets/add-email-activities-select-email-activity.png)

   Der Detailbereich **E** Mail“ wird geöffnet

   ![E-Mail-Detailbereich](assets/add-email-activities-email-details-pane.png)

2. Benennen Sie die Bezeichnung für die Aktivität **E-Mail mit**) um **E-Mail** und klicken Sie auf **E-Mail bearbeiten**. Beachten Sie, dass die Erstellung des E-Mail-Textkörpers nur zu Testzwecken dient

   ![Beschriftung der E-Mail-Aktivität umbenennen und auf „E-Mail bearbeiten“](assets/add-email-activities-rename-and-edit-email.png)

3. Wählen Sie die Registerkarte **Aktionen** und aus der Dropdown-Liste die Option **Profil-E-Mail** Kanalkonfiguration aus

   ![Wählen Sie auf der Registerkarte „Aktionen“ die Konfiguration Profil-E-Mail-Kanal aus](assets/add-email-activities-select-profile-email-channel.png)

4. Klicken Sie anschließend auf **Inhalt bearbeiten** um Testinhalte hinzuzufügen

   ![Klicken Sie auf Inhalt bearbeiten , um Testinhalte hinzuzufügen](assets/add-email-activities-edit-content.png)

5. Geben Sie eine **Betreffzeile** ein („Upgrade-Angebot für Mitglieder des Standardplans„) und klicken Sie auf die Schaltfläche **E-Mail-Textkörper bearbeiten**.

   ![Betreffzeile hinzufügen und E-Mail-Textkörper bearbeiten](assets/add-email-activities-subject-line-edit-body.png)

6. Es gibt viele Optionen. Wählen Sie für diesen Test die Option **Eigenen Code erstellen** HTML aus

   ![Wählen Sie die Option Eigenen HTML codieren &#x200B;](assets/add-email-activities-code-your-own-html.png)

7. Fügen Sie in **E-Mail-**-Designer&quot; die Testzeile „Upgrade-Angebot verfügbar!“ ein. direkt vor den `</body></html>` Tags wie abgebildet und klicken Sie auf **Speichern**

   ![Fügen Sie die Testzeile in Email Designer ein und klicken Sie auf Speichern](assets/add-email-activities-email-designer-save.png)

8. Warten Sie, bis die Bestätigungsmeldung unten rechts angezeigt wird

   ![Bestätigungsmeldung wird angezeigt](assets/add-email-activities-confirmation-message.png)

9. Klicken Sie auf den **Linkspfeil** neben **E-Mail-Designer**, um den Vorgang zu beenden

   ![Klicken Sie auf den Nach-links-Pfeil, um E-Mail-Designer zu verlassen](assets/add-email-activities-exit-email-designer.png)

10. Ein Bestätigungsdialogfeld wird angezeigt, klicken Sie auf die Schaltfläche **Speichern und schließen**.

![Bestätigungsdialogfeld mit der Schaltfläche Speichern und schließen](assets/add-email-activities-save-and-close-dialog.png)

1. Überprüfen Sie die E-Mail-Eigenschaften und -Aktionen einschließlich des Texts, der zum E-Mail-Textkörper hinzugefügt wurde. Klicken Sie auf den **Pfeil nach links**, um zur Kampagnen-Arbeitsfläche zurückzukehren

![Zurück zur Campaign-Arbeitsfläche](assets/add-email-activities-back-to-campaign-canvas.png)

## Hinzufügen der E-Mail-Aktivität der unteren Verzweigung

Zurück auf der Kampagnen-Arbeitsfläche, klicken Sie auf das **+** des unteren Flusses und wählen Sie **E-Mail** aus den **Kanalaktivitäten**. Führen Sie dieselben Schritte wie oben aus (Schritte 2 bis 11), mit Ausnahme der folgenden:

- Benennen Sie die Bezeichnung für die Aktivität **E-Mail** in **E-Mail über Target** um.
- Wählen Sie in den E-Mail-Einstellungen die **Relational-Email** E-Mail-Kanalkonfiguration aus

![Zweite E-Mail-Aktivität, die mit dem Kanal „Relational-Email](assets/add-email-activities-bottom-branch-relational-email.png " konfiguriert istFügen Sie die zweite E-Mail-Aktivität hinzu")

## Zusammenfassung

Sie haben jetzt gesehen, wie Sie die E-Mail-Aktivitäten mit den E-Mail-Kanälen konfigurieren. Jede Aktivität wurde dann mit einem sehr einfachen E-Mail-Betreff und -Textkörper konfiguriert. Als Nächstes wird die gesamte Kampagne getestet.
