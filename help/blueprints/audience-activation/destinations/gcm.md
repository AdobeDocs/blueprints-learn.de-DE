---
title: 'Blueprint: Aktivierung mit Online- und Offline-Daten'
description: Online-/Offline-Zielgruppenaktivierung.
solution: Experience Platform, Real-time Customer Data Platform, Target, Audience Manager, Analytics, Experience Cloud Services, Data Collection
kt: 7086
source-git-commit: f1477d39a2b2349708ad74625bab6c5f4012ae1e
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Blueprint: Aktivierung mit Online- und Offline-Daten

Verwenden Sie Offline-Attribute und -Ereignisse, wie Offline-Bestellungen, Transaktionen, CRM oder Treue-Daten gemeinsam mit Online-Verhaltensdaten für Online-Targeting und Personalisierung.

Aktivieren Sie Zielgruppen für bekannte, profilbasierte Ziele, wie E-Mail-Anbieter, Social Media und Werbeziele.

Zusätzliche Details finden Sie in der [Blueprint zur Zielgruppen- und Profilaktivierung mit Experience Cloud-Programmen](platform-and-applications.md) über Integrationen zwischen Experience Platform und Experience Cloud-Programmen.

## Anwendungsfälle

* Zielgruppen-Targeting für bekannte Zielgruppen in Social-Media- und Werbezielen.
* Online-Personalisierung mit Online- und Offline-Attributen.
* Aktivierung von Zielgruppen für bekannte Kanäle, wie E-Mail und SMS.

## Programme

* Adobe Experience Platform
* [!UICONTROL Real-Time Customer Data Platform]

## Architektur

### Aktivierung mit Online- und Offline-Daten mit Zielen

<img src="assets/online_offline_activation.svg" alt="Referenzarchitektur für die Blueprint „Online-/Offline-Zielgruppenaktivierung“" style="width:80%; border:1px solid #4a4a4a" />
<br>

## Leitlinien

[Beachten Sie die Leitlinien auf der Übersichtsseite zur Zielgruppen- und Profilaktivierung.](overview.md)

## Implementierungsschritte

1. [Erstellen Sie Schemas](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2021.1.xdm) für die zu erfassenden Daten.
1. [Erstellen Sie Datensätze](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-ingestion/create-datasets-and-ingest-data.html?lang=de) für die zu erfassenden Daten.
1. [Konfigurieren Sie die korrekten Identitäten und Identitäts-Namespaces](https://experienceleague.adobe.com/docs/platform-learn/tutorials/identities/label-ingest-and-verify-identity-data.html?lang=de) im Schema, um sicherzustellen, dass aufgenommene Daten zu einem einheitlichen Profil zusammengefügt werden können.
1. [Aktivieren Sie die Schemas und Datensätze für Profile](https://experienceleague.adobe.com/docs/platform-learn/tutorials/profiles/bring-data-into-the-real-time-customer-profile.html?lang=de).
1. [Aufnehmen der Daten](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2020.1.dataingestion&amp;lang=de) in Experience Platform.
1. [Stellen Sie in [!UICONTROL Real-Time Customer Data Platform] die Segmentfreigabe](https://www.adobe.com/go/audiences) zwischen Experience Platform und Audience Manager für Zielgruppen bereit, die in Experience Platform für die Freigabe an Audience Manager definiert sind.
1. [Erstellen Sie Segmente](https://experienceleague.adobe.com/docs/platform-learn/tutorials/segments/create-segments.html?lang=de) in Experience Platform. Das System stellt automatisch fest, ob das Segment per Batch oder Streaming evaluiert wird.
1. [Konfigurieren Sie Ziele](https://experienceleague.adobe.com/docs/platform-learn/tutorials/destinations/create-destinations-and-activate-data.html?lang=de) für die Freigabe von Profilattributen Zielgruppenzugehörigkeiten zu gewünschten Zielen.

## Überlegungen bei der Implementierung

* Die Freigabe von Profildaten an Ziele erfordert, dass der spezifische Identitätswert, der vom Ziel in der Ziel-Payload verwendet wird, mit eingeschlossen wird. Jede Identität, die für ein Ziel notwendig ist, muss in Platform aufgenommen und als eine Identität für das [!UICONTROL Echtzeit-Kundenprofil] konfiguriert werden.

### Zielgruppenfreigabe von Real-time Customer Data Platform an Audience Manager

* Die Zielgruppenmitgliedschaft aus RT-CDP wird für Audience Manager per Streaming freigegeben, sobald die Segmentauswertung abgeschlossen ist. Sie wird unabhängig davon, ob die Segmentauswertung im Batch- oder Streaming-Modus erfolgte, in das Echtzeit-Kundenprofil geschrieben. Wenn das qualifizierte Profil die regionalen Routing-Informationen für zugehörige Profilgeräte enthält, wird die Zielgruppenzugehörigkeit von RTCDP auf dem zugehörigen Audience Manager Edge im Streaming-Modus qualifiziert. Wenn die regionalen Routing-Informationen in den letzten 14 Tagen auf ein Profil mit einem Zeitstempel angewendet wurden, werden sie im Streaming am Audience Manager Edge ausgewertet. Wenn die RTCDP-Profile keine regionalen Routing-Informationen enthalten oder die regionalen Routing-Informationen älter als 14 Tage sind, werden die Profilmitgliedschaften zur Batch-basierten Auswertung und Aktivierung an den Audience Manager-Hub-Speicherort gesendet. Profile, die für die Edge-Aktivierung infrage kommen, werden innerhalb von Minuten nach der Segmentqualifizierung von RTCDP aktiviert. Profile, die nicht für die Edge-Aktivierung qualifiziert sind, qualifizieren sich für den Audience Manager-Hub und verfügen möglicherweise über einen 12 bis 24-Stunden-Zeitraum für die Verarbeitung.

* Regionale Routing-Informationen, für die das Audience Manager-Profil in Edge gespeichert ist, können für die Experience Platform vom Audience Manager, vom Besucher-ID-Dienst, Analytics, Launch oder direkt vom Web SDK als separater Datensatz der Profildatensatzklasse mit der XDM-Feldergruppe &quot;Datenerfassungsregion-Informationen&quot;erfasst werden.

* In Aktivierungsszenarios, in denen Zielgruppen aus Experience Platform für Audience Manager freigegeben werden, werden die folgenden Identitäten automatisch freigegeben: IDFA, GAID, AdCloud, Google, ECID, EMAIL_LC_SHA256. Benutzerdefinierte Namespaces werden derzeit nicht freigegeben.

Die Zielgruppen aus Experience Platform können über Audience Manager-Ziele freigegeben werden, wenn die erforderlichen Zielidentitäten im [!UICONTROL Echtzeit-Kundenprofil] enthalten sind oder wenn Identitäten im [!UICONTROL Echtzeit-Kundenprofil] mit den erforderlichen Zielidentitäten verbunden werden können, die in Audience Manager verknüpft sind.

## Verwandte Dokumentation

* Produktbeschreibung zu [[!UICONTROL Real-Time Customer Data Platform] ](https://helpx.adobe.com/de/legal/product-descriptions/real-time-customer-data-platform.html)
* [Richtlinien für Profile und Segmentierung](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=de)
* [Dokumentation zur Segmentierung](https://experienceleague.adobe.com/docs/experience-platform/segmentation/api/streaming-segmentation.html?lang=de)
* [Dokumentation zu Zielen](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/overview.html?lang=de)

## Verwandte Videos und Tutorials

* Überblick über [[!UICONTROL Real-Time Customer Data Platform] ](https://experienceleague.adobe.com/docs/platform-learn/tutorials/application-services/rtcdp/understanding-the-real-time-customer-data-platform.html?lang=de)
* [Demo zu [!UICONTROL Real-Time Customer Data Platform]](https://experienceleague.adobe.com/docs/platform-learn/tutorials/application-services/rtcdp/demo.html?lang=de)
* [Erstellen von Segmenten](https://experienceleague.adobe.com/docs/platform-learn/tutorials/segments/create-segments.html)