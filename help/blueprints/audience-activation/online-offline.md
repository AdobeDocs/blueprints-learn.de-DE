---
title: Blueprint zur Online-/Offline-Audience Activation
description: Online-/Offline-Audience Activation.
solution: Experience Platform, Real-time Customer Data Platform, Target, Audience Manager, Analytics, Experience Cloud Services, Data Collection
kt: 7086
exl-id: 011f4909-b208-46db-ac1c-55b3671ee48c
translation-type: tm+mt
source-git-commit: db083e30d8add029e99cade25d561a26da78338e
workflow-type: tm+mt
source-wordcount: '1040'
ht-degree: 34%

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

### Leitlinien für die Segmentbewertung und -Aktivierung

| Segmenttyp | Häufigkeit | Durchsatz | Latenz (Segmentbewertung) | Latenz (Segment-Aktivierung) | Aktivierung Nutzlast |
|---|---|---|---|---|---|
| Edge-Segmentierung | Die Edge-Segmentierung befindet sich derzeit in der Beta-Phase und ermöglicht eine Bewertung der gültigen Echtzeit-Segmentierung im Edge-Netzwerk für die Experience Platform, sodass über Adobe Target und Adobe Journey Optimizer dieselbe Seitenentscheidung getroffen werden kann. |  | ~100 ms | Direkt für die Personalisierung in Adobe Target, für Profil-Lookups im Edge-Profil und für die Aktivierung über Cookie-basierte Ziele verfügbar. | Audience-Mitgliedschaften auf Edge für Profil-Lookups und Cookie-basierte Ziele.<br>Adobe Target und Journey Optimizer können Audiencen und Profil-Attribute nutzen. |
| Streaming-Segmentierung | Jedes Mal, wenn ein neues Streaming-Ereignis oder -Datensatz in das Echtzeit-Profil eines Kunden aufgenommen wird und die Segmentdefinition ein gültiges Streaming-Segment ist. <br>Anleitungen zu Streaming-Segmentkriterien finden Sie in der  [Segmentierungsdokumentation ](https://experienceleague.adobe.com/docs/experience-platform/segmentation/api/streaming-segmentation.html?lang=de)  | Bis zu 1500 Ereignis pro Sekunde | ~ p95 &lt;5min | Streaming-Ziele: Streaming-Audiencen werden innerhalb von etwa 10 Minuten aktiviert bzw. je nach den Anforderungen des Zielorts in Kleinststapeln gepackt.<br>Geplante Ziele: Die Mitgliedschaft in Streaming-Audiencen wird im Batch je nach der geplanten Versand-Zielzeit aktiviert. | Streaming-Ziele: Änderungen der Mitgliedschaft in der Audience, Identitätswerte und Profil-Attribute.<br>Geplante Ziele: Änderungen der Mitgliedschaft in der Audience, Identitätswerte und Profil-Attribute. |
| Inkrementelle Segmentierung | Einmal pro Stunde für neue Daten, die seit der letzten inkrementellen oder Batch-Segmentbewertung in das Echtzeit-Profil des Kunden aufgenommen wurden. |  |  | Streaming-Ziele: Inkrementelle Audiencen werden innerhalb von ca. 10 Minuten aktiviert oder je nach Zielbestimmung in Kleinststapeln gepackt.<br>Geplante Ziele: Die Mitgliedschaft in einer inkrementellen Audience wird im Batch je nach der geplanten Versand-Zielzeit aktiviert. | Streaming-Ziele: Änderungen der Mitgliedschaft in der Audience und nur Identitätswerte.<br>Geplante Ziele: Änderungen der Mitgliedschaft in der Audience, Identitätswerte und Profil-Attribute. |
| Stapelsegmentierung | Einmal pro Tag basierend auf einem vordefinierten Systemset-Plan oder manuell über API initiiert. |  | Etwa eine Stunde pro Arbeitsplatz für eine Speichergröße von bis zu 10 TB Profil, 2 Stunden pro Arbeitsplatz für eine Speichergröße von 10 TB bis 100 TB Profil. Die Leistung von Stapelsegmentaufträgen hängt von der Anzahl der Profil, der Größe der Profil und der Anzahl der zu evaluierenden Segmente ab. | Streaming-Ziele: Die Batch-Audience-Mitgliedschaften werden innerhalb von etwa 10 Tagen nach Abschluss der Segmentierungsbewertung bzw. des Mikrobatches entsprechend den Anforderungen des Ziels aktiviert.<br>Geplante Ziele: Die Batch-Audience-Mitgliedschaften werden je nach der geplanten Versand-Zielzeit aktiviert. | Streaming-Ziele: Änderungen der Mitgliedschaft in der Audience und nur Identitätswerte.<br>Geplante Ziele: Änderungen der Mitgliedschaft in der Audience, Identitätswerte und Profil-Attribute. |

### Leitlinien für den Austausch von Audiencen über verschiedene Anwendungen

| Audience-Anwendungsintegrationen | Häufigkeit | Durchsatz/Volumen | Latenz (Segmentbewertung) | Latenz (Segment-Aktivierung) |
|---|---|---|---|---|
| Echtzeit-Kundendatenplattform bis Audience Manager | Abhängig vom Segmentierungstyp - siehe oben Tabelle mit Segmentierungsgarantien. | Abhängig vom Segmentierungstyp - siehe oben Tabelle mit Segmentierungsgarantien. | Abhängig vom Segmentierungstyp - siehe oben Tabelle mit Segmentierungsgarantien. | Innerhalb von Minuten nach Abschluss der Segmentbewertung.<br>Die anfängliche Synchronisierung der Audience-Konfiguration zwischen der Echtzeit-Kundendatenplattform und dem Audience Manager dauert etwa 4 Stunden.<br>Alle während der 4-Stunden-Audience durchgeführten Mitgliedschaften werden beim nachfolgenden Stapelsegmentierungsauftrag als &quot;bestehende&quot;Audiencen in Audience Manager geschrieben. |
| Echtzeit-Kundendatenplattform nach Ad Cloud | Beachten Sie, dass die Freigabe von Audiencen von der Echtzeit-Kundendatenplattform an Adobe Advertising Cloud Audience Manager erfordert. Für die Integration von Audiencen der Echtzeit-Customer Data Platform in Advertising Cloud gelten dieselben Garantien wie für die Freigabe von Kundendaten in Audience Manager in Echtzeit. | - | - | - |
| Adobe Analytics in Echtzeit-Kundendatenplattform | Aktuell nicht verfügbar | Aktuell nicht verfügbar | Aktuell nicht verfügbar | Aktuell nicht verfügbar |
| Adobe Analytics bis Audience Manager | - | Standardmäßig können für jede Adobe Analytics Report Suite maximal 75 Audiencen freigegeben werden. Wenn eine Audience Manager-Lizenz verwendet wird, ist die Anzahl der Audiencen, die zwischen Adobe Analytics und Adobe Target oder Adobe Audience Manager und Adobe Target freigegeben werden können, unbegrenzt. | - | - |






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
* [Dokumentation zur Segmentierung](https://experienceleague.adobe.com/docs/experience-platform/segmentation/api/streaming-segmentation.html)
* [Dokumentation zu Zielen](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/overview.html?lang=de)

## Verwandte Videos und Tutorials

* [Überblick über Real-Time Customer Data Platform](https://experienceleague.adobe.com/docs/platform-learn/tutorials/application-services/rtcdp/understanding-the-real-time-customer-data-platform.html?lang=de)
* [[!UICONTROL Demo zu Real-Time Customer Data Platform]](https://experienceleague.adobe.com/docs/platform-learn/tutorials/application-services/rtcdp/demo.html?lang=de)
* [Erstellen von Segmenten](https://experienceleague.adobe.com/docs/platform-learn/tutorials/segments/create-segments.html?lang=de)
