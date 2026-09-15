---
title: Schema ändern - JSON-Patch
description: Verwenden Sie einen JSON PATCH-API-Aufruf, um einer bestehenden Mandantenfeldgruppe ein neues Feld hinzuzufügen und die Änderung im Schema zu sehen.
doc-type: article
solution: Experience Platform
exl-id: c0313594-d998-4525-a0a4-d9d844bed5ef
source-git-commit: df6c1852a6e0357dc9f166c88e77dcf9d334f955
workflow-type: tm+mt
source-wordcount: '805'
ht-degree: 0%
---

# Schema ändern - JSON-Patch

## Übersicht

Angenommen, Sie müssen nach dem Erstellen des Schemas dem `plan`-Objekt ein zusätzliches Feld namens `planDescription` hinzufügen. Diese Notwendigkeit kann auftreten, weil Sie beim Erstellen des Schemas vergessen haben, es hinzuzufügen, oder weil es eine Anfrage war, die in Monaten später kam. Um diese Aufgabe auszuführen, führen Sie einen `PATCH` aus, der das Schema mit dem neuen Feld aktualisiert.

Weitere Informationen zu JSON PATCH finden Sie unter den folgenden Links. Nehmen wir an, Sie haben für dieses Labor ein allgemeines Verständnis davon, wie es funktioniert.

- [https://jsonpatch.com/](https://jsonpatch.com/)
- [Experience League API-Grundlagen](https://experienceleague.adobe.com/docs/experience-platform/landing/platform-apis/api-fundamentals.html?lang=de#json-patch)

![Diagramm zum Patchen eines fehlenden PlansDescription-Felds in ein vorhandenes Schema](assets/modify-schema-json-patch-patching-missing-plan-description-field.png "Patchen in einer fehlenden Feldplanbeschreibung")

>[!NOTE]
>
>Denken Sie an die folgenden Punkte:
>
>- Ein Schema besteht aus einer Klasse und einer oder mehreren Feldergruppen
>- Sie müssen einer Feldergruppe neue Felder hinzufügen, bevor Sie sie einem Schema hinzufügen. Diese Einschränkung stellt die Wiederverwendbarkeit eines Felds über jedes Schema hinweg sicher, das diese Feldergruppe verwendet.



Um ein neues Feld zu einem Schema hinzuzufügen, müssen Sie die folgenden Vorgänge in der richtigen Reihenfolge ausführen. Dieser Prozess ist das, was Sie in den folgenden Laborschritten tun.

- Identifizieren Sie die Feldergruppe, der Sie die neue Eigenschaft hinzufügen möchten
- Erstellen eines JSON-PATCH-Aufrufs zum Aktualisieren der Feldergruppe
- Ausführen des JSON-PATCH-Aufrufs zum Aktualisieren der Feldergruppe (die das Schema erbt)



## Suchen und identifizieren Sie die zu aktualisierende Feldergruppe

1. Wählen Sie den `Step 1 - Get Tenant Field groups` API-Aufruf im Ordner `XDM Schema Lab -> Customize Schema` aus
1. Ausführen der Anfrage durch Klicken auf die Schaltfläche `Send`

   ![Schritt 1: Anfrage zum Abrufen von Mandantenfeldgruppen-](assets/modify-schema-json-patch-step-1-get-tenant-field-groups.png "Schritt 1: Abrufen von Mandantenfeldgruppen")

   >[!NOTE]
   >
   >Denken Sie daran, dass Sie das `plan`-Objekt innerhalb einer benutzerdefinierten Feldergruppe erstellt haben. Benutzerdefinierte Objekte in der XDM-Schemaregistrierung werden als „Mandant“ bezeichnet. Daher wird der API-Aufruf unter Verwendung des `/schemaregistry/tenant/mixins/`-Pfads durchgeführt.



1. Suchen Sie in der Antwort nach der Schema-ID für die benutzerdefinierte Feldergruppe, die Sie zuvor mit dem Titel `Customer Account Details - Sandbox <your number here> ` erstellt haben

1. Kopieren Sie die `$meta:altId` und speichern Sie sie an einem sicheren Ort, wie Sie sie für den nächsten Schritt benötigen

![Finden der benutzerdefinierten Feldergruppe „Kundenkontodetails“ in der API-Antwort](assets/modify-schema-json-patch-search-field-group-response.jpeg "Suchen Sie in der Antwort nach der Feldergruppe „Kundenkontodetails“")

>[!CAUTION]
>
>Stellen Sie sicher, dass Sie die richtige Feldergruppe zum Kopieren auswählen! Verwenden Sie nicht die Feldergruppe mit dem ähnlichen Namen `dep: Customer Account Details`

>[!WARNING]
>
>Sie benötigen die `$meta:altId` für zukünftige Laborschritte, also speichern Sie sie irgendwo, bevor Sie fortfahren



## Suchen der Feldergruppe nach $meta\:altId

1. Wählen Sie den `Step 2 - Fetch path for the object to be modified`-API-Aufruf im `XDM Schema Lab -> Customize Schema` aus
1. Ersetzen Sie in der URL der Anfrage den `<replace me>` durch den `$meta:altId`, den Sie vom vorherigen Abschnittsschritt bis zum Ende des Aufrufs gespeichert haben, wie unten dargestellt
1. Speichern Sie die an der Anfrage vorgenommenen Änderungen
1. Ausführen der Anfrage durch Klicken auf die Schaltfläche `Send`

![Schritt 2 - Pfad für das zu ändernde Objekt abrufen API-Aufruf](assets/modify-schema-json-patch-step-2-fetch-object-path.jpeg "Schritt 2 - Pfad für das zu ändernde Objekt abrufen Schritte")



Überprüfen Sie die Antwort und beachten Sie, dass der JSON-Zeigerpfad für das **plan**-Objekt mit jeder der unten hervorgehobenen Eigenschaften erstellt wurde.

![Hervorgehobene Eigenschaften, aus denen der JSON-Zeigerpfad zum Planobjekt besteht](assets/modify-schema-json-patch-customer-account-details-path-to-the-plan-object.png "Kundenkontodetailpfad zum Planobjekt")



Der vollständig erstellte Pfad sieht wie folgt aus:  Kopieren Sie diesen Pfad und speichern Sie ihn zur Referenz

```none
/definitions/customFields/properties/_devbc/properties/plan/properties
```

>[!NOTE]
>
>Denken Sie daran, den oben genannten Mandantennamen (\_devbc) mit Ihrem eigenen zu aktualisieren



## PATCH - die Feldergruppe

### Beispiel für einen JSON PATCH-API-Hauptteil

```none
[
    {
        "op": "",
        "path": "",
        "value": {
            "title": "",
            "type": "",
            "description": ""
        }
    }
]
```

- **op (Vorgang)** -> stellt eine Anweisung bereit, welche Aktion die PATCH durchführen soll
- **Path** -> Dies ist der Pfad, den Sie erstellen, aktualisieren oder löschen möchten (d. h. der JSON-Zeiger auf den Speicherort des neuen Felds)
- **Wert** -> Dies ist ein optionales Feld und wird nur beim Erstellen oder Ersetzen eines vorhandenen Felds verwendet



### Ausführen der API-Anfrage

1. Klicken Sie auf den `Step 3 - Modify Tenant Field group` API-Aufruf im Ordner `XDM Schema Lab -> Customize Schema` .

   ![Schritt 3 - API-Aufruf für Mandantenfeldgruppe ändern](assets/modify-schema-json-patch-step-3-modify-tenant-field-group.png "Schritt 3 - Mandantenfeldgruppe ändern")



2. Aktualisieren Sie den Text der Anfrage mit den folgenden Informationen

   - **op** ->` add`
   - **path** -> `path from previous step +`&#x200B;` the new field name`
   - **value** ->
     - **title** -> `Plan Description`
     - **type** -> `string`
     - **description** -> `High-level details about the plan`

   Wenn Sie fertig sind, sollte Ihre API-Anfrage in etwa wie folgt aussehen

   ![Abgeschlossener JSON-PATCH-Anfragetext, der das Feld „planDescription“ hinzufügt](assets/modify-schema-json-patch-step-3-final-call-example.png " Schritt 3 - Beispiel für einen endgültigen Aufruf")

   >[!WARNING]
   >
   >Stellen Sie sicher, dass Sie den neuen Feldnamen **planDescription** in Ihren Pfad aufnehmen



3. Wenn alles gut `Save` deinem Anruf aussieht

4. `Execute` des Aufrufs zum Ausführen der PATCH

Es wird eine `200 OK` Antwort und das `planDescription` Feld in Ihrer Feldergruppe angezeigt, wie in diesem Beispiel:

![200 OK-Antwort nach erfolgreichem Patchen der Feldergruppe mit planBeschreibung](assets/modify-schema-json-patch-step-3-200-ok-successful-patch.png "Schritt 3 - 200 OK Erfolgreiche PATCH")

>[!SUCCESS]
>
>Herzlichen Glückwunsch! Sie haben eine Feldergruppe/ein Schema mithilfe von JSON PATCH erfolgreich aktualisiert.



## Änderung in der Benutzeroberfläche anzeigen

Durchsuchen Sie Ihr Schema über die Benutzeroberfläche und zeigen Sie Ihr neu hinzugefügtes Feld an.

![Feld „Planbeschreibung“ wird im Schema nach dem JSON-Patch in der Experience Platform-Benutzeroberfläche angezeigt.](assets/modify-schema-json-patch-plan-description-added-to-field-group.png " Beschreibung des Plans zur Feldergruppe Kundenkontodetails - Sandbox \&lt;Ihre Nummer> hinzugefügt. Schema-JSON ändern")
