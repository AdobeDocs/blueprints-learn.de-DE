---
title: Endgültigen Zuordnungssatz überprüfen
description: Vergleichen Sie Ihre Streaming-Aufnahme-Zuordnungen mit dem erwarteten endgültigen Passthrough und dem berechneten Feld-Zuordnungssatz.
doc-type: article
solution: Experience Platform
exl-id: 8802aaca-f566-4972-8bd6-41aca9fae9bf
source-git-commit: 3039df0c022176e9dada9c5a300f2df14429033d
workflow-type: tm+mt
source-wordcount: '277'
ht-degree: 0%

---


# Endgültigen Zuordnungssatz überprüfen

## Passthrough-Zuordnungen

&#x200B;> [!NOTE]
>
>Stellen Sie sicher, dass Ihre endgültige Zuordnung mit der unten gezeigten übereinstimmt, bevor Sie fortfahren.

>[!NOTE]
>
>Ersetzen Sie \&lt;tenant-name> durch den Wert aus Ihrer Sandbox.

| Source-Feld | Zielfeld |
| ------------------------- | --------------------------------- |
| account\_create\_date | \&lt;tenant-name>.account.createDate |
| account\_end\_date | \&lt;tenant-name>.account.endDate |
| customer_id | \&lt;tenant-name>.customerID |
| plan\_name | \&lt;tenant-name>.plan.name |
| plan\_id | \&lt;tenant-name>.plan.planID |
| billing\_city | billingAddress.city |
| billing\_zip\_code | billingAddress.PostalCode |
| billing\_state | billingAddress.state |
| billing\_street\_address | billingAddress.street1 |
| email\_optIn | consents.marketing.email.val |
| Mobiltelefon\_phone | mobilePhone.number |
| firstName | person.name.firstName |
| lastName | person.name.lastName |
| E-Mail | personalEmail.address |
| createDate | repo.createDate |
| modifyDate | repo.modifyDate |
| shipping\_city | shippingAddress.city |
| shipping\_zip\_code | shippingAddress.postCode |
| shipping\_state | shippingAddress.state |
| shipping\_street\_address | shippingAddress.street1 |



## Berechnete Zuordnungen

>[!NOTE]
>
>Beachten Sie, dass sich die Zuordnungen für `birth_Date` aufgrund der Formatierung des Datums von den Zuordnungen für das Batch-Aufnahme-Labor unterscheiden.  Batch verwendet Schrägstriche `/` beim Streaming werden Bindestriche `-`

| Berechnete Felder | XDM-Feld |
| ----------------------------------------------------------------------------------------------------------------------------------- | -------------------------- |
| iif(sms\_optIn == null oder sms\_optIn == &quot;&quot;, &#39;n&#39;, sms\_optIn) | consents.marketing.sms.val |
| concat(date\_part(„mm“, date(born\_date, „yyyy-M-d„)).toString(), &quot;-&quot;, date\_part(„dd“, date(born\_date, „yyyy-M-d„)).toString()) | person.bornDayAndMonth |
| date\_part(„jjjj“,date(Birth\_Date,„jjjj-M-d„)) | person.BirthYear |

&#x200B;> [!NOTE]
>
>Stellen Sie sicher, dass Ihre endgültige Zuordnung mit der unten gezeigten übereinstimmt, bevor Sie fortfahren



## Datenfluss abschließen

Wenn Sie fertig sind, klicken Sie auf die Schaltfläche **Weiter** und anschließend auf die Schaltfläche Beenden , um den Datenfluss mit der neuen Zuordnungslogik zu aktualisieren.

![Überprüfen der Datenflussdetails, bevor Sie auf Beenden klicken, um sie zu speichern](assets/check-final-mapping-set-review-and-finish-dataflow.png)



Jetzt sollte ein Bildschirm mit dem HTTP-API-Konto angezeigt werden, das Sie mit allen zugehörigen Datenflüssen erstellt haben, die dieses Konto verwenden. Der von Ihnen erstellte Datenfluss sollte ebenfalls angezeigt werden.
