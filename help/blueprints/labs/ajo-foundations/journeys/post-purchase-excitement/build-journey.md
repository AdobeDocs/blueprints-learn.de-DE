---
title: Build-Journey
description: Erstellen Sie eine einheitliche Journey, die auf ein Bestellversandereignis reagiert, eine benutzerdefinierte Aktion für den Versand von ETA aufruft und eine personalisierte E-Mail sendet.
doc-type: article
solution: Experience Platform
exl-id: 4dd15071-51e5-445a-932d-690d9a73a913
source-git-commit: 3039df0c022176e9dada9c5a300f2df14429033d
workflow-type: tm+mt
source-wordcount: '1061'
ht-degree: 0%

---


# Build-Journey

## Lernziel

Erstellen Sie eine einheitliche Journey, die mit dem konfigurierten Ereignis Bestellung versendet beginnt, die ETA von einem externen Service abruft und eine E-Mail sendet.

## Journey erstellen

Wechseln Sie zu **Journey** und klicken Sie auf **Journey erstellen - Von Grund auf neu erstellen**

![Erstellen einer Journey - Erstellen von neuen Inhalten im Adobe Journey Optimizer-Bildschirm](assets/build-journey-create-journey-from-scratch.png)



## Journey-Eigenschaften

1. Aktualisieren Sie die Journey-Eigenschaften in der rechten Leiste wie folgt:
   - **Name**: `Order Shipped Journey`
   - **Beschreibung**: `Notify customer that order has shipped. Include shipping details.`
   - **Tags**: `Default`
   - **Journey-Metriken**: *leer lassen*

     >[!NOTE]
     >
     >**Leere Dropdown?**
     >
     >Mach dir keine Sorgen und mach weiter. Die allererste Journey, die in einer Sandbox erstellt wird, muss „die Pumpe vorbereiten“.  Sobald wir die Journey veröffentlicht haben, stehen in diesem Dropdown Optionen zur Auswahl.

   - **Erneuten Eintritt erlauben**: `checked`

   - **Wartezeit bis zum erneuten Eintritt:** `5 minutes`

   - **Zugriffsbeschriftungen**: *leer lassen*

   - **Zeitzone**: `Your Local timezone`

   - **Zeitzone des Profils für Wartezeiten und Bedingungen verwenden**: `NOT checked`

   - **Start-/Enddatum**: *leer lassen*

   - **Zeitüberschreitung oder Fehler**: `30`

   - **Begrenzungsregeln:** *leer lassen*

   - **Priorität**: `0`



2. Wenn alles gut aussieht, klicken Sie auf die Schaltfläche **Speichern**.

![Schaltfläche „Speichern“ für das Bedienfeld &quot;Journey-Eigenschaften“](assets/build-journey-save-journey-properties.png)




## Journey-Arbeitsfläche

### Unitäres Ereignis hinzufügen

Ziehen Sie aus dem linken Bereich unter dem Menü **Ereignisse** das Ereignis **orderShipped** wie unten dargestellt auf die Arbeitsfläche

![Ziehen Sie das orderShipped-Ereignis aus dem Menü Ereignisse auf die Journey-Arbeitsfläche](assets/build-journey-drag-order-shipped-event-onto-canvas.png)



![Versandereignis auf der Journey-Arbeitsfläche bestellen](assets/build-journey-drag-order-shipped-event-onto-canvas--2.png)





### Hinzufügen einer benutzerdefinierten Aktion

1. Wenn der linke Bereich das **Menü Aktionen** erweitert und dann die von Ihnen erstellte Aktion mit dem Namen „GetShippingDetails **nach dem** „orderShipped“ auf die Arbeitsfläche zieht

![Ziehen Sie die benutzerdefinierte Aktion GetShippingDetails nach dem orderShipped-Ereignis auf die Arbeitsfläche](assets/build-journey-drag-getshippingdetails-action-onto-canvas.png)

2. Stellen Sie in der rechten Leiste unter der Konfiguration von Zugriff und Datenschutz —> Dropdown-Liste Marketing-Aktion sicher, dass der Wert auf &quot;**&quot;**

![Dropdown-Liste Marketing-Aktion auf Keine in Zugriffs- und Datenschutzkonfiguration festgelegt](assets/build-journey-set-marketing-action-to-none.png)

3. Klicken Sie im Menü Endpunktkonfiguration > Abfrageparameter auf das **Stiftsymbol** neben orderid

![Stiftsymbol zum Bearbeiten des Abfrageparameters „orderid“ in der Endpunktkonfiguration](assets/build-journey-edit-orderid-query-parameter.png)

4. Erweitern Sie in dem erscheinenden Modal **Kontext** -> **orderShipped** -> **Order** und wählen Sie dann **Order ID (orderID)** und klicken Sie auf **OK**

![Wählen Sie Order ID (orderID) aus den Kontextfeldern orderShipped Order aus](assets/build-journey-select-order-id-context-field.png)

5. Stellen Sie sicher, dass die Option Zeitüberschreitung oder Fehler in der rechten Leiste **nicht aktiviert** ist, und klicken Sie dann auf die Schaltfläche **Speichern**

![Option „Zeitüberschreitung“ oder „Fehler“ nicht aktiviert, mit hervorgehobener Schaltfläche „Speichern“](assets/build-journey-uncheck-timeout-or-error.png)



### E-Mail-Aktion hinzufügen

1. Ziehen Sie im Menü Aktionen die Aktion **Aktion** nach der Aktion GetShippingDetails auf die Arbeitsfläche

![Ziehen Sie den Knoten Aktion nach der Aktion GetShippingDetails auf die Arbeitsfläche](assets/build-journey-drag-email-action-onto-canvas.png)

2. Wählen Sie **Marketing** Aktion „E-Mail“ und dann **Hinzufügen** aus.

![Wählen Sie E-Mail als Marketing-Aktion aus und klicken Sie auf Hinzufügen](assets/build-journey-select-email-marketing-action.png)

3. Klicken Sie in der rechten Leiste auf **Aktion konfigurieren**

![Aktionsschaltfläche in der rechten Leiste konfigurieren](assets/build-journey-click-configure-action.png)

4. Legen Sie **E-Mail-**) auf `Profile-Email` fest und klicken Sie dann auf **Inhalt bearbeiten**

![Die Konfiguration des E-Mail-Kanals wurde auf Profil-E-Mail mit dem Link „Inhalt bearbeiten“ festgelegt](assets/build-journey-set-profile-email-channel-configuration.png)



### E-Mail-Textkörper-Inhalt hinzufügen

Für den Inhalt werden Sie die Dinge einfach halten. Wie dumm, einfach.

1. Aktualisieren Sie die Betreffzeile auf `Order Shipped` und klicken Sie dann auf die Schaltfläche **E-Mail-Textkörper bearbeiten**

![Betreffzeile aktualisiert, um die Schaltfläche „E-Mail-Textkörper bearbeiten“ für die Bestellung zu verwenden](assets/build-journey-update-subject-line-order-shipped.png)

2. Klicken Sie in der oberen Leiste auf den Inhaltsbaustein **Von Grund auf** Entwerfen“

![Erstellen von neuen Inhalten in der oberen Leiste](assets/build-journey-click-design-from-scratch.png)

3. Ziehen Sie aus der linken Leiste unter dem Struktur-Container die Spalte **1:1)** die Arbeitsfläche

![Ziehen Sie das 1:1-Spaltenstrukturelement auf die E-Mail-Arbeitsfläche](assets/build-journey-drag-1-1-column-onto-canvas.png)

4. Ziehen Sie dann unter dem Inhalts-Container die Komponente **Text** in Ihre **1:1-Spalte**

![Ziehen Sie die Textkomponente in die 1:1-Spalte](assets/build-journey-drag-text-component-into-column.png)

5. Klicken Sie auf die Textkomponente und **den aktuellen Text löschen** und klicken Sie dann auf das Symbol **Personalization hinzufügen**.

![Symbol &quot;Personalization hinzufügen“ nach dem Löschen des Standardtextes](assets/build-journey-click-add-personalization-icon.png)

6. Klicken Sie in der linken Leiste auf den Ordner **Kontextuelle Attribute** navigieren Sie dann durch **Journey Orchestration** -> **Aktionen** und wählen Sie **GetShippingDetails**

![Wählen Sie GetShippingDetails unter Kontextuelle Attribute - Journey Orchestration - Aktionen aus](assets/build-journey-select-getshippingdetails-contextual-attribute.png)

7. Kopieren Sie im Hauptteil der E-Mail **kopieren und fügen Sie** folgende JSON in den Personalization-**ein**

```json
{{profile.person.name.firstName}}, your order has shipped
ETA: 
Tracking Number: 
```

8. Fügen Sie die Personalisierungsfelder wie folgt hinzu (**klicken Sie auf das Pluszeichen &quot;+&quot; neben dem Feld in der linken Leiste**):
   - **ETA:** `eta`
   - **Tracking-Nummer:** `tracking_number`

![Der E-Mail hinzugefügte Personalisierungsfelder für ETA und Tracking-Nummer](assets/build-journey-add-eta-tracking-number-fields.png)

>[!NOTE]
>
>Klicken Sie auf das **+-**, um Personalisierungsattribute aus der Leiste zur Arbeitsfläche hinzuzufügen.  Dadurch werden sie dort platziert, wo sich Ihr Cursor befindet, sodass Sie entsprechend „ausgerichtet“ sind

>[!NOTE]
>
>Ihre E-Mail verwendet eine Kombination aus Kontextattributen (ETA und Tracking-Nummer) und Profilattributen (Vorname). Wenn Sie weitere Profilattribute hinzufügen möchten, klicken Sie auf die Registerkarte Profilattribute und wählen Sie die gewünschten Informationen aus.
>
>![Registerkarte „Profilattribute“ zum Hinzufügen zusätzlicher Profilattribute](assets/build-journey-profile-attributes-tab.png)

9. Klicken Sie am unteren Bildschirmrand auf die Schaltfläche **Validieren** und stellen Sie sicher, dass Sie keine Fehler haben

![Schaltfläche „Validieren“, die unten auf dem Bildschirm ohne Fehler angezeigt wird](assets/build-journey-click-validate-button.png)

10. Wenn alles gut aussieht, klicken Sie auf **Speichern** oben rechts
11. Klicken Sie dann oben rechts erneut auf **Speichern** und dann oben links auf den **\&lt;- Pfeil nach links**

![Schaltfläche „Speichern“ und der Pfeil „Zurück“ oben rechts und oben links](assets/build-journey-save-and-back-arrow.png)

12. Klicken Sie schließlich oben links auf das Symbol **\&lt; Zurück**, um zur Journey-Arbeitsfläche zurückzukehren

![Zurück-Symbol oben links, um zur Journey-Arbeitsfläche zurückzukehren](assets/build-journey-back-icon-to-journey-canvas.png)

>[!TIP]
>
>Klicken Sie dann erneut auf **Zurück**… Scherz! Das ist der letzte Zurück-Button…in diesem Abschnitt 😜



### E-Mail-Parameter überschreiben

Stellen Sie auf der Haupt-Journey-Arbeitsfläche im E-Mail-Knoten sicher, dass Sie die schreibgeschützten Felder sehen können (Sie müssen möglicherweise auf das Symbol **Schreibgeschützte Felder anzeigen** klicken)

![Schreibgeschützte Felder, die auf dem E-Mail-Knoten auf der Journey-Arbeitsfläche angezeigt werden](assets/build-journey-show-read-only-fields-email-node.png)

1. Scrollen Sie nach unten zu **E-Mail** Parameter und klicken Sie auf das Symbol **Parameterüberschreibungen aktivieren**.

![Symbol „Parameterüberschreibungen aktivieren“ unter „E-Mail-Parameter“](assets/build-journey-enable-parameter-override.png)

2. Klicken Sie in das leere Textfeld und gehen Sie dann in der linken Leiste nach unten zu **Kontext** -> **orderShipped** -> **\_dep** und klicken Sie auf das Feld **personalEmail**.  Klicken Sie dann auf **OK**

![Wählen Sie das Feld personalEmail unter orderShipped context _dep](assets/build-journey-select-personalemail-context-field.png)

>[!WARNING]
>
>Dies ist eine gefährliche Sache. Vermeiden Sie es daher, es sei denn, Sie müssen es in einer Produktionsumgebung tun.  Dadurch wird der Standardspeicherort überschrieben, nach dem Journey im Profil suchen, um Nachrichten auszuführen.



3. Klicken Sie oben rechts auf **Speichern** und anschließend auf den **Rückwärtspfeil** \&lt;- oben links, um die Journey zu ****

![Speichern-Taste und Rückwärtspfeil zum Schließen der Journey](assets/build-journey-save-and-close-journey.png)

## Zusammenfassung

Eine veröffentlichte Journey, die auf den Trigger „Versand bestellen“ reagieren kann, die ETA von einem externen Service abruft und eine E-Mail sendet.
