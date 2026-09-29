---
title: Erstellen eines Datenstroms
description: Erstellen und konfigurieren Sie einen Datenstrom mit Ereignisweiterleitungs- und Adobe Experience Platform-Services, um eingehende Edge-Ereignisse zu routen.
doc-type: article
solution: Experience Platform
exl-id: f7ada451-2f87-48f4-8673-7bfa0df9d0d3
product_v2:
  - id: edbd1a0e-46c8-49da-8c10-dba9ec80bba9
    internal-label: Experience Platform
source-git-commit: 1d6ba1444c119437eb8a86d5c4a1050d56d16023
workflow-type: tm+mt
source-wordcount: '392'
ht-degree: 1%
---

# Erstellen eines Datenstroms

Ein Datenstrom definiert, welche Services ihn verwenden.

- Beim Senden von Daten an die Edge geben Sie an, welcher Datenstrom verwendet werden soll
- Daten, die an diese Datenströme gesendet werden, können dann entsprechend dem konfigurierten Service Aktionen ausführen
  - Ereignisweiterleitung
  - Adobe Experience Platform

## Erstellen eines neuen Datenstroms

1. Klicken Sie in der linken Leiste unter **Datenerfassung** auf **Datenströme**
1. Klicken Sie dann auf **Neuer Datenstrom**, um einen zu erstellen

![Liste der Datenströme mit hervorgehobener Schaltfläche „Neuer Datenstrom“](assets/create-datastream-new-datastream-button.png)

## Konfigurieren des Datenstroms

Konfigurieren Sie den Datenstrom mit folgenden Informationen:

1. Name -> **Datenstrom SB + \&lt;Sandbox-Name> (d. h. Datenstrom SB01)**
1. Ereignisschema -> **dep: Web**
1. Schalten Sie **on** alle Optionen unter **Geolocation und Netzwerksuche**
1. Klicken Sie abschließend auf **Speichern**.

>[!WARNING]
>
>Klicken Sie nicht auf Speichern und Zuordnung hinzufügen .  Wenn Sie versehentlich abbrechen

![Datenstrom-Konfigurationsformular mit eingestellten Optionen für Name, Ereignisschema und Geolokalisierung](assets/create-datastream-configure-datastream-form.png "Konfigurieren des Datenstroms")



Nach dem Speichern des Datenstroms wird der folgende Bildschirm angezeigt:

![Bestätigungsbildschirm wird unmittelbar nach dem Speichern des neuen ](assets/create-datastream-created-confirmation-screen.png " angezeigt")

## Hinzufügen des Ereignisweiterleitungs-Service

Auf diese Weise können Sie die Ereignisweiterleitung für Daten verwenden, die von diesem Datenstrom empfangen werden.



1. Klicken Sie auf **Service hinzufügen**

   ![Datenstromdetailseite mit hervorgehobener Schaltfläche „Service hinzufügen“](assets/create-datastream-add-service-button.png "Service hinzufügen")

1. Konfigurieren Sie die folgenden Elemente:

   - Service -> Ereignisweiterleitung
   - Eigenschaft -> Wählen Sie die Eigenschaft aus, die Sie im vorherigen Schritt erstellt haben.  Sie sollte wie folgt benannt sein: Ereignisweiterleitungseigenschaft SB + \&lt;Ihre Sandbox-Nummer>
   - Umgebung -> Entwicklung

1. Klicken Sie abschließend auf **Speichern**

![Konfiguration des Ereignisweiterleitungs-Service mit ausgewählter Eigenschaft und Entwicklungsumgebung ](assets/create-datastream-event-forwarding-service-config.png "Konfigurationsbildschirm für die Ereignisweiterleitung")



## Adobe Experience Platform-Service hinzufügen

Auf diese Weise können Sie Daten an den Hub senden und für Daten, die von diesem Datenstrom empfangen werden, in einen Datensatz aufnehmen.



1. Klicken Sie auf **Service hinzufügen**

   ![Datenstromdetailseite mit hervorgehobener Schaltfläche „Service hinzufügen“ zum Hinzufügen des Adobe Experience Platform-Service](assets/create-datastream-add-second-service-button.png "Neuen Service hinzufügen")

1. Konfigurieren Sie die folgenden Elemente:

   - Service -> Adobe Experience Platform
   - Ereignisdatensatz -> Tiefe: Web
   - Profildatensatz -> Tiefe: Kundenkonto
   - Kontrollkästchen -> Edge-Segmentierung auswählen
   - Aktivieren Sie das Kontrollkästchen -> Personalization-Ziel

   ![Konfiguration des Adobe Experience Platform-Services mit aktivierten Kontrollkästchen für Ereignis-Datensatz, Profil-Datensatz und Segmentierung](assets/create-datastream-aep-service-config.png "Service konfigurieren")

1. Klicken Sie abschließend auf **Speichern**.

1. Ihr endgültiger Bildschirm sollte wie folgt aussehen, wobei zwei Services vorhanden sind. **Kopieren** und **Speichern** die **Datenstrom-ID** auf Ihrem lokalen Computer (Sie verwenden sie später in Postman)

![Endgültige Datenstromkonfiguration mit aufgelisteten Ereignisweiterleitungs- und Adobe Experience Platform-Services](assets/create-datastream-final-configuration-both-services.png "Endgültige Datenstromkonfiguration")
