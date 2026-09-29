---
title: Entscheidungselement-XDM
description: Erfahren Sie mehr über das vordefinierte XDM-Schema, das jedes Entscheidungselement freigibt, und wie benutzerdefinierte Attribute unter einem Mandanten-Namespace verschachtelt werden.
doc-type: article
solution: Experience Platform
exl-id: c42503a2-24e7-4a5d-98bf-38c16fe69733
product_v2:
  - id: edbd1a0e-46c8-49da-8c10-dba9ec80bba9
    internal-label: Experience Platform
source-git-commit: 1d6ba1444c119437eb8a86d5c4a1050d56d16023
workflow-type: tm+mt
source-wordcount: '176'
ht-degree: 0%
---

# Entscheidungselement-XDM

## Lernziel

Am Ende dieser Lektion können Sie:

- Identifizieren Sie das vordefinierte XDM-Schema, das für jedes Entscheidungselement verwendet wird
- Erläuterung, wo benutzerdefinierte Attribute innerhalb des Schemas vorhanden sind und welche Begrenzung für sie gilt
- Erkennen, wie die Verschachtelung von Attributen unter einem übergeordneten Objekt die Wiederverwendung unterstützt

## Benötigte Materialien

- Notizblock mit mindestens 12 Haftnotizen (mehr, falls Sie Fehler machen)

## Vortrag

Nach einer kurzen Videobearbeitung halten Sie an, um vier Attributnamen oben auf die 12 Haftnotizen zu schreiben - Sie füllen die tatsächlichen Werte in der nächsten Lektion aus.

>[!VIDEO](https://video.tv.adobe.com/v/3502206/)

## Wichtige Erkenntnisse

- Jedes Entscheidungselement verwendet dasselbe vordefinierte Schema: personalisierte Angebotselemente - Experience Decisioning
- Alles unter dem Knoten \_experience ist systemerforderlich und kann nicht bearbeitet werden
- Benutzerdefinierte Attribute befinden sich live unter dem Mandanten-Namespace Ihrer Organisation und sind auf maximal 100 pro Schema begrenzt.
- Für jedes Entscheidungselement gibt es nur ein Schema - keine Duplikate oder alternativen Versionen
