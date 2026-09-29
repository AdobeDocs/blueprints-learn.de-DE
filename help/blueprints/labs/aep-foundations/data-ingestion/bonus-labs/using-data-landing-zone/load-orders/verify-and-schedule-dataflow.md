---
title: Datenfluss überprüfen und planen
description: Überprüfen Sie den vollständigen Zuordnungssatz für Bestellungen, zeigen Sie eine Vorschau der Ausgabe an und planen Sie die Ausführung des Datenflusses alle 15 Minuten.
doc-type: article
solution: Experience Platform
exl-id: b7f0c43b-092c-45ba-b95b-27cb4a49d110
product_v2:
  - id: edbd1a0e-46c8-49da-8c10-dba9ec80bba9
    internal-label: Experience Platform
source-git-commit: 1d6ba1444c119437eb8a86d5c4a1050d56d16023
workflow-type: tm+mt
source-wordcount: '403'
ht-degree: 7%
---

# Datenfluss überprüfen und planen

## Doppelte Überprüfung des Zuordnungssatzes

| # | Source-Spalte | XDM-Spalte |
| -- | ------------------------------------------- | -------------------------------------------------------- |
| 1 | orderStatus | eventType |
| 2 | lastOrderStatusUpdate | Zeitstempel |
| 3 | orderID | order.orderID |
| 4 | orderDate | order.orderDate |
| 5 | orderTotal | order.priceTotal |
| 6 | PaymentType | order.payment.paymentType |
| 7 | PaymentAmount | order.payment.paymentAmount |
| 8 | paymentCurrencyCode | order.payment.currencyCode |
| 9 | paymentTransactionID | order.payment.transactionID |
| 10 | plan.ID | order.\_devbc.plan.planID |
| 11 | customerID | \_devbc.customerID |
| 12 | personalEmail | \_devbc.personalEmail |
| 13 | storeID | store.storeID |
| 14 | shippingStreetAddress | shipping.address.street1 |
| 15 | shippingCity | shipping.address.city |
| 16 | shippingState | shipping.address.state |
| 17 | shippingZip | shipping.address.postalCode |
| 18 | shippingMethod | shipping.shippingMethod |
| 19 | shippingAmount | shipping.shippingAmount |
| 20 | shippingDestination | shipping.shippingDestination |
| 21 | billingStreetAddress | billing.address.street1 |
| 22 | billingCity | billing.address.city |
| 23 | BillingState | billing.address.state |
| 24 | billingZip | billing.address.PostalCode |
| 25 | Produkte\[\*] | productListItems\[\*] |
| 26 | products\[\*].productID | - productListItems\[\*].\_id - productListItems\[\*].SKU |
| 27 | products\[\*].make | productListItems\[\*].\_devbc.make |
| 28 | products\[\*].model | productListItems\[\*].\_devbc.model |
| 29 | Produkte\[\*].Preis | productListItems\[\*].priceTotal |
| 30 | concat(orderID, &quot;-&quot;, lastOrderStatusUpdate) | \_id |
| 31 | „inStore“ | order.\_devbc.acqSource |



## Vorschau der Zuordnungsausgabe

1. Vorschau der Zuordnungsausgabe. Scrollen Sie durch alle Attribute, um sicherzustellen, dass neben keinem der Attribute auf der rechten Seite ein roter Ausruf angezeigt wird.

   ![Zuordnungsbildschirm in der Vorschau anzeigen, ohne Fehler bei zugeordneten Attributen](assets/verify-and-schedule-dataflow-preview-mapping-screen.png " Der Zuordnungsbildschirm in der Vorschau wird wie folgt aussehen")

1. Wählen Sie in der linken Navigationsleiste der Vorschau das Objekt **productListItems**-Array aus. Die rechte Seite wird aktualisiert, sodass nur die Attribute in diesem Objekt-Array angezeigt werden.

>[!NOTE]
>
>Beachten Sie **dass „productListItems.currencyCode** und **productListItems.quantity** automatisch ausgefüllt werden (auch nach dem Entfernen der Zuordnungen). Dies geschieht, weil **productListItems** als übergeordnetes Objekt zugeordnet sind.

![Abgeschlossener Zuordnungsbildschirm für productListItems nach dem Entfernen doppelter Überschreibungen](assets/verify-and-schedule-dataflow-completed-mapping-screenshot.png "Abgeschlossene Zuordnung sieht dem folgenden Screenshot ähnlich")

## Planen des Durchgangs

1. Legen Sie den Zeitplan für die Ausführung **alle 15 Minuten** fest, indem Sie die Häufigkeit auf Minute und das Intervall auf 15 festlegen. Überprüfen Sie den Fluss und klicken Sie auf Beenden .

   >[!CAUTION]
   >
   >Stellen Sie sicher, dass Ihr Zeitplan auf 15 Minuten eingestellt ist. Wenn Sie die Ausführung als **Einmal ausführen** planen, können Sie sie auch dann nicht erneut ausführen, wenn Sie die Zuordnung später ändern.

1. Die Datenflussausführung startet nicht sofort und dauert einige Minuten. Der letzte Ausführungsstatus des Datenflusses ist also auf &quot;*Ausführungen“*.

1. Nach einigen Minuten ist der Datenfluss erfolgreich. Beachten Sie **„Letzter Ausführungsstatus für Datenfluss** und **Letztes Ausführungsdatum für Datenfluss**.

1. Klicken Sie auf den Namen des Datenflusses, um eine Liste der Datenflussausführungen zu erhalten. Es sollten 10 Datensätze aufgenommen werden.

1. Klicken Sie auf die Startzeit des Datenflusses, um Details zur Fehlerdiagnose anzuzeigen.

1. Navigieren Sie in der linken Navigationsleiste zu Datensätze in Platform und klicken Sie auf **Bestellungen - IhrNameHier**

1. Klicken Sie auf **Datensatz in der Vorschau anzeigen.**
