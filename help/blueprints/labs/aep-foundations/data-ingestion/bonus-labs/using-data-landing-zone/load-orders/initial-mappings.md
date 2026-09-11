---
hold: true
title: Erste Zuordnungen
description: Ordnen Sie die erforderlichen _id- und Zeitstempelfelder für einen Erlebnisereignis-Datensatz mithilfe berechneter Feldausdrücke manuell zu.
doc-type: article
solution: Experience Platform
exl-id: 4052d104-bf0c-4b2d-a298-8075279aeaf8
source-git-commit: 2b2b9b9c359c4cc6757ac62ad502ece9a4923095
workflow-type: tm+mt
source-wordcount: '382'
ht-degree: 0%

---


# Erste Zuordnungen

Wie in der vorherigen Übung müssen Sie die Zuordnung überprüfen und in einigen Fällen ändern.

## ML-Empfehlungen überprüfen

1. Im Schritt Zuordnung ordnen ML-Empfehlungen automatisch die meisten Attribute zu. Es werden jedoch auch mehrere Fehler angezeigt. Der Startbildschirm sieht in etwa wie folgt aus.

![Zuordnungsbildschirm, der _id und Zeitstempel als nicht zugeordnete Felder anzeigt, die nicht von ML_id &#x200B;](assets/initial-mappings-id-timestamp-unmapped-fields.png " werden, sind Zeitstempel zwei Felder, für die der ML-Recommender die Zuordnung nicht generieren wird")

>[!NOTE]
>
>Da wir zum ersten Mal einen Erlebnisereignis-Datensatz zuordnen, beachten Sie, dass **\_id** und **timestamp** für Erlebnisereignisse nie standardmäßig empfohlen oder zugeordnet werden. Sie müssen manuell sicherstellen, dass diese korrekt zugeordnet sind.

## \_id, Zeitstempel und Reihenfolge zuordnen.\_devbc.acqSource-Felder

1. Um **\_id zuzuordnen,** Sie den folgenden berechneten Feldausdruck ein und klicken Sie auf „Vorschau“

```none
concat(orderID, "-", lastOrderStatusUpdate)
```

![Berechnetes Feld für Zuordnung _id, bereit zum Speichern](assets/initial-mappings-calculated-field-for-id-mapping.png "Berechnetes Feld für Zuordnung _id sieht in etwa so aus. Klicken Sie auf Speichern , um das berechnete Feld zu speichern")

![Zuordnen des berechneten Felds zum _id-Attribut](assets/initial-mappings-map-calculated-field-to-id.png "Zuordnen des berechneten Felds zu _id")

1. Stellen Sie sicher **dass** Feld „Zeitstempel“ im Zielschema dem folgenden berechneten Feld zugeordnet wird:

```none
lastOrderStatusUpdate
```

![Vorschau des berechneten Feldausdrucks für die Zeitstempelzuordnung: &#x200B;](assets/initial-mappings-expression-preview.png " Sie folgenden Ausdruck und klicken Sie auf „Vorschau“. Beachten Sie, dass bei diesem Wert zwischen Groß- und Kleinschreibung unterschieden wird und er genau so geschrieben werden muss")

![Zuordnen des berechneten Feldausdrucks „inStore“ zu order._devbc.acqSource](assets/initial-mappings-map-instore-expression-to-acqsource.png)

1. Ordnen Sie den berechneten Feldausdruck **„inStore“** zu **order.\_devbc.acqSource**

![Schreiben des berechneten Feldausdrucks „inStore“ und Klicken auf „Vorschau](assets/initial-mappings-write-instore-expression-preview.png "Schreiben Sie folgenden Ausdruck und klicken Sie auf „Vorschau“. Beachten Sie, dass bei diesem Wert zwischen Groß- und Kleinschreibung unterschieden wird und er genau so geschrieben werden muss")

## Umgang mit doppelten Zuordnungen

Wenn im Zuordnungsbildschirm jetzt eine doppelte Zuordnung angezeigt wird, z. B. **orderStatus**, die **order.\_devbc.acqSource zugeordnet ist,** klicken Sie auf das Symbol &quot;-&quot;, um die Zuordnung zu entfernen.

&#x200B;> [!NOTE]
>
>Beachten Sie, dass mehrere Eingabefelder nicht demselben Ausgabefeld zugeordnet werden können, da dies die Zuordnung mehrdeutig macht. Ein einzelnes Eingabefeld kann jedoch mehreren Ausgabefeldern im XDM-Schema zugeordnet werden.

![Warnung zur Duplikatzuordnung für orderStatus, der order._devbc.acqSource](assets/initial-mappings-duplicate-mapping-warning.png "Duplicate-Zuordnung für orderStatus, der order._devbc.acqSource zugeordnet ist")



![Warnung zur Duplikatzuordnung für order._devbc.acqSource nach der Erstellung des berechneten Felds](assets/initial-mappings-duplicate-mapping-for-acqsource.png "Duplikatzuordnung für order._devbc.acqSource, da wir ein berechnetes Feld erstellt haben und es bereits zugeordnet haben. ")
