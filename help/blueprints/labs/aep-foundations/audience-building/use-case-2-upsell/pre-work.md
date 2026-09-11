---
hold: true
title: Vorbereitung
description: Untersuchen Sie Schemafelder auf Abrechnungsnutzung und Plannamen, und heben Sie hervor, wie fehlende Beschreibungen und doppelte Felder Zielgruppenersteller verwirren können.
doc-type: article
solution: Experience Platform
exl-id: c26de19e-82da-4070-a918-2d2c8ef2c116
source-git-commit: 2b2b9b9c359c4cc6757ac62ad502ece9a4923095
workflow-type: tm+mt
source-wordcount: '285'
ht-degree: 0%

---


# Vorbereitung

Für diesen Anwendungsfall gibt es nicht viel Vorarbeit zu leisten. Wir haben im Grunde zwei Dinge, nach denen wir suchen, 1) Nutzung, 2) Plan.  Finde heraus, wo sie sind.

## Datennutzung für Abrechnung

1. Neue Zielgruppe erstellen
1. Suchen Sie in „Attribute“ nach „usage“. Klicken Sie auf das „i“, um die Beschreibung zu überprüfen (es gibt keinen).

![Suche nach Verwendung in Attributen - keine Beschreibung angezeigt](assets/pre-work-search-usage-in-attributes.png)



3. Suchen Sie in „Ereignisse“ nach „Verwendung“.  Klicken Sie auf das „i“, um die Beschreibung zu überprüfen (es gibt keinen).

![Suche nach Verwendung in Ereignissen - keine Beschreibung angezeigt](assets/pre-work-search-usage-in-events.png)

> [!NOTE]
>
>Keiner dieser Werte hat eine Beschreibung, sodass der Marketer einige Annahmen treffen und vermuten kann, dass er falsch liegt.
>
>Beschreibungen sind wichtig.  Wie kann der Marketing-Experte ohne Beschreibungen Folgendes wissen:
>
>- Was ist zu verwenden?
>- Latenz der Daten?
>- Empfohlen/bevorzugt in bestimmten Anwendungsfällen?
>
>Indem wir diese Informationen in Beschreibungen bereitstellen, können wir sie besser anleiten.

> [!NOTE]
>
>Suchen Sie nach „Abrechnung“.  Beachten Sie, dass es nicht als Profilattribut angezeigt wird.  Sie wird als Ereignistyp-Karte zusammen mit dem Feld „Abrechnung der Datennutzung“ angezeigt.
>
>Es gibt auch Namenskonventionen für Ihren Marketer.  Je nachdem, wonach sie suchen oder ob sie suchen/erwarten, dass es sich um ein Ereignis oder ein Profil handelt, wirkt sich dies auf das aus, was sie finden und schließlich verwenden.

## Plan

Suchen Sie in „Attribute“ nach „Plan“.  Beachten Sie, dass wir eine Reihe von Dingen zur Auswahl haben.  Beschränken Sie sie auf „Planname“.  Wir haben zwei Plannamen?!



![Attribut „Vorname des Plans“ bei der Suche nach Plan gefunden](assets/pre-work-duplicate-plan-name-field.png)



![Das Attribut „Zweiter Planname“ wurde bei der Suche nach einem Plan gefunden](assets/pre-work-duplicate-plan-name-field--2.png)

Der Planname (Planname) scheint derjenige zu sein, den wir basierend auf der Beschreibung benötigen, und dem anderen fehlt eine Beschreibung.
