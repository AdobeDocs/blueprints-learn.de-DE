---
title: denormalisieren
description: Wenden Sie die Denormalisierungsregeln der LID-Methodik an, um Bridge- und abhängige Tabellen von einem ERD wieder in ihre übergeordneten Profil-, Ereignis- und Lookup-Tabellen zu falten.
doc-type: article
solution: Experience Platform
exl-id: c98c9f58-03bc-4b28-becb-f84f3de04300
product_v2:
  - id: edbd1a0e-46c8-49da-8c10-dba9ec80bba9
    internal-label: Experience Platform
source-git-commit: 1d6ba1444c119437eb8a86d5c4a1050d56d16023
workflow-type: tm+mt
source-wordcount: '436'
ht-degree: 0%
---

# denormalisieren

## Vortrag

In diesem Video erfahren Sie, wie die drei Denormalisierungsregeln zum Falten von Lookup- und Bridge-Tabellen zurück in die übergeordneten Tabellen verwendet werden und wie sich Personalisierungs- und Streaming-Segmentierungsanforderungen auf diese Entscheidungen auswirken.

>[!VIDEO](https://video.tv.adobe.com/v/3459083/?quality=12&learn=on)



## Labor-Details

>[!NOTE]
>
>Dieses Labor konzentriert sich nur auf die Verbindung 5G Warehouse ERD

## Denormalisierungsregeln:

1. Jede Tabelle im relationalen Modell, die als &quot;**D**&quot; mit einer 1\:M-Kardinalität oder als &quot;**B**&quot; gekennzeichnet ist, wird als Objekt-Array oder -Zuordnung in der übergeordneten Tabelle definiert
1. Wird durch Regel #1 ausgelöst und fragt vor der Denormalisierung von &quot;**D**&quot;- oder &quot;**B**&quot;-Tabellen, die als Arrays oder Zuordnungen dienen, diese ab, um zu bestimmen, wie sie am besten wieder in ihre übergeordnete Tabelle denormalisiert werden können
1. Jede Tabelle im relationalen Modell, die als &quot;**D**&quot; mit einer Kardinalität von M:1 gekennzeichnet ist, agiert als Objekt oder Liste von Feldern in der übergeordneten Tabelle

## Denormalisierung für Personalisierungsregeln:

Denken Sie beim Erstellen des Datenmodells immer daran, die Anwendungsfälle für Kunden zu überprüfen.  Beachten Sie Folgendes:

- Die Streaming-Segmentierung hat zum Zeitpunkt der Auswertung keinen Zugriff auf Lookup-Tabellen
- Für die Personalisierung von Inhalten sind nur die Eigenschaften und Segmentzugehörigkeiten eines Profils verfügbar

![Bei der Anwendung der Denormalisierung für Personalisierung berücksichtigte Anwendungsfälle für die Verbindung ](assets/denormalize-connection-5g-use-cases.png " 5G")

>[!NOTE]
>
>Denken Sie daran, in diesem Labor auf die Datei Connection 5G Training Scenario.pdf zu verweisen!



## Schritt 1: Ausfüllen der Tabelle „Individuelles Profil“

1. Schreiben Sie die Felder, die wieder denormalisiert werden müssen, aus allen zugehörigen &quot;**B“-** &quot;**D**-Schemata zurück in die Tabelle des Kundenkontos
1. Welche zusätzlichen Felder sind erforderlich, um die Streaming-Segmentierung und/oder Personalisierung zu unterstützen, sollten die oben genannten Anwendungsfälle geprüft werden? Fügen Sie diese Felder zur Tabelle hinzu



## Schritt 2: Ausfüllen der Erlebnisereignistabellen

1. Schreiben Sie die Felder, die denormalisiert werden müssen, wieder in die Tabellen Abrechnung und Bestellungen aus allen zugehörigen &quot;**B**&quot; oder &quot;**D**&quot;
1. Welche zusätzlichen Felder sind erforderlich, um die Streaming-Segmentierung und/oder Personalisierung zu unterstützen, sollten die oben genannten Anwendungsfälle geprüft werden? Fügen Sie diese Felder zur Tabelle hinzu



## Schritt 3: Ausfüllen der Lookup-Tabellen

1. Schreiben Sie die Felder, die wieder denormalisiert werden müssen, aus allen zugehörigen „B ****&quot;- oder &quot;**D**-Tabellen zurück in die Produktsuchtabelle
1. Welche zusätzlichen Felder sind erforderlich, um die Streaming-Segmentierung und/oder Personalisierung zu unterstützen, sollten die oben genannten Anwendungsfälle geprüft werden? Fügen Sie diese Felder zur Tabelle hinzu




## Überprüfung

Im folgenden Video wird gezeigt, wie die Verbindungs-5G-Tabellen in Arrays und Objekte denormalisiert wurden und wie die Anwendungsfälle Akquise und Upsell es erforderlich machten, zusätzliche Felder wieder in die primären Profil- und Ereignistabellen zu bringen.

>[!VIDEO](https://video.tv.adobe.com/v/3459086/?quality=12&learn=on)
