---
hold: true
title: Erstellung von Entscheidungselementen
description: Erfahren Sie, wie sich die Attribute von Entscheidungselementen von den Eignungseinstellungen unterscheiden, und lernen Sie außerdem die Leitplanke auf Organisationsebene für Entscheidungselemente und Impressions im Vergleich zu Entscheidungsereignissen kennen.
doc-type: article
solution: Experience Platform
exl-id: 28752ac1-118c-41d9-af6a-9907f854df1e
source-git-commit: 2b2b9b9c359c4cc6757ac62ad502ece9a4923095
workflow-type: tm+mt
source-wordcount: '316'
ht-degree: 0%

---


# Erstellung von Entscheidungselementen

## Lernziel

Am Ende dieser Lektion können Sie:

- Die Attribute eines Entscheidungselements von seinen Eignungseinstellungen unterscheiden
- Geben Sie die Leitplanke für Entscheidungselemente pro IMS-Organisation an und warum sie auf Organisations- und nicht auf Sandbox-Ebene erfolgt
- Unterscheiden einer Impression von einem Entscheidungsereignis
- Entscheidungsregeln von Audiences nach Umfang, Zeitpunkt und den Daten zu unterscheiden, auf die sie zugreifen können

## Benötigte Materialien

- 12 Spielkarten (Bube, Dame, König aus jeder Farbe)
- 12 Haftnotizen, auf denen bereits Attributnamen aus der vorherigen Lektion geschrieben wurden

## Vortrag

Dies ist die bislang praktischste Lektion: Sie fügen jeder Karte einen Haftnotiz bei und halten dann mehrere Male an, um bei Einführung jedes Konzepts Werte für Stufe, Kapazität, Anzeige, Kamera, Priorität und Eignung zu schreiben.

>[!VIDEO](https://video.tv.adobe.com/v/3502207/)

## Wichtige Erkenntnisse

- Ein Entscheidungselement hat zwei Hälften: Attribute (Name, Beschreibung, benutzerdefinierte Attribute, Tags, Priorität) und Eignung (Datumsangaben, Einbeziehung von Entscheidungsregeln, Einbeziehung von Zielgruppen, Begrenzung)
- Eine Kundin oder ein Kunde kann bis zu 10.000 Entscheidungselemente haben - dieses Limit gilt pro IMS-Organisation, nicht pro Sandbox
- Scores mit höherer Priorität werden zuerst zurückgegeben
- Eine Entscheidungsregel ist eine Wenn/True-Bedingung, die auf eine einzelne Kampagne oder Journey angewendet wird, zum Zeitpunkt der Entscheidung ausgewertet wird und Entscheidungselementattribute verwenden kann. Eine Zielgruppe ist eine breitere Gruppe von Profilen, die mit Batch-/Streaming-/Edge-Geschwindigkeit ausgewertet wird und nicht auf Entscheidungselementattribute zugreifen kann
- Verwenden Sie eine Entscheidungsregel anstelle einer Zielgruppe, wenn die Eignung von den eigenen Attributen des Entscheidungselements abhängt
- Ein Entscheidungselement kann mehr als einen Begrenzungsereignis (Impressions, Klicks, Entscheidungsereignisse, benutzerdefinierte Trigger) gleichzeitig enthalten
- Eine Impression zählt, wenn das Element tatsächlich am Edge angezeigt wird. Ein Entscheidungsereignis zählt jedes Mal, wenn die Entscheidungsfindung eine Antwort bewertet und zurückgibt, unabhängig davon, ob sie angezeigt wird oder nicht
- Die Begrenzung wird täglich, wöchentlich oder monatlich um Mitternacht GMT zurückgesetzt - nicht zur Ortszeit
