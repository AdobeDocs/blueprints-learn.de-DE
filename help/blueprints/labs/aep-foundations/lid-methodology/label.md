---
hold: true
title: Label
description: Kennzeichnen Sie relationale Data Warehouse-Tabellen als Klassen für individuelles XDM-Profil, Erlebnisereignis oder Suche als Teil der LID-Methodik.
doc-type: article
solution: Experience Platform
exl-id: 332ead7a-ca6e-4e30-bb35-8419c060c596
source-git-commit: 2b2b9b9c359c4cc6757ac62ad502ece9a4923095
workflow-type: tm+mt
source-wordcount: '370'
ht-degree: 0%

---


# Label

## Vortrag

In diesem Video erfahren Sie, wie Sie relationale Tabellen als Tabelle mit XDM-Kontaktprofil (P), Erlebnisereignis (E) oder Lookup (L) beschriften können, indem Sie als Beispiel die Verbindung 5G ERD verwenden.

>[!VIDEO](https://video.tv.adobe.com/v/3459087/?quality=12&learn=on)



## Labor-Details

Kennzeichnen Sie die Tabellen aus dem Data Warehouse ERD der Verbindung 5G und dem Streaming-ERD mit der entsprechenden XDM-Klassenbezeichnung für die Tabellen „Individuelles Profil“, „Erlebnisereignis“ und „Suche“.

Beachten Sie bei der Durchführung des Labors Folgendes:

- **Individuelles Profil (Eigenschaften) -** beschreibt die Eigenschaften einer Person eindeutig (z. B. Name, E-Mail, Adresse, Voreinstellungen usw.)
- **Erlebnisereignis (Verhalten) -** Beschreibung der Interaktionen und Touchpoints, die eine Person mit einer Marke/einem Unternehmen hat (z. B. Web-Seitenbesuch, Kauf, Callcenter-Interaktionen, Senden von Anwendungen usw.)
- **Lookups (unterstützend) -** bieten zusätzliche kontextuelle Informationen zur Unterstützung des jeweiligen Profils oder Erlebnisereignisses



## Schritt 1. Kennzeichnen von einzelnen XDM-Profiltabellen

1. Identifizieren Sie alle Quelltabellen, die eine einzelne Person sowohl im Kunden-Data-Warehouse-ERD als auch im Kunden-Streaming-ERD darstellen.
1. Markieren Sie jede Tabelle mit einem &quot;**P**&quot;, was bedeutet, dass sie Teil der Klasse „XDM Individual Profile“ ist

>[!NOTE]
>
>Markieren Sie nur die Tabellen, die die Eigenschaften einer Person eindeutig darstellen



## Schritt 2. Kennzeichnen von XDM-Erlebnisereignistabellen

1. Identifizieren Sie alle Quelltabellen, die das Verhalten einer einzelnen Person sowohl im Data Warehouse ERD der Verbindung 5G als auch im Streaming-ERD darstellen.
1. Markieren Sie jede Tabelle mit einem &quot;**E**&quot;, was bedeutet, dass sie Teil der XDM Experience Event-Klasse ist.

>[!NOTE]
>
>Markieren Sie nur die Tabellen, die das Verhalten einer Person eindeutig darstellen



## Schritt 3. Kennzeichnen von XDM-unterstützenden Tabellen

1. Identifizieren Sie alle Quelltabellen, die Suchdaten darstellen und direkt mit einer **„P“**- oder **„E“**-Tabelle verbunden sind, die Sie entweder im Data Warehouse ERD von Connection 5G oder im Streaming-ERD markiert haben.
1. Markieren Sie jede Tabelle mit einem **„L**, was bedeutet, dass sie Teil einer benutzerdefinierten XDM-Klasse ist, die keine Person ist.

>[!NOTE]
>
>Suchtabellen können nur 1 Join-Ebene oder „Hop“ von einer mit „P“ oder „E“ beschrifteten Tabelle entfernt sein



## Überprüfung

Im folgenden Video werden die korrekten Beschriftungen für die Data Warehouse- und Streaming-ERDs von Connection 5G überprüft, wobei erläutert wird, warum das Kundenkonto, die Bestellungen und die Abrechnungstabellen so beschriftet wurden, wie sie waren.

>[!VIDEO](https://video.tv.adobe.com/v/3459081/?quality=12&learn=on)
