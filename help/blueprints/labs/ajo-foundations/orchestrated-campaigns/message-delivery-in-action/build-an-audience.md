---
hold: true
title: Erstellen einer Zielgruppe
description: Erfahren Sie, wie Sie mit der Aktivität „Zielgruppe aufbauen“ einfache Planmitglieder aus einem relationalen Schema auswählen und die resultierende Zeilenanzahl überprüfen können.
doc-type: article
solution: Experience Platform
exl-id: 7576e64b-d99a-4864-b877-f4ae77e1d7bd
source-git-commit: 2b2b9b9c359c4cc6757ac62ad502ece9a4923095
workflow-type: tm+mt
source-wordcount: '477'
ht-degree: 0%

---


# Erstellen einer Zielgruppe

## Ziel

In den nächsten Schritten erstellen Sie eine Audience aus dem relationalen Schema, indem Sie die richtige Zielgruppendimension auswählen und die entsprechenden Bedingungen festlegen. Sie werden auch die Option Aktualisieren verwenden, um die erwartete Anzahl der Zeilen zu überprüfen.

## Zielgruppe erstellen

1. Nachdem die Kampagne gerendert wurde, klicken Sie auf das **+** auf der Arbeitsfläche, um das Optionsmenü zu öffnen, und wählen Sie dann **Zielgruppe erstellen** aus den **Targeting-Aktivitäten**

![Zielgruppe aus den Zielgruppenbestimmungsaktivitäten erstellen](assets/build-an-audience-select-build-audience-activity.png)

2. Die **Zielgruppe aufbauen** öffnet den Detailbereich auf der rechten Seite und klicken auf das Suchsymbol, um die **Zielgruppendimension“**.

![Zielgruppendimension auswählen](assets/build-an-audience-select-targeting-dimension.png)

3. Wählen Sie `dep-rel: Customer Account` aus der Liste aus und klicken Sie auf **Bestätigen**

![Wählen Sie dep-rel: Kundenkontenschema](assets/build-an-audience-select-customer-account-schema.png)

4. Nachdem die **Zielgruppendimension** konfiguriert wurde, klicken Sie auf Zielgruppe erstellen , um den Prozess der Erstellung der Zielgruppe aus dem relationalen Schema zu starten

![Klicken Sie auf die Schaltfläche Zielgruppe erstellen ](assets/build-an-audience-create-audience-button.png)

5. Der Bereich Details der Zielgruppe erstellen wird geöffnet. Klicken Sie auf **Bedingung hinzufügen**

![Klicken Sie im Bereich „Zielgruppe erstellen“ auf „Bedingung hinzufügen“](assets/build-an-audience-add-condition.png)

6. Scrollen Sie nach unten und erweitern Sie die `dep-rel: Plan Lookup`, indem Sie neben **>** klicken

![Dep-rel erweitern: Plansuche](assets/build-an-audience-expand-plan-lookup.png)

7. Wählen Sie `dep-rel: Plan Name` und klicken Sie auf **Bestätigen**

![Wählen Sie Dep-rel: Planname](assets/build-an-audience-select-plan-name.png)

8. Belassen Sie im Bedienfeld Benutzerdefinierte Bedingung den Operator als „gleich“ und wählen Sie für Wert die Option Allgemein aus der Dropdown-Liste.

![Benutzerdefinierte Bedingung mit Planname gleich „Standard“](assets/build-an-audience-plan-name-equals-basic.png)

>[!NOTE]
>
>Beachten Sie, dass alle für die ausgewählte Spalte verfügbaren eindeutigen Werte in der Dropdown-Liste angezeigt werden, was die Erstellung der benutzerdefinierten Bedingungen erleichtert.



9. Klicken Sie bei konfigurierter benutzerdefinierter Bedingung auf das Aktualisierungssymbol, um die Anzahl zu berechnen und anzuzeigen. Es gibt zwei Stellen, an denen Sie die Ergebnisse berechnen können

![Klicken Sie auf das Aktualisierungssymbol, um die erwartete Zeilenanzahl zu berechnen](assets/build-an-audience-refresh-row-counts.png)

>[!NOTE]
>
>Der Aktualisierungsvorgang bewertet die Bedingung anhand der relationalen Daten und zeigt die erwarteten Ergebnisse an. Dieser Vorgang dauert in der Regel nur wenige Sekunden und ist äußerst nützlich, um die Kriterien anzupassen und sicherzustellen, dass er den Erwartungen entspricht.



10. Die Anzahl (**38**) gibt die Anzahl der Zeilen im relationalen Speicher an, die der angegebenen Bedingung entsprechen. Klicken Sie auf **Bestätigen**, um den Bereich **Zielgruppe erstellen** zu verlassen

![Zeilenanzahl bestätigen und Bereich „Zielgruppe erstellen“ verlassen](assets/build-an-audience-confirm-row-count.png)

>[!NOTE]
>
>Weitere Informationen finden Sie unter dem Abschnitt Regeleigenschaften . Klicken Sie auf **Ergebnisse anzeigen**, um die tatsächlichen Ergebnisse anzuzeigen. Verwenden Sie die **Code-Ansicht**, um die ausgeführte Abfrage anzuzeigen.

## Zusammenfassung

Sie haben jetzt gesehen, wie einfach es ist, die Aktivität Zielgruppe aufbauen in der Kampagne zu verwenden, indem Sie die richtige Zielgruppendimension aus dem relationalen Schema auswählen. Anschließend haben Sie eine Bedingung hinzugefügt, um die Kriterien für die Zielgruppenerstellung zu verfeinern, und die Option „Aktualisieren“ verwendet, um die erwartete Anzahl von Zeilen zu überprüfen.

Weitere Informationen finden [ (hier](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/orchestrated-campaigns/design-campaigns/build-audience) wenn Sie Interesse haben.
