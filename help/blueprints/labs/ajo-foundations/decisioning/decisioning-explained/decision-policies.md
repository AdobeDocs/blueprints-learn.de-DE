---
title: Entscheidungsrichtlinien
description: Erfahren Sie, wie Entscheidungsrichtlinien Auswahlstrategien auf einen Versandkanal anwenden und wie einzelne oder gruppierte Kombinationsmethoden die Angebotsreihenfolge ändern.
doc-type: article
solution: Experience Platform
exl-id: 21dc67fd-76ac-4b82-ae78-be024c7bfc55
source-git-commit: 3039df0c022176e9dada9c5a300f2df14429033d
workflow-type: tm+mt
source-wordcount: '304'
ht-degree: 0%

---


# Entscheidungsrichtlinien

## Lernziel

Am Ende dieser Lektion können Sie:

- Erklären, was eine Entscheidungsrichtlinie konfiguriert und wo sie angewendet wird
- Definieren eines Entscheidungspakets und seiner Bestandteile
- Einzel- und Gruppierungsmethoden zur Kombination mehrerer Auswahlstrategien zu unterscheiden
- Erläuterung der Interaktion der Frequenzlimitierung mit der Anzahl der Entscheidungselemente, die eine Richtlinie zurückgibt

## Benötigte Materialien

- 12 Spielkarten (Bube, Dame, König aus jeder Farbe)
- 13 Haftnotizen
  - 12 sowohl mit Attributnamen als auch mit Werten aus vorherigen Lektionen gefüllt
  - Eine neue Haftnotiz zum Nachverfolgen der Anfragen

## Vortrag

Dies ist die längste und am meisten involvierte Simulation im Kurs. Sie simulieren das Verhalten von Live-Entscheidungsrichtlinien - wiederholte „Anfragen“, das Verfolgen von Impressionen anhand von Häufigkeitsbegrenzungen und das Beobachten von Karten, die ausfallen und ersetzt werden - und wenden dann alles auf ein reales Geschäftsszenario an, indem Sie die Kombination aus individuellen und gruppierten Auswahlstrategien vergleichen.

>[!VIDEO](https://video.tv.adobe.com/v/3502211/)

## Wichtige Erkenntnisse

- Eine Entscheidungsrichtlinie wendet Auswahlstrategien auf einen tatsächlichen AJO-Versandkanal an, der auf einem Kanalknoten im Kanalabschnitt einer Journey oder einer Kampagne konfiguriert ist
- Eine Richtlinie kann keine, eine oder mehrere Auswahlstrategien verwenden. Bei keiner gibt sie Elemente nach dem ursprünglichen Prioritätswert zurück, gefiltert nach der Berechtigung auf Elementebene
- Eine Entscheidungsrichtlinie und ihr Versandkanal werden zusammen als Entscheidungspaket bezeichnet - die Konfiguration, die im Hub oder Edge vorhanden ist
- Bei jeder einzelnen Kombination wird die Sammlung jeder Strategie separat sortiert und die Listen werden gestapelt. Bei der Gruppierung werden alle Elemente in einer Liste sortiert, und die Duplikate verwenden den höheren der beiden Bewertungen
- Dieselben Eingänge können je nach Individuum und Gruppe zu drastisch unterschiedlichen endgültigen Bestellungen führen
- Die Frequenzlimitierung begrenzt direkt die Anzahl der verfügbaren Elemente, die zurückgegeben werden können. Planen Sie daher genügend nicht begrenzte Fallback-Elemente, um jeden Slot zu füllen
