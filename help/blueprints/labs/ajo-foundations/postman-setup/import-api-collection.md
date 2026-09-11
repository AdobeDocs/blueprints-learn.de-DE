---
title: API-Sammlung importieren
description: Importieren Sie die Postman-API-Sammlung des Bootcamps und überprüfen Sie, ob die Umgebungsvariablen korrekt in Ihrer Sandbox aufgelöst werden.
doc-type: article
solution: Experience Platform
exl-id: 7562c7f1-0d60-4a3a-8bce-fa42bda08962
source-git-commit: 3039df0c022176e9dada9c5a300f2df14429033d
workflow-type: tm+mt
source-wordcount: '432'
ht-degree: 0%

---


# API-Sammlung importieren

## Ziel

In diesem Schritt importieren Sie die API-Sammlung, die alle verschiedenen Anfragen enthält, die Sie im gesamten Bootcamp ausführen müssen.  Diese API-Anfragen sind von der soeben importierten Umgebungsdatei abhängig.



## Anforderungssammlung importieren

1. Laden Sie die Datei **AJO Bootcamp (Labs).postman\_collection.json** herunter:

Datei herunterladen - [AJO Bootcamp (Labs).postman_collection.json](assets/ajo-bootcamp-labs.postman_collection.json)

2. Klicken Sie wie zuvor auf die Schaltfläche **Importieren**.
3. Fügen Sie die lokale URL der Datei **AJO Bootcamp (Labs).postman\_collection.json** in das Textfeld „Modal importieren“ ein oder legen Sie sie im Dialogfeld „Importieren“ ab.  Dadurch wird ein automatischer Import Trigger.
4. Klicken Sie nach Abschluss des Importvorgangs in der linken **auf** Sammlungen“, erweitern Sie den Ordner **AJO Bootcamp (Labs** und Sie sehen die neu importierte Sammlung

![Überprüfen des Imports der Postman-Sammlung](assets/import-api-collection-verify-collection-imported.png)

>[!TIP]
>
>Herzlichen Glückwunsch!  Sie haben die Postman-Sammlung des Bootcamps erfolgreich importiert



## Validieren von Umgebungsvariablen

Die Sammlung, die Sie importiert haben, enthält alle notwendigen API-Aufrufe, die Sie für Labs im gesamten Bootcamp benötigen.  Jedes Labor ist in einen bestimmten Ordner mit eigenen Anforderungen unterteilt.

Details zu den einzelnen Ordnern finden Sie unten:

- **Profile &amp; Journey Labs** - Enthält eine Reihe von Anfragen zum Senden eines Web-Ereignisses und eines Ereignisses, das eine Versandbestätigung simuliert.
- **Decisioning Labs** - Enthält Anfragen für drei Besuchende, die die Aufrufe der oberen und unteren Seite imitieren, die normalerweise auf einer mit AEP Web SDK-Tags versehenen Site zu finden sind.

Um sicherzustellen, dass die Umgebung und die Sammlung korrekt funktionieren, führen Sie die folgenden Schritte aus.

1. Klicken Sie ggf. in der linken Leiste auf **Sammlungen** und erweitern Sie dann den Ordner **Profile &amp; Journey Labs** .
2. Klicken Sie auf die **Web-Ereignis erstellen**-Anfrage und Sie sehen, dass die Umgebungsvariablen **rot**

![Postman-Anfrage mit rot markierten Umgebungsvariablen, da keine Umgebung ausgewählt ist](assets/import-api-collection-environment-variables-shown-red.png " Überprüfen Sie, ob Postman-Umgebungsvariablen rot sind")

3. Klicken Sie oben rechts auf **Dropdown** Umgebung und wählen Sie die **AJO Bootcamp**-Umgebung.

![Wählen Sie die richtige Postman-Umgebung aus](assets/import-api-collection-select-postman-environment.png)

4. Wenn Sie die richtige Umgebung ausgewählt haben, sehen Sie, dass die Variable EDGE\_REGION jetzt eine hellere blaue Farbe annimmt. Dies zeigt an, dass die Variable jetzt einen Wert für die ausgewählte Umgebung hat. Die Variable DATASTREAM\_CONFIG bleibt rot, da Sie den Datenstrom noch nicht erstellt haben, sodass Sie für diese Umgebungsvariable noch keinen Wert haben. Wenn Sie den Mauszeiger über die EDGE\_REGION bewegen, sehen Sie den Wert des Umgebungswerts.

Die Variable ![Postman EDGE_REGION ist jetzt ausgefüllt und wird nicht mehr in rot angezeigt](assets/import-api-collection-environment-works-with-collection.png " Überprüfen Sie, ob die Postman-Umgebung mit der Sammlung funktioniert")

## Zusammenfassung

Sie haben jetzt die Umgebungs- und Sammlungsdateien importiert und wissen, wie Sie sie verwenden können.
