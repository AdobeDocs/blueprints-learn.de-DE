---
hold: true
title: Endgültigen Zuordnungssatz überprüfen
description: Vergleichen Sie Ihre einfachen und berechneten Feldzuordnungen für das Kundenkontenschema mit dem erwarteten endgültigen Zuordnungssatz.
doc-type: article
solution: Experience Platform
exl-id: d1521d08-1ccb-405f-b728-a2777598cb9f
source-git-commit: 2b2b9b9c359c4cc6757ac62ad502ece9a4923095
workflow-type: tm+mt
source-wordcount: '214'
ht-degree: 0%

---


# Endgültigen Zuordnungssatz überprüfen

> [!NOTE]
>
>Wenn Sie vom Streaming-Aufnahme-Labor kommen, klicken Sie auf den folgenden Link, um mit dem nächsten Schritt in diesem Labor fortzufahren:
>
>[Streaming-Aufnahme-Lab - Überprüfen des endgültigen Zuordnungssatzes](../../stream-ingestion/check-final-mapping-set.md)



## Einfache Zuordnungen

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

> [!NOTE]
>
>Stellen Sie sicher, dass Ihre endgültige Zuordnung mit der unten gezeigten übereinstimmt, bevor Sie fortfahren.



## Berechnete Zuordnungen

| Berechnete Felder | XDM-Feld |
| ------------------------------------------------------------------------------------------------------------------------------------- | -------------------------- |
| iif(sms\_optIn == null oder sms\_optIn == &quot;&quot;, &#39;n&#39;, sms\_optIn) | consents.marketing.sms.val |
| concat(date\_part(„month“, date(born\_date,„M/d/yyyy„)).toString(), &quot;-&quot;, date\_part(„day“, date(born\_date,„M/d/yyyy„)).toString()) | person.bornDayAndMonth |
| date\_part(„jjjj“,date(Geburtsdatum,„M/TT/jjjj„)) | person.BirthYear |

> [!NOTE]
>
>Stellen Sie sicher, dass Ihre endgültige Zuordnung mit der unten gezeigten übereinstimmt, bevor Sie fortfahren
