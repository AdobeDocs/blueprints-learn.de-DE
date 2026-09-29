---
title: Plan-Schema-ID abrufen
description: Fragen Sie die API der Mandanten-Schemaregistrierung ab, um die $id des Plan-Lookup-Schemas zur Verwendung in einem Beziehungsdeskriptor zu finden und zu speichern.
doc-type: article
solution: Experience Platform
exl-id: f66e0483-b5b3-4493-b752-c4e00211a8bd
product_v2:
  - id: edbd1a0e-46c8-49da-8c10-dba9ec80bba9
    internal-label: Experience Platform
source-git-commit: 1d6ba1444c119437eb8a86d5c4a1050d56d16023
workflow-type: tm+mt
source-wordcount: '171'
ht-degree: 0%
---

# Plan-Schema-ID abrufen

## Auflisten aller Mandantenschemas

1. Klicken Sie auf die `Step 1 - Get Lookup Schemas`-API-Anfrage im Ordner `XDM Schema Lab -> Create Relationship Descriptors` .
1. Führen Sie die API aus, indem Sie auf die Schaltfläche `Send` klicken

![Schritt 1: API-Anfrage „Suchschemata abrufen](assets/get-plan-schema-id-step-1-get-lookup-schemas.jpeg "Schritt 1: Suchschemata abrufen")

>[!NOTE]
>
>Dieser GET-Aufruf ruft alle Schemata ab, die im „Mandanten“-Teil der Schemaregistrierung vorhanden sind (d. h. benutzerdefinierte erstellte Schemata). Wir müssen nur nach dem Schema **Plan** suchen, um es mit dem Kundenkontenschema verknüpfen zu können.



## Planschema identifizieren

1. Suchen Sie in `dep: Plan [Lookup] ` Anrufantwort nach dem Schema .
1. Kopieren Sie die `$id` des Schemas und speichern Sie sie zur späteren Verwendung an einem anderen Speicherort

![Das Schema „dep: plan lookup schema $id“ befindet sich in der API-Antwort](assets/get-plan-schema-id-dep-lookup-plan-schema-sid.png "dep: Lookup Plan schema $id")

>[!NOTE]
>
>Dieses Schema sollte bereits in Ihrer Sandbox bereitgestellt werden

>[!WARNING]
>
>Fahren Sie erst fort, wenn Sie `$id` des Schemas an einer anderen Stelle gespeichert haben.  Später muss der Beziehungsdeskriptor erstellt werden
