---
title: Blueprint zur Online-/Offline-Audience Activation
description: Online-/Offline-Audience Activation.
solution: Experience Platform, Real-time Customer Data Platform, Target, Audience Manager, Analytics, Experience Cloud Services, Data Collection
kt: 7086
exl-id: 011f4909-b208-46db-ac1c-55b3671ee48c
translation-type: tm+mt
source-git-commit: 009a55715b832c3167e9a3413ccf89e0493227df
workflow-type: tm+mt
source-wordcount: '731'
ht-degree: 0%

---

# Blueprint zur Online-/Offline-Audience Activation

Verwenden Sie Offline-Attribute und Ereignis wie Offline-Bestellungen, Transaktionen, CRM-Daten oder Treuedaten sowie Online-Verhalten für Online-Targeting und Personalisierung.

Aktivieren Sie Audiencen zu bekannten Profil-basierten Zielen wie E-Mail-Anbietern, sozialen Netzwerken und Werbezielen.

## Anwendungsfälle

* Audience-Targeting für bekannte Audiencen an Social- und Werbezielen.
* Online-Personalisierung mit Online- und Offline-Attributen.
* Aktivieren Sie Audiencen für bekannte Kanal wie E-Mail und SMS.

## Anwendungen

* Adobe Experience Platform
* [!UICONTROL Echtzeit-Kundendatenplattform]

## Architektur

<img src="assets/onoff.svg" alt="Referenzarchitektur für das Konzept der Online-/Offline-Audience Activation" style="border:1px solid #4a4a4a" />

## Guardraht

* [Profil- und Segmentierungsrichtlinien](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=en)
* Stapelsegmentaufträge werden einmal pro Tag basierend auf dem vorab festgelegten Zeitplan ausgeführt. Segmentexportaufträge werden dann vor dem geplanten Versand ausgeführt. Beachten Sie, dass Stapelsegmentaufträge und Ziel-Versand-Aufträge separat ausgeführt werden. Stapelsegmentaufträge und die Exportauftragsleistung hängen von der Anzahl der Profil, der Größe der Profil und der Anzahl der zu evaluierenden Segmente ab.
* Streaming-Segmentaufträge werden innerhalb weniger Minuten nach dem Eintreffen der Streaming-Daten in Profil ausgewertet. Die Segmentmitgliedschaft wird dann sofort in das Profil geschrieben und ein Ereignis gesendet, in dem Anwendungen abonniert werden können.
* Die Streaming-Segmentmitgliedschaft wird für Streaming-Ziele sofort ausgeführt und entweder in einzelnen Segmentmitgliedschaftsmodellen oder in einem Mikrostapel mehrerer Profil-Ereignis bereitgestellt, die von den Erfassungsmustern des Ziels abhängig sind. Geplante Ziele starten vor dem Versand einen Segmentexportauftrag aus Profil für alle im Streaming ausgewerteten Segmente, die über den geplanten Batch-Segment-Versand bereitgestellt werden.
* Für die Freigabe der Segmentmitgliedschaft für [!UICONTROL Echtzeit-Kundendatenplattform] für Audience Manager erfolgt dies innerhalb von Minuten für Streaming-Segmente und innerhalb von Minuten nach Abschluss der Batch-Segmentbewertung für die Stapelsegmentierung.
* Segmente, die von Experience Platform zu Audience Manager freigegeben werden, werden innerhalb von Minuten nach der Segmentrealisierung freigegeben - sei es über die Streaming- oder Batch-Evaluierungsmethode. Es gibt eine anfängliche Segmentkonfigurationssynchronisierung zwischen Experience Platform und Audience Manager, sobald das Segment erstellt wurde. Nach ca. 4 Stunden können die Segmentmitgliedschaften der Experience Platform beginnen, in Audience Manager-Profilen realisiert zu werden. Audience Die Mitgliedschaft, die vor der Konfiguration der Freigabe von Experience Platformen und Audience Managern oder vor der Synchronisierung der Audience-Metadaten von Experience Platform zu Audience Manager durchgeführt wird, wird erst im Audience Manager ausgeführt, wenn der folgende Segmentauftrag, bei dem &quot;bestehende&quot;Segmentmitgliedschaften freigegeben werden, im folgenden Segment-Auftrag ausgeführt wird.
* Für Batch- oder Streaming-Zielaufträge aus Stapelsegmentaufträgen können Profil-Attributaktualisierungen sowie Segmentmitgliedschaften freigegeben werden.
* Beim Streaming von Segmentierungsaufträgen auf Streaming-Ziele werden nur die Aktualisierungen der Segmentmitgliedschaft freigegeben.

## Implementierungsschritte

1. Schema und Datensätze in Experience Platform konfigurieren.
1. Konfigurieren Sie die richtigen Identitäten und Identitäts-Namensraum auf dem Schema, um sicherzustellen, dass erfasste Daten zu einem einheitlichen Profil gehören können.
1. Aktivieren Sie das Schema und die Datensätze zum Profil.
1. Daten in Plattform aufnehmen
1. Bereitstellung der Segmentfreigabe zwischen Experience Platform und Audience Manager für in der Experience Platform definierte Audiencen, die für Audience Manager freigegeben werden sollen.
1. Autorensegmente in Experience Platform, die im Batch- oder Streaming-Verfahren ausgewertet werden sollen. Das System ermittelt automatisch, ob das Segment als Stapel oder Streaming ausgewertet wird.
1. Konfigurieren Sie Ziele für die Freigabe von Profil-Attributen und die Audience-Mitgliedschaft für die gewünschten Ziele.

## Überlegungen zur Implementierung

* Die Freigabe von Profil-Daten an Ziele erfordert, dass Sie den vom Ziel verwendeten spezifischen Identitätswert in die Ziel-Payload aufnehmen. Jede für ein Zielgruppen-Ziel erforderliche Identität muss in Platform integriert und als Identitätsdatei für das [!UICONTROL Echtzeit-Profil des Kunden] konfiguriert werden.

* Bei Aktivierungen, bei denen Audiencen von Experience Platform zu Audience Manager freigegeben werden, werden alle im [!UICONTROL Echtzeit-Kundenstamm] enthaltenen Identitäten für Audience Manager freigegeben. Die Audiencen aus der Experience Platform können über Audience Manager-Ziele freigegeben werden, wenn die erforderlichen Ziel-IDs im [!UICONTROL Echtzeit-Kundenstamm] enthalten sind oder wenn Identitäten im [!UICONTROL Echtzeit-Kundenstamm] mit den erforderlichen Ziel-IDs verknüpft werden können, die in Audience Manager verknüpft sind.

## Verwandte Dokumentation

* [[!UICONTROL Echtzeit-Datenplattform ] für KundenProduktbeschreibung](https://helpx.adobe.com/legal/product-descriptions/real-time-customer-data-platform.html)
* [Profil- und Segmentierungsrichtlinien](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=en)
* [Dokumentation zur Segmentierung](https://experienceleague.adobe.com/docs/experience-platform/segmentation/api/streaming-segmentation.html)
* [Dokumentation zu Zielen](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/overview.html)

## Verwandte Videos und Tutorials

* [[!UICONTROL Echtzeit-] Plattform für Kundendaten](https://experienceleague.adobe.com/docs/platform-learn/tutorials/application-services/rtcdp/understanding-the-real-time-customer-data-platform.html)
* [Demo der  [!UICONTROL Echtzeit-Kundendatenplattform]](https://experienceleague.adobe.com/docs/platform-learn/tutorials/application-services/rtcdp/demo.html)
* [Segmente erstellen](https://experienceleague.adobe.com/docs/platform-learn/tutorials/segments/create-segments.html)
