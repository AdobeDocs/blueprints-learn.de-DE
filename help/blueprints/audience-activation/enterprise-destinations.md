---
title: Blueprint für die Aktivierung von Audiencen und Profilen zu Unternehmenszielen
description: Aktivierung von Audience und Profil zu Unternehmenszielen
solution: Experience Platform,Real-time Customer Data Platform
kt: 7475
exl-id: 32133174-eb28-44ce-ab2a-63fcb5b51cb5,None
translation-type: tm+mt
source-git-commit: d6eaf978a8f587b881480c14f192cb9e29e3c7e2
workflow-type: tm+mt
source-wordcount: '412'
ht-degree: 42%

---

# Blueprint für die Aktivierung von Audiencen und Profilen zu Unternehmenszielen

Geben Sie Profil- und Audiencen-Änderungen und Ereignis im Streaming- oder Batch-Format von [!UICONTROL Kundendatenplattform in Echtzeit] in Unternehmensdatenspeicher und -anwendungen frei. Diese Profil- und Audience-Ereignis können verwendet werden, um eine Verkaufs- oder Supportaktion für den Kunden einzuleiten, z. B. im Anschluss an einen abgebrochenen Antragsprozess oder eine Webinar-Registrierung, oder um Unternehmensanwendungen mit den neuesten Kundenattributen und Informationen von [!UICONTROL Kundendatenplattform in Echtzeit] zu aktualisieren.

## Anwendungsfälle

* Aktivierung von Profil und Audience zu Cloud-Datenspeicherung-Zielen oder Streaming-Zielen für die Unternehmensverfolgung, Datenspeicherung, Analyse und Aktivierung von Kundendaten und -einsichten.

## Programme

* Adobe Experience Platform Aktivierung

## Architektur

<img src="assets/enterprise_destination_activation.svg" alt="Referenzarchitektur für das Enterprise Aktivierung Szenario" style="border:1px solid #4a4a4a" />


## Leitlinien

Lesen Sie die auf der Seite &quot;Übersicht über die Audience und Profil-Aktivierung&quot;beschriebenen Garanten - [LINK](overview.md)

## Implementierungsschritte

1. [Erstellen Sie ](https://experienceleague.adobe.com/docs/platform-learn/tutorials/schemas/create-a-schema.html) Schemata für Daten, die aufgenommen werden sollen.
1. [Erstellen Sie ](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-ingestion/create-datasets-and-ingest-data.html) Datensätze, damit Daten erfasst werden.
1. [Konfigurieren Sie die korrekten Identitäten und Identitäts-Namespaces im Schema, um sicherzustellen, dass aufgenommene Daten zu einem einheitlichen Profil zusammengefügt werden können.](https://experienceleague.adobe.com/docs/platform-learn/tutorials/identities/label-ingest-and-verify-identity-data.html)
1. [Aktivieren Sie die Schema und Datensätze zum Profil](https://experienceleague.adobe.com/docs/platform-learn/tutorials/profiles/bring-data-into-the-real-time-customer-profile.html).
1. [Aufnehmen der Daten in Experience Platform.](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2020.1.dataingestion)
1. [Stellen Sie in Real-Time Customer Data Platform die Segmentfreigabe zwischen Experience Platform und Audience Manager für Zielgruppen bereit, die in Experience Platform für die Freigabe an Audience Manager definiert sind.](https://www.adobe.com/go/audiences)
1. [Erstellen Sie ](https://experienceleague.adobe.com/docs/platform-learn/tutorials/segments/create-segments.html?lang=de) Segmente in der Experience Platform. Das System stellt automatisch fest, ob das Segment per Batch oder Streaming evaluiert wird.
1. [Konfigurieren Sie Ziele für die Freigabe von Profilattributen Zielgruppenzugehörigkeiten zu gewünschten Zielen.](https://experienceleague.adobe.com/docs/platform-learn/tutorials/destinations/create-destinations-and-activate-data.html)

## Verwandte Dokumentation

* [Dokumentation zu Zielen](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/overview.html?lang=de)
* [Übersicht über die Ziele der Cloud-Datenspeicherung](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/cloud-storage/overview.html?lang=en#catalog)
* [HTTP-Ziel](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/http-destination.html?lang=en#overview)
* [Produktbeschreibung zu Real-Time Customer Data Platform](https://helpx.adobe.com/de/legal/product-descriptions/real-time-customer-data-platform.html)
* [Profil- und Segmentierungsrichtlinien](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=de)
* [Dokumentation zur Segmentierung](https://experienceleague.adobe.com/docs/experience-platform/segmentation/api/streaming-segmentation.html?lang=de)

## Verwandte Videos und Tutorials

* [Überblick über Real-Time Customer Data Platform](https://experienceleague.adobe.com/docs/platform-learn/tutorials/application-services/rtcdp/understanding-the-real-time-customer-data-platform.html?lang=de)
* [[!UICONTROL Demo zu Real-Time Customer Data Platform]](https://experienceleague.adobe.com/docs/platform-learn/tutorials/application-services/rtcdp/demo.html?lang=de)
* [Erstellen von Segmenten](https://experienceleague.adobe.com/docs/platform-learn/tutorials/segments/create-segments.html)
