---
title: Erstellen eines Datenstroms
description: Erfahren Sie, wie Sie mit Adobe Experience Platform-, Offer Decisioning- und Journey Optimizer-Services einen Datenstrom erstellen und konfigurieren, um die Edge-Ereignisverarbeitung zu aktivieren.
doc-type: article
solution: Experience Platform
exl-id: 37873340-476a-4303-886d-de4835bba8df
source-git-commit: 3039df0c022176e9dada9c5a300f2df14429033d
workflow-type: tm+mt
source-wordcount: '339'
ht-degree: 0%

---


# Erstellen eines Datenstroms

## Lernziel

Erstellen und konfigurieren Sie einen Datenstrom mit den erforderlichen Services, um die Edge-Ereignisverarbeitung zu aktivieren.

Ein Datenstrom definiert, welche Services ihn verwenden werden.

- Beim Senden von Daten an die Edge geben Sie an, welcher Datenstrom verwendet werden soll
- Daten, die an diese Datenströme gesendet werden, können dann entsprechend dem konfigurierten Service Aktionen ausführen
  - Adobe Experience Platform

## Erstellen eines neuen Datenstroms

1. Klicken Sie in der linken Leiste unter **Datenerfassung** auf **Datenströme**
1. Klicken Sie dann auf **Neuer Datenstrom**, um einen zu erstellen

![Liste der Datenströme mit hervorgehobener Schaltfläche „Neuer Datenstrom“](assets/create-datastream-new-datastream-button.png)

## Konfigurieren des Datenstroms

Konfigurieren Sie den Datenstrom mit folgenden Informationen:

1. Name -> **Datenstrom SB + \&lt;Sandbox-Name> (d. h. Datenstrom SB01)**
1. Zuordnungsschema -> **dep: Web**
1. Schalten Sie **on** alle Optionen unter **Geolocation und Netzwerk-Suche** ein, wenn Sie diese Informationen erfassen möchten.
1. Klicken Sie abschließend auf **Speichern**.

>[!WARNING]
>
>Klicken Sie nicht auf Speichern und Zuordnung hinzufügen .  Wenn Sie es versehentlich tun, brechen Sie einfach ab

![Datenstrom-Konfigurationsformular mit Namen- und Zuordnungsschemafeldern](assets/create-datastream-configure-datastream-form.png "Konfigurieren des Datenstroms")



Nach dem Speichern des Datenstroms wird der folgende Bildschirm angezeigt:

![Bestätigungsbildschirm nach dem Speichern des neuen Datenstroms](assets/create-datastream-created-confirmation.png "Datenstrom erstellt letzten Bildschirm")

## Adobe Experience Platform-Service hinzufügen

Auf diese Weise können Sie Daten an den Hub senden und für Daten, die von diesem Datenstrom empfangen werden, in einen Datensatz aufnehmen.

1. Klicken Sie auf **blaue Schaltfläche** Service hinzufügen“ in der Mitte des Bildschirms

![Schaltfläche „Service hinzufügen“ im Bildschirm zur Datenstromkonfiguration](assets/create-datastream-add-service-button.png)

&#x200B;2. Konfigurieren Sie die folgenden Elemente:
   - **Service** -> `Adobe Experience Platform`
   - **Ereignisdatensatz** -> `dep: Web`
   - **Profildatensatz** -> `dep: Customer Account`
   - **Kontrollkästchen auswählen** -> `Offer Decisioning`
   - **Kontrollkästchen auswählen** -> `Adobe Journey Optimizer`
&#x200B;3. Klicken Sie abschließend auf **Speichern**

![Dialogfeld für die Konfiguration des Adobe Experience Platform-Services mit Ereignis- und Profildatensatzfeldern](assets/create-datastream-configure-aep-service.png)

Der Service wird nun zu Ihrem Datenstrom hinzugefügt

![Zum Datenstrom hinzugefügter Adobe Experience Platform-Service](assets/create-datastream-aep-service-added.png "Im Datenstrom hinzugefügter Adobe Experience Platform-Service")

**Kopieren** und **Speichern** die **Datenstrom-ID** auf Ihrem lokalen Computer (wir werden sie später in Postman verwenden)

![Datenstrom-ID-Feld zum Kopieren und Speichern für die spätere Verwendung](assets/create-datastream-copy-datastream-id.png)

## Zusammenfassung

Es sollte ein funktionierender Datenstrom mit konfiguriertem Adobe Experience Platform-Service vorhanden sein.
