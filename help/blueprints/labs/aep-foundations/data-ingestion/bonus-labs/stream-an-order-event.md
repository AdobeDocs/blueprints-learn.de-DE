---
title: Streamen eines Bestellereignisses
description: 'Best Practice: Erstellen eines HTTP-API-Streaming-Datenflusses, um ein Beispiel für ein Bestellereignis zu senden und es mit einem vorhandenen Kundenprofil zu verknüpfen.'
doc-type: article
solution: Experience Platform
exl-id: 558c21d1-f9b7-489b-9153-5f10d0b8448a
source-git-commit: 3039df0c022176e9dada9c5a300f2df14429033d
workflow-type: tm+mt
source-wordcount: '164'
ht-degree: 0%

---


# Streamen eines Bestellereignisses

## Voraussetzungen

1. Sie haben die [Beispieldateien](../sample-files.md) heruntergeladen und sehen die Datei mit dem Namen —> **Lab\_Single\_Order\_sample.json**
1. Sie haben das Labor [Verwenden der Data Landing Zone](./using-data-landing-zone/overview.md) erfolgreich abgeschlossen und verfügen über einen gültigen Zuordnungssatz zum Importieren

## Challenge

Führen Sie die folgenden Aufgaben genau wie im vorherigen Labor aus.

1. Erstellen eines neuen Kontos mithilfe des HTTP-API-Quell-Connectors
1. Richten Sie einen Datenfluss mit dem neuen Konto ein, um Daten in Ihren eigenen Kundenauftrags-Datensatz zu streamen
1. Verwenden Sie den Zuordnungssatz aus dem Labor [Verwenden der Data Landing Zone](./using-data-landing-zone/overview.md) erneut
1. Füllen Sie in Postman das **Bestellereignis erstellen** mit den erforderlichen Informationen, um die Daten erfolgreich zu streamen und sie an den zuvor erstellten Kundenkonto-Datensatz anzuhängen
1. Überprüfen Sie, ob die Bestellung mit Ihrem Profil verknüpft ist

&#x200B;> [!TIP]
>
>Viel Glück und möge die Götter von Adobe Experience Platform bei euch sein!
