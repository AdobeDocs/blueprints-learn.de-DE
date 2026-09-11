---
title: Vortrag
description: Erkunden Sie das vierschichtige Inhaltsanatomiemodell, die Inhaltsintegrationsmuster von AJO und AEM und die KI-gestützte Content Governance für skalierbare Personalisierung.
doc-type: article
solution: Experience Platform
exl-id: 1ac39a70-51f8-426e-97cf-1ff08450d326
source-git-commit: 3039df0c022176e9dada9c5a300f2df14429033d
workflow-type: tm+mt
source-wordcount: '551'
ht-degree: 0%

---


# Vortrag

## Lernziele

- Erläuterung, warum bei Personalisierungsprogrammen im großen Maßstab nicht Daten, sondern Inhalte die wichtigste Einschränkung sind
- Beschreiben Sie das vierschichtige Inhaltsanatomie-Modell: Assets, Fragmente, Vorlagen und Nachrichten
- Sie können zwischen AJO- und AEM-Inhaltsfragmenten unterscheiden, einschließlich der Art und Weise, wie diese jeweils mit der Verbreitung umgehen
- Zuordnen der Inhaltslebenszyklusphasen von Erstellen, Speichern, Verwalten, Steuern, Aktivieren und Messen
- Vergleichen Sie die drei Inhaltsintegrationsmuster: AJO eigenständig, AJO + AEM Assets und AJO + GenStudio for Performance Marketing
- Identifizieren Sie die architektonischen Signale, die anzeigen, wann von einem Muster zum nächsten eskaliert werden soll.
- Beschreiben Sie die drei Ebenen der KI-Funktionen im Adobe-Stack: Inhaltsassistent, benutzerdefinierte Firefly-Modelle und Unified Brand Service
- Erläuterung des Prinzips der menschlichen Aufsicht in KI-unterstützten Inhalts-Workflows
- ECHTE PERSONALISIERUNG VON DER EINFÜGUNG VON VORNAMEN ODER DER MULTIPLIKATION VON ASSETS UNTERSCHEIDEN

## Video

In diesem Video erfahren Sie, wie das vierschichtige Inhaltsanatomiemodell, die drei AJO-Inhaltsintegrationsmuster und die KI-Funktionen in ein gesteuertes Inhaltssystem passen.

>[!VIDEO](https://video.tv.adobe.com/v/3491063/?quality=12&learn=on)

## Wichtige Erkenntnisse

Personalization im großen Maßstab beruht auf drei Säulen: Inhalt, Daten und Journey. Die meisten Unternehmen investieren stark in Daten- und Journey-Orchestrierung, behandeln Inhalte jedoch als Nebensächlichkeit. Genau aus diesem Grund sind Inhalte der Grund, warum Personalisierungsprogramme zuerst brechen. Für einen AJO-Architekten ist das Verständnis, wie Inhalte als gesteuertes System strukturiert werden, und nicht als Haufen einmaliger Assets, was eine skalierbare Implementierung von einer trennt, die unter der eigenen ausufernden Vorlage reduziert wird.

**In dieser Lektion haben Sie Folgendes behandelt:**

- Die These: Personalisierung schlägt nicht aufgrund von Daten fehl, sondern weil Inhalte nicht als System architektonisch erstellt werden
- Die vierschichtige Inhaltsanatomie: Assets (atomare Medien im DAM), Fragmente (wiederverwendbare visuelle oder Ausdrucksblöcke), Vorlagen (gesperrte oder bearbeitbare Bereiche) und Nachrichten (die endgültig zusammengestellte, kanalfertige Ausgabe)
- Der Inhaltslebenszyklus: Erstellen, speichern, verwalten, steuern, aktivieren, messen - und wie Fehler von links nach rechts kaskadieren, wenn ein Schritt übersprungen wird
- Muster 1, AJO eigenständig: am besten geeignet für Einzelmarkt, Einzelkanal, unter 50 Varianten, wenn Geschwindigkeit die Haupteinschränkung ist; verwendet AEM Assets Essentials als einfaches gebündeltes DAM
- AJO-Fragmente werden in AJO gespeichert und als Duplikate in Vorlagen kopiert, ohne automatische Aktualisierungen und mit einer Beschränkung auf 30-Fragment/1-Verschachtelungsebene
- Muster 2, AJO + AEM: Am besten für mehrere Märkte geeignet, mehr als 50 Varianten, wenn Governance die primäre Einschränkung ist; AEM wird zum „System of Record“, AJO das Aktivierungssystem
- AEM-Inhaltsfragmente werden von AJO referenziert (nicht kopiert), sodass Aktualisierungen sofort auf alle referenzierenden Vorlagen, Journey und Kampagnen übertragen werden können
- Drei Szenarien, die die Fragmentweitergabe im Hintergrund unterbrechen: eine unterbrochene Vererbung (entsperrtes Fragment), neue Personalisierungsattribute, die einem veröffentlichten Fragment hinzugefügt werden, und Beschriftungsbeschränkungen auf Objektebene (OLAC)
- Muster 3, AJO + GenStudio for Performance Marketing: am besten geeignet für die Generierung von Produktionsumgebungen und Varianten mit hohem Volumen; erfordert Governance nach Muster 2 als harte Voraussetzung
- Die vier Säulen, die die KI-Generierung markenbezogen halten: Unified Brand Service, Content Credentials, Human-in-the-Loop-Kuratierung und AJO-Integration
- Die Architektur-Entscheidungsmatrix und das Supply chain-Reifegradmodell für Inhalte (Stufen 1 ad hoc bis 5 autonom) zur Diagnose, wo sich ein Kunde heute befindet
- Eine echte Personalisierung ist eine intelligente Variation innerhalb einer einzelnen verwalteten Vorlage, nicht die Zusammenführungsfelder des Vornamens oder separate Kampagnen pro Segment
