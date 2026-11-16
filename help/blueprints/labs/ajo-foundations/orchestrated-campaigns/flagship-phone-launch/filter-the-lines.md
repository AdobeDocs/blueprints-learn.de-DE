---
title: Zeilen filtern
description: Erfahren Sie, wie Sie abgemeldete Kundenzeilen mit einer Aufspaltungsaktivität herausfiltern und Dimensionsänderung verwenden können, um die Zieldimension eines Workflows an die SMS-Kanalkonfiguration anzupassen.
doc-type: article
solution: Experience Platform
exl-id: fb556a27-5c73-4457-ae98-dba43d445c7f
product_v2:
  - id: edbd1a0e-46c8-49da-8c10-dba9ec80bba9
    internal-label: Experience Platform
source-git-commit: 689f227965176096ccd1785699de65046af4f3d3
workflow-type: tm+mt
source-wordcount: '371'
ht-degree: 0%
---

# Zeilen filtern

## Ziel

In den nächsten Schritten werden Sie alle Zeilen herausfiltern, die aufgrund ihrer Abmeldung auf Zeilenebene tatsächlich nicht mit einer SMS-Nachricht angesprochen werden dürfen.  Sie können sich hier nicht auf die Profilzustimmung verlassen, da dies ein Ziel auf Zeilenebene ist.



## Aufspaltungsaktivität einrichten

1. Klicken Sie auf das Symbol **+** in der unteren Transition der Aktivität Verzweigung und wählen Sie im Popup die Aktivität **Aufspaltung** aus.

   ![Fügen Sie eine Aufspaltungsaktivität zum unteren Verzweigungszweig hinzu](assets/filter-the-lines-add-split-activity.png)



2. Aktualisieren Sie in der rechten Leiste die Bezeichnung , sodass sie Folgendes angibt: `Filter out opt'd out lines`

   ![Der Titel der Aufspaltungsaktivität wurde zum Filtern von Opt-out-Zeilen festgelegt](assets/filter-the-lines-set-split-label.png)



3. Erweitern Sie in der rechten Leiste den Abschnitt **Standardsegment** und klicken Sie auf die Schaltfläche **Filter erstellen**

   ![Schaltfläche „Filter erstellen“ im Abschnitt „Teilmenge“](assets/filter-the-lines-create-filter-button.png)



4. Fügen Sie eine Bedingung hinzu, um sicherzustellen, dass Sie alle Kundenzeilen entfernen, die vom SMS-Messaging abgemeldet wurden, und klicken Sie dann auf **Bestätigen**.

   ![Bedingung zum Entfernen von Kundenzeilen, die von SMS abgemeldet wurden](assets/filter-the-lines-sms-optin-condition.png)

   >[!NOTE]
   >
   >Sie müssen herausfinden, wie Sie die Bedingung erstellen, aber das Endergebnis stimmt mit dem obigen Screenshot überein.  Du hast das!



5. Klicken Sie auf die Schaltfläche Speichern oben rechts, um Ihre Arbeit zu speichern.  Ihre Arbeitsfläche sieht nun wie folgt aus\…

![Workflow-Arbeitsfläche nach dem Speichern der Aufspaltungsaktivität](assets/filter-the-lines-canvas-after-split-save.png)



## Hinzufügen der SMS-Aktivität

1. Klicken Sie auf der Workflow-Arbeitsfläche auf das Symbol **+** nach der hinzugefügten Bedingung für die Aufspaltung und wählen Sie die **Aktivität für mobile Nachrichten**

   ![Fügen Sie die Aktivität Nachricht für Mobilgeräte nach der Aufspaltungsbedingung hinzu](assets/filter-the-lines-add-sms-activity.png)

   ![SMS-Aktivität zur Workflow-Arbeitsfläche hinzugefügt](assets/filter-the-lines-sms-activity-on-canvas.png)



2. Klicken Sie in der rechten Leiste auf die Schaltfläche Mobile-Nachricht bearbeiten , um mit der Konfiguration der SMS-Nachricht zu beginnen

   ![Schaltfläche Mobile-Nachricht bearbeiten in der rechten Leiste](assets/filter-the-lines-edit-sms-button.png)



3. Klicken Sie in der oberen Navigationsleiste auf das Menüelement Aktionen und wählen Sie dann aus der Dropdown-Liste Mobile-Nachrichtenkonfiguration den zuvor erstellten Kanal aus.

![SMS-Konfiguration zeigt den ausgewählten Kanal erfolgreich an](assets/filter-the-lines-sms-configuration-selected.png)




## Zusammenfassung

Sie haben alle Zeilen herausgefiltert, die aufgrund des Opt-outs nicht mit einer SMS-Nachricht angesprochen werden durften, und eine SMS-Aktivität für diejenigen hinzugefügt, die angesprochen werden durften.
