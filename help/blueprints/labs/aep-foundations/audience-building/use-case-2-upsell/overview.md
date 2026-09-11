---
hold: true
title: null
description: Definieren Sie einen Upsell-Anwendungsfall, der auf Kunden mit hoher Datennutzung ohne ultimativen Telefonplan abzielt, indem Sie Ansätze zur Zielgruppenaggregation für die Aktivierung vergleichen.
doc-type: overview-page
solution: Experience Platform
exl-id: d0268de8-87eb-4dd9-b699-99d42716f20c
source-git-commit: 2b2b9b9c359c4cc6757ac62ad502ece9a4923095
workflow-type: tm+mt
source-wordcount: '299'
ht-degree: 0%

---


# #2 - Upsell

## Übersicht

In diesem Video erfahren Sie, wie Sie den Upsell-Anwendungsfall angehen, der auf Kunden mit hoher Datennutzung abzielt, um eine Aktivierung über Paid- und Briefpost-Kanäle durchzuführen.

>[!VIDEO](https://video.tv.adobe.com/v/3459487/?quality=12&learn=on)



**Anwendungsfalldefinition**

Ermitteln Sie alle Kunden, die in den letzten 6 Monaten eine Gesamtnutzung der Abrechnungsdaten von >140 GB hatten, was einem rollierenden Durchschnitt von 6 Monaten entspricht. monatliche Datennutzung von >=20GB und ohne echten Telefonplan.

Aktivieren Sie die Kanäle Facebook / Google und Briefpost .

Briefpost-Personalisierungsfelder:

- Vorname → zur Begrüßung verwendet
- Für den Versand verwendete →
- Planname → für die Zusendung des Kontoauszugs verwendet (z. B. „Eric, jetzt auf einen ultimativen Plan aktualisieren!„)



## Analyseaufgaben

Analysieren Sie das oben Genannte und schreiben Sie es auf:

1. Welche Felder sind Ihrer Meinung nach für diesen Anwendungsfall erforderlich?
1. Muss die Auswertungsmethode Streaming sein?
1. Was müssen wir bei Abrechnungsdaten beachten?
1. Welche anderen Informationen möchten Sie wissen?

Denken Sie daran: Wenn wir von den geschäftlichen Stakeholdern Anforderungen erhalten, sind diese meist unvollständig, verwenden eine andere Terminologie und stellen Annahmen, ohne dass wir davon wissen. Es ist Ihre Aufgabe, so viel davon an die Oberfläche zu bringen und sie zu etwas zu führen, das getan werden kann.



## Annäherung

Für diesen Anwendungsfall werden wir zwei Optionen prüfen:

- Option #1 (zu aggregierende Zielgruppe verwenden)
  - Die Zielgruppe übernimmt die Aggregation.
    - Abrechnung der Datennutzungssumme >140 GB (letzte 6 Monate)
    - Nutzung der Abrechnungsdaten: Durchschn. 20 GB (letzte 6 Monate)
    - Datennutzung in Abrechnung hoch, aber kein Ultimate-Plan
- Option #2 (Verwenden von Pre-Aggregaten)
  - Dabei wird eine Aggregation verwendet, die vor der Eingabe der Daten in das Profil durchgeführt wurde
    - Abrechnung der Datennutzung hoch, aber kein Ultimate-Plan (AGG)
