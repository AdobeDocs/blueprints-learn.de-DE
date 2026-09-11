---
title: Profilklasse abrufen
description: Rufen Sie die API der globalen Schemaregistrierung auf, um die $id der Klasse „XDM Individual Profile“ abzurufen und sie zur Verwendung in einem benutzerdefinierten Schema zu speichern.
doc-type: article
solution: Experience Platform
exl-id: d87c21a2-dad4-4666-b917-cdf8e16058d4
source-git-commit: 3039df0c022176e9dada9c5a300f2df14429033d
workflow-type: tm+mt
source-wordcount: '168'
ht-degree: 0%

---


# Profilklasse abrufen

## Schritt 3 ausführen - Profil-Klasse abrufen

1. Klicken Sie auf die `Step 3 - Get Profile Class` im `XDM API Lab -> Create Schema`
1. Führen Sie durch Klicken auf die Schaltfläche `Send` aus

![Schritt 3 - API-Anfrage für Profilklasse abrufen](assets/get-profile-class-step-3-api-request.jpeg "Schritt 3 - API-Anfrage für Profilklasse abrufen")

>[!NOTE]
>
>Beachten Sie, dass in der GET-Anfrage der `global` Pfad …/schemaRegistry/**global**/classes Denken Sie daran, dass die Verwendung von `global` der Schemaregistrierung mitteilt, dass wir nur standardmäßige Adobe-XDM-Objekte zurückgeben möchten


## Suchen und speichern Sie die Klasse $id

Nachdem Sie die API-Anfrage ausgeführt haben, führen Sie die folgenden Schritte aus, um die `$id` für die Klasse „XDM Individual Profile“ zu suchen und zu speichern.

1. Suchen Sie in der Antwort nach der Klasse `XDM Individual Profile` .
1. Kopieren Sie die `$id` für die `XDM Individual Profile` und speichern Sie sie an einem Ort, auf den Sie später verweisen können.

![Klasse „XDM Individual Profile“ in der API-Antwort](assets/get-profile-class-xdm-individual-profile-class.png "XDM Individual Profile-Klasse")

>[!WARNING]
>
>Fahren Sie erst fort, wenn Sie die `$id` an einer anderen Stelle gespeichert haben.  Später muss das Kundenkontenschema erstellt werden
