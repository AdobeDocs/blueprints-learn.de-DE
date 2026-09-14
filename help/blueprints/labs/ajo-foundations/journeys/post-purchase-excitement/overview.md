---
title: Aufregung nach dem Kauf
description: Erfahren Sie, wie Sie eine ereignisgesteuerte Journey nach dem Kauf erstellen, auf der eine Versandbenachrichtigungs-E-Mail mit dynamischen Tracking-Details von einer Drittanbieter-API Trigger wird.
doc-type: overview-page
solution: Experience Platform
exl-id: 570dc378-e7a3-4895-8f14-89d420b6b340
source-git-commit: df6c1852a6e0357dc9f166c88e77dcf9d334f955
workflow-type: tm+mt
source-wordcount: '326'
ht-degree: 0%
---

# Aufregung nach dem Kauf

## Voraussetzungen

>[!WARNING]
>
>Die folgenden Laboratorien müssen vor Beginn dieses Labors abgeschlossen sein

- **Postman-Setup** **—>** [Postman-Installation](../../postman-setup/postman-installation.md)
- **Datenspeicher — Relationaler Speicher in Aktion** **—>** [Profile Target Dimension](../../data-stores/relational-store-in-action/profile-target-dimension.md)
- **Datenspeicher — E-Mail-Kanäle konfigurieren —>** Für Profil [konfigurieren](../../data-stores/configure-email-channels/configure-for-profile.md)
  *(Dieser Schritt dauert bis zu 3 Stunden)*

Wenn Sie dies nicht getan haben, schließen Sie diese jetzt ab

>[!CAUTION]
>
>Dieses Lab erfordert eine Subdomain, die in Ihrer Sandbox an Adobe delegiert ist. Siehe [Setup](../../setup.md), wenn Sie das Tempo selbst bestimmen und noch keine haben.

## Labor-Übersicht

In diesem Video erfahren Sie, wie der Anwendungsfall „Aufregung nach dem Kauf“ einem Journey zugeordnet wird. Sie lernen dabei die Fragen zum kritischen Denken und die Architektur zum Senden einer personalisierten Versandbenachrichtigung nach der Bestellung kennen.

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

- Die anfängliche Bestellbestätigung wird in der Regel als Transaktionsnachricht implementiert, da Kunden nach der Bestellung nicht auf eine Bestätigung warten möchten.
- Die Benachrichtigung über den Versand von Bestellungen kann auch mithilfe von Transaktionsnachrichten implementiert werden. Sie kann jedoch in einer Journey erstellt werden, sodass eine benutzerdefinierte Aktion zum Abrufen von Versandinformationen und zur Verbesserung der Kundenkommunikation möglich ist.

>[!NOTE]
>
>In diesem Labor erstellen Sie nur die Nachricht Bestellung versendet und überspringen die Nachricht Bestellbestätigung .
