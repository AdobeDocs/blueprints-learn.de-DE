---
title: Leitplanken, KI-Modelle und die Zukunft von Decisioning
description: Lernen Sie die wichtigsten Leitplanken für Entscheidungen kennen und erfahren Sie, wie sich KI-Rangfolgemodelle von Formeln unterscheiden und wie die Bausteine der Entscheidungsfindung eine durchgängige Verbindung herstellen.
doc-type: article
solution: Experience Platform
exl-id: 90902f6e-ba3c-4852-ab82-ad852698b227
source-git-commit: 3039df0c022176e9dada9c5a300f2df14429033d
workflow-type: tm+mt
source-wordcount: '297'
ht-degree: 0%

---


# Leitplanken, KI-Modelle und die Zukunft von Decisioning

## Lernziel

Am Ende dieser Lektion können Sie:

- Erinnern Sie sich an die beiden Leitplanken, die in der Praxis am häufigsten vorkommen
- Unterscheidung zwischen automatischer Optimierung und KI-Modellen für personalisierte Optimierung
- Erläuterung der Erweiterung der Entscheidungsfindung über das alte ODE-Produkt hinaus
- Fassen Sie zusammen, wie die acht Bausteine End-to-End zusammenpassen

## Vortrag

Das folgende Video behandelt die beiden häufigsten Entscheidungs-Leitplanken, wie sich KI-Rangfolgemodelle von manuellen Rangfolgeformeln unterscheiden, wie sich das Decisioning über die alte Offer Decisioning Engine hinaus erstreckt und eine Zusammenfassung, wie die acht Bausteine End-to-End verbunden sind.

>[!VIDEO](https://video.tv.adobe.com/v/3502212/)

## Wichtige Erkenntnisse

- Die beiden am häufigsten aufgerufenen Leitplanken sind 10.000 Entscheidungselemente pro IMS-Organisation (nicht pro Sandbox) und 100 benutzerdefinierte Attribute pro Schema. In der Produktdokumentation finden Sie aktuelle Zahlen, da diese sich ändern können
- KI-Modelle können in Rangfolgeformeln verwendet werden. Die automatische Optimierung ist nicht personalisiert und optimiert die globale Leistung, während die personalisierte Optimierung Elemente für bestimmte Geschäftsziele pro Profil bereitstellt
- Außerhalb von AEP berechnete Modellbewertungen können als Profilattribute übermittelt und in Eignungsregeln oder Rangfolgeformeln verwendet werden
- Die Entscheidungsfindung geht über die alte Offer Decisioning-Engine hinaus: Sie verwendet XDM für die Wiederverwendbarkeit, stellt JSON für Headless-Anwendungen bereit und trennt das Entscheidungselement von der Behandlung
- Decisioning kann Journey-Pfade und Eingabeprioritäten in einer Entscheidungs-Antwort bedingte Bedingungen festlegen
- End-to-End: Entscheidungselement-XDM definiert Attribute → Entscheidungselement-Erstellung weist Sammlungen Werte und Eignung → Gruppenelemente zu → Rangfolgeformeln passen die Priorität pro Profil an → Auswahlstrategien ordnen und filtern eine Sammlung → Entscheidungsrichtlinien wenden Strategien auf einen Kanal an → Entscheidungspakete live auf dem Hub oder Edge
