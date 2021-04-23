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
ht-degree: 81%

---

# Blueprint zur Online-/Offline-Audience Activation

Verwenden Sie Offline-Attribute und -Ereignisse, wie Offline-Bestellungen, Transaktionen, CRM oder Treue-Daten gemeinsam mit Online-Verhaltensdaten für Online-Targeting und Personalisierung.

Aktivieren Sie Zielgruppen für bekannte, profilbasierte Ziele, wie E-Mail-Anbieter, Social Media und Werbeziele.

## Anwendungsfälle

* Zielgruppen-Targeting für bekannte Zielgruppen in Social-Media- und Werbezielen.
* Online-Personalisierung mit Online- und Offline-Attributen.
* Aktivierung von Zielgruppen für bekannte Kanäle, wie E-Mail und SMS.

## Programme

* Adobe Experience Platform
* [!UICONTROL Real-Time Customer Data Platform]

## Architektur

<img src="assets/onoff.svg" alt="Referenzarchitektur für das Konzept der Online-/Offline-Audience Activation" style="border:1px solid #4a4a4a" />

## Leitlinien

* [Richtlinien für Profile und Segmentierung](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=de)
* Batch-Segmentaufträge werden einmal täglich basierend auf dem festgelegten Zeitplan ausgeführt. Segmentexportaufträge werden dann vor der geplanten Zielbereitstellung ausgeführt. Beachten Sie, das Batch-Segment-Aufträge und Zielbereitstellungsaufträge separat ausgeführt werden. Batch-Segmentaufträge und die Performance von Exportaufträgen hängen von der Anzahl der Profile, deren Größe und der Anzahl der zu evaluierenden Segmente ab.
* Streaming-Segmentaufträge werden innerhalb von Minuten nach der Ankunft von Streaming-Daten im Profile evaluiert. die Segmentzugehörigkeit wird sofort in das Profil geschrieben und ein Ereignis für das Abonnieren von Programmen wird gesendet.
* Auf die Streaming-Segmentzugehörigkeit wird sofort bezüglich Streaming-Zielen reagiert. Sie wird abhängig von den Aufnahmemustern des Ziels entweder in einzelnen Segmentzugehörigkeitsereignissen oder als Mikro-Batch mit mehreren Profilereignissen bereitgestellt. Die geplanten Ziele lösen vor der Bereitstellung einen Segmentexport-Auftrag vom Profil vor der Lieferung aus. Dies gilt für alle im Streaming evaluierten Segmente, die über eine geplante Batch-Segmentbereitstellung bereitgestellt werden.
* Für die Freigabe der Segmentmitgliedschaft für [!UICONTROL Echtzeit-Kundendatenplattform] für Audience Manager erfolgt dies innerhalb von Minuten für Streaming-Segmente und innerhalb von Minuten nach Abschluss der Batch-Segmentbewertung für die Stapelsegmentierung.
* Segmente, die von Experience Platform an Audience Manager freigegeben werden, werden innerhalb von Minuten nach der Segmentrealisierung freigegeben - entweder über Streaming- oder Batch-Evaluierung. Es gibt eine anfängliche Segmentkonfigurationssynchronisierung zwischen Experience Platform und Audience Manager, sobald das Segment erstellt wurde. Nach ca. 4 Stunden können die Segmentmitgliedschaften der Experience Platform beginnen, in Audience Manager-Profilen realisiert zu werden. Die Zielgruppenzugehörigkeit, die vor der Konfiguration der Zielgruppenfreigabe zwischen Experience Platform und der Audience Manager-Zielgruppe oder vor dem Synchronisieren der Zielgruppen-Metadaten von Experience Platform mit Audience Manager realisiert wird, wird erst im nächsten Segmentauftrag in Audience Manager realisiert, in dem „vorhandene“ Segmentzugehörigkeiten freigegeben werden.
* Batch- oder Streaming-Zielaufträge aus Batch-Segmentaufträgen können Aktualisierungen von Profilattributen sowie Segmentzugehörigkeiten teilen.
* Beim Streamen von Segmentierungsaufträgen an Streaming-Ziele werden nur Aktualisierungen der Segmentzugehörigkeit geteilt.

## Implementierungsschritte

1. Konfigurier Sie Schemas und Datensätze in Experience Platform.
1. Konfigurieren Sie die korrekten Identitäten und Identitäts-Namespaces im Schema, um sicherzustellen, dass aufgenommene Daten zu einem einheitlichen Profil zusammengefügt werden können.
1. Aktivieren Sie das Schema und Datensätze für Profile.
1. Nehmen Sie Daten in Platform auf.
1. Bereitstellung der Segmentfreigabe zwischen Experience Platform und Audience Manager für in der Experience Platform definierte Audiencen, die für Audience Manager freigegeben werden sollen.
1. Erstellen Sie in Experience Platform Segmente, die per Batch oder Streaming evaluiert werden sollen. Das System stellt automatisch fest, ob das Segment per Batch oder Streaming evaluiert wird.
1. Konfigurieren Sie Ziele für die Freigabe von Profilattributen Zielgruppenzugehörigkeiten zu gewünschten Zielen.

## Überlegungen bei der Implementierung

* Die Freigabe von Profildaten an Ziele erfordert, dass der spezifische Identitätswert, der vom Ziel in der Ziel-Payload verwendet wird, mit eingeschlossen wird. Jede für ein Zielgruppen-Ziel erforderliche Identität muss in Platform integriert und als Identitätsdatei für das [!UICONTROL Echtzeit-Profil des Kunden] konfiguriert werden.

* Für Aktivierungsszenarien, in denen Zielgruppen über Experience Platform für Audience Manager freigegeben werden, werden alle im [!UICONTROL Echtzeit-Kundenprofil] enthaltenen Identitäten für Audience Manager freigegeben. Die Zielgruppen aus Experience Platform können über Audience Manager-Ziele freigegeben werden, wenn die erforderlichen Zielidentitäten im [!UICONTROL Echtzeit-Kundenprofil] enthalten sind oder wenn Identitäten im [!UICONTROL Echtzeit-Kundenprofil] mit den erforderlichen Zielidentitäten verbunden werden können, die in Audience Manager verknüpft sind.

## Verwandte Dokumentation

* [Produktbeschreibung zu Real-Time Customer Data Platform](https://helpx.adobe.com/de/legal/product-descriptions/real-time-customer-data-platform.html)
* [Profil- und Segmentierungsrichtlinien](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=en)
* [Dokumentation zur Segmentierung](https://experienceleague.adobe.com/docs/experience-platform/segmentation/api/streaming-segmentation.html?lang=de)
* [Dokumentation zu Zielen](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/overview.html?lang=de)

## Verwandte Videos und Tutorials

* [Überblick über Real-Time Customer Data Platform](https://experienceleague.adobe.com/docs/platform-learn/tutorials/application-services/rtcdp/understanding-the-real-time-customer-data-platform.html?lang=de)
* [[!UICONTROL Demo zu Real-Time Customer Data Platform]](https://experienceleague.adobe.com/docs/platform-learn/tutorials/application-services/rtcdp/demo.html?lang=de)
* [Erstellen von Segmenten](https://experienceleague.adobe.com/docs/platform-learn/tutorials/segments/create-segments.html?lang=de)
