---
title: Sandbox-Zugriff
description: Überprüfen Sie, ob Ihre Postman-Umgebung Ihre zugewiesene Experience Platform-Sandbox erfolgreich abrufen kann, bevor Sie die Labs starten.
doc-type: article
solution: Experience Platform
exl-id: c841e497-a695-4d3f-85e6-d653478cad1e
source-git-commit: df6c1852a6e0357dc9f166c88e77dcf9d334f955
workflow-type: tm+mt
source-wordcount: '131'
ht-degree: 0%
---

# Sandbox-Zugriff

Bevor Sie fortfahren, überprüfen Sie erneut, ob Ihr Zugriff gültig ist. Führen Sie die folgenden Schritte aus:

1. Öffnen Sie den Ordner mit dem Titel `Check Sandbox Access` und klicken Sie auf den Aufruf mit dem Titel `Retrieve Your Sandbox`
1. Als Nächstes sehen Sie in der oberen rechten Ecke von Postman ein Dropdown-Feld Umgebung .  Wählen Sie unbedingt die `AEP Bootcamp` Umgebung aus
1. Führen Sie den Aufruf aus, indem Sie auf die Schaltfläche `Send` klicken.

![Postman-Anfragebereich für den Sandbox-Aufruf zum Abrufen Ihres Sandbox](assets/sandbox-access-check-sandbox-request.png "Aufrufs vor dem Senden/Abrufen Ihres Sandbox-API-Aufrufs")



Eine erfolgreiche Antwort sieht wie folgt aus:

![200 OK-Antwort, die den erfolgreichen Abruf der zugewiesenen Sandbox bestätigt](assets/sandbox-access-successful-response.png "200 OK Erfolgreiche Sandbox-Anfrage bestätigt")

>[!NOTE]
>
>Der **name**-Wert sollte mit der Variablen „sandbox\_name“ in Ihrer Postman-Umgebung übereinstimmen

>[!SUCCESS]
>
>Herzlichen Glückwunsch!  Sie können jetzt mit der Verwendung der Experience Platform-APIs beginnen
