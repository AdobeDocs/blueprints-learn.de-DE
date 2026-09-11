---
title: Erstellen einer Inhaltsvorlage
description: Erfahren Sie, wie Sie eine wiederverwendbare E-Mail-Vorlage in Adobe Journey Optimizer erstellen, indem Sie HTML importieren und ein zuvor erstelltes Header-Fragment einfügen.
doc-type: article
solution: Experience Platform
exl-id: e73f06b1-be8a-4096-949c-900db13db9f8
source-git-commit: 3039df0c022176e9dada9c5a300f2df14429033d
workflow-type: tm+mt
source-wordcount: '839'
ht-degree: 0%

---


# Erstellen einer Inhaltsvorlage

## Inhaltserstellung mit Vorlagen und Fragmenten

**Zweck:** Erfahren Sie, wie Sie wiederverwendbare Vorlagen in Adobe Journey Optimizer erstellen.

## Lernziele

Am Ende dieses Moduls haben Sie folgende Möglichkeiten:

1. Erstellen Sie eine vollständige E-Mail-Vorlage mit importiertem HTML und Fragmenten.

## Warum Vorlagen wichtig sind

Mit Vorlagen können Sie konsistente, markenorientierte Inhalte erstellen, die in E-Mails, Kampagnen und Journey wiederverwendet werden können.

### Vorlagen

Blueprints mit folgender Struktur:

- Header-Platzierung
- Body-Inhaltsbereich
- Bereich der Fußzeile
- Standard-Layout-Stile

Vorlagen sorgen für eine Team-übergreifende Markenkonsistenz und sparen viel Erstellungszeit.


## Erstellen einer neuen Vorlage mit Fragmenten

Mithilfe von Vorlagen können Benutzer die vollständigen Layouts in Kampagnen wiederverwenden. Inhaltsvorlagen in Adobe Journey Optimizer sind leistungsstarke Tools, die die Erstellung wiederverwendbarer Inhalte für Kampagnen und Journey vereinfachen und optimieren. Unabhängig davon, ob Sie E-Mail-, SMS- oder Push-Benachrichtigungs-Vorlagen erstellen, sparen Sie Zeit, indem Sie vordefinierte Strukturen bereitstellen, die einfach angepasst und projektübergreifend freigegeben werden können.

Für einen beschleunigten und verbesserten Design-Prozess erstellen Sie eigenständige Vorlagen, um benutzerdefinierte Inhalte in Journey Optimizer-Kampagnen und -Journey einfach wiederzuverwenden.

Diese Funktion ermöglicht inhaltsorientierten Benutzenden die Arbeit an Vorlagen außerhalb von Kampagnen oder Journey. Marketing-Benutzer können diese eigenständigen Inhaltsvorlagen dann in ihren eigenen Journey oder Kampagnen wiederverwenden und anpassen.

## Vorlage erstellen

1. Navigieren Sie **Content-Management → Inhaltsvorlagen**.

![Navigieren Sie zu Content-Management und dann zu Inhaltsvorlagen](assets/building-content-template-navigate-content-templates.png)

&#x200B;2. Klicken Sie **Vorlage erstellen** und füllen Sie Folgendes aus:
   - **name:** `Promotional Template`
   - **Beschreibung:** `Promotional Template for phone products`
   - **channel:** `Email`

![Erstellen eines Vorlagenformulars mit Namen, Beschreibung und E-Mail-Kanal](assets/building-content-template-create-template-form-fields.png)

&#x200B;3. Wählen Sie **Erstellen** aus.

![Schaltfläche „Erstellen“, um die Erstellung der Werbevorlage abzuschließen](assets/building-content-template-click-create-button.png)


## Betreffzeile hinzufügen und Email Designer öffnen

1. Betreffzeile hinzufügen: `Promotional Template` und klicken Sie auf **auf den E-Mail-**, um ihn zur Bearbeitung zu öffnen

![Hinzufügen der Betreffzeile und Öffnen des E-Mail-Textkörpers zur Bearbeitung](assets/building-content-template-add-subject-line-open-editor.png)

&#x200B;2. Es werden drei Optionen angezeigt:
   1. Von Grund auf gestalten
   2. Eigenen Code erstellen
   3. HTML importieren

Wählen Sie die dritte Option aus. Klicken Sie **HTML importieren**



![Auswahl der Option HTML importieren aus den drei Design-Optionen](assets/building-content-template-select-import-html-option.png)

## Importieren der bereitgestellten HTML-Vorlage



1. Hochladen der HTML-Vorlagendatei aus dem Toolkit-Ordner `promotional-template-final.html`

![Hochladen der Datei „promotional-template-final.html“ aus dem Toolkit-Ordner](assets/building-content-template-upload-html-template-file.png)

&#x200B;2. Klicken Sie auf die Schaltfläche Importieren **importieren** um die Vorlage zu importieren.

![Importschaltfläche zum Importieren der hochgeladenen HTML-Vorlage](assets/building-content-template-click-import-button.png)

&#x200B;3. Warten Sie, bis das Layout gerendert wird. Sie bemerken Probleme wie fehlerhafte Bild-Links und fehlendes Branding. (Dies ist das erwartete Verhalten, da wir über Platzhalter-Assets verfügen)

![Gerenderte Vorlage mit fehlerhaften Bild-Links und fehlenden Branding-Platzhaltern](assets/building-content-template-rendered-template-broken-images.png)


## Erkunden der Vorlagenstruktur

### Linkes Bedienfeld

Die Komponenten **Strukturen** und **Inhalte** in Adobe Journey Optimizer (AJO) sind wesentliche Elemente, die beim Entwerfen von E-Mails, Landingpages und Inhaltsfragmenten verwendet werden. Strukturen definieren das Layout-Framework, während Inhalte die tatsächlichen Bausteine bereitstellen, die innerhalb dieser Layouts platziert sind.

Der Hauptteil-Abschnitt in Adobe Journey Optimizer ist der Haupt-Container für Ihre E-Mail oder Ihren Seiteninhalt. Er dient als Stamm für den visuellen Design-Bereich, in dem alle Strukturkomponenten (Spalten, Layouts) und Inhaltskomponenten (Text, Bilder, Schaltflächen usw.) verschachtelt sind.

### Rechtes Bedienfeld

Mit den Optionen **Einstellungen** und **Stil** im Hauptteil von Adobe Journey Optimizer können Sie das grundlegende Erscheinungsbild und Layout Ihrer E-Mail oder Seite definieren. Diese Steuerelemente wirken sich auf das gesamte Design aus, da der Hauptteil allen Komponenten übergeordnet ist.

![Einstellungen und Stiloptionen im rechten Bedienfeld für den Hauptteil](assets/building-content-template-body-settings-style-panel.png)


In der Leiste auf der linken Seite finden Sie Abschnitte für:

- Fragmente
- Dateien
- Körperstruktur
- Getrackte URLs

Das Header-Fragment, das Sie in der vorherigen Übung erstellt haben, wird hier angezeigt, wie unten dargestellt. Stellen Sie sicher, dass Ihr Header-Fragment mit einem blauen Punkt live angezeigt wird und sich nicht im Entwurfsmodus befindet. Verbringen Sie Zeit mit der Überprüfung der übrigen Abschnitte.

![Kopfzeilenfragment wird mit einem blauen Punkt in der linken Seitenleiste live angezeigt](assets/building-content-template-header-fragment-live-sidebar.png)

&#x200B;> [!NOTE]
>
>Wenn Ihr Fragment hier nicht angezeigt wird, bedeutet dies, dass Sie es nicht ordnungsgemäß gespeichert haben und erneut hochladen müssen.



## Einfügen von Header-Fragmenten

Verbessern Sie jetzt die Vorlage . Sie haben die Kopf- und Fußzeile bereits erstellt.

1. Ziehen Sie eine **1:1-Spalte** über den vorhandenen Inhalt.

![Ziehen einer 1:1-Spalte über den vorhandenen Vorlageninhalt](assets/building-content-template-drag-1-1-column-above-content.png)

Man sieht so etwas.

![Vorlagen-Layout nach dem Hinzufügen der neuen Spalte über dem Inhalt](assets/building-content-template-column-added-above-content.png)

&#x200B;2. Ihr Hintergrund verwendet die Hintergrundfarbe der Vorlage, die derzeit schwarz ist. Legen Sie die **Hintergrundfarbe“ auf Weiß fest. Klicken** auf die Registerkarte Stil in der rechten Leiste und verwenden Sie eine weiße Farbe aus der Farbauswahl.

![Festlegen der Hintergrundfarbe der Spalte mithilfe der Farbauswahl auf Weiß](assets/building-content-template-set-background-color-white.png)

&#x200B;3. Öffnen Sie **Fragmente** und ziehen Sie das **Header**-Fragment hinein.

![Ziehen Sie das Header-Fragment aus dem Bereich „Fragmente“ in die Vorlage](assets/building-content-template-drag-header-fragment-into-template.png)

&#x200B;4. Beachten Sie, dass das Header-Fragment wie unten dargestellt sauber an Ihrer Vorlage ausgerichtet ist.

![Header-Fragment innerhalb der Vorlage sauber ausgerichtet](assets/building-content-template-header-fragment-aligned-template.png)

&#x200B;5. Klicken Sie auf **Speichern**, um Ihre Vorlage zu speichern, und klicken Sie dann auf **Zurück**.

![Speichern-Schaltfläche zum Speichern der Vorlage, bevor Sie auf „Zurück“ klicken](assets/building-content-template-click-save-button-template.png)

>[!NOTE]
>
>Beachten Sie, dass möglicherweise einige beschädigte Bilder angezeigt werden. Wir werden das später in Ordnung bringen.


## Zusammenfassung

In diesem Modul haben Sie erfolgreich:

- HTML importiert, um eine vollständige Werbevorlage zu erstellen

Sie können jetzt mit dem nächsten Modul fortfahren: **E-Mail erstellen**
