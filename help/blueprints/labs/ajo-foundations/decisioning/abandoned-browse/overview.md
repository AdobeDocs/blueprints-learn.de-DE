---
title: Abgebrochenes Durchsuchen
description: Erfahren Sie, wie Sie einen End-to-End-Entscheidungs-Workflow für die Suche nach aufgegebenen Browsern erstellen, der kanalübergreifend personalisierte Telefonangebote mit Eignung bereitstellt.
doc-type: overview-page
solution: Experience Platform
exl-id: 37b8a0b3-2820-4303-81d2-19890a3c5782
source-git-commit: df6c1852a6e0357dc9f166c88e77dcf9d334f955
workflow-type: tm+mt
source-wordcount: '461'
ht-degree: 0%
---

# Abgebrochenes Durchsuchen

## Voraussetzungen

>[!WARNING]
>
>Die folgenden Laboratorien müssen vor Beginn dieses Labors abgeschlossen sein

- **Postman-Setup** **—>** [Postman-Installation](../../postman-setup/postman-installation.md)
- **Datenspeicher — Profil in Aktion** **—>** [Datenstrom erstellen](../../data-stores/profile-in-action/create-datastream.md)

Wenn Sie diese Labs nicht abgeschlossen haben, tun Sie dies jetzt, bevor Sie fortfahren.

## Labor-Übersicht

In diesem Video erfahren Sie, wie die Beschreibung des Anwendungsfalls „Abgebrochen durchsuchen“ die Entscheidungselemente enthüllt und was Sie in diesem Labor erstellen werden, um in Echtzeit ein personalisiertes Telefonangebot mit Achtsamkeit bereitzustellen.

>[!VIDEO](https://video.tv.adobe.com/v/3491316/)

## Geschäftsziele

Für dieses Labor möchte Connection 5G den Umsatz des neuen Apple Flaggschiff-Telefons, iPhone 17, steigern, indem es sich an Kunden richtet, die die iPhone 17-Übersichtsseite besucht, aber noch nicht gekauft haben. Die wichtigsten Ziele der Kampagne sind:

- **Identifizieren Sie Kunden mit hohen Absichten** indem Sie erkennen, wann ein Benutzer eine Flaggschiff-Telefonseite mehrmals aufruft, ohne einen Kauf abzuschließen.
- **Trigger eines personalisierten Erlebnisses in Echtzeit** auf allen digitalen Oberflächen von Connection 5G, wenn dieses Verhalten auftritt.
- **Bereitstellung kontextueller Angebote** basierend auf wichtigen Kundenattributen wie dem **Alter des Kontoinhabers** und seinem **aktuellen Mobilfunkplan**.
- **Sicherstellen, dass die Angebotseignung durchgesetzt wird** sodass Kunden nur Telefonangebote sehen, die mit ihrem Plan kompatibel sind.
- **Dynamische Anpassung der angebotenen Telefonstufe** (z. B. Basis, Pro, Ultra) auf der Grundlage der Interaktion des Kunden oder der Reaktion auf frühere Angebote.
- **Bieten Sie konsistente Personalisierung über alle Kanäle**, indem Sie eine zentralisierte Entscheidungslogik verwenden, um das beste Angebot in Echtzeit zu ermitteln.
- **Erhöhen Sie die Konversionswahrscheinlichkeit** indem Sie jedem Kunden zum richtigen Zeitpunkt das relevanteste Flaggschiff-Telefonangebot unterbreiten.

## Lab Learning Objectives

Um die oben genannten Geschäftsziele in diesem Labor zu erreichen, lernen Sie Folgendes:

- **Erweitern Sie das Angebotsdatenmodell** indem Sie dem Angebotsschema benutzerdefinierte Attribute hinzufügen, damit sie in der Entscheidungslogik verwendet werden können.
- **Eignungsregeln erstellen** die anhand von Profilattributen bestimmen, welche Profile für bestimmte Angebote qualifiziert sind.
- **Angebotselemente erstellen und konfigurieren** einschließlich der Festlegung von Prioritäten, der Definition von Eignungsbedingungen und der Anwendung der Frequenzlimitierung.
- **Organisieren Sie Angebote in einer Sammlung** damit sie während der Entscheidungsaktivität einfach referenziert und ausgewertet werden können.
- **Erstellen Sie eine Rangfolgenformel** die die Angebotspriorität basierend auf den Profileigenschaften dynamisch anpasst.
- **Konfigurieren Sie eine**, die Angebotssammlungen, Eignungsregeln und Ranking-Logik kombiniert, um zu bestimmen, welche Angebote berücksichtigt werden und wie sie sortiert werden.
- **Richten Sie einen Code-Based Experience (CBE)-** ein, damit externe Systeme Entscheidungsergebnisse anfordern und Angebote im JSON-Format empfangen können.
- **Testen Sie den End-to-End** Entscheidungs-Workflow, indem Sie Erlebnisereignisse und Entscheidungsanfragen senden, um die Eignungslogik, das Ranking-Verhalten und die Frequenzlimitierung zu validieren.

In diesem Labor sammeln Sie praktische Erfahrungen beim Entwerfen und Validieren eines **vollständigen Offer Decisioning-Workflows in Adobe Journey Optimizer** um den geschäftlichen Anwendungsfall zu erfüllen.
