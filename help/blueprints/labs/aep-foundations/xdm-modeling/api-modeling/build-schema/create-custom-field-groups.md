---
title: Erstellen benutzerdefinierter Feldergruppen
description: Verwenden Sie die Schema Registry-API, um eine benutzerdefinierte Feldergruppe für Kundenkontodetails zu erstellen und ihre $id zur Verwendung in einem späteren Schema zu speichern.
doc-type: article
solution: Experience Platform
exl-id: d3262db9-7c0b-476a-843f-1a2c224ee792
source-git-commit: 96308d5726def849ef22540a5d13618017c40cc3
workflow-type: tm+mt
source-wordcount: '458'
ht-degree: 0%
---

# Erstellen benutzerdefinierter Feldergruppen

## Struktur der Feldergruppen

Eine Feldergruppe besteht immer aus den folgenden Feldern. Dies wird im nächsten Schritt in der Anfrage angezeigt.

| Erforderliche Werte | Beschreibung |
| --------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Anrede | Der Name der Feldergruppe, die Sie in der Schemaregistrierung erstellen möchten. Der Name MUSS EINDEUTIG SEIN. |
| Beschreibung | Eine kurze Beschreibung des Zwecks der Feldergruppe |
| Typ | Immer ein Objekt |
| meta\:intendedToExtend | Definiert, mit welchen Klassen die Feldergruppe verwendet werden kann. Klassen werden immer durch ihren `$id` referenziert |
| allOf | Beschreibt die Ressourcen, die in die Feldergruppe aufgenommen werden können. Bei benutzerdefinierten Feldern wird der Pfad immer `#/definitions/customFields` |
| definition.customFields… | Dies ist die standardmäßige JSON-Schemastruktur, die zum Erstellen benutzerdefinierter Feldergruppen erforderlich ist. Sie muss mit dem `allOf` von oben übereinstimmen |
| \&lt;TENANT\_NAME> | Der Mandantenname (d. h. der eindeutige Name) wird während des Bereitstellungsprozesses erstellt. Dadurch wird sichergestellt, dass vorgenommene Anpassungen nicht mit bestehenden oder künftigen Änderungen an der Adobe-Schemaregistrierung in Konflikt stehen |



## Feldergruppe „Kundenkontodetails erstellen“

1. Klicken Sie im Ordner `XDM Schema Lab -> Create Schema` auf den API-Aufruf `Step 2 - Create Customer Account Details Field Group` Anfrage .



![Schritt 2: Feldergruppen-API-Anfrage für Kundenkontodetails erstellen](assets/create-custom-field-groups-step-2-field-group-request.png "Schritt 2: Feldergruppe „Kundenkontodetails erstellen“")



Überprüfen Sie den Text der Anfrage, bevor Sie sie ausführen. Beachten Sie, dass die im Abschnitt Feldergruppenstruktur erwähnten erforderlichen Felder wie folgt aussehen:

![Erforderliche Felder einer benutzerdefinierten Feldergruppe, wie in der Struktur „Hauptteil/Feldergruppe](assets/create-custom-field-groups-field-group-structure.png " der Anfrage gezeigt")



![Die allOf-Eigenschaft, die auf die benutzerdefinierten Felddefinitionen Pfad](assets/create-custom-field-groups-field-group-structure-allof.png " Feldgruppenstruktur allOf verweist")

>[!NOTE]
>
>Beachten Sie, dass im Bild rechts oben der `allOf` auf den Pfad von &quot;/definitions/customFields“ verweist.  Diese muss mit der im Schema definierten Struktur übereinstimmen (Bild links), da sie dem XDM-System mitteilt, wo die benutzerdefinierten erstellten Objekte zu finden sind.
>
>![Vergleich, der hervorhebt, wie der allOf-Pfad mit dem Pfad der benutzerdefinierten Felddefinitionen übereinstimmen muss](assets/create-custom-field-groups-allof-path-highlighted.png)



Beachten Sie außerdem, wie jedes einzelne Feld aus dem Zuordnungsblatt innerhalb der XDM-JSON-Struktur erhärtet wird.



![Zuordnung von Tabellenplan-Punktnotation zu XDM JSON-Struktur](assets/create-custom-field-groups-plan-dot-notation-to-xdm-json.png "Plan-Punktnotation zu XDM JSON")



![Das Zuordnungsblatt für die Punktnotation zur Kunden-ID wurde in die Punktnotation zur Kunden](assets/create-custom-field-groups-account-customer-id-dot-notation-to-xdm.png "Konto- und Kunden-ID zu XDM konvertiert")



1. Aktualisieren Sie die `title` und `description` für die Feldergruppe im folgenden Format: `Customer Account Details - Sandbox <your number here>`



   ![Beispieltitel und Beschreibung ausgefüllt für die benutzerdefinierte Feldergruppe](assets/create-custom-field-groups-field-group-title-description-example.png " Feldgruppe Titel und Beschreibung Beispiel")



1. Führen Sie durch Klicken auf die Schaltfläche `Send` aus.  Es sollte eine -Antwort ähnlich der im folgenden Screenshot angezeigt werden.

1. Kopieren Sie den `$id` Wert der neu erstellten Feldergruppe Kundenkontodetails .

![Erfolgreiche API-Antwort nach der Erstellung der benutzerdefinierten Feldergruppe](assets/create-custom-field-groups-step-2-create-custom-field-group-success.png "Schritt 2: Erstellen einer benutzerdefinierten Feldergruppe - Erfolg")

>[!WARNING]
>
>Fahren Sie erst fort, wenn Sie die `$id` an einer anderen Stelle gespeichert haben.  Später muss das Kundenkontenschema erstellt werden
>
>
