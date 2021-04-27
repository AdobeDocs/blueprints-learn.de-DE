---
title: Blueprint für die Aktivierung von Audiencen und Profilen zu Unternehmenszielen
description: Aktivierung von Audience und Profil zu Unternehmenszielen
solution: Experience Platform,Real-time Customer Data Platform
kt: 7475
exl-id: 32133174-eb28-44ce-ab2a-63fcb5b51cb5,None
translation-type: tm+mt
source-git-commit: 2f35195b875d85033993f31c8cef0f85a7f6cccc
workflow-type: tm+mt
source-wordcount: '1003'
ht-degree: 15%

---

# Blueprint für die Aktivierung von Audiencen und Profilen zu Unternehmenszielen

Geben Sie Profil- und Audiencen-Änderungen und Ereignis im Streaming- oder Batch-Format von [!UICONTROL Kundendatenplattform in Echtzeit] in Unternehmensdatenspeicher und -anwendungen frei. Diese Profil- und Audience-Ereignis können verwendet werden, um eine Verkaufs- oder Supportaktion für den Kunden einzuleiten, z. B. im Anschluss an einen abgebrochenen Antragsprozess oder eine Webinar-Registrierung, oder um Unternehmensanwendungen mit den neuesten Kundenattributen und Informationen von [!UICONTROL Kundendatenplattform in Echtzeit] zu aktualisieren.

## Anwendungsfälle

* Aktivierung von Profil und Audience zu Cloud-Datenspeicherung-Zielen oder Streaming-Zielen für die Unternehmensverfolgung, Datenspeicherung, Analyse und Aktivierung von Kundendaten und -einsichten.

## Programme

* Adobe Experience Platform Aktivierung

## Architektur

<img src="assets/enterprise_destination.svg" alt="Referenzarchitektur für das Enterprise Aktivierung Szenario" style="border:1px solid #4a4a4a" />

## Leitlinien

[Richtlinien für Profile und Segmentierung](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=de)

### Leitlinien für die Segmentbewertung und -Aktivierung

| Segmenttyp | Häufigkeit | Durchsatz | Latenz (Segmentbewertung) | Latenz (Segment-Aktivierung) | Aktivierung Nutzlast |
|-|-|-|-|-|-|-|
| Edge-Segmentierung | Die Edge-Segmentierung befindet sich derzeit in der Beta-Phase und ermöglicht eine Bewertung der gültigen Echtzeit-Segmentierung im Edge-Netzwerk für die Echtzeit-Seitenentscheidung über Adobe Target und Adobe Journey Optimizer. |  | ~100 ms | Direkt für die Personalisierung in Adobe Target, für Profil-Lookups im Edge-Profil und für die Aktivierung über Cookie-basierte Ziele verfügbar. | Audience-Mitgliedschaften auf Edge für Profil-Lookups und Cookie-basierte Ziele.<br>Adobe Target und Journey Optimizer können Audiencen und Profil-Attribute nutzen.  |
| Streaming-Segmentierung | Jedes Mal, wenn ein neues Streaming-Ereignis oder -Datensatz in das Echtzeit-Profil des Kunden aufgenommen wird und die Segmentdefinition ein gültiges Streaming-Segment ist. <br>Anleitungen zu Streaming-Segmentkriterien finden Sie in der  [Segmentierungsdokumentation ](https://experienceleague.adobe.com/docs/experience-platform/segmentation/api/streaming-segmentation.html?lang=de)  | Bis zu 1500 Ereignis pro Sekunde.  | ~ p95 &lt;5min | Streaming-Ziele: Streaming-Audiencen werden innerhalb von etwa 10 Minuten aktiviert bzw. je nach den Anforderungen des Zielorts in Kleinststapeln gepackt.<br>Geplante Ziele: Die Mitgliedschaft in Streaming-Audiencen wird im Batch je nach der geplanten Versand-Zielzeit aktiviert. | Streaming-Ziele: Änderungen der Mitgliedschaft in der Audience, Identitätswerte und Profil-Attribute.<br>Geplante Ziele: Änderungen der Mitgliedschaft in der Audience, Identitätswerte und Profil-Attribute. |
| Inkrementelle Segmentierung | Einmal pro Stunde für neue Daten, die seit der letzten inkrementellen oder Batch-Segmentbewertung in das Echtzeit-Profil des Kunden aufgenommen wurden. |  |  | Streaming-Ziele: Inkrementelle Audiencen werden innerhalb von ca. 10 Minuten aktiviert oder je nach Zielbestimmung in Kleinststapeln gepackt.<br>Geplante Ziele: Die Mitgliedschaft in einer inkrementellen Audience wird im Batch je nach der geplanten Versand-Zielzeit aktiviert. | Streaming-Ziele: Änderungen der Mitgliedschaft in der Audience und nur Identitätswerte.<br>Geplante Ziele: Änderungen der Mitgliedschaft in der Audience, Identitätswerte und Profil-Attribute. |
| Stapelsegmentierung | Einmal pro Tag basierend auf einem vordefinierten Systemset-Plan oder manuell initiiert Ad-hoc über API. |  | Etwa eine Stunde pro Arbeitsplatz für bis zu 10 TB Profil Store Größe, 2 Stunden pro Arbeitsplatz für 10 TB bis 100 TB Profil Store Größe. Die Leistung von Stapelsegmentaufträgen hängt von der Anzahl der Profil, der Größe der Profil und der Anzahl der zu evaluierenden Segmente ab. | Streaming-Ziele: Die Batch-Audience-Mitgliedschaften werden innerhalb von etwa 10 Tagen nach Abschluss der Segmentierungsbewertung bzw. des Mikrobatches entsprechend den Anforderungen des Ziels aktiviert.<br>Geplante Ziele: Die Batch-Audience-Mitgliedschaften werden je nach der geplanten Versand-Zielzeit aktiviert. | Streaming-Ziele: Änderungen der Mitgliedschaft in der Audience und nur Identitätswerte.<br>Geplante Ziele: Änderungen der Mitgliedschaft in der Audience, Identitätswerte und Profil-Attribute. |



## Implementierungsschritte

1. Erstellen Sie Schema für die Datenerfassung.
1. Erstellen Sie Datensätze, damit Daten erfasst werden.
1. Konfigurieren Sie die korrekten Identitäten und Identitäts-Namespaces im Schema, um sicherzustellen, dass aufgenommene Daten zu einem einheitlichen Profil zusammengefügt werden können.
1. Aktivieren Sie die Schema und Datensätze für die Verarbeitung von Profilen.
1. Konfigurieren Sie alle Quellen für die Datenerfassung.
1. Autorensegmente in Experience Platform, die im Batch- oder Streaming-Verfahren ausgewertet werden sollen. Das System stellt automatisch fest, ob das Segment per Batch oder Streaming evaluiert wird.
1. Konfigurieren Sie Ziele für die Freigabe von Profilattributen Zielgruppenzugehörigkeiten zu gewünschten Zielen.

## Überlegungen bei der Implementierung

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

* [Dokumentation zu Zielen](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/overview.html?lang=de)
* [Übersicht über die Ziele der Cloud-Datenspeicherung](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/cloud-storage/overview.html?lang=en#catalog)
* [HTTP-Ziel](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/http-destination.html?lang=en#overview)
* [Produktbeschreibung zu Real-Time Customer Data Platform](https://helpx.adobe.com/de/legal/product-descriptions/real-time-customer-data-platform.html)
* [Profil- und Segmentierungsrichtlinien](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=en)
* [Dokumentation zur Segmentierung](https://experienceleague.adobe.com/docs/experience-platform/segmentation/api/streaming-segmentation.html)

## Verwandte Videos und Tutorials

* [Überblick über Real-Time Customer Data Platform](https://experienceleague.adobe.com/docs/platform-learn/tutorials/application-services/rtcdp/understanding-the-real-time-customer-data-platform.html?lang=de)
* [[!UICONTROL Demo zu Real-Time Customer Data Platform]](https://experienceleague.adobe.com/docs/platform-learn/tutorials/application-services/rtcdp/demo.html?lang=de)
* [Erstellen von Segmenten](https://experienceleague.adobe.com/docs/platform-learn/tutorials/segments/create-segments.html?lang=de)
