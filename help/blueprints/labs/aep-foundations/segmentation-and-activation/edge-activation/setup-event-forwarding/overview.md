---
hold: true
title: Einrichten der Ereignisweiterleitung
description: Erfahren Sie, wie bei der Ereignisweiterleitung Eigenschaften, Datenelemente, Regeln und Datenströme verwendet werden, um Edge-Ereignisse an einen Drittanbieter-Endpunkt weiterzuleiten.
doc-type: overview-page
solution: Experience Platform
exl-id: da3d1c7f-3642-4de7-a297-fc36d09e7336
source-git-commit: 2b2b9b9c359c4cc6757ac62ad502ece9a4923095
workflow-type: tm+mt
source-wordcount: '186'
ht-degree: 0%

---


# Einrichten der Ereignisweiterleitung

Die Ereignisweiterleitung befindet sich auf der Edge und ermöglicht es uns, einen Satz von Regeln und leichten Transformationen zu erstellen, um Ereignisse an einen beliebigen Endpunkt zu senden.

In diesem Schritt leiten wir alle Ereignisse, die wir an Edge senden, an einen Webhook weiter. Der Webhook fungiert als Proxy für einen Drittanbieter und ermöglicht es uns, zu sehen, was passiert.

Zur Konfiguration richten wir Folgendes ein:

- Eine Eigenschaft, die alle Erweiterungen, Datenelemente und Regeln enthält, die erforderlich sind, um zu entscheiden, was wohin weitergeleitet werden soll
  - Ein Datenelement , das auf das eingehende Ereignis verweist oder es bei Bedarf in mehrere einzelne Komponenten zerlegt
  - Eine Regel, um Bedingungen für die Weiterleitung hinzuzufügen, die Payload umzuwandeln und festzulegen, wohin sie gesendet werden soll
- Ein Datenstrom, der konfiguriert, welche Services ihn verwenden werden (z. B. Ereignisweiterleitung und AEP)
  - Daten, die an diese Datenströme gesendet werden, können dann entsprechend dem konfigurierten Service Aktionen ausführen (z. B. ein Ereignis weiterleiten und Daten an einen Datensatz senden)
