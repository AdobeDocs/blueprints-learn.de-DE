---
title: Aktivierung von Audience und Profil
description: Bieten Sie mit der Echtzeit-Kundendatenplattform zielgruppenaktivierte und profilorientierte Kundenerlebnisse.
solution: Experience Platform, Real-time Customer Data Platform
kt: null
thumbnail: null
exl-id: eeeb4325-d0e8-4fd8-86ab-0b8afdd0b69f
translation-type: tm+mt
source-git-commit: 9e0954334e8b8a8c5bf52651611e7afa165f6d21
workflow-type: tm+mt
source-wordcount: '1249'
ht-degree: 15%

---


# Aktivierung von Audience und Profil

Die Aktivierung von Audience und Profil ist der Schlüssel zum Erfolg in einer datengesteuerten Marketingwelt. Allerdings orientieren sich viele Marken bei der Aktivierung noch immer zunächst am Kanal, was häufig in inkonsistenter Reichweite und Personalisierung endet.

Wenn der Kanal an erster Stelle steht, fungiert jeder Kanal als Silo, in dem Personalisierung für Kunden erfolgt, die auf diesem Kanal mit der Marke interagieren. Diese Herangehensweise spiegelt nicht die Realität wider, in der Kunden über viele verschiedene Touchpoints hinweg mit der Marke interagieren. Audience und Profil-Aktivierung ermöglichen es Marken, Kundeninteraktionen über mehrere Kanal hinweg zu verbinden und ein zentralisiertes Profil und eine Audience zu liefern, die für alle Kanal aktiviert werden können.

| Blueprint | Beschreibung | Experience Cloud-Programme |
|---|---|---|
| **[Anonyme Audience Activation](anonymous.md)** | <ul><li>Identifizieren Sie Zielgruppen basierend auf anonymen und verhaltensbasierten Kundendaten über Web- und Werbekanäle hinweg.</li><li>Third-Party-Zielgruppendaten können für bessere Personalisierung integriert werden.</li></ul> | <ul><li>Adobe Audience Manager</li></ul> |
| **[Online-/Offline-Audience Activation](online-offline.md)** | <ul><li>Aktivieren Sie bekannte Profil-basierte Ziele wie E-Mail-Anbieter, soziale Netzwerke und Werbeziele. </li><li>Verwenden Sie Offline-Attribute und -Ereignis, wie z. B. Offline-Bestellungen, Transaktionen, CRM-Daten oder Treuedaten, sowie Online-Verhalten für Online-Targeting und Personalisierung.</li></ul> | <ul><li>Adobe Experience Platform</li><li> [!UICONTROL Real-Time Customer Data Platform]</li><li>Adobe Audience Manager (optional)</li></ul> |
| **[Aktivierung von Audience und Profil zu Unternehmenszielen](enterprise-destinations.md)** | <ul><li>Replikation und Aktualisierung von Profil- und Audience-Änderungen an Unternehmensdatenspeichern für Aktivierung- und Berichte-Anwendungsfälle. </li></ul><ul><li>Starten Sie eine Verkaufs- oder Supportaktion für den Kunden durch Benachrichtigung über eine Kundenaktion von der [!UICONTROL Echtzeit-Kundendatenplattform] zu Unternehmenssystemen und -anwendungen.</li></ul> | <ul><li>Adobe Experience Platform</li><li>[!UICONTROL Real-Time Customer Data Platform]</li><li>Experience Platform Aktivierung</li><li>Adobe Audience Manager (optional)</li></ul> |
| **[Customer Activity Hub](customer-activity.md)** | <ul><li>Besserer Verbraucherkontext für mitarbeitergestützte Interaktionen wie Support- und Vertriebserlebnisse. Mithilfe der Profil-Suche nach Experience Platformen können Kundendienstmitarbeiter mehr Kontexte erhalten, wie z. B. Einkäufe in letzter Zeit, Interaktionen mit Kampagnen, Eigenschaften, Mitgliedschaften in Audiencen und andere Attribute und Einblicke, die im Echtzeit-Kundenkonto gespeichert werden.</li></ul> | <ul><li>Adobe Experience Platform</li></ul> |

## Grundzüge der Aktivierung für Audience und Profil

* [Richtlinien für Profile und Segmentierung](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=de)

### Leitlinien für die Segmentbewertung und -Aktivierung

| Segmenttyp | Häufigkeit | Durchsatz | Latenz (Segmentbewertung) | Latenz (Segment-Aktivierung) | Aktivierung Nutzlast |
|-|-|-|-|-|-|-|
| Edge-Segmentierung | Die Edge-Segmentierung befindet sich derzeit in der Beta-Phase und ermöglicht eine Bewertung der gültigen Echtzeit-Segmentierung im Edge-Netzwerk für die Echtzeit-Seitenentscheidung über Adobe Target und Adobe Journey Optimizer. |  | ~100 Millisekunden | Direkt für die Personalisierung in Adobe Target, für Profil-Lookups im Edge-Profil und für die Aktivierung über Cookie-basierte Ziele verfügbar. | Audience-Mitgliedschaften auf Edge für Profil-Lookups und Cookie-basierte Ziele.<br>Adobe Target und Journey Optimizer können Audiencen und Profil-Attribute nutzen.  |
| Streaming-Segmentierung | Jedes Mal, wenn ein neues Streaming-Ereignis oder -Datensatz in das Echtzeit-Kundensegment eingebunden wird und die Segmentdefinition ein gültiges Streaming-Profil ist. <br>Anleitungen zu Streaming-Segmentkriterien finden Sie in der  [Segmentierungsdokumentation ](https://experienceleague.adobe.com/docs/experience-platform/segmentation/api/streaming-segmentation.html?lang=de)  | Bis zu 1500 Ereignis pro Sekunde.  | ~ p95 &lt; 5 Minuten | Streaming-Ziele: Streaming-Audiencen werden innerhalb von etwa 10 Minuten aktiviert bzw. je nach den Anforderungen des Zielorts in Kleinststapeln gepackt.<br>Geplante Ziele: Die Mitgliedschaft in Streaming-Audiencen wird im Batch je nach der geplanten Versand-Zielzeit aktiviert. | Streaming-Ziele: Änderungen der Mitgliedschaft in der Audience, Identitätswerte und Profil-Attribute.<br>Geplante Ziele: Änderungen der Mitgliedschaft in der Audience, Identitätswerte und Profil-Attribute. |
| Inkrementelle Segmentierung | Einmal pro Stunde für neue Daten, die seit der letzten inkrementellen oder Batch-Segmentauswertung in das Echtzeit-Profil des Kunden aufgenommen wurden. |  |  | Streaming-Ziele: Inkrementelle Audiencen werden innerhalb von ca. 10 Minuten aktiviert oder je nach Zielbestimmung in Kleinststapeln gepackt.<br>Geplante Ziele: Die Mitgliedschaft in einer inkrementellen Audience wird im Batch aktiviert, je nach der geplanten Versand-Zielzeit. | Streaming-Ziele: Änderungen der Mitgliedschaft in der Audience und nur Identitätswerte.<br>Geplante Ziele: Änderungen der Mitgliedschaft in der Audience, Identitätswerte und Profil-Attribute. |
| Stapelsegmentierung | Einmal pro Tag basierend auf einem vordefinierten Systemset-Plan oder manuell initiiert Ad-hoc über API. |  | Etwa eine Stunde pro Auftrag für bis zu 10 Terabytes Profil-Speichergröße, 2 Stunden pro Auftrag für 10 Terabytes bis 100 Terabytes Profil-Speichergröße. Die Leistung von Stapelsegmentaufträgen hängt von der Anzahl der Profil, der Größe der Profil und der Anzahl der zu evaluierenden Segmente ab. | Streaming-Ziele: Die Batch-Audience-Mitgliedschaften werden innerhalb von etwa 10 Tagen nach Abschluss der Segmentierungsbewertung bzw. des Mikrobatches entsprechend den Anforderungen des Ziels aktiviert.<br>Geplante Ziele: Die Batch-Audience-Mitgliedschaften werden je nach der geplanten Versand-Zielzeit aktiviert. | Streaming-Ziele: Änderungen der Mitgliedschaft in der Audience und nur Identitätswerte.<br>Geplante Ziele: Änderungen der Mitgliedschaft in der Audience, Identitätswerte und Profil-Attribute. |

### Leitlinien für den Austausch von Audiencen über verschiedene Anwendungen

| Audience Application Integrations | Häufigkeit | Durchsatz/Volumen | Latenz (Segmentbewertung) | Latenz (Segment-Aktivierung) |
|-|-|-|-|-|-|
| Echtzeit-Kundendatenplattform bis Audience Manager | Abhängig vom Segmentierungstyp - siehe oben Tabelle mit Segmentierungsgarantien. | Abhängig vom Segmentierungstyp - siehe oben Tabelle mit Segmentierungsgarantien. | Abhängig vom Segmentierungstyp - siehe oben Tabelle mit Segmentierungsgarantien. | Innerhalb von Minuten nach Abschluss der Segmentbewertung.<br>Die anfängliche Synchronisierung der Audience-Konfiguration zwischen der Echtzeit-Kundendatenplattform und dem Audience Manager dauert etwa 4 Stunden.<br>Alle während der 4-Stunden-Audience durchgeführten Mitgliedschaften werden beim nachfolgenden Stapelsegmentierungsauftrag als &quot;bestehende&quot;Audiencen in Audience Manager geschrieben. |
| Echtzeit-Kundendatenplattform nach Ad Cloud | Beachten Sie, dass die Freigabe von Audiencen von der Echtzeit-Kundendatenplattform an Adobe Advertising Cloud Audience Manager erfordert. Für die Integration von Audiencen der Echtzeit-Customer Data Platform in Advertising Cloud gelten dieselben Garantien wie für die Freigabe von Kundendaten in Audience Manager in Echtzeit. | - |-  | - |
| Adobe Analytics to Real-time Customer Data Platform | Derzeit nicht verfügbar | Derzeit nicht verfügbar | Derzeit nicht verfügbar | Derzeit nicht verfügbar |
| Adobe Analytics bis Audience Manager |-  | Standardmäßig können für jede Adobe Analytics Report Suite maximal 75 Audiencen freigegeben werden. Wenn eine Audience Manager-Lizenz verwendet wird, ist die Anzahl der Audiencen, die zwischen Adobe Analytics und Adobe Target oder Adobe Audience Manager und Adobe Target freigegeben werden können, unbegrenzt. | - |-  |


### Leitlinien für die Aktivierung von Attributen und Identitäten

* [!UICONTROL Die Echtzeit-Kundendatenplattform ] kann Audiencen-Mitgliedschaften sowie Attribut- und Identitätsänderungen aktivieren, die für Profil auftreten, die zu einer Aktivierung gehören. Wenn Sie Attribute oder Identitäten aktivieren möchten, müssen Sie ein globales Segment definieren, das alle Profil enthält, an die Attribute und Identitätsaktualisierungen gesendet werden. An diesem Punkt können Sie das Segment und die gewünschten Attribute auswählen, die im Rahmen der Zielkonfiguration aktiviert werden sollen.
* Beachten Sie, dass Batch-Ziele keine Aktivierung von Ereignissen unterstützen, die nur mit Attributen geändert werden. Vollständige oder inkrementelle Audiencen-Mitgliedschaften können zur Aktivierung zusammen mit den ausgewählten Attributen gesendet werden. Sie können jedoch keine Ereignis mit Nur-Attribut-Änderungen über Batch-Ziele aktivieren.

Aktivieren von Stapelsegmenten in Streaming-Ziele

* Die Aktivierung des Stapelsegments auf Streaming-Ziele wird unterstützt. Stapelsegmentaufträge platzieren Meldungen in der Pipeline, sobald der Segmentauftrag für die Streaming-Aktivierung abgeschlossen ist

Aktivieren von Streaming-Segmenten an Batch-Ziele

* Die Streaming-Segmentzielsetzung wird unterstützt. Der Stapelziel-Plan exportiert Profil-Segmentmitgliedschaften basierend auf dem Batch-Zielplan. Dies umfasst sowohl Segmentmitgliedschaften, die über Streaming- als auch Batch-Methoden bestimmt werden.

Aktivieren von Erlebnis-Ereignissen

* Die Aktivierung von unverarbeiteten Erlebnis-Ereignissen wird nicht unterstützt. Zum Aktivieren gegen Erlebnis-Ereignis muss ein Segment mit den erforderlichen Ereignis-Regeln erstellt werden, die die Erlebnis-Logik einschließen oder ausschließen. Dadurch wird ein Segment erstellt, das für Erlebnis-Ereignis definiert wird, und die Segmentmitgliedschaft kann als Proxy zur Aktivierung von unformatierten Erlebnis-Ereignissen aktiviert werden. Erwägen Sie auch, [!UICONTROL Serverseite starten] zu verwenden, um über SDK erfasste unverarbeitete Erlebnis-Ereignis zu aktivieren.


## Verwandte Blog-Posts

* [[!DNL Blueprints for Audience Activation in Adobe Experience Platform]](https://medium.com/adobetech/a-blueprint-for-audience-activation-in-adobe-experience-platform-b2b30fae90fd)
* [[!DNL How Adobe Experience Platform Predictive Audiences improves Personalized Experiences]](https://medium.com/adobetech/how-adobe-experience-platform-predictive-audiences-improves-personalized-experiences-1f75a60cb7a3)
* [[!DNL Adobe Experience Platform Web SDK for Audience Management]](https://medium.com/adobetech/adobe-experience-platform-web-sdk-for-audience-management-751fa6d063bc)
