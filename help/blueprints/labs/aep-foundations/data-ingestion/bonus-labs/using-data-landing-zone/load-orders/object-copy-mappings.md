---
hold: true
title: Objektkopie-Zuordnungen
description: Konfigurieren Sie Objektkopie-Zuordnungen für ein Produkt-Array und fügen Sie dann Überschreibungen auf Feldebene über der Standardkopie hinzu bzw. entfernen Sie diese.
doc-type: article
solution: Experience Platform
exl-id: 762d0e19-ed1c-4f4d-91ec-a962bd6277a7
source-git-commit: 2b2b9b9c359c4cc6757ac62ad502ece9a4923095
workflow-type: tm+mt
source-wordcount: '318'
ht-degree: 0%

---


# Objektkopie-Zuordnungen

In diesem Abschnitt fügen Sie die Objektkopie-Zuordnungen hinzu und erstellen einige Überschreibungen.

## Passthrough-Zuordnungen

Fügen Sie die folgenden Passthrough-Zuordnungen zu **products\[\*]** und **products\[\*].productID** hinzu, indem Sie auf Neuer Feldtyp klicken und für jede Zeile hier ein neues Feld hinzufügen. Einige können aufgrund von ML-Empfehlungen bereits vorhanden sein.

| Source-Spalte | XDM-Spalte |
| ----------------------- | ------------------------- |
| orderStatus | eventType |
| lastOrderStatusUpdate | Zeitstempel |
| Produkte\[\*] | productListItems\[\*] |
| products\[\*].productID | productListItems\[\*].SKU |

>[!NOTE]
>
>Beachten Sie, **products\[\*]** eine 1:1-Feldzuordnung zwischen den Objektfeldern durchführt und die explizite Feldzuordnung **products\[\*].productID** die Standardkopie überschreibt.

>[!NOTE]
>
>**products\[\*].productID** ist auch **productListItems\[\*].SKU** sowie **productListItems\[\*].\_id** zugeordnet. Dies ist ein Beispiel für die Zuordnung eines einzelnen Eingabefelds zu mehreren Ausgabefeldern im XDM-Schema. Behalten Sie die Zuordnung bei.

1. Zuordnung beibehalten **products\[\*].price** zu **productListItems\[\*].priceTotal**

## Hinzufügen von Überschreibungen für bestimmte Felder

1. Überschreiben der Objektkopie-Zuordnungen durch
   1. Zuordnung **products\[\*].make** zu **productListItems\[\*].\_devbc.make**
   2. Zuordnung **products\[\*].model** zu **productListItems\[\*].\_devbc.model**

## Löschen von Überschreibungen in bestimmten Feldern

1. Beachten Sie **dass „productListItems.currencyCode** und **productListItems.quantity** automatisch ausgefüllt werden.
1. Entfernen Sie die **productListItems\[\*].quantity** und **productListItems\[\*].currencyCode**-Zuordnungen.
1. Die Überschreibungen finden nicht statt und die Objektkopie übernimmt mit durchlaufenden Passthrough-Feldern.


## Zusammenfassung der Objektkopie-Zuordnungen, -Überschreibungen und -Löschvorgänge

| Source-Spalte | XDM-Spalte | Aktion |
| -------------------------- | ----------------------------------- | -------------------------------------- |
| Produkte\[\*] | productListItems\[\*] | `Add` |
| products\[\*].productID | productListItems\[\*].SKU | `Add` |
| products\[\*].productID | productListItems\[\*].\_id | `No change` |
| products\[\*].make | productListItems\[\*].\_devbc.make | `Change` |
| products\[\*].model | productListItems\[\*].\_devbc.model | `Change` |
| Produkte\[\*].Preis | productListItems\[\*].priceTotal | `No change` |
| products\[\*].quantity | productListItems\[\*].quantity | `Remove` |
| products\[\*].currencyCode | productListItems\[\*].currencyCode | `Remove` |

## Überprüfen von Zuordnungen

Es gibt zwei Sätze von Zuordnungen, die Sie überprüfen sollten. Insgesamt sollten Sie nach dem Entfernen von 2 über 6 Zuordnungen verfügen.



![Resultierende Zuordnungen für productListItems nach dem Hinzufügen von Objektkopieüberschreibungen](assets/object-copy-mappings-resultant-mappings-for-productlistitems.png "Die resultierenden Zuordnungen für productListItems\[*] sollten wie folgt aussehen")

![Zweite Ansicht der resultierenden Zuordnungen für productListItems nach Überschreibungen der Objektkopie](assets/object-copy-mappings-resultant-mappings-for-productlistitems--2.png)
