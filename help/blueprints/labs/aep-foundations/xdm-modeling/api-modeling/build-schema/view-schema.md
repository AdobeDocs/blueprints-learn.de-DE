---
hold: true
title: Schema anzeigen
description: Zeigen Sie ein neu erstelltes Kundenschema sowohl in der Experience Platform-Benutzeroberfläche als auch über einen API-Aufruf zum Abrufen eines Schemas an.
doc-type: article
solution: Experience Platform
exl-id: 29302546-46dc-4c97-8fd8-deab6977635c
source-git-commit: 2b2b9b9c359c4cc6757ac62ad502ece9a4923095
workflow-type: tm+mt
source-wordcount: '220'
ht-degree: 0%

---


# Schema anzeigen

## Über die Benutzeroberfläche anzeigen

1. Öffnen Sie Ihren Browser und navigieren Sie zurück zum Abschnitt `Schema -> Browse` .

>[!NOTE]
>
>Aktualisieren Sie die Benutzeroberfläche, um sie anzuzeigen, da Sie sie gerade erstellt haben und die Schemaregistrierung erneut abfragen müssen

2. Nach dem `Sample Customer Schema - <your sandbox number>` suchen

3. Beachten Sie, dass die erforderliche Klasse und die zugehörigen Feldergruppen zum Schema hinzugefügt werden

![Kundenbeispielschema, das in der Experience Platform-Benutzeroberfläche mit den Klassen- und Feldergruppen angezeigt wird](assets/view-schema-ui-view-of-sample-customer-schema.png "UI-Ansicht des Beispielkundenschemas")


## Über die API anzeigen

1. Wählen Sie die `Step 5 - Get Customer Account Schema`-API aus, indem Sie darauf klicken.
1. Ersetzen Sie in der URL der Anfrage die `<replace me>` durch die `$meta:altId`, die Sie im vorherigen Abschnitt (Schema erstellen) bis zum Ende des Aufrufs gespeichert haben, wie unten dargestellt
1. Speichern Sie die an der Anfrage vorgenommenen Änderungen
1. Ausführen der Anfrage durch Klicken auf die Schaltfläche `Send`

![Schritt 5: Aufruf der API für das Kundenkontenschema abrufen](assets/view-schema-step-5-get-customer-account-schema.jpeg "Schritt 5: Abrufen des Kundenkontenschemas")



Beispiel für die endgültige Anfrage nach dem Hinzufügen des `$meta:altId`

![Schritt-5-Anfrage mit dem Meta:altId-Anhang an die URL](assets/view-schema-final-step-5-request.png "Endgültige Schritt-5-Anfrage")



Wenn Sie eine `200 OK` Antwort erhalten haben, sollten Sie in der Lage sein, das von Ihnen erstellte Schema einfach durch die Linse der XDM-JSON-Struktur zu durchsuchen

![200 OK-Antwort mit dem vollständigen Beispiel-Kundenkontenschema JSON](assets/view-schema-sample-customer-account-schema.png "Muster-Kundenkontenschema")
