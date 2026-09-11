---
title: Zielgruppe lesen
description: Erfahren Sie, wie Sie die Aktivität „Zielgruppe lesen“ mit einer Dimension für Profilzielgruppen in einer orchestrierten Kampagne verwenden und testen, wie nicht übereinstimmende Profile bei der Abstimmung relativer Daten gelöscht werden.
doc-type: article
solution: Experience Platform
exl-id: f825efe9-4349-4195-a017-c956c15df946
source-git-commit: 3039df0c022176e9dada9c5a300f2df14429033d
workflow-type: tm+mt
source-wordcount: '1268'
ht-degree: 0%

---


# Zielgruppe lesen

## Ziel

In den nächsten Schritten erstellen Sie eine Kampagne, um eine Zielgruppe aus AEP zu lesen und sie zusammen mit der zuvor erstellten Dimension-Profilzielgruppe zu verwenden. Verwenden Sie die Aktivität Aufspaltung , um die Daten auf der Grundlage einer Bedingung aufzuteilen. Testen Sie abschließend die Kampagne, um zu verstehen, wie diese Zielgruppen funktionieren, wenn sie mit dem relationalen Schema verwendet werden.

## Lesen der Zielgruppe

In diesem Labor wird die Verwendung der Aktivität „Zielgruppe lesen“ in Verbindung mit dem relationalen Schema für die Anreicherung behandelt.

Orchestrierte Kampagne verwendet das relationale Schema für alle Aktivitäten. Wenn die Aktivität Audience lesen verwendet wird, die die Audience aus AEP liest, sollte eine entsprechende Entität (Target-Dimension) konfiguriert werden, um die Audience mit der Campaign Target-Dimension abzustimmen.

## Erstellen einer Kampagne

1. Klicken Sie in der linken Seitenleiste auf **Kampagnen**

![Navigation in der linken Leiste zu Kampagnen](assets/read-an-audience-navigate-to-campaigns.png)

&#x200B;2. Klicken Sie auf **Kampagne erstellen**

![Schaltfläche „Kampagne erstellen“](assets/read-an-audience-create-campaign-button.png)

&#x200B;3. Wählen Sie **Orchestrierung - Marketing** und klicken Sie auf **Bestätigen**

![Orchestrierung - Auswahl des Marketing-Kampagnentyps](assets/read-an-audience-select-orchestration-marketing.png)

&#x200B;4. Geben Sie die Kampagnendetails wie folgt an und klicken Sie dann auf die Schaltfläche **Speichern**
   - Name: **OC-RSL-ReadAudience-Test**
   - Beschreibung: **RSL-read audience test**

![Kampagneneinstellungen-Formular mit Name und Beschreibung](assets/read-an-audience-campaign-settings-form.png)

&#x200B;5. Auf die Bestätigungsmeldung warten

![Bestätigungsnachricht nach dem Speichern der Kampagneneinstellungen](assets/read-an-audience-campaign-settings-confirmation.png)



## Audience-Aktivität lesen hinzufügen

1. Klicken Sie auf das **+** innerhalb der Arbeitsfläche, um das Optionsmenü zu öffnen, und wählen Sie dann **Zielgruppe lesen** aus den **Targeting-Aktivitäten**

![Menü Zielgruppenbestimmungsaktivitäten mit ausgewählter Option „Zielgruppe lesen“](assets/read-an-audience-add-read-audience-activity.png)

&#x200B;2. Klicken Sie **Detailbereich Zielgruppe lesen** auf das Suchsymbol für **Zielgruppe**

![Bereich mit Zielgruppendetails lesen mit dem Zielgruppensuchsymbol](assets/read-an-audience-search-audience-icon.png)

&#x200B;3. Wählen Sie die Zielgruppe **dep: Basic Plan Members** mit der Profilanzahl von **9** aus und klicken Sie auf **Zielgruppe hinzufügen**

![dep: Grundlegende Zielgruppe von Plannern mit einer Profilanzahl von 9 ausgewählt](assets/read-an-audience-select-basic-plan-members-audience.png)

&#x200B;4. Klicken Sie anschließend auf die Dropdown-Liste für **Entität** und wählen Sie die `dep-rel: Customer Account - customer_id` Campaign Target-Dimension aus

![Dropdown-Liste „Entität“ mit ausgewählter Dimension für das Kundenkonto](assets/read-an-audience-select-entity-target-dimension.png)

>[!NOTE]
>
>Andere Attribute können auch aus dem AEP-Profil extrahiert werden, um sie auf der Arbeitsfläche mithilfe der Schaltfläche **Attribut hinzufügen** zu verwenden. Für dieses Labor sind jedoch keine zusätzlichen Attribute erforderlich, sodass dieser Schritt übersprungen wird.



## Testen der Kampagne

1. Die Einstellungen für die Aktivität **Zielgruppe lesen** sind ausgefüllt. Klicken Sie auf **Starten**, um die Kampagne im **Testmodus“**

![Schaltfläche „Starten“ zum Ausführen der Kampagne im Testmodus](assets/read-an-audience-start-test-mode.png)

>[!NOTE]
>
>Dieser Vorgang dauert einige Minuten.
>
>Der Testmodus ermöglicht die Ausführung der Kampagne zur Überprüfung und Überwachung ihres Verhaltens sowie der Ergebnisse jeder Aktivität. Die Aktivitäten werden sequenziell bis zum Ende der Arbeitsfläche ausgeführt.



&#x200B;2. Die Testausführung beginnt, und die Ergebnisse werden nach Abschluss angezeigt. Klicken Sie auf **Knoten** Ergebnis“ und dann auf Ergebnisse in der Vorschau anzeigen , um die Ausführungsergebnisse anzuzeigen

![Ergebnisknoten mit der Option „Vorschau der Ergebnisse“](assets/read-an-audience-preview-test-results.png)

&#x200B;3. Beachten Sie, dass **2** (von 9) Profile aus dem **Zielgruppe lesen** keine entsprechende **Zielgruppendimension** aus dem relationalen Schema haben (d. h. sie sind im Profilspeicher, aber nicht im relationalen Speicher vorhanden). Und da die koordinierte Kampagne vom relationalen Schema aus funktioniert, werden die nicht übereinstimmenden `customer_id` (**2**) aus der **Zielgruppe lesen** entfernt und nur die *übereinstimmenden*, **7**, sind in nachfolgenden Aktivitäten verwendbar, die **relationalen Daten** in der Kampagne nutzen

![Vorschau der Ergebnisse mit Profilen, denen eine übereinstimmende Target-Dimension fehlt](assets/read-an-audience-missing-target-dimension.png)

>[!NOTE]
>
>Die folgenden Schritte verwenden die relationalen Daten, um die oben aufgeführte Aussage zu bestätigen, dass nicht übereinstimmende `customer_id` verworfen werden.

&#x200B;4. Klicken Sie auf **Stoppen**, um den **Testmodus** der Kampagne zu stoppen

![Schaltfläche „Anhalten“ zum Beenden des Kampagnentestmodus](assets/read-an-audience-stop-test-mode.png)

&#x200B;5. Klicken Sie auf das **+** am Ende des Flusses und fügen Sie **Aufspaltung** aus den **Targeting-Aktivitäten**

![Menü Zielgruppenbestimmungsaktivitäten mit ausgewählter Aufspaltung](assets/read-an-audience-add-split-activity.png)

&#x200B;6. Erweitern Sie im Detailbereich der Aktivität **Aufspaltung** die erste Aufspaltung namens „Teilmenge **&#x200B;**

![Detailbereich der Aufspaltungsaktivität mit erweitertem Segment der Teilmenge](assets/read-an-audience-expand-subset-split.png)

&#x200B;7. Benennen Sie ihn in &quot;**Store** um und klicken Sie auf **Filter erstellen** um die Filterbedingung festzulegen

![Segment wurde mit der Option Filter erstellen in In Store umbenannt](assets/read-an-audience-rename-in-store-segment.png)

&#x200B;8. Klicken **im Bereich** Filter erstellen“ auf **Bedingung hinzufügen**

![Filterbereich mit der Schaltfläche „Bedingung hinzufügen“ erstellen](assets/read-an-audience-add-condition-button.png)

&#x200B;9. Da keine anderen Attribute aus dem AEP-Profil extrahiert wurden, ist das einzige hier verfügbare AEP-Profilattribut das `Customer ID`. Es stehen jedoch Spalten aus dem relationalen Speicher, der der entsprechenden Zieldimension entspricht, zum Einrichten der Filterbedingung zur Verfügung. Erweitern Sie die **Zielgruppendimension** durch Klicken auf **>**

![Die Zielgruppendimension wurde erweitert, um relationale Speicherspalten anzuzeigen](assets/read-an-audience-expand-targeting-dimension.png)

&#x200B;10. Wählen Sie `Source` aus der Liste aus und klicken Sie auf **Bestätigen**

![Aus den Spalten der Zielgruppendimension ausgewähltes Source-Attribut](assets/read-an-audience-select-source-attribute.png)

&#x200B;11. Die unterschiedlichen Werte für die Source-Spalte sind in der Dropdown-Liste verfügbar. Wählen Sie für **Benutzerdefinierte Bedingung** aus der Dropdown-Liste die Option **„In Store“** und klicken Sie auf **Bestätigen**, um den Vorgang zu beenden

![Benutzerdefinierte Bedingung auf „In Store“ festgelegt](assets/read-an-audience-set-in-store-condition.png)

&#x200B;12. Zurück im Detailbereich der Aktivität **Aufspaltung** sind die Einstellungen für die erste Aufspaltung abgeschlossen. Klicken Sie auf **Segment hinzufügen**, um die zweite Aufspaltung zu aktualisieren

![Schaltfläche Segment hinzufügen im Detailbereich der Aufspaltungsaktivität](assets/read-an-audience-add-segment-button.png)

Ein neues Segment mit dem Namen **Ergebnis** wird erstellt

![Neues Segment mit dem Namen „Result“](assets/read-an-audience-new-result-segment.png)

&#x200B;13. Benennen Sie &quot;**Ergebnis**&quot; in &quot;**Nicht im Speicher** um und klicken Sie auf **Filter erstellen**, um die Filterbedingung festzulegen

![Segment wurde mit der Filteroption in „Nicht im Speicher“ umbenannt](assets/read-an-audience-rename-not-in-store-segment.png)

&#x200B;14. Klicken Sie im **Filter erstellen** auf **Bedingung hinzufügen**. Folgen Sie demselben Ansatz wie oben, erweitern Sie die **Zielgruppendimension** indem Sie auf **>** klicken, wählen Sie dann `Source` aus der Liste aus und klicken Sie auf **Bestätigen**

![Die Zielgruppendimension wurde erweitert, um relationale Speicherspalten anzuzeigen](assets/read-an-audience-expand-targeting-dimension.png)

![Aus den Spalten der Zielgruppendimension ausgewähltes Source-Attribut](assets/read-an-audience-select-source-attribute.png)

&#x200B;15. Wählen Sie für **Benutzerdefinierte Bedingung** aus der Dropdown-Liste die Option **„In Store“** und wählen Sie für den Operator &quot;**ungleich**. Klicken Sie auf **Bestätigen**, um den Vorgang zu beenden

![Benutzerdefinierte Bedingung auf ungleich „In Store“ festgelegt](assets/read-an-audience-set-not-in-store-condition.png)

&#x200B;16. Zurück im Detailbereich der Aktivität **Aufspaltung** sind die Einstellungen für die beiden Aufspaltungen abgeschlossen. Klicken Sie auf **Starten**, um die Kampagne im **Testmodus“**

![Schaltfläche „Starten“ zum Ausführen der Kampagne im Testmodus nach der Konfiguration der Aufspaltung](assets/read-an-audience-start-test-mode-second-run.png)

&#x200B;17. Die Testausführung beginnt, und die Ergebnisse werden nach Abschluss angezeigt. Da nur **7** übereinstimmende Zieldimensionen im relationalen Schema gefunden wurden, wird dieselbe Anzahl auch nach den Aufspaltungsvorgängen (**7** und **0**) beobachtet

![Ergebnisse der Aufspaltung mit Zahlen von 7 und 0](assets/read-an-audience-verify-split-counts.png)

&#x200B;18. Klicken Sie auf jedes Ergebnisfeld und **Vorschau der Ergebnisse**, um die Ergebnisse anzuzeigen

![Option „Vorschau der Ergebnisse“ für jedes Teilungs-Ergebnisfeld](assets/read-an-audience-preview-split-results.png)

&#x200B;19. Klicken Sie auf **Stoppen**, um den **Testmodus** der Kampagne zu stoppen

![Stopp-Taste zum Beenden des endgültigen Testmodus-Durchgangs](assets/read-an-audience-stop-test-mode-final.png)

>[!NOTE]
>
>Während beim Audience lesen **9** Profile angezeigt wurden. Da wir einen Filter für Source erstellt haben und das Feld &quot;Source&quot; im relationalen Speicher vorhanden ist, mussten wir den Profilspeicher mit dem relationalen Speicher verbinden, um ihn zu überprüfen. Als es über die Campaign Target Dimension mit dem relationalen Schema verbunden wurde, stimmten nur insgesamt **7** Profile überein. Diese **7** übereinstimmenden Kunden-IDs sind für die Verwendung in den folgenden Aktivitäten verfügbar, die versuchen, relationale Daten zu verwenden. Alle **7**-Kunden-IDs `Source` auf **„In Store“**, was durch die Aufspaltungsflüsse deutlich wurde.
>
>Daher ist die Gewährleistung der Datenkonsistenz von entscheidender Bedeutung, wenn AEP-Profile zusammen mit ihren relationalen Gegenstücken zur Anreicherung verwendet werden.

>[!TIP]
>
>Herzlichen Glückwunsch! Damit ist die Übung zur Verwendung der Aktivität „Zielgruppe lesen“ mit dem relationalen Schema abgeschlossen.

## Zusammenfassung

Sie haben jetzt gesehen, wie einfach es ist, eine Kampagne zu erstellen, eine Aktivität „Zielgruppe lesen“ zusammen mit der Dimension „Profilzielgruppe“ durchzuführen, um das relationale Schema zu nutzen. Sie haben die Aufspaltungsaktivität verwendet, um die Zielgruppe basierend auf einer Bedingung aufzuteilen. Schließlich hat der Testmodus dabei geholfen zu verstehen, dass es wichtig ist, die Datenkonsistenz zwischen dem Profil und dem relationalen Schema zu gewährleisten.

Weitere Informationen finden [&#x200B; (hier](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/orchestrated-campaigns/design-campaigns/read-audience) wenn Sie Interesse haben.
