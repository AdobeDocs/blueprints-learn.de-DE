---
title: Blueprint für die Aktivierung von Audiencen und Profilen zu Unternehmenszielen
description: Aktivierung von Audience und Profil zu Unternehmenszielen
solution: Experience Platform,Real-time Customer Data Platform
kt: 7475
exl-id: 32133174-eb28-44ce-ab2a-63fcb5b51cb5,None
translation-type: tm+mt
source-git-commit: 8bcd82eac5e8837c3cd84524174cf5792d73ac6e
workflow-type: tm+mt
source-wordcount: '662'
ht-degree: 0%

---

# Blueprint für die Aktivierung von Audiencen und Profilen zu Unternehmenszielen

Replikation und Aktualisierung von Profil- und Audience-Änderungen an Unternehmensdatenspeichern für Aktivierung- und Berichte-Anwendungsfälle.

Starten Sie eine Verkaufs- oder Supportaktion für den Kunden durch Benachrichtigung über eine Kundenaktion von der Echtzeit-Kundendatenplattform zu Unternehmenssystemen und -anwendungen.

## Anwendungsfälle

* Aktivierung von Profil und Audience zu Cloud-Datenspeicherung-Zielen oder Streaming-Zielen für die Unternehmensverfolgung, Datenspeicherung, Analyse und Aktivierung von Kundendaten und -einblicken.

## Anwendungen

* Adobe Experience Platform Aktivierung

## Architektur

<img src="assets/enterprise_destination.svg" alt="Referenzarchitektur für das Enterprise Aktivierung Szenario" style="border:1px solid #4a4a4a" />

## Guardraht

[Profil- und Segmentierungsrichtlinien](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=en)

Latenz- und Durchsatzschwellenwerte:

Streaming-Segmentierung:

* Bis zu 5 Minuten für Streaming-Segmentierung mit bis zu 1500 Ereignissen pro Sekunde
* Bis zu 11 Minuten für Streaming-Aktivierungen

Stapelsegmentierung:
Einmal pro Tag oder manuell über API initiierte Ad-hoc-Analysen

* Etwa 1 Stunde pro Arbeitsplatz für bis zu 10 TB Profil
* Etwa 2 Stunden pro Arbeitsplatz bei einer Speichergröße von 10 TB bis 100 TB Profil

## Implementierungsschritte

1. Erstellen von Schemas für zu ingetierende Daten
1. Erstellen von Datensätzen für die Erfassung von Daten
1. Konfigurieren Sie die richtigen Identitäten und Identitäts-Namensraum auf dem Schema, um sicherzustellen, dass erfasste Daten zu einem einheitlichen Profil gehören können.
1. Aktivieren Sie die Schema und Datensätze für die Verarbeitung von Profilen.
1. Konfigurieren von beliebigen Quellen für die Datenerfassung
1. Autorensegmente in Experience Platform, die im Batch- oder Streaming-Verfahren ausgewertet werden sollen. Das System ermittelt automatisch, ob das Segment als Stapel oder Streaming ausgewertet wird.
1. Konfigurieren Sie Ziele für die Freigabe von Profil-Attributen und die Audience-Mitgliedschaft für die gewünschten Ziele.

## Überlegungen zur Implementierung

Aktivierung von Attributen und Identitäten

* Die Echtzeit-Kundendatenplattform kann sowohl Audiencen-Mitgliedschaften als auch Attribut- und Identitätsänderungen aktivieren, die bei Profilen auftreten, die Segmentmitglieder sind, die zur Aktivierung ausgewählt wurden. Wenn der Anwendungsfall die Aktivierung von Attributen und/oder Identitäten ist, muss ein globales Segment definiert werden, das alle Profil umfasst, für die Attribute/Identitätsaktualisierungen gesendet werden, müssen definiert werden. Sobald dies erfolgt ist, können das zu aktivierende Segment und die gewünschten Attribute als Teil der Zielkonfiguration ausgewählt werden.
* Beachten Sie, dass Batch-Ziele keine Aktivierung von Attributen unterstützen, sondern nur Ereignis ändern. Die Mitgliedschaft in voller oder inkrementeller Audience kann zur Aktivierung zusammen mit den ausgewählten Attributen gesendet werden, aber Ereignis mit nur Attributänderungen können nicht über Batch-Ziele aktiviert werden.

Aktivierung des Stapelsegments zu Streaming-Zielen

* Die Aktivierung des Stapelsegments auf Streaming-Ziele wird unterstützt. Stapelsegmentaufträge platzieren Meldungen in der Pipeline, sobald der Segmentauftrag für die Streaming-Aktivierung abgeschlossen ist

Segmentziel-Aktivierung an Stapelziele streamen

* Die Streaming-Segmentzielsetzung wird unterstützt. Der Stapelziel-Plan exportiert Segmentmitgliedschaften der Profil auf Grundlage des Stapelzielplans. Dies umfasst sowohl Segmentmitgliedschaften, die über Streaming- als auch Batch-Methoden bestimmt werden.

Aktivierung von Experience Ereignisses

* Die Aktivierung von unformatierten Experience-Ereignissen wird derzeit nicht unterstützt. Zum Aktivieren gegen Erlebnis-Ereignis muss ein Segment mit den erforderlichen Regeln erstellt werden, die die Erlebnis-Ereignis-Logik einschließen/ausschließen, für die aktiviert werden soll. Dadurch wird ein Segment erstellt, das für Erlebnis-Ereignis definiert wird - und die Segmentmitgliedschaft kann als Proxy zur Aktivierung von unformatierten Erlebnis-Ereignissen aktiviert werden. Erwägen Sie auch die Verwendung der Startseite für die Aktivierung von über SDK erfassten Experience-Ereignissen.

## Verwandte Dokumentation

* [Dokumentation zu Zielen](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/overview.html)
* [Enterprise Cloud-Datenspeicherung-Ziele](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/cloud-storage/overview.html?lang=en#catalog)
* [HTTP-Ziel](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/http-destination.html?lang=en#overview)
* [Produktbeschreibung der Echtzeit-Kundendatenplattform](https://helpx.adobe.com/legal/product-descriptions/real-time-customer-data-platform.html)
* [Profil- und Segmentierungsrichtlinien](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=en)
* [Dokumentation zur Segmentierung](https://experienceleague.adobe.com/docs/experience-platform/segmentation/api/streaming-segmentation.html)

## Verwandte Videos und Tutorials

* [Übersicht über die Echtzeit-Kundendatenplattform](https://experienceleague.adobe.com/docs/platform-learn/tutorials/application-services/rtcdp/understanding-the-real-time-customer-data-platform.html)
* [Demo der Echtzeit-Kundendatenplattform](https://experienceleague.adobe.com/docs/platform-learn/tutorials/application-services/rtcdp/demo.html)
* [Segmente erstellen](https://experienceleague.adobe.com/docs/platform-learn/tutorials/segments/create-segments.html)
