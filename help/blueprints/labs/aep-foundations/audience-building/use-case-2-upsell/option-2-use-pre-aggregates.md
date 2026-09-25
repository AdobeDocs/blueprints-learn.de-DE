---
title: Option #2 - use pre-aggregates
description: Erstellen Sie eine vollständig gestreamte Zielgruppe, indem Sie vorab aggregierte Nutzungsattribute verwenden, die im Vorfeld berechnet wurden, anstatt Ereignisse innerhalb der Zielgruppenregel zu aggregieren.
doc-type: article
solution: Experience Platform
exl-id: fe6ee041-814f-41c1-91cf-c3473cbca0c2
source-git-commit: 96308d5726def849ef22540a5d13618017c40cc3
workflow-type: tm+mt
source-wordcount: '312'
ht-degree: 0%
---

# Option #2 - Verwenden von Pre-Aggregaten

Die Herausforderung bei Aggregaten in unserer Zielgruppe besteht darin, dass unsere Zielgruppe (beim Streaming) auf Aggregationen basiert, die innerhalb von Zielgruppen durchgeführt werden, bei denen es sich um Batch-Zielgruppen handelt. Da das Marketing festgestellt hat, dass ein Echtzeitansatz erforderlich ist, haben wir drei Dinge getan, um dies in das Design zu integrieren:

- Berechnen der Aggregate vor dem Streaming der Daten in

>[!NOTE]
>
>Dies ist recht ungewöhnlich, da die meisten gestreamten Daten auf ein einzelnes Ereignis oder auf ein Aggregat ausgerichtet sind

- Denormalisierten Plannamen verwenden
- Streamen der Daten in

## Zielgruppe erstellen

Erstellen Sie eine Audience für alle Profile, deren Abrechnungsdatennutzung hoch ist, aber derzeit keinen ultimativen Telefonplan hat.

1. Neue Zielgruppe erstellen
1. Suchen Sie auf der Registerkarte Attribute statt Ereignis nach „Tag“ und ziehen Sie die beiden Aggregate auf die Arbeitsfläche. Legen Sie die entsprechenden Operatoren und Werte für jeden Parameter fest.

   ![Legen Sie die entsprechenden Operatoren und Werte für jedes Aggregat fest](assets/option-2-use-pre-aggregates-set-operators-and-values.png)



1. Suchen Sie im Profil nach dem Plannamen und fügen Sie ihn hinzu (XDM-Kontaktprofil > DevBC > Plandetails > Planname). &quot;Ultimate&quot; auswählen

   ![Planname auswählen stimmt nicht mit Ultimate überein](assets/option-2-use-pre-aggregates-select-does-not-equal-ultimate.png)



1. Geben Sie eine Beschreibung ein.  Validieren Sie, ob die Auswertungsmethode Streaming ist.

1. Speichern Sie die Zielgruppe als &quot;*Abrechnung - Datennutzung hoch, aber kein Ultimate-Plan (AGG)*&quot;

>[!NOTE]
>
>Denken Sie daran, dass wir die Aggregatlogik in unsere vorgelagerte Streaming-ETL-Ebene verschoben haben.
>
>Bei dieser Wahl wird zwischen einer Batch-Zielgruppe gewählt, bei der der Marketer die Logik und eine Streaming-Zielgruppe steuert, die Definition und Steuerung jedoch auf die ETL-Ebene bringt, auf der das Engineering beteiligt sein muss.

>[!TIP]
>
>**Optionales Challenge-Lab**
>
>Früh fertig?
>
>Wir möchten unsere VIPs beim Kauf in Echtzeit mit einer speziellen Nachricht kontaktieren.  Erstellen Sie eine Zielgruppe von „VIPs“.  Ein VIP ist jemand, der im letzten Monat mehr als 1.000 Dollar gekauft hat.
