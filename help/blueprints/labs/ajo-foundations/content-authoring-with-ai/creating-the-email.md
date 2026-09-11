---
title: E-Mail erstellen
description: Erfahren Sie, wie Sie in Adobe Journey Optimizer eine markenspezifische Inhaltsvorlage auf eine Kampagnen-E-Mail anwenden und Hero- und Produktbilder ersetzen.
doc-type: article
solution: Experience Platform
exl-id: bf823714-7298-48fc-a18b-9bf2462ae52e
source-git-commit: 3039df0c022176e9dada9c5a300f2df14429033d
workflow-type: tm+mt
source-wordcount: '669'
ht-degree: 0%

---


# E-Mail erstellen

## Inhaltserstellung mit Vorlagen

**Zweck:** Erfahren Sie, wie Sie wiederverwendbare Vorlagen in Adobe Journey Optimizer erstellen und sie dann in einer echten E-Mail innerhalb einer Kampagne anwenden.

## Lernziele

Am Ende dieses Moduls haben Sie folgende Möglichkeiten:

1. Erstellen Sie eine neue Kampagne und verwenden Sie Ihre neue gebrandete Vorlage.
1. Aktualisieren Sie Hero-Bilder, Produktbilder, Schaltflächen und Layout-Stile.

## Erstellen und Aktualisieren der E-Mail in einer Kampagne

### Ziel

In dieser Übung erfahren Sie, wie Sie die von Ihnen erstellte Vorlage auf eine E-Mail in einem Journey anwenden. In einem idealen Szenario können Sie jede vorhandene Journey oder Kampagne verwenden und ihren E-Mail-Inhalt durch eine standardisierte Vorlage ersetzen, um Markenkonsistenz und eine schnellere Ausführung sicherzustellen.

Dieser Schritt zeigt, wie Vorlagen in allen Journey wiederverwendet werden können, sodass Teams Designs aktualisieren können, ohne E-Mails von Grund auf neu erstellen zu müssen.

## Neue E-Mail-Kampagne erstellen

1. Kehren Sie zum Hauptbildschirm zurück und klicken Sie auf **Kampagnen → Journey**.
2. Klicken Sie auf **Kampagne erstellen**

![Schaltfläche „Kampagne erstellen“ in der Kampagnenverwaltung in Journey](assets/creating-the-email-click-create-campaign-button.png)

&#x200B;3. Wählen Sie &quot;**Orchestrierung - Marketing** aus und klicken Sie auf **Bestätigen**

![Orchestrierung auswählen - Marketing und auf „Bestätigen“](assets/creating-the-email-select-orchestration-marketing.png)

&#x200B;4. Benennen Sie Ihre `Flagship Phone Launch Branded`. Drücken Sie **Speichern**.

![Benennung des Kampagnen-Flaggschiffs „Telefonstart“ und Klicken auf „Speichern“](assets/creating-the-email-name-campaign-save.png)

&#x200B;5. Klicken Sie auf das **+-** und wählen Sie die Aktivität **Zielgruppe lesen** aus

![Pluszeichen zur Auswahl der Aktivität „Zielgruppe lesen“](assets/creating-the-email-click-plus-read-audience.png)

&#x200B;6. Der nächste Schritt besteht darin, **Feld „Zielgruppe lesen** auszuwählen und auf das Symbol **Zielgruppenordner“ zu klicken**

![Feld „Zielgruppe lesen“ und Symbol für Zielgruppenordner](assets/creating-the-email-read-audience-folder-icon.png)

&#x200B;7. Wählen Sie die **dep: Interested in iPhone 17** Audience aus und klicken Sie auf **Schaltfläche „Audience hinzufügen**.

![Auswählen der an iPhone 17 interessierten Zielgruppe und Klicken auf „Zielgruppe hinzufügen“](assets/creating-the-email-select-audience-add-button.png)

&#x200B;8. Entität auswählen - **dep-rel: Kundenkonto - customer\_id** (oder beliebige, da es für diesen Teil nicht von Bedeutung ist)
&#x200B;9. Fügen Sie die Aktivität **E-Mail** hinzu, indem Sie auf **+** klicken und dann **E-Mail** aus den Kanalaktivitäten auswählen.

![Hinzufügen der E-Mail -Aktivität aus Kanalaktivitäten](assets/creating-the-email-add-email-channel-activity.png)

&#x200B;10. Klicken Sie auf **E-Mail**.

![Option „E-Mail bearbeiten“ für die Kampagnen-E-Mail-Aktivität](assets/creating-the-email-click-edit-email.png)

&#x200B;11. Klicken Sie auf die **Aktion** und wählen Sie **Ihre** E-Mail-Konfiguration aus. Ihre Sandbox zeigt dies möglicherweise als relationale E-Mail an. (Beliebig auswählen)

![Registerkarte „Aktion“ mit ausgewählter E-Mail-Konfiguration](assets/creating-the-email-action-tab-email-configuration.png)

&#x200B;12. Klicken Sie auf **Registerkarte Inhalt**

![Registerkarte „Inhalt“ im E-Mail-Editor](assets/creating-the-email-click-content-tab.png)

&#x200B;13. Klicken Sie auf **Inhaltsvorlage anwenden**

![Option „Inhaltsvorlage anwenden“ im E-Mail-Editor](assets/creating-the-email-click-apply-content-template.png)

&#x200B;14. Wählen Sie die von Ihnen erstellte Vorlage **„Werbevorlage** aus und klicken Sie auf **Bestätigen**

![Auswählen der Aktionsvorlage und Klicken auf „Bestätigen“](assets/creating-the-email-select-promotional-template-confirm.png)

&#x200B;15. Klicken Sie auf **E-Mail-Textkörper bearbeiten**

![Option „E-Mail-Textkörper bearbeiten“ nach dem Anwenden der Vorlage](assets/creating-the-email-click-edit-email-body.png)

&#x200B;16. Bestätigen Sie, dass die neuen Kopfzeilen-, Helden-, Fußzeilen- und Inhaltsblöcke korrekt angezeigt werden.

![Kopfzeilen-, Helden-, Fußzeilen- und Inhaltsblöcke werden in der E-Mail korrekt angezeigt](assets/creating-the-email-header-hero-footer-blocks-confirmed.png)


## Hero-Bild und Produktbilder ersetzen

Ändern Sie die Bilder von Helden und Telefonen. Sie müssen Inhalte aus dem Toolkit-Ordner in Assets hochladen. Derzeit ist das Bannerbild für den Produktheld ein Platzhalter.

1. Klicken Sie auf das beschädigte Hero-Bannerbild.

![Klicken auf das Hero-Bannerbild des Platzhalters](assets/creating-the-email-click-broken-hero-banner-image.png)

&#x200B;2. Entfernen Sie die temporäre Quell-URL.

![Entfernen der temporären Quell-URL aus dem Bild](assets/creating-the-email-remove-temporary-source-url.png)

&#x200B;3. Klicken Sie auf **Medien importieren**

![Schaltfläche „Medien importieren“ für das Hero-Bild](assets/creating-the-email-click-import-media.png)

&#x200B;4. Laden Sie `hero.png` aus Ihrem Toolkit hoch. (Sie können die Datei ziehen)

![Hochladen von hero.png aus dem Toolkit-Ordner](assets/creating-the-email-upload-hero-png-file.png)

&#x200B;5. Klicken Sie auf **Weiter** Wählen Sie **Ihren Ordner für Assets** und drücken Sie **Importieren**

![Auswählen des Asset-Ordners und Klicken auf „Importieren“ für das Hero-Bild](assets/creating-the-email-select-folder-import-hero.png)

&#x200B;6. Ihre E-Mail-Vorlage kommt gut an. Sie sieht wie folgt aus. Klicken Sie auf **„Speichern“** um Ihre Arbeit zu speichern.

![E-Mail-Vorlage vor dem Speichern mit dem neuen Hero-Bild aktualisiert](assets/creating-the-email-save-updated-email-template.png)


## Optionale Übung

### Produktbilder ersetzen

Aktualisieren Sie dann alle Produktbilder (Bilder aus dem Toolkit-Ordner) und fügen Sie Ihren Wünschen einen abgerundeten Rahmen hinzu. Ihre E-Mail sieht ohne fehlerhafte Links schöner aus, wie unten dargestellt. Wiederholen Sie den Vorgang für alle Produktkarten.

![E-Mail mit allen aktualisierten Produktbildern und ohne fehlerhafte Links](assets/creating-the-email-product-images-updated-no-broken-links.png)

## Zusammenfassung

In diesem Modul haben Sie erfolgreich:

- Neue Kampagne mit E-Mail unter Verwendung Ihrer Markenvorlage erstellt
- Aktualisierte Hero- und Produktbilder
- Erweiterte Formatierung

Sie können jetzt mit dem nächsten Modul fortfahren - **KI-Assistent und Personalisierung von Inhalten** in dem Sie KI verwenden, um Text zu verfeinern und Bilder automatisch zu generieren.
