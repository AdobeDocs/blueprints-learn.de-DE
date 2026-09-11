---
title: Einrichten der Quelle
description: Laden Sie eine JSON-Datei für historische Bestellungen in die Data Landing Zone hoch und konfigurieren Sie einen neuen Datenfluss, der auf das Bestellschema abzielt.
doc-type: article
solution: Experience Platform
exl-id: 046d50ad-687e-4cdb-a8b1-3c55ab39b68e
source-git-commit: 3039df0c022176e9dada9c5a300f2df14429033d
workflow-type: tm+mt
source-wordcount: '353'
ht-degree: 0%

---


# Einrichten der Quelle

## Beispieldatei hochladen

Sie müssen eine Beispieldatendatei über den Azure Storage Explorer in Ihre Data Landing Zone hochladen, damit Sie sie im Labor verwenden können.  Gehen Sie dazu wie folgt vor:

1. Herunterladen der [Beispieldateien](../../../sample-files.md)
1. Ziehen Sie die Datei **Lab\_Historical\_Orders.json“ per Drag-and** Drop in die Data Landing Zone, die Sie oben gespeichert haben.



Nach dem Hochladen sollte Ihr Bildschirm wie der folgende Screenshot aussehen.

![Lab_Historical_Orders.json-Datei, die in die Data Landing Zone hochgeladen wurde](assets/setup-source-lab-historical-orders-json-uploaded-to-dlz.png "Lab_Historical_Orders.json, die in DLZ hochgeladen wurde")

## Zu Quellen navigieren

1. Wechseln Sie zu Adobe Experience Platform und navigieren Sie zu: **Quellen** -> **Katalog** -> **Cloud-Speicher**
1. Klicken Sie auf **Setup**/**Daten hinzufügen** für die Data Landing Zone

![Navigieren Sie zu Quellen > Katalog > Cloud-Speicher, um die Data Landing Zone einzurichten](assets/setup-source-navigate-to-data-landing-zone-source.png "Quellen - Data Landing Zone")

>[!NOTE]
>
>Sie sehen **Daten hinzufügen** als Standardaktion, wenn Sie bereits eine Verbindung aus dem vorherigen Batch-Aufnahme-Labor eingerichtet haben



## Vorschau der Datei

1. Wählen Sie die Datei **Lab\_Historical\_Orders.json** aus und zeigen Sie eine Vorschau des Inhalts an
1. Klicken **oben** auf „Weiter“, um mit dem nächsten Schritt fortzufahren

![Auswählen und Vorschau der Lab_Historical_Orders.json-Dateiinhalte](assets/setup-source-select-and-preview-lab-historical-orders.png "Auswählen und Vorschau der Lab_Historical_Orders.json-Datei")

## Datenfluss einrichten

1. Wählen Sie im Bildschirm Datenflussdetails die Option **Neuer Datensatz**
1. Benennen Sie den Ausgabedatensatz als &quot;**- YourNameHere**
1. Wählen Sie den Schemanamen aus **dep: Orders**
1. Aktivieren Sie das **Profildatensatz**-Umschalter
(Wenn Sie dies nicht aktivieren, kann der Profilspeicher nicht überwachen, ob neue Daten in diesen Datensatz eingehen, und nimmt diese Daten daher nicht in Profile auf.)
1. Aktivieren Sie die **Teilweise Aufnahme aktivieren**
(Wenn Sie dies nicht aktivieren, kann die Aufnahme fehlschlagen, wenn einer der Datensätze Fehler aufweist)
1. Legen Sie den Datenflussnamen als &quot;**- Aufstockung - YourNameHere“ fest**
1. Aktivieren Sie alle Warnhinweise **Quellen: Datenflussstart/-erfolg/-fehler**

![Bildschirm mit Datenflussdetails konfiguriert für den Datensatz „Bestellungen](assets/setup-source-dataflow-details-for-orders.png "Datenflussdetails für Bestellungen")

>[!CAUTION]
>
>Stellen Sie sicher **dass Sie** Datensatz sowohl für die Profil- als auch für die partielle Aufnahme aktiviert haben.

Klicken **oben** auf „Weiter“, um mit dem nächsten Schritt fortzufahren
