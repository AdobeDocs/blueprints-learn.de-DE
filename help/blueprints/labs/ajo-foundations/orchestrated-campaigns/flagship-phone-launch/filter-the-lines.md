---
title: Zeilen filtern
description: Erfahren Sie, wie Sie abgemeldete Kundenzeilen mit einer Aufspaltungsaktivität herausfiltern und Dimensionsänderung verwenden können, um die Zieldimension eines Workflows an die SMS-Kanalkonfiguration anzupassen.
doc-type: article
solution: Experience Platform
exl-id: fb556a27-5c73-4457-ae98-dba43d445c7f
source-git-commit: 3039df0c022176e9dada9c5a300f2df14429033d
workflow-type: tm+mt
source-wordcount: '776'
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

1. Klicken Sie auf der Workflow-Arbeitsfläche nach der hinzugefügten Aufspaltungsbedingung auf das Symbol **+** und wählen Sie die **SMS-Aktivität**

![Fügen Sie die SMS-Aktivität nach der Aufspaltungsbedingung hinzu](assets/filter-the-lines-add-sms-activity.png)

![SMS-Aktivität zur Workflow-Arbeitsfläche hinzugefügt](assets/filter-the-lines-sms-activity-on-canvas.png)



2. Klicken Sie in der rechten Leiste auf die Schaltfläche SMS bearbeiten , um mit der Konfiguration der SMS-Nachricht zu beginnen

![Schaltfläche „SMS bearbeiten“ in der rechten Leiste](assets/filter-the-lines-edit-sms-button.png)



3. Klicken Sie oben in der Navigationsleiste auf das Menüelement Aktionen und wählen Sie dann aus der Dropdown-Liste SMS-Konfiguration den zuvor erstellten Kanal aus.

![Dropdown-Liste „SMS-Konfiguration“ mit Fehlermeldung „Keine Ergebnisse“](assets/filter-the-lines-sms-configuration-no-results.png)

>[!CAUTION]
>
>Oh nein 🫨!  Warum gibt es keine Ergebnisse?  Haben Sie Ihren SMS-Kanal nicht bereits eingerichtet?  Ist das Produkt kaputt?
>
>AUSFLIPPEN!!!!!!!!!



## Ausbruchsmoment

Die Transition der Verzweigung hat derzeit eine Zielgruppendimension der Kundenzeile (d. h. auf welche Tabelle sich das aktuelle Ergebnis im relationalen Speicher bezieht).  Bei orchestrierten Kampagnen ist es jedoch einzigartig, dass Sie sich zum Versandzeitpunkt immer wieder beim Echtzeit-Kundenprofil anmelden, sodass Versand- und Tracking-Informationen aus Nachrichten einem Profil zugeordnet werden.  Dieser Join wurde für Sie aus der Tabelle des Kundenkontos vorkonfiguriert.

Die Kanalkonfiguration für SMS wurde bereits vorab für Sie eingerichtet und sieht derzeit so aus…

![Die Konfiguration der Ausführungsdetails wird im Labor „SMS-Kanal konfigurieren“ eingerichtet](assets/configure-sms-channel-final-execution-details.png)

**So liest du das:**

- Versand einer Nachricht pro Zieldimension (d. h. Kundenkonto) auf der Anzahl der zugehörigen Datensätze, die in der sekundären Dimension (d. h. Kundenzeile) gefunden wurden
- Jeden SMS-Versand unter Verwendung der in der sekundären Dimension (d. h. „Kundenzeile„) enthaltenen Mobiltelefonnummer ausführen

Diese einzigartige Möglichkeit, viele Nachrichten an ein Profil zu senden, ist eine der Hauptfunktionen von Orchestrierten Kampagnen, die es von Journey unterscheidet.


Wie bringt man das hier zum Laufen?  Dimensionsänderung hinzufügen 😀



## Dimensionsänderung hinzufügen

1. Klicken Sie auf die Schaltfläche Zurück im Bildschirm zur SMS-Bearbeitung

![Zurück-Schaltfläche zum Verlassen des SMS-Bearbeitungsbildschirms](assets/filter-the-lines-exit-sms-editor.png)



2. Klicken Sie auf der Workflow-Arbeitsfläche zwischen den **- und SMS-Aktivitäten auf das** Symbol **+** und wählen Sie **Dimension ändern** aus.

![Fügen Sie die Aktivität Dimensionsänderung zwischen Filter und SMS hinzu](assets/filter-the-lines-add-change-dimension.png)



3. Aktualisieren Sie rechts die Dimensionsänderung mit den folgenden Informationen:
   - **label:** `Convert Line to Account`
   - **Neue Zielgruppendimension:**`dep-rel: Customer Account`

![Dimensionsänderung konfiguriert, um Linie in Konto zu konvertieren](assets/filter-the-lines-change-dimension-settings.png)



4. Klicken Sie auf **Speichern** oben rechts auf der Arbeitsfläche, um Ihre Arbeit zu speichern. Wenn Sie fertig sind, sieht Ihr Workflow jetzt wie folgt aus…

![Workflow-Arbeitsfläche nach dem Hinzufügen der Dimensionsänderung](assets/filter-the-lines-workflow-after-change-dimension.png)



## SMS-Nachrichtenkonfiguration

Nachdem Sie den Workflow behoben haben, konfigurieren Sie die SMS neu.



1. Klicken Sie auf die SMS-Aktivität in der Workflow-Arbeitsfläche und klicken Sie dann in der linken Leiste auf die Schaltfläche **SMS bearbeiten**.

![Schaltfläche „SMS bearbeiten“, um die SMS-Nachricht neu zu konfigurieren](assets/filter-the-lines-edit-sms-button.png)

>[!NOTE]
>
>Das Laden dieses Bildschirms dauert eine Weile.  Ich weiß, dass es nervig ist, glauben Sie mir, dass es repariert wird





2. Klicken Sie in der oberen Navigationsleiste auf den **Aktionen** und wählen Sie dann aus der Dropdown-Liste SMS-Konfiguration den zuvor erstellten Kanal aus.

![SMS-Konfiguration zeigt den ausgewählten Kanal erfolgreich an](assets/filter-the-lines-sms-configuration-selected.png)

>[!TIP]
>
>Fühlt sich gut an, 😮‍💨 es nicht



## Zusammenfassung

Sie haben es durch dieses geschafft und hoffentlich zwei sehr wichtige Dinge gelernt:

1. Ihre Zielgruppendimension für die endgültigen Ergebnisse muss mit der Kanalkonfiguration übereinstimmen, die Sie verwenden möchten
1. Die Aktivität Dimensionsänderung wird wahrscheinlich Ihr bester Freund dafür werden, dass dies geschieht
