---
title: Schema anzeigen
description: Zeigen Sie die Lookup-Beziehung des Kundenkontenschemas zum Planschema sowohl über die Schema-Benutzeroberfläche als auch die GET-Schema-API an.
doc-type: article
solution: Experience Platform
exl-id: dae48ef4-f762-4173-8564-c1ad40c0109b
product_v2:
  - id: edbd1a0e-46c8-49da-8c10-dba9ec80bba9
    internal-label: Experience Platform
source-git-commit: 1d6ba1444c119437eb8a86d5c4a1050d56d16023
workflow-type: tm+mt
source-wordcount: '196'
ht-degree: 0%
---

# Schema anzeigen

## Über die Benutzeroberfläche anzeigen

1. Öffnen Sie Ihren Browser und navigieren Sie zurück zum Abschnitt `Schema -> Browse` .
1. Nach dem `Sample Customer Schema - <your sandbox number>` suchen
1. Beachten Sie, dass die Beziehung zum `dep: Plan [Lookup]` definiert ist

![Beispiel-Kundenschema in der Experience Platform-Benutzeroberfläche mit der Beziehung „dep: Plan-Lookup“](assets/view-schema-relationship-to-plan-lookup-schema.png)


## Über die API anzeigen

1. Wählen Sie die `Step 4 - Get Customer Account Schema and its descriptors`-API aus, indem Sie darauf klicken

   ![Schritt 4: Abrufen des Kundenkontenschemas und der zugehörigen Deskriptoren API-Aufruf](assets/view-schema-step-4-get-schema-and-descriptors.png "Schritt 4: Abrufen des Kundenkontenschemas und der zugehörigen Deskriptoren")



2. Ersetzen Sie in der URL der Anfrage die `<replace me>` durch die `$meta:altId`, die Sie im vorherigen Abschnitt [Schema erstellen](../build-schema/create-schema.md) gespeichert haben, wie unten dargestellt

   ![Schritt 4-Anfrage mit dem Meta-:altId, an die URL-](assets/view-schema-final-step-4-request.png "-Anfrage für Schritt 4 angehängt")



3. Speichern Sie die Anfrage mithilfe der Schaltfläche `Save` .

4. Ausführen der Anfrage durch Klicken auf die Schaltfläche `Send`

Sie sollten jetzt eine `200 OK` Antwort sehen und zum Ende des von Ihnen erstellten Schemas navigieren können, um die Identität durch die Linse der XDM-JSON-Struktur zu sehen



![Beziehungsdeskriptor, der im Kundenkontenschema-JSON-Beziehungsdeskriptor &#x200B;](assets/view-schema-relationship-descriptor.png " ist")



![Referenz-Identitätsdeskriptor sichtbar im Kundenkontenschema JSON](assets/view-schema-reference-identity-descriptor.png "Referenz-Identitätsdeskriptor")
