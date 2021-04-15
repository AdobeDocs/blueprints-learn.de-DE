---
title: Blueprint für die Aktivierung von Audiencen und Profilen zu Unternehmenszielen
description: Aktivierung von Audience und Profil zu Unternehmenszielen
solution: Experience Platform,Real-time Customer Data Platform
kt: 7475
exl-id: 32133174-eb28-44ce-ab2a-63fcb5b51cb5,None
translation-type: tm+mt
source-git-commit: b0664edc3d29d693d33eefc3b3c6da8bf7308224
workflow-type: tm+mt
source-wordcount: '660'
ht-degree: 0%

---

# Blueprint für die Aktivierung von Audiencen und Profilen zu Unternehmenszielen

Geben Sie Profil- und Audiencen-Änderungen und Ereignis im Streaming- oder Batch-Format von [!UICONTROL Kundendatenplattform in Echtzeit] in Unternehmensdatenspeicher und -anwendungen frei. Diese Profil- und Audience-Ereignis können verwendet werden, um eine Verkaufs- oder Supportaktion für den Kunden einzuleiten, z. B. im Anschluss an einen abgebrochenen Antragsprozess oder eine Webinar-Registrierung, oder um Unternehmensanwendungen mit den neuesten Kundenattributen und Informationen von [!UICONTROL Kundendatenplattform in Echtzeit] zu aktualisieren.

## Anwendungsfälle

* Aktivierung von Profil und Audience zu Cloud-Datenspeicherung-Zielen oder Streaming-Zielen für die Unternehmensverfolgung, Datenspeicherung, Analyse und Aktivierung von Kundendaten und -einsichten.

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
Einmal pro Tag oder manuell über API initiiert.

* Etwa 1 Stunde pro Arbeitsplatz für bis zu 10 TB Profil
* Etwa 2 Stunden pro Arbeitsplatz bei einer Speichergröße von 10 TB bis 100 TB Profil

## Implementierungsschritte

1. Erstellen Sie Schema für die Datenerfassung.
1. Erstellen Sie Datensätze, damit Daten erfasst werden.
1. Konfigurieren Sie die richtigen Identitäten und Identitäts-Namensraum auf dem Schema, um sicherzustellen, dass erfasste Daten zu einem einheitlichen Profil gehören können.
1. Aktivieren Sie die Schema und Datensätze für die Verarbeitung von Profilen.
1. Konfigurieren Sie alle Quellen für die Datenerfassung.
1. Autorensegmente in Experience Platform, die im Batch- oder Streaming-Verfahren ausgewertet werden sollen. Das System ermittelt automatisch, ob das Segment als Stapel oder Streaming ausgewertet wird.
1. Konfigurieren Sie Ziele für die Freigabe von Profil-Attributen und die Audience-Mitgliedschaft für die gewünschten Ziele.

## Überlegungen zur Implementierung

Aktivieren von Attributen und Identitäten

* [!UICONTROL Die Echtzeit-Kundendatenplattform ] kann Audiencen-Mitgliedschaften sowie Attribut- und Identitätsänderungen aktivieren, die für Profil auftreten, die zu einer Aktivierung gehören. Wenn Sie Attribute oder Identitäten aktivieren möchten, müssen Sie ein globales Segment definieren, das alle Profil enthält, an die Attribute und Identitätsaktualisierungen gesendet werden. An diesem Punkt können Sie das Segment und die gewünschten Attribute auswählen, die im Rahmen der Zielkonfiguration aktiviert werden sollen.
* Beachten Sie, dass Batch-Ziele keine Aktivierung von Ereignissen unterstützen, die nur mit Attributen geändert werden. Vollständige oder inkrementelle Audiencen-Mitgliedschaften können zur Aktivierung zusammen mit den ausgewählten Attributen gesendet werden. Sie können jedoch keine Ereignis mit Nur-Attribut-Änderungen über Batch-Ziele aktivieren.

Aktivieren von Stapelsegmenten in Streaming-Ziele

* Die Aktivierung des Stapelsegments auf Streaming-Ziele wird unterstützt. Stapelsegmentaufträge platzieren Meldungen in der Pipeline, sobald der Segmentauftrag für die Streaming-Aktivierung abgeschlossen ist

Aktivieren von Streaming-Segmenten an Batch-Ziele

* Die Streaming-Segmentzielsetzung wird unterstützt. Der Stapelziel-Plan exportiert Profil-Segmentmitgliedschaften basierend auf dem Batch-Zielplan. Dies umfasst sowohl Segmentmitgliedschaften, die über Streaming- als auch Batch-Methoden bestimmt werden.

Aktivieren von Erlebnis-Ereignissen

* Die Aktivierung von unverarbeiteten Erlebnis-Ereignissen wird nicht unterstützt. Zum Aktivieren gegen Erlebnis-Ereignis muss ein Segment mit den erforderlichen Ereignis-Regeln erstellt werden, die die Erlebnis-Logik einschließen oder ausschließen. Dadurch wird ein Segment erstellt, das für Erlebnis-Ereignis definiert wird, und die Segmentmitgliedschaft kann als Proxy zur Aktivierung von unformatierten Erlebnis-Ereignissen aktiviert werden. Erwägen Sie auch, [!UICONTROL Serverseite starten] zu verwenden, um über SDK erfasste unverarbeitete Erlebnis-Ereignis zu aktivieren.

## Verwandte Dokumentation

* [Dokumentation zu Zielen](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/overview.html)
* [Übersicht über die Ziele der Cloud-Datenspeicherung](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/cloud-storage/overview.html?lang=en#catalog)
* [HTTP-Ziel](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/http-destination.html?lang=en#overview)
* [[!UICONTROL Echtzeit-Datenplattform ] für KundenProduktbeschreibung](https://helpx.adobe.com/legal/product-descriptions/real-time-customer-data-platform.html)
* [Profil- und Segmentierungsrichtlinien](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=en)
* [Dokumentation zur Segmentierung](https://experienceleague.adobe.com/docs/experience-platform/segmentation/api/streaming-segmentation.html)

## Verwandte Videos und Tutorials

* [[!UICONTROL Echtzeit-] Plattform für Kundendaten](https://experienceleague.adobe.com/docs/platform-learn/tutorials/application-services/rtcdp/understanding-the-real-time-customer-data-platform.html)
* [Demo der  [!UICONTROL Echtzeit-Kundendatenplattform]](https://experienceleague.adobe.com/docs/platform-learn/tutorials/application-services/rtcdp/demo.html)
* [Segmente erstellen](https://experienceleague.adobe.com/docs/platform-learn/tutorials/segments/create-segments.html)
