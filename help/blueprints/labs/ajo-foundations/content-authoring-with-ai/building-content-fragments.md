---
title: Erstellen von Inhaltsfragmenten
description: Erfahren Sie, wie Sie einen E-Mail-Entwurf in wiederverwendbare Fragmente unterteilen, z. B. einen Kopfzeilenblock, die in allen Vorlagen in Adobe Journey Optimizer konsistent bleiben.
doc-type: article
solution: Experience Platform
exl-id: 253a9332-dc08-420d-ac11-2bf342f0dc38
source-git-commit: 3039df0c022176e9dada9c5a300f2df14429033d
workflow-type: tm+mt
source-wordcount: '899'
ht-degree: 0%

---


# Erstellen von Inhaltsfragmenten

## Inhaltserstellung mit Vorlagen und Fragmenten

**Zweck:** Erfahren Sie, wie Sie wiederverwendbare Fragmente in Adobe Journey Optimizer erstellen und sie dann in einer echten E-Mail in einem Journey anwenden.

## Lernziele

Am Ende dieses Moduls haben Sie folgende Möglichkeiten:

1. Unterteilen Sie ein E-Mail-Design in wiederverwendbare Fragmente.
1. Erstellen Sie Header-, Footer-, Banner-, Body- und CTA-Fragmente.

## Warum Fragmente wichtig sind

Mit Fragmenten können Sie konsistente, markenorientierte Inhalte erstellen, die in E-Mails, Kampagnen und Journey wiederverwendet werden können.

### Fragmente

Wiederverwendbare Bausteine wie:

- Kopfzeilen
- Footers
- CTAS
- Banner
- Rechtliche Haftungsausschlüsse

Jedes Mal, wenn ein Fragment aktualisiert wird, werden alle E-Mails, die es verwenden, automatisch aktualisiert.

## Wie dies in die E-Mail-Erstellung passt

- **Erstellen Sie Fragmente** für Elemente, die sich nur selten ändern.
- **Erstellen Sie eine Vorlage** die diese Fragmente verwendet.
- **Verwenden Sie die Vorlage** in Ihrer Kampagnen-E-Mail und passen Sie ihren Inhalt an.

Nachfolgend finden Sie die endgültige E-Mail, die Sie aus diesem Labor erstellen werden.

![Endgültiges E-Mail-Design, das Sie in diesem Labor erstellen](assets/building-content-fragments-final-email-preview.png)

Das Design-Team stellt Ihnen jedoch normalerweise Vorlagen wie diese zur Verfügung:

![Vom Design-Team bereitgestellte generische Design-Vorlage](assets/building-content-fragments-generic-design-template.png)


## Schritt 1: Erstellen Sie Inhaltsfragmente

Die folgende Vorlage ist eine allgemeine Design-Vorlage, und unser Ziel ist es, sie in wiederholbare Inhaltsblöcke aufzuteilen. In Adobe Journey Optimizer wird dies als &quot;**&quot;**.

Der erste Schritt besteht darin, festzustellen, wie viele Fragmente wir erstellen müssen. In dieser Vorlage ist es sinnvoll, wie unten gezeigt 5 Fragmente zu verwenden.



![Vorlage, die in fünf identifizierte Fragmente unterteilt ist](assets/building-content-fragments-five-fragments-identified.png)

Wir haben die Vorlagen identifiziert, die 5 Fragmente erfordern wie folgt.

- Kopfzeile
- Banner
- CTA
- Textkörper
- Footer

>[!NOTE]
>
>Für diese Übung erstellen Sie nur ein Header-Fragment, um Zeit zu sparen.



Erstellen Sie zunächst ein Header-Fragment. Richten Sie jedoch vor dem Erstellen des Fragments einen Asset-Ordner ein, da die Assets-Umgebung freigegeben ist. Erstellen Sie dazu zunächst einen eigenen Ordner.

1. Suchen Sie in der linken Navigation den Abschnitt **Content-Management** und klicken Sie auf **Assets**.

![Abschnitt „Content-Management“ mit der Option &quot;Assets&quot; im linken Navigationsbereich](assets/building-content-fragments-content-management-assets-nav.png)

2. Klicken Sie im Abschnitt &quot;Assets-**&quot; auf** Assets.

![Assets-Option im Abschnitt &quot;Assets-Verwaltung“](assets/building-content-fragments-assets-under-assets-management.png)

3. Erstellen Sie einen Ordner, indem Sie auf **Schaltfläche „Ordner erstellen** klicken.

![Schaltfläche „Ordner erstellen“ im Bereich &quot;Assets&quot;](assets/building-content-fragments-click-create-folder-button.png)

4. Geben Sie einen Namen wie Ihren Vor- und Nachnamen an. Beispiel: Nish\_Pithia\_LabAssets (Etwas, an das Sie sich erinnern können)

![Benennung des neuen Asset-Ordners mit Vor- und Nachnamen](assets/building-content-fragments-name-asset-folder.png)

5. **Neues Fragment erstellen:** Klicken Sie unter „Content-Management“ auf **Fragmente** und erstellen Sie ein neues Fragment.

   ![Option „Fragmente“ unter „Content-Management“, um ein neues Fragment zu erstellen](assets/building-content-fragments-click-fragments-create-new.png)

   Geben Sie einen Anzeigenamen wie unten gezeigt an. Fügen Sie alle Details wie folgt hinzu:

   **name:**-Kopfzeile

   **Beschreibung:** Fragment-Kopfzeile für die Vorlage

   **Typ:** visuelles Fragment auswählen

   ![Felder für Kopfzeilenfragmentnamen, Beschreibung und Typ des visuellen Fragments](assets/building-content-fragments-fragment-name-type-details.png)

6. Klicken Sie oben **auf** Schaltfläche „Erstellen“.

![Erstellen-Schaltfläche oben rechts im Dialogfeld Neues Fragment](assets/building-content-fragments-click-create-button-top-right.png)

Dadurch wird ein leerer Bildschirm zur Fragmenterstellung geöffnet.

7. Klicken Sie unter Strukturen auf 1:1 Spalten und ziehen Sie wie unten dargestellt auf die Arbeitsfläche. (Bitte klicken Sie auf das Bild unten, um eine animierte Grafik zu sehen)

![Animierte Demo zum Ziehen einer 1:1-Spaltenstruktur auf die Fragment-Arbeitsfläche](assets/building-content-fragments-drag-1-1-columns-structure.gif)

8. Ziehen Sie als Nächstes &quot;**image** auf die gerade hinzugefügte Zeile 1:1 .

![Ziehen einer Bildkomponente auf die 1:1-Zeile](assets/building-content-fragments-drag-image-onto-row.png)

9. Laden Sie das bereitgestellte Logo-Bild hoch. Klicken Sie auf **Schaltfläche „Medien importieren“**

![Schaltfläche „Medien importieren“, um das Logo-Bild hochzuladen](assets/building-content-fragments-click-import-media-button.png)

10. **Logo hochladen:** Laden Sie das Logo (*C5G-Logo.png*) aus dem Toolkit-Ordner mit Bildern hoch und klicken Sie auf Weiter.

![Auswählen von C5G-Logo.png aus dem Toolkit-Ordner zum Hochladen](assets/building-content-fragments-upload-logo-select-file.png)

![Klicken Sie auf Weiter , nachdem Sie den Logo-Upload ausgewählt haben](assets/building-content-fragments-upload-logo-click-next.png)

11. Wählen Sie den **Asset-Ordner** aus, den Sie erstellt haben, und klicken Sie dann auf **Importieren**. Die Datei wird im Ordner gespeichert.

![Auswählen des erstellten Asset-Ordners und Klicken auf „Importieren“](assets/building-content-fragments-select-asset-folder-import.png)

12. Das Logo ist korrekt platziert, aber es ist zu groß und muss in der Größe verändert werden. Um die Größe des Logos zu ändern, aktualisieren Sie seine Eigenschaften. Klicken Sie auf **Registerkarte Stil** und legen Sie die Breite auf 40 % fest, indem Sie den Schieberegler ziehen, wie unten dargestellt.

>[!NOTE]
>
>Beachten Sie, dass, wenn die Umschalter-Schaltfläche aktiviert ist, die 40-Zahl für % und nicht für Pixel steht. Wenn Sie einen absoluten Wert für die perfekte Pixelanzahl wünschen, schalten Sie die Schaltfläche auf px um.



![Der Regler für die Breite der Registerkarte „Stil“ ist auf 40 Prozent eingestellt, um die Größe des Logos zu ändern](assets/building-content-fragments-resize-logo-width-slider.png)

13. Klicken Sie auf **Speichern** und Ihr Fragment wird gespeichert. Bei der Bestätigung wird eine Benachrichtigung mit einem grünen Balken angezeigt.

![Grüne Bestätigungsleiste nach dem Speichern des Fragments](assets/building-content-fragments-save-fragment-confirmation.png)

14. Das Fragment wird im Entwurfsmodus gespeichert. Bevor Sie sie verwenden, müssen Sie sie veröffentlichen. Klicken Sie auf die Schaltfläche **Zurück**.

![Schaltfläche „Zurück“, um den Fragmententwurf vor der Veröffentlichung zu verlassen](assets/building-content-fragments-click-back-button-draft.png)

15. Klicken Sie auf **Schaltfläche „Veröffentlichen**. Es wird die Meldung „Fragment wird veröffentlicht, dies kann einige Zeit dauern. Wir benachrichtigen Sie, sobald dies geschehen ist.“ Bei Bestätigung. Ihr Fragment ist bereit für die Vorlagenerstellung.

![Schaltfläche „Veröffentlichen“ und Bestätigungsmeldung zum Veröffentlichen des Fragments](assets/building-content-fragments-click-publish-fragment-button.png)

Sie sehen den Statuswechsel zu **„Live“**. An dieser Stelle ist der Aufbau eines Header-Fragments abgeschlossen, das im nächsten Schritt verwendet wird.

![Der Header-Fragmentstatus wurde in Live geändert](assets/building-content-fragments-fragment-status-live.png)

>[!NOTE]
>
>In dieser Übung haben Sie nur ein Fragment erstellt. In der Praxis können Architekten mehrere Fragmente erstellen, z. B. Kopf- und Fußzeilen oder andere wiederverwendbare Komponenten.

## Zusammenfassung

In diesem Modul haben Sie erfolgreich:

- Aufschlüsselung einer E-Mail in wiederverwendbare Header-Fragmente
- Erstellen von Kopfzeilen-Inhaltsblöcken

Sie können jetzt mit dem nächsten Modul fortfahren: **Erstellen einer Inhaltsvorlage** in dem Sie das von Ihnen erstellte Fragment zur Erstellung einer neuen Vorlage verwenden.
