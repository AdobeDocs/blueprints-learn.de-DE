---
title: Activation mit Online- und Offline-Daten-Blueprint
description: Online-/Offline-Zielgruppenaktivierung.
solution: Experience Platform, Real-time Customer Data Platform, Target, Audience Manager, Analytics, Experience Cloud Services, Data Collection
kt: 7086
exl-id: 011f4909-b208-46db-ac1c-55b3671ee48c
source-git-commit: 8f1d76c317dbe4c7e916b4513960b4549a2d3424
workflow-type: tm+mt
source-wordcount: '530'
ht-degree: 91%

---

# Activation mit Online- und Offline-Daten-Blueprint

Verwenden Sie Offline-Attribute und -Ereignisse, wie Offline-Bestellungen, Transaktionen, CRM oder Treue-Daten gemeinsam mit Online-Verhaltensdaten für Online-Targeting und Personalisierung.

Aktivieren Sie Zielgruppen für bekannte, profilbasierte Ziele, wie E-Mail-Anbieter, Social Media und Werbeziele.

Der Plan Aktivierung mit Online- und Offline-Daten ist eng mit dem Blueprint [Zielgruppen- und Profilaktivierung mit Experience Cloud-Anwendungen](platform-and-applications.md) abgestimmt. Zusätzliche Details finden Sie in der [Blueprint zur Zielgruppen- und Profilaktivierung mit Experience Cloud-Programmen](platform-and-applications.md) über Integrationen zwischen Experience Platform und Experience Cloud-Programmen.

## Anwendungsfälle

* Zielgruppen-Targeting für bekannte Zielgruppen in Social-Media- und Werbezielen.
* Online-Personalisierung mit Online- und Offline-Attributen.
* Aktivierung von Zielgruppen für bekannte Kanäle, wie E-Mail und SMS.

## Programme

* Adobe Experience Platform
* [!UICONTROL Real-Time Customer Data Platform]

## Architektur

### Aktivierung mit Online- und Offline-Daten mit Zielen

<img src="assets/online_offline_activation.svg" alt="Referenzarchitektur für die Blueprint „Online-/Offline-Zielgruppenaktivierung“" style="border:1px solid #4a4a4a" />
<br>

## Leitlinien

[Beachten Sie die Leitlinien auf der Übersichtsseite zur Zielgruppen- und Profilaktivierung.](overview.md)

## Implementierungsschritte

1. [Erstellen Sie Schemas](https://experienceleague.adobe.com/docs/platform-learn/tutorials/schemas/create-a-schema.html?lang=de) für die zu erfassenden Daten.
1. [Erstellen Sie Datensätze](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-ingestion/create-datasets-and-ingest-data.html?lang=de) für die zu erfassenden Daten.
1. [Konfigurieren Sie die korrekten Identitäten und Identitäts-Namespaces](https://experienceleague.adobe.com/docs/platform-learn/tutorials/identities/label-ingest-and-verify-identity-data.html?lang=de) im Schema, um sicherzustellen, dass aufgenommene Daten zu einem einheitlichen Profil zusammengefügt werden können.
1. [Aktivieren Sie die Schemas und Datensätze für Profile](https://experienceleague.adobe.com/docs/platform-learn/tutorials/profiles/bring-data-into-the-real-time-customer-profile.html?lang=de).
1. [Aufnehmen der Daten](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2020.1.dataingestion&amp;lang=de) in Experience Platform.
1. [Stellen Sie in [!UICONTROL Real-Time Customer Data Platform] die Segmentfreigabe](https://www.adobe.com/go/audiences) zwischen Experience Platform und Audience Manager für Zielgruppen bereit, die in Experience Platform für die Freigabe an Audience Manager definiert sind.
1. [Erstellen Sie Segmente](https://experienceleague.adobe.com/docs/platform-learn/tutorials/segments/create-segments.html?lang=de) in Experience Platform. Das System stellt automatisch fest, ob das Segment per Batch oder Streaming evaluiert wird.
1. [Konfigurieren Sie Ziele](https://experienceleague.adobe.com/docs/platform-learn/tutorials/destinations/create-destinations-and-activate-data.html?lang=de) für die Freigabe von Profilattributen Zielgruppenzugehörigkeiten zu gewünschten Zielen.

## Überlegungen bei der Implementierung

* Die Freigabe von Profildaten an Ziele erfordert, dass der spezifische Identitätswert, der vom Ziel in der Ziel-Payload verwendet wird, mit eingeschlossen wird. Jede Identität, die für ein Ziel notwendig ist, muss in Platform aufgenommen und als eine Identität für das [!UICONTROL Echtzeit-Kundenprofil] konfiguriert werden.

* Für Aktivierungsszenarien, in denen Zielgruppen über Experience Platform für Audience Manager freigegeben werden, werden alle im [!UICONTROL Echtzeit-Kundenprofil] enthaltenen Identitäten für Audience Manager freigegeben. Die Zielgruppen aus Experience Platform können über Audience Manager-Ziele freigegeben werden, wenn die erforderlichen Zielidentitäten im [!UICONTROL Echtzeit-Kundenprofil] enthalten sind oder wenn Identitäten im [!UICONTROL Echtzeit-Kundenprofil] mit den erforderlichen Zielidentitäten verbunden werden können, die in Audience Manager verknüpft sind.

## Verwandte Dokumentation

* Produktbeschreibung zu [[!UICONTROL Real-Time Customer Data Platform]](https://helpx.adobe.com/de/legal/product-descriptions/real-time-customer-data-platform.html)
* [Richtlinien für Profile und Segmentierung](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=de)
* [Dokumentation zur Segmentierung](https://experienceleague.adobe.com/docs/experience-platform/segmentation/api/streaming-segmentation.html?lang=de)
* [Dokumentation zu Zielen](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/overview.html?lang=de)

## Verwandte Videos und Tutorials

* Überblick über [[!UICONTROL Real-Time Customer Data Platform]](https://experienceleague.adobe.com/docs/platform-learn/tutorials/application-services/rtcdp/understanding-the-real-time-customer-data-platform.html?lang=de)
* [Demo zu [!UICONTROL Real-Time Customer Data Platform]](https://experienceleague.adobe.com/docs/platform-learn/tutorials/application-services/rtcdp/demo.html?lang=de)
* [Erstellen von Segmenten](https://experienceleague.adobe.com/docs/platform-learn/tutorials/segments/create-segments.html)
