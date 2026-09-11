---
title: Schema anzeigen
description: Zeigen Sie die Identitätsdeskriptoren eines Schemas über die Benutzeroberfläche und API an und vergleichen Sie die Accept-Header-Optionen für aufgelöste und nicht aufgelöste Schemaantworten.
doc-type: article
solution: Experience Platform
exl-id: 44eedb82-259f-4f7f-84fe-acc2b42376eb
source-git-commit: 3039df0c022176e9dada9c5a300f2df14429033d
workflow-type: tm+mt
source-wordcount: '468'
ht-degree: 0%

---


# Schema anzeigen

## Über die Benutzeroberfläche anzeigen

1. Öffnen Sie Ihren Browser und navigieren Sie zurück zum Abschnitt `Schema -> Browse` .
1. Suchen nach dem Schema **Kundenkonto**
1. Beachten Sie, dass die Identitäten zum Schema hinzugefügt werden

![Ansicht zum Durchsuchen von Schemata mit Identitäten, die zur Ansicht ](assets/view-schema-schema-ui-with-identities.png " Schema-Benutzeroberfläche mit Identitäten hinzugefügt wurden")


## Über die API anzeigen

1. Wählen Sie die `Step 3 - Get Customer Account Schema and its descriptors`-API aus, indem Sie darauf klicken.

![Schritt 3 - Kundenkontenschema mit Deskriptoren-API-Anfrage abrufen](assets/view-schema-step-3-get-customer-account-schema-w-descriptors.png "Schritt 3 - Kundenkontenschema mit Deskriptoren abrufen")



1. Ersetzen Sie in der URL der Anfrage die `<replace me>` durch die `$meta:altId`, die Sie im vorherigen Abschnitt (Schema erstellen) bis zum Ende des Aufrufs gespeichert haben, wie unten dargestellt

![Endgültige Schritt-5-Anfrage mit Alt-ID, die an die URL/Endgültige ](assets/view-schema-final-step-5-request.png "-5-Anfrage angehängt ist")



1. Speichern Sie die von Ihnen angeforderten Änderungen

1. Ausführen der Anfrage durch Klicken auf die Schaltfläche `Send`

Es sollte jetzt eine `200 OK` Antwort angezeigt werden und Sie sollten das von Ihnen erstellte Schema durch die Linse der XDM-JSON-Struktur durchsuchen können

![Hauptteil der API-Antwort, die die XDM-JSON-Struktur ](assets/view-schema-body-of-the-api-response.png " Schemas der API-Antwort anzeigt")



Navigieren Sie weiter unten in der API-Antwort, um die von Ihnen erstellten Identitätsdeskriptoren anzuzeigen

![Identitätsdeskriptoren, die in der API-Antwort angezeigt werden](assets/view-schema-descriptors-displayed-in-api-response.png "Deskriptoren, die in der API-Antwort angezeigt werden")


## Accept-Kopfzeilen

Beachten Sie die **Accept**-Kopfzeile, die in der Anfrage verwendet wird. Dieser Header teilt der XDM-Schemaregistrierung mit, dass sie die nicht aufgelösten `$refs` des Schemas (d. h. die minimal erforderlichen Informationen anzeigen) zusammen mit den zugehörigen Deskriptoren in der API-Antwort zurückgeben soll.  Adobe bietet weitere **Accept**-Kopfzeilen, mit denen Sie Details zum Schema erhalten können.

![Accept-Header-Feld in Schritt 3 Abrufen des Kundenkontenschemas - ](assets/view-schema-accept-header.png " 3 - Abrufen des Kundenkontenschemas - Accept-Header")

>[!NOTE]
>
>Weitere Informationen zu den verschiedenen Accept-Kopfzeilen finden Sie hier -> [Experience League Schema API-Endpunkt](https://experienceleague.adobe.com/docs/experience-platform/xdm/api/schemas.html?lang=en#lookup)



Um dies in Aktion zu sehen, ändern Sie die **Accept**-Kopfzeile, um der Schemaregistrierung mitzuteilen, dass sie mit allen `$ref` und `allOf` vollständig aufgelöst (d. h. aufgelöst) und allen zugehörigen Deskriptoren antworten soll

1. Aktualisieren Sie den Wert der `Accept`-Kopfzeile wie folgt:
   `application/vnd.adobe.xed-full-desc+json; version=1`
1. Speichern Sie Ihre Anfrage über die Schaltfläche `Save` .
1. Ausführen einer Anfrage über die Schaltfläche `Send`

Sie sollten jetzt eine Antwort sehen, die wie folgt aussieht:

![Vollständig aufgelöste Schemaantwort mit allen aufgelösten Eigenschaften](assets/view-schema-fully-exploded-schema-showing-all-properties.png "Vollständig aufgelöstes Schema mit allen Eigenschaften")

>[!NOTE]
>
>Beachten Sie, dass alle Eigenschaften des Schemas jetzt vollständig in der Antwort angezeigt werden, während Ihnen im vorherigen Aufruf nur die `$ref` Werte des Schemas angezeigt wurden (d. h. welche Feldergruppen es referenziert hat) und nichts für jedes einzelne Feld/jede einzelne Eigenschaft vollständig aufgelöst wurde.

>[!NOTE]
>
>Dies ist wichtig, um zu verstehen, da Sie bei der Arbeit mit -APIs nicht immer die vollständig aufgelöste Antwort benötigen, wenn Sie lediglich die `$id` des Schemas abrufen oder dessen Komposition überprüfen
