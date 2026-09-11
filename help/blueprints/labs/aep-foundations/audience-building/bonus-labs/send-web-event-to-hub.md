---
title: Web-Ereignis an Hub senden
description: Erfahren Sie, wie Sie mit Postman ein Web-Ereignis direkt an den Hub senden und überprüfen Sie, ob es das Profil erreicht und für Streaming-Segmente qualifiziert ist.
doc-type: article
solution: Experience Platform
exl-id: a8343499-b4d5-4540-8fe1-7497bc20e437
source-git-commit: 3039df0c022176e9dada9c5a300f2df14429033d
workflow-type: tm+mt
source-wordcount: '500'
ht-degree: 0%

---


# Web-Ereignis an Hub senden

## Postman öffnen

Starten Sie Postman auf Ihrem Computer und navigieren Sie zum folgenden API-Aufruf:

1. **Postman linke Seitenleiste** —> `Collections`
1. **collection** —> `AEP Foundations Bootcamps (labs)`
1. **Ordner** —> Profile Lab
1. **API-Anfrage** —> `Create Web Event`

![Öffnen Sie die Anfrage „Web Event API erstellen“ in Postman](assets/send-web-event-to-hub-create-web-event-api-request.png)


## API-Anfrage ändern

Um eine Beispiel-API-Anfrage zu erstellen, müssen Sie die folgenden Teile im Hauptteil der API-Anfrage ausfüllen.

Erfassen Sie zunächst die folgenden Werte:



## Konto-Streaming-Endpunkt suchen

1. Navigieren Sie **linken Leiste zu** Quellen“ und klicken Sie dann **oberen Navigationsbereich auf** Konten“
1. Suchen Sie nach **dep: HTTP API \[raw]** markieren Sie die Zeile und kopieren und speichern Sie den Wert des **Streaming-Endpunkts** an einen anderen Ort, auf den Sie später verweisen können

Konto  und seinen Streaming-Endpunkt kopieren&rbrack;(assets/send-order-event-to-hub-http-api-raw-streaming-endpoint.png „dep: HTTP API \[raw]„)

## Web-Datenfluss-ID suchen

1. Klicken Sie in das **HTTP-API \[raw]** Konto
1. Suchen Sie die Datenflusszeile mit dem Namen **dep: Web (Stream)**
1. Kopieren Sie in der rechten Leiste die Werte **Datenfluss-ID** an eine Stelle, auf die Sie später verweisen können

>[!NOTE]
>
>Klicken Sie in ein leeres Feld in der Zeile.  Klicken Sie NICHT auf die blauen Links!

![Kopieren Sie die Datenfluss-ID für die Datenfluss-Web-Datenfluss-](assets/send-web-event-to-hub-web-stream-dataflow-id.png "-ID „dep:Web“")

## Endgültige API-Anfrage erstellen

Kopieren Sie die in den vorherigen Schritten gespeicherten Werte an die unten hervorgehobenen Stellen.

- **red** —> `Streaming Endpoint URL`
- **grün** —> `Dataflow ID`

Ihre endgültige API-Anfrage sollte dann wie folgt aussehen

&#x200B;> [!CAUTION]
>
>NOCH NICHT AUSFÜHREN!

![Anfrage zum Erstellen einer Web-Ereignis-API mit ausgefülltem Streaming-Endpunkt und Datenfluss-ID abgeschlossen](assets/send-web-event-to-hub-final-web-api-request.png)

## Ausführen der API

1. Speichern Sie den API-Aufruf, indem Sie auf die Schaltfläche **Speichern** klicken
1. Ausführen einer Anfrage durch Klicken auf die Schaltfläche **Senden**

Ein erfolgreicher Aufruf sollte zu der folgenden Antwort führen…

![Erfolgreiche API-Antwort nach dem Senden des Web-Ereignisses](assets/send-web-event-to-hub-successful-api-response.png)

## Validieren

1. Navigieren Sie zu Ihrem Profil und suchen Sie Ihr Profil, um zu sehen, ob das Ereignis in das Profil aufgenommen wurde.  Es sollte in Sekunden angezeigt werden.
   1. Verwenden Sie die E-Mail in Ihrem Aufruf, um das Profil zu suchen
1. Je nachdem, wie lange es her ist, seit Sie zuletzt ein Ereignis gesendet haben, sind Sie möglicherweise nicht für neue Segmente qualifiziert. Andernfalls können Sie diese oder andere sehen:
   1. Beliebige Event Edge (innerhalb von 15 Minuten)
      1. Denken Sie daran: Alle mit einer Edge-Auswertung gespeicherten Zielgruppen werden auch im Hub ausgewertet, wenn Streaming-Daten eingehen
   2. Tiefe: Beliebiges Ereignis-Streaming (innerhalb einer Stunde)
1. Möglicherweise wird an Ihrem Webhook nichts angezeigt, wenn Sie keine neuen Segmente haben.
1. Die Ereignisweiterleitung sendet nichts.
   1. Warum? Dieses Ereignis ging an den Hub, nicht an die Edge. Daher wird das Ereignis weder für die Ereignisweiterleitung zum Senden noch in Assurance als etwas angezeigt.
1. Nach mindestens 30 Minuten können Sie Ihren Datensatz sogar mit den folgenden Elementen überprüfen:
   1. Ändern Sie den unten stehenden Tabellennamen in den aus Ihrer Sandbox.  Um ihn zu finden, gehen Sie zu Ihrer Datensatzliste und filtern Sie nach &quot;`dest`&quot;, öffnen Sie den Datensatz und kopieren Sie den Tabellennamen in die rechte Leiste.

```sql
SELECT * FROM profile_export_for_destination_merge_policy_xxx
WHERE extSourceSystemAudit.LASTREFERENCEDDATE >= CURRENT_DATE
AND identitymap['email'][0].ID in ('depche.mode@dep.com')
ORDER BY extSourceSystemAudit.LASTREFERENCEDDATE DESC
LIMIT 10
```
