---
title: Startseite von Flaggschiffen
description: Verschaffen Sie sich einen Überblick über den Aufbau einer orchestrierten Kampagne, die nach einem Vorzeigestart per Telefon mit einem SMS-Upgrade-Angebot auf Kontoinhaber und einzelne Leitungen abzielt.
doc-type: overview-page
solution: Experience Platform
exl-id: 04c509f1-aa10-4d29-aa59-5e627b79e498
source-git-commit: 3039df0c022176e9dada9c5a300f2df14429033d
workflow-type: tm+mt
source-wordcount: '244'
ht-degree: 0%

---


# Startseite von Flaggschiffen

## Voraussetzungen

>[!WARNING]
>
>Die folgenden Laboratorien müssen vor Beginn dieses Labors abgeschlossen sein

- **Datenspeicher — Relationaler Speicher in Aktion** **—>** [Profile Target Dimension](../../data-stores/relational-store-in-action/profile-target-dimension.md)
- **Datenspeicher — Konfigurieren von E-Mail-Kanälen —>** [Konfigurieren für relationale](../../data-stores/configure-email-channels/configure-for-relational.md)
  *(Dieser Setup-Schritt dauert bis zu 3 Stunden)*

Wenn Sie diese Labs nicht abgeschlossen haben, tun Sie dies jetzt, bevor Sie fortfahren.

## Labor-Übersicht

In diesem Video erfahren Sie, wie das wichtigste Anwendungsbeispiel für Telefonstarts orchestrierten Kampagnen zugeordnet wird und wie Sie die kritischen Fragen und die Architektur besprechen, bevor Sie die Kampagne erstellen, die sich an Kontoinhaber und einzelne Linien richtet.

>[!VIDEO](https://video.tv.adobe.com/v/3486217/)

## Lernziele

- Erstellen einer orchestrierten Kampagne mithilfe einer Vielzahl von Workflow-Aktivitäten
- Erstellen einer Zielgruppe mit der Aktivität „Zielgruppe aufbauen“
- Informationen zum Einrichten eines SMS-Kanals
- Speichern einer Zielgruppe im Zielgruppen-Portal
- Ansprechen sowohl des Kundenkontos als auch einzelner Zeilen mit E-Mail- und SMS-Nachrichten



## Beschreibung des Anwendungsfalls

Senden Sie unmittelbar nach dem Launch des neuesten Flagship-Geräts eines Herstellers eine zielgerichtete Nachricht an Kontoinhaber und LINE-Benutzer mit älteren Modellen, um sie zum Upgrade einzuladen und die Zukunft der Mobilgeräte zu erleben.

**Wichtige Hinweise:**

- Zielgruppe aller Kundenzeilen im Zielgruppenportal speichern
- Targeting einzelner Zeilen und Kontoinhaber mit einer Nachricht (Sie verwenden SMS)

>[!NOTE]
>
>Dieses Szenario simuliert eine **Telekom-Vertrag-Upgrade-Kampagne** bei der sekundäre (abhängige) Leitungen gezielte Upgrade-Nachrichten erhalten.
