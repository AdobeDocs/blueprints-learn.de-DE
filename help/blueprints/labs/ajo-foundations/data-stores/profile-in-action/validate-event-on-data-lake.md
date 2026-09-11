---
hold: true
title: Validieren des Ereignisses im Data Lake
description: Erfahren Sie, wie Sie den Data Lake abfragen, um zu überprüfen, ob ein gestreamtes Web-Ereignis in den richtigen Datensatz geschrieben wurde.
doc-type: article
solution: Experience Platform
exl-id: 14445089-aa3c-4cce-9d33-80032b6f9868
source-git-commit: 2b2b9b9c359c4cc6757ac62ad502ece9a4923095
workflow-type: tm+mt
source-wordcount: '170'
ht-degree: 0%

---


# Validieren des Ereignisses im Data Lake

## Lernziel

Stellen Sie sicher, dass das Web-Ereignis in den Data Lake von Experience Platform geschrieben wurde.

## Ereignis validieren

&#x200B;> [!NOTE]
>
>Schließlich erscheinen die Daten im Data Lake.  **Dies kann bis zu 60 Minuten dauern**.  Wir wissen, dass der Datensatz für das Profil aktiviert ist und daher das Ereignis ein Profilfragment erstellt.
>
>Sie können den Web-Datensatz suchen und abfragen.

1. Gehen Sie zu **Abfragen** und **Abfrage erstellen**

![Bildschirm „Abfrage erstellen“ im Abschnitt „Abfragen“](assets/validate-event-on-data-lake-create-query.png)

&#x200B;2. SQL kopieren und in Abfrage einfügen

```sql
SELECT identityMap['email'][0].id, * FROM dep_web
where identityMap['email'][0].id = 'henry.creel@emailsim.io'
```

&#x200B;3. **Ausführen** Abfrage

&#x200B;> [!NOTE]
>
>**Denken Sie**: Schließlich werden die Daten im Data Lake angezeigt.  **Dies kann bis zu 60 Minuten dauern**.
>
>Sie müssen nicht warten, bis sie angezeigt wird. Sie können zu diesem Schritt zurückkehren und es später überprüfen.



![Abfrageergebnisse, die das Streaming-Web-Ereignis im Data Lake zeigen](assets/validate-event-on-data-lake-query-results.png)

## Zusammenfassung

Der Ereignisdatensatz wird im entsprechenden Datensatz angezeigt.
