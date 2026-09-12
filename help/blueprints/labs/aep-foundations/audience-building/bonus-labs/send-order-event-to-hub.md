---
title: Auftragsereignis an Hub senden
description: Erfahren Sie, wie Sie ein Bestellereignis über die API an den Hub streamen, ein Streaming-Bestellsegment erstellen, es für ein Ziel aktivieren und Profilergebnisse validieren.
doc-type: article
solution: Experience Platform
exl-id: d5de39d7-7340-487a-86fa-504344daeab7
source-git-commit: 0b33b2740ee7f5af73d64f217b4475650c1d28a0
workflow-type: tm+mt
source-wordcount: '669'
ht-degree: 0%

---


# Auftragsereignis an Hub senden

## Streaming zu Hub und Edge im Vergleich

Im #1 haben wir ein Ereignis an die Edge gesendet.  Es gibt einige Anwendungsfälle, in denen wir möglicherweise ein Back-End-System haben, das in einem Ereignis streamen möchte, es jedoch nicht an Edge senden muss.  In diesem Labor wird gezeigt, wie dies funktioniert, indem ein Order-Ereignis an den Hub gestreamt wird.

## Erstellen Sie ein Auftragssegment (falls noch nicht geschehen).

Klicken Sie in der linken Leiste auf Audience und dann oben rechts auf die Schaltfläche Audience erstellen .

![Klicken Sie in der linken Leiste auf Zielgruppe und anschließend auf Zielgruppe erstellen &#x200B;](assets/send-order-event-to-hub-click-create-audience-button.png)

Suchen Sie die Karte Ereignistyp „Bestellung platziert“ und ziehen Sie sie auf die Arbeitsfläche.

![Ziehen Sie die Karte Ereignistyp „Reihenfolge platziert“ auf die Arbeitsfläche](assets/send-order-event-to-hub-drag-order-placed-event-onto-canvas.png)

## Ereignisregeln aktualisieren

Nehmen Sie die folgenden Änderungen an den Ereignisregeln vor (möglicherweise müssen Sie das Ereignis erweitern, um es anzuzeigen)

1. Letzte
1. 15
1. Minuten
1. Änderung an Streaming-Auswertung

Speichern unter **Ereignis-Streaming bestellen (innerhalb von 15 Minuten)**



![Speichern Sie die Zielgruppe als Ereignis-Streaming bestellen (innerhalb von 15 Minuten) mit Streaming-Auswertung](assets/send-order-event-to-hub-save-streaming-evaluation-rule.png)

## Für Ziel aktivieren

Öffnen Sie die soeben erstellte Zielgruppe, falls sie geschlossen ist.

Klicken Sie auf Für Ziel aktivieren



![Klicken Sie auf Für Ziel aktivieren für die Bestellzielgruppe](assets/send-order-event-to-hub-click-activate-to-destination.png)

### Ziel

Wählen Sie das zuvor erstellte Streaming-Ziel aus (Streaming DEP Webhook)



![Wählen Sie das Streaming-DEP-Webhook-Ziel aus](assets/send-order-event-to-hub-select-streaming-destination.png)

### Mapping

Lassen Sie die Zuordnung unverändert und klicken Sie auf „Weiter“

![Lassen Sie die Zuordnung unverändert und klicken Sie auf Weiter](assets/send-order-event-to-hub-leave-mapping-click-next.png)

Klicken Sie auf Beenden

## Postman öffnen

Starten Sie Postman auf Ihrem Computer und navigieren Sie zum folgenden API-Aufruf:

1. **Postman linke Seitenleiste** —> `Collections`
1. **collection** —> `AEP Foundations Bootcamps (labs)`
1. **Ordner** —> Profile Lab
1. **API-Anfrage** —> `Create Order Event`

![Öffnen Sie die Anfrage „Bestellereignis-API erstellen“ in Postman](assets/send-order-event-to-hub-create-order-event-api-request.png)


## API-Anfrage ändern

Um eine Beispiel-API-Anfrage zu erstellen, müssen Sie die folgenden Teile im Hauptteil der API-Anfrage ausfüllen.

Erfassen Sie zunächst die folgenden Werte:

## Konto-Streaming-Endpunkt suchen

1. Navigieren Sie **linken Leiste zu** Quellen“ und klicken Sie dann **oberen Navigationsbereich auf** Konten“
1. Suchen Sie nach **dep: HTTP API \[raw]** markieren Sie die Zeile und kopieren und speichern Sie den Wert des **Streaming-Endpunkts** an einen anderen Ort, auf den Sie später verweisen können

Konto  und seinen Streaming-Endpunkt kopieren&rbrack;(assets/send-order-event-to-hub-http-api-raw-streaming-endpoint.png „dep: HTTP API \[raw]„)

## Datenfluss-ID suchen

1. Suchen Sie den Datensatz für **dep: Orders (Stream)** und klicken Sie auf den Link Datenflüsse .
1. Kopieren Sie in der rechten Leiste die Werte **Datenfluss-ID** an eine Stelle, auf die Sie später verweisen können

>[!NOTE]
>
>Klicken Sie in ein leeres Feld in der Zeile.  Klicken Sie NICHT auf die blauen Links!

![Kopieren Sie die Datenfluss-ID für die Datenfluss-/Web-Datenfluss- und Datensatz](assets/send-order-event-to-hub-orders-stream-dataflow-id.png "IDs „dep: Orders (stream)")

## Endgültige API-Anfrage erstellen

Kopieren Sie die in den vorherigen Schritten gespeicherten Werte an die unten hervorgehobenen Stellen.

- **red** —> `Streaming Endpoint URL`
- **grün** —> `Dataflow ID`

Ihre endgültige API-Anfrage sollte dann wie folgt aussehen

>[!CAUTION]
>
>NOCH NICHT AUSFÜHREN!

![Anfrage zum Erstellen eines Auftragsereignisses mit ausgefülltem Streaming-Endpunkt und Datenfluss-ID abgeschlossen](assets/send-order-event-to-hub-final-order-api-request.png)


## Ausführen der API

1. Speichern Sie den API-Aufruf, indem Sie auf die Schaltfläche **Speichern** klicken
1. Ausführen einer Anfrage durch Klicken auf die Schaltfläche **Senden**

Ein erfolgreicher Aufruf sollte zu der folgenden Antwort führen…

![Erfolgreiche API-Antwort nach dem Senden des Auftragsereignisses](assets/send-order-event-to-hub-successful-api-response.png)

## Validieren

1. Navigieren Sie zu Ihrem Profil und suchen Sie Ihr Profil, um zu sehen, ob das Ereignis in das Profil aufgenommen wurde.  Es sollte in Sekunden angezeigt werden.
   1. Profil mithilfe der E-Mail in der Reihenfolge nachschlagen
1. Überprüfen Sie, ob sich das Profil für die Segmente qualifiziert hat (dies kann einige Minuten dauern). Sie sollte in Sekunden bis Minuten angezeigt werden.
   1. Ereignis-Streaming bestellen (innerhalb von 15 Minuten)
1. Überprüfen Sie Ihren Webhook, um festzustellen, ob das Ziel den Webhook über ein Segment „realized“ benachrichtigt hat.  Es sollte in 5-10 Minuten angezeigt werden.
1. Nach 15-30 Minuten können Sie Ihren Datensatz sogar mit den folgenden Elementen überprüfen:
   1. Ändern Sie den unten stehenden Tabellennamen in den aus Ihrer Sandbox.  Um ihn zu finden, gehen Sie zu Ihrer Datensatzliste und filtern Sie nach &quot;`dest`&quot;, öffnen Sie den Datensatz und kopieren Sie den Tabellennamen in die rechte Leiste.

```sql
SELECT * FROM profile_export_for_destination_merge_policy_xxx
WHERE extSourceSystemAudit.LASTREFERENCEDDATE >= CURRENT_DATE
AND identitymap['email'][0].ID in ('depche.mode@dep.com')
ORDER BY extSourceSystemAudit.LASTREFERENCEDDATE DESC
LIMIT 10
```
