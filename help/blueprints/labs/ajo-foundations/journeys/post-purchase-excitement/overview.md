---
hold: true
title: Aufregung nach dem Kauf
description: Erfahren Sie, wie Sie eine ereignisgesteuerte Journey nach dem Kauf erstellen, auf der eine Versandbenachrichtigungs-E-Mail mit dynamischen Tracking-Details von einer Drittanbieter-API Trigger wird.
doc-type: overview-page
solution: Experience Platform
exl-id: 570dc378-e7a3-4895-8f14-89d420b6b340
source-git-commit: 2b2b9b9c359c4cc6757ac62ad502ece9a4923095
workflow-type: tm+mt
source-wordcount: '312'
ht-degree: 0%

---


# Aufregung nach dem Kauf

## Voraussetzungen

>[!WARNING]
>
>Die folgenden Laboratorien müssen vor Beginn dieses Labors abgeschlossen sein

Diese Laboratorien müssen vor Beginn dieses Labors abgeschlossen sein:

- **Datenspeicher — Relationaler Speicher in Aktion** **—>** [Profile Target Dimension](../../data-stores/relational-store-in-action/profile-target-dimension.md)
- **Datenspeicher — E-Mail-Kanäle konfigurieren —>** Für Profil [konfigurieren](../../data-stores/configure-email-channels/configure-for-profile.md)
  *(dieser Vorgang kann bis zu 3 Stunden dauern)*

Wenn Sie dies nicht getan haben, schließen Sie diese bitte jetzt ab.

## Labor-Übersicht

In diesem Video erfahren Sie, wie der Anwendungsfall „Aufregung nach dem Kauf“ einer Journey zugeordnet wird. Sie lernen dabei die wichtigsten Fragen und die Architektur zum Senden einer personalisierten Versandbenachrichtigung nach der Bestellung kennen.

>[!VIDEO](https://video.tv.adobe.com/v/3491146/)

## Lernziele

- Erstellen Sie eine Journey, die mit einem unitären Ereignis beginnt
- Richten Sie eine benutzerdefinierte Aktion ein und konfigurieren Sie sie, um ein Drittanbietersystem aufzurufen und Informationen zurückzugeben, die auf einer Journey verwendet werden
- Ausführen eines Journey durch Streaming in einer Ereignis-Payload
- Testen und Debuggen von Profilen und Journey
- Validieren des gewünschten Erlebnisses durch Berichte und Protokolle
- Personalisierung in einer einfachen E-Mail einrichten und in Aktion sehen



## Beschreibung des Anwendungsfalls

Wenn ein Kunde eine Bestellung aufgibt, möchten Sie eine Bestätigungsnachricht mit den Bestelldetails senden.  Nach dem Versand der Bestellung sollten Sie eine zweite Nachricht mit Tracking-Informationen Trigger erstellen, die dynamisch von einer Drittanbieter-API abgerufen wurden.

**Wichtige Hinweise:**

- Die anfängliche Bestellung wird in der Regel als Transaktionsnachricht implementiert, da die Personen nicht auf eine Bestätigung warten möchten, dass sie nur etwas bestellen.
- Die Benachrichtigung über den Versand von Bestellungen kann auch mithilfe von Transaktionsnachrichten implementiert werden. Sie kann jedoch in einer Journey erstellt werden, sodass eine benutzerdefinierte Aktion zum Abrufen von Versandinformationen und zur Verbesserung der Kundenkommunikation möglich ist.

>[!NOTE]
>
>In diesem Labor erstellen Sie nur die Nachricht Versand der Bestellung und überspringen die Nachricht Bestellbestätigung .
