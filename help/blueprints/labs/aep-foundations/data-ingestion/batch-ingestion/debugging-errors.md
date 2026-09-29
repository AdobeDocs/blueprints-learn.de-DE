---
title: Debuggen von Fehlern
description: Verwenden Sie die Vorschau-Fehlerdiagnose, um einen fehlgeschlagenen Datenfluss zu untersuchen und Fehler im Aufnahmeformat von MAPPER-Konversionswarnungen zu unterscheiden.
doc-type: article
solution: Experience Platform
exl-id: beee191b-a860-494c-873f-ab2e407ffbf5
product_v2:
  - id: edbd1a0e-46c8-49da-8c10-dba9ec80bba9
    internal-label: Experience Platform
source-git-commit: 1d6ba1444c119437eb8a86d5c4a1050d56d16023
workflow-type: tm+mt
source-wordcount: '288'
ht-degree: 0%
---

# Debuggen von Fehlern

## Vorschau der Fehlerdiagnose

Nach einigen Minuten sollten Sie beachten, dass **Status** einen Fehler anzeigt. Drilldown in die Fehlerdetails, um zu sehen, was den Fehler verursacht hat.

1. Klicken Sie auf **Startdatum des Datenflusses**
1. Klicken Sie auf **Vorschau der Fehlerdiagnose**, um die spezifischen Details für jede fehlgeschlagene Zeile anzuzeigen

![Datenflussausführungsstatus, der einen Fehler ](assets/debugging-errors-dataflow-run-failure.png " Datenflussausführungsfehler anzeigt")

![Vorschau des Links Fehlerdiagnose im Bildschirm mit den Datenflussausführungs-Details](assets/debugging-errors-preview-error-diagnostics-link.png "Vorschau der Fehlerdiagnose")



Der Bildschirm, den Sie jetzt sehen, zeigt Ihnen eine Reihe von Details darüber, was die Fehlercodes mit der vollständigen Fehlermeldung bedeuten und welche Zeile fehlgeschlagen ist.

![Detailbildschirm für die Fehlerdiagnose mit Fehlercodes, Meldungen und der Vorschau ](assets/debugging-errors-error-diagnostics-detail-screen.png " fehlgeschlagenen Fehlerzeile")

>[!NOTE]
>
>Scrollen Sie nach rechts, um die mit diesem Fehlercode verknüpften Quelldaten anzuzeigen



## Fehlertypen verstehen

### Fehler beim Aufnehmen von XXXX-XXX

Dieser Fehler tritt auf, weil **person.bornDayAndMonth** im Format eines zweistelligen Monats plus eines zweistelligen Tages erwartet wird (d. h. der 27. April sollte als 04-27 formatiert sein)

```none
The value (9-27) does not conform to the specified
regex pattern: [0-1][0-9]-[0-9][0-9] in field: 
person.birthDayAndMonth of type: String
```

>[!CAUTION]
>
>Beachten Sie, dass person.BirthDayAndMonth kein erforderliches Feld ist, aber die Nichteinhaltung regulärer Ausdrücke vom System als „Datenbeschädigungsproblem“ behandelt wird und einen schwerwiegenden Fehler darstellt.



### MAPPER-XXXX-XXX-Fehler

Dieser Fehler tritt auf, weil das Quellfeld von **createDate** Zeichenfolgenwerte von `Created on 2022-04-22T19:34:17Z` hat. Dieser Wert kann wegen des Textes am Anfang nicht automatisch in ein Datum umgewandelt werden: `Created on`. Ein berechnetes Feld muss zum Bereinigen der Daten verwendet werden.

```none
Error transforming data for destination path 
_dep.account.createDate. Details: Unable to convert 
Created on 2023-09-24T10:19:58Z to schema type DATE_TIME
```

>[!NOTE]
>
>Dieser Fehler ist nicht schwerwiegend, da dies nur zu Warnungen während der Zuordnung führt. Die Datenflussausführung schlägt aus diesem Grund nicht fehl, sodass dieses Labor diesen Fehler nicht behebt.
